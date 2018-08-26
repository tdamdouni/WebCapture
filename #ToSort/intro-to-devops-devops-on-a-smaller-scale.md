# Intro to DevOps: DevOps on a Smaller Scale

_Captured: 2018-06-29 at 17:23 from [dzone.com](https://dzone.com/articles/intro-to-devops-devops-on-a-smaller-scale?edition=383278&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-06-29)_

###  DevOps is such a broad concept that it can be hard to get started. These people-focused steps will help you get started to prepare for the tools and philosophy. 

Read why times series is the [fastest growing database](https://dzone.com/go?i=283423&u=https%3A%2F%2Fwww.influxdata.com%2Ftime-series-database%2F) category.

DevOps is a really cool intersection in tech where processes, tools, and philosophy all collide. But the things that make it interesting are also the things that make it hard to understand and adopt. Being new to DevOps is hard-at least it was for me, so I want to do my part to make it easier for anyone else getting started.

The first time DevOps was mentioned to me at work, I nodded the way you do when you don't know what's going on, but you're pretty sure you can Google it.

![Image title](https://dzone.com/storage/temp/9495213-katy-intro-to-devops-blog-post-1.png)

It turns out it's kind of unGoogle-able because it's so broad. I ran into obstacles with every keyword. I found more words I had never heard. I branched into a thousand smaller searches until I forgot what I was trying to look up in the first place. There were so many tools to choose from, and each of them seemed to demand context I didn't have.

So I Googled every combination of DevOps best practices, but still, I felt like I was missing the DevOps magic.

Because there's a problem with trying to use solutions for global companies with millions of users and thousands of employees, even if they are the most successful models. My company, like the majority of tech companies, doesn't have millions of users and thousands of employees, and we need solutions that fit.

The most innovative DevOps strategies are impressive, and they originate mostly from big companies. Big companies have database teams to build strategies and collect data from the database. Big companies have network teams to orchestrate and monitor their network. Big companies can afford a team for nearly every problem. At average-sized companies, we don't have that. We have to stretch our expertise and make the best decisions we can. This almost always involves tradeoffs.

The problems big companies must solve are hard, of course, but that doesn't mean smaller companies have fewer or less difficult challenges. Almost all of us are trying to prioritize and compromise to make DevOps solutions that work for us. So where do we start?

Adopting DevOps doesn't start with adopting tools -- it starts with adopting the underlying values of the DevOps community.

![](https://2bjee8bvp8y263sjpl3xui1a-wpengine.netdna-ssl.com/wp-content/uploads/katy-intro-to-devops-blog-post-2.png)

## Insight

Insight in tech can come in a lot of forms. We can monitor our systems on different application, infrastructure and platform levels, for example. It's a growing trend, even among smaller companies, to use a combination of tools to do this. We might use one tool to collect logs, one to collect site traffic and another to manage scaling. Then, we might have one last tool to unify all of those data sources.

![Image title](https://dzone.com/storage/temp/9495210-katy-intro-to-devops-blog-post-3.png)

> _Too much insight._

That already sounds overwhelming to me. In the first two months of my job, really brilliant people explained a lot of concepts to me, but I felt like I was looking into the sun-my brain was melting and my eyes were watering. I didn't get it until the first project where I used our tool to get some metrics from an old Rails app of mine. I didn't need refined, granular data. I needed basic metrics from my application, such as response times, response codes and database query times. Even that small amount of data was enough to improve my code.

The tools we use to get insight have a job to do, but they shouldn't take up our resources. In DevOps especially, the tools we use should encourage our culture of collaboration, not create more barriers.

Seeing metrics from your application, even at the most basic level, is far more important than worrying about which tool to use.

## Communication

Communication is the hardest part of DevOps. It's probably the area I've seen the most talks on, the area we all need to improve and the area in which we fail the most.

Think about all the layers of communication: between team members and different teams, between my code and the person who uses it. We have to recognize that even with insight into our application's behavior if there's no communication, there probably won't be any progress.

We should think about the data and metrics we collect in the same way we think about the code we write. Will the next person understand our intention? If we're not careful, instrumenting our applications can cause more work for other people- even when that person is just you six months later wondering what you were thinking).

There's a bit of risk in assuming others will know how to interpret metrics. For example, I might get an alert when I use over 60 percent of a data node in my [InfluxEnterprise](https://www.influxdata.com/influxenterprise/) cluster (shameless plug). It's not necessarily because that data node is in danger, but rather because I'm thinking ahead to a scenario where two data nodes are running at 60 percent, one goes down and then the remaining node is immediately at 120 percent, which means I then have zero nodes available. Someone who didn't have my context might have a very different reaction to that alert, especially if they're getting paged at 3:00 a.m. Our intention isn't written into the data we're collecting, so it's up to us to make sure our intention is clear. In this case, it may be as simple as making the alert message straightforward.

It's also important to realize communication strategies are just as varied and unique as the companies that adopt them. Maybe your team emphasizes comments in the code or descriptive commit messages. Maybe your team wants a written history of the tools you've adopted. It's okay if you change successful communication tools and patterns to suit your organization.

## Conclusion

We are always going to understand our own teams, data and code better than any external source, so it makes sense that we adapt strategies that work for those anomalous organizations. They're successful and special, but remember that smaller companies that never have to worry about global domination are the majority.

![](https://2bjee8bvp8y263sjpl3xui1a-wpengine.netdna-ssl.com/wp-content/uploads/katy-intro-to-devops-blog-post-4.png)

If we're embracing DevOps, we're embracing the idea that we need more communication and insight, so the tools and practices we adopt should never stop us from sharing data, collaborating or building our culture.

Learn how to get 20x more performance than Elastic by [moving to a Time Series database](https://dzone.com/go?i=283422&u=https%3A%2F%2Fwww.influxdata.com%2Fresources%2Fbenchmarking-influxdb-vs-elasticsearch-for-time-series%2F%3Futm_campaign%3Ddbzone%26utm_medium%3Dpartner%26utm_source%3Ddzone%26utm_content%3D%26utm_term%3D).
