## Python Object-Oriented Design Patterns

Presenting Python classes and various related mechanisms without any description of their common uses would be like defining the `for` and `while` statements without any description of the typical uses of these constructions, and how they adapt to various programming needs. It is the purpose of this section to present common uses of classes and objects, the so-called _design patterns_, that have been used for a long time by programmers since object-oriented programming was born. 

Computer science is full of design patterns, and there is no exception for object-oriented programming. A catalog of object-oriented has been published by [Gamma95], and [Christopher2002] has a chapter dedicated to a few of them, with examples implemented in Python. Design patterns are not programs: they are widely used _design_ choices to build programs. As such, they form a kind of conceptual catalog that you are encouraged to _reuse_ to build your application. Not only are they useful in order not to reinvent the wheel and to save your time, but also because they provide a _comprehension framework_ for programmers who intend to reuse your code and who need to understand it. This part does not aim at an exhaustive presentation of object-oriented design patterns, which are very well described elsewhere. Its main purpose is to give a taste of it, with examples in bioinformatics, and to introduce the main related ideas. 

There are three categories of object-oriented patterns: 

  * _Creational_ patterns: patterns that can be used to _create_ objects. 
  * _Structural_ patterns: patterns that can be used to _combine_ objects and classes in order to build structured objects. 
  * _Behavioral_ patterns: patterns that can be used to build a computation and to control data flows. 

**Creational patterns. ** There are two main categories of creational patterns: those for creating objects without having to know the class name, that you could call "abstract object makers" (_abstract factory_ and _factory method_), and those to ensure a certain property regarding object creation, such as prohibiting more than one instance for a class (_singleton_), building a set of instances from different classes in a consistent way (_builder_), or creating an instance with a specific state (_prototype_). 

  * _Factory method:_ a factory method (or a factory function) is a function that creates an object. You don't necessarily know the exact name of the class of this object, but you know its interface. 
    * A function reading a Fasta formatted file may return an instance of the `DNA` class, of the `Protein` class, or any class providing it has a similar interface: 
        
                >>> fh = open(myfile)
        >>> my_seq = fasta_read(fh)
        >>> print my_seq
        s1
        atgaaa
        		      
    * For instance, you can create a sequence object (`Bio.Seq.Seq` in Biopython) by asking the `get_seq_by_num` method of an alignment object (`Bio.Align.Generic.Alignment`): 
        
                first_seq = align.get_seq_by_num(0)
        		      

The method which creates this instance of `Bio.Seq.Seq` is a factory method. The difference with a factory class is also that the factory method is often more than an object maker: it sometimes incorporates much more knowledge about the way to create the object than a factory would. 

    * A simple factory method would be a `new` method defined in a class to create new instances of the same class: 
        
                other_seq = seq.new()
        		      

  * _Abstract factory:_ an abstract factory is an object maker, where, instead of specifying a class name, you specify the kind of object you want. It is very similar to an abstract method: just, instead of being a method, it is a class. For example, the `FastaLoader` is a factory of sequences. Given a filehandle, it returns a list of sequence objects of the proper class: 

    
        seq_factory = FastaLoader()
    fh = open(my_fasta_file)
    my_seqs = seq_factory.load(fh)
    fh.close()
    		    

![](images/exercise.png)

**Exercise 19.5. Point factory**

Let's define a class that can create points for us. We could ask to such a _factory_ to create new points by just providing the coordinates. This class could help us maintain a set of unique points by checking that a point of the sme coordinates does not already exist. 

    
        factory = PointFactory()
    p1 = factory.create(3,4)
    p2 = factory.create(4,5)
    p3 = factory.create(4,5)
    p = factory.search(3,4)
    p.show()
    factory.delete(4,5)
    		    

[Solution 19.1](ch19s07.html#sol_point_factory)

For instance, say that you want to create an agent to run analysis programs, you can ask a factory to do it for you: 

    
        clustalw = AnalysisFactory.program('clustalw')
    result = clustalw.run(seqfile = 'myseqs')
    print result.alig
    		

The `clustalw` object is an instance of, say, the `AnalysisAgent.Clustalw` class, but you do not have to know about it at creation time. The only thing you know is the name of the program you want ('clustalw'), and the factory will do the rest for you. 

  * _Singleton:_ ensures that you cannot create more than one instance. A class attribute could be used to check the number of instanciations: 

    
        class Singleton:
    
        _nb = 0
        
        def __init__(self):
            if Singleton._nb > 0:
                raise Exception, "not more than one instance of " + str(self.__class__)
            Singleton._nb = 1
    
    print "creating a 1st instance"
    s1 = Singleton()
    
    print "creating a 2nd instance"
    s2 = Singleton()
    
    Exception: not more than one instance of __main__.Singleton
    
    		

For example, if you can define a class to contain operations and data for genetic code: you need only one instance of this class to perform the task. Actually, this pattern would not be implemented with a class in Python, but rather with a module, at least if you can define it statically (a dynamic singleton could not be a module, for a module has to be a file): 

    
        >>> import genetic_code
    >>> genetic_code.aa('TTT')
    F
    		

  * _Prototype:_ this pattern also lets you create a new object without knowing its class, but here, the new target object is created with the same state as the source object: 

    
        another_seq = seq.copy()
    		

The interest is that you do not get an "empty" object here, but an object identical to `seq`. You can thus play with `another_seq`, change its attributes, etc... without breaking the original object. 

  * _Builder:_ you sometimes need to create a complex object composed of several parts. This is the role of the builder. 
    * For instance, a builder is needed to build the whole set of nodes and leafs of a tree. 
    * The Blast parser in Biopython simultaneously instantiates several classes that are all component parts of of hit: `Description`, `Alignment` and `Header`. 

**Structural patterns. ** Structural patterns address issues regarding how to combine and structure objects. For this reason, several structural patterns provide alternative solutions to design problems that would else involve inheritance relationships between classes. 

  * _Decorator, proxy, adapter:_ these patterns all enable to combine two (or more) components, as shown in [Figure 19.7](ch19s06.html#fig_delegate_dp). There is one component, A, "in front" of another one, B. A is the visible object a client will see. The role of A is either to extend or restrict B, or help in using B. So, this pattern is similar to subclassing, except that, where a sub-class _inherits_ a method from a base class, the decorator _delegates_ to its decoratee when it does not have the required method. The advantage is flexibility (see [Section 19.4.2](ch19s04.html#sect_class_inherit_comment)): you can combine several of these components in any order at run time without having to create a big and complex hierarchy of subclasses. 

**Figure 19.7. Delegation**

![](images/delegate_dp.png)

Generally, the Python code of the `A` class looks like: 

    
        class A:
            def __init__(self, b):
                """storing of the decoratee b (b is an instance of class B)"""
                self.b = b
    
            def __getattr__(self, name):
                """
                   methods/attributes A does not know about are delegated
                   to b 
                """
                return getattr(self.b, name)
    
    class B:
    
        def f(self):
           return "result of f"
    
    	      

At use time, an instance of class `A` is created by providing a `b` instance. 

    
        >>> b = B()
    >>> a = A(b)
    >>> print a.f()
    'result of f'
    	      

Everything that class `A` cannot perform is forwarded to `b` (providing that class `B` knows about it). 

    * The _decorator_ enables to add functionalities to another object. [Example 19.6](ch19s06.html#exa_dp_deco) shows a very simple decorator that prints a sequence in uppercase. 

**Example 19.6. An uppercase sequence class**

        
                			  
        import string
        
        class UpSeq:
        
            def __init__(self, seqobj):
                self.seqobj = seqobj
        
            def __str__(self):
                return string.upper(self.seqobj.seq)
        
            def __getattr__(self,attr):
                return getattr(self.seqobj, attr)
        
        			

The way to use it is for instance: 

        
                >>> s=UpSeq(DNA(name='name1', seq='atcgctgtc'))
        >>> print s
        ATCGCTGTC
        >>> s[0:3]
        'atc'
        >>> len(s)
        9
        			

![](images/exercise.png)

**Exercise 19.6. An analyzed sequence class**

How would you design sequence classes where all sequence analyses of type `f` would be available as: 

        
                seq.f()
        		      

without actually defining all the possible `f` methods within the sequence class? 

    * The _proxy_ rather handles the access to an object. There are several kinds of proxy: 
      * _protection proxy_: to protect the access to an object. 

**Example 19.7. `ImmutableList` class**

The following example illustrates how to use this pattern. As you know, lists are mutable objects in Python: you can change them. In order to get an immutable list, you can use the `UserList` module provided by python that has a `UserList` class, an redefine the methods that enable to change the list. 

            
                        import UserList
            
            class ImmutableList(UserList.UserList):
            
                def __setitem__(self, i, value):
                    raise ValueError, "operation not supported"
            
                def __delitem__(self, i):
                    raise ValueError, "operation not supported"
            
                def append(self, item):
                    raise ValueError, "operation not supported"
            
                def extend(self, other):
                    raise ValueError, "operation not supported"
            
                def insert(self, other):
                    raise ValueError, "operation not supported"
            
                def pop(self, i):
                    raise ValueError, "operation not supported"
            
                def remove(self, i):
                    raise ValueError, "operation not supported"
            
                def reverse(self):
                    raise ValueError, "operation not supported"
            
                def sort(self):
                    raise ValueError, "operation not supported"
            
            
            l = ImmutableList([3, 4, 5])
            try:
              l.append(10)
            except ValueError, e:
              print e
            
            			      

You could now consider that a list your program is managing can be temporarily made mutable. In contrast with the example above which is using inheritance, you can use the following class definition: 

            
                        class ImmutableList:
            
                def __init__(self, l):
                    self.l = l
            
                def __getattr__(self, attr):
                    return getattr(self.l, attr)
            
                def __setitem__(self, i, value):
                    raise ValueError, "operation not supported"
            
                def __delitem__(self, i):
                    raise ValueError, "operation not supported"
            
                def append(self, item):
                    raise ValueError, "operation not supported"
            
                def extend(self, other):
                    raise ValueError, "operation not supported"
            
                def insert(self, other):
                    raise ValueError, "operation not supported"
            
                def pop(self, i):
                    raise ValueError, "operation not supported"
            
                def remove(self, i):
                    raise ValueError, "operation not supported"
            
                def reverse(self):
                    raise ValueError, "operation not supported"
            
                def sort(self):
                    raise ValueError, "operation not supported"
            
            l1 = [3, 4, 5]
            l2 = ImmutableList(l1)
            
            # provide l2 to another component, preventing temporarily the list to be changed
            # by this component
            other_function(l2)
            
            l1.append(8)
            
            			      

![](images/exercise.png)

**Exercise 19.7. A partially editable sequence**

How would you design a sequence class where the only allowed editions would be: 

            
                        del seq[i]
            			      

on a gap character, and: 

            
                        seq[i] = 'A'
            			      

on a 'N' character? 

      * _virtual proxy_: to physically fetch data only when needed. Database dictionaries in Biopython work this way: 
            
                        prosite = Bio.Prosite.ExPASyDictionary()
            entry = prosite['PS00079']
            		      

Data are fetched only when an access to an entry is actually requested. 

      * _remote proxy_: to simulate a local access for a remotely activated procedure. 
    * The _adapter_ (or _wrapper_) helps in connecting two components that have been developped independantly and that have a different interface. 

For instance, the `Pise` package transforms Unix programs interfaces in standardized interfaces, either Web interfaces, or API. For instance, the **golden** Unix command has the following interface: 

        
                bash> golden embl:MMVASP 
        		      

But the `Pise` wrapper enables to run it and get the result by a Python program, having an interface defined in the Python language: 

        
                factory = PiseFactory()
        golden = factory.program("golden",db="embl",query="MMVASP")
        job = golden.run()
        print job->content()
        		      

  * _Collection_: this is a general pattern on how to collect items. You may need your own collection classes in numerous cases where you have several items to manage as a set, either ordered (list-like) or not ordered but accessible through keys (dictionary-like). Generally, you will need accessors to access the items, in various way: 
    * either by an indice or slice: 
        
                my_collection[i]

or by a key: 

        
                my_collection[key]
    * by a search on values: 
        
                my_collection.search(value)
    * by iterating on all the items: 
        
                for item in my_collection:
        		      ...

or all the keys: 

        
                for item in my_collection.keys():
        		      ...
    * printing: 
        
                        def __str__(self):
                    output = ""
                    for x in my_collection:
                         output = output + str(x)
                    return output
        		      

(as you can notice, the collection's `__str__` method in turn invokes the items' `__str__` method, since the python `str()` function does invoke this special method when defined) 

    * filtering: 
        
                [x for x in my_collection if f(x)]

(see [Section 11.7](ch11s07.html)) 

    * saving items into a file: 
        
                my_collection.save(fh)

You will also have a set of modificators, defined with your own specific rules: 

    * adding/removing elements: 
        
                my_collection.append(value)

(here, for instance, you can check that the collection has unique values, or that the item is added at the right place to keep the collection sorted, etc...) 

        
                my_collection.remove(value)

or 

        
                del my_collection[key]
    * modification, but also creation, can be enabled by assignation if the collection has a dictionary behaviour: 
        
                my_collection[i] = value

or assignation of an element and its key: 

        
                my_collection[key] = value
    * loading items from a file: 
        
                my_collection.load(fh)
    * re-ordering: 
        
                my_collection.sort()

or: 

        
                my_collection.reverse()

**Example 19.8. `SequenceDB` class**

The following `SequenceDB` class is an example of a collection for managing sequences. You can load your sequences from a Fasta file and save it after modifications. You can access to an entry by name or search the database by sub-sequence. The database is either a DNA database (`DnaDB` class) or a protein database (`ProteinDB` class). This is an example of how to use such a collection: 

    
        # loading
    fh = open(fastafile)
    seqdb = DnaDB(fh)
    fh.close()
    # searching
    l = seqdb.search('cctac')
    for seq in l:
        print l
    # modifying:
    seqdb['new_seq'] = 'ccaggaggccctggcctctcactgaacccggccactcctctttggc'
    print seqdb['new_seq']
    # output the whole db:
    print seqdb
    # saving:
    fh = open(fastafile, 'w')
    seqdb.save(fh)
    fh.close()
    		

The code of the classes would be: 

    
        class SequenceDB:
    
        def __init__(self, fh=None):
            self._db = {}
            if fh is not None:
                self.load(fh)
    
        def load(self, fh):
            seq = ""
            line = fh.readline()
            while line:
                if line[0] == '>':
                    if seq != '':
                        self[name] = seq
                    name = line[1:-1]
                else:
                    seq += line
                line = fh.readline()
    
            if seq != '':
                self[name] = seq
     
        def save(self, fh):
            for k in self._db.keys():
                seq = self._db[k]
                fh.write(str(seq))
    
        def __str__(self):
            result = ""
            for seq in self._db.values():
                result += str(seq) + "\n"
            return result[:-1]
    
        def search (self, keywd) :
            return [seq for seq in self._db.values() if keywd in seq.name or keywd in seq.seq]
    
        def __getattr__(self, attr):
            return getattr(self._db, attr)
    
    
    class DnaDB(SequenceDB):
    
        def __setitem__(self, name, seq):
            if self._db.has_key(name):
                raise KeyError, name + ": this sequence already exists"
            self._db[name] = DNA(name=name, seq=seq)
    
    class ProteinDB(SequenceDB):
    
        def __setitem__(self, name, seq):
            if self._db.has_key(name):
                raise KeyError, name + ": this sequence already exists"
            self._db[name] = Protein(name=name, seq=seq)
    		

As you can notice, this example is not only a collection, it illustrates in fact several patterns. The _decorator_ since `SequenceDB` is composed with a Python dictionary and delegates most native dictionary methods through the `__getattr__` special method. Thanks to this delegation, you can do anything a dictionary could do with your database, although it does not use inheritance. Its also an _abstract factory_ for the class creates of set of objects which class does not have to be specified. It also uses the _protection proxy_, since the `__setitem__` method does not allow to override an existing entry. 

  * _Composite_: this pattern is often used to handle complex composite recursive structures. [Example 19.9](ch19s06.html#exa_tree_composite) shows a set of classes for a tree structure, illustrated in [Figure 19.8](ch19s06.html#fig_tree_composite). The main idea of the composite design pattern is to provide an _uniform interface_ to instances from different classes in the same hierarchy, where instances are all components of the same composite complex object. In [Example 19.9](ch19s06.html#exa_tree_composite), you have two types of nodes: `Node` and `Leaf`, but you want a similar interface for them, that is at least defined by a common base class, `AbstractNode`, with two operations: `print` `subtree`. These operations should be callable on any node instance, without knowing its actual sub-class. 

    
        >>> t1 = Leaf( 'A', 0.71399)
    >>> t2 = Node (Leaf('B', -0.00804), 
                   Leaf('C', 0.07470))
    >>> t3 = Node ( Leaf ( 'A', 0.71399),
                    Node ( Node ( Leaf('B', -0.00804), 
                                  Leaf('C', 0.07470), 
                                  0.15685),
                           Leaf ('D', -0.04732),
                           0.0666),
                  ) 
    
    >>> print t3
    (A: 0.71399, ((B: -0.00804, C: 0.0747): 0.15685, D: -0.04732): 0.0666)
    >>> t4 = t3.right.subtree()
    >>> print t4
    ((B: -0.00804, C: 0.0747): 0.15685, D: -0.04732)
    >>> t5 = t3.left.subtree()
    >>> print t5
    'A': 0.71399
    		

**Figure 19.8. A composite tree**

![](images/tree_composite.png)

**Example 19.9. A composite tree**

    
        		                                                                        ![\(1\)](images/callouts/1.png)
    class AbstractNode:
    
        def __str__(self):
            pass
    
        def subtree(self):
            pass
                                                                              ![\(2\)](images/callouts/2.png)
    class Node(AbstractNode):
        def __init__(self, left=None, right=None, length=None):
            self.left=left
            self.right=right
            self.length=length
    
        def __str__(self):
    	if self.length:
    	    return "(" + self.left.__str__() + ", " + self.right.__str__() + ")" + ": " + str(self.length) 
    	else:
    	    return "(" + self.left.__str__() + ", " + self.right.__str__() + ")"
        
        def subtree(self):                                                    ![\(3\)](images/callouts/3.png)
            return Node(self.left, self.right)
    
    class Leaf(AbstractNode):
        def __init__(self, name, length=None):
            self.name = name
            self.length=length
            self.left = None
            self.right = None
    
        def __str__(self):
            return self.name + ": " + str(self.length)
    
        def subtree(self):
            return Leaf(self.name, self.length)
    
    
    if __name__ == "__main__":
        t1 = Leaf( 'A', 0.71399)
        print t1
        t2 = Node (Leaf('B', -0.00804), 
    	       Leaf('C', 0.07470))
        print t2
        t3 = Node ( Leaf ( 'A', 0.71399),
    		Node ( Node ( Leaf('B', -0.00804), 
    			      Leaf('C', 0.07470), 
    			      0.15685),
    		       Leaf ('D', -0.04732),
    		       0.0666),
    		)
    
        print t3
    
    
    
    
    
    		    

![1](images/callouts/1.png)

Abstract class `AbstractNode`, base class for both `Node` and `Leaf`

![2](images/callouts/2.png)

Internal nodes are instances of `Node` class. 

![3](images/callouts/3.png)

Leafs are instances of `Leaf` class. 

**Behavioral patterns. ** Patterns of this category are very useful in sequence analysis, where you often have to combine algorithms and to analyze complex data structure in a flexible way. 

  * _Template_: this pattern consists in separating the invariant part of an algorithm from the variant part. In a sorting procedure, you can generally separate the function which compares items from the main body of the algorithm. The template method, in this case, is the `sort()` method, whereas the `compare()` can be defined by each subclass depending on its implementation or data types. 

The following function defines a typical search, which objective is to verify a property on the whole sequence. So it stops whenever a property is not verified on a single element of the sequence. The structure of this search is a kind of template. 

    
        def check_whole_seq(seq, check_fn):
        for c in seq:
            if not check_fn(c):
                return False
        return True
    		

This type of search is so common that you could imagine to provide an boolean function to this function for the control to perform, in order to have a generic function. 

A related template would be to search in the sequence whether a propoerty is verified at least once: 

    
        def check_has_seq(seq, check_fn):
        for c in seq:
            if check_fn(c):
                return True
        return False
    		

  * _Strategy_: the boolean function in the examples above can be called a strategy, because it provides the logic which decides for the result of the search. Examples of such function are listed below: 

    
        def is_dna(c):
        return c in 'atcgATCG'
    
    def is_gap(c):
        return c in '-.'
    
    def is_amino_acid(c):
        AA = upper(c) 
        if AA < 'A' or AA > 'Z':
            return False
        if AA in 'JOU':
            return False
        return True
    
    def is_upper(c):
        return c == upper(c)
    
    def is_letter(c):
        return c in ascii_letters
    		  

You can use of of these in combination with the template above: 

    
        check_whole_seq('tgtcgt', is_dna)
    check_whole_seq('MAI', is_amino_acid)
    check_has_seq('tg-tcgt', is_gap)
    		  

In the following example, the `f_test` method is a strategy: 

    
        class MotifDB:
    
        def __init__(self, fh=None, db=None):
            self._db = []
            if fh is not None:
                self._load_fh(fh)
            elif db is not None:
                self._load_db(db)
    
        def filter(self, f_test) :
            return self.__class__(db=[motif for motif in self._db if f_test(motif)])
    

Applied to all elements of a set, this function is provided as a parameter to filter the elements. It can be used the following way: 

    
            new_db = db.filter(lambda(motif): 'kinase' in motif.get_desc())
    

where only elements of this motifs databse containing 'kinase' in their description will be returned. 

  * _Iterator_: an iterator is an object that let you browse a sequence of items from the beginning to the end. Generally, it provides: 
    * a method to start iteration 
    * a method to get the next item 
    * a method to test for the end of the iteration 

Usually, one distinguishes _internal_ versus _external_ iterators. An external iterator is an iterator which enables to do a `for` or a `while` loop on a range of values that are returned by the iterator: 

    
        for e in l.elements():
         f(e)
    		  

or: 

    
        i = l.iterator()
    e = i.next()
    while e:
       f(e)
       e = i.next()
    		  

In the above examples, you control the loop. On the other hand, an internal iterator just lets you define a function or a method (say, `f`, called a _visitor_, see below) to apply to all elements: 

    
        l.iterate(f)
    		  

In the Biopython package, files and databases are generally available through an iterator. 

    
        handle = open(...)                                                        ![\(1\)](images/callouts/1.png)
    iter = Bio.Fasta.Iterator(handle)                                         ![\(2\)](images/callouts/2.png)
    seq = iter.next()                                                         ![\(3\)](images/callouts/3.png)
    while seq:
      print seq.name
      print seq.seq                                                           ![\(4\)](images/callouts/4.png)
      seq = iter.next()
    handle.close()
    		  

![1](images/callouts/1.png)

Starting the iterator.

![2](images/callouts/2.png)

Getting the next element.

![3](images/callouts/3.png)

Testing for the end of the iteration.

![4](images/callouts/4.png)

Getting the next element.

  * _Visitor_: this pattern is useful to specify a function that will be applied on each item of a collection. The Python `map` function provides a way to use visitors, such as the `f` function, which visits each item of the `l` list in turn: 

    
        >>> def f(x):
    	return x + 1
    >>> l=[0,1,2]
    >>> map(f,l)
    [1, 2, 3]
    	      

The `map` is an example of an internal iterator (with the `f` function as a visitor). The `f_test` function in the `MotifDB` class above is also a visitor. A visitor is also a strategy that applies to all the elements of a set. 

**Example 19.10. A recursive visitor**

A visitor can be quite useful during the traversal of a recursive data structure. [Section 15.3](ch15s03.html) provide examples of typical recursive traversals (_templates_) of a tree. The functions that traverse a tree could very well be rewritten with a _visitor_. In the following code, `walk_leaves` takes an additional parameter, which is a function that will be executed on each leaf of the tree. this function, for example, can just print the leaf. 

    
        def walk_leaves(tree, visitor):
        if type(tree) is types.ListType:
            for child in tree:
                walk_leaves(child, visitor)
        else:
            visitor(tree)
    
    def output(e):
        print e
    
            
    tree = [[[['human', 'chimpanzee'], 'gorilla'], 'orang-utan'], 'gibbon']
    walk_leaves(tree, output)
    		

Similarly, the following binary traversal takes a function as a parameter (`make`>), which purpose is to build the result of the traversal. 

    
        def binary_traverse(tree, make):
        if type(tree) is types.ListType:
            left = binary_traverse(tree[0], make)
            right = binary_traverse(tree[1], make)
            print left, right
            return make(left, right)
        else:
            return make(tree)
    
    def build_list(*l):
        if len(l) == 1:
            return [l[0]]
        _l = []
        for e in l:
            _l = _l + e
        return _l
    
    t1 = binary_traverse(tree, build_list)
    ['human'] ['chimpanzee']
    ['human', 'chimpanzee'] ['gorilla']
    ['human', 'chimpanzee', 'gorilla'] ['orang-utan']
    ['human', 'chimpanzee', 'gorilla', 'orang-utan'] ['gibbon']
    
    def build_string(*l):
        if len(l) == 1:
            return str(l[0])
        _s = "("
        for e in l:
            _s = _s + str(e) + ","
        return _s[:-1] + ")"
    
    t2 = binary_traverse(tree, build_string)
    human chimpanzee
    (human,chimpanzee) gorilla
    ((human,chimpanzee),gorilla) orang-utan
    (((human,chimpanzee),gorilla),orang-utan) gibbon
    		

  * _Observer_ The _observer_ pattern provides a framework to maintain a consistent distributed state between loosely coupled components. One agent, the observer, is in charge of maintaining a list of _subscribers_, e.g components that have subscribed to be informed about changes in a given state. Whenever a change occurs in a state, the observer has to inform each subscriber about it. 

A well-known example is the Model-View-Controller [Krasner88] framework. The view components, the ones who actually display data, subscribe to "edit events" in order to be able to refresh and redisplay them whenever a change occurs. 

