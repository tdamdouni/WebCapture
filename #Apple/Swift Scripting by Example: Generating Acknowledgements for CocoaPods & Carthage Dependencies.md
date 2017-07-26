# Swift Scripting by Example: Generating Acknowledgements for CocoaPods & Carthage Dependencies

_Captured: 2015-11-13 at 09:41 from [swift.ayaka.me](http://swift.ayaka.me/posts/2015/11/5/swift-scripting-generating-acknowledgements-for-cocoapods-and-carthage-dependencies)_

We started using both [CocoaPods](https://cocoapods.org) and [Carthage](https://github.com/Carthage/Carthage) to manage our dependencies, and we wanted to add a nice little view in our app that shows a list of open-source acknowledgements and licenses. We have around 20 dependencies, and the thought of adding the acknowledgements manually sounded tedious and keeping everything updated every time we added/removed/updated a dependency sounded even worse. 💀

When something is tedious _and_ requires repeating, it's the worst. (Especially if you are lazy like me!) But the good thing is, with a bit of code we can automate all the things. We can take our laziness and do something fun. 🌟

Best of all, we can do this all in Swift!

  1. Get all `LICEN(S|C)E` files for CocoaPods and Carthage dependencies.
  2. Convert the Markdown into HTML.
  3. Put the HTML file in our Xcode project.
  4. Load the HTML into a `WKWebView` (or `UIWebView` for < iOS 9) and show it in the app.

Steps 1-4 can live in a script, and once we write step 5 once, it will be automatically updated everytime we run the script. In our case, we took it one small step further and added it as a task to our `Rakefile` so we regenerate the acknowledgements HTML everytime we run `rake` (which also installs dependencies) so we can keep our licenses up-to-date when we add, remove, or update dependencies. (Thanks [@_eliperkins](https://twitter.com/_eliperkins) for your help with this!)

Even if this isn't the exact solution for the exact problem that you're trying to solve, the concepts that we will go over here will be applicable to other Swift scripts that you might want to write.

Let's get started.

When I learned that "license" can be spelled with two C's as in "licence" I was very surprised. Anyway, let's first see where we can find all of the licenses (and licences too I suppose).

  * CocoaPods LICENSE files live in `Pods/[LibraryName]` (like `Pods/TZStackView/LICENSE`).
  * Carthage LICENSE files live in `Carthage/Checkouts/[LibraryName]` (like `Carthage/Checkouts/SSKeychain/LICENSE`).

To find all of the `LICENSE` files, we can use `[NSFileManager`](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Classes/NSFileManager_Class/) and `[enumeratorAtURL`](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Classes/NSFileManager_Class/#//apple_ref/occ/instm/NSFileManager/enumeratorAtURL:includingPropertiesForKeys:options:errorHandler:). Turns out `Foundation` comes with some pretty useful tools for scripting when it comes to file I/O.

First, we get the URL's for all files in `Pods/` and `Carthage/Checkouts/` which contain the `LICENSE` files for all of our dependencies. Feel free to follow along with the completed script `[acknowledge.swift`](https://gist.github.com/ayanonagon/d87f6c5ca860ccfdbd71). If you are unfamiliar with `guard`, I recommend reading "[Optional?"](http://swift.ayaka.me/posts/2015/10/5/optional) first since `guard` will appear everywhere in this post. 💂🏼

func getLicense(URL: NSURL) throws -> License {

let legalText = try String(contentsOfURL: URL, encoding: NSUTF8StringEncoding)

let pathComponents = URL.pathComponents!

let libraryName = pathComponents[pathComponents.count - 2]

return License(libraryName: libraryName, legalText: legalText)

}

protocol Streamable {

var title: String { get }

var body: String { get }

}

extension Streamable {

var writableString: String {

return "# \\(title)\n\n\\(body)"

}

}

struct License: Streamable {

let libraryName: String

let legalText: String

var title: String {

return libraryName

}

var body: String {

return legalText

}

}

Because `License` conforms to `Streamable` it needs to define a `title` and `body`. Based on this, the `Streamable` protocol provides `writableString` via a protocol extension that formats the License as a nice Markdown string with `title` as a `h1` header style. (Apple has [nice documentation around protocols and protocol extensions](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Protocols.html#//apple_ref/doc/uid/TP40014097-CH25-ID521) if they are new to you!)

This is where things got a little bit interesting. I didn't want to write my own Markdown to HTML converter. (Remember, I'm lazy.) [@hyperspacemark](https://twitter.com/hyperspacemark) found an open-source project called `[Markingbird`](https://github.com/kristopherjohnson/Markingbird) 🐦 that does exactly this. But how do we get `Markingbird` added to our script? My first attempt was to add it as a [Carthage](https://github.com/Carthage/Carthage) dependency so we can `import Markingbird` but I quickly learned that there was no Carthage support for it. (I gave [a talk](https://realm.io/news/swift-scripting/) on using Carthage as a dependency manager for scripting in Swift if you're interested!)

Upon reading the `README` for `Markingbird` more thoroughly, I saw, `the easiest way to use it is to simply copy that file into your own projects.` Knowing that there isn't a simple way to manage multiple files for Swift scripts, I copy-🍝'd the `Markingbird.swift` code, `LICENSE` and all into the top of our script.

And guess what. It looked _horrible_. I could barely tell where the actual script was which the many many lines of `Markingbird.swift` code added. We _had_ to find a way to separate this code out.

After searching around, I found a [Stack Overflow answer](http://stackoverflow.com/a/30537267) that suggested making use of the Unix command `cat`, which con_cat_enates and prints files (type `man cat` into your command line to read the rest of the documentation). 🐱 Using this, we can `cat Markingbird.swift acknowledge.swift` which will print out all of `Markingbird.swift` followed by all of `acknowledge.swift`. We can then take that output and pipe it into `xcrun swift` as below:

The `-` after `swift` means take `stdin` and run that. (If you're curious you can [read more about it](http://unix.stackexchange.com/questions/16357/usage-of-dash-in-place-of-a-filename).)

Anyway, voila! It's a bit weird, but it works and it's very stable since all it does is use basic Unix commands.

#### Breaking News: While I was in the middle of writing this post, [@hyperspacemark](https://twitter.com/hyperspacemark) opened a pull-request to add Carthage support to Markingbird.

That means we can use the [Carthage method](http://stackoverflow.com/a/30537267) to add Markingbird to the script. ✨ In `Cartfile.private` (`.private` because we're not shipping this into our app, check out [the documentation](https://github.com/Carthage/Carthage/blob/master/Documentation/Artifacts.md#cartfileprivate)), we can add `Markingbird` as below:

(Until [this pull request](https://github.com/kristopherjohnson/Markingbird/pull/5) is merged in and a new release is cut, we can point to `venmo/Markingbird` instead of `kristopherjohnson/Markingbird`.)

When you run `carthage bootstrap`, Carthage builds the frameworks and outputs them to `Carthage/Build/iOS` (and/or `Mac`, `watchOS`, `tvOS` depending on what platforms the framework supports). And the `swift` command lets us specify a framework search path with the `-F` option. We can run `acknowledge.swift` with that option like below:

And in `acknowledge.swift`, we can `import Markingbird`.

I don't know about you, but I don't want to type `xcrun swift -F Carthage/Build/Mac acknowledge.swift` all the time. 😪 It's pretty long and it very much defeats the purpose of scripting. The good thing is, we can make it so that we have to only run `./acknowledge.swift` with 2 simple steps:

  1. Run `chmod +x acknowledge.swift` to give it executable permissions.
  2. Put `#!/usr/bin/env xcrun swift -F Carthage/Build/Mac` at the very top of `acknowledge.swift`. This is an [interpreter directive](https://en.wikipedia.org/wiki/Shebang_\(Unix\)) that specifies _how_ to run this file.

Now, all we have to type is `./acknowledge.swift` to run the script. 🎉

But before we do that, let's finish up the script. Our last step is to convert the Markdown to HTML and write it out to a file. We can do this in three lines of code.

You can take a look at the script in all its glory [here](https://gist.github.com/ayanonagon/d87f6c5ca860ccfdbd71). We plan on making this more generic and open-sourcing it properly, so keep an eye out on [github.com/venmo](https://github.com/venmo)! 👀

In our script, we output the generated HTML into our `Resources` directory. Once you add it to the Xcode project once, it'll get updated automatically when you run the script. Unless you also commit your `Pods` and `Carthage` directories (which is fine, just different philosophies), you probably want to put your HTML file into `.gitignore` as well since it's a build product that is generated automatically.

#### Step 5: Load the HTML into a `WKWebView` (or `UIWebView` for < iOS 9) and show it in the app.

At this point we're done talking about things that are specific to scripting, but if you're curious about this web view business, feel free to follow along.

Both `[WKWebView`](https://developer.apple.com/library/ios/documentation/WebKit/Reference/WKWebView_Ref/) and `[UIWebView`](https://developer.apple.com/library/prerelease/ios/documentation/UIKit/Reference/UIWebView_Class/) have a method called `[loadHTMLString(_:baseURL:)`](https://developer.apple.com/library/ios/documentation/WebKit/Reference/WKWebView_Ref/#//apple_ref/occ/instm/WKWebView/loadHTMLString:baseURL:) that lets you load an HTML string directly in the web view. So in our case, we want to load the entire mega HTML string that we generated into this method.

guard

let htmlPath = NSBundle.mainBundle().pathForResource("LICENSES", ofType: "html"),

let html = try? String(contentsOfFile: htmlPath, encoding: NSUTF8StringEncoding)

else {

fatalError("LICENSES.html not found.")

}

let webView = WKWebView(frame: CGRectZero, configuration: WKWebViewConfiguration())

webView.loadHTMLString(html, baseURL: nil)

And that's it! Once you apply some basic CSS to the HTML, you will end up with something like this. (We're still tweaking the CSS to make it look better as well.) Because we hooked in the call to `./acknowledge.swift` to our `Rakefile` to have it get called right after updating any CocoaPods or Carthage dependencies, we never have to worry about about adding/deleting/updating our licenses again. Time to kick back and relax. 😎

![licenses](http://static1.squarespace.com/static/56129a82e4b0147725b391f5/t/563ee5f9e4b093cffcf08618/1446962723522/licenses?format=500w)

That's it for now. This piece goes a little beyond the basics compared to my other step-by-step posts, but I thought it might be fun to start writing a bit about different applications of Swift as well. If you have any questions, please feel free to leave them in the comments below, or tweet at me [@ayanonagon](https://twitter.com/ayanonagon). The biggest reason I'm writing these posts is to get better at explaining concepts and how amazing they are, so any feedback about what was clear vs. not would be much appreciated as well. Also let me know what other topics you want to hear about. Hope you had fun learning, and thanks for reading. 🐣

I'm also incredibly curious what others have been doing for Swift scripting, like what you do for dependency management and what you are automating with the scripts, so please let me know in the comments below! 📩

### References
