# Chain of Command Example

_Captured: 2017-03-28 at 20:42 from [dzone.com](https://dzone.com/articles/chain-of-command-example?edition=286932&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-28)_

One objective of the chain of command design pattern is to be able to write a bunch of functions that link together and form a chain of alternative implementations. The idea is to have alternatives that vary in their ability to compute a correct answer. If Algorithm 1 doesn't work, try Algorithm 2. If that doesn't work, fall back to Algorithm 3, etc.

Perhaps Algorithm 1 has a number of constraints, i.e., it's fast, but only for a limited kind of input. Algorithm 2 may have a different set of constraints. And Algorithm 3 involves the "British Museum" algorithm.

Algorithm zero, at the head of the chain, can be a dynamic cache, perhaps with LRU features. Maybe it can be shared among servers. There are lots of choices here. The idea is that a cache is often first because it's so fast.

We can, of course, write a giant master function with other functions. Maybe they're all linked with a lot of clever if-statements. We know how that turns out, don't we?

Instead, we can make each function a distinct object. The alternative algorithm functions have a relationship with other functions, so a simple non-stateful class definition is appropriate. The cache alternative may involve state changes, so it's a little different than the others.

We'll imagine a simple `doTheThing()` function with a few arguments that return a value. We have several alternatives. The goal to be able to wrap each `doTheThing()` function in a very small class like this:
    
    
    class AlgorithmOne(DoAThing):
        """One way to do it."""
        def doTheThing(self, arg1, arg2):
            # Check some constraints, maybe...
            if arg1 < arg2:
                return Fraction(arg1, arg2)
            else:
                raise DoAThingError("Outside AlgorithmOne Constraints")

Either this algorithm produces a good answer, or it raises an exception that it can't really do the thing. Any other exceptions are ordinary bad code crashing at run time.

The core feature of the abstract superclass is the all-important `try:/except:block` that tries `doTheThing()`. If the `DoAThingError` exception is raised, it moves down the chain of command. If it succeeds, then, we're done.

This has a consequence of wrapping the `doTheThing()` implementation with a function named `theThing()`. The wrapper function, t`heThing()`, contains the `try:/except:block`, a call to a concrete `doTheThing()` implementation, plus the fall-back processing.

The cache version doesn't really have a meaningful implementation of the `theThing()` function. Instead it always tries the fallback chain and caches the result.

A cool way to build the chain is omitted from this design. We're creating a linked list like this:
    
    
    a2 = AlgorithmTwo()
    a1 = AlgorithmOne(a2)
    coc = UseCache(a1)

Some people object to the "backwardness" of this, in which case, they can write a simple constructor function which emits the chain of command by linking the things together in the proper order.
    
    
    def builder(*classes):
        previous = None
        for class_ in classes:
            next = class_(previous)
            previous = next
        return previous

I'm not sure it's essential. But it's simple.

Here's the whole show.
    
    
    """Chain of command."""
    from fractions import Fraction
    import pickle
    
    class DoAThingError(Exception):
        pass
    
    class DoAThing:
        """Abstract superclass."""
        def __init__(self, fall_back=None):
            self.fall_back = fall_back
    
        def theThing(self, arg1, arg2):
            try:
                return self.doTheThing(arg1, arg2)
            except DoAThingError:
                if self.fall_back:
                    return self.fall_back.theThing(arg1, arg2)
    
        def doTheThing(self, arg1, arg2):
            raise DoAThingError("Not Implemented")
    
    class UseCache(DoAThing):
        """Is the answer in cache? Cache is dynamic and grows quickly.
        There's no LRU.
        """
        def __init__(self, *args, **kw):
            super().__init__(*args, **kw)
            self.cache = {}
    
        def load(self, openFile):
            self.cache = pickle.load(openFile)
    
        def dump(self, openFile):
            pickle.dump(self.cache, openFile)
    
        def theThing(self, arg1, arg2):
            if (arg1, arg2) not in self.cache:
                self.cache[arg1, arg2] = self.fall_back.theThing(arg1, arg2)
            return self.cache[arg1, arg2]
    
    class AlgorithmOne(DoAThing):
        """One way to do it."""
        def doTheThing(self, arg1, arg2):
            # Check some constraints, maybe...
            if arg1 < arg2:
                return Fraction(arg1, arg2)
            else:
                raise DoAThingError("Outside AlgorithmOne Constraints")
    
    class AlgorithmTwo(DoAThing):
        """Another way to do it."""
        def doTheThing(self, arg1, arg2):
            return arg1/arg2
    
    
    a2 = AlgorithmTwo()
    a1 = AlgorithmOne(a2)
    coc = UseCache(a1)
    
    print(coc.theThing(1,2))
    print(coc.theThing(2,1))
    print(coc.cache)

And that's it!
