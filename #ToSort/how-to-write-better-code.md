# How to Write Better Code

_Captured: 2018-07-01 at 21:16 from [dzone.com](https://dzone.com/articles/how-to-write-better-code?edition=383282&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-01)_

Discover how you can [take agile development to the next level](https://dzone.com/go?i=294434&u=https%3A%2F%2Fwww.mendix.com%2Fresources%2Ftaking-agile-development-to-the-next-level-with-low-code-mx%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone) with low-code.

[My previous blog post](http://johannesbrodwall.com/2018/06/24/forget-about-clean-code-lets-embrace-compassionate-code/) took off on Twitter. This post pointed out one problem -- the obligation to follow certain rules at all times isn't actually helping people code better. The most common question (or objection) I got to the blog post was "how do we teach new coders how to code well?" In this blog post, I attempt to answer that question.

## Learn to Collaborate

The most important skill we should teach new coders is how to work well with others on a shared code base. In my career, it took me many years to I get good at this, but it had the most impact on my overall effectiveness. So, this is where I want to start with developers who are getting ready to join the workforce. On almost all projects we work on, our success depends on others.

Here are some techniques that have worked well for me:

  * Pair programming -- Good pair programming requires training, but there are training styles, like coding dojos and code retreats. Some of the best programming instructors in the world use pair programming actively as part of their training.
  * Code reviews -- I work so much with pair programming that I personally give code reviews a lower priority. However, many teams find great value in them.
  * Patience -- When working with pair programming, it's easy to get stuck in arguments. Our profession says almost nothing about interpersonal skills, yet we depend on them all the time. Try this: When you are pair programming and you see your pair making a mistake, wait to see if he/she spots it themselves before breaking in.
  * Humility -- I often get asked, "how do I convince others to write clean code?" Of course, the question assumes that you're right and they are wrong. Most of us struggle with the skill of changing our minds. When pair programming, if your pair wants do something that you think is wrong, try indulging them. The worst thing that could happen is that you get the chance to teach them something. At best, you learn something yourself!

Unless you are in a situation where you write all the code yourself, collaboration skills are paramount. It doesn't matter if you "know" what the code should look like if you can't agree with your team.

## Now, Let's Talk About Code!

If you are one of the people who skipped ahead to this section, please go back and read about collaboration. Seriously. Nothing I say about code will help you if you can't work well with others.

Go ahead, read it again. I'll wait here.

Good to see you back! Now, let's talk about learning to write good code. Of course, good code is crucial to professional success. If the code base is better, you spend less time fixing bugs, have an easier time changing the code, and your team will have a better time working with you.

Learning to write good code is quite simple -- you have to read code, you have to write code, you have to change code, and you have to delete the code and start over again.

For the first of these points, great books help you to read code. Some books that I strongly recommend are _Clean Code_, _Implementation Patterns_, _Refactoring_, _The Art of Agile_, _Pragmatic Programmer_, and _Practices of an Agile Developer_. I've enjoyed reading all of these books immensely. These books will teach you considerations such as low coupling, high cohesion, and simple design. They will teach you useful principles like the Single Responsibility Principle and the Open-Closed Principle (although I find I almost never refer to the rest of SOLID). The patterns and principles teach you new information and code to discuss with your team.

For the second of these points, Test-Driven Development is one great way to learn how to write code. I enjoy doing coding katas myself and often use them for teaching. But, the most valuable skill when writing code is one I learned at code retreats (thank you, Corey Haines!). It is essential to learn when to delete the code you write. I don't just mean refactor it in order to be smaller. I mean that, for coding exercises, highlight all the files and press the delete button. I mean for production code, after spending a few hours working on a task, (occasionally) use `git reset --hard HEAD`.

The hallmark of great code is how easy it is to change. Can you navigate in the code? Can you spot errors quickly? Do you know where to make a specific change? You can learn by reading about principles, but the safest teacher is to expose yourself to more experience. When you write and change code, it causes you to reflect on the limitations of the code and your current skillset impedes the changes you want to make.

In short, code more, listen to the code, and listen to your peers.

## Can You Release Smoothly

I almost forgot the #1 quality of good code -- it has to be used! Release cycles of teams can vary from several times per day until a few times per year. If you can release your code at will, you can learn both about your code and your users. When the whole team learns that you will release again tomorrow, or next week, priorities of "now or later" get easier. When you release only a few times a year, people get stressed and discussions get heated.

I've almost always found that teams under-appreciate the value of spending time on build and deployment tools and scripts.

## "Don't Do Stupid Stuff on Purpose"

If you find code that you're unhappy with, it bears remembering that it is that way because it got that way. People did what they did because of reasons. Those reasons are valid, whether it was because the surrounding needs changed, the developer had insufficient experience, the pressure to finish, they wanted to go home to their family instead of sitting late in the office, or, maybe, they just had a difference in opinion on what's good code.

Not everyone agrees with this, but "what about those who just don't care?" After 20 years of working as a programmer, I have never encountered anyone who just didn't care. I have encountered programmers who had different preferences from my own. I've encountered programmers who are delivering under short deadlines. I've encountered programmers who get praised for making apparent progress at the expense of writing good code. And, I've encountered many programmers who don't care _as much as me_ about the code. Having other interests in our life is an excellent reason to spend less time polishing code.

But, I've never encountered a programmer who just doesn't care. Have you? I'd love to learn from your story.

[Download this eBook ](https://dzone.com/go?i=294435&u=https%3A%2F%2Fwww.mendix.com%2Fresources%2Ftaking-agile-development-to-the-next-level-with-low-code-mx%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone)to learn how to prepare your business for agile adoption, how to ensure the proper business-IT collaboration that is critical for agile development, and how to choose the right stakeholders to increase productivity and enable accelerated time-to-value.
