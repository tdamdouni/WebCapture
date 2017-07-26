- [Editorial workflows for Jekyll blogging · Robert Vojta](http://www.robertvojta.pro/2015/05/12/editorial-workflows-for-jekyll-blogging/)

- [RV: Get GitHub Username](http://www.editorial-workflows.com/workflow/5892638356013056/OyRAZAlfgN0)

* * *

# Editorial workflows for Jekyll blogging

12 May 2015

I decided to switch my blog engine to [Jekyll](http://jekyllrb.com) and host it at [GitHub](https://pages.github.com). [Square Space](http://www.squarespace.com) is good, but kind of bloated and sometimes slow. Also I’m trying to fully leverage my iPad - love [Editorial](http://omz-software.com/editorial/) and would like to use it for blogging as well. Did it and … it does work. Also saved some money, because my blog is in [public repository](https://github.com/robertvojta/robertvojta.github.io).

Everything is stored in git in my case (GitHub) and I have to access it somehow. I can use applications like [Working Copy](http://workingcopyapp.com), leverage [x-callback-url](http://x-callback-url.com), iOS extensions, etc. But I don’t like when iPad is switching between lot of apps to do a simple task. Python support in Editorial is superb and I decided to write my own workflows.

## Post editing

Editorial does support Markdown and there’s no need to do anything special.
Except one thing and it’s [YAML Front Matter](http://jekyllrb.com/docs/frontmatter/). Matter contains blog post settings like category and I would like to reuse them. Here comes the first workflow I made to insert or edit YAML matter and save entered values for future use:

  * [RV: Edit Jekyll Post Settings](http://www.editorial-workflows.com/workflow/5897508043620352/K5vl5H_YCBA)

![](/public/images/editorial-jekyll-post-settings.jpg)

## Authorization

Decided to go with personal access token. Not the best way, but suits all my needs for now. Two workflows to make it simpler:

  * [RV: GitHub Authorize](http://www.editorial-workflows.com/workflow/5825105095557120/1i4Z41ccOeY)
  * [RV: GitHub Deauthorize](http://www.editorial-workflows.com/workflow/5909219547021312/py1Hrt4A5Gc)

Both were designed to be used as subworkflows. The first one tries to get personal access token from iOS keychain and asks for it if not found. The second one just removes personal access token from iOS keychain.

![](/public/images/editorial-gh-authorize.jpg)

## Repository picker

We can access GitHub contents now. Next step is repository picker:

  * [RV: GitHub Repository Picker](http://www.editorial-workflows.com/workflow/5219762942509056/vJeCG3fhtjk)

This workflow was designed to be used as subworkflow.

![](/public/images/editorial-repository-picker.jpg)

Used by following workflows (image and post upload). These two workflows store
last used repository in `.jekyll-repository`file. You can confirm it or pick
another one:

![](/public/images/editorial-repository-confirmation.jpg)

## Image upload

Blog post without images? No. Another workflow to upload image:

  * [RV: Upload Jekyll Image](http://www.editorial-workflows.com/workflow/5879582930501632/5Sp64WWxQDs)

This workflow asks for image (iOS picker), filename, resizes it if it’s wider than 800 pixels, uploads it and automatically inserts image link in Markdown format. Don’t like it? Open workflow and edit Python script. Behavior is driven by constants defined at the same beginning.

![](/public/images/editorial-upload-image.jpg)

## Post upload

Images uploaded, text prepared, … Time to upload post itself. Another workflow:

  * [RV: Publish Jekyll Post](http://www.editorial-workflows.com/workflow/5813749671788544/LEaziSS3aDU)

This workflow asks for post filename, uploads it and copies link to clipboard.

![](/public/images/editorial-post-upload.jpg)

## Conclusion

iPad is for content consumers only? Meh. Nonsense. As you can see you’re able to do lot of things. Mainly because of [Pythonista](http://omz-software.com/pythonista/) and [Editorial](http://omz-software.com/editorial/) existence.

Everything mentioned in this post was created entirely on iPad along with this post itself. It’s a bit rough now, UI is not pixel perfect, but it works. Install all workflows and all you need to do is to just tap the wrench icon:

![](/public/images/editorial-jekyll-wrench.jpg)

* * *

(C) 2013 - 2015 Robert Vojta. All rights reserved.



