# Aggregation or Composition?

_Captured: 2018-07-06 at 19:27 from [dzone.com](https://dzone.com/articles/aggregation-or-composition?edition=385206&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-07-06)_

Container Monitoring and Management eBook: [Read about the new realities of containerization.](https://dzone.com/go?i=291440&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fcontainer-monitoring-and-management.html%3Fcid%3DNA-DSP-APM-AEJ-000195-00001663-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_eb1-container-monitoring-mgmt-articlepreroll%26mrm%3D)

I often get questions when I teach object-oriented programming about the difference between aggregation and composition. These are two relationships that are easy to confuse.

Aggregation in the UML class diagram is represented by an open diamond whereas composition is represented as a closed or filled-in diamond. Related to this is the "uses" or "depends on" symbol which is indicated by an arrow. A closed arrow represents inheritance.

So why does the UML call out these different relationships? It is easy to see the difference between inheritance and dependency because inheritance is a very special kind of relationship and we have to explicitly call this out in code. But why does the UML call out the difference between aggregation and composition? It doesn't require any difference in coding syntax, at least not in managed code (we'll discuss unmanaged code in a moment).

It turns out that this distinction is not nearly as important today with managed languages as it was fifteen years ago when we didn't have automatic garbage collection in languages. In unmanaged languages like C or C++ the difference between aggregation and composition includes the notion that composed objects are memory managed by the one who composes them. In other words, if an object allocates memory for an object then it has the responsibility for de-allocating the memory when it's done using it. This is not necessarily true for aggregate objects. However, in managed memory languages like Java and C Sharp, this is no longer an important distinction because memory is cleaned up by the garbage collector.

But there is a conceptual difference between aggregation and composition. I like to illustrate it by talking about parking lots. A parking lot has both aggregation and composition in it. A parking lot is an area that aggregates cars. A parking lot is still a parking lot when there are no cars on it. Aggregation is just a place for the aggregates to inhabit.

By contrast, composition refers to a stronger relationship where the composed object is a required part of its composer. For example, a car is composed of an engine, a steering wheel, four tires, etc. By our definition, a car ceases to be a car if you remove the engine. Composition refers to a strong relationship between the composer and the composed.

I like to think of aggregation as referring to the "has-a" relationship and I like to think of composition as referring to the "has-to-has-a" relationship.

In many situations, we simply do not care whether we are aggregating or composing objects or it may not be clear or relevant to us at the point we are creating a class diagram, so we simply use the arrow that indicates "uses". This arrow indicates that one class uses or depends upon or calls methods upon another class, without specifying who allocates and de-allocates the memory or if the services they are using are required or optional for the other object.

There are only a handful of relationships in software development and in programming languages such as C++ or Java. It is of critical importance that we as developers use the right relationships. When we model using the right relationships it makes a better design. Virtually all of the Gang of Four's twenty-three design patterns are some variation on combining aggregation and inheritance.

One of the most pervasive problems that I see as a software development coach coming in to various organizations or working with various developers is the overuse of inheritance. Inheritance is important and useful but it is not a cure-all for every kind of relationship in programming and a lot of times developers overuse it or use it for the wrong reasons and they end up with brittle code as a result.

Take the Chaos Out of Container Monitoring. [View the webcast on-demand!](https://dzone.com/go?i=291441&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcompany%2Fevents%2Fwebcasts%2Fapplication-performance-monitoring-and-management.html%3Fcommid%3D286663%26cid%3DNA-DSP-APM-AEJ-000195-00001663-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_webcast1-apm-taming-chaos-articlepostroll%26mrm%3D)

Topics:

aggregation ,composition ,gang of four ,design patterns ,memory ,garbage collection ,java ,c++
