# An Algorithm for a Concurrent Queue

_Captured: 2017-11-10 at 00:58 from [dzone.com](https://dzone.com/articles/an-algorithm-for-a-concurrent-queue?edition=334849&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-07)_

In the following post, I want to show you an algorithm for a concurrent queue that supports one reading and multiple writing threads. The writing threads only need a read from a thread local field and a write to a volatile field to publish an event to the queue. Writing does not need to "compare and swap" operations like the standard JDK concurrent queues, leading to an easier and potentially faster algorithm. A usage example is a background thread writing log events asynchronously to a file.

## Writing

The main idea is to use not one single queue, but many. We use one queue per writing thread stored in a thread local field. Then the queue is a simple linked list using a volatile field for the next element and final for the value:

Writing an element to the queue is implemented in the accept method, line 6. When it is the first element written, lastWritten and lastRead will be set to the new LinkedListElement, lines 10-13. Otherwise, the list is extended by the new LinkedListElement, and lastWritten is moved to the end of the list, lines 16 and 17.

And here is the class storing each queue, called Consumer, in a thread local field:
    
    
        private ThreadLocal<Consumer<T>> threadLocal = new  ThreadLocal<Consumer<T>>();

## Reading

When reading the elements, we must remember the last elements we read. We do this in the field lastRead in the LinkedList. The following shows the method used for reading elements from one queue:
    
    
            if(list.lastRead  != null  )
    
    
                if(  ! list.lastRead.isRead )
    
    
                    eventSink.execute( list.lastRead.element.event  );
    
    
                LinkedListElement<T> current = list.lastRead.element;
    
    
                while(  current.next != null )

And here is the class ListElementPointer used to store the last read element:

The field lastRead is initialized by the writing thread and, afterward, only modified by the reading thread.

I've skipped the logic for creating new LinkedLists and reading multiple LinkedLists in the reading thread. You can see the complete source code [here](https://github.com/vmlens/executor-service).

## Usage

The queue is open source and the source code is available on GitHub [here](https://github.com/vmlens/executor-service). We use this queue in [VMLens](http://vmlens.com), a tool that detects race conditions and deadlocks in Java applications. VMLens traces the application and writes the trace events asynchronously using this queue to a file for later analysis.
