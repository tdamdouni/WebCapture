# Get HTML from safari share extension?

_Captured: 2016-05-08 at 10:52 from [stackoverflow.com](http://stackoverflow.com/questions/31919684/get-html-from-safari-share-extension)_

In the extension share, I manage to get the URL of the safari page with the following code:
    
    
    NSExtensionItem*item =self.extensionContext.inputItems.firstObject;NSItemProvider*itemProvider = item.attachments.firstObject;if([itemProvider hasItemConformingToTypeIdentifier:(NSString*)kUTTypeURL]){[itemProvider loadItemForTypeIdentifier:(NSString*)kUTTypeURL
                                            options:nil
                                  completionHandler:^(NSURL *url,NSError*error){NSLog(@"%@", url.absoluteString);}];}

My question is: can I get also the HTML of the page???

Thanks.

[itemProvider loadItemForTypeIdentifier: (NSString *) kUTTypePropertyList
                                            options: 0
                                  completionHandler: ^(id<NSSecureCoding> item, NSError *error) {

                                      if (item != nil) {

                                          NSDictionary *resultDict = (NSDictionary *) item;

                                          NSString *jsString = resultDict[NSExtensionJavaScriptPreprocessingResultsKey][@"content"];

                                      }

                                  }];
