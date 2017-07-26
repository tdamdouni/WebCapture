# abstract data type

_Captured: 2015-11-18 at 11:52 from [xlinux.nist.gov](https://xlinux.nist.gov/dads/HTML/abstractDataType.html)_

(definition)

**Definition:** A set of data values and associated operations that are precisely specified independent of any particular implementation.

**Also known as** ADT.

**Specialization** (... is a kind of me.)  
_[dictionary_](https://xlinux.nist.gov/dads/HTML/dictionary.html), _[stack_](https://xlinux.nist.gov/dads/HTML/stack.html), _[queue_](https://xlinux.nist.gov/dads/HTML/queue.html), _[priority queue_](https://xlinux.nist.gov/dads/HTML/priorityque.html), _[set_](https://xlinux.nist.gov/dads/HTML/set.html), _[bag_](https://xlinux.nist.gov/dads/HTML/bag.html).

**See also** _[data structure_](https://xlinux.nist.gov/dads/HTML/datastructur.html).

_Note: Since the data values and operations are defined with mathematical precision, rather than as an implementation in a computer language, we may reason about effects of the operations, relations to other abstract data types, whether a program implements the data type, etc. _

_

One of the simplest abstract data types is the _[stack_](https://xlinux.nist.gov/dads/HTML/stack.html). The operations new(), push(v, S), top(S), and popOff(S) may be defined with _[axiomatic semantics_](https://xlinux.nist.gov/dads/HTML/axiomaticSemantics.html) as following.

  1. new() returns a stack 
  2. popOff(push(v, S)) = S 
  3. top(push(v, S)) = v 
where S is a stack and v is a value. (The usual pop operation is a combination of top, to return the top value, and popOff, to remove the top value.) Contrast this with the _[axiomatic semantics_](https://xlinux.nist.gov/dads/HTML/axiomaticSemantics.html) definition of a _[set_](https://xlinux.nist.gov/dads/HTML/set.html), a _[dictionary_](https://xlinux.nist.gov/dads/HTML/dictionary.html), or a _[queue_](https://xlinux.nist.gov/dads/HTML/queue.html). 

From these axioms, one may define equality between stacks, define a pop function which returns the top value in a non-empty stack, etc. For instance, the _[predicate_](https://xlinux.nist.gov/dads/HTML/predicate.html) isEmpty(S) may be added and defined with the following additional axioms.

  1. isEmpty(new()) = true 
  2. isEmpty(push(v, S)) = false 
_

_ After Nell Dale <ndale@cs.utexas.edu> May 2001._

Author: [PEB](https://xlinux.nist.gov/dads/Other/contrib.html)

Go to the [Dictionary of Algorithms and Data Structures](http://www.nist.gov/dads/) home page. 

If you have suggestions, corrections, or comments, please get in touch with [Paul Black](mailto:paul.black@nist.gov).

HTML page formatted Mon Feb 2 13:10:39 2015.

Cite this as:  
Paul E. Black, "abstract data type", in _[Dictionary of Algorithms and Data Structures_](http://www.nist.gov/dads/) [online], Vreda Pieterse and Paul E. Black, eds. 10 February 2005. (accessed TODAY) Available from: <http://www.nist.gov/dads/HTML/abstractDataType.html>
