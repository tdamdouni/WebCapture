# See DNS in Action From Your Own Terminal

_Captured: 2018-01-12 at 20:10 from [dzone.com](https://dzone.com/articles/see-dns-in-action-from-your-own-terminal?edition=352108&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-01-12)_

Curious about how DNS works? Follow along with these steps and you'll see how a domain name is resolved, starting all the way from root name servers.

## Step-by-Step DNS Queries With dig

DNS is used to translate domain names into IP addresses. You may have also heard that DNS is distributed - instead of having one server know the IP addresses for every possible domain name, each only knows their own area of responsibility (zone).

You may have heard this multiple times, but hasn't it always remained a bit abstract? To see it in action, you could go ahead and start [constructing your own DNS packets by hand](https://routley.io/tech/2017/12/28/hand-writing-dns-messages.html), but there is a simpler way to follow the resolution process step-by-step without getting your hands quite that dirty.

In your system, you likely already have a command-line tool called `dig` (domain information groper). With dig, you can issue DNS queries to your chosen server.

### Ask the Root Servers First

Each server will either know the answer, or they will tell you where you should ask next. The process of resolving a domain name starts from **root domain servers**. You can find a list of these by simply issuing the command `dig` with no arguments. The response will contain a list such as:

There are 13 root name servers (from **a** to **m**) for redundancy. They are maintained by independent organizations such as NASA, VeriSign, and the US Army. Pick one at random, for example, **c.root-servers.net** maintained by Cogent Communications.

You can ask the root server for the IP address of **example.com** by issuing the following command: `dig @c.root-servers.net example.com`. What this does is it encodes your request in a binary packet, and then sends it over UDP to the server specified with @.

## Making Sense of the Answer

The answer is also a binary packet, but again dig helps you out by outputting a more human-readable version of the response contents:

The beginning of a packet has a number of **flags**, the most interesting here being the number of ANSWERs in the response. Here you may notice "ANSWER: 0". This means the packet did not contain a direct answer to your question.

After the flags, binary DNS packets consist of a number of sections. Dig shows you these sections separated by comments such as _";; QUESTION SECTION"_, _";; ANSWER SECTION"_ or _";; AUTHORITY SECTION"_. The **question section** just repeats your query. The **answer sections** (of which there are none here) would contain the IP address you were looking for.

If the server doesn't know the answer directly, the **authority section** tells you where to ask next. Authority sections indicate the server(s) which have authority over answering DNS queries about the domain. In the above response, you will see a line ending in the authority section, with "_a.gtld-servers.net._"

In essence, this response means "_I don't know the IP address for example.com, but ask this server instead._"

## Consulting the Authorities

To ask this question again to the next server, do the same as before, only this time using the new name server you learned from the response: `dig @a.gtld-servers.net example.com`.

You will get a familiar looking answer:

Again this server says _"I don't know, but ask a.iana-servers.net instead, they are the authority on this."_

Continue with the chain one more step: `dig @a.iana-servers.net example.com`.

From the flags section, you can see that now we have "ANSWER: 1", meaning the response contains one answer section! Indeed a few lines down you'll find that there is an answer section containing the IP address you were looking for: 93.184.216.34.

## Recursive Queries

What you just did is issue a series of DNS queries to nonrecursive servers, where each step might point to the next name server instead of giving you the answer directly.

You can also get dig to perform this step-by-step resolution process for you by using the `+trace` option: `dig +trace www.example.com`. In this case, dig will iterate from one name server to the next without you having to manually issue each new command.

There is yet another way to get at the answer, without needing to do any hopping on your machine. You can issue a **recursive query** to a name server that supports it. With a recursive query, you let the target name server figure out the final answer directly.

The real difference between these two queries is a single bit in the DNS packet sent, indicating whether you wanted the final answer or just the next hop. In the examples above this didn't matter, because the root name servers do not support recursion. If needed you can control this bit flag by the options `+norecurse` or `+recurse` (which is also the default).

For instance, Google operates such a recursive name server at the easy-to-remember IP address 8.8.8.8. You can use dig to ask for the answer as before: `dig @8.8.8.8 example.com`. This time however you will get the answer directly, as Google's name server does all the iteration for you (or likely has the answer already cached).

## Summary

Playing the role of an iterative resolver gives you a good feel for how name resolution happens behind the scenes.

DNS resolution begins with the root servers, which point you towards the authority for each top-level domain. The command-line tool dig allows you to issue queries to these name servers, revealing which name server you should ask next. Repeating the process you can eventually learn the IP address you seek.

Have fun with your new knowledge, it can come in handy when troubleshooting problems with DNS.
