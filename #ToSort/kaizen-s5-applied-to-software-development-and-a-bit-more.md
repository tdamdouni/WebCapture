# Kaizen 5S Applied to Software Development (And a Bit More)

_Captured: 2018-06-12 at 19:00 from [dzone.com](https://dzone.com/articles/kaizen-5s-applied-to-software-development-and-a-bi?edition=379258&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-06-12)_

Discover how you can [take agile development to the next level](https://dzone.com/go?i=294434&u=https%3A%2F%2Fwww.mendix.com%2Fresources%2Ftaking-agile-development-to-the-next-level-with-low-code-mx%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone) with low-code.

We're still getting used to Agile methodologies, improvements, CI/CD, DevOps and all the newest and fanciest terms.

But, once in a while, let's try to get back to the origin of all these words in order to understand the why and how of these basic mechanisms.

When Toyota (mainly with 大野耐 (Ôno Taiichi), and the ideas of W. Edwards Deming) started creating its [Toyota Production System](http://www.toyota-global.com/company/vision_philosophy/toyota_production_system/), some concepts and ideas came out and 改善 (_kaizen_, or "continuous improvement") was the pillar of such a system.

But, even a _kaizen_ mindset (note that _kaizen_ is a mindset and cultural behavior, not a process!) has its own pillars. One is standard work (see my article on _[Implementing (Two) Kanban Practices with Kaizen in Mind](https://dzone.com/articles/implementing-two-kanban-practices-with-kaizen-in-m)_) and the other is the 5S organization method, the five "S"s being five words coming from the Japanese language:

  1. 整理 (整理せいり, [seiri](http://nihongo.monash.edu/cgi-bin/wwwjdic?1MUJ%E6%95%B4%E7%90%86)), meaning "sort" in English, in _kaizen_ context means "to throw away unused things" (いらないものを捨てる);

  2. 整頓 (せいとん, _[seiton_](http://nihongo.monash.edu/cgi-bin/wwwjdic?1MUJ%E6%95%B4%E9%A0%93)), meaning "set in order" in English, in _kaizen_ context means "to put the things in their right places and leave them there, ready for use";

  3. 清掃 (せいそう, _[seiso_](http://nihongo.monash.edu/cgi-bin/wwwjdic?1MUJ%E6%B8%85%E6%8E%83)), meaning "shine/sweeping" in English, in _kaizen_ context means "clean often" (常に掃除をする);

  4. 清潔 (せいけつ, _[seiketsu](http://nihongo.monash.edu/cgi-bin/wwwjdic?1MUJ%E6%B8%85%E6%BD%94)_), meaning "standardize" in English, in _kaizen_ context means "maintain the 3S behaviors (above) and keep the workplace properly" (3S（上の整理・整頓・清掃）を維持し職場の衛生を保つ);

  5. 躾 (しつけ, _[shitsuke](http://nihongo.monash.edu/cgi-bin/wwwjdic?1MUJ%E8%BA%BE)_), meaning "sustain" in English, in _kaizen_ context means "keep and maintain the selected procedures and apply them as habits" (決められたルール・手順を正しく守る習慣をつける).

All these will be applied to the 現場 (げんば, _[genba](http://nihongo.monash.edu/cgi-bin/wwwjdic?1MUJ現場)_), workplace. So, what about thinking 5S in software development?

Let's consider, for the moment, that our _genba_, our workplace, is the source code.

  * Applying _seiri_, let's remove legacy code, unused methods and variables, commented and duplicated code, etc.

  * With _seiton_, put code in its right place, refactor, rename, reduce to single responsibility, apply design patterns whether needed, and so on.

  * Using _seiso_, repeat the activities above frequently and constantly, running tests (possibly) every time you commit, and not only on new parts of the code. Every time you open a source code file, close it shinier than before.

  * _Seiketsu _represents standard work, a mandatory part of any _kaizen_ initiative. Define and maintain (and enforce!) a coding standard for the team, for your group and possibly even for the whole company. Define and maintain (and enforce!) a set of code quality checks and hints for your IDEs and version control environments. Keep them up-to-date and aligned with technologies improvements.

  * _Shitsuke_, is the concept of repeating the activities above, documenting them as standard procedures and habits, and continuously transforming and improving them.

Let's try to widen the workplace definition to your IDE: remove unused plugins and configurations, properly use the code quality hints in the correct way, share configurations and settings, update and align source code by forcing optimization and formatting on commit.

Let's expand our workplace further: keep your desktop clean. Remove or store unused documents, links and icons, clean up your disk, and define standards to organize development common files across teams (properties configurations, VMs, internal servers ports, etc.).

And keep expanding: "In a desk with only two drawers, office supplies and personal items each should occupy one drawer." (see _[Gemba Kaizen](https://www.amazon.com/Gemba-Kaizen-Commonsense-Continuous-Improvement/dp/0071790357) _by Masaaki Imai.

In order to improve something, anything through _kaizen_, doing more with less, you need to have and define your standard work and to keep maintaining it with the 5S method. Consider every environment you use as a workplace to interact with in order to produce value for your customer.

[Download this eBook ](https://dzone.com/go?i=294435&u=https%3A%2F%2Fwww.mendix.com%2Fresources%2Ftaking-agile-development-to-the-next-level-with-low-code-mx%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone)to learn how to prepare your business for agile adoption, how to ensure the proper business-IT collaboration that is critical for agile development, and how to choose the right stakeholders to increase productivity and enable accelerated time-to-value.

Topics:

kaizen ,software development ,agile methodologies ,lean development ,agile ,kaizen values ,5s methodology

Opinions expressed by DZone contributors are their own.
