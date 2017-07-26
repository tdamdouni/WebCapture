# Writing Xcode plugin in Swift

_Captured: 2015-12-11 at 01:38 from [merowing.info](http://merowing.info/2015/12/writing-xcode-plugin-in-swift/)_

![](http://merowing.info/2015/12/logs.gif)

I've found myself using Xcode a lot more than I did in Objective-C.

One of things I've missed a lot from my [AppCode](https://www.jetbrains.com/objc/) setup, is the ability to jump to specific file & line that logged a console message.

Because Xcode doesn't offer such functionality and because I do not like to complain, I've decided to write my own plugin for it.

I wrote it in Swift.

## Idea

If a console logs a **fileName.extension:XX** that name turns into a clickable hyperlink that will open the specific file and highlight the line.

That way you can either use your own logging mechanism and just add this simple prefix, e.g.
    
    
    func logMessage(message: String, filename: String = __FILE__, line: Int = __LINE__, funct: String = __FUNCTION__) {
        print("\((filename as NSString).lastPathComponent):\(line) \(funct):\r\(message)")
    }
    

or if you use [CocoaLumberjack](https://github.com/CocoaLumberjack/CocoaLumberjack) you can use my custom formatter for some really nice logs.

Swift version (Objective-C version is part of [KZBootstrap](https://github.com/krzysztofzablocki/KZBootstrap)):
    
    
    import Foundation
    import CocoaLumberjack.DDDispatchQueueLogFormatter
    
    class KZFormatter: DDDispatchQueueLogFormatter {
    
      lazy var formatter: NSDateFormatter = {
          let dateFormatter = NSDateFormatter()
          dateFormatter.formatterBehavior = .Behavior10_4
          dateFormatter.dateFormat = "HH:mm:ss.SSS"
          return dateFormatter
      }()
    
      override func formatLogMessage(logMessage: DDLogMessage!) -> String {
          let dateAndTime = formatter.stringFromDate(logMessage.timestamp)
    
          var logLevel: String
          let logFlag = logMessage.flag
          if logFlag.contains(.Error) {
              logLevel = "ERR"
          } else if logFlag.contains(.Warning){
              logLevel = "WRN"
          } else if logFlag.contains(.Info) {
              logLevel = "INF"
          } else if logFlag.contains(.Debug) {
              logLevel = "DBG"
          } else if logFlag.contains(.Verbose) {
              logLevel = "VRB"
          } else {
              logLevel = "???"
          }
    
          let formattedLog = "\(dateAndTime) |\(logLevel)| \((logMessage.file as NSString).lastPathComponent):\(logMessage.line): ( \(logMessage.function) ): \(logMessage.message)"
          return formattedLog;
      }
    }
    

## Implementation - selected bites

There are 2 action points we need in order to implement those requirements:

  1. Console NSTextStorage fixAttributesInRange - so that we can change attributes whenever we find our log regular expression.
  2. NSTextView mouseDown - so that when a mouse is clicked in console and it's under our attributed links we can force xcode to open the file and highlight our line.

### How do we inject our functionality into those actions?

Simple Swizzling:
    
    
    static func swizzleMethods() {
      let original = class_getInstanceMethod(NSClassFromString("NSTextStorage"), Selector("fixAttributesInRange:"))
      method_exchangeImplementations(original, class_getInstanceMethod(NSClassFromString("NSTextStorage"), Selector("kz_fixAttributesInRange:")))
    
      let original2 = class_getInstanceMethod(NSClassFromString("NSTextView"), Selector("mouseDown:"))
      method_exchangeImplementations(original2, class_getInstanceMethod(NSClassFromString("NSTextView"), Selector("kz_mouseDown:")))
    }
    

### How do we determine if a NSTextStorage is actually the console one?

We can observe **IDEControlGroupDidChangeNotification**, find IDEConsoleTextView and use associated objects to mark that storage as Console one, which will come in handy later on.
    
    
    guard let consoleTextView = KZPluginHelper.consoleTextView(),
    let textStorage = consoleTextView.valueForKey("textStorage") as? NSTextStorage else {
        return
    }
    textStorage.kz_isUsedInXcodeConsole = true
    

### How can we find the path of a file, while only having relative path in the logs?

We can use shell **find** command, this is how you can run and retrieve response from a shell command in Swift:
    
    
    static func runShellCommand(command: String) -> String? {
      let pipe = NSPipe()
      let task = NSTask()
      task.launchPath = "/bin/sh"
      task.arguments = ["-c", String(format: "%@", command)]
      task.standardOutput = pipe
      let file = pipe.fileHandleForReading
      task.launch()
      guard let result = NSString(data: file.readDataToEndOfFile(), encoding: NSUTF8StringEncoding)?.stringByTrimmingCharactersInSet(NSCharacterSet.newlineCharacterSet()) else {
          return nil
      }
      return result as String
    }
    

### Injecting links into logs

  * Use pattern matching to find occurrences of our logs.
  * Use shell find command to retrieve fullPath in our workspace.
  * Add custom attributes to store that information in the string itself.
    
    
    private func injectLinksIntoLogs() {
        let text = string as NSString
        guard let path = KZPluginHelper.workspacePath() else {
            return
        }
        let matches = pattern.matchesInString(string, options: .ReportProgress, range: editedRange)
        for result in matches where result.numberOfRanges == 4 {
            let fullRange = result.rangeAtIndex(0)
            let fileNameRange = result.rangeAtIndex(1)
            let extensionRange = result.rangeAtIndex(2)
            let lineRange = result.rangeAtIndex(3)
            guard let result = KZPluginHelper.runShellCommand("find \"\(path)\" -name \"\(text.substringWithRange(fileNameRange)).\(text.substringWithRange(extensionRange))\" | head -n 1") else {
                continue
            }
            addAttribute(NSLinkAttributeName, value: "", range: fullRange)
            addAttribute(KZLinkedConsole.Strings.linkedPath, value: result, range: fullRange)
            addAttribute(KZLinkedConsole.Strings.linkedLine, value: text.substringWithRange(lineRange), range: fullRange)
            addAttribute(NSBackgroundColorAttributeName, value: NSColor.whiteColor(), range: fullRange)
        }
    }
    

### Opening file and scrolling to specific line

Opening a file is as simple as calling
    
    
    public func application(sender: NSApplication, openFile filename: String) -> Bool
    

Scrolling to specific line requires a little bit more code:
    
    
    private func scrollTextView(textView: NSTextView, toLine line: Int) {
        guard let text = (textView.string as NSString?) else {
            return
        }
        
        var currentLine = 1
        var index = 0
        for (; index < text.length; currentLine++) {
            let lineRange = text.lineRangeForRange(NSMakeRange(index, 0))
            index = NSMaxRange(lineRange)
            
            if currentLine == line {
                textView.scrollRangeToVisible(lineRange)
                textView.setSelectedRange(lineRange)
                break
            }
        }
    }
    

It's much easier to deal with NSString than String here, otherwise I'd have to introduce conversion from/to Range.

### Attribution

Writing this was much simpler because I was able to look at other people plugins, mostly those related to console, without them being open sourcing it would be more work to figure this stuff out with hopper.

### Installation

Either use Alcatraz and search for **KZLinkedConsole** or you can just [build the project](https://github.com/krzysztofzablocki/KZLinkedConsole) and it will install automatically.

### Conclusion

This is my first attempt at writing an Xcode plugin, and I must say it's interesting to debug Xcode while working in Xcode…

I personally find this plugin very helpful as we often have lots of logs and being able to jump straight to line that logged an error is great time saver.

Be sure to check out the source code on GitHub, as it's interesting to use Swift while dealing with private API's. Using KVC makes it simpler to retrieve values without having to introduce Objective-C binding.

If you are using cmd+shift+f you are **probably doing something wrong**.
