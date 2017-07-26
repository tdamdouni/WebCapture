# Alfresco and CloudFront: The Answer to Enhanced Content Delivery Response Time

_Captured: 2017-05-21 at 20:17 from [dzone.com](https://dzone.com/articles/alfresco-cloudfront-answer-to-enhanced-content-del?oid=twitter&utm_content=buffer73f66&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Alfresco is tagged as one of the best ECM systems; it has raised the standard and bar of document management. Alfresco is a web-based application and the majority of the enterprises using it host the software on a global based connected server that can be easily accessed by people all around the world. But this global proximity also leads to certain obvious problems and performance issues even for the enterprises who do not cater to global use cases. So we can leverage Amazon products like Amazon CloudFront to improve the content management and content delivery and reduce response times and thereby save a lot of dollars.

## Why Is Such an Association Required?

The globe is a gargantuan field with endless scopes and alternatives. Every website that one visits and every resource that one calls for via the internet traverses through a huge interlinked web. While some may require just one server, sometimes it may take up to 2 or 3 servers, so in the majority of cases, it is a very complex process involving a number of servers and multiple requests.

If you run a traceroute command for www.alfresco.com based on where you are sitting, you would get a minimum of 10 hops before reaching the final one. If you observe the ping times, they sum up as the number of hops increases and this ultimately decreases the response time.  
The case is similar with applications like Alfresco, where the situation toughens when the Alfresco libraries become thousands strong. Enter CloudFront! Amazon CloudFront is a content delivery network that aids in tremendously enhancing delivery times. It catches your desired resource at its edge location servers and then helps in serving a cached copy or in another case it directly fetches the resource from the origin server. However, this speed is multiplied when the origin server happens to be Amazon S3 bucket!

So let's consider that we are saving our resources on Amazon S3 and Alfrescobeing the main resource management repository, let's see how to connect them all.

## Create and Configure Web Distribution

The first step to initiate the process is to create and configure CloudFrontand make it ready for connecting with Alfresco and Amazon S3.

  * **Step 1: **Go to https://console.aws.amazon.com/cloudfront/home.

  * **Step 2:** Click Create Distribution.

  * **Step 3:** Click on Get Started for web.

  * **Step 4: **At the Origin Settings Section, you have to select the Origin Domain Name, which would be your S3 bucket's domain.

  * **Step 5:** Select Yes for Restrict Bucket Access this will make sure for users to access Amazon S3 bucket only through CloudFront URLs only.

  * **Step 6: **For the Origin Access Identity you have to select Create a New Identity.

  * **Step 7: **Comment will be auto-populated.

  * **Step 8: **Next you have to select Yes, Update Bucket Policy for Grant Read Permissions on Bucket.

  * **Step 9:** At the Default Cache Behavior Settings Section, check Yes for Restrict Viewer Access and check Self for Trusted Signers.

  * **Step 10: **Leave the rest of the settings to default.

  * **Step 11:** Click on Create Distribution.

  * **Step 12:** After Web Distribution creation please note the Domain Name which will be available at General information section and is going to be used later.

## Creating CloudFront Key Pairs for Your Trusted Signers

The next step involves creating CloudFront Key pairs that we are going to use for security and access purposes.

  * **Step 1:** Sign in to theAWS Management Console.

  * **Step 2:** Go to the account-name menu, and click on Security Credentials.

  * **Step 3: **Expand the CloudFront Key Pairs.

  * **Step 4: **Reconfirm that you have only one active key pair.

  * **Step 5:** Click on Create New Key Pair.

  * **Step 6: **Go to the Create Key Pair dialog box, and then select the Download Private Key File.

  * **Step 7:** Reach out to the Opening dialog box, and then accept the default value of Save File. Then click OK to download and save the private key for your CloudFront key pair.

  * **Step 8: **Next you have to record the key pair ID for your key pair.

  * **Step 9:** Then you have to successfully convert the private key to DER format. You can use OpenSSL for the same. You can do it by running the simple command:

  * **Step 10:** Next put this converted private key at the server and note its path.

## Appending CloudFront With Alfresco

Now the last step remains where we need to append Cloudfront with Alfresco. The basic connection involves creating custom strips that align with Alfresco and also at times simple API modifications. However, it all depends on the situation that is how you want to use CloudFront i.e what you want to cache and which resources are critical to you.

Here we take an example to reduce the amount of time needed to display the thumbnails. It is done by using the CloudFront as thumbnail URLs. There is a huge repository of images and finding a right image means viewing the image thumbnails which is done via website address and gave high latency.

You can override the Alfresco APIhandling thumbnail `/api/node/{store_protocol}/{store_id}/{node_id}/metadata` by incorporating the CloudFront URLs as defaults for thumbs.

You can build the CloudFront URL by the following command:

Next, you have to append the CloudFront URL in the response:

In the above script:

  * `distributionDomain` is the domain name that we had successfully captured in step 12 of Creating Web Distribution.

  * `privateKeyFilePath` is the file path of the key pair file that we had saved in step 10 of Creating CloudFront key pairs.

  * `keyPairId` is the key pair ID that we had generated at step 8 of Creating CloudFront key pairs.

The response of above APIwill be generated and received in share by following `web-preview` web script.When the user navigates to the detail page of the content you need to modify file `web-preview.get.js` to set `cloudfrontURL` in the `webpreview` widget:

Next, you have to take care and alter the "web-preview.js" file and add the `cloudfrontURL` in the options list and subsequently update the function 'getContentUrl.' This is one such use case whose example I have cited however there are endless such possibilities where this association can be brought into use successfully reducing the delivery time and response time and hence freeing of the unnecessary complexities.

On an ending note, you can enhance the application's performance primarily by connecting CloudFront with your Alfresco entity or my shifting your repository to S3 and using the Amazon EC2 as Alfresco's Hosting server. In the case of improving performance more and magnifying speed, you might also consider in investing in a more powerful instance in Amazon and optimize the processes related to Alfresco.
