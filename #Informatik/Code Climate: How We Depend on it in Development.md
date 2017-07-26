# Code Climate: How We Depend on it in Development

_Captured: 2016-03-25 at 00:31 from [medium.com](https://medium.com/@jetruby/code-climate-how-we-depend-on-it-in-development-5e008237938c#.fcc2pfxn6)_

Code climate is aimed at helping a team to write pure code. It provides static and automatized analysis for Ruby on Rails, JavaScript, PHP (beta) or Python (beta) code, and after that gives you easy-to-read and practical results.

#### How does it work?

  1. Push commit into repository (Git repositories are supported).
  2. Code Climate automatically clones and analyses every commit.
  3. After that you are enabled to trace feed changes, smart email alerts and notifications integration

#### Hooks

Code Climate gets information about new events in the repository with the help of hooks, that are sticked on a git server.

They may be of 2 types:

  * webhooks -- which are git server requests for Code Climate endpoint url after commit push into default branch is done;
  * service hooks -- used for Github only. It is a more extended notifications set for Code Climate: information about new branch pushing, PR opening, etc.

In case if a repository doesn't have any of the hooks, but it is connected to Code Climate, one can turn changes auto polling on carried out by Code Climate itself.

#### Github example

1\. Get API token from a profile in Code Climate

![](https://cdn-images-2.medium.com/max/800/1*nIpvUPjQfIVgsaA84Czdhw.png)

2\. Add the repository ID from the Code Climate feed

![](https://cdn-images-2.medium.com/max/800/1*bN5j8GVcqp4copUzLHGVxg.png)

3\. Create a webhook on Github (administrator permission is in the repository)

![](https://cdn-images-2.medium.com/max/800/1*6OxSydSBTLE1_ZkPikn1cQ.png)

### ABS Metrics

It is a commonly used method for the software volume measurement. This index is one of the means, that Code Climate uses to estimate the code complexity -- application's technical debt accumulation feature.

The higher the value the more difficult the code is considered for reading, testing and support.

It is composed of:

  * assignments number in the method;
  * outputs number from the code execution procedural flow;
  * conditional branches number if/elses, cases, try/catches, boolean tests, less than or equal to evaluations.

Special for Ruby a modified Flog gem is used to:

  * estimate meta code;
  * analyse duplicating code parts.

### Code quality estimation (GPA)

GPA (grade point average) -- is a statistics system used to estimate a student's performance. It displays an overall code level on the basis of the average weighted ABC metrics of all existing classes and app methods. Wherein every separate issue has its own weight, allowing us to calculate the value of different kinds of issues (e.g. duplication, method's complexity). It is displayed on the app's dashboard and can be placed as a widget into Github.

![](https://cdn-images-2.medium.com/max/800/1*5Qb0QyXlYTATzb7KFEvIcQ.png)

### а Code Climate as a CI

Code climate can be integrated into some of the CI products: Semaphore, Solano Labs, Travis C., Jenkins. It aggregates text coverage data and displays the current project build status. Code Climate revaluates ABC code values depending on the CI-server report. Hence even a well thought-out code can get a yellow flag, meaning it hasn't been tested enough.
