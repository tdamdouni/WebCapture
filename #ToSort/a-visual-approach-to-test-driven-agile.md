# A Visual Approach to Test-Driven Agile

_Captured: 2017-04-05 at 10:54 from [www.scrumalliance.org](https://www.scrumalliance.org/community/articles/2015/september/a-visual-approach-to-test-driven-agile?mkt_tok=3RkMMJWWfF9wsRonv67LZKXonjHpfsX67uwoX7Hr08Yy0EZ5VunJEUWy2YYIRNQ/cOedCQkZHblFnVkJSq2mSKgNr6UK&utm_content=buffer638f7&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![](https://certification.scrumalliance.org/system/members/photos/000/391/512/200x200/IMG_8669.JPG?1460305005)

> _[Nigel Thurlow](https://www.scrumalliance.org/community/profile/nthurlow/)_

### Context

Test-driven development (TDD) should be the aim of any Scrum development team. We all have heard the "Test first, code next" mantra, and there are numerous articles and even books written on TDD and XP. This article does not attempt to better them.

What I am presenting here is a visual guide to Test-Driven Agile Development. My visuals are based around the Agile Testing Matrix created by Brian Marick, one of the authors of the [Agile Manifesto](http://www.agilemanifesto.org/) and a leading voice in the Agile testing world. I have slightly modified the labeling also used in SAFe.

###   
Agile testing matrix based on the original idea of Brian Marick

![](https://www.scrumalliance.org/getattachment/df9383d4-6e12-4ad5-b5a1-689403b36e49/Quadrants.png.aspx?width=700&height=546)

The quadrant numbering system does _not_ dictate some order of testing you work through as if doing Waterfall. It is purely an arbitrary numbering used as a reference when referring to the matrix. The quadrants are merely a guide to help teams plan their testing and make sure they foresee all the resources they need to accomplish it.

The following visuals take the concepts in this matrix and attempt to make them easy to understand and consume. I use this as a guide when teaching TDD.

There is a link to downloadable 11x17 (A3) PDF of the teaching aid at the end of this article.

### Test-driven development (TDD)

![](https://www.scrumalliance.org/getattachment/28fd33c5-c70e-44d7-8dd2-e63c82a5f8ec/TDD.png.aspx?width=700&height=286)

Most of us understand the concept of TDD, and this simple picture captures the essence of how we would like teams to create value when coding. If you are new to the concepts of TDD, look for books by [Kent Beck](http://www.amazon.com/Kent-Beck/e/B000APC0EY/ref=sr_tc_2_0?qid=1441644955&sr=1-2-ent) and [David Astels](http://www.amazon.com/David-Astels/e/B0034PE5P4/ref=sr_tc_2_0?qid=1441645024&sr=1-2-ent).

### Test automation is essential

![](https://www.scrumalliance.org/getattachment/f23df3f7-1afe-4b3b-add3-33543a5a6b94/Automating-Acceptance-Testing.png.aspx?width=700&height=283)

You will see that automation is a key theme in this article. Wherever possible, automate your tests. Not doing so will make your regression and aggregated unit testing take over most of your development time. The phrase "The faster you go, the faster they grow, the slower you go" sums this up perfectly. I just wish I'd thought of it.

### Acceptance Test-Driven Development (ATDD)

![](https://www.scrumalliance.org/getattachment/64df9f5f-0a3f-4f0c-a9e6-529abea94de7/ATDD.png.aspx?width=700&height=285)

ATDD is the nirvana for many practitioners of our craft.

With ATDD (also known as Behavior-Driven Development or BDD), you write a single [acceptance test](http://www.agilemodeling.com/artifacts/acceptanceTests.htm) and then just enough functionality or code to fulfill that test. The goal of ATDD is to specify sufficiently detailed and executable requirements for your solution on a just-in-time (JIT) basis.

I spend a lot of time with product owners and teams, teaching them how to write good acceptance criteria. ATDD is a key reason why I do this.

There are a number of tools, from simple record and playback to more advanced scripting language to automated acceptance tests.

### Example of an automated acceptance test using Easyb

Easyb is a behavior-driven development framework for the Java platform.

_Scenario: _User can approve an invoice for an amount less than the agreed maximum  
{  
given "the User has selected an open invoice",  
and "the User has chosen to approve the invoice",  
and "the invoice amount is less than the agreed maximum amount",  
when "the User completes the action",  
then "the invoice should be successfully approved"  
}

### Unit and Component Tests

![](https://www.scrumalliance.org/getattachment/f41656bc-ebc4-4add-8eb2-2f03ccc2b2ca/Q1-Unit-and-Component.png.aspx?width=700&height=284)

Every Agile development team should already be automating their unit and component tests. These tests build your incremental test bed/platform that all new check in code is executed against. This effectively builds you a "free to use" regression testing environment!

### User-facing story and feature acceptance tests

![](https://www.scrumalliance.org/getattachment/161bbaad-1984-48ab-9a7b-7a43503847fc/Q2-User-Facing-and-Feature-Acceptance-Tests.png.aspx?width=700&height=284)

I view these tests as potential replacement for UAT. The user can simply perform some action and see the outcome as it happens. This is black-box testing and is verification of the efficacy of the code delivered, without exposing any technical aspects to the end user. It's another testing reason that I work hard with POs and teams to write exacting acceptance criteria for every story.

### System acceptance tests

![](https://www.scrumalliance.org/getattachment/599bb6d8-ca52-4d7d-9aca-aa8bfb964b31/Q3-System-Acceptance.png.aspx?width=700&height=285)

Tests are designed to ensure that the system meets usability and functional requirements. These tests may involve many users and many scenarios, so automation is harder if test coverage of many dynamic scenarios is required. I still maintain that if the use cases are known, many of these tests can be scripted and automated, given appropriate skills and tooling.

Accessibility and exploratory testing are examples of testing that will, in the main, be manual. By definition, accessibility testing relies on human testing of the interfaces, and there is little value in automating exploratory tests that may never be reused.

### System quality tests

![](https://www.scrumalliance.org/getattachment/084742e7-b8b4-488a-91d3-46a92d64d41e/Q4-System-Qualities-Tests.png.aspx?width=700&height=286)

Nonfunctional requirements (NFRs) testing should be executed continuously and also automated, as any change to the underlying system could violate one of our NFRs. Any small change could have a big impact on performance, and you really want to detect what small change caused that problem at the moment the change was made, rather than go hunting for the proverbial needle in a haystack when you run system quality tests at the end of development. Not to mention that it would be a Waterfall approach.

I hope this visual learning aid is useful to you and your teams. As always, I welcome any comments or improvement suggestions.

To download your own copy of the A3 visual, click here: <https://www.dropbox.com/sh/euqhagbybt4fqfb/AAC9S09nz9lTFpCI2dNNtX_Ka?dl=0>

![](https://www.scrumalliance.org/getattachment/fd201535-3ee8-4623-b068-9b1fe51b7ba8/A3.png.aspx?width=700&height=455)
