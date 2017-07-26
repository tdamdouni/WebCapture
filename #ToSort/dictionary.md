# dictionary

_Captured: 2015-11-18 at 11:53 from [xlinux.nist.gov](https://xlinux.nist.gov/dads/HTML/dictionary.html)_

(data structure)

**Definition:** An _[abstract data type_](https://xlinux.nist.gov/dads/HTML/abstractDataType.html) storing items, or values. A value is accessed by an associated _[key_](https://xlinux.nist.gov/dads/HTML/key.html). Basic operations are new, insert, find and delete.

**Formal Definition:** The operations new(), insert(k, v, D), and find(k, D) may be defined with _[axiomatic semantics_](https://xlinux.nist.gov/dads/HTML/axiomaticSemantics.html) as follows.

  1. new() returns a dictionary 
  2. find(k, insert(k, v, D)) = v 
  3. find(k, insert(j, v, D)) = find(k, D) if k ≠ j 

where k and j are keys, v is a value, and D is a dictionary. 

The modifier function delete(k, D) may be defined as follows.

  1. delete(k, new()) = new() 
  2. delete(k, insert(k, v, D)) = delete(k, D) 
  3. delete(k, insert(j, v, D)) = insert(j, v, delete(k, D)) if k ≠ j 

If we want find to be a _[total function_](https://xlinux.nist.gov/dads/HTML/totalfunc.html), we could define find(k, new()) using a special value: _fail_. This only changes the return type of find.

  1. find(k, new()) = _fail_

**Also known as** association list, map, property list.

**Generalization** (I am a kind of ...)  
_[binary relation_](https://xlinux.nist.gov/dads/HTML/binaryRelation.html), _[abstract data type_](https://xlinux.nist.gov/dads/HTML/abstractDataType.html).

**Specialization** (... is a kind of me.)  
_[associative array_](https://xlinux.nist.gov/dads/HTML/assocarray.html).

**See also** _[total order_](https://xlinux.nist.gov/dads/HTML/totalorder.html), _[set_](https://xlinux.nist.gov/dads/HTML/set.html) Some implementations: _[linked list_](https://xlinux.nist.gov/dads/HTML/linkedList.html), _[hash table_](https://xlinux.nist.gov/dads/HTML/hashtab.html), _[B-tree_](https://xlinux.nist.gov/dads/HTML/btree.html), _[jump list_](https://xlinux.nist.gov/dads/HTML/jumpList.html), _[directed acyclic word graph_](https://xlinux.nist.gov/dads/HTML/directedAcyclicWordGraph.html).

_Note: The terms "association list" and "property list" are used with LISP-like languages and in the area of Artificial Intelligence. These suggest a relatively small number of items, whereas a dictionary may be quite large. Professionals in the Data Management area have specialized semantics for "dictionary" and related terms. _

_

A dictionary defines a _[binary relation_](https://xlinux.nist.gov/dads/HTML/binaryRelation.html) that maps keys to values. The keys of a dictionary are a _[set_](https://xlinux.nist.gov/dads/HTML/set.html).

_

Author: [PEB](https://xlinux.nist.gov/dads/Other/contrib.html)

## Implementation

[(C++, Pascal, and Fortran)](http://www3.cs.stonybrook.edu/~algorith/files/dictionaries.shtml). Maksim Goleta's [Collections (C#)](http://goletas.com/csharp-collections) implementing stacks, queues, linked lists, binary search trees, AVL trees, and dictionaries. Go to the [Dictionary of Algorithms and Data Structures](http://www.nist.gov/dads/) home page. 

If you have suggestions, corrections, or comments, please get in touch with [Paul Black](mailto:paul.black@nist.gov).

Entry modified 2 September 2014.  
HTML page formatted Mon Feb 2 13:10:39 2015.

Cite this as:  
Paul E. Black, "dictionary", in _[Dictionary of Algorithms and Data Structures_](http://www.nist.gov/dads/) [online], Vreda Pieterse and Paul E. Black, eds. 2 September 2014. (accessed TODAY) Available from: <http://www.nist.gov/dads/HTML/dictionary.html>
