# Comments in Clean Code? Think Documentation

_Captured: 2017-02-14 at 19:18 from [dzone.com](https://dzone.com/articles/comments-in-clean-code-think-documentation?edition=268944&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-14)_

### When you need to convey information about code to developers, make your code clean. When it's for the business, use documentation. Code comments work for none.

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

Notwithstanding some oddball calculator and hobby PC hacking, my first serious programming experience came in college. A course called "Intro to C++" got us acquainted with arrays, loops, data structures, and the like. Given its introductory nature, this class did not pose a particularly serious challenge (that would come later). So, with all of the maturity generally possessed by 18-year-olds, we had a bit of fun.

I recall contests to see how much application logic we could jam into the loop conditions, and contests to see how much code could be packed onto one line. These sorts of scavenger hunt activities obviously produced dense, illegible code. But then, that was kind of the point.

Beyond these silly hijinks, however, a culture of code illegibility permeated this (and, I would learn later) other campuses. Professors nominally encouraged code readability. After all, such comments facilitated partial credit in the event of a half-baked homework submission. But, even still, the mystique of the ingenious, but inscrutable, algorithm pervaded the culture both for students and faculty. I had occasion to see code written by various professors, and I noticed no comments that I can recall.

## Professionalism via Thoroughness

When I graduated from college, I carried this culture with me, but not for long. I took a job where I spent most of my days working on driver and kernel module programming. There, I noticed that the grizzled veterans to whom I looked up meticulously documented their code. Above each function sat a neat, orderly comment containing information about its purpose, parameters, return values, and modification history.

This, I realized, was how professionals conducted themselves. I was hooked. Fresh out of college, and looking to impress the world, I sought to distinguish myself from my undisciplined student ways. This decision ushered in a period of many years in which I documented my code with near religious fervor.

![Image title](https://dzone.com/storage/temp/4288045-brandnewsetup.jpg)

My habit included, obviously, the method headers that I emulated. But on top of that, I added class headers and regularly peppered my code with line comments that offered such wisdom as, "increment the loop counter until the end of the array." (Okay, probably not that bad, but you get the idea). I also wrote lengthy readme documents for posterity and maintenance programmers alike. My professionalism knew no bounds.

## Clean Code as Plot Twist

Eventually, I moved on from that job but carried my habits with me. I wrote different code for different purposes in different domains but stayed consistent in my commenting diligence. This I wore as a badge of pride.

While I was growing in my career, I started to draw inspiration from the clean code movement. I began to write unit tests, I practiced the [SOLID principles](https://en.wikipedia.org/wiki/SOLID_\(object-oriented_design\)), I watched Uncle Bob talks, made my methods small, and sought to convince others to do the same. Through it all, I continued to write comments.

But then something disconcerting happened. In the clean code circles I followed and aspired to, I started to see [posts like this one](http://memeagora.blogspot.co.uk/2008/11/comments-code-smell.html). In it, the author had written extensively about comments as a something to avoid.

> Comments are a great example of something that seems like a Good Thing, but turn out to cause more harm than good. 

For a while, I dismissed this heresy as an exception to the general right-thinking of the clean code movement. I ignored it. But it nagged at me nonetheless, and eventually, I had to confront it.

When I finally did, I realized that I had continued to double down on a practice simply because I had done it for so long. In other words, the extensive commenting represented a ritual of diligence rather than something in which I genuinely saw value.

## Down with Comments

Once the floodgates had opened, I did an about-face. I completely stopped writing comments of any sort whatsoever, unless it was part of the standard of the group I was working with.

The clean coder rationale flooded over me and made sense. Instead of writing inline comments, make the code self-documenting. Instead of comments in general, write unit and acceptance tests that describe the desired behaviors. If you need to explain in English what your code does, you have failed to explain with your code.

Probably most compelling of all, though, was the tendency that I'd noticed for comments to rot. I cannot begin to estimate how many times I dutifully wrote comments about a method, only to return a year later and see that the method had been changed while the comments had not. My once-helpful comments now lied to anyone reading them, making me look either negligent or like an idiot. Comments represented a duplication of knowledge, and duplication of knowledge did what it always does: gets out of sync.

My commenting days were over.

## Best of All Worlds

That still holds true to this day. I do not comment my code in the traditional sense. Instead, I write copious amounts of unit, integration, and acceptance tests to demonstrate intent. And, where necessary and valuable, I generate documentation.

Let's not confuse documentation and commenting. Commenting code targets maintenance programmers and team members as the intended audience. Documenting, on the other hand, targets external consumers. For instance, if I maintained a library at a large organization, and other teams used that library, they would be external consumers rather than team members. In effect, they constitute customers.

If we think of API consumers as customers, then generating examples and documentation becomes critically important. In a sense, this activity is the equivalent of designing an intuitive interface for end-users of a GUI application. They need to understand how to quickly and effectively make the most of what you offer.

So if you're like me -- if you believe firmly in the tenets of the clean code movement -- understand that comments and documentation are not the same things. Also, understand that documentation has real business value and occupies an important role in what we do. Documentation may take the form of actual help documents, files, or XML-doc style comments that appear in Intellisense implementations.

To achieve the best of all worlds, avoid duplication. Make publishing documentation and examples a part of your process and, better yet, automate these activities. Your code will stay clean and maintainable and your API users will be well-informed and empowered to use your code.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
