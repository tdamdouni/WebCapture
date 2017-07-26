# How to create a contact form for a GitHub Pages served Jekyll website

_Captured: 2016-12-11 at 17:40 from [coderwall.com](https://coderwall.com/p/8lq1ba/how-to-create-a-contact-form-for-a-github-pages-served-jekyll-website)_

I have recently put together a [Jekyll](http://jekyllrb.com) website hosted in [GitHub Pages](http://pages.github.com) here: [tgarcia.com.br](http://tgarcia.com.br)

As you probably know, GitHub Pages serve static-only websites (which I will refer as front-end), which means there is no available back-end to create things such as contact form.

So firstly I was just giving my email address on the website, which turned out to be BAD IDEA. Thinking better I decided I needed a contact form with a Captcha challenge - and for that I need a back-end to send this email.

It didn't take long for me to find the post [Create a contact form for Jekyll](http://www.tommyblue.it/2012/08/28/create-a-contact-form-for-jekyll), which is awesome, however it describes a solution for sites that serve both the front-end and back-end on the same node.

Which differs from my case, once I have the front-end being served on GitHub pages, and the back-end must be served somewhere else (in my case I use [Heroku](http://heroku.com)).

Well, after a weekend of work I was able to put together a solution to contemplate my scenario and here I describe it. I had to add CORS requests handling and I improve the workflow by doing all the validation on the same request, without using sessions to make it more secure and faster.

  * Sign up for a [Heroku](http://heroku.com) free account if you don't have an account already.
  * Create an app on Heroku and pick a meaningful name for you (mine is **tgarcia-contact-form**), otherwise Heroku will generate a random one.
  * Sign up for a [Sendgrid](https://addons.heroku.com/sendgrid) Starter plan on your app.
  * Sign up for a [reCAPTCHA](https://www.google.com/recaptcha) account and register your Heroku back-end (mine is **tgarcia-contact-form.herokuapp.com**). IMPORTANT: select the option to generate it as a GLOBAL KEY, otherwise your GitHub Pages front-end won't work with reCAPTCHA.
  * Create a local git repo for a [Rack-based application](https://devcenter.heroku.com/articles/rack) and add the following files:

**Gemfile**
    
    
    source 'https://rubygems.org'
    ruby '2.0.0'
    gem 'rack'
    gem 'rack-recaptcha'
    gem 'sinatra'
    gem 'pony'
    gem 'json'

**config.ru**
    
    
    require 'rubygems'require 'sinatra'require 'json'require 'rack/recaptcha'require 'pony'use Rack::Recaptcha, :public_key => 'YOUR_PUBLIC_KEY_FROM_RECAPTCHA', :private_key => YOUR_PRIVATE_KEY_FROM_RECAPTCHA'
    helpers Rack::Recaptcha::Helpers
    
    require './application'
    run Sinatra::Application

Please insert your reCAPTCHA's public and private keys where specified.

**application.rb**
    
    
    before do
      content_type :json
      headers 'Access-Control-Allow-Origin' => '*',
              'Access-Control-Allow-Methods' => ['POST']endset :protection, falseset :public_dir, Proc.new { File.join(root, "_site") }
    
    post '/send_email' do
      if recaptcha_valid?
        res = Pony.mail(
          :from => params[:name] + "<" + params[:email] + ">",
          :to => 'YOUR_EMAIL_ADDRESS',
          :subject => "[YOUR FILTER] " + params[:subject],
          :body => params[:message],
          :via => :smtp,
          :via_options => {
            :address              => 'smtp.sendgrid.net',
            :port                 => '587',
            :enable_starttls_auto => true,
            :user_name            => ENV['SENDGRID_USERNAME'],
            :password             => ENV['SENDGRID_PASSWORD'],
            :authentication       => :plain,
            :domain               => 'heroku.com'
          })
        content_type :json
        if res
          { :message => 'success' }.to_json
        else
          { :message => 'failure_email' }.to_json
        end
      else
        { :message => 'failure_captcha' }.to_json
      endend
    
    not_found do
      File.read('_site/404.html')endget '/*' do
      file_name = "_site#{request.path_info}/index.html".gsub(%r{\/+},'/')
      if File.exists?(file_name)
        File.read(file_name)
      else
        raise Sinatra::NotFound
      endend

Please insert your email address and a filter for the email subject.

  * Now you need to add some client-side code that will go to your Jekyll site at GitHub Pages:
    
    
    function showRecaptcha(element) {
      Recaptcha.create('YOUR_PUBLIC_KEY_FROM_RECAPTCHA', element, {
        theme: 'custom', // you can pick another at https://developers.google.com/recaptcha/docs/customization
        custom_theme_widget: 'recaptcha_widget'
      });}function setupRecaptcha() {
      var contactFormHost = 'YOUR_BACKEND_ADDRESS_FROM_HEROKU',
          form = $('#contact-form'),
          notice = form.find('#notice');
    
      if (form.length) {
        showRecaptcha('recaptcha_widget');
    
        form.submit(function(ev){
          ev.preventDefault();
    
          $.ajax({
            type: 'POST',
            url: contactFormHost + 'send_email',
            data: form.serialize(),
            dataType: 'json',
            success: function(response) {
              switch (response.message) {
                case 'success':
                  form.fadeOut(function() {
                    form.html('<h4>' + form.data('success') + '</h4>').fadeIn();
                  });
                  break;
    
                case 'failure_captcha':
                  showRecaptcha('recaptcha_widget');
                  notice.text(notice.data('captcha-failed')).fadeIn();
                  break;
    
                case 'failure_email':
                  notice.text(notice.data('error')).fadeIn();
              }
            },
            error: function(xhr, ajaxOptions, thrownError) {
              notice.text(notice.data('error')).fadeIn();
            }
          });
        });
      }}

And here is my HTML form:
    
    
    <form id="contact-form" class="contact-form" method="post" data-success="Message successfully sent!">
    
      <label for="name">Name</label>
      <input id="name" type="text" name="name" class="field" required autofocus /><br/>
    
      <label for="email">E-mail</label>
      <input id="email" type="email" name="email" class="field" required /><br/>
    
      <label for="subject">Subject</label>
      <input id="subject" type="text" name="subject" class="field" required /><br/>
    
      <label for="message">Message</label>
      <textarea id="message" name="message" required ></textarea><br/>
    
      <label for="recaptcha_response_field">Captcha</label>
      <div id="recaptcha_widget" class="recaptcha">
        <div class="image">
          <div id="recaptcha_image"></div>
        </div>
    
        <div class="headline recaptcha_only_if_image">Enter the words above:</div>
        <div class="headline recaptcha_only_if_audio">Enter the numbers you hear:</div>
    
        <input type="text" id="recaptcha_response_field" name="recaptcha_response_field" required />
    
        <span class="recaptcha_icon"><a href="javascript:Recaptcha.reload()"><i class="fa fa-refresh"></i></a></span>
        <span class="recaptcha_icon recaptcha_only_if_image"><a href="javascript:Recaptcha.switch_type('audio')"><i class="fa fa-volume-up"></i></a></span>
        <span class="recaptcha_icon recaptcha_only_if_audio"><a href="javascript:Recaptcha.switch_type('image')"><i class="fa fa-font"></i></a></span>
        <span class="recaptcha_icon"><a href="javascript:Recaptcha.showhelp()"><i class="fa fa-question-circle"></i></a></span>
      </div><br/>
      <div id="notice" class="notice" data-captcha-failed="Incorrect captcha!" data-error="There was an error sending the message, please try again."></div>
      <button type="submit">Send</button></form><script type="text/javascript" src="http://www.google.com/recaptcha/api/js/recaptcha_ajax.js"></script>

BTW I am using [Font Awesome](http://fontawesome.io) here.

And should you want to see my styles (I used LESS here)
    
    
    .contact-form {
      h4 {
        color: #668944;
        margin-left: 20px;
      }
      label {
        width: 100px;
        margin: 5px 0;
        display: inline-block;
        vertical-align: top;
      }
      input, textarea, .recaptcha, button {
        margin: 5px 0;
        padding: 5px;
        -webkit-border-radius: 5px;
        -moz-border-radius: 5px;
        border-radius: 5px;
        border: 1px solid #bbb;
    
        &:focus {
          outline-color: @accent-color;
        }
      }
      input.field, textarea {
        min-width: 330px;
      }
      input[name=subject], textarea {
        width: 73%;
      }
      textarea {
        height: 150px;
      }
      button {
        border: 0;
        background-color: @accent-color;
        padding: 8px 20px;
        color: #fff;
        margin-top: 20px;
    
        &:hover {
          background-color: darken(@accent-color, 10%);
          color: darken(#fff, 10%);
        }
      }
      .notice {
        display: none;
        background-color: #f2dede;
        border: 1px solid #ebccd1;
        -webkit-border-radius: 5px;
        -moz-border-radius: 5px;
        border-radius: 5px;
        padding: 10px 15px;
        color: #a94442;
        margin-top: 15px;
      }
      .recaptcha {
        padding: 0;
        display: inline-block;
    
        div.image {
          -webkit-border-radius: 5px 5px 0 0;
          -moz-border-radius: 5px 5px 0 0;
          border-radius: 5px 5px 0 0;
          padding: 10px;
          background-color: #fff;
          width: 320px;
    
          br {
            display: none;
          }
          embed, span {
            float: left;
            clear: both;
            a {
              cursor: pointer;
              font-size: 0.9em;
            }
          }
        }
    
        div.headline {
          padding: 5px 5px 0 10px;
        }
    
        input[type=text] {
          margin: 10px;
        }
      }}

In here, @accent-color is my default link color.

I hope it serves you well!

I'd suggest to use something like <http://www.kvstore.io>. It's a key/value pair storage service that supports the "client-side only environments" like static websites.

It's super easy to use it and gives you the strength to manage your data with a full set of RESTful API... I just posted an article on github/jekyll or whatever integration with kvstore.io... : [https://medium.com/](https://medium.com/@lordkada/store-user-generated-content-from-jekyll-github-pages-or-similar-ded76aabf17#.aqjafjiez)[@lordkada](https://coderwall.com/lordkada)/store-user-generated-content-from-jekyll-github-pages-or-similar-ded76aabf17#.aqjafjiez

Just my 2 cents..

DISCLAIMER: I'm the author of kvstore.io ;-)
