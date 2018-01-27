# What Programming Language Should I Learn? (2017 Edition)

_Captured: 2017-08-23 at 19:37 from [dzone.com](https://dzone.com/articles/what-programming-language-should-i-learn-2017-edit?edition=319409&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-23)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

I occasionally find someone asking this question in my inbox. I've learned that for every person that bothers there are a bunch more with the same question, so I thought I'd take a break from relentlessly plugging my side hustle [Later for Reddit](https://laterforreddit.com/) to answer it publicly.

(Apologies to the most recent guy who asked this, because I'm copying and pasting large sections of this post from my email reply.)

### Just Starting Out? Learn Python

As far as I'm concerned, there's exactly one right answer here. Python is an astonishingly well-designed language. The syntax is simple but effective, the performance is good enough for most tasks, the standard library is probably the most batteries-included of any language, the significant whitespace forces you to format your code as you ought to be doing anyhow, and yet it's still flexible enough to [get weird with](https://unpythonic.com/).

![](https://imgs.xkcd.com/comics/python.png)

After you pick up a bit of Python, you can branch out in a few directions. Ruby is quite similar, and you wouldn't be ill-served to try it out. Java is a bit harder on your carpal tunnels than Python but is still increasing in importance after some 20 years.

### Desperate for Work?

If you want to do anything involving the internet, learn JavaScript. Just be careful - despite looking familiar, JavaScript is a very quirky language indeed, which is why I wouldn't recommend it as a first choice.

If you want a serious job with a serious company, learn Java (an almost-completely unrelated language). Just enough to write a basic `HelloWorldPrinterFactory` class, you can pick the rest up on the job.

Ultimately, learn both of these. Java is almost essential for high-throughput server software, and half the people who are shouting counterexamples at their monitors right now were going to name a JVM language anyhow. As for JavaScript, it's getting harder and harder to get by knowing no JS - even tooling is starting to become Javascript-flavored, and you might want to get a handle on some of those quirks I mentioned before you have to deploy it in production.

### Got This Far and Don't Know C? Learn C

If you are a professional programmer but don't know C at least well enough to read and understand it, you will probably feel a vague sense of shame about this fact. You are correct to feel so, but don't be discouraged. Knowing Java or C# will get you a lot of the way there, the rest is just pointer arithmetic and manual memory management, which you should absolutely know how to do just in case you need to someday.

C++ is a fine language, but nowhere near the mandatory level that C is.

### Want Low Memory Consumption and High Performance but Don't Want to Write C?

Try Go or Rust.

### Tired of OO and Want to Try Something Functional?

I highly encourage any developer to try them some functional programming. But, as has been pointed out elsewhere, "functional programming" probably puts the emphasis in the wrong place, since a lot of modern functional programming techniques emerge as an effect of working with immutable data. A nice side effect of this is that immutable data structure implementations exist for many languages, and once you know how to wrangle them in one language you can do it anywhere.

I'm a [well-documented fan of Clojure](https://adambard.com/blog/ten-reasons-to-use-clojure). It's still my weapon of choice for personal projects. Clojure has some nice performance characteristics over Python and other dynamic languages, especially with the core.async library letting you do go-style CSP concurrency but still maintains its brevity. It also has the best utilities for working with immutable collections of any language I'm aware of.

Haskell is also a very good language to know. It takes some effort to intuitively grasp the whole type system, but once you do you'll miss that surity whenever you use anything else.

Other options for educational-but-esoteric languages include:

  * OCaml
  * Erlang
  * Elixir (Erlang meets Ruby)

### The Final Answer: It Doesn't Really Matter That Much

Software is software. Different languages and libraries and runtimes and virtual machines and compilers and other such things will expose different tradeoffs, but in the end, your choice of language is secondary to your ability to solve problems in a way that a computer will understand. You can pick up the rest on the way. (Another plug: try [Learn X in Y Minutes](https://adambard.com/blog/what-programming-language/learnxinyminutes.com) for a quick primer on just about any programming language.)

If you ask me, your end goal is to get to the point where language is no obstacle - every language is some combination of other ones, and the more languages you're familiar with, the greater your head start picking up a new one. As long as you're learning something new, or trying to do things differently, you're headed in the right direction.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
