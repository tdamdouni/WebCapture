# The Rise of Test Impact Analysis

_Captured: 2017-08-10 at 08:18 from [martinfowler.com](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

One curse of modern software development is having "too many" tests to run all of them prior to check-in. When that becomes true, developers use a costly coping strategy of not running any tests on their local developer workstation. Instead they rely on tests running later on an integration server. And quite often even those fall into disrepair, which is inevitable when [shift right](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) becomes normal for a dev team.

Of course, everything that you test [pre-integrate](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) should immediately be tested [post-integrate](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) in the [Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html) (CI) infrastructure. Even the highest functioning development teams might experience breakages born from timing alone for commits landing in real time. Those teams might also harbor someone who sometimes wants to 'economize' on the agreed integration process and NOT run tests. Luckily, CI servers and a decent series of build steps are how you quickly catch those moments.

Various techniques exist to speed up test execution, including running them in parallel over many machines and using [test doubles](https://martinfowler.com/bliki/TestDouble.html) for slow remote services. But this article will focus on reducing the number of tests to run, by identifying those most likely to identify a newly added bug. With a [test pyramid](https://martinfowler.com/bliki/TestPyramid.html) structure, we run unit tests more frequently because they usually run faster, are less brittle and give more specific feedback. In particular, we frame a suite of tests that should be run as part of CI: [pre-integrate and post-integrate](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer). We then create a deployment pipeline to run slower tests later.

The same problem restated: **If tests ran infinitely quickly, we would run all the tests all the time, but they are not, so we need to balance cost vs value when running them.**

In this article, I detail an emerging field of testing-related computer science where Microsoft is leading the way, a field that companies with long test automation suites should take note of. You may be able to benefit from Microsoft's advances around "Test Impact Analysis" immediately, if you are in the .NET ecosystem. If you are not doing .NET, you have to be able to engineer something yourself fairly cheaply. A former employer of mine engineered something themselves based on proof of concept work that I share below.

## Conventional strategies to shorten test automation

To complete the picture, I will recap the traditional "run a subset of the tests" strategies, that remain dominant in the industry. Well, with the newer reality of parallel test execution and service virtualization.

### Creation of suites and tags

![](https://martinfowler.com/articles/rise-test-impact-analysis/suites_and_tags.png)

> _Major groupings of unit, service and functional UI. Within unit tests, tags for meaningful sub-groupings, including one 'express' that samples a subset of the the others._

![](https://martinfowler.com/articles/rise-test-impact-analysis/suites_and_tags_e.png)

> _After 'Shopping Cart' tests were run, all bar one passing. here._

This approach works with recursive build technologies such as Ant, Maven, MSBuild, Rake, and alike.

Historically, teams would give up on making their tests infinitely fast, and use suites or tags to targeting a subset of tests at any one time. With the creation of suites and tags, a subset of tests can be verbally describable. For example "UI tests for the shopping cart". Tags or suites could allude to business areas of the application, or to technical or tiered groupings. Defining tags and suites requires expert human design creativity. At least in order to push towards optimal groupings. That implied that they could be insufficiently, inexactly, and incorrectly grouped too, which is common enough, even if difficult for humans to determine. Too few and too many tests executed at the same time is a strong possibility for running one suite only - a wasteful use of computing esources and time, that also risks letting a bug slip through. Teams might choose to have CI jobs that use a smaller suite per commit, and then also a nightly build job that runs all tests. Obviously that delays bad news, and defeats the aims of [Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html).

Suites and tags, however, is the way the majority of the software development world has organized its test code-base.

### Pre-calculated graphs of source vs tests

![](https://martinfowler.com/articles/rise-test-impact-analysis/tags.png)

> _276 tests with their notional 'size' designations._

The ones executed for given commits, with two failures resulting. As it happens, some of those turn out to be small, some medium, and some large. I have only depicted a tree/fractal because it helps explain the concepts (it is not really like that).

Google's fabled internal build system [Blaze](http://google-engtools.blogspot.com/2011/08/build-in-cloud-how-build-system-works.html), has been copied into a few open source technologies over the years. Most notable are [Buck](https://buckbuild.com/) from Facebook and [Bazel](https://bazel.build) from Google. [Pants](http://www.pantsbuild.org/) by Twitter, Foursquare and Square. Blaze inside Google navigates a single **directed graph** across their entire monorepo. Blaze has a mechanism of direct association of test to production code. That mechanism is a fine grained directory tree of production sources and associated test sources. It has explicit dependency declarations via [BUILD](https://bazel.build/versions/master/docs/build-ref.html) files that were checked in too. Those BUILD files could be maintained and evolved by the developers, but could also be verified as correct or incorrect by automated tooling. That process repeated over time goes a long way to make the directed graphs correct and efficient.

Importantly, that tooling could point out redundant claims about dependencies. Thus for a given directory/package/namespace, the developer could kick off a subset of the tests quite easily - but just the ones that are possible via directed graphs from the BUILD files. The ultimate time saver, both for the developer [pre-integrate](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) and the integration infrastructure, was scaled CI infrastructure 'Forge' (later TAP), was the automated subsetting of tests to run per commit based on this baked-in intelligence.

There are a bunch of mind-blowing stats in [Taming Google-Scale Continuous Testing](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/45861.pdf). In my opinion this stuff has cost Google tens of millions but made them tens of billions over the years. Perhaps far greater than the earnings:wages ratio.

## Test Impact Analysis

Test Impact Analysis (TIA) is a technique that helps determine which subset of tests for a given set of changes.

![](https://martinfowler.com/articles/rise-test-impact-analysis/tags_e.png)

> _A similar depiction for tests to run for a hypothetical change._

The key to the idea is that not all tests exercise every production source file (or the classes made from that source file). Code coverage or instrumentation, while tests are running is the mechanism by which that intelligence is gleaned (details below). That intelligence ends up as a map of production sources and tests that would exercise them, but begins as a map of which productions sources a test would exercise.

![](https://martinfowler.com/articles/rise-test-impact-analysis/tests_to_prod_map.png)

> _One test (from many) exercises a subset of the production sources._

![](https://martinfowler.com/articles/rise-test-impact-analysis/prod_to_tests_map.png)

> _One prod source is exercised by a subset of the tests (whether unit, integration or functional)_

So you will note that the stylized diagram of executed tests, is the same as for the Directed graph build technologies above. It's effectively the same, as the curation of the BUILD files over time leads to more or less the same outcome as TIA.

The TIA maps can only really be used for changes versus a reference point. That can be as simple as the work the developer would commit or has committed. It could also be a bunch of commits too. Say everything that was committed today (nightly build), or since the last release.

One realization from using a TIA approach is that you have too many tests covering the same sections of prod code. Of those are straight duplicates, then deleting tests after analysis of the test and the paths through prod code that it exercises, is a possibiity. Often they are not though, and working out how to focus testing on what you want to test, and not on at all on transitive dependencies in the code is a different focus area that inevitably rests on the established practice of using [test doubles](https://martinfowler.com/bliki/TestDouble.html) and more recently Service Virtualization (for integration tests).

The minimal level of creating a list of what has changed is "Changed production sources", but the ideal would to determine what methods/functions have changed, and further subset to only tests that would exercise those. Right now though, there is one ready to go technology from Microsoft that works at the source-file level, and one reusable technique (by me). Read on.

### Microsoft's extensive TIA work

Microsoft has put in the longest concerted effort to productionize Test Impact Analysis ideas, and gave the concept that name and its acronym.

They have a current series of blog entries that span March to August of 2017, so far: **Accelerated Continuous Testing with Test Impact Analysis - **[Part 1](https://blogs.msdn.microsoft.com/devops/2017/03/02/accelerated-continuous-testing-with-test-impact-analysis-part-1/), [Part 2](https://blogs.msdn.microsoft.com/devops/2017/05/16/accelerated-continuous-testing-with-test-impact-analysis-part-2/), [Part 3](https://blogs.msdn.microsoft.com/devops/2017/06/13/accelerated-continuous-testing-with-test-impact-analysis-part-3/), and [Part 4](https://blogs.msdn.microsoft.com/devops/2017/08/04/accelerated-continuous-testing-with-test-impact-analysis-part-4/).

Their older articles on this go back eight years:

Microsoft's Pratap Lakshman detailed the evolution of their implementation. Concerning the current evolution of their TIA tech, Pratap says:[[1]](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)

The map of the impacted tests versus production code is recalculated when there is a build that is triggered. The job to do that runs as part of the VSTest task within a VSTS build definition.

Our TIA implementation collects dynamic dependencies of each test method as the test method is executing.

At a high level here is what we do: As the test is executing it will cover various methods - the source file in which those methods reside are the dynamic dependencies we track.

So we end up with a mapping like the following:
    
    
            Testcasemethod1 <--> a.cs, b.cs. d.cs
            Testcasemethod2 <--> a.cs, k.cs, z.cs 

and so on …

Now when a commit comes in to say `a.cs`, we run all `Testcasemethod(s)` that had `a.cs` as their dynamic dependency. We, of course, take care of newly introduced tests (that might come in as part of the commit) and carry forward previously failing tests as well.

Our TIA implementation does not do test prioritization yet (e.g. most often broken first). That is on our radar, and we will consider it if there is sufficient interest from the community.

The actual TIA map data is stored in TFS as in an SQLServer database. When a commit comes in, TIA uses TFVC/Git APIs to open up the commit and see the files into the which the changes are going into. Once it knows the files, TIA then consults the mapping to know which tests to run.

Of course, usage of this TIA technology is supported in pull request (PR) and regular CI workflows, as well as [pre-integrate](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) on the developer's workstation.

We want our users to embrace the [Shift Left](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) and move as many of their tests to earlier in the pipeline. In the past we have seen customers a little concerned about doing that because it would mean running more tests at every commit, thereby making the CI builds take longer. With TIA we want to have our users [Shift Left](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) and let TIA take care of running only the relevant tests - thereby taking care of the performance aspect.

Concerning the first few years of TIA inside TFS and Visual Studio, he says:

The TIA technology at that time was quite different in many ways:

  * It would only identify impacted tests. it was the left to the user to explicitly run them.
  * It used block level code coverage as the approach to generate the test <\--> mapping. In the subsequent build, it would do an IL-diff with the earlier build to find out blocks that changed, and then use the mapping to identify and list impacted tests. Note that it would not run them for you.
  * The above approach made it slow (compared to the current implementation), and required way more storage for the mapping information (compared to the current implementation)
  * The above approach also caused it to be less safe than the current implementation (it would miss identifying impacted tests in some cases).
  * It did not support the VSTS build workflow (it was only supported in the older XAML build system) 

### Test Impact Analysis via conventional code coverage tools and scripting

I had an idea to co-opt modern, off the shelf, code-coverage tools into the same impact analysis when I worked at HedgeServ. From that idea, I made two proof of concept blog entries (with the associated code on Github): One for Maven & Java[[2]](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer), and one for Python[[3]](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer). Of course, like an [eejit](https://en.oxforddictionaries.com/definition/eejit), I thought I had a novel invention, but I did not know at the time that there was a quite a bit of prior-art in this space (Microsoft above). The technique I've shown is cheap to develop within your tool chain, even if it may have a cost to run within your CI infrastructure.

A simple implementation of the idea of Test Impact Analysis requires that you have one up front activity:

  1. Run single test and collect code-coverage for it
  2. From the prod source files touched for the test, make a temporary map of the prod sources (key) to test path/name (value)
  3. Update the source files that contain the master map, replacing all previous entries for that test
  4. Commit those changed map source file to VCS (only the CI job in question should have permission to do this)
  5. Clear the coverage data (so as to not entangle coverage reports per test)
  6. Go back to #1 for the next test (most recently changed sources/tests first?)

After running all the tests one at a time you have a comprehensive map connecting prod code to the tests that cover them.

Then when you later make changes to some prod code, you can figure out which tests exercised that code, and are thus likely to be informative when run. Any test failures produced are provably the only test failures that could happen from the changes made. The two proofs of concept referred to above contain a small amount Python code that attempts to:

  * Calculate TIA maps ahead of need
  * Use TIA maps in a [pre-integrate](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) situation (with small modifications it could be used in CI jobs too)

HedgeServ's test-base is comprised of regular speedy unit tests, followed by integration tests that are Microsoft Excel spreadsheets which in turn indirectly invoke Python. There are 12,000 of them. Those tests are many hours of extensive and advanced algorithm tests that would be impossible to do per-integration in CI infrastructure without some "run less of them" strategy. Their DevOps team operationalized the proof of concept as "Test Reducer" (the initial name I gave this tech), and the quickest permutations are now ten minutes. A fantastic improvement. Developers and Test Engineers can run them [pre-integrate](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer), and the CI infrastructure can do the same. HedgeServ's Managing Director of Software Development, Kevin Loo, tells me that "developers count on the quicker test runs, and the pace of development has increased because of an increased confidence".

Because generic code coverage tools are being used the TIA aspect has to be run one test at a time, which has an up front cost. For that reason, the map that results from the analysis is checked into source-control and incrementally updated. It, therefore, has to be text and ordered in nature so that the diffs can be terse and have some meaning. Checking the map into source control also benefits the CI infrastructure and the individual developers looking to run fewer tests prior to integration (and code review).

This TIA design has a limitation because of the nature of code coverage tools: Only one test can be run at a time in order for an accurate impact graph to be calculated. In order to use the map data, there is a need run "git status" (or git show >hash>) and then parse the output to find the 'changed/added/deleted' production code sources. And those are the keys to the impact map, that result in a list of tests to run. It is only the data gathering CI job that has the limitation of "one test at a time", which is why you more or less consider it perpetually running.

The testing technology, as you see, can be totally alien to your main language choices for the prod code. In HedgeServ's case, their algorithmic tests were in Microsoft Excel files under source control (that even the BAs contributed to). If that is possible then so are SmartBear's TestComplete, HP's Unified Functional Testing (UFT - formerly QTP), and of course Selenium. The only requirement is that tests can be scripted to run one at a time (while you build the TIA map). You are also going to have to commit to updating the map at some frequency following its initial creation - use your CI infrastructure.

You are then left with a decision as to where to store that map data. You could choose a file share, or a document store, or a relational schema. I chose (and would recommend) text files in a directory that's in the same repo/branch as the prod source itself. That at least allows branching to work (whatever your branching-model) and have divergent impact maps perhaps reflecting the divergent nature of the code.

For a client recently, I was looking at a project that uses [KDB](https://en.wikipedia.org/wiki/Kdb%2B) and [Q](https://en.wikipedia.org/wiki/Q_\(programming_language_from_Kx_Systems) for its system and trying to advise them on how to bring down test times. There is no code coverage tech for these, so that was the end of that conversation.

Vector Software has made a product called [ VectorCAST/QA](https://www.vectorcast.com/software-testing-products/vectorcast-qa-predictable-quality-embedded-development) that is a one stop shop application that leverages code-coverage in the same way to run fewer impacted tests (and more). Their technology is mostly sold to the automotive (and related) industry that embeds C, C++ and Ada software. VectorCAST working in this mode of operation also predates my _kitchen sink_ experiments. I have to work on my googling skills!

## TIA support in IDEs

Microsoft also has a powerful Live Unit Testing[[4]](https://martinfowler.com/articles/rise-test-impact-analysis.html?utm_content=buffer73904&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer) feature in Visual Studio that, if enabled, automatically runs impacted unit tests even as you edit the code. While related to TIA, this is perhaps worth a separate analysis.

Last month I thought I would [raise a feature request for JetBrains](https://youtrack.jetbrains.com/issue/IDEA-174949) to equivalent create TIA functionality to their IDEs. During the triage of the ticket I had raised, JetBrains connected it to [another one from 2010 on the same topic](https://youtrack.jetbrains.com/issue/IDEA-62832), and in that one there was a suggestion that some of this functionality [is already implemented](https://confluence.jetbrains.com/display/IDEADEV/IDEA+Coverage+Runner). I could not get it working when I tried it though ☹️
