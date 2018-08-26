![DZone](/themes/dz20/images/logo2.png)

/ [DevOps Zone](/devops-tutorials-tools-news)

Over a million developers have joined DZone.

Log In / Sign Up

__

![](/themes/dz20/images/DZone_MobileLogin2.png)

  *   * {{node.title}}

{{node.type}} * {{ node.urlSource.name }} * by [{{node.authors[0].realName }}]({{ node.authors\[0\].url }})

__[ Download]({{node.pdf}}) __ {{node.downloads}}

{{totalResults}} search results

  *   * _[Refcardz_](/refcardz)
  * _[Guides_](/guides)
  * _[Zones_](/portals)
  * _[Jobs_](https://jobs.dzone.com?ref=nav)
  * |
  * [ Agile](/agile-methodology-training-tools-news)
  * [ AI](/artificial-intelligence-tutorials-tools-news)
  * [ Big Data](/big-data-analytics-tutorials-tools-news)
  * [ Cloud](/cloud-computing-tutorials-tools-news)
  * [ Database](/database-sql-nosql-tutorials-tools-news)
  * [ DevOps](/devops-tutorials-tools-news)
  * [ Integration](/enterprise-integration-training-tools-news)
  * [ IoT](/iot-developer-tutorials-tools-news-reviews)
  * [ Java](/java-jdk-development-tutorials-tools-news)
  * [ Microservices](/microservices-news-tutorials-tools)
  * [ Open Source](/open-source-news-tutorials-tools)
  * [ Performance](/apm-tools-performance-monitoring-optimization)
  * [ Security](/application-web-network-security)
  * [ Web Dev](/web-development-programming-tutorials-tools-news)

{{announcement.body}}

{{announcement.title}}

Let's be friends:

  * __
  * __
  * __
  * __
  * __

[ ![](//dz2cdn3.dzone.com/storage/partner-logo/7740958-ca-atlantic-lockup-black-01.png) ](http://www.automic.com)

#  Why JSON Isn't a Good Configuration Language 

DZone's Guide to 

#  Why JSON Isn't a Good Configuration Language 

###  Many projects use JSON for configuration, but is that a mistake? See what you should be using for configuration when creating your application, framework, or library. 

[ ![](https://secure.gravatar.com/avatar/78e2a9fed0b202a590a912246647f520?d=identicon&r=PG) ](/users/2835874/thayne.html) by 

[ Thayne McCombs](/users/2835874/thayne.html)

__

*

Jul. 17, 18 * [DevOps Zone](/devops-tutorials-tools-news) *

Free Resource 

__ Like (8)

__ Comment (8) 

__

Save

__ Tweet

__ {{ articles[0].views | formatCount}} Views

__

  * Edit
  * Delete
  * {{ articles[0].isLocked ? 'Enable' : 'Disable' }} comments
  * {{ articles[0].isLimited ? 'Remove comment limits' : 'Enable moderated comments' }} 

Join the DZone community and get the full member experience.

Join For Free

[Download the blueprint](https://offers.automic.com/blueprint-to-continuous-delivery-with-automic-release-automation?utm_campaign=AMER%2520Online%2520Syndication%2520DZone%2520Platinum%2520Sponsorship%2520Ads%2520JULY-2017&utm_source=Dzone%2520Ads&utm_medium=Blueprint%2520to%2520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic’s 20+ years of business automation experience, and the proven tools and practices the company is already leveraging. 

Many projects use JSON for configuration files. Perhaps the most obvious example is the package.json file used by [npm](https://wwww.npmjs.com/) and [yarn](https://yarnpkg.com/lang/en/), but there are many others, including [CloudFormation](https://aws.amazon.com/cloudformation/) (originally JSON only, but now supports YAML as well) and [composer](https://getcomposer.org/) (PHP).

However, JSON is actually a pretty terrible configuration language for a number of reasons. Don't get me wrong - I like JSON. It is a flexible format that is relatively easy for both machines and humans to read, and it's a pretty good data interchange and storage format. But as a configuration language, it falls short.

## Why Is JSON Popular as a Config Language?

There are several reasons why JSON is used for configuration files. The biggest reason is probably that it is easy to implement. Many languages have JSON support in the standard library, and those that don't almost certainly have an easy-to-use JSON package readily available. Then there is the fact that developers and users are probably already familiar with JSON and don't need to learn a new configuration format to use the product. And that's not to mention all the existing tooling for JSON, including syntax highlighting, auto-formatting, validation tools, etc.

These are actually all pretty good reasons. It's too bad that this ubiquitous format is so ill-suited for configuration.

## The Problems With JSON

### Lack of Comments

One feature that is absolutely vital for a configuration language is comments. Comments are necessary to annotate what different options are for and why a particular value was chosen and-perhaps most importantly-to temporarily comment out parts of the config while using a different configuration for testing and debugging. If you think of JSON as a data interchange format, then it doesn't really make sense to have comments.

There are, of course, workarounds for adding comments to JSON. One common workaround is to use a special key in an object for a comment, such as "//" or"__comment". However, this syntax isn't very readable, and in order to include more than one comment in a single object, you need to use unique keys for each. David Crockford (the inventor of JSON) [suggests using a preprocessor to remove comments](https://plus.google.com/+DouglasCrockfordEsq/posts/RK8qyGVaGSr). If you are using an application that requires JSON configuration, I recommend that you do just that, especially if you already have any kind of build step before the configuration is used. Of course that does add some additional work to editing configuration, so if you are creating an application that parses a configuration file, don't depend on your users being able to use that.

Some JSON libraries do allow comments as input. For example, Ruby's JSON module and the Java Jackson library with the JsonParser.Feature.ALLOW_COMMENTS feature enabled will handle JavaScript-style comments just fine in JSON input. However, this is non-standard, and many editors don't properly handle comments in JSON files, which makes editing them a little harder.

### Overly Strict

The JSON specification is pretty restrictive. Its restrictiveness is part of what makes it easy to implement a JSON parser, but in my opinion, it also hurts the readability and, to a lesser extent, writability by humans.

#### Low Signal to Noise

Compared to many other configuration languages, JSON is pretty noisy. There is a lot of punctuation that doesn't aid human readability, although it does make it easier to write implementations for machines. In particular, for configuration files, the keys in objects are almost always identifiers, so the quotation marks around the keys are redundant.

Also, JSON requires curly braces around the entire document, which is part of what makes it an (almost) subset of JavaScript and helps delimit different objects when multiple objects are sent over a stream. But, for a configuration file, the outermost braces are just useless clutter. The commas between key-value pairs are also mostly unnecessary in config files. Generally, you will have a single key-value pair per line, so it would make sense to accept a newline as a delimiter.

Speaking of commas, JSON doesn't accept trailing commas. If you need commas after each pair, it should at least accept trailing commas, since trailing commas make adding new entries to the end easier and lead to cleaner commit diffs.

#### Long Strings

Another problem with JSON as a configuration format is it doesn't have any support for multi-line strings. If you want newlines in the string, you have to escape them with "\n", and what's worse, if you want a string that carries over onto another line of the file, you are just out of luck. If your configuration doesn't have any strings that are too long to fit on a line, this isn't a problem. However, if your configuration includes long strings, such as the description of a project or a GPG key, you probably don't want to put it on a single line with "\n" escapes instead of actual newlines.

#### Numbers

In addition, JSON's definition of a number can be problematic in some scenarios. As defined in the JSON spec, numbers are arbitrary precision finite floating point numbers in decimal notation. For many applications, this is fine. But if you need to use hexadecimal notation or represent values like infinity or NaN, then TOML or YAML would be able to handle the input better.

    
    
    {  
       "name":"example",
       "description":"A really long description that needs multiple lines.\nThis is a sample project to illustrate why JSON is not a good configuration format. This description is pretty long, but it doesn't have any way to go onto multiple lines.",
       "version":"0.0.1",
       "main":"index.js",
       "//":"This is as close to a comment as you are going to get",
       "keywords":[  
          "example",
          "config"
       ],
       "scripts":{  
          "test":"./test.sh",
          "do_stuff":"./do_stuff.sh"
       },
       "bugs":{  
          "url":"https://example.com/bugs"
       },
       "contributors":[  
          {  
             "name":"John Doe",
             "email":"johndoe@example.com"
          },
          {  
             "name":"Ivy Lane",
             "url":"https://example.com/ivylane"
          }
       ],
       "dependencies":{  
          "dep1":"^1.0.0",
          "dep2":"3.40",
          "dep3":"6.7"
       }
    }

## What You Should Use Instead

The configuration language you choose will depend on your application. Each language has different pros and cons, but here are some choices to consider. They are all languages that are designed for configuration first and would each be a better choice than a data language like JSON.

### TOML

[TOML](https://github.com/toml-lang/toml) is an increasingly popular configuration language. It is used by Cargo (Rust build tool), pip (Python package manager), and dep (golang dependency manager). TOML is somewhat similar to the INI format, but unlike INI, it has a standard specification and well-defined syntax for nested structures. It is substantially simpler than YAML, which is attractive if your configuration is fairly simple. But if your configuration has a significant amount of nested structure, TOML can be a little verbose, and another format, such as YAML or HOCON, may be a better choice.

    
    
    name = "example"
    description = """
    A really long description that needs multiple lines.
    This is a sample project to illustrate why JSON is not a \
    good configuration format. This description is pretty long, \
    but it doesn't have any way to go onto multiple lines."""
    
    version = "0.0.1"
    main = "index.js"
    # This is a comment
    keywords = ["example", "config"]
    
    [bugs]
    url = "https://example.com/bugs"
    
    [scripts]
    
    test = "./test.sh"
    do_stuff = "./do_stuff.sh"
    
    [[contributors]]
    name = "John Doe"
    email = "johndow@example.com"
    
    [[contributors]]
    name = "Ivy Lane"
    url = "https://example.com/ivylane"
    
    [dependencies]
    
    dep1 = "^1.0.0"
    # Why we depend on dep2
    dep2 = "3.40"
    dep3 = "6.7"

### HJSON

[HJSON](https://hjosn.org/) is a format based on JSON but with greater flexibility to make it more readable. It adds support for comments, multi-line strings, unquoted keys and strings, and optional commas. If you want the simple structure of JSON but something more friendly for configuration files, HJSON is probably the way to go. There is also a command line tool that can convert HJSON to JSON, so if you are using a tool that requires plain JSON, you can write your configuration in HJSON and convert it to JSON as a build step. [JSON5](https://json5.org/) is another option that is pretty similar to HJSON.

    
    
    {
      name: example
      description: '''
      A really long description that needs multiple lines.
      
      This is a sample project to illustrate why JSON is 
      not a good configuration format.  This description 
      is pretty long, but it doesn't have any way to go 
      onto multiple lines.
      '''
      version: 0.0.1
      main: index.js
      # This is a a comment
      keywords: ["example", "config"]
      scripts: {
        test: ./test.sh
        do_stuff: ./do_stuff.sh
      }
      bugs: {
        url: https://example.com/bugs
      }
      contributors: [{
        name: John Doe
        email: johndoe@example.com
      } {
        name: Ivy Lane
        url: https://example.com/ivylane
      }]
      dependencies: {
        dep1: ^1.0.0
        # Why we have this dependency
        dep2: "3.40"
        dep3: "6.7"
      }
    }

### HOCON

[HOCON](https://github.com/lightbend/config/blob/master/HOCON.md) is a configuration designed for the [Play](https://www.playframework.com/) framework but is fairly popular among Scala projects. It is a superset of JSON, so existing JSON files can be used. Besides the standard features of comments, optional commas, and multi-line strings, HOCON supports importing from other files, referencing other keys of other values to avoid duplicate code, and using dot-delimited keys to specify paths to a value, so users do not have to put all values directly in a curly-brace object.

    
    
    name = example
    description = """
    A really long description that needs multiple lines.
    
    This is a sample project to illustrate why JSON is 
    not a good configuration format.  This description 
    is pretty long, but it doesn't have any way to go 
    onto multiple lines.
    """
    version = 0.0.1
    main = index.js
    # This is a a comment
    keywords = ["example", "config"]
    scripts {
      test = ./test.sh
      do_stuff = ./do_stuff.sh
    }
    bugs.url = "https://example.com/bugs"
    contributors = [
      {
        name = John Doe
        email = johndoe@example.com
      }
      {
        name = Ivy Lane
        url = "https://example.com/ivylane"
      }
    ]
    dependencies {
      dep1 = ^1.0.0
      # Why we have this dependency
      dep2 = "3.40"
      dep3 = "6.7"
    }

### YAML

[YAML](http://yaml.org/) (YAML Ain't Markup Language) is a very flexible format that is almost a superset of JSON and is used in several conspicuous projects such as Travis CI, Circle CI, and AWS CloudFormation. Libraries for YAML are _almost_ as ubiquitous as JSON. In addition to support of comments, newline delimiting, multi-line strings, bare strings, and a more flexible type system, YAML also allows you to reference earlier structures in the file to avoid code duplication.

The main downside to YAML is that the specification is pretty complicated, which results in inconsistencies between different implementations. It also treats indentation levels as syntactically significant (similar to Python), which some people like and others don't. It can also make copy and pasting tricky. See [YAML: probably not so great after all](https://arp242.net/weblog/yaml_probably_not_so_great_after_all.html) for a more complete description of downsides to using YAML.

    
    
    name: example
    description: >
      A really long description that needs multiple lines.
      
      This is a sample project to illustrate why JSON is not a good 
      configuration format. This description is pretty long, but it 
      doesn't have any way to go onto multiple lines.
    version: 0.0.1
    main: index.js
    # this is a comment
    keywords:
      - example
      - config
    scripts: 
      test: ./test.sh
      do_stuff: ./do_stuff.sh
    bugs: 
      url: "https://example.com/bugs"
    contributors:
      - name: John Doe
        email: johndoe@example.com
      - name: Ivy Lane
        url: "https://example.com/ivylange"
    dependencies:
      dep1: ^1.0.0
      # Why we depend on dep2
      dep2: "3.40"
      dep3: "6.7"

### Scripting Language

If your application is written in a scripting language such as Python or Ruby, and you know the configuration comes from a trusted source, the best option may be to simply use a file written in that language for your configuration. It's also possible to embed a scripting language such as Lua in compiled languages if you need a truly flexible configuration option. Doing so gives you the full flexibility of the scripting language and can be simpler to implement than using a different configuration language. The downside to using a scripting language is it may be _too_ powerful, and of course, if the source of the configuration is untrusted, it introduces serious security problems.

### Write Your Own

If for some reason a key-value configuration format doesn't meet your needs, and you can't use a scripting language due to performance or size constraints, then it _might_ be appropriate to write your own configuration format. But if you find yourself in this scenario, think long and hard before making a choice that will not only require you to write and maintain a parser but also require your users to become familiar with yet another configuration format.

## Conclusion

With so many better options for configuration languages, there's no good reason to use JSON. If you are creating a new application, framework, or library that requires configuration choose something other than JSON.

[Download](https://offers.automic.com/blueprint-to-continuous-delivery-with-automic-release-automation?utm_campaign=AMER%2520Online%2520Syndication%2520DZone%2520Platinum%2520Sponsorship%2520Ads%2520JULY-2017&utm_source=Dzone%2520Ads&utm_medium=Blueprint%2520to%2520CD) the ‘Practical Blueprint to Continuous Delivery’ to learn how Automic Release Automation can help you begin or continue your company’s digital transformation. 

### Like This Article? Read More From DZone

[ ![](https://dz2cdn1.dzone.com/thumbnail?fid=4923360&w=120)](/articles/musings-in-yaml-tips-for-configuring-elasticsearch?fromrel=true) [Musings in YAML: Tips for Configuring Elasticsearch Beats](/articles/musings-in-yaml-tips-for-configuring-elasticsearch?fromrel=true)

[ ![](https://dz2cdn1.dzone.com/thumbnail?fid=3119092&w=120)](/articles/i-am-feeling-the-same-about-yaml-as-i-did-with-jso?fromrel=true) [ I Am Feeling The Same About YAML As I Did With JSON A Decade Ago](/articles/i-am-feeling-the-same-about-yaml-as-i-did-with-jso?fromrel=true)

[ ![](https://dz2cdn1.dzone.com/thumbnail?fid=9519772&w=120)](/articles/from-go-to-rust-json-and-yaml?fromrel=true) [From Go to Rust: JSON and YAML](/articles/from-go-to-rust-json-and-yaml?fromrel=true)

[ ![](https://dz2cdn1.dzone.com/thumbnail?fid=9612808&w=120)](/refcardz/introduction-to-devsecops?fromrel=true) [

Free DZone Refcard

Introduction to DevSecOps](/refcardz/introduction-to-devsecops?fromrel=true)

DOWNLOAD

Topics:

devops ,configuration ,json ,yaml ,tutorial

__ Like (8)

__ Comment (8) 

__

Save

__ Tweet

__ {{ articles[0].views | formatCount}} Views

__

  * Edit
  * Delete
  * {{ articles[0].isLocked ? 'Enable' : 'Disable' }} comments
  * {{ articles[0].isLimited ? 'Remove comment limits' : 'Enable moderated comments' }}

Published at DZone with permission of Thayne McCombs , DZone MVB. [See the original article here.__](https://www.lucidchart.com/techblog/2018/07/16/why-json-isnt-a-good-configuration-language/)

Opinions expressed by DZone contributors are their own.

## DevOps Partner Resources

[Removing Secrets From Application Code](https://www.conjur.org/lp/get-open-source/?utm_source=dzone&utm_medium=paid_display&utm_term=partner_resources&utm_content=conjur_lp&utm_campaign=conjur_os_en)

CyberArk

__

[Uncover your DevOps maturity level in four key areas.](https://automic.com/devops-maturity-assessment?utm_campaign=AMER%20Online%20Syndication%20DZone%20Platinum%20Sponsorship%20Ads%20JULY-2017&utm_source=Dzone%20Ads&utm_medium=Maturity%20Assessment)

Automic

__

[The DevOps 2.0 ToolKit brought to you by Cloudbees](https://pages.cloudbees.com/thedevops20toolkit_cloudbees.pdf?utm_source=dzone&utm_medium=partner-resource&utm_campaign=2018_0411_Global_DZone_PartnerResource_DevOps2.0ToolKit)

CloudBees

__

[What To Look for in a Logging Framework](http://blog.scalyr.com/2017/09/logging-framework)

Scalyr

__

[6 Core Principles For DevOps Security](https://www.cyberark.com/resource/6-core-principles-establishing-devops-security-scale/?utm_source=dzone&utm_medium=paid_display&utm_term=partner_resources&utm_content=security_at_scale_ebook&utm_campaign=conjur_os_en)

CyberArk

__

[Examining the Features of a Good Log File Viewer](http://blog.scalyr.com/2017/09/features-good-log-file-viewer)

Scalyr

__

[How InfluxDB outperforms Cassandra by 20x for Time Series Data Management](https://www.influxdata.com/resources/comparing-influxdb-and-cassandra/?ao_campid=70137000000JZvY&utm_campaign=dbzone&utm_medium=partner&utm_source=dzone&utm_content=&utm_term=)

InfluxData

__

[Automate Security in Your DevOps Pipeline](https://www.sonatype.com/devsecops?utm_campaign=dzone&utm_source=gartner%20devsecops)

Sonatype

__

[DevSecOps Reference Architectures](https://www.sonatype.com/devsecops-reference-architectures?utm_campaign=dzone&utm_source=DZone%20-%20DSO%20Reference%20Archs%202018&utm_medium=DZone%20-%20DSO%20Reference%20Archs%202018)

Sonatype

__

[The Transformative Technologies Driving DevOps](https://pages.cloudbees.com/transformative-technologies-driving-devops?utm_source=dzone&utm_medium=partner-resource&utm_campaign=2018_0411_Global_DZone_PartnerResource_TransformativeTechnologies)

CloudBees

__

[DevSecOps Best Practices. Read this guide and learn 4 steps that are critical to DevSecOps success. Download now!](https://www.xmatters.com/resources/reports/devsecops-best-practices-guide?utm_campaign=70138000001F6XsAAK&utm_source=dzon&utm_medium=banner&utm_content=devsecops-best-practices-guide)

xMatters

__

[Why Time-Series DBs matter - How InfluxDB outperforms MongoDB by 3x](https://www.influxdata.com/resources/benchmarking-influxdb-vs-mongodb-for-time-series-data-metrics-and-management/?ao_campid=70137000000JgNw&utm_campaign=dbzone&utm_medium=partner&utm_source=dzone&utm_content=&utm_term=)

InfluxData

__

## DevOps Partner Resources

[Removing Secrets From Application Code](https://www.conjur.org/lp/get-open-source/?utm_source=dzone&utm_medium=paid_display&utm_term=partner_resources&utm_content=conjur_lp&utm_campaign=conjur_os_en)

CyberArk

__

[Uncover your DevOps maturity level in four key areas.](https://automic.com/devops-maturity-assessment?utm_campaign=AMER%20Online%20Syndication%20DZone%20Platinum%20Sponsorship%20Ads%20JULY-2017&utm_source=Dzone%20Ads&utm_medium=Maturity%20Assessment)

Automic

__

[The DevOps 2.0 ToolKit brought to you by Cloudbees](https://pages.cloudbees.com/thedevops20toolkit_cloudbees.pdf?utm_source=dzone&utm_medium=partner-resource&utm_campaign=2018_0411_Global_DZone_PartnerResource_DevOps2.0ToolKit)

CloudBees

__

[What To Look for in a Logging Framework](http://blog.scalyr.com/2017/09/logging-framework)

Scalyr

__

### **{{ editionName }}**

  * {{ node.blurb }}

Free {{node.type}}

{{ ::node.title }}

__ __

# {{ parent.title || parent.header.title}}

### {{ parent.tldr }}

### {{ parent.linkDescription }}

{{ parent.urlSource.name }}

by {{ parent.authors[0].realName || parent.author}} 

__

__

* {{ parent.articleDate | date:'MMM. dd, yyyy' }} {{ parent.linkDate | date:'MMM. dd, yyyy' }}
* [{{ parent.portal.name }} Zone]({{ parent.portal.url }})

__Tweet

__ {{ parent.views }} ViewsClicks

__

  * Edit
  * Delete
  * {{ parent.isLocked ? 'Enable' : 'Disable' }} comments
  * {{ parent.isLimited ? 'Remove comment limits' : 'Enable moderated comments' }} 

___
