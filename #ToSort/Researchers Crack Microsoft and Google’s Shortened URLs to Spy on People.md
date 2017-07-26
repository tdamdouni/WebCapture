# Researchers Crack Microsoft and Google’s Shortened URLs to Spy on People

_Captured: 2016-04-18 at 01:06 from [www.wired.com](http://www.wired.com/2016/04/researchers-cracked-microsoft-googles-shortened-urls-spy-people/)_

![Bit_ly.gif](http://www.wired.com/wp-content/uploads/2016/04/Bit_ly.gif)[Click to Open Overlay Gallery](javascript:;)

> _Then One/WIRED_

For anyone with minimalist tastes or an inability to use copy-paste keyboard shortcuts, URL shorteners may seem like a perfectly helpful convenience. Unfortunately, the same tools that turn long web addresses into a few characters also offer the same conveniences to hackers--including any of them motivated enough to try millions of shortened URLs until they hit on the one you thought was private.

That's the lesson for companies including Google, Microsoft, and Bit.ly in a paper published today by researchers at Cornell Tech. The researchers' work demonstrates the unexpected privacy-invasive potential of "brute-forcing" shortened URLs: By guessing at shortened URLs until they found working ones, the researchers say that they could have pulled off tricks ranging from spreading malware on unwitting victims' computers via Microsoft's cloud storage service to finding out who requested Google Maps directions to abortion providers or drug addiction treatment facilities.

The Cornell Tech researchers' work began more than a year and a half ago when they noticed that certain Google and Microsoft services--namely Microsoft OneDrive and Google Maps--used Bit.ly's URL shortening service to generate web addresses with only six seemingly random characters. That's few enough that a determined nerd could use software to automatically generate, visit and analyze all of the millions of possible shortened URLs, or at least a significant fraction of them. "With a decent number of machines you can scan the entire space," says Cornell Tech computer scientist Vitaly Shmatikov. "You just randomly generate the URLs and see what's behind them."

Despite that simple method to discover the shortened URLs, both Google and Microsoft still treated some of those addresses as relatively private--or at least, private enough to assume that only the creator of the link or someone they directly shared it with would ever access it. But in fact, the researchers write, "online resources that were intended to be shared with a few trusted friends or collaborators are effectively public and can be accessed by anyone. This leads to serious security and privacy vulnerabilities."

The researchers went on to show exactly how that mismatch of privacy expectations could have serious consequences for both Google and Microsoft's services' data protection.

### Private Microsoft Storage Compromised

In Microsoft's case, the company used Bit.ly to generate shortened URLs for files or folders that people have made shareable on its OneDrive storage site. So the Cornell researchers randomly generated more than 71 million possible OneDrive short URLs, of which more than 24,000 turned out to be live, working links to files and folders. To avoid ethical and legal ambiguity, the researchers say they never downloaded any of those files. But by loading the resulting pages and looking at the full URL, the researchers say they could often tweak that web address to access other files or folders uploaded by the same OneDrive user. And about 7 percent of the files or folders were editable by anyone who visited.

That means, the researchers point out, that they could not only mess around with peoples' data, but even add malware to their cloud storage, which--thanks to a synchronization feature--is often copied automatically to the victim's PC. "If someone wanted to inject a lot of malicious content into people's computers, it's a pretty interesting way of doing it," says Shmatikov. "By scanning you can find these folders, you put whatever you want in them, and it gets automatically copied to people's hard drives."

### Your Google Maps Directions Captured

A demonstration that the researchers pulled off with Google Maps, which similarly uses Bit.ly to shorten links for sharing locations and directions, was even more disturbing. The researchers generated more than 23 million shortened Google Maps URLs, and found that about 10 percent of those loaded actual directions that someone had requested. And because those directions often included one end of the route at the what was likely a home address, they represent serious potential privacy breaches. In fact, destinations the researchers found included "clinics for specific diseases (including cancer and mental illnesses), addiction treatment centers, abortion providers, correctional and juvenile detention facilities, payday and car-title lenders, [and] gentlemen's clubs." More than 16,000 of the directions had one end of the route at a hospital and the other at a residence, for instance. (They found that the same problem applied to Mapquest, Bing Maps, and Yahoo! Maps, albeit on a much smaller scale.)

To fully illustrate the creepy potential of that publicly accessible mapping data, the researchers went so far as to identify one "young woman" who had shared directions to a Planned Parenthood facility. Starting with the Google Maps data from shortened URLs that pointed to her home, they were able to confirm her address, full name and age--thankfully none of which they shared in the paper. "That's a very substantial privacy leak," Shmatikov says.

### Longer Is Better

When the researchers notified Google about their work in September of last year, the company responded by lengthening its shortened URLs to 11 or 12 randomized characters and taking new measures to identify and block automated scanning of shortened URLs. In a statement to WIRED, a Google spokesperson writes that the company "appreciate[s] [the Cornell Tech researchers] contributions to the safety of Google Maps and other Google products. The Cornell researchers notified us last year about this issue and we've since strengthened URL protections based on their findings and our own studies."

The researchers say that Microsoft, on the other hand, initially brushed off their concerns when they contacted the company in May of last year. But last month Microsoft removed the URL shortening feature from OneDrive altogether. "We're continually looking for ways to improve the usability, features and security of our products and services for customers," a Microsoft spokesperson writes in a statement to WIRED. "As part of these efforts, earlier this year we began removing shortened URLs from file sharing options to simplify for users and prepare for future developments." Meanwhile, the Cornell Tech researchers say that all the vulnerable links to OneDrive they identified still work.

Cornell's Shmatikov argues that much of the exposed data they found remains live and vulnerable, and that the broader warning about the public nature of some shortened URLs still applies. Both companies and people need to be more aware of the privacy implications of shortening a URL, the Cornell researchers argue. "It's not clear that users understand this," says Shmatikov. "They think they're sharing a document with a collaborator. But if you're sharing a six character shortened URL, you're sharing it with the whole world."

Here's the Cornell Tech researchers' full paper:
