# Simulate JavaScript Key Events

up vote 130 down vote favorite

**40**

Is it possible to simulate key press events programatically in JavaScript?

[javascript](/questions/tagged/javascript) [javascript-events](/questions/tagged/javascript-events)

[share](/q/596481)|[improve this question](/posts/596481/edit)

[edited Jul 7 '14 at 19:47](/posts/596481/revisions)

![](https://www.gravatar.com/avatar/ae15c48f686a0ecb39848f980b296611?s=32&d=identicon&r=PG)

[Shog9](/users/811/shog9)♦

102k26176212

asked Feb 27 '09 at 20:17

![](https://www.gravatar.com/avatar/d9efdd86a69733a9f86530a5628d0313?s=32&d=identicon&r=PG)

[tan](/users/72022/tan)

654265

add a comment | 

##  11 Answers 11

[ active](/questions/596481/simulate-javascript-key-events?answertab=active#tab-top) [ oldest](/questions/596481/simulate-javascript-key-events?answertab=oldest#tab-top) [ votes](/questions/596481/simulate-javascript-key-events?answertab=votes#tab-top)

up vote 72 down vote

A non-jquery version that works in both webkit and gecko:
    
    
    var keyboardEvent = document.createEvent("KeyboardEvent");
    var initMethod = typeof keyboardEvent.initKeyboardEvent !== 'undefined' ? "initKeyboardEvent" : "initKeyEvent";
    
    
    keyboardEvent[initMethod](
                       "keydown", // event type : keydown, keyup, keypress
                        true, // bubbles
                        true, // cancelable
                        window, // viewArg: should be window
                        false, // ctrlKeyArg
                        false, // altKeyArg
                        false, // shiftKeyArg
                        false, // metaKeyArg
                        40, // keyCodeArg : unsigned long the virtual key code, else 0
                        0 // charCodeArgs : unsigned long the Unicode character associated with the depressed key, else 0
    );
    document.dispatchEvent(keyboardEvent);
    

[share](/a/12187302)|[improve this answer](/posts/12187302/edit)

answered Aug 29 '12 at 22:18

![](https://www.gravatar.com/avatar/f23b95482d01c24db2d51c6c4b402b6f?s=32&d=identicon&r=PG)

[Philip Nuzhnyy](/users/320419/philip-nuzhnyy)

1,6451414

2
 

Philip, this looks like the code i need, but i need to dispatch the keypress event to a textarea. i tried to modify your code to send to a textarea, but it doesnt appear to work, in chrome at least, any idea what could be wrong? here is the jsfiddle that i have made to demonstrate: [jsfiddle.net/szmJu](http://jsfiddle.net/szmJu/) - [user280109](/users/280109/user280109) Sep 11 '12 at 12:53

2
 

Turns out there's a bug in Chromium with KeyboardEvent dispatching. Check out this thread for more details: [stackoverflow.com/questions/10455626/…](http://stackoverflow.com/questions/10455626/keydown-simulation-in-chrome-fires-normally-but-not-the-correct-key/12522769#12522769). - [Philip Nuzhnyy](/users/320419/philip-nuzhnyy) Sep 21 '12 at 18:12

8
 

`keyCode` is always 0, and I cannot change it. - [Ata Iravani](/users/963543/ata-iravani) May 22 '13 at 6:50

2
 

Note: the above link to KeyboardEvent.initKeyboardEvent() on MDN is wrong. Correct link: [developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/…](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/initKeyboardEvent) - [groovecoder](/users/571420/groovecoder) Jun 12 '15 at 11:20

1
 

It appears that there's a bug in Chromium that causes the `event.which` to always be `0` when using `document.createEvent("KeyboardEvent")`. @lluft shared the details and a workaround, which worked for me, in this [comment](http://stackoverflow.com/questions/961532/firing-a-keyboard-event-in-javascript#comment-44022523) on a different thread. Basically, you need to use `document.createEvent('Event')` to create a generic event and then set the type to `keydown` and give a `keyCode` property equal to the key's charcode. - [A-Diddy](/users/3858863/a-diddy) Jan 6 at 16:47

 |  show **2** more comments

up vote 48 down vote

If you are ok to use jQuery 1.3.1:
    
    
    function simulateKeyPress(character) {
      jQuery.event.trigger({ type : 'keypress', which : character.charCodeAt(0) });
    }
    
    $(function() {
      $('body').keypress(function(e) {
        alert(e.which);
      });
    
      simulateKeyPress("e");
    });
    

[share](/a/596580)|[improve this answer](/posts/596580/edit)

[edited Mar 5 '09 at 1:18](/posts/596580/revisions)

answered Feb 27 '09 at 20:36

![](https://www.gravatar.com/avatar/e1e2dd8c03c8e9e0680cfd802df0a04b?s=32&d=identicon&r=PG)

[alex2k8](/users/62192/alex2k8)

17.4k36123191

  
 

Hi What I meant is: 1. Register a key event (letter e executes some JS) 2. From a other method I want to programatically press the letter e) - [tan](/users/72022/tan) Mar 3 '09 at 20:20

5
 

It does not work properly in Chrome, sorry. jQuery creates Event, but without important attributes - which, charCode, keyCode. - [hamczu](/users/396754/hamczu) Sep 17 '11 at 21:55

2
 

@tan This is not possible. See my answer for the reasoning behind it. - [Lo Sauer](/users/901946/lo-sauer) Nov 9 '13 at 22:22

1
 

Note that `trigger` [can't be used to mimic native browser events](http://stackoverflow.com/questions/32428993/why-doesnt-simulating-a-tab-keypress-change-focus-of-input-fields). - [Adam Zerner](/users/1927876/adam-zerner) Sep 7 '15 at 1:19

add a comment | 

up vote 18 down vote

What you can do is programmatically trigger _keyevent listeners_ by firing _keyevents_. It makes sense to allow this from a sandboxed security-perspective. Using this ability, you can then apply a typical [observer-pattern](http://en.wikipedia.org/wiki/Observer_pattern). You could call this method "simulating".

Below is an example of how to accomplish this in the W3C DOM standard along with jQuery:
    
    
    function triggerClick() {
      var event = new MouseEvent('click', {
        'view': window,
        'bubbles': true,
        'cancelable': true
      });
      var cb = document.querySelector('input[type=submit][name=btnK]'); 
      var canceled = !cb.dispatchEvent(event);
      if (canceled) {
        // preventDefault was called and the event cancelled
      } else {
        // insert your event-logic here...
      }
    }
    

This example is adapted from: <https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Creating_and_triggering_events>

In jQuery:
    
    
    jQuery('input[type=submit][name=btnK]')
      .trigger({
        type: 'keypress',
        which: character.charCodeAt(0 /*the key to trigger*/)      
       });
    

**But as of recently, there is no [DOM] way to actually trigger keyevents leaving the browser-sandbox.** And all major browser vendors will adhere to that security concept.

As for plugins such as Adobe Flash - which are based on the NPAPI-, and permit bypassing the sandbox: these are [phasing-out](http://blog.chromium.org/2013/09/saying-goodbye-to-our-old-friend-npapi.html) ; [Firefox](http://blog.mozilla.org/futurereleases/2013/09/24/plugin-activation-in-firefox/).

**Detailed Explanation:**

You cannot and you must not for security reasons (as Pekka already pointed out). You will always require a user interaction in between. Additionally imagine the chance of the browser vendors getting sued by users, as various programmatic keyboard events will have led to spoofing attacks.

See this [post](http://goo.gl/ghyhA0) for alternatives and more details. There is always the flash based copy-and-paste. Here is an elegant [example](http://www.colorzilla.com/gradient-editor/). At the same time it is a testimony why the web is moving away from plugin vendors.

There is a similar security mindset applied in case of the [opt-in CORS policy](http://goo.gl/JiYNEE) to access remote content programmatically.

The answer is:  
**There is no way to programmatically trigger input keys in the sandboxed browser environment under normal circumstances**. 

**Bottomline:** I am not saying it will not be possible in the future, under special browser-modes and/or privileges towards the end-goal of gaming, or similar user-experiences. However prior to entering such modes, the user will be asked for permissions and risks, similar to the [Fullscreen API model](https://www.google.at/search?client=opera&q=w3c%20fullscreen%20api%20permission). 

**Useful:** In the context of KeyCodes, [this](http://www.lsauer.com/2011/08/javascript-keymap-keycodes-in-json.html) tool and keycode mapping will come in handy.

_Disclosure:_ The answer is based on the answer [here](http://stackoverflow.com/questions/8668192/programmatically-triggering-ctrls/19882728#19882728).

[share](/a/19883789)|[improve this answer](/posts/19883789/edit)

[edited Sep 8 '15 at 17:15](/posts/19883789/revisions)

![](https://www.gravatar.com/avatar/941be6aedf5e975c30fa6f9a3f29a823?s=32&d=identicon&r=PG)

[poxip](/users/2221315/poxip)

526520

answered Nov 9 '13 at 22:20

![](https://www.gravatar.com/avatar/ff49f35d2cfb3501503c9a99459e4caa?s=32&d=identicon&r=PG)

[Lo Sauer](/users/901946/lo-sauer)

8,78843863

  
 

So with the JavaScript KeyboardEvent API ([developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent)) you can simulate key events, for example say that a key is pressed but it is not possible to have the key press effect, like writing characters 'a', 'b', 'c'? If it is possible, writing these basics characters is not a security problem but I understand that a special key like "F12" or a combination like "Alt+F4" should be forbidden. - [baptx](/users/1176454/baptx) Jan 30 at 19:37

add a comment | 

up vote 10 down vote

You can use `dispatchEvent()`:
    
    
    function simulateKeyPress() {
      var evt = document.createEvent("KeyboardEvent");
      evt.initKeyEvent ("keypress", true, true, window,
                        0, 0, 0, 0,
                        0, "e".charCodeAt(0)) 
      var canceled = !body.dispatchEvent(evt);
      if(canceled) {
        // A handler called preventDefault
        alert("canceled");
      } else {
        // None of the handlers called preventDefault
        alert("not canceled");
      }
    }
    

I didn't test this, but it's adapted from the code on [dispatchEvent()'s documentation](https://developer.mozilla.org/en/DOM/element.dispatchEvent). You'll probably want to read through that, and also the docs for createEvent() and initKeyEvent().

[share](/a/839635)|[improve this answer](/posts/839635/edit)

[edited Oct 3 '13 at 18:17](/posts/839635/revisions)

![](https://www.gravatar.com/avatar/292fd1d3a18cee7c77ec34dccd9c004f?s=32&d=identicon&r=PG)

[Mike Atlas](/users/101827/mike-atlas)

6,22932650

answered May 8 '09 at 12:44

![](https://www.gravatar.com/avatar/c131814bb9a4a205b11955fc20ebf361?s=32&d=identicon&r=PG)

[Plutor](/users/53060/plutor)

2,08811528

7
 

Note: This is supported by Gecko browsers only. - [lhunath](/users/58803/lhunath) Nov 26 '10 at 20:56

3
 

Did you mean `simulateClick` -> `simulateKeyPress`? :-) - [Andres Riofrio](/users/237285/andres-riofrio) Jun 1 '12 at 3:39

  
 

@AndresRiofrio I fixed the function name. - [Mike Atlas](/users/101827/mike-atlas) Oct 3 '13 at 18:18

1
 

"initKeyEvent is not a function" - [Maximilian](/users/2768038/maximilian) Feb 10 at 14:17

add a comment | 

up vote 9 down vote

Building on the answer from alex2k8, here's a revised version that works in all browsers that jQuery supports (the problem was in missing arguments to jQuery.event.trigger, which is easy to forget when using that internal function).
    
    
    // jQuery plugin. Called on a jQuery object, not directly.
    jQuery.fn.simulateKeyPress = function (character) {
      // Internally calls jQuery.event.trigger
      // with arguments (Event, data, elem). That last arguments is very important!
      jQuery(this).trigger({ type: 'keypress', which: character.charCodeAt(0) });
    };
    
    jQuery(document).ready(function ($) {
      // Bind event handler
      $('body').keypress(function (e) {
        alert(String.fromCharCode(e.which));
        console.log(e);
      });
      // Simulate the key press
      $('body').simulateKeyPress('x');
    });
    

You could even push this further and let it not only simulate the event but actually insert the character (if it is an input element), however there are many cross-browser gotcha's when trying to do that. Better use a more elaborate plugin like [SendKeys](http://bililite.com/blog/2008/08/20/the-fnsendkeys-plugin/).

[share](/a/7627165)|[improve this answer](/posts/7627165/edit)

[edited Mar 21 '14 at 17:31](/posts/7627165/revisions)

answered Oct 2 '11 at 15:11

![](https://www.gravatar.com/avatar/49061e8503ca321a8045c9065963a8c6?s=32&d=identicon&r=PG)

[Krinkle](/users/319266/krinkle)

6,02221731

2
 

4 years later finding this useful nice one! - [Robert Pounder](/users/3652863/robert-pounder) Jan 16 '15 at 11:03

  
 

SendKeys does NOT simulate keypresses it just injects values into the target elements. - [Ahmed Masud](/users/894328/ahmed-masud) Mar 4 '15 at 16:28

1
 

Not simulating a hardware keypress, just calling binded keypress function. - [Erwinus](/users/565244/erwinus) Mar 22 '15 at 1:30

add a comment | 

up vote 6 down vote

You can create and dispatch keyboard events, and they will trigger appropriate registered event handlers, however they **will not produce any text**, if dispatched to input element for example.

To fully simulate text input you need to produce a sequence of keyboard events plus explicitly set the text of input element. The sequence of events depends on how thoroughly you want to simulate text input.

The simplest form would be:
    
    
    $('input').val('123');
    $('input').change();
    

[share](/a/17475636)|[improve this answer](/posts/17475636/edit)

answered Jul 4 '13 at 17:28

![](https://www.gravatar.com/avatar/c196f0f982f1168aec37296bf282e3bc?s=32&d=identicon&r=PG)

[Alex Burtsev](/users/235715/alex-burtsev)

5,59913966

add a comment | 

up vote 4 down vote

This approach support cross-browser changing the value of **key code**. [Source](http://bresleveloper.blogspot.co.il/2013/03/jsjq-simulate-enter-event.html)
    
    
    var $textBox = $("#myTextBox");
    
    var press = jQuery.Event("keypress");
    press.altGraphKey = false;
    press.altKey = false;
    press.bubbles = true;
    press.cancelBubble = false;
    press.cancelable = true;
    press.charCode = 13;
    press.clipboardData = undefined;
    press.ctrlKey = false;
    press.currentTarget = $textBox[0];
    press.defaultPrevented = false;
    press.detail = 0;
    press.eventPhase = 2;
    press.keyCode = 13;
    press.keyIdentifier = "";
    press.keyLocation = 0;
    press.layerX = 0;
    press.layerY = 0;
    press.metaKey = false;
    press.pageX = 0;
    press.pageY = 0;
    press.returnValue = true;
    press.shiftKey = false;
    press.srcElement = $textBox[0];
    press.target = $textBox[0];
    press.type = "keypress";
    press.view = Window;
    press.which = 13;
    
    $textBox.trigger(press);
    

[share](/a/16685966)|[improve this answer](/posts/16685966/edit)

[edited Mar 21 '14 at 17:41](/posts/16685966/revisions)

![](https://www.gravatar.com/avatar/49061e8503ca321a8045c9065963a8c6?s=32&d=identicon&r=PG)

[Krinkle](/users/319266/krinkle)

6,02221731

answered May 22 '13 at 7:32

![](https://www.gravatar.com/avatar/4679b65873c20b558e0d710bb6ab8293?s=32&d=identicon&r=PG)

[Ata Iravani](/users/963543/ata-iravani)

61111225

2
 

worked flawless. Thanks @Krinkle and Ata Iravani - [Mahesh Vemuri](/users/1843044/mahesh-vemuri) Jan 22 '15 at 8:41

  
 

Can you have a look at [this](https://github.com/maxisme/crypter/issues/4)? - [Maximilian](/users/2768038/maximilian) Feb 10 at 14:45

add a comment | 

up vote 2 down vote

For those interested, you can, in-fact recreate keyboard input events reliably. In order to change text in input area (move cursors, or the page via an input character) you have to follow the DOM event model closely: <http://www.w3.org/TR/DOM-Level-3-Events/#h4_events-inputevents>

The model should do:

  * focus (dispatched on the DOM with the target set)

Then for each character:

  * keydown (dispatched on the DOM)
  * beforeinput (dispatched at the target if its a textarea or input)
  * keypress (dispatched on the DOM)
  * input (dispatched at the target if its a textarea or input)
  * change (dispatched at the target if its a select)
  * keyup (dispatched on the DOM)

Then, optionally for most:

  * blur (dispatched on the DOM with the target set)

This actually changes the text in the page via javascript (without modifying value statements) and sets off any javascript listeners/handlers appropriately. If you mess up the sequence javascript will not fire in the appropriate order, the text in the input box will not change, the selections will not change or the cursor will not move to the next space in the text area.

Unfortunately the code was written for an employer under an NDA so I cannot share it, but it is definitely possible but you must recreate the entire key input "stack" for each element in the correct order.

[share](/a/23964375)|[improve this answer](/posts/23964375/edit)

answered May 30 '14 at 22:40

![](https://www.gravatar.com/avatar/e09b35437b109c418488ff7d0f7d37c3?s=32&d=identicon&r=PG)

[Trevor](/users/2475670/trevor)

21327

1
 

NDA for JavaScript? Really? , anyway for each character your algorithm is wrong, simulating "input" event anyway adds text without going through whole keydown,keyup event or any other event. Problem is how to handle multiple keypress events etc like pressing "a" button and expecting "aaaaaaa" multiple times. - [Akash Kava](/users/85597/akash-kava) Jul 12 '14 at 10:02

  
 

The trick is to fire a keydown, input, then keyup. If you want multiple "aaaaaa" keep firing the input event. and don't tell anyone. - [Trevor](/users/2475670/trevor) Jul 15 '14 at 2:27

add a comment | 

up vote 1 down vote

Here's a library that really helps: <https://cdn.rawgit.com/ccampbell/mousetrap/2e5c2a8adbe80a89050aaf4e02c45f02f1cc12d4/tests/libs/key-event.js>

I don't know from where did it came from, but it is helpful. It adds a `.simulate()` method to `window.KeyEvent`, so you use it simply with `KeyEvent.simulate(0, 13)` for simulating an `enter` or `KeyEvent.simulate(81, 81)` for a `'Q'`.

I got it at <https://github.com/ccampbell/mousetrap/tree/master/tests>.

[share](/a/25776608)|[improve this answer](/posts/25776608/edit)

answered Sep 10 '14 at 23:18

![](https://www.gravatar.com/avatar/b760f503c84d1bf47322f401066c753f?s=32&d=identicon&r=PG)

[fiatjaf](/users/973380/fiatjaf)

3,2082434

add a comment | 

up vote 0 down vote

You should be using some JS lib with support for wrapping DOM Event Model. From withing there, you can fire and test your handlers.

[share](/a/1587980)|[improve this answer](/posts/1587980/edit)

answered Oct 19 '09 at 10:40

![](https://www.gravatar.com/avatar/6f4ff03626875d9943afa17659984261?s=32&d=identicon&r=PG)

[skrat](/users/104337/skrat)

3,0551631

add a comment | 

up vote 0 down vote

just use CustomEvent
    
    
    Node.prototype.fire=function(type,options){
         var event=new CustomEvent(type);
         for(var p in options){
             event[p]=options[p];
         }
         this.dispatchEvent(event);
    }
    

4 ex want to simulate ctrl+z
    
    
    window.addEventListener("keyup",function(ev){
         (if(ev.ctrlKey && ev.keyCode === 90) console.log(ev); // or do smth
         })
    
     document.fire("ketup",{ctrlKey:true,keyCode:90,bubbles:true})
    

[share](/a/34095590)|[improve this answer](/posts/34095590/edit)

answered Dec 4 '15 at 19:00

![](https://www.gravatar.com/avatar/c7f9b3409e83d6d62f3a84346a7b503d?s=32&d=identicon&r=PG)

[bortunac](/users/953374/bortunac)

1,0841011

add a comment | 

## Your Answer

 

draft saved

draft discarded

### Sign up or [log in](/users/login?ssrc=question_page&returnurl=http%3a%2f%2fstackoverflow.com%2fquestions%2f596481%2fsimulate-javascript-key-events%23new-answer)

Sign up using Google

Sign up using Facebook

Sign up using Email and Password

### Post as a guest

Name

Email

### Post as a guest

Name

Email

discard

By posting your answer, you agree to the [privacy policy](http://stackexchange.com/legal/privacy-policy) and [terms of service](http://stackexchange.com/legal/terms-of-service).

##  Not the answer you're looking for? Browse other questions tagged [javascript](/questions/tagged/javascript) [javascript-events](/questions/tagged/javascript-events) or [ask your own question](/questions/ask). 

asked

**7 years ago**

viewed

**155938 times**

active

**[3 months ago](?lastactivity)**

#### [Visit Chat](http://chat.stackoverflow.com)

#### Linked

[

0

](/q/6427690) [Full Screen Page by pressing button instead of F11](/questions/6427690/full-screen-page-by-pressing-button-instead-of-f11)

[

0

](/q/7805021) [Simulate keypresses in javascript](/questions/7805021/simulate-keypresses-in-javascript)

[

1

](/q/21982351) [Can I simulate keypress(CTRL+F1) in javascript or jquery?](/questions/21982351/can-i-simulate-keypressctrlf1-in-javascript-or-jquery)

[

0

](/q/14939861) [Javascript press key on input class](/questions/14939861/javascript-press-key-on-input-class)

[

3

](/q/13294702) [Simulate / Fake a keypress in javascript](/questions/13294702/simulate-fake-a-keypress-in-javascript)

[

0

](/q/25128119) [Trigger javascript keyboard events with code?](/questions/25128119/trigger-javascript-keyboard-events-with-code)

[

0

](/q/16688906) [can we get Tab key action on click on a tag using javascript or jquery](/questions/16688906/can-we-get-tab-key-action-on-click-on-a-tag-using-javascript-or-jquery)

[

3

](/q/34402686) [How to press any char by javascript (not by keyboard)](/questions/34402686/how-to-press-any-char-by-javascript-not-by-keyboard)

[

0

](/q/29983247) [Is it is possible to press the keyboard key by javascript code](/questions/29983247/is-it-is-possible-to-press-the-keyboard-key-by-javascript-code)

[

46

](/q/1468384) [Simulate Keypress With jQuery](/questions/1468384/simulate-keypress-with-jquery)

[see more linked questions…](/questions/linked/596481)

#### Related

[

5493 

](/q/111102)[How do JavaScript closures work?](/questions/111102/how-do-javascript-closures-work)

[

508 

](/q/570960)[How to debug JavaScript/jQuery event bindings with Firebug (or similar tool)](/questions/570960/how-to-debug-javascript-jquery-event-bindings-with-firebug-or-similar-tool)

[

1234 

](/q/1098040)[Checking if a key exists in a JavaScript object?](/questions/1098040/checking-if-a-key-exists-in-a-javascript-object)

[

7 

](/q/1803338)[simulate the tab key function in javascript](/questions/1803338/simulate-the-tab-key-function-in-javascript)

[

244 

](/q/3369593)[How to detect escape key press with JavaScript or jQuery?](/questions/3369593/how-to-detect-escape-key-press-with-javascript-or-jquery)

[

430 

](/q/4616694)[What is event bubbling and capturing?](/questions/4616694/what-is-event-bubbling-and-capturing)

[

71 

](/q/6157929)[How to simulate a mouse click using JavaScript?](/questions/6157929/how-to-simulate-a-mouse-click-using-javascript)

[

203 

](/q/7306669)[How to get all properties values of a Javascript Object (without knowing the keys)?](/questions/7306669/how-to-get-all-properties-values-of-a-javascript-object-without-knowing-the-key)

[

-1 

](/q/13355241)[How to use javascript to simulate Enter key event?](/questions/13355241/how-to-use-javascript-to-simulate-enter-key-event)

[

3 

](/q/25748013)[Simulate key press using native javascript](/questions/25748013/simulate-key-press-using-native-javascript)

####  [ Hot Network Questions ](//stackexchange.com/questions?tab=hot)

  * [ How can I define variables that follow a naming pattern? ](http://mathematica.stackexchange.com/questions/109440/how-can-i-define-variables-that-follow-a-naming-pattern)
  * [ Do I need to use a heat sink? ](http://raspberrypi.stackexchange.com/questions/43752/do-i-need-to-use-a-heat-sink)
  * [ In simple English, what does it mean to be transcendental? ](http://math.stackexchange.com/questions/1686156/in-simple-english-what-does-it-mean-to-be-transcendental)
  * [ How to list all files in a directory with absolute paths in linux/unix ](http://unix.stackexchange.com/questions/268474/how-to-list-all-files-in-a-directory-with-absolute-paths-in-linux-unix)
  * [ Is it ok to remove outliers from data? ](http://stats.stackexchange.com/questions/200534/is-it-ok-to-remove-outliers-from-data)
  * [ What weapons would be effective at a microscopic level? ](http://worldbuilding.stackexchange.com/questions/37678/what-weapons-would-be-effective-at-a-microscopic-level)
  * [ Skipping 's' ending in 3rd person ](http://english.stackexchange.com/questions/312279/skipping-s-ending-in-3rd-person)
  * [ Supercapacitors as car batteries ](http://electronics.stackexchange.com/questions/221531/supercapacitors-as-car-batteries)
  * [ What is the real intention for admin-post.php? ](http://wordpress.stackexchange.com/questions/220073/what-is-the-real-intention-for-admin-post-php)
  * [ Is there anything I could/should do about a professor who gives lectures so dry that less than 10% of the class turn up? ](http://academia.stackexchange.com/questions/64749/is-there-anything-i-could-should-do-about-a-professor-who-gives-lectures-so-dry)
  * [ How can I add datetime to an existing file name in Linux? ](http://unix.stackexchange.com/questions/268324/how-can-i-add-datetime-to-an-existing-file-name-in-linux)
  * [ How to prevent username and password matches when changing a username? ](http://security.stackexchange.com/questions/116738/how-to-prevent-username-and-password-matches-when-changing-a-username)
  * [ Canadian/Iranian Citizen Transit USA aiport ](http://travel.stackexchange.com/questions/64917/canadian-iranian-citizen-transit-usa-aiport)
  * [ Texas and New York Township, Range, and Section GIS Data ](http://gis.stackexchange.com/questions/183947/texas-and-new-york-township-range-and-section-gis-data)
  * [ Which rules could help to prevent the endless reviewing loop? ](http://workplace.stackexchange.com/questions/63243/which-rules-could-help-to-prevent-the-endless-reviewing-loop)
  * [ If there are students of other religions at Hogwarts, why are only the Christian holidays celebrated? ](http://scifi.stackexchange.com/questions/121441/if-there-are-students-of-other-religions-at-hogwarts-why-are-only-the-christian)
  * [ How many steps did I walk? ](http://codegolf.stackexchange.com/questions/75130/how-many-steps-did-i-walk)
  * [ Cleanest way to obtain the numeric prefix of a string ](http://stackoverflow.com/questions/35866847/cleanest-way-to-obtain-the-numeric-prefix-of-a-string)
  * [ Placing seven point-sized pawns ](http://puzzling.stackexchange.com/questions/28584/placing-seven-point-sized-pawns)
  * [ “To not know if…” construct in German ](http://german.stackexchange.com/questions/28545/to-not-know-if-construct-in-german)
  * [ What is this hole in the nose of the A330? ](http://aviation.stackexchange.com/questions/25948/what-is-this-hole-in-the-nose-of-the-a330)
  * [ What is it called when a movie breaks the illusion of fantasy? ](http://movies.stackexchange.com/questions/49724/what-is-it-called-when-a-movie-breaks-the-illusion-of-fantasy)
  * [ Probability of picking 4 red balls ](http://math.stackexchange.com/questions/1688391/probability-of-picking-4-red-balls)
  * [ Is it possible to statically predict when to deallocate memory---from source code only? ](http://programmers.stackexchange.com/questions/311972/is-it-possible-to-statically-predict-when-to-deallocate-memory-from-source-cod)
more hot questions 

[ question feed ](/feeds/question/596481)

![](/posts/596481/ivc/3b88)

default

[about us](http://stackoverflow.com/company/about) [tour](/tour) [help](/help) [blog](http://blog.stackoverflow.com?blb=1) [chat](http://chat.stackoverflow.com) [data](http://data.stackexchange.com) [legal](http://stackexchange.com/legal) [privacy policy](http://stackexchange.com/legal/privacy-policy) [work here](http://stackoverflow.com/company/work-here) [advertising info](http://stackexchange.com/mediakit) mobile **[contact us](/contact)** **[feedback](http://meta.stackoverflow.com)**

Technology  Life / Arts  Culture / Recreation  Science  Other 

  1. [Stack Overflow](//stackoverflow.com)
  2. [Server Fault](//serverfault.com)
  3. [Super User](//superuser.com)
  4. [Web Applications](//webapps.stackexchange.com)
  5. [Ask Ubuntu](//askubuntu.com)
  6. [Webmasters](//webmasters.stackexchange.com)
  7. [Game Development](//gamedev.stackexchange.com)
  8. [TeX - LaTeX](//tex.stackexchange.com)

  1. [Programmers](//programmers.stackexchange.com)
  2. [Unix & Linux](//unix.stackexchange.com)
  3. [Ask Different (Apple)](//apple.stackexchange.com)
  4. [WordPress Development](//wordpress.stackexchange.com)
  5. [Geographic Information Systems](//gis.stackexchange.com)
  6. [Electrical Engineering](//electronics.stackexchange.com)
  7. [Android Enthusiasts](//android.stackexchange.com)
  8. [Information Security](//security.stackexchange.com)

  1. [Database Administrators](//dba.stackexchange.com)
  2. [Drupal Answers](//drupal.stackexchange.com)
  3. [SharePoint](//sharepoint.stackexchange.com)
  4. [User Experience](//ux.stackexchange.com)
  5. [Mathematica](//mathematica.stackexchange.com)
  6. [Salesforce](//salesforce.stackexchange.com)
  7. [ExpressionEngine® Answers](//expressionengine.stackexchange.com)
  8. [ more (13) ](http://stackexchange.com/sites#technology)

  1. [Photography](//photo.stackexchange.com)
  2. [Science Fiction & Fantasy](//scifi.stackexchange.com)
  3. [Graphic Design](//graphicdesign.stackexchange.com)
  4. [Movies & TV](//movies.stackexchange.com)
  5. [Seasoned Advice (cooking)](//cooking.stackexchange.com)
  6. [Home Improvement](//diy.stackexchange.com)
  7. [Personal Finance & Money](//money.stackexchange.com)
  8. [Academia](//academia.stackexchange.com)
  9. [ more (9) ](http://stackexchange.com/sites#lifearts)

  1. [English Language & Usage](//english.stackexchange.com)
  2. [Skeptics](//skeptics.stackexchange.com)
  3. [Mi Yodeya (Judaism)](//judaism.stackexchange.com)
  4. [Travel](//travel.stackexchange.com)
  5. [Christianity](//christianity.stackexchange.com)
  6. [Arqade (gaming)](//gaming.stackexchange.com)
  7. [Bicycles](//bicycles.stackexchange.com)
  8. [Role-playing Games](//rpg.stackexchange.com)
  9. [ more (21) ](http://stackexchange.com/sites#culturerecreation)

  1. [Mathematics](//math.stackexchange.com)
  2. [Cross Validated (stats)](//stats.stackexchange.com)
  3. [Theoretical Computer Science](//cstheory.stackexchange.com)
  4. [Physics](//physics.stackexchange.com)
  5. [MathOverflow](//mathoverflow.net)
  6. [Chemistry](//chemistry.stackexchange.com)
  7. [Biology](//biology.stackexchange.com)
  8. [ more (5) ](http://stackexchange.com/sites#science)

  1. [Stack Apps](//stackapps.com)
  2. [Meta Stack Exchange](//meta.stackexchange.com)
  3. [Area 51](//area51.stackexchange.com)
  4. [Stack Overflow Careers](//careers.stackoverflow.com)

site design / logo (C) 2016 Stack Exchange Inc; user contributions licensed under [cc by-sa 3.0](https://creativecommons.org/licenses/by-sa/3.0/) with [attribution required](http://blog.stackoverflow.com/2009/06/attribution-required/)

rev 2016.3.8.3324 

Stack Overflow works best with JavaScript enabled![](http://pixel.quantserve.com/pixel/p-c1rF4kxgLUzNc.gif)
