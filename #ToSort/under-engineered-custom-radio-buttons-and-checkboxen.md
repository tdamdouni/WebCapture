# Under-Engineered Custom Radio Buttons and Checkboxen

_Captured: 2017-06-01 at 20:19 from [adrianroselli.com](http://adrianroselli.com/2017/05/under-engineered-custom-radio-buttons-and-checkboxen.html)_

I keep seeing overly-complex controls with additional elements as style hooks, scripting to make up for non-semantic replacements, images that need to be downloaded, and so on.

This is silly. Here are some really simple styles to make radio buttons and checkboxes look _unlike_ native controls (which seems to be the main goal from these over-engineered attempts).

The code in here is not perfect, but it is simple, semantic, and accessible. It does not require any third-party libraries, it does not use images, and no scripting is needed. It is pure HTML and CSS. Barring the `<div>`s, the HTML cannot get much leaner. I have embedded a CodePen so you can play around with it. Or you can [visit it directly on CodePen](https://codepen.io/aardrian/pen/PmgyaY/).

## Some Detail

There are a few bits in here that I think warrant some explanation beyond just throwing CSS and HTML at you. After all, when making something without jacking up the HTML, I think it is important to note _how_ you did not jack it up.

### Some HTML Notes

The styles rely on the following very simple mark-up: `<input>`, then `<label>`. That is it. If you use explicit labeling (by wrapping the entire control and its text inside a `<label>`) then you will need to re-write the CSS. That is on you.
    
    
    <input type="radio" name="spam" id="spamY" checked>
    <label for="spamY">
      Please send me all the spam.
    </label>

What is great about this approach is that if your CSS fails for some reason, you still have a fully functional accessible field.

Please note that there is no ARIA, whether by converting a `<button>` element via `role` abuse or relying on any of the `aria-label`, `aria-labelledby`, nor `aria-describedby` variations.

### Some CSS Notes

I do not remove the control from the page. I do not give it a `display: none` property since that hides it from assistive technology. Instead I rely on a CSS technique to visually hide the control that does not rely on the kinds of hacks that mess up RTL content (or content translated to RTL). If you see me answer questions on Stack Overflow about off-screen techniques, this is the style block I typically use, but with a `visually-hidden` class name as the selector:
    
    
    input[type=radio],
    input[type=checkbox] {
      position: absolute;
      top: auto;
      overflow: hidden;
      clip: rect(1px 1px 1px 1px); /* IE 6/7 */
      clip: rect(1px, 1px, 1px, 1px);
      width: 1px;
      height: 1px;
      white-space: nowrap; /* https://medium.com/@jessebeach/beware-smushed-off-screen-accessible-text-5952a4c2cbfe */
    }

Having visually hidden the controls, I can now create some fake visible replacement controls using CSS:
    
    
    input[type=radio] + label:before,
    input[type=checkbox] + label:before {
      content: '';
      background: #fff;
      border: .1em solid rgba(0, 0, 0, .75);
      background-color: rgba(255, 255, 255, .8);
      display: block;
      box-sizing: border-box;
      float: left;
      width: 1em;
      height: 1em;
      margin-left: -1.5em;
      margin-top: .15em;
      vertical-align: top;
      cursor: pointer;
      text-align: center;
      transition: all .1s ease-out;
    }
    
    input[type=radio] + label:before {
      border-radius: 100%;
    }

Note the `transition`. That helps animate the control just enough that it feels like an action happened instead of just an awkward swap. Note that the radio button is made into a circle, but otherwise is the same code. All sizing is based on `em`s so this should scale to whatever font size you want. You can test it in my example by changing `body { font-size: 100%; }` to whatever value you want.

The radio button is easy. It just gets a fill and shadow. It animates easily enough, and does not get announced by screen readers.
    
    
    input[type=radio]:checked + label:before {
      background-color: #00f;
      box-shadow: inset 0 0 0 .15em rgba(255, 255, 255, .95);
    }

The checkbox could be as easy, but the shape of square versus circle is not enough in my opinion to denote the difference between the two types of controls. Instead I looked for a checkmark character to use. Unfortunately, any character I use will be announced by a screen reader so I have to be careful to choose one that is not confusing.
    
    
    input[type=checkbox] + label:before {
      /*content: '\00d7';*/
      /*content: '\002718';*/
      /*content: '\002715';*/
      /*content: '\0025a0';*/
      content: '\002713';
      font-weight: bold;
      text-align: center;
      line-height: 1.15;
      color: rgba(0, 0, 255, 0);
    }
    
    input[type=checkbox]:checked + label:before {
      color: rgba(0, 0, 255, 1);
      line-height: .75;
      text-shadow: .05em 0 0 rgba(0, 0, 255, 1), -.05em 0 0 rgba(0, 0, 255, 1);
    }

I commented out some examples that you can try. The one I use in the demo is a checkmark, and is stated as such when spoken. It is a bit redundant but acceptable. Also be careful to test across browsers. The character for the heavy checkmark (✔) was rendering fine in all browsers but Edge, where it displayed it as a green checkmark. This meant I could not make it transparent for my animated check effect and it also messed with my `disabled` style. Unfortunately, using the simpler character meant I had to use `text-shadow` to add weight to the standard checkmark character (✓).

## Variations

The colors I chose are arbitrary. You can obviously change them. You can also play around with the CSS generated content. For example, in [this (less accessible) example](https://s.codepen.io/aardrian/debug/ZKNXOW) (embedded below) I replaced the circle in the radio buttons with a peach (🍑), and checkmark in the checkbox with an aubergine (yep, I called 🍆 that).

Please be aware how this impacts a screen reader. As I navigate through the form with the emoji using NVDA and Firefox, this is what I hear (and NVDA is correct to do it this way):

> Peach please send me all the spam radio button checked one of two. 
> 
> Clickable eggplant I have read your terms and they make no sense. 

I kinda like putting screen reader output in `<blockquote>`s when it is talking crazy.

## Update

There is always more than one way to skin a form. From the Twitters, here is a variation using SVG that is hidden from screen readers:

> [@aardrian](https://twitter.com/aardrian) [@a11yhunt](https://twitter.com/a11yhunt) <label class="customCheckbox">  
<input type="checkbox">  
<svg aria-hidden="true"><use/><g/></svg>  
MOAR SPAM??  
</label>
> 
> Florens Verschelde (@fvsch) [May 29, 2017](https://twitter.com/fvsch/status/869297118866964480)
