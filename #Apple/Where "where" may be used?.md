# Where "where" may be used?

_Captured: 2015-11-19 at 19:55 from [blog.krzyzanowskim.com](http://blog.krzyzanowskim.com/2015/11/13/where-where-may-be-used/)_

This is by far the most faved/retweeted [Swift](https://developer.apple.com/swift/) tip of mine lately:

> don't forget you can do this 🎉 in Swift [#swiftlang](https://twitter.com/hashtag/swiftlang?src=hash) [pic.twitter.com/izVlfcqOYv](https://t.co/izVlfcqOYv)
> 
> -- Marcin Krzyzanowski (@krzyzanowskim) [November 10, 2015](https://twitter.com/krzyzanowskim/status/664130236506841088)

indeed cool, unexpected and forgettable feature of Swift pattern-matching.

The fact is you can use `where` keyword in a case label of a `switch` statement, a `catch` clause of a do statement, or in the case condition of an `if`, `while`, `guard`, `for-in` statement, or to define type constraints.

### for-in
    
    
    let arr = [1,2,3,4]  
    let dict = [1:"one", 2:"two"]
    
    for num in array where dict[num] != nil {  
        // 1, 2
    }
    

### do-catch
    
    
    enum ResponseError: ErrorType {  
        case HTTP(Int)
    }
    
    func errorProne() throws {  
        throw ResponseError.HTTP(404)
    }
    
    do {  
        try errorProne()
    } catch ResponseError.HTTP(let code) where code >= 400 && code % 2 == 0 {
        print("Bad Request") // match
    } catch ResponseError.HTTP(let code) where code >= 500 && code < 600  {
        print("Internal Server Error")
    }
    

### while
    
    
    var mutableArray:[Int]? = []  
    while let arr = mutableArray where arr.count < 5 {  
        mutableArray?.append(0) // [0,0,0,0,0]
    }
    

### if
    
    
    let string:String? = "checkmate"
    
    if let str = string where str == "checkmate" {  
        print("game over") // match
    } else {
        print("let's play")
    }
    

### guard
    
    
    let string:String? = "checkmate"
    
    guard let str = string where str != "checkmate" else {  
        fatalError("game over") // match
    }
    print("let's play")  
    

### switch-case
    
    
    var value = (1,2)  
    switch value {  
        case let (x, y) where x == 1:
            // match 1
        break
        case let (x, y) where x / 5 == 1:
            // not-match
        break
        default:
        break
    }
    

### type constraint
    
    
    func genericFunction<S where S: StringLiteralConvertible>(string: S) {  
        print(string)
    }
    
    genericFunction("lambada")  
    

pity though, `where keyword` is not really described in details by the "The Swift Programming Language` book.

![](http://blog.krzyzanowskim.com/content/images/2015/11/Screen-Shot-2015-11-13-at-12-28-47.png)

anyway... now it's clear. [Gist code is here](https://gist.github.com/krzyzanowskim/cfdc1990b8988469decf).

# Conclusion

Of course `where` is part of control flow of [Swift](https://developer.apple.com/swift/) program and may be used almost everywhere.
