# Two Words About Clean Code

_Captured: 2017-04-24 at 23:27 from [dzone.com](https://dzone.com/articles/two-words-about-clean-code?edition=292911&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-24)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

There are many things to say about clean code and it might not be something new or be revealing to you, but I want to share a very helpful approach, which can help you to write nice looking code.

## Background

Let's imagine that we have a piece of software that allows us to create documents with some indexes and file attachments. Our task is to listen to an event, like DOCUMENT_CREATED or something like that, and then carry out the following actions:

\- Validate the document and move it to the Error folder if needed.

\- Send an email to the administrator.

\- Move the document to another folder based on its category index.

That's all, and enough to screw up the code.

## A Reasonable Approach

1\. Do not write any implementations first.

2\. Instead, write out all your logic using only method names (i.e. descriptions).

We don't even have logic methods in the above code, but our IDE can create ones instead of us (ex: Eclipse).

The method above is the same as describing the each step in this process, as it allows us to think about each step.

3\. Write implementations.

4\. Fun!

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

Opinions expressed by DZone contributors are their own.
