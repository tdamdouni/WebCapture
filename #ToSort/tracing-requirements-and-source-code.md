# Tracing requirements and source code

_Captured: 2017-04-13 at 22:26 from [blogs.itemis.com](https://blogs.itemis.com/en/feature-of-the-month-march-2017-tracing-requirements-and-source-code?utm_source=hs_email&utm_medium=email&utm_content=50499857&_hsenc=p2ANqtz-_pp9VbBoJjcX88KbA-sWAgGobl2IFHUe9JTIs1JlJTJ3laq6iOhgokwoSayaRitq4ZzOvzXKiE5P1lfm10lCjk1-juzO8bgFs_l6RsRMW-HXyz2V8&_hsmi=50498919)_

In the last month, our team behind [YAKINDU Traceability](https://www.itemis.com/en/yakindu/traceability/) received a couple of questions regarding how to establish bidirectional traceability between requirements or design elements and software units a.k.a source code - as for example required in the [Automotive Spice](https://www.slideshare.net/DominikStrube/automotive-spice-30-what-is-new-and-what-has-changed/24) model. We also optimized the performance of our C/C++ adapter and therefore decided that it qualifies to be called "feature of the month".

With YAKINDU Traceability, you can

  * recognize elements of the source code as traceable artifacts, e.g. files, functions, variables
  * create bidirectional trace links from source code artifacts to requirements, elements of your design, test-cases, etc.

You can configure whether trace links should be stored non-invasively (i.e. in an external file, leaving the source code untouched) or in the form of dedicated comments in the source code. If you decide to link by means of comments, YAKINDU Traceability is able to recognize and write the unique identifier of linked artifacts within source code comments. The following image illustrates how a trace link from a C-header file to the design element _RainSensor [Component]_ which resides in an Enterprise Architect model becomes manifest in a comment.

![Verlinkung Kommentare ID.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/Verlinkung%20Kommentare%20ID.png?t=1492099761217&width=362&height=219&name=Verlinkung%20Kommentare%20ID.png)

The actual format of a comment can be configured freely. So for example in the case illustrated above, each link information within a comment is prefixed by „@SDD". The image below shows an example configuration of YAKINDU Traceability which covers exactly this case:

![Verlinkung Kommentare Konfiguration.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/Verlinkung%20Kommentare%20Konfiguration.png?t=1492099761217&width=362&height=330&name=Verlinkung%20Kommentare%20Konfiguration.png)

Depending on whether you link requirements or test cases (or both), YAKINDU Traceability can easily calculate the progress of your project or the source code implementation as it measures coverage of requirements by software units or test coverage at ease. For example, the gaps on the left side of the following sheet show missing trace links from elements of the _Software detailed design_ to _Software units_ which already exist.

![Traceability Artifact Coverage.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/Traceability%20Artifact%20Coverage.png?t=1492099761217&width=362&height=146&name=Traceability%20Artifact%20Coverage.png)

Having a coverage report in mind, it is important to decide on which detail level you want to trace to source-code-artifacts. Do you want to link from requirements to complete source code files (e.g. to translation units in C)? Is it necessary to trace to functions or variables within a file? There is a trade-off: The more fine grained you want to evaluate your traceability, coverage analysis, impact analysis etc, the more expensive your maintenance will be. Of course, the detail level of source-code traceability can be adjusted in YAKINDU Traceability. Our example is configured to trace on the level of translation units:

![Verlinkung Translation Unit.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/Verlinkung%20Translation%20Unit.png?t=1492099761217&width=362&height=273&name=Verlinkung%20Translation%20Unit.png)

Concluding, I want to summarize the results of our performance-tuning. In a real-world scenario comprising about 1,300 C files with about 1,600 comments relevant for traceability, it took YAKINDU Traceability about nine seconds to analyze these files and to recognize artifacts and links.

Please find more information about YAKINDU Traceability on our website.
