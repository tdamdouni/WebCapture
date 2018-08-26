# C and Functional Safety in the Automotive Industry (Part 2): The Usual Suspects

_Captured: 2018-07-03 at 23:12 from [dzone.com](https://dzone.com/articles/c-and-functional-safety-in-the-automotive-industry)_

In the [last post](https://blog.tremend.com/history-c-embedded-auto-industry/), we recapped the emergence of C as the dominant programming language for embedded automotive systems. From its roots in Unix in the early 1970s up to its gathering criticism around its relative eccentricities, this platform has greatly matured over the years. We also covered the emergence of safety standards in ISO 26262 and IEC 61508, as well as the launch of MISRA C.

In this post, we'll examine the scope that C gives a developer to generate problematic code. We'll also outline the kind of rigor and mindset necessary to safely harness the power of the language and to avoid those conflicts of intent and execution that have garnered C some critics, from a safety standpoint, over the last few decades.

It may not be immediately clear what exactly constitutes a safety-related risk in the context of safety-critical embedded software. Here, there are a couple of unusual considerations.

As long as the programming language is documented, everything should be clear, leaving the developer free to write code under a due regimen of quality-checks. But, developing safety-critical software puts the developer in the unusual position of having limited access to their own toolbox. There are still areas of the[ ANSI C standard](https://www.le.ac.uk/users/rjm1/cotter/page_47.htm) that are not fully specified and, therefore, must remain out-of-bounds. Consequently, different compilers may follow different implementation strategies, which can lead to unexpected behavior across platforms.

In addition to this, some language constructs are simply more prone to human error than others -- a factor which I'll investigate in the next post of this series.

## **Language Features With Undefined Behavior**

C is very flexible, permitting a wide range of operations that are valid from a syntax perspective, but could make the compiled program dangerously unstable if used in the wrong way. Certainly, people like Dennis Ritchie and Brian Kernighan were betting hard on the professionalism and competence of software developers when they offered such sharp knives to them.

The same applies for the compiler vendors in regards to the optimization of generated binaries. In order to produce very efficient binary code, most C compilers do not provide 'sanity checks' to the code generation process, but rather rely on the developer deploying the code in a context (and within set boundaries) appropriate to its design.

The possibility of undefined behavior in C-based projects is minimized two important ways. Firstly, this is done by taking the responsibility to write all meaningful safety checks directly into the routines. Second, this enables the compiler's warning levels by using [static analyzers](https://www.owasp.org/index.php/Static_Code_Analysis) to automatically identify risk-laden code segments that might have slipped by the developer.

Let's discuss a few of the essential rules that even the most seasoned C practitioner can lose touch with during the organized chaos of a large project.

## **Using an Uninitialized Variable**

Unlike many other programming languages, declaring a variable in C does not imply having it filled with a default value like 0, empty string, null_,_ or whatever else a software developer might imagine. A C variable is just an address to a memory area with unknown content.

Even C beginners know this rule, but far more mature developers fall foul of its consequences, due to inattention or hard-to-read, too-complex code as their project grows.

Bugs that result from uninitialized variables can be very hard to discover through testing, since functional failures might be randomly reproduced, depending on the memory state behind them.

Such anomalies can not only survive the debugging process, but they can even get compounded by further structural conflicts. For example, review the code below:

At first glance, you might think that the wheel will turn either to the left or the right. However, the closer inspection reveals that bDirection can receive a random integer that is different from the equivalent integer values of true or false, meaning that the car will keep going straight forward!

As an added bonus, a compiler could potentially abandon the logic of the code after these uninitialized variables and decide to take both conditionals as true (or false), just to reduce the number of branches! Let's hope that such a scenario never appears in a functional safety-qualified compiler.

Luckily, compilers and third-party static analyzers support the detection of uninitialized variables. Data flow analysis is a critical aspect in the development of functional safety-related applications. Therefore, enabling the corresponding warning levels in static analyzers is one of the first things to check off in a project.

## **Accessing Out-Of-Bounds Elements**

[Arrays](https://www.tutorialspoint.com/cprogramming/c_arrays.htm) are another area where the programmer needs to pay close attention to scope and methodology. Defining a C array opens the gates to [out-of-bounds indexed accesses](https://cwe.mitre.org/data/definitions/125.html) to it, either by specifying negative indexes or by exceeding the array size.

Out-of-bounds read accesses are less 'undefined' (if we can use this term), since they will either read meaningless data or will generate an exception when trying to access invalid memory space, but, at least, the control flow can be anticipated.

Out-of-bounds writes are [worse](https://cwe.mitre.org/data/definitions/787.html), since they can randomly change data referenced by other variables in an unpredictable way. Furthermore, when such write attempts start to touch stack frames, they can also change CPU [return instruction pointers](https://c9x.me/x86/html/file_module_x86_id_280.html) that tell the CPU to decode and execute instructions from unrelated memory areas.

## **Division By Zero**

Division by zero does not work -- everyone knows this. So, why is it worth discussing, when the behavior is well-defined and it's known that attempting this calculation will generate nothing worse than a crash?

(Though it's a topic for another time, it's worth noting that a dumb crash of the compiled application may not be enough to preserve the safe state of the host system)

Take this snippet:

Based on the code above, we might be pretty confident that `safetyCriticalAction()` will always be called, since the division by zero should appear only after the function returns.

However, the anticipated crash is not controlled by the compiler by the hardware and the host operating system. The arithmetic units on many CPUs are able to detect the situation and signal an exception to the operating system, which will most likely terminate the application.

But, don't be surprised if that isn't what actually happens. The compiler doesn't care about the problem, since there's no dependency between u32Speed and the called function. However, the compiler might decide to generate the binary code for the division _before_ the critical call.

An even trickier situation emerges in the case of CPUs that feature [out of order execution](https://pdfs.semanticscholar.org/presentation/aca5/296063117f7c057d00648a06095a2639cf33.pdf). They have internal optimizers for the execution flows based on data dependency, similar to compilers. So, even if the compiler preserves the instructions order defined by the C code, it's possible that instruction reordering could still occur in the CPU.

## **Arithmetic or Logical Overflows**

C doesn't define behavior for overflow operations, which are most likely to be hardware-specific or driven by a compiler's internal algorithms.

Look at the piece of code below:

We might expect results based on a common-sense extrapolation of what we learned about the logical operations of CPUs, assuming that INT_MAX + 1 == INT_MIN, or _zero_ whipped out the results on any shift operation with a count equal or higher to the width of the type. Though such issues can be anticipated, it's better to avoid any such 'out-of-standard' scenarios in the first place, rather than relying on platform-specific behavior.

## **Compiler Optimization Algorithms**

Compilers should not be considered as a separate source of undefined behavior. Those qualified for use in functionally safe applications (such as in the embedded automotive sector) are expected to be stable and adherent to a standard C definition.

But in order to be able to [generate](https://www.slideshare.net/hardikmdev/compiler-optimization-techniques) optimized binaries, compilers have license to consider all those code segments _undefined_ by the C standard as potential areas of optimization. Undefined behaviors can, therefore, end up as a kind of wildcard for compiler writers who, with the aim of squeezing the most from each CPU tick, might deliberately allow the generation of messy code for undefined behavior scenarios. This is to determine if the code will provide less branching and better data or code locality for the valid and most probable execution paths.

To give you an idea of the possible problems that compiler optimizations can cause, compiling the code example above on arithmetic and logical overflows with gcc v5.4 with different optimization flags (-O0, -O1, -O2) will return different results when executed on Linux.

![](https://blog.tremend.com/wp-content/uploads/2018/06/gcc.png)

As you can see, in the case of -O2 usage, despite the fact that s32N is evaluated to INT_MAX and(s32N+1) is evaluated to INT_MIN, (s32N < s32N +1) is aggressively hardcoded to _true_. This should be the general correct value in all cases, except the one considered here, which, being under the umbrella of 'undefined behavior,' is allowed to return incorrect results.

Equally interesting variations can also be observed for [shifting operations](https://docs.microsoft.com/en-us/cpp/cpp/left-shift-and-right-shift-operators-input-and-output).

In the next post in this series, we'll examine some of the key areas which require particular vigilance in C-based embedded projects.

## **Other References**

  * ISO26262: Part 6 

  * MISRA C:2012
