# Parallelizing Tasks with Dependencies — Design Your Code to Optimize Performance

_Captured: 2018-02-02 at 16:47 from [dzone.com](https://dzone.com/articles/parallelizing-tasks-with-dependencies-design-your?edition=359112&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-02-02)_

Let's imagine you need to write a tool that can execute a series of asynchronous tasks; each with a different set of dependencies that influence the order of the operations. You can address this with sequential and imperative execution, but if you want to maximize the performance, sequential operations won't do. Instead, you must build the tasks to run in parallel. Many concurrent problems can be considered to be a static collection of atomic operations with dependencies between their inputs and outputs. On completion of the operation, the output is used as input to other dependent operations. To optimize performance, these tasks need to be scheduled based on the dependency, and the algorithm must be optimized to run the dependent tasks in serial as necessary and in parallel as much as possible.

You want a reusable component that runs a series of tasks in parallel ensuring that all the dependencies that could influence the order of the operations are respected. How do we create a programming model that exposes the underlying parallelism of a collection of operations which are executed efficiently, either in parallel or serially depending on the dependencies with other operations?

### Solution: Implementing a Dependencies Graph of Tasks Using the F# Mailboxprocessor and Exposing the Methods as Standard Task to Be Consumed Also by C#

The solution is called Directed Acyclic Graph (DAG), which aims to form a graph by breaking down operations into a series of atomic tasks with defined dependencies. The acyclic nature of the graph's important as it removes the possibility of deadlocks between tasks, provided the tasks are truly atomic. When specifying the graph, it's important to understand all dependencies between tasks, particularly hidden dependencies that may result in deadlocks or race condition. Below is a typical example of a data structure in the shape of a Graph, which can be used to represent scheduling constraints between the operations of the graph.

A graph's an extremely powerful data structure in computer science that gives rise to powerful algorithms.

![Image title](https://dzone.com/storage/temp/7990190-screen-shot-2018-01-28-at-42321-pm.png)

_Figure 1 A graph is a collection of vertices connected by edges. In this representation of a Directed Graph, Node 1 has dependencies on Node 4 and 5, Node 2 depends on Node 5, Node 3 has dependencies on Node 5 and 6 and so on._

You can apply the DAG structure as a strategy to run tasks in parallel while respecting the order of the dependencies for increasing the performance. You can define this graph structure using the F# MailboxProcessor, which keeps an internal state for the tasks registered to be performed in the shape of edge dependencies.

### Validating a Directed Acyclic Graph

When working with any graph data structure, like DAG, we need to deal with the problem of registering the edges correctly. For example, in figure 1, what if Node 2 with dependencies to Node 5 is registered, but Node 5 doesn't exist? It could also happen that some edges depend on each other, which leads to a Directed Cycle. In the case of a Directed Cycle, it's critical to run some tasks in parallel; otherwise, certain tasks could wait on another forever in a deadlock.

The solution's called Topological Sort, which means that we can order all the vertices of the graph in such a way that all its directed edges target from a vertex earlier in the order to a vertex later in that order. For example, if Task A must complete before Task B, and Task B must complete before Task C which must complete before Task A; then there's a cycle reference and the system notifies you of the mistake by throwing an exception. If a precedence constraint has a direct cycle, then there's no solution. This kind of checking's called Directed cycle detection. If a Directed Graph satisfies these rules, it's considered a Directed Acyclic Graph (DAG), which is primed to run several tasks that have dependencies in parallel.

You can find the complete version of the listing 2, which includes the DAG validation, in the source code online.

The following code listing exploits F# MailboxProccessor as the perfect candidate to implement a DAG to run in parallel operations with dependencies. First, let's define the discriminated union used to manage the tasks and run their dependencies.

Listing 1 Message type and data structure to coordinate the Tasks execution according to their dependencies
    
    
          Edges : int array; Id : int; Task : Func<Task>

**#A Commands send to the ParallelTasksDAG underlying dagAgent agent, which is responsible for the tasks execution coordination.**

**#B Wraps the details of each task to run. **

The TaskMessage type represents the message cases sent to the underlying agent of the ParallelTasksDAG. These messages are used for task coordination and dependency synchronization. The TaskInfo type contains and tracks the details of the registered tasks during the execution of the DAG, including the dependency edges. The execution context (https://msdn.microsoft.com/en-us/library/system.threading.executioncontext(.110).aspx) is captured to be able to access information during the delayed execution, such as the current user, any state associated with the logical thread of execution, code-access security information, and the like. The start and end of the execution time are published when the event fires.

**Listing 2 DAG F# Agent to parallelize the execution of operations with dependencies **
    
    
        let onTaskCompleted = new Event<TaskInfo>()  // #A
    
    
      let dagAgent = new MailboxProcessor<TaskMessage>(fun inbox ->
    
    
        let rec loop (tasks : Dictionary<int, TaskInfo>)   // #B
    
    
                     (edges : Dictionary<int, int list>) = async {  // #B
    
    
        let! msg = inbox.Receive()  // #C
    
    
            let fromTo = new Dictionary<int, int list>()
    
    
            let ops = new Dictionary<int, TaskInfo>()   // #E
    
    
            for KeyValue(key, value) in tasks do  // #F
    
    
                  let exists, lstDependencies = fromTo.TryGetValue(from)
    
    
                    fromTo.Add(from, [ operation.Id ])
    
    
                  else fromTo.[from] <- (operation.Id :: lstDependencies)
    
    
            ops |> Seq.iter (fun kv ->       // #F
    
    
                | Some(n) when n = 0 -> inbox.Post(QueueTask(kv.Value))
    
    
                | null -> op.Task.Invoke() |> Async.AwaitATsk
    
    
                | ctx -> ExecutionContext.Run(ctx.CreateCopy(),  // #I
    
    
                         (fun op -> let opCtx = (op :?> TaskInfo)
    
    
                                    opCtx.Task.Invoke().ConfigureAwait(false)), [CA] taskInfo)
    
    
                let exists, deps = edges.TryGetValue(op.Id)
    
    
                if exists && deps.Length > 0 then
    
    
                   depOps |> Seq.iter (fun nestedOp ->
    
    
        | AddTask(id, op) -> tasks.Add(id, op)   // #M
    
    
        loop (new Dictionary<int, TaskInfo>(HashIdentity.Structural))
    
    
             (new Dictionary<int, int list>(HashIdentity.Structural)))
    
    
      member this.AddTask(id, task, [<ParamArray>] edges : int array) =
    
    
                     Edges = edges; Id = id; Task = task
    
    
                     NumRemainingEdges = None; Start = None; End = None }

  * #A Instance of the onTaskCompletedEvent, used to notify when a task completes

  * #B Agent internal state to track the tasks registers and their dependencies. The collections are mutable because the state changes during the execution of the ParallelTasksDAG, and because they inherited thread-safety from being inside an Agent

  * #C Waiting asynchronously for a message

  * #D Message case that starts the execution of the ParallelTasksDAG

  * #E Collection that maps a monotonically increased index with a task to run 

  * #F The process iterates through the task list analyzing the dependencies among the other tasks to create a topological structure representing the order of the task execution. 

  * #G Message case to queue up a task, run it, and ultimately, remove it from the agent state as active dependency when it completes.

  * #H If the ExecutionContext captured's null, then run the task function in the current context, otherwise #I.

  * #I Run the task using the ExecutionContext captured.

  * #L Triggering and publishing the onTaskCompleted event to notify that a task is completed. The event contains the task information.

  * #M Message case use to add a task to be executed according with its dependencies, if any.

  * #N Starts the execution of the tasks registered.

  * #O Adding a task, its dependencies and the current ExecutionContext for the DAG execution.

The purpose of the function AddTask is to register a task including arbitrary dependency edges. This function accepts a unique ID, a function task that must be executed and a set of edges that represent the IDs of other registered tasks, all of which must be completed before the current task can be executed. If the array is empty, it means there are no dependencies. The MailboxProcessor named dagAgent is keeping the registered tasks in a current state "tasks," which is a map (tasks : Dictionary<int, TaskInfo>) between the ID of each task and its details. Moreover, the Agent also keeps the state of the edge dependencies for each task ID (edges : Dictionary<int, int list>). When the Agent receives the notification to start the execution, part of the process involves verifying that all the edge dependencies are registered and that there are no cycles within the graph. This verification step is available in the full implementation of the ParallelTasksDAG in the code downloadable. The following code is an example in C# that references and consumes the F# library to run the ParallelTasksDAG. The tasks registered mirror the dependencies from the previous figure 1.
    
    
    Func<int, int, Func<Task>> action = (id, delay) => async () => {
    
    
    dagAsync.OnTaskCompleted.Subscribe(op => Console.WriteLine($"Operation {op.Id} completed in Thread Id      { Thread.CurrentThread.ManagedThreadId}"));

The helper function action purpose is to print when a Task start indicating the current thread Id as a reference to prove the multithreaded functionality. On the other hand, the event OnTaskCompleted is registered to notify when each task completes printing in the console the task ID and the current thread Id. Here's the output when the method ExecuteTasks is called.

As you can see, the tasks run in parallel with a different thread of execution (different thread ID), and the dependency order is preserved.

And that's how to parallelize tasks with dependencies, in a nutshell. If you want to see more, read the first chapter of [Concurrency in .NET](https://www.manning.com/books/concurrency-in-dotnet) and see this [Slideshare presentation](https://www.slideshare.net/ManningBooks/concurrency-in-net-functional-concurrency-and-scalability-in-net) for more details.
