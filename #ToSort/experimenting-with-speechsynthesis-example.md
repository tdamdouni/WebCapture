# Experimenting with `speechSynthesis`, example 1

_Captured: 2017-02-15 at 04:30 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/02/experimenting-with-speechsynthesis/)_

  * [0 Comments](https://www.smashingmagazine.com/2017/02/experimenting-with-speechsynthesis/)

Meet the new [Sketch Handbook](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1), our brand **new Smashing book** that will help you master all the tricky, advanced facets of Sketch. Filled with **practical examples and tutorials in 12 chapters**, the book will help you become more proficient in your work. [Get the book now ->](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1)

I've been thinking a lot about speech for the last few years. In fact, it's been a major focus in several of my talks of late, including my well-received Smashing Conference talk "[Designing the Conversation](https://vimeo.com/184234783)." As such, I've been keenly interested in the development of the [Web Speech API](https://developer.mozilla.org/docs/Web/API/Web_Speech_API).

If you're unfamiliar, this API gives you (the developer) the ability to voice-enable your website in two directions: listening to your users via the [SpeechRecognition interface](https://developer.mozilla.org/docs/Web/API/SpeechRecognition) and talking back to them via the [SpeechSynthesis interface](https://developer.mozilla.org/docs/Web/API/SpeechSynthesis). All of this is done via a JavaScript API, making it easy to test for support. This testability makes it an excellent candidate for progressive enhancement, but more on that in a moment.

A lot of my interest stems from my own personal desire to experiment with new ways of interacting with the web. I'm also a big fan of podcasts and love listening to great content while I'm driving and in other situations where my eyes are required elsewhere or are simply too tired to read. The Web Speech API opens up a whole range of opportunities to create incredibly useful and natural user interactions by being able to listen for and respond with natural language:

> - Hey Instapaper, start reading from my queue!

The possibilities created by this relatively simple API set are truly staggering. There are applications in accessibility, Internet of Things, automotive, government, the list goes on and on. Taking it a step further, imagine combining this tech with real-time translation APIs (which also recently began to appear). All of a sudden, we can open up the web to millions of people who struggle with literacy or find themselves in need of services in a country where they don't read or speak the language. This. Changes. Everything.

But back to the Web Speech API. As I said, I'd been keeping tabs on the specification for a while, checked out several of the demos and such, but hadn't made the time to play yet. Then Dave Rupert finally spurred me to action with a single tweet:

![Tweet by Dave Rupert](https://www.smashingmagazine.com/wp-content/uploads/2017/01/tweet-by-dave-rupert-opt.png)[5](https://www.smashingmagazine.com/2017/02/experimenting-with-speechsynthesis/)

Within an hour or so, I'd gotten a basic implementation together for [my blog](https://www.aaron-gustafson.com/notebook/) that would enable users to listen to a [blog post](https://www.aaron-gustafson.com/notebook/insert-clickbait-headline-about-progressive-enhancement-here/) rather than read it. A few hours later, I had added more features, but it wasn't all wine and roses, and I ended up having to back some functionality out of the widget to improve its stability. But I'm getting ahead of myself.

I've decided to hit the pause button for a few days to write up what I've learned and what I still don't fully understand in the hope that we can begin to hash out some best practices for using this awesome feature. Maybe we can even come up with some ways to improve it.

So far, my explorations into the Web Speech API have been wholly in the realm of speech synthesis. Getting to "Hello world" is relatively straightforward and merely involves creating a new `SpeechSynthesisUtterance` (which is what you want to say) and then passing that to the `speechSynthesis` object's `speak()` method:
    
    
    var to_speak = new SpeechSynthesisUtterance('Hello world!');
    window.speechSynthesis.speak(to_speak);

Not all browsers support this API, although [most modern ones do](http://caniuse.com/#feat=speech-synthesis). That being said, to avoid throwing errors, we should wrap the whole thing in a simple conditional that tests for the feature's existence _before_ using it:
    
    
    if ( 'speechSynthesis' in window ) {
      var to_speak = new SpeechSynthesisUtterance('Hello world!');
          window.speechSynthesis.speak(to_speak);
    }

Once you've got a basic example working, there's quite a bit of tuning you can do. For instance, you can tweak the reading speed by adjusting the `SpeechSynthesisUtterance` object's `rate` property. It accepts values from 0.1 to 10. I find 1.4 to be a pretty comfortable speed; anything over 3 just sounds like noise to me.

You can also tune things such as the [pitch](https://developer.mozilla.org/docs/Web/API/SpeechSynthesisUtterance/pitch), the [volume](https://developer.mozilla.org/docs/Web/API/SpeechSynthesisUtterance/volume) of the voice, even the [language being spoken](https://developer.mozilla.org/docs/Web/API/SpeechSynthesisUtterance/lang) and the [voice itself](https://developer.mozilla.org/docs/Web/API/SpeechSynthesisUtterance/voice). I'm a big fan of defaults in most things, so I'll let you explore those options on your own time. For the purpose of my experiment, I opted to change the default `rate` to 1.4, and that was about it.

When I began working with this code on my own website, I was keen to provide four controls for my readers:

  * play
  * pause
  * increase reading speed
  * decrease reading speed

The first two were relatively easy. The latter two caused problems, which I'll discuss shortly.

To kick things off, I parroted the code Dave had tweeted:
    
    
    var to_speak = new SpeechSynthesisUtterance(
      document.querySelector('main').textContent
    );
    window.speechSynthesis.speak(to_speak);

This code grabs the text content (`textContent`) of the `main` element and converts it into a `SpeechSynthesisUtterance`. It then triggers the synthesizer to speak that content. Simple enough.

Of course, I didn't want the content to begin reading immediately, so I set about building a user interface to control it. I did so in JavaScript, within the feature-detection conditional, rather than in HTML, because I did not want the interface to appear if the feature was not available (or if JavaScript failed for some reason). That would be frustrating for users.

I created the buttons and assigned some event handlers to wire up the functionality. My first pass looked something like this:
    
    
    var $buttons = document.createElement('p'),
        $button = document.createElement('button'),
        $play = $button.cloneNode(),
        $pause = $button.cloneNode(),
        paused = false,
        to_speak;
    
    if ( 'speechSynthesis' in window ) {
    
      // content to speak
      to_speak = new SpeechSynthesisUtterance(
        document.querySelector('main').textContent
      );
    
      // set the rate a little faster than 1x
      to_speak.rate = 1.4;
    
      // event handlers
      to_speak.onpause = function(){
        paused = true;
      };
    
      // button events
      function play() {
        if ( paused ) {
          paused = false;
          window.speechSynthesis.resume();
        } else {
          window.speechSynthesis.speak( to_speak );
        }
      }
      function pause() {
        window.speechSynthesis.pause();
      }
    
      // play button
      $play.innerText = 'Play';
      $play.addEventListener( 'click', play, false );
      $buttons.appendChild( $play );
      
      // pause button
      $pause.innerText = 'Pause';
      $pause.addEventListener( 'click', pause, false );
      $buttons.appendChild( $pause );
    
    } else {
    
      // sad panda
      $buttons.innerText = 'Unfortunately your browser doesn’t support this feature.';
    
    }
    
    document.body.appendChild( $buttons );

This code creates a play button and a pause button and appends them to the document. It also assigns the corresponding event handlers. As you'd expect, the play button calls `speechSynthesis.speak()`, as we saw earlier, but because pause is also in play, I set it up to either speak the selected text or resume speaking -- using `speechSynthesis.resume()` -- if the speech is paused. The pause button controls that by triggering `speechSynthesis.pause()`. I tracked the state of the speech engine using the boolean variable `paused`. You can kick the tires of this code [over on CodePen](http://codepen.io/aarongustafson/pen/ygOrNj).

I want to (ahem) pause for a moment to tuck into the `speak()` command, because it's easy to misunderstand. At first blush, you might think it causes the supplied `SpeechSynthesisUtterance` to be read aloud from the beginning, which is why I'd want to `resume()` after pausing. That is true, but it's only part of it. The speech synthesis interface actually maintains a queue for content to be spoken. Calling `speak()` pushes a new `SpeechSynthesisUtterance` to that queue and causes the synthesizer to start speaking that content if it's not already speaking. If it's in the process of reading something already, the new content takes its spot at the back of the queue and patiently waits its turn. If you want to see this in action, check out my [fork of the reading speed demo](http://s.codepen.io/aarongustafson/pen/ggryNo/).

If you want to clear the queue entirely at any time, you can call `speechSynthesis.cancel()`. When testing speech synthesis with long-form content, having this at the ready in the browser's console is handy.

As I mentioned, I also wanted to give users control over the reading speed used by the speech synthesizer. We can tune this using the `rate` property on a `SpeechSynthesisUtterance` object. That's fantastic, but you can't (currently, at least) adjust the rate of a `SpeechSynthesisUtterance` once the synthesizer starts playing it -- not even while it's paused. I don't know enough about the inner workings of speech synthesizers to know whether this is simply an oversight in the interface or a hard limitation of the synthesizers themselves, but it did force me to find a creative way around this limitation.

I experimented with a bunch of different approaches to this and eventually settled on one that works reasonably well, despite the fact that it feels like overkill. But I'm getting ahead of myself again.

Every `SpeechSynthesisUtterance` object offers a handful of events you can plug in to do various things. As you'd expect, `[onpause`](https://developer.mozilla.org/docs/Web/API/SpeechSynthesisUtterance/onpause) fires when the speech is paused, `[onend`](https://developer.mozilla.org/docs/Web/API/SpeechSynthesisUtterance/onend) fires when the synthesizer has finished reading it, etc. The `[SpeechSynthesisEvent`](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesisEvent) object passed to each of these includes information about what's going on with the synthesizer, such as the position of the virtual cursor (`[charIndex`](https://developer.mozilla.org/docs/Web/API/SpeechSynthesisEvent/charIndex)), the length of time after the current `SpeechSynthesisUtterance` started being read (`[elapsedTime`](https://developer.mozilla.org/docs/Web/API/SpeechSynthesisEvent/elapsedTime)), and a reference to the `SpeechSynthesisUtterance` itself (`[utterance`](https://developer.mozilla.org/docs/Web/API/SpeechSynthesisEvent/utterance)).

Originally, my plan to allow for real-time reading-speed adjustment was to capture the virtual cursor position via a pause event so that I could stop and start a new recording at the new speed. When the user adjusted the reading speed, I would pause the synthesizer, grab the `charIndex`, backtrack in the text to the previous space, slice from there to the end of the string to collect the remainder of what should be read, clear the queue, and start the synthesizer again with the remainder of the content. That would have worked, and it should have been reliable, but Chrome kept giving me a `charIndex` of `0`, and in Edge it was always `undefined`. Firefox tracked `charIndex` perfectly. I've filed a [bug for Chromium](https://bugs.chromium.org/p/chromium/issues/detail?id=681026) and [one for Edge](https://twitter.com/aarongustafson/status/819944910308646913), too.

Thankfully, another event, `[onboundary`](https://developer.mozilla.org/docs/Web/API/SpeechSynthesisUtterance/onboundary), fires whenever a word or sentence boundary is reached. It's a little noisier, programmatically speaking, than `onpause` because the event fires so often, but it reliably tracked the position of the virtual cursor in every browser that supports speech synthesis, which is what I needed.
    
    
    var progress_index = 0;
    
    to_speak.onboundary = function( e ) {
      if ( e.name == 'word' ) {
        progress_index = e.charIndex;
      }
    };

Once I was set up to track the cursor, I added a numeric input to the UI to allow users to change the speed:
    
    
    var $speed = document.createElement('p'),
        $speed_label = document.createElement('label'),
        $speed_value = document.createElement('input');
    
    // label the field
    $speed_label.innerText = 'Speed';
    $speed_label.htmlFor = 'speed_value';
    $speed.appendChild( $speed_label );
    
    // insert the form control
    $speed_value.type = 'number';
    $speed_value.id = 'speed_value';
    $speed_value.min = '0.1';
    $speed_value.max = '10';
    $speed_value.step = '0.1';
    $speed_value.value = Math.round( to_speak.rate * 10 ) / 10;
    $speed.appendChild( $speed_value );
    
    document.body.appendChild($speed);

Then, I added an event listener to track when it changes and to update the speech synthesizer:
    
    
    function adjustSpeed() {
      // cancel the original utterance
      window.speechSynthesis.cancel();
      
      // find the previous space
      var previous_space = to_speak.text.lastIndexOf( ' ', progress_index );
      
      // get the remains of the original string
      to_speak.text = to_speak.text.slice( previous_space );
      
      // math to 1 decimal place
      speed = Math.round( $speed_value.value * 10 ) / 10;
      
      // adjust the rate
      if ( speed > 10 ) {
        speed = 10;
      } else if ( speed < 0.1 ) {
        speed = 0.1;
      }
      to_speak.rate = speed;
    
      // return to speaking
      window.speechSynthesis.speak( to_speak );
    }
    
    $speed_value.addEventListener( 'change', adjustSpeed, false );

This works reasonably well, but ultimately I decided that I was not a huge fan of the experience, nor was I convinced it was really necessary, so this functionality remains commented out in [my website's source code](https://github.com/aarongustafson/aarongustafson.github.io/blob/source/source/_javascript/post/speak.js). You can make up your mind after seeing it [in action over on CodePen](https://codepen.io/aarongustafson/pen/vgKpMg?editors=0010).

At the top of every blog post, just after the title, I include quite a bit of meta data about the post, including things like the publication date, tags for the post, comment and webmention counts, and so on. I wanted to selectively control which content from that collection is read because only some of it is really relevant in that context. To keep the configuration out of the JavaScript and in the declarative markup where it belongs, I opted to have the JavaScript look for a specific `class` name, "dont-read", and exclude those elements from the content that would be read. To make it work, however, I needed revisit how I was collecting the content to be read in the first place.

You may recall that I'm using the `textContent` property to extract the content:
    
    
    var to_speak = new SpeechSynthesisUtterance(
      document.querySelector('main').textContent
    );

That's all well and good when you want to grab everything, but if you want to be more selective, you're better off moving the content into memory so that you can manipulate it without causing repaints and such.
    
    
    var $content = document.querySelector('main').cloneNode(true);

With a clone of `main` in memory, I can begin the process of winnowing it down to only the stuff I want:
    
    
    var to_speak = new SpeechSynthesisUtterance()
        $content = document.querySelector('main').cloneNode(true),
        $skip = $content.querySelectorAll('.dont-read');
    
    // don’t read
    Array.prototype.forEach.call( $skip, function( $el ){
      $el.innerHTML = '';
    });
    
    to_speak.text = $content.textContent;

Here, I've separated the creation of the `SpeechSynthesisUtterance` to make the code a little clearer. Then, I've cloned the `main` element (`$content`) and built a `nodeList` of elements that I want to be ignored (`$skip`). I've then looped over the `nodeList` -- borrowing `Array`'s handy `forEach` method -- and set the contents of each to an empty string, effectively removing them from the content. At the end, I've set the text property to the cloned `main` element's `textContent`. Because all of this is done to the cloned `main`, the page remains unaffected.

Done and done.

Sadly, the value of a `SpeechSynthesisUtterance` can only be text. If you pipe in HTML, it will read the tag names and slashes. That's why most of the demos use an input to collect what you want read or rely on `textContent` to extract text from the page. The reason this saddens me is that it means you lose complete control over the pacing of the content.

But not all is lost. Speech synthesizers are pretty awesome at recognizing the effect that punctuation should have on intonation and pacing. To go back to the first example I shared, consider the difference when you drop a comma between "hello" and "world":
    
    
    if ( 'speechSynthesis' in window ) {
      var to_speak = new SpeechSynthesisUtterance('Hello, world!');
      window.speechSynthesis.speak(to_speak);
    } 

Here's the original again, just so you can compare:

With this in mind, I decided to tweak the pacing of the spoken prose by artificially inserting commas into the specific elements that follow the pattern I just showed for hiding content:
    
    
    var $pause_before = $content.querySelectorAll(
      'h2, h3, h4, h5, h6, p, li, dt, blockquote, pre, figure, footer'
    );
    
    // synthetic pauses
    Array.prototype.forEach.call( $pause_before, function( $el ){
      $el.innerHTML = ' , ' + $el.innerHTML;
    });

While I was doing this, I also noticed some issues with certain elements running into the content around them. Most notably, this was happening with `pre` elements. To mitigate that, I used the same approach to swap carriage returns, line breaks and such for spaces:
    
    
    var $space = $content.querySelectorAll('pre');
    
    // spacing out content
    Array.prototype.forEach.call( $space, function( $el ){
      $el.innerHTML = ' ' + $el.innerHTML.replace(/[\r\n\t]/g, ' ') + ' ';
    });
    

With those tweaks in place, I've been incredibly happy with the listening experience. If you'd like to see all of this code in context, head over to [my GitHub repository](https://github.com/aarongustafson/aarongustafson.github.io/blob/source/source/_javascript/post/speak.js). The code you use to drop the UI into the page will likely need to be different from what I did, but the rest of the code should be plug-and-play.

As it stands right now, the Web Speech API has not become a standard and [isn't even on a standards track](https://dvcs.w3.org/hg/speech-api/raw-file/tip/webspeechapi.html#status). It's an experimental API and some of the details of the specification remain in flux. For instance, the `elapsedTime` property of a `SpeechSynthesisEvent` originally tracked milliseconds and then switched to seconds. If you were doing math that relied on that number to do something else in the interface, you might get widely different experiences in Chrome (which still uses milliseconds) and Edge (which uses seconds).

If I was granted one wish for this specification--apart from standardization--it would be for real-time speed, pitch and volume adjustment. I can understand the need to restart things to get the text read in another voice, but the others feel like they should be manipulable in real time. But again, I don't know anything about the inner workings of speech synthesizers, so that might not be technically possible.

In terms of actual browser implementations, basic speech synthesis like I've covered here is pretty solid in [browsers that support the API](http://caniuse.com/#feat=speech-synthesis). As I mentioned, Chrome and Edge currently fail to accurately report the virtual cursor position when speech synthesis is paused, but I don't think that's a deal-breaker. What is problematic is how unstable things get when you start to combine features such as real-time reading-speed adjustments, pausing and such. Often, the synthesizer just stops working and refuses to start up again. If you'd like to see that happen, take a look at a [demo I set up](https://codepen.io/aarongustafson/pen/ZLOxLe). Chances are that this issue would go away if the API allowed for real-time manipulation of properties such as `rate` because you wouldn't have to `cancel()` and restart the synthesizer with each adjustment.

Long story short, if you're looking at this as a progressive enhancement for a content-heavy website and only want the most basic features, you should be good to go. If you want to get fancy, you might be disappointed or have to come up with more clever coding acrobatics than I've mustered.

As with most things on the web, I learned a ton by viewing other people's source, demos and such -- and the documentation, naturally. Here are some of my favorites (some of which I linked to in context):

_(rb, yk, il, al)_
