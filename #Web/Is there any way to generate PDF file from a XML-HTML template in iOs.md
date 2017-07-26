# Is there any way to generate PDF file from a XML/HTML template in iOs

_Captured: 2016-04-06 at 09:03 from [stackoverflow.com](http://stackoverflow.com/questions/9528658/is-there-any-way-to-generate-pdf-file-from-a-xml-html-template-in-ios/9577488#9577488)_

@TomSwift : agree with his answer but i would like to explain in better way

## To be able create `PDF` from `UIWebView` is load HTML to yourWebView or there might be case yourWebView can also be hidden to generate PDF but process remains the same

### 1) Added `Category` of `UIPrintPageRenderer` for getting PDF Data as yourWebView.viewPrintFormatter need to be used
    
    
    @interface UIPrintPageRenderer (PDF)
    - (NSData*) printToPDF;
    @end
    
    @implementation UIPrintPageRenderer (PDF)
    - (NSData*) printToPDF
    {
      NSMutableData *pdfData = [NSMutableData data];
      UIGraphicsBeginPDFContextToData( pdfData, self.paperRect, nil );
      [self prepareForDrawingPages: NSMakeRange(0, self.numberOfPages)];
      CGRect bounds = UIGraphicsGetPDFContextBounds();
      for ( int i = 0 ; i < self.numberOfPages ; i++ )
      {
        UIGraphicsBeginPDFPage();
        [self drawPageAtIndex: i inRect: bounds];
      }
      UIGraphicsEndPDFContext();
      return pdfData;
    }
    @end

### 2) Add these define for A4 size or any custom size you want
    
    
    #define kPaperSizeA4 CGSizeMake(595.2,841.8)

### 3) Process how we can create PDF
    
    
    //create print renderer
    UIPrintPageRenderer *render = [[UIPrintPageRenderer alloc] init];
    [render addPrintFormatter:yourWebView.viewPrintFormatter startingAtPageAtIndex:0];
    
    //provide padding ---- increase these values according to your requirement
    float topPadding = 10.0f;
    float bottomPadding = 10.0f;
    float leftPadding = 10.0f;
    float rightPadding = 10.0f;
    
    //provide rect for printing and for actual PDF Rect of page
    CGRect printableRect = CGRectMake(leftPadding,
                                      topPadding,
                                      kPaperSizeA4.width-leftPadding-rightPadding,
                                      kPaperSizeA4.height-topPadding-bottomPadding);
    CGRect paperRect = CGRectMake(0, 0, kPaperSizeA4.width, kPaperSizeA4.height);
    [render setValue:[NSValue valueWithCGRect:paperRect] forKey:@"paperRect"];
    [render setValue:[NSValue valueWithCGRect:printableRect] forKey:@"printableRect"];
    
    //category created above is used here 
    NSData *pdfData = [render printToPDF];
    //Save PDF to directory for usage
    if (pdfData) {
      [pdfData writeToFile:[NSString stringWithFormat:@"%@/tmp.pdf",NSTemporaryDirectory()] atomically: YES];
    }
    else
    {
      NSLog(@"PDF couldnot be created");
    }
