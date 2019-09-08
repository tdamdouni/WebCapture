# Google's "Director of Engineering" Hiring Test

_Captured: 2019-09-05 at 15:12 from [www.gwan.com](http://www.gwan.com/blog/20160405.html)_

## › Google's "Director of Engineering" Hiring Test

Recently, I have been interviewed over the phone by a Google recruiter. As I qualified for the (unsolicited) interview but failed to pass the test, **_this blog post lists the questions and the expected answers_**. That might be handy if Google calls you one day. 

For the sake of the discussion, I started `coding` 37 years ago (I was 11 years old) and never stopped since then. Beyond having been appointed as `[R&D Director`](https://ch.linkedin.com/in/pierregilbertgauthier) 24 years ago (I was 24 years old), among [(many) other works](https://ch.linkedin.com/in/pierregilbertgauthier), I have since then designed and implemented the most demanding parts of TWD's R&D projects* – all of them delivering commercial products: 

  * [Global-WAN](http://global-wan.ch/) (a [C/VHDL distributed L2 VPN](http://twd.ag/archives/global-wan_executive-summary.pdf) relying on a custom kernel-bypass IP stack and our own [post-quantum encryption](/blog/20160801.html))
  * [G-WAN](http://g-wan.com/) (a 200 KB application server with [17 scripted programming languages](http://gwan.ch/developers#servlet) C/C++, C#, Objective-C, Java, Go, PHP, etc.)
  * [Remote-Anything](http://remote-anything.com/imgs/remote-anything.jpg) (a patented enterprise network management solution, [280 millions of licenses deployed in 138 countries](http://twd.ag/en/customers.html))

Google's representative stated that _both_ `management` and up-to-date `coding` skills were required (a rare mix). But having exercised the former for more than 2 decades and the latter for almost 4 decades was not enough: I failed to give the _"right answers"_. Is Google raising the bar too high or is their recruiting staff seriously lacking the skills they are supposed to rate? 

Let's have a look! 

  


### Google's "Director of Engineering" Q&A Test

* * *

Here are the "highly technical" questions and their answers – until the test was interrupted as it was obvious that I did not fit the task: 

1\. What is the opposite function of malloc() in C? 

Me: free(). 

Recruiter: right. 

Thought: _I imagine that in these rare moments you are supposed to feel proud of your 35 years of programming in the 40-year old C._

2\. What Unix function lets a socket receive connections? 

Me: listen(). 

Recruiter: right. 

Thought: _Does this make me really qualify as a network guru?_

3\. How many bytes are necessary to store a MAC address? 

Me: six. 

Recruiter: right. 

Thought: _I figure I just earned the [Ethernet] badge..._

4\. Sort the time taken by: CPU register read, disk seek, context switch, system memory read. 

Me: CPU register read, system memory read, context switch, disk seek. 

Recruiter: right. 

Thought: _Typical Computer Science University (1st year) lectures._

5\. What is a Linux inode? 

Me: a unique file identifier for any given file system. 

Recruiter: wrong, it's file metadata. 

Me: the inode is an index uniquely identifying a file on a given filesystem, and you can lookup this index to fetch file attributes like size, time, owner and permissions; you can even add your own attributes on some file systems. 

Recruiter: wrong, not "attributes", it's "metadata". 

Thought: _"Metadata" is more informative than "file attributes", really?_

6\. What Linux function takes a path and returns an inode? 

Me: I wrote a custom LIBC for G-WAN, our app. server, but I can't remember any syscall returning an inode. 

Recruiter: stat(). 

Me: stat(), fstat(), lstat(), and fstatat() all return an error code, not an inode; they fill a _stat structure_ holding the file attributes discussed previously and not only the file's inode index. 

Recruiter: that's not the answer: the inode contains all the metadata. 

Thought: _Could Google have secretly licensed the nefarious _[Microsoft Tay AI bot_](http://uk.businessinsider.com/microsoft-deletes-racist-genocidal-tweets-from-ai-chatbot-tay-2016-3)?_

7\. What is the name of the KILL signal? 

Me: SIGKILL which #define is set to 9. 

Recruiter: no, it's "TERMINATE". 

Me: SIGTERM (15) is different from the KILL signal (9). 

Recruiter: that's not the answer I have on my sheet of paper. 

Thought: _I guess that's what happens when AI bots discover recreational drugs._

8\. Why Quicksort is the best sorting method? 

Me: It's not always the case, nor even suitable. 

Recruiter: Quicksort has the best big-O. 

Me: "big-O" ignores data storage latencies, topology, volume, available memory, and even the computational cost of every CPU instructions involved in a given implementation – instead, it merely counts the number of algorithmic operations! Big-O can be a valuable indication when designing algorithms but the best performing and scaling solution depends on the particular constraints of any specific problem and environment. 

Recruiter: wrong, you had to give me the Quicksort big-O score. 

Thought: _When will the OMS will recognize the tobacco-scandal patterns in the damages caused by Academia to public mental health? The Linux kernel (that Google relies on) opted for Heapsort rather than Quicksort... for its lower memory usage and more predictable execution time._

9\. There's an array of 10,000 16-bit values, how do you count the bits most efficiently? 

Me: you shift the bits right on all the 64-bit words, the Kernighan way. 

Recruiter: no. 

Me: there are faster methods processing 64-bit words with masks but I can't explain it over the phone, I must write code. 

Recruiter: the correct answer is to use a lookup table and then sum the results. 

Me: on which kind of CPU? Why not let me compare my code to yours in a benchmark? 

Recruiter: that's not the point of this test. 

Me: what's the point of this test? 

Recruiter: I have to check that you know the _right answers_. 

Thought: _How long is this crap going to last? A 8-bit lookup table can process bytes one after another, while the 64-bit mask-based method processes 8-byte words at a time (on top of that, modern CPU instructions even let you process 128-bit words with a 10x speed gain if portability is not a concern). As a 64-bit lookup table is out of reach for today's computers, there's no doubt on what is faster._

10\. What is the type of the packets exchanged to establish a TCP connection? 

Me: in hexadecimal: 0x02, 0x12, 0x10 – literally "synchronize" and "acknowledge". 

Recruiter: wrong, it's SYN, SYN-ACK and ACK; if Google is down you will need to know this to diagnose what the problem is. We will stop here because it's obvious that you don't have the necessary skills to write or review network applications. You should learn the Linux function calls, how the TCP/IP stack works, and what big-O means to eventually qualify if you are interviewed at a later time. Good luck, bye. 

Thought:_ When you have to read hexadecimal packet dumps to find what's happening, 3-letter mnemonics won't help you to troubleshoot a dead network service. Maybe Google should have stated that practice is not necessary for the job._

On another hand, my score is four on ten, that's better than my best Google pagerank** ever! 

* * *

(*) Google and TWD were both founded in 1998.  
(**) Google pagerank: the ultra-secret mathematical formula demonstrating that sponsored search results rank higher than reality can. 

  


  **Tip**: hiring people that know things that _you don't know_ helps more than hiring people who merely know what _everybody knows_. 

  


* * *
