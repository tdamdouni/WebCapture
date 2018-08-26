# domcurl: curl + JavaScript

_Captured: 2018-03-17 at 18:05 from [dzone.com](https://dzone.com/articles/domcurl-curl-javascript?edition=367206&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-17)_

[Read this guide](https://dzone.com/go?i=266422&u=https%3A%2F%2Fwww.appian.com%2Fresources%2Fresource%2Fguide-robotic-process-automation-rpa%2F%3Futm_source%3Ddzone%26utm_medium%3Dcontextual-ads%26utm_campaign%3Drpa%26utm_content%3Dlookbook-guide-rpa) to learn everything you need to know about RPA, and how it can help you manage and automate your processes.

For a long time, I've been thinking about what the future of the web looks like when we go past what we know as the traditional web browser. I called this [The Headless Web ](https://paul.kinlan.me/the-headless-web/)and I wanted to answer, "What if everything was powered by 'The Web,' but you never saw a browser?" Specifically, I believe that if you have access to a full browser, but no visible "chrome," then there is a huge opportunity for a new set of services.

> Using the browser as a service is an incredible opportunity. It allows us to take the declarative HTML and combine it with the developer defined procedural execution of JavaScript and run deep analysis on the content.
> 
> …
> 
> Running a browser on the server will allow us to more easily build services which parse data that is generated dynamically, it will allow us to more easily run our own logic against the logic in a page (form fill as an example) and I believe that it will open up the ability to more effectively run actions against data embedded on the page.

It's taken a while, but I think we are getting there.

I'm enamored by [Puppeteer](https://developers.google.com/web/tools/puppeteer/). Puppeteer is a JavaScript library that sits on top of the Chrome Dev Tools protocol and it allows you to automate and script the Chrome browser.

My day-to-day work involves a lot of debugging web servers and ensuring. Like many developers, I use `curl` to make requests to a web server and check the response. It's an amazing utility, however, in today's world, many developers are building sites that are built using a lot of JavaScript and this makes it impossible to inspect the complete response.

I decided to create a cUrl-like utility for fetching a resource and running the JavaScript on the page called `[domcurl`](https://www.npmjs.com/package/domcurl).

`domcurl` is a small Node.js application that uses Puppeteer and can be installed by issuing the following command: `npm i domcurl`. Like the `curl` command, you can issue a simple `domcurl [url]` to fetch the resource and run the JS on the page.

It doesn't replicate all of `curl`, but it is quite featureful with the following features.

  * Specify a URL to fetch, i.e, `domcurl [url]`
  * Inspect the response headers with `-v`. i.e, `domcurl -v [url]`
  * Set cookies with `-b` i.e, `domcurl [url] -b "test=hello; Domain=airhorner.com; HttpOnly;" -b `
  * `"hello=world; Domain=airhorner.com; HttpOnly;"`
  * Add custom headers using the `-H` argument.
  * Manually set the STDOUT with `-o` and STDERR with `\--stderr`

I'm finding it quite useful even though it can't stream the results like `curl` can because it has to wait for the CSS and JS to be downloaded and executed.

I also took the liberty to add a couple of extra features that are specific to JavaScript and Chrome.

  * Output a Chrome Dev Tools trace file (including screenshots.) `domcurl --url[https://example.com](https://example.com/) \--trace test.json`
  * Include it as a JavaScript module if you have the need to integrate it into any of your existing applications.
    
    
    const {domcurl} = require('domcurl');

While this tool is more of a demo than a full service, I think [The Headless Web](https://paul.kinlan.me/the-headless-web/) is maturing and tools like Puppeteer and others are going to help us realize the continued power of the web. We just need to build for it.

[Get the senior executive's handbook](https://dzone.com/go?i=266423&u=https%3A%2F%2Fwww.appian.com%2Fresources%2Fresource%2Fguide-digital-transformation%2F%3Futm_source%3Ddzone%26utm_medium%3Dcontextual-ads%26utm_campaign%3Ddigital-transformation%26utm_content%3Dtransformers-almanac) of important trends, tips, and strategies to compete and win in the digital economy.
