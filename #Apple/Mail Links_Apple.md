# Mail Links

_Captured: 2016-04-10 at 23:00 from [developer.apple.com](https://developer.apple.com/library/ios/featuredarticles/iPhoneURLScheme_Reference/MailLinks/MailLinks.html)_

The `mailto` scheme is used to launch the Mail app and open the email compose sheet. When specifying a `mailto` URL, you must provide the target email address. The following examples show strings formatted for Safari and for native apps.

* HTML link:

```
<a href="mailto:frank@wwdcdemo.example.com">John Frank</a>
```
	
* Native app URL string:

```
mailto:frank@wwdcdemo.example.com
```

You can also include a subject field, a message, and multiple recipients in the To, Cc, and Bcc fields. (In iOS, the `from` attribute is ignored.) The following example shows a `mailto` URL that includes several different attributes:

```
mailto:foo@example.com?cc=bar@example.com&subject=Greetings%20from%20Cupertino!&body=Wish%20you%20were%20here!
```

For detailed information on the format of the `mailto` scheme, see [RFC 2368](http://www.ietf.org/rfc/rfc2368.txt).

**iOS Note:** If the Mail app is not installed, clicking a `mailto` URL displays an appropriate warning message to the user.

[Next](https://developer.apple.com/library/ios/featuredarticles/iPhoneURLScheme_Reference/PhoneLinks/PhoneLinks.html)[Previous](https://developer.apple.com/library/ios/featuredarticles/iPhoneURLScheme_Reference/Introduction/Introduction.html)
