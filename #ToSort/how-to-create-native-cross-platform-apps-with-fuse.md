# How To Create Native Cross-Platform Apps With Fuse

_Captured: 2017-05-12 at 00:25 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/05/fuse-native-cross-platform-apps/)_

  * [0 Comments](https://www.smashingmagazine.com/2017/05/fuse-native-cross-platform-apps/)

Today, too many websites are still inaccessible. In our new book _Inclusive Design Patterns_, we explore how to craft **flexible front-end design patterns** and make **future-proof and accessible interfaces without extra effort**. Hardcover, 312 pages. [Get the book now!](https://shop.smashingmagazine.com/products/inclusive-design-patterns?utm_source=magazine&utm_campaign=inclusive-design-patterns&utm_medium=html-ad-content-1)

Fuse is a toolkit for creating apps that run on both iOS and Android devices. It enables you to create apps using UX Markup, an XML-based language. But unlike the components in [React Native](https://facebook.github.io/react-native/) and [NativeScript](https://www.nativescript.org/), Fuse is not only used to describe the UI and layout; you can also use it to add effects and animation.

Styles are described by adding attributes such as `Color` and `Margin` to the various elements. Business logic is written using JavaScript. Later on, we'll see how all of these components are combined to build a truly native app.

In this article, you will learn what Fuse is all about. We'll see how it works and how it compares to other platforms such as React Native and NativeScript. In the second half of the article, you will create your first Fuse app. Specifically, you will create a weather app that shows the weather based on the user's current location. Here's what the output will look like:

![Weather app Fuse preview](https://www.smashingmagazine.com/wp-content/uploads/2016/09/app-preview-opt.png)[3](https://www.smashingmagazine.com/2017/05/fuse-native-cross-platform-apps/)

> _Weather app Fuse preview_

In creating the app, you will learn how to use some of Fuse's built-in UI components and learn how to access native device functionality such as geolocation. Towards the end of the article, you will consolidate your learning by looking at the advantages and disadvantages of using Fuse for your next mobile app project.

I'd like to describe how Fuse works using the following diagram:

![How Fuse works](https://www.smashingmagazine.com/wp-content/uploads/2016/09/how-fuse-works-opt.png)[8](https://www.smashingmagazine.com/2017/05/fuse-native-cross-platform-apps/)

> _How Fuse works_

On the top layer are the UX Markup and JavaScript. This is where we will spend most of our time when working with Fuse. On the middle layer are the libraries that are packaged with Fuse. This includes the JavaScript APIs that allow access to native device features such as geolocation and the camera. Lastly, on the bottom layer is the Uno compiler, which is responsible for translating the UX Markup into pure native code (Objective-C for iOS and C++ for Android). Once the app runs, all of the UI that you will see will be native UI for that particular platform. JavaScript code is executed via a virtual machine on a separate thread. This makes the UI really snappy because JavaScript won't affect the UI's performance.

Before we create an app with Fuse, one of the important questions that needs to be answered is how does it stack up against existing tools that do the same job. In this section, we'll learn about the features and tools available in Fuse compared to those of React Native and NativeScript, as well as how things are done on each platform. Specifically, we'll compare the following areas:

  * UI markup
  * Layout
  * JavaScript APIs
  * Extendability
  * JavaScript Libraries
  * Animation
  * Community
  * Development Workflow
  * Debugging

On all platforms, the UI can be built using an XML-based language. Common UI components such as text fields, switches and sliders are available on each platform.

React Native has the most of these components, although some are not unified, which means that there can be a maximum of two ways to use a particular component. For example, one can be used on both platforms, and one for a specific platform only. A few components, such as the `ProgressBar`, are also implemented differently on each platform, which means that it's not totally "write once, run everywhere."

On the other hand, NativeScript has a unified way of implementing the different UI components on each platform. For every component, there's an equivalent native component for both Android and iOS.

Fuse has a decent number of UI components that will cover the requirements of most projects. One component that's not built into either React Native or NativeScript is the `Video` component, which can be used to play local videos and even videos from the Internet. The only component that is currently missing is the date-picker, which is especially useful during user registration. Though you can always create your own using the components that are already available to Fuse.

In React Native, layout is done with Flexbox. In a nutshell, Flexbox enables you to specify how content should flow through the available space. For example, you can set `flex` to `1` and `flexDirection` to `row` in a container element in order to equally divide the available space among the children and to arrange the children vertically.
    
    
    <View style={{flex: 1, flexDirection: 'row'}}>
    	<View style={{backgroundColor: 'powderblue'}} />
    	<View style={{backgroundColor: 'skyblue'}} />
    	<View style={{backgroundColor: 'steelblue'}} />
    </View>
    

In NativeScript, layout is achieved using layout containers, the most basic one being `StackLayout`, which puts all elements on top of each other, just like in the example below. In a horizontal orientation, they're placed side by side.
    
    
    <StackLayout orientation="vertical">
        <Image src="assets/images/dog.png" />
        <Image src="assets/images/cat.png" />
        <Image src="assets/images/gorilla.png" />
    </StackLayout>	
    

Similarly, Fuse achieves layout by using a combination of the different elements in UX Markup, the most common ones being `StackPanel`, `Grid` and `DockPanel`. `StackPanel` works similar to `StackLayout` in NativeScript. Here's an example:
    
    
    <StackPanel Orientation="Vertical">
    	<Panel Height="100" Background="Red" />
    	<Panel Height="100" Background="White" />
    	<Panel Height="100" Background="Blue" />
    </StackPanel>
    

All of the platforms cover all of the basics with JavaScript APIs. Things like camera functionality, platform information, geolocation, push notifications, HTTP requests and local storage can be done on all platforms. However, looking at the documentation for each platform, you could say that React Native has the most JavaScript APIs that bridge the gap between native and "JavaScript native" features. There's no official name yet for platforms such as React Native, NativeScript and Fuse, so let's just stick with "JavaScript native" for now, because they all use JavaScript to write code and they all offer native-like performance.

If you need access to specific device features that don't expose a JavaScript API yet, each platform also provides ways for developers to tap into native APIs for Android and iOS.

NativeScript gives you access to all of the native APIs of the underlying platform through JavaScript. This means you don't have to touch any Swift, Objective-C or Java code in order to make use of the native APIs. The only requirement is that you know how the native APIs work.

React Native falls a bit short in accessing native APIs because you'll have to know the native language in order to extend native functionality. This is done by creating a native module (an Objective-C class for iOS or a Java class for Android), exposing your desired public methods to JavaScript, then importing it into your project.

Fuse allows you to extend functionality through a feature that it refers to as "foreign code." This allows you to call native code on each platform through the Uno language. The Uno language is the core technology of Fuse. It's what makes Fuse work behind the scenes. Making use of native features that aren't supported by the core Fuse library is done by creating an Uno class. Inside the Uno class, you can write the Objective-C or Java code that implements the functionality you want and have it exposed as JavaScript code, which you can then call from your project.

Both React Native and NativeScript supports the use of all npm packages that don't have dependencies on the browser model. This means you can use a library such as lodash and moment simply by executing `npm install {package-name}` in your project directory and then importing it in any of your project files, just like in a normal JavaScript project.

Fuse, on the other hand, is currently lacking in this regard. Usage of existing JavaScript libraries is mostly not possible; only a [short list of libraries](https://www.fusetools.com/docs/fusejs/third-party-modules) are known to work. The good news is that the developers are constantly working on polyfills to improve compatibility with existing libraries.

Another important part of the UX is animation. In React Native, animation is implemented via its Animated API. With it, you can customize the animation a lot. For example, you can specify how long an animation takes or how fast it runs. But this comes with the downside of not being beginner-friendly. Even simple animation such as scaling a particular element requires a lot of code. The good thing is that libraries such as [React Native Animatable](https://github.com/oblador/react-native-animatable) make it easier to work with animation. Here's sample code for implementing a `fadeIn` animation using the Animatable library:
    
    
    <Animatable.View animation="fadeIn">Fade me in!</Animatable.View>

NativeScript animations can be implemented in two ways: via the CSS3 animations API or the JavaScript API. Here's an example of scaling an element with a class of `el`:
    
    
    .el {
        animation-name: scale;
        animation-duration: 1;
    }
    
    @keyframes scale {
        from { transform: scale(1, 1); }
        to { transform: scale(1.5, 1.5); }
    }
    

And here's the JavaScript equivalent:
    
    
    var view = page.getViewById('box'); //must have an element with an ID of box in the markup
    view.animate({
        scale: { x: 1.5, y: 1.5},
        duration: 1000
    });
    

Animation in Fuse is implemented via triggers and animators. Triggers are used to detect whether something is happening in the app, whereas animators are used to respond to those events. For example, to make something bigger when pressed, you would have this:
    
    
    <Rectangle Width="50" Height="50" Fill="#ccc">
    	<WhilePressed>
        	<Scale Factor="2" />
    	</WhilePressed>
    </Rectangle>
    

In this case, `<WhilePressed>` is the trigger and `<Scale>` is the animator.

When it comes to community, React Native is the clear winner. Just the fact that it was created by Facebook is a big deal. Because the main technology used to create apps is React, React Native taps into that community as well. This means that a lot of projects can help you to develop apps. For example, you can reuse existing React components for your React Native project. And because many people use it, you can expect to quickly get help when you get stuck, because you can just search for an answer on Stack Overflow. React Native is also open-source, and the source code is [available on GitHub](https://github.com/facebook/react-native). This makes development really fast because the maintainers can accept help from developers outside of the organization.

NativeScript, meanwhile, was created by Telerik. The project has a decent-sized community behind it. If you look at [its GitHub page](https://github.com/NativeScript/NativeScript), currently over 10,000 people have starred the project. It has been forked 700 times, so one can assume that the project is getting a lot of contributions from the community. There are also a lot of NativeScript packages on npm and questions on Stack Overflow, so expect that you won't have to implement custom functionality from scratch or be left alone looking for answers if you get stuck.

Fuse is the lesser known among the three. It doesn't have a big company backing it up, and Fuse is basically the company itself. Even so, the project comes complete with documentation, a forum, a Slack channel, sample apps, sample code and video tutorials, which make it very beginner-friendly. The Fuse core is not yet open-source, but the developers will be making the code open-source soon.

With React Native and NativeScript, you need to have an actual mobile device or an emulator if you want to view changes while you're developing the app. Both platforms also support live reloading, so every time you make a change to the source files, it automatically gets reflected in the app -- although there's a slight delay, especially if your machine isn't that powerful.

Fuse, on the other hand, allows you to preview the app both locally and on any number of devices currently connected to your network. This means that both designers and developers can work at the same time and be able to preview changes in real time. This is helpful to the designer because they can immediately see what the app looks like with real data supplied by the developer's code.

When it comes to debugging, both React Native and NativeScript tap into Chrome's Developer Tools. If you're coming from a web development background, the debugging workflow should make sense to you. That being said, not all features that you're used to when inspecting and debugging web projects are available. For example, both platforms allow you to debug JavaScript code but don't allow you to inspect the UI elements in the app. React Native has a built-in inspector that is the closest thing to the element inspector in Chrome's Developer Tools. NativeScript currently doesn't have this feature.

On the other hand, Fuse uses the Debugging Protocol in Google's V8 engine to debug JavaScript code. This allows you to do things like add breakpoints to your code and inspect what each object contains at each part in the execution of the code. The Fuse team encourages the use of the [Visual Studio Code](https://code.visualstudio.com/) text editor for this, but any text editor or IDE that supports V8's Debugging Protocol should work. If you want to inspect and visually edit the UI elements, Fuse also includes an inspector -- although it allows you to adjust only a handful of properties at the moment, things like widths, heights, margins, padding and colors.

Now you're ready to create a simple weather app with Fuse. It will get the user's location via the GeoLocation API and will use the OpenWeatherMap API to determine the weather in the user's location and then display it on the screen. You can find the full source code of the app in the [GitHub repository](https://github.com/anchetaWern/fuse-simple-weatherapp).

To start, go to the OpenWeatherMap website and [sign up for an account](https://home.openweathermap.org/users/sign_up). Once you're done signing up, it should provide you with an API key, which you can use to make a request to its API later on.

Next, visit the [Fuse downloads page](https://www.fusetools.com/downloads), enter your email address, download the Fuse installer for your platform, and then install it. Once it's installed, launch the Fuse dashboard and click on "New Project". This will open another window that will allow you to select the path to your project and enter the project's name.

![Creating a new Fuse project](https://www.smashingmagazine.com/wp-content/uploads/2016/09/creating-a-project-opt.png)[17](https://www.smashingmagazine.com/2017/05/fuse-native-cross-platform-apps/)

> _Creating a new Fuse project (_

Do that and then click on the "Create" button to create your project. If you're using Sublime Text 3, you can click on the "Open in Sublime Text 3" button to open a new Sublime Text instance with the [Fuse project](https://packagecontrol.io/packages/Fuse) already loaded. Once you're in there, the first thing you'll want to do is install the Fuse package. This includes code completion, "Goto definition," previewing the app from Sublime and viewing the build.

Once the Fuse plugin is installed, open the `MainView.ux` file. This is the main file that we will be working with in this project. By default, it includes sample code for you to play with. Feel free to remove all of the contents of the file once you're done inspecting it.

When you create an app with Fuse, you always start with the `<App>` tag. This tells Fuse that you want to create a new page.
    
    
    <App>
    </App>
    

Fuse allows you to reuse icon fonts that are commonly used for the web. Here, we're using [Weather Icons](https://erikflowers.github.io/weather-icons/). Use the `<Font>` tag to specify the location of the web font file in your app directory via the `File` attribute. For this project, it's in the `fonts` folder at the root directory of the project. We also need to give it a `ux:Global` attribute, which will serve as its ID when you want to use this icon font later on.
    
    
    <Font File="fonts/weather-icons/font/weathericons-regular-webfont.ttf" ux:Global="wi" />
    

Next, we have the JavaScript code. We can include JavaScript code anywhere in UX Markup by using the `<JavaScript>` tag. Inside the tag will be the JavaScript code to be executed.
    
    
    <JavaScript>
    </JavaScript>
    

In the `<JavaScript>` tag, require two built-in Fuse libraries: Observable and GeoLocation. Observable allows you to implement data-binding in Fuse. This makes it possible to change the value of the variable via JavaScript code and have it automatically reflected in the UI of the app. Data-binding in Fuse is also two-way; so, if a change is made to a value via the UI, then the value stored in the variable will also be updated, and vice versa.
    
    
    var Observable = require('FuseJS/Observable');	
    

GeoLocation allows you to get location information from the user's device.
    
    
    var Geolocation = require('FuseJS/GeoLocation');	
    

Create an object containing the hex code for each of the weather icons that we want to use. You can find the hex code on the [GitHub page of the icon font](https://erikflowers.github.io/weather-icons/).
    
    
    var icons = {
       'clear': '\uF00d',
       'clouds': '\uF002',
       'drizzle': '\uF009',
       'rain': '\uF008',
       'thunderstorm': '\uF010',
       'snow': '\uF00a',
       'mist': '\uF0b6',
       'fog': '\uF003',
       'temp': '\uF055'
    };	
    

Create a function to convert Kelvin to Celsius. We need it because the OpenWeatherMap API returns temperatures in Kelvin.
    
    
    function kelvinToCelsius(kelvin){
        return kelvin - 273.15;
    }	
    

Determine whether it's currently day or night based on the time on the user's device. We'll use orange as the background color for the app if it's day, and purple if it's nighttime.
    
    
    var hour = (new Date()).getHours();
    var color = '#7417C0';
    if(hour >= 5 && hour <= 18){
        color = '#f38844';
    }	
    

Add the OpenWeather Map API key that you got earlier and create an observable variable that contains the weather data.
    
    
    var api_key = 'YOUR OPENWEATHERMAP API KEY';
    var weather_data = Observable();	
    

Get the location information:
    
    
    var loc = Geolocation.location;	
    

This will return an object containing the `latitude`, `longitude` and `accuracy` of the location. However, Fuse currently has a problem with getting location information on Android. If the location setting is disabled on the device, it won't ask you to enable it when you open the app. So, as a workaround, you'll need to first enable location before launching the app.

Make a request to the OpenWeatherMap API using the `fetch()` function. This function is available in Fuse's global scope, so you can call it from anywhere without including any additional libraries. This will work the same way as the `fetch()` function available in modern browsers: It also returns a promise that you need to listen to using the `then()` function. When the supplied callback function is executed, the raw response is passed in as an argument. You can't really use this yet since it contains the whole response object. To extract the data that the API actually returned, you need to call the `json()` function in the response object. This will return another promise, so you need to use `then()` one more time to extract the actual data. The data is then assigned as the value of the observable that we created earlier.
    
    
    var req_url = 'http://api.openweathermap.org/data/2.5/weather?lat=' + loc.latitude + '&lon=' + loc.longitude + '&apikey=' + api_key;
    fetch(req_url)
    .then(function(response) {
        return response.json();
    })
    .then(function(responseObject) {
        weather_data.value = {
            name: responseObject.name,
            icon: icons[responseObject.weather[0].main.toLowerCase()],
            weather: responseObject.weather[0],
            temperature: kelvinToCelsius(responseObject.main.temp)  + ' °C'
        };
    });	
    

For your reference, here's a sample response returned by the API:
    
    
    {
       "coord":{
          "lon":120.98,
          "lat":14.6
       },
       "weather":[
          {
             "id":803,
             "main":"Clouds",
             "description":"broken clouds",
             "icon":"04d"
          }
       ],
       "base":"stations",
       "main":{
          "temp":304.15,
          "pressure":1009,
          "humidity":74,
          "temp_min":304.15,
          "temp_max":304.15
       },
       "visibility":10000,
       "wind":{
          "speed":7.2,
          "deg":260
       },
       "clouds":{
          "all":75
       },
       "dt":1473051600,
       "sys":{
          "type":1,
          "id":7706,
          "message":0.0115,
          "country":"PH",
          "sunrise":1473025458,
          "sunset":1473069890
       },
       "id":1701668,
       "name":"Manila",
       "cod":200
    }	
    

Export the variables so that it becomes available in the UI.
    
    
    module.exports = {
        weather_data: weather_data,
        icons: icons,
        color: color
    };	
    

Because this project is very small, I've decided to put everything in one file. But for real projects, the JavaScript code and the UX Markup should be separated. This is because the designers are the ones who normally work with UX Markup, and the developers are the ones who touch the JavaScript code. Separating the two allows the designer and the developer to work on the same page at the same time. You can separate the JavaScript code by creating a new JavaScript file in the project folder and then link it in your markup, like so:
    
    
    <JavaScript File="js/weather.js">	
    

Finally, add the actual UI of the app. Here, we're using `<DockPanel>` to wrap all of the elements. By default, `<DockPanel>` has a `Dock` property that is set to `Fill`, so it's the perfect container for filling the entire screen with content. Note that we didn't need to set that property below because it's implicitly added. Below, we have only assigned a `Color` attribute, which allows us to set the background color using the color that we exported earlier.
    
    
    <DockPanel Color="{color}">
    </DockPanel>	
    

Inside `<DockPanel>` is `<StatusBarBackground>`, which we'll dock to the top of the screen. This allows us to show and customize the status bar on the user's device. If you don't use this component, `<DockPanel>` will consume the entirety of the screen, including the status bar. Simply setting this component will make the status bar visible. We don't really want to customize it, so we'll just leave the defaults.
    
    
    <StatusBarBackground Dock="Top" />	
    

Below `<StatusBarBackground>` is the actual content. Here, we're wrapping everything in a `<ScrollView>` to enable the user to scroll vertically if the content goes over the available space. Inside is `<StackPanel>`, containing all of the weather data that we want to display. This includes the name of the location, the icon representing the current weather, the weather description and the temperature. You can display the variables that we exported earlier by wrapping them in braces. For objects, individual properties are accessed just like you would in JavaScript.
    
    
    <ScrollView>
        <StackPanel Alignment="Center">
            <Text Value="{weather_data.name }" FontSize="30" Margin="0,20,0,0" Alignment="Center" TextColor="#fff" />
            <Text Value="{weather_data.icon}" Alignment="Center" Font="wi" FontSize="150" TextColor="#fff" />
            <Text Value="{weather_data.weather.description}" FontSize="30" Alignment="Center" TextColor="#fff" />
            <StackPanel Orientation="Horizontal" Alignment="Center">
                <Text Value="{icons.temp}" Font="wi" FontSize="20" TextColor="#fff" />
                <Text Value="{weather_data.temperature}" Margin="10,0,0,0" FontSize="20" TextColor="#fff" />
            </StackPanel>
        </StackPanel>
    </ScrollView>	
    

You might also notice that all attributes and their values are always capitalized; this is the standard in Fuse. Lowercase or uppercase won't really work. Also, notice that `Alignment="Center"` and `TextColor="#fff"` are repeated a few times. This is because Fuse doesn't have the concept of inheritance when it comes to styling properties, so setting `TextColor` or `Alignment` in a parent component won't actually affect the nested components. This means we need to repeat it for each component. This can be mitigated by creating components and then simply reusing them without specifying the same style properties again. But this isn't really flexible enough, especially if you need a different combination of styles for each component.

The last thing you'll need to do is to open the `{your project name}.unoproj` file at the root of your project folder. This is the Uno project file. By default, it contains the following:
    
    
    {
      "RootNamespace":"",
      "Packages": [
        "Fuse",
        "FuseJS"
      ],
      "Includes": [
        "*"
      ]
    }	
    

This file specifies what packages and files to include in the app's build. By default, it includes the `Fuse` and `FuseJS` packages and all of the files in the project directory. If you don't want to include all of the files, edit the items in the `Includes` array, and use a glob pattern to target specific files:
    
    
    "Includes": [
        "*.ux",
        "js/*.js"
    ]	
    

You can also use `Excludes` to blacklist files:
    
    
    "Excludes": [
        "node_modules/"
    ]	
    

Going back to the `Packages`, `Fuse` and `FuseJS` allow you to use Fuse-specific libraries. This includes utility functions such as getting the environment in which Fuse is currently running:
    
    
    var env = require('FuseJS/Environment');
    if (env.mobile) {
        debug_log("There's geo here!");
    }	
    

To keep things lightweight, Fuse includes only the very basics. So, you'll need to import things like geolocation as separate packages:
    
    
    "Packages": [
        "Fuse",
        "FuseJS",
        "Fuse.GeoLocation"
    ],	
    

Once `Fuse.GeoLocation` has been added, Fuse will add the necessary libraries and permissions to the app once you've compiled the project.

You can run the app via the Fuse dashboard by selecting the project and clicking on the "Preview" button.

![Running the app](https://www.smashingmagazine.com/wp-content/uploads/2016/09/running-the-app-opt.png)[22](https://www.smashingmagazine.com/2017/05/fuse-native-cross-platform-apps/)

> _Running the app (View large version)_

This lets you pick whether to run on Android, iOS or locally. (Note that there is no iOS option in the screenshot because I'm running on Windows.) Select "Local" for now, and then click on "Start." This should show you a blank screen because geolocation won't really work in a local preview. What you can do is close the preview then update the `req_url` to use the following instead, which allows you to specify a place instead of the coordinates:
    
    
    var req_url = 'http://api.openweathermap.org/data/2.5/weather?q=london,uk&apikey=' + api_key;
    

You'll also need to comment out all of the code that uses geolocation:
    
    
    //var Geolocation = require('FuseJS/GeoLocation');
    //var loc = Geolocation.location;
    //var req_url = 'http://api.openweathermap.org/data/2.5/weather?lat=' + loc.latitude + '&lon=' + loc.longitude + '&apikey=' + api_key;
    

Run the app again, and it should show you something similar to the screenshot at the beginning of the article.

If you want to run on a real device, please check "[Preview and Export](https://www.fusetools.com/docs/basics/preview-and-export)" in the documentation. It contains detailed information on how to deploy your app to both Android and iOS devices.

Now that you have tested the waters, it's time to look at some of the pros and cons of using Fuse for your next mobile app project. As you have seen so far, Fuse is both developer- and designer-friendly, because of its real-time updates and multi-device preview feature, which enables developers and designers to work at the same time. Combine that with the native UX and access to device features, and you've got yourself a complete platform for building cross-platform apps. This section will drive home the point on why you should (or shouldn't) use Fuse for your next mobile app project. First, let's look at the advantages.

Fuse is developer-friendly because it uses JavaScript for the business logic. This makes it a very approachable platform for creating apps, especially for web developers and people who have some JavaScript experience. In addition, it plays nice with JavaScript transpilers such as Babel. This means that developers can use new ECMAScript 6 features to create Fuse apps.

At the same time, Fuse is designer-friendly because it allows you to import assets from tools such as Sketch, and it will automatically take care of slicing and exporting the pieces for you.

Aside from that, Fuse clearly separates the business logic and presentation code. The structure, styles and animations are all done in UX Markup. This means that business-logic code can be placed in a separate file and simply linked from the app page. The designer can then focus on designing the user experience. Being able to implement animations using UX Markup makes things simpler and easier for the designer.

Fuse makes it very easy for designers and developers to collaborate in real time. It allows for simultaneous previewing of the app on multiple devices. You only need USB the first time you connect the device. Once the device has been connected, all you need to do is connect the device to the same Wi-Fi network as your development machine, and all your changes will be automatically reflected on all devices where the app is open. The sweetest part is that changes get pushed to all the devices almost instantly. And it works not just on code changes: Any change you make on any linked asset (such as images) will trigger the app to reload as well.

Fuse also comes with a preview feature that allows you to test changes without a real device. It's like an emulator but a lot faster. In "design mode," you can edit the appearance of the app using the graphical user interface. Developers will also benefit from the logging feature, which allows them to easily debug the app if there are any errors.

If you need functionality not already provided by the Fuse libraries, Fuse also allows you to implement the functionality yourself using Uno. Uno is a language created by the Fuse team itself. It's a sub-language of C# that compiles to C++. This is Fuse's way of letting you access the native APIs of each platform (Android and iOS).

UX Markup is converted to the native UI equivalent at compile time. This makes the UI really snappy and is comparable to native performance. And because animations are also written declaratively using UX Markup, animations are done natively as well. Behind the scenes, Fuse uses [OpenGL ES](https://en.wikipedia.org/wiki/OpenGL_ES) acceleration to make things fast.

No tool is perfect, and Fuse is no exception. Here are a few things to consider before picking Fuse.

  * Structure and style are mixed together. This makes the code a bit difficult to edit because you have to specify styles separately for each element. This can be alleviated by creating components in which you put common styles.
  * Linux is not supported, and it's not currently on the road map. Though Linux developers who want to try out Fuse can still use a Windows Virtual Machine or Wine to install and use Fuse on their machine.
  * It's still in beta, which means it's still rough around the edges and not all the features that you might expect from a mobile app development platform is supported. That said, Fuse is very stable and does a good job at the small set of features that it currently supports.
  * It's not open-source, though there are plans to open-source the core Fuse platform. This doesn't mean that you can't use Fuse for anything though. You can freely use Fuse to create production apps. If you're interested about licensing, you can read more about it in the [Fuse License Agreement.](https://res.cloudinary.com/fusetools/raw/upload/staticwebsitecontent_v2/f904f85bf03ee6f2898f99d78777d445__media/fuse_developer_preview_license_agreement.pdf)

We've learned about Fuse, a newcomer in the world of JavaScript native app development. From what I've seen so far, I can say that this project has a lot of potential. It really shines in multi-device support and animation. And the fact that it's both designer- and developer-friendly makes it a great tool for developing cross-platform apps.

  * [Fuse documentation](https://www.fusetools.com/docs)  
There's no better place to learn about a new technology than the official documentation.
  * "[Learning Fuse](https://www.youtube.com/playlist?list=PLdlqWm6b-XALJgM3fGa4q95Yipsgb8Q1o)," YouTube  
If you learn better through videos, the Fuse team has put together this YouTube playlist to help you learn about the features that Fuse offers.

_(da, vf, yk, al, il)_
