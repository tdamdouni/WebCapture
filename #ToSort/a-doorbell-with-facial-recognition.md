# A Doorbell With Facial Recognition

_Captured: 2017-02-08 at 15:59 from [dzone.com](https://dzone.com/articles/doorbell-with-facial-recognition?edition=154266&utm_source=Weekly%20Digest&utm_source=Weekly%20Digest&utm_medium=email&utm_medium=email&utm_campaign=wd%202017-02-08&utm_campaign=wd%202017-02-08)_

Biometric screening using fingerprint or retina scans are not new. Since the advancements in high-resolution cameras and development of 3D facial recognition algorithms in the past few years, facial recognition as a means of biometrics has become pretty popular. My first encounter with this technology was in 2012-13 timeframe when Google first released its [Face Unlock](https://developer.android.com/about/versions/android-4.0-highlights.html), a feature in one of their Android Operating Systems that could unlock the phone by recognizing the owner's face.

Thus, facial recognition is not new. What is new is the access to some of the most sophisticated facial recognition algorithms through open source libraries and AWS AI services (a.k.a. Rekognition) to developers. We are going to talk about some of these libraries in this blog.

## The Doorbell Project

In my previous rudimentary attempts at doorbell(s), I had used Arduino with motion and range sensors, where the motion would trigger my range sensor and measure the range every few milliseconds to determine if the object (person) at my door was approaching towards my door or was just passing by - thus concluding whether someone is really at the door.

How about if I knew not only when someone was at the door, but also tell me who s/he was and his/her name if I knew the person already. I would also love a picture of my visitors to be sent to my phone so I could be notified even if I was not at home. Finally, in the ideal state, the visitor has to simply walk at the door … no buttons to press!

## Components

To conceptualize such a doorbell, I would need a (1) camera connected to a (2) computer that would constantly look for and (3) identify objects, or visitors in this case. Upon detection of a body-like feature (or a face), the computer would capture the image, (4) compare it with known faces and if found amongst the known faces, it would (6) notify me (on my phone) about who was at the door. Obviously, if it was a new face, I would like my computer to (4) learn the face and (5) remember it for next time. For kicks, I also thought it would be a cool idea for my computer to (7) greet my visitor if it was a known face.

This was going to be a lot of moving parts! They got mapped out as follows:

  1. A USB webcam

  2. Raspberry Pi 2 Model B as my portable computer with Python 3 scripting

  3. OpenCV. OpenCV (Open Source Computer Vision Library) is an open source computer vision and machine learning software library. [[opencv.org](http://opencv.org/about.html)]

  4. AWS Rekognition. Amazon Rekognition is an Amazon AI service that makes it easy to detect, index and search faces in images. [[AWS Rekognition](https://aws.amazon.com/rekognition)]

  5. AWS DynamoDB. Amazon DynamoDB is a fast and flexible NoSQL database service. [[AWS DynamoDB](https://aws.amazon.com/dynamodb/)]

  6. AWS Simple Notification Service. Amazon Simple Notification Service (Amazon SNS) is a fast, flexible, fully managed push notification service that lets you send messages to mobile device users, email recipients or even text messages. [[AWS SNS](https://aws.amazon.com/sns/)]

  7. AWS Polly. Amazon Polly turns text into lifelike speech. It uses Amazon AI service that synthesizes speech that sounds like a human voice. [[AWS Polly](https://aws.amazon.com/polly)]

  8. AWS Lambda. AWS Lambda runs code without requiring to provision or manage servers (i.e. no EC2's). In this case, Lambda was used for overall orchestration of all AWS services listed above.

## The Blueprint

As the above components are mapped out to the high-level vision, the execution was as described below.

_Please Note_: _The purpose of this blog is primarily to discuss the concept and idea, hence as much possible, I am going to stay away from `the code` and/or installation instructions. At the same time I will try my best to provide all my references so you can refer to them, too._

![Image title](https://dzone.com/storage/temp/4250794-screen-shot-2017-02-06-at-45646-pm.png)

Let's walk through some of the key components/modules of this project.

## 1: Face Tracking

The Python script on the Raspberry Pi utilizes the OpenCV libraries and the _Haar_ feature-based _cascade_ classifiers to constantly track faces. Read more about the [Haar cascade classifiers](http://docs.opencv.org/trunk/d7/d8b/tutorial_py_face_detection.html) on opencv.org.
    
    
        ret, img = cam.read() # we got image
    
    
          print("Psst! "+str(len(faces))+" peep(s) at the door!")
    
    
          for (x,y,w,h) in faces:
    
    
            cv2.rectangle(img,(x,y),(x+w,y+h),(255,0,0), 2) # red box around the face

![Image title](https://dzone.com/storage/temp/4250795-screen-shot-2017-02-06-at-45757-pm.png)

## 2: Face Recognition

After detecting the face(s), the Python script utilizes [AWS CLI](https://aws.amazon.com/cli/) to upload the images in S3. A Lambda function is then invoked that utilizes AWS Rekognition service to search from an indexed faces collection. If a match is not found, we then index the image as a new face.

AWS facial identification algorithm stores faces in their collection as feature vectors. This makes it possible to search any image from the indexed collection as well as to save any face as a feature vector. An example of image search, as well as results of indexing an image, is shown below.
    
    
    exports.handler = (event, context, callback) => {
    
    
      rekognition.indexFaces(paramsIdx, function (err, data) {

I have intentionally missed a step in the code snippet above that involves reading and writing into the database. The database is a simple table that stores a matrix of FaceId and a name, so I can return the name of the visitor for any matched FaceId obtained from the `rekognition.searchFacesByImage` method above.

An example of the database table is shown below:

FaceId Name

ff43d742-0c13-5d16-a3e8-03d3f58e980b
Mangesh

ff499e32-0c13-3d26-a6e5-0553e5fd9e0e
John

ff493332-0c13-34d6-a6f5-0f53ehf494ee

Someone

  


  


## 3: Notification

Within the same Lambda function above, when a matched face is found and the name of the visitor is retrieved from the database table, I utilized SNS to send SMS notification. Please note that there is an assumption here that an SNS topic has been setup and the required phone numbers are subscribed to that topic.
    
    
      Message: db.visitors.join(", ") + ' ' + (db,visitors.length > 1 ? 'are' : 'is') + ' at the door. ' + fullimage,
    
    
      callback(err, db.visitors.join(",")); // exit out of Lambda

![Image title](https://dzone.com/storage/temp/4250815-screen-shot-2017-02-06-at-45934-pm.png)

## 4: Greeting Visitors by Name

Essentially, we want to greet the user with their name. This is by far the simplest of all steps, as we need our greeting text to be converted to audio. Just to set expectations, there are multiple services that could have been used for this text-to-speech conversion, but I decided to stick with AWS, just because it is easier to call AWS services from Lambda (same ecosystem) and because it is a new offering that claims to be more realistic (and it does indeed feel that way!).

In this case, we again use the AWS CLI from the Raspberry Pi Python script. The AWS Polly service, in response, returns an MP3 file, which can be then played using any available audio player on the Raspberry Pi itself (make sure the speaker is connected via HDMI or 3.5mm port).

## Conclusion

Artificial intelligence and machine learning don't feel out of reach now, as open source libraries and services like those of Amazon Web Services are more accessible to developers. One can simply imagine the breadth and depth of applications that can be developed using these ready-to-use machine learning algorithms (services). The doorbell is just an example, but I cannot stop fathoming applications of AI in a variety of domains, such as social networking, security, traffic, medicine, education, etc.

There is still uncharted territory in this space outside of facial recognition, such as assessing facial emotions, recognizing moving objects and vehicles, color recognition, etc. that I will continue to pursue and keep sharing updates. If you have any experience to share in this space, I'm sure we're all ears!
