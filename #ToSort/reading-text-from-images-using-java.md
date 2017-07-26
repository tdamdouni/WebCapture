# Reading Text from Images Using Java

_Captured: 2017-03-11 at 23:03 from [dzone.com](https://dzone.com/articles/reading-text-from-images-using-java-1?edition=281881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-11)_

This post will help read texts from your images. It makes use of the Tesseract library.

You can also use the module below to check if the Captcha on your site is strong enough and cannot be easily broken.

## References

## **Language Used**

## **Git Location**

  * <https://github.com/csanuragjain/extra/tree/master/ReadFromImages>

## **POM Dependency**

## **Prerequisites**

  1. Let's assume you are running this program from c:\myprogram. Now, you can follow either of two methods, based on your requirements.  
_  
Space saving method: Only download the language data you need. That only requires 30MB for an English dataset._

  2. Create a folder named tessdata inside c:\myprogram\

  3. Download eng.traineddata for breaking Captchas with English (trained data is available for other languages as well).

  4. Place the eng.traineddata inside the tessdata folder.

  5. Finally, your folder structure should look like: c:\myprogram\tessdata\eng.traineddata  
_  
Time-saving method: Download trained data packages larger than 1GB from several languages._

  6. You can also skip Step 2 to Step 5 and simply download the tessdata-master folder from <https://github.com/tesseract-ocr/tessdata>

  7. Unzip the content of tessdata-master.zip file in your main project folder (for example, here, it is c:\myprogram\\)

  8. Rename tessdata-master to tessdata

  9. Finally, your folder structure should look like c:\myprogram\tessdata\<Trained data from several languages>.

## **Program**

### ImageCracker Class, crackImage Method
    
    
            System.err.println(e.getMessage());  

#### **How It Works**

  1. First, crackImage takes the image that needs to be read.

  2. We point a file object to that image.

  3. We make a Tesseract object named instance.

  4. We call the predefined method doOCR of the Tesseract library, passing the file object from step 2.

  5. The doOCR method returns the text read from the image and returns the same.

  6. In case of failure, it prints the error message and returns an error string.

### Driver Class, Main Method

#### **How It Works**

  1. We call the crackImage method, passing the image to be read from.

  2. We print the text read from the method on the console.

### **Input Image (testImage.PNG)**

### **Output**

Create a Youtube metadata crawler using Java.

## **Full Program**

### _**ImageCracker Class**_

### **Driver Class**

Hope it helps!
