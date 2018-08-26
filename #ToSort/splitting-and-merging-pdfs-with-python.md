# Splitting and Merging PDFs With Python

_Captured: 2018-04-26 at 15:50 from [dzone.com](https://dzone.com/articles/splitting-and-merging-pdfs-with-python?edition=376203&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=big%20data%202018-04-26)_

[Hortonworks Sandbox](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) for HDP and HDF is your chance to get started on learning, developing, testing and trying out new features. Each [download](https://dzone.com/go?i=285437&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) comes preconfigured with interactive tutorials, sample data and developments from the Apache community.

The [PyPDF2](https://pythonhosted.org/PyPDF2/) package allows you to do a lot of useful operations on existing PDFs. In this article, we will learn how to split a single PDF into multiple smaller ones. We will also learn how to take a series of PDFs and join them back together into a single PDF.

## Getting Started

PyPDF2 doesn't come as a part of the Python Standard Library, so you will need to install it yourself. The preferred way to do so is to use `[pip](https://packaging.python.org/tutorials/installing-packages/)`.

Now that we have PyPDF2 installed, let's learn how to split and merge PDFs!

## Splitting PDFs

The PyPDF2 package gives you the ability to split up a single PDF into multiple ones. You just need to tell it how many pages you want. For this example, we will download a [W9 form](https://www.irs.gov/pub/irs-pdf/fw9.pdf) from the IRS and loop over all six of its pages. We will split off each page and turn it into its own standalone PDF.

Let's find out how:
    
    
        fname = os.path.splitext(os.path.basename(path))[0]
    
    
    with open(output_filename, 'wb') as out:
    
    
    print('Created: {}'.format(output_filename))

For this example, we need to import both the `PdfFileReader` and the `PdfFileWriter`. Then we create a fun little function called `pdf_splitter`. It accepts the path of the input PDF. The first line of this function will grab the name of the input file, minus the extension. Next, we open the PDF up and create a reader object. Then we loop over all the pages using the reader object's `getNumPages` method.

Inside of the `for` loop, we create an instance of `PdfFileWriter`. We then add a page to our writer object using its `addPage` method. This method accepts a page object, so to get the page object, we call the reader object's `getPage` method. Now, we added one page to our writer object. The next step is to create a unique file name, which we do by using the original file name plus the word "page" plus the page number + 1. We add the one because PyPDF2's page numbers are zero-based, so page 0 is actually page 1.

Finally, we open the new file name in write-binary mode and use the PDF writer object's `write` method to write the object's contents to disk.

## Merging Multiple PDFs Together

Now that we have a bunch of PDFs, let's learn how we might take them and merge them back together. One useful use case for doing this is for businesses to merge their dailies into a single PDF. I have needed to merge PDFs for work and for fun. One project that sticks out in my mind is scanning documents in. Depending on the scanner you have, you might end up scanning a document into multiple PDFs, so being able to join them together again can be wonderful.

When the original PyPdf came out, the only way to get it to merge multiple PDFs together was like this:
    
    
            for page in range(pdf_reader.getNumPages()):
    
    
                pdf_writer.addPage(pdf_reader.getPage(page))
    
    
    with open(output_path, 'wb') as fh:

Here, we create a `PdfFileWriter` object and several `PdfFileReader` objects. For each PDF path, we create a `PdfFileWriter` object and then loop over its pages, adding each and every page to our writer object. Then we write out the writer object's contents to disk.

PyPDF2 made this a bit simpler by creating a `PdfFileMerger` object:
    
    
    with open(output_path, 'wb') as fileobj:
    
    
        paths = glob.glob('w9_*.pdf')

Here, we just need to create the `PdfFileMerger` object and then loop through the PDF paths, appending them to our merging object. PyPDF2 will automatically append the entire document, so you don't need to loop through all the pages of each document yourself. Then, we just write it out to disk.

The `PdfFileMerger` class also has a `merge` method that you can use. Its code definition looks like this:
    
    
    def merge( self, position, fileobj, bookmark=None, pages=None, import_bookmarks=True ):
    
    
            Merges the pages from the given file into the output file at the
    
    
            :param int position: The *page number* to insert this file. File will
    
    
            :param fileobj: A File Object or an object that supports the standard read
    
    
                and seek methods similar to a File Object. Could also be a
    
    
            :param str bookmark: Optionally, you may specify a bookmark to be applied at
    
    
                the beginning of the included file by supplying the text of the bookmark.
    
    
            :param pages: can be a :ref:`Page Range <page-range>` or a ``(start, stop[, step])`` tuple
    
    
                to merge only the specified range of pages from the source
    
    
            :param bool import_bookmarks: You may prevent the source document's bookmarks
    
    
                from being imported by specifying this as ``False``.

Basically, the `merge` method allows you to tell PyPDF where to merge a page by page number. So, if you have created a merging object with three pages in it, you can tell the merging object to merge the next document in at a specific position. This allows the developer to do some pretty complex merging operations. Give it a try and see what you can do!

## Wrapping Up

PyPDF2 is a powerful and useful package. I have been using it off and on for years to work on various home and work projects. If you need to manipulate existing PDFs, then this package might be right up your alley!

[Hortonworks Sandbox](https://dzone.com/go?i=285441&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) for HDP and HDF is your chance to get started on learning, developing, testing and trying out new features. Each [download](https://dzone.com/go?i=285441&u=https%3A%2F%2Fhortonworks.com%2Fproducts%2Fsandbox%2F%3Futm_campaign%3Ddzonepre%2Fpostroll%26utm_medium%3Ddisplay%26apos%3B%26utm_source%3Ddzone%26utm_id%3D2216633) comes preconfigured with interactive tutorials, sample data and developments from the Apache community.
