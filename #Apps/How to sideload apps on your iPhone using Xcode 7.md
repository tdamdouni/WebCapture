# How to sideload apps on your iPhone using Xcode 7

_Captured: 2015-06-14 at 16:04 from [bouk.co](http://bouk.co/blog/sideload-iphone/)_

[Github](https://github.com/bouk) [Twitter](https://twitter.com/bvdbijl)

Apple just [released the Xcode 7 Beta](https://developer.apple.com/xcode/), and one of the new features is that anyone can now load apps onto their device without having to be a member of the developer program. I'm going to demonstrate how to do this using [GBA4iOS](https://bitbucket.org/rileytestut/gba4ios).

  1. Open Xcode 7, open preferences and login to your Apple Account. ![](https://monosnap.com/image/LHWIw08QfN4DhVXfo4uAPg1AG6ORGb.png)

> _Download the source code of the app you want to install and follow any setup instructions. (_

  2. `sudo gem install cocoapods; git clone https://bitbucket.org/rileytestut/gba4ios.git; cd gba4ios; pod install` for GBA4iOS). Open the workspace or project in Xcode.
  3. Plug in your iPhone and select it as the build destination. ![](https://monosnap.com/image/x52sXmKKYKu2nyPuOy89z2P4X4tris.png)

> _We now need to generate a code signing signature for the app. Click on the project on the left, fill in a unique "Bundle Identifier" and click on "Fix Issue" (make sure your name is selected as "team")_

  4. ![](https://monosnap.com/image/tPx4KY779FtuD1YkkfuiZn5vYNPiMU.png)

> _Click the play button in the top left. If there's no build errors the app should now launch on your phone!_

[Follow me on Twitter](https://twitter.com/BvdBijl)

### FAQ

**Q:** Will I need to install the iOS 9 beta/OSX El Capitan?

**A:** Nope, this will work on any iOS/OSX version.

**Q:** I'm getting this error message:

**A:** You will need to try a different Apple ID because of a [bug](https://twitter.com/kaptin/status/608727199965958144).

**Q:** I'm getting and error containing `'GCControllerPlayerIndex' with an rvalue of type 'int'` while trying to compile GBA4iOS

**A:** Change line 546 in `GBA4iOS/GBAEmulationViewController.mm` to `[controller setPlayerIndex:GCControllerPlayerIndex1];`
