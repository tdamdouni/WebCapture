# The current art of Build Configuration Tests

_Captured: 2016-03-14 at 23:09 from [ericasadun.com](http://ericasadun.com/2016/03/14/the-current-art-of-build-configuration-tests/)_

Swift now supports the following configuration tests:

  * The literals ``true`` and ``false``
  * The ``os()`` function that tests for ``OSX, iOS, watchOS, tvOS, Linux, Windows, and FreeBSD``
  * The ``arch()`` function that tests for ``x86_64, arm, arm64, i386, powerpc64, and powerpc64le``
  * The ``swift()`` function that tests for specific Swift language releases, e.g. ``swift(>=2.2)``

Update additions thanks to [Dmitri Gribenko](https://twitter.com/gribozavr), who knows the source code.
