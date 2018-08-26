# Build Incrementation Techniques for the iOS Release Train

_Captured: 2018-05-31 at 15:36 from [dzone.com](https://dzone.com/articles/building-incrementation-techniques-for-the-ios-rel?edition=379209&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=mobile%202018-05-31)_

Continuous delivery of iOS apps is essential to stay relevant in the competitive market. Companies with the infrastructure to release features to the customers as soon as it is developed win the race over companies who do manual releases from someone's local Xcode. In continuous delivery mode, we should be constantly uploading the iOS build to iTunes Connect or TestFlight to get feedback from all the technical and non-technical people involved in the release. There isn't any harm in uploading the build to iTunes Connect as long as we have a proper build and versioning process. In this post, we will see the best techniques to automatically increment build numbers in the continuous delivery pipeline.

## Release Train

Before we jump into the automatic build numbers for our iOS app, we will see how version numbers, build numbers, and release trains work when submitting an iOS app to the App Store. Apple has great documentation on [version number and build numbers](https://developer.apple.com/library/content/technotes/tn2420/_index.html) that every iOS developer should understand. The combination of the version number and build number uniquely identify an App Store submission.

### Version Number

Version numbers of an iOS app differentiate the app from the previous version. We need to create a separate version number for new app release. It is similar to creating a release on GitHub using semantic versioning. The legal version numbers would be 1.0, 1.1.1, etc., but you can not combine letter and numbers like `abc.123` as that would be an illegal version number. The version numbers cannot be reused, so you have to decide in advance for the major and minor releases. The new version number value MUST be greater than previously used value and it should be subsequently incremented. The value of the current version number can be found in the `Info.plist` file of the iOS app with the key `CFBundleShortVersionString`, or in the case of an uploaded iOS app, we can check in iTunes Connect to find out the version number. We can check the current version number using Apple's `agvtool` command line tool.

### Build Number

Multiple builds can be uploaded for the specific version number, however, the build number uploaded for the specific version number should be unique and in incremental order. The value of the build's number can be reused for a different version number. The value of the current build number can be found in the `Info.plist` file of the iOS app with the CFBundleVersion key. We can check the current version number using Apple's `agvtool` command line tool.

### Release Train

The number of builds submitted for the specific version forms Release Train for that specific version. In the release train, build number are in the incremental order and unique. The train can take multiple builds with the specific feature and we can promote any build to App Store if needed. In short, the release train is the foundation of Continuous Delivery.

## Build Incrementation in the Release Train

There are a few strategies for incrementing the build numbers within the release trains. We will see each of them and discuss which one would be great for release trains.

### agvtool

Apple has a native command line tool to deal with version and build numbers. We can enable `agvtool` and write the script to automatically increment the build number in the specific release train. In order to enable agvtool, we need to make sure that **Current Project Version** and **Versioning System** properties are set correctly in the target build settings. Select the target build settings and search for "versioning." Now, set **Current Project Version **to** 1** and set the **Versioning System value **to** "Apple Generic." **The next thing to verify is that make sure the **Info** tab has Bundle versions and Bundle versions string, and short values are set probably to 1 for the new project.

We can increment the build number to the next build number using the following command:

When we execute this from the CI server, it updates the Info.plist files which we need to commit back to source control once the build is successfully uploaded. This is one of the drawbacks of this technique. We have to update source control frequently from the CI server.

### PlistBuddy

We can achieve the version bump of the build number using the PlistBuddy tool, which is used for dynamically updating the plist files. We can easily write the script:

This will increment the build number by one. Again, this updates the Info.plist files which we need to commit back to source control once the build is successfully uploaded

### Fastlane Plugin

There are some other third-party tools, like [Fastlane](https://fastlane.tools/), which can also do the same thing. Fastlane has actions to increment both build and version number. The [increment_version_number](https://docs.fastlane.tools/actions/increment_version_number/) action can be used to increment the version number, which has various options as well. We can bump it to a major or minor version, and we can specify the version number.

The [increment_build_number ](https://docs.fastlane.tools/actions/increment_build_number/)action can be used to update the build number values.

There is a number of options to manage the build and version numbers, but these actions also use agvtool under the hood. In this case, we have to use another Fastlane action to [commit the version bump](https://docs.fastlane.tools/actions/commit_version_bump/#commit_version_bump), to commit the new version back to source control from our CI server.

Again, this approach needs integration with GitHub and frequent changes in the source control from the continuous integration server.

### Scripted Build Numbers

There is another way which doesn't require us to commit back the version number from the continuous integration server. This technique uses a scripted build based on some magic number and increments the build number accordingly. You can read more about this technique [here](https://tgoode.com/2014/06/05/sensible-way-increment-bundle-version-cfbundleversion-xcode/).

This technique works very well; we just need to add another Run Script build phase to execute this script.
    
    
    buildNumber=$(expr $(git rev-list $branch --count) - $(git rev-list HEAD..$branch --count))
    
    
    /usr/libexec/PlistBuddy -c "Set :CFBundleVersion $buildNumber" "${TARGET_BUILD_DIR}/${INFOPLIST_PATH}"
    
    
    if [ -f "${BUILT_PRODUCTS_DIR}/${WRAPPER_NAME}.dSYM/Contents/Info.plist" ]; then

This will give a new build number whenever we upload a new build. The benefit of using this approach is that we don't have to commit the version bump back from the continuous integration server.

## Which Technique to Use?

As of now, we have seen four different techniques to increment the build numbers in the iOS release train. It's bit tricky to choose the technique that is suitable for your iOS app because it depends on the skills of the iOS developers working on the team. All the techniques will work well if scripted and managed properly. However, I would prefer the last one with the scripted build as it doesn't involve changing source control repository from the continuous integration server.

## Conclusion

In the iOS continuous delivery pipeline, automating the version and build number saves a lot of time and we can easily form a release train without any hassle using the build incrementation techniques mentioned above. Which strategy do you use for build incrementation? Please let me know if I missed anything.

Topics:

continuous delivery ,ios ,mobile ,mobile app development ,tutorial ,Build Incrementation
