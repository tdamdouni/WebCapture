# The Pipeline Pattern — for fun and profit

_Captured: 2016-12-09 at 21:52 from [medium.com](https://medium.com/@aaronweatherall/the-pipeline-pattern-for-fun-and-profit-9b5f43a98130?source=userActivityShare-c79006fee040-1481316743)_

![](https://cdn-images-1.medium.com/max/800/1*OiDHR7xk6uiKnuSzNy9arQ.jpeg)

I wanted to share a little about my favourite design pattern -- I literally can not get enough of it. Think of the 'Pipeline Pattern' like a conveyor belt or assembly line that takes an object, modifies it and passes it onto the next class.

We do this all the time in engineering.

**Consider an order transaction in an eCommerce site.**

  1. User places the order
  2. Payment processor takes the payment
  3. Invoice is generated and sent to the user
  4. The order is sent to your ERP system
  5. The order is packed and shipped
  6. Customer receives a thank-you email.

While this may be more useful with some kind of state-machine, this clearly shows the concept of a pipe.

There is one primary constant in all of these steps -- the _order_. This _order_ _Array/Class/Object/TransferObject_ etc is passed to each phase of the process until completed.

If you've created something similar in the past, it's a pretty good bet that there's something ugly like this going on in a file called Order.php.
    
    
    **if** ($order->getStatus() === 'success') {  
     $this->getErpAdapter()->sendOrder($order);  
    }

To figure out the whole process, I'd have to go through EVERY line of code to figure out what's going on! Ain't no one got time for that!

Here's one of my favourite quotes from Martin Fowler.

> Any fool can write code that a computer can understand. Good programmers write code that humans can understand.

Now, consider this.
    
    
    $pipeline = (new Pipeline)  
     ->pipe(new createOrder)  
     ->pipe(new processPayment)  
     ->pipe(new sendInvoice)  
     ->pipe(new exportOrder);
    
    
    $pipeline->process($order);

Can someone say '_readability_', please?

This is also a _huge_ win for testability and single responsibility -- what this means is that each piece of code only does one or two things that it was designed to do, then passes the torch to the next class.

To make testing easier, each of these stages can be easily mocked -- or even the whole pipeline!

### Definition of the Pipeline Pattern

If you're still not sure about the definition, here's a better description from some great algorithm design documentation.

> As each stage completes a step of a calculation, it passes the calculation-in-progress to the next stage and begins work on the next calculation."

### Implementation in PHP

Since I'm a PHP developer (well, mostly!), I'm doing my examples in that -- BUT, you can easily apply this pattern to any language.

There are plenty of libraries out there that implement this pattern, but my favourite is PHP League Pipeline.

It's super simple and FAST -- go and check out their site.

If you're not already a fan of the PHP League, please go and check it out immediately, their packages are first rate. Their packages are rock-solid, backed by incredible code coverage/testing and have awesome documentation.

See that? Builds passing, code quality and coverage.. it's that good.

From the authors:

> "This package provides a plug and play implementation of the Pipeline Pattern. It's an architectural pattern which encapsulates sequential processes. When used, it allows you to mix and match operation, and pipelines, to create new execution chains. The pipeline pattern is often compared to a production line, where each stage performs a certain operation on a given payload/subject. Stages can act on, manipulate, decorate, or even replace the payload.

> If you find yourself passing results from one function to another to complete a series of tasks on a given subject, you might want to convert it into a pipeline."

So.. how do we use it?

#### Composer install

Run `composer require league/pipeline` in your project folder to add it to your project. Great.. we're ready to go!

#### Assemble your class

We're going to need a few pieces, so let me first show you how it all goes together, then we'll look at the individual class requirements.

Here's a new class which we'll call **RunAllTheThings --** all this class will do is when we call the RunAllTheThings->doIt method, we will execute the pipeline and return the result.
    
    
    <?php  
    **namespace** Example\Pipeline;
    
    
    /**  
     * Class RunAllTheThings  
     * [@package](http://twitter.com/package) Example\Pipeline  
     */  
    **class** RunAllTheThings  
    {  
     /**  
     * [@return](http://twitter.com/return) Payload  
     */  
     **public** **function** doIt()  
     {  
     // Define the pipeline stages  
     $pipeline = (new Pipeline)  
     ->pipe(new Segment\DoStage1))  
     ->pipe(new Segment\DoStage2))  
     ->pipe(new Segment\DoStage3));  
       
     // The payload is an object that's passed between stages  
     $payload = new Payload();
    
    
     // Run the pipeline  
     $pipeline->process($payload);
    
    
     **return** $payload;  
     }  
    }

Simple, eh? Let's have a look at some of the sub classes.

#### Payload

The payload is something I really like to add in here as it keeps the data being passed though the pipe clean and readable.

In this example, payload is just a simple entity with a protected property and some getters and setters. It gives us a clean way to not only update the results, but an expected format at the end.

Because the `doIt` method returns this object, we know that we can do something like `$result->getResult()` to get what we need.

This payload can be as simple of as complex as you need.
    
    
    <?php  
    **namespace** Example\Pipeline;
    
    
    /**  
     * Class Payload  
     * [@package](http://twitter.com/package) Example\Pipeline  
     */  
    **class** Payload  
    {  
     /**  
     * [@var](http://twitter.com/var) null|string  
     */  
     **protected** $result = null;
    
    
     /**  
     * [@param](http://twitter.com/param) string $result  
     * [@return](http://twitter.com/return) static  
     */  
     **public** **function** setResult($result)  
     {  
     $this->result = $result;  
     **return** $this;  
     }
    
    
     /**  
     * [@param](http://twitter.com/param) $result  
     * [@return](http://twitter.com/return) $this  
     */  
     **public** **function** addResult($result)  
     {  
     $this->result .= $result;  
     **return** $this;  
     }  
    }

#### Stage 1

Stages need to be `callable` this means that they need to either be a closure, a callback or have an `__invoke` method. We're going to use the latter for this example.

For more about the `callable` type, please see the following reference. <http://php.net/manual/en/language.types.callable.php>
    
    
    <?php  
    namespace Example\Pipeline;
    
    
    /**  
     * Class Stage1  
     * [@package](http://twitter.com/package) Example\Pipeline  
     */  
    **class** Stage1  
    {  
     **public function** __invoke(Payload $payload)  
     {  
     $payload->addResult('all');  
     **return** $payload;  
     }  
    }

In this stage, we're adding the word `all` to the result string. Once we've modified the result, you simply return the payload and the next stage will run.

#### Stage 2

You may start to see the pattern emerging here. This stage takes the payload, adds the word `the` and continues.
    
    
    <?php  
    namespace Example\Pipeline;
    
    
    /**  
     * Class Stage2  
     * [@package](http://twitter.com/package) Example\Pipeline  
     */  
    **class** Stage2  
    {  
     **public function** __invoke(Payload $payload)  
     {  
     $payload->addResult('the');  
     **return** $payload;  
     }  
    }

#### Stage 3

Guess what this stage does? Yep, we add the word `things` to the result.
    
    
    <?php  
    namespace Example\Pipeline;
    
    
    /**  
     * Class Stage3  
     * [@package](http://twitter.com/package) Example\Pipeline  
     */  
    **class** Stage3  
    {  
     **public function** __invoke(Payload $payload)  
     {  
     $payload->addResult('things');  
     **return** $payload;  
     }  
    }

Right, so let's run our code.
    
    
    **<?php**  
    $allThethings = **new** \Example\Pipeline\RunAllTheThings();  
    $result = $allThethings->doIt();
    
    
    **var_dump**($result->getResult());

This will print the the following array to the screen.
    
    
    string "allthethings"

### **Short-circuiting**

Sometimes you simply don't want to continue processing. If an order is _invalid_ why would you attempt to capture payment?

How do we tackle that?

The simplest way is with a try/catch. Now just throw a `LogicException` in one of your stages.
    
    
    try {  
     $pipeline->process($payload);  
    catch (LogicException $e) {  
     // Do something else!  
    }

### Dynamic Pipelines

There's another useful aspect of League\Pipeline that I love which is the `PipeBuilder` -- This allows you to add logic as to whether to add a stage to the pipeline.
    
    
    use League\Pipeline\PipelineBuilder;
    
    
    // Instantiate the PipelineBuilder  
    $builder = (new PipelineBuilder)  
     ->add(new CreateOrder);
    
    
    // Conditional stage  
    if ($order->getOrigin() === 'New Zealand') {  
     $builder->add(new PreBookCarrier);  
    }
    
    
    // Continue adding more stages  
    $builder->add(new processPayment)  
     ->add(new sendInvoice)  
     ->add(new exportOrder);
    
    
    // Assemble to pipeline  
    $pipeline = $builder->build();
    
    
    // Process  
    $pipeline->process($order);

### Reusing Pipes

It may be useful sometimes to reuse a pipe inside another pipe! Easy enough since the pipe method can accept a `callable` OR another pipe.
    
    
    $createOrder = (new Pipeline)  
     ->pipe(new CreateOrder)  
     ->pipe(new GenerateInvoice);
    
    
    $pipeline = (new Pipeline)  
     ->pipe($createOrder)  
     ->pipe(new ProcessPayment)  
     ->pipe(new SendInvoice)  
     ->pipe(new ExportOrder);
    
    
    $pipeline->process($order);

### Conclusion

While the pipeline pattern isn't for every occasion, there is a LOT of ugly code out there that could benefit from the simplicity and readability this pattern provides.

Next time you find yourself building a multi-stage piece of code try the pattern out and see how it goes.
