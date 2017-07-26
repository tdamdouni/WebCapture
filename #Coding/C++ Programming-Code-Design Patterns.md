# C++ Programming/Code/Design Patterns

_Captured: 2015-10-25 at 20:35 from [en.m.wikibooks.org](https://en.m.wikibooks.org/wiki/C%2B%2B_Programming/Code/Design_Patterns)_

Software design patterns are abstractions that help structure system designs. While not new, since the concept was already described by [Christopher Alexander](//en.wikipedia.org/wiki/Christopher_Alexander) in its architectural theories, it only gathered some traction in programming due to the publication of [Design Patterns: Elements of Reusable Object-Oriented Software](//en.wikipedia.org/wiki/Design_Patterns) book in October 1994 by [Erich Gamma](//en.wikipedia.org/wiki/Erich_Gamma), [Richard Helm](//en.wikipedia.org/wiki/Richard_Helm), [Ralph Johnson](//en.wikipedia.org/wiki/Ralph_Johnson) and [John Vlissides](//en.wikipedia.org/wiki/John_Vlissides), known as the **Gang of Four (GoF)**, that identifies and describes 23 classic software design patterns.

A design pattern is neither a static solution, nor is it an algorithm. A **pattern** is a way to describe and address by name (mostly a simplistic description of its goal), a repeatable solution or approach to a common design problem, that is, a common way to solve a generic problem (how generic or complex, depends on how restricted the target goal is). Patterns can emerge on their own or by design. This is why design patterns are useful as an abstraction over the implementation and a help at design stage. With this concept, an easier way to facilitate communication over a design choice as normalization technique is given so that every person can share the design concept.

Depending on the design problem they address, design patterns can be classified in different categories, of which the main categories are:

Patterns are commonly found in objected-oriented programming languages like C++ or Java. They can be seen as a template for how to solve a problem that occurs in many different situations or applications. It is not code reuse, as it usually does not specify code, but code can be easily created from a design pattern. Object-oriented design patterns typically show relationships and interactions between classes or objects without specifying the final application classes or objects that are involved.

Each design pattern consists of the following parts:

Problem/requirement 
    To use a design pattern, we need to go through a mini analysis design that may be coded to test out the solution. This section states the requirements of the problem we want to solve. This is usually a common problem that will occur in more than one application.

    This section states the technological boundaries, that helps and guides the creation of the solution.

    This section describes how to write the code to solve the above problem. This is the design part of the design pattern. It may contain class diagrams, sequence diagrams, and or whatever is needed to describe how to code the solution.

Design patterns can be considered as a standardization of commonly agreed best practices to solve specific design problems. One should understand them as a way to implement good design patterns within applications. Doing so will reduce the use of inefficient and obscure solutions[_[citation needed](https://en.m.wikibooks.org/wiki/Wikibooks:OR)_]. Using design patterns speeds up your design and helps to communicate it to other programmers[_[citation needed](https://en.m.wikibooks.org/wiki/Wikibooks:OR)_].

In [software engineering](//en.wikipedia.org/wiki/software_engineering), **creational design patterns** are [design patterns](//en.wikipedia.org/wiki/design_pattern_\(computer_science\)) that deal with [object creation](//en.wikipedia.org/wiki/object_lifetime) mechanisms, trying to create objects in a manner suitable to the situation. The basic form of object creation could result in design problems or added complexity to the design. Creational design patterns solve this problem by somehow controlling this object creation.

In this section of the book we assume that the reader has enough familiarity with functions, global variables, stack vs. heap, classes, pointers, and static member functions as introduced before.

As we will see there are several creational design patterns, and all will deal with a specific implementation task, that will create a higher level of abstraction to the code base, we will now cover each one.

The Builder Creational Pattern is used to separate the construction of a complex object from its representation so that the same construction process can create different objects representations.

    We want to construct a complex object, however we do not want to have a complex constructor member or one that would need many arguments.

    Define an intermediate object whose member functions define the desired object part by part before the object is available to the client. Builder Pattern lets us defer the construction of the object until all the options for creation have been specified.
    
    
    #include <string>
    #include <iostream>
    
    using namespace std;
    
    // "Product"
    class Pizza
    {
    	public:
    		void setDough(const string& dough)
    		{
    			m_dough = dough;
    		}
    		void setSauce(const string& sauce)
    		{
    			m_sauce = sauce;
    		}
    		void setTopping(const string& topping)
    		{
    			m_topping = topping;
    		}
    		void open() const
    		{
    			cout << "Pizza with " << m_dough << " dough, " << m_sauce << " sauce and "
    			<< m_topping << " topping. Mmm." << endl;
    		}
    	private:
    		string m_dough;
    		string m_sauce;
    		string m_topping;
    };
    
    // "Abstract Builder"
    class PizzaBuilder
    {
    	public:
                    virtual ~PizzaBuilder() {}; 
    
    		Pizza* getPizza()
    		{
    			return m_pizza;
    		}
    		void createNewPizzaProduct()
    		{
    			m_pizza = new Pizza;
    		}
    		virtual void buildDough() = 0;
    		virtual void buildSauce() = 0;
    		virtual void buildTopping() = 0;
    	protected:
    		Pizza* m_pizza;
    };
    
    //----------------------------------------------------------------
    
    class HawaiianPizzaBuilder : public PizzaBuilder
    {
    	public:
                    virtual ~HawaiianPizzaBuilder() {}; 
    
    		virtual void buildDough()
    		{
    			m_pizza->setDough("cross");
    		}
    		virtual void buildSauce()
    		{
    			m_pizza->setSauce("mild");
    		}
    		virtual void buildTopping()
    		{
    			m_pizza->setTopping("ham+pineapple");
    		}
    };
    
    class SpicyPizzaBuilder : public PizzaBuilder
    {
    	public:
                    virtual ~SpicyPizzaBuilder() {}; 
    
    		virtual void buildDough()
    		{
    			m_pizza->setDough("pan baked");
    		}
    		virtual void buildSauce()
    		{
    			m_pizza->setSauce("hot");
    		}
    		virtual void buildTopping()
    		{
    			m_pizza->setTopping("pepperoni+salami");
    		}
    };
    
    //----------------------------------------------------------------
    
    class Cook
    {
    	public:
    		void setPizzaBuilder(PizzaBuilder* pb)
    		{
    			m_pizzaBuilder = pb;
    		}
    		Pizza* getPizza()
    		{
    			return m_pizzaBuilder->getPizza();
    		}
    		void constructPizza()
    		{
    			m_pizzaBuilder->createNewPizzaProduct();
    			m_pizzaBuilder->buildDough();
    			m_pizzaBuilder->buildSauce();
    			m_pizzaBuilder->buildTopping();
    		}
    	private:
    		PizzaBuilder* m_pizzaBuilder;
    };
    
    int main()
    {
    	Cook cook;
    	PizzaBuilder* hawaiianPizzaBuilder = new HawaiianPizzaBuilder;
    	PizzaBuilder* spicyPizzaBuilder   = new SpicyPizzaBuilder;
    	
    	cook.setPizzaBuilder(hawaiianPizzaBuilder);
    	cook.constructPizza();
    	
    	Pizza* hawaiian = cook.getPizza();
    	hawaiian->open();
    	
    	cook.setPizzaBuilder(spicyPizzaBuilder);
    	cook.constructPizza();
    	
    	Pizza* spicy = cook.getPizza();
    	spicy->open();
    	
    	delete hawaiianPizzaBuilder;
    	delete spicyPizzaBuilder;
    	delete hawaiian;  
    	delete spicy;     
    }
    

**Definition**: A utility class that creates an instance of a class from a family of derived classes

**Definition**: A utility class that creates an instance of several families of classes. It can also return a factory for a certain group.

The Factory Design Pattern is useful in a situation that requires the creation of many different types of objects, all derived from a common base type. The Factory Method defines a method for creating the objects, which subclasses can then override to specify the derived type that will be created. Thus, at run time, the Factory Method can be passed a description of a desired object (e.g., a string read from user input) and return a base class pointer to a new instance of that object. The pattern works best when a well-designed interface is used for the base class, so there is no need to cast the returned object.

    We want to decide at run time what object is to be created based on some configuration or application parameter. When we write the code, we do not know what class should be instantiated.

    Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.

In the following example, a factory method is used to create laptop or desktop computer objects at run time.

Let's start by defining `Computer`, which is an abstract base class (interface) and its derived classes: `Laptop` and `Desktop`.
    
    
     class Computer
     {
     public:
         virtual void Run() = 0;
         virtual void Stop() = 0;
         
         virtual ~Computer() {}; /* without this, you do not call Laptop or Desktop destructor in this example! */
     };
     class Laptop: public Computer
     {
     public:
         virtual void Run(){mHibernating = false;}; 
         virtual void Stop(){mHibernating = true;}; 
         virtual ~Laptop() {}; /* because we have virtual functions, we need virtual destructor */
     private:
         bool mHibernating; // Whether or not the machine is hibernating
     };
     class Desktop: public Computer
     {
     public:
         virtual void Run(){mOn = true;}; 
         virtual void Stop(){mOn = false;}; 
         virtual ~Desktop() {};
     private:
         bool mOn; // Whether or not the machine has been turned on
     };
    

The actual `ComputerFactory` class returns a `Computer`, given a real world description of the object.
    
    
     class ComputerFactory
     {
     public:
         static Computer *NewComputer(const std::string &description)
         {
             if(description == "laptop")
                 return new Laptop;
             if(description == "desktop")
                 return new Desktop;
             return NULL;
         }
     };
    

Let's analyze the benefits of this design. First, there is a compilation benefit. If we move the interface `Computer` into a separate header file with the factory, we can then move the implementation of the `NewComputer()` function into a separate implementation file. Now the implementation file for `NewComputer()` is the only one that requires knowledge of the derived classes. Thus, if a change is made to any derived class of `Computer`, or a new `Computer` subtype is added, the implementation file for `NewComputer()` is the only file that needs to be recompiled. Everyone who uses the factory will only care about the interface, which should remain consistent throughout the life of the application.

Also, if there is a need to add a class, and the user is requesting objects through a user interface, no code calling the factory may be required to change to support the additional computer type. The code using the factory would simply pass on the new string to the factory, and allow the factory to handle the new types entirely.

Imagine programming a video game, where you would like to add new types of enemies in the future, each of which has different AI functions and can update differently. By using a factory method, the controller of the program can call to the factory to create the enemies, without any dependency or knowledge of the actual types of enemies. Now, future developers can create new enemies, with new AI controls and new drawing member functions, add it to the factory, and create a level which calls the factory, asking for the enemies by name. Combine this method with an [XML](https://en.m.wikibooks.org/wiki/XML) description of levels, and developers could create new levels without having to recompile their program. All this, thanks to the separation of creation of objects from the usage of objects.

Another example:
    
    
    #include <stdexcept>
    #include <iostream>
    #include <memory>
    
    class Pizza {
    public:
        virtual int getPrice() const = 0;
        virtual ~Pizza() {};  /* without this, no destructor for derived Pizza's will be called. */ 
    };
     
    class HamAndMushroomPizza : public Pizza {
    public:
        virtual int getPrice() const { return 850; }; 
        virtual ~HamAndMushroomPizza() {}; 
    };
     
    class DeluxePizza : public Pizza {
    public:
        virtual int getPrice() const { return 1050; }; 
        virtual ~DeluxePizza() {};
    };
     
    class HawaiianPizza : public Pizza {
    public:
        virtual int getPrice() const { return 1150; }; 
        virtual ~HawaiianPizza() {}; 
    };
     
    class PizzaFactory {
    public:
        enum PizzaType {
             HamMushroom,
             Deluxe,
             Hawaiian
        };
     
        static Pizza* createPizza(PizzaType pizzaType) {
            switch (pizzaType) {
                case HamMushroom:
                    return new HamAndMushroomPizza();
                case Deluxe:
                    return new DeluxePizza();
                case Hawaiian:
                    return new HawaiianPizza();
            }
            throw "invalid pizza type.";
        }
    };
     
    /*
     * Create all available pizzas and print their prices
     */
    void pizza_information( PizzaFactory::PizzaType pizzatype )
    {
    	Pizza* pizza = PizzaFactory::createPizza(pizzatype);
    	std::cout << "Price of " << pizzatype << " is " << pizza->getPrice() << std::endl;
    	delete pizza;
    }
    
    int main ()
    {
    	pizza_information( PizzaFactory::HamMushroom );
    	pizza_information( PizzaFactory::Deluxe );
    	pizza_information( PizzaFactory::Hawaiian );
    }
    

A prototype pattern is used in software development when the type of objects to create is determined by a prototypical instance, which is cloned to produce new objects. This pattern is used, for example, when the inherent cost of creating a new object in the standard way (e.g., using the `new` keyword) is prohibitively expensive for a given application.

**Implementation**: Declare an abstract base class that specifies a pure virtual `clone()` method. Any class that needs a "polymorphic constructor" capability derives itself from the abstract base class, and implements the `clone()` operation.

Here the client code first invokes the factory method. This factory method, depending on the parameter, finds out the concrete class. On this concrete class, the `clone()` method is called and the object is returned by the factory method.

  * This is sample code which is a sample implementation of Prototype method. We have the detailed description of all the components here. 
    * `Record` class, which is a pure virtual class that has a pure virtual method `clone()`.
    * `CarRecord`, `BikeRecord` and `PersonRecord` as concrete implementation of a `Record` class.
    * An [enum](https://en.m.wikibooks.org/wiki/C%2B%2B_Programming/Programming_Languages/C%2B%2B/Code/Keywords/enum) RECORD_TYPE_en as one to one mapping of each concrete implementation of `Record` class.
    * `RecordFactory` class that has a `Factory` method `CreateRecord(…)`. This method requires an [enum](https://en.m.wikibooks.org/wiki/C%2B%2B_Programming/Programming_Languages/C%2B%2B/Code/Keywords/enum) RECORD_TYPE_en as parameter and depending on this parameter it returns the concrete implementation of `Record` class.
    
    
      /**
       * Implementation of Prototype Method 
       **/
      #include <iostream>
      #include <map>
      #include <string>
      
      using namespace std;
      
      enum RECORD_TYPE_en
      {
        CAR,
        BIKE,
        PERSON
      };
      
      /**
       * Record is the base Prototype
       */
      
      class Record
      {
        public :
      
          Record() {}
      
          virtual ~Record() {}
      
          virtual Record* clone()=0;
          
          virtual void print()=0;
      };
      
      /**
       * CarRecord is a Concrete Prototype
       */
      
      class CarRecord : public Record
      {
        private:
          string m_carName;
          int m_ID;
      
        public:
          CarRecord(string carName, int ID)
            : Record()
            , m_carName(carName)
            ,m_ID(ID)
          {
          }
        
          CarRecord(const CarRecord& carRecord)
            : Record(carRecord)//call the base default copy  constructor
          {
            m_carName = carRecord.m_carName;
            m_ID = carRecord.m_ID;
          }
        
          ~CarRecord() {}
      
          Record* clone()
          {
            return new CarRecord(*this);
          }
        
          void print()
          {
            cout << "Car Record" << endl
              << "Name  : " << m_carName << endl
              << "Number: " << m_ID << endl << endl;
          }
      };
      
      
      /**
       * BikeRecord is the Concrete Prototype
       */
      
      class BikeRecord : public Record
      {
        private :
          string m_bikeName;
        
          int m_ID;
        
        public :
          BikeRecord(string bikeName, int ID)
            : Record()
            , m_bikeName(bikeName)
            , m_ID(ID)
          {
          }
        
          BikeRecord(const BikeRecord& bikeRecord)
            : Record(bikeRecord)
          {
            m_bikeName = bikeRecord.m_bikeName;
            m_ID = bikeRecord.m_ID;
          }
        
          ~BikeRecord() {}
      
          Record* clone()
          {
            return new BikeRecord(*this);
          }
        
          void print()
          {
            cout << "Bike Record" << endl
              << "Name  : " << m_bikeName << endl
              << "Number: " << m_ID << endl << endl;
          }
      };
      
      
      /**
       * PersonRecord is the Concrete Prototype
       */
      
      class PersonRecord : public Record
      {
        private :
          string m_personName;
          
          int m_age;
        
        public :
          PersonRecord(string personName, int age)
            : Record()
            , m_personName(personName)
            , m_age(age)
          {
          }
        
          PersonRecord(const PersonRecord& personRecord)
            : Record(personRecord)
          {
            m_personName = personRecord.m_personName;
            m_age = personRecord.m_age;
          }
        
          ~PersonRecord() {}
        
          Record* clone()
          {
            return new PersonRecord(*this);
          }
        
        void print()
        {
          cout << "Person Record" << endl
            << "Name : " << m_personName << endl
            << "Age  : " << m_age << endl << endl ;
        }
      };
      
      
      /**
       * RecordFactory is the client
       */
      
      class RecordFactory
      {
        private :
          map<RECORD_TYPE_en, Record* > m_recordReference;
      
        public :
          RecordFactory()
          {
            m_recordReference[CAR]  = new CarRecord("Ferrari", 5050);
            m_recordReference[BIKE] = new BikeRecord("Yamaha", 2525);
            m_recordReference[PERSON] = new PersonRecord("Tom", 25);
          }
        
          ~RecordFactory()
          {
            delete m_recordReference[CAR];
            delete m_recordReference[BIKE];
            delete m_recordReference[PERSON];
          }
        
          Record* createRecord(RECORD_TYPE_en enType)
          {
            return m_recordReference[enType]->clone();
          }
      };
      
      int main()
      {
        RecordFactory* poRecordFactory = new RecordFactory();
      
        Record* poRecord;
        poRecord = poRecordFactory->createRecord(CAR);
        poRecord->print();
        delete poRecord;
        
        poRecord = poRecordFactory->createRecord(BIKE);
        poRecord->print();
        delete poRecord;
        
        poRecord = poRecordFactory->createRecord(PERSON);
        poRecord->print();
        delete poRecord;
      
        delete poRecordFactory;
        return 0;
      }
    

Another example:

To implement the pattern, declare an abstract base class that specifies a pure virtual `clone()` member function. Any class that needs a "polymorphic constructor" capability derives itself from the abstract base class, and implements the `clone()` operation.

The client, instead of writing code that invokes the `new` operator on a hard-wired class name, calls the `clone()` member function on the prototype, calls a factory member function with a parameter designating the particular concrete derived class desired, or invokes the `clone()` member function through some mechanism provided by another design pattern.
    
    
     class CPrototypeMonster
     {
     protected:            
         CString           _name;
     public:
         CPrototypeMonster();
         CPrototypeMonster( const CPrototypeMonster& copy );
         virtual ~CPrototypeMonster();
     
         virtual CPrototypeMonster*    Clone() const=0; // This forces every derived class to provide an overload for this function.
         void        Name( CString name );
         CString    Name() const;
     };
    
     class CGreenMonster : public CPrototypeMonster
     {
     protected: 
         int         _numberOfArms;
         double      _slimeAvailable;
     public:
         CGreenMonster();
         CGreenMonster( const CGreenMonster& copy );
         ~CGreenMonster();
     
         virtual CPrototypeMonster*    Clone() const;
         void  NumberOfArms( int numberOfArms );
         void  SlimeAvailable( double slimeAvailable );
     
         int         NumberOfArms() const;
         double      SlimeAvailable() const;
     };
    
     class CPurpleMonster : public CPrototypeMonster
     {
     protected:
         int         _intensityOfBadBreath;
         double      _lengthOfWhiplikeAntenna;
     public:
         CPurpleMonster();
         CPurpleMonster( const CPurpleMonster& copy );
         ~CPurpleMonster();
     
         virtual CPrototypeMonster*    Clone() const;
     
         void  IntensityOfBadBreath( int intensityOfBadBreath );
         void  LengthOfWhiplikeAntenna( double lengthOfWhiplikeAntenna );
     
         int       IntensityOfBadBreath() const;
         double    LengthOfWhiplikeAntenna() const;
     };
    
     class CBellyMonster : public CPrototypeMonster
     {
     protected:
         double      _roomAvailableInBelly;
     public:
         CBellyMonster();
         CBellyMonster( const CBellyMonster& copy );
         ~CBellyMonster();
     
         virtual CPrototypeMonster*    Clone() const;
     
         void       RoomAvailableInBelly( double roomAvailableInBelly );
         double     RoomAvailableInBelly() const;
     };
    
     CPrototypeMonster* CGreenMonster::Clone() const
     {
         return new CGreenMonster(*this);
     }
    
     CPrototypeMonster* CPurpleMonster::Clone() const
     {
         return new CPurpleMonster(*this);
     }
    
     CPrototypeMonster* CBellyMonster::Clone() const
     {
         return new CBellyMonster(*this);
     }
    

A client of one of the concrete monster classes only needs a reference (pointer) to a `CPrototypeMonster` class object to be able to call the 'Clone' function and create copies of that object. The function below demonstrates this concept:
    
    
     void DoSomeStuffWithAMonster( const CPrototypeMonster* originalMonster )
     {
         CPrototypeMonster* newMonster = originalMonster->Clone();
         ASSERT( newMonster );
     
         newMonster->Name("MyOwnMonster");
         // Add code doing all sorts of cool stuff with the monster.
         delete newMonster;
     }
    

Now originalMonster can be passed as a pointer to CGreenMonster, CPurpleMonster or CBellyMonster.

The **Singleton pattern** ensures that a class has only one instance and provides a global point of access to that instance. It is named after the singleton set, which is defined to be a set containing one element. This is useful when exactly one object is needed to coordinate actions across the system.

**Check list**

  * Define a private static attribute in the "single instance" class.
  * Define a public static accessor function in the class.
  * Do "lazy initialization" (creation on first use) in the accessor function.
  * Define all constructors to be protected or private.
  * Clients may only use the accessor function to manipulate the Singleton.

Let's take a look at how a Singleton differs from other variable types.

Like a global variable, the Singleton exists outside of the scope of any functions. Traditional implementation uses a static member function of the Singleton class, which will create a single instance of the Singleton class on the first call, and forever return that instance. The following code example illustrates the elements of a C++ singleton class, that simply stores a single string.
    
    
     class StringSingleton
     {
     public:
         // Some accessor functions for the class, itself
         std::string GetString() const 
         {return mString;}
         void SetString(const std::string &newStr)
         {mString = newStr;}
     
         // The magic function, which allows access to the class from anywhere
         // To get the value of the instance of the class, call:
         //     StringSingleton::Instance().GetString();
         static StringSingleton &Instance()
         {
             // This line only runs once, thus creating the only instance in existence
             static StringSingleton *instance = new StringSingleton;
             // dereferencing the variable here, saves the caller from having to use 
             // the arrow operator, and removes temptation to try and delete the 
             // returned instance.
             return *instance; // always returns the same instance
         }
     
     private: 
         // We need to make some given functions private to finish the definition of the singleton
         StringSingleton(){} // default constructor available only to members or friends of this class
     
         // Note that the next two functions are not given bodies, thus any attempt 
         // to call them implicitly will return as compiler errors. This prevents 
         // accidental copying of the only instance of the class.
         StringSingleton(const StringSingleton &old); // disallow copy constructor
         const StringSingleton &operator=(const StringSingleton &old); //disallow assignment operator
     
         // Note that although this should be allowed, 
         // some compilers may not implement private destructors
         // This prevents others from deleting our one single instance, which was otherwise created on the heap
         ~StringSingleton(){} 
     private: // private data for an instance of this class
         std::string mString;
     };
    

Variations of Singletons:

Applications of Singleton Class:

One common use of the singleton design pattern is for application configurations. Configurations may need to be accessible globally, and future expansions to the application configurations may be needed. The subset C's closest alternative would be to create a single global _`struct`_. This had the lack of clarity as to where this object was instantiated, as well as not guaranteeing the existence of the object.

Take, for example, the situation of another developer using your singleton inside the constructor of their object. Then, yet another developer decides to create an instance of the second class in the global scope. If you had simply used a global variable, the order of linking would then matter. Since your global will be accessed, possibly before main begins executing, there is no definition as to whether the global is initialized, or the constructor of the second class is called first. This behavior can then change with slight modifications to other areas of code, which would change order of global code execution. Such an error can be very hard to debug. But, with use of the singleton, the first time the object is accessed, the object will also be created. You now have an object which will always exist, in relation to being used, and will never exist if never used.

A second common use of this class is in updating old code to work in a new architecture. Since developers may have used globals liberally, moving them into a single class and making it a singleton, can be an intermediary step to bring the program inline to stronger object oriented structure.

Another example:
    
    
    #include <iostream>
    using namespace std;
    
    /* Place holder for thread synchronization mutex */
    class Mutex
    {   /* placeholder for code to create, use, and free a mutex */
    };
    
    /* Place holder for thread synchronization lock */
    class Lock
    {   public:
            Lock(Mutex& m) : mutex(m) { /* placeholder code to acquire the mutex */ }
            ~Lock() { /* placeholder code to release the mutex */ }
        private:
            Mutex & mutex;
    };
    
    class Singleton
    {   public:
            static Singleton* GetInstance();
            int a;
            ~Singleton() { cout << "In Destructor" << endl; }
    
        private:
            Singleton(int _a) : a(_a) { cout << "In Constructor" << endl; }
        
    
            static Mutex mutex;
    
            // Not defined, to prevent copying
            Singleton(const Singleton& );
            Singleton& operator =(const Singleton& other);
    };
    
    Mutex Singleton::mutex;
    
    Singleton* Singleton::GetInstance()
    {
        Lock lock(mutex);
    
        cout << "Get Instance" << endl;
    
        // Initialized during first access
        static Singleton inst(1);
    
        return &inst;
    }
    
    int main()
    {
        Singleton* singleton = Singleton::GetInstance();
        cout << "The value of the singleton: " << singleton->a << endl;
        return 0;
    }
    

**Note:**  
In the above example, the first call to `Singleton::GetInstance` will initialize the singleton instance. This example is for illustrative purposes only; for anything but a trivial example program, this code contains errors.

Convert the interface of a class into another interface that clients expect. **Adapter** lets classes work together that couldn't otherwise because of incompatible interfaces.
    
    
    #include <iostream>
    
    class Muslim {  // Abstract Target
    	virtual ~Muslim() = default;
    	virtual void performsMuslimRitual() = 0;
    };
    
    class MuslimFemale : public Muslim {  // Concrete Target
    	virtual void performsMuslimRitual() override {std::cout << "Muslim girl performs Muslim ritual." << std::endl;}
    };
    
    class Hindu {  // Abstract Adaptee
    	virtual ~Hindu() = default;
    	virtual void performsHinduRitual() = 0;
    };
    
    class HinduFemale : public Hindu {  // Concrete Adaptee
    	virtual void performsHinduRitual() override {std::cout << "Hindu girl performs Hindu ritual." << std::endl;}
    };
    
    class MuslimRitual {
    	void carryOutRitual (Muslim* muslim) {
    		std::cout << "On with the Muslim rituals!" << std::endl;
    		muslim->performsMuslimRitual();
    	}
    };
    
    class MuslimAdapter : public Muslim {  // Adapter
    	private:
    		Hindu* hindu;
    	public:
    		MuslimAdapter (Hindu* h) : hindu(h) {}
    		virtual void performsMuslimRitual() override {hindu->performsHinduRitual();}
    };
    
    int main() {  // Client code
    	HinduFemale* hinduGirl = new HinduFemale;
    	MuslimFemale* muslimGirl = new MuslimFemale;
    	MuslimRitual muslimRitual;
    //	muslimRitual.carryOutRitual (hinduGirl);  // Will not compile of course since the parameter must be of type Muslim*.
    	MuslimAdapter* adaptedHindu = new MuslimAdapter (hinduGirl);  // hinduGirl has adapted to become a Muslim!
    	
    	muslimRitual.carryOutRitual (muslimGirl);
    	muslimRitual.carryOutRitual (adaptedHindu);  // So now hinduGirl, in the form of adaptedHindu, participates in the muslimRitual!
                    // Note that hinduGirl is carrying out her own type of ritual in muslimRitual though.
    	
    	delete adaptedHindu;  // adaptedHindu is not needed anymore
    }
    

The Bridge Pattern is used to separate out the interface from its implementation. Doing this gives the flexibility so that both can vary independently.

The following example will output:
    
    
    API1.circle at 1:2 7.5
    API2.circle at 5:7 27.5
    
    
    
    #include <iostream>
    
    using namespace std;
    
    /* Implementor*/
    class DrawingAPI {
      public:
       virtual void drawCircle(double x, double y, double radius) = 0;
       virtual ~DrawingAPI() {}
    };
    
    /* Concrete ImplementorA*/
    class DrawingAPI1 : public DrawingAPI {
      public:
       void drawCircle(double x, double y, double radius) {
          cout << "API1.circle at " << x << ':' << y << ' ' << radius << endl;
       }
    };
    
    /* Concrete ImplementorB*/
    class DrawingAPI2 : public DrawingAPI {
    public:
       void drawCircle(double x, double y, double radius) {
          cout << "API2.circle at " << x << ':' << y << ' ' <<  radius << endl;
       }
    };
    
    /* Abstraction*/
    class Shape {
      public:
       virtual ~Shape() {}
       virtual void draw() = 0;
       virtual void resizeByPercentage(double pct) = 0;
    };
    
    /* Refined Abstraction*/
    class CircleShape : public Shape {
      public:
       CircleShape(double x, double y,double radius, DrawingAPI *drawingAPI) :
    	   m_x(x), m_y(y), m_radius(radius), m_drawingAPI(drawingAPI)
       {}
       void draw() {
          m_drawingAPI->drawCircle(m_x, m_y, m_radius);
       }
       void resizeByPercentage(double pct) {
          m_radius *= pct;
       }
      private:
       double m_x, m_y, m_radius;
       DrawingAPI *m_drawingAPI;
    };
    
    int main(void) {
       CircleShape circle1(1,2,3,new DrawingAPI1());
       CircleShape circle2(5,7,11,new DrawingAPI2());
       circle1.resizeByPercentage(2.5);
       circle2.resizeByPercentage(2.5);
       circle1.draw();
       circle2.draw();
       return 0;
    }
    

Composite lets clients treat individual objects and compositions of objects uniformly. The Composite pattern can represent both the conditions. In this pattern, one can develop tree structures for representing part-whole hierarchies.
    
    
    #include <vector>
    #include <iostream> // std::cout
    #include <memory> // std::auto_ptr
    #include <algorithm> // std::for_each
    #include <functional> // std::mem_fun
    using namespace std;
     
    class Graphic
    {
    public:
      virtual void print() const = 0;
      virtual ~Graphic() {}
    };
     
    class Ellipse : public Graphic
    {
    public:
      void print() const {
        cout << "Ellipse \n";
      }
    };
     
    class CompositeGraphic : public Graphic
    {
    public:
      void print() const {
        // for each element in graphicList_, call the print member function
        for_each(graphicList_.begin(), graphicList_.end(), mem_fun(&Graphic::print));
      }
     
      void add(Graphic *aGraphic) {
        graphicList_.push_back(aGraphic);
      }
     
    private:
      vector<Graphic*>  graphicList_;
    };
     
    int main()
    {
      // Initialize four ellipses
      const auto_ptr<Ellipse> ellipse1(new Ellipse());
      const auto_ptr<Ellipse> ellipse2(new Ellipse());
      const auto_ptr<Ellipse> ellipse3(new Ellipse());
      const auto_ptr<Ellipse> ellipse4(new Ellipse());
     
      // Initialize three composite graphics
      const auto_ptr<CompositeGraphic> graphic(new CompositeGraphic());
      const auto_ptr<CompositeGraphic> graphic1(new CompositeGraphic());
      const auto_ptr<CompositeGraphic> graphic2(new CompositeGraphic());
     
      // Composes the graphics
      graphic1->add(ellipse1.get());
      graphic1->add(ellipse2.get());
      graphic1->add(ellipse3.get());
     
      graphic2->add(ellipse4.get());
     
      graphic->add(graphic1.get());
      graphic->add(graphic2.get());
     
      // Prints the complete graphic (four times the string "Ellipse")
      graphic->print();
      return 0;
    }
    

The decorator pattern helps to attach additional behavior or responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality. This is also called "Wrapper". If your application does some kind of filtering, then Decorator might be good pattern to consider for the job.
    
    
    #include <string>
    #include <iostream>
    using namespace std;
    
    class Car //Our Abstract base class
    {
            protected:
                    string _str;
            public:
                    Car()
                    {
                            _str = "Unknown Car";
                    }
     
                    virtual string getDescription()
                    {       
                            return _str;
                    }
     
                    virtual double getCost() = 0;
     
                    virtual ~Car()
                    {
                            cout << "~Car()\n";
                    }
    };
     
    class OptionsDecorator : public Car //Decorator Base class
    {
            public:
                    virtual string getDescription() = 0;
     
                    virtual ~OptionsDecorator()
                    {
                            cout<<"~OptionsDecorator()\n";
                    }
    };
     
     
    class CarModel1 : public Car
    {       
            public:
                    CarModel1()
                    {
                            _str = "CarModel1";
                    }
                    virtual double getCost()
                    {
                            return 31000.23;
                    }
     
                    ~CarModel1()
                    {
                            cout<<"~CarModel1()\n";
                    }
    };
     
     
    class Navigation: public OptionsDecorator
    {
                    Car *_b;
            public:
                    Navigation(Car *b)
                    {
                            _b = b;
                    }
                    string getDescription()
                    {
                            return _b->getDescription() + ", Navigation";
                    }
     
                    double getCost()
                    {
                            return 300.56 + _b->getCost();
                    }
                    ~Navigation()
                    {
                            cout << "~Navigation()\n";
                    }
    };
     
    class PremiumSoundSystem: public OptionsDecorator
    {
                    Car *_b;
            public:
                    PremiumSoundSystem(Car *b)
                    {
                            _b = b;
                    }
                    string getDescription()
                    {
                            return _b->getDescription() + ", PremiumSoundSystem";
                    }
     
                    double getCost()
                    {
                            return 0.30 + _b->getCost();
                    }
                    ~PremiumSoundSystem()
                    {
                            cout << "~PremiumSoundSystem()\n";
                    }
    };
     
    class ManualTransmission: public OptionsDecorator
    {
                    Car *_b;
            public:
                    ManualTransmission(Car *b)
                    {
                            _b = b;
                    }
                    string getDescription()
                    {
    		        return _b->getDescription()+ ", ManualTransmission";
                    }
     
                    double getCost()
                    {
                            return 0.30 + _b->getCost();
                    }
                    ~ManualTransmission()
                    {
                            cout << "~ManualTransmission()\n";
                    }
    };
     
        class CarDecoratorExample{
        	public:
            
            void execute()
            {
                //Create our Car that we want to buy
                Car *b = new CarModel1();
    			
                cout << "Base model of " << b->getDescription() << " costs $" << b->getCost() << "\n";  
                
                //Who wants base model lets add some more features
                
                b = new Navigation(b);
                cout << b->getDescription() << " will cost you $" << b->getCost() << "\n";
                b = new PremiumSoundSystem(b);
                b = new ManualTransmission(b);
                cout << b->getDescription() << " will cost you $" << b->getCost() << "\n";
    
               // WARNING! Here we leak the CarModel1, Navigation and PremiumSoundSystem
               // objects! either we delete them explicitly or rewrite the Decorators to take 
               // ownership and delete their Cars when destroyed.
                delete b;  
            }
            
        };
    
    
    int main()
    {
    	CarDecoratorExample b;
    	b.execute();
    	return 0;
    }
    

The output of the program above is:
    
    
    Base model of CarModel1 costs $31000.2
    CarModel1, Navigation will cost you $31300.8
    CarModel1, Navigation, PremiumSoundSystem, ManualTransmission will cost you $31301.4
    ~ManualTransmission()
    ~OptionsDecorator()
    ~Car()
    

Another example:
    
    
    #include <iostream>
    #include <string>
    #include <memory>
    
    class Interface {
    	public:
    		virtual ~Interface() { }
    		virtual void write (std::string&) = 0;
    };
    
    class Core : public Interface {
    	public:
    	   	~Core() {std::cout << "Core destructor called.\n";}
    	   	virtual void write (std::string& text) override {};  // Do nothing.
    };
    
    class Decorator : public Interface {
    	private:
    	   	std::unique_ptr<Interface> interface;
    	public:
    	   	Decorator (std::unique_ptr<Interface> c) {interface = std::move(c);}
    	   	virtual void write (std::string& text) override {interface->write(text);}
    };
    
    class MessengerWithSalutation : public Decorator {
    	private:
    	   	std::string salutation;
    	public:
    	   	MessengerWithSalutation (std::unique_ptr<Interface> c, const std::string& str) : Decorator(std::move(c)), salutation(str) {}
    	   	~MessengerWithSalutation() {std::cout << "Messenger destructor called.\n";}
    	   	virtual void write (std::string& text) override {
    		   	text = salutation + "\n\n" + text;
    		 	Decorator::write(text);
    		}
    };
    
    class MessengerWithValediction : public Decorator {
    	private:
    	   	std::string valediction;
    	public:
    	   	MessengerWithValediction (std::unique_ptr<Interface> c, const std::string& str) : Decorator(std::move(c)), valediction(str) {}
    	   	~MessengerWithValediction() {std::cout << "MessengerWithValediction destructor called.\n";}
    	   	virtual void write (std::string& text) override {
    		 	Decorator::write(text);
    			text += "\n\n" + valediction;
    		}
    };
    
    int main() {
    	{
    		const std::string salutation = "Greetings,",  valediction = "Sincerly, Andy";
    		std::string message1 = "This message is not decorated.",
    			message2 = "This message is decorated with a salutation.",
    			message3 = "This message is decorated with a valediction.",
    			message4 = "This message is decorated with a salutation and a valediction.";
    		std::unique_ptr<Interface> messenger1 = std::make_unique<Core>();
    		std::unique_ptr<Interface> messenger2 = std::make_unique<MessengerWithSalutation> (std::make_unique<Core>(), salutation);
    		std::unique_ptr<Interface> messenger3 = std::make_unique<MessengerWithValediction> (std::make_unique<Core>(), valediction);
    		std::unique_ptr<Interface> messenger4 = std::make_unique<MessengerWithValediction> (std::make_unique<MessengerWithSalutation>
                        (std::make_unique<Core>(), salutation), valediction);
    	
    		messenger1->write(message1);
    		std::cout << message1 << '\n';
    		std::cout << "\n------------------------------\n\n";
    		messenger2->write(message2);
    		std::cout << message2 << '\n';
    		std::cout << "\n------------------------------\n\n";
    		messenger3->write(message3);
    		std::cout << message3 << '\n';
    		std::cout << "\n------------------------------\n\n";
    		messenger4->write(message4);
    		std::cout << message4 << '\n';
    		std::cout << "\n------------------------------\n\n";
    	}
    }
    

The output of the program above is:
    
    
    This message is not decorated.
    
    ------------------------------
    
    Greetings,
    
    This message is decorated with a salutation.
    
    ------------------------------
    
    This message is decorated with a valediction.
    
    Sincerly, Andy
    
    ------------------------------
    
    Greetings,
    
    This message is decorated with a salutation and a valediction.
    
    Sincerly, Andy
    
    ------------------------------
    
    MessengerWithValediction destructor called.
    Messenger destructor called.
    Core destructor called.
    MessengerWithValediction destructor called.
    Core destructor called.
    Messenger destructor called.
    Core destructor called.
    Core destructor called.
    

The Facade Pattern hides the complexities of the system by providing an interface to the client from where the client can access the system on an unified interface. Facade defines a higher-level interface that makes the subsystem easier to use. For instance making one class method perform a complex process by calling several other classes.
    
    
    /*Facade is one of the easiest patterns I think... And this is very simple example. 
    
    Imagine you set up a smart house where everything is on remote. So to turn the lights on you push lights on button - And same for TV,
    AC, Alarm, Music, etc...
    
    When you leave a house you would need to push a 100 buttons to make sure everything is off and are good to go which could be little 
    annoying if you are lazy like me 
    so I defined a Facade for leaving and coming back. (Facade functions represent buttons...) So when I come and leave I just make one 
    call and it takes care of everything...
    
    */
    
    #include <string>
    #include<iostream>
    
    using namespace std;
    
    class Alarm
    {
    public:
    	void alarmOn()
    	{
    		cout<<"Alarm is on and house is secured"<<endl;
    	}
    
    	void alarmOff()
    	{
    		cout<<"Alarm is off and you can go into the house"<<endl;
    	}
    };
    
    class Ac
    {
    public:
    	void acOn()
    	{
    		cout<<"Ac is on"<<endl;
    	}
    
    	void acOff()
    	{
    		cout<<"AC is off"<<endl;
    	}
    };
    
    class Tv
    {
    public:
    	void tvOn()
    	{
    		cout<<"Tv is on"<<endl;
    	}
    
    	void tvOff()
    	{
    		cout<<"TV is off"<<endl;
    	}
    
    
    };
    
    class HouseFacade
    {
    	Alarm alarm;
    	Ac ac;
    	Tv tv;
    
    public:
    	
    	HouseFacade(){}
    
    	void goToWork()
    	{
    		ac.acOff();
    		tv.tvOff();
    		alarm.alarmOn();
    	}
    
    	void comeHome()
    	{
    		alarm.alarmOff();
    		ac.acOn();
    		tv.tvOn();
    	}
    
    };
    
       int main()
       {
         HouseFacade hf;
    
         //Rather than calling 100 different on and off functions thanks to facade I only have 2 functions...
         hf.goToWork();
         hf.comeHome();
       }
    

The output of the program above is:
    
    
    AC is off
    TV is off
    Alarm is on and house is secured
    Alarm is off and you can go into the house
    Ac is on
    Tv is on
    

The pattern for saving memory (basically) by sharing properties of objects. Imagine a huge amount of similar objects which all have most of their properties the same. It's natural to move these properties out of these objects to some external data structure and provide each object with the link to that data structure.
    
    
    #include <iostream>
    #include <string>
    #include <vector>
    
    #define NUMBER_OF_SAME_TYPE_CHARS 3;
    
    /* Actual flyweight objects class (declaration) */
    class FlyweightCharacter;
    
    /*
    	FlyweightCharacterAbstractBuilder is a class holding the properties which are shared by
    	many objects. So instead of keeping these properties in those objects we keep them externally, making
    	objects flyweight. See more details in the comments of main function.
    */
    class FlyweightCharacterAbstractBuilder {
    	FlyweightCharacterAbstractBuilder() {}
    	~FlyweightCharacterAbstractBuilder() {}
    public:
    	static std::vector<float> fontSizes; // lets imagine that sizes be may of floating point type
    	static std::vector<std::string> fontNames; // font name may be of variable length (lets take 6 bytes is average)
    
    	static void setFontsAndNames();
    	static FlyweightCharacter createFlyweightCharacter(unsigned short fontSizeIndex,
    		unsigned short fontNameIndex,
    		unsigned short positionInStream);
    };
    
    std::vector<float> FlyweightCharacterAbstractBuilder::fontSizes(3);
    std::vector<std::string> FlyweightCharacterAbstractBuilder::fontNames(3);
    void FlyweightCharacterAbstractBuilder::setFontsAndNames() {
    	fontSizes[0] = 1.0;
    	fontSizes[1] = 1.5;
    	fontSizes[2] = 2.0;
    
    	fontNames[0] = "first_font";
    	fontNames[1] = "second_font";
    	fontNames[2] = "third_font";
    }
    
    class FlyweightCharacter {
    	unsigned short fontSizeIndex; // index instead of actual font size
    	unsigned short fontNameIndex; // index instead of font name
    
    	unsigned positionInStream;
    
    public:
    
    	FlyweightCharacter(unsigned short fontSizeIndex, unsigned short fontNameIndex, unsigned short positionInStream):
    		fontSizeIndex(fontSizeIndex), fontNameIndex(fontNameIndex), positionInStream(positionInStream) {}
    	void print() {
    		std::cout << "Font Size: " << FlyweightCharacterAbstractBuilder::fontSizes[fontSizeIndex]
    			<< ", font Name: " << FlyweightCharacterAbstractBuilder::fontNames[fontNameIndex]
    			<< ", character stream position: " << positionInStream << std::endl;
    	}
    	~FlyweightCharacter() {}
    };
    
    FlyweightCharacter FlyweightCharacterAbstractBuilder::createFlyweightCharacter(unsigned short fontSizeIndex, unsigned short fontNameIndex, unsigned short positionInStream) {
    	FlyweightCharacter fc(fontSizeIndex, fontNameIndex, positionInStream);
    
    	return fc;
    }
    
    int main(int argc, char** argv) {
    	std::vector<FlyweightCharacter> chars;
    
    	FlyweightCharacterAbstractBuilder::setFontsAndNames();
    	unsigned short limit = NUMBER_OF_SAME_TYPE_CHARS;
    
    	for (unsigned short i = 0; i < limit; i++) {
    		chars.push_back(FlyweightCharacterAbstractBuilder::createFlyweightCharacter(0, 0, i));
    		chars.push_back(FlyweightCharacterAbstractBuilder::createFlyweightCharacter(1, 1, i + 1 * limit));
    		chars.push_back(FlyweightCharacterAbstractBuilder::createFlyweightCharacter(2, 2, i + 2 * limit));
    	}
    	/*
    		Each char stores links to it's fontName and fontSize so what we get is:
    
    		each object instead of allocating 6 bytes (convention above) for string
    		and 4 bytes for float allocates 2 bytes for fontNameIndex and fontSizeIndex.
    
    		That means for each char we save 6 + 4 - 2 - 2 = 6 bytes.
    		Now imagine we have NUMBER_OF_SAME_TYPE_CHARS = 1000 i.e. with our code
    		we will have 3 groups of chars whith 1000 chars in each group which will save us
    
    		3 * 1000 * 6 - (3 * 6 + 3 * 4) = 17970 saved bytes.
    
    		3 * 6 + 3 * 4 is a number of bytes allocated by FlyweightCharacterAbstractBuilder.
    
    		So the idea of the pattern is to move properties shared by many objects to some
    		external container. The objects in that case don't store the data themselves they
    		store only links to the data which saves memory and make the objects lighter.
    		The data size of properties stored externally may be significant which will save REALLY
    		huge ammount of memory and will make each object super light in comparisson to it's counterpart.
    		That's where the name of the pattern comes from: flyweight (i.e. very light).
    	*/
    	for (unsigned short i = 0; i < chars.size(); i++) {
    		chars[i].print();
    	}
    
    	std::cin.get(); return 0;
    }
    

The Proxy Pattern will provide an object a surrogate or placeholder for another object to control access to it. It is used when you need to represent a complex object with a simpler one. If creation of an object is expensive, it can be postponed until the very need arises and meanwhile a simpler object can serve as a placeholder. This placeholder object is called the "Proxy" for the complex object.

This technique is known more widely as a mixin. Mixins are described in the literature to be a powerful tool for expressing abstractions[_[citation needed](https://en.m.wikibooks.org/wiki/Wikibooks:OR)_].

Interface-based programming is closely related with Modular Programming and Object-Oriented Programming, it defines the application as a collection of inter-coupled modules (interconnected and which plug into each other via interface). Modules can be unplugged, replaced, or upgraded, without the need of compromising the contents of other modules.

The total system complexity is greatly reduced. Interface Based Programming adds more to modular Programming in that it insists that Interfaces are to be added to these modules. The entire system is thus viewed as Components and the interfaces that helps them to co-act.

Interface-based Programming increases the _modularity_ of the application and hence its maintainability at a later development cycles, especially when each module must be developed by different teams. It is a well-known methodology that has been around for a long time and it is a core technology behind frameworks such as CORBA.

This is particularly convenient when third parties develop additional components for the established system. They just have to develop components that satisfy the interface specified by the parent application vendor.

Thus the publisher of the interfaces assures that he will not change the interface and the subscriber agrees to implement the interface as whole without any deviation. An interface is therefore said to be a _Contractual agreement_ and the [programming paradigm](//en.wikipedia.org/wiki/programming_paradigm) based on this is termed as "interface based programming".

Chain of Responsibility pattern has the intent to avoid coupling the sender of a request to its receiver by giving more than one object a chance to handle the request. Chains the receiving objects and passes the requests along the chain until an object handles it.

Command pattern is an Object behavioral pattern that decouples sender and receiver by encapsulating a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undo-able operations. It can also be thought as an object oriented equivalent of call back method.

Call Back: It is a function that is registered to be called at later point of time based on user actions.
    
    
    #include <iostream>
    
    using namespace std;
    
    /*the Command interface*/
    class Command 
    {
    public:
    	virtual void execute()=0;
    };
    
    /*Receiver class*/
    class Light {
    
    public:
    	Light() {  }
    
    	void turnOn() 
    	{
    		cout << "The light is on" << endl;
    	}
    
    	void turnOff() 
    	{
    		cout << "The light is off" << endl;
    	}
    };
    
    /*the Command for turning on the light*/
    class FlipUpCommand: public Command 
    {
    public:
    
    	FlipUpCommand(Light& light):theLight(light)
    	{
    
    	}
    
    	virtual void execute()
    	{
    		theLight.turnOn();
    	}
    
    private:
    	Light& theLight;
    };
    
    /*the Command for turning off the light*/
    class FlipDownCommand: public Command
    {
    public:   
    	FlipDownCommand(Light& light) :theLight(light)
    	{
    
    	}
    	virtual void execute() 
    	{
    		theLight.turnOff();
    	}
    private:
    	Light& theLight;
    };
    
    class Switch {
    public:
    	Switch(Command& flipUpCmd, Command& flipDownCmd)
    	:flipUpCommand(flipUpCmd),flipDownCommand(flipDownCmd)
    	{
    
    	}
    
    	void flipUp()
    	{
    		flipUpCommand.execute();
    	}
    
    	void flipDown()
    	{
    		flipDownCommand.execute();
    	}
    
    private:
    	Command& flipUpCommand;
    	Command& flipDownCommand;
    };
    
     
    /*The test class or client*/
    int main() 
    {
    	Light lamp;
    	FlipUpCommand switchUp(lamp);
    	FlipDownCommand switchDown(lamp);
    
    	Switch s(switchUp, switchDown);
    	s.flipUp();
    	s.flipDown();
    }
    

Given a language, define a representation for its grammar along with an interpreter that uses the representation to interpret sentences in the language.
    
    
    #include <iostream>
    #include <string>
    #include <map>
    #include <list>
    
    namespace wikibooks_design_patterns
    {
    
    //	based on the Java sample around here
    
    typedef std::string String;
    struct Expression;
    typedef std::map<String,Expression*> Map;
    typedef std::list<Expression*> Stack;
    
    struct Expression {
        virtual int interpret(Map variables) = 0;
    	virtual ~Expression() {}
    };
     
    class Number : public Expression {
    private:
    	int number;
    public: 
    	Number(int number)       { this->number = number; }
    	int interpret(Map variables)  { return number; }
    };
     
    class Plus : public Expression {
        Expression* leftOperand;
        Expression* rightOperand;
    public: 
    
        Plus(Expression* left, Expression* right) { 
            leftOperand = left; 
            rightOperand = right;
        }
        ~Plus(){ 
    	delete leftOperand;
    	delete rightOperand;
        }
     
        int interpret(Map variables)  { 
            return leftOperand->interpret(variables) + rightOperand->interpret(variables);
        }
    };
     
    class Minus : public Expression {
        Expression* leftOperand;
        Expression* rightOperand;
    public: 
        Minus(Expression* left, Expression* right) { 
            leftOperand = left; 
            rightOperand = right;
        }
        ~Minus(){ 
    	delete leftOperand;
    	delete rightOperand;
        }
     
        int interpret(Map variables)  { 
            return leftOperand->interpret(variables) - rightOperand->interpret(variables);
        }
    };
     
    class Variable : public Expression {
        String name;
    public: 
    	Variable(String name)       { this->name = name; }
        int interpret(Map variables)  { 
            if(variables.end() == variables.find(name)) return 0;
            return variables[name]->interpret(variables); 
        }
    };
    
    //	While the interpreter pattern does not address parsing, a parser is provided for completeness.
     
    class Evaluator : public Expression {
        Expression* syntaxTree;
     
    public:
    	Evaluator(String expression){
            Stack expressionStack;
    
    	size_t last = 0;
    	for (size_t next = 0; String::npos != last; last = (String::npos == next) ? next : (1+next)) {
    	    next = expression.find(' ', last);
    	    String token( expression.substr(last, (String::npos == next) ? (expression.length()-last) : (next-last)));
    
                if  (token == "+") {
    		Expression* right = expressionStack.back(); expressionStack.pop_back();
                    Expression* left = expressionStack.back(); expressionStack.pop_back();
                    Expression* subExpression = new Plus(right, left);
                    expressionStack.push_back( subExpression );
                }
                else if (token == "-") {
                    // it's necessary remove first the right operand from the stack
                    Expression* right = expressionStack.back(); expressionStack.pop_back();
                    // ..and after the left one
                    Expression* left = expressionStack.back(); expressionStack.pop_back();
                    Expression* subExpression = new Minus(left, right);
                    expressionStack.push_back( subExpression );
                }
                else                        
                    expressionStack.push_back( new Variable(token) );
            }
    
            syntaxTree = expressionStack.back(); expressionStack.pop_back();
        }
    
         ~Evaluator() {
    	delete syntaxTree;
         }
     
        int interpret(Map context) {
            return syntaxTree->interpret(context);
        }
    };
    
    }
    
    void main()
    {
    	using namespace wikibooks_design_patterns;
    
    	Evaluator sentence("w x z - +");
    
    	static
    	const int sequences[][3] = {
    		{5, 10, 42}, {1, 3, 2}, {7, 9, -5},
    	};
    	for (size_t i = 0; sizeof(sequences)/sizeof(sequences[0]) > i; ++i) {
    		Map variables;
    		variables["w"] = new Number(sequences[i][0]);
    		variables["x"] = new Number(sequences[i][1]);
    		variables["z"] = new Number(sequences[i][2]);
    		int result = sentence.interpret(variables);
    		for (Map::iterator it = variables.begin(); variables.end() != it; ++it) delete it->second;
        
    		std::cout<<"Interpreter result: "<<result<<std::endl;
    	}
    }
    

The 'iterator' design pattern is used liberally within the STL for traversal of various containers. The full understanding of this will liberate a developer to create highly reusable and easily understandable[_[citation needed](https://en.m.wikibooks.org/wiki/Wikibooks:OR)_] data containers.

The basic idea of the iterator is that it permits the traversal of a container (like a pointer moving across an array). However, to get to the next element of a container, you need not know anything about how the container is constructed. This is the iterators job. By simply using the member functions provided by the iterator, you can move, in the intended order of the container, from the first element to the last element.

Let us start by considering a traditional single dimensional array with a pointer moving from the start to the end. This example assumes knowledge of pointer arithmetic. Note that the use of "it" or "itr," henceforth, is a short version of "iterator."
    
    
     const int ARRAY_LEN = 42;
     int *myArray = new int[ARRAY_LEN];
     // Set the iterator to point to the first memory location of the array
     int *arrayItr = myArray;
     // Move through each element of the array, setting it equal to its position in the array
     for(int i = 0; i < ARRAY_LEN; ++i)
     {
        // set the value of the current location in the array
        *arrayItr = i;
        // by incrementing the pointer, we move it to the next position in the array.
        // This is easy for a contiguous memory container, since pointer arithmetic 
        // handles the traversal.
        ++arrayItr;
     }
     // Do not be messy, clean up after yourself
     delete[] myArray;
    

This code works very quickly for arrays, but how would we traverse a linked list, when the memory is not contiguous? Consider the implementation of a rudimentary linked list as follows:
    
    
     class IteratorCannotMoveToNext{}; // Error class
     class MyIntLList
     {
     public:
         // The Node class represents a single element in the linked list. 
         // The node has a next node and a previous node, so that the user 
         // may move from one position to the next, or step back a single 
         // position. Notice that the traversal of a linked list is O(N), 
         // as is searching, since the list is not ordered.
         class Node
         {
         public:
             Node():mNextNode(0),mPrevNode(0),mValue(0){}
             Node *mNextNode;
             Node *mPrevNode;
             int mValue;
         };
         MyIntLList():mSize(0) 
         {}
         ~MyIntLList()
         {
             while(!Empty())
                 pop_front();
         } // See expansion for further implementation;
         int Size() const {return mSize;}
         // Add this value to the end of the list
         void push_back(int value)
         {
             Node *newNode = new Node;
             newNode->mValue = value;
             newNode->mPrevNode = mTail;
             mTail->mNextNode = newNode;
             mTail = newNode;
             ++mSize;
         }
         // Remove the value from the beginning of the list
         void pop_front()
         {
             if(Empty())
                 return;
             Node *tmpnode = mHead;
             mHead = mHead->mNextNode;
             delete tmpnode;
             --mSize;
         }
         bool Empty()
         {return mSize == 0;}
     
         // This is where the iterator definition will go, 
         // but lets finish the definition of the list, first
     
     private:
         Node *mHead;
         Node *mTail;
         int mSize;
     };
    

This linked list has non-contiguous memory, and is therefore not a candidate for pointer arithmetic. And we do not want to expose the internals of the list to other developers, forcing them to learn them, and keeping us from changing it.

This is where the iterator comes in. The common interface makes learning the usage of the container easier, and hides the traversal logic from other developers.

Let us examine the code for the iterator, itself.
    
    
         /*
          *  The iterator class knows the internals of the linked list, so that it 
          *  may move from one element to the next. In this implementation, I have 
          *  chosen the classic traversal method of overloading the increment 
          *  operators. More thorough implementations of a bi-directional linked 
          *  list would include decrement operators so that the iterator may move 
          *  in the opposite direction.
          */
         class Iterator
         {
         public:
             Iterator(Node *position):mCurrNode(position){}
             // Prefix increment
             const Iterator &operator++()
             {
                 if(mCurrNode == 0 || mCurrNode->mNextNode == 0)
                     throw IteratorCannotMoveToNext();e
                 mCurrNode = mCurrNode->mNextNode;
                 return *this;
             }
             // Postfix increment
             Iterator operator++(int)
             {
                 Iterator tempItr = *this;
                 ++(*this);
                 return tempItr;
             }
             // Dereferencing operator returns the current node, which should then 
             // be dereferenced for the int. TODO: Check syntax for overloading 
             // dereferencing operator
             Node * operator*()
             {return mCurrNode;}
             // TODO: implement arrow operator and clean up example usage following
         private:
             Node *mCurrNode;
         };
         // The following two functions make it possible to create 
         // iterators for an instance of this class.
         // First position for iterators should be the first element in the container.
         Iterator Begin(){return Iterator(mHead);}
         // Final position for iterators should be one past the last element in the container.
         Iterator End(){return Iterator(0);}
    

With this implementation, it is now possible, without knowledge of the size of the container or how its data is organized, to move through each element in order, manipulating or simply accessing the data. This is done through the accessors in the MyIntLList class, Begin() and End().
    
    
     // Create a list
     MyIntLList myList;
     // Add some items to the list
     for(int i = 0; i < 10; ++i)
         myList.push_back(i);
     // Move through the list, adding 42 to each item.
     for(MyIntLList::Iterator it = myList.Begin(); it != myList.End(); ++it)
         (*it)->mValue += 42;
    

  * Discussion of iterators in the STL, and the usefulness of iterators within the algorithms library.
  * Iterators best practices
  * Warnings on creation of and usage of
  * When use of operator[] is better and simplifies understanding
  * Cautions about the impact of templates on generated code size (this could make for a good student research paper)

The following program gives the implementation of an iterator design pattern with a generic template:
    
    
    /************************************************************************/
    /* Iterator.h                                                           */
    /************************************************************************/
    #ifndef MY_ITERATOR_HEADER
    #define MY_ITERATOR_HEADER
    
    #include <iterator>
    #include <vector>
    #include <set>
    
    //////////////////////////////////////////////////////////////////////////
    template<class T, class U>
    class Iterator
    {
    public:
    	typedef typename std::vector<T>::iterator iter_type;
    	Iterator(U *pData):m_pData(pData){
    		m_it = m_pData->m_data.begin();
    	}
    
    	void first()
    	{
    		m_it = m_pData->m_data.begin();
    	}
    
    	void next()
    	{
    		m_it++;
    	}
    
    	bool isDone()
    	{
    		return (m_it == m_pData->m_data.end());
    	}
    
    	iter_type current()
    	{
    		return m_it;
    	}
    private:
    	U *m_pData;
    	iter_type m_it;
    };
    
    template<class T, class U, class A>
    class setIterator
    {
    public:
    	typedef typename std::set<T,U>::iterator iter_type;
    	
    	setIterator(A *pData):m_pData(pData)
    	{
    		m_it = m_pData->m_data.begin();
    	}
    
    	void first()
    	{
    		m_it = m_pData->m_data.begin();
    	}
    
    	void next()
    	{
    		m_it++;
    	}
    
    	bool isDone()
    	{
    		return (m_it == m_pData->m_data.end());
    	}
    
    	iter_type current()
    	{
    		return m_it;
    	}
    
    private:
    	A			*m_pData;		
    	iter_type		m_it;
    };
    #endif
    
    
    
    /************************************************************************/
    /* Aggregate.h                                                          */
    /************************************************************************/
    #ifndef MY_DATACOLLECTION_HEADER
    #define MY_DATACOLLECTION_HEADER
    #include "Iterator.h"
    
    template <class T>
    class aggregate
    {
    	friend class Iterator<T, aggregate>;
    public:
    	void add(T a)
    	{
    		m_data.push_back(a);
    	}
    
    	Iterator<T, aggregate> *create_iterator()
    	{
    		return new Iterator<T, aggregate>(this);
    	}
    	
    
    private:
    	std::vector<T> m_data;
    };
    template <class T, class U>
    class aggregateSet
    {
    	friend class setIterator<T, U, aggregateSet>;
    public:
    	void add(T a)
    	{
    		m_data.insert(a);
    	}
    
    	setIterator<T, U, aggregateSet> *create_iterator()
    	{
    		return new setIterator<T,U,aggregateSet>(this);
    	}
    
    	void Print()
    	{
    		copy(m_data.begin(), m_data.end(), std::ostream_iterator<T>(std::cout, "\n"));
    	}
    
    private:
    	std::set<T,U> m_data;
    };
    
    #endif
    
    
    
    /************************************************************************/
    /* Iterator Test.cpp                                                    */
    /************************************************************************/
    #include <iostream>
    #include <string>
    #include "Aggregate.h"
    using namespace std;
    
    class Money
    {
    public:
    	Money(int a = 0): m_data(a) {}
    
    	void SetMoney(int a)
    	{
    		m_data = a;
    	}
    
    	int GetMoney()
    	{
    		return m_data;
    	}
    	
    private:
    	int m_data;
    };
    
    class Name
    {
    public:
    	Name(string name): m_name(name) {}
    
    	const string &GetName() const
    	{
    		return m_name;
    	}
    
    	friend ostream &operator<<(ostream& out, Name name)
    	{
    		out << name.GetName();
    		return out;
    	}
    
    private:
    	string m_name;
    };
    
    struct NameLess
    {
    	bool operator()(const Name &lhs, const Name &rhs) const
    	{
    		return (lhs.GetName() < rhs.GetName());
    	}
    };
    
    int main()
    {
    	//sample 1
    	cout << "________________Iterator with int______________________________________" << endl;
    	aggregate<int> agg;
    	
    	for (int i = 0; i < 10; i++)
    		agg.add(i);
    
    	Iterator< int,aggregate<int> > *it = agg.create_iterator();
    	for(it->first(); !it->isDone(); it->next())
    		cout << *it->current() << endl;	
    
    	//sample 2
    	aggregate<Money> agg2;
    	Money a(100), b(1000), c(10000);
    	agg2.add(a);
    	agg2.add(b);
    	agg2.add(c);
    
    	cout << "________________Iterator with Class Money______________________________" << endl;
    	Iterator<Money, aggregate<Money> > *it2 = agg2.create_iterator();
    	for (it2->first(); !it2->isDone(); it2->next())
    		cout << it2->current()->GetMoney() << endl;
    
    	//sample 3
    	cout << "________________Set Iterator with Class Name______________________________" << endl;
    	
    	aggregateSet<Name, NameLess> aset;
    	aset.add(Name("Qmt"));
    	aset.add(Name("Bmt"));
    	aset.add(Name("Cmt"));
    	aset.add(Name("Amt"));
    
    	setIterator<Name, NameLess, aggregateSet<Name, NameLess> > *it3 = aset.create_iterator();
    	for (it3->first(); !it3->isDone(); it3->next())
    		cout << (*it3->current()) << endl;
    }
    

Console output:
    
    
    ________________Iterator with int______________________________________
    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    ________________Iterator with Class Money______________________________
    100
    1000
    10000
    ________________Set Iterator with Class Name___________________________
    Amt
    Bmt
    Cmt
    Qmt
    

Define an object that encapsulates how a set of objects interact. Mediator promotes loose coupling by keeping objects from referring to each other explicitly, and it lets you vary their interaction independently.
    
    
    #include <iostream>
    #include <string>
    #include <list>
    
    class MediatorInterface;
    
    class ColleagueInterface {
    		std::string name;
    	public:
    		ColleagueInterface (const std::string& newName) : name (newName) {}
    		std::string getName() const {return name;}
    		virtual void sendMessage (const MediatorInterface&, const std::string&) const = 0;
    		virtual void receiveMessage (const ColleagueInterface*, const std::string&) const = 0;
    };
    
    class Colleague : public ColleagueInterface {
    	public:
    		using ColleagueInterface::ColleagueInterface;
    		virtual void sendMessage (const MediatorInterface&, const std::string&) const override;
    	private:
    		virtual void receiveMessage (const ColleagueInterface*, const std::string&) const override;
    };
    
    class MediatorInterface {
        private:
    		std::list<ColleagueInterface*> colleagueList;
        public:
        	const std::list<ColleagueInterface*>& getColleagueList() const {return colleagueList;}
    		virtual void distributeMessage (const ColleagueInterface*, const std::string&) const = 0;
    		virtual void registerColleague (ColleagueInterface* colleague) {colleagueList.emplace_back (colleague);}
    };
    
    class Mediator : public MediatorInterface {
        virtual void distributeMessage (const ColleagueInterface*, const std::string&) const override;
    };
    
    void Colleague::sendMessage (const MediatorInterface& mediator, const std::string& message) const {
    	mediator.distributeMessage (this, message);
    }
    
    void Colleague::receiveMessage (const ColleagueInterface* sender, const std::string& message) const {
     	std::cout << getName() << " received the message from " << sender->getName() << ": " << message << std::endl;			
    }
    
    void Mediator::distributeMessage (const ColleagueInterface* sender, const std::string& message) const {
    	for (const ColleagueInterface* x : getColleagueList())
    		if (x != sender)  // Do not send the message back to the sender
    			x->receiveMessage (sender, message);
    }
     
    int main() {
    	Colleague *bob = new Colleague ("Bob"),  *sam = new Colleague ("Sam"),  *frank = new Colleague ("Frank"),  *tom = new Colleague ("Tom");
    	Colleague* staff[] = {bob, sam, frank, tom};
    	Mediator mediatorStaff, mediatorSamsBuddies;
    	for (Colleague* x : staff)
    		mediatorStaff.registerColleague(x);
    	bob->sendMessage (mediatorStaff, "I'm quitting this job!");
    	mediatorSamsBuddies.registerColleague (frank);  mediatorSamsBuddies.registerColleague (tom);  // Sam's buddies only
    	sam->sendMessage (mediatorSamsBuddies, "Hooray!  He's gone!  Let's go for a drink, guys!");	
    	return 0;
    }
    

Without violating encapsulation the Memento Pattern will capture and externalize an object's internal state so that the object can be restored to this state later. Though the [Gang of Four](//en.wikipedia.org/wiki/Design_Patterns) uses friend as a way to implement this pattern it is not the best design[_[citation needed](https://en.m.wikibooks.org/wiki/Wikibooks:OR)_]. It can also be implemented using [PIMPL (pointer to implementation or opaque pointer)](//en.wikipedia.org/wiki/Opaque_pointer). Best Use case is 'Undo-Redo' in an editor.

The Originator (the object to be saved) creates a snap-shot of itself as a Memento object, and passes that reference to the Caretaker object. The Caretaker object keeps the Memento until such a time as the Originator may want to revert to a previous state as recorded in the Memento object.
    
    
    #include <iostream>
    #include <string>
    #include <sstream>
    #include <vector>
    
    const std::string NAME = "Object";
    
    template <typename T>
    std::string toString (const T& t) {
    	std::stringstream ss;
    	ss << t;
    	return ss.str();
    }
    
    class Memento;
    
    class Object {
      	private:
        	    int value;
        	    std::string name;
        	    double decimal;  // and suppose there are loads of other data members
      	public:
    	    Object (int newValue): value (newValue), name (NAME + toString (value)), decimal ((float)value / 100) {}
    	    void doubleValue() {value = 2 * value;  name = NAME + toString (value);  decimal = (float)value / 100;}
    	    void increaseByOne() {value++;  name = NAME + toString (value);  decimal = (float)value / 100;}
    	    int getValue() const {return value;}
    	    std::string getName() const {return name;}
    	    double getDecimal() const {return decimal;}
    	    Memento* createMemento() const;
    	    void reinstateMemento (Memento* mem);
    };
    
    class Memento {
      	private:
     	    Object object;
      	public:
        	    Memento (const Object& obj):  object (obj) {}
        	    Object snapshot() const {return object;}  // want a snapshot of Object itself because of its many data members
    };
    
    Memento* Object::createMemento() const {
    	return new Memento (*this);
    }
    
    void Object::reinstateMemento (Memento* mem) {
    	*this = mem->snapshot();
    }
    
    class Command {
      	private:
    	    typedef void (Object::*Action)();
    	    Object* receiver;
    	    Action action;
    	    static std::vector<Command*> commandList;
    	    static std::vector<Memento*> mementoList;
    	    static int numCommands;
    	    static int maxCommands;
      	public:
    	    Command (Object *newReceiver, Action newAction): receiver (newReceiver), action (newAction) {}
    	    virtual void execute() {
    	    	if (mementoList.size() < numCommands + 1)
    	    		mementoList.resize (numCommands + 1);
    	        mementoList[numCommands] = receiver->createMemento();  // saves the last value
    	    	if (commandList.size() < numCommands + 1)
    	    		commandList.resize (numCommands + 1);
    	        commandList[numCommands] = this;  // saves the last command
    	        if (numCommands > maxCommands)
    	          	maxCommands = numCommands;
    	        numCommands++;
    	        (receiver->*action)();
    	    }
    	    static void undo() {
    	        if (numCommands == 0)
    	        {
    	            std::cout << "There is nothing to undo at this point." << std::endl;
    	            return;
    	        }
    	        commandList[numCommands - 1]->receiver->reinstateMemento (mementoList[numCommands - 1]);
    	        numCommands--;
    	    }
    	    void static redo() {
    	        if (numCommands > maxCommands)
    	        {
    	            std::cout << "There is nothing to redo at this point." << std::endl;
    	            return ;
    	        }
    	        Command* commandRedo = commandList[numCommands];
    	        (commandRedo->receiver->*(commandRedo->action))();
    	        numCommands++;
    	    }
    };
    
    std::vector<Command*> Command::commandList;
    std::vector<Memento*> Command::mementoList;
    int Command::numCommands = 0;
    int Command::maxCommands = 0;
    
    int main()
    {
    	int i;
    	std::cout << "Please enter an integer: ";
    	std::cin >> i;
    	Object *object = new Object(i);
    	
    	Command *commands[3];
    	commands[1] = new Command(object, &Object::doubleValue);
    	commands[2] = new Command(object, &Object::increaseByOne);
    	
    	std::cout << "0.Exit,  1.Double,  2.Increase by one,  3.Undo,  4.Redo: ";
    	std::cin >> i;
    	
    	while (i != 0)
    	{
    		if (i == 3)
    		  	Command::undo();
    		else if (i == 4)
    		  	Command::redo();
    		else if (i > 0 && i <= 2)
    		  	commands[i]->execute();
    		else
    		{
    			std::cout << "Enter a proper choice: ";
    			std::cin >> i;
    			continue;
    		}
    		std::cout << "   " << object->getValue() << "  " << object->getName() << "  " << object->getDecimal() << std::endl;
    		std::cout << "0.Exit,  1.Double,  2.Increase by one,  3.Undo,  4.Redo: ";
    		std::cin >> i;
    	}
    }
    

The Observer Pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

    In one place or many places in the application we need to be aware about a system event or an application state change. We'd like to have a standard way of subscribing to listening for system events and a standard way of notifying the interested parties. The notification should be automated after an interested party subscribed to the system event or application state change. There also should be a way to unsubscribe.

    Observers and observables probably should be represented by objects. The observer objects will be notified by the observable objects.

    After subscribing the listening objects will be notified by a way of method call.
    
    
    #include <list>
    #include <algorithm>
    #include <iostream>
    using namespace std;
    
    // The Abstract Observer
    class ObserverBoardInterface
    {
    public:
        virtual void update(float a,float b,float c) = 0;
    };
    
    // Abstract Interface for Displays
    class DisplayBoardInterface
    {
    public:
        virtual void show() = 0;
    };
    
    // The Abstract Subject
    class WeatherDataInterface
    {
    public:
        virtual void registerOb(ObserverBoardInterface* ob) = 0;
        virtual void removeOb(ObserverBoardInterface* ob) = 0;
        virtual void notifyOb() = 0;
    };
    
    // The Concrete Subject
    class ParaWeatherData: public WeatherDataInterface
    {
    public:
        void SensorDataChange(float a,float b,float c)
        {
            m_humidity = a;
            m_temperature = b;
            m_pressure = c;
            notifyOb();
        }
    
        void registerOb(ObserverBoardInterface* ob)
        {
            m_obs.push_back(ob);
        }
    
        void removeOb(ObserverBoardInterface* ob)
        {
            m_obs.remove(ob);
        }
    protected:
        void notifyOb()
        {
            list<ObserverBoardInterface*>::iterator pos = m_obs.begin();
            while (pos != m_obs.end())
            {
                ((ObserverBoardInterface* )(*pos))->update(m_humidity,m_temperature,m_pressure);
                (dynamic_cast<DisplayBoardInterface*>(*pos))->show();
                ++pos;
            }
        }
    
    private:
        float        m_humidity;
        float        m_temperature;
        float        m_pressure;
        list<ObserverBoardInterface* > m_obs;
    };
    
    // A Concrete Observer
    class CurrentConditionBoard : public ObserverBoardInterface, public DisplayBoardInterface
    {
    public:
        CurrentConditionBoard(ParaWeatherData& a):m_data(a)
        {
            m_data.registerOb(this);
        }
        void show()
        {
            cout<<"_____CurrentConditionBoard_____"<<endl;
            cout<<"humidity: "<<m_h<<endl;
            cout<<"temperature: "<<m_t<<endl;
            cout<<"pressure: "<<m_p<<endl;
            cout<<"_______________________________"<<endl;
        }
    
        void update(float h, float t, float p)
        {
            m_h = h;
            m_t = t;
            m_p = p;
        }
    
    private:
        float m_h;
        float m_t;
        float m_p;
        ParaWeatherData& m_data;
    };
    
    // A Concrete Observer
    class StatisticBoard : public ObserverBoardInterface, public DisplayBoardInterface
    {
    public:
        StatisticBoard(ParaWeatherData& a):m_maxt(-1000),m_mint(1000),m_avet(0),m_count(0),m_data(a)
        {
            m_data.registerOb(this);
        }
    
        void show()
        {
            cout<<"________StatisticBoard_________"<<endl;
            cout<<"lowest  temperature: "<<m_mint<<endl;
            cout<<"highest temperature: "<<m_maxt<<endl;
            cout<<"average temperature: "<<m_avet<<endl;
            cout<<"_______________________________"<<endl;
        }
    
        void update(float h, float t, float p)
        {
            ++m_count;
            if (t>m_maxt)
            {
                m_maxt = t;
            }
            if (t<m_mint)
            {
                m_mint = t;
            }
            m_avet = (m_avet * (m_count-1) + t)/m_count;
        }
    
    private:
        float m_maxt;
        float  m_mint;
        float m_avet;
        int m_count;
        ParaWeatherData& m_data;
    };
    
    
    int main(int argc, char *argv[])
    {
       
        ParaWeatherData * wdata = new ParaWeatherData;
        CurrentConditionBoard* currentB = new CurrentConditionBoard(*wdata);
        StatisticBoard* statisticB = new StatisticBoard(*wdata);
    
        wdata->SensorDataChange(10.2, 28.2, 1001);
        wdata->SensorDataChange(12, 30.12, 1003);
        wdata->SensorDataChange(10.2, 26, 806);
        wdata->SensorDataChange(10.3, 35.9, 900);
    
        wdata->removeOb(currentB);
    
        wdata->SensorDataChange(100, 40, 1900);  
        
        delete statisticB;
        delete currentB;
        delete wdata;
    
        return 0;
    }
    

The State Pattern allows an object to alter its behavior when its internal state changes. The object will appear as having changed its class.
    
    
    #include <iostream>
    #include <string>
    #include <cstdlib>
    #include <ctime>
    #include <memory>
    
    enum Input {DUCK_DOWN, STAND_UP, JUMP, DIVE};
    
    class Fighter;
    class StandingState;  class JumpingState;  class DivingState;
    
    class FighterState {
    	public:
    		static std::shared_ptr<StandingState> standing;
    		static std::shared_ptr<DivingState> diving;
    		virtual ~FighterState() = default;
    		virtual void handleInput (Fighter&, Input) = 0;
    		virtual void update (Fighter&) = 0;
    };
    
    class DuckingState : public FighterState {
    	private:
    		int chargingTime;
    		static const int FullRestTime = 5;
    	public:
    		DuckingState() : chargingTime(0) {}
    		virtual void handleInput (Fighter&, Input) override;
    		virtual void update (Fighter&) override;
    };
    
    class StandingState : public FighterState {
    	public:
    		virtual void handleInput (Fighter&, Input) override;
    		virtual void update (Fighter&) override;
    };
    
    class JumpingState : public FighterState {
    	private:
    		int jumpingHeight;
    	public:
    		JumpingState() {jumpingHeight = std::rand() % 5 + 1;}
    		virtual void handleInput (Fighter&, Input) override;
    		virtual void update (Fighter&) override;
    };
    
    class DivingState : public FighterState {
    	public:
    		virtual void handleInput (Fighter&, Input) override;
    		virtual void update (Fighter&) override;
    };
    
    std::shared_ptr<StandingState> FighterState::standing (new StandingState);
    std::shared_ptr<DivingState> FighterState::diving (new DivingState);
    
    class Fighter {
    	private:
    		std::string name;
    		std::shared_ptr<FighterState> state;
    		int fatigueLevel = std::rand() % 10;
    	public:
    		Fighter (const std::string& newName) : name (newName), state (FighterState::standing) {}
    		std::string getName() const {return name;}
    		int getFatigueLevel() const {return fatigueLevel;}
    		virtual void handleInput (Input input) {state->handleInput (*this, input);}  // delegate input handling to 'state'.
    		void changeState (std::shared_ptr<FighterState> newState) {state = newState;  updateWithNewState();}
    		void standsUp() {std::cout << getName() << " stands up." << std::endl;}
    		void ducksDown() {std::cout << getName() << " ducks down." << std::endl;}
    		void jumps() {std::cout << getName() << " jumps into the air." << std::endl;}
    		void dives() {std::cout << getName() << " makes a dive attack in the middle of the jump!" << std::endl;}
    		void feelsStrong() {std::cout << getName() << " feels strong!" << std::endl;}
    		void changeFatigueLevelBy (int change) {fatigueLevel += change;  std::cout << "fatigueLevel = " << fatigueLevel << std::endl;}
    	private:
    		virtual void updateWithNewState() {state->update(*this);}  // delegate updating to 'state'
    };
    
    void StandingState::handleInput (Fighter& fighter, Input input)  {
    	switch (input) {
    		case STAND_UP:  std::cout << fighter.getName() << " remains standing." << std::endl;  return;
    		case DUCK_DOWN:  fighter.changeState (std::shared_ptr<DuckingState> (new DuckingState));  return fighter.ducksDown();
    		case JUMP:  fighter.jumps();  return fighter.changeState (std::shared_ptr<JumpingState> (new JumpingState));
    		default:  std::cout << "One cannot do that while standing.  " << fighter.getName() << " remains standing by default." << std::endl;
    	}
    }
    
    void StandingState::update (Fighter& fighter) {
    	if (fighter.getFatigueLevel() > 0)
    		fighter.changeFatigueLevelBy(-1);
    }
    
    void DuckingState::handleInput (Fighter& fighter, Input input)  {
    	switch (input) {
    		case STAND_UP:  fighter.changeState (FighterState::standing);  return fighter.standsUp();
    		case DUCK_DOWN:
    			std::cout << fighter.getName() << " remains in ducking position, ";
    			if (chargingTime < FullRestTime) std::cout << "recovering in the meantime." << std::endl;
    			else std::cout << "fully recovered." << std::endl;
    			return update (fighter);
    		default:
    			std::cout << "One cannot do that while ducking.  " << fighter.getName() << " remains in ducking position by default." << std::endl;
    			update (fighter);
    	}
    }
    
    void DuckingState::update (Fighter& fighter) {
    	chargingTime++;
    	std::cout << "Charging time = " << chargingTime << "." << std::endl;
    	if (fighter.getFatigueLevel() > 0)
    		fighter.changeFatigueLevelBy(-1);
    	if (chargingTime >= FullRestTime && fighter.getFatigueLevel() <= 3)
    		fighter.feelsStrong();
    }
    
    void JumpingState::handleInput (Fighter& fighter, Input input)  {
    	switch (input) {
    		case DIVE:  fighter.changeState (FighterState::diving);  return fighter.dives();
    		default:
    			std::cout << "One cannot do that in the middle of a jump.  " << fighter.getName() << " lands from his jump and is now standing again." << std::endl;
    			fighter.changeState (FighterState::standing);
    	}
    }
    
    void JumpingState::update (Fighter& fighter) {
    	std::cout << fighter.getName() << " has jumped " << jumpingHeight << " feet into the air." << std::endl;
    	if (jumpingHeight >= 3)
    		fighter.changeFatigueLevelBy(1);
    }
    
    void DivingState::handleInput (Fighter& fighter, Input)  {
    	std::cout << "Regardless of what the user input is, " << fighter.getName() << " lands from his dive and is now standing again." << std::endl;
    	fighter.changeState (FighterState::standing);
    }
    
    void DivingState::update (Fighter& fighter) {
    	fighter.changeFatigueLevelBy(2);
    }
    
    int main() {
    	std::srand(std::time(nullptr));
    	Fighter rex ("Rex the Fighter"), borg ("Borg the Fighter");
    	std::cout << rex.getName() << " and " << borg.getName() << " are currently standing." << std::endl;
    	int choice;
    	auto chooseAction = [&choice](Fighter& fighter) {
    		std::cout << std::endl << DUCK_DOWN + 1 << ") Duck down  " << STAND_UP + 1 << ") Stand up  " << JUMP + 1
    			<< ") Jump  " << DIVE + 1 << ") Dive in the middle of a jump" << std::endl;
    		std::cout << "Choice for " << fighter.getName() << "? ";
    		std::cin >> choice;
    		const Input input1 = static_cast<Input>(choice - 1);
    		fighter.handleInput (input1);	
    	};
    	while (true) {
    		chooseAction (rex);
    		chooseAction (borg);
    	}
    }
    

Defines a family of algorithms, encapsulates each one, and make them interchangeable. Strategy lets the algorithm vary independently from clients who use it.
    
    
    #include <iostream>
    using namespace std;
    
    class StrategyInterface
    {
        public:
            virtual void execute() const = 0;
    };
    
    class ConcreteStrategyA: public StrategyInterface
    {
        public:
            virtual void execute() const
            {
                cout << "Called ConcreteStrategyA execute method" << endl;
            }
    };
    
    class ConcreteStrategyB: public StrategyInterface
    {
        public:
            virtual void execute() const
            {
                cout << "Called ConcreteStrategyB execute method" << endl;
            }
    };
    
    class ConcreteStrategyC: public StrategyInterface
    {
        public:
            virtual void execute() const
            {
                cout << "Called ConcreteStrategyC execute method" << endl;
            }
    };
    
    class Context
    {
        private:
            StrategyInterface * strategy_;
    
        public:
            explicit Context(StrategyInterface *strategy):strategy_(strategy)
            {
            }
    
            void set_strategy(StrategyInterface *strategy)
            {
                strategy_ = strategy;
            }
    
            void execute() const
            {
                strategy_->execute();
            }
    };
    
    int main(int argc, char *argv[])
    {
        ConcreteStrategyA concreteStrategyA;
        ConcreteStrategyB concreteStrategyB;
        ConcreteStrategyC concreteStrategyC;
    
        Context contextA(&concreteStrategyA);
        Context contextB(&concreteStrategyB);
        Context contextC(&concreteStrategyC);
    
        contextA.execute(); // output: "Called ConcreteStrategyA execute method"
        contextB.execute(); // output: "Called ConcreteStrategyB execute method"
        contextC.execute(); // output: "Called ConcreteStrategyC execute method"
        
        contextA.set_strategy(&concreteStrategyB);
        contextA.execute(); // output: "Called ConcreteStrategyB execute method"
        contextA.set_strategy(&concreteStrategyC);
        contextA.execute(); // output: "Called ConcreteStrategyC execute method"
    
        return 0;
    }
    

By defining a skeleton of an algorithm in an operation, deferring some steps to subclasses, the Template Method lets subclasses redefine certain steps of that algorithm without changing the algorithm's structure.
    
    
    #include <ctime>
    #include <assert.h>
    #include <iostream>
    
    namespace wikibooks_design_patterns
    {
    /**
     * An abstract class that is common to several games in
     * which players play against the others, but only one is
     * playing at a given time.
     */
    
    class Game {
    
    public:
       Game(): playersCount(0), movesCount(0), playerWon(-1)
       {
    	srand( (unsigned)time( NULL));
       }
    
    	/* A template method : */
        void playOneGame(const int playersCount = 0) {
    
    	if (playersCount)
    	      this->playersCount = playersCount;
    
            InitializeGame();
    	assert(this->playersCount);
    
            int j = 0;
            while (!endOfGame()) {
                makePlay(j);
                j = (j + 1) % this->playersCount;
    	    if (!j) {
    	        ++movesCount;
    	    }
            }
            printWinner();
        }
    
    protected:
        virtual void initializeGame() = 0;
        virtual void makePlay(int player) = 0;
        virtual bool endOfGame() = 0;
        virtual void printWinner() = 0;
    
    private:
        void InitializeGame()
        {
    	movesCount = 0;
    	playerWon = -1;
    
    	initializeGame();
        }
    
    protected:
        int playersCount;
        int movesCount;
        int playerWon;
    };
     
    //Now we can extend this class in order 
    //to implement actual games:
     
    class Monopoly: public Game {
     
        /* Implementation of necessary concrete methods */
        void initializeGame() {
            // Initialize players
    	playersCount = rand() * 7 / RAND_MAX + 2;
            // Initialize money
        }
        void makePlay(int player) {
            // Process one turn of player
    
    	//	Decide winner
    	if (movesCount < 20)
    	    return;
    	const int chances = (movesCount > 199) ? 199 : movesCount;
    	const int random = MOVES_WIN_CORRECTION * rand() * 200 / RAND_MAX;
    	if (random < chances)
    	    playerWon = player;
        }
        bool endOfGame() {
            // Return true if game is over 
            // according to Monopoly rules
    	return (-1 != playerWon);
        }
        void printWinner() {
    	assert(playerWon >= 0);
    	assert(playerWon < playersCount);
    
            // Display who won
    	std::cout<<"Monopoly, player "<<playerWon<<" won in "<<movesCount<<" moves."<<std::endl;
        }
    
    private:
        enum
        {
            MOVES_WIN_CORRECTION = 20,
        };
    };
     
    class Chess: public Game {
     
        /* Implementation of necessary concrete methods */
        void initializeGame() {
            // Initialize players
    	playersCount = 2;
            // Put the pieces on the board
        }
        void makePlay(int player) {
    	assert(player < playersCount);
    
            // Process a turn for the player
    
    	//	decide winner
    	if (movesCount < 2)
    	    return;
    	const int chances = (movesCount > 99) ? 99 : movesCount;
    	const int random = MOVES_WIN_CORRECTION * rand() * 100 / RAND_MAX;
    	//std::cout<<random<<" : "<<chances<<std::endl;
    	if (random < chances)
    	    playerWon = player;
        }
        bool endOfGame() {
            // Return true if in Checkmate or 
            // Stalemate has been reached
    	return (-1 != playerWon);
        }
        void printWinner() {
    	assert(playerWon >= 0);
    	assert(playerWon < playersCount);
    
            // Display the winning player
    	std::cout<<"Player "<<playerWon<<" won in "<<movesCount<<" moves."<<std::endl;
        }
    
    private:
        enum
        {
    	MOVES_WIN_CORRECTION = 7,
        };
    };
    
    }
    
    int main()
    {
        using namespace wikibooks_design_patterns;
    
        Game* game = NULL;
    
        Chess chess;
        game = &chess;
        for (unsigned i = 0; i < 100; ++i)
    	 game->playOneGame();
    
        Monopoly monopoly;
        game = &monopoly;
        for (unsigned i = 0; i < 100; ++i)
    	game->playOneGame();
    
        return 0;
    }
    

The Visitor Pattern will represent an operation to be performed on the elements of an object structure by letting you define a new operation without changing the classes of the elements on which it operates.
    
    
    #include <string>
    #include <iostream>
    #include <vector>
    
    using namespace std;
     
    class Wheel;
    class Engine;
    class Body;
    class Car;
     
    // interface to all car 'parts'
    struct CarElementVisitor 
    {
      virtual void visit(Wheel& wheel) const = 0;
      virtual void visit(Engine& engine) const = 0;
      virtual void visit(Body& body) const = 0;
     
      virtual void visitCar(Car& car) const = 0;
      virtual ~CarElementVisitor() {};
    };
     
    // interface to one part
    struct CarElement 
    {
      virtual void accept(const CarElementVisitor& visitor) = 0;
      virtual ~CarElement() {}
    };
     
    // wheel element, there are four wheels with unique names
    class Wheel : public CarElement
    {
    public:
      explicit Wheel(const string& name) :
        name_(name)
      {
      }
      const string& getName() const 
      {
        return name_;
      }
      void accept(const CarElementVisitor& visitor)  
      {
        visitor.visit(*this);
      }
    private:
        string name_;
    };
     
    // engine
    class Engine : public CarElement
    {
    public:
      void accept(const CarElementVisitor& visitor) 
      {
        visitor.visit(*this);
      }
    };
     
    // body
    class Body : public CarElement
    {
    public:
      void accept(const CarElementVisitor& visitor) 
      {
        visitor.visit(*this);
      }
    };
     
    // car, all car elements(parts) together
    class Car 
    {
    public:
      vector<CarElement*>& getElements()
      {
        return elements_;
      }
      Car() 
      {
        // assume that neither push_back nor Wheel(const string&) may throw
        elements_.push_back( new Wheel("front left") );
        elements_.push_back( new Wheel("front right") );
        elements_.push_back( new Wheel("back left") );
        elements_.push_back( new Wheel("back right") );
        elements_.push_back( new Body() );
        elements_.push_back( new Engine() );
      }
      ~Car()
      {
        for(vector<CarElement*>::iterator it = elements_.begin(); 
          it != elements_.end(); ++it)
        {
          delete *it;
        }
      }
    private:
      vector<CarElement*> elements_;
    };
     
    // PrintVisitor and DoVisitor show by using a different implementation the Car class is unchanged
    // even though the algorithm is different in PrintVisitor and DoVisitor.
    class CarElementPrintVisitor : public CarElementVisitor 
    {
    public:
      void visit(Wheel& wheel) const
      { 
        cout << "Visiting " << wheel.getName() << " wheel" << endl;
      }
      void visit(Engine& engine) const
      {
        cout << "Visiting engine" << endl;
      }
      void visit(Body& body) const
      {
        cout << "Visiting body" << endl;
      }
      void visitCar(Car& car) const
      {
        cout << endl << "Visiting car" << endl;
        vector<CarElement*>& elems = car.getElements();
        for(vector<CarElement*>::iterator it = elems.begin();
          it != elems.end(); ++it )
        {
          (*it)->accept(*this);	// this issues the callback i.e. to this from the element  
        }
        cout << "Visited car" << endl;
      }
    };
     
    class CarElementDoVisitor : public CarElementVisitor 
    {
    public:
      // these are specific implementations added to the original object without modifying the original struct
      void visit(Wheel& wheel) const
      {
        cout << "Kicking my " << wheel.getName() << " wheel" << endl;
      }
      void visit(Engine& engine) const
      {
        cout << "Starting my engine" << endl;
      }
      void visit(Body& body) const
      {
        cout << "Moving my body" << endl;
      }
      void visitCar(Car& car) const
      {
        cout << endl << "Starting my car" << endl;
        vector<CarElement*>& elems = car.getElements();
        for(vector<CarElement*>::iterator it = elems.begin();
          it != elems.end(); ++it )
        {
          (*it)->accept(*this);	// this issues the callback i.e. to this from the element  
        }
        cout << "Stopped car" << endl;
      }
    };
     
    int main()
    {
      Car car;
      CarElementPrintVisitor printVisitor;
      CarElementDoVisitor doVisitor;
      
      printVisitor.visitCar(car);
      doVisitor.visitCar(car);
    
      return 0;
    }
    

A pattern often used by applications that need the ability to maintain multiple views of the same data. The model-view-controller pattern was until recently[_[citation needed](https://en.m.wikibooks.org/wiki/Wikibooks:OR)_] a very common pattern especially for graphic user interlace programming, it splits the code in 3 pieces. The model, the view, and the controller.

The Model is the actual data representation (for example, Array vs Linked List) or other objects representing a database. The View is an interface to reading the model or a fat client GUI. The Controller provides the interface of changing or modifying the data, and then selecting the "Next Best View" (NBV).

Newcomers will probably see this "MVC" model as wasteful, mainly because you are working with many extra objects at runtime, when it seems like one giant object will do. But the secret to the MVC pattern is not writing the code, but in maintaining it, and allowing people to modify the code without changing much else. Also, keep in mind, that different developers have different strengths and weaknesses, so team building around MVC is easier. Imagine a View Team that is responsible for great views, a Model Team that knows a lot about data, and a Controller Team that see the big picture of application flow, handing requests, working with the model, and selecting the most appropriate next view for that client.

For example: A naive central database can be organized using only a "model", for example, a straight array. However, later on, it may be more applicable to use a linked list. All array accesses will have to be remade into their respective Linked List form (for example, you would change myarray[5] into mylist.at(5) or whatever is equivalent in the language you use).

Well, if we followed the MVC pattern, the central database would be accessed using some sort of a function, for example, myarray.at(5). If we change the model from an array to a linked list, all we have to do is change the view with the model, and the whole program is changed. Keep the interface the same but change the underpinnings of it. This would allow us to make optimizations more freely and quickly than before.

One of the great advantages of the Model-View-Controller Pattern is obviously the ability to reuse the application's logic (which is implemented in the model) when implementing a different view. A good example is found in web development, where a common task is to implement an external API inside of an existing piece of software. If the MVC pattern has cleanly been followed, this only requires modification to the controller, which can have the ability to render different types of views dependent on the content type requested by the user agent.
