# CSS Only Slider

_Captured: 2017-01-31 at 11:46 from [blog.significa.pt](https://blog.significa.pt/css-only-slider-71727effff0b#.q6egl7yxg)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*TUrFr1Bb5H2zodtMPTwMZQ.png?q=20)![](https://cdn-images-1.medium.com/max/800/1*TUrFr1Bb5H2zodtMPTwMZQ.png)

This is a step-by-step tutorial for anyone with a reasanoble amount of knowledge in HTML & SCSS. If you don't want to do it step by step, scroll faster! Plus, I'll be using BEM- if you're not familiar with how BEM should be written, take a look at this: <http://getbem.com/introduction/>

Ok, ready to go! First of all, let's take a look at the design:

#### **Conceptual aside: Radio buttons**

Before starting with the actual tutorial, let me tell you a bit about radio buttons' features and how to use them properly. If you already know how to handle them, feel free to skip this part.

First of all, this is how an input type radio basic markup looks like:
    
    
    <input type=“radio”>

A very important feature about radio buttons that we'll be leveraging during this tutorial is the fact that only one can be checked at the time.   
However, in order to make that happen, all of them require the same **_name_**:
    
    
    <input type=“radio” **name=“slider”**>

Another relevant feature about radio button is that you can define which one is checked directly on the HTML. This will be very useful later on.
    
    
    <input type=“radio” name=“slider” **checked**>

A cool fact is that you don't actually need to click on the radio button itself to make it checked, you might as well click on it's label.   
And in order to get that working, you need this:
    
    
    <label for=“”>This is a clickable label</label>

In order for the label to check a specific radio, you need to identify each radio button, this way the label knows which one it is referring to.   
For this tutorial, we'll use _ID_'s but you may use _classes_ as well -- _classes_ work with radio buttons but not with checkboxes.
    
    
    <input type=“radio” name=“slider” **id=“slider-1”**>

And then we'll make the label refer for it:
    
    
    <label **for=“slider-1”**>This is clickable</label>

That's all we'll need to know regarding radio buttons for now!

#### **1\. The Markup**

**Step 1 -- Wrappers**

Lets start by having a parent _section_ which we'll call **_slider_**. And then lets set up a _div_ inside **_slider_** which we can call **_slider__holder_**.  
The inner one will wrap the slider itself and the outer one will hold the inner, plus the titling content.

**Step 2 -- Radio buttons**

Done that, let's markup the radio buttons. We got to put them as a **_slider__holder_** sibling so we can easily refer to it later on.   
We'll need 5 of them, so:

<section class="section slider">

<input type="radio" name="slider" id="slide-1" class="slider__radio">

<input type="radio" name="slider" id="slide-2" class="slider__radio">

<input type="radio" name="slider" id="slide-3" class="slider__radio" checked>

<input type="radio" name="slider" id="slide-4" class="slider__radio">

<input type="radio" name="slider" id="slide-5" class="slider__radio">

<div class="slider__holder">

</div><!-- slider__holder -->

</section>

Don't forget to change the _ID_'s number on each radio button.  
Plus, I want the middle one to be the visible one on page load, that's why I defined it as **_checked_**.

**Step 3 -- Card as labels**

We want all cards to be clickable, so each one of them will be a label for each one the 5 radios.  
Mind that each **_label for="slide-X"_ **has to refer to each radio button, so don't forget to change the number when you copy and paste.

<section class="section slider">

<input type="radio" name="slider" id="slide-1" class="slider__radio">

<input type="radio" name="slider" id="slide-2" class="slider__radio">

<input type="radio" name="slider" id="slide-3" class="slider__radio" checked>

<input type="radio" name="slider" id="slide-4" class="slider__radio">

<input type="radio" name="slider" id="slide-5" class="slider__radio">

<div class="slider__holder">

<label for="slide-1" class="slider__item slider__item--1 card">

<!-- Card Content goes here -->

</label>

<label for="slide-2" class="slider__item slider__item--2 card">

<!-- Card Content goes here -->

</label>

<label for="slide-3" class="slider__item slider__item--3 card">

<!-- Card Content goes here -->

</label>

<label for="slide-4" class="slider__item slider__item--4 card">

<!-- Card Content goes here -->

</label>

<label for="slide-5" class="slider__item slider__item--5 card">

<!-- Card Content goes here -->

</label>

</div><!-- slider__holder -->

</section>

You might have noticed that each slide has a modifier **_slider__item -- n. _**We'll be using it as soon as we need to refer to each **_slider__item_**.

**Step 4 -- Cards content**

For the content of each card, I'll leave it up to you. I'll do mine but it doesn't influence the slider's functionality in any way, so this is up to your creative designer skills.

**Step 5 -- Navigation bullets**

Besides giving an important visual clue of the current card selected, the bullets below the cards should be clickable to help the navigation between the slides.  
Which is the same as saying that each bullet has to be a label for the radios as well.

Also, lets make **_bullets_** as a new element rather than have it as a **_slider_** element:

Once again we're using **_bullets__item -- n _**modifier since we'll be referring to each one of them separately in the future.

Just place them under **_<div class="slider__holder"></div>_** as a sibling.

Done that, we're done with the markup.

You might have noticed that **_slider_** also has a **_section_** class.  
That's because I wanted to add a section title and description to it and make it as a separate element. It doesn't have any influence in the functionality whatsoever and you're free to ignore it. All the styles will be available in the source code.

Here's the whole snippet:

<section class="section slider">

<div class="section__entry section__entry--center">

<h1 class="section__title heading-2">SCSS Only Slider</h1>

<p class="section__text text">This tutorial will teach you how to 

create a SCSS only responsive slider.</p>

</div>

<input type="radio" name="slider" id="slide-1" class="slider__radio">

<input type="radio" name="slider" id="slide-2" class="slider__radio">

<input type="radio" name="slider" id="slide-3" class="slider__radio" checked>

<input type="radio" name="slider" id="slide-4" class="slider__radio">

<input type="radio" name="slider" id="slide-5" class="slider__radio">

<div class="slider__holder">

<label for="slide-1" class="slider__item slider__item--1 card">

<!-- Card Content goes here -->

</label>

<label for="slide-2" class="slider__item slider__item--2 card">

<!-- Card Content goes here -->

</label>

<label for="slide-3" class="slider__item slider__item--3 card">

<!-- Card Content goes here -->

</label>

<label for="slide-4" class="slider__item slider__item--4 card">

<!-- Card Content goes here -->

</label>

<label for="slide-5" class="slider__item slider__item--5 card">

<!-- Card Content goes here -->

</label>

</div><!-- slider__holder -->

<div class="bullets">

<label for="slide-1" class="bullets__item bullets__item--1"></label>

<label for="slide-2" class="bullets__item bullets__item--2"></label>

<label for="slide-3" class="bullets__item bullets__item--3"></label>

<label for="slide-4" class="bullets__item bullets__item--4"></label>

<label for="slide-5" class="bullets__item bullets__item--5"></label>

</div> <!-- Bullets -->

</section>

#### 2\. The Functionality

Before anything else, I think we should make sure the labels are in fact checking the radio buttons.

The best option would be for us write some text inside the Cards, inside the bullet's **_label_** tag and click on them. If the checked input changes, then it's ok. If not, something might be wrong.

I did the following for debugging:

<section class="section slider">

<div class="section__entry section__entry--center">

<h1 class="section__title heading-2">SCSS Only Slider</h1>

<p class="section__text text">This tutorial will teach you how to 

create a SCSS only responsive slider.</p>

</div>

<input type="radio" name="slider" id="slide-1" class="slider__radio">

<input type="radio" name="slider" id="slide-2" class="slider__radio">

<input type="radio" name="slider" id="slide-3" class="slider__radio" checked>

<input type="radio" name="slider" id="slide-4" class="slider__radio">

<input type="radio" name="slider" id="slide-5" class="slider__radio">

<div class="slider__holder">

<label for="slide-1" class="slider__item slider__item--1 card">

Card 1

</label>

<label for="slide-2" class="slider__item slider__item--2 card">

Card 2

</label>

<label for="slide-3" class="slider__item slider__item--3 card">

Card 3

</label>

<label for="slide-4" class="slider__item slider__item--4 card">

Card 4

</label>

<label for="slide-5" class="slider__item slider__item--5 card">

Card 5

</label>

</div><!-- slider__holder -->

<div class="bullets">

<label for="slide-1" class="bullets__item bullets__item--1">Bullet 1</label>

<label for="slide-2" class="bullets__item bullets__item--2">Bullet 2</label>

<label for="slide-3" class="bullets__item bullets__item--3">Bullet 3</label>

<label for="slide-4" class="bullets__item bullets__item--4">Bullet 4</label>

<label for="slide-5" class="bullets__item bullets__item--5">Bullet 5</label>

</div> <!-- Bullets -->

</section>

As I told you before, I won't make any reference to each slide content and design, I rather focus on the functionality. However, for this tutorial sake, I'll use my design and it's styles as an example.

**Step 1 -- Active Slide**

First of all, we need to set each card default style. Feel free to write your own styles as long as you include a **_transform: scale(0.85) _**_among them._

.slider {

// Your styles

&__item {

transform: scale(0.85);

// Your styles

}

}

Then we need to define how it will look when a certain slide is active. And that's when the fun part starts.

So, when **_#slide-1_** is checked we want .**_slider__item -- 1_** to be 100% scaled, so we do the following:

.slider {

// .slider__item

&__item {

z-index: 2;

transform: scale(0.85);

// .slider__item--1

&\--1 {

// #slide-1:checked ~ .slider__holder .slider__item--1

#slide-1:checked ~ .slider__holder & { 

transform: scale(1);

}

}

}

}

Explaining what just happended:   
First: we referred to **_.slider__item -- 1 _**(line 7);Second: we told it to **_scale(1)_** when **_#slide-1_** is **_checked_** (line 11 and 12);

In current language it means that when **_#slide-1_** is **_checked,_** it's **_sibling's (~)_** **_.slider__holder_** son **_.slider__item -- 1_** will be **_100% scaled_**.

Basically when you click on Card 1 it will get 100% scaled.

Then we must replicate it for the remainder cards. So when we click on Card 2 it will get 100% scaled and the sames for cards 3, 4 and 5.

.slider {

// .slider__item

&__item {

transform: scale(0.85);

// .slider__item--1

&\--1 {

// #slide-1:checked ~ .slider__holder .slider__item--1

#slide-1:checked ~ .slider__holder & { 

transform: scale(1);

}

}

// .slider__item--2

&\--2 {

// #slide-2:checked ~ .slider__holder .slider__item--2

#slide-2:checked ~ .slider__holder & { 

transform: scale(1);

}

}

// .slider__item--3

&\--3 {

// #slide-3:checked ~ .slider__holder .slider__item--3

#slide-3:checked ~ .slider__holder & { 

transform: scale(1);

}

}

// .slider__item--4

&\--4 {

// #slide-4:checked ~ .slider__holder .slider__item--4

#slide-4:checked ~ .slider__holder & { 

transform: scale(1);

}

}

// .slider__item--5

&\--5 {

// #slide-5:checked ~ .slider__holder .slider__item--5

#slide-5:checked ~ .slider__holder & { 

transform: scale(1);

}

}

}

}

At this point, when you click on a card it will get 100% scaled and all the other ones will get smaller -- 85% scaled.

The same will happen if you could click on the bullets since they are labels as well.

**Step 2-- Non Active Slides**

Now, we'll have to define each slide position for when a certain slide is active. In the following case, for example, when **_#slide-1 _**is checked/active, **_.slider__item -- 2_** is 0.85 scaled and translated 100px.

.slider {

// .slider__item

&__item {

&\--1 {

// CARD 1 CONTENT 

}

// .slider__item--2

&\--2 {

// #slide-1:checked ~ .slider__holder .slider__item--2

#slide-1:checked ~ .slider__holder & { 

z-index: 1;

transform: scale(0.85) translateX(100px);

}

}

&\--3 {

// CARD 3 CONTENT 

}

&\--4 {

// CARD 4 CONTENT 

}

&\--5 {

// CARD 5 CONTENT 

}

}

}

And in the following one, **_#slide-1 _**is checked/active, **_.slider__item -- 3 _**is 0.65 scaled, translated 210px and with **_z-index: 0._**

.slider {

// .slider__item

&__item {

&\--1 {

// CARD 1 CONTENT 

}

&\--2 {

// CARD 2 CONTENT 

}

// .slider__item--3

&\--3 {

// #slide-1:checked ~ .slider__holder .slider__item--3

#slide-1:checked ~ .slider__holder & { 

z-index: 0;

transform: scale(0.65) translateX(210px);

}

}

&\--4 {

// CARD 4 CONTENT 

}

&\--5 {

// CARD 5 CONTENT 

}

}

}

And in the following one, **_#slide-1 _**is checked/active, **_.slider__item -- 4 _**and**_ .slider__item -- 5 _**are0.65 scaled, translated 210px, with 0 opacity and with **_z-index: -1._**

.slider {

// .slider__item

&__item {

&\--1 {

// CARD 1 CONTENT 

}

&\--2 {

// CARD 2 CONTENT 

}

&\--3 {

// CARD 3 CONTENT

}

// .slider__item--4

&\--4 {

// #slide-1:checked ~ .slider__holder .slider__item--4

#slide-1:checked ~ .slider__holder & {

z-index: -1;

opacity: 0;

transform: translateX(210px) scale(0.65);

} 

}

// .slider__item--5

&\--5 {

// #slide-1:checked ~ .slider__holder .slider__item--5

#slide-1:checked ~ .slider__holder & {

z-index: -1;

opacity: 0;

transform: translateX(210px) scale(0.65);

} 

}

}

}

And in the following one… there is no following one! Imagine doing this for all the active slides -- defining each card position when a certain slide is active. It would be plain crazy!

Specially because there's a pattern as you can see in the image below:

At certain active cards, some of the remainder ones behave the same way. For example, when card 1 is active, cards 4 and 5 assume the same position -- behind card 3.

**Step 3 -- Loop it!**

To tackled this kind of madness, lets use SCSS loops.   
The following code does exactly the same but saves 90% of trouble!

Take a look:

.slider {

// .slider__item

&__item {

@include default-transition(all);

// Loop through .slider__item--(slide-number)

@for $slide from 1 through 5 {

// .slider__item--(slide-number)

&\--#{$slide} {

// Within each .slider__item--(slide-number) loop through #slide-(number)

@for $i from 1 through 5 {

@if $i <= $slide - 3 {

// For the slides 3 or more positions on the right

// #slide-(number):checked ~ .slider__holder .slider__item--(slide-number)

#slide-#{$i}:checked ~ .slider__holder & {

z-index: -1;

opacity: 0;

transform: translateX(210px) scale(0.65);

}

}

@if $i == $slide - 2 {

// For the slide 2 positions on the right

// #slide-(number):checked ~ .slider__holder .slider__item--(slide-number)

#slide-#{$i}:checked ~ .slider__holder & {

z-index: 0;

transform: translateX(210px) scale(0.65);

}

}

@if $i == $slide - 1 {

// For the slide 1 positions on the right

// #slide-(number):checked ~ .slider__holder .slider__item--(slide-number)

#slide-#{$i}:checked ~ .slider__holder & {

z-index: 1;

transform: translateX(100px) scale(0.85);

}

}

@if $i == $slide {

// For the slide 1 positions under the active one

// #slide-(number):checked ~ .slider__holder .slider__item--(slide-number)

#slide-#{$i}:checked ~ .slider__holder & {

position: relative;

z-index: 2;

transform: translate(0) scale(1);

}

}

@if $i == $slide + 1 {

// For the slide 1 positions on the left

// #slide-(number):checked ~ .slider__holder .slider__item--(slide-number)

#slide-#{$i}:checked ~ .slider__holder & {

z-index: 1;

transform: translateX(-100px) scale(0.85);

}

}

@if $i == $slide + 2 {

// For the slide 2 positions on the left

// #slide-(number):checked ~ .slider__holder .slider__item--(slide-number)

#slide-#{$i}:checked ~ .slider__holder & {

z-index: 0;

transform: translateX(-210px) scale(0.65);

}

}

@if $i >= $slide + 3 {

// For the slide 3 positions or more on the left

// #slide-(number):checked ~ .slider__holder .slider__item--(slide-number)

#slide-#{$i}:checked ~ .slider__holder & {

z-index: -1;

opacity: 0;

transform: translateX(-210px) scale(0.65);

}

}

}

}

}

}

}

Let me explain:

  * Inside each loop iteration, we loop again all slides, validating if:  
\- The current slide is **3 or more** positions to the right  
\- is **2** positions to the right  
\- is **1** position to the right  
\- **is the current slide**  
\- is **1** position to the left  
\- is **2** positions to the left  
\- is **3 or more** positions to the left

This way, we can tackle all the possibilities and give them style accordingly.  
Take a second look at the following image for further understanding:

**Step 4-- Bullets**

Now, we have to have a loop for the bullets as well:

.bullets {

// .bullets__item

&__item {

@include default-transition();

// Loops through all the bullet points

@for $bullet from 1 through 5 {

// .bullets__item--(bullet-number)

&\--#{$bullet} {

// #slide-(number):checked ~ .bullets .bullets__item--(bullet-number)

#slide-#{$bullet}:checked ~ .bullets & {

background: $white;

}

}

}

}

}

This is a much simpler loop since you just have to define the active one.  
Don't forget to style it.

We just built a card slider that works on any browser and any device, highly performative (using GPU transitions) without the need of a single line of Javascript.

The same logic can be applied to build image sliders, tabbed content, and many more.

We hope everything was easy to follow and if you have any questions or comments, drop us a line in the commenting section!

If you liked it, please press 💚. It will let us know you want us to keep on writing more stuff like this.

**Update:** we've seen some comments regarding the pertinence of this tutorial and we just want to make clear that javascript isn't, by any mean, a bad choice to achieve something like this. In fact, javascript probably IS the way to go. This tutorial is intended to stretch the boundaries of CSS a bit and learn some cool things like Sass loops while we're at it :)
