# Python Singleton

Several approaches, ordered by when they were posted... 

* * *

class Singleton: 
    
    
    	class __OnlyOne: 
    	def __init__(self): 
    		pass
    
    
    
    	def __str__(self): 
    		return 'Non'
    
    
    
    	instance = {} 
    	def __init__(self): 
    		if self.__class__ not in Singleton.instance: 
    			Singleton.instance[self.__class__] = Singleton.__OnlyOne()
    			return True
    		else :
    			print 'warning : trying to recreate a singleton'
    			return False
    
    
    
    	def __getattr__(self, name): 
    		return getattr(self.instance[self.__class__], name)
    
    
    
    	def __setattr__(self, name, value):
    		return setattr(self.instance[self.__class__], name, value)
    

A little addition to the former proposal. this way, subclassing is possible. :) \-- LBdN 

* * *

**One line**

Just add the one line to singleton classes' __init__ method! 
    
    
    	>>> def singleton(self, instance={}):
    		try:
    			instance[self.__class__]
    			instance[self.__class__] = self
    		except KeyError[?](wiki?edit=KeyError):
    			raise RuntimeError[?](wiki?edit=RuntimeError), "Instance already exists: %s" % self.__class__
    
    
    
    	>>> class GreatThing[?](wiki?edit=GreatThing):
    	def __init__(self):
    		singleton(self)
    

This example is provided by Peter Norvig. 

\-- Sridhar 

\--- 

**Function returns same object every time**
    
    
    	class _Linkpref:
    	instance = None
    	def __init__(self):
    		self.on = True
    	def setOn(self):
    		self.on = True
    	def setOff(self):
    		# print 'linking turned off'
    		self.on = False
    	def isOn(self):
    		return self.on
    
    
    
    	def Linkpref():
    	if _Linkpref.instance == None:
    		_Linkpref.instance = _Linkpref()
    	return _Linkpref.instance
    

[History of this post: _I had started this page when I was new to Python and trying to figure out how to create a singleton. I was working with Wiki code where I needed to make a quick patch to turn off links. Since making this post, I have rewritten the code without the singleton pattern, but the above code did work as intended._ \-- [SteveHowell](wiki?SteveHowell)] 

* * *

**Create a module from a class**
    
    
    	class Linkpref:
    	def __init__(self):
    		self.on = True
    	def setOn(self):
    		self.on = True
    	def setOff(self):
    		# print 'linking turned off'
    		self.on = False
    	def isOn(self):
    		return self.on  #btw, I don't think setter/getter methods are good here.
    	>>> import sys
    	>>> sys.modules['Linkpref']=Linkpref()  
    	>>> import Linkpref
    	>>> #now Linkpref is a singleton
    

or simply as a single line 
    
    
    	>>> Linkpref=Linkpref() 
    

\-- [JuneKim](wiki?JuneKim)

* * *

**or just use a module instead of a class...**

isn't python module a singleton? (*) 
    
    
    	# linkpref.py
    	def doThis():
    	...  
    	def doThat():
    	...
    
    
    
    	>>> import linkpref
    	>>> linkpref.doThis()
    	>>> linkpref.doThat()
    

\-- NirSoffer[?](wiki?edit=NirSoffer)

(*) No, a module is no good as a singleton when you subclass. when you inherit by "from parent import *" that still doesn't make the parent call overridden methods 

\-- YairChuchem[?](wiki?edit=YairChuchem)

* * *

**Using lambda**

That's a slight behaviour change. Here's yet-another one: 
    
    
      class L:
    	pass
    
    
    
      L = lambda single_L=L(): single_L
    
    
    
      l = L()
      l.one = "one"
      l2 = L()
      print l2.one
    

* * *

**Feather weight proxy**

or feather weight proxy as like: 
    
    
    	class _Linkpref: 
    	# blah blah... 
    
    
    
    	class Linkpref: 
    	theSingleInstance = _Linkpref() 
    	def __init__(self): 
    		self.__dict__ = Linkpref.theSingleInstance.__dict__ 
    		self.__class__ = Linkpref.theSingleInstance.__class__ 
    
    
    
    

,where you can have multiple Link****Prefs all sharing the same **state**. More often than not, this pattern is more preferable than single-identity-single-state singletones. 

\-- [JuneKim](wiki?JuneKim)

* * *

**Static/class methods**

You can use static/class methods as well, which are added in Python 2.2 
    
    
    	>>> class Linkpref:
    	_instance=None
    	def getInstance():
    		if not Linkpref._instance:
    			Linkpref._instance=Linkpref() 
    		return Linkpref._instance		
    	getInstance=staticmethod(getInstance)
    

If you want to make it sure the client doesn't make instances by Linkpref(), use new.instance in getInstance to skip __init__, and call another constructor method, say, _init. And you may make Linkpref.__init__ raise an error for protection. 

\-- [JuneKim](wiki?JuneKim)

* * *

**Borg Pattern**

Recently in the python cook book, [AlexMartelli](wiki?AlexMartelli) showed us how Borg pattern works. It's in the same spirit of having the same state but not necessarily the same identity. (<http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/66531>) 
    
    
    	class Borg:
    	__shared_state = {}
    	def __init__(self):
    		self.__dict__ = self.__shared_state
    	# and whatever else you want in your class -- that's all!
    

\-- [JuneKim](wiki?JuneKim)

_The Borg Pattern looks more like that [MonostatePattern](wiki?MonostatePattern) than the [SingletonPattern](wiki?SingletonPattern), at least to me. I suspect some of the other variations above would also fall into that same category. -- [JimWeirich](wiki?JimWeirich)_

* * *

**Guarding against incorrect instantiation**

Using the featherweight proxy method above (which was my favorite), I made things just a bit more foolproof by actually checking to make sure the singleton's initializer was called from the proxy only. I do this by getting the stack trace data one level up and checking the context. 

class _SingletonClass: 
    
    
      def __init__(self):
    	st = traceback.extract_stack()
    	if st[-2][2] != "SingletonClass[?](wiki?edit=SingletonClass)":
    	raise Exception("Illegal to instantiate directly, use proxy class.")
    
    
    
    

class SingletonClass[?](wiki?edit=SingletonClass): 
    
    
      __instance = _SingletonClass() 
      def __init__(self): 
    	self.__dict__ = SingletonClass[?](wiki?edit=SingletonClass).__instance.__dict__ 
    	self.__class__ = SingletonClass[?](wiki?edit=SingletonClass).__instance.__class__ 
    
    
    
    

\-- Kevin K 

* * *

In this approach, the Singleton class itself keeps track of all the classes that are singletons that have been instantiated and stores them in its internal dictionary, deleting the instance reference when the subclass is destroyed. 

class Singleton: 
    
    
    	"""
    	an abstract class that should be inherited to provide
    	instance creation restriction
    	"""
    	__instance = {}
    
    
    
    	def getClassName( self ):
    		return self.__class__.__name__
    
    
    
    	def hasInstance( self ):
    		return self.getClassName() in Singleton.__instance
    
    
    
    	def __init__( self ):
    		classname = self.getClassName()
    		if self.hasInstance():
    			raise Singleton.__instance[ self.getClassName() ] 
    		Singleton.__instance[ self.getClassName() ] = self
    
    
    
    	def __del__( self ):
    		if self.hasInstance():
    			del Singleton.__instance[ self.getClassName() ]
    

\-- [AdrianCumiskey](wiki?AdrianCumiskey)

* * *

I've been using this idiom: 
    
    
     instance = None
    
    
    
     class Singleton(object): # subclassing from object for 2.2, unnecessary after that
    	def __new__(cls):
    	if instance is not None:
    	return instance
    	instance = object.__new__(cls)
    	return instance
    
    
    
    

__new__ allows you to take complete control of constructing a new-style object, including returning anything you want from the constructor. "Singleton()" returns what __new__ returns, which can technically be anything though you obvious break a lot of things if you return, say, an int. 

This gets really cool with "singletons" that aren't necessarily one instance per "class", but that you'd like to be one instance per some other criteria. For instance, I have an "XML Name" class (binds together the namespace of an XML element and the element name) that in skeleton form looks like this: 
    
    
     ExistingNames[?](wiki?edit=ExistingNames) = {}
    
    
    
     class XMLName(object):
    	def __new__(cls, name):
    	if name in ExistingNames[?](wiki?edit=ExistingNames):
    	return ExistingNames[?](wiki?edit=ExistingNames)[name]
    
    
    
    	self = object.__new__(cls)
    
    
    
    	self.name = name
    	ExistingNames[?](wiki?edit=ExistingNames)[name] = self
    
    
    
    	return self
    

Technically this isn't one instance per "class", but you can conceptualize each name as its own Singleton class. 

No special Python syntax needed or care in created instances, just "XMLName('img')" and off you go. -- [JeremyBowers](wiki?JeremyBowers)

You can get mixin behavior in Python too by mixin in a simple class, like the [RubySingleton](wiki?RubySingleton), it just isn't shipped with Python: 
    
    
     singletons = {}
     class SingletonMixin[?](wiki?edit=SingletonMixin)(object):
    	def __new__(cls, *args, **kwargs):
    	 if cls in singletons:
    		return singletons[cls]
    	 self = object.__new__(cls)
    	 cls.__init__(self, *args, **kwargs)
    	 singletons[cls] = self
    	 return self
    

Behavior may vary slightly and there are a lot of useful varients, but that should get most of the way there. Write a class with a normal __init__ and it should work correctly. (__init__ will only be run the first time; you can tweak it to behave as you need.) -- [JeremyBowers](wiki?JeremyBowers)

Using python 2.3.4 here, and it seems that __init__ will be run multiple times. 

* * *

Thanks to feedback I've had on my blog and the suggestion about using __new__ above, I have reworked my version. 

""" A Python Singleton mixin class that makes use of some of the ideas found at <http://c2.com/cgi/wiki?PythonSingleton>. Just inherit from it and you have a singleton. No code is required in subclasses to create singleton behavior -- inheritance from Singleton is all that is needed. 

Assume S is a class that inherits from Singleton. Useful behaviors are: 

1) Getting the singleton: 
    
    
    	S.getInstance() 
    
    
    
    

returns the instance of S. If none exists, it is created. 

2) The usual idiom to construct an instance by calling the class, i.e. 
    
    
    	S()
    
    
    
    

is disabled for the sake of clarity. If it were allowed, a programmer who didn't happen notice the inheritance from Singleton might think he was creating a new instance. So it is felt that it is better to make that clearer by requiring the call of a class method that is defined in Singleton. An attempt to instantiate via S() will restult in an SingletonException[?](wiki?edit=SingletonException) being raised. 

3) If S.__init__(.) requires parameters, include them in the first call to S.getInstance(.). If subsequent calls have parameters, a SingletonException[?](wiki?edit=SingletonException) is raised. 

4) As an implementation detail, classes that inherit from Singleton may not have their own __new__ methods. To make sure this requirement is followed, an exception is raised if a Singleton subclass includ es __new__. This happens at subclass instantiation time (by means of the MetaSingleton[?](wiki?edit=MetaSingleton) metaclass. 

By Gary Robinson, grobinson@transpose.com. No rights reserved -- placed in the public domain -- which is only reasonable considering how much it owes to other people's version which are in the public domain. The idea of using a metaclass came from a comment on Gary's blog (see <http://www.garyrobinson.net/2004/03/python_singleto.html#comments>). Not guaranteed to be fit for any particular purpose. """

class SingletonException[?](wiki?edit=SingletonException)(Exception): 
    
    
    	pass
    
    
    
    

class MetaSingleton[?](wiki?edit=MetaSingleton)(type): 
    
    
    	def __new__(metaclass, strName, tupBases, dict):
    	if '__new__' in dict:
    		raise SingletonException[?](wiki?edit=SingletonException), 'Can not override __new__ in a Singleton'
    	return super(MetaSingleton[?](wiki?edit=MetaSingleton),metaclass).__new__(metaclass, strName, tupBases, dict)
    
    
    
    	def __call__(cls, *lstArgs, **dictArgs):
    	raise SingletonException[?](wiki?edit=SingletonException), 'Singletons may only be instantiated through getInstance()'
    
    
    
    

class Singleton(object): 
    
    
    	__metaclass__ = MetaSingleton[?](wiki?edit=MetaSingleton)
    
    
    
    	def getInstance(cls, *lstArgs):
    	"""
    	Call this to instantiate an instance or retrieve the existing instance.
    	If the singleton requires args to be instantiated, include them the first
    	time you call getInstance.	
    	"""
    	if cls._isInstantiated():
    		if len(lstArgs) != 0:
    		raise SingletonException[?](wiki?edit=SingletonException), 'If no supplied args, singleton must already be instantiated, or __init__ must require no args'
    	else:
    		if len(lstArgs) != cls._getConstructionArgCountNotCountingSelf():  
    		raise SingletonException[?](wiki?edit=SingletonException), 'If the singleton requires __init__ args, supply them on first instantiation'
    		instance = cls.__new__(cls)
    		instance.__init__(*lstArgs)
    		cls.cInstance = instance
    	return cls.cInstance
    	getInstance = classmethod(getInstance)
    
    
    
    	def _isInstantiated(cls):
    	return hasattr(cls, 'cInstance')
    	_isInstantiated = classmethod(_isInstantiated)
    
    
    
    	def _getConstructionArgCountNotCountingSelf(cls):
    	return cls.__init__.im_func.func_code.co_argcount - 1
    	_getConstructionArgCountNotCountingSelf = classmethod(_getConstructionArgCountNotCountingSelf)
    
    
    
    	def _forgetClassInstanceReferenceForTesting(cls):
    	"""
    	This is designed for convenience in testing -- sometimes you 
    	want to get rid of a singleton during test code to see what
    	happens when you call getInstance() under a new situation.
    
    
    
    	To really delete the object, all external references to it
    	also need to be deleted.
    	"""
    	del cls.cInstance
    	_forgetClassInstanceReferenceForTesting = classmethod(_forgetClassInstanceReferenceForTesting)
    

For a python source file with unit tests, taken from the CVS tree of an active commercial product, and incorporating any future improvements and notes, see <http://www.garyrobinson.net/2004/03/python_singleto.html>. 

* * *

Why is the simplest solution not posted? 

In module Singleton.py: 

class Singleton: 
    
    
    	pass
    

Single_Instance = Singleton() 

In your module: 

from Singleton import Single_Instance 

* * *

I've just got an insight of a really simple Singleton-in-python version. It's just an improvement over the Single_Instance above, but it at least implements a bit of the regular class-object interface. 

It works like this: 

class Singleton(object): 
    
    
    	def __call__(self):
    	return self
    

Singleton = Singleton() 

And, doing this, you've just rebound the class name to an instance of itself, that, when called, returns itself. So, if you say MyObj[?](wiki?edit=MyObj) = Singleton() and MyOther[?](wiki?edit=MyOther) = Singleton(), MyObj[?](wiki?edit=MyObj) is MyOther[?](wiki?edit=MyOther) returns true. 

This is by far the simplest solution I found, as it involves no weird metaclass-hacks or dictionary-hacks. The only disadvantage I can think of is that, as Singleton isn't strictly a class, it can't be inherited from, so every singleton implemented this way would have to do this same thing. But I think it's probably worth the trouble. 

* * *

def Singleton(name, bases, d): 
    
    
    	def __init__(self, *args, **kw):
    	raise TypeError[?](wiki?edit=TypeError)("cannot create '%s' instances" %
    			self.__class__.__name__)
    	instance = type(name, bases, d)()
    	instance.__class__.__init__ = __init__
    	return instance
    

Any class that uses this as its metaclass should behave identically to any of the built-in singleton types (such as None). Note that this includes forbidding inheritance. 

\-- IanBollinger[?](wiki?edit=IanBollinger)

* * *

None of these are thread-safe, right? 

Between the moment the instance is checked and the moment the instance is created, another thread might create an instance on his own. 

_I would start by noting that Python's import mechanism is thread-safe. You can use a module as the singleton object for most purposes. It is easy to implement, easy to understand and easy to extend. If your program is complicated enough that it needs to use the [SingletonPattern](wiki?SingletonPattern), Don't scrimp on the number of files._

_If you really need an object from an already written class (i.e. using the property() builtin), I present the following adapted from:_

  * <http://stackoverflow.com/questions/31875/is-there-a-simple-elegant-way-to-define-singletons-in-python>

import threading 

class Singleton(type): 
    
    
    	""" A singleton metaclass. """
    	def __init__(cls, name, bases, dictionary):
    		super(Singleton, cls).__init__(name, bases, dictionary)
    		cls._instance = None
    		cls._rlock = threading.RLock()
    
    
    
    	def __call__(cls, *args, **kws):
    		with cls._rlock:
    			if cls._instance is None:
    				cls._instance = super(Singleton, cls).__call__(*args, **kws)
    		return cls._instance
    
    
    
    

_You can probably replace the re-entrant lock with threading.Lock. If you are interested in [PrematureOptimization](wiki?PrematureOptimization) you can add to the beginning of the __call__() method the condition _if cls._instance is not None: return cls._instance_ so you do not need to acquire the lock in most cases._

''Usage example: '' 
    
    
    	>>> class C(object):
    	... 	__metaclass__ = Singleton
    	>>> c1 = C()
    	>>> c2 = C()
    	>>> c1 is c2
    	True
    	>>> id(c1) == id(c2)
    	True
    
    
    
    

* * *

Compare with [PerlSingleton](wiki?PerlSingleton) and [RubySingleton](wiki?RubySingleton)

[CategoryPython](wiki?CategoryPython)

* * *

View edit of [August 28, 2011](quickDiff?PythonSingleton) or [FindPage](wiki?FindPage) with title or text search  
