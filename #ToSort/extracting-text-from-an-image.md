# Extracting Text From an Image

_Captured: 2017-04-23 at 10:14 from [dzone.com](https://dzone.com/articles/extracting-text-from-image-converting-image-text?edition=292908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-22)_

Years ago, extracting text from images seemed to be one of the greatest challenges to all developers. Now, with the arrival of great tools, reading and extracting text from images is easy.

Today's I'll be explaining how to extract text from images using the Java Tesseract API from `net.sourceforge.tess4j`.

Extracting text from an image means that you are considering the flowchart imagery that's processed to extract the text components and then extracting the geometrical shapes components. The text components are extracted with geometrical components, as well. The internal relationship between the components is set up by tracing the flow lines that connect different components. The extracted components are output to metadata (in XML format), which is machine-readable. This metadata can be archived, stored in a knowledge base, or shared with others.

Below is the code for extracting text from images using the Java Tesseract API from `net.sourceforge.tess4j`.

## 1\. Adding the API

Add the `net.sourceforge.tess4j.*;` API to your `pom.xml`:

This is the image that we're extracting the text from:

![Image title](https://dzone.com/storage/temp/4963240-img.png)

## 2\. Download the CAPTCHA Language Extractor

Download the CAPTCHA language extractor and put it in the [tessdata folder](https://github.com/tesseract-ocr/tessdata).

For example, if you download `eng.trainedata` from the above URL, put the file at the project root folder `tessdata/eng-trainedata` .

##  3\. Read the Code

Here's the Java code that will read the text from an image in any format:

![Image title](https://dzone.com/storage/temp/4963241-2017-04-04-at-13-13-03.png)

> _For more information, check out the source code and the demo._
