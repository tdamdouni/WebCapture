# DeepCoder builds programs using code it finds lying around

_Captured: 2017-02-28 at 02:30 from [techcrunch.com](https://techcrunch.com/2017/02/23/deepcoder-builds-programs-using-code-it-finds-lying-around/?ncid=rss)_

![](https://tctechcrunch2011.files.wordpress.com/2017/02/markus-spiske-207946.jpg?w=738)

Like all great programmers I get most of my code from StackOverflow questions. Can't figure out how to add authentication to Flask? [Easy](http://stackoverflow.com/questions/6972999/flask-user-authentication). Want to shut down sendmail? [Boom](http://stackoverflow.com/questions/10359437/sendmail-how-to-configure-sendmail-on-ubuntu). Now, thanks to all the code on the Internet, a robot can be as smart as a $180,000 coder.

The system, called [DeepCoder](https://openreview.net/pdf?id=ByldLrqlx), basically searches a corpus of code to build a project that works to spec. It's been used to complete programming competitions and could be pointed at a larger set of data to build more complex products.

From the paper:

￼Building an IPS system requires solving two problems. First, the search problem: to find consistent programs we need to search over a suitable set of possible programs. We need to define the set (i.e., the program space) and search procedure. Second, the ranking problem: if there are multiple programs consistent with the input-output examples, which one do we return? Both of these problems are dependent on the specifics of the problem formulation. Thus, the first important decision in formulating an approach to program synthesis is the choice of a Domain Specific Language.

The system gets smarter as it keeps practicing, figuring out which snippets of code work best together and when to use a certain snippet in place of another. Because it "learns" the system can get faster and faster as it builds more programs.

Matej Balog at the University of Cambridge and Alexander L. Gaunt, Marc Brockschmidt, Sebastian Nowozin, Daniel Tarlow at Microsoft Research built the product and co-authored a paper on its use. Programmers note that [a system like this can't build larger projects out of small snippets of code](https://www.newscientist.com/article/mg23331144-500-ai-learns-to-write-its-own-code-by-stealing-from-other-programs/) which, to be fair, sounds like whistling past the graveyard.

Given that this is how many programmers work - cutting up code and repurposing it - this seems like an excellent use for deep learning systems. I can imagine this being a great solution for simple CRUD apps - the basic tools needed to update and add records to a database. In fact, it could mean the end of the entry level programmer job all together. I, for one, welcome our job-killing AI-powered robot overlords.
