# Method Length and Extract 'Til You Drop

_Captured: 2017-04-28 at 19:41 from [dzone.com](https://dzone.com/articles/method-length-and-extract-till-you-drop?edition=292940&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-28)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

As a typical nerd (and a DZone [Zone Leader](https://dzone.com/pages/zoneleader)), I tend to read a lot of blog posts and comments about programming. One thing that keeps amazing me is how long people's functions tend to be and how many people are convinced this is the right way to code. In reality, a readable function should rarely exceed five lines of code.

Take a short look at this function:
    
    
        System.out.println(week.getStart() + " - " + week.getEnd());
    
    
            System.out.println(day + ":");
    
    
                    System.out.println(visit.getTime() + ": " + visit.getOwnerName());
    
    
                    System.out.println("Pets: " + visit.getPetNames());
    
    
        try (Scanner scanner = new Scanner(System.in)) {
    
    
            } while (!controller.execute(command));

How readable is that piece of code? Are you able to tell what it does just by taking a quick look at it? Two little extractions should make things clearer:
    
    
        System.out.println(week.getStart() + " - " + week.getEnd());
    
    
            System.out.println(day + ":");
    
    
                System.out.println(visit.getTime() + ": " + visit.getOwnerName());
    
    
                System.out.println("Pets: " + visit.getPetNames());
    
    
        try (Scanner scanner = new Scanner(System.in)) {
    
    
            } while (!controller.execute(command));

Much better. Now, the three functions are fairly readable and it should be easier to reason about what's happening in there. But that's still not good enough. Our show() method has [mixed levels of abstraction](https://dzone.com/articles/slap-your-methods-and-dont-make-me-think) and there's still a loop inside an if statement. To deal with the first problem, we can simply extract two methods:
    
    
        System.out.println(week.getStart() + " - " + week.getEnd());

Now, how readable is that? It's trivial, but that's a good thing. We want our code to be trivial. Now to the second problem. Guess what we'll do. That's right, extract again!
    
    
        System.out.println(visit.getTime() + ": " + visit.getOwnerName());
    
    
        System.out.println("Pets: " + visit.getPetNames());

Do you see how much clearer the code becomes? That's exactly the point. When you extract, things become more digestible and it's easier to [preserve proper levels of abstraction](http://tidyjava.com/slap-your-methods-and-dont-make-me-think/). The fun part of it? You can extract all the time! [Extract till you drop!](https://sites.google.com/site/unclebobconsultingllc/one-thing-extract-till-you-drop)

And in the meantime, your functions will become smaller and smaller. Usually less than six lines of code long. This is approximately the size at which code becomes pleasantly trivial. Therefore, beware of functions longer than that and continuously seek possibilities to extract further. The readers of your code will thank you.

[Download Modern Java EE Design Patterns](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035): Building Scalable Architecture for Sustainable Enterprise Development. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202130&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157035).
