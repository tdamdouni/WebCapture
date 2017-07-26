# Prune: A Code Editor that is Not a Text Editor

_Captured: 2015-08-23 at 09:39 from [m.facebook.com](https://m.facebook.com/notes/kent-beck/prune-a-code-editor-that-is-not-a-text-editor/1012061842160013)_

> Co-authored with Thiago Hirai

You want to change the tree structure of a program. You figure out what series of text editing operations, operations that manipulate a 2D grid of characters, are equivalent to the change in the tree you desire. What a waste of time and energy.

![](https://fbcdn-photos-b-a.akamaihd.net/hphotos-ak-xfp1/v/t1.0-0/11887919_10153576066383675_9029286239017821809_n.jpg?oh=3a3973c93ed186e665b37c16766f28be&oe=567CC21D&__gda__=1446731128_80d2b4b5332f55a5ecdd669b269b8dec)Programmers waste energy translating tree transformations into character grid transformations

Religious editor wars are a symptom that the whole paradigm of editing programs with a text editor is broken. Text editors for code have been universally used for decades, however.

Prune lets programmers edit the tree structure directly using commands invoked by typing and rendering the resulting code in a familiar textual format. However, it's time for someone else to pick up the torch of tree-based editing.

![](https://fbcdn-photos-h-a.akamaihd.net/hphotos-ak-xtp1/v/t1.0-0/p720x720/11924259_10153576067688675_6046809493243199041_n.jpg?oh=a4c9e0604aef0efff87cbd02c74d2acf&oe=5678E0AC&__gda__=1451211034_11d5ce3d2af4217087bab032b991bd17)In Prune, programmers transform the tree directly

Prune is a code editor that operates directly on the tree structure of the code. While it renders code in a familiar textual format, it doesn't offer text editing operations. Programs are created and edited by creating, deleting, and re-organizing nodes in the program's abstract syntax tree.

Prune grew out of hundreds of hours of observing programmers editing programs with text editors. Proficient users spent considerable energy learning and optimizing their use of the editor. Unskilled users spent considerable energy using the editor badly. Perhaps the problem is not their skill, but the whole idea of using a text editor, a very general tool, for the specific task of program editing.

Structure editors have been around for decades, yet they never caught on for mainstream usage. Prune would have to be substantially better to have a chance of being adopted. While our overall goal was to reduce the cognitive load of manipulating programs, "cognitive load" is hard to measure, so we chose three quantifiable goals:

  * Fewer keystrokes 
  * Fewer errors 
  * Greater overall efficiency

The fundamental operation in Prune takes one program tree and produces another. For example, making a statement conditional is a single operation:
    
    
    cache = computeValue;
    ==>
    if (!cache) {
      cache = computeValue;
    }

This transformation is one of a class of "wrap" transformation--take the current selection, make it a child of a new node, and replace the selection with the new node. Other "wraps" are looping over a statement or statements, surrounding statements with an exception handler, and returning the value of an expression. Mirror "unwrap" transformations replace a parent node with one or more of its children, such as making a statement unconditional only executing it once instead of in a loop. Other transformations create nodes, delete nodes, and reorder nodes.

The transformations are all atomic, in that they take a syntactically correct program and produce another syntactically correct program. This is one way Prune helps reduce errors--programs are syntactically correct by construction. The transformations compose--each takes a tree and a selection and produces a tree and a selection that can act as the input to another transformation. Once we had a basic library of transformations, we found that we could sometimes synthesize new transformations by composition instead of having to write new code to manipulate the tree. The transformations are also reversible, a property lacking in many text editors that have been enhanced to work on code.

One serendipitous discovery that deserves special mention is the TBD node, used above. Some transformations require two or more parameters. For example, creating a binary expression requires a left side, a right side, and an operator. In a panic we added a special node to the tree representing code to be filled in later. We found it useful in many situations and it never intruded on our work as users of Prune. It did require us to modify the pretty printer we used (esprima), but it was well worth it.

One piece of interface philosophy we carried through Prune is that the editor should allow the user to build a tree by introducing nodes in any order. We have so little experience coding through tree transformations that we have no confidence we have found the most efficient sequence (if one exists).

One of the risks we identified at the beginning of the project was the number of distinct transformation. If hundreds or thousands of distinct transformations were required to program effectively no one would want to learn them all.

It turns out that a hundred or so transformation suffice for editing JavaScript (our source and our target language). Even a hundred transformations is a lot to remember. When we measured our performance editing samples of code, we found selecting transformations and entering identifiers to be a bottleneck.

To accelerate editing and make Prune feel more familiar, we created a typeahead. When the user begins typing, Prune can guess what tree transformation is implied. For example, typing "if" implies a conditional, a guess that is confirmed when a space follows. The If transformation is invoked at that point, leaving the typeahead ready for input at the condition.

With practice, pruning with the typeahead feels a little like just typing. However, all the "noise" characters, put there just to make the parser happy, like parentheses and curly braces appear automatically. Typeahead adds to the efficiency of editing, reduces keystrokes, and makes Prune more approachable.

Prune began as a part-time project, motivated, as mentioned earlier, by watching programmers struggle with text editors. The first prototype was completely simulated on paper, just enough to validate that reducing the keystroke count was possible.

With that bit of evidence in hand, the authors applied for a Hackamonth. After a year with the same team, Facebook engineers are encouraged to take a month and work on something unrelated. It's considered reasonable to fail attempting an ambitious hack, so off we went. Early in the project we created a Facebook-only group devoted to Prune, which slowly accumulated interested members as we posted the results of experiments, demo videos, and the occasional plea for someone to put us out of our misery.

After the first month we had a version of Prune that we were able to frequently use to add features to Prune. However, reflection on usage showed that our pure "invoke transformations through key bindings" wasn't going give us the efficiency we wanted. We applied for a second month to implement and measure the typeahead.

At the end of the second month the developers and those who were interested in embedding Prune in their tools met to discuss its future. In the end we struck a rock we had identified in our first presentation--programmers don't spend that much time manipulating programs compared to all the other things they do. Doing the math, enabling a few hundred programmers to do a 50% better job (an ambitious goal) of a task requiring 10% of their time just doesn't make economic sense.

However, we were surprised by what we learned working on Prune and we hope the ideas live and grow. That's why we are publishing this, in hopes that a graduate student somewhere won't mind a project that takes over his or her life and brings joy to (eventually) millions.

  * Pure tree transformation is a viable option for editing code. The goals of reducing keystrokes and errors are within reach.
  * Insisting on a pure tree transformation-based editor accelerated our research. If we had a text editor to fall back on, we wouldn't have thought hard enough about the problems that were eventually solved by the typeahead.
  * Dogfooding is a powerful resource allocation heuristic. A complete code editor is a sizeable beast, but implementing what we needed to make the next change to Prune in Prune gave us a series of bite-sized features in a reasonable order. Bad experiences helped us quickly eliminate bad ideas.
  * Structure research around questions, not features. We were able to get answers to critical questions about efficiency quickly because we were explicit about what questions we were asking. Working features to completion would have delayed, by months or years, those answers.
  * Collaborate. Most Hackamonths are fairly solitary affairs, with an engineer seconded to a host team but running a separate project. We coded together daily in spite of our geographical split, which resulted in faster learning, more energy, and fewer dead-ends.
  * We didn't miss formatting. We are both fussy about code formatting, but almost as soon as we were constrained to what the pretty-printer (esprima) gave us, we didn't waste any more thought on it.
  * Typing is an effective way of identifying and invoking tree transformations.

One of the curses and blessings of programming at Facebook is there is no shortage of impact work, so both of us reluctantly decided to move on. We still believe in the promise of tree-based editing and would love to use a completed version of Prune. We hope to encourage someone out there to take up the torch. Here are a few tips if it's you:

  * Target a tablet first. Going head-to-head with vim and emacs is always going to be tough. Deliver on an input-deprived format like tablets, though, and you increase your chance of success. Prune's sparing use of input may also open up the possibility of voice input or other ways of making programming accessible to programmers who find typing difficult.
  * Use a declarative language to define transformations. We defined out transformations imperatively, which was tedious and error prone.
  * Use a predictive parser, one that can tell you what characters can legally come next and what tree transformations each character implies. We wrote an ugly, fragile state machine for our typeahead, which quickly became a source of pain and shame.
  * Try to use the language-oriented tools from JetBrains. It seems like they have infrastructure that might make Prune an order of magnitude easier to implement.
  * Implement macros. Letting programmers compose their own sequences of composable transformations seems like a good way to learn what operations are needed.
  * Reuse the transformations. It seems like it should be possible to write a version control system that merges streams of transformations instead of textual diffs, potentially reducing the number of merge conflicts.
  * Code tree transformations declaratively. We coded them imperatively and it took much too long.
  * To further reduce the input required, consider using machine learning to predict which transformation will come next. Tune it well enough and much of programming could become "yep, yep, yep", saving the hard thinking for the hard problems.
