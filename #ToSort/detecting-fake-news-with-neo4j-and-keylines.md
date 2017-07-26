# Detecting Fake News With Neo4j and KeyLines

_Captured: 2017-05-21 at 12:41 from [dzone.com](https://dzone.com/articles/detecting-fake-news-with-neo4j-amp-keylines?edition=299092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-20)_

Whether you work in SQL Server Management Studio or Visual Studio, Redgate tools integrate with your existing infrastructure, [enabling you to align DevOps for your applications with DevOps for your SQL Server databases.](https://dzone.com/go?i=188128&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25667) Discover true Database DevOps, brought to you in partnership with [Redgate](https://dzone.com/go?i=188128&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25667).

Fake news is one of the more troubling trends of 2017. The term is liberally applied to discredit everything, from stories with perceived bias through to alternative facts and downright lies. It has a warping effect on public opinion and spreads misinformation.

[Fake news](https://dzone.com/articles/how-can-artificial-intelligence-combat-fake-news) is nothing new -- bad journalism and propaganda have always existed -- but what _is_ new is its ability to spread through social media.

In this post, we'll see how graph analysis and visualization techniques can help social networking sites stop the spread of fake news. We'll see how, [like fraud](https://cambridge-intelligence.com/keylines/fraud/), fake news detection is about understanding networks. We'll discuss how Neo4j and the [KeyLines graph visualization toolkit](https://cambridge-intelligence.com/keylines/) can power a comprehensive fake news detection process.

A quick note: For simplicity, in this post, we'll limit the term "fake news" to describe completely fictitious and unsubstantiated articles (see examples like [PizzaGate](http://www.snopes.com/pizzagate-conspiracy/) and the [Ohio lost votes](http://www.snopes.com/clinton-votes-found-in-warehouse/) story).

## How Is Fake News a Graph Problem?

To detect fake news, it's essential to understand how it spreads online between accounts, posts, pages, timestamps, IP addresses, websites, etc. Once we model these connections as a graph, we can differentiate between normal behaviors and abnormal activity where fake content could be shared.

Let's get started.

## Building Our Graph Data Model

When we're detecting fraud, we usually rely on verifiable, watch-list friendly, demographic data like real names, addresses, or credit card details. With fake news, we don't have this luxury, but we _do_ have data on social networking sites. This can give us useful information, including:

  * Accounts (or pages).
  * Age, history, connections to other accounts, pages, and groups.
  * Posts.
  * Device fingerprint/IP address, timestamp, number of shares, comments, reactions, and "reported" flags.
  * Articles.
  * Host URL, WHOIS data, title, content, and author,

There are many ways to [model this data as a graph](https://cambridge-intelligence.com/graph-data-modeling-101/). We usually start by mapping the main items to nodes: account, post, and article. We know that IP addresses are important, so we can add those as nodes, too. Everything else is added as a property:

![Graph model for fake news detection](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508063800/fake-news-detection-graph-model-1024x462.jpg)

> _Our fake news detection graph model._

### Detection vs. Investigation

Fake news spreaders are just as determined as regular fraudsters. They'll adapt their behavior to avoid detection and employ bots to run brute-force attacks.

Relying on algorithmic or manual detection isn't enough. We need a hybrid approach that combines automated detection and manual investigation:

![The process model for fake news detection between Neo4j and KeyLines](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508064031/KeyLines-Neo4j-process-model.png)

> _A simplified model showing fake news detection powered by Neo4j and KeyLines._

  * **Automated detection**: This uses a [Neo4j](https://neo4j.com/product/?ref=blog) graph database as the engine for an automated, rule-based detection process. It isolates posts and accounts that match patterns of behavior previously associated with fake news (known fraud).
  * **Manual investigation**: At the same time, a manual investigation process, powered by a KeyLines graph visualization tool, helps uncover new behaviors (unknown fraud).

New behaviors are fed back into the automated process, so automated detection rules can adapt and become more sophisticated.

## Detecting Fake News With Neo4j

Once we've created our data store, we can run complex queries to detect high-risk content and accounts.

Here's where [graph databases](https://neo4j.com/blog/why-graph-databases-are-the-future/?ref=blog/#definition) like Neo4j offer huge advantages over traditional SQL or relational databases. Queries that could take hours now take seconds and can be expressed using intuitive and clean [Cypher](https://neo4j.com/blog/why-database-query-language-matters/?ref=blog/#cypher) queries.

For example, we know that fake news botnets tend to share content in short bursts, using recently registered accounts with few connections. We can run a Cypher query that:

  * Returns all accounts... 
    * ...that have fewer than 20 friend connections.
    * ...that shared a link to _www.example.com_.
    * ...between 12:07 p.m. -- 12:37 p.m. on February 13, 2017.

In Cypher, we'd simply express this as:
    
    
    MATCH (account:Account)--(ip:IP)--(post:Post)--(article:Article)
    
    
          WHERE account.friends < 20 AND article.url = 'www.example.com'

## Investigating Fake News With Keylines

To seek out unknown fraud (cases that follow patterns that can't be fully defined yet), our manual investigation process looks for anomalous connections.

![Image title](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508062815/keylines-fake-news-detection-neo4j.png)

_Visual investigation tools provide an intuitive way to uncover unusual connections that could indicate fake content._

A graph data visualization tool like KeyLines is essential for this.

## Building a Visual Graph Model

Let's define a visual graph model so we can start to load data from Neo4j into KeyLines.

It's not a great idea to load every node and link in our source data. Instead, we should focus on the minimal viable elements that tell the story and then add other properties as tooltips or nodes later.

We want to see our four key node types with glyphs to highlight higher-risk data points like:

  * New accounts.
  * Posts that have been reported by users.
  * URLs that have previously been associated with fake content.

This gives us a visual model that looks like this:

![Image title](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508064242/visual-data-model-high-risk-data-point-glyphs-768x125.png)

_Loading the data._

To find anomalies, we need to define normal behavior. Graph visualization is the simplest way to do this.

Here's what happens when we load 100 Post IDs into KeyLines:

![Image title](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508064437/data-loading-post-ids-facebook-keylines-768x345.png)

> _Loading the metadata of 100 Facebook posts into KeyLines to identify anomalous patterns._

Our synthesized dataset is simplified, with a lower rate of sharing activity and more anomalies than real-world data. But even in this example, we can see both normal and unusual behavior:

![Image title](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508064612/normal-social-media-user-behavior-768x413.png)

> _Normal user sharing behavior visualized as a graph._

Normal posts look similar to our data model -- featuring an account, IP, post, and article. Popular posts may be attached to many accounts, each with their own IP, but generally, this linear graph with no red glyphs indicates a low-risk post.

Other structures in the graph stand out as unusual. Let's take a look at some examples.

## Monitoring New Users

New users should always be treated as higher risk than established users. Without a known history, it's difficult to understand a user's intentions. Using the New User glyph, we can easily pick them out:

![Image title](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508064746/non-suspicious-user-behavior-post.png)

> _A non-suspicious post being shared by a new user._

![Image title](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508064906/unusual-user-sharing-behavior-fake-news-768x550.png)

_This is structure is much more suspicious, with a new user sharing flagged posts to articles on known fake news domains._

## Identifying Unusual Sharing Behavior

We can also use a graph view to uncover suspicious user behavior. Here's one strange structure:

![Image title](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508065026/deviant-pattern-user-sharing-behavior-fake-news.png)

> _An anomalous structure for investigation._

We can see one article has been shared multiple times, seemingly by three accounts with the same IP address. By expanding both the IP and article nodes, we can get a full view of the accounts associated with the link farm.

## Finding New Fake News Domains

In addition to monitoring users, social networks should monitor links to domains known for sharing fake news. We've represented this in our visual model using red glyphs on the domain node. We've also used the combine feature to merge articles on the same domain:

![Image title](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508065300/combining-domain-tracking-graph-visualization.gif)

> _Using combos to see patterns in article domains._

This view shows the websites being shared, rather than just the individual articles. We can pick out suspicious domains:

![Image title](https://s3.amazonaws.com/dev.assets.neo4j.com/wp-content/uploads/20170508065411/suspicious-fake-news-web-domain-pattern-768x374.png)

> _Try It for Yourself_

This post is just an illustration of how you can use graph visualization techniques to understand the complex connected data associated with social media. We've used simplified data and examples to show how graph analysis could become part of the crackdown on fake news.

It's easier than you think to [extend DevOps practices to SQL Server with Redgate tools](https://dzone.com/go?i=188129&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25673). Discover how to introduce true Database DevOps, brought to you in partnership with [Redgate](https://dzone.com/go?i=188129&u=http%3A%2F%2Fwww.red-gate.com%2Fsolutions%2Fdatabase-devops%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplayad%26utm_content%3Ddbdevops_keep%26utm_campaign%3Dsqltoolbelt%26utm_term%3Dtextad-25673).
