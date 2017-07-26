# How we use Fastlane

_Captured: 2016-12-05 at 23:42 from [www.whitesmith.co](https://www.whitesmith.co/blog/how-we-use-fastlane/)_

If you already know me or if you paid attention to our blog, we use [Fastlane](https://fastlane.tools) a lot to automate some iOS development processes. I [wrote](https://www.whitesmith.co/blog/build-mobile-cross-automation-with-fastlane/) about it almost a year ago and I [talked](http://www.slideshare.net/Whitesmithco/fastlane-by-ricardo-pereira) about it as well to my fellows Whitesmithians in on of our Lunch'n'Learn sessions. I'm a huge fan of [Fastlane](https://fastlane.tools). It let us save a ton of time while we are coding. Personally, I hate dealing with version incrementation, code signing, provisioning profiles, etc. Who doesn't, right? 😅

> Version numbers: one of the hard problems of computer science.
> 
> -- Jesse Squires (@jesse_squires) [August 1, 2016](https://twitter.com/jesse_squires/status/760203109767315457)

Let's keep this straightforward and let me show you how we use Fastlane 🚀 and how we get away from all those frustrations.

## Fantastic 4

On an app, we always use 4 lanes: `setup`, `test`, `beta` and `release`.

### SETUP 🚝

The `setup` lane is responsible for setting up a development machine for any new member that is joining the team. It usually runs a couple of commands that install all the dependencies needed. We often use something like setting up CocoaPods, Carthage, etc.

Here is an example:
    
    
    desc "Setup workspace"  
    lane :setup do  
      ## Setup pre-commit hook
      sh "ln -s scripts/pre-commit.sh .git/hooks/pre-commit"
      ## Setup badge to add a beta watermark to your iOS app icon
      sh "gem install badge"
      ## Install CocoaPods
      # Remove old versions
      sh "gem uninstall cocoapods -aIx"
      # v1
      sh "gem install cocoapods -v '1.0.1' --no-rdoc --no-ri --no-document --quiet"
      ## Install Carthage
      sh "brew install carthage || true"
      ## Verify project dependencies
      carthage update
      cocoapods
    end  
    

### TEST 🚝

Next, we have a `test` lane that is really short. We can assume it as a basic task. However, a lane can help you standardize the way that the developer tests the app.
    
    
    desc "Runs all tests"  
    lane :test do |options|  
      # `scan` makes it easy to run tests of your iOS app
      scan skip_slack: (not options[:slack])
    end
    

The lane accepts an optional parameter called `slack` where the developer can choose if he wants to push a slack message when the test suite fails.
    
    
    error do |lane, exception, options|  
      if options[:slack]
        slack(message: "<APP_SCHEME> App: " + exception.message, success: false)
      end
    end  
    

### BETA 🚝

`beta` lane is my **favorite**! Why? Because it does everything for me, that's why 😄. This one runs the test suite, builds a beta release, submits the binary to [TestFlight](https://developer.apple.com/testflight/) and [Crashlytics](https://fabric.io/kits/android/crashlytics) 🙌.

First of all, there is a sub-lane called `version_bump_project` that the `beta` lane uses to increment the version and build a number of the project before it builds the binary. You can call the sub-lane on the terminal as well, independently of any other lane.
    
    
    desc "Increment the version and build number"  
    lane :version_bump_project do |options|  
      # Set build number to current date and time
      build_number = Time.new.strftime("%Y.%m.%d.%H.%M")
      ENV["BUILD_NUMBER"] = build_number
      increment_build_number build_number: build_number
      # Set version number conforming the bump type
      if options[:bump_type]
        increment_version_number bump_type: options[:bump_type]
      end
    end  
    

The lane accepts an important argument named `bump_type` where it can be `patch`, `minor` and `major`. It will automatically increment the patch, minor, or major version number according to your choice. In this case, the build number will always be the current date and time, so the final result will be something like "**_v2.1.1 (2016.8.5.9.53)_**".

Now for the `beta`, there are many steps to digest. First, we need to bump the project version with
    
    
    version_bump_project bump_type: options[:bump]  
    

then we call the `badge` gem that will add a watermark to your iOS app icon (take a look at the [gem](https://github.com/HazAT/badge)).
    
    
    badge(dark: true)  
    

This is a nice touch when you want to send the app to someone. He can easily see which version of the app he wants to install or run on his device.

Next, the glorious step!   
We use [match](https://github.com/fastlane/fastlane/tree/master/match) to prevent code signing issues and to simplify the codesigning setup. It has the great advantage to share one code signing identity across the team. That means that anyone can build a binary quite easily.

For **Crashlytics**, the `match` action will retrieve and setup the right AdHoc provisioning profile
    
    
    match(type: "adhoc")  
    

Then the binary is created using the current profile
    
    
    gym(  
      scheme: "<APP_SCHEME>",
      export_method: "ad-hoc",
      xcargs: "APP_PROFILE='#{ENV["sigh_<PRODUCT_BUNDLE_IDENTIFIER>_adhoc"]}'",
    )
    

**Note:** don't forget to replace `<APP_SCHEME>` and `<PRODUCT_BUNDLE_IDENTIFIER>` with your app project information. For example, `scheme: "Qold"` and `xcargs: "APP_PROFILE='#{ENV["sigh_co.whitesmith.qold_adhoc"]}'"`.

After the successful archive, it is necessary to upload the binary to the Crashlytics service and it is done.
    
    
    crashlytics(  
      api_token: "???",
      build_secret: "???",
      ipa_path: "./build/<APP_SCHEME>.ipa",
      notes: "Build at " + Time.new.strftime("%H:%M:%S %d.%m.%Y")
    )
    

For **TestFlight**, it is quite the same but `match` will select a different profile.
    
    
    match(type: "appstore")
    
    # Archive
    gym(  
      scheme: "<APP_SCHEME>",
      export_method: "app-store",
      xcargs: "APP_PROFILE='#{ENV["sigh_<PRODUCT_BUNDLE_IDENTIFIER>_appstore"]}'",
    )
    
    # Submit to iTunes Connect
    pilot(  
      skip_submission: true,
      skip_waiting_for_build_processing: true
    ) # Skip the distribution of the app to all beta testers
    

We distribute the beta binary to iTunes Connect with the AppStore profile just for convenience. We could be using the same AdHoc profile from Crashlytics. The other way around is not supported (I mean, Crashlytics does not support AppStore profiles. An AdHoc profile always needs a list of registering test devices, so if you use Crashlytics then it gives you more work like registering each test device on the provisioning profile).

Finally, after the archive and upload, the lane can notify that the beta is ready:
    
    
    slack(message: "Build " + build_number + " is ready.")  
    

### RELEASE 🚝

Now for the `release` lane, it is quite the same as the `beta`. You only need to remove the beta badge and just upload it to the AppStore (iTunes Connect).

You can check the full `Fastfile` [here](https://gist.github.com/ricardopereira/05e588c4b6d5af2232ae6809af275cc5).

**Update**: I made some changes on how to pass parameters to Fastlane based on [this](https://github.com/fastlane/fastlane/blob/master/fastlane/docs/Advanced.md#passing-parameters). Thank you [@KrauseFx](https://twitter.com/KrauseFx) for the tip.

**Note:** If you want to run a `release` lane because of a small bug fix, you can do it like `fastlane release bump:patch`.

## Considerations

About building the binary, it is important to setup `match` correctly. All required keys, certificates, and provisioning profiles should be installed successfully on your machine.

If you want to add more test devices to an AdHoc provision profile that `match` manage then you just need to add each device on iTunes Connect and run `match adhoc --force_for_new_devices true`.

We are still in Xcode 7 but if you are already using the new version then check [this](https://github.com/fastlane/fastlane/blob/master/fastlane/docs/Codesigning/XcodeProject.md). Seems that **Xcode 8** provides new features to simplify the process of certificate management and app signing.

That's it. I hope that you enjoyed it as much as I did and as always... if you liked it and if you want to receive more posts about us then please subscribe ♥️.
