# Semicolons in JavaScript are optional

_Captured: 2016-06-19 at 20:22 from [mislav.net](http://mislav.net/2010/05/semicolons/)_

JavaScript is a scripting language where semicolons as statement terminators are _optional_, as in:

> **op*tion*al** (_adjective_)  
Available to be chosen but not obligatory

However, there is a lot of FUD (fear, uncertainty, and doubt) around this feature and, as a result, most developers in our community [will recommend always including semicolons](http://stackoverflow.com/questions/444080/do-you-recommend-using-semicolons-after-every-statement-in-javascript), just to be safe.

Safe from _what?_ I've been searching for reasons programmers have to force semicolons on themselves. Here's what I generally found:

## Spec is cryptic and JavaScript implementations differ

[Rules for automatic semicolon insertion](http://bclary.com/2004/11/07/#a-7.9) are right here and are, while somewhat difficult to comprehend by a casual reader, quite explicitly laid out. As for JavaScript implementations where interpretation of these rules _differs_, well, I've yet to find one. When I ask developers about this, or find archived discussions, typically they are yeah, there's this browser where this is utterly broken, I simply forgot which. Of course, they never remember.

I write semicolon-less code and, in my experience, there isn't a JavaScript interpreter that can't handle it.

## You can't minify JavaScript code without semicolons

There are 3 levels of reducing size of JavaScript source files: _compression_ (e.g. gzip), _minification_ (i.e. removing unnecessary whitespace and comments) and _obfuscation_ (changing code, shortening variable and function names).

Compression like gzip is the easiest; it only requires one-time server configuration, doesn't need extra effort by developers and _doesn't change_ your code. There was a time when IE6 couldn't handle it, but if I remember correctly it was patched years ago and pushed as a Windows update, and today nobody really cares anymore.

Minification and obfuscation _change your code_. They are tools which you run on your source code saying "here are some JavaScript files, try to make them smaller, but **don't change functionality**". I'm reluctant to use these tools because many developers report that if I don't use specific coding styles, like writing semicolons, they will break my code. I'm OK with people (community) forcing certain coding styles on me, but not tools.

Suppose I have code that works in every JavaScript implementation that I target (major browsers and some server-side implementations). If I run it through your minification tool and that tools _breaks_ my code, then I'm sad to report that your tool is _broken_. If this tool edits JavaScript code, it'd better understand it as a real interpreter would.

While on the topic of minification, let's do a reality check. I took the jQuery source and [removed all semicolons](http://github.com/mislav/jquery/commit/4a2faf8987fc3fcb8aefc99def5b5ed2b4de190c), then ran it through [Google Closure Compiler](http://code.google.com/closure/compiler/). Resulting size was 76,673 bytes. The size of original "jquery.min.js" was 76,674 (1 byte more). So you see, there was almost no change; and of course, its test suite passed as before.

How is that possible? Well, consider this code:
    
    
    var a=1
    var b=2
    var c=3

That's 24 bytes right there. Stamp semicolons everywhere and run it through a minifier:
    
    
    var a=1;var b=2;var c=3;

Still 24 bytes. So, adding semicolons and removing newlines saved us a whopping zero bytes right there. Radical. Most size reduction after minification isn't gained by removing newline characters -- it's thanks to removing code comments and leading indentation.

**Update:** a lot of people have pointed out that their minifiers _rewrite_ this expression as `var a=1,b=2,c=3`. I know that some tools do this, but the point of this article is just to explore how semicolons relate to whitespace. If a minifier is capable of rewriting expressions (e.g. Closure Compiler) it means that it can also insert semicolons automatically.

Also, some people recommend forcing yourself do use curly braces for blocks, even if they're only one line:
    
    
    // before
    if(condition) stuff()
    
    // after
    if(condition){
      stuff()
    }
    
    // after minification
    if(condition){stuff()}

Enforced curly braces add at least a byte to our expression, even after minification. I'm not sure what the benefit is here--it's not size and it's not readability, either.

Here are some other whitespace-sensitive languages that you might have heard about:

  * Ruby -- messing with spaces in expressions with operators and method calls can break the code
  * Python -- duh.
  * HTML -- see notes about [Kangax's HTML minifier](http://perfectionkills.com/experimenting-with-html-minifier/)

Of course, there's no need for minification on the server-side. I made this list for the sake of the following argument: Whitespace can, and often is, part of the (markup) language. It's not necessarily a bad thing.

## It's good coding style

Also heard as:

  * It's good to have them for the sake of consistency

This is another way of expressing the "everybody else is doing it" notion and is used by people during online discussion in the (rather common) case of a lack of arguments.

My advice on JSLint: don't use it. Why would you use it? If you believed that it helps you have less bugs in your code, here's a newsflash; only people can detect and solve software bugs, not tools. So instead of tools, get more people to look at your code.

Douglas Crockford also says "four spaces", and yet most popular JavaScript libraries are set in either tabs or two spaces. Communities around different projects are _different_, and that's just how it should be. As I've said before: let _people_ and yourself shape your coding style, not some single person or tool.

You might notice that in this article I'm not telling you _should_ be semicolon-free. I'm just laying out concrete evidence that you _can_ be. The choice should always be yours.

As for _coding styles_, they exist so code is more readable and easier to understand for a group of people in charge of working on it. Think deeply if semicolons actually improve the readability of your code. What improves it the most is whitespace--indentation, empty lines to separate blocks, spaces to pad out expressions, and good variable and function naming.

## Semicolon insertion bites back in return statements

When I searched for "JavaScript semicolon insertion", here is the problem most blog posts described:
    
    
    function add() {
      var a = 1, b = 2
      return
        a + b
    }

When you're done trying to wrap your brain around why would anyone in their right mind want to write a return statement on a new line, we can continue and see how this statement is interpreted:
    
    
    return;
      a + b;

Alas, the function didn't return the sum we wanted! But you know what? This problem _isn't_ solved by adding a semicolon to the end of our wanted `return` expression (that is, after `a + b`). It's solved by _removing_ the newline after `return`:
    
    
    return a + b

Still, in an incredible display of ignorance these people actually _advise_ their readers to avoid such issues by adding semicolons everywhere. Uh, alright, only it doesn't help this particular case at all. We just needed to understand better how the language is parsed.

## The only real pitfall when coding without semicolons

Here is the only thing you have to be aware if you choose to code semicolon-less:
    
    
    // careful: will break
    a = b + c
    (d + e).print()

This is actually evaluated as:
    
    
    a = b + c(d + e).print();

This example is taken from an [article about JavaScript 2.0 future compatibility](http://www.mozilla.org/js/language/js20-2000-07/rationale/syntax.html), but I've ran across this in my own programs several times while using [the module pattern](http://www.yuiblog.com/blog/2007/06/12/module-pattern/).

Easy solution: when a line starts with parenthesis, prepend a semicolon to it.
    
    
    ;(d + e).print()

This might not be elegant, but does the job. [Michaeljohn Clement elaborates on this](http://inimino.org/~inimino/blog/javascript_semicolons) even further:

> If you choose to omit semicolons where possible, my advice is to insert them immediately before the opening parenthesis or square bracket in any statement that begins with one of those tokens, or any which begins with one of the arithmetic operator tokens `/`, `+`, or `-` if you should happen to write such a statement.

Adopt this advice as a rule and you'll be fine.
