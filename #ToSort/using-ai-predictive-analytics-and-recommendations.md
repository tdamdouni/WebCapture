# Using AI, Predictive Analytics, and Recommendations

_Captured: 2017-04-20 at 23:57 from [dzone.com](https://dzone.com/articles/powered-by-ai-how-to-use-recommendation-system-in?edition=292902&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-20)_

### Predictive analytics and recommendation algorithms in AI are finding their way to retail. Read an example of how they were recently implemented at a grocery chain.

Need to build an application around your data? [Learn more](https://dzone.com/go?i=200129&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) about dataflow programming for rapid development and greater creativity.

This is an overview of what a recommendation system in retail is and how we implemented it at a grocery chain.

These days, recommendation systems empower social networks, healthcare, finance, and e-commerce. At the end of 2016, Starbucks [announced](http://www.businessinsider.com/starbucks-develops-personalization-system-2016-12) that they will be implementing an AI-based recommendation system in their cafes all over the world. This means that [predictive analytics](http://www.predictiveanalyticstoday.com/what-is-predictive-analytics/) has finally found its way into retail.

## What Does It Mean?

Like e-commerce entrepreneurs, retailers can now send customers personalized offers based on their behavior. In other words, when you purchase your morning coffee, you'll be automatically offered a fresh muffin. When you buy steaks for grilling, you will get a reminder offering mustard, ketchup, or whatever else you'll need for a barbecue.

## Both Retailers and Customers Love Recommendations

Let's look at an average grocery shop customer who needs all items from his or her dinner list ticked off. At the end of the day, the customer realizes that the list is missing, and it seems impossible to recall all the items. Thanks to a supermarket app, the customer can make a list from a food catalog. Right after adding pasta to the list, the app recommends them to buy a Bolognese sauce. The customer grabs the sauce and wonders how they ever forgot about it. The recommendation works because someone in the past purchased Bolognese sauce right alongside pasta.

Here's what retailers can get from using recommendation systems:

  * Increased customer loyalty by sending offers based on specific customer needs.

  * Increased revenue.

  * An understanding of what customers really need.

  * A demand for new products by adding them to suggestions.

Grocery stores cannot analyze customer responses to the offered good in real time. However, the majority of retail chains have loyalty programs and a database of receipts. This data can be enough to make specific recommendations for customers.

There are several implementation solutions for a grocery store. It depends whether the grocery has an app and a website.

![Image title](https://dzone.com/storage/temp/4990151-operation-principle-of-the-recommendation-system.png)

## How We Made It

There are three main approaches to a recommendation system development: a content-based approach, collaborative filtering, and a hybrid approach.

When we developed a recommendation system for a big Russian grocery chain, we used collaborative filtering.

The system parses similarity of profiles: customer similarity, goods similarity, and other content. Therefore, the system recommends items similar to the goods a specific customer and shoppers with the same profiles purchased.

In our project, we used several models within the collaborative filtering approach.

### Association Rules

![Image title](https://dzone.com/storage/temp/4990223-bigram-rules-the-model-in-our-project.png)

> _Where 0, 1, 2, 3 mean a transaction for specific goods. For example, 0--bread, 1--spring onions._

_k_-nearest neighbor method (kNN) allows us to find _k_-nearest customers with similar market baskets and create personal recommendations for them. It's based on the hypothesis that similar customers purchase similar goods. The idea is simple: we define a market basket for every customer and calculate the distance between the specific customer and others having similar items in the market basket. Then, we recommend customers buy the goods purchased earlier by those customers with similar market baskets.

![Image title](https://dzone.com/storage/temp/4990233-k-nearest-neighbor-method.png)

_Where k--number of nearest neighbors, Xj--randomly selected customer, and AB--distance in the metric system that defines similarity between objects._

Factorization Machines find unclear similarities in customer profiles. Every customer and every item are described by a specific feature set. If a customer feature set coincides with an item feature set, then this customer gets a recommendation for this specific item. The feature set is usually not obvious.

For example, an item A has a description of "spicy, small pack, foreign, sweet, expensive." The customer feature set coincides with the feature set of item A. So, this customer receives the corresponding recommendation.

The algorithm processes additional data like item type, seasonal index, time of purchase, price, etc.

![Image title](https://dzone.com/storage/temp/4998999-factorization-machines.png)

We developed a recommendation system targeted at increasing the average number of items bought. As a result, revenue per customer increased.

A personalized approach to customers is the future. Recommendation systems are the key factor here. Retailers will appreciate recommendation systems when they see the obvious benefits: raised loyalty, a better understanding of customer needs, and thus increased profits.

What about you guys? Have you ever developed recommendation systems? I'd be happy to read about your experience!

[Check out](https://dzone.com/go?i=200130&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) the Exaptive data application Studio. Technology agnostic. No glue code. Use what you know and rely on the community for what you don't. [Try the community version](https://dzone.com/go?i=200130&u=https%3A%2F%2Fexaptive.city%2F%23%2Flanding%3Freferrer%3DGeneral).
