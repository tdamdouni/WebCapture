# Who Uses Your Open Source Code Anyway?

_Captured: 2018-08-16 at 06:55 from [dzone.com](https://dzone.com/articles/who-uses-your-open-source-code-anyway?edition=385377&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-08-15)_

DON'T STRESS! Assess your OSS. [Get your free code scanner from Flexera](https://dzone.com/go?i=294429&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-oszone-banner%26utm_campaign%3Ddzone-fnca-oszone-banner-June2018%26id%3Ddzone-fnca-oszone-banner-June2018). [FlexNet Code Aware](https://dzone.com/go?i=294429&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-oszone-banner%26utm_campaign%3Ddzone-fnca-oszone-banner-June2018%26id%3Ddzone-fnca-oszone-banner-June2018) **scans Java, NuGet, and NPM packages**.

I'm not exaggerating when I say there is a whole world of open-source code out there. This is for good reason, considering open-source code covers most of the functionality currently available to computers. From the tried-and-true libraries you take with you everywhere, to the experimental ones that warn you, "This is experimental stuff! Do not use in production."

Open-source code is so plentiful that most of it is composed of other open-source code, which in turn is itself composed of even more open-source code. It's open-source code all the way down.

In fact, there is so much open-source code out there that you may have even created a few open-source libraries yourself. They may even be so kick-ass that you are completely aware of people and companies that are actually using them in production. Kudos to you, seriously.

However, if you're not aware of (or would like to be more aware of) the usage of your source code, then get ready to be excited about [GitDetective.io](https://gitdetective.io).

![](https://cdn-images-1.medium.com/max/2000/1*cQVX85qWTvpQk8gairihFA.png)

## What Does It Do?

GitDetective is an open-source web application for viewing the use and users of open-source code. GitDetective allows you to observe how other people use the source code you release down to the exact line of usage. This is achieved by extracting and cataloging source code references during compilation. GitDetective's ultimate goal is to surface the underlying trends discovered within these source code references.

Source code references meaning **function A **refers to/invokes **function B **(with support for cross-language references). Trends refers to the ebb and flow of references discovered in open-source code.

Essentially, **function A **is used to refer to **function B **but has since been modified and now points to **function C**. Ideally this previous reference shouldn't be removed as the fact that it used to exist can be of value but the new relationship needs to be accounted for moving forward.

**Note:** While tracking trends is the ultimate goal of GitDetective, the current version as of writing this (v1.3) can only accumulate references. This is not the end objective but does help illustrate the idea behind GitDetective. As of now, GitDetective holds external references for over 10,000 projects on GitHub. This accounts for over 3 million references between approximately 5 million indexed methods. The projects indexed were chosen based on pull request data from [GH Archive](https://www.gharchive.org/) in the months of June and July (2018).

## But Why?

Put bluntly, GitHub stars aren't enough. I'm positive there are many projects I commonly use that I still haven't gotten around to starring. I have no doubt there are also projects I've starred that I've never taken another look at. GitHub stars have very little indication of what a developer's actual relationship is with a project. It merely shows that a developer is aware of and may have an interest in the project. The developer's version of a head nod.

![](https://cdn-images-1.medium.com/max/1200/1*piI6tok7p0hEn1EUKpKlUg.gif)

GitDetective believes as a developer of open-source code you should be able to gather a more tangible sense of how your source code is used. Understanding how your source code is used by others can lead to more informed decision making when designing and improving your source code.

#### GitDetective aims to answer more in-depth questions such as:

  * What are the most popular functions in my code?
  * How many people total use my code?
  * Did more people use my code this month as opposed to last month?
  * What's the daily/monthly/yearly growth in usage of my code?
  * When was the first and last time someone used my code?
  * At which line in someone else's code was my code used?
  * Who are the heaviest users of my code?
  * Who are the newest users of my code?
  * What are common conventions/variable names/etc. used with my code?

While stars may indicate the possibility of a relationship between a developer and a project, they cannot provide clear answers to the questions above. GitDetective bridges this gap by providing concrete observations of when and where your code is actually used. How does GitDetective achieve this you ask? By using open-source code, of course! Most notably [Kythe](https://kythe.io/) and [Grakn](https://grakn.ai/).

## Plugging in Kythe

**Kythe describes itself as:**

> A pluggable, (mostly) language-agnostic ecosystem for building tools that work with code 

Meaning to say that Kythe is software created to understand the source code of other software. It defines a universal schema over source code (which covers multiple languages) and provides indexers capable of extracting facts which fit this schema. For example, in most languages (if not all) there are concepts such as [childof](https://kythe.io/docs/schema/#childof), which describes some entity being contained or dominated by another; or such as [refcall](https://kythe.io/docs/schema/#refcall), which describe calls to functions.

In addition to formalizing entities and relationships for all the aspects of source code, Kythe also provides a unique identifier for everything. This includes non-addressable source code like default constructors, anonymous functions, implicit arguments, AST constructs, and local variables. This unique identifier is how GitDetective is able to determine when functions are being referenced regardless of which project it's coming from.

This unique identifier takes the form of a custom URI similar to:

![](https://cdn-images-1.medium.com/max/2000/1*pssgULLJY0HyzgBm-h1Jlw.png)

If it's not already obvious, Kythe produces a [plethora of information](http://kythe.io/docs/schema/). This is done purposely so that Kythe can provide useful information for any desirable understanding of source code. There is no reason why everything it outputs needs to be considered, however. The important part is just making Kythe-compatible tools. The ambition of Kythe is that any tools you build with it are then suitable to work with any source code language.

Given that GitDetective is only interested in the references between projects, it only needs to evaluate those relationships necessary to determine which files define which functions and which defined functions call which undefined functions. Calls between defined functions are considered internal while calls between defined functions to undefined functions are considered external. All the internal calls are suppressed as this is easily available in most IDEs. GitDetective's purpose is the references the IDE doesn't show. These are the references to source code not created in that project.

GitDetective makes use of only the following Kythe entities and relationships:

![](https://cdn-images-1.medium.com/max/1600/1*BUmS6RgCz457H6oMvx9hUg.png)

This minimal structure is enough to hold all the different variations of external references between source code. Files can define functions and both files and functions can invoke other functions of which you didn't write the source code for. This structure is extracted by the indexer module in GitDetective which are scaled horizontally for cloning and compiling projects concurrently. After a project has been indexed the reference calls contained within the source code are then added to the knowledge graph in Grakn.

## Releasing the Grakn

**Grakn describes itself as:**

> The knowledge graph engine to organise complex networks of data and making it queryable, by performing knowledge engineering 

True to its word, Grakn is the one-stop-shop for creating powerful knowledge graphs through knowledge engineering (the process of storing knowledge). Grakn provides the knowledge graph as well as the apparatus for querying data via their expressive and inference-capable query language, called Graql. Graql allows you to define the schema of your knowledge graph just as it exists in the real world by allowing you to describe the domain.

In GitDetective's domain there are the following concepts:

  * `project`
  * `file`
  * `function-instance`
  * `function-definitions`
  * `function`
  * `function-references`

GitDetective stores these entities in two scopes, a global scope and a local scope. Entities stored with a global scope are unique and appear once in the knowledge graph. They represent entities which are the outer most edges of the graph and serve as entry points. When storing data in a graph it is necessary to connect related data. However, with domains in which data is highly interconnected, this presents a problem in traversal as everything is connected to everything else. In order to efficiently traverse large and highly connected graphs, you must have entry points near your desired entities.

Entities with a global scope in GitDetective include:

> `_project_`, `_file_`, `_function-definitions_`, `_function_`, `_function-references_`

The local scope represents entities which are particular to a specific point in time or source code location in a project. The only entity with a local scope is `function-instance` , but they account for the vast majority of the data stored. They are not meant to be searched upon but rather followed when you know precisely the version of the function you wish to explore the usage of.

In essence, projects are global entities which define global files. Files define local function-instances. A function-instance represents a project's local representation of a global function. This is necessary in order to store the file offsets of source code references so they can be traced back to the source line and commit. Finally, each local function-instance is linked to a global function via either function-definitions (a definition of the global function) or function-references (a reference to the global function).

Visually, the schema as described looks like:

![](https://cdn-images-1.medium.com/max/2000/1*qccH66oIVYeKA1JOkVBVAg.png)

The beauty of Grakn and Graql is most evident in how easily the above (and any other describable domain) can be represented with their technology. Graql is such an expressive language that if you can describe it to another human, you can model it in Graql. For a taste of how easily you can model a particular domain in Graql, I've included a sample from GitDetective. It shows all the core entities used in GitDetective. Even without ever seeing Graql before, I'm confident a considerable amount will still make sense.

**Note:** Only `sub`, `entity`, `has`, and `plays` are Graql keywords. The remaining are concepts extracted from GitDetective's specific domain.

The first line defines a `project` which subtypes`entity` (the root object; like Java's Object). It then declares `project`has attributes such as `project_name` and plays the role of `has_defines_file`. An opposing role of `is_defines_file` exists which is played by `file`. Using this relationship projects can be tracked to their files as well as files tracked back to their project. A similar relationship between `file` and `function-instance` also exists via `has_defines_function` and `is_defines_function`.

Each `function-instance` is connected to either a `function-definitions` or to a `function-references`. This is determined by whether or not a particular `function-instance` is defining a `function` or referencing one.

The [full schema](https://github.com/CodeBrig/GitDetective/blob/master/web/src/main/resources/gitdetective-schema.gql) is about twice as long as the sample above but remains just as approachable. It describes the entities, attributes, and relationships that GitDetective uses to store source code references.

Once a schema has been defined data can be imported and later queried using Graql. You will find that Graql can be used to extract information just as naturally as it's used to define the graph's schema. This is partly due to all the concepts in Graql supporting inheritance. Using inheritance in Graql queries allows you to be as specific or as broad in a query as desired.

For example, in the schema above there are two relationships related to defining an entity ( `defines_file` and `defines_function`). Both of these relationships inherit from `defines` which can also be used in queries. Using the fact that `defines_file` and `defines_function` both inherit `defines` I can simplify queries in which the distinction between the two isn't necessary while preserving the ability to distinguish between them when it is.

Exploiting inheritance (and some shorthand notations), references between disparate projects can be linked with the following pocket-sized query:

The above returns all the references to functions which are in the source code of [bfergerson/myproject](https://github.com/bfergerson/myproject). Given that this is an example project, one would expect there not to be any other projects which reference it. Luckily, I'll still make use of my code even if no one else will. This example project was packaged into a .jar and used in the separate project [bfergerson/otherproject](https://github.com/bfergerson/otherproject). Besides this .jar file there is no direct connection between the two projects to determine that one project references the other. Not even a shared stargazer. Nonetheless, GitDetective detects those connections and displays them [here](https://gitdetective.io/bfergerson/myproject).

## What's Next?

The next immediate milestone for GitDetective is to track the trends of references instead of just accumulating them. GitDetective will then be able to follow the progress of how source code references change over time rather than showing a view over all time.

I also plan on releasing more software that combines Grakn and Kythe. Kythe converts source code of many flavors to something describable. Grakn provides the apparatus to make the describable, queryable. Together they provide a powerful solution for creating artificially intelligent source code tools. This is why I am working on GitDetective's sister project: GitSocratic.

GitSocratic is a console-based application which takes a more personal and in-depth view of your source code. GitSocratic allows local querying of source code and makes use of the full arsenal of Kythe with added AST structures as well as additional edges generated by control and data dependence analysis.

Finally, don't forget to star [GitDetective](https://github.com/CodeBrig/GitDetective) on GitHub. This is crucial so I know how extensively you use GitDetective in all of your production applications.

[Try FlexNet Code Aware Today](https://dzone.com/go?i=294430&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-oszone-banner%26utm_campaign%3Ddzone-fnca-oszone-banner-June2018%26id%3Ddzone-fnca-oszone-banner-June2018)! A [free scan tool](https://dzone.com/go?i=294430&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-oszone-banner%26utm_campaign%3Ddzone-fnca-oszone-banner-June2018%26id%3Ddzone-fnca-oszone-banner-June2018) for developers. Scan Java, NuGet, and NPM packages for open source security and license compliance issues.
