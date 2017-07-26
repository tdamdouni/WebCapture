# Payload Transformation: JSON to Object

_Captured: 2017-04-18 at 19:49 from [dzone.com](https://dzone.com/articles/payload-transformation-json-to-object?edition=293881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-18)_

[Discover how Microservices are a type of software architecture](https://dzone.com/go?i=201129&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-how-to-build-scale-with-microservices%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%252520zone%26utm_content%3Debook-how-to-build-scale-with-microservices%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital) where large applications are made up of small, self-contained units working together through [APIs that are not dependent on a specific language.](https://dzone.com/go?i=201129&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-how-to-build-scale-with-microservices%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%252520zone%26utm_content%3Debook-how-to-build-scale-with-microservices%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital) Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201129&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-how-to-build-scale-with-microservices%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%252520zone%26utm_content%3Debook-how-to-build-scale-with-microservices%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

When you are first starting out with Mule, it is very important to learn the basics, such as how to manipulate the incoming payload.

In this article, I am going to explain how you to transform an incoming payload (JSON) to a Java object.

Most of the work in development revolves around payload transformation, so it is very important to tackle this -- especially for beginners.

I will first show the basics, and later on, we will get into the more advanced stuff.

## **The Basics**

Let's first start by posting a very basic JSON string as payload.

![Image title](https://dzone.com/storage/temp/4942207-screen-shot-2017-04-12-at-42302-pm.png)

Given the JSON string above, let's now define a transformer component in our flow.

In our case, we are going to use a JSON to Object transformer.

![Image title](https://dzone.com/storage/temp/4942234-screen-shot-2017-04-12-at-43140-pm.png)

Under the **General** properties of the JSON to Object transformer component, you can define your desired return class.

Let's define `java.util.HashMap` as the return class for this example.

![Image title](https://dzone.com/storage/temp/4942251-screen-shot-2017-04-12-at-43927-pm.png)

Once you run the flow above, our JSON string payload is then converted to a Java object `HashMap`. You will then be able to access the properties of your payload through `payload.<propertyname>`, where`propertyname` is defined in the JSON string (i.e. `payload.age`).

You can also use other Java Objects such as `java.util.ArrayList`, `java.util.LinkedList`, etc.

## **Taking It Further**

What if you would like to transform the incoming JSON string into a custom Java object?

In order for us to satisfy this, let's first define a custom Java class (`Student`) with`GET` and `SET` methods.

![Image title](https://dzone.com/storage/temp/4942452-screen-shot-2017-04-12-at-50804-pm.png)

Note: The custom Java class' variables should have the exact same name (case sensitive) as the JSON string's properties. If the names are different, the transformer component will throw an error.

Once this is done, we can then change the return class of the JSON to Object transformer component we defined earlier to our custom class: `packageName.className`.

For example, `myschool.model.Student`:

![Image title](https://dzone.com/storage/temp/4942548-screen-shot-2017-04-12-at-51737-pm.png)

> _Let's try to debug this example._

![Image title](https://dzone.com/storage/temp/4942588-screen-shot-2017-04-12-at-52040-pm.png)

As you can see, our original payload has been transformed into the custom Java object `Student`.

We can then try to access the properties of our payload through `payload.<propertyname>`,`propertyname` being defined in the custom Java class -- i.e. `payload.age`.

## **Next Steps**

How about transforming the JSON String into a custom Java object with a custom Java object `children`?

Does this also work using the JSON to Object component?

The answer is yes!

Let's try to make our JSON string a little bit more complex.

![Image title](https://dzone.com/storage/temp/4942658-screen-shot-2017-04-12-at-53108-pm.png)

> _We now have an additional JSON properties named subjects ._

If we are going to use the previous custom Java class we defined, the transformer component will throw an `UnrecognizedPropertyException` exception since we have not defined any property named `subjects` in our Java class.

In order for us to satisfy this condition, let's first start creating another class named `Subject` and add the list of `Subject` into our `Student` class later on.

Our `Subject` class should look like this:

![Image title](https://dzone.com/storage/temp/4942700-screen-shot-2017-04-12-at-53838-pm.png)

After defining our `Subject` class, we can then add it into our `Student` class.

Add the following code into `Student.java`: `private List subjects; `.

Don't forget to add the `GET` and `SET` methods for the newly added variable subjects.

![Image title](https://dzone.com/storage/temp/4942721-screen-shot-2017-04-12-at-54236-pm.png)

Let's now test our application and check to see if the payload transformation to our newly defined custom Java class is successful.

![Image title](https://dzone.com/storage/temp/4942769-screen-shot-2017-04-12-at-55129-pm.png)

As you can see from the image above, our JSON string has been successfully transformed into our new custom Java object!

[Discover the six challenges and best practices in managing microservice performance](https://dzone.com/go?i=201130&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Ftop-6-performance-challenges-in-managing-microservices%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%252520zone%26utm_content%3Dtop-6-performance-challenges-in-managing-microservices%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital), brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201130&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Ftop-6-performance-challenges-in-managing-microservices%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%252520zone%26utm_content%3Dtop-6-performance-challenges-in-managing-microservices%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

Opinions expressed by DZone contributors are their own.
