# An Intro to PyPDF2

_Captured: 2018-06-14 at 19:24 from [dzone.com](https://dzone.com/articles/an-intro-to-pypdf2?edition=382195&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-14)_

The PyPDF2 package is a pure-Python PDF library that you can use for splitting, merging, cropping, and transforming pages in your PDFs. According to the PyPDF2 website, you can also use PyPDF2 to add data, viewing options, and passwords to the PDFs, too. Finally, you can use PyPDF2 to extract text and metadata from your PDFs.

PyPDF2 is actually a fork of the original pyPdf, which was written by Mathiew Fenniak and released in 2005. However, the original pyPdf's last release was in 2014. A company called Phaseit, Inc. spoke with Mathieu and ended up sponsoring PyPDF2 as a fork of pyPdf.

At the time of writing, the PyPDF2 package hasn't had a release since 2016. However, it is still a solid and useful package that is worth your time to learn.

The following lists what we will be learning in this article:

  * Extracting metadata
  * Splitting documents
  * Merging 2 PDF files into 1
  * Rotating pages
  * Overlaying/watermarking Pages
  * Encrypting/decrypting

Let's start by learning how to install PyPDF2!

## Installation

PyPDF2 is a pure Python package, so you can install it using _pip_ (assuming _pip_ is in your system's path):

As usual, you should install third-party Python packages to a Python virtual environment to make sure that it works the way you want it to.

## Extracting Metadata From PDFs

You can use PyPDF2 to extract a fair amount of useful data from any PDF. For example, you can learn the author of the document, its title and subject, and how many pages there are. Let's find out how by downloading the sample of this book from [Leanpub](https://leanpub.com/reportlab). The sample I downloaded was called _reportlab-sample.pdf_. I will include this PDF for you to use in the GitHub source code as well.

Here's the code:
    
    
        with open(path, 'rb') as f:

Here, we import the _PdfFileReader_ class from _PyPDF2_. This class gives us the ability to read a PDF and extract data from it using various accessor methods. The first thing we do is create our own _get_info_ function that accepts a PDF file path as its only argument. Then, we open the file in read-only binary mode. Next, we pass that file handler into PdfFileReader and create an instance of it.

Now, we can extract some information from the PDF by using the _getDocumentInfo_ method. This will return an instance of _PyPDF2.pdf.DocumentInformation_, which has the following useful attributes, among others:

  * _author_
  * _creator_
  * _producer_
  * _subject_
  * _title_

If you print out the _DocumentInformation_ object, this is what you will see:

We can also get the number of pages in the PDF by calling the _getNumPages_ method.

## Extracting Text From PDFs

PyPDF2 has limited support for extracting text from PDFs. It doesn't have built-in support for extracting images, unfortunately. I have seen some recipes on StackOverflow that use PyPDF2 to extract images, but the code examples seem to be pretty hit-or-miss.

Let's try to extract the text from the first page of the PDF that we downloaded in the previous section:
    
    
        with open(path, 'rb') as f:
    
    
            print('Page type: {}'.format(str(type(page))))

You will note that this code starts out in much the same way as our previous example. We still need to create an instance of _PdfFileReader_. But this time, we grab a page using the _getPage_ method. PyPDF2 is zero-based, much like most things in Python, so when you pass it a one, it actually grabs the second page. The first page, in this case, is just an image, so it wouldn't have any text.

Interestingly, if you run this example, you will find that it doesn't return any text. Instead, all I got was a series of line break characters. Unfortunately, PyPDF2 has pretty limited support for extracting text. Even if it is able to extract text, it may not be in the order you expect and the spacing may be different, as well.

To get this example code to work, you will need to try running it against a different PDF. I found one on the [United States Internal Revenue Service website](https://www.irs.gov/pub/irs-pdf/fw9.pdf).

This is a W9 form for people who are self-employed or contract employees. It can be used in other situations too. Anyway, I downloaded it as _w9.pdf_. If you use that PDF instead of the sample one, it will happily extract some of the text from page 2. I won't reproduce the output here as it is kind of lengthy though.

## Splitting PDFs

The PyPDF2 package gives you the ability to split up a single PDF into multiple ones. You just need to tell it how many pages you want. For this example, we will open up the W9 PDF from the previous example and loop over all six of its pages. We will split off each page and turn it into its own standalone PDF.

Let's find out how:

For this example, we need to import both the _PdfFileReader_ and the _PdfFileWriter_. Then we create a fun little function called _pdf_splitter_. It accepts the path of the input PDF. The first line of this function will grab the name of the input file, minus the extension. Next we open the PDF up and create a reader object. Then we loop over all the pages using the reader object's _getNumPages_ method.

Inside of the _for_ loop, we create an instance of _PdfFileWriter_. We then add a page to our writer object using its _addPage_ method. This method accepts a page object, so to get the page object, we call the reader object's _getPage_ method. Now, we had added one page to our writer object. The next step is to create a unique file name, which we do by using the original file name plus the word "page" plus the page number + 1. We add the one because PyPDF2's page numbers are zero-based, so page 0 is actually page 1.

Finally, we open the new file name in write-binary mode and use the PDF writer object's _write_ method to write the object's contents to disk.

## Merging Multiple PDFs Together

Now that we have a bunch of PDFs, let's learn how we might take them and merge them back together. One useful use case for doing this is for businesses to merge their dailies into a single PDF. I have needed to merge PDFs for work and for fun. One project that sticks out in my mind is scanning documents in. Depending on the scanner you have, you might end up scanning a document into multiple PDFs, so being able to join them together again can be wonderful.

When the original PyPdf came out, the only way to get it to merge multiple PDFs together was like this:

Here, we create a _PdfFileWriter_ object and several _PdfFileReader_ objects. For each PDF path, we create a _PdfFileReader_ object and then loop over its pages, adding each and every page to our writer object. Then we write out the writer object's contents to disk.

PyPDF2 made this a bit simpler by creating a _PdfFileMerger_ class:

Here, we just need to create the _PdfFileMerger_ object and then loop through the PDF paths, appending them to our merging object. PyPDF2 will automatically append the entire document so you don't need to loop through all the pages of each document yourself. Then, we just write it out to disk.

The _PdfFileMerger_ class also has a _merge_ method that you can use. Its code definition looks like this:

Basically, the merge method allows you to tell PyPDF where to merge a page by page number. So if you have created a merging object with three pages in it, you can tell the merging object to merge the next document in at a specific position. This allows the developer to do some pretty complex merging operations. Give it a try and see what you can do!

## Rotating Pages

PyPDF2 gives you the ability to rotate pages. However, you must rotate in 90 degrees increments. You can rotate the PDF pages either clockwise or counterclockwise. Here's a simple example:

Here we create our PDF reader and writer objects as before. Then we get the first and second pages of the PDF that we passed in. We then rotate the first page 90 degrees clockwise or to the right. Then we rotate the second page 90 degrees counter-clockwise. Finally, we add the third page in its normal orientation to the writer object and write out our new three-page PDF file.

If you open the PDF, you will find that the first two pages are now rotated in opposite directions of each other with the third page in its normal orientation.

## Overlaying/Watermarking Pages

PyPDF2 also supports merging PDF pages together or overlaying pages on top of each other. This can be useful if you want to watermark the pages in your PDF. For example, one of the eBook distributors I use will "watermark" the PDF versions of my book with the buyer's email address. Another use case that I have seen is to add printer control marks to the edge of the page to tell the printer when a certain document has reached its end.

For this example we will take one of the logos I use for my blog, "The Mouse vs. the Python," and overlay it on top of the W9 form from earlier:

The first thing we do here is extract the watermark page from the PDF. Then we open the PDF that we want to apply the watermark to. We use a _for_ loop to iterate over each of its pages and call the page object's _mergePage_ method to apply the watermark. Next we add that watermarked page to our PDF writer object. Once the loop finishes, we write our new watermarked version out to disk.

Here's what the first page looked like:

![Image title](http://www.blog.pythonlibrary.org/wp-content/uploads/2018/06/watermark.png)

> _That was pretty easy._

## PDF Encryption

The PyPDF2 package also supports adding a password and encryption to your existing PDFs. As you may recall from Chapter 10, PDFs support a user password and an owner password. The user password only allows the user to open and read a PDF, but may have some restrictions applied to the PDF that could prevent the user from printing, for example. As far as I can tell, you can't actually apply any restrictions using PyPDF2 or it's just not documented well.

Here's how to add a password to a PDF with PyPDF2:

All we did here was create a set of PDF reader and write objects and read all the pages with the reader. Then we added those pages out to the specified writer object and added the specified password. If you only set the user password, then the owner password is set to the user password automatically. Whenever you add a password, 128-bit encryption is applied by default. If you set that argument to False, then the PDF will be encrypted at 40-bit encryption instead.

## Wrapping Up

We covered a lot of useful information in this article. You learned how to extract metadata and text from your PDFs. We found out how to split and merge PDFs. You also learned how to rotate pages in a PDF and apply watermarks. Finally, we discovered that PyPDF2 can add encryption and passwords to our PDFs.
