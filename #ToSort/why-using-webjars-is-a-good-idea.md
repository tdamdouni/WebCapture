# Why Using WebJars Is a Good Idea!

_Captured: 2018-01-18 at 15:13 from [dzone.com](https://dzone.com/articles/why-using-webjars-is-a-good-idea?edition=355097&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-01-18)_

[Get the senior executive's handbook](https://dzone.com/go?i=266423&u=https%3A%2F%2Fwww.appian.com%2Fresources%2Fresource%2Fguide-digital-transformation%2F%3Futm_source%3Ddzone%26utm_medium%3Dcontextual-ads%26utm_campaign%3Ddigital-transformation%26utm_content%3Dtransformers-almanac) of important trends, tips, and strategies to compete and win in the digital economy.

### 1\. Assessment

Since I started working on web applications, I noticed that we often tend to manage our web dependencies like this:

  1. Find a great and reliable library (either JS or CSS) like jQuery, Bootstrap, AngularJS, or even some great directives for AngularJS found on GitHub.

  2. Copy and paste it to your application in a completely subjective directory (resources, web-resources, CSS, etc.) and hope that your fellow project members will use it correctly (and not copy/paste it elsewhere in the project).

  3. Use it in your templates, either HTML or with your JS Framework.

Yes, most of the time, that's it. **But how can one member of your team easily be aware of the JS framework version that you use? How can one update it? Will it be easy? How can you be sure that the code copied in your project has not been modified?**

As far as I know, it will often be a painful, long, and hard process.

That's why, for a personal project, I searched for a better and a new way to manage my web dependencies: that's where I found WebJars.

### 2\. What Are WebJars?

WebJars are client-side web libraries packaged into JAR (Java Archive) files. Many of you have used CDN or even Bower/NPM to load web dependencies, but there is another way (and a nice one).

With WebJars, you can explicitly and easily manage web dependencies in your applications, your build tools will be aware of your web libraries versions, and everything is available in [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Corg.webjars).

For a further and complete reference, go to [webjars.org](https://www.webjars.org/).

### 3\. How Does it Work?

It's simple. Using WebJars is as easy as using your favorite build tool (I hope Gradle) to add a dependency to your project.

Let's say we would like to build a web application using the classic Bootstrap-AngularJS combination. Simply add these lines to your build.gradle:
    
    
    compile group: 'org.webjars', name: 'angularjs', version: '1.6.6'
    
    
    compile group: 'org.webjars', name: 'bootstrap', version: '3.3.7-1'
    
    
    compile group: 'org.webjars', name: 'angular-ui-bootstrap', version: '2.2.0'

Now, all AngularJS and Bootstrap libraries are available within your application using the following links:
    
    
    <script type="text/javascript" src="webjars/bootstrap/3.3.7-1/js/bootstrap.min.js"></script>
    
    
    <script type="text/javascript" src="webjars/angularjs/1.6.6/angular.min.js"></script>
    
    
    <script type="text/javascript" src="webjars/angularjs/1.6.6/angular-resource.min.js"></script>
    
    
    <script type="text/javascript" src="webjars/angular-ui-bootstrap/2.2.0/ui-bootstrap-tpls.min.js"></script>

From now on, all your web dependencies are packaged in a common and standard way, available for all, and easily manageable.

[Read this guide](https://dzone.com/go?i=266422&u=https%3A%2F%2Fwww.appian.com%2Fresources%2Fresource%2Fguide-robotic-process-automation-rpa%2F%3Futm_source%3Ddzone%26utm_medium%3Dcontextual-ads%26utm_campaign%3Drpa%26utm_content%3Dlookbook-guide-rpa) to learn everything you need to know about RPA, and how it can help you manage and automate your processes.

Opinions expressed by DZone contributors are their own.
