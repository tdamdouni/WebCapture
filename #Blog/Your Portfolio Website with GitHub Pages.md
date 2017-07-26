# Your Portfolio Website with GitHub Pages

_Captured: 2016-12-21 at 19:12 from [thejackalofjavascript.com](http://thejackalofjavascript.com/your-portfolio-website-with-github-pages/)_

In this quick and dirty post, we will see how you can build a static Portfolio website for yourself. We will be leveraging the power of GitHub pages and the default sub-domain that you get when you create an account with GitHub.

First off, you need to be aware of what [GitHub](https://github.com/) is. If you don't, I recommend going through [Git & GitHub for Beginners](http://thejackalofjavascript.com/git-and-github-for-beginners/) and if you not aware of GitHub pages, please go through [Github Pages - Free Hosting](http://thejackalofjavascript.com/github-pages-free-hosting/) as well.

A live demo of what we are going to build : <http://arvindr21.github.io>

**Step 1** : Create a [new](https://github.com/new) Repo named _**username.github.io**_. If your Github username is _arvindr21_, your repo name would be _arvindr21.github.io _and gh-pages will automatically take this to be your home page. Add description if needed. Click on '_Create repository_'

**Step 2** : Navigate to [Start Bootstrap](http://startbootstrap.com/) or [Bootstrap Zero](http://bootstrapzero.com/) or [Luis Zuno's blog](http://luiszuno.com/blog/) or any other place where you can download a quick Portfolio template. You can also build a site from scratch and follow the next steps to deploy to your hosting. I picked this [One Page Resume](http://www.mrova.com/free-one-page-responsive-html-resume-template/) and downloaded it on my machine. (_Please be aware of the License before downloading_)

**Step 3** : Create a folder where you want manage your site. I named my _gh-portfolio_. Next, open terminal/prompt here and clone the repo to your local by running

git clone https://github.com/arvindr21/arvindr21.github.io.git

_Update the command with your repo name._

**Step 4** : Copy the contents of your template to the cloned repo folder. Make sure that _index.html_ file is at the root of this folder.

**Step 5** : Add the changes to the remote repo. Do not forget to CD into the newly created repo folder and then run

git commit -am "Initial Commit"

to stage the newly added files

git push origin master

to push the changes to the remote repo.

Navigate to [http://arvindr21.github.io](http://arvindr21.github.io/) (_http://username.github.io_) to see your newly created website.

_If you are deploying to GitHub pages for the first time, you may need to wait for 10 -15 mins before you see the actual site._

You can also [setup custom domain name](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages) if you want. Say : _http://arvindravulavaru.com_ and that would be redirected to your GitHub hosted page.

And whenever you want to make changes, do them locally and push it to the repo. DO NOT make changes directly to the pages.

You can also host your own blog on GitHub using [jekyll](https://help.github.com/articles/using-jekyll-with-pages). GitHub rocks!!

Thanks for reading! Do comment.  
@arvindr21
