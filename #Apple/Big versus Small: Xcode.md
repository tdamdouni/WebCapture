# Big versus Small: Xcode

_Captured: 2015-06-18 at 23:26 from [wczekalski.com](http://wczekalski.com/big-versus-small-xcode/)_

Apple has announced Xcode 7. Not a surprise. This update brings us SpriteKit/SceneKit visual editors, UI Tests, more powerful Playgrounds, and [many more](https://developer.apple.com/library/prerelease/ios/documentation/DeveloperTools/Conceptual/WhatsNewXcode/Articles/xcode_7_0.html).

**A 3D graphics editor inside an IDE.** It sounds sort of controversial. Xcode is not a _swift_ application. It just got bigger.

### Loosing focus

I build software with text. I also debug, profile, use assets, take advantage of amazing visual tools, but 90% of time, I **write** code.

When I started iOS development -- not a long time ago -- Xcode 3.2 had just been announced. There was _just_ a decent text editor, a debugger, and _build & run_ magic.

It has been extended with enormous amount of features since then. Storyboards, Interface Builder was integrated, App Store submission tools and many others. In fact it has grown so now much that we can almost go from an idea to the App Store submission without leaving the application.

I have all those amazing toys now, but I still build software with text. What bothers me is that despite slightly improved auto completion, I cannot recall any enhancments to text editing. _Refactoring_ doesn't work, there's no code generation or support for more test driven [workflow](https://www.jetbrains.com/objc/).

New features are not expected to be perfect. Innovation is great, but any regression -- in terms of speed, responsiveness, reliability -- undermines its importance.

### Massive IDE

The notion of _massivness_ is very popular in Xcode. `IDEEditorContext`, a view controller which is the **container** for the text editor view controller has **230 method implementations**. That's massive, and what follows, hyper-vulnerable.

Big applications tend to be slow, they are usually hard to maintain, error-prone, and extremely challenging to iterate upon. Building decent UX for big apps is a struggle. It all adds up and makes maintaining high quality nearly impossible.

The iOS community is growing. Inherently, there are different groups of developers having completely different expectations and needs. If Apple tries to satisfy every single group with Xcode, it _might_ just mean making the experience worse.

What's more, separation introduces completely new possibilites. Imagine if we could make Interface Builder designer friendly. Or give the power of creating the UI tests -- with all those amazing tools -- to the QA team. It's not impossible now, but it's so much harder. The entry barrier to the IDE is rather high.

Given my limited knowledge this one-stop-shop strategy is not reasonable. I hope there is a rationale behind it. _I don't know_, so I filed a radar for it.

If you feel the same duplicate `rdar://21359244`.

_Just don't forget: tooling is not just what Apple can do:_   
<https://www.youtube.com/watch?v=flSMEw_Hxik>
