# Making It Easier to Clean Big Data

_Captured: 2017-04-04 at 00:13 from [dzone.com](https://dzone.com/articles/making-it-easier-to-clean-big-data?edition=286971&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-03)_

Need to build an application around your data? [Learn more](https://dzone.com/go?i=200129&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) about dataflow programming for rapid development and greater creativity.

Big Data is great, but it's only really useful if you can derive insights from it. With much of the data we harvest being somewhat messy and unstructured, organizations often spend far more time tidying up the data than they do gaining insights from it.

I've [written before](http://adigaskell.org/2016/11/22/using-ai-to-clean-up-big-data/) about automated approaches to doing this, with projects such as Active Clean from researchers at Columbia University and the University of California at Berkeley, which uses prediction models to test out datasets, and uses the results to understand the fields that require cleaning whilst simultaneously updating the models at the same time.

> "Big Data sets are still mostly combined and edited manually, aided by data cleaning software like Google Refine and Trifacta or custom scripts developed for specific data cleaning tasks," the researchers say. "The process consumes up to 80 percent of analysts' time as they hunt for dirty data, clean it, retrain their model and repeat the process. Cleaning is largely done by guesswork."

## Error Spotting

Whilst sorting our what is largely inconsequential data is a major part of an analysts' time, there is also the sizeable task of cleaning up erroneous data that can skew datasets.

A new tool called [Vizier](http://odin.cse.buffalo.edu/vizier/), developed by researchers at the University of Buffalo aims to help by proactively catching data errors. The tool allows users to interactively work with datasets, cleaning, curating, and visualizing data in what the team hope are meaningful ways.

The tool is intended for very large datasets with millions of data points.

> "We are creating a tool that'll let you work with the data you have, and also unobtrusively make helpful observations like 'Hmm… have you noticed that two out of a million records make a 10 percent difference in this average?'" the team says. 

The hope is that these kinds of automated tools will make it easier for a wider spread of organizations to start utilizing data, as they won't have to invest huge sums in building the kind of teams required to clean up the data they're collecting.

This is especially so as a growing number of government agencies are releasing data, and open data is rapidly becoming the defacto way of operating for governments across the western world.

As an open source tool, Vizier hopes to play an active and positive role in this ecosystem.

> "We want to make it easier for data scientists -- and eventually data hobbyists -- to discover and communicate not only what the data says, but why the data says that," the team says. 

[Check out](https://dzone.com/go?i=200130&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) the Exaptive data application Studio. Technology agnostic. No glue code. Use what you know and rely on the community for what you don't. [Try the community version](https://dzone.com/go?i=200130&u=https%3A%2F%2Fexaptive.city%2F%23%2Flanding%3Freferrer%3DGeneral).
