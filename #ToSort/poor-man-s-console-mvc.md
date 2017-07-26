# Poor Man's Console MVC

_Captured: 2017-04-21 at 21:27 from [dzone.com](https://dzone.com/articles/poor-mans-console-mvc?edition=292907&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-21)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

After [two ](https://dzone.com/articles/mvc-pattern-language-part-1)[posts](https://dzone.com/articles/mvc-pattern-language-part-2-patterns-6-11) of pure theory about the MVC Pattern Language, I was looking to provide some practical examples. The technical part is easy - everybody already knows how to implement that in various ways, but I couldn't figure out how to show the whole mental models part of it. In the end, I came up with what follows - an MVC "Pet Clinic" in the console!

As we learned in the previous posts, on the idea level, MVC is most concerned with understanding the user's way of thinking. Therefore, we won't jump straight into code here. Instead, we'll visit a real pet clinic on the outskirts of your town and watch our user at work.

## She Ain't a Computer Lady

The clinic that hired you is actually a small office that consists of a few rooms, the most important being the visiting room. The old lady that runs the place has no computer at the moment and you keep wondering why does she want to pay so much money for dedicated software. After a while, you conclude that this is exactly the kind of person who needs a dedicated piece of software. If you tried to give her the Spring's Pet Clinic and call it a day, she'd be totally lost in it. You need to create a habitable environment for her, as she'll be learning both using the computer and your program at the same time.

## Gathering Requirements

Instead of acting like an idiot and asking the old lady for the "requirements" directly, you sit quietly and watch her work for a few hours. This gives you a pretty good idea of her workflow.

She keeps track of all her visits inside a calendar. When somebody calls to schedule a visit, she asks about the person's name, pet names and preferred visit time. Then, when both sides agree on the time of the visit, she notes it down in her calendar.

When the visit time comes, the old lady takes out pets' files, which contain all important information about their health history. Then she takes care of the pet itself. Not much interesting stuff here. She makes the same "you're so lovely" face every time and solves all kinds of problems - from a pet being actually sick to being moody and not wanting to play with its owner (sigh). After she finishes the "care-taking" stuff, she sits down and writes a short summary of the visit. The summary consists of two parts - course and recommendations. She always writes down two copies - one for the owner and one to put in the pet's file.

## Modeling the Domain

You tried talking to the woman about the veterinary domain but it seems that talking to her about abstract terms and relationships is as productive as talking with you about Malaysian poetry of the 19th century. Luckily, the concepts behind scheduling a visit seem easy enough to create the first prototype without creating an advanced domain model. You start off with something like this:

![](http://tidyjava.com/wp-content/uploads/2017/04/ss2017-04-18at08.50.36.png)

## What's in the Lady's Head?

As we said before, simply creating a CRUD for visits, pets, and owners is not enough. We want better than this. Therefore, we have to look for things that will make the user instantly familiar with our software; something that _improves _his workflow instead of completely turning it around. In the case of our vet lady, these things would be the visit calendar and the pet files.

The physical calendar that the lady uses looks like a big notebook in which every two pages represent a single week. When a visit is scheduled, she notes things down using a specific format: hour goes first, then the owner's name and the pets in the end.

The pet files are cardboard folders containing all of the summaries from the previous visits and occasionally some other medical documentation. The old lady keeps them in a desk's locker, sorted alphabetically so that she can find the right one faster when the visit starts.

## Implementing a Visit Calendar

The visit calendar will become a _[business_ ](http://tidyjava.com/mvc-pattern-language/#business-objects)_[object](http://tidyjava.com/mvc-pattern-language/#business-objects) _in our system. Since there will be quite a lot console printing and input parsing, we'll separate it into the famous MVC triplet: _[model, view_, and _controller_](http://tidyjava.com/mvc-pattern-language-2/). This triplet should work together to give the lady a feeling that she's working with her old calendar, just that the calendar is now computerized. Therefore, we'll keep the weekly grouping of visits and allow her to switch the weeks like she'd be flipping pages in her old calendar. We'll also print the visit information in a format similar to the one she used in her old calendar. I did some basic implementation, let's take a look at it.

## Controller

So far our _controller_ recognizes three commands: "next" and "previous", which change the calendar's week, and "add", which allows for adding a visit to the calendar:
    
    
            if ("next".equals(command)) {
    
    
            if ("previous".equals(command)) {
    
    
            if (command.startsWith("add")) {

## Model

The _model_ is responsible for holding the information about the currently selected week and allows manipulating the underlying visits. By the means of changed() method, it lets the _view_ know whenever something changes in the calendar:
    
    
        static final DayOfWeek[] OPEN_DAYS = {MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY};
    
    
            return visits.on(currentWeek.get(day));
    
    
        void addVisit(DayOfWeek dayOfWeek, LocalTime time, String ownerName, String[] petNames) {

## View

The _view _displays weekly visits in a format similar to the one already used by the vet lady and accepts user's commands:
    
    
            System.out.println(week.getStart() + " - " + week.getEnd());
    
    
            System.out.println(day + ":");
    
    
            System.out.println(visit.getTime() + ": " + visit.getOwnerName());
    
    
            System.out.println("Pets: " + visit.getPetNames());
    
    
            try (Scanner scanner = new Scanner(System.in)) {
    
    
                } while (!controller.execute(command));

## Conclusion and Next Steps

That's everything I did in this prototype so far. The whole source code is available [here](https://github.com/tidyjava/console-mvc-pet-clinic). As you probably noticed, there's no technical rocket science in there and not even any new concept at the first glance. I think the most important thing about this example is that the user is communicating directly with the [business objects](http://tidyjava.com/mvc-pattern-language/#business-objects). She's not talking to some generic `VisitController`, which talks to some generic `VisitService`. Instead, we're exposing her to communication with an object she already knows - the `VisitCalendar`.

In the next post, I'll try to move our visit calendar to the web and we'll see how the concept of business objects plays with "so-called" Web MVC frameworks like Spring MVC. If I have enough time (which is unlikely, but possible), I'll try to add the second business object to the system - the pet files. Obviously, if someone from the readership wants to try their strengths in doing that, pull requests are welcome!

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).
