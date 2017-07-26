# How CAPTCHA Works

_Captured: 2017-02-21 at 01:44 from [blog.jscrambler.com](https://blog.jscrambler.com/how-captcha-works/)_

![how-captcha-works](https://blog.jscrambler.com/content/images/2017/02/captcha-2.png)

## What is CAPTCHA?

You are surely familiar with this technology, even if you don't really know the name. CAPTCHA stands for _Completely Automated Public Turing Test to Tell Computers and Humans Apart_. Its goal is to check if a user (of an app or a website) is a real person or a bot. To do that, it relies on specific traits that people have and machines don't. It's widely used in the web industry as a good protection against spam, bots or DOS attacks.

## Why do we need CAPTCHA?

There are a lot of people out there who want to harm your website, for different reasons. Unfair competition, advertising, sometimes malicious behavior or just fun. You can imply it's not the majority of web users that are trying to exploit your system's weaknesses, but the problem remains.

The simplest example is the DOS (The Denial of Service), which is a type of attack that is focused on making a resource unavailable. The attacker sends a big amount of requests to the server to make it incapable to return results. It simply blocks your website. Doing this attack individually, by a real person, would be a horror. It would be boring, exhausting and simply impossible. You can't manually make the efficient amount of requests, but computers don't get exhausted or bored. It's not a problem for them to make hundreds of requests every... second. CAPTCHA helps you to identify such behaviors and block them.

Another example is malicious advertising tactic. Every internet user is familiar with spam. You receive tons of unwanted emails every day. It's easy to block one particular email, but it's hard to protect against unknown ones. If a spammer uses only one email account, we can easily block it. But imagine now that he/she hires a bot to use one of the free email providers (the one that doesn't use CAPTCHA). That way, it can set up a new account every several minutes and send spam content from the different addresses.

A third example, more trivial - comments. A lot of websites, even small blogs, are fighting with unwanted adverts. Of course, we can turn a blind eye on one or two spam messages. Unfortunately, we often see hundreds of them. It's usual to find well-written content with a spammed comments section. If you see a post with hundreds of the same message (not really related to the text), the owner probably doesn't use CAPTCHA. Even for real people, but with evil intentions (so-called "trolls"), it can be a discouraging barricade.

## How does it work?

CAPTCHA roots date back to the beginning of the twentieth century when Alan Turing wanted to answer one question - Are computers able to think like humans? He set up a game of imitation, where an interrogator was obligated to ask two participants series of questions. The participants were humans and machines. The interrogator's challenge was to figure out which one was the human being. The interrogator was unable to see or hear them and needed to rely only on responses. If the interrogator was unable to decide or decided wrong, the machine passed the Turing test. The CAPTCHA goal is to ask such question or to make such challenge that computers are unable to deal with. At the same time, it should be easy to answer for humans.

The scheme is simple. You type some data or perform any other action and then confirm it by passing a CAPTCHA test. The most common type of test is an image of a bunch of distorted letters. It uses the issue of computers not being able to think abstractly and "see" the world the way people do. While humans are really sophisticated with processing visual data, computers lack those skills. When you look at the image, you can quickly read the pattern. The brain of humans is constructed in such a way that it's always searching for a known pattern or shape. You know the paradox of seeing faces and shapes in trees, clouds... even it's just an illusion. It's called pareidolia.

![captcha-request](https://blog.jscrambler.com/content/images/2017/02/CAPTCHA1.png)

While you are easily able to read the above words and write them down, for computers it's just a mass of zeros and ones. Nevertheless, we have to remember how machines work. CAPTCHA's challenges shouldn't be limited to any fixed number. If they would, it would be easy to teach a computer which text corresponds to a given image. Therefore, many creators use sophisticated algorithms in order to generate their distorted texts randomly. Creators of reCAPTCHA figured out another idea. They used the process of... digitalizing books and asked users to decrypt the short pieces.

Due to the evolving bot algorithms, text-distorted CAPTCHAS have become a lot harder to solve. Just look at the two examples below.

While the first one is quite readable, the second one could already cause some problems for someone without a sharp eyesight. Therefore, a lot of developers tried to think out a new type of CAPTCHA. The result of their work was select-images CAPTCHA.

![select-images-captcha](https://blog.jscrambler.com/content/images/2017/02/CAPTCHA4.png)

It relies on the same foundation, but it's just harder to solve for machines. And what's more important, it's easier to solve for humans.

The scheme is easy. You have a collection of images and have to pick the ones that match the requirements. It's easy for you to pick the right ones. Computers, however, don't think like humans and it's not so easy for them. It relies on a [classic computer vision problem of image labeling](https://en.wikipedia.org/wiki/Computer_vision ). Also, it's really mobile-friendly. It's easier to tap images corresponding with a clue than type a line of distorted text.

These approaches have their cons. For machines, they're hard to solve, but text-reading systems are also just algorithms. Thus, they encourage problems with reading CAPTCHAs and are treated like bots. For blind people and people with different eyes dysfunctions, it causes a technological barrier. With that in mind, developers often add sound-CAPTCHA to their text-distorting solutions.

![sound-captchas](https://blog.jscrambler.com/content/images/2017/02/CAPTCHA5.png)

It works in a similar manner. The script adds additional background noise to audio in order to make it harder for bots to solve. It has a small impact on humans, but it adds a lot of problems for voice-recognition programs.

While all these solutions are perfect on paper, they can still be annoying and confusing. Therefore, Google introduced a new CAPTCHA (No CAPTCHA reCAPTCHA) that asks you only to check a box.

![No-CAPTCHA-reCAPTCHA1](https://blog.jscrambler.com/content/images/2017/02/CAPTCHA6.png)

## CAPTCHA Example

You already have some overall knowledge about different types of CAPTCHA. Now I want to tell you more about the newest and the most popular solution - noCAPTCHA reCAPTCHA.

It was created as a result of the quite obvious realization. Bots got so advanced that it's now impossible to generate images that are easy to solve for humans but unsolvable for them. As spammers get more and more sophisticated, images got harder and harder to read. But Google's research showed that it's a dead end. Today's AI technology can solve even the most difficult distorted texts (almost 99.8% accuracy).

So instead of making it harder for humans, they've decided to find a way to make a more advanced algorithm. Its goal is to make the checking process easy for you but still effective for protecting against bots.

We can't say how it really works in detail, because - it's understandable - it's not available for the public. What we know is that Google created sophisticated analyzing technology. It somehow tries to guess if you're a human or not. If it thinks you are, you just have to check a box to prove it.

![No-CAPTCHA-reCAPTCHA2](https://blog.jscrambler.com/content/images/2017/02/CAPTCHA7.png)

It's simple, accessible and not annoying. If the analysis isn't enough to decide, the system asks you to solve select-image CAPTCHA. If it's still not enough, it asks you to solve a more classic CAPTCHA, but a lot harder than old ones.

![No-CAPTCHA-reCAPTCHA3](https://blog.jscrambler.com/content/images/2017/02/CAPTCHA8.png)

Okay, now let's get back to analyzing the engine behind. We don't know the details, but let's try to think how could it work. [At GitHub](https://github.com/neuroradiology/InsideReCaptcha ) you can find a great analysis what steps reCAPTCHA takes to make it all work. Combining it with the paper "[I'm not a human: Breaking the Google reCAPTCHA"](https://www.blackhat.com/docs/asia-16/materials/asia-16-Sivakorn-Im-Not-a-Human-Breaking-the-Google-reCAPTCHA-wp.pdf ) (by Suphannee Sivakorn, Jason Polakis, and Angelos D. Keromytis), we know that the script gathers at least information about:

  * Plug-ins
  * User-agent (it tests if it's real)
  * Execution time, timezone
  * Number of click/keyboard/touch actions in the `<iframe>` of the CAPTCHA
  * Likely cookies server-side

and it...

  * compares environment with the behavior of many browser-specific functions and CSS rules
  * checks the rendering of canvas elements.

Also, screen resolution and mouse events don't really matter. We use different devices, we use tablets (there is almost no mouse behavior), so it seems wise. In the paper, you can also read that keeping a cookie active for +9 days allows you to pass reCAPTCHA by only clicking the checkbox.

Is the CAPTCHA a secure solution? In order to break a CAPTCHA completely, you would have to try to manipulate your computer to think in a human manner. It's not really possible, but there are some workarounds. Computers try to detect the text at least partly and "guess" what's the result or use sophisticated algorithms. It's really helpful for them to have a database of already broken CAPTCHAs string. There are websites that even pay their users for solving the image CAPTCHAs. It seems that it can be really helpful for bots in the fight with CAPTCHA.

As long as people know about computers weaknesses, they will try different approaches. They will try to tackle CAPTCHA by reducing its complexity. A clever hacker would look at generated CAPTCHA and analyze what makes them so hard to solve. Is there something in the background? Let's play with contrast and get rid of middle values. If you make your image black and white, your challenge will be much simpler. If you'll take into account enough amount of factors, you'll be able to build a really working algorithm.

Nobody thought that image CAPTCHA would always be safe and it was a matter of time that it would be cracked and... it already was. For a long time, Google image reCAPTCHA system seemed like a safe choice. Unfortunately, researchers already taught the machine to guess the correct answer. At 70.78 percent accuracy, as they recorded. It's a great result, with an average time of solving less than 20 seconds. The Facebook CAPTCHA system failed even worse with 83.5% of success rate.

A lot of image CAPTCHA systems failed against advanced algorithms. Jennifer Tam, Jiri Simsa, Sean Hyde, and Luis von Ahn (all working for Carnegie Mellon University, Pittsburgh) wanted to figure out if it was easy to fool sound CAPTCHA as well. They succeeded with some of them. In the spring of 2012, there were reports that Google's audio CAPTCHA system had been broken with a 99% success rate. The engineers made a little oversight. The noise background (the main protection) didn't use the high-frequency sounds. It made it easy for the hackers to isolate each word by locating the regions with higher frequencies.

And what about the newest solution - noCAPTCHA reCAPTCHA? This technique may seem harder to crack but is not unbreakable. This year the security experts from Columbia University have deployed an attack technique against Facebook and Google noCAPTCHA reCAPTCHA. They succeed with 41.57 percent success rate (at about 20 seconds per challenge). It's less than 50%, but it's enough for bots to make your website spammed. They can bombard you with hundreds of requests per minute after all. How did they crack it? They created their own sophisticated reCAPTCHA-breaking algorithm and compared it with other available CAPTCHA-breakers. Thanks to that they've deployed a balanced solution. They've achieved such success while in offline mode. So, we can presume that a lot of noCAPTCHA reCAPTCHA power comes from analyzing user history, inaccessible without the internet connection.

## Cons of CAPTCHA

CAPTCHA is widely used and it can be really annoying. Let's be honest - typing some strangely shaped letters or solving any other types of challenges over and over is simply irritating. Ok, we know why developers use it. Nevertheless, it looks like they're trying to shake off their responsibilities and make it yours. By saying that, you would be partly right. There is some truth in it, but it's really hard to find another way to do that. You can try some sophisticated algorithms, but in most cases, it's easy to fool them.

Another problem - accessibility. Even if you have great eyes, you can face problems sometimes. Identifying a valid text or image (select-image CAPTCHAS) isn't always a simple thing. And what if your vision is a little blurry or you have some kind of eye dysfunction? The audio version seems a perfect solution, but it often has poor quality. And what if you use text-only browsers or don't have a sound card installed?

CAPTCHA also consumes your time. You could say it only takes 2,3 seconds but now imagine that every website uses it. How many of them do you visit a day? How many actions could a site ask you to perform in order to verify your humanity?

A CAPTCHA can harm your website usability and accessibility. Even if the new reCAPTCHA made by Google deals well with it, not every system is so good at that.

## Conclusion

It seems there is no perfect solution. With every new generation of CAPTCHA, there are new generations of bots. The more sophisticated algorithms you use to protect from them, the wiser they become. But does it mean CAPTCHA is completely unuseful and just annoys users? No, the idea is still good. Even simple CAPTCHAs represent a significant barrier for most primitive bots. We shouldn't deprive of it but please note that CAPTCHA does not protect you and/or your users about data/credentials leakage, which can be triggered by any third-party scripts included in the page, browser extensions or a MitB trojan.

Do you want to know more? Here are some helpful links:

_CAPTCHA's goal_

_Breaking CAPTCHA_

_How Google's noCAPTCHA re CAPTCHA works?_

_CAPTCHA accessibility_

![promotion](https://blog.jscrambler.com/assets/images/94a9d166fe534df505a5ba174799496d.png)
