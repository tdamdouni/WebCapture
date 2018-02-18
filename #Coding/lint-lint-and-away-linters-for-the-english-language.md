# Lint, Lint and Away! Linters for the English Language

_Captured: 2018-02-18 at 21:46 from [dzone.com](https://dzone.com/articles/lint-lint-and-away-linters-for-the-english-languag?edition=362110&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-18)_

You have probably used linters to check the quality of your code, but there is also a myriad of linters available for providing best practice guidance on your writing. In this post, I'll round up those that I've discovered, what they do, and how you can use them.

## Alex

[Alex](https://github.com/wooorm/alex) is a single purpose linter to highlight potentially insensitive words on the basis of gender, race, religion or other potentially insensitive language. Such as:

> He started the master node and connected two slaves to it.

In this case, Alex would suggest you replace "he" with "they" and use different terms for "master" and "slave."

Alex is available for:

  * [npm](https://www.npmjs.com/package/alex), that you can also hook up to CI systems.

## Just Say No

Another single purpose linter, Just Say No highlights so-called "hedge words," which can often make your writing sound unconvincing, unconfident, or are unnecessary noise. Such as:

> React seems like a good fit for your project.

In this case, the linter would suggest you replace "seems" with something more confident, such as:

> React is a good fit for your project.

Just Say No is available for:

  * [Atom](https://github.com/lexicalunit/linter-just-say-no)

## Write Good

One of my favorite linters, [write good](https://github.com/btford/write-good) highlights a selection of possible problems with your text, with checks that you can enable or disable. For example:

> Just install the package, it's really easy.

In this case, the linter highlights "just" and "really" as words that weaken the meaning of a sentence.

Write good is available for:

## Prose

[Proselint](http://proselint.com/)'s use is a little more vague than some of the others on this list, combining learning from a collection of "great" writers (in quote marks as this is subjective) to help you write better prose. It's a little unclear what checks it undertakes, but as it works more broadly, analyzing whole sentences instead of individual words, it could help you find issues that other linters mentioned so far won't.

For example:

> In the centre of the center sat a bunch of cats. What were they doing.

In this case, prose would highlight the inconsistent spelling of center/centre and correct "bunch of cats" to "glaring of cats." [Here's a full list](http://proselint.com/checks/) of what it checks for.

Prose lint is available for:

  * [Python](https://pypi.python.org/pypi/proselint) that you can connect to CI systems.

## Vale

Moving us into the bigger, more configurable linters, [Vale](https://valelint.github.io/docs/) combines a series of checks from other linters, [and also lets you add your style definitions](https://valelint.github.io/docs/styles/) to check for, which is useful for in-house style guides. Thanks to this feature, others have contributed custom styles for write-good and proselint meaning you can use Vale to manage a selection of linters for you. You can create global or project level configuration files on a project basis that enable specific checks, and it supports more text formats than many of the linters here.

Because of this extensibility, it's hard to provide a concrete example of what Vale recommends, but for example:

> You are not old enough to be published.

Depending on what you've enabled, Vale would suggest replacing "not old enough" with "too young" (A "Litotes" check), and "be published" as an example of passive voice.

Vale is available for:

## Textlint

In a similar vein to Vale, [Textlint](https://textlint.github.io/) is pluggable, configurable linter with support for many of the other linters (or similar) mentioned here. By default, nothing is enabled, and you need to create global or project level configuration files for Textlint to check anything. For example:

> This is very useful, but how much is TBD.

In this case, the linter highlights "very" and "TBD" (as an unexpanded acronym).

Textlint is available for:

## Coala

Again [Coala](https://www.coala.io/#/home) combines several linters, aiming to create an all-in-one linter you can use for your entire project, code as well as documentation. [You do this by adding "](https://coala.io/#/languages)[bears"](https://coala.io/#/languages) that are other linters packaged to work with Coala, and this includes many of those on this list.

Coala is available for:

## And There Are More!

The list above are my favorite and most commonly used linters, and those with good editor support, but naturally, there are more.

  * [Anorack](http://jwilk.net/software/anorack) for checking you use the correct indefinite article.
  * [American](https://atom.io/packages/linter-american) for correcting those sneaky British spellings.
  * [IBM Style guide](https://atom.io/packages/linter-ibmstyleguide) a linter for checking your documents against the IBM writing style guide.

Also, honorable mentions for tools like [Hemmingway](http://www.hemingwayapp.com), [Grammarly](https://www.grammarly.com), [Nitpicker](http://nitpickertool.com), and [Langauge Tool](https://languagetool.org) which I use on a regular basis, but are not optimized for technical writing and are all standalone tools that you can't hook up to CI, or use with APIs etc.
