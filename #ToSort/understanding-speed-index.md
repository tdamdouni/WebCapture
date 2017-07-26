# Understanding Speed Index

_Captured: 2017-05-09 at 01:23 from [dzone.com](https://dzone.com/articles/understanding-speed-index?edition=298022&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-08)_

Discover 50 of the latest mobile performance statistics with the [Ultimate Guide to Digital Experience Monitoring](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE).

There's a lot of buzz around the speed index metric, but what exactly is this metric and how is it calculated? Even more so, why do we need a new metric when there are so many already on the plate? This article gives you detailed answers to these questions.

## **What Is Speed Index?**

User expectations have changed drastically, web pages are expected to load faster with all elements rendering as soon as possible, and user frustration increases if the visual content of the page is slow to load.

There are several metrics used to measure user experience, but do these give us a clear enough picture? Not really. For example, render start indicates when the page started painting, but this could mean it loaded a white background, a random object, or just a dot on the page; the user, however, may still be looking at a blank page. The document complete metric, which flags the onLoad event, may not be important from an end user's perspective as it considers below-the-fold requests as well; there could be instances where the Document complete is triggered even when the page is blank.

Speed Index is an abstract score that was introduced to overcome the limitations of the current set of metrics. It measures user experience and unlike render start or document complete, it is not a timing metric; therefore, the smaller the score, the better it is. Speed index takes into account the visual completeness of the page above-the-fold. It does a much better job of measuring the perceived performance of a page, but does this mean other metrics are irrelevant? This is debatable. Instead, the choice of a metric depends on the scenario and the nature of the website being analyzed.

### **How Relevant Is Speed Index?**

Speed index will let you know if the visible content is loading quickly or not. The lower the score, the better is the user experience, and vice versa. The speed index score indicates whether you need to optimize your page or not. To maintain a good score, there are two critical aspects that you should look at: [optimizing content efficiency](http://blog.catchpoint.com/2016/08/31/web-performance-101-page-size-optimization/) and [optimizing the critical rendering path](http://blog.catchpoint.com/2017/01/27/critical-render-path/).

![](http://blog.catchpoint.com/wp-content/uploads/2017/04/rendering.png)

Web applications continue to grow in terms of functionality, scope, and usability; hundreds of resources make up these applications and fetching each resource adds to the page load time. Maintaining performance is possible only when the resources and content that make up the page are optimized. Speed index plays a critical role in monitoring the performance of visible content.

### _**How Is It Calculated?**_

Speed index lets you measure how quickly a page's content is visible. However, it can be a little tricky to understand what it means and what factors contribute to the score.

Speed index uses film strips to calculate the score, each frame is scored for visual completeness above the fold; the score is 0% for a blank screen and 100% for a visually complete screen. The score for each frame is calculated using this formula:
    
    
    interval time*(1 – visual complete %/100)

The process is repeated for every frame and the cumulative of all the scores gives you the speed index of that page.

Let's take an example:

![](http://blog.catchpoint.com/wp-content/uploads/2017/04/img1.png)

![](http://blog.catchpoint.com/wp-content/uploads/2017/04/ind1.png)

> _Adding all of the scores gives the speed index score:_

Here is another example:

![](http://blog.catchpoint.com/wp-content/uploads/2017/04/img2.png)

![](http://blog.catchpoint.com/wp-content/uploads/2017/04/ind2.png)

> _Let's add up the score:_

From a performance point of view, the lower the score the better it is. There is no defined benchmark for speed index, however, a score of <1000 is considered good. User experience is better if above-the-fold content is displayed faster, and this is what speed index determines.

## **Measuring Speed Index Using Catchpoint**

To check speed index, you will need to enable the **_Capture Filmstrip_** option under the **Advanced Settings** of a test. It is displayed along with other metrics in the charts, and you can also view it in the waterfall graphs. Here are a few examples that illustrate how pages that load the visual content faster have a better speed index score.

Example 1:

![](http://blog.catchpoint.com/wp-content/uploads/2017/04/ex1-1024x399.png)

In the above example, the page has a good speed index score of 1260. If you look at the film strip, the interval is of 500ms, and from the second frame, the visual content is visible, which is about 1 second. Frame three has almost all the content loaded. From a user's point of view, we have engaged them from the very first second due to the fact that the page is optimized.

Example 2:

![](http://blog.catchpoint.com/wp-content/uploads/2017/04/ex2-1024x417.png)

In the above image, the visual is visible in the third frame. The first two frames are blank, which is why the speed index score of 1741 is higher than the first example. The user views content at 1.6 seconds, unlike the first example, where the user viewed the content within a second.

Example 3:

![](http://blog.catchpoint.com/wp-content/uploads/2017/04/ex3-1024x411.png)

Based on the final example above, we are able to understand what is happening. The first two frames are blank and in the third frame visual content starts to load. However, the completeness is less compared to the other two images in the same frame. The visual content continues to load in the fourth frame, but it's not complete until the fifth frame. This means that the user needs to wait for 1.6 seconds to see something on the page, and another 2.8 seconds to view the complete visual content.

In all of the examples, the render start is triggered before the user views anything on the page. In the second example, the render start happens at 1195ms and the visible content starts to load at 1604ms. In the third example, the render start happens at 1296ms and the visible content starts to load at 1597ms. This is the uniqueness of speed index. With a highly unoptimized website, the difference could be extremely high, with render start happening quickly but the visible content loads quite late. You need these insights to optimize your websites.

## **Limitations of Speed Index**

When running transaction tests for dynamic sites or single page applications that use ajax, the score is always good in the steps that follow once the page is opened. This is because the page does not refresh after it is loaded. Pages featuring carousels that rotate automatically may be penalized because they continue to change even after the page load is completed.

## **Summary**

Speed index indicates the visual completeness of the page; however, it does not indicate if the content was critical or non-critical for the user. As such, it should not be a replacement for other metrics and should be considered a rather useful and much-needed addition to the list of metrics. You will still need to look at render start and document complete to understand the overall performance. Speed index gives you a different perspective of the user experience that your site delivers.

[Is your APM strategy broken?](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) This [ebook](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) explores the latest in Gartner research to help you learn how to [close the end-user experience gap in APM](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE).
