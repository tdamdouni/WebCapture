# Deploying Your Serverless Functions to Google Cloud Platform

_Captured: 2017-04-14 at 20:42 from [dzone.com](https://dzone.com/articles/deploying-serverless-functions-to-google-cloud-platform?edition=290908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-14)_

In this tutorial, we are going to cover how to host a minified `HTTP GET`-based serverless application on Google Cloud Platform. Such a typical app is an excellent serverless side to an Ionic mobile app. When we say serverless platforms, it doesn't mean it's running on no server, so while the term serverless is good, it's a bit misleading. The following is taken from Google [Firebase serverless platform](https://www.npmjs.com/package/firebase-functions):

_"Cloud Functions is a hosted, private, and scalable Node.js environment where you can run JavaScript code. The Firebase SDK for Cloud Functions integrates the Firebase platform by letting you write code that responds to events and invokes functionality exposed by other Firebase features."_

Martin Fowler, in his great [serverless blog](https://martinfowler.com/articles/serverless.html), also mentions that serverless is a slightly misleading term:

_"The term 'Serverless' is confusing since with such applications there are both server hardware and server processes running somewhere, but the difference to normal approaches is that the organization building and supporting a 'Serverless' application is not looking after the hardware or the processes - they are outsourcing this to a vendor."_

So with that understanding in hand, we are going to write a small server implementation, ehh, that is a `serverless` implementation hosted on Google Cloud Platform.

Our plan:

  * Step 1: Make sure you have an up-to-date gcloud.

  * Step 2: Enable gcloud beta components.

  * Step 3: Code the serverless function.

  * Step 4: Prepare GCP to host your function.

  * Step 5: Upload your function to GCP.

  * Step 6: Test your function with an HTTP GET request!

## Step 1: Make Sure You Have an Up-to-Date gcloud

gcloud is a great command line utility for manipulating -- you guessed it -- Google Cloud Platform.

I already have gcloud installed, so that means I don't need to install it -- but I would need to update it.

If you don't already have gcloud installed, then download [Google Cloud Platform](https://cloud.google.com/sdk/downloads) and install it. If you already have it installed, then make sure you update it with:

`$ gcloud components update`

The result should be similar to:

**Note**: You need to start a new shell, as mentioned, for the changes to take effect!

## Step 2: Enable gcloud Beta Components

This step is extremely short -- just enable the beta components for gcloud.

`gcloud components install beta`

And the result would be similar to this:

## Step 3: Code the Serverless Function!

We are going to have a simple function that will return 'hello world'.

`vi index.js`
    
    
      if (req.body.message === undefined) {

## Step 4: Prepare GCP to Host Your Function

Now we are going to create a project and a bucket inside GCP in order to host our function there:

  1. Click "create project".

  2. Enter the name "serverless-example" and hit ENTER.

  3. Enable billing if not enabled (you will see a message in GCP). (Don't worry).

  4. Now for the important command in that section, relate your function folder to your Google Cloud Storage project and bucket `gsutil mb -p [PROJECT_ID] gs://[BUCKET_NAME]`

In our case:

In this step, we are going to enable functions on GCP. That's easy.

  1. On Google Cloud Console's left menu...

  2. Click "cloud functions"

  3. Click "Enable"

Set the current project to "serverless-example".

## Step 5: Upload (Deploy) the Function!

## Step 6: Run Your Function!

Run a similar URL to: <https://us-central1-serverless-example.cloudfunctions.net/helloWorld>, and it should return `200 OK`. If you check out the logs on your GCP console, you should see:

## Summary

We have deployed a Google Cloud function with a few easy steps. We have enabled billing, created a bucket, created a short function that responds to HTTP GET requests, deployed it, and then simply ran it. We have also briefly mentioned the fact that serverless functions are also kind of servers, only not managed by you.
