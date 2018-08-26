# C and Functional Safety in the Automotive Industry (Part III): Mind Your Language

_Captured: 2018-07-17 at 19:13 from [dzone.com](https://dzone.com/articles/c-and-functional-safety-in-the-automotive-industry-1?edition=385243&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-07-17)_

In the previous posts, we [took a look](https://blog.tremend.com/history-c-embedded-auto-industry/) at the rise of C as the dominant language for safety-critical embedded systems. Then, we will [examine](https://blog.tremend.com/c-functional-safety-automotive-industry-part-2-usual-suspects/) some of the pitfalls that programmers fall into when using such a powerful tool. There is a growing need to be unusually self-reliant in terms of anticipating safety concerns in compiling and runtime environments.

In this post, we'll take a further look at institutions and practices that focus on a C subset's clarity and readability, as well as the challenges that this aspect of programming contains.

## **Avoiding Language Constructs That are Prone to Human Errors**

Many software bugs appear because the code is written in an unstructured way, using a poor or non-scalable design. In such cases, only a couple of incremental changes can transform the project into ungovernable [spaghetti code](https://daedtech.com/colleague-creates-spaghetti-code/).

Another source of potential issues is the more or less obfuscated code sometimes enjoyed by geek programmers; these are things like packing several expressions, statements, and calls onto a single line for the sake of maximizing code visibility on your screen. Obviously, these are aspects that have to be avoided in developing functional, safe software.

The rule of thumb here is to maximize transparency and make the code easy to read, understand, and review by others. In this respect, there are several powerful constructs provided by C that should be _avoided_ as much as possible. [Preprocessor directives](https://www.cprogramming.com/reference/preprocessor/), [pointer arithmetic](https://www.tutorialspoint.com/cprogramming/c_pointer_arithmetic.htm), and [typecasting ](https://www.improgrammer.net/type-casting-c-language/)are just a few of them.

MISRA C standardized a very detailed set of rules to help developers reduce the risks of using error-prone coding patterns. One essential tool in regards to code clarity is the project's coding guidelines. If MISRA C is an official standard shared by different industries, the coding guidelines are an organization/project-specific document intended to address stylistic or conventional aspects that won't necessarily be related to the language subset, but will help to cohere the team's efforts and expectations for how the code is to be structured and documented. Such guidelines will usually include naming conventions, code file structure, coding layout, and even comment documentation formats.

## **Strong Typing**

Returning to MISRA C, it's notable that this industry-oriented branch of C programming language enforces strong guidelines and restrictions intended to minimize error-prone coding patterns.

[Strong typing](https://stackoverflow.com/questions/2690544/what-is-the-difference-between-a-strongly-typed-language-and-a-statically-typed) is not really enforced in C, but is one of the best practices in safety-critical systems, in order to avoid issues caused by loss of value, loss of sign, or loss of precision. Therefore, MISRA C provides a number of rules for moving C closer to a more strictly-typed methodology.

Firstly, it decrees that [implicit type casting](http://en.cppreference.com/w/c/language/conversion) is avoided in order to prevent accidental and undesirable casts. Next, the explicit type casts need to be limited to cases where the entire information of the value is preserved. For example, this could include permitting integers and floats to be converted only to wider types, whilst preserving the original signs of any affected integers.

MISRA C also rules that [function-like](https://stackoverflow.com/questions/18444813/misra-rule-19-7-function-like-macro) preprocessing macros be avoided, since, among other reasons, they do not allow parameter type checking. Another forbidden practice is [unions usage](https://www.geeksforgeeks.org/union-c/), because of the [risk](http://www.drdobbs.com/flexible-c-8-union-casts-considered-harm/184403890) that data may be misinterpreted.

## **Limited Usage of Pointers**

[Pointers](https://users.cs.cf.ac.uk/Dave.Marshall/C/node10.html) are one of the key features in C and are hard to avoid entirely in any real-life application. In the context of C, ISO 26262 casts constraints for enforcing strong typing and also stipulates that pointer to integer conversions (and the other way around) is forbidden. Furthermore, additions and subtractions are the only mathematics that pointers are permitted to undertake during operations that involve array indexing.

## **Preprocessor Directives**

Another nice feature of C is [macros](https://gcc.gnu.org/onlinedocs/cpp/Macros.html), which are considered to be on 'the dark side' with respect to safety-critical systems. The possibility to define, redefine, and undefine them at any moment can [easily lead to confusion](http://www.brainbell.com/tutors/c/Advice_and_Warnings_for_C/Macros_and_Miscellaneous_Pitfalls.html) with respect to the existence or meaning of a macro.

Enabling or disabling code blocks by preprocessing macro directives can also lead to code that is hard to read, opening the gates for [dead code](https://wiki.sei.cmu.edu/confluence/display/c/MSC12-C.+Detect+and+remove+code+that+has+no+effect+or+is+never+executed) or strange control flows.

Function-like macros also have to be avoided, for the reasons previously mentioned, in regards to strong typing. Fortunately, in this case, the inline functions represent a much [better alternative](https://gcc.gnu.org/onlinedocs/gcc/Inline.html).

## **Coding Layout**

Though the coding layout is outside the scope of MISRA C (which defers projecting or organization specific coding guidelines, as mentioned above), it, nonetheless, has a couple of rules for addressing the structure of standard C constructs.

Examples of rules in this category include:

  * [If](https://www.codingunit.com/c-tutorial-the-if-and-switch-statement) constructs shall always be followed by a compound statement (i.e. a statement block in braces), switch constructs should always have a [default clause](https://rules.sonarsource.com/cpp/RSPEC-131).
  * For loop counters and control variables, they must fulfill a set of rules regarding where and how they are initialized, modified, or checked.
  * Parentheses should be used for emphasizing [operator priority ](https://wiki.sei.cmu.edu/confluence/display/c/EXP00-C.+Use+parentheses+for+precedence+of+operation)in expressions.

## **Data Flow Consistency Enforcement**

This aspect is generally derived from the design in regards to those few features in C that support concepts such as data encapsulation and modularity. The best practice advises developers to use unique identifiers to avoid ambiguity about the meaning of a variable, to minimize the visibility of a variable to the relevant scope only, and to use [const](https://www.geeksforgeeks.org/const-qualifier-in-c/) for read-only variables.

## **Control Flow**

Though constraints related to control flow are not specific to C, two basic rules also considered to be best practice are: not to use [unbounded recursions](https://www.geeksforgeeks.org/recursion/), since they represent a high risk of generating stack overflows; and to ensure that a function concludes in only [single possible exit point](http://wiki.c2.com/?SingleFunctionExitPoint). Though the latter guideline is intended to promote better readability, it has since come a question for a tendency to lead to deeper if-block trees, which, in themselves, make code harder to read.

That's it for this look at the pre-eminent place of C (and its subset) over nearly fifty years into the embedded software sector. Opinions might differ as to whether its dominance in the field is due to a luxurious legacy infrastructure from decades of development, or because it's still the best and most powerful tool for the job after all these years. But, in an increasingly locked-down software development world, C still represents the power that accompanies responsibility.
