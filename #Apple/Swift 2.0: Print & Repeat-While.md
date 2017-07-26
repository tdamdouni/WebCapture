# Swift 2.0: Print & Repeat-While

_Captured: 2015-10-10 at 22:56 from [ios-blog.co.uk](http://ios-blog.co.uk/swift-tutorials/swift-2-0-print-repeat-while/)_

Like most things that get a version update, there are bound to be some changes and replacements. Swift 2.0 is no different.  
**Print** is now replacing **Println** and the **Repeat-While** loop is now replacing the **Do-While** loop.

### Swift 2.0: Print Replaces Println()

Did you know that print was already in Swift along with **println()**? so why the aggregation? In the first version of Swift, we had the **println()** function. This has now been replaced with the **print()** function. Initially, **println()** would just print a line of text, with a 'newline' character at the end, so each call to **println()** would be on a new line. If you just wanted to print on a single line, you would have used **print()**. Perhaps people didn't use print as much as **println()**? Either way, it was decided to take that function name for the more common **println()** call.

So.. What if you wanted to use the original **print()** in Swift 2.0? It is still there of course, however now it is in a longer format. In Swift 1.2, we had:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    
    print(value: T)  
    
    print(value: T, &target: TargetStream)  
    
    println()  
    
    println(value: T)  
    
    println(value: T, &target: TargetStream)  
    
      
    
    //Swift 1.2
    
    
    

Now, Swift 2.0 is written like this:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    
    print(value: T)  
    
    print(value: T, &target: TargetStream)  
    
    print(value: T, &target: TargetStream, appendNewline: Bool)  
    
    print(value: T, appendNewline: Bool)  
    
      
    
    //Swift 2
    
    
    

That is pretty neat huh? We have managed to condense 6 lines (functions) into just 4.

What is that: **TargetStream**? Well.. this option lets you print the output elsewhere. Currently, the only option I can see in the standard library is to have it outputted into another string, making the String a sort of buffer. For most situations however, you will probably be using just **print(value: T)** or **print(value: T, appendNewLine: Bool)**.

So.. What If you wanted a line that automatically ended with the newline character? Then you would use:
    
    
    1  
    
    print("text with newline")
    
    
    

What's that? You don't want to have the newline character, do not fret. We can just use:
    
    
    1  
    2  
    3  
    
    print("When I am outputted, I ", appendNewline: false)  
    
    print("Will be on the same line, ", appendNewline: false)  
    
    print("Swift 2.0 is neat right.", appendNewline: false)
    
    
    

It may be something small, but I think that it is a significant change. If nothing else, your tests or debugging code that use **println()** will need to be updated.

### Swift 2.0: Repeat-While

For those of you who use other languages, this loop might make you think that Swift 2.0 has brought in a completely new and radical way of looping right? I mean apple are good at that. But do not worry, Apple just decided to take the keyword 'do', and put it in their brand new Error Handling framework. Which kind of leaves the classic do-while loop in a bit of a bind. So, they decided to rename it and avoid the conflicts, this was not only to use it elsewhere, but to make their intention a little clearer. Some while/do-while loops can be quite large. With a while loop, that isn't so bad, because you can tell right at the top that it is a while loop, and it will keep running until a certain condition.

With the original do-while loop, it is a bit less clear. You will see a very small **do** at the top of a code block, then all of the code, and all the way down at the bottom you will see the **While** conditional. The idea behind it is basically to say: Do {this big block of code} while (this conditional is true). A good piece of advice is that if written down the line makes sense, then its usually a good start, and as you can see this makes sense, but the main point of loops is usually to repeat things.

Now, that sentence says: Repeat {this large block of code} while (my condition is true). Saying repeat also makes it very clear that this will be repeated if the while statement condition part remains true. They also changed this to make it obvious to us humans that area reading the boggling Swift 2.0 code. The word repeat not only implies repetition but it is literally longer than the word do and when you are scanning quickly through large pieces of code, stress, frustrated or lost it's going to stand out a lot easier. Agree?

Essentially the **Swift 2.0 Repeat-While** loop is the same as the do-while loop prior to its evolution. It is a while loop that will always run the block of code once, and then check the conditional. This is as opposed to a normal 'while' loop, that checks the conditional statement first and if it does not result in true, then the block of code will be skipped entirely.

Anyway, lets see it in action:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    
    var count = 0  
    
       
    
    repeat {  
    
        print("Swift 2.0 is da bomb!")  
    
        count++  
    
    } while count <= 15
    
    
    

That concludes this quick introduction for Swift 2.0 Repeat-While and Print - What do you think? Easier? Let me know in the comments or through social media.

### Problems?

We have a new Questions and Answers section so you can get help from the awesome community.

[Ask a Question](http://ios-blog.co.uk/questions/)

### Enjoyed this post?

Subscribe to our [RSS Feed](http://feeds.feedburner.com/iosdevblog) or [Follow us on twitter](http://twitter.com/ios_blog) to keep up to date with the latest from iOS-Blog. Remember, Sharing is caring so please click one of the following options:
