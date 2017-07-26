# Is This Code Functional Vomit?

_Captured: 2017-04-17 at 21:20 from [dzone.com](https://dzone.com/articles/is-this-code-functional-vomit?edition=291881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-17)_

Navigate the Maze of the End-User Experience and pick up this [APM Essential guide](https://www.ca.com/us/collateral/industry-analyst-report/apm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html?mrm=519574), brought to you in partnership with [CA Technologies](https://www.ca.com/us/collateral/industry-analyst-report/apm-essentials-navigating-the-maze-of-end-user-experience-solutions.register.html?mrm=519574).

Hi. My name is Matt, and I have pull-request-criticism-ophobia. I die a little inside every time someone tells me what a noob I have been when writing code.

I am also a Java 8 developer and have developed an interest in functional programming. One day, I found the Optional class, and my life has been a living hell ever since. Here's why.

I was tasked to write the following code:

  * The method must convert an object of type ObjectA to an object of type ObjectD

  * The conversion will be done via a number of service objects that will do the hard work of converting ObjectA to ObjectB, ObjectB to ObjectC, and ObjectC to ObjectD.

  * These services do not throw exceptions, or throw only runtime exceptions.

  * These services return a mixture of null or empty Optional objects to indicate that no conversion could take place.

  * The method should return an empty Optional if the supplied ObjectA was null, or if any conversion returns null or an empty Optional.

Because I have read no less than three blog posts on Monads (so many cute pictures of cats in boxes) and have spent several hours reading up on functional programming, I feel like I am a functional programming boss, and pump out the following code:
    
    
    public class MyClass {
        @Autowired
        private ConvertAToB convertAToB;
    
        @Autowired
        private ConvertBToC convertBToC;
    
        @Autowired
        private ConvertCToD convertCToD;
    
        public Optional<ObjectD> convertAToD(ObjectA objectA) {
            return Optional.ofNullable(objectA)
                .flatMap(convertAToB::convertToB)
                .map(convertBToC::convertToC)
                .map(convertCToD::convertToD);
        }
    }

The code is clean, declarative, and functional. I've neatly dealt with nulls and empty optionals without nested if blocks. I'm feeling pretty good at this point. Until I go and listen to a [talk by Stuart Marks](https://virtualjug.com/vjug24-session-optional-the-mother-of-all-bikesheds-by-stuart-marks/), one of the guys who designed the Optional class, who very clearly says this:

> Optional is intended to provide a limited mechanism for library method return types where there is a clear need to represent "no result," and where using null for that is overwhelmingly likely to cause errors. 

He goes on to list a number of rules around the use of the Optional class:

  1. Never, ever, use null for an Optional variable or return value.

  2. Never use Optional.get() unless you can prove that the Optional is present.

  3. Prefer alternatives to Optional.isPresent() and Optional.get().

  4. It's generally a bad idea to create an Optional for the specific purpose of chaining methods from it to get a value.

  5. If an Optional chain has a nested Optional chain, or has an intermediate result of Optional, it's probably too complex.

  6. Avoid using Optional in fields, method parameters, and collections.

  7. Avoid using identity-sensitive operations on Optionals.

My heart sinks. It seems like my clever method chaining with map and flatMap just violated the intended purpose of the Optional class. Given my fear of criticism in pull requests, I quickly refactor the code to only use Optional as a return type and remove all method chaining:
    
    
    public class MyClass {
        @Autowired
        private ConvertAToB convertAToB;
    
        @Autowired
        private ConvertBToC convertBToC;
    
        @Autowired
        private ConvertCToD convertCToD;
    
        public Optional<ObjectD> convertAToD(ObjectA objectA) {
            if (objectA != null) {
                Optional<ObjectB> objectB = convertAToB.convertToB(objectA);
                if (objectB.isPresent()) {
                    ObjectC objectC = convertBToC.convertToC(objectB.get());
                    if (objectC != null) {
                        ObjectD objectD = convertCToD.convertToD(objectC);
                        return Optional.ofNullable(objectD);
                    }
                }
            }
            return Optional.empty();
        }
    }

Great. I'm pretty sure I'm no longer violating the intended use of the Optional class here. It is used as a return type and nothing more, and I am no longer chaining methods to get a value.

But, try as I might, I just can't see this refactoring as better code.

Help me, Internet. Is Optional map and flatMap chaining an example of clean code, or is it functional vomit that abuses the limited scope of the Optional class?

Thrive in the application economy with [an APM model that is strategic](https://www.ca.com/us/collateral/ebook/epic-apm-toward-a-better-apm-model-for-the-application-economy.register.html?mrm=519574). Be E.P.I.C. with CA APM. Brought to you in partnership with [CA Technologies](https://www.ca.com/us/collateral/ebook/epic-apm-toward-a-better-apm-model-for-the-application-economy.register.html?mrm=519574).

### Like This Article? Read More From DZone

Opinions expressed by DZone contributors are their own.
