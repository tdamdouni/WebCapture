# Clean Code From the Trenches: Validation

_Captured: 2017-05-17 at 00:19 from [dzone.com](https://dzone.com/articles/clean-code-from-the-trenches-validation?edition=298107&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-16)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).

Let's start with an example. Consider a simple web service that allows clients to place an order to a shop. A very simplified version of the order controller could look something like below:

And the corresponding DTO class:

The most common approach for creating an order from this DTO is to pass it to a service, validate it as necessary, and then persist it in the database:
    
    
            if (menuId == null || menuId.trim().isEmpty()) {
    
    
            if (description == null || description.trim().isEmpty()) {
    
    
            if (price == null || price.trim().isEmpty()) {
    
    
            if (orderItem.getQuantity() == null) {
    
    
            if (orderItem.getQuantity() <= 0) {

The validate method is not written well. It is very hard to test. Introducing a new validation rule in the future would also be hard, and so would removing/modifying any of the existing ones. From my experience, I have seen that most people write a few generic assertions for this type of validation check, typically in an integration test class, touching only one or two (or more, but not all) of the validation rules. As a result, refactoring in the future can only be done in **_[Edit and Pray](https://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052) _**mode.

We can improve the code structure if we use polymorphism to replace these conditionals. Let's create a common super type for representing a single validation rule:

The next step is to create validation rule implementations, which will focus on separate validation areas for the DTO. Let's start with the menu validator:
    
    
            String menuId = Optional.ofNullable(orderItem.getMenuId())
    
    
                .filter(id - > !id.isEmpty())
    
    
            if (!menuRepository.menuExists(menuId)) {

Then the item description validator:
    
    
                .filter(description - > !description.isEmpty())

Price validator:
    
    
                throw new IllegalArgumentException("Given price [" + price + "] is not in valid format", ex);

And finally, the quantity validator:
    
    
                throw new IllegalArgumentException("Given quantity " + quantity + " is not valid.");

Each of these validator implementations can now be easily tested -- independently from each other. Reasoning about each one of them also becomes easier, as do future additions, modifications, and removals.

Now the wiring part. How can we integrate these validators with the order service?

One way would be to directly create a list in the OrderService constructor and populate it with the validators. Or we could use Spring to inject a List into the OrderService:
    
    
            validators.forEach(validator - > validator.validate(orderItem));

In order for this to work, we will have to declare each of the validator implementations as a Spring Bean.

We could improve our abstraction even further. The OrderService is now accepting a List of the validators. However, we can change it to be only aware of the OrderItemValidator type, and nothing else. This gives us the flexibility of injecting either a single validator or any composition of validators in the future.

So now our goal is to change the order service to treat a composition of order item validators in the same way as a single validator. There is a well-known design pattern called [Composite](https://sourcemaking.com/design_patterns/composite) that lets us do exactly that.

Let's create a new implementation of the validator interface, which will be the composite:
    
    
            validators.forEach(validators - > validators.validate(orderItem));

We then create a new Spring configuration class, which will instantiate and initialize this composite, and then expose it as a bean:

We then change the OrderService class in the following way:

And we are done!

The benefits of this approach are many. The whole validation logic has completely been abstracted away from the ordering service. Testing is easier. Future maintenance is easier. Clients only know about one validator type, and nothing else.

However, all of the above come with some problems, too. Sometimes people are not comfortable with this design. They may feel like this is just too much abstraction, or that they will not need this much flexibility or testability for future maintenance. I'd suggest adopting this approach based on the team culture. After all, there is no single right way of doing things in software development.

Note that for the sake of this article, I have taken some shortcuts here as well. These includes throwing a generic IllegalArgumentException when validation fails. You'd probably want a more specific/custom exception in a production-grade application to identify between different scenarios. The decimal parsing is also done naively. You might want to fix on a specific format, and then use DecimalFormat to parse it.

The full code has been uploaded to [GitHub](https://github.com/sayembd/java-examples/tree/20170511-clean-code-from-the-trenches-validation/java-validation).

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).
