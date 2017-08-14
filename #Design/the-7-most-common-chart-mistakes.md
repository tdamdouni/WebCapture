# The 7 Most Common Chart Mistakes

_Captured: 2017-08-01 at 07:17 from [dzone.com](https://dzone.com/articles/the-7-most-common-chart-mistakes?edition=311403&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-07-31)_

Get gorgeous, [multi-touch charts](https://dzone.com/go?i=228229&u=http%3A%2F%2Fbit.ly%2Fiosdzone) for your iOS application with just a few lines of code.

As humans, we like to use patterns in our daily lives, as they allow us to use less energy while processing data and making decisions in a short period of time. However, we are easily influenced by the way patterns are represented. Since many content providers depend heavily on charts to represent data and find patterns, they should be aware that charts could affect the perception of their audience.

To raise awareness about this issue, I summarize the most common chart mistakes in this article.

## 1\. Start With the Origin

![Image title](https://dzone.com/storage/temp/6024073-chart-2.png)

![Image title](https://dzone.com/storage/temp/6024074-chart-3.png)

View interactive chart [here](https://www.highcharts.com/blog/post/182-7-most-common-chart-mistakes/)

Chart A1 shows a graph increasing in the beginning but decreasing toward the end. This chart could be interpreted as a good sign if it describes the propagation of a disease over time, or a warning if it represents a company's profit.

Chart A1, however, doesn't start from zero, it starts from the smallest value of the Y axis. The interpretation of the data could, therefore, be different if the whole chart is presented (see chart B1), your audience will then be less enthusiastic about the disease spreading and it will not stress about their company's profit.

In that case, a zoom capability of an interactive chart is highly recommended, as it allows the audience to check the chart in different perspectives (see chart B1, click and drag to zoom).

Good practice: Start the chart from the origin, and add a zoom capability if it is possible.

## 2\. Shapes

![Image title](https://dzone.com/storage/temp/6024085-chart.png)

![Image title](https://dzone.com/storage/temp/6024110-chart-4.png)

View interactive chart [here](https://www.highcharts.com/blog/post/182-7-most-common-chart-mistakes/)

The shape and size of elements are perceived in relation to each other. Chart A2 creates the illusion that the element at the top is the smallest one due to its position on the top of a cone. Your audience has to read the value of each element to be able to interpret the data, whereas chart B2 shows the values of each element without any confusion.

Good practice: avoid using shapes, unless you have a good reason.

## 3\. Maps
    
    
                data: [{name:"Non Aboriginal population",y:95}, 
    
    
                       {name:"Aboriginal population",y:5, color:'green'}],

![Image title](https://dzone.com/storage/temp/6024118-chart-6.png)

View interactive chart [here](https://www.highcharts.com/blog/post/182-7-most-common-chart-mistakes/)

The green color on the map shows the parts of Canada where aboriginal people are demographically the majority, the green part represents 34.5% of the national area.

The map could easily deceive your audience when it comes to the demographic percentage of aboriginal people, as your audience could guess the number of the demographic percentage based only on the green area, i.e. the Aboriginal population owns the biggest territory so their number is significant in Canada. The circular chart, in the upper corner, however, shows both the green area and the demographic number leaving no room, for any misinterpretation.

Good practice: Always support your maps with information to prevent your audience from assuming the missing information.

## 4\. Cumulative Chart

![Image title](https://dzone.com/storage/temp/6024136-chart-7.png)

![Image title](https://dzone.com/storage/temp/6024139-chart-8.png)

View interactive chart [here](https://www.highcharts.com/blog/post/182-7-most-common-chart-mistakes/)

Cumulative charts are the most confusing charts since it is very easy to misinterpret the data and miss details. On chart A4, it is difficult to see the low values on May 15 and July 15; however, this is not the case on chart B4 where there is no data accumulation. If you must use a cumulative chart, consider to also show a non-cumulative chart for the same data.

Good practice: for more clarity, use data in a cumulative and a non-cumulative chart.

## 5\. Conventions

![Image title](https://dzone.com/storage/temp/6024142-chart-9.png)

![Image title](https://dzone.com/storage/temp/6024144-chart-10.png)

View interactive chart [here](https://www.highcharts.com/blog/post/182-7-most-common-chart-mistakes/).

Conventions are different from one culture to another. The following charts have the same data but target different audiences. In North America, I will go with chart A5, because reading from left to right is the convention; however, I will use chart B5 for the Middle East, as people in that area read from right to left.

Good practice: Know your audience to set up more effective charts.

## 6\. Illusion of 3D Charts

![Image title](https://dzone.com/storage/temp/6024153-chart-11.png)

![Image title](https://dzone.com/storage/temp/6024162-chart-12.png)

View interactive chart [here](https://www.highcharts.com/blog/post/182-7-most-common-chart-mistakes/).

Chart A6 makes it difficult to see the difference between the values on Oct 14, Jan 15 and Apr 15, due to the curvature of the 3D top part of the column. I have to admit that even with 2D charts (see chart B6), the comparison of the three values is tricky, as they are close to each other numerically. Nevertheless, it is much better than the 3D chart especially when the values are exposed on the top of the columns.

Good practice: 3D is cool, but 2D is easier to understand.

## 7\. Too Much Data in One Chart

![Image title](https://dzone.com/storage/temp/6024170-chart-13.png)

View interactive chart [here](https://www.highcharts.com/blog/post/182-7-most-common-chart-mistakes/).

This chart shows that too much information kills information. Most people start to make irrational decisions when presented with too much information at the same time.

Good practice: reduce the amount of data in your chart as much as possible.

## Conclusion

Charts are part of our daily lives, and they have a great influence on our decision-making process. To avoid misunderstandings and wrong assumptions, be sure to show the necessary data, to use the right shapes, and to know your audience.

.Net developers: use [HIghcards](https://dzone.com/go?i=228230&u=http%3A%2F%2Fbit.ly%2Fdzone-dotnet), the industry's leading interactive charting library, without writing a single line of JavaScript.
