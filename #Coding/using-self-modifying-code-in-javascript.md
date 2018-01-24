# Using Self-Modifying Code in JavaScript

_Captured: 2017-11-29 at 18:26 from [dzone.com](https://dzone.com/articles/using-self-modifying-code-in-javascript?edition=339091&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202017-11-29)_

Should you build your own web experimentation solution? [Download this whitepaper](https://dzone.com/go?i=250341&u=https%3A%2F%2Fwww.optimizely.com%2Fresources%2Fbuild-vs-buy%2F%3Futm_medium%3Dpaid%26utm_source%3Ddzone%26utm_campaign%3D2017-08-dzone-fs-promo%26utm_content%3Dtext-link) by Optimizely to find out.

When I started working in Information Technology (over 25 years ago), I met a guy named Dave who had been at the large insurance company (where I accepted employment) for a few years. Dave's job focused on program code supporting a core product called "Individual Life Insurance." If you bought a personal life insurance policy from an agent representing this company, Dave's code was running in the background to support the needs of that business line.

One of our initial conversations was regarding a task he had recently completed. That task was to remove all the self-modifying code that was running for years on the mainframe system which handled the individual life insurance family of products. For those who are not aware, self-modifying code is defined by [Wikipedia](https://en.wikipedia.org/wiki/Self-modifying_code) as:

> Self-modifying code is code that alters its own instructions while it is executing - usually to reduce the instruction path length and improve performance or simply to reduce otherwise repetitively similar code, thus simplifying maintenance. - Wikipedia 

In the case Dave was removing, self-modifying code was used to alter the program logic at run-time to maximize the efficiency of the available memory on the mainframe. I believe I remember my boss telling me they had only 8k of RAM on the mainframe when it was purchased, years before I cared about computer technology.

So, for this Thanksgiving holiday, I thought I would provide an example of using self-modifying code using the JavaScript language.

### JavaScript Example

Thursday, November 23, 2017, is the day when the United States celebrates [Thanksgiving](https://en.wikipedia.org/wiki/Thanksgiving_\(United_States\)). A majority of corporations recognize this as a holiday, providing employees the opportunity to be thankful for one's blessings. With this in mind, the following JavaScript can be created:

When the `selfModifyingCode` function is initialized, the value is equal to the following function:

When the function is called via the `selfModifyingCode()` command, the two date variables (turkeyDay and date) are set and then evaluated to see if the date versions are equal.

If the two dates match (which means today is Thanksgiving), the `selfModifyingCode` function is re-written to be as noted below:

If the two dates do not match (today is not Thanksgiving), the `selfModifyingCode` function is re-written to be as follows:

As a result, when program logic calls the ` selfModifyingCode() ` function, the results will be different - depending on the date in which the program is called.

### Conclusion

Self-modifying code can be an effective way to handle logic that needs to be evaluated at run-time. However, it is recommended that use is restricted to only cases where it makes sense.

Back when my former employer bought their mainframe, they had to use self-modifying code to maximize the amount of memory available for processing requests. Once the memory issue was resolved, my friend Dave was assigned the task to remove this logic, because it was difficult to support and maintain.

The same would be true with the simple example above. There are much better ways to handle the end-result that I provided in the examples above. Certainly, it would be confusing for someone to support my example, where every day of the year (except one), the function code within the `selfModifyingCode()` function is the same.

Have a really great day!

Implementing an Experimentation Solution: [Choosing whether to build or buy?](https://dzone.com/go?i=250361&u=https%3A%2F%2Fwww.optimizely.com%2Fresources%2Fbuild-vs-buy%2F%3Futm_medium%3Dpaid%26utm_source%3Ddzone%26utm_campaign%3D2017-08-dzone-fs-promo%26utm_content%3Dtext-link)
