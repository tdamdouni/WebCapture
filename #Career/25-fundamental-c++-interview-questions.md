# 25 Fundamental C++ Interview Questions

_Captured: 2017-08-22 at 19:51 from [pangara.com](https://pangara.com/blog/cplusplus-interview-questions/?ref=quuu&utm_content=buffer7b2e1&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![25 Fundamental C++ Interview Questions](https://i2.wp.com/pangara.com/wp-content/uploads/2017/08/Graphic-Opt2-310717.jpg?resize=960%2C540&ssl=1)

Here, we demonstrate **Fundamental C++ interview questions **that are likely to come your way.  This list of questions and answers will be extremely helpful to people looking to stretch their already blossoming careers. It is imperative at any interview to be prepared and present a confident front to the interviewer. Fore warned is fore armed and these likely questions will put you firmly in that camp.

It is imperative that as a programmer you realise the enormous size of C++ as a core language. It is not difficult to fall into one of the common pitfalls; there are many mistakes that are easy to make. 

When **[applying for a job**](https://pangara.com/become-it-freelance-talent/) in this field, you will need to fully understand the language and just how it acts as a tool for creating good products. Common questions are often about binary trees or linked lists. 

These are designed in order that the interviewer can test the applicant on more than one capability at once. When focusing on performance it is important not to ignore theory questions about memory. It is important that applicants fully understand computer architecture, this of course enables better understanding of the need for common idioms.

## **Why Fundamental C++ Interview Questions Are Important**

It is worth remembering that you will be dealing with C++ regardless of whether you are working as a game programmer, an engine developer, a software/tool developer or a graphics programmer. The questions though will vary depending upon which position you are applying for.

![c++ interview questions](https://i2.wp.com/pangara.com/wp-content/uploads/2017/08/math.jpg?resize=499%2C333&ssl=1)

Regardless of the position for which you are applying, a solid mathematics and C++ foundation will be imperative. Graphics programmers will face questions about shaders, graphic concepts and of course 3D mathematics. For engine developers the questions are more likely to lean towards low level knowledge. 

You will need to demonstrate that you can program optimally whilst also focusing on the target hardware. If your area of expertise is as a game programmer, then you will be questioned about common idioms and algorithms. 

It is more important that the candidate and the job are a good fit. If only part of the job description fits your skill set, then maybe this simply is not the position for you. Interview technique is only part of the equation when job hunting. Don’t over stress on the Question and Answer part. Make sure you are competent and confident in your abilities. There is no substitute for knowledge and experience. 

Yes, by all means practice your Q&A session but remember the basics will remain constant. 

If you have any worries, [contact us](https://pangara.com/contact/) directly at [Pangara](https://pangara.com/), we will be only too happy to assist. Remember that math is a prerequisite for this kind of work, and whilst it may not come up in the interview stage, it certainly will as soon as the job starts. So it’s important you keep up to speed with your mathematics. The strong links between math and programming will become apparent. The sooner you spot this, the better your programming will be. 

A strongly motivated candidate with drive and enthusiasm is more than a substitute for an over qualified one, with a laissez-faire attitude.

### **And Now to the Fundamental C++ Interview Questions**

OK, so you are a **[talented C++ programmer**](https://pangara.com/our-talent-tech-freelancers/c-sharp-developer-hire-top-c-sharp-freelancers-vietnam) and you are confident in your abilities, but you still have to get through that dreaded job interview. How do you prepare and what is likely to happen? Here is a list of questions that are likely to be asked of you at an interview. Read and memorise these and we will help you secure that life changing job.

## Questions

1\. Explain mutable and volatile keywords.

Volatile keywords are designed to prevent the writer from applying optimisations on objects over which he or she has no control. Any objects that are declared as volatile are just omitted from optimisation to prevent values being changed by coding outside the scope of the original code. 

Mutable keywords are useful on occasions where most members need to remain constant but some need to be updated at a later time. members set up as mutable are able to be modified even though the full object is declared as constant. Mutable keywords can not be used in conjunction with names that have previously been declared as constant, static or reference. 

* * *

2\. How many times does this loop execute? Please give an explanation.

```
unsigned char half_limit = 150;

for (unsigned char i = 0; i < 2 * half_limit; ++i)  
[  
// do something;  
]  

unsigned char half_limit = 150;
```

If i was declared as ‘inst' the correct would be 300. However as it was declared to be an ‘unsigned char’ the answer is that it will loop indefinitely. The explanation for this is as follows:

‘2 * half_limit is in fact promoted to ‘int’ This is based on C++ Conversion Rules. It therefore has a value of 300. In this instance i is an unsigned char, and represents an 8-bit value which, after reaching 255, will overflow and return to zero. The loop will therefore go on ad infinitum.

* * *

3\. What is the difference between struct and class?

Whilst being almost the same, differences do occur when looking at the access modifiers. The default settings are that struct members remain public whilst class are private. Use struct members when working with simple data objects and class for objects with methods.

* * *

4\. What is an object??

An instance of the class is called as object.

* * *

5\. When would you use virtual inheritance?

In an ideal situation, one would not use virtual inheritance (though it could be done). However it is important that one understands how it works. This is necessary to understand how your class will be used.

Here is an example of how to use it:

```
#include

class D {  
public:  
void foo() {  
std::cout << "Foooooo" << std::endl;  
}  
};

class C: public D {  
};

class B: public D {  
};

class A: public B, public C {  
};

int main(int argc, const char * argv[]) {  
A a;  
a.foo();  
}  
```

If you don’t use virtual inheritance in this case, you will get two copies of D in class A: one from B and one from C. To fix this you need to change the declarations of classes C and B to be virtual, as follows:

```
class C: virtual public D {  
};

class B: virtual public D {  
};
```

* * *

6\. When is it possible to have a recursive inline function?

Whilst it is possible to have an inline function within itself, the compiler is not able to figure out the depth of recursion whilst compiling and therefore is not able to generate inline code.

The inline specification on a function is simply a hint. In fact, the compiler can — and often does — completely ignore the presence or absence of an inline qualifier. However, a compiler can inline a recursive function. In much the same way as it can unroll an infinite loop.

It merely has to place a limit on the level to which it will "unroll" the function.

* * *

7\. The code featured below is inaccurate, please define the problem and explain how you would change it?

```
size_t sz = buf->size();  
while ( --sz >= 0 )  
[  
/* do something */  
]  
```

In the example given, -sz >= 0 remains true making it impossible to exit the while loop. -sz >= 0 remains true as sz is size_t. size_t and therefore just an alias of the fundamental unsigned integer types. As sz is unsigned, it cannot be less than zero, meaning the condition is never true. 

A way to correct this would been using a for loop, this:

```
for (size_t i = 0; i < sz; i++)  
{  
/* do something */  
}
```

* * *

8\. As multiple inheritance is supported by C++, explain the “diamond problem,” with multiple inheritance that can sometimes occur? Please provide an example.
  
Imagine the administrator of a large school. Their job is to manage the day to day dealings of students, teachers, TAs, admin staff, parents and management, etc. In this instance, a simple inheritance scheme would require different people in various roles, though all would inherit from a common “person” class. This class can be defined as a abstract getRole() method. This would be overridden by subclasses and returned to the correct type.

If you then needed to model the role of a TA, being both a member of the faculty and a grad student, this would cause the classic diamond problem of multiple inheritance. The TA’s getRole() method would be ambiguous.

![c++ interview questions](https://i0.wp.com/pangara.com/wp-content/uploads/2017/08/Infographic-Opt1-310717.jpg?resize=445%2C345&ssl=1)

It is then questionable as to which getRole() method the TA should inherit. It can be argued that the TA class could override the getRole() method and be defined as simply a TA. This is however not an idea, as it fails to recognise that the TA is both a grad student and a faculty member.

Have a look [here](https://isocpp.org/wiki/faq/multiple-inheritance#mi-diamond) for another example here.

* * *

9\. What does the acronym OOPS stand for?

Object Oriented Programming System

* * *

10\. What does protected access specifier do?

When a class/struct member is protected it is accessible within the inherited class. Outside, however, both private and protected members will not be accessible.

* * *

11\. Define encapsulation.

This is when you tie the data and the functions that are acting together in a class. In OOP, encapsulation is one of four mechanisms. Encapsulation is when you tie the data and the functions that are acting together in a class. In encapsulation, the data is not accessed directly; it is accessed through the functions present inside the class. In simpler words, attributes of the class are kept private and public getter and setter methods are provided to manipulate these attributes. Thus, encapsulation makes the concept of data hiding possible.  

* * *

12\. Define data abstraction.

This refers to the act of hiding internal implementation and showing only necessary details. Data abstraction refers to providing only essential information to the outside world and hiding their background details. That is, to represent the needed information in program without presenting the details. Data abstraction is a programming (and design) technique that relies on the separation of interface and implementation.  

* * *

13\. Define an inline function.

This is when a function is prefixed and the keyword 'inline' is placed before the function definition. They often work faster than normal functions as the compiler replaces the definition of inline functions at compile-time instead of the referring function definition at run-time. 

* * *

14\. Name the storage classes that are supported in C++.

Auto, extern, mutable, register and static.  

.

* * *

15\. Explain the difference between shallow and deep copy.

Shallow copy dumps memory bit at a time from one object to another. Shallow copies duplicate as little as possible. They are copies of the collection structure, and not the elements. Hence, two collections share the individual elements. Deep copy, on the other hand, duplicates everything. In a deep copy collection, two collections with all of the elements in the original collection are duplicated. They work field by field from object to object. To achieve deep copy, use copy constructor and or an overloading assignment operator.  

.

* * *

16\. Explain a pure virtual function.

If a virtual function doesn’t have a function body and is assigned with a zero value, it is name a pure virtual function. Pure virtual function is to make the class abstract, so that it can't be instantiated. A child class, however, can override the pure virtual methods to form a concrete class.  

.

* * *

17\. Explain the function of static keyword on class member variable.

A static variable may exist even without objects for the memory class being created. Static member variables have the same memory across all objects that have been created for that class. To refer to the static member variable use the class name itself.  

.

* * *

18\. In C++, what data type is used to store wide characters?

wchar_t

 

.

* * *

19\. Which operators are used to access class members?

Arrow ( -> ) and Dot (.)

 

.

* * *

20\. Which data type would you use to store the Boolean value?

The new primitive data type used in C++ language is bool.  

.

* * *

21\. Define function overloading.

Function overloading is when you define several functions with the same name and unique list of parameters.  

.

* * *

22\. What is a destructor and can it be overloaded?

A member function of the class that has the same name as the class name and has the prefix tilde (~) is known as a destructor. At the moment, when the object loses its scope it is executed automatically w.r.t. No, it cannot be overloaded. It's only form is without parameters.  

.

* * *

23\. Define the term constructor.

The member function of the class is known as a constructor when it has the same name as the class and is executed automatically at the point of creation of the object for the respective class.  

.

* * *

24\. Is it possible to use the () malloc function of C language in C++ to allocate dynamic memory?

Yes, C is the subset of C++ and all functions of c in C++ can be used.  

.

* * *

25\. Define namespace.

[Microsoft Developer Network](https://msdn.microsoft.com/en-us/library/5cb46ksf.aspx) defines namespace as, "a declarative region that provides a scope to the identifiers (the names of types, functions, variables, etc) inside it. They are used to organise code into logical groups and to prevent name collisions that can occur especially when your code base includes multiple libraries. All identifiers at namespace scope are visible to one another without qualification. Identifiers outside the namespace can access the members by using the fully qualified name for each identifier." 

We'd like to thank **[Vinh Đoàn Thế'](https://www.linkedin.com/in/the-vinh-doan-4a240133) **for lending his C++ expertise to this article.

![PANGARA_LOGO_](https://i0.wp.com/pangara.com/wp-content/uploads/2017/02/PANGARA_LOGO_notext.png?resize=160%2C149&ssl=1)

**_If you're ready to take the next step and join Pangara's exclusive network of freelancers, then let's get started! _****_[Become a Pangara Talent](https://pangara.com/become-pangara-talent/) today. _**

**_Stay tuned for Pangara’s latest news updates and events on our _****_[Facebook_**](https://www.facebook.com/pangara.itjobs/)**_ page, _****_[LinkedIn_**](https://www.linkedin.com/company/7576715?trk=tyah&trkInfo=clickedVertical%3Acompany%2CclickedEntityId%3A7576715%2Cidx%3A2-1-2%2CtarId%3A1465895250962%2Ctas%3Apangara)**_ and _****_[Twitter_**](https://twitter.com/PangaraWorld)**_._**

 
