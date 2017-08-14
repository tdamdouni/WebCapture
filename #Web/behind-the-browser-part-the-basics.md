# Behind the Browser, Part 1: The Basics

_Captured: 2017-08-09 at 13:54 from [dzone.com](https://dzone.com/articles/behind-browser-basicspart-1?edition=313402&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=java%202017-08-09)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

The browser. It's a great idea which helps people to access various web applications in one place. Browsers are the most widely used software applications for retrieving, presenting, and traversing information resources on the World Wide Web identified by a URI/URL.

![](https://cdn-images-1.medium.com/max/1600/1*7Z5Yr1rxyZsevxYxWSgYQA.png)

> _Web Browser Components (Credits -- https://www.html5rocks.com)_

> As a web developer, learning about browsers' internal operations and their architecture helps you to make better decisions during development and to discover the best and worst practices. 

## Browser Functionality

Browsers operate to mainly display the web resources (HTML, XML, CSS, JS, JSON, PDF, etc.) you choose. In general, a browser requests this information from the server and the server responds to the browser window. The resource location is specified by the user using a URI (Uniform Resource Identifier).

> [W3C ](https://www.w3.org/)maintains the specification on how browsers should interpret and display the web page (HTML) and this has helped to solve compatibility issues between browsers that once existed. 

## Browser Components

Browsers have a set of components with a particular work flow. Let's have a look at each component in detail, one by one.

### User Interface

The address bar is a good example. It interfaces with the user to insert a URI and interacts with various components to render a web page.

There are plenty of user interfaces for various needs, like Back and Forward Buttons, Bookmarks, Reload, and Stop and Home Buttons, which you see below.

![](https://cdn-images-1.medium.com/max/1600/1*7LMdXYEbP2AK0OVxnSyAAQ.png)

> _Address Bar in Chrome_

The interface layer communicates with the data layer to retrieve data. The interface layer also communicates with the UI Backend to draw widgets as per requests by the HTTP Response body (our HTML source code). The browser engine communicates between the UI and the rendering/layout engine.

> Modern browsers now have interfaces (Dev Tools) which help you see the client data like Cookies, Local Storage, Session Storage, IndexDB, etc. 

### Browser Engine

It's a bridge between the user interface and the rendering engine. It provides methods to initiate the loading of a URL and other actions like reload, back, and forward.

### Layout/Rendering Engine

It's able to render the content of a given URL in the browser screen and interprets the HTML, XML, and CSS. It is single threaded. By default, it displays data according to your specified content type (MIME). For example: HTML, Images, XML, CSS, JSON, PDF, etc.

A key operation of the rendering engine is the HTML Parser. Each browser uses various engines. Chrome and Opera use Blink, Firefox uses Gecko, IE Edge uses EdgeHTML, Internet Explorer uses Trident, and Safari uses WebKit.

**_What is the Flow?_**

  1. Parsing an HTML document with the HTML Parser converts elements to Node and creates a Content Tree.

  2. Parsing styles for code/documents with the CSS Parser and creates a Render Tree.

  3. The Render Tree goes through the Layout Process. An element's node gets position coordinates.

  4. The Render Tree will be traversed and each node will be painted using the UI Backend Layer.

**What is a Dirty bit system?**

  1. This will be used for small changes which don't require a full layout change.

  2. It uses incremental layout asynchronously.

  3. Its two flags are dirty and its children are dirty.

### **A Few Other Stages**

Width calculation - It's calculated using the container width attribute/style attribute.

Line Breaking - While a user is scrolling, the layout parent creates the extra renderers and calls the layout on them.

  1. A render tree is traversed and the renderer's "paint()" method is called.

  2. The paint method is called to display content on the screen.

  3. It uses the UI infrastructure component.

  4. Painting order (background color, background image, border, children, outline).

## Network

  1. Networking handles all aspects of Internet communication and handles URLs to use with HTTP, FTP.

  2. Implements a cache of retrieved documents to minimize network traffic.

## JavaScript Interpreter -- Scripting Engines

JavaScript Interpreter executes the JS code and sends the results to the rendering engine.

Each browser uses various scripting engines, for example, Chrome uses [V8](https://en.wikipedia.org/wiki/V8_%28JavaScript_engine%29), Firefox uses [Spider Monkey](https://en.wikipedia.org/wiki/SpiderMonkey), IE Edge uses [Chakra (JavaScript Engine)](https://en.wikipedia.org/wiki/Chakra_%28JavaScript_engine%29), Internet Explorer uses [Chakra (JScript Engine)](https://en.wikipedia.org/wiki/Chakra_%28JScript_engine%29), Safari uses [Nitro (JavaScript Core)](https://en.wikipedia.org/wiki/WebKit#JavaScriptCore)

## UI Backend

Backend helps to draw widgets like a select box, an input box, a check box, etc.

## Data Persistence

This layer is persistent which helps the browser to store data (like Cookies, Local Storage, Session Storage, IndexedDB, WebSQL, and FileSystem) locally.

## Do All Modern Browsers Use the Same Engine?

No. Each Browser Development Team developed various Rendering and Scripting Engines. Below are the Layout and Scripting engines which are used by modern browsers.

**Browser Name**
**Layout and Rendering Engine**
**Scripting Engine**

Chrome

Blink (C++)

V8 (C++)

Mozilla Firefox

Gecko (C++)

SpiderMonkey (C/C++)

IE Edge

EdgeHTML (C++)

Chakra JavaScript engine (C++)

IE Edge

EdgeHTML (C++)

Chakra JavaScript engine (C++)

Opera

Blink (C++)

V8 (C++)

Internet Explorer

Trident (C++)

Chakra JScript engine (C++)

Apple Safari
WebKit (C++)
JavaScript Core (Nitro)

Yes. You are done and you are in the last lines of this article but this is not the end of this story and there are few more parts coming soon. Stay tuned!

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

Opinions expressed by DZone contributors are their own.
