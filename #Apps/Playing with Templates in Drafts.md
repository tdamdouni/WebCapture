# Playing with Templates in Drafts

_Captured: 2016-05-22 at 22:34 from [onetapless.com](https://onetapless.com/playing-with-templates-drafts)_

Each case of automation is unique to the individual and how you organize your life, and the objects around it, is a personal subject. When it comes down how we treat our text files, I doubt that freeform writing covers all the reports, posts, journal entries or most of the notes you jot down.

This post will show a simple way to create dynamic structures in [Drafts](https://itunes.apple.com/us/app/drafts-4-quickly-capture-notes/id905337691?mt=8&uo=4&at=10l4KL) that you can use whenever you have a specific use for a text model.

## Why Drafts?

I'm very comfortable working with [Drafts](https://itunes.apple.com/us/app/drafts-4-quickly-capture-notes/id905337691?mt=8&uo=4&at=10l4KL) for most of my writing, despite lacking the deep automation features offered by [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=4&at=10l4KL) or access to AJAX requests, which are available on [1Writer](https://itunes.apple.com/us/app/1writer/id680469088?mt=8&uo=4&at=10l4KL). Still, you can't beat how simple it is to craft, search for, and trigger actions in Drafts

.

There are also features and implementations that make Drafts a great tool to expand templates, for example, you can chain multiple actions from the app itself, as we gonna do now to open a draft (our template), expand its tags and build a new draft with the generated content. Afterwards, we can even automate actions in the new draft, which we gonna cover later in the article.

## Building a template

I'm going to use one of the templates I use to publish in the site as an example:
    
    
    %%Blog Post%%
    Title: 
    ----
    Date: [[date|%Y-%m-%d %H:%M]]
    ----
    Excerpt: 
    ----
    Text: 

Running this template will generate the following draft:
    
    
    Title: 
    ----
    Date: 2016-05-22 11:59
    ----
    Excerpt: 
    ----
    Text: 

First thing to notice is that the action reserves the first line for a title that is not duplicated to the generated draft

and that the `[[date]]` field was expanded to its value. This would work with any [tag available in Drafts](https://agiletortoise.zendesk.com/hc/en-us/articles/202843484-Templates-and-Tags), such as _latitude_, _longitude_ and _clipboard_ . You can get the action below and play with it a little:

## Creating prompts

One of the things I missed in the previous example is to create prompts on the fly.[ Introduced in version 4.2](https://onetapless.com/taming-the-prompt-on-drafts), prompts are one of the best features of Drafts and since they work like [Launch Center Pro](https://itunes.apple.com/us/app/launch-center-pro/id532016360?mt=8&uo=4&at=10l4KL) lists, you can set its contents dynamically. So I created a template tag for prompts and I run an action that generates the list for us after we expand our template:

Now when you run this action with a content like:
    
    
    [[prompt:Yes=true|No=false|Skip]]

You'll get a nice prompt like this:

![IMG_0351](http://img-1775.kxcdn.com/playing-with-templates-drafts/IMG_0351.png)

> _a prompt with the labels_

If you select "Yes", the `[[prompt]]` will be replaced by _true_, if you choose "No", the new value will be _false_, but if you choose the "Skip", the value will be _Skip_ as well.

It was difficult to support multiple prompts from the same action since you can't invoke a prompt from JavaScript, therefore I can't iterate over multiple prompts and call a prompt for each of them, neither can I skip the prompt step entirely if there's none. You also can't make an action to include itself using the _Include Action_ step or build any sort of recursion with this method, since the step doesn't trigger the included action, it adds its steps. My workaround was to make the action re-open and re-run the action until there's no prompt to parse, so the action looks like this:

  1. A script looks for a `[[prompt]]` tag in the current draft, parses its values and stores everything into custom template tags: `prompt_object` and `prompt_buttons`.
  2. A prompt step will use the values from the `prompt_buttons` to create its list.
  3. Another script will pick the option you selected in the prompt and match it against all the options from the prompt using the `prompt_object` tag. This step also replaces the content and verifies if there are more instances of the `[[prompt]]` tag afterwards.
  4. Re-opens the draft, if there are more prompts to expand, re-calls the action itself. This trigger is set in the previous step.

This workaround is a tad disappointing because I wanted this template engine to be customizable and that you could plug more tags and workflows to parse your templates. You can still do that if you don't use prompts or anything that can't be ignored. You can create modular plugins and add them to a _After Template_ action, which you'd trigger from the _New from Template_ action. Also, nothing prevents you from appending more actions after all prompts are filled.

## Using Launch Center Pro

I've been evaluating the role of some tools in my workflow and [Launch Center Pro](https://itunes.apple.com/us/app/launch-center-pro/id532016360?mt=8&uo=4&at=10l4KL) gained more rounds to keep its spot and it also is the best place to trigger your templates since you can just archive them and call them from the URL scheme with their UUID. For example, this is a valid action:
    
    
    x-drafts4://x-callback-url/open?uuid=968B36CF-4638-49D8-902D-FD0310723816&action={{New From Template}}

Easiest way to get that link is to run the following action that copied the link to the draft and append the _action_ parameter afterwards:

Then in Launch Center Pro you can set multiple actions to trigger different templates by UUID but also different template engines, for example, I have a _New From Template_ action that triggers _Fill Prompts_ afterwards.

![IMG_0353](http://img-1775.kxcdn.com/playing-with-templates-drafts/IMG_0353.png)

> _Linking to different templates from Launch Center Pro._

To create your own, duplicate the _New from Template_ action and add an _action_ parameter to the link called in the URL action step, like `&action={{Fill Prompts}}`. I admit it is a little cumbersome to call the right actions in sequence, but the ultimate goal was to build something you could use in several scenarios.

There are some complex features that could improve this workflow, definitely the one I'd appreciate the most is the ability to request user input from a Script step, easiest way would probably be a version of the Prompt tag, but it probably is much more complicated due to the asynchronous aspect of JavaScript.

My second request is broader and would require all Drafts' actions to share the same context, because right now actions and keys don't have the same environment. You can't access the `draft` object from the keyboard (unless you run an action from it) and you can't actually set a selection from an action (I tried very hard to build a custom template tag that would set the cursor whenever you wanted).

Reading this, I think I'll stick to just asking Greg to keep the sepia theme.
