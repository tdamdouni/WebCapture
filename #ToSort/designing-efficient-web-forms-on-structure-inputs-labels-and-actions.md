# Designing Efficient Web Forms: On Structure, Inputs, Labels And Actions

_Captured: 2017-06-01 at 20:17 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)_

Someone who uses your app or website has a particular goal. Often, the one thing standing between the user and their goal is a form. Forms remain one of the most important types of interactions for users on the web and in apps. In fact, forms are often considered the final step in the journey of completing their goals. Forms are just a means to an end. Users should be able to complete them quickly and without confusion.

In this article, you'll see practical techniques that have been gleaned from usability testing, field testing, eye-tracking studies and actual complaints from disgruntled users. These techniques -- when used correctly -- enable designers to produce faster, easier and more productive form experiences. There's a way you can create and design your own prototypes: All you need to do is to download [Adobe XD](https://adobe.ly/2rVwVsU) (for free) and get started right away. At the end of the article, you'll also find new ways to design forms.

The typical form has the following five components:

  * **Structure**  
This includes the order of fields, the form's appearance on the page and the logical connections between multiple fields.
  * **Input fields**  
These include text fields, password fields, checkboxes, radio buttons, sliders and any other fields designed for user input.
  * **Field labels**  
These tell users what the corresponding input fields mean.
  * **Action button**  
When the user presses this button, an action is performed (such as submission of the data).
  * **Feedback**  
The user is made to understand the result of their input through feedback. Most apps and websites use plain text as a form of feedback. A message will notify the user about the result and can be positive (indicating that the form was submitted successfully) or negative ("The number you've provided is incorrect").

Forms may also have the following components:

  * **Assistance**  
This is any explanation of how to fill out the form.
  * **Validation**  
This automatic check ensures that the user's data is valid.

This article covers many aspects related to structure, input fields, labels, action buttons and validation.

A form is a type of conversation. And like any conversation, it should consist of logical communication between two parties: the user and the app.

Make sure to ask only what you really need. Every extra field you add to a form will affect its conversion rate. Always consider why you are requesting certain information from the user and how you will use it.

Ask details logically from the user's perspective, not from the application or database's perspective. Typically, asking for someone's address before their name would be unusual.

Group related information into logical blocks or sets. The flow from one set of questions to the next will better resemble a conversation. Grouping together related fields will also help users make sense of the information they must fill in. Compare how it works in the contact information form below.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/1-Designing-More-Efficient-Forms-preview-opt.png)[6](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _Group together related fields (Image:_

One of the problems with arranging form fields into multiple columns is that users will likely interpret the fields inconsistently. If a form has horizontally adjacent fields, then the user must scan in a Z pattern, slowing the speed of comprehension and muddying the path to completion. But if a form is in a single column, the path to completion is a straight line down the page.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/2-Designing-More-Efficient-Forms-preview-opt.png)[8](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _On the left, one of many ways to interpret how the form fields relate when they are arranged in a standard two-column layout, versus on the right, a straight line down the page.  
_

Input fields are what enable users to fill in a form. Various types of fields exist for the information you need: text fields, password fields, dropdowns, checkboxes, radio buttons, date-pickers and more.

A rule of thumb in form design is that shorter is better. And this certainly seems intuitive: Less effort on the part of the user will lead to higher conversion. Thus, minimize the number of fields as much as possible. This will make your form feel less loaded, especially when you're requesting a lot of information. However, don't overdo it; no one likes a three-field form that turns into a 30-field interrogation. Displaying only [five to seven input fields](https://en.wikipedia.org/wiki/The_Magical_Number_Seven,_Plus_or_Minus_Two) at a given time is a common practice.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/3-Designing-More-Efficient-Forms-800w-opt.png)[10](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _Combine multiple fields in one easy-to-fill field. (Image: Luke Wroblewski) (View Large version)_

Try to avoid optional fields in forms. But if you use them, at least clearly distinguish which input fields may not be left blank. The convention is to use an asterisk (*) for required fields or the word "optional" for non-required fields (which is preferable in long forms with multiple required fields). If you decide to use an asterisk for mandatory fields, show a hint at the bottom of the form explaining what the asterisk is for, because not everyone understands what it means.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/4-Designing-More-Efficient-Forms-preview-opt.png)[13](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _MailChimp's mailing-list subscription form._

Avoid setting defaults unless you believe a large portion of your users (for example, 90% of them) will select that value. Particularly avoid it for required fields. Why? Because you're likely to introduce errors. People scan online forms quickly, so don't assume they will take the time to parse through all of the choices. They might skip something that already has a value.

But this rule doesn't apply to smart defaults -- that is, values set based on information available about the user. Smart defaults can make form completion faster and more accurate. For example, preselect the user's country based on geo-location data. Still, use these with caution, because users tend to leave preselected fields as they are.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/5-Designing-More-Efficient-Forms-preview-opt.png)[14](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _An intelligently preselected country in the checkout form_

Field masking is a technique that helps users format inputted text. A mask appears once a user focuses on a field, and it formats the text automatically as the field is being filled out, helping users to focus on the required data and to more easily notice errors. In the example below, the parentheses, spaces and dashes are applied automatically as the phone and credit-card numbers are entered. This simple technique saves time and effort with phone numbers, credit cards, currencies and more.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/6-Designing-More-Efficient-Forms.gif)[15](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _(Image: [Josh Morony](https://www.joshmorony.com/wp-content/uploads/2017/01/input-mask.gif)[16](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/))  
_

Users should be able to focus on and edit every field using only the keyboard. Power users, who tend to use the keyboard heavily, should be able to easily tab through and edit fields, all without lifting their fingers off the keyboard. You can find detailed requirements for keyboard interaction in the [W3C's guidelines on design patterns](https://www.w3.org/TR/wai-aria-practices/#aria_ex).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/7-Designing-More-Efficient-Forms-800w-opt.png)[18](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _Even a simple date-picker should adhere to the W3C's guidelines. (Image: Salesforce) (_

Autofocusing a field gives the user an indication and a starting point to quickly begin filling out a form. Provide a clear visual signal that focus has moved there, whether by changing a color, fading in a box, flashing an arrow, whatever. Amazon's registration form has both autofocus and visual indicators.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/8-Designing-More-Efficient-Forms-800w-opt.png)[20](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _View large version_

Phone users appreciate apps that provide the appropriate keyboard for text being requested. Implement this consistently throughout the app, rather than merely for certain tasks but not others.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/9-Designing-More-Efficient-Forms-preview-opt.png)[22](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _(Image: [Google](https://www.thinkwithgoogle.com/articles/chapter-5-form-entry.html)[23](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/))  
_

With more and more people using mobile screens, anything that can be done to prevent unnecessary typing will improve the user experience and decrease errors. Autocompletion makes it possible to eliminate a huge amount of typing. For example, filling out an address field is often the most problematic part of any registration form. A tool such as [Place Autocomplete Address Form](https://developers.google.com/maps/documentation/javascript/examples/places-autocomplete-addressform) (which uses both geo-location and address prefilling to provide accurate suggestions based on the user's exact location) enables users to enter their address with fewer keystrokes than regular input fields.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/10-Designing-More-Efficient-Forms.gif)[25](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

Clearly written labels are one of the primary ways to make a UI more accessible. A good label tells the user the purpose of the field, maintains its usefulness when focus is on the field itself, and remains visible even after the field has been filled in.

Labels are not help text. Use succinct, short, descriptive labels (a word or two) so that users can quickly scan your form. Previous versions of Amazon's registration form contained a lot of words, which resulted in slow completion rates. The current version is much better and has short labels.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/amazon-sign-in-comparison-800w-opt.png)[26](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _View large version_

In most digital products today, there are two ways to capitalize words:

  * title case: capitalize every word. "This Is Title Case."
  * sentence case: capitalize the first word. "This is sentence case."

Sentence case used for labels has one advantage over title case: It is slightly easier (and, thus, faster) to read. While the difference for short labels is negligible ("Full Name" and "Full name"), for longer labels, sentence case is better. Now You Know How Difficult It Is to Read Long Text in Title Case.

Never use all caps, or else the form will be difficult to read and much harder to scan quickly, because there will be no variation in character height.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/12-Designing-More-Efficient-Forms-preview-opt.png)[28](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _All-caps labels are very hard to read._

Matteo Penzo's 2006 [article on label placement](http://www.uxmatters.com/mt/archives/2006/07/label-placement-in-forms.php) suggests that forms are completed faster if labels are on top of the fields. Top-aligned labels are good if you want users to scan the form as quickly as possible.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/13-Designing-More-Efficient-Forms-800w-opt.png)[30](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _Left-aligned, right-aligned and top-aligned labels (Image: UX Matters) (_

The biggest advantage of **top-aligned labels** is that different-sized labels and localized versions can more easily fit the UI. (This is especially good for screens with limited space.)

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/16-Designing-More-Efficient-Forms-preview-opt.png)[32](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _(Image: [CSS-Tricks](https://css-tricks.com/label-placement-on-forms/)[38](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)[35](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)[33](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/))_

The biggest disadvantage to **left-aligned labels** is that it has the slowest completion times. This is likely because of the visual distance between the label and input field. The shorter the label, the further away it will be from the input. However, a slow completion rate isn't always a bad thing, especially if the form asks for sensitive data. If you are asking for something like a driver's license number or a social security number, you might deliberately want to slow down users a bit to make sure they enter it correctly. Thus, the time spent reading labels for sensitive data is insignificant. Left-aligned labels have another disadvantage: They require more horizontal space, which might be a problem for mobile users.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/14-Designing-More-Efficient-Forms-preview-opt.png)[34](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _(Image: [CSS-Tricks](https://css-tricks.com/label-placement-on-forms/)[38](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)[35](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)[33](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/))_

The big advantage of **right-aligned labels** is the strong visual connection between the label and input. Items near each other appear to be related. This principle isn't new; it derives from the [law of proximity](https://en.wikipedia.org/wiki/Principles_of_grouping), from Gestalt psychology. For short forms, right-aligned labels can have great completion times. The disadvantage is discomfort; such forms lack that hard left edge, which makes it less comfortable to look at and harder to read.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/15-Designing-More-Efficient-Forms-preview-opt.png)[37](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _(Image: [CSS-Tricks](https://css-tricks.com/label-placement-on-forms/)[38](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)[35](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)[33](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/))_

**Takeaway:** If you want users to scan a form quickly, put labels above the fields. The layout will be easier to scan because the eye will move straight down the page. However, if you want users to read carefully, put labels to the left of the fields. This layout will slow down the reader and make them scan in a Z-shaped motion.

A label set as a placeholder in an input field will disappear once the field gains focus; the user will no longer be able to view it. While placeholder text might work for two-field forms (a simple log-in form with username and password fields), it's a poor substitute for visual labels when more information is required from the user.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/17-Designing-More-Efficient-Forms.gif)[39](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _(Image: [snapwi](https://www.snapwi.re/)[40](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/))_

Once the user clicks on the input field, the label will disappear, and so the user cannot double-check that they wrote what was being asked of them. This increases the chance of error. Another problem is that users could mistake placeholder text for prefilled data and, hence, ignore it (as [Nielsen Norman Group's eye-tracking study](https://www.nngroup.com/articles/form-design-placeholders/) confirms).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/18-Designing-More-Efficient-Forms-preview-opt.png)[42](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _Placeholder text as field label_

A good solution for placeholder text is a floating label. The placeholder text would be shown by default, but once an input field is tapped and text is entered, the placeholder text fades out and a top-aligned label animates in.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/19-Designing-More-Efficient-Forms.gif)[43](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _(Image: [MDS](https://dribbble.com/mds)[44](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/))_

**Takeaway:** Don't just rely on placeholders; include a label as well, because once a field has been filled out, the placeholder will no longer be visible. Use a floating label so that users are sure they've filled out the correct field.

When clicked, an action button triggers some activity, such as submission of the form.

A lack of visual distinction between primary and secondary actions can easily lead to failure. Reducing the visual prominence of secondary actions minimizes the risk of error and reinforces people's path to a successful outcome.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/20-Designing-More-Efficient-Forms-preview-opt.png)[45](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _Equal visual weight versus visual distinction (Image: Luke Wroblewski)_

Complex forms usually need a back button. If such a button is located right below an input field (like in the first screenshot below), a user could accidentally click it. Because a back button is a secondary action, make it less accessible (the second form below has the right location for buttons).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/21-Designing-More-Efficient-Forms-800w-opt.png)[46](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _View large version_

Avoid generic words such as "Submit" for actions, because they give the impression that the form itself is generic. Instead, state what action the button will perform when clicked, such as "Create my account" or "Subscribe to weekly offers."

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/22-Designing-More-Efficient-Forms-800w-opt.png)[48](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _View large version_

Avoid multiple action buttons because they might distract users from their goal of submitting the form.

Don't use a reset button. This button almost never helps users and often hurts them. The web would be a happier place if almost all reset buttons were removed.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/23-Designing-More-Efficient-Forms-preview-opt.png)[50](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

Make sure action buttons look like buttons: Indicate that it is possible to click or tap them.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/24-Designing-More-Efficient-Forms.gif)[51](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _Shading indicates that it is possible to click. (Image:_

Design the "Submit" button in a way that clearly indicates the form is being processed after the user's action. This provides feedback to the user while preventing double submission.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/25-Designing-More-Efficient-Forms.gif)[53](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _(Image: [Michael Villar](https://medium.com/@michaelvillar?source=post_header_lockup)[54](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/))_

Form validation errors are inevitable and are a natural part of data entry (because users are prone to making errors). Yes, error-prone conditions should be minimized, but validation errors will never be eliminated. So, the most important question is, How do you make it easy for the user to recover from errors?

Users dislike having to go through the process of filling out a form, only to find out upon submission that they've made an error. Especially frustrating is completing a long form and upon pressing "Submit," you are rewarded with multiple error messages. It's even more annoying when it isn't clear what errors you've committed and where.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/26-Designing-More-Efficient-Forms-preview-opt.png)[55](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _(Image: [Stack Exchange](http://ux.stackexchange.com/questions/33108/how-to-best-show-connectivity)[56](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/))_

Validation should inform users about the correctness of text **as soon as the user has inputted the data**. The primary principle of good form validation is this: Talk to the user! Tell them what is wrong! Real-time inline validation immediately informs the user about the correctness of their data. This approach allows them to correct any errors faster, without having to wait until they press the "Submit" button to see the errors.

However, avoid validating on each keystroke because, in most cases, you simply cannot verify until someone has finished typing an answer. Forms that validate during data entry punish the user as soon as they start entering data.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/27-Designing-More-Efficient-Forms.gif)[57](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _Google Forms states the email address isn't valid before you've finished typing. (Image:_

On the other hand, forms that validate after data entry do not inform the user soon enough that they've fixed an error.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/28-Designing-More-Efficient-Forms.gif)[59](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _Validation in the Apple Store is performed after data entry. (Image:_

Mihael Konjević, in his article "[Inline Validation in Forms: Designing the Experience](https://medium.com/wdstack/inline-validation-in-forms-designing-the-experience-123fb34088ce#.fl86493cl)," examines different validation strategies and proposes a hybrid strategy to satisfy both sides: **Reward early, punish late**.

  * If the user enters data in a field that was in a valid state (i.e. previously inputted data was valid), then validate after data entry.
  * If the user enters data in a field that was in an invalid state (i.e. previously entered data was invalid), then validate during data entry.
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/29-Designing-More-Efficient-Forms.gif)[62](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _A hybrid approach: Reward early, punish late. (Image:_

Jef Raskin once said, "The system should treat all user input as sacred." This is absolutely true for forms. It's great when you start filling in a form and then accidentally refresh the page but the data remains in the fields. Tools like [Garlic.js](http://garlicjs.org) help you to persist a form's values locally until the form is submitted. This way, users won't lose any precious data if they accidentally close the tab or browser.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/30-Designing-More-Efficient-Forms.gif)[65](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _View large version_

Recently, we've seen a lot of excitement around conversational interfaces and chatbots. Several trends are contributing to this phenomenon, but one in particular is that people are [spending more time in messaging apps](http://www.businessinsider.com/the-messaging-app-report-2015-11) than on social networks. This has led to a lot of experimentation with supporting a range of interactions, such as shopping, in threaded conversations, often in a way that mimics messaging. Even as established an element as a web form has undergone a change under this trend. Designers are looking to transform traditional web forms into interactive conversational interfaces.

**Every interface is a conversation.** Traditional forms (the ones we design every day) are quite similar to a conversation. The only difference is the way we ask the questions. But what if we designed our forms to ask questions in a format that more closely reflects real human (not machine) conversation? So, instead of communicating with a machine on its own inhuman terms, you would interact with it on yours. The form shown below creates a conversational context, facilitating understanding without relying on the traditional elements of web forms (such as labels and input fields).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/31-Designing-More-Efficient-Forms-780w.gif)[68](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

> _This form design from Codrops uses a conversational pattern to better resemble the task. (View large version)_

[Conversational Form](https://github.com/space10-community/conversational-form) is an open-source concept that easily turns any form on a web page into a conversational interface. It features conversational replacement of all input elements, reusable variables from previous questions, and complete customization and control over the styling. This project represents an interesting shift in how we think about user experiences and interactions, leaning more towards text-based conversation to help users achieve their goals.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/32-Designing-More-Efficient-Forms.gif)[72](https://www.smashingmagazine.com/2017/06/designing-efficient-web-forms/)

Users can be reluctant to fill out forms, so make the process as easy as possible. Minor changes -- such as grouping related fields and indicating what information goes in each field -- can significantly increase usability. Usability testing is simply indispensable in form design. Very often, testing with just a few people or simply asking a colleague to go through a prototype can give you good insight into how usable a form is.

> This article is part of the UX design series sponsored by Adobe. The newly introduced Adobe Experience Design CC (Beta) tool is made for a [fast and fluid UX design process](https://adobe.ly/2rVwVsU), as it lets you go from idea to prototype faster. Design, prototype and share -- all in one app.  
You can check out more inspiring projects created with Adobe XD on [Behance](https://www.behance.net/galleries/adobe/5/Experience-Design), and also visit the [Adobe XD blog](https://adobe.ly/2rOmEi0) to stay updated and informed. Adobe XD is being updated with new features frequently, and since it's in public Beta, you can [download and test it for free](https://adobe.ly/2rVwVsU).

_(ms, vf, al, yk, il)_
