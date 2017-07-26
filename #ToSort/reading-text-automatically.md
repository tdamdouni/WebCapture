# Reading Text Automatically

_Captured: 2017-03-26 at 19:32 from [dzone.com](https://dzone.com/articles/reading-text-automatically?edition=286925&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-26)_

It is now very easy to read (automatically) some text that can be found in a [PDF file](https://en.wikipedia.org/wiki/Portable_Document_Format). For instance, consider the program of the conference we had yesterday - and today - in Rennes.

![](https://freakonometrics.hypotheses.org/files/2017/03/laboCREM.png)

As you can see, it is working well, even in French, where we have those weird letters (with accents). Here, it is working well because the PDF is vectorized -- it was generated properly by an open office.

But sometimes, we can have only a scanned version of a letter:

![](https://freakonometrics.hypotheses.org/files/2017/03/expert.png)

Or just a picture with some typed text. I will not mention handwriting because it is much more complex.

The other day, my friend Fleur did show me a picture, and some very simple lines of code,{

![](https://freakonometrics.hypotheses.org/files/2017/03/rapport-expert-fr.png)

It looks like we've been able to extract typed text from a picture! I want to check. I have to admit, first of all, that installation on a Linux machine is tricky. One has to install the first [leptonica](https://github.com/danbloomberg/leptonica) and then follow some guidelines to install [tesseract](https://github.com/ropensci/tesseract) (see also [Artem](https://medium.com/@lucas63?source=post_header_lockup)'s [advices](https://medium.com/@lucas63/installing-tesseract-3-04-in-ubuntu-14-04-1dae8b748a32#.tgeq7u340)). It took me some time, but I've been able to install the package.

The first important step, it to train the algorithm with some texts in French (because it is in French in my picture)

Then, I did try with the picture that Fleur did send me (the picture was inserted in the core of the message):

![](https://freakonometrics.hypotheses.org/files/2017/03/unnamed.png)

> _> pic2="https://f.hypotheses.org/wp-content/blogs.dir/253/files/2017/03/unnamed.png"_

Clearly, something went wrong here. When I got that output, I thought that I did not train properly the function. But it was not the answer. As described in that [post](https://geekeries.org/2015/12/reconnaissance-de-caracteres-avec-tesseract-ocr/) (in French) it is necessary to have a clean picture, to read it properly:

![](https://freakonometrics.hypotheses.org/files/2017/03/BasicBoundry.png)

And actually, if we zoom in our picture -- the first one, used by Fleur, to show me that package -- we have:

![](https://freakonometrics.hypotheses.org/files/2017/03/teser1.png)

> _While for the second one -- with a lower resolution -- we have:_

![](https://freakonometrics.hypotheses.org/files/2017/03/teser2.png)

> _If you don't see the difference, look more carefully:_

![](https://freakonometrics.hypotheses.org/files/2017/03/tes12.png)

> _For the first one, and for the second one:_

![](https://freakonometrics.hypotheses.org/files/2017/03/teser22.png)

It is necessary to have a scan of a typed text with high resolution. And you have to admit: That it is awesome.

The good thing is that I have to work with a judge in France to assess the quality of experts. And since most of the reports are typed and then scanned, I am glad to have such a function. I just have to make sure that the resolution is high enough.
