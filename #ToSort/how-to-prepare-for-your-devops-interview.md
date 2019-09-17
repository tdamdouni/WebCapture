# How to Prepare for Your DevOps Interview - DZone DevOps

_Captured: 2019-09-12 at 10:23 from [dzone.com](https://dzone.com/articles/how-to-prepare-for-your-devops-interview?edition=521321&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202019-09-11)_

Over the past decade, DevOps has emerged as a new tech culture and career that marries the rapid iteration desired by software development with the rock-solid stability of the infrastructure operations team. For system administrators, operations engineers, and others with strong systems and software backgrounds, there’s perhaps no better time than the present to transition into DevOps. As of August 2019, there are currently over 50,000 [LinkedIn DevOps job listings](https://www.linkedin.com/jobs/search/?keywords=devops&location=United%20States) in the United States alone. For a good overview of what DevOps entails and how to transition, check out this [blog post](https://blog.insightdatascience.com/preparing-for-the-transition-to-devops-engineering-7b1589e1e034).

> You may also enjoy:  [10 DevOps Interview Answers](https://dzone.com/articles/10-devops-interview-answers)

Let’s say you’ve learned the fundamentals and are ready to start your job hunt. How do you ace your DevOps interview? DevOps Engineers must be both good software developers and infrastructure experts and, as such, they are expected to know Linux infrastructure, networking, algorithms, and DevOps tools such as Terraform, Docker, and Kubernetes. [Interviews](https://dzone.com/articles/what-to-expect-from-a-devops-interview) can range from standard software engineer coding questions to questions on system design, Linux debugging, and DevOps tools.

This is an intimidating list, but have no fear! At [Insight](https://www.insightdevops.com/?utm_source=dzone-devops), the DevOps Fellowship has launched the careers of many individuals with transferrable skills into highly desired industry DevOps positions. Here’s how we prepare them for interviews.

## Introduction

Motivation is a great start, but you’ll need the discipline to prepare effectively. I’ve written this guide to help you develop a disciplined interview preparation routine. Interviewing can really suck — it’s random and can make you feel bad about yourself. There’s so much you can’t control in the process, but you **can** control how you prepare.

There is a lot here to chew on, so don’t expect to be able to learn everything all at once. Maybe one day you’ll choose one topic to focus on. Maybe you’ll focus on another topic for a week straight. In general, though, you should pick two or three activities to do habitually each day, rotating through different topics so your mind stays fresh and engaged. These categories are listed in order of importance:

  1. [Linux Fundamentals](https://dzone.com/articles/5-free-courses-to-learn-linux-commands-in-depth)
  2. [Data Structures and Algorithms](https://dzone.com/articles/top-5-data-structures-and-algorithm-online-courses)
  3. [System Design](https://dzone.com/articles/scalable-system-design)
  4. [Parsing](https://dzone.com/articles/a-guide-to-parsing-algorithms-and-technology-part)
  5. [DevOps Tools](https://dzone.com/articles/what-devops-tools-do-you-really-need-in-2019)

It’s good to develop a wide, shallow base of knowledge first, so load balance across topics in a round-robin fashion at first. That will widen your conceptual framework of the DevOps space so that you can more easily put new information into context. The activities within each category are ranked more or less in order of importance as well. Certain activities lend themselves to daily practice, like CodeSignal problems or OverTheWire challenges. Others lend themselves to deep study.

If you want to go fast, go alone. But if you want to go far, go together. Create a study group with your peers. Hold each other accountable. Do weekly or daily check-ins and info-sharing sessions. During those time that you feel unmotivated, remember that doing something is much better than doing nothing. During those times when you are too motivated, remember that sleep and exercise are every bit as important to your success as anything else. These activities are the stepping stones to the next phase of your life, but remember to allow yourself to become fascinated with the shape of each stone.

## Linux Fundamentals

As a DevOps Engineer, you’re expected to know Linux as well as the back of your hand. Any questions about Linux is fair game, from the kernel to networking to command line commands.

### Example Questions

  * What is the sequence of steps that occur when a Linux computer is powered up?
  * What happens when you type google.com into your browser that causes a web page to return to you? What if the web page doesn’t appear — how do you debug the problem?
  * How do you check if your filesystems are running out of space? How do you print a list of the largest files? How do you delete all .mov files larger than 1 GB?

### Activities

  * Work through _[The Linux Command Line_](http://solutionsproj.net/software/The_Linux_Command_Linex.pdf) book
  * Work through the [OverTheWire](https://overthewire.org/wargames/) wargames. These are fun scavenger hunts through Linux systems that are well-designed to teach you the fundamental concepts. At least get through the Bandit levels. Don’t be afraid to Google solutions if you get stuck. I highly suggest you document your progress in GitHub as you go.
  * Learn vim by simply using the vimtutor command. It’s just the best editor ever and don’t let anyone convince you otherwise.
  * Consider paying for [acloudguru](https://acloud.guru/courses) or [Linux Academy](https://linuxacademy.com/) courses to get certifications in Linux fundamentals (Linux+, RedHat, etc.). It’s true that a pound of certifications is less valuable than an ounce of experience, but when you are low on experience, certifications can help fill in gaps in your knowledge and prove that you have a basic understanding.

### References

  * The best reference manual for Linux commands is [tldr.sh](https://tldr.sh/). I highly suggest you download the tl;dr mobile app for quick reference. This has helped me on phone interviews where I didn’t know a command off the top of my head.
  * [devhints.io](https://devhints.io/) is a great source for all manner of cheat sheets.
  * It doesn’t look flashy, but the [Advanced Bash Scripting Guide](https://www.tldp.org/LDP/abs/html/) is a goldmine.

## Data Structures and Algorithms

Remember that DevOps is **Development** \+ Operations, so you’re expected to know how to code. Choose a language of your choice (not Bash — if you don’t have a strong preference, I recommend Python) and practice, practice, practice. It’s not just about finding an optimal solution — you must clearly communicate the parameters of the problem with your interviewer, convey your thought process as you go along, and calculate the time and space complexity of different algorithms.

### Example questions

  * Remove all duplicates from a list.
  * Find the missing IP in a file containing all possible IPs except one.
  * Sort all nodes of a binary tree.

### Activities

  * [Khan Academy](https://www.khanacademy.org/computing/computer-science/algorithms) has a really nice data structures and algorithms primer. It’s in Javascript, but don’t hold that against it. This curriculum was made in partnership with Tom Cormen, the author of the [definitive book on data structures and algorithms](https://en.wikipedia.org/wiki/Introduction_to_Algorithms) that’s definitely worth owning a copy of.
  * [LeetCode](https://leetcode.com/) has a large repository of problems that are close to real interview questions. In fact, many companies will directly ask you LeetCode questions! Do at least 10 easy and medium questions of each type of algorithms. You can start to feel prepared when you’ve done 100 problems and can actually solve each without looking anything up.
  * Work through the interview prep material daily on [CodeSignal](https://codesignal.com/developers/interview-practice/). I suggest Python, but you can work in any language. Copy and paste your code into files and version control it with GitHub. Each day, look through the code you did yesterday and document it in detail. Writing code is easier than reading your old code and trying to remember what’s going on. Revisiting your old code after a day or two will force you to synthesize the concepts you are learning.
  * Work through CodeSignal’s Python Arcade. It is a nice tour of all the important standard Python libraries. Some of the exercises really miss the mark but, overall, this is a nice playlist.
  * Research Dynamic Programming, Directed Acyclic Graphs, Topological Sort.
  * Everyone needs a little SQL. No need to spend large amounts of time on this, but you should sign up for a free account on [Mode Analytics](https://mode.com/) and make use of their great interactive SQL tutorials that use real public databases.
  * As you get more comfortable with your coding skills, use [Pramp](https://www.pramp.com/) to practice live technical interviews. This is an important component. Nothing quite prepares you for technical phone screens like practicing technical phone screens.
  * Remember that the only knowledge that counts is what you can demonstrate in front of the interviewer, either on the whiteboard or live coding. If you tend to freeze up in high-pressure situations, you’re far from the only one — be sure to do lots of practice with peers.

### References

  * [LearnXinYminutes](https://learnxinyminutes.com/docs/python3/) is a great, example-driven cheat sheet for Python
  * [Python Cheat Sheet](https://gto76.github.io/python-cheatsheet/#main): The best Python cheat sheet, although it is on the terse side
  * [Hitchhiker’s Guide to Python](https://docs.python-guide.org/): The best Python documentation.
  * My [scripts GitHub repo](https://github.com/chuckinator0/Projects/tree/master/scripts) has lots of examples of thoroughly documented code, although it’s really unorganized!

## System Design

The system design interview tests your big-picture thinking, ability to architect complex infrastructure, and communication skills. Be sure to practice a top-down design approach with clear infrastructure diagrams and DevOps considerations.

### Example Question

  * Design a microblogging message-based social network like Twitter. How would you ensure high availability across different regions?

### Activities

  * Chip away at the [System Design Primer](https://github.com/donnemartin/system-design-primer/blob/master/README.md). One fun thing to do is to pick a topic and ask a friend to pick another topic, then spend 2 hours researching your topic before coming back together for an hour or two to share. Take turns playing the roles of interviewer and interviewee.
  * Read the [Google SRE Book](https://landing.google.com/sre/sre-book/toc/index.html). This is a must-read book for modern DevOps.

## Parsing

Sysadmins frequently analyze system outputs and logs to obtain system insights and debug issues. Command-line parsing with tools like grep, awk, and sed is an important skill for the DevOps arsenal.

### Example Questions

  * Given an Apache web server log, how many requests are made per day? Which IPs are the most frequent visitors? Which pages and images are the most requested?

### Activities

  * Work through the **exercises** in Insight’s [parsing workshop materials](https://github.com/InsightDataScience/Parsing-Workshop). Focus on awk. The chapter materials are good, but the exercises are the most important part to do.

### References

  * [LearnXinYminutes](https://learnxinyminutes.com/docs/awk/): Another great example-driven reference — this time for awk.
  * [Regexr](https://regexr.com/): The best regular expression reference.

## DevOps Tools

Docker, Terraform, and Kubernetes are essential DevOps tools, and you can’t go wrong learning them thoroughly. You should also know at least one CI/CD tool, such as Jenkins. It’s highly recommended that you learn these tools on at least one of the big three clouds: AWS, GCP, or Azure.

### Example Question:

  * Deploy a Docker application onto a new AWS EC2 instance using Terraform.

### Activities

  * You need to learn Kubernetes. In order to learn Kubernetes, you need to learn about containerization and Docker.
  * Work through the [Docker for Beginners](https://github.com/docker/labs/blob/master/beginner/readme.md) lab
  * Work through the [Play With Docker Classroom](https://training.play-with-docker.com/)
  * Kubernetes (concept: container orchestration)
  * Read through [Kubernetes concepts](https://kubernetes.io/docs/concepts/overview/what-is-kubernetes/)
  * Work through the [Kubernetes Basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/) tutorial
  * For a deeper dive, work through the [Katacoda course](https://www.katacoda.com/courses/kubernetes)
  * Work through an introductory [Jenkins tutorial](https://jenkins.io/doc/tutorials/build-a-python-app-with-pyinstaller/) or two to learn more about CI/CD (concept: deployment pipeline as code). I honestly don’t know that much about Jenkins, so I don’t know better resources for this.
  * Use [Vagrant](https://www.vagrantup.com/intro/getting-started/index.html) to declaratively define a VM, and then use [VirtualBox](https://www.virtualbox.org/) or [Packer](https://www.packer.io/intro/getting-started/install.html) to export that VM as an OVA file (concepts: immutable infrastructure, configuration as code).
  * Terraform (concept: infrastructure as code)
  * Read Terragrunt’s [Comprehensive Guide to Terraform](https://blog.gruntwork.io/a-comprehensive-guide-to-terraform-b3d32832baca)
  * Work through the [Terraform Tutorial](https://learn.hashicorp.com/terraform/)
  * Ansible (concept: configuration as code)
  * Watch the [intro video](https://www.ansible.com/resources/videos/quick-start-video)
  * For some hands-on labs, I think Linux Academy might be the best bet (not free)
  * Do the [Honeycomb Quickstart](https://docs.honeycomb.io/learning-about-observability/quick-start/) to give a flavor of monitoring/tracing tools (concept: full-stack tracing)
  * Work through the [Consul tutorial](https://learn.hashicorp.com/consul/) (concept: service discovery).
  * Work through the [Vault tutorial](https://learn.hashicorp.com/vault/) (concept: enterprise-scale secrets management)
  * Play with [Linkerd](https://linkerd.io/2/getting-started/) (concept: service mesh)
  * Apache Kafka (concept: fault-tolerant, high throughput event streaming)
  * Shameless plug for Apache Kafka — find the free [Confluent Training](https://cloud.contentraven.com/confluent/self-userpackage) course on the site to get a nice set of videos about Kafka fundamentals
  * Check out the [operations training repo](https://github.com/confluentinc/training-operations-src) to get your own local docker-compose Kafka cluster up and start playing with Kafka

### References

  * Ansible: The [User Guide](https://docs.ansible.com/ansible/latest/user_guide/index.html).
  * Want to do something specific in Kubernetes? Check the [Tasks](https://kubernetes.io/docs/tasks/) section of the docs. There are many task-specific guides.
  * Docker’s [Samples](https://docs.docker.com/samples/) page has good examples of fully built applications as well as some good hands-on tutorials. I like the [Django+Postgres](https://docs.docker.com/compose/django/) sample.

## Other High-Value Items

### Activities

  * Listen regularly to the [Software Engineering Daily](https://softwareengineeringdaily.com/) podcast. This is by far the best way to keep a finger on the pulse of the DevOps world. I suggest getting the app so that you can easily search through old episodes for in-depth talks about the technologies and concepts you are studying. In the DevOps Tools section, I gave keywords for the concepts behind each tool. You can use these keywords to search SEdaily for relevant podcasts.
  * Read about [Kanban](https://www.atlassian.com/agile/kanban/boards) boards and use them to enhance your focus and productivity. GitHub has a simple kanban board you can use to keep yourself productive. I also personally like [bullet journaling](https://www.youtube.com/watch?v=fm15cmYU0IM) and the [Pomodoro Method](https://en.wikipedia.org/wiki/Pomodoro_Technique).
  * Dig deep into the technical details of some of your favorite tools. Start with the documentation. Pair up and share your takeaways from the technical deep-dives.
  * Consider paying for Linux Academy or acloudguru courses to get AWS, GCP, or Azure certifications.

### References

  * Digital Ocean has great tutorials. When I Google, I tend to try “<research topic> site:digitalocean.com” first. This is especially helpful when you are first learning to install something manually.

Credit to Insight DevOps alum Chuck Larrieu Casias for writing this blog.

_Interested in transitioning to a career in DevOps engineering? Learn more about the [Insight Fellows program](https://www.insightdevops.com/?utm_source=dzone-devops) and [start your application today](https://apply.insightdatascience.com/?utm_source=dzone-devops)._

## _ _Further Reading

[ Questions to Ask in a DevOps Interview

](https://dzone.com/articles/find-how-prepared-you-are-for-devops-interview)

[ What to Expect From a DevOps Interview

](https://dzone.com/articles/what-to-expect-from-a-devops-interview)
