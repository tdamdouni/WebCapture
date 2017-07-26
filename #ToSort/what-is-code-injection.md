# What Is Code Injection?

_Captured: 2017-05-11 at 21:50 from [dzone.com](https://dzone.com/articles/what-is-code-injection?edition=298053&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-11)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

Code Injection, or Remote Code Execution (RCE) refers to an attack wherein an attacker is able to execute malicious code as a result of an injection attack. **Code** Injection differs from **Command** Injection since an attacker is confined to the limitations of the language executing the injected code. While it's possible for an attacker to escalate an attack from Code Injection to execute arbitrary shell commands, it's not always the case.

Typically, Code Injection occurs when an application evaluates code without validating it first. In general, code evaluations containing user input are almost always bound to get you into trouble, hence the common mantra _"eval() is evil."_

The following is an example of PHP that is vulnerable to Code Injection.

In the above example, an attacker could make the following request to execute arbitrary PHP code. In this case, a PHP info page will be displayed.

## OS Command Execution

While code injection has the potential to do a lot of damage, an attacker might have the ability to escalate a code injection vulnerability even further by executing arbitrary operating system (OS) commands on the server by using PHP itself to execute shell commands.

The following refers to the above example, but executes the `whoami` shell command.

Once an attacker manages to gain OS command execution, the attacker could attempt to gain persistence by using a [webshell](https://www.acunetix.com/websitesecurity/introduction-web-shells/) or install other malware. Form there, an attacker can even attempt to pivot to other internal systems which are not usually exposed publicly.

## Preventing Code Injection Vulnerabilities

The most effective method for eliminating Code Injection vulnerabilities is to avoid code evaluation at all costs unless absolutely and explicitly necessary (i.e. there is no possibility of achieving the same result without code evaluation).

In the event where code evaluation is necessary, it is crucial for any user input to be very strongly validated, with as many restrictions as possible on the inputted data.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
