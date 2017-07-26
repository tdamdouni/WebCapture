# Become a Better Programmer by Mastering Google

_Captured: 2017-05-25 at 21:21 from [dzone.com](https://dzone.com/articles/become-a-better-programmer-by-mastering-google?oid=twitter&utm_content=buffer757b7&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190137&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190137&u=https%3A%2F%2Fwww.wakanda.io%2F).

Modern programming is now often equated to being really good at Google. If you're trying to achieve something in code, 99% of the time it's likely that someone else has already done it and posted it up on Stack Overflow or Github. No longer is there a need for a stack of textbooks at a developers desk; instead, we just need to type it into the search box and hope it shows up in the first 9 results.

What a lot of people don't realise is that Google has a lot of powerful tricks hidden up it's sleeve. As much as we have become obssesed with the power of keyboard shortcuts for speed and agility in coding, there are a selection of commands which can take your Google-fu to the next level. Here are some of those commands and how they can be best used by a developer.

## Exact Phrase Search

If you wrap part or all of your search with quotation marks, Google will search for the exact phrase entered, unlike normal where it searches for the words individually. This is my most common go-to power function on Google.

As a developer, this can be really useful when searching for exception strings. You know you want that exact exception without variance, so this can cut out the cruft in the results.

**Example**

_"Failed to parse configuration at: logging.appenders.[0]" mvn assembly plugin_

The exact exception text is in the quotations, but I've then thrown in some extra terms that are relevant to help focus.

## Exclude Term

There can be a lot of overlap in our little world of programming. Projects with similar names and overloaded terms can make it very frustrating when combing through search results. It's really easy to exclude a word from search results though; simply add a "-" before a word.

**Example**

_Spark Java -Apache_

Annoyingly in Java there is sparkjava and Apache Spark. If searching for the former, you can remove all Apache based results with ease.

Want to know what the alternatives are to a technology? The related keyword has your back. It expects a URL and will return websites which have a similar content. In practice, I've found it useful for bringing up alternative technologies or frameworks, or finding things which are additive and compatible.

**Example**

_related:mongodb.org_

![Image title](https://dzone.com/storage/temp/1020308-screen-shot-2016-01-21-at-70724-pm.png)

> _We now have a list of similar and alternative NoSQL databases to MongoDB._

## FileType

Did you know you can mandate the type of file you want to search for in Google? This can be really useful when looking for printable cheatsheets as you can specify PDF files, although this can be applicable to a host of searches.

**Example**

_IntelliJ shortcuts filetype:PDF_

![Image title](https://dzone.com/storage/temp/1020314-screen-shot-2016-01-21-at-71215-pm.png)

## Search Within a Site

I often find that the search on a website or forum is terrible. Fortunately, Google can rescue the situation. It's possible to specify Google specifically search a site or subdomain.

**Example**

_intellij shortcuts site:stackoverflow.com_

## Bonus Feature! Directly Search a Website From Chrome

Chrome has support for custom search engines. This is immensely powerful, particularly if you're always searching on a particular site such as StackOverflow.

First, right click the address bar and select Edit Search Engines.

![Image title](https://dzone.com/storage/temp/1020332-screen-shot-2016-01-21-at-71805-pm.png)

In the box that comes up, scroll to the bottom of "Other Search Engines". Let's say we want to add support for Stack Overflow. In the first field, we'll put "Stack Overflow" as that's the name of the engine. In the second we need a shortcut; when enabled, we'll type this into the address bar to say that is the engine we want to use. I'll use "so" for this purpose. We then need a URL, where we replace the search term with %s. If we do a sample search on StackOverflow and check out the URL we can see where to replace the term with %s:

![Image title](https://dzone.com/storage/temp/1020337-screen-shot-2016-01-21-at-72452-pm.png)

We replace my term with %s to give us http://www.stackoverflow.com/search?q=%s. Put this into the third field. Click done, and your engine is live.

In the address bar, type "so" then space. Chrome should then tell you you're searching Stack Overflow.

![Image title](https://dzone.com/storage/temp/1020339-screen-shot-2016-01-21-at-72704-pm.png)

> _Pop any questions or queries into the comments, or follow me directly on Twitter via_

[@SambaHK](http://www.twitter.com/sambahk).

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190138&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190138&u=https%3A%2F%2Fwww.wakanda.io%2F).
