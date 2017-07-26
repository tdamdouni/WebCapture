# The Struggle With Rust

_Captured: 2017-02-02 at 03:50 from [dzone.com](https://dzone.com/articles/the-struggle-with-rust?edition=267881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-01)_

[Learn NoSQL for free](https://dzone.com/go?i=177130&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F73561%3B2342927%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D13811243) with hands-on sample code, example queries, tutorials, and more. Brought to you in partnership with[ Couchbase](https://dzone.com/go?i=177130&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F73561%3B2342927%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D13811243).

So I spent a few evenings with Rust and managed to do some pretty trivial stuff with it. But then I tried to do something non-trivial (low-level trie that relies on low-level memory manipulations). And after I realized that I just have to fight the language non-stop, I am not going to continue forward with this.

Here is where I gave up:

![image](https://ayende.com/blog/Images/Open-Live-Writer/The-struggle-with-Rust_13BD4/image_thumb_1.png)

I have a buffer that I want to mutate using pointers. So I allocated a buffer with the intent to use the first few bytes for some header and use the memory directly and efficiently. Unfortunately, I can't. I need to mutate the buffer in multiple places at the same time (both the trie header and the actual node), but Rust refuses to let me do that because then I'll have multiple mutable references, which is exactly what I _want_.

It just feels that there is so much _ceremony _involved in getting a Rust program to actually _compile_ that there isn't any time left to do anything else. [This post](https://blog.ntpsec.org/2017/01/18/rust-vs-go.html) certainly resonated with me strongly.

That is about the language and what it requires. But the _environment_ isn't really nice either. It starts from the basic: I want to allocate some memory.

Sure, that's easy to do, right?

  * `alloc::heap::allocate` is only for unstable and might change underneath you.
  * `alloc::raw_vec::RawVec`, which gives you raw memory directly, is unstable and likely to remain so, even though it is much safer to use than directly allocating memory.

We are talking about _allocating_ memory, in a system-level language, and unless you are jumping through hoops, there is just no way to do that.

I'll admit that I'm also spoiled in terms of tooling (IDEs, debuggers, etc.), but the Rust environment is pretty much, "Grab a text editor, you'll have syntax highlighting and maybe something a bit more," and that is it. I tried three or four different editors, and while some of them, intellij-rust for example, were able to do some code analysis, they weren't able to actually _build_ anything (I think that I needed to install JDE or some such). VS Code could build and run (but not debug), but it marks every single warning. Combined with Rust's eagerness of warning, it made it very hard to write code. Consider what it feels like to work when everything you code looks like this:

![image](https://ayende.com/blog/Images/Open-Live-Writer/The-struggle-with-Rust_13BD4/image_thumb_2.png)

No debugger beyond println (and yes, I know about GDB, that ain't a good debugging experience) is another major issue.

I really want to like Rust, and it has some pretty cool ideas, but the problem is that it is just too hard to actually get something done in any reasonable timeframe.

What is really concerning is that any time that I want to do anything really interesting, you need to either go and find a crate to do it (without any assurances of quality, maintainability, etc.) or you have to use a nightly version or enable various feature flags or use unstable API versions. And you have to do it for anything beyond the most trivial stuff.

The very same trie code that I tried to write in Rust I wrote in one and a half evenings in C++ (including copious searches for the correct modern ways to do something). And it works. It is obvious, and I don't have to fight the compiler all the time.

Granted, I've written in C++ before, and C# (my main language) is similar, but the differences are staggering. It isn't just the borrow checker, it is the sum of the language features that make it very hard to reason about what the code is doing. I mentioned before that the fact that generics are resolved on _usage_, which can happen quite a bit further down from the actual declaration, is very confusing. It might have been different if I had been coming from an ML background, but Rust is just too much work for too little gain.

One of my core requirements, the ability to write code and iterate over behavior quickly is blocked because every time that I'm trying to compile, I'm getting weird, complicated errors, and then I need to implement workarounds to make the compiler happy, which introduces complexity into the code for very simple tasks.

Let us take a simple example. I want to cache the result of a DNS lookup. Here is the code:

We'll ignore the unstable API usage with lookup_host and the fact that it literally took me over an hour to get 30 lines of code out in a shape that I can actually demonstrate the issue.

There is a _lot_ of stuff going on here. We have a cache of boxed strings in the hash map to maintain ownership on them. We look them up, then add a cloned key to the cache because the owner of the host string is the caller, etc. But most importantly, this code is simple, expressive, and wrong. It won't compile because we have both immutable borrow (on line 17) and a mutable one (on lines 25 and 26).

And yes, I'm aware of the entry API on the HashMap that is meant to deal with this situation. The problem is that all those details, and making the compiler happy in a very simple code path, is adding a _lot_ of friction to the code. To the point where you don't get anything done other than fight the compiler all the time. It's annoying, and it doesn't feel like I'm accomplishing anything.

[The Getting Started with NoSQL Guide](https://dzone.com/go?i=177131&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F73561%3B2342928%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D13811244) will get you hands-on with NoSQL in minutes with no coding needed. Brought to you in partnership with [Couchbase](https://dzone.com/go?i=177131&u=https%3A%2F%2Fservedby.flashtalking.com%2Fclick%2F8%2F73561%3B2342928%3B369307%3B211%3B0%2F%3Fft_width%3D1%26ft_height%3D1%26url%3D13811244).
