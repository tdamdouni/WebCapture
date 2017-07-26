# Exploring Apple’s 3D Touch

_Captured: 2015-10-16 at 10:21 from [medium.com](https://medium.com/@rknla/exploring-apple-s-3d-touch-f5980ef45af5)_

I was pretty giddy when Apple revealed 3D Touch at their September event. In a past work-life, I was working with TouchCo's developer kit at around the same time that [Roger Linn was experimenting](http://createdigitalmusic.com/2010/05/roger-linn-imagines-a-new-multi-touch-instrument-and-help/) with the ideas that would become the [Linnstrument](http://www.rogerlinndesign.com/linnstrument.html). TouchCo got bought, my project morphed from hardware to software as the company turned into [Zya](http://www.zyamusic.com), and I moved onto other things, putting the interest and ambition in gesture control on the backburner.

With Apple's announcement, that excitement rushed back to me: not only would it be relatively cheap to get a development kit -- just the cost of the phone -- but it also fits in my pocket, and has a huge existing user-base and app economy.

Now that the phone is out and in the wild, I've had a chance to experiment a bit with making a basic MIDI controller. In the process, I've learned some interesting things about Apple's 3D Touch APIs that I'm sharing here in hopes that it will be helpful for other folks interested in developing on the platform.

#### **The public APIs**

First, let's start with Apple's published documentation. On supported devices, each UITouch now has the following relevant new properties:

Tangentially relevant, Apple's API also exposes whether or not the "touch" is coming "directly" from a finger on the screen, "indirectly", or from a stylus. Presumably the indirect touches are coming from an accessibility framework, or some other kind of input device. Since I'm interested in musical applications that don't require any additional hardware, I'm only really concerned with the above two properties. But, the documentation leaves me with the questions that I explore below.

What kind of behavior does _force_ have? Is the output linear, or predictable? And what should I expect for _maximumPossibleForce_?

### Beginning the experiments

#### maximumPossibleForce

Answering the last question was perhaps the most straight-forward. Spinning up a project and listening for a touch in a view, I can print the touch's _maximumPossibleForce_. On my iPhone 6S, it's 6.666666666667. I haven't tested it on a 6S Plus.

Even after all of this research, this max value still seems pretty bizarre to me. I was originally expecting a number on the unit-interval or something, or at least a number between 1 and 100. But a number between 0.00 and 6.6666667? Color me confused.

Perhaps the range is different with a Pencil, or on different devices.

#### touch timing

In making a basic MIDI controller, one of my primary interests in the _force_ value is computing the velocity of a note trigger, meaning I'll want to map the force's native CGFloat value to a number between 1 and 127 (a Note On message with a velocity of 0 is usually interpreted to be synonymous with a Note Off message).

To start with, as the name "velocity" implies, I'm ideally interested in calculating a change of force, so one of the first things I looked at was the UITouch's _timestamp_ value between update callbacks. After some quick eye-ball tests, I could see that, with the debugger on, my touch sample rate is approximately once every 10-15ms. For context, a 16th note at 120bpm lasts 125ms, and an audio engine running with a 256 frame buffer at 44.1kHz sample rate has a single-buffer latency of ~5.8ms.

While I was looking at these timestamps, I noticed something else interesting about the force values. Most of the time, but not 100%, the force of the very first touch that comes through the _[touchesBegan_](https://developer.apple.com/library/prerelease/ios/documentation/EventHandling/Conceptual/EventHandlingiPhoneOS/multitouch_background/multitouch_background.html#//apple_ref/doc/uid/TP40009541-CH5-SW3) is actually 0.00.

From my perspective, this means that I'm basically forced into looking at the first two touch values to calculate any kind of meaningful velocity, but depending on what you're doing with 3D Touch, this quirk is worth being aware of: **_The first force is usually 0.00_**.

#### force quantization

The next thing to catch attention, and subsequently send me into a flurry of investigative Python coding, was the nature of the _force_ values that I was seeing at the gentle-pressure end of the spectrum. At extremely light force levels, I was mostly seeing the actual force value fluctuate between one of a few specific numbers. Yes, they are floating point, but they also exhibited extreme uniformity to the point that it was easy to hypothesize that the actual values were merely integers divided by a multiple-of-3 divisor.

The lowest non-zero _force_ that I saw was always 0.016666666667, which seemed to be just as bizarre as the arbitrary 6.666666667 maximum value. So, I decided to investigate a bit.

First, some basic math to get us started: 0.01666667 is 1/60. If the float values actually _are _just integers divided by a common divisor, that divisor might be 60.

Next, we can this hypothesized divisor, 60, and multiply it by the maximum value to get the high end of the range: 6.666667 * 60 is 400.

Ok. Now we have some context to design the experiment: Let's try to generate collect all of the possible force values across the range to see if the floating point values correspond to an integer range between 0 and 400.

To set up the experiment, I used a Set of the CGFloats to store unique force values, and log to the console whenever a new value is successfully added to the set.

With this integrated into my app, I went to town trying to generate as many points in the touch spectrum as possible, to make the set exhaustive. When I was done with the pressure testing, I stopped the debugger, and copied the log to a text file for some Python processing. I had plenty of other console logs in the app to make the actual logs a bit messy, but the above log message is unique to that code path, so I was able to use a simple regex to extract the _touch.force_ value from the string.

The dataset generated is also [publicly available as a gist](https://gist.github.com/rknLA/e687e5b0193dd1d6336d).

At this point, I can finally start asking the Python repl questions.

How many unique forces had I collected?
    
    
    >>> len(sorted_forces)  
    336

Out of the hypothesized 400, this isn't so bad!

Finding the distribution of the actual _force_ values was a bit more involved. I started by using _pprint_ on the sorted list and manually looking at the values at the beginning of the list. The first handful of values seemed to match up pretty well. Everything going up in 1/60 increments.
    
    
    [0.0,  
     0.0166666666666667,  
     0.0333333333333333,  
     0.05,  
     0.0666666666666667,  
     0.0833333333333333,  
     0.1,  
     0.116666666666667,  
     0.133333333333333,  
     0.15,  
     ... ]

Looking at this list got pretty exhausting pretty quickly, though, so how about a quick loop to extract the actual differences?

Now we have a distances list that runs in parallel to the _sorted_forces_ set. Using _pprint_ again, we can look at the distances. So far, we're seeing data that supports our hypothesis: a long stream of _0.0166666666667. _This list turns out to be much easier to manually scan, since all of the numbers are the same… until suddenly one is different.

Visually, it seems that the first anomalie is pretty far down the list, and it prompts the question: where do the anomalies occur, and do they occur because our sample set isn't exhaustive, or because the hypothesis is wrong?

Let's explore this a bit more with some list comprehensions:
    
    
    indexed_distances = { ix: val for ix, val in enumerate(distances) }

This gives us a javascript-style array-object, where we can see both the item, and its index in the dictionary, making it easier to visually scan for the anomalies. We can also use it to programmatically extract the anomalous indices.

Since we're expecting values to be 0.01666666667 or multiples of that number, we're bound to encounter some floating point rounding issues, and precision issues in comparing the values, so we simplify the math a bit by multiplying everything by 60, rounding to the nearest integer, and then casting to int. This leaves us with 0.0166666666666666667 mapped to 1, making for an easy comparison.

At this point, I can see that, of my 336 touch values (and the 335 intervals between them), only 42 intervals differ from the expected 0.0166667. I can also see in my own dataset that the indices don't appear to be clumped together in any meaningful way.

The highest questionable index is 332, meaning the values at indices 333, 334, and 335 are all spaced 1/60 apart. Revisiting the dataset, we can see that the highest index value is indeed the maximum value of 6.66666666667. This means that the maximum, and the 3 possible values that showed up below it all correspond to the same intervals that we saw on the low end. This is pretty promising support of our hypothesis so far, but what about the intervals associated with those _questionable_indices_?

To compute an integer-interval stride analogous to the original distances we extracted, we can use a variant of the integer rounding technique we used to generate the _questionable_indices_.
    
    
    integer_stride = int(round(val * 60 * 100)) / 100.0

The only difference between this and the above is that we get a float value out, and the rounding happens with the decimal place moved over two spots, giving us two places of precision to the right of the decimal. If these values are just "missed data" rather than non-linearities, we expect them to be multiples of 1/60, and thus to see a whole-number _integer_stride_ value. If there are non-inearities, then the two digits to the right of the decimal place should be non-zero.

We use another comprehension to generate this value for each of the questionable distances:

The resulting dictionary contains the questionable indices as keys, and the integer strides as values.

Sure enough, with this dataset, these are all integer values between 2 and 5.

### Conclusions

At this point, it seems pretty safe to say that the floating point value that Apple propagates to the developer interface is actually an integer between 0 and 400 that's divided by 60 somewhere along the way.

#### Why would Apple do this?

My initial guess is that it's two-fold, and the first is liability/cost/safety. The nearest power-of-two multiple to support the maximum force value is 512, or a 9 bit register. In all likelihood, they're able to generate force values that go higher than the 6.666667 that's documented, possibly all the way up to the 8.5166667 value that corresponds to 511/60

But, I do have to apply a pretty serious amount of force to get the sensor to rail to 6.666667. Serious enough that people would probably bend or break their phones if developers encouraged them to hit it hard enough. Just imagine a [High Striker](https://en.wikipedia.org/wiki/High_striker) as the App Store's next big hit.

The second reason here, I think, is related to usability and forward compatibility. Apple doesn't specify how many newtons of force the phone can take, and probably for good reason. People, in general, don't have a deep, fundamental, quantitative understanding of how much force they use when they push buttons or tap their phone. In musical instruments (acoustic and digital), there is certainly a qualitative grasp on force, but it's difficult to bridge that grasp to the quantitative realm. This is why DAWs and virtual instruments offer customizable velocity curves.

By providing developers with a starting range of 0 to about 6, with some overflow up to almost-7, Apple has inferred some usability guidance for general purpose applications: You can probably get away with segmenting your pressure sensitivity into 6 compartments, but more precision than that becomes a burden more than it helps. And in fact, if you look at Apple's own implementations that use force, they're only really creating three segments: normal touch, and Peek pressure, and Pop pressure.*

The forward compatibility point is related: On future devices, they may likely have force sensors with higher precision (the technology always gets better, right?). If they exposed this value as an integer, then any new precision must be added on top, which would create a usability nightmare for existing apps running on new, higher-precision devices -- suddenly the 100 force required to fling my angry peacock at the bowling pins has doubled!

By using a floating point value, the increased precision can go in the middle, keeping the force required to generate a 1.0 value the same, but offering granularity that's finer than 1/60.

_*Edited: The original post claimed that Apple creates two segments in pressure sensitivity: normal touch, and forceful touch. While this is true on the home screen, their Peek and Pop functionality creates three segments._
