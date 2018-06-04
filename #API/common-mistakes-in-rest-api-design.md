# Common Mistakes in REST API Design

_Captured: 2018-03-21 at 15:20 from [dzone.com](https://dzone.com/articles/common-mistakes-in-rest-api-design?edition=367211&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-03-21)_

I was thinking API design is pretty easy and intuitive. But actually, it's not.

Just like the famous difficulty of naming things (functions, variables, modules), designing a clean and just-enough API takes experience and effort.

![](https://raw.githubusercontent.com/DennyZhang/images/master/design/basic_rest_example.png)

Good Examples/Resources:

Common Mistakes

  * In GET requests, add parameters inside the body, instead of in a URL.
  * Use lengthy names, while we have better choices
  * Define our own error code and error message. Try to reuse the HTTP protocol first. 

  * Better use a dash(-), instead of an underline("_").

  * Missing API protocol versions in the URL. It would be hard to manage, when we have API breaking changes. 

  * NO authentication to protect our system from malicious requests. 

See example from[ GitHub](https://developer.github.com/v3/).

  * Unnecessary or useless parameters in the BODY of request or response.
  * Make sure the APIs are logically correct.
  * Remember to support pagination, if too much data isinvolved.
  * The response is a JSON file with an embedded list. Make sure it's valid JSON.

  * Sample: `startMachine`
