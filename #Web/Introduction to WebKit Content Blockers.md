# Introduction to WebKit Content Blockers

_Captured: 2015-06-24 at 21:59 from [www.webkit.org](https://www.webkit.org/blog/3476/content-blockers-first-look/)_

Browser extensions have been a big part of modern browsers for a while now. With extensions, everyone can change their browser to their preferences.

Today, there are several models to extend browsers. Most extensions are written in JavaScript and loaded by the browser, following a model introduced by Mozilla over a decade ago. That model is also used with WebKit. It is the classical way to write extensions for OS X Safari, Web/Epiphany, and other browsers.

On OS X and iOS, there is also the concept of [App Extensions](https://developer.apple.com/app-extensions/) with a different approach to security and performance. They are essentially little sandboxed applications that are launched on demand to extend some specific piece of functionality, known as an extension point.

The JavaScript extensions model has been great for many use cases, but there is one category of extensions where members of the WebKit project felt we should do better: the content blocking extensions. Such extensions are the most popular kind; they let users decide what should load and not load, who can track them, what should be visible on pages, etc.

The reason we are unhappy about the JavaScript-based content blocking extensions is they have significant performance drawbacks. The current model uses a lot of energy, reducing battery life, and increases page load time by adding latency for each resource. Certain kinds of extensions also reduce the runtime performance of webpages. Sometimes, they can allocate tremendous amounts of memory, which goes against our efforts to reduce WebKit's memory footprint.

It is an area were we want to do better. We are working on new tools to enable content blocking at a fraction of the cost.

One new feature, we are developing allows describing content blocking rules in a structured format ahead-of-time, declaratively, rather than running extension-provided code at the moment a decision about blocking needs to be made. This model allows for WebKit to compile the ruleset into a format that's very efficient to apply to loads and page content.

## Content blockers in action

Before I dive into the details, let's see what a declarative extension look like in the new format.

In essence, each content blocker extension is a list of rules that tells the engine how to act when loading a resource.

The rules are written in JSON format. For example, here is an extension with two rules:
    
    
        [
            {
                "trigger": {
                    "url-filter": "evil-tracker.js"
                },
                "action": {
                    "type": "block"
                }
            },
            {
                "trigger": {
                    "url-filter": ".*",
                    "resource-type": ["image", "style-sheet"]
                    "unless-domain": ["reputable-content-server.com"]
                },
                "action": {
                    "type": "block-cookies"
                }
            }
        ]
    
    

The first rule activates for any URL that contains the string "evil-tracker.js". When the first rule is activated, the load is blocked.

The second rule activates for any resource loaded as an image or a style sheet on any domain except "reputable-content-server.com". When the rule is activated, cookies are stripped from the request before sending it to the server.

The rules are passed to the engine by the browser. In iOS Safari, it is done through the native app extension mechanism. In OS X Safari, browser extensions can provide their rules through a new API. If you hack on WebKit, MiniBrowser also lets you load rule sets directly from the Debug menu.

Once the rules are passed to WebKit, they are compiled into an efficient bytecode format. The engine then executes this bytecode for each resource request, and uses the result to modify the request or inject CSS.

The bytecode is executed for each resource in the network subsystem. The goal is to reduce the latency between a request being created by the page and the request being actually dispatched over the network.

## Content blocker format

The content blocker rules are passed in JSON format. The top level object is an array containing every rule that needs to be loaded.

Each rule of the content blocker is a dictionary with two parts: a trigger which activates the rule, and an action defining what to do when the rule is activated.

A typical rule set looks like this:
    
    
        [
            {
                "trigger": {
                    …
                },
                "action": {
                    …
                }
            },
            {
                "trigger": {
                    …
                },
                "action": {
                    …
                }
            }
        ]
    
    

The order of the rules is important. For every extension, the actions are applied in order. There is an action that skip all the rules that appears before the current one: "ignore-previous-rules".

Let's dive into the "trigger" and "action" objects.

### Trigger definition

The "trigger" defines what properties activate a rule. When the rule is activated, its action is queued for execution. When all the triggers have been evaluated, the actions are applied in order.

Currently, the triggers are based on resource load information: the url and type of each resource, the domain of the document, and the relation of the resource to the document.

The valid fields in the trigger are:

  * "url-filter" (string, mandatory): matches the resource's URL.
  * "url-filter-is-case-sensitive": (boolean, optional): changes the "url-filter" case-sensitivity.
  * "resource-type": (array of strings, optional): matches how the resource will be used.
  * "load-type": (array of strings, optional): matches the relation to the main resource.
  * "if-domain"/"unless-domain" (array of strings, optional): matches the domain of the document.

The most important field, and the only mandatory one, is "url-filter". In this field, you define a regular expression that will be evaluated against the URL of each resource. It is possible to match every URL by matching every character (e.g. ".*") but in general it is better to be as precise as possible to avoid unforeseen side effects.

The syntax of the regular expression is a strict subset of JavaScript regular expressions. It is introduced later in this post.

It is possible to change the case-sensitivity of "url-filter" with the field "url-filter-is-case-sensitive". By default, the matching is case-insensitive.

The optional field "resource-type" specifies the type of load to match. The content of this field is an array with all the types of load that can activate the trigger. The possible values are:

  * "document"
  * "image"
  * "style-sheet"
  * "script"
  * "font"
  * "raw" (any untyped load, like XMLHttpRequest)
  * "svg-document"
  * "media"
  * "popup"

Since the triggers are evaluated before the load starts, these types defines how the engine intends to use the resource, not necessarily the type of the resource itself (for example, <img src="something.css"> is identified as an image.)

If "resource-type" is not specified, the default is to match all types of resources.

The field "load-type" defines the relation between the domain of the resource being loaded and the domain of the document. The two possible values are:

  * "first-party"
  * "third-party"

A "first-party" load is any load where the URL has the same security origin as the document. Every other case is "third-party".

Finally, it is possible to make a trigger conditional on the URL of the main document. In this case, the rule only applies for a particular domain, or only outside of a particular domain.

The domain filters are "if-domain" and "unless-domain", those fields are exclusive. In those fields, you can provide a domain filter for the main document.

It is important to be careful with the trigger to avoid rules being unexpectedly activated. Since it is impossible to test the entire web to validate a trigger, it is advised to be as specific as possible.

### Action definition

The "action" part of the dictionary defines what the engine should do when a resource is matched by a trigger.

Currently, the action object has only 2 valid fields:

  * "type" (string, mandatory): defines what to do when the rule is activated.
  * "selector" (string, mandatory for the "css-display-none" type): defines a selector list to apply on the page.

There are 3 types of actions that limit resources: "block", "block-cookies", "css-display-none". There is an additional type that does not have any impact on the resource but changes how the content extension behaves: "ignore-previous-rules".

The action "block" is the most powerful one. It tells the engine to abort loading the resource. If the resource was cached, the cache is ignored and the load will still fail.

The action "block-cookies" changes the way the resource is requested over the network. Before sending the request to the server, all cookies are stripped from the header. Safari has its own privacy policy that applies on top of this rule. It is only possible to block cookies that would otherwise be accepted by the privacy policy, combining "block-cookies" and "ignore-previous-rules" still follows the browser's privacy settings.

The action "css-display-none" acts on the CSS subsystem. It lets you hide elements of the page based on selectors. When this action is set, there should be a second entry named "selector" containing a selector list. Any element matching the selector list has its "display" property set to "none" which hides it.

Every selector supported by WebKit is supported for content extensions, including compound selectors and the new selectors from [CSS Selectors Level 4](http://dev.w3.org/csswg/selectors-4/). For example, the following action definition is valid:
    
    
        "action": {
            "type": "css-display-none",
            "selector": "#newsletter, :matches(.main-page, .article) .annoying-overlay"
        }
    

Finally, there is the action type "ignore-previous-rules". All it does is ignore every rule before the current one if the trigger is activated. Note that it is not possible to ignore the rules of an other extension. Each extension is isolated from the others.

## The Regular expression format

Triggers support filtering the URLs of each resource based on regular expression.

All strings in "url-filter" are interpreted as regular expressions. You have to be careful to escape regular expression control characters. Typically the dot appears in filters and needs to be escaped (for example, "energy-waster.com" should appear as "energy-waster\\.com".

The format is a strict subset of JavaScript regular expressions. Syntactically, everything supported by JavaScript is reserved but only a subset will be accepted by the parser. An unsupported expression results in a parse error.

The following features are supported:

  * Matching any character with ".".
  * Matching ranges with the range syntax [a-b].
  * Quantifying expressions with "?", "+" and "*".
  * Groups with parenthesis.

It is possible to use the beginning of line ("^") and end of line ("$") marker but they are restricted to be the first and last character of the expression. For example, a pattern like "^bar$" is perfectly valid, while "(foo)?^bar$" causes a syntax error.

All URL matching is done against the canonical version of the URL. As such, you can expect the URL to be completely ASCII. The domain will already be punycode encoded. Both the scheme and domain are already lowercase. The resource part of the URL is already percent encoded.

Since the URL is known to be ASCII, the url-filter is also restricted to ASCII. Patterns with non-ASCII characters result in a parse error.

## Privacy

We have been building these features with a focus on providing better control over privacy. We wanted to enable better privacy filters, and that is what has been driving the feature set that exists today.

There is a whole universe of features that can take advantage of the content blocker API, around privacy or better user experience. We would love to hear your feedback about what works well, what needs improvement, and what is missing.

A major benefit of the declarative content blocking extension model is that the extension does not see the URLs of pages and resources the user browsed to or had a page request. WebKit itself does not keep track of what rules have been executed on which URLs; we do not track you by design.

Everything has been developed in the open; everyone is welcome to audit and improve the code. The main part of content blockers lives in [Source/WebCore/contentextensions](http://trac.webkit.org/browser/trunk/Source/WebCore/contentextensions).

## Performance advice

A big focus of this feature is performance. We are trying to have good scalability with minimal performance impact.

If the rule compiler detects that a set of rules would negatively impact user experience, it refuses to load them and returns an error.

There are parameters in your extensions that do impact performance. In this section, I will give some general rules to get good performance. There are a few big themes to maximize performance:

  * Avoid quantifiers ("*", "+", "?") in "url-filter" as much as possible.
  * CSS rules are best defined before any "ignore-previous-rules"
  * Make the trigger as specific as possible.
  * Group rules with similar actions.

### Minimize quantifiers in regular expressions

Avoiding quantifiers helps us optimize the triggers in the backend. Quantifiers are useful but they increase the matching possibilities which tends to reduce performance. We have found that many existing privacy extensions sometimes use quantifiers excessively which tends to be costly.

One particularly bad case is quantifier appearing in the middle of a string. Cases like:
    
    
        foo.*bar
    
    

tends to be slower than "foo" and "bar" separately. Using too many of them can cause the rule set to be rejected.

One exception to that rule is common prefixes. For example, if you have many rules such as those:
    
    
        https?://user-tracker.com
        https?://we-follow-you.com
        https?://etc.com
    
    

The rules are grouped by the prefix "https?://, and it only counts as one rule with quantifiers.

### Have CSS rules before "ignore-previous-rules"

When compiling the rules, we group the CSS rules whenever we determine they will be used together. For example, if a set of rules applies on every page (by using the filter ".*"), a special stylesheet is prepared for them to be ready to use them instantly when the page has loaded.

When a "ignore-previous-rules" appears, it forces the compiler to break the stylesheet since the rules appearing before an action "ignore-previous-rules" are all dismissed when the action is activated.

### Use specific triggers

Good triggers try to exclude everything that could be activated by accident. Regular expressions should be as specific as possible to achieve your desired goal. Specifying the resource types if possible, and using domain filter if the rule should only apply on certain domains.

Having specific rules is important to avoid changing pages inadvertently, but it is also useful for performance. Having few actions to execute is a good idea.

### Grouping rules with the same actions

Finally, grouping rules with similar actions can simplify the execution. Ideally, your extension will have all the rules blocking loads, followed by all the rules blocking cookies, etc.

Since rules are evaluated in order, it is useful to have them grouped together since matching a trigger means all the following rules of the same action can be skipped.

For example, if all the "block" rules are together, as soon as the first one is activated, all the following block rules are skipped since they have the same actions. The trigger evaluation continues on the first following rule with a different action.

## We want your feedback

We have been developing these capabilities with the goal of achieving better privacy without incurring an unreasonable performance cost. We have intentionally limited ourselves to just a few features that could be improved.

If you start building content blocker extensions, it would help us if you send us your JSON files. Having many different use cases will help us optimize the code better.

For short questions, you can contact [me](https://twitter.com/awfulben) on Twitter. For longer questions, you can email [webkit-help](https://lists.webkit.org/mailman/listinfo/webkit-help) or [file bug report](https://bugs.webkit.org/enter_bug.cgi?product=WebKit). If you're interested in hacking on the code, feel free to ask [me](https://twitter.com/awfulben), [Alex Christensen](https://twitter.com/alexfchr), [Brady Eidson](https://twitter.com/bradeeoh) and [Sam Weinig](https://twitter.com/samweinig) for help.

For questions about Safari's adoption of these APIs, contact [Brian Weinstein](https://twitter.com/cleatsupkeep) or [Jon Davis](mailto:web-evangelist@apple.com).

You can follow any responses to this entry through the [RSS 2.0](https://www.webkit.org/blog/3476/content-blockers-first-look/feed/) feed. Both comments and pings are currently closed.

Comments are closed.
