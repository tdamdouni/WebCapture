# Approaching Complex Problems

_Captured: 2015-10-14 at 23:06 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/approaching-complex-problems)_

## Approaching Complex Problems and Websites

![Complex problem](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/complex_problem_small.jpg)

> _Complex problem_

So you've learned how engineers approach problems in theory and some of the specific heuristics and techniques of software engineering. But how does all this apply to real problems and websites?

You're probably here because you want to build a website of your own. Or maybe you're working on a specific module of a much larger corporate site. Or maybe you're just being asked a brain teaser question in your job interview.

In this lesson, we'll follow the engineering approach laid out in the previous lesson as it applies to three real examples -- building a car, building Facebook, and building a consumer email system. These are designed to help you see the engineering problem-solving approach in action so you begin to internalize its steps (come to the dark side...!)

As a recap, here is the overall approach with a few additional specifics:

  1. **Understand the Problem**
    1. Clarify the problem
    2. Model the system and break the problem into pieces
    3. Research similar solutions
  2. **Come up with a Plan**
    1. Prioritize your work
    2. Map out your strategy
  3. **Implement the Plan**
  4. **Verify your Results**

Okay, let's see this stuff in action!

### Step 0: Blind Panic

Okay, just kidding (sort of)... Any time you're staring at a problem that you can't entirely fit in your head, you'll probably feel a bit overwhelmed. Take a deep breath and remember that everything can be broken down into bite-sized pieces. The following approach is meant to guide you through that.

### Step 1: Understand the Problem

The first step is always the same:

  1. Clarify what the problem is
  2. Come up with a model for how the system works so you can break the problem into pieces
  3. Research so you can learn from similar solutions.

#### Example A: Building a Car

Let's start with a concrete example and say that you've been tasked with building a car. It's not a website but actually follows pretty much an identical process. How do you tackle that problem?

![exploded car diagram](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/car_exploded_small.jpg)

> _exploded car diagram_

  1. **Clarify** \-- What are they really asking for? Do they want a whole car or just a vehicle that acts like a car? What's the use case? The use case for the vehicle could dictate some pretty major differences (e.g. a worksite pickup truck vs a sportscar). How durable or inexpensive must it be? In our example here, let's assume our client is really just looking for something to get from point A to B on a construction site without much in the way of creature comforts.
  2. **Model the system and break down the problem** \-- In this case, realize that a car is really just a series of almost-independent systems. There's the main drive train which powers the wheels, the power system which works everything from the starter to the windshield wipers, the cooling system that works the A/C and cools the engine, the steering system that converts the steering wheel inputs into physical action and so on. Digging further, each of the car's systems can be broken down into subsystems and, ultimately, individual components.

Given the use case, which systems are likely to be the most important and which can we skip? It sounds like we really just need to build a good power train and can skimp on things like air conditioning, power steering, and maybe even lights! 

  3. **Research other solutions** \-- There are very few novel problems anymore. Certainly in the case of cars, a bit of research would show you all sorts of approaches from do-it-yourselfers with mail-order part kits to six-sigma manufacturing techniques and global supply chains. What this should tell you is how much work you really need to do and how many of the components you'll be using are available out of the box. In the ideal case, you just need to put together a series of ready-to-go parts.

#### Example B: Cloning Facebook

For our second example, let's say you're tasked with building a clone of Facebook. That's a _huge_ website with dozens of major features. Where do you start?

![facebook status bar](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/facebook_status_bar_small.jpg)

> _facebook status bar_

  1. **Clarify** \-- Are we supposed to make every feature on the site or just stick with the major ones? What's the intended use of this clone site? In this case, let's assume we're really just trying to replicate several core functions to test it out in the new Westerosi market. Lucky for us, it seems like only the major features like "friending" and "commenting" and "posting" are in the scope of the problem (good thing we asked).
  2. **Model the system and break down the problem** \-- In the early phases of a user-facing site (ie. before it has to deal with scaling issues), the features you work on will be primarily dictated by the user flows we talked about in the UX section. Try to come up with a model of these features and the major subsystems required to support them. You'll likely build mockups and user flow diagrams to help you understand the system.

How you break down the problem will vary a bit depending on whether you're working more on the front-end (e.g. what's actually displayed in the browser) or the back-end (the guts of the server-side code). On the front-end, you'll take apart your mockup and identify the pieces of it that you'll need to build first. On the back end, you'll need to figure out what sorts of data are needed to support these user-facing features -- typically, what the user actually sees is just the tip of the iceberg. 

For example, something like sending a "friend request" actually has a whole lot going on beneath the surface. You obviously need to save a couple of users in your database but you'll also need some sort of "request" stored too since your intended friend needs the option of either accepting or rejecting that request. If the request is rejected, you'll probably need to save that state as well so the person can't ask again (or something like that). You need the logic that figures out whether to display a notification to the recipient, to send an email about that request, and even whether to display the "unfriend" button yet.

As you can see, there are a whole lot of subsystems that get pulled into this. Sending an email after a friend request is an example -- there is probably a whole email infrastructure set up to handle multiple different cases of emailing people and our friend request feature just needs to hook into it. Is that within the scope of your problem or is that best left for another day? 

  3. **Research other solutions** \-- in this case, you can probably find other Facebook clones out there or similar sites and see what they've implemented. You'll find that there are a number of frameworks you can use which contain large amounts of boilerplate code that you would otherwise have to write yourself. In terms of best practices, there are lots of blog posts out there about similar challenges of working with user relationships.

#### Example C: A Customer Email System

Speaking of email systems, we recently encountered exactly that problem when working with an open source project. The project had been using a web-based email provider with lots of helpful user features but they decided that they wanted a cheaper solution with more control over how and when emails were sent. That meant that it was time to "roll their own" system where they could send smart emails to their users based on things like how long they've been on the site, their inactivity period, and certain actions they've recently taken like viewing a product.

This is a good example of the kind of "below the surface" system that doesn't show up on all the fancy mockups but which will represent a large portion of your time if you step into a more back-end focused role. Where do you start with this one?

![Tip of the iceberg](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/iceberg_small.jpg)

> _Tip of the iceberg_

  1. **Clarify the problem** \-- There are all sorts of really interesting challenges here, and of course the complexity of the solutions will depend on the scale and scope of the customer's needs. In this case (thankfully) they just needed to send occasional batches of emails based on simple business logic from their existing user table (which wasn't terribly large). That meant we didn't have to worry about too many issues around heavy use or abuse or hooking into many other systems. 

Unfortunatley, email can be devilishly complex and we still needed to implement things like tracking unsusbscribes to conform with CAN-SPAM regulations and logging sends to prevent duplications. But only by working with the project maintainers to define their needs were we able to properly determine these things.

  2. **Model the system and break down the problem** \-- This is where designing back end systems gets really fun because they're all different and you need to roll up your sleeves and dig into the guts of how things work. In this case, we had to really think it through before tackling the problem itself. 

We started by breaking down the actual process of sending an email, for instance how we start by identifying the recipient, generating the HTML template for the email, and sending that template to our email provider.

Next we broke down the problem by starting from the perspective of our system's "user" (which is sometimes actually just another process). That led us to identify sub-problems based on goals like "I need to send an email manually from my application", "I need to send email to a batch of users", "I need to automate the sending of these emails daily", "I need emails to be customized for each user", "I need to record the sending of each email", and "I need to record unsubscription of these emails". 

  3. **Research the solution** \-- As you can tell, we had to do a lot of thinking but also a lot of research. We obviously weren't going to build our own email sending system from scratch (email is seriously complex stuff when you get to the implementation level) so we identified several providers with APIs that we could hook into. 

We also looked around at all the blog posts we could find about doing similar projects with our chosen framework (Ruby on Rails). Much of the solution still needed to be custom built (many of the existing pre-packaged solutions felt too constricting) but we still avoided reinventing the wheel at several turns.

### Step 2: Come up with a Plan

Once we've figured out what we should be building and how it's broken down, we've got some momentum. At this point, we need to start by prioritizing what we're working on. This is important because some systems will depend on others or build in complexity but also because we only have so many hours and dollars to devote to a given problem.

Also, the scope or requirements of the project are almost guaranteed to change midway through so we need to make sure we've tackled the highest priority challenges first. Once we've prioritized our work, we map out the actual approach to solving it in as much detail as we can.

So the two steps here are:

  1. Prioritize your work
  2. Map out your intended approach
![blueprint](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/blueprint_small.jpg)

#### Example A: Building a Car

  1. **Prioritize your work** \-- In a system without constraints, we'd get everything done. In the real world, we need to focus on certain things first and potentially cut others out. For our car, our power train is the most important component because we really just need to get something that works. The frame and the rest of the systems can be built up around that, so we'll cascade our priority from there.
  2. **Map out the approach** \-- For each subsystem, we'll figure out which components we can puchase and from where. We determine how much effort it'll take to bring them together and what we'll need to do so (e.g. welding kit, tools, screws).

#### Example B: Cloning Facebook

  1. **Prioritize your work** \-- Because this is a user-focused application, the users' priorities guide our own. We'll assume their critical goal is to check out the status of their friends. That means we need to prioritize helping users "friend" each other and smoothly displaying these things. 

But it also means we'll need to build the systems to support actually signing up users in the first place (you need to register to be "friendable"!). We'll also skip the idea that users need to approve friend requests at first -- we're assuming it's more important to just make friends at first. 

  2. **Map out the approach** \-- For the initial features we're building, let's assume that we still have the mockups we created when we first broke down the problem. We also should have a pretty good idea of the kinds of data we'll need to handle on the back end to make them a reality. In this step, we'll flesh out specifically what data tables we need, what existing libraries we'll bring in to help us solve common problems, and how our systems will interact with each other.

#### Example C: A Customer Email System

  1. **Prioritize your work** \-- We decided to start with the most granular bit of work first: sending a single email manually. That simple act would have to interact with a lot of sub systems and represented the smallest achievable goal. All the other goals, like then sending to batches at once or automating the sending, flowed from that initial goal. We prioritized based on that hierarchy.
  2. **Map out the approach** \-- From our research, we knew what provider we wanted to use for the email and we fleshed out exactly what sorts of data we would need to save in order to create the email itself in our system and start tracking things like unsubscribes and sends. In a problem like this, once you've figured out what data you need and how it will flow through the system, you've pretty much nailed the solution.

### 3\. Execute the Plan

![Sprinters at the start](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/sprinters_start_small.jpg)

> _Sprinters at the start_

The hard part is really over -- now it's time to get your hands dirty and actually implement your plan. When you're first learning how to code, you'll find yourself spending more time with this execution phase (usually debugging errors along the way). As your familiarity with your tools grow, it will get easier to express your solutions with code and you'll spend less time debugging errors and more time pondering better approaches.

It's hopefully obvious that no plan is ever really set in stone -- you'll almost certainly be required to re-plan your approach several times based on changing requirements. Maybe the client decided it'd be too expensive to build the full feature set or the users just aren't responding well to the initial features or you hit a technological roadblock. Responsiveness to change is key!

#### Example A: Building a Car

Thankfully we're not running an auto school so we don't have to cover how exactly a car is produced. I'm sure you can use your imagination... lots of sparks and winches and grease. Just remember to start with the highest priority bits.

#### Example B: Cloning Facebook

This is where you'll see how helpful it is to first break down the problem into prioritized pieces -- now, instead of trying to build a giant system all at once, you can focus on tackling a manageable piece of it.

If it's just you working on the project, a good approach is to start with the back end for that initial piece and work your way to the front (while using the mockup as your target). That means you'll need to build the database, the infrastructure to serve the right data to the front end, then the front end to display that data. If you're receiving data back from the user (e.g. via a form), you might alter the order a bit.

If you're working in a team, you'll probably focus on just the back end or just the front end portion of each feature.

#### Example C: A Customer Email System

The email system is completely in the back end so, instead of starting from the database and working towards a shiny user-facing mockup like we did with our Facebook features, we relied on completing the individual goals for each of our bite-sized tasks. We started with the highest priority one -- sending that single email -- and it required:

  1. Hooking into an external API
  2. Setting up the appropriate accounts and access keys
  3. Creating a mailer to generate the email
  4. Creating the data table to store the email
  5. Firing off that email manually from the command line

### 4\. Verify the Results

We're done, right? Well, not exactly... this is the real world and we need to verify that we've actually solved the problem we set out to solve. This should ideally be done at each point in the process on both a high level (e.g. by checking with the client or user that you've built the correct thing) and at an implementation level (e.g. by using automated testing to verify that your software works properly and you haven't broken anything else in the process).

We'll cover this in much greater depth during the upcoming lessons on Agile Development and testing.

![verified stamp](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/verified_stamp_small.jpg)

> _verified stamp_

## Wrapping Up

You just got a chance to see how the engineering approach might be applied to three different problems. Yes, it required a bit of role-playing, but it should give you a general sense for the way we break down real challenges. We didn't get into any of the formal project management techinques or implementation details because we wanted to keep things high level for now.

In upcoming lessons, you'll see how these kinds of projects are actually instantiated and implemented by teams of developers, designers and "product people", as well as some of the best practice techinques for crafting effective solutions yourself. First, though, we want to take a look at the difference between "Product" and "Process".

###  Next Lesson: Engineering Product vs Process 

[ Onward! ](http://www.vikingcodeschool.com/software-engineering-basics/engineering-product-vs-process) [ or go to previous lesson... ](http://www.vikingcodeschool.com/software-engineering-basics/basic-principles-of-software-engineering)
