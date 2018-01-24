# Testing Your Frontend Code: Part IV (Integration Testing)

_Captured: 2017-12-07 at 13:43 from [dzone.com](https://dzone.com/articles/testing-your-frontend-code-part-iv-integration-tes?edition=342109&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202017-12-07)_

Tips, tricks and tools for creating your own [data-driven app](https://dzone.com/go?i=247321&u=http%3A%2F%2Fplayground.qlik.com%2Flearn%2Fnoobs%2Fintro%3Futm_source%3Ddzone_web_dev_zone%26utm_medium%3Dbumper_text_1%26utm_campaign%3Ddzone), brought to you in partnership with Qlik.

A while ago, a friend of mine, who is just beginning to explore the wonderful world of frontend development, asked me how to start testing her application. Over the phone. I told her that, obviously, I can't do it over the phone as there is _so_ much to learn about this subject. I promised to send her links to guide her along the way.

And so I sat down at my computer and googled the subject. I found lots of links, which I sent her, but was dissatisfied with the depth of what they were discussing. I could not find a comprehensive guide -- from the point of view of a frontend newbie -- to testing frontend applications. I could not find a guide that discusses both the theory and the practice and is oriented towards testing frontend applications.

So I decided to write one. And this is the fourth part of this series of blogs. You can find the other parts here:

Also, for the purpose of this blog, I wrote a small app -- [Calculator](http://frontend-testing.surge.sh/) -- that I will use to demonstrate the various types of testing. You can see the source code [here](https://github.com/giltayar/frontend-testing).

## Integration Testing

So we've seen the two parts of the spectrum of testing -- unit testing your modules (or classes, functions, etc.), and End-to-End (E2E) testing of…well, everything. But a lot of testing happens between these two endpoints. Myself, and lots of other people, tend to call them integration tests.

### A Word About Nomenclature

Having talked a lot with TDD aficionados, I have come to understand that they have a different meaning for the term "integration tests." From their point of view, an integration test checks the "outer boundaries" of their code, the code that interfaces with the outer-world.

So if their code uses Ajax, or localStorage, or IndexedDB, and thus that code can't be unit-tested, they will wrap up the usage of those things in an interface, mock that interface when doing the unit tests, and test the real implementation of that interface with what is called an "integration test." An "integration test," from this point of view, just tests code that interfaces with the "real world" outside of those pure units that work without regards to the real world.

I, and others, tend to use "integration tests" to mean tests that check the integration of two or more units (again -- modules, classes, etc). Whether you hide the real world via interfaces that you mock (or whether you don't) is orthogonal (i.e. independent) to this.

My rule of thumb on whether to use real implementations of Ajax and other I/O in integration tests is this -- if you can do it and the tests still run fast and are not flaky, then test again the real I/O. If the real I/O is difficult, slow, or flaky -- then in the integration tests test using a fake/mock.

In our case, the calculator app, fortunately, the only real I/O is the DOM. There are no Ajax calls, so this question doesn't arise.

## Faking The DOM

This begs the question -- do we need to fake the DOM in integration tests? Let's try out my rule of thumb -- will using a real DOM make the tests slower? Unfortunately, the answer is "yes" -- using a real DOM means using the browser, and using the browser means, unfortunately, slow and flaky tests.

So either we somehow separate most of the code from the DOM, or we test most of everything in E2E tests? That's not good. Fortunately, there's a third solution: [jsdom](https://github.com/tmpvar/jsdom). This wonderful and amazing package does what it says -- it's an implementation of DOM _in Node.js_.

It works, it's fast, and it runs in Node. If you use it, you can stop treating the DOM as "I/O." Which is incredibly important, because it is very difficult (I would say practically impossible) to separate the DOM from any frontend code (I wouldn't know how to do it). I'm guessing that JSDom was written precisely for this reason -- to enable running frontend tests under Node.

Let's see how this works. As usual -- there's the initialization code, and there's the test code, but this time -- we'll look at the test code first. But first -- an apology.

## Apology

This part is the only part of the series that is framework-specific. And the framework that I chose to use is React. Not because it's the _best_ framework. I firmly believe that there is no such thing as the _best_ framework. I don't even believe, as others do, that there are _best_ frameworks for specific use-cases. No -- the only thing I believe in is that people should use the framework that they are most comfortable in, that they feel is the best for them.

And the framework _I_ am most comfortable in is React, and so the following code is React code. But as we shall see, the solution of using jsdom in frontend integration tests should work across all modern frameworks.

OK, back to using jsdom.

## Using Jsdom
    
    
        expect(displayElement.textContent).to.equal('0')

The interesting lines are lines 10 to 14. In line 10 we render the `CalculatorApp` component, which (if you follow [the code in the repository](https://github.com/create-oss/frontend-testing/blob/master/lib/calculator-app.js)) also renders the `Display`and `Keypad` components.

Then, in line 12 and 14, we check that the element in the DOM that shows the calculator display has the (initial) value of 0.

And this code, that is running under Node, is using `document`! The first time I tried it, it was absolutely amazing. The global variable `document` is a browser variable, yet here it is, in Node.js. A very large amount of code is needed to make those simple lines work. That very large amount of code, that sits in jsdom, is a mostly complete implementation of all that is in the browser, minus the rendering itself! (And I want to thank [Domenic Denicola](https://medium.com/@domenic), [Elijah Insua](https://medium.com/@tmpvar), and [the other contributors to this package](https://github.com/tmpvar/jsdom/graphs/contributors) for their amazing work.)

![](https://cdn-images-1.medium.com/max/800/1*KW3YGuqJk7ZNxDiPTuT7-A.png)

Actually, line 10 itself (the line that calls ReactDom to render the component), also uses `document` (and `window`!), as ReactDom uses them extensively in its code.

So who's creating those global variables? The test is -- let's look at the code:
    
    
        global.document = jsdom(`<!doctype html><html><body><div id="container"/></div></body></html>`)

In line 3 we are creating a simple document -- just a simple div that we can "hang" our component on.

Line 4 is where we are creating a global window that accompanies the object. Why do we need it? We don't, but React does, somewhere in its code.

The cleanup is just deleting those global variables so that they don't waste memory.

Does this `document` and `window` have to be global? Because global is bad. Not only for a theoretical reason, but also for practical ones -- if they're global, then we can't run these tests in parallel with other integration tests (sorry, users of [ava](https://github.com/avajs/ava)), because each would override the other's global variables.

Well, unfortunately, yes, they have to be global -- React and ReactDOM _need_`document` and `window` to be global -- you can't pass it to them. Maybe when React Fiber comes out? Maybe. For now -- we're stuck with global `document`and `window`.

## Handling Events

What about the rest of the test? Let's look at that.
    
    
      ReactDom.render(e(CalculatorApp), document.getElementById('container'))
    
    
        expect(displayElement.textContent).to.equal('0')
    
    
        const digit4Element = document.querySelector('.digit-4')
    
    
        const digit2Element = document.querySelector('.digit-2')
    
    
        expect(displayElement.textContent).to.equal('84')

The rest of the test checks one scenario -- tests the scenario where the user clicks "42*2=" and should get an "84."

And it does it in the nicest manner possible -- gets the elements using the well-known `querySelector` function, and then uses `click` to click on them. You can even create an event and dispatch it manually, using something like:

But the built-in `click` method works here, so we use that.

So simple!

The astute among you may notice that this test tests _exactly_ the same thing as the E2E test. True, but notice that this test is about 10 times faster, and is _synchronous_ in nature. It's much easier to write, and much easier to read.

But why, if the tests are the same, do we need the integration test? Well, because this is a toy project, and not a real one. Two components comprise the whole application, so integration and E2E tests do the same. But in a real application, an E2E test comprises _hundreds _of units, while integration tests comprise a few, maybe 10 units. So in a real application, there would be around 10 tests, but hundreds of integration tests.

## So Simple!

It's almost embarrassing how simple writing integration tests in Node is. Please -- go forth and do this!

## Summary

What did we see this week?

  * We saw how to test an app using jsdom.
  * And that's it. It is as simple as that!

Explore [data-driven apps](https://dzone.com/go?i=247322&u=http%3A%2F%2Fplayground.qlik.com%2F%3Futm_source%3Ddzone_web_dev_zone%26utm_medium%3Dbumper_text_2%26utm_campaign%3Ddzone) with less coding and query writing, brought to you in partnership with Qlik.
