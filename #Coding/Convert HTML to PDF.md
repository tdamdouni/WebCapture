# Convert HTML to PDF

_Captured: 2016-12-10 at 11:04 from [beebole.com](https://beebole.com/blog/general/convert-html-to-pdf-with-full-css-support-an-opensource-alternative-based-on-webkit/)_

As a background task for our web application [BeeBole](http://beebole.com), I was looking for an easy and efficient way to produce PDF documents without being stuck with postscript like syntax or being feature limited in a design point of view.

Last week I discovered the tool I was looking for : [WKHTMLTOPDF](http://code.google.com/p/wkhtmltopdf/)

By leveraging the power of the webkit engine through [QtWebKit module](http://doc.trolltech.com/4.4/qtwebkit.html), this thing is converting HTML with full CSS support to PDF the same way you "Save as PDF" from your browser

In this article, I'll show you the very first prototype I did of a possible WKHTMLTOPDF integration with our application.

Let's start by installing this nifty tool the easy way (tested on Ubuntu Hardy and Jaunty 64 bit):

`wget http://wkhtmltopdf.googlecode.com/files/wkhtmltopdf-0.8.3-static.tar.bz2  
tar -jxvf wkhtmltopdf-0.8.3-static.tar.bz2  
sudo aptitude install ia32-libs`

Next, you'll have to make a symbolic link pointing to WKHTMLTOPDF in /usr/local/bin.

`sudo ln -s /full_path/WKHTMLTOPDF /usr/local/bin/WKHTMLTOPDF`

Et voila, we are ready to go!

Here is a way to post an arbitrary HTML portion of our current document to the server and have it converted as a PDF on the fly. We will use the following workflow:

  1. Post the innerHTML to the server
  2. Write a temporary HTML file with the posted data (file:write_file)
  3. Convert this file to PDF using the command line WKHTMLTOPDF (os:cmd)
  4. Read and store the PDF file content to a variable (file:read_file)
  5. Delete the temporary HTML and PDF files (file:delete)
  6. Send back the final document to the client using the 'application/pdf' content type header

We will be using Mochiweb as our web server (You can follow our [tutorial](http://beebole.com/en/blog/erlang/tutorial-web-application-erlang/) about Mochiweb if you feel lost).

Just create priv/www/index.html and copy the following HTML in it :

<http://friendpaste.com/7Kvh0SWRMyCgTMMEOy4x2B>

and here is the Erlang server code which will handle the post request (myapp_web.erl):

<http://friendpaste.com/538mWzeOfBKxiE2uScDjT4>

No magic trick! Regarding the Javascript, I'm just filling an input text value with the innerHTML source and submit the form to the server.

The Erlang code is really straight forward. We defined a new case clause under the 'POST' part named 'pdf'.

In order to generate the temporary file names, I'm simply concatenating the current date time. The important part here is to set the response's content type to 'application/pdf'.

Now, we can test our page by connecting to http://127.0.0.1:8000/pdf and clicking the '>>>PDF' button (tested under Firefox).

I hope this was useful for you to start toying with that tool which is certainly going to replace their licensed versions counterpart
