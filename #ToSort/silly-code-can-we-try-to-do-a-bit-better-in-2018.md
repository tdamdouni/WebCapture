# Silly Code: Can We Try to Do a Bit Better in 2018?

_Captured: 2018-01-11 at 09:57 from [dzone.com](https://dzone.com/articles/silly-code-can-we-try-to-do-a-bit-better-in-2018?edition=352091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-10)_

[Learn how](https://dzone.com/go?i=268439&u=http%3A%2F%2Falm.parasoft.com%2Flaser-focus-your-testing-with-change-based-testing%3Futm_campaign%3DImpact%252520of%252520Change%2525202018%26utm_source%3DDZone%26utm_medium%3DDZone%252520Java%252520Partner%252520Resources) to stop testing everything every sprint and only test the code you've changed. Brought to you by Parasoft.

The new year has officially started and around the world, individuals are working to meet goals and resolutions that were made in the late stages of 2017. If I could cast a wish across our entire software engineering industry, I would ask if we could maybe try a little harder to avoid writing silly code in 2018.

For a majority of the year, I returned to the role of a consultant, but even in those months where I was a corporate employee, I still encountered what I would call "silly code."

To me, silly code is something that an engineer or developer pushed into production with what appears to be little thought on the consequences. In each example below, the result is not meant to reflect against the author's programming skills, but rather to point out a lack of consideration over the long-term impact on the decisions that were made to allow this logic entire the code stream.

In every case below, the original code has been modified to protect the silliness of the original author.

## Example #1: Dude, That Method Name Is Way Too Long

I understand that method names should be descriptive in order to provide a clear definition of what is being accomplished, but consider this example:

In this case, the method was used to check the Widget (fictional of course) service to determine if a customer, account, and contact record existed for the provided customerNumber. If found, an object which represented provided an established hierarchy will be returned.

The method name is certainly one of the longest I remember seeing and reading the references to this object, including the unit tests, made me laugh out loud seeing how long the method name was ... over and over again.

> _Rule of thumb: Keep your method names descriptive, but shorter rather than longer._

## Example #2: Does 1 Ever Equal 2?

I was assigned a task to work on a defect that was occurring in a web-based application. Another individual expressed to me that the problem area is likely between a range of line numbers in the code. Since I was billing the client by the hour, I followed their advice and reviewed the code at the line numbers suggested. Everything seemed to make sense in the code that I was reviewing. I looked at the objects provided in the code with an understanding of their purpose and felt like the code was running correctly.

Before debugging, I decided to scan the entire class, just to make sure.

Aside from the long method having code that spanned multiple screens, which I like to personally avoid as much as possible, I noticed there was a condition that was a cause of concern:

There it was, the condition to check to see if the numeric value of one is equal to the numeric value of two. Decades ago, before source control, I used to see this occasionally -- when the developer did not want to lose the code while making sure it would not execute. I never understood why comments were not used, but maybe they did not exist in the language the individual initially utilized to program.

The `if (1 == 2) {` logic made an appearance in the code I was reviewing. Clearly, it was the reason why the code I was analyzing was not actually being evaluated. I am not sure how this code made it through code review. My only hope is that it was checked in without a code review.

> _Rule of thumb: Leverage the source control system to remove program code that is no longer required._

## Example #3: Hard-Coding in a Sea of Constants

While working on a project, I came across code similar to what is listed below:

The original code was more complex, but the item to note was that the author simply hard-coded an additional evaluation criterion to the else if logic, instead of using a constant. Initially I thought, "Maybe the developer was in a hurry and did not take the time to add a new constant."

When I attempted to add the new `TYPE.CUSTOMER` constant, I realized it was created at the same time the `ACCOUNT` and `CONTACT` constants were created.

> _Rule of thumb: Follow the established pattern, even if it means taking a couple extra steps to complete the task._

## Example #4: The Empty Exception

The use of `try/catch` blocks is not only required at times, but can assist the developer in handling situations that do not adhere to the expected path. Earlier this year, I noticed the following code:

Basically, whenever any type of exception occurred in the code, it was basically ignored. There wasn't a `// TODO` in the code or even a comment on why nothing was added to the exception block.

When using exceptions, the developer should make sure to handle the condition being caught. Otherwise, the cause of the exception simply disappears and the underlying application code or support staff have no idea that an issue has occurred.

> _Rule of thumb: Exceptions should be caught and handled properly._

## Example #5: Querying the World When You Only Need a Small Village

When introducing new program code as a part of a feature, I asked the team lead how I would gain access to the data I was developing. I noticed that I was going to use the same API call that was used in several other aspects of the application. When I called the API and reviewed the source data, I noticed the size of the payload that was returned. It was huge!

Not only was the service returning the data I required, it was also returning other aspects of the record. I felt like I was getting 80% of the data model returned to me, including child references that were not needed, from that one single API call. In essence, I felt like I was querying the world instead of fetching a small village of data that was required to complete the feature that was assigned to me.

What was worse is that the expectation is that I would POST this payload back to the API, even if I only modified a few of the objects in the payload. When I viewed this design from a production-support perspective, I could not imagine the impact of performance and save conflicts that could occur with this model once deployed to a large user base.

> _Rule of thumb: Try to keep your payloads focused on meeting the needs of functionality being addressed._

## Conclusion

With the year 2018 officially underway, one solid resolution to consider is to avoid adding silly code into the code stream of your project. Bonus points to find/fix any silly code along the way for code that is going to be validated and tested as part of your development effort.

Have a really great day!

[Get the top tips](https://dzone.com/go?i=268440&u=http%3A%2F%2Falm.parasoft.com%2Fget-unit-testing-done-right%3Futm_campaign%3DUTA%2525202018%26utm_source%3DDZone%26utm_medium%3DDZone%252520Java%252520Partner%252520Resources) for Java developers and best practices to overcome common challenges. Brought to you by Parasoft.
