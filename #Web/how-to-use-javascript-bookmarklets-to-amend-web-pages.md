# How to Use JavaScript Bookmarklets to Amend Web Pages

_Captured: 2017-05-25 at 10:23 from [dzone.com](https://dzone.com/articles/how-to-use-javascript-bookmarklets-to-amend-web-pa?edition=300092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-24)_

## Background

When I first learned how to code it was in BASIC with an interpreter. This was great because I didn't have to write a lot of scaffolding code to create an application, I just wrote code and it ran.

I can experience a similar process using JavaScript in the browser console which makes JavaScript a good first language to hack about with and take your first steps in learning how to code.

It also means that I can get a lot done very quickly from the console to help me when I test web applications.

I can manipulate a web application client in my browser by:

  * Changing the DOM.
  * Amending the JavaScript.
  * Changing the values of variables.
  * Adding new elements into the DOM.

A client, in a browser, is ours to command.

## A Set of Twitter Links

Bearing the above in mind. I visited the [TestingCircus.com list of testers on Twitter](https://www.testingcircus.com/testers-in-twitter/) and there were a few names I didn't recognize.

The page handily provides the Twitter handle and the URL, but the URL is a text element, not a clickable URL. Therefore, in order for me to check if I follow that person I have to engage in some manual effort to copy and paste the text into the browser URL field and visit the page.

Ugh, manual effort.

Fortunately, however:

  * This is a web page.
  * The URLs are on the page as text.
  * I know how to get the URL from the page with JavaScript.
  * I know how to amend the DOM with JavaScript.
  * I can write some JavaScript to convert all the text URLs into clickable URLs.

The full process for this is shown in a [video on youtube](https://youtu.be/M4NnLlffh2w).

## The Code

If I inspect the page and paste the following code into the JavaScript console and hit return to execute the code, then all the Twitter URLs will become clickable:

  * Get all the elements with tag name "td".
  * Iterate over them all in a `for` loop.
  * If the text in the table data/cell starts with "https://" then: 
    * Change the text so that it is a clickable link.

## The Bookmarklet

Since I will probably want to do this a few times, I can make this easier by creating a bookmarklet.

A bookmarklet is Javascript code that is wrapped in an anonymous function that executes immediately and is prefixed with "javascript:" that is added to your browser's bookmarks

If I paste the above code into my bookmark toolbar then I'll create a bookmarklet that I can click on to change all the listed URLs to clickable URLs.

Bookmarklets can sync across machines, e.g. if logged into the Chrome Browser then your bookmarklets sync across all logged in browser sessions.

## A Tool

Because I create small JavaScript snippets and convert them into bookmarklets to help me with my testing and general web navigation, I created a tool to help with this process.

You can see the tool in action in the video below.

## End Notes

  * A small knowledge of JavaScript can help you do very powerful actions.
  * JavaScript is a useful language to learn to 'do stuff' quickly.
  * You can automate web applications from the JavaScript console.
  * The Web Client pages are manipulatable and yours to control.
  * Bookmarklets allow you have easy access to custom JavaScript.

## The Video
