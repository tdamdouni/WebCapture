# GNU make – an oldie but goldie (Part I)

_Captured: 2016-09-07 at 16:06 from [blog.it-agenten.com](http://blog.it-agenten.com/2015/12/gnu-make-%E2%80%93-an-oldie-but-goldie-part-i/)_



  * [Webseite](http://it-agenten.com)
  * [Corporate Blog](http://blog.it-agenten.com)

[ ![IT:Agenten GmbH](http://it-agenten.com/fileadmin/templates/img/ita-logo.png) ](http://blog.it-agenten.com) [IT:Agenten GmbH](http://blog.it-agenten.com) Corporate Weblog der IT:Agenten München

  * [Start](http://blog.it-agenten.com)
  * [Events](http://blog.it-agenten.com/events/)
  * [Kontakt](http://blog.it-agenten.com/kontakt/)
  * [Subscribe to RSS](http://blog.it-agenten.com/feed/)

9\. Dezember 2015 

  * by [db](http://blog.it-agenten.com/author/daniel-bruder/)
  * in [company news](http://blog.it-agenten.com/category/company-news/), [development](http://blog.it-agenten.com/category/development/)
  * Kommentare deaktiviert

# GNU make – an oldie but goldie (Part I)

As far as build systems are concerned, this article will not present anything particularly new – instead, we will focus on some piece of software that one might even considered "done". "Done" in the sense that it is essentially bug-free and feature-complete. How many software products do you know (apart from TeX) that can be considered this way?

With a plethora of "new", "modern" or just plain "fancy" build systems, GNU Make is the old veteran of them all. But why should you care? It is old, it seems clunky at first sight, it is just _not javascript_ – why the hell should we bother?

GNU Make is just plain fantastic, so let's put this old fella to a test and see what it has up its sleeves!

![make sandwich  © xkcd ](http://imgs.xkcd.com/comics/sandwich.png)

  © xkcd

 

But before sending the old veteran to compete in a classic example (make sandwich) with the youngsters, let's have a look whether build system X actually plays in the same league and what makes _make_ so special:

  * Does build system X offer auto-threadability? (_make_ does)
  * Is system X as near to the shell as it can get? (_make_ is)
  * Can it auto-resume on tasks? (_make_ can)
  * Can it intelligtenly figure out ways to find a faraway goal, where you haven't given it direct clues on how to get there? (_make_ will)
  * Is it as concise as possible, while maintaining a maximum of flexibility and thus can be considered "mighty"? (hell yes!)
  * Can it be called "declarative"? (_make_ is the definition of _declarative_!)

Sounds too good to be true? Then, let's visit a classic example, highlighting a few key concepts on the way: let it _make_ a sandwich for us!

Let's start out very simple and let us – in best declarative manner – define how our sandwich is to be built from the ground up.

Well actually: we're coming from the end result. A sandwich is made of sliced bread, butter, ham, sliced tomatoes and a little salad (preferably washed).

Let's write a file named `Makefile` and declare our rules:

    
    
    sandwich: sliced.bread washed.salad sliced.tomatoes butter ham
      echo sliced.bread washed.salad sliced.tomatoes butter ham &gt; sandwich

Now, how do we instruct _make_ to make us a sandwich?

Given you have provided the ingredients, issue a simple `make sandwich` on the commandline and there you go!

    
    
    $ touch sliced.bread washed.salad sliced.tomatoes butter ham
    $ make sandwich
    $ ls
      [...] sandwich

Since `sandwich` is the first and only _target_ we have defined in our _Makefile_, we might also just say `make` – and _make_ will pick up the first target it finds. To make sure we will always get a sandwich when we just say `make`, let's set up a default target which we will keep on top of our _Makefile_, and, for simplicity's sake, call it `default`:

    
    
    default: sandwich
    
    sandwich: sliced.bread washed.salad sliced.tomatoes butter ham
      echo sliced.bread washed.salad sliced.tomatoes butter ham &gt; sandwich

Since we're at it, let's shorten this down a little and get to know our first funky variable, `$^`:

    
    
    default: sandwich
    
    sandwich: sliced.bread washed.salad sliced.tomatoes butter ham
      echo $^ &gt; sandwich

`$^` will hold the names of all _prerequisites_ of our _target_, namely: `sliced.bread`, `washed.salad`, `sliced.tomatoes`, `butter`, and, finally `ham`.

The _rule_ or _recipe_ of our target will paste all of these into our yummy-file called `sandwich` using `echo`.

Let's assume we only have bread (in our case a file called `bread`), not yet "sliced". How do we declare how to slice the bread? We will assume that renaming the file `bread` to be `sliced.bread` will do the job in this case:

    
    
    sliced.bread: bread
        mv bread sliced.bread

So `sliced.bread` will be made out of `bread` by renaming it. Nice. Let's see if it works, by creating a file called bread, and then having it sliced for us through _make_:

    
    
    $ touch bread
    $ make sliced.bread
    $ ls
      sliced.bread

Let's follow right up and do the same for the tomatoes:

    
    
    sliced.tomatoes: tomatoes
      mv tomatoes sliced.tomatoes

See the pattern? Let's go ahead, DRY this out a little and refactor, so we can roll this same pattern (slicing) into one rule for both ingredients: tomatoes _and_ bread. On the way we will yet again meet funky variables (also called "[Automatic Variables](https://www.gnu.org/software/make/manual/make.html#Automatic-Variables)") and, through the refactoring, arrive at a so called "[Pattern Rule](https://www.gnu.org/software/make/manual/make.html#Pattern-Rules)".

    
    
    sliced.%: %
      mv $&lt; $@

Here we go: both rules rolled into one! A "sliced _something_" is made by taking _something_ and slicing (in our case renaming) it from _something_ to _sliced.something_! Easy, huh?

The percent sign `%` in this case is very similar to the shell's globbing `*`. Its name here is `%` however, so that it doesn't collide with the shell's glob-`*`.

Now how about `$< ` and `$@`? As one can easily infer from our former rules, `$< ` will hold the _prerequisite_'s name (`bread` in one case, `tomatoes` in the other), while `$@` will hold the _target_'s name: `sliced.bread` or `sliced.tomatoes` respectively.

Very well, now that we can slice bread as well as tomatoes, let's move on! Washing the salad (or anything else) should be easy enough now:

    
    
    washed.%: %
        mv $&lt; $@

How about we loosen up a little and make the washing itself a little more configurable? Maybe someone will come along and would like to wash the ingredients differently rather than with `mv`? We can certainly account for that, so let's declare the washing mechanism a variable:

    
    
    WASH ?= mv
    
    washed.%: %
        $(WASH) $&lt; $@

Excellent! Make now knows how to make `sliced.bread` from bread, `sliced.tomatoes` from tomatoes and `washed.salad` from salad!

What if we were to _copy_ rather than _move_ in order to wash the salad and how would we go about it? Again, this task is trivial: we simply set the variable that we just declared in order to change the executing mechanism by setting the variable `WASH` to `cp `in our environment:

    
    
    $ make washed.salad WASH=cp
      cp salad washed.salad

Beautiful! Now what if we would like to wash the salad again?

    
    
    $ make washed.salad WASH=cp
      make: 'washed.salad' is up to date.

Obviously, there is no need to wash the salad again and make informs us that everything was done already: clever! Make will figure out that there is nothing to do by inspecting the timestamps: the file `washed.salad` is younger than the `salad` so there can't be any possible changes that would force us to do the same work another time.

To wrap up for this first episode, let's see what we have up to now and continue to have make do the groceries for us in our next installment:

    
    
    WASH ?= mv
    
    default: sandwich
    
    sliced.%: %
      mv $&lt; $@
    
    washed.%: %
      $(WASH) $&lt; $@
    
    sandwich: sliced.bread washed.salad sliced.tomatoes butter ham
      echo $^ &gt; sandwich

Until we have taught make how to do groceries always make sure you have the right ingredients prepared for it by creating the necessary files using `touch bread salad tomatoes butter ham`.

Continue reading: [GNU make - an oldie but goldie (Part II)](http://blog.it-agenten.com/?p=2929)

[Tweet](http://twitter.com/share)

#### This post was written by 

![](http://0.gravatar.com/avatar/08933fa9951b858974efea8afe0c5df1?s=96&d=http%3A%2F%2F0.gravatar.com%2Favatar%2Fad516503a11cd5ca435acc9bb6523536%3Fs%3D96&r=G)[db]() - who has written [5](http://blog.it-agenten.com/author/daniel-bruder/) posts on [IT:Agenten GmbH](http://blog.it-agenten.com).  

[Email](mailto:db@it-agenten.com)

Tags: [automatic variables](http://blog.it-agenten.com/tag/automatic-variables/), [GNU](http://blog.it-agenten.com/tag/gnu/), [make](http://blog.it-agenten.com/tag/make/), [pattern rules](http://blog.it-agenten.com/tag/pattern-rules/), [sandwich](http://blog.it-agenten.com/tag/sandwich/)

«[ The ELK-Stack Experience](http://blog.it-agenten.com/2015/11/the-elk-stack-experience/)

[GNU make – an oldie but goldie (Part II) »](http://blog.it-agenten.com/2015/12/gnu-make-an-oldie-but-goldie-part-ii/)

Comments are closed.

![](wp-content/uploads/2016/09/JSK-Content-Ad-v2.gif)

### Wer schreibt hier?

Die **IT:Agenten** sind Ihre Experten für exzellente Web 2.0 und Enterprise 2.0 Anwendungen. Kunden, Geschäftspartner, Mitarbeiter und Geschäftsfreunde können sich ab sofort in unserem Blog über Neuigkeiten aus dem Umfeld der IT:Agenten informieren.

### Tags

[Apple](http://blog.it-agenten.com/tag/apple/) [Augmented Reality](http://blog.it-agenten.com/tag/augmented-reality/) [automatic variables](http://blog.it-agenten.com/tag/automatic-variables/) [code](http://blog.it-agenten.com/tag/code/) [decoded@mcbw](http://blog.it-agenten.com/tag/decodedmcbw/) [Django](http://blog.it-agenten.com/tag/django/) [DWX](http://blog.it-agenten.com/tag/dwx/) [GNU](http://blog.it-agenten.com/tag/gnu/) [Hackerbrücke](http://blog.it-agenten.com/tag/hackerbrucke/) [Ideen](http://blog.it-agenten.com/tag/ideen/) [Informatik](http://blog.it-agenten.com/tag/informatik/) [IT-Projekte](http://blog.it-agenten.com/tag/it-projekte/) [Java](http://blog.it-agenten.com/tag/java/) [JavaScript](http://blog.it-agenten.com/tag/javascript/) [Komplexität](http://blog.it-agenten.com/tag/komplexitat/) [linux](http://blog.it-agenten.com/tag/linux/) [Logik](http://blog.it-agenten.com/tag/logik/) [make](http://blog.it-agenten.com/tag/make/) [Mathematik](http://blog.it-agenten.com/tag/mathematik/) [Meteor](http://blog.it-agenten.com/tag/meteor/) [mobile](http://blog.it-agenten.com/tag/mobile/) [MongoDB](http://blog.it-agenten.com/tag/mongodb/) [node.js](http://blog.it-agenten.com/tag/node-js/) [NoSQL](http://blog.it-agenten.com/tag/nosql/) [Open Source](http://blog.it-agenten.com/tag/open-source/) [pattern rules](http://blog.it-agenten.com/tag/pattern-rules/) [payment](http://blog.it-agenten.com/tag/payment/) [php](http://blog.it-agenten.com/tag/php/) [programmierung](http://blog.it-agenten.com/tag/programmierung/) [projektmanagement](http://blog.it-agenten.com/tag/projektmanagement/) [QA](http://blog.it-agenten.com/tag/qa/) [QM](http://blog.it-agenten.com/tag/qm/) [Quality Assurance](http://blog.it-agenten.com/tag/quality-assurance/) [qualität](http://blog.it-agenten.com/tag/qualitat/) [sandwich](http://blog.it-agenten.com/tag/sandwich/) [scrum](http://blog.it-agenten.com/tag/scrum/) [security](http://blog.it-agenten.com/tag/security/) [Standardisierung](http://blog.it-agenten.com/tag/standardisierung/) [start up](http://blog.it-agenten.com/tag/start-up/) [Technische Schuld](http://blog.it-agenten.com/tag/technische-schuld/) [testing](http://blog.it-agenten.com/tag/testing/) [ubuntu](http://blog.it-agenten.com/tag/ubuntu/) [user interface](http://blog.it-agenten.com/tag/user-interface/) [Workshop](http://blog.it-agenten.com/tag/workshop/) [zukunft](http://blog.it-agenten.com/tag/zukunft/)

### IT:Agenten Events

No events

### Kategorien

  * [company news](http://blog.it-agenten.com/category/company-news/)
  * [CSS](http://blog.it-agenten.com/category/css/)
  * [development](http://blog.it-agenten.com/category/development/)
  * [Django](http://blog.it-agenten.com/category/development/django/)
  * [ecommerce](http://blog.it-agenten.com/category/ecommerce/)
  * [eZ Publish](http://blog.it-agenten.com/category/ezpublish/)
  * [Git](http://blog.it-agenten.com/category/git/)
  * [Java](http://blog.it-agenten.com/category/java/)
  * [Javascript](http://blog.it-agenten.com/category/javascript-2/)
  * [Messen+Events](http://blog.it-agenten.com/category/messenevents/)
  * [Mobile](http://blog.it-agenten.com/category/mobile-2/)
  * [MySQL](http://blog.it-agenten.com/category/mysql/)
  * [Nachberichte](http://blog.it-agenten.com/category/nachberichte/)
  * [NodeJS](http://blog.it-agenten.com/category/nodejs/)
  * [NoSQL](http://blog.it-agenten.com/category/nosql/)
  * [php](http://blog.it-agenten.com/category/php/)
  * [PostgreSQL](http://blog.it-agenten.com/category/postgresql/)
  * [projektmanagement](http://blog.it-agenten.com/category/projektmanagement/)
  * [Qualitätsmanagement](http://blog.it-agenten.com/category/qualitatsmanagement/)
  * [querdenken](http://blog.it-agenten.com/category/querdenken/)
  * [security](http://blog.it-agenten.com/category/security/)
  * [Tool of the Week](http://blog.it-agenten.com/category/tool-of-the-week/)
  * [UI & UX](http://blog.it-agenten.com/category/ui-ux/)
  * [Unix & Linux](http://blog.it-agenten.com/category/unix-linux/)
  * [zeitgeist](http://blog.it-agenten.com/category/zeitgeist/)

### Blogroll

  * [allfacebook.de](http://allfacebook.de/)
  * [Barcamp München](http://barcampmunich.mixxt.de/)
  * [blog.fefe.de](http://blog.fefe.de/)
  * [deutsche-startups](http://www.deutsche-startups.de)
  * [Förderland.de](http://www.foerderland.de/)
  * [Futurebiz.de](http://www.futurebiz.de/)
  * [Gründerszene.de](http://www.gruenderszene.de/)
  * [Netzwertig.com](http://netzwertig.com)
  * [smashing magazine](http://www.smashingmagazine.com/)
  * [techcrunch.com](http://techcrunch.com/)

### IT:Agenten Events

No events

### Letzte Kommentare

  * [Guido Biermann](http://www.crossvertise.com) bei [Testing und Test-driven Development](http://blog.it-agenten.com/2015/10/testing-und-test-driven-development/#comment-451)
  * Franz bei [Say "No" to NoSQL: Reflexionen über einen Fehlgriff](http://blog.it-agenten.com/2014/10/say-no-to-nosql-reflexionen-uber-einen-fehlgriff/#comment-381)
  * C. Fiedler bei [Talk @ TUM: Tor and the Censorship Arms Race: Lessons Learned](http://blog.it-agenten.com/2013/07/talk-tum-tor-and-the-censorship-arms-race-lessons-learned/#comment-359)
  * Tech-Bert bei [Firefox OS ist da!](http://blog.it-agenten.com/2013/05/firefox-os-ist-da/#comment-346)
  * Florian Sesser bei [Der Seeweg nach Indien](http://blog.it-agenten.com/2012/10/der-seeweg-nach-indien/#comment-326)

### Kategorien

  * [company news](http://blog.it-agenten.com/category/company-news/)
  * [CSS](http://blog.it-agenten.com/category/css/)
  * [development](http://blog.it-agenten.com/category/development/)
    * [Django](http://blog.it-agenten.com/category/development/django/)

  * [ecommerce](http://blog.it-agenten.com/category/ecommerce/)
  * [eZ Publish](http://blog.it-agenten.com/category/ezpublish/)
  * [Git](http://blog.it-agenten.com/category/git/)
  * [Java](http://blog.it-agenten.com/category/java/)
  * [Javascript](http://blog.it-agenten.com/category/javascript-2/)
  * [Messen+Events](http://blog.it-agenten.com/category/messenevents/)
  * [Mobile](http://blog.it-agenten.com/category/mobile-2/)
  * [MySQL](http://blog.it-agenten.com/category/mysql/)
  * [Nachberichte](http://blog.it-agenten.com/category/nachberichte/)
  * [NodeJS](http://blog.it-agenten.com/category/nodejs/)
  * [NoSQL](http://blog.it-agenten.com/category/nosql/)
  * [php](http://blog.it-agenten.com/category/php/)
  * [PostgreSQL](http://blog.it-agenten.com/category/postgresql/)
  * [projektmanagement](http://blog.it-agenten.com/category/projektmanagement/)
  * [Qualitätsmanagement](http://blog.it-agenten.com/category/qualitatsmanagement/)
  * [querdenken](http://blog.it-agenten.com/category/querdenken/)
  * [security](http://blog.it-agenten.com/category/security/)
  * [Tool of the Week](http://blog.it-agenten.com/category/tool-of-the-week/)
  * [UI & UX](http://blog.it-agenten.com/category/ui-ux/)
  * [Unix & Linux](http://blog.it-agenten.com/category/unix-linux/)
  * [zeitgeist](http://blog.it-agenten.com/category/zeitgeist/)

(C) 2011 IT:Agenten GmbH München 

[Impressum](http://it-agenten.com/#imprint))
