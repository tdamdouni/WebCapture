# Lightweight reactive coding with Swift & VinceRP

_Captured: 2015-11-19 at 20:30 from [blog.alltheflow.com](https://blog.alltheflow.com/lightweight-reactive-coding-with-swift-and-vincerp/)_

In case you are wondering why this blog is all about reactive, it's just the fact that I'm searching for the best possible way to write code. You are probably ahead of me if you already feel comfy with your current setup - if that's the case please share your story. If you are still looking for the right one, read on to check out my latest discovery.

## ReactiveCocoa

As you've probably seen in [my previous posts](https://blog.alltheflow.com/tag/reactive/) I started my journey at Objective-C and [ReactiveCocoa](https://github.com/ReactiveCocoa/ReactiveCocoa) after I joined my team a year ago. I was amazed by the power of ReactiveCocoa and the experience of our new way of coding. I learned every single operator, every kind of signal's every possible behavior through using them. It took a lot of time, but in the end I had the well-deserved feeling of **wow-I-can-write-reactive-code**. As soon as I started to use it with Swift it turned out it's still the great silver bullet if you are looking for one.

Although this time I'm looking for something simpler, I just want to write a showcase app. Should I drop my favorite framework now and start coding imperative again? I was wondering if there's anything I can just pull in and write this simple app without blowing everyones brains off with signals.

## VinceRP

So my friend and teammate [@bvic23](https://twitter.com/bvic23) wrote this reactive [framework called VinceRP](https://github.com/bvic23/VinceRP/) named after his little son (how lovely is that?). I'm aware that he secretly developed a lot of passion for Scala in the past years, that's the reason why he tried to reform its advantages with our shiny new Swift's amazing features like type inference, generics and operator overloading.

I thought it'd be the best time for giving it a try!

## Pasteflow

My idea was to create [a Mac app](https://github.com/alltheflow/pasteflow) which is a real time feed of my pasteboard including text (code), images, URLs with the corresponding graphical representation as the content of the feed. I know there are some apps for the base functionality already, but I missed the visuals, the infinite database and the search feature I'm planning to implement so I started out and hope to finish some weekends later.

It's powered by ❤, Swift, reactive & functional approaches - as much as I use at least.

If you're interested in `VinceRP` check out the [basic example](https://github.com/bvic23/VinceRP/tree/master/examples/BasicExample/BasicExample) of using the framework, but here's also a sneak peek from my app:

### Reactive variables

Just a reactive `Array` of any type. The type of the reactive values will be determined based on the initial value. It's necessary to provide and it can't be optional, [yet](https://github.com/bvic23/VinceRP/issues/16).
    
    
    let pasteboardItems = reactive([AnyObject]())  
    

### UIKit/AppKit bindings

Binding UI elements to the reactive variable's values:
    
    
    countLabel.reactiveText = pasteboardItems.map { ("\($0.count) items") }
    

Or hiding if there's no item available:
    
    
    countLabel.reactiveHidden = definedAs {  
        self.pasteboardService.changeCount* == 0
    }
    

Where `*` is just a shortcut for `value()`.

### Observation

Propagate changes and updating the UI accordingly:
    
    
    pasteboardService.pasteboardItems.onChange { _ in  
        self.collectionView.reloadData() 
    }
    

### Putting values

Push values manually into the `reactive` variable if some shiny new AppKit classes property is not KVO compliant for example.

![NSPasteboard docs](https://blog.alltheflow.com/content/images/2015/11/Screen-Shot-2015-11-17-at-11-23-55.png)

> _NSPasteboard docs_

Updating the values manually:
    
    
    self.pasteboardItems <- self.pasteboardItems*.arrayByAppending(item)  
    

### Dispatch

To be on the safe side, you can [dispatch on your favorite queue](https://github.com/bvic23/VinceRP/blob/f6d2268dc091071c2b6a913227867a5eb7e1fbc5/VinceRP/Threading/Dispatchable.swift#L10).
    
    
    pasteboardService.pasteboardItems.dispatchOnMainQueue().onChange { _in  
        self.collectionView.reloadData() 
    }
    

## About & more

If you are wondering what's the magic behind `VinceRP`, check out its [GitHub page](https://github.com/bvic23/VinceRP/), or find [Viktor on Twitter](https://blog.alltheflow.com/lightweight-reactive-coding-with-swift-and-vincerp/\(https://twitter.com/bvic23\)).
