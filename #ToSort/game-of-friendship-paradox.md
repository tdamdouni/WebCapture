# Game of Friendship Paradox

_Captured: 2018-07-19 at 19:09 from [dzone.com](https://dzone.com/articles/game-of-friendship-paradox?edition=385254&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-07-19)_

In the introduction of my course next week, I will (briefly) mention networks, and I wanted to provide some illustration of the Friendship Paradox. On [network of thrones](https://www.macalester.edu/~abeverid/thrones.html) (discussed in [Beveridge and Shan (2016)](https://www.maa.org/sites/default/files/pdf/Mathhorizons/NetworkofThrones%20\(1\).pdf)), there is a dataset with the network of characters in [Game of Thrones](https://en.wikipedia.org/wiki/Game_of_Thrones). The word "friend" might be abusive here, but let's continue to call connected nodes "friends." The friendship paradox states that:

> People, on average, have fewer friends than their friends.

This was discussed in [Feld (1991)](http://www.macroeconomics.tu-berlin.de/fileadmin/fg124/networks/Lectures/Summer2012/Material/American_Journal_of_Sociology_1991_Feld.pdf) for instance, or [Zuckerman & Jost (2001)](http://www.psych.nyu.edu/jost/Zuckerman%20&%20Jost%20\(2001\)%20What%20Makes%20You%20Think%20You%27re%20So%20Popular1.pdf). Let's try to see what it means here. First, let us get a copy of the dataset:
    
    
    download.file("https://www.macalester.edu/~abeverid/data/stormofswords.csv","got.csv")

Because it is difficult for me to incorporate some [d3.js](https://en.wikipedia.org/wiki/D3.js) scripts in the post, I will illustrate this with a more basic graph:

![](https://f-origin.hypotheses.org/wp-content/blogs.dir/253/files/2018/06/graph-of-thrones.png)

Consider a vertex v ∈V in the undirected graph G=(V,E) (with classical graph notations), and let d(v) denote the number of edges touching it (i.e., v has d(v) friends). The average number of friends of a random person in the graph is:

![Image title](https://dzone.com/storage/temp/9769887-screen-shot-2018-07-17-at-113315-am.png)

The average number of friends that a typical friend has is:

![Image title](https://dzone.com/storage/temp/9769890-screen-shot-2018-07-17-at-113342-am.png)

But:

![Image title](https://dzone.com/storage/temp/9769893-screen-shot-2018-07-17-at-113402-am.png)

Thus:

![Image title](https://dzone.com/storage/temp/9769894-screen-shot-2018-07-17-at-113432-am.png)

Note that this can be related to the variance decomposition:

i.e.:

![Image title](https://dzone.com/storage/temp/9769896-screen-shot-2018-07-17-at-113452-am.png)

(Jensen inequality). But let us get back to our network. The list of nodes is:
    
    
    M=(rbind(as.matrix(GoT[,1:2]),as.matrix(GoT[,2:1])))

And we each of them, we can get the list of friends, and the number of friends:
    
    
    friends = function(x) as.character(M[which(M[,1]==x),2])
    
    
    nb_friends = Vectorize(function(x) length(friends(x)))

As well as the number of friends our friends have, and the average number of friends.
    
    
    friends_of_friends = function(y) (Vectorize(function(x) length(friends(x)))(friends(y)))
    
    
    nb_friends_of_friends = Vectorize(function(x) mean(friends_of_friends(x)))

We can look at the density of the number of friends, for a random node.

![](https://f-origin.hypotheses.org/wp-content/blogs.dir/253/files/2018/06/GoT-paradox.png)

And we can also compute the averages, just to check:

So, indeed, people on average have fewer friends than their friends.
