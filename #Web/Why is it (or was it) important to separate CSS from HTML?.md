# Why is it (or was it) important to separate CSS from HTML?

_Captured: 2015-12-16 at 13:16 from [programmers.stackexchange.com](http://programmers.stackexchange.com/questions/271294/why-is-it-or-was-it-important-to-separate-css-from-html)_

## Intro

I recently watched the slides from [React: CSS in JS](https://speakerdeck.com/vjeux/react-css-in-js) and I really like the idea of having CSS applied using JS (and with JSX, this would mean having all the HTML, JS and CSS in one file, which is just great for small, reusable components); however I'm worried about possible problems with semantic/performance/whatever, which lead me to...

Why is it important to separate CSS from HTML?

Obvious reasons I can think of are avoiding duplication and keeping the HTML purely semantic while letting CSS handle the styling. I can do both in JS. Are there any other reasons I'm missing?

**Edit**: I missed a very important thing here - I'm designing architecture for a **big** web application, not some small blog thing. It will have its own build pipeline, with virtually any configuration possible.

**Edit #2**: I see a lot of arguments about separation of concerns, most of which are (in my understanding) based on assumption that it is more often to change just HTML or just CSS and once as opposed to editing HTML and CSS in parallel. While this might be the case for small websites, my commit history shows me the opposite - I usually edit both HTML and CSS together. So instead of separating all HTML from all CSS I would separate each component from each other.

I still don't see any serious drawback of doing this. Caching? Each component file could be cached. Semantic? I could still have semantic in HTML and styles in CSS, just in one file. Re-use and maintainability? It will be even easier with separated components instead of a bunch of HTML and CSS files with unclear relationships. MVC? I could have my mini MVC inside each component.

**Edit #3**: FYI all: @keithjgrant wrote a great folow-up article about this question: <http://keithjgrant.com/posts/against-css-in-js.html>
