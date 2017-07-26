# Defining the Surface Area of the Facebook API

_Captured: 2017-05-07 at 19:18 from [dzone.com](https://dzone.com/articles/defining-the-surface-area-of-the-facebook-api)_

![](http://kinlane-productions.s3.amazonaws.com/api_evangelist_site/blog/the_facebook_api_index_screenshot.png)

I learn a lot by studying APIs. One of the ways I get to know what an API does is by creating an OpenAPI for the API, which helps define all of the paths available for an API--helping me understand what is possible. After defining the API requests that are possible, ensuring there are simple descriptions for each path, I also like to make sure all the data that is being passed back and forth via an API is also defined in the OpenAPI--giving me a good snapshot of what data is stored behind an API.

[In my current Facebook API definition, there is a total of 271 paths, with 90 objects defined using 654 data points](http://facebook.stack.network/). The machine-readable OpenAPI definition tells me what data is stored and transmitted, and what actions I can take involving these items. The Facebook API definition isn't complete, but it does provide me with a nice view of the Facebook Graph API landscape, and since the project is hosted on Github, anyone can help me continue adding to and expanding on the definition, as well as the documentation and other tools I'm building on top of the definition.

There are three parts to my research: 1) to define Facebook's API operation from a technical and business perspective, 2) to understand which of my bits Facebook tracks about me and my business(es), and how I can take more control over these bits with the Facebook API, and 3) to understand how Facebook can be orchestrated and manipulated as part of a social engineering toolbox. Facebook isn't on my list of top places I hang out online, but I grasp its magnitude, and importance to my business and my career, and our democracy--so I work to understand WTF is going on with it.

I currently post stories to Facebook from my content management system. When I blog something, if I want it on Facebook, I can schedule it, and my system posts the story using the Facebook API. I'm looking to expand this to my photos, video, and the other bits I make available online. Profiling an API like this helps me understand the wider Facebook API landscape, better understanding what is possible, but it also helps me get my personal and professional world in order when it comes to one of the most important social networks out there right now.
