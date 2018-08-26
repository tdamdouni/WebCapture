# Identifying Senior Developers

_Captured: 2018-06-20 at 19:39 from [dzone.com](https://dzone.com/articles/identifying-senior-developers?edition=383232&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-20)_

Discover how you can [take agile development to the next level](https://dzone.com/go?i=294434&u=https%3A%2F%2Fwww.mendix.com%2Fresources%2Ftaking-agile-development-to-the-next-level-with-low-code-mx%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone) with low-code.

Recently I came across the question of "How can we identify senior developers within our interview process?"

This was a very interesting question that required further thought and investigation.

## Initial Thoughts

My initial thoughts were:

  * Try the algorithms and data structures approach as described in _[Cracking the Coding Interview_](https://www.amazon.com/Cracking-Coding-Interview-Programming-Questions/dp/098478280X) book. However, as the book itself states, it's not for everyone or every company or every situation. I personally am not a fan of this approach as I prefer to commit ideas to memory rather than their implementations.
  * Try the take-home coding challenge. I think this is a fair approach because: 
    * It delineates the demands of a developer (using their problem-solving skills to create business solutions).
    * It's challenging translating ideas in your head into quality code.
    * Provides time for a candidate to express their skillset.

## Personal Experience

I also reflected on my own experience some years back when I joined a team tasked with building a greenfield project. At that point, I had been a software developer for quite a few years and therefore considered myself to be a senior developer.

However, when I joined the team I discovered that there was a considerable gap between myself and most of the other developers. Effectively, I wasn't a senior developer but a step below - an average developer.

This lead me to conclude that seniority is not an absolute truth based on time served but rather relative to your surroundings.

Am I suggesting that a senior developer who joins a team that has stronger competencies or experience suddenly drops to the level of an average developer?

No, not at all, because there are certain traits that senior developers exhibit regardless of whether they have the same experience or competencies of their fellow team members.

#### What constitutes an average developer

One description would be a developer who solves a problem by getting it to work (regardless of whether they understand it or not) and then moves on to the next task.

#### What constitutes a senior developer

One description would be a developer who

  * Solves a problem by getting it to work and makes sure they understand how it works
  * Refactors the code until it is to a high standard
  * Adds a sufficient amount of quality assurance (this would be in the form of tests)
  * Adds a sufficient amount of documentation so that others in future will know why the system is the way it is.
  * Ensures that code reviews are carried out to: 
    * Share their reasoning about what problem they are solving and how they solved it
    * Encourage constructive feedback to capture mistakes and/or improvements
  * Tries to continually improve so that their knowledge is up-to-date and relevant to the team's needs.

## The Technical Interview

This can take one of two forms:

  * Provide a take-home coding challenge which is then reviewed as part of the technical interview
  * In the absence of a take-home coding challenge, one can try to assess the candidate's technical abilities by putting forward a business problem and asking them how they would solve it (they can, of course, use the whiteboard freely to visualize their answers). This approach is detailed below.

## Business Problem

Build a web application that allows a customer to log in, view, and edit their details.

### Questions

  * **How would you go about architecting the application?**
    * _Hints / Further questions to facilitate the topic:_
      * How would you prevent undesirable situations like circular dependencies?
      * How would you try to maintain the integrity of the architecture, so that others coming after you do not unintentionally violate it?
  * **Which language and framework would you choose to build the application?**
    * _Hints / Further questions to facilitate the topic:  
_
      * For the UI?
      * For the backend?
  * **How would you document the application so that others coming after you can understand why the system is the way it is?**
    * _Hints / Further questions to facilitate the topic:  
_
      * How much documentation is needed?
      * Where should the documentation reside?
  * **How would you try to ensure that the code is written to a high standard?**
    * _Hints / Further questions to facilitate the topic:  
_
      * Would any programming principles help?
      * Would you use any static analysis tools? 
        * How would you execute it so that you would get regular feedback?
      * What about code reviews? 
        * In what format would they produce the best results?
  * **As this is a public facing application what security concerns would you have? And how would you address them?**
    * _Hints / Further questions to facilitate the topic:  
_
      * OWASP top ten?
      * How would you address: 
        * SQL Injection?
        * CSRF attacks?
        * XSS attacks?
        * Direct object references?
        * Any others?
      * What about DDOS? 
        * Would rate limiting help? If so what are its advantages and disadvantages?
  * **If session state is needed, how would you manage it if there are multiple instances of the application?**
    * _Hints / Further questions to facilitate the topic:  
_
      * Would you store the session in a database, on the server or on the client? 
        * What are some of the benefits and disadvantages of each approach?
  * **How would you go about testing the application?**
    * _Hints / Further questions to facilitate the topic:_
      * What benefits does testing provide?
      * What different types of tests would you write (e.g. unit tests, integration tests, acceptance tests, performance tests, penetration tests etc…)? 
        * Are there any specific libraries that you would use?
        * What benefits do each of these types of tests provide?
  * **How would you automate the build, test, and deployment of the application?**
    * _Hints / Further questions to facilitate the topic:  
_
      * Would you use any CI/CD tools? 
        * How would a build pipeline potentially look?
      * Any other automation tools that could help with reducing manual effort?
  * **How would you monitor and visualize the application?**
    * _Hints / Further questions to facilitate the topic:  
_
      * Would the Elastic stack (Elasticsearch/Logstash/Kibana) be of value?
      * Would you use Grafana? 
        * What sort of metrics would be of value?
  * **In what ways do you try to improve your skillset and technical competency?**
    * _Hints / Further questions to facilitate the topic:  
_
      * What conferences do you attend? 
        * How have they helped you improve?
      * What resources do you use (e.g. books, blogs, videos)? 
        * Can you name a few and how they have helped you improve?

[Download this eBook ](https://dzone.com/go?i=294435&u=https%3A%2F%2Fwww.mendix.com%2Fresources%2Ftaking-agile-development-to-the-next-level-with-low-code-mx%2F%3Futm_medium%3Ddisplay%26utm_source%3Ddzone)to learn how to prepare your business for agile adoption, how to ensure the proper business-IT collaboration that is critical for agile development, and how to choose the right stakeholders to increase productivity and enable accelerated time-to-value.

Opinions expressed by DZone contributors are their own.
