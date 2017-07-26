# Convert a PDF page to image on the iPhone and iPad

_Captured: 2016-03-30 at 19:53 from [ipdfdev.com](http://ipdfdev.com/2011/03/28/convert-a-pdf-page-to-image-on-the-iphone-and-ipad/)_

A common requirement when working with PDF files is to convert them to images. Because the iOS includes native PDF support, converting a PDF page to image seems easy. A graphic context is created for the image, the PDF page is rendered on image's graphic context and then the image is saved. Yet there is a catch when rendering the PDF page on the image's graphic context.

Now lets see how we put this idea into practice and convert a PDF page to image at a specific resolution.

The page visible area is determined by the page CropBox. The page orientation is given by the page rotation angle. We need these values to compute the size of the destination image.

    
        CGRect cropBox = CGPDFPageGetBoxRect(page, kCGPDFCropBox);
        int pageRotation = CGPDFPageGetRotationAngle(page);

Assuming the application will run on iOS 4.x, we can use the `UIGraphicsBeginImageContextWithOptions` method to create the graphic context and its underlying image.

    
        if ((pageRotation == 0) || (pageRotation == 180) ||(pageRotation == -180)) {
            UIGraphicsBeginImageContextWithOptions(cropBox.size, NO, resolution / 72); 
        }
        else {
            UIGraphicsBeginImageContextWithOptions(
                CGSizeMake(cropBox.size.height, cropBox.size.width), NO, resolution / 72); 
        }
     
        CGContextRef imageContext = UIGraphicsGetCurrentContext();

The PDF page can now be rendered on image's graphic context. But this can be a complex task because of all possible page rotations and page CropBox positions. Lucky for us this has been already implemented in the `renderPage:inContext:` method developed in the article ['Display a PDF page on the iPhone and iPad'](http://ipdfdev.com/2011/03/23/display-a-pdf-page-on-the-iphone-and-ipad/ ). It is a static method in `PDFPageRenderer` class and it takes care of all the complications related to coordinate systems and transformations.

    
        [PDFPageRenderer renderPage:page inContext:imageContext];

The page has been rendered, we can now use the image in the application.
   
    
        UIImage *pageImage = UIGraphicsGetImageFromCurrentImageContext();  	
        UIGraphicsEndImageContext();

The complete source code and test PDF files can be downloaded below.  
I placed the code in the static method `convertPDFPageToImage:withResolution:` in the `PDFPageConverter` class, the method is used like this:

    
        CGPDFPageRef page = CGPDFDocumentGetPage(pdfDocument, 1);
     
        UIImage *pageImage = [PDFPageConverter convertPDFPageToImage:page withResolution:144];
        NSString *pngPath = [NSHomeDirectory() stringByAppendingPathComponent:destinationPath];
        [UIImagePNGRepresentation(pageImage) writeToFile:pngPath atomically:YES];
