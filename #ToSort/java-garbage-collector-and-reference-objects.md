# Java Garbage Collector and Reference Objects

_Captured: 2017-05-08 at 16:18 from [dzone.com](https://dzone.com/articles/java-garbage-collector-and-reference-objects?oid=twitter&utm_content=buffer4c55c&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The single app analytics solutions to [take your web and mobile apps to the next level.](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D322361301%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Try today! Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D321036346%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

![Image title](http://i2.wp.com/www.egimaben.com/wp-content/uploads/2017/01/GarbageCollection4.jpg?w=907)

In this article, we will discuss a few memory management concepts in Java with a heavy focus on the interaction between the Garbage Collector and the different reference objects available.

This is no introduction, so let us mutually agree that you have Java Heap and GC basics down. Many articles cover this topic quite well, and you might actually wonder why am covering something that is already well discussed over the www.

  1. I found that most articles introduce Java memory very well, but start choking later on stuff like reference objects. It is either a variant of _"Who doesn't know that stuff?"_ attitude or author fatigue. I would like to give my shot and, hopefully, not fall into the same pool.

  2. Memory is a gold mine of **interview questions for Senior Dev positions**. "_Java manages its own memory, I really don't have to know how it does it._" Nice story for your neighbor or close friend. Good luck convincing that mean-looking interviewer. Moral: You must understand memory.

## **Analogy**

Analogies make understanding computing concepts short and sweet, full of _oooh! _and_ uh huh!_ moments. I hope you experience nothing less.

Picture a school cafeteria. Plates are scarce, but the manager is smart. He derives a strategy together with his staff with one aim: To feed all the hungry students in time without anyone missing food due to a shortage of plates.

**Strategy0:** They plan to collect all used plates for washing whenever a student finishes eating and leaves the cafeteria, such that the same plates are reused by those that have not yet eaten.

Therefore, whenever the serving team reports that plates are running out, a dedicated waitress is sent out to collect all used plates. A plate will be collected as long as the student that was using it has left the cafeteria. These plates are then washed and added to the pile to serve more students.

This strategy works very well, and Mr. Manager is pleased with himself and his staff. Soon, he realizes that some students finish eating but stick around chatting and laughing with friends. He had told his collector waitress to only collect a plate when a student has left the table. The result, a lot of dirty plates stuck on tables simply because satisfied students are still seated there while the cafeteria is frequently running into plate crisis.

**Strategy1:** Mr. Manager has another trick up his sleeve. His instruction to the collector waitress changes: _Collect a plate as long as a student has finished eating, regardless of whether he/she is still seated on the table or not_. Word reaches students of the new and "hostile" changes, a lot of special groups come with complaints seeking a compromise with Mr. Manager. This strategy is marked a failure.

**Strategy2:** Being the smart man he is, he comes up with yet more brilliant ideas and draws up an instruction set for any collector waitress:

  * If a student is a prefect or guild rep, allow them to retain their plate for as long as they like until they explicitly call you to collect it or they leave the table.
  * If a student is a girlfriend or boyfriend to a prefect or guild rep, allow them privileges of their partner… meaning, even if they have finished eating but are still on the table, don't rush to collect their plates unless there is absolutely no alternative and the cafeteria has literally reached its limit in terms of available plates.
  * If the student is not a prefect and not in a relationship with any prefect, as is the case with most first-years, be very vigilant about collecting his/her plate -- no delays, no compromise. Whether they are still seated on the table or not, as long as they have finished eating… even if they beg and cry. They are not allowed any kind of privilege whatsoever.
  * Finally, the doctor has sent a list of diabetic students and needs to know the exact time they had their last meal every day in order to determine when to do routine blood sugar level checks. Collect their plates as you do for the students in the previous category, but always note down the exact time when you pick the plate and notify me.

This turned out to be an excellent strategy. Talk about iterative problem solving .

References to objects in Java follow a certain hierarchy of strength and privilege, as do the students in the cafeteria. Let us dive into the technical rundown.

## **Strong Reference**

In every Java program, objects are the way to hold and manipulate data:

In the above snippet, the _new_ key word creates a _StringBuilder_ object and stores a **strong reference** to it in variable _sb_. This is the default level of strength for all objects we create, so we don't use any special label to identify them as we do for the rest.

To create the rest of the references in the hierarchy, we need special wrapper objects that reside in the _java.lang.ref_ package.

Any object with at least one **strong reference** is not eligible for garbage collection. In our analogy, **prefects** hold strong references to their plates. In technical terms, we say the object is **strongly reachable**.

It **only becomes eligible for collection when we nullify its reference**, akin to a prefect leaving the table:

## **Soft Reference**

A soft reference can be created to an object by wrapping its instance in a _java.lang.ref.SoftReference_ object:

In the above snippet, the first line creates a string builder object with a **strong reference** stored in _sb_. The second line creates a **soft reference** to it inside _sbSoftRef_ so that now the string builder object has two references.

At this stage, the string builder is not eligible for collection whatsoever. However, the third line nullifies the strong reference, and now the object only boasts of a soft reference.

The object is now similar to a used plate sitting in front of the boyfriend/girlfriend of a prefect -- it can be collected only as a last resort when the cafeteria staff is absolutely sure there are no more plates available. Technically, we say the object is **softly reachable.**

In this phase, we can still retrieve a **strong reference** to the object by calling the get method of the _SoftReference_ object, which returns null if the object is already collected:

Objects with only soft references to it are **collected if and only if the JVM has concluded that there is no more memory to allocate to new objects and is on the brink of throwing an _OutOfMemory_ error**.

**Soft references are intended for use in memory-sensitive caches**. As the cache grows, available memory for new objects reduces yet you need the cache, so the JVM compromises with "you" until it can't anymore.

## **Weak Reference**

A weak reference can be created to an object by wrapping its instance in a _java.lang.ref.WeakReference_ object:

In the above snippet, after nullifying the strong reference in the third line, the object immediately becomes eligible for GC.

The object is now similar to a used plate sitting in front of a first-year student with no privileges. It can be collected right away without any regard for whether the student is still seated at the table. Technically, we say the object is **weakly reachable**.

Though we can still retrieve a strong reference to the object, the window of opportunity is way smaller than that of soft reference. We will get a null much more often than in the other cases:

Objects with only weak references are **collected eagerly by the GC whether memory is tight or not**.

**Weak references are intended for use in Canonicalized mapping.** Just 5 minutes of googling will give you an understanding of this use case, so I will not dwell…

## **Phantom Reference**

A phantom reference can be created to an object by wrapping its instance in a _java.lang.ref.PhantomReference_ object:

In the above snippet, after nullifying the strong reference in the fourth line, the object immediately becomes eligible for GC. Ignore the _ReferenceQueue_ object, that's for later. For now, just remember that **_PhantomReference,_ unlike soft and weak references, is useless without a _ReferenceQueue_**.

The object is now similar to a used plate sitting in front of a first-year student who is diabetic. It can be collected right away without any regard for whether the student is still seated at the table, albeit with one condition: the exact time of collection is noted and the doc notified.

For as long as the piece of paper on which the time has been noted has not yet been used and discarded by the doctor, we refer to the object as **phantom reachable**. (_Major point of confusion, continue reading but watch out _).

The _get_ method of a _PhantomReference_ object is useless because it always returns _null_. This further strengthens the uniqueness of this reference object vis-a-vis soft and weak refs. The next sections will make this uniqueness even more crystal clear.

**Phantom references are intended for use as a more flexible alternative to the _Object.finalize()_ method.**

## **Reference Queue**

True to its name, a reference queue is a data structure that enqueues reference objects namely: _WeakReference_, _SoftReference,_ and _PhantomReference_.

Whether a reference object is enqueued at any time or not depends on whether we provide a _ReferenceQueue_ object upon creation of the reference object. Apart from _PhantomReference_, it is not mandatory or even useful to provide one.

Depending on the type of reference object, the exact point at which it is enqueued varies. I don't intend to dwell much on this subject apart from furthering the coverage of phantom references. **Read the next paragraph very keenly**.

A **phantom reference is enqueued as soon as the object it is referring to has been finalized** by the garbage collector. **"Finalized"** means its _finalize()_ method has been called. The GC calls the _finalize()_ method of objects just before collecting them for the benefit of the application that created them. The benefit is the opportunity to release non-"**GC'eable" **resources that the object must have created or used during its earthly life (read Java heap life). Non-"GC'eable" resources are inaccessible to the GC. One obvious example is a file handle provided by the OS. To demonstrate, take a look at the finalize method of _FileInputStream_ class in all its glory:

Notice the _close()_ method call at the end, look familiar? Yes, it's that _fis.close()_ call your Java teacher told you to always place in the _finally_ clause of _try/catch/finally_ blocks. Wondering whether it is a duplicate call, since you always _close()'_'d your file resources? Great, read on!

Now notice the _if_ check at the top of the method body. If you already called _close()_ inside your code, then _fd_ in the above code would be _null_ and the rest of the method body would not be executed. _Phewww!!!!_ (Did that come too late???). Read on!

It so happens that, these days, the _finalize()_ method, especially in library/platform classes such as _FileInputStream_ above, acts as a safety net for cases where we as developers are reckless and forget to release non-heap resources.(**_I may already by whispering to you that you may never have to use phantom refs, but read on_**).

So what the heck does all this have to do with phantom references and reference queues. Am I losing focus? Well, you asked, so I'll answer:

The _finalize()_ method is plagued with numerous issues that counter almost all the advantages it sought to offer. There is actually a **detailed coverage in Joshua Bloch's Effective Java book**, and several blogs talk about its problems extensively. Don't think that they are just staining the image of an otherwise brilliant API. Unless you are an upcoming James Gosling, I would highly recommend that you just take their word and make peace with other alternatives for cleaning up after your resources. Now, keep reading -- we're almost done.

We can now _finalize()_ this section with why phantom refs and ref queues come in. _PhantomReference_ object was created to **_"provide a more flexible alternative to finalize()." _**Whether it has succeeded or not is quite a huge topic, but my bet is **NO**.

How we as programmers do this is by supplying a _ReferenceQueue_ instance while creating a _PhantomReference_ instance as we saw earlier. As soon as the _finalize()_ method of the object is called, its phantom ref is enqueued. It is up to us to keep polling the reference queue to keep track of when this event happens. Here is where we manually release resources, including a final call to _phantomRef.clear()_ method to nullify the underlying reference.

## **Differences Put Together**

I know the title of this section is kinda lame, but bear with me. I will try to put together the differences of the three reference objects just to clear any doubts:

  * **Enqueuing**: Soft and weak reference objects are enqueued as soon as the GC, from its algorithms, has "marked" their memory objects for collection, but has not yet finalized them. On the other hand, phantom references are enqueued as soon as the memory objects have been finalized.
  * **Reference.get()**: The _get_ method of both soft and weak references returns a strong reference to the underlying object or null if that object has already been marked for collection. On the other hand, the _get_ method of phantom reference always returns null (whether you are Josh Bloch or Jon Skeet calling it. Kidding!). This difference strikes a key point about their use cases, for weak and soft refs to be of any use, one should be able to recreate a strong ref to their objects within the "window of opportunity." But phantom refs don't need this quality as we explored earlier.
  * **Reference.clear()**: This method is available in all the three ref objects. It sets the underlying reference to null hence explicitly availing the memory object for collection before its time. This is a useless facility for weak and soft refs as it would counter their benefit. But it is key for phantom refs as you have to call it on Mr. phantom at the end of your clean up steps.
  * **ReferenceQueue**: it is useless for soft and weak refs but without it, phantom refs are useless.
  * **Use cases**: Soft refs: memory-sensitive cache, weak-refs: canonicalized mapping, phantom-refs: more flexible substitute for _finalize()_.

## **Conclusion**

In this, albeit very long, article, I have tried to discuss my findings on the relationship between the GC and reference objects. I hope it has, at least, given you a better understanding of the reference objects specifically and the GC generally.

It goes without saying that you may never have to deal with these reference types directly:

  * Need memory-sensitive caching? (A very complex and meticulous endeavor to get right, by the way?) U**use solid and battle-hardened libs like _ehcache_**_._
  * Need canonicalized mapping? Simply **use_ java.util.WeakHashMap_ **and save yourself hair loss.
  * Need to do pre-mortem clean up? Don't be deceived by Mr. Phantom's offering as opposed to finalize(), **stick to age-old try/catch/finally.**

CA App Experience Analytics, a whole new level of visibility. [Learn more.](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

### Like This Article? Read More From DZone
