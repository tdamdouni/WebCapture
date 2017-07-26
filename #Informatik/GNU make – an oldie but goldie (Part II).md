# GNU make – an oldie but goldie (Part II)

_Captured: 2016-09-07 at 16:07 from [blog.it-agenten.com](http://blog.it-agenten.com/2015/12/gnu-make-an-oldie-but-goldie-part-ii/)_



  * [Webseite](http://it-agenten.com)
  * [Corporate Blog](http://blog.it-agenten.com)

[ ![IT:Agenten GmbH](http://it-agenten.com/fileadmin/templates/img/ita-logo.png) ](http://blog.it-agenten.com) [IT:Agenten GmbH](http://blog.it-agenten.com) Corporate Weblog der IT:Agenten München

  * [Start](http://blog.it-agenten.com)
  * [Events](http://blog.it-agenten.com/events/)
  * [Kontakt](http://blog.it-agenten.com/kontakt/)
  * [Subscribe to RSS](http://blog.it-agenten.com/feed/)

21\. Dezember 2015 

  * by [db](http://blog.it-agenten.com/author/daniel-bruder/)
  * in [company news](http://blog.it-agenten.com/category/company-news/), [development](http://blog.it-agenten.com/category/development/)
  * Kommentare deaktiviert

# GNU make – an oldie but goldie (Part II)

In our [last installment](http://blog.it-agenten.com/?p=2921) we presented a very simple `Makefile` and taught _make_ how to `make sandwich`, visiting a few key concepts on the way ([automatic variables](https://www.gnu.org/software/make/manual/make.html#Automatic-Variables), [pattern rules](https://www.gnu.org/software/make/manual/make.html#Pattern-Rules)). For our toolchain to adapt to different situations (out of bread or out of butter? go do the groceries!) and to present some more concepts let's teach make a few more tricks.

Before a good chef starts working in the kitchen he will make sure the kitchen is nice and clean, so let's teach _make_ how to clean the kitchen (while conforming to the best practices outlined by the make documentation as well as the [user's expectation](https://www.gnu.org/software/make/manual/make.html#Standard-Targets). To cut a long story short, let's write a _target_ named `clean-up-kitchen!` and an alias named `clean`:

    
    
    clean-up-kitchen!:
      rm -f sliced.bread washed.salad sliced.tomatoes butter ham
    
    clean: clean-up-kitchen!

The exclamation mark in the _target_'s name doesn't carry meaning, it is only there to show that this in fact is a valid character in a target's name. Actually, targets are very open to characters you wouldn't expect to work. You are free to use almost every character (thus forming "patterns" in your makefile, such as "private", internal targets vs. public-facing targets), except `%` ([see last installment](http://blog.it-agenten.com/?p=2921)), `*` and `:`.

The target `clean: clean-up-kitchen!` without a _recipe_ can be seen as a simple alias in this case: If `clean` is called, call `clean-up-kitchen!`. If `clean-up-kitchen!` is fulfilled, `clean` will be fulfilled, too, without a recipe.

In one of the targets we have used in our last installment, slicing the bread, we defined another prerequisite, `bread`.

    
    
    sliced.bread: bread
      mv $&lt; $@

What if bread is missing? How to get/fulfill bread? We will have to instruct _make_ to go for the groceries and get us `bread`. If already going for groceries, why not pick up all the ingredients that are needed? Again, let's define that:

    
    
    ingredients = bread butter ham tomatoes salad
    
    $(ingredients): groceries

This again is so simple, there's isn't too much to tell. We define a _variable_ `ingredients`, holding our shopping list of bread, butter, ham, tomatoes and salad.

Following that, we use this variable as the _target_ part of a _rule_ with a _prerequisite_, `groceries`, but without a _recipe_ per se. Essentially, what this means are a few things:

  * once the variable is lazily evaluated (see [link](https://www.gnu.org/software/make/manual/make.html#Flavors)), the rule `$(ingredients): groceries` will basically become `bread butter ham tomatoes salad: groceries`, i.e. multiple _target_s can be cobbled into a single rule, saving space, refactoring work, etc. Likewise, they could be spelled out one-for-one but why would that be a good idea?
  * If anything is missing, one will need to take care of the `groceries` -- which we will define next, making sure that the whole list of ingredients will be checked, but something will only be bought if it is really missing (i.e. file `bread` or whatever doesn't exist).
  * Along the way, we will meet one of the many text manipulation [functions](https://www.gnu.org/software/make/manual/make.html#Functions) of make.

Let's go ahead and look at the current situation…

    
    
    ingredients = bread butter ham tomatoes salad
    
    $(ingredients): groceries

…and add the following:

    
    
    groceries: $(addprefix buy-,$(ingredients))
    
    buy-%: %
      touch $*

In a nutshell, our current state of affairs mean the following:

  * in case any ingredient is missing, say `bread`, then:
  * `bread` will trigger the prerequisite `groceries` through `$(ingredients): groceries`
  * once the target `groceries` is triggered, it will take care of its own prerequisites, which will be provided by a text substitution in its list of prerequites: `$(addprefix buy-,$(ingredients))`
  * `$(addprefix buy-,$(ingredients))` will, as the name suggests, add the prefix `buy-` to the list of `$(ingredients)`, providing yet another list: `buy-bread buy-butter buy-ham buy-tomatoes buy-salad`
  * Whether something needs buying or is still in stock is decided by `buy-%: %`. Remember pattern rules and timestamps from last [installment](http://blog.it-agenten.com/?p=2921)? As long as the _prerequisite_ `bread` is met (by a file existing by the same name), everything is fulfilled and no more action is needed. If this is not the case (no file `bread`), then fulfill the prerequisite by executing the recipe, i.e. `touch bread`. `touch $*` in this case, by the means of another [automatic variable](https://www.gnu.org/software/make/manual/make.html#Automatic-Variables), `$*`, takes care of anything that needs to be bought in an abstract manner: the automatic variable `$*` will hold whatever the "make-glob-sign", `%`, matched in `buy-%: %`

In order to present yet another key concept of make, _order only prerequisites_, let's refactor another small thing and create the following:

    
    
    buy-%: % | clean-up-kitchen!
      touch $*

This is yet another type of prerequisite, an order-only prerequisite. While a normal prerequisite, that needs fulfilling automatically forces the target to update, an order-only prerequisite will not. It is still a prerequisite of the target but it doesn't influence whether the target itself needs updating. Maybe a bit far off for now, but remember this for cases where you want to guarantee, that a certain directory exists. It might come in handy. For now, make will clean our kitchen before going for groceries to make us a sandwich.

Last but not least, let's add a target which offers a quick help to the user and set a new default rule (the first rule of the Makefile):

    
    
    default: help
    
    help: ; @echo "Help yourself: 'make sandwich' or 'make sliced.bread' or 'make bread', and feel at home..."

Key concepts to be seen here:

  * Make let's you append the _recipe_-part of the _rule_ to the same line as the _target_ by placing it behind `;`
  * If a _rule_ begins with `@` it will not be shown to the user while it's running

What we finally arrive at should be the following Makefile:

    
    
    WASH ?= mv
    
    ingredients = bread butter ham tomatoes salad
    
    default: help
    
    help: ; @echo "Help yourself: 'make sandwich' or 'make sliced.bread' or 'make bread', and feel at home..."
    
    buy-%: % | clean-up-kitchen!
        touch $*
    
    clean: clean-up-kitchen!
    
    clean-up-kitchen!:
        rm -f sliced.bread washed.salad sliced.tomatoes butter ham
    
    $(ingredients): groceries
    
    groceries: $(addprefix buy-,$(ingredients))
    
    sliced.%: %
        mv $&lt; $@
    
    washed.%: %
        $(WASH) $&lt; $@
    
    sandwich: sliced.bread washed.salad sliced.tomatoes butter ham
        echo $^ &gt; sandwich

Now as for the usage, `make help` offers good hints: use `make sandwich`, or `make bread`.

Make actually allows for multiple targets to be placed after each other and to be run in order, e.g. `make clean default sandwich`.

Another very interesting feature is `-n`, or `\--dry-run`: in dry-run mode make will display all the commands it _would_ run, without actually running them.

One more interesting option is `-j`, the auto-threading switch. Calling `make -j2 sliced.tomatoes sliced.bread` could, for the sake of the pattern rule, spread out to two CPUs and do the slicing in parallel.

So much for this time. Thanks for reading and hope you're hungry for make now!

[Tweet](http://twitter.com/share)

#### This post was written by 

![](http://0.gravatar.com/avatar/08933fa9951b858974efea8afe0c5df1?s=96&d=http%3A%2F%2F0.gravatar.com%2Favatar%2Fad516503a11cd5ca435acc9bb6523536%3Fs%3D96&r=G)[db]() - who has written [5](http://blog.it-agenten.com/author/daniel-bruder/) posts on [IT:Agenten GmbH](http://blog.it-agenten.com).  

[Email](mailto:db@it-agenten.com)

Tags: [automatic variables](http://blog.it-agenten.com/tag/automatic-variables/), [clean](http://blog.it-agenten.com/tag/clean/), [GNU](http://blog.it-agenten.com/tag/gnu/), [make](http://blog.it-agenten.com/tag/make/), [makefile](http://blog.it-agenten.com/tag/makefile/), [pattern rules](http://blog.it-agenten.com/tag/pattern-rules/), [sandwich](http://blog.it-agenten.com/tag/sandwich/)

«[ GNU make – an oldie but goldie (Part I)](http://blog.it-agenten.com/2015/12/gnu-make-%e2%80%93-an-oldie-but-goldie-part-i/)

[cu @ internetworld 2016 »](http://blog.it-agenten.com/2016/02/cu-internetworld-2016/)

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
