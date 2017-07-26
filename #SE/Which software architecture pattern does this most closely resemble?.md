# Which software architecture pattern does this most closely resemble?

_Captured: 2015-12-12 at 22:51 from [programmers.stackexchange.com](http://programmers.stackexchange.com/questions/304936/which-software-architecture-pattern-does-this-most-closely-resemble)_

It has just 4 interoperable components, that may appear in any order, any number of times, within a single source file:

  1. A function containing what is often a large swath of code that takes all the "user input" (GET, POST, and SERVER variables from the web engine), sanitizes it, re-formats it as needed, and returns it as a bundled data structure.
  2. A function that assembles what is often a large chunk of SQL, integrating sanitized parameters and conditional logic, and bundles it up and makes a call with it to a database engine.
  3. A function that takes a data structure received back from a database call, unpacks it, parses its results, and re-formats the elements in what is often another large litany of code.
  4. A function that composes what is often a lengthy blurb of HTML/JavaScript or XML, painstakingly woven together with Alan Turing's beloved conditions and loops.

Inside any component, there could be a mix of front-end code (HTML, etc.), database code (SQL), and server-side code (PHP, Python, Perl, or whatever), all bedfellows.

Surely someone has thought of this before. If so, does it have a name? I've browsed the common architectural patterns and maybe it's one of them, but I'm not familiar enough with the implementation details of all of them to know.

The answer: **a web app**
