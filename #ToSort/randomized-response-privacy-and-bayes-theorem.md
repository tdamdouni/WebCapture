# Randomized Response, Privacy, and Bayes Theorem

_Captured: 2017-10-12 at 16:56 from [dzone.com](https://dzone.com/articles/randomized-response-privacy-and-bayes-theorem?edition=329562&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202017-10-12)_

[Learn best practices](https://dzone.com/go?i=239229&u=http%3A%2F%2Fgo.qubole.com%2FLP---DataOps---Book-Offer.html%3Futm_campaign%3DCS-Dzone%26utm_content%3DDataOps_Book%26utm_medium%3DPartnerResource%26utm_term%3DQ317) according to DataOps.[ Download the free O'Reilly eBook](https://dzone.com/go?i=239229&u=http%3A%2F%2Fgo.qubole.com%2FLP---DataOps---Book-Offer.html%3Futm_campaign%3DCS-Dzone%26utm_content%3DDataOps_Book%26utm_medium%3DPartnerResource%26utm_term%3DQ317) on building a modern Big Data platform.

Suppose you want to gather data on an incriminating question. For example, maybe a statistics professor would like to know how many students cheated on a test. Being a statistician, the professor has a clever way to find out what he wants to know while giving each student deniability.

## Randomized Response

Each student is asked to flip two coins. If the first coin comes up heads, the student answers the question truthfully (yes or no). Otherwise, the student reports "yes" if the second coin came up heads and "no" it came up tails. Every student has deniability because each "yes" answer may have come from an innocent student who flipped tails on the first coin and heads on the second.

How can the professor estimate _p_, the proportion of students who cheated? Around half the students will get heads on the first coin and answer truthfully; the rest will look at the second coin and answer yes or no with equal probability. So, the expected proportion of yes answers is _Y_ = 0.5 _p_ \+ 0.25, and we can estimate _p_ as 2 _Y_ \- 0.5.

## Database Anonymization

The calculations above assume that everyone complied with the protocol, which may not be reasonable. If everyone were honest, there'd be no reason for this exercise in the first place. But we could imagine another scenario. Someone holds a database with identifiers and answers to a yes/no question. The owner of the database could follow the procedure above to introduce randomness in the data before giving the data over to someone else.

## Information Contained in a Randomized Response

What can we infer from someone's randomized response to the cheating question? There's nothing you can infer with _certainty_; that's the point of introducing randomness. But that doesn't mean that the answers contain no information. If we completely randomized the responses, dispensing with the first coin flip, _then_ the responses would contain no information. The responses _do_ contain information -- but not enough to be incriminating.

Let _C_ be a random variable representing whether someone cheated and let _R_ be their response, following the randomization procedure above. Given a response _R_ = 1, what is the probability _p_ that _C_ = 1, i.e. that someone cheated? This is a classic application of Bayes' theorem.

![](https://www.johndcook.com/randomized_response_bayes.svg)

If we didn't know someone's response, we would estimate their probability of having cheated as _p_, the group average. But knowing that their response was "yes" we update our estimate to 3 _p_ / (2 _p_ \+ 1). At the extremes of _p_ = 0 and _p_ = 1 these coincide. But for any value of _p_ strictly between 0 and 1, our estimate goes up. That is, the probability that someone cheated, conditional on knowing they responded "yes", is higher than the unconditional probability. In symbols, we have:

...when 0 < _p _< 1\. The difference between the left and right sides above is maximized when _p_ = (√3 - 1)/2 = 0.366. That is, a "yes" response tells us the most when about 1/3 of the students cheated. When _p_ = 0.366, _P_( _C _= 1 | _R_= 1) = 0.634, i.e. the posterior probability is almost twice the prior probability.

You could go through a similar exercise with Bayes theorem to show that _P_( _C_ = 1 | _R_ = 0) = _p_/(3 - 2 _p_), which is less than _p_ provided 0 < _p_ < 1\. So if someone answers "yes" to cheating, that _does_ make it more likely that the actually cheated, but not so much more that you can justly accuse them of cheating. (Unless _p_ = 1, in which case you're in the realm of logic rather than probability. If everyone cheated, then you can conclude that any individual cheated.)

**Update**: See the [next post](https://www.johndcook.com/blog/2017/09/20/quantifying-privacy-loss-in-a-statistical-database/) for a more general randomization scheme and more about the trade-off between privacy and utility. The [post after that](https://www.johndcook.com/blog/2017/09/20/adding-laplace-or-gaussian-noise-to-database/) gives an overview of randomization for more general kinds of data.

Find the perfect platform for a scalable self-service model to manage Big Data workloads in the Cloud. [Download the free O'Reilly eBook to learn more](https://dzone.com/go?i=239230&u=http%3A%2F%2Fgo.qubole.com%2FLP---DataOps---Book-Offer.html%3Futm_campaign%3DCS-Dzone%26utm_content%3DDataOps_Book%26utm_medium%3DPartnerResource%26utm_term%3DQ317).

Topics:

bayesian ,big data ,data science ,anonymized data ,randomized response ,tutorial
