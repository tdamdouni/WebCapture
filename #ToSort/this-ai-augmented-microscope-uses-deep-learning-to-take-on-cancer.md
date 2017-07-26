# This AI-augmented microscope uses deep learning to take on cancer

_Captured: 2017-02-26 at 00:44 from [blogs.mathworks.com](http://blogs.mathworks.com/headlines/2016/07/12/how-deep-learning-enabled-microscopy-can-detect-cancer-and-improve-biofuels/?s_eid=PSM_gen)_

According to the American Cancer Society, [cancer kills more than 8 million people each year](http://www.cancer.org/research/infographicgallery/rising-global-cancer-epidemic). Early detection can boost survival rates. Researchers and clinicians are feverishly exploring avenues to provide early and accurate diagnoses, as well as more targeted treatments.

Blood screenings are used to detect many types of cancers, including liver, ovarian, colon and lung cancers. Current blood screening methods typically rely on affixing biochemical labels to cells or biomolecules. The labels adhere preferentially to cancerous cells, enabling instruments to detect and identify them. But these biochemicals can also damage the cells, leaving them unsuitable for further analyses.

The ideal approach would not require labels… but without a label, how can you get an accurate signal or any signal at all?

## Combining [microscopy](http://www.mathworks.com/solutions/biological-sciences/microscopy-biomedical-imaging.html) and deep learning to d**iagnose cancer**

To address this, researchers are developing new approaches using label-free techniques, where unaltered blood samples are analyzed based on their physical characteristics. Label-free cell analysis also faces limitations: The method can damage cells, due to the intense illumination required. Label-free cell analysis can also be highly inaccurate since it often relies on a single physical attribute. New research aims to improve accuracy while minimizing damage to cells.

In a recent issue of _[Nature Scientific Reports_](http://www.nature.com/articles/srep21471)_, _a multidisciplinary team of UCLA researchers combined a new form of microscopy called [photonic time-stretch imaging](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0125106) with deep learning. With this powerful new technique, they were able to capture 36 million video frames per second. (Compare that rate to human vision: We can theoretically process 1000 separate frames per second, but our brains blur images into motion at speeds high than 150 frames/second. Most television and films run at 24 frames/second.) They then used these images to detect cancerous cells.

![UCLA Dr. Claire Chen with microscope](http://blogs.mathworks.com/headlines/files/2016/07/UCLA-Dr.-Claire-Chen-with-microscope-2-1024x768.jpg)

> _UCLA Dr. Claire Chen with microscope_

## **The team at UCLA: A multidisciplinary approach**

The team's strategy was to devise a new and accurate label-free methodology by developing and integrating three key components into one system: quantitative phase imaging, photonic time stretch, and deep learning enabled by big imaging data analytics. All three components were developed using MATLAB.

The study was led by [Bahram Jalali](http://www.ee.ucla.edu/bahram-jalali/), UCLA professor and Northrop-Grumman Optoelectronics Chair in electrical engineering; [Claire Lifan Chen](https://www.linkedin.com/in/clairelifanchen), a UCLA doctoral student; and [Ata Mahjoubfar](http://atamahjoubfar.github.io/), a UCLA postdoctoral fellow.

![photonic time stretch diagram, UCLA](http://blogs.mathworks.com/headlines/files/2016/07/photonic-time-stretch-diagram-UCLA-1.png)

> _photonic time stretch diagram, UCLA_

## **

## Part 1: Quantitative phase imaging

**

The microscope uses rainbow pulses of laser light, where distinct colors of light target different locations, resulting in space-to-spectrum encoding. Each pulse lasts less than one billionth of a second. The ultrashort laser pulses freeze the motion of cells, giving blur-free images. The photons with different wavelengths (colors) carry different pieces of information about the cells.

As the photons travel through the cells, the information about the spatial distributions of the cells' protein concentrations and biomasses are encoded in the phase and amplitude of the laser pulses at various wavelengths. This information is later decoded in the big data analytics pipeline and used by the artificial intelligence algorithm to accurately identify cancerous cells without any need for biomarkers.

The microscope also uses low illumination and [post-amplification](https://www.osapublishing.org/josaa/abstract.cfm?uri=josaa-30-10-2124). This solves the common problem in label-free cell analysis, where the illumination used to capture the images destroys the cells.

"In our system, the average power was a few milliwatts in the field of view, which is very safe for the cells," stated Claire Lifan Chen. "But, after passing through the cells, we amplify the signal by about 30 times in the photonic time stretch."

Specially designed optics improve image clarity in this microscope. The researchers have used MATLAB to design the microscope according to the resolution requirements in their biomedical experiments. Image reconstruction and phase recovery are also designed in MATLAB for further downstream analysis.

## **

## Part 2: Amplified time-stretch system

**

[Photonic time stretch, invented by Professor Jalali](https://www.researchgate.net/profile/Bahram_Jalali2/publication/3379368_Time-stretched_analogue-to-digital_conversion/links/0c96052c876046ed2e000000.pdf), [transforms the optical signals](http://www.nature.com/articles/srep17148) and slows the images so that the microscope can capture them. The microscope can image 100,000 cells per second. The images are digitized at a rate of 36 million images per second, equivalent to 50 billion pixels per second.

The photons travel through a long, specialized fiber and arrive at the sensors during the time between laser pulses. [MATLAB](http://www.mathworks.com/products/matlab/) was used to determine the parameters for this dispersion compensating fiber.

"The system adds different delays to the pixels within a pulse and feeds them one-by-one, serially, into the photodetector," said Ata Mahjoubfar.

A software implementation of the physics behind phase stretch transform (PST) as an image feature detection tool from the UCLA Jalali Lab is available for [download](http://www.mathworks.com/matlabcentral/fileexchange/55330-jalalilabucla-image-feature-detection-using-phase-stretch-transform) from MathWorks File Exchange. The code uses [Image Processing Toolbox](http://www.mathworks.com/products/image/?s_tid=srchtitle).

The PST code is also available on [Github](https://github.com/JalaliLabUCLA/Image-feature-detection-using-Phase-Stretch-Transform): It has downloaded or viewed more about 27,000 times since May. At the time of this post, it has the third highest star rating of the current MATLAB repositories.

![UCLA Microscope in Lab](http://blogs.mathworks.com/headlines/files/2016/07/UCLA-Microscope-in-Lab-1-1024x766.jpg)

> _UCLA Microscope in Lab_

## **

## Part 3: Big data analytics using deep learning

**

Once the microscope captures the images, the team used domain expertise to extract 16 biophysical features of the cells, such as size and density. Recording these features is like documenting the fingerprints of each individual cell. This method yields a high-dimensional dataset which is used to train the machine learning application for identifying cancer cells.

With millions of images to analyze, the team turned to [machine learning](http://www.mathworks.com/solutions/machine-learning/) to solve the multivariate problems. Using MATLAB, the authors implemented and compared the accuracy of multiple machine learning approaches ranging from [Naive Bayes](http://www.mathworks.com/help/stats/naivebayes-class.html) and [Support Vector Machines](http://www.mathworks.com/help/stats/support-vector-machine-classification.html), to [Deep Neural Network (DNN)](http://www.mathworks.com/help/nnet/convolutional-neural-networks.html).

The approach that provided the best performance was a custom DNN implementation that maximized the area under ROC curve (AUC) during training. The AUC is calculated based upon the entire data set, providing inherently high accuracy and repeatability. The success of DNNs for this challenging problem is derived from their ability to learn complex nonlinear relationships between input and output.

In comparing the performance of various classification algorithms, the DNN AUC classifier provided an accuracy of 95.5 % compared to 88.7 % for a simple Naive Bayes classifier. For applications like cancer cell classification, where implications of positive or negative diagnosis are so high, this improvement in accuracy highly impacts the usability of a method.

The more images provided, the more accurate the training system can become. The team trained the machine learning model with millions of line images and used parallel processing to speed up the data analytics. Using high-performance computing ([HPC](http://www.mathworks.com/products/distriben/?s_tid=srchtitle)), the image processing and deep learning can be readily performed in real-time by an online learning configuration.

## **

## The language of innovation

**

Not content with simply developing a new microscopy technique, the team utilized the augmented microscope to detect cancer cells more accurately and in less time than current techniques. They also were able to determine which strains of algae provide the most lipids for subsequent refining into [biofuels](http://www.popsci.com/how-algae-can-fuel-planes-feed-livestock-and-fight-climate-change). Yes, one methodology that tackled both biofuels and cancer.

Innovation cannot be achieved without creativity, inspiration, and dedication. Having an interdisciplinary team also helps: This work was a result of collaborations between computer scientists, electrical engineers, bioengineers, chemists, and physicians.

> "As we were developing our artificial-intelligence microscope, we crossed the boundaries of scientific fields and modeled biological, optical, electrical, and data analytic systems interconnectedly. MATLAB is a great language for prototyping and provided cohesion to this process, " said Ata Mahjoubfar.

And, as these researchers demonstrate so eloquently in their publication, having a single language of innovation can facilitate collaboration and accelerate innovation amongst various disciplines in science and engineering.

You can find this and other useful community-developed tools for microscopy [here.](http://www.mathworks.com/solutions/biological-sciences/microscopy-biomedical-imaging.html)

For more information on this research, read[ this article by the UCLA researchers](https://www.mathworks.com/company/newsletters/articles/cancer-diagnostics-with-deep-learning-and-photonic-time-stretch.html).
