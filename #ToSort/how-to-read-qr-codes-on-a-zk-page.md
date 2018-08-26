# How to Read QR Codes on a ZK Page

_Captured: 2018-03-15 at 16:15 from [dzone.com](https://dzone.com/articles/how-to-read-qr-codes-in-my-zk-page?edition=368200&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-03-15)_

Hey there my friend. Just received a call from the boss, they want our website to read [QR codes](https://en.wikipedia.org/wiki/QR_code) if the viewing device has a video access, then push the result to their business layer.

**What, like on a smartphone?**

Sure, but they also said something about webcams on laptops. Doesn't matter though, there's a MediaDevices[ API in HTML5](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices), so we just need to find a way to extract QR code data from that. Then the only thing left to do will be to push it to the server. Good thing is, we made their current application using the [ZK Framework](https://www.zkoss.org/).

**Wait a second! What's this ZK framework business again?**

Right… to keep it short, we use the ZK framework to build our dynamic web application based on the Java servlet spec. One of the basic ideas is that a ZK page is a [component tree](https://www.zkoss.org/wiki/ZK%20Developer's%20Reference/UI%20Composing/Component-based%20UI) much like an HTML page is a DOM tree. The framework itself put listeners and callbacks in and translates these components into HTML, JavaScript, and Ajax requests that can be accessed in a browser. Component types range from one-to-one representations of DOM elements (like a div or a radio button) to complex structures (like a grid with selection). Plus, since the component tree exists in Java, you can access business and persistence layers accordingly to fill in data or receive events accordingly. Read the [manual](https://www.zkoss.org/wiki/ZK_Developer%27s_Reference/UI_Composing/Component-based_UI) if you want to go deeper.

**That's nice but I already read the manual and there is no QR code reader component in ZK, so we can't use it.**

True, there is no component for this feature, but that won't stop us. If there's a library for it, we can integrate it. And let's be honest, between Java and JavaScript, there is a library for most common use-cases. See, since the client part of the ZK web application is based on HTML and JavaScript, we can plug a JS QR code reader library into our page.

**Can't we do it on the server-side with Java?**

We could, but that means sending a picture from the device to the server. I'd rather send the QR code content as a string after parsing for efficiency.

**Got it. But then we need a JavaScript QR reader library first.**

Good point! Fortunately, I found a lot of those using my favorite search engine. I chose one that supports the HTML 5 camera API and has a nice manual on their [git page](https://github.com/schmich/instascan). I'm going to plug it in the page and use their callbacks to interact with the ZK Framework.

![client to server process graph](https://dzone.com/storage/temp/8421032-zk-qr-sequence-no-shadow.png)

> _client to server process graph_

**Hum. That makes sense. So how do you go about doing this? We only need to push events to the server when the scanner triggers a callback, right?**

Yes! For all intents and purposes, I'm going to consider the scanner library as a black box. From my point of view, only two things matter in this integration. First, we need to initialize the scanner, then we need to receive callbacks by hooking into the scanner API. Let's do a step by step rundown.

## Phase 1: Throw it at the Wall and See What Sticks

We will start by grabbing the library and the example page from the library's git page. We just need to make sure that it works as intended outside our ZK application, then inside. I'll make a subfolder for phase one [here](https://github.com/zkoss-demo/zk-qrcode-integration-demo/tree/master/src/main/webapp/phase1) and we will put the [original demo page](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/webapp/phase1/originaldemo.html) and a [new zul page](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/webapp/phase1/zkintegration1.zul) inside.

**Zul page? What are you even talking about? **

That's just the ZK component syntax. I can write a component tree structured like an HTML page and the framework will build the actual page for me. I could create all the components in Java code, but it's just easier to read this way. The point is, we will make a zul page containing the same elements as the original demo page to make sure we can run this library inside a ZK page.

**Alright, looks like it's working. I got a popup asking me if I want to allow the website to access my Webcam.**

Of course, that's part of the HTML5 API. Ok, I can read a QR code and the result is displayed in the browser's console. Look at the initializing JavaScript:

We can register a callback whenever a scan is triggered. That's very good! Since we already have a callback available, we only need to send an event to the server whenever the callback is triggered. Let's start doing that in phase 2.

## Phase 2: Need More Events

**Alright, I will guess you already know how to do that?**

Yes. We have a handy tool available already. I will make a new zul page for phase 2 [here](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/webapp/phase2/zkintegration2.zul). Remember when I said ZK components can receive events from the client? We just use that to register our own unique event. Let's call it "onScan."

**Ten points for originality here…**

Well, it's not an existing default event in ZK and this name is easy to understand. So, I could register the event listener in Java but there is a shortcut for that in zul. I will use the div component as the main target. To make a listener, in this case, I will just write:

This way, whenever an "onScan" event is sent to the div, I will show its "content" data on the screen.

**Ok, but you also need to initialize the scanner, remember?**

That's correct. But we need to wait for the div to be initialized on the client side. Lucky for us, we can hook our code onto the client-side `onBind` listener available on the ZK component. It is invoked when the div is ready on the client side.

**Client-side listener?**

Oh right. Remember when I said that ZK components exist on the server side as a Java object? They also have a widget, a JavaScript "ghost" object on client-side which deals with everything happening in the browser and notifies the server-side component when appropriate. The zul language is used to control the Java side of things, but I can declare the client namespace to also add specific client-side attributes or behavior. I will assign it to the w: namespace, for Widget.

**Ok, Ok… So, you are registering a JavaScript listener which will be invoked when the div is ready in the browser.**

You have it there. And since the DOM elements will be ready by this point, we can just execute the `loadScanner` script to initialize our library. Next step is to actually send a value back to the server when the scanner finds a QR code. For that purpose, we will pass the widget (the JavaScript object) to the initialization script. Since we already have access to the widget, we can fire an event directly to the Component.

Remember the original callback firing results to the console? We are going to fire results to the div with the onScan listener instead. At first, it looked like this:

But since we have access to the widget Javascript object, we can fire an event directly to it's matching component on the Java server. We are going to put the same name as used in our listener, the data to transfer, and the "toServer" option.

**So, to recap, after initialization… the **JavaScript** QR code library triggers a callback in JavaScript, and in this callback, we fire an event from the client to the server. And then?**

Then in the server-side listener, we just display the result using this part:

**Ok, ok… You made a page that displays a QR value, good grief. How's that useful? We are trying to add a feature to our own platform, not make POC pages.**

But that's just a step on the road to the good stuff because we can now get into phase 3.

## Phase 3 - Getting Down to Business

Let's see now. Are we integrating with MVVM or MVC? That will depend on which of these patterns is used in our main application. Doesn't matter though, if it works with one, it should also work with the other. I have a personal preference for MVVM, but it doesn't hurt to be ready to use either. I will make a folder [here](https://github.com/zkoss-demo/zk-qrcode-integration-demo/tree/master/src/main/webapp/phase3) for the phase 3 pages.

**MVC? MVVM?**

MVC and MVVM are design patterns. Choose one for your project and stick to it. Also, you can read up [here](https://www.zkoss.org/wiki/ZK_Developer's_Reference/Overture/Technology_Guidelines) if you have time.

**Alright, so you said it doesn't matter?**

Well, kind of. It matters in the sense that the implementation will be slightly different depending on which pattern is used. But it's not a big deal because the general idea will be the same.

Here's the thing: In MVC (Model - View - Controller), the controller pilots the view directly. So, in our [controller class](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/java/local/example/zk_integration_qr/mvc/QrIntegrationComposer.java), we can just write an event listener and declare it on our QR reader Div. I'll just call the div "myScanner." Inside my listener, I will just add scanned entries to a list, which I can display using another component.

**Seems reasonable, and how would that be different in MVVM?**

Well, in MVVM (Model - View - View Model), the View Model and the View are not tied together. They just send events to each other. So, I will start with the view - [my zul file](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/webapp/phase3/zkintegration3mvvm.zul) - and declare a listener for the `onScan` event. Then, I will forward this event to the View Model using a command.

**Don't you need to do something on the View Model when it receives this command?**

I'm getting there. In the [View Model](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/java/local/example/zk_integration_qr/mvvm/QrIntegrationViewModel.java), I will just declare my `handleScan` command, and annotate it with `@Command`.

**And the myScannedEntries List?**

Same as in the MVC case. I just store the value in a list, which I can display with another component. Let's use a `listbox` for an example.

**Well… ok, it works. But that's a lot of stuff to copy every time we need to use that QR feature.**

True, let's use a ZK component instead, that will simplify the code a lot.

## Phase 4 - Got Some Code? Let's Package it!

**What the… I swear you are messing up with me. You told me there is no component for that!**

I know what I said. There isn't a component for that yet. Then let's just make one! We only have to package it once, then we can use a simple syntax in every page. The documentation for component creation is [here](https://www.zkoss.org/wiki/ZK_Component_Development_Essentials), but I'm going to show you the steps we need for this one.

**Go on…**

Well, first we need a resource folder accessible to the server in which we will put our component file. So, let's make a [src/main/resources/web/js/codereader/ folder](https://github.com/zkoss-demo/zk-qrcode-integration-demo/tree/master/src/main/resources/web/js/codereader) in our project. Could be in a separate jar though, if we plan on deploying it to multiple applications.

This folder can be accessed by ZK, so we only need to tell it that there is something here to compile. First order of business, let's make a [zk.wpd](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/resources/web/js/codereader/zk.wpd) file inside this folder. In this wpd file, we will declare all of the resources used by the custom component. Let's call it "codereader."

The package name and the widget name will be used when targeting our custom widget on teh client-side. With this config, the widget will be called "codereader.Codereader." The script tag indicates to ZK that we need it to bundle the instascan.min.js file in the resources for our codereader. That means the content of this file will automatically be loaded by the client if we declare a `codereader` component.

Next step, under the same folder we will create the actual widget class. It needs to have the same name as declared in zk.wpd, so it will be [/src/main/resources/web/js/codereader/Codereader.js](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/resources/web/js/codereader/Codereader.js). This one will contain the custom client-side logic.

**So, what. Are you going to re-implement the client's entire client widget functionality set manually? I'd like to go home before next month…**

Yeah, no. Remember that our component in the last phase was just a jury-rigged div? Well, let's do that again! Create a div, and just add our initialization code in the `bind_` callback. We just need to declare the `loadScanner` function above, but that's basically it. The rest of the client widget functionalities will be inherited from the original Div class.

**Alright… but that can't be that easy. Our div was hosting a video element! Where is it now?**

Good point. We will need to add a mold to our component. It needs to be created with the same name, but in the /mold folder. In this case: [/src/main/resources/web/js/codereader/mold/codereader.js](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/resources/web/js/codereader/mold/codereader.js). The mold is the DOM tree structure of the component. Since we are based on a div, we will need to open and close with one. But inside, we can automatically create our <video> node. I will give it an id="'+ uuid +'-preview", which will make it easy to target from the main widget.

With that id based on the unique id of the codereader widget, I will find it easily with `document.getElementById(wgt.uuid+'-preview')` during widget initialization.

**So, that covers the client side. What about the server side?**

Well, same as before. We are going to [extend a div](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/java/local/example/zul/Codereader.java) to add our customization. I'll keep it short, because we only need to listen to "onScan" events inbound on this extended div, then fire our own custom event. I've even made my own [event class](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/java/local/example/ui/event/ScanEvent.java) to extract the scan value for me from the original event.

**Ok. Are you done?**

Almost. The only thing left for us to do is to let ZK know that we want to use this component in zul. To that end, we need to add it to the zul language using a lang-addon file.

In [zk.xml](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/webapp/WEB-INF/zk.xml), we will declare a lang-addon file like this:

Then, we can create that very same [lang-addon.xml](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/webapp/WEB-INF/lang-addon.xml) file and declare our component:

**I see. Our custom server-side component class, our custom client-side widget class, the mold, the extra CSS if we want to add any. Everything is here, right?**

Sure! Let's make a folder for phase 4 [here](https://github.com/zkoss-demo/zk-qrcode-integration-demo/tree/master/src/main/webapp/phase4), and now have a look and my [zul page](https://github.com/zkoss-demo/zk-qrcode-integration-demo/blob/master/src/main/webapp/phase4/componentintegration.zul):

**Nice!**

Nice! And it also works in MVC and MVVM.

I made a [repository](https://github.com/zkoss-demo/zk-qrcode-integration-demo/tree/master/src/main) to store everything we just talked about. Have a look, or just download and run the project if you want to see how it works.
