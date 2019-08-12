# What Is Serverless Architecture?

_Captured: 2018-09-14 at 07:02 from [dzone.com](https://dzone.com/articles/what-is-serverless-architecture?edition=396191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-13)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

This just might be the beginning of the end of an era in the world as we know it. Are the machines already talking over? Not literally the "Terminator" movie scenario, but indeed, serverless architecture is getting us a step closer to independence from humans while it brings us much closer to the machine dependency. Let's roll back a little and start at the beginning.

Serverless architecture, or better yet, serverless computing as it's also known, refers to applications that are dependent on third-party services and custom code that's running in ephemeral containers.

Considering its name, serverless architecture doesn't mean that it runs its code without servers. The name it has, "serverless computing_"_, is used only because the person or a company owning the system does not have to purchase or rent servers/virtual machines for the back-end code to be able to run. Simply put, serverless architecture is a way of building and running applications and services with no need, whatsoever, for infrastructure management.

Your application will still be running on servers, but bare in mind that [AWS Lambda](https://aws.amazon.com/lambda/) or other hosts do all of the server management. We conclude that the user no longer needs to scale, provision, and maintain servers to run his application, database or storage system.

## Why Should I Choose Serverless Architecture?

Using serverless architecture will significantly help developers focus more on their core product. If not for serverless, developers would still be worrying about managing and operating servers or runtimes, whether managing them on the cloud or on-site. This way, the developer's focus will solely be on individual functions in their application code. Services like AWS Lambda, Google Cloud Functions, Firebase and Microsoft Azure Functions will take care of the physical hardware, virtual machine operating system as well as the web server, while you would only need to worry about one thing -- your code.

## Who Are The Ones That Should Be Using Serverless Architecture?

If you have a small number of functions that you need to be hosted, you should consider switching to a serverless provider. Considering that your application is more complex, serverless architecture can still be a good choice since it comes with lots of benefits, but you'd need to architect your application quite differently. Some clear benefits are easier concurrency management at scale and optimizing resource usage. If you already have an existing application, this might not be the best solution. Consider migrating smaller pieces of the application into serverless functions over time.

## The Drawbacks Of Serverless Architecture

Since everything else in life has downsides and drawbacks, it would be unwise to believe that serverless architecture is flawless. Let's talk about what we can expect regarding the disadvantages.

Problems that occur are vendor control and vendor lock-in, but also security concerns as well as multitenancy problems. Considering that you give up system control while implementing APIs, it can cause system downtime, forced API upgrades, functionality loss, as well as unexpected limits and cost changes.

Serious drawbacks, though, are the essential tools to work with we seem to be missing. Developers depend on vendors for debugging and monitoring tools. Luckily, [Dashbird](https://dashbird.io/) has an [observability solution](https://dashbird.io/features/) to ease the pain.

While fighting a fight without operational tools, there is another problem causing the flawed usage of serverless architecture, and it's the architectural complexity. To decide how small a function should be, it takes quite some time to assess, implement and perform a test. The easiest way to perform such a test is with this [Step Functions state machine](https://github.com/alexcasalboni/aws-lambda-power-tuning) by AWS Sr. Technical Evangelist [Alex Casalboni](https://mobile.twitter.com/alex_casalboni).

## Serverless Architecture And Its Advantages

Keeping it simple, serverless architecture is an outsourcing solution allowing you to pay someone else to manage your servers, databases, and even application logic that you might manage yourself otherwise. You would pay less for your managed database because a vendor that hosts you is running thousands of very similar databases.

Reduced packaging and deployment complexity is yet another example of how packaging and deploying FaaS functions is simple if you compare it with the deployment of an entire server.

"Green" computing is considered as a great hit among developers and rest of the population. Since over the last couple of decades the number of servers increased drastically, so did the need to serve those servers with sufficient power supply. Therefore, large sized data centers in the world came to the existence. Extremely large companies such as Google, Apple, Facebook etc. are fighting their way through saving the environment from the pollution they cause by implementing and moving their servers on the clouds and moving their data centers near renewable energy sources, so that way they fight against the fossil-fuel burning impact on sites like those. Those "clouds" never produce rain, so your Facebook account is quite safe, do not worry. Making these differences should further lead to the far more efficient use of resources across the data centers. By making those differences, people are reducing the environmental impact which can be compared to a traditional capacity management approach.

## Conclusion

Serverless architecture is something you implement if you are in need of it. If not, learn more about it, and you might discover that you need it, but you weren't aware of that fact, yet. Feel free to comment in the comment section below or visit our [blog](https://dashbird.io/blog/) and find an article of interest to start a discussion with other readers! Feel free send us a question, and we'll gladly help you out with any doubts that might concern you.

_We aim to improve [Dashbird](https://dashbird.io/) every day and user feedback is extremely important for that, so if you have any feedback about these improvements and new features! We would really appreciate it!_

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)
