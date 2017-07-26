# Why Should I Write Getters and Setters?

_Captured: 2017-04-20 at 23:53 from [dzone.com](https://dzone.com/articles/why-should-i-write-getters-and-setters?edition=292902&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-20)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://bs.serving-sys.com/serving/adServer.bs?cn=trd&mc=click&pli=20943538&PluID=0&ord=%5Btimestamp%5D) Brought to you in partnership with [IBM](https://bs.serving-sys.com/serving/adServer.bs?cn=trd&mc=click&pli=20943538&PluID=0&ord=%5Btimestamp%5D).

When I started my career in Java, I was confused about getters and setters. One question always comes to mind: _Why should I write getters/setters?_ It looked like some kind of weird syntax to me.

I learned that through the public access modifier, one field of a class is accessible to any packages, and with getters/setters, I am actually doing the same thing -- making the field private while the getter/setter method is public, so it can be accessed by any packages.

So, what is the difference between the following two expressions?
    
    
    public String name = "Shamik";
    
    // caller:
    String name = X.name;   //(X is a object instance);
    X.name = "Shamik Mitra";
    
    
    private String name = "Shamik";
    
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    // caller:
    String name = X.getname();
    X.setName("Shamik Mitra");

Slowly, I realized why we use getters/setters and why they are important. In this article, I share that realization.

## Realization

The main difference between making a field public vs. exposing it through getters/setters is holding control over the property. If you make a field public, it means you provide direct access to the caller. Then, the caller can do anything with your field, either knowingly or unknowingly. For example, one can set a field to a null value, and if you use that field in another method, it may blow up that method with a null pointer exception.

But, if you provide a getter/setter, you provide them indirect access while taking full control. The only way to set a value is through setter, and you get a value through a getter, so now you have exactly one entry and one exit point for your field, as getter/setters are methods, which allows blocks of code, so you can do validation checks on them! The object takes the decision whether you should set the caller value or not. The same applies to a getter method -- you can take the decision to return the actual reference or clone it and return the same to the caller.

So, getters/setters work as a fuse or circuit breaker -- where the electric current has to be passed through the fuse. If anything goes wrong, the fuse is detached from the main circuit, so the circuit is safe. The concept is the same here. If anything goes wrong, the setter will not pass the value to a class member field.

After reading the explanation, I know still you have one question:

> I understand, but generally, we do not write anything in getters/setters. We just return and set the field, which is same as exposing a field as public. So why are you saying all of this? 

To answer this question, I say by writing getters/setters, we create a provision to add any validation method in the future, currently, there is no validation, but if anything goes wrong in the future we just add validation logic in the setter.

But still, it opens a debate with those who claim to be big followers of YAGNI (You Ain't Gonna Need It). They can say that when there are no such validation constraints for a field, why bother writing a getter/setter? I can simply expose it as public.

As per my understanding, The crux of YAGNI is to avoid making your code unnecessarily complex. It's like when someone tries to think big and makes their code base so generic that it welcomes any changes. But most of the changes he/she thinks of will never come.

## **Conclusion**

Getters/setters do not make your code complex and welcome future validations. So please, go for it.

Discover how the Watson team is [further developing SDKs in Java](https://bs.serving-sys.com/serving/adServer.bs?cn=trd&mc=click&pli=20943536&PluID=0&ord=%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://bs.serving-sys.com/serving/adServer.bs?cn=trd&mc=click&pli=20943536&PluID=0&ord=%5Btimestamp%5D).

### Like This Article? Read More From DZone
