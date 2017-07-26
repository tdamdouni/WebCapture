# Separate Content from Functionality and Design

_Captured: 2015-12-16 at 13:12 from [www.practicalecommerce.com](http://www.practicalecommerce.com/articles/292-Separate-Content-from-Functionality-and-Design)_

A website can be broken down into three main development parts: content, design and functionality. To optimize a website for search engines, it's important for developers to separate content, which is of interest to search engines, from design and functionality, which are not.

### Content

Content is the information a web page contains, usually in the form of the text and links, and is available to visitors. This information is at the heart of why people visit a web page and is what developers want the search engines to recognize. Content for a web page belongs in the actual HTML document, and should be the only thing in that HTML document. Developing the HTML document for a web page should center on:

  * keyword and key-phrase placement, 
  * content placement within the code, and
  * accessibility and standards compliance.

### Design

Once you have created the content for a web page and put it into clean HTML document, you can move on to design and functionality. To design a web page, you should use cascading style sheets. The reason for using CSS is:

  * it allows for easy design changes, 
  * you can define visual formatting for different devices such as web browsers and mobile phones; and
  * it does not compete, for search engine purposes, with the content because you're not using HTML code for the design.

### Functionality

For functionality of your website, use JavaScript. All JavaScript should go into an external file (.js) and not embedded within HTML. This is similar to external CSS files: You don't want to bloat your HTML and therefore confuse the search engines as to what is legitimate content and what is programming code.

Next month, I'll address ideas for keeping CSS and JavaScript external to your HTML. This will include a discussion of JavaScript event handlers and challenges involved with targeting HTML elements.
