# What are websites made of?

_Captured: 2017-05-20 at 09:56 from [www.bbc.co.uk](http://www.bbc.co.uk/academy/articles/art20150410110346412)_

![What are websites made of?](https://ichef.bbc.co.uk/images/ic/832x468/p02lv1l7.jpg)

Web pages on the internet have been around for some time now and like all technology-related things, the way they look, feel and are built is constantly evolving.

In order to create a website we have to consider several things. These could be summarised as: content (what do we want to say? What pictures will we use?), style (what will it look like?), and user experience (how will users interact with the website, using menus, buttons, animation, and so on?).

In web development, these three areas are mainly created using the following different languages:

  * **content **(the text, links and images) is handled using **HTML**
  * **style **(the appearance and layout) is defined in **CSS**
  * **interaction **(how it behaves) is controlled using **JavaScript**

In this article we will look at simple examples of each of these languages and see how they interact to display a web page.

If you would like further information about any of these languages, there are standards provided by the governing bodies, the [World Wide Web Consortium](http://www.w3.org/standards/webdesign/) (HTML, CSS and some JavaScript) and [ECMA](http://www.ecmascript.org/index.php) (JavaScript).

**HTML  
**When you create content for a web page, the browser needs a way of knowing what that content is. Which parts of the content are titles, images, links, and so on?

That's where HTML comes in. **H**yper **T**ext **M**ark-up **L**anguage is a way of labelling bits of the content so the web browser knows what they are.

For example, if we wanted the text, "The quick brown fox…" to be a title (shown on a tab or in the top left hand corner of the browser), we can label it as a title with the

Here's what that might look like:

![The quick brown fox...](http://ichef.bbci.co.uk/images/ic/640xn/p02ksgbg.png)

> _However if we use a_

tag it will be treated as a normal paragraph on the page:
    
    
    The quick brown fox…
    
     

![The quick brown fox...](http://ichef.bbci.co.uk/images/ic/raw/p02ksh90.png)

There are all sorts of other tags we can use to give context and meaning to the contents of a web page, for example:

  * - an 'unordered list' (bullet points as opposed to numbers) 
    * - a division, or part of a page
    * - an image that you want to display on the page

Because technology, and the way that we use it, is subject to constant change, new versions of languages have to be created.** HTML5** is the latest version of HTML. Many websites have been developed with this version in mind as it has lots of exciting new features, for example: the 

tag lets you display a video without needing a video plugin installed. 

In the example below you can see the 

tag. Extra information is given using attributes, for example the 'src' attribute which gives the name and web address of the film we will be watching:

This would look like this on the web page:

![Simple video page](http://ichef.bbci.co.uk/images/ic/640xn/p02kvf6j.png)

This latest version of HTML also includes some new ways of allowing JavaScript to interact with your web page. For example, it can use geolocation to find out where you are. These new capabilities are provided by a series of APIs (application programming interfaces), which can be thought of as libraries of code that give additional functionality. 

Many of the games on the [CBeebies](http:/www.bbc.co.uk/cbeebies/) site take advantage of HTML5's graphical capabilities. HTML5 has a feature that lets you create a drawing canvas (the tag) and write/control images via an API. Another API, called WebGL, allows you to use JavaScript to create 3D images.

The [Helloracer](http://www.helloracer.com/) website builds a 3D Formula 1 car (using and the WebGL API) which you can then drive around your browser using the arrow keys and spacebar. Previously this would have been extremely difficult, if not impossible, to render within the browser.

![Helloracer](http://ichef.bbci.co.uk/images/ic/640xn/p02kvgcd.png)

Some older browsers cannot properly display web pages that use the new HTML5 features.

**CSS  
**You can see from the "quick brown fox" and simple video page examples above that whilst we included content on the page, there was no layout or style (everything was just shoved in the top left hand corner). We can use CSS to introduce styling to a page.

We don't need to change every individual bit of content to edit the style; if we want all normal paragraphs to have blue text, we only need to make that change once. We can also group styles together if they apply to the same tags, elements or groups of content.

In the example you can see that as well as blue text, we have also added a border, set the font/text to 'Arial' and moved the content to the right hand side of the page.

![CSS](http://ichef.bbci.co.uk/images/ic/raw/p02kvgp8.png)

![CSS](http://ichef.bbci.co.uk/images/ic/raw/p02kvh4c.png)

CSS3 is the latest version of CSS, and it has many new styles that you find on modern web pages. Importantly, from a web developer's point of view, it simplifies the code for some styling that previously proved to be very fiddly.

In the example below you can see how the CSS gives rounded corners and a containing box to some text:

![Rounded corners](http://ichef.bbci.co.uk/images/ic/raw/p02l519j.png)

> _The text has been defined using HTML (denoted by the_

tag). Notice that the bits of HTML and CSS are linked by an identifier called myText (which is defined using the 'id' attribute) 

This is the HTML:
    
        This shows how to round corners on boxes in web pages 

This is the CSS:

In the example above, border-radius is how you define the round corners, and padding relates to the space around the text. The box has been given a background colour and a width. 

The 'px' after the numbers is the measurement unit we use and it stands for pixels. In the border-radius settings we are telling the browser to count 10 pixels in from a corner, round it off from there, move to the next corner, count 30 pixels in, round it off from there, and so on for each corner.

Another important consideration when designing a style for a website is the different devices that the web page might be viewed on. A web page designed for a desktop computer might not look good when it is viewed on a smartphone, for example.

Modern web pages are often designed to be 'responsive'. This means that the layout of a page changes depending on the device that is being used to view it. CSS allows us to easily change the layout depending on device capabilities.

The examples below show screenshots of a very simple responsive page:

![Responsive CSS](http://ichef.bbci.co.uk/images/ic/raw/p02l53fk.png)

> _You can see in the CSS that the '@media' option looks at the available screen width of the user's device and displays the appropriate layout:_
    
        @media (min-width: 481px) and (max-width: 768px) {  
     #logo { width:740px; }  
     #logo img { max-width:740px; max-height:222px; }  
      #main { width:740px; }  
      #main-content { width:450px; float:left; }  
      #extras-container { width:200px; float:right; }  
      .extras-content { width:160px; }  
    }  
    @media (min-width: 321px) and (max-width: 480px) {  
      #logo { width:450px; }  
      #logo img { max-width:450px; max-height:135px; padding:0px;}  
      #main { width:450px; }  
      #main-content { width:400px; }  
      #extras-container { width:400px;}  
      .extras-content { width:120px; margin:5px; float:left;}  
      .extras-text { display:none; }  
    }  
    @media (max-width: 320px) {  
      #logo { width:275px; }  
      #logo img { max-width:275px; max-height:83px; padding:0px;}  
      #main { width:250px; }  
      #main-content { width:250px; padding:0px; }  
      .extras-content { width:250px; margin:5px;}  
      .extras-text { display:none; }  
    

**JavaScript  
**We can use JavaScript to give our web pages more interaction, for example: facilitating the buying process on an e-commerce website, or animating parts of a page (scrolling the headlines across a news page, perhaps).

If we wanted to change the content of the box shown in the first CSS example so that when the user clicked the button we gave them a 'Thank You' message, we could use this JavaScript code:
    
        document.getElementById("myText").innerHTML = "Thank You!";  
    

We first tell the browser to look in the document (the web page). We then get the element that we want to change, using its identifier (again you can see that we selected 'myText'). Finally we tell the computer to set the HTML inside the selected element to "Thank You!"

The code above uses something called the 'DOM' (document object model). Every browser keeps a model of the web page in memory, and every part of the web page is represented by its own 'object'. This controls how you select parts of the web page and what you can do with them once they are selected.

Putting together some slight variations of the previous ideas with this JavaScript, we can see what the web page might look like (remember we have a limited amount of content at the moment).

![Simple video page with JavaScript](http://ichef.bbci.co.uk/images/ic/640xn/p02l83n0.png)

> _This is the HTML:_

This is the CSS:
    
        #boxMeIn  
    {  
     border-width:2px;  
     border-style:solid;  
     border-color:#a1a1a1;  
     padding-top:10px;  
     padding-bottom:10px;  
     padding-left:40px;  
     padding-right:40px;  
     background-color:#dddddd;  
     width:555px;  
     border-radius:10px 10px 30px 30px;  
    }  
    button  
     {  
     float:right;  
     }  
    

This is the JavaScript:
    
        function doThis() {  
     document.getElementById("myText").innerHTML = "Thank You!"  
     }  
    

You can see that when the user clicks on the "Yes I did" button, it is directed to a piece of code (a function) called doThis (by the onclick attribute), that's where we gave it the instructions to change the text in the box.

You will also see that the HTML has been changed slightly from our earlier examples. The 

tag is now used to enclose the text and button together in a box, and the text is now enclosed in a tag. The tag is used to enclose some content that we want to select for either styling using CSS or manipulation via JavaScript. 

This is what the result will look like after the button is pressed:

![Simple video page with JavaScript - button pressed](http://ichef.bbci.co.uk/images/ic/raw/p02l8d6d.png)

Earlier on we mentioned the geolocation API that we can use with JavaScript. Here is some sample code and a screenshot showing the result:
    
        function findMe() {  
     navigator.geolocation.getCurrentPosition(show_map, big_error);  
    }  
    function show_map(position) {  
     var latitude = position.coords.latitude;  
     var longitude = position.coords.longitude;  
     var mapme = "http://maps.google.com/maps/api/staticmap?center=" + latitude + "," + longitude + "&zoom=14&size=400x400&sensor=false";  
     var content = '[Link to Map](http://google.co.uk/maps?hl=en&ie=UTF8&z=14&11=' + latitude + )  
    ';  
     content = content + "";  
     document.getElementById('mapHere').innerHTML = content;  
    }  
    function big_error(err) {  
     alert("Error " + err.code + " " + err.message  
    }  
    

![Geolocation with JavaScript](http://ichef.bbci.co.uk/images/ic/raw/p02l8fzc.png)

The JavaScript uses a different part of the DOM (the navigator) to get the geolocation information. Once the browser has tried to find the location it can either go to a function that creates the map (using Google maps), or it can go to a function which handles an error if the location is not available.

**Summary  
**These are just some of the elements that make up a web page. These languages are constantly being evolved by a combination of browser makers and developers as they respond to new possibilities of technology and the way people use the web.

To find out more about HTML, CSS and JavaScript check out the resources below.

##### _Jill Clarke is a freelance trainer and developer working at JB International Training._
