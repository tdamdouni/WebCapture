# Reinventing Existing Products – Big Bite vs Small Nibble Rewrites

_Captured: 2017-07-08 at 09:38 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2016/11/reinventing-existing-products-big-bite-vs-small-nibble-rewrites.html?utm_content=buffera29de&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer#.WWCL_oWbGaN)_

Twice now in my career I've done a massive rewrite to replace an existing product. In both cases, it didn't end well. Each time, the new product was competing with an existing product that was making the company money. So, of course, the existing product got enhancements on a rickety structure, and on the new product we never caught up. In one case we solved the problem by getting bought out, in the other, the two products lived side by side for far too long.

It's tempting to say that we'll just start fresh, write it greenfield (i.e. from scratch). It's an attractive idea, because we start off with clean code (no legacy) and we're not hamstrung by decisions of the past.

The problem is that rewrites never happen as rapidly as promised, and never do they deliver everything that is expected. If it must be a massive overhaul and reinvention of an existing product, why not consider doing piece-meal, in-place replacements instead of a total, big-bang rewrite. There are some considerable benefits to this approach:

- Existing Product can gain new features and continue to serve client needs while you're developing new.

- Is more resilient against delays in time to market, which is always longer than you expect.

- Allows for the organizational pressures that created the original product to change. If they don't, then the rewritten product will suffer the same problems as the original.

Use a [strangler approach](http://www.martinfowler.com/bliki/StranglerApplication.html). Replace one small part of the system, adding new features, writing tests, etc. as you go. Do that one small chunk at a time, until the new system replaces the old. Bonus points awarded for going from monolithic to a number of mid-sized services (you'll note I didn't say the overused MicroServices word).

Hmm, I think I just summarized [Feather's book](https://www.amazon.ca/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052/&tag=notesfromatoo-20) in one paragraph. Another good legacy code book: "[The Mikado Method](https://www.amazon.ca/Mikado-Method-Ola-Ellnestam/dp/1617291218/&tag=notesfromatoo-20)". Finally, if you need more Legacy Code reading, checkout out our [Legacy Code Resources](https://agilepainrelief.com/scrum-developer-resources-and-references#living-well-with-legacy-code).

_Image attribution: Unsplash: Alec Weir, Bonnie Kittle_

![big bite vs. small nibble - original photos courtesy of Unsplash](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2016/11/big-bit-small-nibble.jpg)
