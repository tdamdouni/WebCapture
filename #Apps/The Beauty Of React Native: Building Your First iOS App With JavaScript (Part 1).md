# The Beauty Of React Native: Building Your First iOS App With JavaScript (Part 1)

_Captured: 2016-06-19 at 22:43 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)_

The idea of building mobile apps with JavaScript is not new. We've seen frameworks like [Ionic](http://ionicframework.com/) and [PhoneGap](https://www.smashingmagazine.com/2014/02/four-ways-to-build-a-mobile-app-part3-phonegap/) take on the challenge, and to some extent succeed in gaining a fair amount of developer and community support. To [part 2](https://www.smashingmagazine.com/2016/04/how-to-build-your-first-ios-app-with-javascript/) of the tutorial.

These frameworks and **the whole idea of building mobile apps with JavaScript** never appealed to me, though. I always thought, why not just learn Swift/Objective-C or Java and build real apps? That definitely requires a significant amount of learning, but isn't that what we developers do and should be good at? Quickly learn new languages and frameworks? What's the point, then? For me, the advantages never outweighed the doubts.

Until I read [this article from Chalk + Chisel](https://medium.com/ios-os-x-development/an-ios-developer-on-react-native-1f24786c29f0#.avhlz9qsr), the following line in particular:

> Fast-forward a couple of months, and I'm confident enough to say I may never write an iOS app in Objective-C or Swift again.

What? Are you, like… serious?

Reading such a bold assertion made me go ahead and give React Native a shot. Why not? I was already using React and loving it. React Native is so similar to React (duh!), you'll feel right at home if you're already a React developer. Even if you're not, React luckily happens to be very easy to wrap your head around.

I've never had luck finding the perfect wallpaper app for my iPhone in the App store. On the desktop, [Unsplash](http://unsplash.com/) is the one-stop shop for all my wallpaper needs. On the phone: Settings -> Wallpaper :(

So, unlike some other tutorials where you build counters and barely use them, in this tutorial, together we'll build ourselves an app that will pull random stunning wallpapers from Unsplash, display them in an aesthetically pleasing way, and allow you to save wallpapers of your choice to the Camera Roll. Believe me, I have found myself using this app more than I initially thought. Even if by the end of this tutorial React Native fails to impress you, you'll still end up having a really cool wallpaper app. Isn't that great?

Before we start, here are **some things you should be familiar with:**

  1. JavaScript
  2. Mac OS X Terminal
  3. CSS (yup!)

One more thing. As the title clearly states, in this tutorial we'll be building an _iOS_ app. Which requires, yes, even with React Native, that you're on a Mac. With React Native you can definitely [build Android apps on Windows and Linux](https://facebook.github.io/react-native/docs/linux-windows-support.html) but not iOS ones. Therefore, from here on in, this tutorial assumes you're running Mac OS X.

By the end of this tutorial, you'll be familiar enough with React Native to start writing your own apps right away. We'll go over setting up a project in Xcode, installing third party modules and components, linking libraries, styling with flexbox, creating a custom gesture listener, and many other things.

If you haven't used React before, this tutorial will also set you up with React. React is the new hot JS library with a lot of potential, and I don't see it going anywhere in near future.

This tutorial has been divided into two parts for your convenience. Each part has five sections. In each section we accomplish a goal that takes us a step closer to finishing our app. I'd advise that once started you should finish that whole section in one go since they are short, and in that way you'll get to know the whole concept I am trying to introduce without breaking your flow.

For your reference, the final code for the app we're building can be found in [this GitHub repo](https://github.com/nashvail/SplashWalls).

Advertisement

Make sure you have [Xcode 7.0](https://developer.apple.com/xcode/) or higher installed. it can be downloaded free from the App Store.

Chances are (if you're a web developer and reading this in 2016) you already have Node installed. But if that's not the case, go ahead and install [Node](https://nodejs.org/en/) too. Another important tool we'll need is [npm](https://docs.npmjs.com/getting-started/what-is-npm). Node comes with npm installed; you'll need to update it, however, as it gets updated rather frequently. Follow [this installation guide](https://docs.npmjs.com/getting-started/installing-node).

That's all we'll need. Now, from the terminal run `npm install -g react-native-cli`. This will install React Native globally on your system.

If everything seems way too new to you, or you're just feeling a little lost in the whole installation process, the [official getting started guide](https://facebook.github.io/react-native/docs/getting-started.html#content) is always there to help you out.

Find a good location on your computer where you would like to set up the project. Once there, from the terminal run `react-native init SplashWalls`.

This should fetch and install all the required modules and create a new folder called _SplashWalls_.

![Initial contents of SplashWalls folder.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/01-react-native-preview-opt.png)[19](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Contents of SplashWalls folder._

One great thing about React Native is you can write both Android and iOS applications together with a majority of JavaScript code shared between them. Inside the newly created folder you will find two _.js_ files: _index.android.js_ and _index.ios.js_ - the names are self-explanatory. If you're building an iOS app you'll work with _index.ios.js_; with _index.android.js_ for an Android app; and both for, you know, both platforms.

Since we're building an iOS app, for the sake of this tutorial and to keep things clean we will get rid of the _index.android.js_ and the _android_ folder altogether. _index.ios.js_ is the file we'll be working with. This is the file that is first executed when the app launches.

Next, head on over to the _ios_ folder and fire up _SplashWalls.xcodeproj_.

You should see a Xcode window pop up like one shown below.

![Xcode on first launch.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/02-react-native-preview-opt.png)[20](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Xcode on first launch._

Notice the warning in the image above that says "No matching provisioning profiles found." Let's fix this.

First, change the text in the field **Bundle Identifier** to something custom. You need to make sure that whatever you enter follows [reverse DNS convention](https://en.wikipedia.org/wiki/Reverse_domain_name_notation), in which the domain name of your organization is reversed and suffixed with further identifiers. This convention helps distinguish your application from others on a device and on the App Store. I will use _com.nashvail.me.tutorial.SplashWalls_; simply substitute your name in place of mine if you can't seem to make something up.

Next, choose your name from the team dropdown.

![Choose a team name.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/03-react-native-preview-opt.png)[22](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Choose a team name._

Click on **Fix Issue**.

While we're at it, notice the **Deployment Info** section. It has some default settings applied.

![Initial Deployment info settings.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/04-react-native-preview-opt.png)[23](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Initial deployment info settings._

Change the settings to match the following:

![Final deployment info settings.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/05-react-native-preview-opt.png)[24](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Final deployment info settings._

We'll make the app portrait-only and hide the status bar as well.

Go ahead and hit the **Run** button at the top-left in Xcode. Doing so will launch a terminal window like one shown below. Initial transformation takes a bit of time.

![Terminal window on first run.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/06-react-native-preview-opt.png)[25](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Terminal window on first run._

Once done, you should see the following output in the simulator:

![Simulator on first launch.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/07-react-native-preview-opt.png)[26](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Simulator on first launch._

And with this we've completed our very first section.

In this section we will make calls to the [Unsplash.it](http://unsplash.it) API asking for wallpaper data. But before we start doing all the interesting work, there is some set-up to be done.

On opening the _index.ios.js_ file you'll notice some initial code already present. This is the code responsible for the output in the simulator (previous image).

Inside _index.ios.js_ notice the line of code that says `var SplashWalls = React.createClass({ ... })`. We are going to modify this. We will use ES2015's `class` syntax for this tutorial.

We developers are curious souls. I know you must be asking, Why? Why switch to the `class` syntax?

It all comes down to personal preference. I have programmed extensively in object-oriented languages before and `class` just feels more familiar to me. Moreover, by using `class` you also choose to keep the code a little cleaner as you don't have to add commas after each method declaration.

On the flip side, when you choose `class` you don't get features like autobinding or access to the `isMounted` method, which is not a bad thing at all, as you're not really going to find yourself at a loss by not using these.

Whichever way you go, you're creating a class after all. My advice would be to use `class`. It's a new feature and sooner or later you'll find yourself using ES2015. And if you're following this tutorial, you will have to use `class` - you don't really have a choice!

For more on this consider reading "[React.Component vs React.createClass](https://reactjsnews.com/composing-components)" by Naman Goel and Zach Silveira.

Once you've made the necessary changes, the block of code should now be as shown:
    
    
    class SplashWalls extends Component{
      render() {
        return (
          
      . <View style={styles.container}>
            <Text style={styles.welcome}>
              Welcome to React Native!
            </Text>
            <Text style={styles.instructions}>
              To get started, edit index.ios.js
            </Text>
            <Text style={styles.instructions}>
              Press Cmd+R to reload,{'\n'}
              Cmd+D or shake for dev menu
            </Text>
           
       .</View>
        );
      }
    };
    

For folks new to React, the code inside `return` parens may seem a little wacky, but it's not rocket science, just good old XML-like syntax called JSX. [Read more about it here](https://facebook.github.io/jsx/).

Compared with the pre-`class` implementation, the `var` syntax is gone. Also `render: function(){…` is now just `render(){…`.

Hey! But what is that `Component` you are extending? And you'd be right to ask. If you ran the project in Xcode now, you'd get an error saying `Component` is not defined. You can do two things here: replace `Component` with `React.Component`; or add a new line inside the block (shown below) at the top of the file.

In this and later code examples, I surround the newly added lines with `/***/` so that it's easier for you to compare the code you're writing with what is shown here. Just make sure that if you copy code from the samples you don't end up copying `/***/` along with the actual code. Since JSX doesn't support `/***/` comments, you will end up crashing the app if you included these in your JSX code.
    
    
    var {
      AppRegistry,
      StyleSheet,
      Tex .t,
      View,
      /***/
      Component 
      /***/
    } = React;
    

All the block of code above does is save you a couple of keystrokes. For example, if you didn't include these lines of code at the top, you'd have to write `React.AppRegistry` instead of just `AppRegistry` every time you wanted to do so. Pretty frigging cool! Isn't it? OK, not so much.

Go back to Xcode and run the project once again to make sure you didn't break anything in the process.

Everything good? Great! Let's move on.

Inside the `SplashWalls` class, the first thing we need to do is add a constructor. Inside the constructor we will initialize our state variables. The only two state variables we will need at this point are an array - `wallsJSON` - which is going to store all the JSON data fetched from the API, and `isLoading`, which is a Boolean variable, meaning it will hold a value of either true or false. Having this state variable will help us show and hide the loading screen depending on whether the data has been loaded or not.

Inside the `SplashWalls` class, add the `constructor` as shown below.
    
    
    class SplashWalls extends Component{
    /***/
      constructor(props) {
        super(props);
    
        this.state = {
          wallsJSON: [],
          isLoading: true
        };
      }
    /***/
    ...
    }
    

Next, we will define a _fetchWallsJSON_ method, which, well, does what it says. Leave a couple of lines below the constructor's closing brace and add the following lines of code:
    
    
    fetchWallsJSON() {
    	console.log(‘Wallpapers will be fetched’);
    }

We would like this function to fire once our component has been successfully mounted. Add the `componentDidMount` method. Most of the described methods go inside the `SplashWalls` class - I'll not forget to mention when they don't.

`componentDidMount` is a lifecycle method which is fired immediately after the first rendering occurs.

![Initial render LifeCycle method call sequence.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/32-react-native-preview-opt.png)[30](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Initial render lifecycle method call sequence. (Image credit:_

[Here's a good explanation of all the React component's lifecycle methods](https://facebook.github.io/react/docs/component-specs.html). Just remember that since we're using the newer `class` syntax, we can omit the `getInitialState` method. It is substituted by a `this.state` variable declaration in the `constructor`.

It's a good idea to organize methods inside your class in a clean manner. I like to keep all the custom methods separate from the lifecycle methods. You should too.

Let's declare `componentDidMount`:
    
    
    componentDidMount() {
    	this.fetchWallsJSON();
    }

Notice that inside the `fetchWallsJSON` method we have logged a message to the console - but where is the console? Hold tight.

Make sure you have the Simulator window selected and press Cmd + Control + Z. From the menu that pops up, select **Debug in Chrome**. This opens up a new tab. While in the same tab, head over to Dev Tools (Option + Cmd + J). In the console you will find the message "Wallpapers will be fetched".

![Logged message in the console.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/08-react-native-preview-opt.png)[33](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Logged message in the console._

Keep the debugger open for now. Visit [unsplash.it/list](http://unsplash.it/list) in a new tab. You should see the whole viewport filled with a JSON array. Each element in the array is a JavaScript object holding data for a single wallpaper. This is the data we will be filtering through and grabbing random wallpapers from.

Let us first make `fetchWallsJSON` do more than just log a message to the console.
    
    
      fetchWallsJSON() {
    	/***/
        var url = 'http://unsplash.it/list';
        fetch(url)
          .then( response => response.json() )
          .then( jsonData => {
            console.log(jsonData);
          })
    	.catch( error => console.log(‘Fetch error ‘ + error) );
    	/***/
      }

Refresh the simulator (Cmd + R) or, better, enable live reload by pressing Cmd + Ctrl + Z and choosing **Enable live reload**. By enabling live reload you don't have to refresh the simulator each time you make a change to your code. Just save in the IDE and the simulator will automatically be refreshed. If you've ever developed an app in Xcode or Android Studio before, you'll find this feature particularly amazing as you don't have to hit the **Run** button and recompile the app every single time you make a change. These little bits make React Native so much more appealing.

On refresh, after waiting a few seconds, you should see the following output in the console:

![Retrieved data logged in the console.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/09-react-native-preview-opt.png)[35](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Retrieved data logged in the console._

Good, now we're able to fetch wallpapers' JSON data from the API. As you might have noticed there is a little delay before the data is logged to the console. This is because in the background the data is being downloaded from the servers, which takes time.

This looks like a perfect time to add a loading screen.

By the end of this section we will have a loading screen show up while the JSON data is being downloaded.

First, get rid of everything from inside `SplashWall` class's `render` method and add these lines of code:
    
    
      render() {
        var {isLoading} = this.state;
        if(isLoading)
          return this.renderLoadingMessage();
        else
          return this.renderResults();
      }

We have two new methods. Let's declare them too, while we're at it
    
    
      renderLoadingMessage() {
        return (
          
      . <View style={styles.loadingContainer}>
            <ActivityIndicatorIOS
              animating={true}
              color={'#fff'}
              size={'small'} 
              style={{margin: 15}} />
              <Text style={{color: '#fff'}}>Contacting Unsplash</Text>
           
       .</View>
        );
      }
    
      renderResults() {
        return (
          
      . <View>
            <Text>
              Data loaded
            </Text>
           
       .</View>
        );
      }

Depending on what value the `isLoading` state variable holds, two different `View` components will be rendered. If `isLoading` is true we show a loading spinner followed by the text "Contacting Unsplash"; when `isLoading` is false (implying data has been loaded) we show the results, which as of now is just a `Text` component that says "Data loaded".

But we're missing something here: we're not changing the value of `isLoading` once our data has been downloaded. Let us do just that. Head over to the `fetchWallsJSON` method and below the line that logs `jsonData` to the console, add one extra line to update `isLoading`.
    
    
      fetchWallsJSON() {
        var url = 'http://unsplash.it/list';
        fetch(url)
          .then( response => response.json() )
          .then( jsonData => {
            console.log(jsonData);
    	/***/
            this.setState({isLoading: false}); //update isLoading 
    	/***/
          })
    	.catch( error => console.log(‘Fetch error ‘ + error) );
      }

[setState](https://facebook.github.io/react/docs/component-api.html#setstate) is one of [React's Component API methods.](https://facebook.github.io/react/docs/component-api.html) It is the primary method used to trigger UI updates.

Notice, in `renderLoadingMessage` we have a new component: `ActivityIndicatorIOS` (put simply, the spinner). We need to import this component before we can use it. [Remember when we imported `Component` ](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)where we saved a couple of keystrokes? We'll need to do just that.
    
    
    var {
      AppRegistry,
      StyleSheet,
      Tex .t,
      View,
      Component,
    /***/
      ActivityIndicatorIOS // Add new component
    /***/
    } = React;

We need to do one more thing before we can see the results. Notice the `View` containing `ActivityIndicatorIOS` has style set to `styles.loadingContainer`. We'll need to define that. Find the line that says `var styles = StyleSheet.create({…`. Here you will see there are some styles already defined. These styles are responsible for styling the initial "Welcome to React Native" message in the simulator. Get rid of all of the predefined styles and add just one for the `loadingContainer` as shown.
    
    
    var styles = StyleSheet.create({
    /***/
      loadingContainer: {
    	flex: 1,
        flexDirection: 'row’,
        justifyContent: 'center',
        alignItems: 'center',
        backgroundColor: '#000'
      }
    /***/
    });

All of the styles you apply on components in React Native are declared in the manner shown above. `StyleSheet.create` takes in a JavaScript object containing styles as an argument and then the styles can be accessed using the `dot[.]` operator. Like we applied the style to wrapper `View` in the following manner.
    
    
    <View style={styles.loadingContainer}/>

You're also allowed to declare styles inline:
    
    
    <View style={{
    	flex: 1,
        flexDirection: 'row',
        justifyContent: 'center',
        alignItems: 'center',
        backgroundColor: '#000'
      }} />

This makes our code a little cluttered, though. When you have a number of styles applied to a component, it's always a good idea to store them in a variable.

The styles look a lot like CSS, don't they? You know why? Because they're supposed to - they're not any different. This makes React Native even easier for web developers to pick up. When you build an app in a dedicated IDE (Xcode, for example) you're provided with a _StoryBoard_ to directly drag and position UI elements like buttons and labels on the screen. You can't do that in React Native, which - believe me - isn't a bad thing at all.

**React Native makes heavy use of flexbox to position elements on the screen.** Once you're comfortable with flexbox, positioning elements around is a breeze. I will on any day prefer flexbox layout over StoryBoard, period. It's just one of those things you have to try yourself to tell the difference.

Save the changes, head over to the simulator and press Cmd + R. You should see the loading screen.

![Loading screen we just finished building.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/10-react-native-preview-opt.png)[39](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Loading screen we just finished building._

After a few seconds you should see the screen that says "Data loaded".

![Data loaded message is visible once data finishes loading.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/11-react-native-preview-opt.png)[40](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _The data loaded message is visible once data finishes loading._

In this section we will filter through the wallpaper data and pick specified number of random wallpapers.

This section will focus more on JavaScript than React Native. We will go through creating a new module (file) that will handle random number generation. If modules in JavaScript sound new to you, consider going through the [Node.js modules docs](https://nodejs.org/api/modules.html#modules_modules).

Go to the line above the `class` declaration and declare a new constant that will tell the app the number of random wallpapers to pick; let's make it five.
    
    
    const NUM_WALLPAPERS = 5;

Now we're going to create a module that'll help us with the generation of random numbers. This module will export two functions. Let's look a look at each one of them.

  * `uniqueRandomNumbers`: This function takes in three arguments. First is the number of random numbers that are to be returned. The next two arguments define the range in which the random numbers are to be returned, namely `lowerLimit` and `upperLimit`. If you call the function `uniqueRandomNumbers(5, 10, 20)` you will be returned an array of five unique random numbers between 10 and 20. 
  * `randomNumberInRange`: This function takes in two arguments defining the lower and upper limit respectively between which a single random number is returned. For example, if you call `randomNumberInRange(2, 10)` a unique random number between 2 and 10 is returned. 

We could have merged both of these functions into one, but as I am a preacher of good quality code, I follow the [single responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle). SRP states, more or less, that each function should do one thing well and not do anything else. Following good programming principles saves you from a number of future headaches.

Create a new file in the same directory as _index.ios.js_. If we wanted to, we can put these functions in _index.ios.js_, but think about it: for the kind of purpose this new file serves we can simply copy this file and paste in any of our new projects that requires generation of random numbers and use it from there. Also, this keeps the code within _index.ios.js_ that much cleaner.

We'll call the file _RandManager.js_. Shown below is its content:
    
    
    module.exports = {
    	uniqueRandomNumbers(numRandomNumbers, lowerLimit, upperLimit) {
    		var uniqueNumbers = [];
    		while( uniqueNumbers.length != numRandomNumbers ) {
    			var currentRandomNumber = this.randomNumberInRange(lowerLimit, upperLimit);
    			if( uniqueNumbers.indexOf(currentRandomNumber) === -1 ) 
    				uniqueNumbers.push(currentRandomNumber);
    		}
    		return uniqueNumbers;
    	},
    
    	randomNumberInRange(lowerLimit, upperLimit) {
    		return Math.floor( Math.random() * (1 + upperLimit - lowerLimit) ) + lowerLimit;
    	}
    
    };

Don't forget to require the `RandManager` module in _index.ios.js_. Just add: `var RandManager = require('./RandManager.js');` below the `use strict;` statement. Once we have `RandManager` ready, we'll make the following changes to our `fetchWallsJSON` function:
    
    
    fetchWallsJSON() {
      var url = 'http://unsplash.it/list';
      fetch(url)
        .then( response => response.json() )
        .then( jsonData => {
        /***/
          var randomIds = RandManager.uniqueRandomNumbers(NUM_WALLPAPERS, 0, jsonData.length);
          var walls = [];
          randomIds.forEach(randomId => {
            walls.push(jsonData[randomId]);
          });
    
          this.setState({
            isLoading: false,
            wallsJSON: [].concat(walls)
          });
        /***/
        })
        .catch( error => console.log('JSON Fetch error : ' + error) );
    }

Once we have the `jsonData`, we retrieve unique random numbers from `RandManager` and store them in the `randomIds` array. We then loop through this array, picking up wallpaper data objects present at a particular `randomId` and storing them in `walls` array.

Then we update our state variables: `isLoading` to false as data has been downloaded; and `wallsJSON` to `walls`.

To see the results, modify the `renderResults` function to resemble the following:
    
    
    renderResults() {
    /***/
      var {wallsJSON, isLoading} = this.state;
      if( !isLoading ) {
        return (
          
      . <View>
            {wallsJSON.map((wallpaper, index) => {
              return(
                <Text key={index}>
                  {wallpaper.id}
                </Text>
              );
            })}
           
       .</View>
        );
      }
    /***/
    }
    

In the very first line inside `renderResults` we're using a new ES2015 feature called [destructuring](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment). With destructuring we have managed to substitute:
    
    
    var wallsJSON = this.state.wallsJSON,
    	isLoading = this.state.isLoading;
    

with:
    
    
    var {wallsJSON, isLoading} = this.state;

ES2015 is pretty cool, I am telling you.

Then, inside the `View` we loop through the retrieved `wallsJSON` data using [map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map). Whenever you want to loop through a collection in [JSX](https://facebook.github.io/jsx/) you use the `map` construct.

Also, when looping through an array or collection and rendering a component, React Native requires you to give a `key`, a unique ID to each of the child components that renders. That is why you see a _key_ property in
    
    
    <Text key={index}>

Once the simulator refreshes…

![Randomly generated Ids are visible once data finishes loading.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/12-react-native-preview-opt.png)[46](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Randomly generated IDs are visible once data finishes loading._

We see five different random wallpaper IDs being displayed. Change `{wallpaper.id}` to `{wallpaper.author}` in `renderResults` and you should see something like the following.

![Author names corresponding to random ids.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/13-react-native-preview-opt.png)[47](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Author names corresponding to random IDs._

Great! Now we're talking. We are now able to fetch and filter the specified number (five, in this case) of random wallpapers from the API. Looks like we're done for this section. High five!

In this section we will include a _Swiper_ component in our app. This component will allow us to display wallpapers in a swipeable container.

You'll learn how to include a third-party React Native component in our app. React Native has amazing community support and on GitHub there is a [rich collection](https://react.parts/native) of all kinds of different third-party components.

Head to the project directory in the terminal and run the following command:
    
    
    npm install react-native-swiper --save

Now require the `Swiper` component: add `var Swiper = require('react-native-swiper');` below `use strict`.

Let's try out our newly included `Swiper` component.

Go to the `renderResults` method and replace `View` with `Swiper`. After doing this, your `renderResults` should look like this:
    
    
    renderResults() {
      var {wallsJSON, isLoading} = this.state;
      if( !isLoading ) {
        return (
        /***/
          <Swiper>
        /***/
            {wallsJSON.map((wallpaper, index) => {
              return(
                <Text key={index}>
                  {wallpaper.author}
                </Text>
              );
            })}
        /***/
          </Swiper>
        /***/
        );
      }
    }
    

Doing so results in the following:

![Each author name visible in its very own container.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2016/02/14-react-native-preview-opt.png)[50](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/)  


> _Each author name is visible in its very own container._

Instead of showing the names of authors as a list, we have put them in a swiper which gives each wallpaper its very own screen, which we can swipe across. We need to do a couple more things here: add the following attributes to the `Swiper` component as shown.
    
    
    <Swiper
    /***/
    dot.{<View style={{backgroundColor:'rgba(255,255,255,.4)', width: 8, height: 8,borderRadius: 10, marginLeft: 3, marginRight: 3, marginTop: 3, marginBottom: 3,}} />}
    
    activeDot.{<View style={{backgroundColor: '#fff', width: 13, height: 13, borderRadius: 7, marginLeft: 7, marginRight: 7}} />}
    
    loop={false}
    
    onMomentumScrollEnd={this.onMomentumScrollEnd}
    /***/
    >
      {wallsJSON.map((wallpaper, index) => {
        return(
          <Text key={index}>
            {wallpaper.author}
          </Text>
        );
      })}
    </Swiper>

Doing this:

  * Styles the pagination dots (makes the blue dots you see at the bottom in the previous image white and bigger).
  * Disables continuous swiping (`loop={false}`). That is, once you reach the final page and you swipe further you're not taken back to the first wallpaper.
  * Will fire `onMomentumScrollEnd` (which we'll be delving further into in the next part of the tutorial) each time we're done swiping.

With this, we've come to an end of the first part. What a journey!

  * In the first section you learned how to set up a blank React Native project in Xcode.
  * In the second section we talked about ES2015 classes and why you should prefer the newer syntax along with creating state variables and grabbing raw data from the API.
  * In section three we went over dynamically rendering the app based on the value a state variable holds. Also, we did some light flexbox positioning.
  * In the fourth section we created a brand new module to handle random number generation and also went over including it in the main file.
  * In the last section we added the first third-party component to our app, which was a cakewalk, thanks to Node.

Up until now, to be honest, our app doesn't look very special. I know. In the next part we will add actual images instead of just author names. Not only that, we will be doing some advanced stuff like creating a custom double-tap detector using the `PanHandler` API. You will learn how to link a library in Xcode and grant your app access to the Camera Roll. We will also create our very own component and a lot more. Sound interesting? See you in the next part.

_(da, ml, og, il)_

**Hold on, Tiger! Thank you for reading the article.** Did you know that we also publish [printed books](https://www.smashingmagazine.com/books/) and run [friendly conferences](https://www.smashingmagazine.com/smashing-workshops/) - crafted for pros like you? Like [SmashingConf New York](http://ny.smashingconf.com/), on June 14-15, with smart design patterns and front-end techniques.
