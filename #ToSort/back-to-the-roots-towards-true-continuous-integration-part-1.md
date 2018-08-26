# Back to the Roots: Towards True Continuous Integration (Part 1)

_Captured: 2018-04-27 at 15:55 from [dzone.com](https://dzone.com/articles/back-to-the-roots-towards-true-continuous-integrat?edition=376213&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-04-27)_

[Discover the easy-to-use control panel and API](https://dzone.com/go?i=286445&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F417595668%3B219047635%3Bx) that let you spend more time coding and less time managing your infrastructure. Brought to you in partnership with [DigitalOcean](https://dzone.com/go?i=286445&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F417595668%3B219047635%3Bx)

In this article, I would like to show you what many people believe CI is, what is true Continuous Integration, and what is not CI. Also, I will give you some examples to better understand it.

## What Is CI?

[CI](https://apiumhub.com/tech-blog-barcelona/benefits-of-continuous-integration/) (continuous integration) is a software development practice in which a continuous integration server polls a version control repository builds an artifact and validate the artifact with a set of defined tests. It is a common practice for most enterprises and individuals… and this is not the true Continuous Integration definition, sorry for the joke.

## What Is True Continuous Integration?

True Continuous Integration is not simply some kind of "Jenkins/Travis/Go/Teamcity" that polls the git repository of the project, compiles it, and runs a bunch of tests against the artifact. In fact, this is the less interesting part of CI, which is not a technology (like Jenkins) but an agile practice created by Grady Booch and adopted and prescribed by the [Extreme programming methodology](https://apiumhub.com/tech-blog-barcelona/extreme-programming-tips-advantages/).

As an analogy with another Extreme programming technique, [TDD](https://apiumhub.com/tech-blog-barcelona/advantages-of-test-driven-development/) is not about [unit testing](https://apiumhub.com/tech-blog-barcelona/top-benefits-of-unit-testing/) (although it uses unit testing), but about feedback and obtaining feedback as soon as possible to speed up the development cycles (which is implemented in a concrete usage of unit testing).

With CI, software is built several times a day (ideally, every few hours) - every time a developer integrates code in the mainline (which should be often) in order to avoid "integration hell" (merging code from different developments at the end of a development interaction). CI avoids this "integration hell" by integrating code as soon as possible and forcing team members to view what other developers are doing to make shared team decisions about new code.

The methodology states that every team member integrates into the mainline as often as possible. Every contribution to the VCS (Version Control System) is potentially a release, so every contribution should not break functionality and should pass all known tests.

A CI server will construct an artifact from the last sources of the mainline and pass all known tests. If there is a failure, the CI server will warn all members of the team of the state of the build (RED). The maximum priority of the team is to keep the build in its default value (GREEN).

## What Is Not CI?

Once we realize that CI is far more than the simple use of a CI server, we can state that:

  * Working with feature branches and have a CI checking master is not CI.
  * Working with pull requests is not CI.

It's important to note that I'm not judging in terms of good/bad practices; both feature branches and pull requests are simply other methodologies different than CI.

Both feature branches and pull requests mandates that the work must be done in another branch different than the master (the one monitored by the CI Server) this leads to longer cycles before they could be merged into master.

Feature branches and pull requests rely profoundly on team resource/task planification to avoid refactors on one task(branch) that affects developments on another task(branch) minifying the threaded "integration hell."

An example of integration hell: we have the following code; two classes that leverage the API, and the rest calls to an external API:
    
    
        public function __construct(string $host, string $username, string
    
    
            $request = \Requests::GET($this->host.self::USERS_API_PATH,
    
    
        public function __construct(string $host, string $username, string
    
    
            $request = \Requests::GET($this->host.self::PRODUCTS_API_PATH,

As you can see, both blocks of code are very similar (the classical code duplication). Now we are going to start two development features with two development branches. The first development must add a telephone number to the request to the Products API; the second one must create a new API to query all cars available at a store. This is the code in the Products API after adding the telephone number:￼
    
    
        public function __construct(string $host, string $username, string

The developer has added the missing field and has added it to the request. The developer of branch 1 expects this diff as the merge with a master:

![true continuous integration](https://apiumhub.com/wp-content/uploads/2018/04/Screen-Shot-2018-04-06-at-11.07.36-1.png)

The problem is that developer 1 does not know that developer 2 has made a refactor in order to reduce code duplication because CarAPI is too similar to UserAPI and ProductAPI, so the code in his branch will be like this:
    
    
            $request = \Requests::GET($this->host.$this->apiPath, $headers,
    
    
        public function __construct(string $host, string $username, string
    
    
            parent::__construct($host, "/cars", $username, $password);
    
    
        public function __construct(string $host, string $username, string
    
    
            parent::__construct($host, "/users", $username, $password);
    
    
        public function __construct(string $host, string $username, string
    
    
            parent::__construct($host, "/products", $username, $password);

So the real merge will be:

![true continuous integration](https://apiumhub.com/wp-content/uploads/2018/04/Screen-Shot-2018-04-06-at-11.10.57.png)

Basically, we will have a big conflict at the end of development cycle when we merge branch 1 and branch 2 into the mainline. We will have to do a lot of code reviews, which will involve an archaeological process of reviewing all past decisions in a development phase to see how to merge the code. In this concrete case, the telephone number will also involve some kind of rewrite.

Some will argue that developer 2 should not have done a refactor because planning stated that he has to develop _only_ CarAPI, and planning stated clearly that there should be no collision with UserAPI. Well, yes…but to make that this kind of extreme planification work, there should be a good planning of all resources, we should have a lot of architectural meetings involving developer 1 and developer 2.

In these architectural meetings, developer 1 and developer 2 should have realized that there was some kind of code duplication and they have to decide to intervene and replan, or do nothing and increase technical debt, moving the refactor decision to future iterations. This may not sound too agile, right? The point is that is difficult to mix agile and non-agile practices.

If we do feature branch/pull requests, a full iterative planification process works better if we're doing agile continuous integration. Again, I'm not stating that feature branches/pull requests are good/bad tools, I'm simply stating that they are non-agile practices.

Agile is all about communication and continuous improvement, and it's all about feedback as soon as possible. In the agile approach, developer 1 will be aware of the refactoring of developer 2 in the beginning, being able to start a dialog with developer 1, and check if the type of abstraction that they're proposing will be the correct one to fit, and the addition of a telephone number.

**OK….but** **wait! I need a feature branch! What if not all features are deliverable at the end of an iteration?**

Feature branches are a solution to a problem - what to do if not all code is deliverable at the end of an iteration - but it is not the only solution.

CI has another solution to this problem - "feature toggles." Feature branches isolate the work-in-progress feature from the final product via a branch (the WIP lives in a separate copy of the code), feature toggles isolate the feature from the rest of the code using.. Code!

The simplest feature toggle one can write is the dreaded if-then-else, is the example you will find in most sites when you googled "feature toggle." It is not the only way to implementing, as any other type of software engineering you can replace this conditional logic with polymorphism.

In this example in Slim, we are creating in the current iteration a new REST endpoint, we do not want to be ready for production, we have this code:￼
    
    
        $logger = LoggerFactory::getInstance($settings['logger']['name'],

We can define the feature toggle with a simple _if_ clause￼:

We can refine our code to express better what we're doing and be able to have several environments (maybe for having a test AB situation?)￼￼
    
    
    $app->group("", function () use ($app, $configurationMap){

The advantages of this technique is consistent with the main goal of CI (having constant feedback about code integration/validation and collisions with other developments), the code in progress is developed and deployed into production, and we have constant feedback about the integration of the new feature with the rest of the code, leveraging the risk of enabling the feature when it's developed.

It is a good practice to remove this kind of toggle from code once a new feature has been stabilized in order to avoid adding complexity to the codebase.

We have arrived at the end of this first part of true Continuous Integration. We have rediscovered that continuous integration is "not only" using a CI server but adopting a practice with perseverance and discipline. In the second part, we will talk about how to model a _good_ CI flow.

[Learn about the optimized the configuration process](https://dzone.com/go?i=286446&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F417595650%3B219047638%3Br) to save your team time when running and scaling distributed applications, AI & machine learning workloads, hosted services, client websites, or CI/CD environments. Brought to you in partnership with [DigitalOcean](https://dzone.com/go?i=286446&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F417595650%3B219047638%3Br)
