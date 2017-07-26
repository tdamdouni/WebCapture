# Groovy Goodness: Redirecting Print Methods in Scripts

_Captured: 2017-04-23 at 10:12 from [dzone.com](https://dzone.com/articles/groovy-goodness-redirecting-print-methods-in-scripts?edition=292908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-22)_

[Bitbucket](https://dzone.com/go?i=201143&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=201143&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

Running external Groovy scripts in our Java or Groovy application is easy to do. For example, we can use `GroovyShell` to evaluate Groovy code in our applications. If our script contains print methods like `println`, we can redirect the output of these methods. The `Script` class, which is a base class to run script code, has an implementation for the `print`, `printf` and `println` methods. The implementation of the method is to look for a property `out`, either as part of a `Script` subclass or in the binding added to a `Script` class. If the property `out` is available, then all calls to the `print`, `printf`, and `println` methods are delegated to the object assigned to the `out` property. When we use a `PrintWriter` instance, we have such an object, but we could also write our own class with an implementation for the `print` methods. Without an assignment to the `out` property, the fallback is to print on `System.out`.

In the following example, we have an external script defined with the variable `scriptText`, but it could also be a file or other source with the contents of the script we want to run. We assign our own `PrintWriter` that encapsulates a `StringWriter` to capture all invocations to the `print`methods:
    
    
    def shellBinding = new Binding(out: new PrintWriter(stringWriter))

Another option is to directory set the `out` property of a `Script` object:

Written with Groovy 2.4.10.

[Bitbucket is the Git solution](https://dzone.com/go?i=201144&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=201144&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
