# When not to use a JavaScript framework

_Captured: 2017-08-08 at 20:15 from [opensource.com](https://opensource.com/article/17/6/javascript-frameworks?ref=quuu&utm_content=buffera9812&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_


# When not to use a JavaScript framework

## Helpful hints on where frameworks make sense, and where they don't.

![](https://opensource.com/sites/default/files/styles/byline_thumbnail/public/pictures/todprofilepic-square-sm.png?itok=xi3n7TEm) 26 Jun 2017 [Tod Hansmann](/users/todpunk) [Feed](/user/143256/feed)

25

[up](/article/17/6/javascript-frameworks?ref=quuu&utm_content=buffera9812&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer&rate=bCUbhFH6oToM21XH0FfH_b-tudtBieBL9Qvo2Yf3bu4)

3 comments

![When not to use a JavaScript framework](https://opensource.com/sites/default/files/styles/image-full-size/public/images/business/BUSINESS_barnraising_2.png?itok=G6JfjV77)

Image by : 

opensource.com

As the internet has evolved, web development has grown well beyond its intended abilities—for good and bad. To smooth over the rougher edges, web developers have invented a plethora of frameworks, both [small](http://monkberry.js.org/) and [not so small](https://angular.io/). This has been good for developers, because browser fragmentation and standards problems abound, especially for those who want new features in APIs and more unified syntax for those features. Plus, for the most part the frameworks have been open source, which is great for everyone.

Now, seeing that those rough edges have been worn down by time and aren't as sharp as they once were, we should probably reduce our use of some of the frameworks we created. In other ways, we simply need to consider the cost of using a framework for the given task.

Programming and development

  * [New Python content](https://opensource.com/tags/python?src=programming_resource_menu1)
  * [Our latest JavaScript articles](https://opensource.com/tags/javascript?src=programming_resource_menu2)
  * [Recent Perl posts](https://opensource.com/tags/perl?src=programming_resource_menu3)
  * [Red Hat Developers Blog](https://developers.redhat.com/?intcmp=7016000000127cYAAQ&src=programming_resource_menu4)

## Things we can do ourselves

Consider the humble HTTP request, once a good 50-line function for a simple **GET** that worked both in Firefox and Internet Explorer. For example, here is a simple function that does a **POST**; we used it in production in [Phone Janitor](https://phonejanitor.com/) for more than a year as our main [React](https://facebook.github.io/react/) data pump:

    
    
    
    
    function postMe(name, data, callback, onError) {  
    
        var request = new XMLHttpRequest();  
    
        request.onreadystatechange = function() {  
    
            if (request.readyState != 4 || request.status != 200) { return; }  
    
            var body = JSON.parse(request.responseText);  
    
            if (body.error) {  
    
                onError(body.error);  
    
            }  
    
            else {  
    
                callback.(body);  
    
            }  
    
        };  
    
        request.open("POST", '/api/' + name, true);  
    
        request.setRequestHeader("Content-type", "application/json");  
    
        request.send(JSON.stringify(data));  
    
    }

This framework-free code could easily be rewritten to work with **[Promises]( https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)**, be adaptable for request types, or support any number of features that might be critical to your application. Is it well-engineered? Maybe not. Is it robust? It was for our needs at the time. The takeaway is less about what it is or isn't, and more about why I would use anything else.

If I don't want to write my own HTTP request engine, there is a cornucopia of options. They all come with a cost, though. How big are they? How can I include them in my code, and how does it affect my workflow? What other unnecessary things are they doing that waste time in execution? If I spent an hour (which is about what we spent on the code and testing) implementing this function to meet all my needs, would that save a lot of time compared to what it would take to integrate a library to do the same thing? Each of us will have different answers.

## All things to all people

We consume services that try to be many things for a variety of use cases. This is really the crux of the issue. It is a good thing to unify APIs for the community's benefit, because some things are nuanced and hard to do alone. jQuery was invented because browsers did things wildly differently, and the JavaScript API didn't have much to it. There was a time, though, that every web dev included jQuery just so they could select document object module (DOM) elements for simple innerHTML, and it made a noticeable impact on page-load times. Consider that use case now:

    
    
    
    
    // Author's note, this is mostly for example, don't manipulate DOM unless you know what that means for your app  
    
      
    
    var el1 = document.getElementById(id_Name);  
    
    var el2 = document.getElementsByClass(class_Name); // returns array  
    
    var el3 = document.querySelector("div.user-panel.main input[name='login']");  
    
      
    
    // Want it in a jquery style function name?  
    
      
    
    var $ = document.querySelector; // Or get fancier if you wish  
    
    var el4 = $("div.user-panel.main input[name='login']");

We still include jQuery for this in a lot of places  (e.g., the average WordPress theme). Don't take my word for it; feel free to look and see where it's included or not. There isn't much we can't do these days without it.

## Even if we use frameworks

This is not just a matter of how and when we use frameworks, though; it's also about how we approach features and add-ons. For instance, consider Google Visualization integration into the Angular framework. At MobilSense, we rely heavily on charts for reporting to management teams—but we also use Angular 1.5. So how do we integrate updating functionality into our app's charts?

Our options were using **[angular-google-chart](https://github.com/angular-google-chart/angular-google-chart)** or developing our own solution. Although **angular-google-chart** is a fantastic library—I have used it elsewhere and I appreciate the author supporting his project for free—we decided to do our own for some now obvious reasons. Here's how they stacked up:

Angular-Google-Charts Our own

20 src files

1 src file

~40 lines of code per file on average

81 lines of code including comments (there aren’t many, sadly)

npm package includes all of angular

Not a package, doesn’t depend on anything, it’s just another directive

Our own solution does not handle all the cases the library does. We don't need those cases, and if we did, we could probably add them pretty easily and in a way that is portable to our workflows and other frameworks. This is the type of tradeoff we each need to decide based on our own specific needs. There is no shame in either choice.

## When we should and shouldn't use frameworks

I strongly advocate for knowing the purpose in coding a given tool. If our goal is a quickly cobbled-together thing that exists temporarily, engineering it well probably doesn't matter. If we're looking for longevity, I think using framework tools is something we need to weigh more heavily. A framework is hard to transition away from, especially if we add in libraries that further tie us into that framework.

If it will take just a day or two to write your own solution, I would lean toward that. If it will take a week or more, the considerations may change.

Another good reason to write your own would be if it would be costly to couple yourself to a framework that may not be around for the life of your project. However, if it is a really complicated thing, such as integrating PDF support, you probably don't want to consider writing your own, as in that way lies madness.

As with any type of software engineering, consider your work like construction. If you're building a doghouse, whatever you do is probably fine. If you're building a skyscraper, you've got to do more planning. Where do we draw the line between them? The role of frameworks is the same as the role of the materials and styles of construction you are building. Does it fit the environment, and can we get replacement materials later on when we need them? Although your decisions are your own, I hope this information and these examples will help guide you.

_Tod Hansmann will give a talk called [JavaScript: What Not to Use Frameworks For](https://www.openwest.org/custom/description.php?id=20) at [OpenWest](https://www.openwest.org) in Salt Lake City, which will be held July 12-15, 2017._

