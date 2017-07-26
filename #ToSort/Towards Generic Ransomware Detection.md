# Towards Generic Ransomware Detection

_Captured: 2016-05-01 at 00:08 from [objective-see.com](https://objective-see.com/blog/blog_0x0F.html)_

I'm not claiming these ideas are novel, nor unbeatable. My goal is simply to raise awareness about alternate means to help stymie the ransomware epidemic. Plus, attempting to write a tool that could generically protect my computer against OS X ransomware, seemed like a fun challenge! Finally, both this research and tool are version 1.0, meaning, likely room for improvement - so feedback is welcome :)

Outline  
** ›** [background](https://objective-see.com/blog/blog_0x0F.html)  
** ›** [ransomware on os x](https://objective-see.com/blog/blog_0x0F.html)  
** ›** [generic ransomware detection](https://objective-see.com/blog/blog_0x0F.html)  
** ›** [ransomWhere?](https://objective-see.com/blog/blog_0x0F.html)  
** ›** [future research](https://objective-see.com/blog/blog_0x0F.html)  
** ›** [conclusions](https://objective-see.com/blog/blog_0x0F.html)

Background  
Unless you've been living under an 'infosec rock', you're likely aware that ransomware is somewhat of a problem - to put it mildly. There are already claims that "2016 is shaping up as the year of ransomware" and that "this is basically becoming a national cyber emergency". And everywhere one looks, ransomware-related articles, tweets, and even FBI bulletins abound:

  * "OK, panic - newly evolved ransomware is bad news for everyone" ([arstechnica](http://arstechnica.com/security/2016/04/ok-panic-newly-evolved-ransomware-is-bad-news-for-everyone))   
  

  * "Adobe rolls out emergency update to counter ransomware threat" ([cnn](http://money.cnn.com/2016/04/08/technology/adobe-emergency-update))   
  

  * "CryptoWall 3.0 Ransomware Operators Made $325 Million" ([softpedia](http://news.softpedia.com/news/cryptowall-3-0-ransomware-operators-made-325-million-495582.shtml))   
  

  * "The FBI is providing indicators regarding businesses that were recently infected with a ransomware variant..." ([fbi 'flash' bulletin](http://proprivatus.com/wp-content/uploads/2016/02/flash-MC-000068-MW.pdf ))  
  

  * "The ransomware is that good... To be honest, we often advise people just to pay the ransom." ([fbi's cyber & counterintelligence program](https://nakedsecurity.sophos.com/2015/10/28/did-the-fbi-really-say-pay-up-for-ransomware-heres-what-to-do/)   
  

  * And how about this!?:   
  
![](https://objective-see.com/images/blog/blog_0x0F/elevatorRansomware.png)

  


...and don't think that just because you're on a Mac you're safe! Open-source proof-of-concept OS X ransomware is freely available [online](https://github.com/gdbinit/gopher), while recently the first 'in the wild' OS X ransomware, [KeRanger,](http://researchcenter.paloaltonetworks.com/2016/03/new-os-x-ransomware-keranger-infected-transmission-bittorrent-client-installer) emerged infecting thousands of Mac users. Moreover, recent ransomware attacks that utilized 0day exploits, were found to contain [Mac-specific exploit code](http://blog.trendmicro.com/trendlabs-security-intelligence/look-adobe-flash-player-cve-2016-1019-zero-day-vulnerability):

![](https://objective-see.com/images/blog/blog_0x0F/flash0day.png)

So hopefully we can agree that ransomware is clearly a problem, even on OS X. Moreover, with the massive financial incentives for hackers, it's surely to only increase in its prevalence. Sadly, existing anti-virus solutions fail to detect new samples, leaving most users completely unprotected. So what to do? panic? join the dark-side and create ransomware to make millions? naw...let's do something a little more productive (and responsible).

But first let's take a closer look at ransomware on OS X.

Ransomware on OS X  
The following is a brief, yet comprehensive history of ransomware that targets Mac computers.

**1 )** FBI 'ransomware' (july 2013)  
Detailed in a MalwareBytes Labs blog titled, "[FBI Ransomware Now Targeting Apple's Mac OS X Users"](https://blog.malwarebytes.org/threat-analysis/2013/07/fbi-ransomware-now-targeting-apples-mac-os-x-users/) this malicious code (obviously not from the FBI), 'locked' user's browser stating: "your browser has been blocked...you have been viewing or distributing prohibited Pornographic content...To unlock your computer and to avoid other legal consequences, you are obligated to pay a release fee of $300"

![](https://objective-see.com/images/blog/blog_0x0F/fbiScareware.png)

In reality, this browser-based code simply 'locked' the browser by creating 150 iFrames via Javascript:

![](https://objective-see.com/images/blog/blog_0x0F/fbiScarewareJS.png)

![](https://objective-see.com/images/blog/blog_0x0F/fbiScarewareIFrame.png)

Obviously the user could simply kill the browser process (or click the prompt 150 times!) to escape from the attack. And regardless, the attack did not (and could not) encrypt any of the user's personal data. So does this count as ransomware? Perhaps...however IMHO, the takeaway here is that attackers trying to extort money from OS X users via scare or ransomware-like tactics, is not new.

**2 )** OSX/FileCoder (june 2014)  
According to Kaspersky, FileCoder appeared as an [unfinished OS X ransomware specimen](https://securelist.com/blog/research/66760/unfinished-ransomware-for-macos-x). While it did contain logic to encrypt files and demand money from its victims, in reality it appeared somewhat nonfunctional: _"As, at the moment, Trojan-Ransom.OSX.FileCoder.a encrypts only its own files"_, Moreover, the Kaspersky researchers noted that the encryption key is stored within the trojan's binary and is static.

![](https://objective-see.com/images/blog/blog_0x0F/fileCoder.png)

**3 )** Gopher (sept. 2015)  
In 2015, Pedro Vilaca ([@osxreverser](https://twitter.com/osxreverser)) published a proof of concept ransomware named 'Gopher' to [github](https://github.com/gdbinit/gopher) He states:

_"Its goal is to demonstrate that there are really no special barriers in OS X against crypto ransomware. This menace hasn't arrived to OS X purely because of laziness from malware authors and scale, since it should be magnitudes more profitable against Windows targets."_

The code utilizes the [libsodium](https://github.com/jedisct1/libsodium) cryptography library and will encrypt all .docx files in the current user's home directory:

//code snippet(s) from gopher_encrypt/gopher_encrypt/main.m

NSString *extension = [[NSURL fileURLWithPath:filePath] pathExtension];  
if ([extension isEqualToString:@"docx"] == YES)  
{  
[targetFiles addObject:filePath];  
}

for (id object in targetFiles)  
{  
...  
fd = open([object UTF8String], O_RDWR);  
unsigned char *source_buf = mmap(0, filestat.st_size, PROT_READ, MAP_SHARED, fd, 0);  
unsigned char *buf = malloc(filestat.st_size + crypto_box_SEALBYTES);  
crypto_box_seal(buf, source_buf, filestat.st_size, session_pub_key);  
...  
}

**4 )** Mabouia (nov. 2015)  
Shortly after Pedro's ransomware PoC, another security research, Rafael Salema Marques, demonstrated yet another PoC ransomware for OS X. As far as I'm aware, source code was never released, however [analysis](http://www.symantec.com/connect/blogs/proof-concept-threat-reminder-os-x-not-immune-crypto-ransomware) states:

_"encrypting files on the infected computer and sending the encryption key to a command-and-control (C&C) server. The malware displays payment instructions on the infected computer, including a unique ID the victim would need to use to retrieve a decryption key."_

![](https://objective-see.com/images/blog/blog_0x0F/mabouia.jpg)

**5 )** GinX (feb. 2016)   
According to the writeup titled, "[OSX Ransomware Sold in the Underground"](http://www.infosecisland.com/blogview/24699-OSX-Ransomware-Offered-for-Sale-in-the-Underground.html), a _"relatively new vendor on an underground marketplace is now offering a new type of Ransomware, dubbed 'GinX...What makes 'GinX' relatively unique is that it does not only come in Windows-form, but also has an OSX version."_

![](https://objective-see.com/images/blog/blog_0x0F/ginx.jpg)

The writeup provides details from the vendor, who states:

_ "Once the file is executed it activates immediately and begins encrypting their files. This also can be set to a delay in minutes if required. Once the files are encrypted the target will be prompted that they have been infected with GinX RaaS along with instructions on how to make payment to get their files back. Just before the user is prompted it takes a picture via their internal webcam and displays it to the victim in the instructions file for added affect (Yes the webcam green light does come on). Default payment is required within 96 hours. After 96 hours has pass the files are no longer accessible. This prompt will appear once and once only." _

While these claims cannot be verified, this may be the first instance of a 'non-PoC' malware that maliciously encrypts files on an infected user's Mac.

**6 )** KeRanger (mar. 2016)   
Detected and [comprehensively analyzed](http://researchcenter.paloaltonetworks.com/2016/03/new-os-x-ransomware-keranger-infected-transmission-bittorrent-client-installer) by Claud Xiao ([@claud_xiao](https://twitter.com/claud_xiao)) of Palo Alto Networks, KeRanger is likely _"the first fully functional ransomware seen on the OS X platform [in the wild]."_ KeRanger infected the legitimate version of Transmission, a BitTorrent client for OS X. As it was both signed and hosted on Transmission's official site - it was able to infect several thousand unsuspecting Mac users.

Claud's writeup is technically in-depth and quite thorough - so if you're interested in the inner working of KeRanger, it's highly recommended. Here, we'll note that when run, after a certain period of dormancy it will encrypt all files under the /Users directory, as well as a variety of files (such as .doc, .jpg, etc), under /Volumes:

![](https://objective-see.com/images/blog/blog_0x0F/keRangerEncrypt.png)

In each directory that contains files encrypted by KeRanger (readily identified by the .encrypted extension), the ransomware will leave a README_FOR_DECRYPT.txt file that contains instructions on how to pay the ransom and recover the encrypted files:

![](https://objective-see.com/images/blog/blog_0x0F/keRangerReadMe.png)

Generic Ransomware Detection  
I don't claim to be an expert on ransomware, but after studying various specimens, a general (and obvious?) commonality seems to be that ransomware rapidly encrypts user files. (And after googling around, it appears that others allude to having perhaps [similar ideas](https://blog.malwarebytes.org/malwarebytes-news/2016/01/introducing-the-malwarebytes-anti-ransomware-beta/) \- at least for Windows). So to me, this rapid encryption of user files, seemed like a promising heuristic that could lead to the generic detection and prevention of ransomware. As such my hypothesis was:

"if we can monitor file I/O events and detect the rapid creation of encrypted files by untrusted processes, then ransomware may be generically detected"

To test this hypothesis, let's break it down into three separate sub-tasks:

  1. monitoring file I/O events
  

  2. determining if a file is encrypted
  

  3. determining if a process is untrusted

Each of these sub-tasks will be examined in detail. In culmination, they come to fruition in a new OS X tool, that is pitted against known ransomware in order to test the hypothesis.

» monitoring file i/o events  
The first piece of the 'generic ransomware detection' puzzle is the ability to monitor file I/O events. Such a capability will provide notifications of file creations or modifications, which in turn may be passed off to an encryption classification algorithm (step #2).

On OS X there are a variety of methods to monitor the file-system for file I/O events, each with its pros and cons. (note; as I wanted to avoid the complexities of ring-0 code, only user-mode methods are presented here).

**a )** dtrace   
dtrace can be used to monitor file or disk I/O events. In fact, OS X ships with a script to perform this exact behavior; /usr/bin/iosnoop:

#!/bin/sh  
##!/usr/bin/sh  
#  
# iosnoop - A program to print disk I/O events as they happen, with useful  
# details such as UID, PID, filename, command, etc.  
# Written using DTrace (Solaris 10 3/05).

Unfortunately, as of El Capitan (thanks to SIP), dtrace is essentially useless :/ Running iosnoop even as root will fail:

$ sudo /usr/bin/iosnoop  
dtrace: invalid probe specifier  
...  
: probe description io:::start does not match any probes

Of course SIP could be disabled, but this IMHO, isn't a good idea from a security point of view, nor feasible as a requirement for an end-user tool. As such, using dtrace was out of the question.

**b )** fs_usage  
With dtrace out of contention, let's looked into the well known OS X file monitoring utility /usr/bin/fs_usage. Unlike dtrace, fs_usage works fine on the latest versions of OS X. It is also [open-source](http://opensource.apple.com//source/system_cmds/system_cmds-671.10.3/fs_usage.tproj). In order to receive file I/O notifications, fs_usage utilizes kernel event tracing (kdebug). The tracing facility is detailed in Amit Singh's "Mac OS X Internal" book (see 6.8.7 'Fine-Grained Kernel Event Tracing', pp. 625), as well as Jonathan Levin's "Mac OS X and iOS Internals: To the Apple's Core" book (see 'KDEBUG , pp 165). Though Levin validly notes, the kdebug feature is "poorly documented", examples in the books, as well as reading Apple's source code make it fairly easy to create a custom file I/O monitor.

For example, to read kdebug messages (after enabling kdebug via sysctl/KERN_KDENABLE), invoke:

//code snippet /system_cmds-671.10.3/fs_usage.tproj/fs_usage.c

mib[0] = CTL_KERN;  
mib[1] = KERN_KDEBUG;  
mib[2] = KERN_KDREADTR;

sysctl(mib, 3, my_buffer, &needed, NULL, 0);

//parse 'my_buffer' for kdebug messages  
// ->look for those related to file i/o

Running this custom fs_usage code, one can observe file I/O events, such as those related to the KeRanger ransomware (kernel_service), creating an encrypted file:

$ sudo ./custom_fsUsage  
kdebug event (open):   
process: /Users/0wned/Library/kernel_service  
path: /Users/0wned/Documents/resume.docx.encrypted  
file descriptor: 8

kdebug event (write):  
process: /Users/0wned/Library/kernel_service  
file descriptor: 8

kdebug event (close):  
process: /Users/0wned/Library/kernel_service  
file descriptor: 8

Though it appeared that using kdebug to trace file I/O notification could work to detect the creation of files - it has a rather problematic limitation; only one task (process) can use the trace facility at a time. Thus, if a ransomware detection tool is constantly monitoring file I/O via the kdebug facility , and the user attempts to execute any other tools that uses kdebug (e.g. fs_usage), it will fail:

$ sudo fs_usage  
fs_usage: the trace facility is currently in use...  
fs_usage, sc_usage, and latency use this feature.

As creating a tool that breaks or constrains legitimate OS tools seemed unwise, another solution was sought.

**c )** OpenBSM  
OpenBSM is [described](http://www.trustedbsd.org/openbsm.html) as a _"portable, open source implementation of Sun's Basic Security Module (BSM) security audit API"_. It is supported on OS X (and [open-source](http://opensource.apple.com//source/bsm/bsm-13)) and can be used to monitor file I/O events.

While there, isn't a ton of documentation or examples of using this framework/API for auditing file I/O events, a few blog posting such as "[OpenBSM auditd on OS X: these are the logs you are looking for"](http://ilostmynotes.blogspot.com/2013/10/openbsm-auditd-on-os-x-these-are-logs.html) and [Audit in a OS X System"](http://www.scip.ch/en/?labs.20150108) were very informative.

To use OpenBSM to monitor for events (such as file I/O), first open /dev/auditpipe. Then use the ioctl function to to specify parameters and configurations, such as the 'event' classes one is interested in. Various event classes, (basically the audit events one is interested in), are defined in /etc/security/audit_class:

$ less /etc/security/audit_class  
#  
# $P4: //depot/projects/trustedbsd/openbsm/etc/audit_class#6 $  
#  
0x00000000:no:invalid class  
0x00000001:fr:file read  
0x00000002:fw:file write  
0x00000004:fa:file attribute access  
0x00000008:fm:file attribute modify  
0x00000010:fc:file create  
0x00000020:fd:file delete  
0x00000040:cl:file close

For example, to monitor file I/O events (such as file closure events - which can then be passed to the encryption classification algorithm), specify an event class of: 0x00000040:cl:file close   
Then in a loop, call:

Its important to note Apple's docs for [au_read_rec()](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man3/au_read_rec.3.html) are incorrect. They state; _the "au_read_rec() functions return 0 on success, or -1."_ However, in actuality, au_read_rec() returns the number of bytes read!

Once au_read_rec() has returned with a buffer of audit events, invoke the au_fetch_tok function on the buffer of audit events, to parse each 'record.' For example, one can extract the process responsible for event, as well other pertinent information such as the file path (in the case of monitoring file close events).

Compiling and executing this code, allows file I/O events to be monitored (such as the Gopher ransomware, as it encrypts files in place):

$ sudo ./custom_openBSM  
audit record (file close):  
process: /Users/0wned/Desktop/gopher_encrypt  
path: /Users/0wned/Documents/resume.docx

audit record (file close):  
process: /Users/0wned/Desktop/gopher_encrypt  
path: /Users/0wned/Documents/taxes.docx

Ok so this looked promising - any downsides? Not really; though preliminarily testing indicated it was a touch CPU 'intensive' (continually using about 1% of the CPU). However, I ultimately decided to go with another method (fsevents), simply as it has proven successful, efficient, and reliable in another Objective-See tool (hooray for code reuse)!

**d )** fsevents (API)  
Apple documentation "[Using the File System Events API"](https://developer.apple.com/library/mac/documentation/Darwin/Conceptual/FSEvents_ProgGuide/UsingtheFSEventsFramework/UsingtheFSEventsFramework.html#//apple_ref/doc/uid/TP40005289-CH4-SW4) describes an API that one can utilize to receive notification _"when files or directories are created, modified, or removed"_...sounds promising, as a mechanism for monitoring file I/O events.

In short, a process that is interested in file I/O events should invoke the FSEventStreamCreate function to create a 'file event stream.' Then, as Apple notes, _"to start receiving callbacks you must also call FSEventStreamScheduleWithRunLoop() and FSEventStreamStart()"_.

However, there is an immediate downside to using the API. AFAIK, there is no way to identify the process that generated the file I/O event. I posted a question about this on stackoverflow, "[FSEvents - get PID of the process that performed the operation?"](http://stackoverflow.com/questions/26049915/fsevents-get-pid-of-the-process-that-performed-the-operation  ) in 2014...but nobody answered :(

![](https://objective-see.com/images/blog/blog_0x0F/stackoverflow.png)

For generic ransomware detection, it's imperative to identify the process responsible for generating the file I/O event (to see if its an untrusted process that's rapidly encrypting user files). So using the official API is a clearly a no go. Turns out though, fsevents can be directly accessed, which provides the means to identify the responsible process.

**f )** fsevents (direct)  
One of my other OS X security tools, [BlockBlock](https://objective-zee.com/products/blockblock.html) continually monitors common persistence locations and displays an alert whenever a persistent component is added to the OS. It uses fsevents directly to receive file I/O events related to persistence.

Again, both Amit and Levin provide insight into this mechanism, both thru code samples; [fslogger](http://osxbook.com/software/fslogger/download/fslogger.c) and [filemon](http://www.newosxbook.com/src.jl?tree=listings&file=3-filemon.c).

By perusing these code samples, it is pretty easy to understand how to monitor file I/O event via direct access to the fsevents device. First open the /dev/fsevents device:

Then, specify what file I/O events one is interested in. The events and their values can be found [online](http://opensource.apple.com//source/xnu/xnu-3248.20.55/bsd/sys/fsevents.h):

//from /bsd/sys/fsevents.h  
#define FSE_INVALID -1  
#define FSE_CREATE_FILE 0  
#define FSE_DELETE 1  
#define FSE_STAT_CHANGED 2  
#define FSE_RENAME 3  
#define FSE_CONTENT_MODIFIED 4  
#define FSE_EXCHANGE 5  
#define FSE_FINDER_INFO_CHANGED 6  
#define FSE_CREATE_DIR 7  
#define FSE_CHOWN 8  
#define FSE_XATTR_MODIFIED 9  
#define FSE_XATTR_REMOVED 10  
#define FSE_DOCID_CREATED 11  
#define FSE_DOCID_CHANGED 12

#define FSE_MAX_EVENTS 13  
#define FSE_ALL_EVENTS 998

The events of interest, can be set via an ioctl call (request: FSEVENTS_CLONE). Then code can simply read off the device in a loop to begin receiving events. Parsing the returned data is a touch tricky, as it contains variable length structures depending on the events and the data each contains. However, the previously mentioned code samples both contain example of parsing code.

Once parsing logic is complete, file I/O events can be read and processed in an efficient (<0.5% CPU usage) and reliable manner. For example, one can register for FSE_CONTENT_MODIFIED events, to detect the closure of files that have been modified (for example by the KeRanger ransomware):

$ sudo ./custom_fsEvents  
fsEvent (FSE_CONTENT_MODIFIED):   
process: /Users/0wned/Library/kernel_service  
path: /Users/0wned/Documents/resume.docx.encrypted

$ sudo ./custom_fsEvents  
fsEvent (FSE_CONTENT_MODIFIED):   
process: /Users/0wned/Library/kernel_service  
path: /Users/0wned/Documents/taxes.docx.encrypted

In terms of downsides, Apple claims using fsevents (directly) is unsupported. However, they continue to directly use it, so why can't we!?

//code snippet from bsd/vfs/vfs_fsevents.c  
if (!strncmp(watcher->proc_name, "fseventsd", sizeof(watcher->proc_name)) ||   
!strncmp(watcher->proc_name, "coreservicesd", sizeof(watcher->proc_name)) ||  
!strncmp(watcher->proc_name, "mds", sizeof(watcher->proc_name))) {

watcher->flags |= WATCHER_APPLE_SYSTEM_SERVICE;

} else {

printf("fsevents: watcher %s (pid: %d) -  
Using /dev/fsevents directly is unsupported. Migrate to FSEventsFramework\n",  
watcher->proc_name, watcher->pid);

}

It's also important to note, that when specifying the queue size of events to read ('event_queue_depth' member of the struct fsevent_clone_args), a large value (say 4096+), may cause other system processes such as mds to drop events. In other words, don't be too greedy!

As the downsides to this method are minimal, coupled with the fact that [BlockBlock](https://objective-zee.com/products/blockblock.html) already successfully uses fsevents to monitor file I/O events - this method was selected as the first piece of the 'generic ransomware detection' puzzle.

» determining if a file is encrypted  
For generic ransomware detection, one is only interested in file I/O events that deal with the creation of encrypted files. As such, determining whether a file is encrypted or not, is paramount.

In the past, I (as well as many others!) have written code that used entropy analysis to generically detect packed malware. This method computes a distribution of the number of unique byte values in a file as a basic measure of randomness. Generally speaking, packed malware has a much higher distribution of unique bytes (i.e. it's more random) that a normal executable.

Based on my past experience I first attempted to generically detect encrypted files via basic entropy calculation. However, while this could effectively differentiate between and encrypted and 'plain text' files - it was not able to able to reliably tell the difference between an encrypted and compressed file (e.g. a .zip archive), as these both high levels of apparent randomness. (Which is why, always compress; then encrypt).

The following table shows the entropy calculations for various compressed file types. It should be noted that an 8 (due to the use of log2 in the entropy computation), is the highest possible level of randomness. As the can be seen in the 'Entropy' column, all compressed files have a high level of randomness:

File Type Entropy

test.lzma
lzma
7.874  


blockBlock.zip
zip
7.93  


python3.3.zip
zip
7.989  


dproto_0_8_72.rar
rar
7.998  


I assumed somebody smarter than I had already figured this out, so off to Google; and success: "[Differentiate Encryption From Compression Using Math"](http://www.devttys0.com/2013/06/differentiate-encryption-from-compression-using-math). As described in the blog, mathematically constructs such as Chi Square distributions and Monte Carlo pi approximations can be leveraged to identify if a file is truly encrypted (versus compressed). In short, such constructs quantify the true randomness of data, and are "more sensitive to deviations in randomness" when compared to simply entropy analysis.

From the blog:

_"Chi square distribution is used to determine the deviation of observed results from expected results; for example, determining if the outcomes of 10 coin tosses were acceptably random, or if there were potentially external factors that influenced the results. Substantial deviations from the expected values of truly random data indicate a lack of randomness.   
  
Monte Carlo pi approximation is used to approximate the value of pi from a given set of random (x,y) coordinates; the more unique well distributed data points, the closer the approximation should be to the actual value of pi. Very accurate pi approximations indicate a very random set of data points.   
  
Since each byte in a file can have one of 256 possible values, we would expect a file of random data to have a very even distribution of byte values between 0 and 255 inclusive. We can use the chi square distribution to compare the actual distribution of values to the expected distribution of values and use that comparison to draw conclusions regarding the randomness of data.   
  
Likewise, by interpreting sets of bytes in a file as (x,y) coordinates, we can approximate the value of pi using Monte Carlo approximation. We can then measure the percentage of error in the approximated value of pi to draw conclusions regarding the randomness of data."_

Using a pseudorandom number sequence test program, [ent](http://www.fourmilab.ch/random/) as suggested in the blog, its fairly easy to calculate entropy, Chi Square distribution, and Monte Carlo pi approximations. The blog, and other sources such as "[How to determine if some blob is encrypted or not"](http://sgros.blogspot.com/2014/12/how-to-determine-if-some-blob-is.html), suggest empirical values or 'rules' based on these calculations that can reliably determine if a file is truly encrypted:

  * Large deviations in the chi square distribution, or large percentages of error in the Monte Carlo approximation are sure signs of compression.   
  

  * Very accurate pi calculations (< .01% error) are sure signs of encryption.   
  

  * Higher chi values (> 300) with lower pi errors (< .03%) are indicative of encryption.   
  


Of course, I wanted to test this out, as believing everything you read on the internet may get you into trouble ;) As such, I wrote a simple program that (which utilized ent), to compute simple entropy, Chi Square distribution, and Monte Carlo pi approximations:

$ ./doMath blog_0xF.html  
input file: blog_0xF.html

results:  
entropy = 5.119934  
chi square distribution for 39073 samples is 385760.14  
monte carlo value for pi is 4.000000000 (error 27.32 percent)

$ ./doMath python3.3.zip  
input file: python3.3.zip

results:  
entropy = 7.989483  
chi square distribution for 2649206 samples is 55686.15  
monte carlo value for pi is 3.182495572 (error 1.30 percent)

$ ./doMath malware.zip.encrypted  
input file: malware.zip.encrypted

results:  
entropy = 7.999539  
chi square distribution for 10362098 samples is 7092.85  
monte carlo value for pi is 3.148339101 (error 0.21 percent)

The first time executing the program (doMath), this blog's html page was passed in as input. As the entropy is quite low (5.11), and the monte carlo pi approximation is really far off (27.32% error), clearly indicate the file is not encrypted.

Following this, the program was fed a compressed (zipped) file; python3.3.zip. Here, the entropy is extremely high (7.989483), so from computation alone, it cannot be reliably determined whether the file is compress or encrypted. However, looking at the Chi Square distribution (55686.15) - that's a rather large deviation. Moreover, the Monte Carlo pi approximation (error 1.30%), is still considered high (by the 'compression vs. encrypted' rules mentioned above). Thus, its easy to classify this file as compressed.

Finally, a password-protected zip file (malware.zip.encrypted) was provided as input. From the output of the program, its clear to see that this file is encrypted! Why? First, the extremely high entropy (7.999539) means its not a 'plain' file (i.e. its either compressed or encrypted). Looking at the Chi Square distribution (7092.85) and Monte Carlo pi approximation (0.21%), this aligns with the final 'rule': _"Higher chi values (> 300) with lower pi errors (< .03%) are indicative of encryption"_.

The following table shows a few more results; first on a set of files prior to a ransomware infection, then after both Gopher and KeRanger infections.

File Entropy Chi Square Monte Carlo Pi Approx

**original files**

logo.png
7.91
7383.25
3.04%

blockBlock.zip
7.93
5482.31
1.05%

blog_0xF.html
5.12
385760.14
27.32%

**ransomware'd files (gopher)**

logo.png
7.99
250.05
1.30%

blockBlock.zip
7.99
259.99
0.33%

blog_0xF.html
7.99
236.03
0.23%

**ransomware'd files (keranger)**

logo.png.encrypted
7.99
235.03
0.15%

blockBlock.zip
7.99
256.71
0.79%

blog_0xF.html
7.99
127.28
0.01%

As may be seen, when the various files (even compressed ones, i.e .png and .zip files) were encrypted with ransomware, both the Chi Square distributions and Monte Carlo pi approximations dropped significantly. Based on further empirical testing of files on my Mac computer, I went with the following code to classify if files are encrypted or not:

//determine if a file is encrypted  
// ->high entropy and  
// a) very low pi error  
// b) low pi error and low chi square  
BOOL isEncrypted(NSString* path)  
{  
//flag  
BOOL encrypted = NO;

//test results  
NSMutableDictionary* results = nil;

//do computations  
// ->entropy, chi square, and monte carlo pi approx  
results = testFile(path);  
if(nil == results)  
{  
//bail  
goto bail;  
}

//encrypted files have super high entropy  
// ->so ignore files that have 'low' entropy  
if([results[@"entropy"] doubleValue] < 7.95)  
{  
//ignore  
goto bail;  
}

//monte carlo pi error gotta be less than 1.5%  
if([results[@"montecarlo"] doubleValue] > 1.5)  
{  
//ignore  
goto bail;  
}

//when monte carlo pi error is above 0.5  
// ->gotta have low chi square as well  
if( ([results[@"montecarlo"] doubleValue] > 0.5) &&  
([results[@"chisquare"] doubleValue] > 500) )  
{  
//ignore  
goto bail;  
}

//encrypted file!  
// ->file as very low pi error, or, lowish pi error *and* low chi square  
encrypted = YES;

//bail  
bail:

return encrypted;  
}

...and yes, I'll be the first to admit that this could most likely be improved! However, feeding a wide range of files ('plain', compresses, and encrypted), thru this code confirmed the accuracy of this method in generically detecting encrypted files. It should be notes that as this 'isEncrypted' algorithm is tuned to favor false positives over false negatives, occasionally a file would be misclassified as encrypted (for example, the infrequent .png image). As discussed in the [limitations](https://objective-see.com/blog/blog_0x0F.html) section - several 'false-positive' reduction mechanisms were added in attempt to reduce misclassifications.

» determining if a process is untrusted  
At this point the code could reliably detect the creation of files, and classify them as encrypted or not. So are we done? No! It turns out that somewhat frequently legitimate processes create encrypted files (e.g. 1Password, etc). Of course such legitimate scenarios should obviously be ignored, and not flagged as ransomware.

Determining wether a process is 'legitimate' (and thus should be trusted) is not an exact science. The goal was to take an approach that would allow trusted processes to encrypt files at will without being flagged, while ensuring that ransomware would (hopefully) always be detected. As such, the following simple algorithm was created in an attempt to fulfil this goal:

  1. Any process's binary signed by Apple proper is inherently trusted.   
That is to say, those signed by:  
Authority=Software Signing  
Authority=Apple Code Signing Certification Authority  
Authority=Apple Root CA  
  
note, this does not include binaries signed with an Apple developer ID!   
  

  2. Applications already installed when the tool is first run are inherently trusted. 

Everything else is assumed to be untrusted, and thus will generate an alert if detected rapidly generating encrypted files. Of course these trust assumptions may be abused by ransomware with a priori knowledge of them. For example, if the ransomware injects itself into a trusted Apple process at runtime to perform its encryption, this would likely allow it to remain undetected. Such limitations (and others) are more fully articulated [below](https://objective-see.com/blog/blog_0x0F.html)

Determinging if a binary is signed by Apple is fairly straightforward via code signing checks:

//determine if a file is signed by Apple proper  
BOOL isAppleBinary(NSString* path)  
{  
//flag  
BOOL isApple = NO;

//code  
SecStaticCodeRef staticCode = NULL;

//signing reqs  
SecRequirementRef requirementRef = NULL;

//status  
OSStatus status = -1;

//create static code  
status = SecStaticCodeCreateWithPath((__bridge CFURLRef)([NSURL fileURLWithPath:path]),  
kSecCSDefaultFlags, &staticCode);  
if(STATUS_SUCCESS != status)  
{  
//bail  
goto bail;  
}

//create req string w/ 'anchor apple'  
status = SecRequirementCreateWithString(CFSTR("anchor apple"), kSecCSDefaultFlags,   
&requirementRef);  
if( (STATUS_SUCCESS != status) ||  
(requirementRef == NULL) )  
{  
//bail  
goto bail;  
}

//check if file is signed by apple by checking if it conforms to req string  
// note: ignore 'errSecCSBadResource' as lots of signed Apple binaries return this :/  
status = SecStaticCodeCheckValidity(staticCode, kSecCSDefaultFlags, requirementRef);  
if( (STATUS_SUCCESS != status) &&  
(errSecCSBadResource != status) )  
{  
//bail  
// ->just means binary isn't signed by apple  
goto bail;  
}

//ok, happy  
// ->file is signed by Apple proper  
isApple = YES;

//bail  
bail:

//free req reference  
if(NULL != requirementRef)  
{  
//free  
CFRelease(requirementRef);  
}

//free static code  
if(NULL != staticCode)  
{  
//free  
CFRelease(staticCode);  
}

return isApple;  
}

In order to enumerate ('baseline') all applications that are already installed on the system (and thus should be inherently trusted), one can make use of the system_profiler tool. When system_profiler (found in /usr/sbin) is executed with the 'SPApplicationsDataType' and 'xml' arguments, it will enumerate most installed applications output its finding in an easily digestible plist (xml):

$ system_profiler SPApplicationsDataType -xml  
<?xml version="1.0" encoding="UTF-8"?>  
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">  
<plist version="1.0">  
<array>  
<dict>

<key>_items</key>  
<array>  
<dict>  
<key>_name</key>  
<string>Console</string>  
<key>has64BitIntelCode</key>  
<string>yes</string>  
<key>lastModified</key>  
<date>2016-03-26T22:29:02Z</date>  
<key>obtained_from</key>  
<string>applev/string>  
<key>path</key>  
<string>/Applications/Utilities/Console.app</string>  
<key>runtime_environment</key>  
<string>arch_x86</string>  
<key>signed_by</key\>  
<array>  
<string>Software Signing</string>  
<string>Apple Code Signing Certification Authority</string>  
<string>Apple Root CA</string>  
</array>  
<key>version</key>  
<string>10.11</string>  
</dict>

....

RansomWhere?  
Recall the initial hypothesis:

"if we can monitor file I/O events and detect the rapid creation of encrypted files by untrusted processes, then ransomware may be generically detected"

Now, we have all the pieces, or sub-tasks to test this. Time to simply put them all together into a tool named RansomWhere? Hopefully this tool can solve the generic ransomware detection puzzle!

In order to provide generic ransomware protection, RansomWhere? performs the following actions:

  1. persist  

  

  2. baseline the system (first time only)  

  

  3. classify running processes  

  

  4. begin file I/O event monitoring  

  

  5. process file I/O events forever:  
  

    1. is path of interest?  

    2. is process trusted?  

    3. is file encrypted?  

    4. is (untrusted) process rapidly creating encrypted files?   

  
note: if the answer is 'NO' to any of these, loop to #5   
  

    5. suspend process as its likely ransomware  

    6. alert the user and handle the response (resume/terminate)  


Let's take a closer look at each of these.

**1 )** persist  
First, RansomWhere? needs to ensure it is automatically started and is always running (in order to provide continual protection). This is easily achieved by installing it as a launch daemon, and setting the 'RunAtLoad' key to 'true'. A side benefit of running as a launch daemon is that it can run as root, which provides some protections against non-privileged ransomware. For example, if the ransomware is not root, it cannot unload the launch daemon (to proactively thwart detection).

$ less /Library/LaunchDaemons/com.objective-see.ransomwhere.plist

<?xml version="1.0" encoding="UTF-8"?>  
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">  
<plist version="1.0">  
<dict>  
<key>Label</key>  
<string>com.objective-see.ransomwhere</string>  
<key>ProgramArguments</key>  
<array>  
<string>/Library/RansomWhere/RansomWhere</string>  
</array>  
<key>RunAtLoad</key>  
<true/>  
</dict>  
</plist>

**2 )** baseline the system (first time only)  
The first time RansomWhere? is started, it will enumerate all installed applications. As previously mentioned, such applications will be inherently trusted, and can be enumerated via the system_profiler tool.

This may take a minute or so to execute, but is only executed the first time. It's important to note that the system_profiler tool may miss several installed applications (or rather application components). For example it appears to ignore application login items (for details on application login items see: ['Modern Login Items'](http://martiancraft.com/blog/2015/01/login-items)). As such, the system_profiler is supplemented by manually searching the /Applications directory for any application login items. Also, the system_profiler utility does not enumerate non-application binaries (for example OS binaries found in /usr/bin). The initial version of RansomWhere? does not baseline these. However, as most non-application binaries belong to Apple proper, they are inherently trusted, and thus 'ignored' regardlessly. RansomWhere? saves its list of baselined binaries into /Library/RansomWhere/installedApps.plist. This file (and directory) is set to be owned by root, to ensure that non-privileged ransomware cannot tamper with it.

**3 )** classify running processes  
Runtime profiling illustrated that process classification (via verification of code signatures), is one of the most CPU intensive operations the RansomWhere? performs. Thus in order to increase the speed at which RansomWhere? can process file I/O events (i.e. ignoring those that are generated by trusted processes), this classification is performed 'up front' as much as possible. In terms of classification, all running processes signed by Apple proper are trusted, while others (unless they existed when the system was baselined, or have been explicitly trusted by the user), are not.

**4 )** begin file I/O event monitoring  
RansomWhere? then spins off a high-priority thread to monitor file I/O events via fsevents. Recall that when using fsevents, one must specify a mask of which file I/O event types are of interest. So what event type(s) should RansomWhere? register for in order to detect the creation of encrypted files? Well, Amit's book (pp. 1416) describes the various event types, including FSE_CONTENT_MODIFIED:

This looks to be the perfect candidate - as it essentially says, _"hey, a file was just closed that had been modified"_ allowing RansomWhere? to then examine said file, to see if it's encrypted and created by an untrusted process (i.e. likely ransomware).

The initialization code to register for FSE_CONTENT_MODIFIED via fsevents is presented below:

//open the fsevents device  
fs = open("/dev/fsevents", O_RDONLY);

//explicitly init all events to ignore  
memset(events, FSE_IGNORE, FSE_MAX_EVENTS);

//report FSE_CONTENT_MODIFIED  
events[FSE_CONTENT_MODIFIED] = FSE_REPORT;

//clear out struct  
memset(&clonedArgs, 0x0, sizeof(clonedArgs));

//set fs to the clone  
clonedArgs.fd = &clonedFS;

//set queue depth  
clonedArgs.event_queue_depth = 1024;

//set list  
clonedArgs.event_list = events;

//set size of list  
clonedArgs.num_events = FSE_MAX_EVENTS;

//clone descriptor  
ioctl(fs, FSEVENTS_CLONE, &clonedArgs);

**5 )** process file I/O events forever  
Now, RansomWhere? can simply call read() in a loop to process FSE_CONTENT_MODIFIED file I/O events forever.

//kernel file-system event struct  
typedef struct kfs_event_a  
{  
uint16_t type;  
uint16_t refcount;  
pid_t pid;  
} kfs_event_a;

//kernel file-system event args struct  
typedef struct kfs_event_arg  
{  
uint16_t type;  
uint16_t pathlen;  
char data[0];  
} kfs_event_arg;

//process file system (FSE_CONTENT_MODIFIED) events foreverz  
while(YES)  
{  
//read 'em  
bytesRead = read(cloned_fsed, fsEvents, BUFSIZE);

//parse events  
// ->just need pid and file path  
while(bufferOffset < bytesRead)  
{  
//init pointer to current event struct  
struct kfs_event_a *fse = fsEvents + bufferOffset;

//init args (immediately following event struct)  
struct kfs_event_arg *fseArgs = fse + sizeof(struct kfs_event_a);

//process id: fse->pid

//file path: fse_arg->data

...  
}  
...  
}

**5a )** is path of interest?  
Whenever a new FSE_CONTENT_MODIFIED file I/O event is received, the tool first checks if it's a path of interest. Currently, for efficiency reasons, only files within ('under') /Users are watched. That is to say, if a file is created in /tmp, etc, it will be ignored and processing of that specific file event will cease. However, if the file is created under /Users, processing continues. (The assumption here is ransomware will encrypt user's files likely within the same location/directory).

**5b )** is process trusted?  
If the file path is of interest, RansomWhere? inserts the event in an queue for continued processing. A secondary thread continually processes such events off the queue. The first check performed (by the queue thread) on a dequeued event is whether it was generated by a trusted process (signed by Apple proper, baselined, etc):

//SKIP  
// ->events generated by OS X apps (signed by Apple proper)  
if(YES == event.binary.isApple)  
{  
//bail  
goto bail;  
}

//SKIP  
// ->events generated by apps baselined/prev. installed apps  
if(YES == event.binary.isBaseline)  
{  
//bail  
goto bail;  
}  
...

//file event generated by untrusted process!  
// ->keep processing...

As the code shows, if the FSE_CONTENT_MODIFIED file I/O event was generated by a trusted process it is ignored. On the other hand if the event was generated by an untrusted process, processing continues.

**5c )** is file encrypted?  
Assuming the file I/O event was generated by an untrusted process, processing continues. Now, comes the check to determine if the file is encrypted. This is accomplished via the previously described mathematical constructs (Chi Square distribution, Monte Carlo pi approximation, etc). After this step, RansomWhere? will know if the file created (or modified) is encrypted or not. Unencrypted files mean the file I/O event should be ignored, while if the file is indeed encrypted, processing continues.

**5d )** is (untrusted) process rapidly creating encrypted files?  
At this point, an untrusted process has been detected creating an encrypted file. Does this indicate ransomware? Perhaps...but it could also be a legitimate application (installed after RansomWhere? baselined the system) that is simply creating an encrypted file. Recall that ransomware has the characteristic of rapidly encrypting many files. As such, RansomWhere? keeps track of both when, and how many encrypted files an untrusted process has/is creating. When a threshold it hit (that takes into account both the speed and number of encrypted files generated), RansomWhere? takes action!

**5e )** suspend process as its likely ransomware  
When an untrusted process is observed rapidly creating encrypted files, RansomWhere? suspends the process via a SIGSTOP signal:   
**5f )** alert the user and handle the response (resume/terminate)  
Once the suspected ransomware process has been suspended, RansomWhere? alerts the user:

![](https://objective-see.com/images/blog/blog_0x0F/alertKeRanger.png)

Programmatically this is accomplished via the CFUserNotificationDisplayAlert function, which allows a daemon process (running as root, not in the UI session), to display an alert the user:

//show alert  
// ->will block until user interaction, with user's response saved in 'response' var  
CFUserNotificationDisplayAlert(0.0f, kCFUserNotificationStopAlertLevel, (CFURLRef)self.icon, NULL, NULL, title, body, (__bridge CFStringRef)@"Terminate", (__bridge CFStringRef)@"Allow", NULL, &response);

Alerts shown by RansomWhere? contain two important pieces of information; the process that RansomWhere? has suspended (until the user allows or terminates it), and the list of encrypted files that the process has created. If the user trusts the process, or the files created by the process are legitimate, they should click 'allow' to allow the program to continue executing in an unabated manner. On the other hand, if the user does not recognize the process or the files it is creating, they should click 'terminate' to kill it.

The following list summarizes the 'allow' and 'terminate' actions:

  * 'allow'  
Tells RansomWhere? it's ok to let the process continue running. This will be persistently remembered; the user will never be alerted about this binary again.  

  

  * 'terminate'  
Tells RansomWhere? to kill the process. As this action is a little more drastic, RansomWhere?, (by design) will not remember such actions. Thus if the terminated process is ran again, it will cause another alert.  


In code, the user's response is handled as so:

//terminate process  
if(PROCESS_TERMINATE == response)  
{  
//terminate  
kill(event.processID.intValue, SIGKILL);  
}

//resume process  
else  
{  
//resume  
kill(event.processID.intValue, SIGCONT);  
}

And that's RansomWhere? in a nutshell! For more details on installing and using the tool; see its [product page](https://objective-see.com/products/ransomwhere.html).

» testing & results  
So the million dollar question, "does RansomWhere? generically detect and thwart OS X ransomware?" Well considering there are only a few (ok, two) pieces of publicly available functional OS X ransomware, the breadth of testing is somewhat limited. However the answer looks like "YES"!

First; RansomWhere? vs. the proof-of-concept OS X malware; Gopher. Recall that Gopher encrypts all .docx files in the current user's directory. First, I downloaded a handful of random documents from the internet (google search: filetype:docx):

![](https://objective-see.com/images/blog/blog_0x0F/docx.png)

Then, once RansomWhere? was installed and fully initialized (look for 'OBJECTIVE-SEE RANSOMWHERE?: completed initializations; monitoring engaged!' in the system log), Gopher was executed - and began its encryption:

./gopher_encrypt -e  
[DEBUG] crypto_box_keypair result: 0  
[DEBUG] Session public key:  
\x70\xc7\x61\xdc\x38\xed\x89\x5e\x6b\x06\x1a\xdc...

gopher_encrypt[11027:11140122] /Users/0wned  
gopher_encrypt[11027:11140122] Target is /Users/0wned//Documents/AII_2190_0001.docx  
[DEBUG] Success encrypting!  
gopher_encrypt[11027:11140122] Target is /Users/0wned//Documents/Customers.docx  
[DEBUG] Success encrypting!  
gopher_encrypt[11027:11140122] Target is /Users/0wned//Documents/hands_on_lab.docx  
[DEBUG] Success encrypting!  
gopher_encrypt[11027:11140122] Target is /Users/0wned//Documents/Manual_469537_7.docx

[1]+ Stopped ./gopher_encrypt -e

Hooray; RansomWhere? generically detected (and suspended) Gopher!

![](https://objective-see.com/images/blog/blog_0x0F/alertGopherDocx.png)

You might be wondering, why Gopher was able to continue for a short while, successfully encrypting hands_on_lab.docx before being stopped. In short, due to the way RansomWhere? is implemented, it's slightly reactive - see the [limitations](https://objective-see.com/blog/blog_0x0F.html) section below for details.

Since Gopher is open-source, I then tweaked it to be more generic to instead encrypt all user files (note: no other changes were made). I removed the .docx files and placed a random assortment of file types into the ~/Documents folder. Then, Gopher was re-ran:

./gopher_encrypt -e  
[DEBUG] crypto_box_keypair result: 0  
[DEBUG] Session public key:  
\x86\x24\x9b\x88\x4d\x58\x0d\xe9\x8e\x47\x1d....

gopher_encrypt[6165:31376] /Users/0wned  
gopher_encrypt[6165:31376] Target is /Users/0wned//Documents/logo.psd  
[DEBUG] Success encrypting!  
gopher_encrypt[6165:31376] Target is /Users/0wned//Documents/novel.txt  
[DEBUG] Success encrypting!  
gopher_encrypt[6165:31376] Target is /Users/0wned//Documents/picture.jpg  
[DEBUG] Success encrypting!  
gopher_encrypt[6165:31376] Target is /Users/0wned//Documents/taxes.zip

[1]+ Stopped ./gopher_encrypt -e

Again; detection success!

![](https://objective-see.com/images/blog/blog_0x0F/alertGopher.png)

Next up, RansomWhere? vs. KeRanger. Recall KeRanger encrypts all user files into .encrypted files (e.g. logo.psd -> logo.psd.encrypted). Also, it may lay dormant for awhile (running as task named kernel_service), before executing its ransomware logic:

$ ps aux | grep -i [k]ernel_service  
0wned 6114 /Users/0wned/Library/kernel_service

However, once it begins encrypting files, it quickly runs into RansomWhere?:

Again this success came without specific knowledge of KeRanger. In other words, RansomWhere? was successfully able to generically detect this insidious OS X ransomware.

And what about false positives? RansomWhere? is tuned to favor false positives over false negatives, and thus may occasionally alert on a legitimate process that is encrypting files. As discussed in the [limitations](https://objective-see.com/blog/blog_0x0F.html) section - several 'false-positive' reduction mechanisms have been added in attempt to reduce misclassifications. However, if RansomWhere? does display an alert to the user and the process is legitimate (i.e. not ransomware), the user can simply click 'allow' so that the process can continue running. This will be persistently remembered; the user will never be alerted about this binary again :)

» limitations  
RansomWhere? was designed to generically stop OS X ransomware. However several design choices were consciously made (to facilitate reliability, simplicity, and speed) that may impact its protection capabilities. First, it is important to understand that the protections afforded by any security tool, if specifically targeted, can be bypassed. That is to say, if a new piece of OS X ransomware was designed to specifically bypass RansomWhere? it would likely succeed.

Other limitations include:

  * Reactivity  
RansomWhere? detects and blocks ransomware by detecting untrusted processes that are rapidly creating encrypted files. This is inherently reactive; and as such, the ransomware will likely encrypt a handful of files (ideally only two or three), before being detected and blocked.   

  

  * Scope  
RansomWhere? currently only monitors all users' home directories (i.e. anything under ~, for all users) for encrypted files. Thus if the ransomware encrypts files outside these directories, RansomWhere? may fail to detect and block it.   

  

  * Trust  
RansomWhere? explicitly trusts binaries signed by Apple proper (though not ones signed with an Apple developer ID). As such, if ransomware abuses an signed Apple binary (or process, perhaps via injection), RansomWhere? would not detect this. Moreover, the tool inherently trusts applications that are already present on the system when it is installed. Thus if ransomware is already present on the system (before RansomWhere? is installed), it may not be detected.   

  

  * False-positive reductions  
RansomWhere? attempts to reduce false positives, specifically in terms of misclassifying encrypted files. For example, it attempts to filter out files that may be legitimately encrypted, or file types that may appear to be encrypted when in reality they are not (e.g. some image files). Also, small files (<1024 bytes) are skipped as the current encryption classification algorithm is somewhat inaccurate when there's not a lot of bytes to analyze. If ransomware was aware of this fact, it could in theory abuse this to avoid detection. 

Future Research  
This was my first attempt at creating a tool for OS X that strives to generically detect ransomware. As such, there's obviously room for improvements! In my opinion, one of the biggest drawbacks of this tool is its reactivity or lack thereof (as noted above, ransomware may be able to encrypt a few files before being blocked). There are likely several ways to combat this that I'd like to research further. For example moving code into the kernel or perhaps using 'file canaries' may both improve detection times. Let's look at both.

OS X provides various mechanisms in ring-0, to receive notifications about events of interest. For example, one can use the KAuth framework to register a listener for the KAUTH_SCOPE_FILEOP scope. Then, the listener will be automatically invoked by the OS when file system operations occur, such as whenever a file system object is about to be closed (KAUTH_FILEOP_CLOSE). Processing such file events in the kernel, while more complex, would likely reduce the amount of time that occurs between ransomware's encryptions, and its detection. Future research will look into the effectiveness and efficiency of this approach.

Recently, others have suggested using 'file canaries' to detect ransomware infections. In short, unique files are created on a user's computer and then monitored. It's them assumed that any modifications to these files are a result of a ransomware infection. For example, in ['Proactively Reacting to Ransomware'](http://www.freeforensics.org/2016/03/proactively-reacting-to-ransomware.html), various Powershell scripts and C# coding examples are provided that create such files and then explicitly monitor (just) them for any modifications (e.g. overwrites). Somewhat similarly, a PoC github project ['Ransomware BEGONE'](https://github.com/ofercas/ransomware_begone) creates a 'honeypot' folder, (0honeypot), then monitors any file writes to this folder via a filter kernel driver. Both projects are Windows specific.

Using such 'file canaries' seems like an interesting idea that I'd like to research further and/or perhaps incorporate into future versions of RansomWhere? It's possible that they could provide a more proactive detection mechanism - as (at least in theory), nothing should be modifying the canaried files. If anything is, that process can be immediately blocked (suspended); no need to wait for it to modify or encrypt any other files.

However, just using such 'file canaries', IMHO seems a touch brittle. First, I'm not thrilled by the idea of creating random files on users' computers... Second, if one's 'file canaries' do not match the ransomware's target (e.g. Gopher only targets .docx files), the ransomware detection would fail. Lastly, it's possible that legitimate processes may modify the canaries (for example, perhaps NTFS compression on Windows?), as such one would still have to apply logic to identify and classify the process that was modifying the 'file canary'. Still, even with these 'downsides', a hybrid approach that combined RansomWhere?'s more comprehensive monitoring with the precision of 'file canaries' might be a winning combination!

Conclusions  
It is likely that 2016 will be remembered as the year of ransomware. And unfortunately, even Mac users are at risk! Sadly, current anti-virus solutions have proven ineffective at protecting users - so IMHO, another more generic methodology for detecting and thwarting ransomware is needed! In this blog, we hypothesized that monitoring file-system events to detect the rapid creation of encrypted files by untrusted processes might lead to generic ransomware protection. After diving into technical details, RansomWhere? was introduced and pitted against known ransomware in order to test the hypothesis. As it was able to generically detect and thwart all samples it was tested against, it seems that this hypothesis holds true - at least for now ;)
