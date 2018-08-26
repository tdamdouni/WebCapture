# The Concept of Cross-Browser Accessibility

_Captured: 2018-08-17 at 17:29 from [dzone.com](https://dzone.com/articles/the-concept-of-cross-browser-accessibility?edition=385389&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-08-17)_

Container Monitoring and Management eBook: [Read about the new realities of containerization.](https://dzone.com/go?i=291440&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fcontainer-monitoring-and-management.html%3Fcid%3DNA-DSP-APM-AEJ-000195-00001663-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_eb1-container-monitoring-mgmt-articlepreroll%26mrm%3D)

Is your website cross-browser accessible? How will you make sure of that? By performing accessibility testing. But you must be aware of accessibility and accessibility testing, first. Let's unbox what cross-browser accessibility is and how you can test it.

Accessibility, in terms of web technology has varied and vast meaning. It is not just about making your website or web application friendly for the people with disabilities but it is a lot more than that.

It simply means how accessible your website or web application is to different users.  
It can be anything ranging from

  * People using screen readers to access your text.
  * Utilization of captions for video to understand the context by people having hearing disabilities.
  * People with motor impairments who use non-mouse methods like keyboards and shortcuts to use the web.

To

  * People on older versions of browsers
  * People using different devices, like mobile phones and tablets

Everything counts in accessibility.

With various people and choices, it becomes necessary to make your website accessible to everyone. Making sure that your website is accessible to every user is **Accessibility Testing.**

In this blog, we'll cover the cross-browser compatibility aspect of accessibility. Cross-browser compatibility ensures that your website is accessible to different people across different browsers.

## Common Cross Browser Issues for Accessibility

When we talk about accessibility in web technology, the direct thing that it is related with is website and web app accessibility. Since modern websites are built on HTML, CSS, and JS technologies the unsaid problems lie behind their tech.

Let's discuss them one by one.

### Issues Affecting Accessibility

The hero of front-end tech, HTML, has a lot more to offer than to just coding of a website. The various tags and structures used in HTML add a lot to the accessibility of a website.

Semantic structure is necessary to maintain while writing HTML code, to make sure that the code is accessible. As you might be aware, heading tags ` h1 ` , `h2` , `h3` , etc and paragraph tags in HTML `p` , when used by screen readers, helps them to understand and distinguish between different text.

**Example of Semantic HTML:**
    
    
    <p>I’ll write a basic introduction here </p>

**Example of Bad HTML:**
    
    
    <font size="5">My main heading</font>
    
    
    <font size="4">My first subheading</font>
    
    
    <font size="3">One more subheading</font>

As you can see from the structure, that semantic structure contains headings and paragraphs, which makes it easier for various screen readers and also for the search engine to get a clear context of your content.

This also adds to the SEO of your website. Using semantic HTML helps search engines to find and read your content easily. It is an added advantage.

### Using the Keyboard to Access Features

People who are very fond of using the keyboard to do every function are not going to like your website if you don't make it accessible using the basic keyboard features.

For example:

  * Tab functionality to switch between different buttons and text inputs
  * The enter button to click on a button or submit a form
  * Escape functionality to close a popup
  * The return key to get back to previous page
  * Other shortcuts that we love to use in our daily lives

This has a huge effect on the accessibility of your website for a section of users, so you need to make sure that your website is accessible through native keyboards in different browsers

### Alt Text in Accessibility

If someone has visual impairments, seeing or reading content is not for them. In that case, alt text or text alternatives are important to the user. By using alt text in images in your content, you make it easier for search engines to find the content easily. Once figured out, screen readers can describe out loud the content to the user and they can access your content.

You can use the `alt` attribute to add alt text to your images. For example, if you want to add an alt text "testalttext" to the image testimage.jpg located at www.yourwebsite.com/ assets, you can use the following code:
    
    
    <img src="”http://www.yourwebsite.com/assets/testimage.jpg”" alt="“testalttext”" />

You need to test if your alt text works across different browsers. Many times, some tags work fine on one browser but fail on others. Make sure they work on every browser.

### Hidden Content Affecting Accessibility

Many times, to make design effective and beautiful, we add elements to our stylesheets, like absolute positioning used for Tabbed content. You can access various content that is on top of each other and accessible through the tab button on your keyboard. But for screen readers, it becomes difficult to read that. Use of elements like `display:none` hides content from screen readers and makes it difficult for people with impairments to read.

### Color Schemes and Contrast

People with color blindness are not blind, but they see colors differently. While deciding the background colors for your website, you need to think of people who see colors differently, too. Keeping good contrast on your website can make a huge difference for the people with color blindness and make your website accessible to them, too.

### Closed Captioning: Aid to Accessibility

By using closed captioning in videos, you can make them accessible for people with hearing impairments. They can access your videos and other video content by going through the closed captions. This also helps your content to be more search-engine friendly along with being accessible to a different section of your audience.

## Ending Note

There are various small things that we usually ignore while developing and testing a website, but these things can affect your website by making it accessible to every type of person. Taking care of every small element, tag, and feature across all the browsers can add huge value to your website.

Happy testing!

Take the Chaos Out of Container Monitoring. [View the webcast on-demand!](https://dzone.com/go?i=291441&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcompany%2Fevents%2Fwebcasts%2Fapplication-performance-monitoring-and-management.html%3Fcommid%3D286663%26cid%3DNA-DSP-APM-AEJ-000195-00001663-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_webcast1-apm-taming-chaos-articlepostroll%26mrm%3D)
