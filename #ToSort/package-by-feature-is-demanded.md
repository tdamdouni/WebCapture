# Package by Feature Is Demanded

_Captured: 2017-03-03 at 19:32 from [dzone.com](https://dzone.com/articles/package-by-feature-is-demanded?edition=273883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-03)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

In the [DZone comments](https://dzone.com/articles/layered-architecture-is-good) under my post about [Layered Architecture](https://dzone.com/articles/layered-architecture-is-good), some people believed that layering should be realized as what I call _Packaging by Feature_. I intentionally delayed writing about this to cover [hexagons](https://dzone.com/articles/hexagonal-architecture-is-powerful) and [onions](https://dzone.com/articles/onion-architecture-is-interesting) first but now that we have those behind us, we can jump straight into the so demanded architectural style.

## What Is Package by Feature?

In a typical [Layered Architecture](http://tidyjava.com/layered-architecture-good/), code organization follows the horizontal decomposition created by dividing the system into layers. This is what is often called _Package by Layer_.

![](http://tidyjava.com/wp-content/uploads/2017/02/dependencies.png)

The problem with this approach is that _cohesion_ inside each package is usually low and the _coupling_ between packages is very high. This seems like exactly the opposite of what we want to achieve. At the same time, most people agree that separating the concerns of presentation, application, domain, and infrastructure makes sense. _Package by Feature _capitalizes on both points by moving the layering a level down -- to the class level -- and focusing on _coupling_ and _cohesion_ at a higher level by keeping all classes related to the same _feature _in the same package/module:

![](http://tidyjava.com/wp-content/uploads/2017/03/features_for_my_husband-1.png)

You might wonder now _what is a feature?_ It's a valid question. I have seen different implementations and examples, varying from a _feature_ meaning effectively one _use case_ to _feature_ meaning a whole set of operations related to a particular business concern. I have seen more of the latter when doing research for this article, but I don't think it's necessarily a good thing.

## The Essence of Package by Feature

I see two things that form the essence of _Package by Feature_: maintaining _high cohesion_ and _low coupling_ at the package/module level and being able to say what an application does by looking at its package/module structure.

In a typical Layered Architecture, the _cohesion _inside a package is low and the _coupling _between the packages is high. We rarely change technologies or conventions regarding a particular layer, comparing to how often we add a single feature, hence _low cohesion_. And, in most cases, each class in a layer (package) depends on at least one class in another layer (package), making the _coupling_ between them _high._ In _Package by Feature_ style, we ideally change classes only in a single package - the one related to the feature we're working on - so _cohesion_ is high, and there are only a few dependencies between _features_, so coupling is low.

![](http://tidyjava.com/wp-content/uploads/2017/03/i_love_you_and_even_if_i_had_to_do_it_three_times.png)

The two terms above are useful but, to be honest, these are nerd metrics. The more human side of _Package by Feature_ is that you don't have to be a nerd that knows every piece of a codebase to be able to say what it does - a quick look at the package/module structure should tell you that. This is one step towards what Uncle Bob calls _[Screaming Architecture_](https://8thlight.com/blog/uncle-bob/2011/09/30/Screaming-Architecture.html).

## Implementing Package by Feature

The name _Package by Feature_ strongly suggests that you should implement this style by putting each feature in a separate package and that's mostly true. The only caveat that I see is that it could also be a module, namespace or any other mechanism available in your language in case you're not using Java.

The second important thing about _Package by Feature_ is that when related stuff is in a single package, one can finally make some use of access modifiers i.e. make most of the things package-local instead of public. This way we can limit the public interface of our feature to just the things that we actually want to expose. In the _Package by Layer_ style, this was not possible because related classes needed to communicate across packages, which forces us to make everything public.

### Example

Even though I feel like [Spring Pet Clinic](https://github.com/spring-projects/spring-petclinic) is not the best resource to learn about software development from, it does a pretty good job at presenting a flavor of _Package by Feature_. The _features_, in this case, are sets of operations performed on same domain objects:

![](http://tidyjava.com/wp-content/uploads/2017/02/ss2017-02-12at05.21.58.png)

As you can see, we have three dominating _features_ here - managing owners, vets and visits. Whether this decomposition into _features_ is good or not, is a very complicated topic. At the moment, we should focus on the fact that classes representing different layers like controllers, repositories, and domain objects are all kept together, and that the package structure is more _feature_-oriented.

## Benefits of Package by Feature

  * **More Informative Package Structure **- you can deduce some of the system's main _features_ or behaviors from the code structure
  * **High Cohesion & Low Coupling** - we explained this point already in the essence part, although a bit idealistically
  * **Better Encapsulation **- you can make effective use of access modifiers to hide the information that's ought to stay hidden
  * **Better Growth Potential**, in the code volume sense - unless you develop too big or too small _features_, you shouldn't encounter the problem of too big or too many packages

## Drawbacks of Package by Feature

  * **Unspecified Feature Size **- I found no clear guidance or proof that one understanding of _feature_ is better than the other
  * **Learning Curve **- the concept is simple, but since you need to find your own way to slice a system into _features_, mastering it can be really hard
  * **Messiness Potential **- in a tangled domain, in which everything is connected to everything, the slicing into _features_ might become artificial and the low coupling promise might not be fulfilled

## When to Use Package by Feature?

Obviously, it can work for smaller applications in which you can shuffle stuff around and try different things at a very low cost. At the same time, since it carries the promise of higher_ cohesion_, lower _coupling_, and better growth potential, it seems like a perfect fit for bigger applications, which could actually suffer from the drawbacks of _packaging by layer_. Given its moderate learning curve i.e. the necessity to sort out the best definition of a _feature_, I'd be wary of using it for the first time when working on a critical application. I'd opt for dividing the problem into bounded contexts and implementing each one in a [layered](http://tidyjava.com/layered-architecture-good/)/[hexagonal](http://tidyjava.com/hexagonal-architecture-powerful/) way instead.

## Summary

_Packaging by Feature_ is a really appealing idea and I'm totally not surprised that a lot of people push it forward. Our favorite nerdy metrics like _cohesion_ and _coupling_ seem good, and we can see what the application is doing by simply looking at packages. At the same time, I can see its drawbacks and the potential to become a huge mess if someone tries to use an artificial slicing into _features_ in a tangled domain. If you know how to leverage its benefits effectively, go for it. If you don't, be careful.

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
