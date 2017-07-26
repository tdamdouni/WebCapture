# What I learned introducing a domain-specific language for configurable traceability analysis

_Captured: 2017-04-14 at 00:05 from [blogs.itemis.com](https://blogs.itemis.com/en/what-i-learned-introducing-a-domain-specific-language-for-configurable-traceability-analysis?utm_source=hs_email&utm_medium=email&utm_content=50499857&_hsenc=p2ANqtz-8HQmR3MY-8ZjARkiXhb3ab_NNPAJSNEjTuO3Nw7UTDuyEivMv3MOfK1nkCFG4XBIBiSPYTK6JPLB64MXg7AzDJ12PPYV_HR1OQPaFe3r0SsK7S2Vo&_hsmi=50498919)_

At this years [Modelsward conference](https://modelsward.org/) I had the opportunity to present a paper about "A Domain-specific Language for Configurable Traceability Analysis" that was written in close collaboration with Prof. Dr. Kuchen and Christoph Rieger from [[ERCIS]](https://www.ercis.org/) of the University of Muenster. The Modelsward conference provides a platform for practioners and academics to present their research and development activities in model-driven engineering. Since the paper contributes a domain-specific language build with [Xtext](https://www.itemis.com/en/xtext/) that is integrated into [Yakindu Traceability](https://www.itemis.com/en/yakindu/traceability/), it perfectly fits the purpose of the conference.

## The challenge of traceability in practice

Many companies create traceability information models (TIM) for their software development activities either because they are obligated by regulations or because it is prescribed by process maturity models. However, there is a lack of support for the analysis of these models. Therefore, inherent information that could benefit project managers in terms of tracking project progress and quality, developers in terms of easing maintanance activities, and quality engineers in terms of analysing test coverage remains unused.

On the one hand, research has been done on querying traceability information models, but the raw data can not be aggregated further. On the other hand, research has been done defining relevant metrics for traceability information models, but the data collection process is not configurable. The introduced Traceability Analysis Language (TAL) closes this gap by introducing domain-specific language to query, aggregate and check traceability information that is well integrated into Yakindu Traceability.

## Traceability Analysis Language

The capabilities of the TAL will be exemplified by defining a simple query for the following traceability information model.

![TIM.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Xtext/TIM.png?t=1492099761217&width=216&height=198&name=TIM.png)

The TIM is an instance of the so called traceability configuration model both are created using Yakindu Traceability. This configuration model consist of five different traceable artifact types _User Documentation, Requirement, Technical Specification, Java Class, and JUnit Test_ that are connected by different trace link types. We take this TIM as basis for computing the metric number of related requirements (NRR). The NRR metric can be used to evaluate the complexity of each requirement, since it has been shown that with every relation to another requirement, which can be direct or transitive, the complexity of the originated requirement increases. In addition, we will check that the metrics values is smaller than a given threshold.

![Analysis.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Xtext/Analysis.png?t=1492099761217&width=362&height=108&name=Analysis.png)

The TAL expression above consists of three main parts: first, the query part introduced by the keyword _result_. Second, the metric part that aggregates the raw data returned by the query introduced by the keyword _metric_. Finally, the keyword _rule_ is the beginning of a check that will be performed on the aggregated data.

The query statement is given a name _relatedRequirements_ before in the next line the function _tracesFromTo_ is called. The function encapsulates the graph traversal making the analysis expression very resilient to changes in the traceability configuration model. In addition, the function is parameterized with artifacts defined in that configuration model, so that queries can be written using well known terms. The last part of the query expression defines the tabular structure of the resulting raw data that in this case consist of one column containing the name of the start artifact and one column containing the name of the target artifact. The metric statement is also given a name before the result of the _cnt_ (count) function is assigned after the equal sign. The count function takes a column of the query result as input and counts all values with the same content. Finally, the rule statements defining a rule named _highNRR_ is defined that will produce a warning message if the NRR metrics value is greater than three. In addition, to checking metric results the rule expressions can also directly work with query results.

![SamplePath.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Xtext/SamplePath.png?t=1492099761217&width=220&height=199&name=SamplePath.png)

For the given example the figure above shows one sample path starting from _RQ1_ over _TS2_ and _JC1_ and _TC1_ to _RQ2_. This path shows that _RQ1_ has a relation to _RQ2_ that can be created since trace links are bidirectional navigable and we are looking for direct and transitive relations. In addition, the figure also contains the second path that starts with the same four traceable artifacts and than goes through _TS4_ to _RQ3_. Thereby, the number of related requirements for _RQ1_ is 2. The following table shows the result of computing the metric for each requiremetn in the given graph.

![NRR.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Xtext/NRR.png?t=1492099761217&width=154&height=108&name=NRR.png)

Evaluating the rule expression in this case shows that all metric values are in the expected range, so that no warning message needs to be produced.

## Conclusion

The introduced approach closes the gap between information retrieval, metrics definition, and result evaluation, thus forming a solid foundation for project- or company-specific metrics. Since the analysis language is based on a highly configurable TIM, it allows for a large variety of traceable artifacts, including formerly unused documents such as documentation, test results or even tickets from collaboration tools. It is well integrated into Yakindu Traceability using Xtext and the Eclipse Modeling Framework. Features such as live validation and error markers detect broken or outdated expressions early and ensure a rich user experience.

All in all, the Modelsward conference was an interesting and well organized convention for people working in the area of model-driven and language engineering. Talking to other academics and practioners has once again ensured me that model-driven development has a bright future in a variety of areas ranging from embbeded systems over business software to even non software developing areas like catastrophy management. The Traceability Analysis Language is another example for a DSL that benefits not only developers, but also requirement engineers, project managers, and quality engineers.
