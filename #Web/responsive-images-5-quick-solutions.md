# Responsive Images: 5 Quick Solutions

_Captured: 2017-09-07 at 19:43 from [dzone.com](https://dzone.com/articles/responsive-images-5-quick-solutions?edition=324391&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=mobile%202017-09-07)_

### Here are five easy solutions to help you make your mobile site's images more responsive, providing a better, faster experience for users.

Get gorgeous, [multi-touch charts](https://dzone.com/go?i=237241&u=http%3A%2F%2Fbit.ly%2Fiosdzone) for your iOS application with just a few lines of code.

Serving responsive images on your site is important in providing an optimal user experience. Mobile devices already have a [higher market share](http://gs.statcounter.com/platform-market-share/desktop-mobile-tablet) than their desktop counterparts, making it critical to serve images that dynamically fit the different screen sizes used by your website's visitors.

![Image title](https://dzone.com/storage/temp/6434856-responsive-1622825-960-720.png)

Serving responsive images becomes more complex when you consider that many basic solutions just adjust the image dimensions but still require visitors to download the full image size, often markedly reducing your website's speed on slow connections.

The following guide offers five quick solutions that can help you make the images on your site's pages responsive.

## 1\. Use a PHP Script

[Adaptive Images](http://www.adaptive-images.com/) is a PHP script that checks every website visitor's maximum screen size when your server receives an image request from their device. The script checks if a rescaled image exists, and if it doesn't, Adaptive Image creates a new down-scaled image, serving it to the user and storing it in the cache for easy retrieval when the next person with the same maximum screen size visits your website.

The method used by Adaptive Images requires looking for a cookie on each visiting device. If the script cannot find a cookie, it checks the User Agent String, which identifies whether someone is visiting your site on desktop or mobile. If the script finds the latter, in the absence of a cookie it will serve the lowest resolution image available.

Since Adaptive Images resizes the image files and sends the resized files to visitors' devices, this is a responsive image solution that maximizes the user experience. The main drawbacks are the coding knowledge required to install Adaptive Images, the need to use Apache 2 web servers, and the fact that your images must be hosted on the servers.

## 2\. HTML Picture Tags

A relatively new HTML5 development, the picture element, has changed the way developers deal with the issue of responsive images. Since images are essentially data and HTML deals with data, it makes sense to use a solution like this for responsive images.

The picture element has revolutionized the problem of serving responsive images by allowing you to customize the image served according to a number of factors, such as:

  * Pixel densities, serving higher quality images on devices with higher pixel densities.

  * Resolution, allowing you to optimize the image served depending on the resolution of the screen used to browse your site.

  * Art direction, meaning the images get cropped to fit a particular screen's features.

**![Art Direction Example - http://usecases.responsiveimages.org/#resolution-based-selection](https://lh5.googleusercontent.com/t2hdCnO5CXuEGzD3KfaZzeoTJrIsg_TDM_X6XW7CX9DT9k0rURLZOELG_K_Wp7PjAw3GTDZyRARJO08KZ6RJzyVHMixvtb4te_o4UKY3AF1yWHrMgkf1sEx4hT3QWEEa0c10uRoG)**

> _Art Direction Example - http://usecases.responsiveimages.org/#resolution-based-selection_

With the picture element, you get a true responsive image solution that doesn't necessitate complicated hacks, including Javascript. You can even serve different images types, such as WebP, to devices using browsers that support this file type. Additionally, the coding can be customized to allow the visiting device's browser to choose an optimal image for a device depending on the selection of images specified.

Again, the picture element in HTML5 is a responsive image solution that requires adequate coding knowledge, but it is well worth the benefits to your website's visitors to hire a developer for implementing the picture element on your site.

## 3\. Responsive Image Plugins

You're in luck if your website is based on a Content Management System such as Wordpress. There are plenty of free and paid plugins available for Wordpress that allow you to serve responsive images effortlessly, requiring little more than a few clicks of your mouse.

[RICG](https://wordpress.org/plugins/ricg-responsive-images/) Responsive Images is one such plugin which is helpful for serving responsive images. The plugin works by including all available sizes for each image you upload and including these images sizes in the srcset so that visitor's browsers can choose the optimal image for their devices.

There are many other excellent responsive image options available in the Wordpress plugin repository so you don't need to limit yourself to RICG Responsive Images. Other options include WP Responsive Image, Picture Fill WP, and Simple Responsive Image.

## 4\. Network Information API - Automatically Adapt to Device Network Speed

Estimating the exact connection speed of a device used to browse your website is a difficult task that hasn't seen much progress over the last few years. According to Google, 70 percent of global mobile network connections globally will occur at 3G or slower speeds through 2020.

When serving responsive images to a device, ideally you would use a solution that incorporates the connection speed of that device when choosing the right image.

The [Network Information API](https://mobiforge.com/design-development/html5-mobile-web-network-information-api) is a HTML5 API for acquiring information about a device's network connection. For responsive images, you can add a CSS class based on the network speed, with the rules determining whether to serve high-quality or low-quality images. One issue is that not all devices support this API, but it represents the best of what's available in terms of serving responsive images that cater for connection quality.

## 5\. Cloud-Based Image Platforms

Using a cloud-based image management platform is another great way to serve [responsive images](http://cloudinary.com/documentation/responsive_images). A service such as Cloudinary (_disclaimer: I am an advisor for Cloudinary_) can serve true responsive images without much work on your behalf or any need for coding knowledge. Simply upload your images to your cloud management platform and the platform does the rest for you.

Cloudinary, for example, uses dynamic image URLs to create different versions of your images as they are uploaded, automatically sets the <img> src URL to use the dynamic Cloudinary version, and finally, serves the optimal image based on the available width reported in the Client Hints request header.

## Conclusion

To summarize, a few quick solutions that can help you serve responsive images on your site are:

  * Using a PHP script such as Adaptive Images.

  * Taking advantage of the new HTML5 picture element to better customize the responsive image selection.

  * Using a responsive plugin on Wordpress if your site uses this CMS.

  * Incorporating connection speed into the image selection process by using an API such as the Network Information API and customizing your website's CSS.

  * Leveraging a cloud-based image management platform to handle responsive image design automatically.

.Net developers: use [Highcharts](https://dzone.com/go?i=237242&u=http%3A%2F%2Fbit.ly%2Fdzone-dotnet), the industry's leading interactive charting library, without writing a single line of JavaScript.
