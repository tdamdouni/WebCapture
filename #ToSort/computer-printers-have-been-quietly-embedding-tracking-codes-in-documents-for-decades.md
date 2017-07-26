# Computer printers have been quietly embedding tracking codes in documents for decades

_Captured: 2017-06-10 at 17:08 from [qz.com](https://qz.com/1002927/computer-printers-have-been-quietly-embedding-tracking-codes-in-documents-for-decades/)_

In 2004, when color printers were still somewhat novel, PCWorld magazine [published](http://www.pcworld.com/article/118664/article.html) an article headlined: "Government Uses Color Laser Printer Technology to Track Documents."

It was one of the first news reports on a quiet practice that had been going on for 20 years. It revealed that color printers embed in printed documents coded patterns that contain the printer's serial number, and the date and time the documents were printed. The patterns are made up of dots, less than a millimeter in diameter and a shade of yellow that, when placed on a white background, cannot be detected by the naked eye.

![](https://qzprod.files.wordpress.com/2017/06/printer_steganography_illustration.png?w=50)![Printer_Steganography_Illustration](https://qzprod.files.wordpress.com/2017/06/printer_steganography_illustration.png?w=1920)

> _The dots are less than a millimeter in diameter and invisible to the naked eye (Wikimedia Commons)_

The existence of the hidden dots gained renewed interest this week when they were found embedded in a [top-secret report](https://qz.com/999323/fbi-arrests-reality-winner-a-25-year-old-contractor-after-an-nsa-report-on-the-russian-military-hacking-the-us-election-was-leaked-to-the-intercept/) by the US National Security Agency (NSA) that was [published](https://theintercept.com/2017/06/05/top-secret-nsa-report-details-russian-hacking-effort-days-before-2016-election/) by The Intercept on June 5. About an hour after the report was published, the Department of Justice (DOJ) announced that the Federal Bureau of Investigation (FBI) had arrested a suspected leaker. The 25-year-old NSA contractor, Reality Leigh Winner, was charged "with removing classified material from a government facility and mailing it to a news outlet."

In an affidavit released by the DOJ, an FBI agent described how Winner [had been tracked down](https://qz.com/999484/how-us-law-enforcement-caught-reality-winner-the-nsa-contractor-charged-with-leaking-top-secret-materials/). The scanned copy of the document, which The Intercept had given to the government to confirm its authenticity, "appeared to be folded and/or creased," the agent wrote, "suggesting they had been printed and hand-carried out of a secured space."

When researchers later discovered the tracking dots embedded in the document, many quickly [assumed](http://blog.erratasec.com/2017/06/how-intercept-outed-reality-winner.html#.WTrEjRPytBw) that the NSA had used them to find Winner. However, according to the affidavit, an internal government audit found that only six people had printed out the classified documents. Winner was one of those six people, and the audit found that she had also sent an email to the news outlet from her work computer. An analysis of the dots was therefore probably not necessary to track down Winner, despite several [misleading](https://news.vice.com/story/nsa-leak-suspect-was-ratted-out-by-an-office-printer) [news](https://arstechnica.com/security/2017/06/how-a-few-yellow-dots-burned-the-intercepts-nsa-leaker/) [reports](http://boingboing.net/2017/06/06/reality-winner-was-outed-by-in.html) that suggest otherwise. But their presence has nonetheless resurfaced long-standing privacy concerns.

By analyzing the dots in the top-secret document, researchers were able to conclude it came from a printer with a serial number of 29535218, model number 54, and that it was printed on May 9, 2017, at 6:20 a.m., at least according to the printer's internal clock. In a case where a leaker had covered his or her tracks more carefully, or where the leaked documents had been printed by far more than six people, or perhaps printed on a non-government printer, the dots certainly could have come into play.

![](https://qzprod.files.wordpress.com/2017/06/doc.png?w=50)![](https://qzprod.files.wordpress.com/2017/06/doc.png?w=1920)

> _The hidden dots cover the document in a grid, containing information about when and on what device it was printed. Here, one set of the dots is enlarged and highlighted._

Looking into how the embedded codes came to be, we found a secret history that's been little told. The technology meant to track our paper documents back to us has been hidden in plain sight for more than 30 years.

The 2004 article in PCWorld was based on information provided by Peter Crean, who was a senior research fellow at Xerox at the time. In his first public interview about the practice since talking to the magazine 13 years ago, Crean told Quartz that Xerox hadn't done much to share information about the dots' existence.

"We didn't advertise it much to the people that had [the printers]," said Crean, now retired. "We didn't _not_ tell them if they asked. The salespeople were told, 'Don't lead with it in any sales, but if they ask you about it, you can tell them we have the security feature in there.'"

When color printers were first introduced, he said, governments were worried the devices would be used for all sorts of forgery, particularly counterfeiting money. An early solution came from Japan, where the yellow-dot technology, known as printer steganography, was originally developed as a security measure.

Fuji, which has been in a joint-venture partnership with Xerox since 1962, was the first to implement the codes in printers. Fuji-Xerox manufactures most of Xerox's printing and copying devices, and has done so for several decades. Amid rampant counterfeiting issues in Japan in the mid-1980s, Crean said, the company began programming color printers to embed the dots.

"They put it on early and we went along with it," Crean said, "because the machines came with it."

There are no laws or regulations in the US that force printer manufacturers to include the tracking codes. It became standard practice primarily because some countries would have refused to import the products without some assurance that if the printers were used to counterfeit money, they'd be able to track the owners down. If Xerox hadn't implemented steganography in its early color printers, the US may have tried to block their import from Japan, Crean said.

In addition to the yellow-dot technology, Xerox implemented another feature around the same time that forced color copiers to shut down if they detected steganography in documents indicating they were currency. In 1994, the US Central Intelligence Agency approached Xerox about using the same technology to stop the unauthorized copying of classified documents, and Crean provided some ideas in a brainstorming session with two agents that year, he said. He wasn't aware of whether the agency used any of his ideas, but the functionality to detect currency, he said, "was in most of the machines at least through the mid-2000s."

When Crean talked to PCWorld in 2004, Xerox had been pushing a PR campaign focused on the technology and science behind some of its innovations, including steganography. The company had asked Crean to highlight the tech as a neat security feature the company's printers included, and to talk about the science behind it. Crean had talked publicly about the codes a few times before, and nothing much had come of it. The company likely assumed the techie readers of PCWorld would get a kick out of the obscure feature.

"Our PR people set it up for me," said Crean. "When I gave the interview at my desk, our PR person was sitting right across the desk from me, nodding at everything I said."

The article created an uproar among privacy advocates, who said the practice was a violation of Americans' constitutional rights. Although the article quoted a Secret Service counterfeiting specialist, who said "the only time any information is gained from these documents is purely in [the case of] a criminal act," privacy advocates pointed out there were no laws to hold the government to that.

"The possible misuses of this marking technology are frightening," wrote the Electronic Frontier Foundation (EFF) in a [blog post](https://www.eff.org/wp/investigating-machine-identification-code-technology-color-laser-printers) responding to the article. "Individuals using printers to create political pamphlets, organize legal protest activities, or even discuss private medical conditions or sensitive personal topics can be identified by the government with no legal process, no judicial oversight, and no notice to the person spied upon."

Salespeople at Xerox were told at this point to refer all questions about the dots to Xerox headquarters, Crean said.

A security researcher at the EFF, Seth Schoen, began looking into the dots shortly after the article was published, hoping to figure out how to read the encoded patterns. The organization asked the public to submit samples of their own printed documents, Schoen said, which helped them to compare differences between patterns on many printer models.

"We also went to a number of Kinko's locations and printed our own samples, which is a great way to get DocuColor samples," Schoen said, referring to Xerox model they were researching. "We looked at them with scanners and microscopes (and blue-light flashlights)."

![](https://qzprod.files.wordpress.com/2017/06/eff.png?w=50)![How to decode the hidden dot patterns](https://qzprod.files.wordpress.com/2017/06/eff.png?w=512)

> _How to decode the hidden dot patterns (Electronic Frontier Foundation)_

Eventually, a volunteer working with the EFF noticed that the dots represented a binary code, Schoen said. It allowed them to crack the logic behind them, and to read the information embedded in any document that used yellow-dot steganography. The organization [published](https://w2.eff.org/Privacy/printers/docucolor/) the results of its work, along with an interactive tool to decode the dots.

The researchers also published a list of all the models they found that embed the same pattern of dots, but Schoen pointed out in a phone interview that we should assume every color printer embeds tracking information in one way or another. He referred to information the EFF obtained in 2005 through a Freedom of Information Act request to the US government.

"Some of the documents that we previously received through FOIA suggested that all major manufacturers of color laser printers entered a secret agreement with governments to ensure that the output of those printers is forensically traceable," the EFF [said](https://www.eff.org/pages/list-printers-which-do-or-do-not-display-tracking-dots) on its website.

Indeed, Crean said that after Fuji-Xerox began embedding tracking codes, the practice became ubiquitous.

"Other companies came up with other variants of that scheme that were more complicated, harder to decode. Canon kind of twist theirs around in a spiral," Crean said, "but everybody was basically putting a small digital set of bits smack dab all over the print."

Xerox, HP, Canon, and the NSA did not immediately respond to our requests for comment.

Although the code behind the yellow-dot patterns was cracked, there is likely other steganography still in use that has yet to be discovered. In addition to the various implementations Crean mentioned, Schoen said there is at least one newer version that is even more difficult to find in a document.

"What we've learned is that there is a second generation of the technology that some of the manufacturers have switched over to," Schoen said. "We've never cracked that or even had a way to detect it."
