# WTF Is a Thread?

_Captured: 2017-11-10 at 17:18 from [dzone.com](https://dzone.com/articles/wtf-is-a-thread?edition=334900&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202017-11-10)_

What exactly is a thread? Many developers have been exposed to threads and processes over their careers without actually knowing how they work. Knowing more about our tools makes us better developers. To answer "WTF is a Thread?", I took an operating systems course at Georgia Tech and then put my own spin on the information:

  * Video is 6 minutes and 22 seconds.

If you prefer text explanations, here's the synopsis:

What is a thread? Before we can talk about a thread we have to understand a process. A process is an instance of an executing program, at its core, a process is essentially a blob of memory. It has code that needs to be executed, it has data such as variables, it has a register, and a stack to keep track of the order of execution. The code is going to be compiled into instructions that can run on our CPU.

Here's an example of a program in C.
    
    
      for(i=0; i < 10; i+=1) {

When we compile this, it's going to turn into instructions that are gonna look like this:

> Thanks to Julia Evans for some inspiration in the post[ What is the Stack?](https://jvns.ca/blog/2016/03/01/a-few-notes-on-the-stack/)

As it runs, instructions are pulled off of memory and executed on the CPU. There are two really important parts of a process. There is a program counter. The program counter keeps track of where the process is currently executing. Imagine the program counter like an arrow pointing at an instruction set.

As the program runs, this location is kept by the hardware on a register on the CPU. When the program pauses or is preempted by another program, we have to store that counter somewhere.

There's also a thing called the stack. This keeps track of the depth of our program. Here is another example program:
    
    
      printf("Incremented to: %i\n", increment(i)); # <==== HERE

When this executes, the main function is added to the stack. The increment function is called and it is added to the stack. The increment function will eventually return.

Whenever we return, where does it go? The program looks at the stack and sees where we were currently executing and uses that to determine where to resume execution. The last entry on the stack before `increment` was `main` so that is where it goes.

At this point, we've got roughly everything we need to start and stop a program, including the program counter and the stack pointer. We need a way to store all of this data, and so it goes into a struct in the operating system called the process control block or PCB.

![](https://www.dropbox.com/s/63x1a8jv89tkb6k/Screenshot%202017-09-27%2014.22.37.png?dl=1)

The PCB includes process state, process number, program counter, registers, memory limits, list of open files, signal mask, and CPU scheduling information. In addition to some other things. Fun fact: since a process is entirely described by a PCB, whenever we wanna fork a process, essentially all we have to do is copy a parent process control block to a child process control block. Neato!

A process can execute two types of tasks. The first type of task is a CPU bound task. When the program is running and spending the majority of the time actually executing code. An example would be, processing data, or calculating prime numbers. The second type of a task a process can do is called an IO task (input/output task). An example of an IO task would be, reading a file from disk, or making a database call or making a network call, for example, to the Heroku API.

Whenever we're doing an IO heavy task the process doesn't do much. It makes the request and then it just sits there and waits for data to come back. This matters because we pay for our CPU time. We don't want our program to not be doing anything. We want to maximize our CPU utilization. How exactly can we do that?

If we have one CPU heavy process and one CPU then we're set.

![](https://www.dropbox.com/s/mo3bvrx3bhwcujc/Screenshot%202017-09-27%2014.23.53.png?dl=1)

> _The CPU is working at maximum speed. But what happens when we start to see IO?_

![](https://www.dropbox.com/s/b6eok9ttm16xm8q/Screenshot%202017-09-27%2014.24.07.png?dl=1)

In this example, our program is just sitting there and sleeping, our CPU is sitting there and not doing anything for a third of the time. And we're no longer using our CPU efficiently. We can fix this by adding an additional process.

![](https://www.dropbox.com/s/sd5bqh8vmaypisj/Screenshot%202017-09-27%2014.24.24.png?dl=1)

In this example, while one of our processes is sleeping, the other process is running. Aside from the context switch we are pretty much using our CPU 100% of the time. What are the pros of maximizing CPU with multiple processes?

Whenever we're using multiple processes to utilize our CPU then, well, we get better CPU utilization. So that's good.

What are the cons? Unfortunately, to do this, we need a lot of processes. Processes take up memory, which is a finite resource. Loading and unloading a PCB is expensive. Sharing data between processes is also hard: you can do things like map memory to different processes; though it's really difficult and most people don't really do it. We can also share data via sockets, but that's very limiting and also fairly difficult.

Wouldn't it be cool if there was some kind of really lightweight process that uses less memory, something with smaller time to context switch? Well, we have it, it's called threads.

Previously, we looked at a process and everything we need to run a program. With a thread, we can share code and we can also share data. Really, with a thread, all we need is a new stack and a new register.

This an example of what a single threaded process would look like.

![](https://www.dropbox.com/s/1irfa4cc7h9t981/Screenshot%202017-09-27%2014.25.29.png?dl=1)

It's a process and inside of it we have a thread, and that thread has a register and a stack. And if we want to have multiple threads on our process, then we don't have to duplicate that code or the data, we just need new registers and new stacks for each of our threads.

![](https://www.dropbox.com/s/tmqj0nxwxpk8sl7/Screenshot%202017-09-27%2014.25.47.png?dl=1)

All right, what are the pros of using multiple threads? Well, like before, we get much better CPU utilization. Unlike before, we can reuse existing process memory. Which means that we don't have to duplicate code, and we don't have to duplicate data. This means that we're not gonna run out of memory, or at least not nearly as fast. It also means that we have a smaller context switch time between the different threads as opposed to having the context switch between different processes. We can also reuse cached values, such as memory lookups.

All right, now there has to be a downside to this, and the downside actually looks a lot like the upside. Shared code and shared data inside of our thread makes things faster, and it makes things lightweight. Unfortunately, it means multi-threaded code is much harder to work with.

With shared code and data, now we have to consider other threads will be accessing our data. We have to introduce new constructs like mutexes and condition variables. The core value-add of threads is having that shared code. That's basically all a thread is - just a process with shared resources. Unfortunately, by doing that, we also add a lot of complexities.

Hopefully today you understand better what exactly a thread is: it's just a process with shared code and data. Threads are not mythical. Threads are a tool in our toolbox. Unfortunately, since a thread is so simple it would be hard to make them easier to use without turning them into a process.

> If you're interested in this kind of "how do components of operating systems work" I recommend [this operating system course on Udacity](https://www.udacity.com/course/introduction-to-operating-systems--ud923). It's basically the same content as a Georgia Tech Online Masters degree, but minus the homework assignments, tests, TAs, and office hours. If you prefer books, I like the [Operating System Concepts "dinosaur book"](https://www.amazon.com/Operating-System-Concepts-Abraham-Silberschatz/dp/1118129385) though it's not as approachable as the Udacity course.
> 
> The other major form of dealing with IO overhead in a program, is with an "evented" model. Which is what JavaScript currently uses. Although there have been talks about adding threads to JS. Evented code is not a magic bullet, and has it's own pros and cons. It is a tool like a process or a thread. While there is overlap in what each can accomplish, there are cases where each can be useful. As this post is about threads, I'm not going to dig into event driven concurrency.
