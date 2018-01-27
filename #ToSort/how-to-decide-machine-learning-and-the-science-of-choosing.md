# How to Decide: Machine Learning and the Science of Choosing

_Captured: 2017-11-09 at 23:44 from [dzone.com](https://dzone.com/articles/how-to-decide-machine-learning-and-the-science-of?edition=334850&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-08)_

[Find out how AI-Fueled APIs from Neura](https://dzone.com/go?i=244221&u=https%3A%2F%2Fhubs.ly%2FH08wTJ10) can make interesting products more exciting and engaging.

> "If you choose not to decide, you've still made a choice." \- Neil Peart 

Decisions can be fatiguing and prone to bias -- not just for individuals but for whole organizations. The bigger the decision and the more complex the inputs, the greater the consequences of failure. Consider the vetting of millions of tax returns. Consider an airline that needs to decide when and where to perform maintenance between flights. Or consider an emergency response agency that needs to decide where to distribute disaster services. Examples range across manufacturing, healthcare, finance, and beyond -- and in each case, the decision starts with _data_ and ends with _action_. But what are the steps and how can machine learning play a role to help decision-makers reduce fatigue and bias -- and raise confidence?

In a [previous post](http://bit.ly/DO-1), I talked about the emotional, political, and personal biases that creep into decisions -- and offered some thoughts about a decision optimization [offering](http://www-03.ibm.com/software/products/en/decision-optimization-center) from IBM that helps organizations make more informed decisions by setting constraints, finding bottlenecks, evaluating what-if scenarios, and offering choices. I gave a sense of the flow of inputs and outputs at a high level, but let's go deeper.

We can think of machine learning as focused on insights -- for example, insights that help enable better forecasts. By contrast, decision optimization focuses on actions such as creating specific plans or schedules based on those forecasts.

## **Predictive vs. Prescriptive**

We know that machine learning can offer help for complex, next-best action decisions, whether the decision is about choosing a career, choosing a business strategy, or choosing whether to turn left or right at a point in a journey. But we also know that many difficult choices are really a combination of more than one decision -- decisions that involve complex, interdependent trade-offs. For those choices, it's important to consider how the decisions might affect each other, how they affect larger goals, and how various rules or constraints limit the range of good decisions.

For example, the airline mentioned above will have access to public data for weather patterns, airport closures, and [air traffic activity](http://openflights.org/data.html) -- in addition to their own private data of engine types, instrumented data, mechanical expertise for maintenance tasks, and staffing.

With good predictive algorithms and enough data, they can anticipate the likelihood of failure of each engine for each plane. That helps them create a preventive maintenance plan for each plane. But what if two planes need to be maintained at a time when only one technician is available? What if two planes are triggered for maintenance on the same critical route? The maintenance planner ends up having to solve the conflict manually -- but extrapolate that conflict to a large, international airline with thousands of planes and the manual approach becomes untenable, or at least massively inefficient.

This is where decision optimization can play a role. The airline's failure predictions become the data input to a decision optimization model that can not only consider multiple predictions simultaneously but can also factor in customer service, costs, and other trade-offs, as well as availability and skill of maintenance engineers, demand on the airline routes, availability of maintenance facilities -- all within a single model. The output is a maintenance schedule for the entire fleet, which can potentially minimize customer disruption and costs, and [eliminate manual intervention by the maintenance planner](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?subtype=AB&infotype=PM&htmlfid=ASC12372WWEN&attachment=ASC12372WWEN.PDF).

A quick aside: I spend most of my time focused on clients whose data lives _behind_ the firewall. These are often industry giants with masses of accumulated data that they're eager to feed into machine learning algorithms to generate deep knowledge about the organization. Whether it's transaction records, logs of customer behavior online, healthcare archives, or other proprietary information, taking advantage of that data can be like wielding a secret weapon.

But as the airline example makes clear, tapping that data for _predictions_ isn't enough. To get to more informed decisions requires _prescriptive_ analytics.

## **Goals + Predictions + Rules + Data = Decisions**

To generate decisions such as plans and schedules, optimization models and optimizer engines consider business goals, and how those goals can be affected by various decisions. For this, the models also take input predictions, business rules, and other business data required to describe the goals and rules.

Another good example of how predictive and prescriptive technology complement each other is the global tire manufacturer that wanted to gain a competitive advantage by eliminating inefficiencies in its production across 10,000 different products. Using predictive technology, the company could anticipate the demand of these 10,000 products across its supply network. This was then used as an input to IBM [Decision Optimization](http://www-03.ibm.com/software/products/en/decision-optimization-center), which simultaneously [considered up to ten million constraints](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?subtype=AB&infotype=PM&htmlfid=ASC12372WWEN&attachment=ASC12372WWEN.PDF) across all plants and products -- and automatically generated a production plan for all products across all locations, highlighting where bottlenecks might occur.

In this example, the decision optimization model also considered the many business goals and rules (also called constraints), such as demand, available resources, costs, yields, production recipes, operational constraints, and customer preferences.

In other words, the optimization engine generates decisions by using one or more mathematical models to combine a machine learning analysis of the situation at hand and the possible future states (data and predictions) with a set of goals and choice of possible decisions affecting those goals. Optimization can consider millions of choices simultaneously to provide plans and schedules [much faster than traditional planning approaches](https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?subtype=AB&infotype=PM&htmlfid=ASC12372WWEN&attachment=ASC12372WWEN.PDF) -- typically with significant improvements in key performance indicators (KPIs).

Configuring business rules and constraints doesn't happen automatically and normally requires human intervention, but advances in natural language processing can enable non-experts to build, test, and visualize rules involving, for example, revenue, inventory capacity, schedules, labor limits, or any number of additional business impacts. With machine learning, optimization, and rules engines combined, decision models could get more sophisticated over time by suggesting additional rules or adapting existing rules.

As the figure below suggests, the inputs of an optimization process are a combination of forecasts generated by machine learning technology (such as demand forecasts), other data (such as resource availability, costs, yields, and recipes), and a description of the rules or constraints limiting the decisions (such as capacities or customer preferences), as well as the business goals to optimize (such as costs, revenue, or customer service).

All these factors are input into one or more optimization models, which are analyzed by the optimizer engines. The output from the process is usually a recommended set of actions, plans, or schedules designed to optimize the defined goals.

![](https://cdn-images-1.medium.com/max/1600/1*9A1g3WuZU8ymrAyR2BUh1g.png)

The optimization process typically happens continuously in an organization, and often in the form of what-if analysis. What if the demand forecast is 10% higher? What if the demand forecast is 10% lower? To go a step further, we advance to technology for optimization under uncertainty, which could answer the what-if questions within a single model. (But that's the topic of another post.)

This post just scratches the surface of where we think decision optimization is headed over the next months and years. Check back for more posts as we go deeper, and in the meantime, find out more about IBM's [Decision Optimization Center](http://www-03.ibm.com/software/products/en/decision-optimization-center).

To find out how AI-Fueled APIs can increase engagement and retention, [download Six Ways to Boost Engagement for Your IoT Device or App with AI](https://dzone.com/go?i=244222&u=https%3A%2F%2Fhubs.ly%2FH08wTJ50) today.
