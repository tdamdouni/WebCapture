# The Real Cost of Slow Time vs Downtime [SLIDES]

_Captured: 2017-05-08 at 16:39 from [www.webperformancetoday.com](http://www.webperformancetoday.com/2014/11/12/real-cost-slow-time-vs-downtime-slides/?utm_content=buffer5c563&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Last week, I had the pleasure of being invited to speak at the CMG's annual **[Performance & Capacity Conference**](http://www.cmg.org/conferences/performance-capacity-2014/). One of my sessions was a presentation of Radware's research into **[mobile web stress**](http://www.slideshare.net/Radware/radware-velocity-conferencemobilestresstammyeverts). The other was a brand-new talk that I'm frankly kind of surprised I've never done before: a shallow dive into the topic of measuring the financial impact of slow performance versus the financial impact of outages.

Here are my slides. More discussion below.

![](https://image.slidesharecdn.com/radwarecmg2014tammy-evertsslowtime-vs-downtime-141105090117-conversion-gate02/95/the-real-cost-of-slow-time-vs-downtime-1-638.jpg?cb=1415179166)

If you run an ecommerce site, it's relatively easy to measure the cost of an outage:

![Slow time versus downtime](http://3vavpsbeqbk19ao0rfgkqm17sj.wpengine.netdna-cdn.com/wp-content/uploads/2014/11/slowtime-downtime-losses.jpg)

Sure, there's also the cost of disaster recovery and other behind-the-scenes numbers, but the fact remains that it's comparatively easy to paint a compelling picture of the damage that downtime has on your organization. It can be much more challenging to paint a compelling picture of the damage wrought by sub-par performance. In my talk, I outlined a couple of ways to paint this picture:

  1. **Identify your cut-off performance threshold.** According to a survey of 300+ companies by TRAC Research, [4.4 seconds is the average delay in response time when business performance begins to decline](http://www.slideshare.net/KenGodskind/alertsitetrac). This is a good number to use if you're not sure about the specific threshold for your business.
  2. **Measure the Time to Interact (or comparable performance metric) for pages in flows for typical use cases on your site.** Time to Interact (TTI) is the moment that a page's key content renders and becomes interactive. If you use a measurement tool like [WebPagetest](http://www.webpagetest.org/), then the Speed Index score correlates pretty closely (in milliseconds) to Time to Interact.
  3. **Calculate the difference between the performance threshold and the actual TTI for each page.** For example, if the threshold is 4.4 seconds, and the actual TTI is 5.6 seconds, then the difference is 2.2 seconds.
  4. **Pick a business metric (e.g. cart size, conversions, page views, bounce rate, customer satisfaction).** Each of these KPIs (key performance indicators) has a solid case study that proves a correlation between it and performance. Depending on which case study you look at, a 1-second delay correlates to: 
    * 2.1% decrease in cart size
    * 3.5-7% decrease in conversions
    * 9-11% decrease in page views
    * 8% decrease in bounce rate
    * 16% decrease in customer satisfaction
  5. **Calculate losses.** For example, to measure the estimated impact on conversions, take the 2.2 second slowdown from point 3 and multiply it by 3.5. By this calculation, a 2.2 slowdown equals a 7.7% conversion rate hit.

This formula is predicated on understanding the customer lifetime value (CLV) of people who make purchases on your site. **CLV is the total amount of dollars flowing from a customer over their entire relationship with your business. This metric is one of the best predictors of retail success, yet it's rarely discussed.** CLV is usually calculated over a fixed period of time. (As a simplified example, a retailer might calculate their CLV using a six-year window. A customer's total spend over the previous three years is their projected spend for the next three years. The total of past and projected is their CLV.)

When considering the relationship between CLV and performance, it's important to know that, when it comes to abandonment, people react very differently to sites that are down versus sites that are slow. According to [this survey](http://www.uniteu.com/assets/images/Akamai_eRetail_Success_Whitepaper.pdf), 9% of users will permanently abandon a site that they try to visit during an outage. But a staggering 28% of users will permanently abandon a site that is unacceptably slow.

  1. **Identify your site's performance poverty line.** Or use our findings that, **[for a typical ecommerce site, the performance poverty line is around 8 seconds**](http://blog.radware.com/applicationdelivery/applicationaccelerationoptimization/2013/06/web-performance-poverty-line/). (Performance poverty line = the plateau at which your website's load time ceases to matter because you've hit close to rock bottom in terms of business metrics.)
  2. **Identify percentage of converting traffic that experiences speeds slower than your poverty line threshold.**
  3. **Identify current CLV for those customers' (individual or median).**
  4. **Using the stat that 28% of those customers will permanently abandon pages that are unacceptably slow, identify the lost CLV.**

Using this formula, here's a sample CLV loss scenario:

_If the total value of your median customer spend for the past three years is $1000, then the predicted future value is $1000, making the median CLV $2000. Let's say that your site has a current converting user base of 10,000, and 10% (1000) of those converting users experiences a TTI slower than your performance poverty line of 8 seconds. If 28% (280) of those customers won't return, then your net CLV loss is $280,000._

I'm always on the hunt for other formulas and proxies people have used to measure the impact of better/worse performance in their organization. If you have any to share, please let me know!
