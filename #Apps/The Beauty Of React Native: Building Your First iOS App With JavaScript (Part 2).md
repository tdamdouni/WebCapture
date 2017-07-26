# The Beauty Of React Native: Building Your First iOS App With JavaScript (Part 2)

_Captured: 2016-06-19 at 22:41 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2016/04/how-to-build-your-first-ios-app-with-javascript/)_

In [part 1 of this tutorial](https://www.smashingmagazine.com/2016/04/the-beauty-of-react-native-building-your-first-ios-app-with-javascript-part-1/), we started building our iOS app from scratch. We started out by setting up a blank React Native project. Then we pulled data from the [Unsplash.it](http://unsplash.it) API.

Because downloading data takes time, we built a loading screen. In the process we went over positioning UI elements with flexbox and styling them using CSS-like properties. Towards the end of part 1 we downloaded and included a third-party `Swiper` component from GitHub, which allowed us to display wallpaper data in a swipeable container.

It doesn't do much yet but that's all about to change. In this part of the tutorial we will start by replacing the photographer's name with the actual wallpaper image along with proper credits. During this process you'll learn how to link a library in Xcode, as well as more on general styling and positioning of UI elements. Then we will go over building a custom double-tap listener using the PanResponder API and a little bit of math. Toward the end you will learn how to save pictures to the Camera Roll and also how to run your app on a physical device. To apply all your newly learned React Native skills there is a challenge waiting for you at the end.

Just like the first part, this article has five sections. Completing each section takes us a step closer to finishing our app.

Let's take a look at the data each wallpaper object holds. Consider the following sample data.
    
    
    {
    	author: "Patryk Sobczak"
    	author_url: "https://unsplash.com/patryksobczak"
    	filename: "0611_bS92UkQY8xI.jpeg"
    	format: "jpeg"
    	height: 1280
    	id: 611
    	post_url: "https://unsplash.com/photos/bS92UkQY8xI"
    	width: 1920
    }

To look at the wallpaper you can point your browser to `http://unsplash.it/{width}/{height}?image={id}` which translates to `<http://unsplash.it/1920/1280?image=611>` in this case. That is one high-quality wallpaper.

Since we're able to construct a URL for the image, we can add an `Image` component with proper `source` attribute.

But let's not get ahead of ourselves. Wallpapers that we pull from Unsplash are high quality and may take time to load. If we simply use React Native's `Image` component we will leave our users staring at a blank screen while the wallpaper loads. We need a progress bar-like component here - luckily, there is a component for just that.

The two components we will use to achieve our goal are [react-native-image-progress](https://github.com/oblador/react-native-image-progress) and [react-native-progress](https://github.com/oblador/react-native-progress).

Head over to the project directory from terminal and run the following two commands:
    
    
    npm install --save react-native-image-progress
    
    
    npm install --save react-native-progress

Let's import these into our _index.ios.js_ file. Add the following two lines right below the `use strict;` statement:
    
    
    var NetworkImage = require('react-native-image-progress');
    var Progress = require('react-native-progress');

Since our wallpaper images cover the whole viewport, we will need to know the width and height of the viewport. To do that add:
    
    
    var {width, height} = React.Dimensions.get('window’);

outside the class declaration and right below the import statements. If you have been following carefully you'll of course know that we can substitute `React.Dimensions` with `Dimensions` by adding a new line to the React import code block.
    
    
    var {
      AppRegistry,
      StyleSheet,
      Text,
      View,
      Component,
      ActivityIndicatorIOS,
    /***/
      Dimensions // Add this line 
    /***/
    } = React;

Just saving a couple of keystrokes, y'know.

Now, we will use the `NetworkImage` component in `renderResults`.
    
    
    <Swiper ... >
      {wallsJSON.map((wallpaper, index) => {
        return(
        /***/
          <View key={index}>
            <NetworkImage
              source={{uri: `https://unsplash.it/${wallpaper.width}/${wallpaper.height}?image=${wallpaper.id}`}}
              indicator={Progress.Circle}
              style={styles.wallpaperImage}>
            </NetworkImage>
          </View>
        /***/
        );
      })}
    </Swiper>

Notice the value that `uri` holds inside `NetworkImage`'s `source` attribute. This is one of ES2015's new features called [template strings](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/template_strings). Template strings allow you to include variables right inside the string using `${variableName}` instead of concatenating them again and again using `+`.

I'll tell you again. ES2015 _is_ pretty cool!

Add the following style definition to the `styles` variable:
    
    
    wallpaperImage: {
      flex: 1,
      width: width,
      height: height,
      backgroundColor: ‘#000’
    }

Refresh the simulator and you should end up with a bunch of errors. Don't worry, we didn't break anything. The compiler is just complaining about a library it needs and cannot find. Let's help the compiler out.

Taking a closer look at the code we just added, notice one of the `NetworkImage`'s properties is `indicator` and it holds the value of `Progress.Circle`. As mentioned in the component's docs on GitHub (don't tell me you didn't [read the docs](https://github.com/oblador/react-native-progress)) `Progress.Circle` requires ReactART, which is a library to draw vector graphics using React. We don't need to download anything new here, just include it in our project, this time through Xcode.

Clicking on any of the images below will point you to a larger version of that image, which will give you a better idea of what's going on.

Concentrate and pay close attention here.

Head to the following path from the root of the project: _node_modules/react-native/Libraries/ART/_
