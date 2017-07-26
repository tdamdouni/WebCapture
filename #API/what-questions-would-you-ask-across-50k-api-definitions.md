# What Questions Would You Ask Across 50,000 API Definitions?

_Captured: 2017-04-21 at 00:00 from [dzone.com](https://dzone.com/articles/what-questions-would-you-ask-across-50000-api-defi?edition=292902&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-20)_

Mike Ralphson ([@PermittedSoc](https://twitter.com/PermittedSoc)) asked me the other day, _[If you could run SQL/GraphQL queries over nearly 50K API definitions, what would you ask?_](https://twitter.com/PermittedSoc/status/847814927792451586) I told him I would respond via blog post, which is one way I help amplify the conversation I have with other API folks in the space. Mike is doing some important work when it comes to API discovery, something that needs amplification if we are going to move this conversation forward.

OK, so what would I ask about nearly 50K API definitions if I had the opportunity to ask? Here are some of my thoughts:

  * **What are all the paths used? **I'd like to see a list of all path folders, separated by the forward slash, minus any parameters.
  * **What paths folders actually are words?** I'd like to know how coherent API design patterns are and how many are actually words in a dictionary. 
  * **What are all the tags applied? **A listing of all tags applied to APIs with counts for each time it is used.
  * **What are all the parameters?** A listing of all the parameters applied to APIs with counts for each used.
  * **What are all the definitions?** A listing of all definitions used as part of API requests and responses with counts next to each.
  * **How many don't have definitions?** What percentage of the API definitions do not have definitions describing their responses?
  * **What businesses are involved? **A listing of all companies involved with API definitions from contact information to domain ownership.
  * **What is "whois" information for each domain? **Pull "whois" information for all the domains involved in API definitions.
  * **Which definitions do not have path summary or description? **Which definitions have omitted the description of the path?
  * **What's the average length of path summary and descriptions? **Of the definitions with a description or summary, what is the average length?
  * **How many APIs provide a link to terms of service? **Checking to see if a term of service is part of the definition.
  * **How many APIs provide contact information for an API? **Checking to see if contact information is part of the definition.
  * **How many APIs describe their headers? **Looking for specific headers described as part of each path definition.
  * **How many APIs use the body as part of their request? **Looking for heavy body use as part of the request surface area of an API.
  * **How many APIs have a security definition? **Which of the APIs has provided a definition for how an API is secured?
  * **How many APIs do not use response codes? **Which of the APIs do not provide response codes for their API responses?
  * **Which API response HTTP status codes used? **Provide a list of API response HTTP status codes used, with counts for each.

This is a starting list of what I'd like to ask of 50K API definitions. It is something I'd have to think and write about more to be able to come up with more creative questions. I recommend publishing them all to a Github repository and let people start asking questions via an interface. You might not be able to answer all of the questions, but it would be interesting to see what people want to know--I am sure you could develop a pretty interesting look at how folks see API discovery, and what they are looking for.

API discovery is one of the areas of the API lifecycle that is pretty deficient due to how people view their APIs and how they often have their blinders on regarding the wider API community. Most folks are thinking about their APIs and maybe a handful of other APIs they are familiar with but do not consider API usage across industries, or the entire space. We need more work like this to occur. We need more API definitions to be made available, as well as more dynamic ways for folks to discover, understand, and learn about APIs that already exist.
