# Clean Architecture

_Captured: 2015-10-17 at 22:04 from [blog.8thlight.com](http://blog.8thlight.com/uncle-bob/2011/11/22/Clean-Architecture.html)_

In the weeks since I started talking about the need to clean up our architecture, I've noticed a surprising resistance to the idea. Apparently the notion that it's a good idea to hide the framework, UI, or database from the application code is not universally accepted.

I first blogged about this topic [here](http://blog.8thlight.com/uncle-bob/2011/09/30/Screaming-Architecture.html), I did some short video blogs [here](http://cleancoder.posterous.com/retarded-architecture), [here](http://cleancoder.posterous.com/architecture-deference), and I did a whole cleancoders.com [episode](http://www.cleancoders.com/codecast/clean-code-episode-7/show) on the topic. I've also done several keynotes on the topic, the slides for which are [here](http://dl.dropbox.com/u/4730299/Architecture%20the%20lost%20years.key), and a video recording of which is [here](http://mchenry.softwarecraftsmanship.org/the-a-word-a-discussion-about-architecture).

One somewhat dissenting view, written by _The Frustrated Architect_ in his _coding {the} architecture_ blog is [here](http://www.codingthearchitecture.com/2011/11/06/the_delivery_mechanism_is_an_annoying_detail.html). He shows a picture, which I'll repeat:

![](http://www.codingthearchitecture.com/images/the-delivery-mechanism-is-an-annoying-detail-5.png)

The point he's trying to make is that if the UI and Database are a much larger part of the system than the business rules, then the architecture of the system should be more oriented around those larger elements. Of course I disagree. No matter how large any one part of the system is, the other parts should be decoupled from it.

Other dissenting (or perhaps a better word is "skeptical") views have been less formal. One person simply asked me: "Have you ever actually done this -- _in a Rails project_", as if Rails was somehow special and changed the game so much that the normal rules of good design don't apply.

Other folks have worried that the net result of my advice would be lots of duplicated code, and lots of rote copying of data from one data structure to another across the layers of the system. Certainly I don't want this either; and nothing I have suggested would inevitably lead to repetition of data structures and an inordinate of field copying. I'll explain why below.

One particularly colorful complaint was: "_This sounds like a dogmatic rant, I want to see code._" While I sympathize with that view, the concepts here are just not that difficult to grasp; and, in fact, lots of code would obscure them more than help.

## Not Rocket Science.

This isn't rocket science. The basic idea is very simple. You separate the UI from the business rules by passing simple data structures between the two. You don't let your controllers know anything about the business rules. Instead, the controllers unpack the HttpRequest object into a simple vanilla data structure, and then pass that data structure to an interactor object that implements the use case by invoking business objects. The interactor then gathers the response data into another vanilla data structure and passes it back to the UI. The views do not know about the business objects. They just look in that data structure and present the response. There are, of course, more details than that; and they are well described in the references above. But at the bottom, that's all there is to it.

The benefit should be obvious. The application code is completely decoupled from the UI. You can test the application code without the UI present. You don't need to fire up the web server, or the container, or Rails, or any of the other frameworks in order to run your tests. What's more, if you don't like your current UI, you can change it by replacing it with another.

Is this a perfect scheme? Of course not. Might one kind of UI be so different from another that they couldn't share a common interface? Of course that's possible. Does that mean this kind of decoupling is a waste? Are you kidding me?

## It'll slow me down.

No it won't. For goodness sake, it will speed you up. You'll be able to run your tests without delay. You'll be able to defer decisions about the UI. You'll be able to test business rules without the UI present. That kind of flexibility and decoupling _always_ speeds you up. If there's one thing we've learned about coupling over the last fifty years it that nothing is better as slowing you down.

## We shouldn't defer decisions.

One of the more strident comments I've made about architecture is that a good architecture allows you to defer critical decisions like the UI, frameworks, database, etc. One point made by several people is that customers don't want the UI deferred. DBAs don't want the database deferred. From iteration to iteration they want to see the whole system working, including the UI, the Database, and the frameworks. They don't want an iteration to be spent solely on business rules. Indeed, good agile practices specifically demand long skinny slices through the entire architecture.

Of course I agree with all of that. However long skinny slices don't have to be coupled. A good architecture _allows_ you to defer critical decisions, it doesn't _force_ you to defer them. However, if you _can_ defer them, it means you have lots of flexibility. For example, you could create an interim simple UI for the first few sprints, and then replace it with a more capable UI later.

## What about convention over configuration?

The Rails mantra of depending on conventions rather than configuring everything is a powerful idea; and one that I fully agree with. But that doesn't mean you should couple your system. Conventions do not necessarily cause coupling! There is no reason, for example, why the model objects in Rails should hold business rule methods. Keeping the business rules separate and decoupled from the ActiveRecord derivatives does not violate any _Rails_ conventions. Even if it did, I think decoupling trumps convention.

## What about GOOS?

One of the better books about software design is "Growing Object Oriented Software" by Steve Freeman and Nat Pryce. They recommend an outside-in approach to developing systems. You start at the interface and work your way in to the business rules.

At first this sounds like it contradicts my advice. After all, I focus on the use-cases and consider the UI to be a annoying little detail. However, there's nothing wrong with working on the annoying little details first, so long as you _decouple_ your business rules from them. There's nothing in the GOOS ideology that opposed decoupling the business rules from the UI.

Now, truth be told, I don't use the GOOS methodology. I prefer an inside-out approach. I like to focus on the business rules first, and then put a UI around it later. But that does't mean that the GOOS technique is bad (it's not) or that if you follow GOOS you won't have a decoupled architecture (you'd better!).

## Oh no, it's Big Up Front Design!

No it's not. I'm not telling you to spend months and months drawing UML diagrams. I'm telling you to _decouple_. You can do that decoupling while you are writing your code and making your tests pass. You don't need a big up front plan in order to create a nicely decoupled architecture. All you have to do is _think_ about the problem while you are coding it.

However, I should point out that there is nothing whatever wrong with spending a few hours, or even a day or two, pondering the shape of your system. There's nothing wrong with drawing some UML, or other diagrams in order to get some ideas about how your system should be structured. I don't want you doing this for months, but there's nothing wrong with _thinking_. (see: [Hammock Driven Development](http://blip.tv/clojure/hammock-driven-development-4475586))

## This ain't new.

I've been surprised by the reactions to these ideas. I understand that people naturally resist change; and that lots of programmers aren't used to the ideas of decoupling (_read that clause several times and weep_). But this is not some new idea that occurred to me out of the blue. These ideas are _old_. They come from people like David Parnas, Tom Demarco, Grady Booch, Ivar Jacobson, and many, many others. The fact that they are old doesn't necessarily mean that they are good; but in this case -- _they are_.

What happened to us? How did we forget these rules? When did the old rules of coupling and cohesion evaporate from our awareness? Are we really so naive as to think that the best way to write a complex system is to throw a bunch of components into a bag and shake it until it works?

Robert Martin (Uncle Bob) is a Master Craftsman. He's an award-winning author, renowned speaker, and has been an uber software geek since 1970.

#### More Posts by This Author
