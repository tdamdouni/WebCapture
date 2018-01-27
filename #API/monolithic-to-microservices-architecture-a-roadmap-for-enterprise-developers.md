# Monolithic to Microservices Architecture: A Roadmap for Enterprise Developers

_Captured: 2017-11-28 at 09:54 from [dzone.com](https://dzone.com/articles/monolithic-to-microservices-architecture-a-roadmap?edition=337920&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-27)_

### The shift from a monolithic to a microservices mindset isn't easy. These steps will help enterprise developers make a plan to transition to microservices architecture.

The Integration Zone is brought to you in partnership with [Cloud Elements](https://dzone.com/go?i=109831&u=http%3A%2F%2Fresources.cloud-elements.com%2Fh%2Fi%2F232813135-the-definitive-guide-to-api-integrations-ebook%3Futm_campaign%3DAPI%2520Integration%2520eBook%26utm_medium%3Ddisplay%26utm_source%3Ddzone). What's below the surface of an API integration? Download [The Definitive Guide to API Integrations](https://dzone.com/go?i=109831&u=http%3A%2F%2Fresources.cloud-elements.com%2Fh%2Fi%2F232813135-the-definitive-guide-to-api-integrations-ebook%3Futm_campaign%3DAPI%2520Integration%2520eBook%26utm_medium%3Ddisplay%26utm_source%3Ddzone) to start building an API strategy.

For most enterprise developers with good enterprise app development experience, transitioning from a monolithic architecture mindset to a microservices mindset is not an easy task. There is a bit of confusion on what should be the next career goal or what tech area someone should dive into. There is also the baggage of proven experience and techniques that worked for a long time but might hinder our transformation effort.

I will try to focus on giving guidance to enterprise developers who might be tied so much into the current enterprise application development and are getting a bit confused on how to get off the ground.

This article is a mix of things enterprise developers need to think of differently from the so-called old school approach.

## **Your Strength as an Experienced Enterprise Developer Is of Huge Value**

There is so much out there that makes money for businesses that we all developed for years. We need people who can handle complex brownfield projects and eventually get them to a new home. Most places can't afford or face the bigger risk of stopping everything and just rebuilding a new product, so we need creative ways to build a new home underneath the old house, and eventually all that is left is new.

There are many modern techniques and tools that can transform both products and developers to the new world much faster than before, and this is the key. Enterprise developers are already comfortable dealing with different technology changes over time.

More than technology, there are a few key things that developers need to change in their attitude, team building efforts, and overall thought process. What I'm sharing here is not so much about microservices architecture but kind of a pre-step to get you ready for it.

Below are few soft guidelines; they are like lane markers on the road, and we should drive based on what we see - not drive rigidly by lane markings.

### **1\. Dynamic Vision With Quick Deliverables**

Have the vision to see things beyond today, but be open to seeing it differently as we learn new facts and opportunities.

### **2\. Fact-Based Measurable Progress Over a Perception-Based Approach**

More often, facts show a different story than our gut feeling. It is important to document facts when solving key issues. For example: a big and ugly looking SQL is disturbing and it is tempting to fix it right away or jump to the assumption of that being performance blocker. But in reality, that query might be finishing up in 30ms and you are losing time elsewhere. Why lose all that precious time on silly things that will not add much value?

### **3\. You May Not Get It Right Even If You Get All the Time You Need**

Productivity is a combined measure of quality, quantity, and time. Driving the team for perfection is self-satisfying, but not necessarily helpful in all cases. Try to be dynamic and creative, to find a solution that is best for a given scenario.

### **4\. Fail Fast**

If we misunderstand, it will encourage the team to push bad code without testing to prod and claim it as an agile process with a more fail-fast approach.

Fail-fast is an idea to quickly try building a new product or feature to get more visibility. If this is not what clicks with customers eventually, we want to know earlier rather than later. It is a lot easier to try something you think is cool and find out the reality quickly than to keep living in the planning phase.

### **5\. What Is Agile?**

This is very old, but I still like this deck: <http://agilemanifesto.org/>. If you just look at this, you can quickly say if your team is agile in practice or not. In my opinion, it has all the good stuff nailed down in those four points.

### **6\. Proactive Thinking and Reactive Implementation**

We need to think proactively to know scenarios and what to expect, but we may need to deliver features more iteratively that may not address all the concerns of proactive thinking in the first cut. By the time feature is ready for prime time use, you may get things in place, but if a feature is not much used, why build a storm-shelter when a temporary shelter saves the day?

### **7\. The QA Team Is Not There to Find Technical Bugs in Your Code**

It is an age-old approach to depend on the QA team to deliver code to production. For many years, I was used to delivering code to production with no or minimal QA team. The key is to build enough unit testing and functional testing, and I am a big fan of automated testing: mostly custom automation solutions, taking the best of the tools available.

### **8\. Build for Now and We Can Cross the Bridge When We Get There**

Build a clean and simple solution that solves the problem. What comes next is something I would not imagine and build upfront. If we do it right, the code can be easily extended or refactored as and when we see the need.

### **9\. Don't Burn That Old Bridge Before Getting a New One in Place**

When we are replacing some existing feature with a new approach, it is important to make sure we get the new approach fully working and accurate before the enthusiastic cleanup of older code. We should not end up with, "We can't use the product because the old feature is not available and the new feature doesn't work."

### **10\. Focus on High-Risk Functionality First**

It is important to not to lose sight of our main goal when building any solution. If specific tasks are high-risk due to complexity or new technology, it is important to get it right than spending time on fine-tuning things we know how to get working quickly. Most often, I see losing valuable time and finding blockers close to release due to the wrong priorities.

### **11\. A Polyglot and Heterogeneous Environment**

Just because the product is built in [ASP.NET](http://ASP.NET) or with a SQL/OracleDB backend, there is no reason to get locked into this. With an API-based approach and microservices, you can start building or migrating an API over time to technology that matters in the specific scenario.

We can also take advantage of out-of-the-box messaging, streaming, distributed cache, search, troubleshooting solutions, and complement the existing product with minimal impact. This approach helps us to focus more on the product domain and deliver new features quickly.

### **12\. It Is Easy to Get Exposure but Not Experience**

You can gain exposure to new technology easily by watching videos and reading a few articles. While this helps you to talk about it, there is no shortcut to experience. It is important to build this experience in key areas of your interest while you gain exposure to wider areas.

### **13\. Start Small and Start Early**

Build something small- even a hello world app to start with. Then try to go a little further. Don't keep dreaming of a big product plan that never materializes. Once you start, you will face technical challenges that are beyond hello world apps and will eventually get pulled into deeper hands-on experience.

### **14\. It's a Team Effort**

In every situation, there is something good, and in every team member, there is some good quality you can appreciate and take advantage of. It important to build teams that complement each other and work towards one goal, one product, and one team attitude.

The [State of API Integration Report](https://dzone.com/go?i=201150&u=http%3A%2F%2Foffers.cloud-elements.com%2Fthe-state-of-api-integrations-report-2017%3Futm_campaign%3DState%252520of%252520API%252520Integrations%252520Report%26utm_source%3Ddzone%26utm_medium%3Ddisplay) provides data from the [Cloud Elements](https://dzone.com/go?i=201150&u=http%3A%2F%2Foffers.cloud-elements.com%2Fthe-state-of-api-integrations-report-2017%3Futm_campaign%3DState%252520of%252520API%252520Integrations%252520Report%26utm_source%3Ddzone%26utm_medium%3Ddisplay) platform and will help all developers navigate the recent explosion of APIs and the implications of API integrations to [work more efficiently in 2017 and beyond.](https://dzone.com/go?i=201150&u=http%3A%2F%2Foffers.cloud-elements.com%2Fthe-state-of-api-integrations-report-2017%3Futm_campaign%3DState%252520of%252520API%252520Integrations%252520Report%26utm_source%3Ddzone%26utm_medium%3Ddisplay)
