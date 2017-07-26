# Which For Loop?

_Captured: 2017-01-24 at 20:50 from [dzone.com](https://dzone.com/articles/which-for-loop?edition=265881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-24)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

Java 8 introduced another type of _for _loop. This gave us the third way to use them. You would think that releasing another way to use the loop would suggest that it must be better than the others. But that is not the case. Each one has subtle differences, meaning you should have a little think before you decide which one to use.

Types of for loops:

  * Normal _for _loop
  * _For-each_ loop
  * Java 8 _for-each_ loop

## Normal _For _Loop

Now I'm just going to come straight out and say this: These loops look ugly and I try to stay away from them as much as possible. Anyway, now that I have said that, let's get back to explaining what they are. This type of loop uses a counter to iterate through the elements of a list or array. The easiest way to explain it is through an example.
    
    
    List<Integer> list = Arrays.asList(1,2,3,4,5,6);
    
    
    for(int index=0; index<list.size(); index++) {
    
    
        System.out.println("I have read the number: " + list.get(index));
    
    
    int[] array = new int[]{ 1,2,3,4,5,6};
    
    
    for(int index=0; index<array.length; index++) {
    
    
        System.out.println("I have read the number: " + array[index]);

The above shows how to iterate through both a list and an array. It does so by increasing the counters value _index _and retrieving the element at that position using _list.get(index)_ or_ array[index]_. After it has the element it can do whatever it wants with it.

The advantage of using this type of loop is that you have more control over how you read the elements than you do with the other types of loops. If you wanted, you could retrieve the element at position _index-1_ very easily. Just remember to handle the scenario of _index = 0_, or you're going to have an _IndexOutOfBoundsException_ on your hands. This advantage of control is also its downside, as you need to manually retrieve the elements, which makes the code look cluttered. The ugliness of this loop is not found in the other types of loops.

## The_ For-Each_ Loop

The name of this loop pretty much sums up what it does. For each element in the collection or array, do something with it. The is no need to increment through the list using a counter as that is all done behind the scenes. Simply give the object you want to retrieve and type and name and you are good to go.
    
    
    List<Integer> list = Arrays.asList(1,2,3,4,5,6);
    
    
        System.out.println("I have read the number:" + number);
    
    
    int[] array = new int[]{ 1,2,3,4,5,6};
    
    
        System.out.println("I have read the number: " + number);
    
    
    Set<Integer> set = new HashSet<>(Arrays.asList(1,2,3,4,5,6));
    
    
        System.out.println("I have read the number: " + number);

Look how simple and pretty they are, so much nicer than those ugly loops above. Anyway, the loops will go through the elements and, during each iteration, provide the defined variable a value from the collection or array. The order in which the values are retrieved follows the same order that the elements have in the collection or array. Another advantage of the _for-each_ loop is that it can iterate through the elements of a Set, as it does not have its own _get()_ method.

## The Java 8 _For-Each_ Loop

This is the new _for _loop that has been added with the release of Java 8. It has all the characteristics of the normal_ for-each_ loop but uses lambda expressions to define what it does with each element it iterates over from the collection, although this form cannot be used on an array. The example below is pretty self-explanatory.
    
    
    List<Integer> list = Arrays.asList(1,2,3,4,5,6);
    
    
    list.forEach(number -> System.out.println("I have read the number:" + number));

This form of _for_ loop can be used instead of the normal _for-each_ loop, as, functionally, they are the same, but the syntax is different. This form looks nicer for simple lambda expressions and can allow a loop to be defined in a single line if the expression is small enough. When it comes to loops with more statements inside them, it is the user's preference which _for-each_ loop they use, as the benefit of decreasing the amount of code written is no longer there.

So which loop should you use? If you need total control over the elements you read or need to add and remove elements from the list, then a normal _for _loop is the way to go. If you simply need to perform some statements on elements of the list and don't need to add or remove elements, then both the normal_ for-each_ and Java 8 _for-each_ loops will suffice. Determining which _for-each_ loop to use is up to you. Personally, for singular or such smaller statements, I would use the Java 8 _for-each_ loop, but for loops with longer statements inside, then the good old normal _for-each_ will be my loop of choice.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
