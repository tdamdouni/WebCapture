# The Performance of a Single Worker

_Captured: 2017-01-26 at 23:01 from [dzone.com](https://dzone.com/articles/on-the-performance-of-a-single-worker-1?edition=265882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-26)_

Discover 50 of the latest mobile performance statistics with the [Ultimate Guide to Digital Experience Monitoring](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE).

## **Introduction**

In this article, we will investigate how the average waiting time and the average numbers of jobs and tasks (in the queue) vary when the jobs and tasks are processed using a single worker with a single queue. The following figure illustrates the system model.

![](https://lh4.googleusercontent.com/6NS8cFWGZ3FpATrpu1DGqSHWKT1izfVy_7s_X6Nvnx9oQvLqZ1JNzfHmx46cUutMWNzgtByG3L0heixw7XxkKh_T-5khWp1KqyvE90s27LTEhUeMifyuZuqbfEWHbvh9Yy3Js5U1)

The tasks, jobs, and requests that arrive at the system placed in the queue and processed in First-Come-First-Served (FCFS) manner until completion. The worker here could represent a thread or process that processes tasks, request, and jobs using a given CPU/Core on a machine.

In this article, we will investigate the following:

  1. The behavior of average waiting time with the utilization.

  2. The behavior of average waiting time with the arrival rate.

  3. The behavior of average queue length time with the utilization.

  4. The behavior of average queue length with the arrival rate.

Note that in this article, when we mention average waiting time, we refer to the average waiting time in the queue (refer to the above diagram).

## Performance Results

The results presented in this article have been obtained using queuing theoretic modeling techniques. The [queueing theory](https://en.wikipedia.org/wiki/Queueing_theory) provides a stochastic and probabilistic approach for investigating the operation of queues.

The two factors that affect the waiting time and the queue length are:

  1. **Arrival pattern. **Arrival pattern describes the distribution of time between request arrivals. The arrival pattern of a queueing system is typically described in terms of the average time between two successive arrivals or the average number of arrivals per some unit of time. The exponential distributions are sometimes used to model the time between the arrival of requests.

  2. **Service pattern. **Service pattern describes the distribution of service times (time it takes to process).

For more information about a basic queuing process, refer to [this](https://medium.com/@malith.jayasinghe/performance-testing-with-a-think-time-64b6b737e3f9#.d8k6k2x03). To compute the average waiting time in the queue for the system described above, we use the Pollaczek-Khinchine formula:

![](https://lh5.googleusercontent.com/mAR8A2v31XHOYMCxE7vcthB-6EALwXBhIZgRtNYlHcjO4445p0MDcBB7-I9ZtpX3VzZ4AHVrSN9nv35KPpj2Uts6WIBYveF7NPUgY5ywBEzov3H4iAakJRF7uWnHvx0e2Aqk6Muv)

  * **E[W]FCFS** denotes the average waiting time.

  * **E[X]** is called the first moment of the distribution. The first moment is simply the mean (average) of the service time distribution which is a measure of how much time a task/job will take to process on the system on average.

  * **E[X2]** is called the second moment of distribution and it is a measure of the variability of service times. As can be seen from the equation above, the average waiting time is inversely proportional to the variability/variance of service times.

  * **λ** denotes the average arrival rate into the system which relates to arrival process described above.

The above equation is valid for any service time distribution provided that the arrival pattern of tasks into the system is [Poisson](https://en.wikipedia.org/wiki/Poisson_point_process). Note that the Poisson arrivals also imply that the time between arrivals (i.e., inter-arrival times) is exponentially distributed. In this article, we will assume that the tasks arrive according to a Poisson process and service times are exponentially distributed.

It is worth noting that in (certain) systems the service and inter-arrival times may not follow exponential distributions. In fact, there is evidence that shows that service times distribution of jobs and tasks have long tails. Such distributions can be represented using distributions such as Pareto. Our objective was to provide present results under certain basic assumptions.

## Service Time Distributions

The results presented in this article consider the following three exponential distributions with different rates. Note that the exponential distribution is defined by the single parameter lambda (λ) which is also called the rate.** It is important to point out that λ parameter in exponential distribution (i.e., rate) and λ parameter in the average waiting time equation (which represent the average arrival rate) are not the same.**

**Rate = lambda (λ)**

**E[X] (First Moment = Mean) (ms)**

**E[X2] (Second Moment)**

50

0.02

0.0008

500

0.002

0.000008

5000

0.0002

0.00000008

The following figure illustrates the above three exponential distributions.

![aa_expont.png](https://lh5.googleusercontent.com/4hV9RZnMSxCvVchvAlfslGVHRmXwYFGE24GFUjolJoRDdMV6GB_EIsCpJikt1XfiWcdNrqrj9a7YzZ5ElZOHydI7bHW2B6aRg_2RvYIAp9oHs7N_7PXo9tERH6DptvMRlR2IXqWk)

Note that properties and the shape of the distribution vary with lambda (λ) parameter. For example, if we take the exponential distribution with λ = 50, compared to the other two distributions (i.e., with the distributions with λ = 500 and 5000), it has relatively large number jobs and requests with high service times and a relatively small number of jobs with small service times resulting in a higher mean. In addition to this, variability of these service times is also higher in the distribution with the lower rate (λ) leading to a higher second moment (refer to the table above).

## **Average Waiting Time**

Let's now consider how the average waiting time varies with the (average) arrival rate.

The following figure illustrates the way in which the average waiting time varies with the increasing arrival rate.

![plot.jpg](https://lh3.googleusercontent.com/DlyKAQeH1d5I8CCq13YbxU8QDffj--g-0Lbccj9W-Q2oYUwgiFFkaINT3iBFsNBoBJgXI06tlvz0APzyqM0wO2IxDwEGzys3QkRE_XM5szW8nq981izSv5SjnaWe39LR0jOOb91k)

Note that the system has the worst average waiting under the distribution with λ = 50 while the system has the best waiting time (i.e., lowest) under distribution with λ = 5000. We also notice that there is a rapid increase in the average waiting time as the arrival rate approaches towards a certain (fixed) value. For example, for the distribution with λ = 500, as the average arrival rate approaches 500 requests/second (refer to the figure above), the average waiting time approaches towards a very high value (i.e., infinity).

From the above figure, we can also note that the system can continue to performance perform well (i.e. with the low average waiting time) under high arrival rates (i.e., 4,000 requests/second) provided that λ is high (i.e., 5000). The reason for this (as discussed above) is that the distribution with higher λ value has relatively large number of tasks/jobs/requests with small services times that take a relatively small amount of time to process. Furthermore, the variance of the distribution is low when λ is high (note: the waiting time is proportional to the variance). As a result, the average waiting time of tasks in the queue is low when λ is high.

Let us now have a look at the behavior of the average waiting time with the utilization under the above three service time distributions. The queuing theoretic equations for obtaining the utilization is given below [note: there are other ways to compute the utilization as well]

** Utilization = Average Arrival Rate x Mean Service Time**

The behavior of the average waiting time with the utilization is illustrated in the following figure.

![aa_util.png](https://lh5.googleusercontent.com/6YpKxc5WLoQx0Jsp8glsZEC45s6-k0PjaqcbMOlGM6if7rmEgh9YA-rj9Co1BdUT4Xm_MO9zhbLg39AnTx0AS57S2WIcyE9N3d-TofXkB57mKnpDRIgAylR2fUefNoQCIL7AMesC)

As we can see from the figure, the way the average waiting time varies is different under the three service time distributions.

Notice that for the distribution with λ = 50, the average waiting time increases rapidly if the utilization increases above 20%. For the distribution with λ = 5000, the average waiting time increases rapidly when the utilization increase above 95%. The reason for the behavior (as discussed above) has to do with distribution with lower λ values having higher mean (i.e., E[X]) and second moment (E[X2])) which has direct impact on the expected waiting time (refer to the average waiting time equation presented above).

Let's now assume that there is a requirement which states that the average waiting time of the system must be less than 2 ms. The following table shows the maximum utilization the system should function to satisfy this requirement.

**Rate = lambda (λ)**

**Average waiting time**

**Utilization**

50

2 ms

9.90 %

500

2 ms

50 %

5000

2 ms

90 %

## Average Queue Length

Let's now have look at how the average queue length varies with the arrival rate. The average queue length is computed using the [little's formula](http://web.mst.edu/~gosavia/queuing_formulas.pdf).

The following figure shows the behavior under the three distributions.

![aa_d_arivel-Recovered.jpg](https://lh3.googleusercontent.com/mgwqj1ptbLS0uA3ASJHruvpuwMRHHTtnF48iaKoe2ObCaWfrWazGmmeiADvgDzOWlH47_Jk-I4HAP3bC8G3dLox93kzjWQFk8SKShqbMgW4r5cvNKBr6RrGt08SEU7_bVMWmLTdd)

Note that the behavior of queue length (with arrival rate) is very similar to that of average waiting time with the arrival rate. We see the longest (average) queue length under the distribution with λ = 50 while the shortest average queue length under the distribution λ = 5000. The reason for this has already been discussed earlier and it has to to do with the fact the distribution with λ = 5000 having relatively large number of jobs and tasks with small service times resulting in relatively smaller number of items in the queue resulting (compared to that of distribution with λ = 50 or λ = 500).

Let's now have a brief look at the behavior of the average queue length with the utilization. This is illustrated in the following figure:

![aaaaa.jpg](https://lh5.googleusercontent.com/T1HB0Uc-kOF-0CFRk3VGWLxRzQ-i6LxBIHHHv91XfnZyTBdYHyCePqeuzETx-ZQfrJLnaavaSlCUC7jAc19IJL2g0zty7VJEoB9FznAetxEeDMzjxUR7mKhhQHhGGGH2OU2gBxrp)

The behavior of the average queue length is similar under the three distributions considered. This can be explained using the utilization equation and the little's formula presented above. Let's assume that the utilization of the system is U. According to the utilization equation presented above, as the mean service time increases, the maximum arrival rate the system can receive tasks to maintain the utilization under U decreases. This means that when we compute the average queue length under a given utilization (using the little's formula) we have to substitute a higher arrival rate for the distribution with lower mean (or higher rate). Note that the distribution with the lower mean has a lower average waiting time. As a result, the behavior of average queue lengths are similar.

## Conclusion

In this article, we looked at the average waiting time and queue length of a server that process tasks on FCFS basis. Such a model can be considered as a worker with a single queue where the worker process tasks on the FCFS basis. The main objective was to investigate how the average waiting time and the queue length vary under different service time distributions with different arrival rates (and system utilizations).

[Is your APM strategy broken?](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) This [ebook](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) explores the latest in Gartner research to help you learn how to [close the end-user experience gap in APM](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE).

Opinions expressed by DZone contributors are their own.
