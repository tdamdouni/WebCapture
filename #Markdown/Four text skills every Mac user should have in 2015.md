# Four text skills every Mac user should have in 2015

_Captured: 2016-12-21 at 15:54 from [www.macworld.com](http://www.macworld.com/article/2864499/four-text-skills-every-mac-user-should-have-in-2015.html)_

![text tips large 1](http://images.techhive.com/images/article/2015/01/text-tips-large-1-100538767-large.jpg)

The new year is upon us. Although I'm not much for resolutions (with the [occasional exception](http://www.macworld.com/article/2082570/seven-new-years-resolutions-for-the-mac-home-office.html)), this is a time when many people dedicate themselves to improving their lives over the coming months. If you're casting about for resolutions that can boost your productivity, I'd like to suggest learning (or brushing up on) four key skills. They all involve working with text and each of them will benefit almost any Mac user (and, for that matter, almost any computer user, period).

## Write in Markdown

If your work involves writing of almost any kind--blog posts, articles, books, or even academic papers--a couple of hours spent learning the basics of Markdown will pay huge dividends. Many major publications (including _Macworld_) and blogging platforms (including WordPress) support this powerful yet lightweight method of text formatting. You mark up plain text files using simple tags (which are much friendlier and more readable than HTML), and then a behind-the-scenes converter can render that text as a fully formatted document in HTML, PDF, EPUB, or other format.

For example, if you wanted to insert a clickable link using raw HTML, you'd have to do it like this:

`<a href="http://www.macworld.com/">Macworld</a>`

But in Markdown, it's much simpler:

`[Macworld](http://www.macworld.com/)`

In all likelihood you'll quickly get the gist of Markdown just by looking at Markdown creator John Gruber's [Markdown](http://daringfireball.net/projects/markdown/) page, but you may find it more fun to use the interactive [Markdown Tutorial](http://markdowntutorial.com/) website instead.

![editorial](http://images.techhive.com/images/article/2015/01/editorial-100538753-medium.png)

> _Editorial for iOS features syntax styling, Markdown shortcuts, and a built-in preview pane for Markdown documents._

The beauty of Markdown is that because it's based on plain text, you can use virtually any word processor or text editor, on any platform, to write and edit--without sacrificing the richness of full formatting in the final product. I generally work in unadorned Markdown using BBEdit or Nisus Writer Pro, but if you want extra bells and whistles--such as a live preview of the formatted output, shortcuts for adding tags, or syntax coloring--you can find innumerable Markdown editors and utilities in the Mac or iOS App Store. A few examples of highly-rated Markdown apps are Brett Terpstra's [Marked 2](http://www.macworld.com/article/2455118/marked-2-review-preview-and-improve-your-online-writing-on-the-fly.html) (OS X; 5.0 mice, $12), Information Architects' [iA Writer for OS X](http://www.macworld.com/article/1164543/ia_writer_is_a_solid_no_distraction_writing_tool.html) (4.0 mice, $9) and [iOS](http://www.macworld.com/article/1158053/iawriter.html) (3.5 mice, $1), and omz:software's [Editorial](http://www.macworld.com/article/2057231/editorial-for-ipad-review-text-editor-ideal-for-building-custom-workflows.html) (iOS; 5.0 mice, $5).

You're bound to encounter numerous variants of John Gruber's original Markdown specification that add features not supported in the original (such as tables, footnotes, and definition lists) or follow stricter interpretation rules. But the core features are pretty much the same in every implementation, and once you know the basics, you can easily adapt to alternative versions if the need arises.

## Use regular expressions

On countless occasions you've undoubtedly used Spotlight to search for a file on your Mac, or your word processor's Find and Replace feature to locate or change text. But sometimes a simple search doesn't cut it, even with the addition of simple wildcards like `?` for any single character or `*` for multiple characters. For example, what if I want to find every instance of a caption in a book I'm working on--something like "Figure 42: Blah blah blah" and make just the figure number (and the trailing colon) bold--but _not_ touch any references to those figures (like "see Figure 42") in the body text?

In cases like these, which I encounter on a daily basis, I use a regular expression (or "regex" for short), which is a sort of forumla, based on a flexible system of wildcards, that lets me identify nearly any sort of textual pattern. (A regex for the word Figure, followed by a space, one or more digits, and a colon--but only if it appears at the beginning of a line--is `^Figure [0-9]+\:`.)

The best implementation of regex I've ever seen is in Nisus Software's [Nisus Writer Pro](http://www.macworld.com/article/1167342/nisus_writer_pro_2_0_2_full_of_power_features.html) (4.5 mice, $79) (a less-powerful version is found in [Nisus Writer Express](http://www.macworld.com/article/1167325/nisus_writer_express_3_4_1_is_a_solid_word_processor_lacks_high_powered_features.html) (3.5 mice, $45). Other apps that support regex include Bare Bones Software's [TextWrangler](http://www.macworld.com/article/2031703/mac-gems-textwrangler-4-5-is-a-free-text-editor-that-belongs-on-your-mac.html) (5.0 mice, free) and [BBEdit](http://www.macworld.com/article/2852981/bbedit-11-review-the-veteran-text-editor.html) (4.5 mice, $50), Peter Borg's [Smultron](http://www.macworld.com/article/1165773/smultron_is_a_capable_and_inexpensive_text_editor.html) (3.5 mice, $5), and Nikolai Krill's [Patterns](http://www.macworld.com/article/2109200/patterns-review-utility-makes-quick-work-of-regular-expressions.html) (3.5 mice, $3). You can also employ regular expressions to find files on your Mac using the `grep` command-line utility in Terminal. For details, see [Find anything with grep](http://www.macworld.com/article/1041504/jangeekfactor.html).

![nisus writer](http://images.techhive.com/images/article/2015/01/nisus-writer-100538751-large.png)

> _Nisus Writer has the best implementation of regex-based find and replace I've ever seen._

For a quick introduction to regular expressions, see [Transform HTML with regular expressions](http://www.macworld.com/article/1027276/regex.html). A great way to teach yourself the ins and outs of regex is to use an interactive website that shows you matching text in real time as you change your input. Sites that do this include [regexpal](http://regexpal.com/), [RegexOne](http://regexone.com/), and [RegExr](http://www.regexr.com/).

## Use Boolean expressions

Continuing the theme of identifying patterns, sometimes it's not a _sequence_ of characters or words you're looking for but rather a logical combination of terms within a file. For example, I might want to find any email message that contains the word "apple" but only if it also has a term that suggests a dessert, such as "pie," "cobbler," or "whipped cream." Whenever you're looking for a file, message, contact, or other item that contains this _or_ that, this _and_ that, or some other logical combination such as "(this _or_ that) _and_ the other thing but _not_ something else," you want a Boolean expression.

A Boolean expression uses the logical terms AND, OR, and NOT (often along with parentheses and quotation marks) to come up with a "true" or "false" statement. Search for "sticks OR stones" and you'll match anything that has _either_ term; search for "sticks AND stones" and you'll match only items that contain both. For the most part, it's that simple.

You can use Boolean expressions in Spotlight, [Mail rules](http://www.macworld.com/article/2142029/how-to-search-smarter-in-mail.html), Calendar searches, and many third-party apps. Unfortunately, Boolean logic isn't currently supported in Contacts, iTunes, or the App Store.

## Create a secure password

A good password--one that will resist almost any attempt at cracking--should be long and unguessable, with a combination of uppercase and lowercase letters, digits, and punctuation. But when we're asked to create such passwords, many of us encounter a mental block.

You often hear mnemonic tips like "Make a long sentence, and then your password becomes the first letter of each word (and that can include capitalization and punctuation)." That wouldn't be terrible advice if you had only one or two passwords to remember. But you probably have dozens, or maybe even hundreds. (I have well over 700 unique passwords.) One of the worst security mistakes you can make is reusing the same password in multiple places--if one password were stolen, leaked, or cracked, an attacker could access all the accounts that use the same password. Keeping every password unique contains the damage.

![1password](http://images.techhive.com/images/article/2015/01/1password-100538752-large.png)

> _1Password's flexible password generator lets you determine length, number of digits and symbols, and other attributes._

The sane way to create and remember lots of long, random passwords is to use software that does all the work for you, syncs your passwords securely across all your devices, and automatically fills them in when needed. If you use Safari on OS X and iOS, [iCloud Keychain](http://www.macworld.com/article/2058081/how-to-use-icloud-keychain.html) can do all this for you. If you want to use multiple browsers or non-Apple operating systems, if you want longer and stronger passwords, or if you'd like additional features such as storing software licenses and other personal data, you might prefer a third-party app such as AgileBits' [1Password](http://www.macworld.com/article/2839274/review-1password-5-for-mac-offers-state-of-the-art-protection-for-your-passwords-and-more.html) (5 mice, $50), [Dashlane Premium](https://www.dashlane.com/) ($39 per year), or [LastPass](http://www.macworld.com/article/2032046/review-lastpass-takes-your-passwords-to-the-cloud.html) (4.0 mice, free).
