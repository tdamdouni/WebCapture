# Understanding URL Encoding

_Captured: 2015-09-22 at 11:26 from [onetapless.com](https://onetapless.com/understanding-url-encoding)_

You know how chaining multiple actions can turn what was once a simple url on the Cthulhu of hyperlinks. My head twirls on the subject and I bet so do yours and as my actions became more and more complex over time, I realized it was time to take a step back and study how url encoding works across our actions and multiple apps.

## Reading a URL scheme

The first steps to understand what a url does is to picture the elements that compose it and since we're exploring the depths of URL encoding, we can divide a URL action as **calls**, **fields** and **queries**.

![call-field-query](https://onetapless.com/content/1-blog/130-understanding-url-encoding/call-field-query.png)

> _Splitting a URL action in CALL, FIELD and QUERY_

I'll explain each one of the elements with analogies that would make Scott Forstall proud. First, there is the `CALL`, which can be interpreted as a phone number. One app _calls_ the other, in the previous example we're calling [Drafts](https://itunes.apple.com/us/app/drafts/id502385074?mt=8&uo=4&at=10l4KL) in the `create` [extension](http://en.wikipedia.org/wiki/Extension_\(telephone\)).

We're calling Drafts because we're requesting one of the services it provides, however, Drafts requires information to perform it, so we send a letter

in an envelope entitled **TEXT**. For each parameter requested by Drafts, we'd send one envelope. Each envelope label is a `FIELD` and they're responsible for specifying where we want Drafts to apply our letter contents.

You sent the letter, you made the call. Drafts finally picks up and receives the envelope, then it hangs up. How rude. Drafts will now open the envelope and check the letter, which is our `QUERY` and contains what we want Drafts to parse as _text_, which is the title in the envelope. The act of sealing/opening the envelope is what we call URL encoding/decoding.

![hello-world](https://onetapless.com/content/1-blog/130-understanding-url-encoding/hello-world.png)

> _The outcome from our long-distance call_

_Technology._

## How URL encoding works

The best way to comprehend why we must url encode contents is paying attention to **who** carries out the actions in the story above. **_You_**, the first app, is making the call and sending the envelopes, but **_Drafts_**, in the other line, is the one who opens the envelopes and reads the letter. When you put something in the envelope, it is url encoded, only to be decoded when read.

But why? Well, try sending a letter without an envelope. What if it is your book manuscript? All those paper sheets, arriving upside-down at their destination. We pack things because we want to control how things arrive and Drafts also want us to pack because it smooths its work. The [union](http://en.wikipedia.org/wiki/Trade_union) is so rough that if you don't send your letters within an envelope they won't even arrive at their destinations.

A URL must be a full string without any white space, that's why your regular spaces are converted to `%20` and your line breaks to `%0A`. Also, some character have a function in the URL, such as the ampersand (&), which states that we're creating another `FIELD`.

![fields-divider](https://onetapless.com/content/1-blog/130-understanding-url-encoding/fields-divider.png)

> _Use an ampersand to set a new FIELD_

Let's pretend that is the full action we're triggering, which is going to call [GoodTask](https://itunes.apple.com/us/app/goodtask-reminders-to-do-task/id767998024?mt=8&uo=4&at=10l4KL) and specify the `FIELDS` _text_ and _dueDate_. GoodTask will open the letters and place the contents in their respective fields.

![go-to-the-supermarket](https://onetapless.com/content/1-blog/130-understanding-url-encoding/go-to-the-supermarket.png)

> _How GoodTask interprets the FIELDS_

Wrapping up, you url encode your `QUERIES` because they must arrive safely to their destination, where they're decoded, just as opening a letter.

## The x-success envelope

The core of the x-callback-url is a `FIELD` called `x-success`, which sets a url for the destination app to call after it processes the `QUERIES` you sent. If that's confusing you, think of envelopes: the `x-success` envelope is a [business reply mail](http://en.wikipedia.org/wiki/Freepost), so when the receiver attends to all the `QUERIES`, it will trigger the `x-success`, just as if posting the reply mail in the post office.

This is where the [inception](http://www.imdb.com/title/tt1375666/) begins since we must send our `x-success` as a `QUERY`, thus it must be in an envelope (URL encoded) to be properly read by the next recipient. The URL in the `x-success` will have its own `CALL`, `FIELDS` and `QUERIES`, but as disguising it as an unique `QUERY` in our letter and since every `QUERY` must be encoded, our cloaked `QUERY` must be in an envelope for itself, that's why we encode it twice.

![x-callback](https://onetapless.com/content/1-blog/130-understanding-url-encoding/x-callback.png)

> _Comprehending how the x-success works_

When we trigger the URL above, GoodTask will decode the `x-success` envelope and act on its content, calling Drafts to create a new document written _Hello World_.

## Understanding unique app markups

[Drafts](https://itunes.apple.com/us/app/drafts/id502385074?mt=8&uo=4&at=10l4KL) has a myriad of _templates_ and _tags_ to manipulate the current document

and generate new text. [Launch Center Pro](https://itunes.apple.com/us/app/launch-center-pro/id532016360?mt=8&uo=4&at=10l4KL) has many different prompts for content input, lists for selection and more. [TextTool](https://itunes.apple.com/us/app/texttool/id751972884?mt=8&uo=4&at=10l4KL) supports the `[[output]]` keyword to attach the transformed text into the `x-success`, much alike [Terminology](https://itunes.apple.com/us/app/terminology-3-extensible-dictionary/id687798859?mt=8&uo=4&at=10l4KL) and the `[[term]]` parameter to add a selected word into the callback action.

I want you to create a new action in Launch Center Pro with the following url:
    
    
    drafts://x-callback-url/create?text=[prompt:Hello World]

Now I want you to call this action and write _Hello World_ in the prompt. Trigger and you're at Drafts, with _Hello World_ written in the document. You remember this outcome from our first actions, when we had to manually encode the space between the words, this may give you a hint on how these attributes work: **They put your content in the envelope for you**.

Some of these apps even offer you a syntax to URL encode whatever is within it. For example, get back to our first _Hello World_ action in Drafts and wrap the `QUERY` in double curly brackets:
    
    
    drafts://x-callback-url/create?text={{Hello%20World}}

![encoded-hello-world](https://onetapless.com/content/1-blog/130-understanding-url-encoding/encoded-hello-world.png)

> _Envelopes within envelopes within envelopes_

Trigger it and you'll get a _Hello%20World_ in the screen, so if you don't want to read the double curly brackets as a force encoding, you can picture it as a safeguard for your `QUERY` that will preserve its current state when it arrive to its destination. An invisible envelope, some may tell you.

It is also important to point out how these apps register this force encoding, they'll often resolve every other variable, such as `[prompt]` in [Launch Center Pro](https://itunes.apple.com/us/app/launch-center-pro/id532016360?mt=8&uo=4&at=10l4KL), before encoding anything. Also, in most apps you can't nest multiple forced encodings, however, I believe this landscape is about to change.
