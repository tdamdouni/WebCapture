# Read This Post, Especially if You Don’t Have Time

_Captured: 2017-04-05 at 23:47 from [dzone.com](https://dzone.com/articles/read-this-post-especially-if-you-dont-have-time?edition=288883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-05)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

> "Time keeps on slipin' slipin' slipin', into the future" -- "Fly Like An Eagle", The Steve Miller Band 

Your web server's system time can keep on slippin' far into the future if Network Time Protocol ([NTP](https://en.wikipedia.org/wiki/Network_Time_Protocol)) is not properly configured. Having accurate system time is critical for application logic, scheduled jobs, and of course logging. With logging, if the system time is off, log forensics and log correlation of security events across systems become a nightmare, if not impossible. Many software components on your servers rely on accurate system time, including the Signal Sciences agent. The agent uses the local system clock to generate timestamps when logging detections and other events. As a result, ensuring accurate system time on all your web servers is a must for robust security -- _and this is especially true for virtual machine based deployments_.

Why do I call out virtual machines? Our agent has been deployed in numerous environments and on thousands of machines (bare metal, virtual machines, containers, IaaS, PaaS, and whatever else you might imagine). In new deployments, virtual machines without NTP configured stick out like a sore thumb since their system time is way off. We've seen ranges from tens of thousands to hundreds of thousands of seconds off into the future! This drastic time skew has a severe impact on security related events since the timestamps can be so significantly skewed. One example of impact is when presenting events in a dashboard that is time-based, e.g. displaying all events within the last 6 hours. You won't see the data if its timestamps are several hours in the future. Time skew can happen on any infrastructure, but if you are running virtualized infrastructure you'll want to pay close attention.

In addition to NTP not being configured, there has been research published on attacks against the NTP protocol. Some of which result in shifting time on NTP clients. This research is published[ here](https://eprint.iacr.org/2015/1020.pdf) and referenced in this [Ars Technica](https://arstechnica.com/security/2015/10/new-attacks-on-network-time-protocol-can-defeat-https-and-create-chaos/) article. Another threat consideration is a malicious insider, who could modify system time in attempts to hide events or manipulate time sensitive transactions.

## "Watching" Time

How can we mitigate the risk of skewed timestamps, missing data, and possible attacks on system time? First, NTP is a beautiful thing. Make sure you have a consistent NTP implementation across all your servers. Second, periodically verify the system time on your servers is not skewed beyond an acceptable threshold. Fortunately for Signal Sciences customers, you already have visibility into your server time! Since time is such a crucial part of security, our agent provides visibility on your server clock skew. This is just one of the many metrics reported on by the agent, and it can be found via the UI by navigating to the agent's graph page. On that page, scroll down towards the bottom to find the **Agent Clock Skew** graph.

![](https://cdn-images-1.medium.com/max/1600/1*RBi-0OOWtADyPMWr8LrqCg.png)

The screenshot above is from a VM, where the clock skew is obviously drastically off until it was corrected.

![](https://cdn-images-1.medium.com/max/1600/1*FCnu8BLxY9beInCGE1k5yQ@2x.jpeg)

The screen shot above is from an agent running in a popular PaaS environment. A one-second clock skew is relatively negligible, but depending on your circumstances perhaps it could be an issue.

_ In the next section, I've published two scripts, one is a proof-of-concept Bash shell script that can be used to help monitor system time across many servers._

## Monitoring Clock Skew

Ok, visibility on clock skew -- great! Pretty graph -- great! But what if you are like many of our customers and have hundreds of agents deployed. That's a lot of looking at pretty graphs to find hosts with clock skew -- not great! Good news, Signal Sciences makes all data available via its API -- great!!! This means you now have the ability to automate monitoring of clock skew across your web server farm.

With the API you can integrate with any monitoring system you may have, however, I've provided an example of checking clock skew with just two scripts. The first script, [SigSciApiPy](https://github.com/signalsciences/SigSciApiPy), handles authenticating and pulling agent metrics from the API. The second script is shown below, [clock_skew.py](https://gist.github.com/foospidy/06c263747ea3291dec60b9555cb5f2af), loops through the agent data looking for the value of **host.clock_skew**. **Host.clock_skew** is the median number of seconds that the particular agent's clock is skewed compared to the time on our servers, over the past 5 minutes. So for example, if we have **"host.clock_skew": 30**, that means that we saw a median skew of 30 seconds over the past 5 mins. The **clock_skew.py** script will print a warning or alert message to the console based on defined thresholds.
    
    
    agents = open('/tmp/sigsci-agents.json', 'r')
    
    
            print("ALERT: Clock skew for {0} is {1}".format(agent['agent.name'], skew))
    
    
            print("WARNING: Clock skew on {0} is {1}".format(agent['agent.name'], skew))

Download or view the script on [Github](https://gist.github.com/foospidy/06c263747ea3291dec60b9555cb5f2af).

An example run of these scripts together looks like this:
    
    
    ./SigSci.py --agents > /tmp/sigsci-agents.json; ./clock_skew.py

Note, if you do use **clock_skew.py**, you'll want to set the WARN and ALERT threshold variables to values that make sense to you.

Below is a script that can achieve a similar result in monitoring for clock skew. If shell scripts are not your thing, there are many other tools that may be a better fit in your environment. For example, monitoring systems like [Nagios](https://www.nagios.org/) or [Zabbix](http://www.zabbix.com/), or configuration management tools such as [Ansible](https://www.ansible.com/), [Chef](https://www.chef.io/), or [Puppet](https://puppet.com/). I'm sure there are other, and even better, ways to monitor for clock skew. If you have suggestions please add them in the comments section.
    
    
    IFS=':' read -a host_config <<< "${host}"
    
    
    if [ ! -z ${host_config[1]} ];
    
    
    remote_time=`sshpass -e ssh -p ${p} ${h} date`
    
    
    local_sec=`date --date="${local_time}" +%s`
    
    
    remote_sec=`date --date="${remote_time}" +%s`
    
    
    skew=`expr ${remote_sec} - ${local_sec}`

Download or view the script on [Github](https://gist.github.com/foospidy/77c43ec2b2b71e4447f0534f7ac26798).

## Monitoring for Time Skew Is a Security Must

I think we can all agree that ensuring you have accurate system time across your servers is critical for security. Also, having the ability to monitor for time skew is equally as important. I hope the example scripts I've provided help to jump start your clock skew monitoring efforts in a _timely_ manner.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
