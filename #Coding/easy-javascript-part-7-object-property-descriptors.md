# Easy JavaScript Part 7 : Object Property Descriptors

_Captured: 2017-12-05 at 21:06 from [dzone.com](https://dzone.com/articles/easy-javascript-part-7-object-property-descriptors)_

In JavaScript, you can create an object literal as shown in the listing below:

At first sight, it looks like the object **cat** has two properties with a string and number value. However, it's much more than that to a JavaScript interpreter. In ES5, the concept of a **Property Descriptor **was introduced. Before we go ahead and discuss property descriptors, let's try to answer a few questions:

  1. How do I create a read-only property?
  2. How do I make an unenumerable property?
  3. How do I make property not configurable?
  4. How do I determine whether a property is read-only?

You can answer all these questions when you understand **Property Descriptors**.

Let's consider the code below:

Here, your output will be as follows:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.js7/2500.p1.png)

As you can see here, there are four characteristics of a property:

The value holds the data of the property, whereas writeable, enumerable, and configurable describe other characteristics of the property. Let's take a closer look at each of these characteristics in the rest of this post.

## Writable

Whether the value of the property can be changed or not is decided by the **writable **characteristic. If **writable** is set to false, then the value of the property can't be changed and JavaScript will ignore any changes in the property value. Consider the code below:
    
    
    Object.defineProperty(cat, 'name', { writable: false });

You can change the value of the writable, configurable, and enumerable characteristics using **Object.defineProperty. **We'll talk more about Object.defineProperty later in this post, but as you see in the code snippet above, we have set the writable to **false**, thereby changing the value of the name property. JavaScript will ignore the reassignment, and the value of the name property would remain **foo**.

If you run the code in **strict mode,** for reassignment of the property value where writable is set to false, JavaScript will throw an exception. Consider the code below:
    
    
    Object.defineProperty(cat, 'name', { writable: false });

Here, JavaScript is running in strict mode, hence when you reassign the value for the name property, JavaScript will throw an exception as shown below:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.js7/0652.p2.png)

The error message here says you cannot assign something to a read-only property. Here, a** property acts as a read-only property if the writable characteristic of the property is set to false**.

## Configurable

Whether a property's other characteristics can be configured or not depends on the value of **configurable**. If a property configurable is set to false, then you cannot change the value of writable and enumerable. Consider the code below:

Here we are setting the configurable to false for the name property. After that, we're then setting the enumerable to false. As discussed, once the configurable is set to false for a property, you cannot change another characteristic.

For the above code, JavaScript will throw a **TypeError **exception as shown in the image below. You will get a **cannot redefine property name **error:

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.js7/4237.p3.png)

While working with **configurable**, you need to keep in mind that** changing the value of configurable can be done only once**. If you set the property configurable to false, you can't reassign it; you cannot undo changes done on configurable. Let's consider the following:

We are reassigning true to the configurable of the name property, however, JavaScript will throw a TypeError for the above operation as shown in the image below. So as you can see, once the configurable is set to false, that change cannot be undone.

![](https://www.infragistics.com/community/cfs-filesystemfile.ashx/__key/CommunityServer.Blogs.Components.WeblogFiles/infragistics.js7/4863.p4.png)

Another important thing you should keep in mind is that even if the configurable is set to false, the writable can be changed from true to false -** but not vice versa**. Consider the following code:

If not in strict mode, the above code will not throw any exceptions. As we discussed earlier, even if the configurable is false, the writable can be changed from true to false but not vice versa. Another important thing you need to keep in mind is that you **cannot delete a property for which the configurable is set to false. **
    
    
    Object.defineProperty(cat, 'name', { configurable: false });

In the above code, you will find that JavaScript does not delete the name property because its configurable is set to false.

## Enumerable

For a property, if you set **enumerable: false**, then that property will not appear for enumeration and it, therefore, won't be available in statements such as a **for...in** loop.

Consider the code here:
    
    
    Object.defineProperty(cat, 'name', { enumerable: false });

Here, you'll only get the age because the enumerable for the name is set to false. This is another important note to remember: by setting **enumerable: false**, the only property won't be available for enumeration. Let's see this in the following code:

Here, the name property enumerable is set to false, but you can access it. You'll also see **true **when checking whether the name is a property of cat or not.

Sometimes, you may have a requirement to check whether a particular property enumerable is set to false or true. You can do this by using the **propertyIsEnumerable** method:

## Conclusion

As a pro JavaScript developer, you must have a good understanding of JavaScript object property descriptors, and I hope that you've gotten just that from this post! Stay tuned for our next post, where you will learn about more important concepts in JavaScript.
