# Understanding '*', '*args', '**' and '**kwargs'

_Captured: 2016-06-01 at 11:50 from [agiliq.com](http://agiliq.com/blog/2012/06/understanding-args-and-kwargs/)_

When i started learning Python, i was very confused regarding what args, kwargs, * and ** does. And i feel there are few like me who had this confusion and problem. With this post, i intend to reduce (hopefully i can eliminate) that confusion.

Throughout this post, i will be using ipython and i suggest you to try everything on ipython as well. We will intentionally make some mistakes along the way, so that we can understand this topic better.

### Let's divide our work under five sections:

  1. Understanding what '*' does from inside a function call.
  2. Understanding what '*args' mean inside a function definition.
  3. Understanding what '**' does from inside a function call.
  4. Understanding what '**kwargs' mean inside a function definition.
  5. A practical example of where we use 'args', 'kwargs' and why we use it.

### Understanding what * does from inside a function call.

Let's define a function "fun" which takes three positional arguments.
    
    
    In[5]:deffun(a,b,c):  
       ...:printa,b,c  
       ...:       
       ...:

Call this function passing three positional arguments
    
    
    In[7]:fun(1,2,3)123#Output

So, calling this function by passing three positional arguments, prints the three arguments passed to the function.

Let's make a list with three integer values in it.

Let's use '*' now.
    
    
    In[9]:fun(*l)123#Output

#### What did '*' do?

It unpacked the values in list 'l' as positional arguments. And then the unpacked values were passed to function 'fun' as positional arguments.

So, unpacking the values in list and changing it to positional arguments meant writing fun(*l) was equivalent to writing fun(1,2,3). Keep in mind that l=[1,2,3]. Let's try with some other value of 'l'.

Let's make some errors now. Let's put four values in "l".

Now, try to call function "fun".

So, in our last statement which is 'fun(*l)' we did not get a proper output and a TypeError was raised. See the error, it says "TypeError: fun() takes exactly 3 arguments (4 given)".

#### Why did it happen?

list 'l' contains four values. So, when we tried 'fun(*l)', 'l' was unpacked so that its value could be sent as positional arguments. But, "l" has four values in it. So, writing 'fun(*l)' was equivalent to writing 'fun(3,5,6,9)'. But, 'fun' is defined to take only three positional arguments and hence we got this error. Similary, you can follow same steps with two values in list 'l' and notice the error.

Let's mix '*l' with a positional argument.

Here we gave one positional argument which is 1 and two values i.e 5 and 6 were unpacked from "l" and hence 1,5 and 6 were passed to 'fun'.

Hope you were able to follow what '*' does when used inside a function call.

### Understanding what '*args' mean inside a function definition.

Let's change the function definition now.

Call this function with one positional argument.

Now call this function with two positional arguments or any number of positional arguments you wish.

#### What does '*args' in a function definition do?

It recieves a tuple containing the positional arguments beyond the formal parameter list. So, "args" is a tuple. Don't worry about the part "formal parameter list" in our explanation, it will be clear with next few examples. In our last example when we printed "args", it printed a tuple which contained all the values we passed while calling the function.

Let's mix "*args" with some "formal parameter list". Note that in our last example we didn't have any formal parameter list. Let's redefine our function.

In this function definition, parameter "a" constitue the "formal parameter list". Let's call "fun" with four positional argument.

So, we can see that 'a' is assigned 1 which was the first positional argument. There is only one parameter "*args" defined after "a". So, "args" received a tuple containing the positional arguments beyond the formal parameter list. So, args received 2, 3 and 4 as a tuple.

We can also call "fun" with just one positional argument. Let's do that.

Here, we passed only one argument to the function which was assigned to the formal parameter 'a'. So, 'args' received an empty tuple as can be seen from the output.

After we have "args", we can extract the values and do whatever we want. Let's redefine "fun".

We can call "fun" with any number of arguments.

Since 'args' is a tuple, we could iterate over it.

Now, let's consider a case where we use whatever we saw till here. Here we need to use two functions. First function has to take an arbitrary number of arguments and it has to calculate the sum of all the arguments except the first argument. Also, this function has to make use of another function to calculate the sum. Weird use case, but we just need to recap whatever we did till here. The objective here is to see how we get a variable number of arguments in a function and pass these arguments to another function.

Let's first write the function which has to calculate the sum i.e the second function. For our use case, this function will be used in the first function which we are yet to write.

Here we make use of 'sum'. Function 'sum' is an inbuilt function which takes a tuple or a list and return the sum of all the elements in the tuple. From our function definition we can see that 'args' will receive a tuple containing all the positional arguments passed to this function. So, 'args' will be a tuple and can be directly used as an argument to function 'sum'. Let's write the other function which takes any number of arguments and uses previous function to calulate the sum of all arguments except the first argument.

We can pass any number of arguments to this function. First argument will be recieved by 'a' which is a formal parameter. All other arguments will be recieved by 'iargs' as a tuple. As per the case we are considering, we want to calculate the sum of all arguments except the first. So, we leave 'a' as it receives the first argument. 'iargs' is the tuple containing all arguments except the first. We will make use of function 'calculate_sum'. But 'calculate_sum' expects number of positional arguments to be sent to it which it will receive in 'args' as a tuple. So, in function 'ignore_firstargs_calculate_sum' we need to unpack 'iargs', as it is a tuple, and then send the unpacked positional arguments to 'calculate_sum'. Remember, we used '*' to unpack a list/tuple.

So, we write 'required_sum=calculate_sum(*iargs)'.

We can't write 'required_sum=calculate_sum(iargs)' because we need to unpack the values in the tuple 'iargs' before sending to 'calculate_sum'. Not using '*' will not unpack the values and hence we won't have the desired behaviour. Let's use the function we wrote.

The output is the sum of all arguments except the first argument.

### Understanding what '**' does when used from inside a function.

Let's consider a simple example first. Let's define a function which takes three arguments.

Let's call this function in various ways.

Let's use "**" from inside the function call. For this we want a dictionary. Remember, while using "*" in the function call, we required a list/tuple. For using "**" in the function call, we require a dictionary.

Let's call "fun" using "**" in the function call.

#### What "**" did while being used in a function call?

It unpacked the dictionary used with it, and passed the items in the dictionary as keyword arguments to the function. So writing "fun(1, **d)" was equivalent to writing "fun(1, b=5, c=7)".

Let's try some more examples to understand it better.

Let's make some errors now.

Last statement was equivalent to fun(a=1, b=2, c=3, d=4). But, "fun" expected only three arguments and hence we got this error.

Last statement was equivalent to fun(a=1, b=5, d=9). Although it passed three arguments which is the number of arguments expected by "fun", but "fun" does not have 'd' in its parameter list. But, 'd' was passed as a keyword argument And hence we got this error.

So, "**" unpacks the dictionary i.e the key values pairs in the dictionary as keyword arguments and these are sent as keyword arguments to the function being called. "*" unpacks a list/tuple i.e the values in the list as positional arguments and these are sent as positional arguments to the function being called.

### Understanding "**kwargs" in a function definition.

Let's redefine our function "fun".

So, this function can only take one positional argument since formal parameter list contains only one variable 'a'. But with "**kwargs", it can take any number of keyword arguments. Let's see some examples.

#### What does "**kwargs" mean when used in a function definition?

With "**kwargs" in the function definition, kwargs receives a dictionary containing all the keyword arguments beyond the formal parameter list. Remember 'kwargs' will be a dictionary. In our previous two examples, when we printed kwargs, it printed a dictionary containing all the keyword arguments beyond the formal parameter list.

Let's again redefine our function.

Let's call "fun" now.

Let's make some errors now.

We were able to call the function. First positional argument was printed. Keyword argument 'b' was printed. But the other keyword argument we passed was 'd'. Since function expected a keyword argument 'c' and tried to access it from the dictionary "kwargs". But since we did not pass any keyword argument 'c', we got this error. If we add a keyword argument 'c' in the function call, we won't get the error anymore.

Since having "**kwargs" in the function argument list, we can pass any number of keyword arguments. We passed 'd' but did not make any use of it in the function.

Let's make one more error.

As the error says, Function "fun" expected only one postional argument but was given two. So, although 'kwargs' receives the keyword arguments as a dictionary, you cannot pass a dictionary as a positional argument to 'kwargs'. Although you could have done somehing like:

Using "**" in front of the dictionary unpacks the dictionary and passes the items in dictionary as keyword arguments.

### A practical example of where we use '_args', '_*kwargs' and why we use it.

Whenever we inherit a class and override some of the methods of inherited class, we should use '*args' and '**kwargs' and pass the received positional and keyword arguments to the superclass method. Can be better understood with an example.

We defined a class. We can create objects of this class and objects of this class have a method "save()". Assume that the objects of this class can be saved in a database which is being done inside the save() method. Depending on the arguments we pass to save() method, it is determined whether new records need to be created in the database or an existing record need to be updated.

We want a new class where we want 'Model' behaviour but we only want to have save the objects of this class after we have checked some conditions. So let's subclass 'Model' and override 'save()' of 'Model'.

Actual saving of object(as per our assumption, connecting with database and creating/updating) happens in the "save" method of "Model". So we need to call the "save()" method of superclass from save() method of ChildModel. Also, save() method of subclass i.e ChildModel should be able to accept any arguments that save() of superclass accepts and must pass through these arguments to the superclass save(). So we have "*args" and "**kwargs" in the argument list of subclass save() method to receive any positional arguments or keyword arguments beyond the formal parameter list.

Let's create an instance of ChildModel and save it.

So, we created an instance of ChildModel with name='abcd'.

Here, we passed a keyword argument to save() of the object. The save() we called is the subclass save(). It received a dictionary containing the keyword argument in "kwargs". Then it used "**" to unpack this dictionary as keyword arguments and then passed it to the superclass save(). So, superclass save() got a keyword argument 'force_insert' and acted accordingly.

Let's try to pass another keyword argument.

That was all about it. Hope you liked the post.

Can we help you build amazing apps? [Contact us today.](http://agiliq.com/contactus)
