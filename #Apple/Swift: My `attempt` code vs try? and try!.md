# Swift: My `attempt` code vs try? and try!

_Captured: 2016-03-15 at 20:20 from [ericasadun.com](http://ericasadun.com/2016/03/15/swift-my-attempt-code-vs-try-and-try/)_

In Swift, the `try?` keyword converts a call that may throw an error into an optional value. It returns a successful value (`.some(T)`) or nil (`.none`). Using `try?` enables you to incorporate throwing code into `guard` statements, allowing you to break the error handler chain and leave scope, and into conditional binding for success-specific clauses.

The merits and costs of `try?` are numerous. It allows you to create more predictable code, especially in completion blocks and playgrounds, but discards errors which are almost always of value to the developer.

A while ago, I created [a version of `try?` that prints](http://ericasadun.com/2015/11/05/implementing-printing-versions-of-try-and-try-on-steroids-in-swiftlang/). It offered a balance between the desire to retain error information and the need to use optional-based control statements.

Over time, I've been tweaking away at this, evolving and refining the idea to get to a point where I could reproduce the overall behavior of both `try?` and its fatal-error sibling `try!` while retaining error-handling features. I call this multi-purposed alternative `attempt`.

My `attempt` function passively picks up context where a throwing statement executes and provides a default printing error-handler. If you set `crashOnError` to `true`, the attempt acts like `try!` and aborts execution, but only after printing the error that caused this and the source location where the problem originated.

The newest component of `attempt` is a custom error handler, the one that defaults to printing. It's a little overkill, but I like the idea that I can customize the behavior as needed. If you just want to add clean-up and then print, you can call the default handler from the custom one.

An `attempt` call looks like this in standalone use, with a trailing closure:
    
    
    attempt {
       let mgr = NSFileManager.defaultManager()
       try mgr.createDirectoryAtPath(
           "/Users/notarealuser",
           withIntermediateDirectories: true,
           attributes: nil)
    }

But requires a more traditional argument approach when combined with `guard` calls that cannot distinguish the trailing closure from their required `else` clause.
    
    
    guard let fileContents = attempt(closure: {
        _ -> [NSURL] in
        let url = NSURL(fileURLWithPath: 
            "/Users/notarealuser")
        return try NSFileManager
            .defaultManager()
            .contentsOfDirectoryAtURL(
                url, 
                includingPropertiesForKeys: nil, 
                options: [])
    }) else { fatalError("failed") }

The code for attempt follows below or you can visit the wider-scoped [CoreError.swift implementation](https://github.com/erica/SwiftUtility/blob/master/Sources/CoreError.swift) on Github, which adds (updated) contextualization utilities as well. The screaming snake case constants will change soon as the [modernized debug identifiers](https://github.com/apple/swift-evolution/blob/master/proposals/0028-modernizing-debug-identifiers.md) are adopted into Swift.

/// consists of filename, line number, error tuple

public typealias CommonErrorHandlerType = (String, Int, ErrorType) -> Void

/// Default error handler prints context and error

public let defaultCommonErrorHandler: CommonErrorHandlerType = {

filePath, lineNumber, error in

let trimmedFileName: String = (filePath as NSString).lastPathComponent

print("Error \\(trimmedFileName):\\(lineNumber) \\(error)")

}

/// Replacement for `try?` that introduces an error handler

/// The default error handler prints an error before returning nil

public func attempt<T>(

file fileName: String = __FILE__,

line lineNumber: Int = __LINE__,

crashOnError: Bool = false,

errorHandler: CommonErrorHandlerType = defaultCommonErrorHandler,

// Thanks, http://twitter.com/Kametrixom/status/709809975447707648

@noescape closure: () throws -> T) -> T? { 

do {

// Return executes only if closure succeeds, returning T

return try closure()

} catch {

// Emulate try! by crashing

if crashOnError {

print("Fatal error \\(fileName):\\(lineNumber): \\(error)")

fatalError()

}

// Execute error handler and return nil

errorHandler(fileName, lineNumber, error)

return nil

}

}

As always, if you find any issues or have any suggestions, please let me know.
