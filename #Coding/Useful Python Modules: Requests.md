# Useful Python Modules: Requests

_Captured: 2016-09-13 at 19:40 from [dancallahan.info](https://dancallahan.info/journal/python-requests/)_

[Source](https://dancallahan.info/journal/python-requests/ "Permalink to Useful Python Modules: Requests | Dan Callahan")

Published Wednesday, November 9th, 2011.

This article is based on a presentation I gave at [PyMNtos][2] in June, 2011.

Working with HTTP in Python is needlessly cumbersome. The included `urllib2` module is comprehensive at the expense of great complexity. [Kenneth Reitz][3]'s [Requests][4] module, by contrast, eschewes completeness in favor of simplifying common use cases.

## A Simple Example

Imagine we're trying to `GET` a resource at `http://example.test/` and look up the response code, its `content-type` header, and the contents of the response. This is pretty simple with both `urllib2` and Requests:

### urllib2

    >>> import urllib2
    >>> url = 'http://example.test/'
    >>> response = urllib2.urlopen(url)
    >>> response.getcode()
    200
    >>> response.headers.getheader('content-type')
    'text/html; charset=utf-8'
    >>> response.read()
    'Hello, world!'

### Requests

    >>> import requests
    >>> url = 'http://example.test/'
    >>> response = requests.get(url)
    >>> response.status_code
    200
    >>> response.headers['content-type']
    'text/html; charset=utf-8'
    >>> response.content
    u'Hello, world!'

The two are very similar, with Requests offering access to the response's properties via attributes, versus the method calls required by `urllib2`. There are two other subtle but important differences illustrated above:

1. Responses automatically decoded the response into Unicode.

2. Responses automatically saved the content, so you can access it multiple times, unlike the read-once file-like object returned by `urllib2.urlopen()`.

The second issue is particularly annoying when sketching out code in the Python REPL.

## A More Complex Example

Now let's try something slightly more complex: `GET` a resource at `http://foo.test/secret`, which requires HTTP Basic authentication. Using the code above as a template, it seems like we just need to replace the call to `urllib2.urlopen()` or to `requests.get()` with something that sends a username and password along with the request.

This is where `urllib2` goes off the rails.

### urllib2

    >>> import urllib2
    >>> url = 'http://example.test/secret'
    >>> password_manager = urllib2.HTTPPasswordMgrWithDefaultRealm()
    >>> password_manager.add_password(None, url, 'dan', 'h0tdish')
    >>> auth_handler = urllib2.HTTPBasicAuthHandler(password_manager)
    >>> opener = urllib2.build_opener(auth_handler)
    >>> urllib2.install_opener(opener)
    >>> response = urllib2.urlopen(url)
    >>> response.getcode()
    200
    >>> response.read()
    'Welcome to the secret page!'

What was one simple function call ballooned into instantiating two classes, building a third, installing that one into the global urllib2 module, and then finally making the `urlopen` call.

Confused? Here's a link to the [urllib2 documentation][5].

So how does Requests handle the same situation?

### Requests

    >>> import requests
    >>> url = 'http://example.test/secret'
    >>> response = requests.get(url, auth=('dan', 'h0tdish'))
    >>> response.status_code
    200
    >>> response.content
    u'Welcome to the secret page!'

By simply adding an `auth` keyword parameter to the function call.

I bet you can remember how to do that without consulting the docs, too.

## Error Handling

Requests also has far more convenient error handling. If you used an invalid username and password above, `urllib2` would raise a `urllib2.URLError`, while Requests would return a normal response object, as expected. All it takes to determine if the request was successful is a quick peek at the boolean `response.ok` attribute:

    >>> response = requests.get(url, auth=('dan', 'wrongPass'))
    >>> response.ok
    False

The same goes for the remote server being down: `urllib2` raises a `urllib2.URLError`, while Requests returns a normal response object, which you can introspect to learn more about the reason for failure.

## Other Features

* Requests exposes a similarly simple API for `HEAD`, `POST`, `PUT`, `PATCH`, and `DELETE`.
* It handles multipart file uploads, as well as automatically form-encoding dictionaries.
* The documentation is great.
* And much more.

Requests is fantastic. Give it a shot the next time you need to communicate over HTTP.

## Links

* The [Requests][4] website.
* The [PyPI entry][6] for Requests.

You can also find me on [Google+][7], [LinkedIn][8], [BitBucket][9], and [GitHub][10].

You can [subscribe][11] to this blog in your favorite RSS / Atom reader.

Need to get in touch? <a href="http://www.google.com/recaptcha/mailhide/d?k=01D3TeD8cNv8XZ2VE2ADcqxw==&c=HxuBclsHxKB2RrX-Ucgof2UQ4x3MQ82ci5l43cj636Q=" onclick="window.open('http://www.google.com/recaptcha/mailhide/d?k

[1]: /
[2]: http://python.mn/
[3]: http://kennethreitz.com/
[4]: http://python-requests.org
[5]: http://docs.python.org/release/2.7/library/urllib2.html
[6]: http://pypi.python.org/pypi/requests
[7]: https://plus.google.com/100352373939446760176/posts
[8]: http://www.linkedin.com/in/callahad/
[9]: https://bitbucket.org/callahad/
[10]: https://github.com/callahad/
[11]: /atom.xml
