# Using the System Font in Web Content

_Captured: 2015-12-09 at 12:22 from [webkit.org](https://webkit.org/blog/3709/using-the-system-font-in-web-content/)_

Web content is sometimes designed to fit in with the overall aesthetic of the underlying platform which it is being rendered on. One of the ways to achieve this is by using the platform's system font, which is possible on iOS and OS X by using the `-apple-system` CSS value for the "font-family" CSS property. On iOS 9 and OS X 10.11, doing this allows you to use Apple's new system font, San Francisco. Using `-apple-system` also correctly interacts with the font-weight CSS property to choose the correct font on Apple's latest operating systems.

On platforms which do not support `-apple-system`, the browser will simply fall back to the next item in the font-family fallback list. This provides a great way to make sure all your users get a great experience, regardless of which platform they are using.

There are [currently discussions in the w3c regarding standardizing this value](https://lists.w3.org/Archives/Public/www-style/2015Jul/0169.html) so authors could simply specify `system`. However, these discussions have not reached consensus, so WebKit prefixes this value.

Using any other mechanism to specify the system font is not guaranteed to behave as you might expect. This includes using any implementation details such as period-prefixed family names.

Going beyond the system font, iOS has dynamic type behavior, which can provide an additional level of fit and finish to your content. These text styles identify more than simply a particular font family; instead, they represent an entire style, including size and weight. These styles are therefore characterized by values given to the more-general `font` CSS property. The supported values are:
    
    
    font: -apple-system-body 
    font: -apple-system-headline 
    font: -apple-system-subheadline 
    font: -apple-system-caption1 
    font: -apple-system-caption2 
    font: -apple-system-footnote 
    font: -apple-system-short-body 
    font: -apple-system-short-headline 
    font: -apple-system-short-subheadline 
    font: -apple-system-short-caption1 
    font: -apple-system-short-footnote 
    font: -apple-system-tall-body 
    

For more information, please see [Antonio Cavedoni's fantastic WWDC presentation](https://developer.apple.com/videos/wwdc/2015/?id=804) or contact [@jonathandavis](https://twitter.com/jonathandavis/).
