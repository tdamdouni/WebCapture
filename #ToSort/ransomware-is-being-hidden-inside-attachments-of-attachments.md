# Ransomware Is Being Hidden Inside Attachments of Attachments

_Captured: 2017-04-25 at 15:29 from [lifehacker.com](http://lifehacker.com/ransomware-is-being-hidden-inside-attachments-of-attach-1794610034?utm_campaign=socialflow_lifehacker_twitter&utm_source=lifehacker_twitter&utm_medium=socialflow)_

> _Example of Locky source code. Photo by [Christiaan Colen](https://www.flickr.com/photos/christiaancolen/33318605932/)._

Ransomware attacks are [getting more and more clever](http://lifehacker.com/a-crash-course-in-ransomware-and-how-to-protect-yoursel-1783372708) as the public gets wise to them. The latest involves hiding a malicious macro inside a Word document attached to a seemingly harmless PDF file.

The new ransomware campaign, [highlighted by the Naked Security blog](https://nakedsecurity.sophos.com/2017/04/24/ransomware-hidden-inside-a-word-document-thats-hidden-inside-a-pdf/), works like this:

  1. You're sent a spam email with a PDF attachment (which _should_ already be a red flag), but the PDF looks safe and clear with most antivirus apps.  

  2. The PDF has an attached document that Acrobat Reader tries to open when you open the PDF.  

  3. The document gets opened by Microsoft Word, then asks you to enable editing. But it's actually a social engineering attack trying to get you to enable a VBA macro.  

  4. When you say yes to enable editing, the VBA macro runs, then downloads and runs the crypto ransomware [Locky](https://nakedsecurity.sophos.com/2016/02/17/locky-ransomware-what-you-need-to-know/).  


By hiding the actual attack inside an attached document _within_ another safe-looking document, ransomware attackers can get around most antivirus filters. SophosLabs likens the approach to a Russian matryoshka doll, hiding an attack within a file within a file.

Fortunately, to avoid these types of attacks you simply need to follow the same rules you should have been following all along--with one caveat. Be wary of email attachments, yes, but also don't fully rely on your security software when it says a suspicious file looks safe.

Even if it looks like it's coming from a friend, take a few extra moments to make sure it's really them. Attackers have been [getting better at masquerading as people you trust](http://lifehacker.com/beware-this-clever-fake-attachment-gmail-phishing-sca-1793264478). And never enable macros in documents you receive via email. Microsoft keeps auto-execution of macros disabled by default, but don't let clever social engineering tricks get you to turn them back on.
