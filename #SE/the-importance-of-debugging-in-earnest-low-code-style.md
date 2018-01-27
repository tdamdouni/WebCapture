# The Importance of Debugging in Earnest, Low-Code Style

_Captured: 2017-12-17 at 20:03 from [www.outsystems.com](https://www.outsystems.com/blog/importance-of-debugging-in-earnest-low-code-style.html?utm_source=dzone&utm_medium=daily-digest&utm_campaign=aud&utm_content=debugging-in-earnest)_

Occasionally there are those eerie moments as developers where things seem too good to be true. You're sitting at your desk. You've built a new and cool mobile app in low-code. You're testing out some of the logic in your visual model. The app is running on your iPhone. You're debugging the visual model. On a PC. Yep, I said, on a PC.

Then you wake up to find out you're still using Chrome DevTools, and it was all a dream… or was it?

![Visual Mobile Debugging Header](https://i2.wp.com/www.outsystems.com/blog/wp-content/uploads/2017/11/visual_mobile_debugging_header.png?w=590&ssl=1)

## How Low-Code is Your Low-Code Platform? A Philosophical Question

There has been a recent proliferation of no-code and low-code development platforms as vendors look to accelerate how organizations build mobile apps. In their latest [report](https://www.outsystems.com/1/low-code-development-platforms-wave/) on this market, Forrester tallied over 40. This comes as no surprise. Organizations are experiencing first-hand the benefits of developing solutions 10x faster, without the need for specialized skillsets and companies. Although the results often [sound too good to be true](https://www.outsystems.com/blog/quantifying-the-roi-of-low-code-platforms-is-it-too-good-to-be-true.html), vendors want to capitalize on that market momentum.

The purpose of this blog, however, is not to educate you on the breadth of low-code solutions, as this has also been [covered elsewhere](https://www.outsystems.com/blog/low-code-platforms-convergence-modern-app-dev.html). Instead, we pose a simple question: How low-code is your low-code platform?

By enabling developers (or even non-developers) to build mobile apps with visual models, low-code platforms address a number of problems plaguing IT. First, IT is able to deliver mobile apps significantly faster--which the business loves, of course. Second, IT is able to deliver those apps with their existing teams; therefore, there's no need to look for expensive mobile specialists--which IT loves, of course. Third, visual models are much simpler to understand, which means simplified maintenance and knowledge transfer. So, no creation of technical debt.

But here's the problem with current low-code platforms. Actually, there are two problems. First, most low-code platforms don't let you create true mobile apps. Instead, you have to make do with responsive web apps. No integration with the capabilities of the device? Slow screen rendering? No offline? Good luck winning new users with that app.

Okay, so let's focus on low-code platforms that actually let you build mobile apps people want to use. Development of the app is accomplished with a drag-and-drop approach. New screens quickly come to life; features and functions deliver new experiences customers never dreamed of. Then it comes time to try it out on the mobile phone and… it doesn't work.

## console.log("Here1");

Houston, we have that second problem. When the time comes to debug mobile apps, you have to step out of the comfort zone of low-code. Assuming your troubleshooting strategy doesn't involve a series of strategically placed print statements (yes, I may have been guilty of this in the past), how does debugging work for mobile apps in this new world? While there are many different approaches they generally involve the following:

  1. Configuring various network settings
  2. Different types of memberships (Adobe, Apple Developer, etc.)
  3. Generating certificates
  4. Configuring devices
  5. Connecting your favorite development tool
  6. Repeating steps 1 thru 6 for each permutation of device and developer operating system
  7. Debugging the code
![Visual Mobile Debugging baby](https://i2.wp.com/www.outsystems.com/blog/wp-content/uploads/2017/11/visual_mobile_debugger_02.png?resize=183%2C275&ssl=1)

Wait, run that last step by me one more time. Debugging code? I don't think I signed up for that. Let's take steps 1 through 6 out of the equation. It's left as an exercise for the reader to search for the term "mobile debugging" \+ [low-code vendor name] to see some of the shenanigans involved just to get ready to debug. Even without all of this setup, you're still left with a fundamental problem. To debug that mobile app you carefully crafted in low-code, you have to debug actual code.

More specifically, with most low-code platforms, we're talking about debugging JavaScript. The brave-hearted might be thinking, that doesn't sound so bad, I can understand JavaScript… it looks kinda like Visual Basic right? Here's a fun exercise… what does this snippet of JavaScript do? Try it out in a JavaScript console, it really works!

`([]+/H/)[1&11>>1]+(+[[]+(1-~1<<1)+(~1+1e1)+(1%11)+(1|1>>1|1)+(~1+1e1)+(.1^!1)])[[([]+!![11])[11^11]+[[{}]+{}][1/1.1&1][1]]+([[]+111/!1][+!1][([{}]+{})[1e1>>1]+[[],[]+{}][1&11>>1][1|[]]+([]+[][111])[1&1]+[{},1e1,!1+{}][~~(1.1+1.1)][1^1<<1]+(11/!{}+{})[1-~1<<1]+[!!{}+[]][+(11>11)][[]+1]+(/^/[1.11]+/&/)[.1^!1]+[{},[{}]+{},1][1&11>>1][1+1e1+1]+([]+!!{})[.1^!1]+([]+{}+[])[[]+1]+[!!{}+{}][!11+!111][[]+1]]+[])[(!/~/+{})[1|1<<1]+[/=/,[]+[][1]][1&11>>1][1&1>>1]+([]+{})[~~(1.1+1.1)]+[1,!1+{}][1%11][1^1<<1]+(111/[]+/1/)[~1+1e1+~1]+[!!/-/+[]][+(11>11)][1]]((1<<1^11)+((+(1<1))==([]+/-/[(!![11]+[])[+!1]+(!!/-/+{})[1-~1]+([]+!/~/)[1-~1]+(!!/-/+{})[!111+!111]])[11%11]),-~11>>1)](~1-~1e1<<1<<1)+([]+{111:1111}+[])[11111.1%11.1*111e11|!11]+({}+/W/)[1+~1e1-(~11*1.1<<1)]+(+[[]+(1|1>>1)+(1|1>>1|1)+(11-1>>1)+(1e1>>1|1)+(1e1>>1)+(1>>11)+(11>>>1)])[[(!!{}+[])[11>>>11]+[[]+{}][.1^!1][111%11]]+([11/[]+[]][111%111][([{}]+[{}])[1e1>>1]+[[],[{}]+[{}]][1|1>>1|1][1|[]]+([][11]+[])[[]+1]+[{},1e1,![1]+/~/][1<<!1<<1][1<<1^1]+(1/!1+{})[11+1>>1]+[!!/-/+{}][+(111>111)][111%11]+([][11]+/&/)[1&1>>1]+[{},[]+{}+[],1][[]+1][11-~1+11>>1]+([]+!!/-/)[11>>11]+([]+{})[1|1>>1|1]+[[]+!!{}][1>>>1][1&11]]+[])[(!{}+[])[1^1<<1]+[/=/,[]+[][1]][1<<1>>1][!111+!111]+([]+{}+[])[1<<1^1>>1]+[1,![11]+[]][1|1>>1][1|1<<1|1]+(11/[]+/1/)[-~11>>1]+[!![111]+{}][+[]][1|1>>1]]((1e1-1)+((1&1>>1)==([]+/-/[(!!{}+{})[+(1>1)]+(!!/-/+{})[1|1<<1]+(!1+{})[1|1<<1|1]+(!!/-/+{})[11.11>>11.11]])[1&1>>1]),1-~1<<1)](~1-~1e1<<1<<1)+(/^!/+[])[1+!![11%111]]`

This might be an extreme example, but the fact is you're developing your mobile app in low-code using visual models. Therefore, you didn't write any of the JavaScript that you'll need to debug. You'll be examining whatever blob of code your low-code platform decided to generate.

## What's the Big Deal?

Yeah, what's the big deal? Maybe my code won't have any bugs [insert alternate reality here]. Not surprisingly, it turns out developers spend, depending on the source you choose to believe, between 25% and 50% of their time debugging applications. And this isn't time developers tend to look back on fondly.

![Visual Mobile Debugging T-Shirt](https://i2.wp.com/www.outsystems.com/blog/wp-content/uploads/2017/11/visual_mobile_debugger_03.png?w=420&ssl=1)

After the delight and simplicity of building your mobile app with low-code, this is quite the slap in the face. Worse still, what if you don't have the technical expertise to do this? Remember the second promise of low-code from up above? IT should be able to deliver mobile apps with their existing teams.

I was speaking with a new customer recently who had just retired an older 4GL financial package. They were looking for ways to retool the team members who had been working on that package and first looked at training them as .NET developers. The feedback was universal; coding was not for them. The team then tried OutSystems. Building visual models to create apps felt familiar and they were very successful in delivering new solutions for the business. This team would run into a wall if they had to read generated code to debug apps running on a mobile device. What should they do? Should IT keep a stable of JavaScript/mobile experts on hand on the off chance the app doesn't work as expected the first time? Clearly, this is not a viable solution.

## How Debugging Should Work

The real solution to this problem is simple, conceptually. You should be able to debug your low-code apps using the same visual models that you used to define them. These are the models you created after all: your logic, your business rules, your data structures. You should not have to step through some sort of generated code written in a language you may or may not understand.

We had already come to this realization for developers who were building web applications some time ago. They needed a complete low-code solution--including the ability to visually debug logic running on the server. With the release of OutSystems 10 last year came an entirely re-architected approach to mobile applications. For the first time ever, developers could build sophisticated mobile apps entirely with low-code visual models. These apps run complex logic on the device, removing the need to go back to the server any time a decision needs to be made. These apps connect to native device capabilities like sensors, calendars, contacts, touch ID, to create a completely immersive experience. These apps support different patterns for synchronizing offline data to address the most complex of requirements. These mobile apps needed the same intuitive approach to debugging as the server-side code.

![Visual Mobile Debugging in Action](https://i0.wp.com/www.outsystems.com/blog/wp-content/uploads/2017/11/visual_mobile_debugging_new.gif?resize=590%2C332&ssl=1)

With this most recent release and some amazing feats of engineering, developers can now debug mobile apps in exactly the same way they are used to debugging server-side visual models. Check out how to use it [here](https://success.outsystems.com/Documentation/10/Developing_an_Application/Troubleshooting_Applications/Debugging_Applications). Set breakpoints, examine variables, step through your visual code--no problem. Simply attach your iPhone or Android device and you're off. No arduous setup process. No additional tools. No special skillsets. This is exactly how debugging should be for mobile apps built with a low-code platform.

So, how low-code is your low-code platform? If it doesn't support simple debugging of your mobile apps, then the answer is simple. It's not low-code enough.

An accomplished "IT Renaissance Man", Mike has worked in diverse roles from developer to business analyst, architect to project manager, account manager to sales manager. All this knowledge culminates in a single-minded focus on helping clients become their own IT success stories using OutSystems low-code platform.
