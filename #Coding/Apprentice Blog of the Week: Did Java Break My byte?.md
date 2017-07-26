# Apprentice Blog of the Week: Did Java Break My byte?

_Captured: 2015-10-17 at 22:13 from [blog.8thlight.com](http://blog.8thlight.com/dave-torre/2014/09/10/did-java-break-my-byte.html)_

In Java, we use `InputStream` objects to read data. The smallest amount of data we can read at once is eight bits (one byte), using the `read()` method. Java has a `byte` data type, but the `read()` method doesn't use it. Instead, it returns each byte of data as an `int`.

Presumably, this is because the `read()` method wants to use one of its return values to indicate that it has reached the end of the stream. The `byte` data type, and bytes in general, can only represent 256 different values, and whatever stream you're reading from probably wants to use all 256 of them. Therefore, there wouldn't be any values left to tell the `read()` method when to stop reading. `read()` gets around this by returning each byte as an `int`--a data type that can store many more than 256 values.

To find out what a returned `int` looks like, I did an experiment.

First, I chose eight bits, 11111101, and stored them in a `byte` variable. Java's `byte` data type is a two's complement integer (two's complement is a way of representing positive and negative integers with bits). The two's complement value of 11111101 is -3, so to store that byte inside a `byte` variable, I assigned -3 to it.
    
    
    byte myByte = -3; // 11111101
    

Then I put `myByte` into an array, and used the array to create an `InputStream`.
    
    
    byte[] myArray = {myByte};
    InputStream in = new ByteArrayInputStream(myArray);
    

Finally, I called `read()` and printed the result.
    
    
    int myInt = in.read();
    System.out.println(myInt); // 253
    

But when I ran the program, it printed out 253, not -3. What the...?!

As it happens, Java's `int` data type is also a two's complement integer. It uses 32 bits instead of 8. Using 32 bits, the two's complement representation of 253 is:
    
    
    00000000000000000000000011111101
    

That looks a lot like my original byte, but with a bunch of zeros added to it. The `read()` method must be doing just that: tacking on a bunch of zeros. It could then theoretically add a new number that is all ones, and know that it will not only not interfere with the byte's data, but also recognize it as a place to stop. The two's complement that is always all ones (1111, 1111, etc.) is the value -1. Therefore, -1 must be the value `read()` uses for the end of the stream.

I can change my returned value of 253 back to my original value of -3 with a cast, since all casting to a byte does is get rid of everything but the right-most eight bits.
    
    
    byte gotMyByteBack = (byte)myInt; // 11111101
    System.out.println(gotMyByteBack); // -3
    

`InputStream` also offers a `read(byte[] b)` method that reads bytes directly into the array `b` one after another. This method still returns an `int`, and still uses -1 to signal the end; but the `int` represents the number of bytes read, not any of the bytes themselves. In this way, it doesn't require a middle step of returning a byte as an `int` and casting it back.
    
    
    byte[] before = {-3};
    byte[] after = new byte[1];
    InputStream in = new ByteArrayInputStream(before);
    int someInt = in.read(after);
    System.out.println(after[0]); // -3
    

So beware. Not only does Java interpret `byte` variables as two's complement integers, but `InputStream`'s `read()` method actually changes the incoming bytes. It crams reading and signaling into the same return value. Using `read(byte[] b)` instead will cleanly separate the two.

#### More Posts by This Author
