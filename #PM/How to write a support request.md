# How to write a support request

_Captured: 2015-10-09 at 21:49 from [brettterpstra.com](http://brettterpstra.com/2015/10/09/how-to-write-a-support-request/)_

![](http://cdn3.brettterpstra.com/uploads/2015/10/suxplzfix.png)

I publish a lot of software projects, and as a result I deal with a lot of customer support. I pride myself on providing support at a level that users and customers are excited about.

Most of the software I produce is free, but I try to provide the most helpful answers I can without draining all of my time. With my commercial software, such as [Marked 2](http://marked2app.com) and [StretchLink](http://stretchlinkapp.com), I strive to provide excellent responses to all queries. There are a few things that help me (and any software developer/company) provide that quickly and pleasantly.

These tips aren't your job or responsibility. You're the customer, and you deserve good support. Not following these guidelines should never prevent excellent customer service, but taking them into account when submitting a problem or request will make the experience better for both user and developer.

Here's a summary, in case you don't want to read all of the details:

  1. Be pleasant-maybe even kind-and set a [level-headed tone](http://brettterpstra.com/2015/10/09/how-to-write-a-support-request/)
  2. Be descriptive in the [subject line](http://brettterpstra.com/2015/10/09/how-to-write-a-support-request/)
  3. Provide [as much information](http://brettterpstra.com/2015/10/09/how-to-write-a-support-request/) up front as you can
  4. When possible, [post your request publicly](http://brettterpstra.com/2015/10/09/how-to-write-a-support-request/) so that the response can benefit other users who may have the same issue

Those are probably self-explanatory, but allow me to elaborate.

### Public Forums

If the support forum offers the option, make your request public (unless your problem is terribly embarrassing or needs to contain personal/proprietary information). Not only does this open the possibility of more users helping with debugging or describing the issue, it also leaves a public record of the conversation that other users can reference, making it possible for them to understand and solve an issue without the support department having to spend time repeating the same result.

### Channels and continuity

Most software websites have easy-to-find links to support options, including Twitter accounts, forums, and email forms.

Personally, email is my least favorite because it involves a lot of repetition and only helps one user at a time.

I provide dedicated Twitter accounts for apps like [Marked](http://twitter.com/markedapp) and [StretchLink](https://twitter.com/stretchlink), and I have no problem with questions being posted there. If I can answer with a yes or no, or in less than 140 characters, it's a great medium for easy questions. If the answer is longer or requires additional questions, though, users will be directed to a support site.

If you start a support conversation on one platform--such as Twitter or direct email--and then move to a new one, collate prior conversation when switching channels. It's difficult to keep support conversations going when doing so involves searching back through emails or Twitter conversations to put it all together.

If you have access to other user's conversations, such as on a support forum, search for existing conversations first. You may find the answer is already there, or a conversation is in place that you can add to. Collaboration with other users helps everyone in solving problems.

While it's preferable to keep a topic in one continuous thread, it's also best to separate discrete issues. Especially in the case of public forums, switching topics in the middle of a thread makes searching difficult for other users and muddies the waters for the support personnel.

### Tone

If you want really good support, keep the tone positive, or at least informative and not an attack. Yes, you spent money on a product, and you have a problem with it, but give the customer support folks a chance to rectify it before you express anger or disappointment. The answer may be very easy, or you may have uncovered a bug that's easily fixed. Making a support request an attack is unproductive.

It may seem like a stretch, but starting a request with a compliment changes the entire tone, and puts the responder into a much more sympathetic position. Express gratitude, pleasure, or admiration for something you like about the product before detailing what you don't. I'm absolutely serious about this, it changes everything.

Bad: _"I SPENT GOOD MONEY ON THIS AND IT DOESN'T WORK, I'VE BEEN RIPPED OFF."_

Good: _"I'm excited about this app, but I'm having an issue with…"_

In my opinion, offensive tones are never warranted. However, it works both ways. If a response from customer service is offensive (or defensive) in tone, or repeated attempts go unacknowledged, I think there's just cause for a more heated note at that point.

### Subject line

Make your subject line a clear description of the issue. In cases where the request is part of a public forum, it makes it searchable for people who may be experiencing the same problem. Even in private conversations, it makes it easier for customer support to track and organize issues.

It also makes for a level-headed response and keeps the CS responder from responding defensively.

The subject line sets the mood for the entire interaction. If a subject line includes negative words such as "annoying," "frustrating," or "sucks," you've automatically made the reader assume that the entire report is going to be in a negative tone.

Bad: _"[feature] sucks, plz fix"_

Good: _"[feature] produces [incorrect result]"_

As a side note, the phrase "Please fix" (or "plz fix," or any other variation) is redundant and somewhat offensive. You can safely assume that if you're reporting an issue to a responsible developer, they already have that goal in mind.

### Body

There are several things you should always include in a bug report or support request.

  1. A description of the issue 
    * what you think it should do
    * what the unacceptable or deficient result was
    * if the issue is an error dialog, provide the exact information presented by the application, either as text or via a screenshot of the dialog
  2. A list of steps the support or development team can use to replicate the issue. Even if your issue is intermittent or unpredictable, an attempt to provide context for something like a random crash makes it easier to guess where the issue is
  3. When applicable, sample documents, screenshots, screencasts, or any materials that demonstrate the issue
  4. Any configuration information you can easily determine is applicable (OS version, application version, unique configuration options)
  5. A description of steps (if any) you've already taken in an attempt to fix the issue. This helps the developer/CS personnel to avoid asking obvious questions that require additional back and forth.
  6. If you include a crash report, it's preferable in most situations to provide it as an attachment instead of pasting the entire report into the request (see [Crash Reports](http://brettterpstra.com/2015/10/09/how-to-write-a-support-request/))

#### Crash Reports

In the case of a crash, the developer may or may not have automatically received a crash report.

Pasting long crash reports into a thread is undesirable, both to the support personnel and to other users who want to view the conversation. Pages of scrolling through information that is only marginally searchable is frustrating.

The exception to this is specific information within the report that may be exactly what gets typed into Google when someone else is looking for a solution. This would be a short block found in crash details such as:
    
    
    Exception Type:        EXC_CRASH (Code Signature Invalid)
    Exception Codes:       0x0000000000000000, 0x0000000000000000
    Exception Note:        EXC_CORPSE_NOTIFY
    

The rest of the report is likely useful, but is better attached rather than pasted.

##### Finding and attaching a crash report

On a Mac, if you experience a crash or a hang, you can usually find a report generated by the system in Console.app. Launch it from /Applications/Utilities/Console.app, and in the left sidebar locate "User Diagnostic Reports" where crash logs are listed by the name of the application.

![](http://brettterpstra.com/uploads/2015/10/console-crash@2x.jpg)

These reports can be dragged from the sidebar into an email, a sharing service such as [Droplr](http://droplr.com/) or [CloudApp](https://www.getcloudapp.com/), or uploaded as an attachment to a ticket. Alternatively, paste the report to a [GitHub gist](http://gist.github.com) or [Pastebin](http://pastebin.com/) and link to it from the request.

### In Closing

As I said at the beginning, it's not necessarily the user's responsibility to provide this kind of information, but taking these steps _will_ increase the possibility and likelihood of delightful customer support.

Submitting a bug report or support request shouldn't be a hassle. I've recently added a feature to [Marked 2](http://marked2app.com) under Help->Report an Issue which provides an outline for submitting a request.

Here's to you not having to write too many of these, and always getting support that makes you happy with your software choices. Cheers.
