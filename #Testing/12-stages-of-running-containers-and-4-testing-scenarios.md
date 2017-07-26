# 12 Stages of Running Containers and 4 Testing Scenarios

_Captured: 2017-03-08 at 01:05 from [dzone.com](https://dzone.com/articles/12-stages-of-running-containers-and-4-testing-scen?edition=276883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-07)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

This blog post is a brief summary of our webinar hosted together with Codefresh on Thursday, February 9, 2017. The webinar includes two talks: "Docker Inside/Out: The 'Real' Real World of Stacking Containers in Production" by Daniel van Gils and "Testing Strategies for Docker-Driven Development" by Alexei Ledenev.

If you missed the webinar, [click here](https://www.youtube.com/watch?v=dbzbpscFDt4&t=9s) to find out more about tips and tricks to run Docker containers in production and review the testing strategies for your deployments.

## The 12 Stages of Running Containers in Production

The first couple of stages are very straightforward. You work on your project with the methods that you already know. Then, you hear about containers. You see what they can do and it looks magical!

Next, at stage three, you start to think, "How can I implement containers in my current workflow?" You conduct some research to get the idea, but you need practical knowledge and experience to use containers in production.

Stage four: meet Your mentor! A mentor is someone who's already using containers in production and knows more than you, and is happy to take you on the containers journey.

Apply the artichoke model, which shows how each role in your company can benefit from containers. Everybody needs to understand the core concepts of containers and their impact on the organization. It's part of change management.

Stage five: now, you are crossing the threshold and starting to understand the containerization machine. Try using containers with a simple project, and then move to more difficult ones. This will involve a lot of testing (more about testing from Alexei's talk).

Golden rule: Make sure that containers work on your local machine before moving to production! Think global, act local.

Stage six: you are using the containers, and run into some problems and have made some mistakes. This is part of the process. Try to take a step back and take your time to find a solution. No shortcuts. This is the stage where most of the developers realize that their Docker image contains too many components and half of them are not needed. Try to clean your image.

Remember: sh*t in, sh*t out. You can't polish a turd.

![](http://blog.cloud66.com/content/images/2017/02/Screenshot-2017-02-17-17.58.43.png)

Welcome to stage seven. Now, you are more aware of what your container image needs. You need to keep it slim, secure, speedy, stable, set! (That's K.I.S.S.S.S.S.)

  * **Slim: **Remove all the layers that you don't need.
  * **Secure:** Ensure you have the latest updates and remember to remove all secrets.
  * **Speedy: **Follow best deployment practices and run performance tests.
  * **Stable: **Use version numbers for your Docker files.
  * **Set: **Immutable; don't put databases or complicated volumes into your containers. You can, but the technology is still too new.

Stage eight. It's time for production! First, let's do a reality check. Does everybody really use the microservices? The answer is no.

  * **60% of developers use a monolith containerization. **This is understandable as it is a part of the learning curve.
  * **30% of developers use an API-first approach**, mainly when dealing with the frontend.
  * **7% of developers split their architecture with the containers. **This includes workers, API and background processes, etc.
  * **3% of developers are truly using microservices** in their projects.

Stage nine. Now, you know all the parts of the containers ecosystem and what you need to look after. This is your container nursery:

![](http://blog.cloud66.com/content/images/2017/02/Screenshot-2017-02-20-11.37.45.png)

Stage ten: proof of concept. Done. You know how to implement the containers and now, you need some head space -- check what services and products are out there, and observe the market for new technologies.

Stage eleven. With the knowledge and the experience you gained, you have a new approach and you understand what you need to fit containers in your infrastructure.

Stage twelve. You are a containers hero. You and anybody who joined your journey understands the power of containers and how it can be applied to all the projects and divisions.

## 4 Testing Scenarios

Alexei started with listing some of the benefits of using containers, such as portability, speed, configurations, flexibility, etc., with a brief description of the Docker architecture components.

Before we move to the test scenarios, these are the components for the demo app and tests:

  * **Demo app: **All the tests are based on the simple Rest API server that is written in Golang.
  * Node.js application.
![image](http://blog.cloud66.com/content/images/2017/02/Screenshot-2017-02-17-17.47.40.png)

### 1\. Modifying the Existing Pipeline

Scenario number 1 (AKA the naive approach) involves modification of the existing pipeline.

See the first scenario demo starting at 29:30 in the webinar.

The outcomes: You'll achieve a familiar CI flow, app portability, and smaller Docker image, but won't have a portable dev or test environment.

This means it isn't possible to reproduce the same development or testing environment outside the CI. The same procedure would have to be repeated for each machine.

### 2\. How Can We Improve the Situation?

Place all the Cl flows (compile and test) in the container.

See the second scenario demo starting at 33:38 in the webinar.

As a result, you'll gain a simple CI flow, application portability, and a portable dev and test environment. On the downside, the Docker image gets bigger and polluted with some unneeded dependency packages. The image has to be rebuilt each time on the code or test changes and you need to decide on how to manage tests results.

### 3\. Split the Image Into Two

In this test scenario, you still have one Docker file with the application and test code, but you need to extract some of the image layers and split it into two images.

See the third scenario demo starting at 38:31 in the webinar.

Now, the application has portability and a portable dev and test environment, and you end up with two separate images and one Docker file -- but you still need to rebuild the whole Docker image on code or test changes. Also, you need some shell "magic" to create a clean app image.

### 4\. Create a Docker Automation Flow

You can do this by using containers for every step, including building and testing.

See the fourth scenario demo starting at 42:56 seconds in the webinar.

You'll achieve application portability, a portable dev and test environment (so that you can build and test anywhere), a small app image, and fast build. However, you'll still need a tool to automate and orchestrate Docker build flows, such as bash, ansible, dobi, [Habitus.oi](http://www.habitus.io/), or Docker CI/CD services like [Code Fresh](https://codefresh.io/) or [Cloud66](http://www.cloud66.com/).

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
