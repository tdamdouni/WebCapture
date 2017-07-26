# What Is Email Header Injection?

_Captured: 2017-05-14 at 17:35 from [dzone.com](https://dzone.com/articles/what-is-email-header-injection?edition=298099&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-13)_

It's common practice for websites to implement contact forms which in-turn send emails to an intended recipient of the message by a legitimate user. Most of the time such a contact form would set SMTP headers such as `From` and `Reply-to` to make it easy for the recipient to treat communication from the contact form just like they would any other email.

Unfortunately, unless the user's input is validated before being inserted into SMTP headers, the contact form might be vulnerable to Email Header Injection (also referred to as SMTP header injection). This is because an attacker may be able to inject additional headers into the message, thereby instructing the SMTP server to carry out different instructions than intended.

The following PHP code is an example of a typical contact form that is vulnerable to Email Header Injection. The following code takes the name and email address provided by a website visitor and prepares a list of headers for the email.

The From header is used so that the email's recipient (in this example it's _root@localhost_) will know who is the author of the email. The Reply-To header allows the email's recipient to reply back to the person who sent the email via the reply button in their email client.

A typical genuine POST request would be as follows.

An attacker could abuse this contact form by sending the following POST request.

In this example, an attacker is inserting a newline (`\n` on most UNIX and Linux systems, `\r\n` on Windows systems) and appending a bcc SMTP header containing additional email addresses to whom the SMTP server will deliver the email to in BCC.

An attacker could use such tactics to send large numbers of messages anonymously, or even send phishing emails where the recipient believes these messages are originating from a trusted source. It's also worth noting that this vulnerability is not limited to PHP; it can potentially affect any application that sends email messages based on arbitrary user input.

## Detecting Email Header Injection Vulnerabilities

In order to detect Email Header Injection automatically, we'll need to rely on an intermediary service since the detection of such a vulnerability requires an out-of-band and time-delay vector. Acunetix solves this by making use of AcuMonitor as its intermediary service during an automated scan.

During a scan, Acunetix will locate the contact form and inject a custom BCC SMTP header pointing to an AcuMonitor email address. If the application in question causes the SMTP server to send the email to AcuMonitor, then AcuMonitor knows it's vulnerable and it will send a notification back to Acunetix indicating it should raise an alert for Email Header Injection.

## Mitigation

Mitigating against email header injection involves validating user input to not allow any newline characters in the input which would cause another SMTP header to be appended. In general, when validating user input, the simplest and most robust way to achieve strong input validation is through a whitelist of allowed characters for use in the SMTP headers.
