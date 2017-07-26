# Programming Without a Framework

_Captured: 2017-07-08 at 09:20 from [dzone.com](https://dzone.com/articles/programming-without-a-framework?edition=306238&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-07)_

[Download Microservices for Java Developers](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034): A hands-on introduction to frameworks and containers. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=202129&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F157034).

I've recently been working on a nice project that was small enough to make me feel free to experiment and, on the other hand, big enough to validate my ideas and see how they scale. One of the experiments that I've conducted throughout the project was, _can I do it without using any major framework? Is is going to take more time? Is it going to be considerably harder?_

## The Approach

Obviously, the ideas presented here are nothing new and quite a few people consider it the right way to do software. Therefore, if you're familiar with the notions of dependency inversion or using many small libraries instead of one big framework, this section won't be very enlightening.

As I already hinted in the previous paragraph, I decided to rely heavily on the Dependency Inversion Principle, so that whatever extra "infrastructure" code I produced in the process is what I'd adjust to my needs, not the other way around.

To be more specific, for any kind of code that would "normally" be provided by a framework, I started with an interface that describes my actual, current needs at that moment. Once the interface design was complete, I implemented it in the infrastructure layer of my application. Essentially, I went into a loop of inventing some kind of "API of my dreams" for a given problem and then provided myself with exactly that.

Since I had a hard deadline on the project, I treated the interfaces as a kind of fallback scheme in case of timeline issues. If anything wrong was to happen, I could try to bring in some heavy artillery (i.e. Spring) and implement the interfaces with that.

As long as there were no issues with the timeline or my low-level programming skills, I decided to stick with using (relatively) small libraries and coding some of the important chunks myself.

## Example: REST Endpoints

I guess that the code for exposing a REST endpoint is a pretty good example of functionality that would normally be provided by a framework like Spring, Ratpack or the like. I also think it's a good example for this post, as cool ways of defining endpoints are supposedly an important thing when choosing a framework.

My "dream API" in this case was pretty simple. It required the infrastructure layer to implement two interfaces and defined two extra type aliases (we're in the Kotlin world):
    
    
        fun <T : Any> body(clazz: KClass<T>): T

Obviously, I didn't write all this at once. I iterated over it feature by feature, method by method. If I remember correctly, my first endpoint required just the "post" support and a request body.

During application startup, an instance of the `Router` implementation is passed onto a method responsible for initializing all the routes in the application:
    
    
        router.get("/groups/:id/members") { req, res ->
    
    
        router.post("/groups/:id/members") { req, _ ->
    
    
        router.get("/groups/:id/lessons") { req, res ->
    
    
        router.post("/groups/:id/lessons") { req, _ ->

Your opinion might differ here, but I really think this is a nice piece of API. What's most important here is that it does everything I needed for the particular use cases of this application.

Now, I don't really want to show the whole implementation here for a few good reasons, but I'd like you to know that it's much simpler than many people think.

For instance, a simple mechanism for handling path parameters using the Servlet API is a matter of splitting Strings and looping over URI parts:
    
    
        val pathParams = mutableMapOf<String, String>()
    
    
        for (i in pathParts.indices) {
    
    
            if (pathParts[i].startsWith(":")) {
    
    
                val key = pathParts[i].replace(":", "")
    
    
                pathParams.put(key, uriParts[i])

Another good example connected with exposing REST endpoints from your application is starting an embedded web server. Some people are so happy that frameworks like Spring Boot have this functionality out of the box even though starting the server by yourself is actually a piece of cake:
    
    
    fun main(args: Array<String>) {
    
    
        server.handler = HandlerList(routerServletHandler())
    
    
        servletHandler.addServletWithMapping(RouterServlet::class.java, "/*")

## Results

I'm glad to report that my little experiment was successful and the application was delivered on time without using any major frameworks. I'm also glad to report that writing applications this way is not a struggle. On the contrary, I had a lot of fun and I didn't feel like I was going much slower than using some of the popular frameworks.

Fun aside, I'm not sure whether there's any important lesson learned during this experiment. One side of me keeps asking me why do we, developers, blindly follow the framework hype when there's not _that _much benefit to it (if any). On the other hand, is there any point in reinventing the wheel every single project that we start, especially in the world of microservices where there's so many of them?

[Download Building Reactive Microservices in Java](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031): Asynchronous and Event-Based Application Design. Brought to you in partnership with [Red Hat](https://dzone.com/go?i=219225&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F166031).
