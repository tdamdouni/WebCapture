# IMAP, Therefore I Am

_Captured: 2018-06-07 at 16:08 from [dzone.com](https://dzone.com/articles/nylas-imap-therefore-i-am?edition=379242&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-06-07)_

In this post, we're going to dive into IMAP. IMAP stands for Internet Message Access Protocol, and it's the open standard that describes how to access messages in an email mailbox. While IMAP is an important part of receiving emails, it's not always the easiest thing to implement (or understand). In short, IMAP is the protocol that email clients like Mail.app, Thunderbird, and Mailspring use to download messages from your email account and to make changes like archiving messages or sorting them into folders.

## A Brief History of IMAP

IMAP was originally created by Mark Crispin at Stanford in the 1980s. Crispin later moved to the University of Washington and spent 20 years there working on the [IMAP specs and reference implementation](https://www.washington.edu/imap/). The IMAP specification comes in the form of a "Request for Comments," or RFC, which is basically a memo describing how to implement the protocol that has been adopted as a standard by the Internet Engineering Task Force. RFCs may be revised to make clarifications or changes, and the current RFC that describes IMAP is [RFC3501](https://tools.ietf.org/html/rfc3501.html) which was published in 2003. That's right: the protocol most mail clients use to sync email is over 15 years old!

IMAP was initially designed as a better alternative to an older protocol called POP, with the goal being "[to permit manipulation of remote mailboxes as if they were local](https://www.washington.edu/imap/papers/imap.vs.pop.brief.html)" \- specifically, POP's mode of operation was to download mail to your local machine and delete it from the server, which made it difficult to manage your mail if you were using multiple computers. This was no problem in the days of timesharing mainframes but became one as personal computers became more prevalent and you might have a PC at home as well as at work, and wanted to browse your email from either place.

The original version of IMAP is lost to history, and [IMAP2](https://tools.ietf.org/html/rfc1064) (released in 1988) is the first version that made it into the standards. This first version of IMAP only supported "online" operation: it assumed that your mail client would be connected to the server when viewing or modifying messages. You couldn't use it to sync a copy of your mailbox locally and then update your local copy when you reconnected, because messages were only identified by a "sequence" number, and sequence numbers were not persistent across client sessions. One can only imagine that in those days folks figured that it'd always be the case that whenever you wanted to check your email, you'd be sure to have a reliable network connection. My guess is that it was because computing from mainframes and timesharing systems was essentially logging directly into a server machine, and meant you had an always-on internet connection at your disposal.

Fast forward a few years to the dial-up era, and it became apparent that hogging your phone line constantly so you could read your email just wasn't going to cut it. Enter support for "disconnected" operations, which was bolted on to IMAP with the introduction of [IMAP4](https://tools.ietf.org/html/rfc1730) in 1994. This revision to the protocol added persistent message identifiers (called "UIDs") and an entire [draft spec](https://tools.ietf.org/html/draft-ietf-imap-disc-00) explaining how you could sync changes made to locally cached data to data stored on a server using IMAP commands. We'll talk more about this later, but this evolution of the protocol over time is a major reason why implementing IMAP clients is complex in the modern era, as a disconnected operation is a required feature for modern apps.

The basic IMAP protocol has remained unchanged since 1996, with all new features since then being implemented in optional extensions to the protocol, some of which have become standards-but adoption of even the most common extensions still varies wildly across email service providers.

## How IMAP Works

Now that you know some of the history of the protocol, we're going to interactively introduce you to the nuts and bolts of how it works. We're going to connect to an email account, list all of the available folders in the mailbox, and download a message. Along the way, we'll identify and explain the relevant parts of the protocol needed to understand what is happening.

You'll be able to follow along as we walk through the protocol, as long as you have access to a terminal, the `openssl` command-line utility, and an email account that supports IMAP (including Gmail).

### TCP, HTTP, and IMAP

Many modern client-server protocols take place between a web browser and a server, or an app and an API. These APIs are all implemented on top of a base protocol, HTTP ("hypertext transfer protocol"), which defines the semantics of different types of requests - GET, PUT, POST, etc. HTTP is in turn implemented on top of a lower-level protocol called TCP ("transmission control protocol"), which simply guarantees that packets of information are delivered reliably to the destination.

IMAP, like HTTP, is implemented on top of TCP - and it defines the semantics of different types of requests, called IMAP commands. IMAP, in general, is a lot more concise than HTTP, which was key for IMAP in the early '90s as network connections were very low-bandwidth.

## IMAP Step-by-Step

Let's get started! Follow along at home in your terminal by typing the commands, subbing in the details of your email account where relevant. Note that if you're using Gmail, you may need to [disable protection](https://support.google.com/accounts/answer/6010255?hl=en) against logins from "less secure apps" for this to work.

The first thing any client needs to do is to to make a connection to the remote server on a specific port. These ports can vary because mail servers first accepted plaintext connections and later added support for secure encrypted connections. You can generally find the settings for your provider by checking their help articles. For example, [here's](https://support.google.com/mail/answer/7126229?hl=en) where to find the settings for Gmail (if you're curious as to the background of why different ports are used, we recommend [this fantastic guide](https://www.fastmail.com/help/technical/ssltlsstarttls.html) from Fastmail).

Got your settings to make a secure connection? Let's go!

On the command line, we can connect using the `openssl` command-line utility. We have to use `openssl` rather than `telnet`, because, otherwise, we could end up sending sensitive data like passwords and private emails in plaintext over the network, leaving them open to network sniffing by an attacker. `openssl` protects our connection by making a secure connection and verifying the remote server's certificate before proceeding.

In the above command, `s_client` means we're invoking `openssl`'s functionality to act as a basic SSL/TLS client, `-connect` specifies which hostname and port to connect to, and `-crlf` converts when you press "Enter" in your terminal to the characters expected by the IMAP server to properly end a line. After connecting, `openssl` checks the SSL/TLS certificate on the server to make sure our connection isn't being hijacked, and the IMAP server displays a greeting that says it is ready to receive requests from the client.

### Commands

IMAP commands generally look like this:

**<tag> <command> [<arg1><arg2>...]**

We'll explain these parts in the context of an example command, called CAPABILITY. CAPABILITY allows you to ask a server which IMAP extensions it supports:

Wahoo, we just communicated with an IMAP server! Let's explain what we sent and what we got back.

A command is similar to a request in HTTP. It's telling the server to do something or asking it for information. In this case, we're asking the server to tell us which capabilities it supports. More on capabilities in just a bit.

The CAPABILITY command has no arguments, but if it did, we'd simply type them in after the command name and before we press enter.

### Tagging

Tags (`tag1`, in this example) are generated by the client, and the server sends the tag back on the final line of the response to a command. Tags can contain any alphanumeric characters and even some symbols and don't need to contain an ascending integer - though that can be a convenient way to generate unique ones. Server responses that start with `*` are called untagged responses, which means that they don't represent the completion of a command requested by the client. In this case, the untagged response is the capability list, and the tagged response is the `OK` status of the command and a funny message left by the server programmers.

This tagging ability means that it's possible for a server to handle more than one request at the same time from a client on the same connection, and to indicate their completion by sending back the appropriate tag. In practice, many clients don't support this ability to send concurrent requests, and simply block waiting for data to arrive on the open socket after a command is sent.

### Capabilities

So what does this list of "capabilities" mean, anyway? A "capability" is a short name for a feature the server supports. Some of these capabilities, like `AUTH=PLAIN`, are included in the base IMAP4rev1 spec, and others are enabled by extensions. Extensions allow new commands to be added to the IMAP protocol without requiring a new version of the protocol specification. Before logging in, the list of supported capabilities on a server will be different from the capabilities after logging in, as there's little use in listing capabilities that aren't relevant to the logged-out or logged-in states.

### Authentication

Here's how you authenticate your mail account to an IMAP server:

### Server Responses

As you can see, server responses don't always say `OK`. Here's a quick guide to the allowed server responses to a command:

`OK` = success!  
`NO` = failure!  
`BAD` = I didn't understand what you said!

The server is free to add a bit more information after the response if it so desires, like `[AUTHENTICATIONFAILED] Invalid Credentials (Failure)`.

As you can see, after a successful login, the server sends the client the list of capabilities again, showing what new capabilities have been unlocked as a result of the login and which old ones have gone away. Some standard extensions in this list are `UIDPLUS`, `MOVE`, and `CONDSTORE`. Some custom extensions supported by Gmail but not elsewhere are `ESEARCH` and `X-GM-EXT-1`.

### Listing Folders

OK, now that we're logged in, let's try to do something useful. First, let's check which folders exist in the mailbox:

Whoops! As you can see, if you get the arguments wrong to a command, the server will reject it and say `BAD` client!

### Folder Flags

Here we can see the folder hierarchy that exists in the mailbox. Folders have special flags, indicated in parentheses. Some of these flags are useful for traversing the folder hierarchy, like `\HasNoChildren` and `\HasChilden`, while others are used to denote special characteristics of a given folder, like if it contains drafts (`\Drafts`) or sent messages (`\Sent`). These flags allow clients to tailor their behavior to the mailbox and do things like save sent messages to the right folder no matter which language the user's mailbox is in.

### Sessions

OK, let's read some email now. First, because IMAP connections are stateful, we need to open a session on the folder that we care about using the `SELECT` command:

There's a lot of information the server sends us here! Sessions are a key component of how IMAP works, and a session lasts from when you `SELECT` a mailbox until you `UNSELECT` it, `SELECT` another mailbox, or log out.

When opening a session, this server has sent us, in addition to the OK indicating success:

  * a list of active flags in use on messages in the mailbox.
  * a list of supported flags that could be used on messages in the mailbox.
  * the `UIDVALIDITY` \- more on this in a bit.
  * the number of messages in the mailbox.
  * how many "recent" messages are in the mailbox, which means how many messages are tagged with the `\Recent` flag.
  * the "predicted next UID."
  * a `HIGHESTMODSEQ` value - more on this in a bit.

A few of these items are going to require a bit more explanation. First, UIDs.

### UIDs and Sequence Numbers

A reminder: a long long time ago, there was IMAP2, and in IMAP2 messages were identified by sequence numbers. Sequence numbers were literally just that: monotonically increasing numbers, one for each message in a mailbox:

Every time you selected a mailbox, if there were new messages, there would be more sequence numbers. And if you moved messages around and started a new session, the sequence numbers assigned to messages might be different from the ones from the old session.

This very simple scheme worked pretty well if all you did was connect, read your mail online, and disconnect. But it didn't work if you wanted to connect, download all of your mail locally for offline access, and then reconnect later and have your client sync its local state with the state on the server-because these non-persistent sequence numbers didn't allow clients to map local mailbox state to remote mailbox state, because messages on each side might have different IDs!

Enter IMAP4 and UIDs. UIDs (unique IDs) are persistent to a message as long as it stays in the same folder and the server's UIDVALIDITY integer has not increased. So when a client starts a new session on a mailbox, it has to check the UIDVALIDITY and compare it to its local cached value, and if the server's UIDVALIDITY is higher, it must throw away all cached local UIDs and resync from scratch. But otherwise, it's free to compare its local cached data to the data on the server and only sync changes.

To retain backward compatibility, IMAP4 supports both sequence numbers and UIDs, and you can ask for UIDs by prefixing any command that returns message identifiers with `UID`:

As you can see, unlike sequence numbers, UIDs are not guaranteed to be increasing in increments of one - gaps develop in the UIDs assigned to a mailbox as messages arrive and are moved around between folders.

### Statefulness

While we're here, one aside about statefulness: Generally, statefulness is not a desirable feature in protocols. Statefulness makes it trickier to use connection pools with IMAP, because the `SELECT` command can be quite slow, and every time a pool consumer checks out a new connection, it needs to ensure that the correct mailbox is selected. Statefulness also means that application code has to keep track of the state and make sure it's in sync with the actual state of the connection, or else make another client-server back-and-forth every time the information is needed. Generally, it's easier to program with stateless protocols than with stateful ones.

### Fetching Message Data

OK, let's finally actually download data from a message!

IMAP provides lots of knobs for allowing clients to request partial data about messages, including the size of a message, flags (like `\Seen` which means the message has been read, and `\Answered` which means the message has been replied to), individual headers, and individual MIME parts from within a MIME message, which allows clients to optimize their bandwidth usage by downloading only the data they need. For example, a client can quickly download only basic headers for all the messages in a folder in order to generate a listing of messages for a user to browse through and then fetch the message bodies on demand.

There are just a couple more concepts we want to cover about IMAP before we wrap up.

### Unsolicited Responses and IDLE

You may have noticed some strange untagged responses in the previous example:

This is actually a notification about one message disappearing from the mailbox and another message appearing while we've had the mailbox open. It's valid in IMAP for the server to send these unsolicited messages to a connected client at any time. There's also a mode you can put an IMAP connection into, called [IDLE](https://tools.ietf.org/html/rfc2177), which is essentially only for handling notifications about changes to a mailbox and is often used by clients to quickly sync new messages coming in.

### Disconnected Syncing

Disconnected syncing allows email apps to work well in the face of airplane wifi and bad cellular connections. It's not so much a first-class feature of IMAP as a thing that you can build on top of the protocol, with significant effort, because IMAP wasn't originally designed to support it.

The way to do a disconnected sync with IMAP4 in its original form was pretty simplistic: you'd have to take the list of UIDs you have locally for each folder and compare it to the list of UIDs currently in the folder on the server, and fetch new messages and delete old ones based on the differences. As mailboxes grew, this became more and more complex for clients to handle, and later extensions like [CONDSTORE and QRESYNC](https://tools.ietf.org/html/rfc7162) improved the flow for disconnected resyncs. But even with these extensions, the process for doing a disconnected resync is complicated to implement - and even today many IMAP server implementations don't support the newer extensions, so general-purpose clients must contain conditional logic for different servers. The general reference for how to implement disconnected syncing on top of IMAP is [RFC4549](https://tools.ietf.org/html/rfc4549).

## Summary

Alright, we've done it! Through following along in this post, you've learned about the history and major components of IMAP, an open protocol for accessing and manipulating remote mailboxes. We've connected to an IMAP server, logged in to our email account, listed folders on the remote server, and downloaded message data. This is exactly what happens under the hood in email apps as you browse your mailbox. We also learned that because of how IMAP developed over the years, disconnected syncing is fairly complicated for clients to implement, which is why we built our [delta API](https://docs.nylas.com/reference#deltas) to simplify the process.

Next time, we'll be diving into the other vital open protocol for email: SMTP, which is how emails are sent. We hope you'll stick around and join in on the fun!
