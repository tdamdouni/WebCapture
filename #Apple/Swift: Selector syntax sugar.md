# Swift: Selector syntax sugar

_Captured: 2016-03-23 at 21:45 from [medium.com](https://medium.com/swift-programming/swift-selector-syntax-sugar-81c8a8b10df3#.5ojme38vi)_

![](https://cdn-images-1.medium.com/max/2000/1*L100yxVCNnyvn7Q5m8CCiQ.jpeg)

#### Objective-C developers be jelly

Objective-C has been around for several years, and during that time developers been crafting their code style to make it nice and readable for following generations to benefit. But not Swift, Swift is new. There's not really a single or most common style to conform with, so a lot of us have had to forge our own way with experimentation.

Over the past 12 months I've been fortunate enough to work with Swift for about 98.2% of my working week. During that time I've learnt to craft some (in my opinion) really nice code styles, which I'll share part of with you today.

#### Selectors

Before Swift 2.2, selectors were string literals and prone to error because we, as humans invented, and still contribute to typos whenever given the chance to write something without autocomplete.
    
    
    let button = UIButton(type: .System)
    
    
    button.addTarget(self, action: **Selector(“buttonTapped:”)**, forControlEvents: .TouchUpInside)
    
    
    func buttonTapped(sender: UIButton) { }

One good naming convention for your function calls should be the objects object name plus action. In this case we had our **_button_** object **_tapped_**, **_buttonTapped: _**. Also remember to always pass in the sender and the correct type as the first and only argument, because it's better to have it and not need it, than to need it and not have it.

A few other examples of how I like to name corresponding user interaction functions:
    
    
    func segmentedControlValueChanged(sender: UISegmentedControl) { }
    
    
    func barButtonItemTapped(sender: UIBarButtonItem) { }
    
    
    func keyboardWillShowNotification(notification: NSNotification) { }

#### Improvements in Swift 2.2

However, our selectors are now much safer in Swift 2.2, but it's still   
U-G-L-Y (It ain't got no alibi). And to have all these selectors littered throughout your codebase makes the matter worse. What if you have Massive View Controller? What if you use the same selector multiple times?
    
    
    button.addTarget(self, action: **#selector(ViewController.buttonTapped(_:))**, forControlEvents: .TouchUpInside)

This line is seriously way too long and kind of hard to read if you're just scanning through. Imagine writing/copy-pasting that several times. Let's tidy it up by placing all the selectors in _one_ spot, where we can reference and edit them in a uniform matter.
    
    
    private struct Action {
    
    
     static let buttonTapped =   
     **#selector(ViewController.buttonTapped(_:))**
    
    
    button.addTarget(self, action: **Action.buttonTapped**,   
     forControlEvents: .TouchUpInside)

Awesome. Now we have one spot to put all our selectors in, and each object that wants to use that selector, gets it's value from a static constant inside the **_Action_** struct. We have to use the name Action because it's the next best thing to Selector, Selector is taken by the Selector class, obviously.

Another wise thing to do is to use the same names for the static constant and functions, this will help you remember and maintain uniformity.

It's **_private_** because we don't want Xcode presenting us with "redeclaration conflict" errors, so this struct is _only_ available to _this_ specific **_.swift_** file.

I had actually been using this for quite a few months now, and it has served me well for that time. But this morning I realised I could take this even farther, and make it more …sugary. Why make an Action struct when we can make a Selector **_extension_**?
    
    
    private **extension Selector** {
    
    
     static let buttonTapped =   
     #selector(ViewController.buttonTapped(_:))
    
    
    button.addTarget(self, action: **.buttonTapped**,   
     forControlEvents: .TouchUpInside)

Omg, right? We've made an **_extension_** to **_Selector_** which contains a static constant of the selector we want to use to call the method in our class.

We've taken advantage of Swift's type inference too. Because this method is expecting a **_Selector_ **object for the **_action:_** argument, we can omit the **_Selector. _**prefix completely when passing in a value.

It's just like when you omit **_UIColor. _**prefixfor setting a color to a view:
    
    
    view.backgroundColor = .blackColor()

Anyways, hope you liked this quick post about Selector syntax sugar. If you decide to use it in your code, please send me a [tweet](https://twitter.com/AndyyHope). Would love to hear if other people are adopting this approach.
