# Code Smells: Iteration

_Captured: 2017-08-24 at 23:17 from [dzone.com](https://dzone.com/articles/code-smells-iteration?edition=319412&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-24)_

The single app analytics solutions to [take your web and mobile apps to the next level.](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D322361301%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Try today! Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D321036346%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

[Last time](https://dzone.com/articles/code-smells-deeply-nested-code) we looked at some suspicious nested code, and I suggested that the best way to deal with this was to move some of it into a different class to stop the original class having to understand the internals of how the data was stored.

## **The Smell: Iteration**

But that's not the end of the story. In this article, I want to explore a different problem that code iteration might be pointing to. The nested iteration in the last example suggested the logic was in the wrong place. The existence of iteration at all in our new `hasName` method (whether implemented as a for loop or using the Streams API) suggests another problem: This might not be the correct data structure to store the names in.

This may even be hidden (or at least less obvious) when using the Streams API because this gives us a readable way to query our collection. But it doesn't necessarily give us a _fast_ way to query our collection.

## **Example 1: Set Instead of List**

Let's take a closer look at the code in question. In the [Deeply Nested Code article](https://blog.jetbrains.com/idea/2017/08/code-smells-deeply-nested-code/) we created `hasName()` in `MappedField`

I'm going to expand it back out to a for loop so it's more obvious what's happening

![Turn Streams API call into a for loop](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/01-turn-into-loop.gif)

> _Turn Streams API call into a for loop_

We end up with:

The `getLoadNames` method returns a List of Strings, which we iterate over in order to see if a particular String value is in there. If we look at the other places `getLoadNames` is used, the usage is pretty similar - we iterate over the list to find something we want.

![Find usages of getLoadNames\(\)](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/02-find-usages.gif)

> _Find usages of getLoadNames()_

This seems pretty wasteful - why iterate over the same list again and again, when you can store it in a data structure which lets you ask immediately if it contains what you want? Given that in this particular case, the names are either unique, or duplicates are effectively ignored, it seems that `Set` might be the data structure we want instead.

The `getLoadNames` method is not a simple getter, as you might expect from the name (but misleading naming is not the topic of this blog post, nor is caching the results of an operation that only needs to be done once, so let's gloss over those smells for now). It processes some data in order to calculate the list of names. The implementation details aren't important for the purpose of this article, we're just going to do the simplest thing that works and change the method to return a Set.

![Return a Set from getLoadNames\(\)](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/03-return-set.gif)

_Return a Set from getLoadNames()_

Because Set is also a Collection (like the original return type List), all of the code that calls this method still passes - the three callers only used the method in a for loop. Going back to our original method `hasName`, we can simplify it to:

That's it. No more looping, just a simple check.

We should look at the other callers to see if they can be simplified as well, but if they need to iterate over the Set (for any reason) we can leave them as they are.

Running all the tests for the project shows everything still works as expected so we can commit these changes.

## **Example 2: Map Instead of List**

Here's a very similar example, with a slightly different solution:

In this method, we're iterating over all the fields, and looking for one with the same `javaFieldName` as some given value. This sounds like something which would be better handled by a different data structure. In this case, a Map of `String` name to `MappedField`would let us immediately find the right field with this name.

The `persistenceFields` field is used in a number of places in this class, so it's best to take a safe approach to migrating its data structure. I'm going to replace it with a new field, `fields`, which is a Map of `String` to `MappedField`.

![Create a new Map field](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/04-new-fields-field-2.png)

_Create a new Map field_

I use highlight usages to find everywhere in this class that `persistenceFields` was used. The first step is to initialize the Map in the same place the `List` was initialized

![Initialise the new Map](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/05-initialise-map-3.gif)

_Initialize the new Map_

Then I can find all the places that queried `persistenceFields`, and the simplest way to migrate them to use the new field is to use the `values()` Collection from the Map, so all the existing code works the same way it used to

![Use Map.values\(\) instead of original list](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/06-use-values.gif)

> _Use Map.values() instead of original list_

Most of these changes only impact this class and not other code. The exception is the getter, which we have to change to return a Collection rather than a List. A quick look at the usages of this method show that the List is only used for iteration, or other cases where a Collection will work just as well. So we change this to return the Collection

![Change the return type of the getter](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/07-return-collection.gif)

> _Change the return type of the getter_

When we've replaced the usages of the original List with the new Map, we can safely remove the old List and rename the Map (if we like) to the name of the original field.

![Remove original list](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2017/08/08-remove-list.gif)

> _Remove original list_

Rebuilding the project and re-running the tests shows everything still compiles and runs as expected.

Now we can go back to the original method with the smell, and make the use of the map. The updated method is:

Much simpler!

If there are other methods that were iterating over the list to find the name, we can make the same change (or simply delegate to `getMappedFieldByJavaField`). All callers that were iterating for any other reason still work exactly the same as before, just iterating over the Map's `values()`. We may want to look at these other methods later to see if there's some way to simplify them. Remember, it's OK to have more than one data structure to store the same information, if the purpose is to provide fast access to the data - this is particularly useful if reading happens more frequently than updating. In our case, we might want to store our `MappedField`s in several Maps keyed by different values.

## **In Summary**

If you see iteration code (for loops or Streams API calls) you should question whether this is really needed. If the data structure is always being iterated over in order to find some value, you may be better off using a Set or a Map. This will give you not only simpler, cleaner code, but usually better performance as well.

Remember when choosing a data structure that there are two main access patterns to consider - adding/updating data, and reading the data. How frequently you read vs write and what sorts of update operations you do will determine which is the most efficient data structure for you.

Symptoms:

  * For loops iterating over a collection looking for some value
  * Streams API calls with `findFirst`/`findAny`/`anyMatch`.

Possible solutions:

  * If the code is checking if a value exists in a List, consider using a Set instead, if the values are unique or duplicates are ignored.
  * If the code is always looking for an Object with a particular property, a Map of the Objects keyed by that property will be much more efficient.
  * The Collections API gives you a lot of useful methods too, so even if you can't change the data structure directly, you should check if there's a Collection method that does what you want. Our first example could have continued being a List, if duplicates were expected, but we could have used `List.contains()` instead of writing out own iteration code. This is more concise, and the Collections implementation is usually the most efficient version for the data structure.
  * If, for some reason, you really do need to write your own iteration code, it may be best to [encapsulate the implementation details](https://refactoring.com/catalog/encapsulateCollection.html) of how data is written/read, and provide nice helpfully named methods for your domain objects to use this. This way at least the iteration code is kept out of your business logic.

CA App Experience Analytics, a whole new level of visibility. [Learn more.](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
