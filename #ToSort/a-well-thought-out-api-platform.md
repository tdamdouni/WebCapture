# A Well Thought-Out API Platform

_Captured: 2017-02-23 at 19:53 from [dzone.com](https://dzone.com/articles/a-well-thought-out-api-platform?edition=272883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-23)_

I was playing with one of the [API deployment solutions](http://deployment.apievangelist.com) that I track on, appropriately called [API Platform](https://api-platform.com/). It is an open-source PHP solution for defining, designing, and deploying your linked data APIs. I thought their list of features provided a pretty sophisticated look at what an API can be, and was something I wanted to share.

![](http://kinlane-productions.s3.amazonaws.com/api_evangelist_site/blog/api_platform_upside_down.png)

This is what it says:

  * Create a [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) API in minutes.
  * Automatic [Swagger](http://swagger.io/) documentation.
  * Built with [Symfony](https://symfony.com/) and [Doctrine](http://www.doctrine-project.org/).
  * [Docker](https://www.docker.com/) integration.
  * Data validation and error management.
  * Pagination, filtering and sorting.
  * Generate the data model using [Schema.org](https://schema.org/).
  * [FOSUser](http://symfony.com/doc/current/bundles/FOSUserBundle/index.html), [JWT](https://jwt.io/), CORS, and [OAuth](https://oauth.net/) support.
  * Implements [OWASP's recos](https://www.owasp.org/index.php/REST_Security_Cheat_Sheet).
  * Modular.
  * Designed for speed and caching.
  * [Behat](http://behat.org/), [PHPUnit](http://phpunit.de/), and [Postman](https://www.getpostman.com/) spec and testing.
  * 100% open source (MIT).

There are a couple of key elements here: API definition-driven with JSON-LD, Hydra, HAL, and OpenAPI Spec out-of-the-box. Containerized. Schema.org FTW! JWT, and OAuth. OWASP's security checklist. Postman ready! These features make for a pretty compelling approach to [designing](http://design.apievangelist.com) and [deploying](http://deployment.apievangelist.com) your APIs. While I see some of these features on other platforms, it is the first with an open-source solution possessing such an impressive resume.

I'm going to take this list and add to my list of API design and deployment building blocks in my research. These are features that other API deployment solutions should be considering as part of their offering. This approach to API deployment may not be the right answer for every type of API, but I know many data- and content-focused APIs that would benefit significantly from a deployment solution like [API Platform](https://api-platform.com/).
