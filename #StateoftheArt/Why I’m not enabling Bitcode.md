# Why I’m not enabling Bitcode

_Captured: 2015-09-24 at 22:15 from [medium.com](https://medium.com/@FredericJacobs/why-i-m-not-enabling-bitcode-f35cd8fbfcc5)_

#### Thoughts on application binaries packaging and software distribution

At Apple's annual WWDC developer event, the compiler infrastructure team unveiled "**Bitcode**" and recommended iOS developers to opt-in , even requiring it for Apple Watch applications.

**_The Problem with fat archives_**

Multi-architecture iOS (and OS X) executables are packaged in [fat archives](https://en.wikipedia.org/wiki/Fat_binary). The fat format (not to same as the filesystem) is quite simple: the application binaries contain headers describing the scope of the instructions for a given infrastructure. Fat headers of a binary can be looked up by running:
    
    
    otool -f binaryName

In the following screenshot, we can see that [Signal Private Messenger](https://itunes.apple.com/us/app/signal-private-messenger/id874139669?mt=8) is compiled for the two following architectures:
    
    
      
    - armv7: ARM has CPU type 12, armv7 is CPU subtype 9. (The armv7-specific instructions start at offset 16384 and go on for the next 5306144 bytes.)  
    - arm64: CPU type 16777228, the ARM 64-bit CPU type. 64-bit instructions start at offset 5324800 and have length of 6457600 bytes.

![](https://cdn-images-1.medium.com/max/800/1*k8Tosjf0wf_wKeO2Gbqqjw.png)

> _Screenshot from running the 'otool' command_

Note: The FAT_MAGIC value `0xCAFEBABE` indicates what kind of archive it is. [Different flags](http://www.opensource.apple.com/source/xar/xar-202/xar/lib/macho.c) are defined for big/little-endian & 32/64 bit configurations.

![](https://cdn-images-1.medium.com/max/800/1*waAmF8YhYnezR3rUeI3vQQ.png)

> _macho.h from Apple's Open Source page_

As we can see, adding architectures come at a significant **storage cost**. Apple has regularly updated the underlying ARM processor architectures of their series A SoCs.

![](https://cdn-images-1.medium.com/max/800/1*VBc3ESeMTxvP0uD-d3IF7Q.png)

> _iOS Support Matrix. Each color represents a different processor architecture. [Source](http://iossupportmatrix.com)_

It is fairly common for Apple to _continue delivering operating system updates_ for devices that are more than four years old. For instance, the iPhone 4S, released in 2011, still gets an iOS 9 update. iOS developers also build their apps to be able to _run on multiple older versions of iOS_ and therefore have to support sometimes even more architectures. In addition, Apple has started releasing _multiple iPhone models per year_ powered by different architectures. iPhones are not the only devices running these apps: the same binaries can be executed on_ iPads_ too. And since recently, iPhone app bundles are shipping with _WatchOS_ binaries too. All of this results in application binaries becoming substantially larger as time goes by.

Applications are built for all architectures, but only one is required on a specific device. So, why not just distribute the binary for the device's architecture? Apple introduced exactly that with App Thinning.

### App Thinning

> Slicing is the process of creating and delivering variants of the app bundle for different target devices. A variant contains only the executable architecture and resources that are needed for the target device. You continue to develop and upload full versions of your app to iTunes Connect.

Slicing looks great. It not only strips away unused executable architectures, but also deals away with resources that won't be used based on your screen resolution or size, such as images and icons.

Great! Binary size growth is no more an issue, but what about new architectures? What stripped architecture should Apple serve them? That's where Bitcode comes in.

### Bitcode

Bitcode isn't actually anything new. It's been around in the LLVM project for some time now. Let's review the compilation process.

> The most popular design for a traditional static compiler (like most C compilers) is the three phase design whose major components are the front end, the optimizer and the back end.

> The **front end** parses source code, checking it for errors, and builds a language-specific Abstract Syntax Tree (AST) to represent the input code. The AST is optionally converted to a new representation for optimization, and the optimizer and back end are run on the code.

> The **optimizer** is responsible for doing a broad variety of transformations to try to improve the code's running time, such as eliminating redundant computations, and is usually more or less independent of language and target.

> The **back end** (also known as the code generator) then maps the code onto the target instruction set. In addition to making correct code, it is responsible for generating goodcode that takes advantage of unusual features of the supported architecture. Common parts of a compiler back end include instruction selection, register allocation, and instruction scheduling.

![](https://cdn-images-1.medium.com/max/800/1*k9VzcEMNbMZiN51AtPW80w.png)

> _LLVM three stages compilation_

> The most important win of this classical design comes when a compiler decides to support multiple source languages or target architectures. If the compiler uses a common code representation in its optimizer, then a front end can be written for any language that can compile to it, and a back end can be written for any target that can compile from it.

![](https://cdn-images-1.medium.com/max/800/1*t6ZR_0K-GoImrv9i1vtjKQ.png)

The front-end produces LLVM "bytecode" (LLVM **I**ntermediate **R**epresentation) for a virtual machine, that is later optimized and mapped to native instruction sets. [Bitcode](http://llvm.org/docs/BitCodeFormat.html) is simply a **bitstream** of LLVM IR.

With iOS 9, Apple wants developers to upload LLVM Bitcode to iTunes Connect (the App Store's backend). Apple would then optimize the LLVM IR and generate the binaries for each platform. In practice, the LLVM Bitcode is compressed and packed into the Mach-O binary that is uploaded to iTunes.

If you're curious about how Bitcode is packed into application binaries when uploaded to the App Store, I suggest you the following article:

**[Bitcode Demystified**  
_Few months ago Apple announced a 'new feature', called 'Bitcode'. In this article I'll try to answer the questions like…_lowlevelbits.org](http://lowlevelbits.org/bitcode-demystified/)

#### Is LLVM-IR really platform independent?

Even though the three stages compilation infrastructure appeared to be designed to be platform independent. It appears to be very different in practice.

In [a lengthy write-up](http://lists.llvm.org/pipermail/llvm-dev/2011-October/043724.html) in 2011 on the LLVM-dev mailing list, (ex-)Apple engineer Dan Gohmanargued about why IR would be "a poor system for building a Platform, any system where LLVM IR would be a  
format in which programs are stored or transmitted for subsequent  
use on multiple underlying architectures".
    
    
    However, there are several ways in which LLVM IR differs from actual  
    platforms, both high-level VMs like Java or .NET and actual low-level  
    ISAs like x86 or ARM.  
      
    First, the boundaries of what capabilities LLVM provides are nebulous.  
    LLVM IR contains:  
      
     * Explicitly Target-specific features. These aren't secret;  
       x86_fp80's reason for being is pretty clear.  
      
     * Target-specific ABI code. In order to interoperate with native  
       C ABIs, LLVM requires front-ends to emit target-specific IR.  
       Pretty much everyone around here has run into this.  
      
     * Implicitly Target-specific features. The most obvious examples of  
       these are all the different Linkage kinds. These are all basically  
       just gateways to features in real linkers, and real linkers vary  
       quite a lot. LLVM has its own IR-level Linker, but it doesn't  
       do all the stuff that native linkers do.  
      
     * Target-specific limitations in seemingly portable features.  
       How big can the alignment be on an alloca? Or a GlobalVariable?  
       What's the widest supported integer type? LLVM's various backends  
       all have different answers to questions like these.  
      
    Even ignoring the fact that the quality of the backends in the  
    LLVM source tree varies widely, the question of "What can LLVM IR do?"  
    has numerous backend-specific facets. This can be problematic for  
    producers as well as consumers.  
      
    Second, and more fundamentally, LLVM IR is a fundamentally  
    vague language. It has:  
      
     * Undefined Behavior. LLVM is, at its heart, a C compiler, and  
       Undefined Behavior is one of its cornerstones.  
      
       High-level VMs typically raise predictable exceptions when they  
       encounter program errors. Physical machines typically document  
       their behavior very extensively. LLVM is fundamentally different  
       from both: it presents a bunch of rules to follow and then offers  
       no description of what happens if you break them.  
      
       LLVM's optimizers are built on the assumption that the rules  
       are never broken, so when rules do get broken, the code just  
       goes off the rails and runs into whatever happens to be in  
       the way. Sometimes it crashes loudly. Sometimes it silently  
       corrupts data and keeps running.  
      
       There are some tools that can help locate violations of the  
       rules. Valgrind is a very useful tool. But they can't find  
       everything. There are even some kinds of undefined behavior that  
       I've never heard anyone even propose a method of detection for.  
      
     * Intentional vagueness. There is a strong preference for defining  
       LLVM IR semantics intuitively rather than formally. This is quite  
       practical; formalizing a language is a lot of work, it reduces  
       future flexibility, and it tends to draw attention to troublesome  
       edge cases which could otherwise be largely ignored.  
      
       I've done work to try to formalize parts of LLVM IR, and the  
       results have been largely fruitless. I got bogged down in  
       edge cases that no one is interested in fixing.  
      
     * Floating-point arithmetic is not always consistent. Some backends  
       don't fully implement IEEE-754 arithmetic rules even without  
       -ffast-math and friends, to get better performance.  
      
    If you're familiar with "write once, debug everywhere" in Java,  
    consider the situation in LLVM IR, which is fundamentally opposed  
    to even trying to provide that level of consistency. And if you allow  
    the optimizer to do subtarget-specific optimizations, you increase  
    the chances that some bit of undefined behavior or vagueness will be  
    exposed.  
      
    Third, LLVM is a low level system that doesn't represent high-level  
    abstractions natively. It forces them to be chopped up into lots of  
    small low-level instructions.  
      
     * It makes LLVM's Interpreter really slow. The amount of work  
       performed by each instruction is relatively small, so the interpreter  
       has to execute a relatively large number of instructions to do simple  
       tasks, such as virtual method calls. Languages built for interpretation  
       do more with fewer instructions, and have lower per-instruction  
       overhead.  
      
     * Similarly, it makes really-fast JITing hard. LLVM is fast compared  
       to some other static C compilers, but it's not fast compared to  
       real JIT compilers. Compiling one LLVM IR level instruction at a  
       time can be relatively simple, ignoring the weird stuff, but this  
       approach generates comically bad code. Fixing this requires  
       recognizing patterns in groups of instructions, and then emitting  
       code for the patterns. This works, but it's more involved.  
      
     * Lowering high-level language features into low-level code locks  
       in implementation details. This is less severe in native code,  
       because a compiled blob is limited to a single hardware platform  
       as well. But a platform which advertizes architecture independence  
       which still has all the ABI lock-in of HLL implementation details  
       presents a much more frightening backwards compatibility specter.  
      
     * Apple has some LLVM IR transformations for Objective-C, however  
       the transformations have to reverse-engineer the high-level semantics  
       out of the lowered code, which is awkward. Further, they're  
       reasoning about high-level semantics in a way that isn't guaranteed  
       to be safe by LLVM IR rules alone. It works for the kinds of code  
       clang generates for Objective C, but it wouldn't necessarily be  
       correct if run on code produced by other front-ends. LLVM IR  
       isn't capable of representing the necessary semantics for this  
       unless we start embedding Objective C into it.

[Chris Lattner](https://twitter.com/clattner_llvm), primary author of the LLVM project and now director of the developer tools at Apple [responded](http://lists.llvm.org/pipermail/llvm-dev/2011-October/043735.html):

> I agree with almost all of the points you make, but not your conclusion. Many of the issues that you point out as problems are actually "features" that a VM like Java doesn't provide. For example, Java doesn't have uninitialized variables on the stack, and LLVM does. LLVM is capable of expressing the implicit zero initialization of variables that is implicit in Java, it just leaves the choice to the frontend.

> Many of the other issues that you raise are true, but irrelevant when compared to other VMs. For example, LLVM allows a frontend to produce code that is ABI compatible with native C ABIs. It does this by requiring the frontend to know a lot about the native C ABI. Java doesn't permit this at all, and so LLVM having "this feature" seems like a feature over-and-above what high-level VMs provide. Similiarly, the "conditionally" supported features like large and obscurely sized integers simply don't exist in these VMs. […]

> It isn't LLVM's fault that people want LLVM to magically solve all of C's portability problems.

It's clear that nobody claims that LLVM IR is actually portable. Once the LLVM-IR has been generated from a specific front-end, you can't just plug another backend and hope that your application will just work.

This exchange being from 2011, has anything changed since? I compiled a simple App with Bitcode to see. You can find the AppDelegate.m and the associated LLVM-IR in the following [Gist](https://gist.github.com/FredericJacobs/816e85e1b69b372b094a). Unsurprisingly, the IR is highly dependent on a specific target (casts, word sizes …).

Bitcode will enable support for** better ****[microarchitecture**](https://en.wikipedia.org/wiki/Microarchitecture)** support **but gets nowhere close to target independence. Applications compiled for the armv7 target could still run on armv7s devices but additional optimisations make applications faster if they contain a armv7s slice. The advantage that Bitcode provides on top of app thinning is negligible in my opinion since it will only provide a _slight speed up_ until the developer uploads a new build with the optimized slice.

### Security Implications

Now that we know what Bitcode actually does, let's review the security implications.

#### Compiler Optimizations Correctness

Compiler optimizations correctness is nothing new and of course it also applies to programs not distributed with Bitcode. But usually, the developer of the application has complete control on what types of optimizations will be performed and on what files these should be applied. Bitcode doesn't provide any fine-grained control over this. Apple **does not provide any documentation or sample configuration** of what optimizations are applied on the LLVM-IR. It acts like a black-box, and you can't reproduce the output locally as far as I know.

Compiler optimizations correctness has been studied for a long time. A [recent paper](https://nebelwelt.net/publications/15LangSec/CorrectnessSecurityGap-LangSec15.pdf) by Vijay D'Silva, Mathias Payer and Dawn Song presented at LangSec 2015, analyses optimizations from a security perspective. Here are a few examples of what could go wrong:

  * information leaks through persistent state.

> A compiler optimization that manipulates security critical code may cause information about a secure computation to persist in memory thereby introducing a persistent state violation.

Examples: Dead Store Elimination, Function Call Inlining, Code Motion

  * elimination of security-relevant code due to undefined behavior

> The term undefined behavior refers to situation in which  
the behavior of a program is not specified. Language specifications  
deliberately underspecify the semantics of some  
operations for various reasons such as to allow working  
around hardware restrictions or to create optimization opportunities.

> Examples of undefined behavior in C are using  
an uninitialized variable, dividing by zero, or operations that  
trigger overflows.

  * introduction of side channels

> A side channel leaks information about the state of the  
system. Side channel attacks allow an attacker external to  
the system to observe the internal state of a computation  
without direct access to the internal state. We say that a side  
channel violation occurs if optimized code is susceptible to  
a side channel attack but the source code is not.

Examples: Common Subexpression Elimination, Strength Reduction, Peephole Optimizations

All of these bugs are bad. With cryptographic implementations in mind, all of these represent important vulnerabilities. From key leakage to timing attacks via fault attacks, a lot of things can go wrong.

#### Compiler trust

In his 1984 [Turing Award Lecture "Reflections on trusting trust"](https://www.ece.cmu.edu/~ganger/712.fall02/papers/p761-thompson.pdf), Ken Thompson describes how compilers can be used to inject trojans.

![](https://cdn-images-1.medium.com/max/800/1*wQsIXi5cqgV2Nyk1kwbC6Q.png)

> _Extract from Ken Thompson's Turing Award Lecture_

An interesting example of the inherent trust issue in compilers has been doing rounds recently with the detection of [XcodeGhost](http://researchcenter.paloaltonetworks.com/2015/09/novel-malware-xcodeghost-modifies-xcode-infects-apple-ios-apps-and-hits-app-store/), a modified version of Xcode that reportedly infected millions of users. It is already difficult to trust compilers. LLVM being open-source and reviewable makes it easier to trust than a blackbox. But that doesn't entirely solve the problem since you will need a compiler binary to compile your compiler.

The **centralization of the building and signing process **is what worries me: an adversary could find a vulnerability in the LLVM backend to obtain remote code execution on Apple's Bitcode compilation infrastructure to inject a compiler trojan that would affect every single app on the App Store that was submitted with Bitcode.

#### Potential for backdoor injection

Compromising Apple's infrastructure isn't the only way to backdoor iOS apps in that setting. Since Apple is going to centralize the process of building application binaries, it will become really appealing to **governments desiring to get "lawful" access to application content**, circumventing any kind of encryption, no matter how strong it is. [An article](https://www.washingtonpost.com/world/national-security/obama-administration-ponders-how-to-seek-access-to-encrypted-data/2015/09/23/107a811c-5b22-11e5-b38e-06883aacba64_story.html) published today by the Washington Post explains how the Obama administration working group has been working on compelling phone manufacturers or App Store services to provide a way to insert a backdoor on the device.

> The second approach would exploit companies' automatic software updates. Under a court order, the company could insert spyware onto targeted customers' phones or tablets -- essentially hacking the device.

Adding backdoors to Bitcode applications becomes easier than ever. Apple has your application's **IR** (easier to decompile than binary) with** all the associated symbols**!

While this sounds bad, worse of all is the lack of accountability in such a setting because of the difficulty to verify builds.

#### Verifiability

There is currently no easy way of verifying (save with a jailbroken iPhone) that an application on the App Store is the one you uploaded as a developer. And I'm not even talking about reproducible builds, which consist of reproducing the same binary from a given source code. The biggest pain point up to now for verifiable and reproducible builds was **FairPlay, Apple's DRM** applied to applications. App Store binaries are encrypted (with a key that even the app's developer doesn't have). Hence, they have to be decrypted before being able to analyze with binary analysis tools such as Hopper, IDA …

FairPlay encryption already made it really difficult for developers to make sure that Apple distributes the build you think they are distributing. But at least, with jailbroken iPhone, I'm currently able to get some idea of what the binary I'm distributing looks like and compare it to the one I submitted to Apple.

With Bitcode builds, this becomes significantly harder. Since I **can't reproduce a target binary** since I don't know what optimizations Apple is performing on my binaries, I can't 'diff' them to find possibly altered parts. I have to analyze the entire binary to figure out that nothing nasty is going on. It became so bad that some developers weren't even able to symbolicate the crash logs of their own applications since binaries were built on the server and Apple was failing to provide the symbolication files (dSYM).

#### Conclusions

App thinning solves the binary size problem that I understand needed to be solved. The potential performance improvements during a short time period on new microarchitectures isn't outbalancing all of the issues I cited in this post. It might be a different deal for you, but I strongly think it's unwise for any developer who cares about security.

**Just not gonna happen, Bitnope …**

Update 1 (24-09-2015 17:19 GMT): Some grammatical and layout issues were fixed based on feedback from [Nadim Kobeissi](https://twitter.com/kaepora).
