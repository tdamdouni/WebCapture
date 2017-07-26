# Smarten up your Pi Zero Web Camera with Image Analysis and Amazon Web Services (Part 2)

_Captured: 2017-05-25 at 13:32 from [utbrudd.bouvet.no](https://utbrudd.bouvet.no/2017/01/10/smarten-up-your-pi-zero-web-camera-with-image-analysis-and-amazon-web-services-part-2/)_

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/Screen-Shot-2017-01-14-at-18.57.43-1024x568.png)

This blog post continues the story of how I reduced the amount of [false positives](https://en.wikipedia.org/wiki/False_positives_and_false_negatives) triggered by my [motion activated Raspberry Pi Zero security camera](https://utbrudd.bouvet.no/2017/01/05/building-a-motion-activated-security-camera-with-the-raspberry-pi-zero/), by utilising Amazon Web Services (aka AWS).

[Part One](https://utbrudd.bouvet.no/2017/01/10/smarten-up-your-pi-zero-web-camera-with-image-analysis-and-amazon-web-services-part-1/) of this blog post focused on me finding a strategy for dealing with false positives. In summary I decided to try adding [AWS Rekognition](https://aws.amazon.com/rekognition/) (a Cloud based image analysis service) to my security camera project. This would enable the solution to filter out false positives which in turn would reduce the amount of false email alerts I was receiving.

The [original version of my Pi Zero Security Camera](https://utbrudd.bouvet.no/2017/01/05/building-a-motion-activated-security-camera-with-the-raspberry-pi-zero/) handled everything locally, from detecting movement to firing off alert emails. Adding AWS Rekognition to the solution required me to think differently. Did I really want the Pi Zero to make synchronous calls to AWS Rekognition, wait for a reply and then decide whether or not to send an email?

A more tempting alternative was to move the whole image processing solution to the Cloud as follows:

  1. The Pi Zero would focus on running the Motion Software. Any detected movement would result in a snapshot from the video stream being uploaded to the Cloud component.
  2. The Cloud component would call AWS Rekognition and send an alert email if the snapshot was found to contain one or more people.

This solution had the benefit of decoupling the Pi Zero and Cloud components (making it easier to change either one with minimal effect on the other).

With all this in mind I decided to build the whole image processing solution in Amazon's Cloud, using the following Amazon Web Service components:

  * **[Lambda Functions**](https://aws.amazon.com/lambda/): These allowed me to define and run code snippets (or microservices) in a serverless environment. My code snippets where written in Node.js, but one can also use Java, Python or C#.
  * **[Step Functions**](https://aws.amazon.com/step-functions): I used these to orchestrate the aforementioned Lambda Functions into an image processing workflow.
  * **[s3](https://aws.amazon.com/s3): **The destination for all image files uploaded from the Pi Zero.
  * **[Simple Email Service (SES)**](https://aws.amazon.com/ses/): Used to send emails from the image processing solution.
  * **[IAM**](https://aws.amazon.com/iam/): Used to give all resources access to their required dependancies.
  * **[Rekognition**](https://aws.amazon.com/rekognition/): Used for image analysis and elimination of false positives.

Both Rekognition and Step Functions are both relatively new additions to the AWS family, having been formally launched at the close of 2016.

Note that I had never used any of these services before! Luckily for me it was easy to get started thanks to [good documentation](https://aws.amazon.com/documentation/) and the occasional visit to [stack overflow](http://stackoverflow.com/questions/tagged/amazon-web-services)

So how did all these components fit together?

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/Screen-Shot-2017-01-13-at-17.26.41-1024x491.png)

> _Overview of Smart Pi Zero Security Camera (click to view a bigger version)_

Lots of boxes, arrows and pretty pastel colours here - but what is actually happening? Let us begin at the Pi Zero:

  1. The Motion Software constantly monitors the camera's video feed.
  2. When Motion detects movement, it creates an image file (a snapshot of the event).
  3. The image file is uploaded from the Pi Zero to s3 via a Node.js script.
  4. Each file uploaded to the s3_ /upload_ directory s3 triggers a Lambda Function that in turn activates a Step Function (in other words a separate Step Function instance is created for each image file).
  5. The Step Function orchestrates Lambda Functions into a workflow that process the image file. These Lambda Functions use the AWS Rekognition (for image analysis) and AWS SES (for sending emails) API's.
  6. After processing the image file is finally moved to the_ /archive_ directory in s3.

Although it is not shown in the above diagram, AWS IAM is also involved here, by ensuring that all components have access to the resources they need to do their job. For example, any resources trying to interact with s3 will receive a 403 (forbidden) error code unless their IAM Role contains the correct access permissions.

The code for this solution can be found on [GitHub](https://github.com/markwest1972/smart-security-camera), where I've also included tips for replicating this project. Creating components in AWS is pretty straightforwards and well documented, so rather than writing a complete «How To» guide I will summarise my experiences with some of the AWS components I used.

Node.js Upload Script

[Here you'll find the code for the upload script](https://github.com/markwest1972/smart-security-camera/tree/master/s3-upload).

The easiest way to upload files to s3 is to use one of the [many AWS SDK's](https://aws.amazon.com/tools/). I chose to use the [Node.js SDK](http://docs.aws.amazon.com/AWSJavaScriptSDK/latest/top-level-namespace.html) which was quickly installed via the following steps:

  1. [Install a recent version of Node.js and npm](https://github.com/sdesalas/node-pi-zero).
  2. Install the AWS SDK for Node.js by running this command (or alternatively add _aws-sdk_ to you package.json file):

s3

s3 is an online storage service where objects are stored in «buckets» - basically logical storage units. Objects in buckets can be organised into directories.

I started by creating an s3 bucket with 2 root directories:

  * _/upload _: destination for all uploaded image files.
  * _/archive_ : storage of processed image files.

My next step was to make sure that an event would be triggered for each new upload. I did this by creating an [s3 Notification](http://docs.aws.amazon.com/AmazonS3/latest/dev/NotificationHowTo.html) that would trigger a Lambda Function for each **Object Created** event in the_ /upload_ directory.

Lambda Functions

[Here you'll find code for all the Lambda Functions used by the solution](https://github.com/markwest1972/smart-security-camera/tree/master/aws-lambda-functions).

A Lambda Function is basically a single unit of code with a standardised input and output. These functions run in Amazon's Cloud without any need for managing or provisioning servers. [Serverless FTW](https://martinfowler.com/articles/serverless.html)!

**The Lambda Function Handler**

I created six Node.js Lambda Functions for this project, each with their own distinct task. In order to work with the AWS Lambda Function infrastructure [you'll need to wrap your code with a handler](http://docs.aws.amazon.com/lambda/latest/dg/nodejs-prog-model-handler.html). This looks like this:

This handler provides three objects:

  * **event**: This contains input to the Lambda Function.
  * **context**: This provides runtime information, such as request id, log information and so on.
  * **callback**: This is used for [returning information from the Lambda Function](http://docs.aws.amazon.com/lambda/latest/dg/nodejs-prog-model-handler.html#nodejs-prog-model-handler-callback).

By using the event and callback parameters you can exchange information between Lambda Functions. This is especially important when orchestrating multiple Lambda Functions in a workflow via a Step Function.

**Defining Lambda Functions**

Lambda Functions can be defined in two ways:

  1. Via a browser based code editor (see [rekognition-image-assessment](https://github.com/markwest1972/smart-security-camera/tree/master/aws-lambda-functions/rekognition-image-assessment) for an example).
  2. Via uploading a Zip File (see [nodemailer-send-notification](https://github.com/markwest1972/smart-security-camera/tree/master/aws-lambda-functions/nodemailer-send-notification) for an example).

Zip Files are mainly used when you need to bundle up dependancies in your Lambda Function. Note that the AWS SDK is available to Lambda Functions by default, and usage of this does not require bundling. However if your Lambda Function uses a third party library then these dependancies will be need to be bundled up with the code in a Zip File.

**Logging**

Running Lambda Functions result in log files being created on [AWS CloudWatch](https://aws.amazon.com/cloudwatch/?sc_channel=PS&sc_campaign=acquisition_ND&sc_publisher=google&sc_medium=cloudwatch_b&sc_content=cloudwatch_e&sc_detail=aws%20cloudwatch&sc_category=cloudwatch&sc_segment=161191660305&sc_matchtype=e&sc_country=ND&s_kwcid=AL!4422!3!161191660305!e!!g!!aws%20cloudwatch&ef_id=VzdeqAAAAP0g1pEf:20170114172302:s). Any calls to:

will be recorded here.

**Configuration**

The configuration of Lambda Function also allows you to amongst other things specify the amount of memory each function uses. When testing my [nodemailer-send-notification](https://github.com/markwest1972/smart-security-camera/tree/master/aws-lambda-functions/nodemailer-send-notification) Lambda Function I received a large amount of timeout errors. This function is responsible for sending alert emails with the attached image file. I figured the size of the attachment was part of the problem and therefore doubled the memory available to this function - from 128 to 256. This resolved the timeout errors.

**Calling other AWS services via the AWS SDK**

The AWS SDK is natively available to all Lambda Functions, and provides a mechanism for calling services such as Rekognition, SES and s3. To see examples of this, check out the following Lambda functions on GitHub:

  * [rekognition-image-assessment](https://github.com/markwest1972/smart-security-camera/tree/master/aws-lambda-functions/rekognition-image-assessment) - calls Rekognitions detectLabels function.
  * [s3-archive-image](https://github.com/markwest1972/smart-security-camera/tree/master/aws-lambda-functions/s3-archive-image) - moves files in s3.
  * [nodemailer-error-handler](https://github.com/markwest1972/smart-security-camera/tree/master/aws-lambda-functions/nodemailer-error-handler) - sends emails via AWS SES and NodeMailer (a third party plugin).

**Summary**

Lambda Functions are one of the more established AWS services, and this shows. It was really simple to get up and running with these, but I would advise working on your code locally before uploading it to AWS, as it the round trip between coding and testing is somewhat quicker.

Step Functions

Step Functions are a new addition to the AWS portfolio, and give the possibility to orchestrate Lambda Functions (MicroServices) into State Machines or even workflows.

You create a Step Function by manually creating a JSON file in a in-browser editor. Blueprints are available to help you get started and you can generate a on the fly visualisation of your model at the press of the button. The Step Function uses a unique identifier or **arn** to identify the Lambda Functions it wishes to use.

My favourite feature of Step Functions is the Logging. Each instance of the Step Machine is logged and visualised as follows:

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/Screen-Shot-2017-01-14-at-18.57.43.png)

> _A visualisation of a completed Step Machine instance, showing output from the first step (Lambda Function) call. Each box represents a call to a Lambda Function. The white box is an error handler and was not called in this instantiation._

This feature makes it possible to drill through previous instances, in addition to following those that are currently executing. Inputs and output for each step are also available via this view. Perfect for debugging!

One aspect of Step Functions I disliked was that you cannot edit them once they are created. Instead you need to create a whole new Step Function from scratch. Adding a version number to the Step Function name is therefore a smart tactic.

IAM Roles

You are required to specify a Role for each Step and Lambda Function you create. This Role specifies when resources these functions are allowed to access.

There are multiple ways in which you can specify roles, but perhaps the easiest way is to define these using the AWS IAM Console. In this console you can also see an overview of all the roles you have created.

See the various [Lambda Functions in the project GitHub](https://github.com/markwest1972/smart-security-camera/tree/master/aws-lambda-functions) for examples of Roles I defined for this project.

So how much does all this Cloud functionality cost? Surprisingly little. As a newcomer to AWS I was able to sign up for the [AWS free tier](https://aws.amazon.com/free/) which gives me the following for free:

  * **Lambda Functions**: Up to 1 million requests per month, indefinitely.
  * **Step Functions**: Up to 4,000 instances per month, indefinitely.
  * **SES**: Up to 62,000 outbound message per month, indefinitely.

Frankly I doubt that my camera will ever exceed these thresholds. But if I do, the costs are minimal. For example 1,000 step function instances will cost me a grand total of $0.025!

The [AWS free tier](https://aws.amazon.com/free/) also gives me the following free of charge _for the first 12 months_:

  * **s3**: 5GB of storage, 20,000 get requests and 2,000 put requests per month.
  * **Rekognition**: 5,000 requests per month.

Again this is more than enough for my cameras requirements. Should my camera still be in operation in 12 months I can expect to incur the following costs:

  * **s3**: $0.023 per GB storage, $0.004 per 10,000 GET requests and $0.005 per 1,000 PUT requests.
  * **Rekognition**: $1.00 per month for up to 1,000 Image Analysis requests.

My camera doesn't create a lot of AWS traffic because it is pointing at a quiet back yard. 50 images a day is less than 20,000 a year so all this is pretty affordable from my perspective.

I also made a few further adjustments to the same [Motion configuration file that I originally defined when building the security camera](https://utbrudd.bouvet.no/2017/01/05/building-a-motion-activated-security-camera-with-the-raspberry-pi-zero/):

  * I changed the **on_picture_save** parameter to call the s3 upload script by setting the value to _/usr/local/bin/scripts/s3-upload/process-picture.sh smart-security-camera-upload %f._ See [s3-upload on GitHub](https://github.com/markwest1972/smart-security-camera/tree/master/s3-upload) for more information about this.
  * I changed the **quality** parameter to _100_. My reason for doing this was to provide Rekognition with the best possible quality of image files.
  * I changed **minimum_motion_frames** from _1_ to _2_. This means that two frames of movement need to be detected before a motion event is triggered.
  * I set **text_double** to _on_. This was a purely cosmetic change that doubled the size of the text displayed on the image.
  * I set** text_left** to _GardenCam_. Another cosmetic change that identifies my camera.

I will probably continue to tweak Motion as I gather more results from field testing the camera. [All changes to the Motion configuration file will be documented on GitHub](https://github.com/markwest1972/smart-security-camera/tree/master/motion-config).

A weekends field testing of the complete solution yielded favourable results. False positive images are now successfully filtered out by the AWS image processing solution, which means that I no longer receive false alarm emails for pictures such as this:

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/Screen-Shot-2017-01-15-at-12.26.55-1024x764.jpg)

> _False positive triggered by throwing a cushion out of a second floor window (rock and roll). This was filtered out by the AWS image processing, meaning that I didn't receive an alert email_

The solution also successfully dealt with images containing people. In the below example you can see that my lab assistant / daughter was correctly identified as a «Human» and a «Person». This was despite low light, motion blur and her head being partially covered.

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/Screen-Shot-2017-01-15-at-14.35.01-1024x554.png)

> _Example of a positive movement alert email with image and Rekognition labels enclosed_

Although I am happy with the solution, I can't resist making a few more tweaks. Here's my plan for the next few weeks:

  1. Tweaking the Motion configuration file to improve the image files being sent to Rekognition (and perhaps resolve the issue where Rekognition misses people in the images).
  2. Improve formatting of alert emails.
  3. Improve error handing and logging.
  4. Add _/falsepositive_, _/alert_ and_ /error_ subdirectories under _/archive _(and change the Step Function to use these).

If you'd like to follow these changes and others, they will be made available from the [project GitHub](https://github.com/markwest1972/smart-security-camera) as and when I implement them.

This project has been one of the most rewarding hobby projects I have worked with, mainly because it introduced me to how I could smarten up my Raspberry Pi projects by the power of the Cloud!

  * Using **Amazon Web Services** has been a positive experience. The documentation and examples for the Node.js SDK is of good quality and well structured, even for the newer services such as Step Functions. I've also picked up some skills that could be applied in my day job.
  * Editing **Lambda and Step Functions** via the in-browser code editor was perhaps the most cumbersome part of this project. At the time of writing it doesn't seem that IDE support for AWS is widespread, and it would be nice to see this situation improve.
  * **Lambda Functions** are great. Theres no need to worry about server configuration or provisioning as this is all taken care of. They lend themselves well to a microservice architecture and provide massive scalability out of the box.
  * **Rekognition** is an amazing service, and by using it to remove false positives I've only scratched the service of it's potential. By making a simple change to my code I could enable my camera to perform facial detection, recognition and sentiment analysis.

So that's it for now. If you have any comments or questions please share them in the comments below. You can also find me under @markawest on Twitter.

### _Thanks for reading!_

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/Screen-Shot-2017-01-15-at-15.42.12.png)

> _Exit stage left!_
