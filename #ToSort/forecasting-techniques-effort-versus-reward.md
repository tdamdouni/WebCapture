# Forecasting techniques – effort versus reward

_Captured: 2017-04-14 at 00:51 from [focusedobjective.com](http://focusedobjective.com/forecasting-techniques-effort-versus-reward/?utm_content=bufferbb2c4&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Why should I use probabilistic forecasting? This is a common question I have to answer with new clients. I always use and recommend the simplest technique that answers the specific question being asked and progress in complexity only when absolutely necessary. I see forecasting capabilities in five stages of incremental improvement at an effort cost. Here is my simple 5 level progression of forecasting techniques -

![forecasting levels of capability](http://focusedobjective.com/wp-content/uploads/2016/08/forecasting-levels-of-capability.png)

> _Level 1 - Average regression_

Traditional Agile forecasting (1) relies on using a running average and projecting that average out over time for the remaining work being forecast. This is level 1 on our capability measure. Does it work? Mostly. But it does rely on the future pace being similar to the past, and it suffers from the Flaw of Averages (read about it in the book, Flaw of Averages by Sam Savage). The flaw of averages is the terminology that covers errors in judgement because a single value is used to describe a result when the result is actually many possible outcomes each with a higher or lower possibility. When we project the historical average pace (story point velocity or throughput), the answer we calculate has around 50% chance. A coin toss away from being late. We often want better odds than that when committing real money and people to a project.

![flaw of averages 1](http://focusedobjective.com/wp-content/uploads/2016/08/flaw-of-averages-1-300x207.png)

![flaw of averages 2](http://focusedobjective.com/wp-content/uploads/2016/08/flaw-of-averages-2-300x225.png)

> _Level 2, 3, and 4 - Probabilistic Forecasting_

Probabilistic forecasting returns a fuller range of possibilities that allow the likelihood of a result to be calculated. In the forecasting software world, this is normally "On or before date x." In a probabilistic forecast we look at what percentage of the possible results versus all results we calculated were actually "on or before date x." This allows us to say things like, "We are 85% certain to deliver by 7th August."

Probabilistic forecasting relies upon the input parameters being non-exact. A simple range estimate like 1 to 5 days (or points, or whatever unit pace is measured) for each of the remaining 100 items is enough to perform a probabilistic forecast. Its the simplest probabilistic model and gets us to level 2 in our capability. The goal is that the eventual actual result is actually between 1 to 5 days for an item. Our spreadsheet tools use this technique when estimates are set to "Range estimate" ([download it here](https://github.com/FocusedObjective/FocusedObjective.Resources/raw/master/Spreadsheets/Throughput%20Forecaster.xlsx)).

Levels 3 and 4 are more refined range estimate forecasts. Level 3 specifies a probability distribution that helps you specify if part of the range estimate is more likely than another. Low-Most Likely-High estimates are this type of distribution. It helps firm up the probabilistic forecast by showing preference to some range estimate values based on our knowledge of the work. Over the years different processes have demonstrated different distribution curves, for example, manufacturing often shows a bell curve (Normal distribution) and software work shows a left-skewed distribution where the lower values are more likely than the higher tails. This allows us to take a good "guess" given what we know what values are more likely and encode this guess in our tools. It is more complex, and to be honest, we only use it after exhausting a straight range estimate and proving an input factor makes a material difference in the forecast. Out of ten inputs there might be two that fall into this category.

Level 4 forecasts use historical data. Historical data is a mix of a range estimate (it has a natural lowest and highest value), and probability for each value. Some values occur more often than others, and when we use it for forecasting, those values will be given more weight. This naturally means our forecast match the historical nature of the system giving reliable results. Our spreadsheet tools use this technique when estimates are set to "Historical data" ([download it here](https://github.com/FocusedObjective/FocusedObjective.Resources/raw/master/Spreadsheets/Throughput%20Forecaster.xlsx)).

### Level 5 - Simulation + Probabilistic Forecasting

Level 5 forecasts model the interactions of a process through simulation. This is the domain of our KanbanSim and ScrumSim tool ([see Downloads to download this tool](http://focusedobjective.com/kanbansim_scrumsim/downloads/)). It allows you to make a simple or as complex a model as you need that exhibits the same response as your organizational process. This not only helps understand the system and forecast in detail, it allows you to perform "what-if" experiments to detect what factors and process setup/assumptions give a desirable result. This what-if analysis is often called Sensitivity Analysis, and we use it to answer complex process questions with reliable results. But, it takes some work, and if your process is changing, or inconsistent, or unstable - then this may not be the best investment in time. We can help advise if we think you need this level of forecasting.

### Which one should you use?

Avoid any regression based forecasting. With our free spreadsheets and tools there is little upside in doing it the "traditional" way and risking the Flaw of Averages causing you to make a judgment error.

A probabilistic technique at level 2 if you have no historic data, or level 4 if you do is our advice. All of our spreadsheet tools allow you to use either range estimates or data for the forecast inputs. Given its free, we can't break down the barrier to entry any more than we have - [download it here](https://github.com/FocusedObjective/FocusedObjective.Resources/raw/master/Spreadsheets/Throughput%20Forecaster.xlsx).

Use our simulator if you have complex questions, and we are here to help you make that step when you need it.

Troy.
