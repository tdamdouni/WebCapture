# DevOps: Who Does What (Part 1)

_Captured: 2018-07-15 at 03:06 from [dzone.com](https://dzone.com/articles/devops-who-does-what)_

Easily enforce open source policies in real time and reduce MTTRs from six weeks to six seconds with the Sonatype Nexus Platform. See for yourself - [Free Vulnerability Scanner.](https://dzone.com/go?i=290455&u=https%3A%2F%2Fwww.sonatype.com%2Fsoftware-bill-of-materials%3Futm_campaign%3Ddzone%252520-%252520AHC%26utm_source%3DDZone%252520-%252520AHC%2525202018%26utm_medium%3DDZone%252520-%252520AHC%2525202018)

The following is an excerpt from a presentation by Cornelia Davis, Senior Director for Technology at Pivotal, titled "_DevOps: Who Does What_."

You can watch the [video of the presentation](https://www.youtube.com/watch?v=kpuJSpp3hhA), which was originally delivered at the 2017 DevOps Enterprise Summit in London.

Throughout the years, I've had the great opportunity of working with very, very large enterprises across all verticals. My background is as a technologist, I'm a computer scientist, and initially, I spent a lot of time talking tech at the whiteboard. But then I realized that there was so much more that needed to change, which is why I'm sharing now about the organizational changes that can support our technology needs.

## My First Question to You Is, Is This Your Reality Today?

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.36.40-AM.png)

We have different business silos across the organization and different individuals that are coming from those silos. When we have a new idea for a product, we kick off a project and individuals go into the project to do some work.

The first individuals from the first silos come in, and they generate their artifact. Then what do they do? They throw it over the wall to the next step. If you look at this slide below you'll notice once they're done they leave the project.

If for some reason we have to go backwards, we have to figure out how to get them back into the project. And, so it goes through each silo. We all recognize that this is a slow and challenging process. If it only moved linearly, it might be okay. But we all know that it goes this process goes backwards, and forwards, even circular!

But that's not even the biggest problem of these things.

The biggest problem is that each one of these organizations are incentivized differently.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.37.33-AM.png)

> _My favorite examples are App, Dev, and QA -- so let's look at these._

Application Development is almost always incentivized by 'Did you release the features that you promised on time, and ideally on budget?' And, if you released the features on time you get a 'Way to go, you achieved your goals.'  
Then it moves over to QA.

What is QA incentivized on? Well, they're responsible for quality. So they are generally incentivized by the number of bugs that they have found and fixed.

Now, let's look at these things in combination. What happens when the application development process starts to fall a little bit behind? Developers start working late into the evenings. They work on weekends, they start working very unsustainable hours, and what happens? Quality suffers, but they hit their features on time.

Well, when they throw that over the wall to QA, what's gonna happen now?

QA is going to find more bugs. Way to go! So we've got locally optimized metrics that do not create a globally optimized solution. That's a big problem.

Well, the answer is really simple…

### The Answer Is Balanced Teams!

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.39.10-AM.png)

What we're going to do is we're going to center things around a product and the product team is incentivized to deliver value to a customer, to deliver value to some constituency.

For example if I'm in an e-commerce scenario:

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.40.06-AM.png)

I have a product team that is really about the best experience around showing product images, recommendations, soliciting reviews, or it could be some back office product that is enabling your suppliers. These are all the different product teams.

There's been a lot of research, and a lot of discussion, and a lot of proof points that product teams are really the way to go.

But what if we don't have product teams? What if we have different roles within the SDLC, how do you create product teams of these different disciplines to come together into a product?

### We're Going to Try and Put Things Through the Sorting Hat

If you have been living in a cave for the last 10 years, and you don't know what the sorting hat is, this comes from Harry Potter. When new students come to Hogwarts School of Witchcraft and Wizardry on their first day, each one of them places the hat on their head and they get sorted into one of four houses, and that's the house that they live in for the next seven years.

So we're going to take those roles and we're going to sort them into houses. But the question then is, what are the houses that we're going to sort into? So let's take a little bit of a tangential ride over to the side and think about a couple of houses. (I'm going to end up with four houses in the end, but I want to start with two.)

The left part of this slide you've all seen for the last several years.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.42.40-AM.png)

That is where we were maybe 15 years ago. IT was responsible for the entire stack from the hardware all the way up through the application.

Then VM Ware came along and virtualized infrastructure.

Then a whole host of people made infrastructure as a service available. Amazon web services of course being kind of the behemoth of that.

That made it so that we could just get machines, EC2 machines for example, and then we could stand up everything that we needed on those machines. Getting machines was easy.

Then in the last five years or so, we've taken that abstraction up another level and we've created application platforms where we have individuals who can be building applications, and the only thing that they need to worry about is their application code.

What's important about that application platform is that it generates a new set of abstractions. Those abstractions are at a higher level. They are fundamentally the application, or maybe some services there in support of that application, and it allows us to not do things like implement security by creating firewall rules that machine boundaries, but instead allows us to implement security at the application boundary.

This new abstraction is one of the key things that's happened in platforms over the last five years. It's given us something really interesting and really important. It's allowed us to define two different teams. And it's defined a contract between those teams that allows these teams to operate autonomously.

When we hear about all of the different goals of an enterprise, they all talk about needing to bring software solutions to market more quickly, and more frequently. So agility, and autonomy, and teams is incredibly important. We're always looking for those boundaries where we can create more autonomy.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.44.26-AM.png)

### Now the Application Team…

The team that's going to create the next mobile app or the next web app or even some analytics app for example, can focus on building that application, and they don't need to worry about even the middleware that sits below it.

They're responsible for creating the artifact. They're also responsible for configuring the production environment, deploying to production. They are doing Dev and Ops. It's not necessarily the same person, but it is the same team. They're deploying to production, they're monitoring. When they notice that they need more capacity, they're scaling so that they can achieve better performance. They deploy new versions when they need to.

It's entirely up to them.

### Now There's Another Product Team, and That Is the Platform Team

So that's the team that's providing the platform, and notice that they're doing exactly the same things.

They are deploying the platform, they're configuring it, they are monitoring it, they are upgrading it when they need more capacity, or upgrading it to the next version. They're doing the same things but they have their own products that they're working on. So the product orientation is really key.

This separation gives us the first two houses that were going to sort into. The APP team, and the platform team.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.45.26-AM.png)

> _Now let's take all of these roles that come from traditional organizations and start sorting them. And, so here's our two houses, the APP team and the platform team._

We're going to do this piece by piece and I'll explain the steps as we go along.

The first ones that we're going to do is we're going to start with the purple bubble there. Before I sort them, notice that this Middleware and App Dev team is actually taking care of both the Middleware and the application development.

In retrospect, having worked in this new world for the last five years, I find this kind of counterintuitive because why would somebody who's creating an application i.e., using the middleware be in the same group as the middleware itself? To a large extent, it's because in the past middleware required a great deal of expertise. You had to know a lot about the middleware to be able to effectively program against it. That's something that we're trying to move away from. We're having more agile middleware platforms and so on.

Notice what happens here.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.47.17-AM.png)

We've got middleware and we've got App Dev, and we break those apart. We put the middleware engineers inside of the platform team. They're part of that team providing the capabilities that the APP team can then use. Then we take kind of a full stack application development team and put them up in the APP team. We've got front end, and we've got back end. All of those individuals are there.

That one's pretty straightforward.

The next one that's also pretty straightforward is we're going to pull some of the folks out of the infrastructure team, the folks responsible for building out the servers and the networks.

You might have noticed I put virtualized infrastructure and platform together in one team that many of our customers actually keep those as separate, but in this case it really wasn't important to make that separation. You could be separating the platform team into two separate individual ones as well. The thing that I would caution you is you need to make sure that you then have a very crisp contract between the platform team and the infrastructure team.

I'll be honest with you, that's a little bit harder to find at the moment, so that's part of the reason I've put them together.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.47.26-AM.png)

> _Again, server build-out, network build-out, they are part of the platform team providing the view of the infrastructure up to the App team._

The next one that we'll talk about here is what I like to call the control functions.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.47.29-AM.png)

There is information security for example, and change control. Why did I move them at the same time? Change control was usually often coming out of the infrastructure team, and information security coming out of the chief security office. I moved them at the same time because they share a common characteristic. They are functions that today can stop a deployment. They are functions that on every release, on every release into production, they need to give their blessing.

We've seen when it comes to the very end, and we find problems in information security or any other types of security, it can actually stop things. There's a great huge ball of things that we need to check off.

These functions here, information security and change control should engage with your teams that are providing the platforms, and the automation around the deployments to ensure that their concerns are satisfied. Their concerns are not wrong. It's just the way that we've been solving them is something that's in need of transformation.

In Part 2, we'll talk about Ops.

Automate open source governance at scale across the entire software supply chain with the Nexus Platform. [Learn more.](https://dzone.com/go?i=290456&u=https%3A%2F%2Fwww.sonatype.com%2Fwp-enforce-open-source-policies-with-confidence)
