# Top 5 Free Tools for Rapid Web App Development

_Captured: 2017-06-22 at 03:04 from [dzone.com](https://dzone.com/articles/top-5-free-tools-for-rapid-web-app-development?edition=305124&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-21)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

Starting up has never been easier, but it's easy to forget yourself and start shaving a yak instead of getting things done. I've been there so many times, I decided to settle for a toolkit that allows me to start (and fail) fast, without spending a single cent, with a limited amount of time. The 5 tools I want to present now are the absolute minimum with which I tend to start every new project.

The list contains mostly the applications that are helpful in setting up landing pages and very limited MVPs. You won't find here backend solutions or languages that will help you build an application with killer performance. Usually the solution there is to go with whatever is the cheapest, but the end-user does not see the end result anyway.

## ReactJS for Setting Up Your Source Code

In 2017, building for the Web means writing a lot of JavaScript. Sure, you can do your project in vanilla JS, but if you want to move fast, you need to rely on a framework. And among the incredible noise of numerous Javascript frameworks, libraries, MVC pattern implementations, template processors, and other inventions, there is one choice that you can't go wrong with: [React](https://facebook.github.io/react/) from the Facebook team. The main goal was to build a framework that will be fast and light for the browser, and the developers achieved that by implementing a virtual DOM so that the actual changes in the site happen way less often. The model turned out to be versatile enough to be used for [React Native](https://facebook.github.io/react-native), allowing you to write the same JS code for iOS and Android apps. This is a topic for another post though, so let's just take a look what makes React so powerful.

First of all, React is surprisingly easy to learn. This is mainly thanks to the perfect documentation with lots of examples, but also to the simplicity of the project itself. If you had been working with AngularJS, you may be startled by how limited React seems in comparison. Fear not, this limitation actually allows you to focus on the behavior of your app, instead of figuring out the order of rendering and the dependency injection of components. Another thing is tooling built around React. Starting with phenomenal `[create-react-app](https://github.com/facebookincubator/create-react-app)` (official project template and configuration), through multiple tools for different tasks, it quickly turns out that most of the problems for web app developers have already been solved and all one has to do is `yarn add` (or `npm install`). All of that means is that creating a new application with React is incredibly fast.

## Semantic UI for Making it Look Stunning

Creating a compelling design for your website used to be a dire chore back in the day. As a developer, I wanted to concentrate on how my software worked, not on such dull tasks like ensuring that everything is displayed as expected on different browsers. Things changed a lot when Twitter released [Bootstrap](http://getbootstrap.com) and other CSS systems started emerging. I was finally able to create an interface that looks good, without spending too much time on it. And none of these CSS systems feels as complete as [Semantic UI](https://semantic-ui.com/).

The main difference between Semantic UI and other similar solutions is that Semantic UI's main tenet is that your website should be built in hierarchical structures of reusable components. This led to a library of over 50 components, which not only provide basic solutions, like typography or forms but also a lot of widgets used is modern web apps, like feeds, user cards, etc. The default theme is clean and pleasant to see, and theming is incredibly easy - there are even demos that show you how to make your site look like Twitter or GitHub!

The final thing that makes Semantic UI my choice for app development is how well-supported it is. The default way to use it is to install the source files with 'npm,' but the integrations provided (and supported!) mean development time is reduced to a minimum. Of course, there is also React integration, and I haven't yet met an implementation I would need that wouldn't be provided by either of these frameworks.

## Netlify to Host Your Site

Google's acquisition of divbase.io left a hole in my heart. The promising startup provided exactly what I needed, free of charge as long as you do not exceed liberal limits and do not need more advanced features. It was a perfect mix for anyone trying to quickly wrap up an MVP for a new project. Once Divbase was shut down (as far as I understand it was incorporated into Firebase as Firebase Hosting), I tried a couple of similar solutions, finally settling on cloud storage solutions like Amazon S3 or Google Cloud Storage. Until I learned about [Netlify](https://www.netlify.com/).

Netlify basically allows you to host your site (or more like web application). Its free version offers everything that you need to set up an initial version, including your own custom domains and SSL certificates from Let's Encrypt, something I never managed to set up properly on cloud storage hosting. And with its nice CLI, you can set up your site is a matter of minutes.

Even though the free option should be enough for many solutions, the basic plan costs a measly 9$/month and offers features that will make your development even easier, like form handling and proxy rules (no more setting up an API just for handling a single call!). This is great for the first milestone of your application.

## Google Analytics for Capturing What's Happening

[Google Analytics](https://analytics.google.com/) is the standard solution for capturing basic analytics about your web applications. And it's not difficult to understand why it is. It's incredibly easy to set up and provides multiple features and analyses out of the box. With GA on board, you should be able to answer most of the questions about your users.

One thing that makes GA awesome is the support. If you don't have much experience in digital marketing (like myself), the resources for learning provided by Google are priceless. There are video courses for both beginners and advanced users, and a huge knowledge database for those that need more.

Google Analytics is the first choice, but you may need a slightly more sophisticated tool, and [Mixpanel](https://mixpanel.com/) is probably the solution I would look to first. Compared with other services, it offers a generous free option, perfect if you are starting up and don't want to spend money on things that you might not really need.

## Mailgun for Sending and Receiving Emails

No matter what kind of application you are building, if you are going to have customers, you'll need some email service to communicate with them. A good hosted choice seems to be whatever email provided by your domain operator, but these usually have a hideous user interface, and, generally, lack in possibilities. You can go with [Google GSuite](https://gsuite.google.com/) (or Microsoft Office 365), but these are more oriented toward business users.

[Mailgun](https://www.mailgun.com/) turned out to be surprisingly convenient to use. The pricing plan makes your first 10000 emails each month free, so scaling up is very cheap. At the same time, it is very developer oriented, so it's API is super simple to use. Moreover, they provide SDKs for popular environments, so that you don't even have to write a special REST layer.

The killer feature is the configuration of the email accounts. This means you don't have to set up a full blown email server in order to receive emails from you customers; you can forward it to the email of your choice - even your Gmail account. It doesn't even have to be another email address - you can wrap your email into JSON and call it with an external REST service (or serverless endpoint). One feature I might be missing though is better email marketing management, or at least I haven't found it yet.

This concludes the list. I know it's pretty limited, but it is enough to build your landing page or even MVP in a matter of hours and have it available for your customers.

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).
