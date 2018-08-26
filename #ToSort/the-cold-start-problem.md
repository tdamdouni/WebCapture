# The Cold Start Problem

_Captured: 2018-08-16 at 20:59 from [dzone.com](https://dzone.com/articles/the-cold-start-problem?edition=385380&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-08-16)_

[Hortonworks Sandbox](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) for HDP and HDF is your chance to get started on learning, developing, testing and trying out new features. Each [download](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) comes preconfigured with interactive tutorials, sample data and developments from the Apache community.

How do you operate a data-driven application before you have any data? This is known as the **cold start problem**.

We faced this problem all the time when I designed clinical trials at MD Anderson Cancer Center. We used Bayesian methods to design **adaptive clinical trial designs**, such as clinical trials for determining chemotherapy dose levels. Each patient's treatment assignment would be informed by data from all patients treated previously.

But what about the** first patient** in a trial? You've got to treat a first patient, and treat them as well as you know how. They're struggling with cancer, so it matters a great deal what treatment they are assigned. So you treat them according to expert opinion. What else could you do?

Thanks to the magic of **Bayes theorem**, you don't have to have an _ad hoc_ rule that says, "Treat the first patient this way, then turn on the Bayesian machine to determine how to treat the next patient." No, you use Bayes theorem from beginning to end. There's no need to handle the first patient differently because expert opinion is already there, captured in the form of prior distributions (and the structure of the probability model).

Each patient is treated according to **all information available** at the time. At first, all available information is prior information. After you have data on one patient, most of the information you have is still prior information, but Bayes' theorem updates this prior information with your lone observation. As more data becomes available, the Bayesian machine incorporates it all, automatically shifting weight away from the prior and toward the data.

**The cold start problem for business applications is easier** than the cold start problem for clinical trials. First of all, most business applications don't have the potential to cost people their lives. Second, business applications typically have fewer competing criteria to balance.

What if you're not sure where to draw your prior information? Bayes can handle that too. You can use **Bayesian model selection** or **Bayesian model averaging** to determine which source (or weighting of sources) best fits the new data as it comes in.

Once you've decided to use a Bayesian approach, there's still plenty of work to do, but the Bayesian approach provides scaffolding for that work, a framework for moving forward.

[Hortonworks Community Connection (HCC)](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295) is an online collaboration destination for developers, DevOps, customers and partners to get answers to questions, collaborate on technical articles and share code examples from GitHub. [Join the discussion.](https://dzone.com/go?i=293443&u=https%3A%2F%2Fcommunity.hortonworks.com%2Findex.html%3Futm_campaign%3Ddzonepre%2Fpostrollv2%26utm_medium%3D3rd-party-resource%26utm_source%3Ddzone%26utm_id%3D2307295)
