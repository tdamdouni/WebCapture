# Removing the Unfairness From AI

_Captured: 2017-05-14 at 17:34 from [dzone.com](https://dzone.com/articles/removing-the-unfairness-from-ai?edition=298099&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-13)_

Need to build an application around your data? [Learn more](https://dzone.com/go?i=200129&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) about dataflow programming for rapid development and greater creativity.

AI has a tremendous amount of potential to improve our decision-making, but it also has the potential to bake in the numerous biases that inflict our own decision-making processes. With AI making increasingly sensitive and decisive decisions about crucial matters, it is paramount that the biases of human developers aren't coded into the algorithms that underpin our AI.

As such, it's perhaps not surprising that a number of research projects have emerged to try and rectify matters. One of these, led by researchers from Google, was [published](https://arxiv.org/abs/1610.02413) last Autumn and aimed to detect discrimination in algorithms.

## Analyzing Fairness

The paper suggests that biases can be uncovered simply by looking at the data that is fed into the algorithm and then comparing that with the decisions that come out the other end. Knowledge of the algorithm itself is therefore not required.

> "Our criteria does not look at the innards of the learning algorithm," the authors say. "It just looks at the predictions it makes."

It's an approach known as equality of opportunity in supervised learning and works on the principle that an algorithm should not reveal anything about an individual's race or gender beyond what is in the data itself.

Whilst the approach is interesting, it has a number of flaws. For instance, transparency around how an algorithm works is seen as fundamental to public trust in AI, especially when it begins to take on more important, and sensitive, decision making.

The approach also fails to take a contextual exploration of why biases and discrimination occur in the first place, which is something a team of researchers from the Turing Institute aimed to overcome in a recently published [paper](https://arxiv.org/pdf/1703.06856.pdf).

## The Context of Discrimination

The research used causal inference to analyze fairness in an approach they refer to as counterfactual fairness. The authors argue that any assessment mechanism must examine the underlying factors that cause unfairness in data.

> "One central fact of statistics is that 'correlation' is not 'causation.' For example, there is a correlation between number of Nobel prizes won by people in a given country and the level of [chocolate consumption](https://blogs.scientificamerican.com/the-curious-wavefunction/chocolate-consumption-and-nobel-prizes-a-bizarre-juxtaposition-if-there-ever-was-one/). Such correlations can often be explained by some other factor, in this case something like economic wealth. Wealth is required to fund the great educational institutions that conduct Nobel prize winning research and to purchase luxury goods like chocolate," the authors say. 

They argue that if fairness is only defined in terms of correlations, it can lead to nonsensical decisions, such as the correlation between chocolate and education outlined above. Indeed, such rationale could even increase unfairness rather than decrease it.

The counterfactual fairness approach hopes to tackle the issue via the causal relationships that emerge rather than relying purely on correlations. The team demonstrated their approach using stop and frisk data in New York City.

The authors hope that the framework provides organizations that are utilizing AI in their decision-making processes a better way of ensuring they are fair and without bias.

> "Firms may have specific legal obligations regarding fairness and they could potentially use our framework not just as way to achieve fairness, but also to explain how and why they are making those decisions. We would like to explore further how to relate our work to actual legal and regulatory requirements, and to collaborate with Turing partners or other organizations to apply this to real-world problems," the authors say. 

[Check out](https://dzone.com/go?i=200130&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) the Exaptive data application Studio. Technology agnostic. No glue code. Use what you know and rely on the community for what you don't. [Try the community version](https://dzone.com/go?i=200130&u=https%3A%2F%2Fexaptive.city%2F%23%2Flanding%3Freferrer%3DGeneral).
