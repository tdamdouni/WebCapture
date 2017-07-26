# Early detection of configuration errors to reduce failure damage

_Captured: 2016-11-30 at 09:57 from [blog.acolyer.org](https://blog.acolyer.org/2016/11/29/early-detection-of-configuration-errors-to-reduce-failure-damage/)_

Here's one of those wonderful papers that you can read in the morning, and be taking advantage of the results the same afternoon! Remember the '[Simple testing can prevent most critical failures](https://blog.acolyer.org/2016/10/06/simple-testing-can-prevent-most-critical-failures/)' paper from OSDI'14 that we looked at last month? In that paper we learned that trivial mistakes in error handling, which are easy to test for, accounted for a vast majority of catastrophic production incidents. Well, as soon as you've got your error / exception handlers sorted out, you might want to read today's paper to discover another class of easy-to-test for bugs that are also disproportionately responsible for nasty production failures.

Facebook's '[Holistic configuration management](https://blog.acolyer.org/2015/10/16/holistic-configuration-management-at-facebook/)' paper stresses the importance of version control and testing for configuration, as configuration errors are a major source of site errors. Xu et al. study configuration parameters in the wild, focusing especially on those associated with reliability, availability, and serviceability (RAS) features. What they find is that very often configuration values are not tested as part of system initialization. The program runs along happily until reaching a point (say for example, it needs to failover) where it needs to read some configuration for the first time, and then it blows up - typically when you most need it.

So here's the short takeaway **test all of your configuration settings as part of system initialization and fail-fast if there's a problem**. Do that, and you'll cut out another big source of major production errors. The paper itself is in two parts: the first part (where I'll focus most of my attention in this short write-up) is an analysis of these _latent_ configuration errors in real code bases; the second part introduces a tool called PCheck, which if your program is written in C or Java can even find latent configuration usage and automatically write tests for you!

> Latent configuration errors can result in severe failures, as they are often associated with configurations used to control critical situations such as fail-over, error handling, backup, load balancing, mirroring, etc… Their detection or exposure is often too late to limit the failure damage. 

In a study of real-world configuration issues in the the products of COMP-A, "major storage company in the US," with footnote "we are required to keep the company and its products anonymous," it turns out that 75% of all high severity configuration-related errors are caused by _latent configuration_ errors. It may well be that the authors are required to keep COMP-A anonymous, but I couldn't help noticing the author affiliations printed in big type on the front page. A more than fair chance that company is NetApp I would say!

The authors also studied a number of real-world open-source systems (see table below), and inspected usage of all of their RAS-related configuration parameters.

![](https://adriancolyer.files.wordpress.com/2016/11/pcheck-table-3.png?w=600)

They looked at how many of those parameters were explicity checked vs simply being used when first required, yielding the results below:

![](https://adriancolyer.files.wordpress.com/2016/11/pcheck-table-4.png?w=600)

> Many of the studied RAS parameters do not have any special code for checking the correctness of their settings. Instead, the correctness is verified (implicitly) when the parameters' values are actually used in operations such as a file open call. 

Here's an example of a real-world latent configuration error in MapReduce:

![](https://adriancolyer.files.wordpress.com/2016/11/pcheck-fig-2.png?w=600)

And here are some other bugs found during the study, in the most recent versions of the software under inspection in (a) HDFS:

![](https://adriancolyer.files.wordpress.com/2016/11/pcheck-fig-3a.png?w=600)

> _and (b), Apache httpd:_

![](https://adriancolyer.files.wordpress.com/2016/11/pcheck-fig-3b.png?w=600)

So we know that many configuration parameters aren't checked before usage. It's also the case that many of these parameters aren't _used_ during system startup (and so are not verified even implicitily):

> Many (12-38.6%) of the studied RAS configuration parameters are not used at all during the system's initialization phase. 

Put these two finding together, and what you have is a collection of ticking time bombs! Remember that since these are _configuration settings_ they may be changed on deployment - i.e. these are not bugs that unit testing can catch.

> 4.7-38.6% of the studied RAS parameters do not have any early checks and and thereby subject to latent configuration errors which can cause severe impact on the system's dependability. 

Here's the summary of how many of these ticking time bombs can exist in the systems studied:

![](https://adriancolyer.files.wordpress.com/2016/11/pcheck-table-6.png?w=600)

> The threats are prevalent: Latent configuration errors can reside in 10+% of the RAS parameters in five out of six systems. As all theses latent configuration erros are discovered in the latest versions, any of them could appear in a real deployment and would impair the system's dependability in a latent fashion. 

The authors wrote a tool called PCheck which uses static code analysis to find instructions that load configuration parameters into program variables, looks for all instructions that use the parameter value, figures out the execution context of those instructions and composes checkers that can be run at initialization to verify the configurarion is well-formed in the target environment. I feel bad skipping over all of the details of the authors hard work here, but I'm going to refer you to the paper for full details if you're interested.

With the PCheck tests in place, the authors harvested 830 configuration files for the studied systems (from mailing lists and technical forums) and validated them. With the checks in place, 70+% of latent configuration errors were detected.

![](https://adriancolyer.files.wordpress.com/2016/11/pcheck-table-10.png?w=600)

> PCheck reports 282 true configuration errors (from 830 configs!) and three false alarms. Many (37.5-87.8%) of the reported configuration erros can only be detected by considering the system's native execution environment. These configuration settings are valid in terms of format and syntax (in fact, they are likely to be correct in the original hosts). However, they are erroneous when used on the current system because the values violate environment constraints such as undefined environment variables, non-existing file-paths, unreachable IP addresses etc.. 

(Which leaves me a little unsure as to what the authors count as a 'true configuration error'  
- a configuration file which may have been perfectly valid on the system from which it was cut-and-pasted onto a mailing list may of course give problems in another context, but this doesn't imply it was truly a configuration error on the original system).

Nevertheless, I think the overall message of this paper is clear: **Ladies and Gentlemen, please eagerly check all of your configuration variables on system startup.**

> This paper advocates early detection of configuration errors to minimize failure davage, especially in cloud and data-center systems. Despite all the efforts of validation, review, and testing, configuration errros (even those obvious errors) still cause many high-impact incidents of today's Internet and cloud systems. 
