# Terrapattern is Like a Search Engine for Satellite Imagery

_Captured: 2016-05-27 at 12:24 from [www.wired.com](http://www.wired.com/2016/05/terrapattern-like-search-engine-satellite-imagery/)_

![Gallery Image](http://www.wired.com/wp-content/uploads/2016/05/Patterns6Final-1-932x524.jpg)

> _ Slide: 1 / of 6 . 

Caption: Terrapattern 

_

## Related Galleries

[ ![Students participating in “call outs.” One person names two random points in the city, and the other must choose from memory the most direct route to get there.](http://www.wired.com/wp-content/uploads/2016/05/Wilson_03-600x338-e1464288142913.jpg) ![Students participating in “call outs.” One person names two random points in the city, and the other must choose from memory the most direct route to get there.](http://www.wired.com/wp-content/uploads/2016/05/Wilson_03-200x200-e1464287644893.jpg) ](http://www.wired.com/2016/05/alexander-wilson-the-knowledge/) [ ![HopscotchHP.jpg](http://www.wired.com/wp-content/uploads/2016/05/HopscotchHP-600x450-e1464284642401.jpg) ![HopscotchHP.jpg](http://www.wired.com/wp-content/uploads/2016/05/HopscotchHP-600x338-e1464284636803.jpg) ![HopscotchHP.jpg](http://www.wired.com/wp-content/uploads/2016/05/HopscotchHP-200x200-e1464284615561.jpg)

### Hopscotch Teaches Kids to Code Without That Pesky Command Line

](http://www.wired.com/2016/05/hopscotch-teaches-kids-code-without-command-line/) [ ![OtterBox uniVERSE Case](http://www.wired.com/wp-content/uploads/2016/05/otterbox-ft-600x450.jpg) ![OtterBox uniVERSE Case](http://www.wired.com/wp-content/uploads/2016/05/otterbox-ft-600x338-e1464203591135.jpg) ![OtterBox uniVERSE Case](http://www.wired.com/wp-content/uploads/2016/05/otterbox-ft-200x200-e1464203551121.jpg)

### Who Needs a Modular Phone When You Can Have a Modular Case?

](http://www.wired.com/2016/05/needs-modular-phone-can-modular-case/) [ ![JuiceroHP.jpg](http://www.wired.com/wp-content/uploads/2016/05/JuiceroHP-600x450-e1464135535462.jpg) ![JuiceroHP.jpg](http://www.wired.com/wp-content/uploads/2016/05/JuiceroHP-600x338-e1464135516394.jpg) ![JuiceroHP.jpg](http://www.wired.com/wp-content/uploads/2016/05/JuiceroHP-200x200-e1464135484950.jpg)

### How on Earth Could a Juicer Cost $700? Because Yves Behar

](http://www.wired.com/2016/05/juicero-yves-bhar/) [ ![osmo-codingkit-inline1.jpg](http://www.wired.com/wp-content/uploads/2016/05/osmo-codingkit-inline1-600x450.jpg) ![osmo-codingkit-inline1.jpg](http://www.wired.com/wp-content/uploads/2016/05/osmo-codingkit-inline1-600x338-e1464019995395.jpg) ![osmo-codingkit-inline1.jpg](http://www.wired.com/wp-content/uploads/2016/05/osmo-codingkit-inline1-200x200-e1464020039694.jpg)

### Osmo Turns Blocks Into Code to Teach Kids Programming

](http://www.wired.com/2016/05/osmo-turns-blocks-code-teach-kids-programming/)

> _Inside the London School Where Cabbies Learn the Fabled Knowledge_

In 2008, through something of a happy accident, a team of zoologists from the University of Duisburg-Essen in Germany [discovered](http://www.pnas.org/content/105/36/13451.full) that grazing cows and deer tend to align their bodies with magnetic north. It was an odd thing to notice, particularly because the researchers had been perusing satellite imagery for something else entirely. But that's what happens when you look at something from 400 miles above the Earth's surface--change your perspective, and you'll change what you see.

When Golan Levin, a professor of new media art at Carnegie Mellon University, heard about the cow discovery, he found it "to be simultaneously wonderful and very inspiring and totally useless." He was also overcome, he says, by the desire to make similar discoveries. So he, along with artists and researchers Kyle McDonald, David Newbury, Irene Alvarado, Aman Tiwari, and Manzil Zaheer, created Terrapattern, a tool that lets people search for patterns otherwise hidden in troves of publicly available satellite imagery.

[Terrapattern](http://www.terrapattern.com/) works a lot like Google's reverse image search: click on a map tile, and the tool searches for satellite imagery with similar visual attributes. For example, if you happen to click on a purple tennis court in San Francisco, Terrapattern will surface dozens of examples of similar tennis courts in the area and show their locations on a map. Same goes for crosswalks, pools, baseball diamonds--pretty much anything with distinctive visual characteristics. "Our tool is extremely good at finding various things that are un-mappable or unmapped or unconventionally unworthy of mapping," Levin says.

Like many [recent computer vision projects](http://www.wired.com/2014/08/deep-learning-yann-lecun/), Terrapattern uses something called a [convolutional neural network](http://www.wired.com/2014/08/deep-learning-yann-lecun/) to make sense of what it's looking at. The system analyzes images in layers: Lower layers identify basic visual characteristics like edges and curves; while higher layers make sense of the shapes identified by layers below them. But unlike other convolutional neural networks, which might eventually tell you the thing it's looking at is a school bus, or a picture of a cat, Terrapattern's network doesn't assign a final classification to any of the images it analyzes. Instead, using half a million satellite images from OpenStreetMap, Levin and his team trained the network to recognize the descriptions of features in an image--roundness, smoothness, color, and so on. "When we want to discover places that look similar to your query, we just have to find places whose descriptions are similar to those of the tile you selected," Levin explains on the tool's website. This allows Terrapattern to be more flexible in its search.

Using aerial observation to uncover unseen patterns isn't a new idea. Researchers have been using the technique for decades to track animal migration, monitor deforestation, and [unearth stunning archaeological discoveries.](http://www.wired.com/2016/02/sarah-parcak/) Recently, companies like Orbital Insights have even combined satellite imagery and computer vision to [collect (and sell) market-impacting intelligence](http://www.wired.com/2015/03/orbital-insight/). But Levin's vision is more egalitarian. He wants to create an Orbital Insights for the average person.

Of course, it remains to be seen just how the average person will use Terrapattern. Levin used it to discover graveyards of rotting boats along the coasts of New York City. He imagines journalists could use it to aid their investigations, and humanitarians to better coordinate relief efforts--though he concedes "there is a visual pleasure in using the project which I think goes beyond utility." The way he sees it, it's an artist's job to push the boundaries of new technologies, to investigate how they might impact society sometime in the future. It's not so much about providing obvious applications. "I give myself permission to explore things that may not have obvious use," he says.
