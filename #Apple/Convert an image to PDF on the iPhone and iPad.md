# Convert an image to PDF on the iPhone and iPad

_Captured: 2016-03-30 at 19:56 from [ipdfdev.com](http://ipdfdev.com/2011/04/22/convert-an-image-to-pdf-on-the-iphone-and-ipad/)_

A reader asked a me about image to PDF conversion a few days ago and I promised him an article, so here it is.

Image to PDF conversion is based on Quartz API. Using Quartz we can create PDF files and add content to them, the conversion actually means drawing the image on a PDF page.

Let's begin.

First we compute the size of the PDF page. Based on the image size and the resolution we want to draw the image, the page size is computed like this (for flexibility different horizontal and vertical resolutions are supported):
    
    double pageWidth = image.size.width * image.scale * 72 / horzRes;
        double pageHeight = image.size.height * image.scale * 72 / vertRes;

Now we're ready to create the PDF file. It can be created directly on disk or in memory. For flexibility let's create it in memory.
    
        NSMutableData *pdfFile = [[NSMutableData alloc] init];
        CGDataConsumerRef pdfConsumer = 
            CGDataConsumerCreateWithCFData((CFMutableDataRef)pdfFile);
        // The page size matches the image, no white borders.
        CGRect mediaBox = CGRectMake(0, 0, pageWidth, pageHeight);
        CGContextRef pdfContext = CGPDFContextCreate(pdfConsumer, &amp;mediaBox, NULL);

The PDF context is created, we can now perform the conversion based on image's orientation (mostly required by the images taken with the camera):

        CGContextBeginPage(pdfContext, &amp;mediaBox);
        switch (image.imageOrientation) {
            case UIImageOrientationDown:
                CGContextTranslateCTM(pdfContext, pageWidth, pageHeight);
                CGContextScaleCTM(pdfContext, -1, -1);
                break;
            case UIImageOrientationLeft:
                mediaBox.size.width = pageHeight;
                mediaBox.size.height = pageWidth;
                CGContextTranslateCTM(pdfContext, pageWidth, 0);
                CGContextRotateCTM(pdfContext, M_PI / 2);
                break;
            case UIImageOrientationRight:
                mediaBox.size.width = pageHeight;
                mediaBox.size.height = pageWidth;
                CGContextTranslateCTM(pdfContext, 0, pageHeight);
                CGContextRotateCTM(pdfContext, -M_PI / 2);
                break;
            case UIImageOrientationUp:
            default:
                break;
        } 
        CGContextDrawImage(pdfContext, mediaBox, [image CGImage]);
        CGContextEndPage(pdfContext);

The work is done, finalize the PDF file and release the used objects.
    
        CGContextRelease(pdfContext);
        CGDataConsumerRelease(pdfConsumer);

The PDF file is now available in the pdfFile variable.  
I placed all the code above in the `convertImageToPDF:withHorizontalResolution:verticalResolution:` static method in the `PDFImageConverter` utility class, it can be used like this:

Sometimes it is necessary to convert an image to PDF and use a predefined page size, such as Letter or A4. Also a maximum bounding rectangle can be specified for the image, so it is placed at a specific position on the page and it does not get out of the page. In this situation the image size must be adjusted (increased resolution) to make sure the image fits the given rectangle.

    
        double imageWidth = image.size.width * image.scale * 72 / resolution;
        double imageHeight = image.size.height * image.scale * 72 / resolution;
     
        double sx = imageWidth / boundsRect.size.width;
        double sy = imageHeight / boundsRect.size.height;
     
        // At least one image edge is larger than maxBoundsRect, reduce its size.
        if ((sx &gt; 1) || (sy &gt; 1)) {
            double maxScale = sx &gt; sy ? sx : sy;
            imageWidth = imageWidth / maxScale;
            imageHeight = imageHeight / maxScale;
        }
     
        // Put the image in the top left corner of the bounding rectangle
        CGRect imageBox = CGRectMake(
            boundsRect.origin.x, boundsRect.origin.y + boundsRect.size.height - imageHeight, 
            imageWidth, imageHeight);

Having the final box, the image can be converted to PDF using the code in the first half of the article.  
The code for the new conversion method is placed in the `convertImageToPDF:withResolution:maxBoundsRect:pageSize:` static method in the `PDFImageConverter` utility class, it is used like this:

    
        CGSize pageSize = CGSizeMake(612, 792);
        CGRect imageBoundsRect = CGRectMake(50, 50, 512, 692);
     
        NSData *pdfData = [PDFImageConverter convertImageToPDF: image 
            withResolution: 300 maxBoundsRect: imageBoundsRect pageSize: pageSize];
     
        NSString *path = [NSHomeDirectory() stringByAppendingPathComponent: @"Documents/image.pdf"];
        [pdfData writeToFile:path atomically:NO];
