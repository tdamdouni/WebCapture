# Split a File as a Stream

_Captured: 2017-12-01 at 20:27 from [dzone.com](https://dzone.com/articles/split-a-file-as-stream?edition=341091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-01)_

Try [Okta](https://dzone.com/go?i=247339&u=https%3A%2F%2Fdeveloper.okta.com%2Fsignup%2F%3Futm_campaign%3DSyndication%25253EGlobal%25253Edeveloper-trial-sep-14-FY18Q3%26utm_medium%3Dpre-text%26utm_source%3Ddzone-java-zone-all-developer) to add social login, MFA, and OpenID Connect support to your Java app in minutes. Create a [free developer account](https://dzone.com/go?i=247339&u=https%3A%2F%2Fdeveloper.okta.com%2Fsignup%2F%3Futm_campaign%3DSyndication%25253EGlobal%25253Edeveloper-trial-sep-14-FY18Q3%26utm_medium%3Dpre-text%26utm_source%3Ddzone-java-zone-all-developer) today and never build auth again.

I recently discussed how the new (@since 1.8) method `splitAsStream` in the class `Pattern` works on character sequences, reading only as much as needed by the stream and not running ahead with pattern matching, creating all the possible elements and returning them as a stream. This behavior is the true nature of streams, and it is the way it has to be to support high-performance applications.

In this article, I will show a practical application of `splitAsStream`, where it really makes sense to process the stream and not just split the whole string into an array and work on that.

The application, as you may have guessed from the title of the article, is splitting up a file along some tokens. A file can be represented as a `CharSequence` as long it is not longer than 2GB. The limit comes from the fact that the length of a `CharSequence` is an `int` value, and that is 32 bits in Java. The file length is `long`, which is 64-bit. Since reading from a file is much slower than reading from a string that is already in memory, it makes sense to use the laziness of stream handling. All we need is a character sequence implementation that is backed up by a file. If we can have that, we can write a program like the following:

This code does not read any part of the file -- that is not needed yet -- and assumes that the implementation `FileAsCharSequence` is not reading the file greedily. The class `FileAsCharSequence` implementation can be:
    
    
    package com.epam.training.regex;
    
    
            this.length = (int) file.length();
    
    
            if (buffer.length() < index) {
    
    
                final byte[] bytes = new byte[index - buffer.length()];
    
    
                    int length = input.read(bytes);
    
    
                    buffer.append(new String(bytes, "utf-8"));

This implementation reads only that many bytes from the file as needed for the last, actual method call to `charAt` or `subSequence`.

If you are interested, you can improve this code to keep only the bytes in memory that are really needed and delete bytes that were already returned to the stream. To know which bytes are not needed, a good hint is that the `splitAsStream` never touches any character that has a smaller index than the first (`start`) argument of the last call to `subSequence`.

However, if you implement the code in a way that it throws the characters away and fails if anyone wants to access a character that was already thrown, then it will not truly implement the `CharSequence` interface, though it still may work well with `splitAsStream` so long as long the implementation does not change and it starts needing some already passed characters. (Well, I am not sure, but it may also happen in a case where we use some complex regular expression as a splitting pattern.)

Happy coding!

Build and launch faster with Okta's user management API. Register today for the [free forever developer edition](https://dzone.com/go?i=226224&u=https%3A%2F%2Fdeveloper.okta.com%2Fsignup%2F%3Futm_campaign%3DSyndication%253EGlobal%253Edeveloper-trial-FY18Q2%26utm_medium%3Dpost-text%26utm_source%3Ddzone-java-zone-all-developer)!
