# PDF Generation using UIPrintPageRenderer

_Captured: 2016-04-06 at 09:01 from [www.labs.saachitech.com](http://www.labs.saachitech.com/2012/10/23/pdf-generation-using-uiprintpagerenderer/)_

_Source at [Github](https://github.com/SalilJain/PDFRender)_

AirPrint enabled printers accept PDF files and UIPrintPageRenderer prints that content to PDF file. Hence UIPrintPageRenderer can draw to PDF context though there are none public API provided to use this functionality. In this post we will explore this possibility.

There are several StackOverFlow question which talk about how to use private API to achieve pdf generation utilizing UIPrintPageRenderer:

[Is there any way to generate PDF file from a XML/HTML template in iOs](http://stackoverflow.com/questions/9528658/is-there-any-way-to-generate-pdf-file-from-a-xml-html-template-in-ios/9577488#9577488)  
[Generating a PDF using the new printing stuff in iOS 4.2](http://stackoverflow.com/questions/4356436/generating-a-pdf-using-the-new-printing-stuff-in-ios-4-2/8141008#8141008)  
[How to pretend to be a Printer on iOS like the Apps Save2PDF or Adobe® CreatePDF?](http://stackoverflow.com/questions/10051791/how-to-pretend-to-be-a-printer-on-ios-like-the-apps-save2pdf-or-adobe-createpdf)

In this post we have employed the methods explained in above stack overflow questions. Following steps lead to PDf generation from simple text, html or a view:

1) Create a Print Formatter: This is basically the content you want to generate PDF with. A print formatter can be an instance of UISimpleTextPrintFormatter, UIMarkupTextPrintFormatter, or UIViewPrintFormatter. These allow to create pdf with simple text, html or a view respectively.

> NSString *html = @"<b>Hello <i>World!</i></b>";
> 
> UIMarkupTextPrintFormatter *fmt = [[UIMarkupTextPrintFormatter alloc] initWithMarkupText:html];

2) Assign print formatter to UIPrintPageRenderer: Once you have created your print formatter add it to UIPrintPageRenderer at proper index. Method addPrintFormatter:startingAtPageAtIndex: allows any print formatter to be added. One has to pass appropriate index as well.

> UIPrintPageRenderer *render = [[UIPrintPageRenderer alloc] init];
> 
> [render addPrintFormatter:fmt startingAtPageAtIndex:0];

3) Assign paperRect and printableRect: There is no public API to assign these values hence we need to use setValue:forKey: to assign these values. First we calculate the proper CGRect for these values and then use setValue:forKey: to assign these.

> CGRect page;
> 
> page.origin.x=0;
> 
> page.origin.y=0;
> 
> page.size.width=792;
> 
> page.size.height=612;
> 
> CGRect printable=CGRectInset( page, 0, 0 );
> 
> [render setValue:[NSValue valueWithCGRect:page] forKey:@"paperRect"];
> 
> [render setValue:[NSValue valueWithCGRect:printable] forKey:@"printableRect"];

4) Create PDF Context and draw: Now we create PDF context UIGraphicsBeginPDFContextToData and draw using UIPrintPageRenderer.

> NSMutableData * pdfData = [NSMutableData data];
> 
> UIGraphicsBeginPDFContextToData( pdfData, CGRectZero, nil );
> 
> for (NSInteger i=0; i < [render numberOfPages]; i++)
> 
> {
> 
> UIGraphicsBeginPDFPage();
> 
> CGRect bounds = UIGraphicsGetPDFContextBounds();
> 
> [render drawPageAtIndex:i inRect:bounds];
> 
> }
> 
> UIGraphicsEndPDFContext();

5) Save PDF file:Once the drawing is complete we can save this in a file in documents directory.

> NSArray *paths = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES);
> 
> NSString *documentsDirectory = [paths objectAtIndex:0];
> 
> NSString * pdfFile = [[documentsDirectory stringByAppendingPathComponent:@"test.pdf"] retain];
> 
> [pdfData writeToFile:pdfFile atomically:YES];
