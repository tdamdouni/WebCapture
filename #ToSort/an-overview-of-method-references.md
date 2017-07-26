# An Overview of Method References

_Captured: 2017-01-27 at 19:39 from [dzone.com](https://dzone.com/articles/methodreference?edition=265886&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-27)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ).

Method references are a feature of Java 8. They are effectively a subset of lambda expressions, because if a lambda expression can be used, then it might be possible to use a method reference, but not always. They can only be used to call a singular method, which obviously reduces the possible places they can be used, unless your code is written to cater for them.

It would be a good idea if you knew the notation for a method reference. In fact, you have probably already seen it assuming you read the title. If not then just look below.

`Person::getName`

The example above is the equivalent of writing _person.getName()_, where _person_ is an instance of _Person_. Let me tell you a bit more about when you can use method references and show some examples as it makes a lot more sense with them.

## **Types of Method References**

**Type**
**Syntax**
**Method Reference**
**Lambda expression**

Reference to a static method
_Class::staticMethod_
_String::valueOf_
_ s -> String.valueOf(s)_

Reference to an instance method  
of a particular object
_instance::instanceMethod_
_s:toString_
_() -> "string".toString()_

Reference to an instance method  
of an arbitrary object of a particular type
_Class:instanceMethod_
_String::toString_
_s -> s.toString()_

Reference to a constructor
_Class::new_
_String::new_

_() -> new String()_

## **Reference to a Static Method**
    
    
            List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
    
    
        public static void print(final int number) {
    
    
            System.out.println("I am printing: " + number);

Here, it calls the static method _StaticMethodReference.print. _This example is pretty simple. There is a static method, and for each element in the list, it calls this method using the element as the input.

## **Reference to an Instance Method of a Particular Object**
    
    
            final List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
    
    
            Collections.sort(list, (a,b) -> myComparator.compare(a,b));
    
    
            public int compare(final Integer a, final Integer b) {

Here, it calls the instance method _myComparator.compare_, where _myComparator_ is a particular instance of _MyComparator_.

## **Reference to an Instance Method of an Arbitrary Object of a Particular Type**
    
    
        public static void main(String args[]) {
    
    
            final List<Person> people = Arrays.asList(new Person("dan"), new Person("laura"));
    
    
            people.forEach(person -> person.printName());

This calls the method _Person.getName_ for each _Person_ object in the list. _Person_ is the particular type, and the arbitrary object is the instance of _Person_ that is used during each loop. This looks very similar to a reference to a static method, but the difference is how the object is passed to the method reference. Remember, a static reference passes the current object into the method, whereas an arbitrary method reference invokes a method onto the current object.

## **Reference to a Constructor**
    
    
            final List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
    
    
            copyElements(list, () -> new ArrayList<Integer>());
    
    
        private static void copyElements(final List<Integer> list, final Supplier<Collection<Integer>> targetCollection) {
    
    
            list.forEach(targetCollection.get()::add);

This is the example I had the most trouble trying to make, as no matter how hard I thought, I couldn't think of a way this could be used in something complicated. I am sure my opinion would change if I used Java 8 while at work, but for now, I do not see why this type of method reference is particularly useful. The example uses the _Supplier_ functional interface to pass _Integer::new_ into the _copyElements_ method.

## Conclusion

In conclusion, method references can be used to make your code even more concise, but they have some restrictions on when they can be used for and what they can do. If you simplify your code by using a lambda expression, then you might be able to make it even shorter by using a method reference. Eventually, your code will be so short your bosses will wonder what you have even been doing as you have only written a few lines of code!

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ).
