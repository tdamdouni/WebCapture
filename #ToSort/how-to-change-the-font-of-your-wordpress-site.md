# How to Change the Font of Your WordPress Site

_Captured: 2017-04-23 at 10:53 from [whatswp.com](https://whatswp.com/change-font-wordpress-site/)_

You use the word to tell stories, showcase expertise, and build the relationship with your readers. It is just the meat and potatoes of your personal website or blog. However, you'd better pay attention to the font selection as it largely influences the readability and uniqueness of a site.

In fact, the change of website fonts may happen for two situations:

  * You want the word display to be 100% match your website design.
  * You hope your readers can view the content easily whatever the fonts they install.

In the following, we have come out a tutorial concerning about how to change the font of WordPress no matter what situation you encounter.

## Change Font for Website Design

Generally, every WordPress theme comes with a default font featuring a wide variety of types, sizes, and styles. If you dislike it and want to make some changes, simply make use of your WordPress admin panel and do some configurations of the Appearance section.

**Log into WordPress Dashboard**

In the very beginning, you need to log into the WordPress dashboard using your account and password. Then, scroll down to the Appearance section that is located at the left sidebar, and click on the Editor button.

Now, hit the Stylesheet button at the right hand of the whole screen, which is under the Styles category like the image showed in below.

![Stylesheet screen](https://whatswp.com/wp-content/uploads/2014/01/css.png)

After making sure that you are on the main stylesheet (style.css) screen, you can add some attributes to your CSS to change the size, color, font, and many more for your text using some codes listed in the following parts.

![WordPress Appearance section](https://whatswp.com/wp-content/uploads/2014/01/appearance.jpg)

**Font Family**

The CSS of font-family property indicates a list of primary font names to display your contents. Different names are separated by a comma, indicating that they are alternative options. Generally, the browser chooses the first font on the list. If it is not installed on the computer, then browser will select from the fallback fonts.

As there is no guarantee that a certain font selected by you is installed on the computer of your readers, you'd better add some generic fonts, such as Arial, Calibri, Serif, Times New Roman, and Verdana.

To achieve this, you simply need to paste the following code at the top of the "style.css" sheet, and click Update File button. Note that we are taking the "Courier New, Courier, monospace" font type as an example.

![Font Family](https://whatswp.com/wp-content/uploads/2014/05/family-coding.png)

**Font Size**

You can also change the font size as you wish, making it suitable for the overall layout of your theme. In the following, we have listed a simple example of how to set a fixed font size of your navigation menu to 24 pixels (24px).

![Font Size](https://whatswp.com/wp-content/uploads/2014/05/font-size.png)

In fact, setting your font with a fixed size has a disadvantage. After all, your readers use different browsers with different settings, so your content can not be guaranteed to display perfectly with a fixed size.

To resolve the drawback and ensure a high level of scalability, you can make use of the flexible relative unit of em to control the typography like size, margins and indents, leading. Thus, the word displayed on your readers' screen can resize itself according to the computer settings. The code just looks like the following.

![Font Size Example](https://whatswp.com/wp-content/uploads/2014/05/font-size-example.png)

**Font Color**

Generally, the default font color is black, which is best suited to a white background. However, if the background color of the theme is dark blue, then you'd better change your font with a light color. To do this, simply add the following code into your style.css page.

![Font Color](https://whatswp.com/wp-content/uploads/2014/05/font-color.png)

## Change Font for Reading Experience

Sometimes, you may encounter a fonts problem that visitors visit your site but don't have the corresponding fonts installed on their local computer, which results in they cannot see your standard design. This issue is serious because you never know which font might be replaced and what it looks like on others' browser.

As a webmaster, it's your job to make your site looks exactly like your clients want. Therefore, you should use custom fonts, which ensure that all visitors are able to see the same fonts you see when looking at the pages.

**Manually Add Custom Fonts to WordPress with @Font-face**

![@font-face](https://whatswp.com/wp-content/uploads/2014/05/fontface.jpg)

You can use @Font-face to manually add custom fonts to WordPress and other websites. @Font-face is a CSS rule that enables visitors to download your custom font from your server to properly view your site if they don't have the font installed. With it, web designers no long have to use one of the "web-safe" fonts, but can freely utilize a stunning font as they wish, and visitors can see the exactly same presentation no matter they install the font or not.

First of all, you need to download the required fonts. Generally, Dafont and Google Fonts Directory are good places. Once you find the proper font, download it and unzip the file. Now, you can read the readme file for font's usage and installation instructions.

Note that, you'd better install the custom CSS on the server to make it work with the download font perfectly. And also, you are allowed to upload the font file into a custom folder created by yourself. Besides, you should remember the font URL and head over to the theme's style files for quick editing.

Then, you can add support for custom fonts by including the font file in the CSS file. In order to add support for almost custom fonts, you can insert the following code to the main style.css file.

![add custom fonts code](https://whatswp.com/wp-content/uploads/2014/05/add-custom-fonts-code-1.jpg)

Still now, you have successfully added a custom font to WordPress. To make use of it, you can simply input the name of the custom font within the font-family selector, such as

At present, the new custom font has been included on your site and your visitors can see your webpage normally whether they have installed the font or not.

## Font Plugin

The above mentioned method requires you to have a certain degree of CSS coding knowledge. If you know nothing about this field, you can also take advantage of some user-friendly WordPress plugins. Note that using plugins to add custom fonts is very easy. You can simply install the required plugin by following [this tutorial](https://whatswp.com/how-to-install-wordpress-plugins/) and customize the settings as you need.

**WP Google Fonts** - Google's free font directory is one of the most exciting developments in web typography in a very long time. The WP Google Fonts plugin enables users to easily add fonts from its directory to WordPress theme.

**Use Any Font** - This is a specialized WordPress plugin that allows you to embed any fonts in your websites. It gives users freedom to use any fonts so that you can use the font you wish if you have its font format. With the simple working interface, you can handle it with ease, no css knowledge needed.

**Typecase Web Fonts** - With over 500 fonts from Google Web Fonts, Typecase is a unique and easy-to-use typography plugin that allows you to quickly browse, find, and select fonts to apply to your website.
