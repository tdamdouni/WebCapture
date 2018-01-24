# It’s Different at the Edge

_Captured: 2017-11-29 at 18:27 from [dzone.com](https://dzone.com/articles/its-different-at-the-edge?edition=339091&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202017-11-29)_

[Download Red Hat's blueprint for building an open IoT platform](https://dzone.com/go?i=250323&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2Fintelligent-systems-solution-internet-things)--open source from cloud to gateways to devices.

Sometimes it seems like technology development runs in a loop. We go from centralized to decentralized and back again -- smart computers to dumb terminals and back to smart computers again. We moved to the cloud for seemingly unbounded compute resources, and now we've begun a shift in the other direction toward edge-based computing.

There has been plenty of analysis around this topic, including by Peter Levine, General Partner at a16z, on [how cloud computing as we know it is coming to end and will be displaced by decentralized computing at the "edge"](http://a16z.com/2016/12/16/the-end-of-cloud-computing/) -- in IoT devices closer to the sources of network interaction with the world.

It is worth noting that simply retrofitting existing technology is not going to work for this process. The edge really is different than previous iterations in decentralized computing. We're not talking about desktops or laptops; we're talking about tiny devices (sometimes embedded) with a vastly different set of compute resources.

## **Edge Constraints**

While edge technology is becoming more powerful from a compute perspective, the resources available for application execution are still extremely limited both in terms of RAM and CPU. Leveraging a technology that has been retrofitted into such an environment is either not possible, due to compute requirements (as with machine learning), or is limiting (as when deploying edge-native microservices). If you attempt to deploy 10 apps, all requiring 1GB in an edge environment, it is very likely that you will not be successful.

Intermittent and expensive network connectivity are also common in edge scenarios. Simply put, if you've deployed an edge device deployed to the middle of nowhere and you rely on cloud resources to make all decisions, you're likely going to have a solution that doesn't work or works only part of the time. You need to provide some level of autonomy at the edge, which is where machine learning (ML) enters the picture.

## **Edge-Forward Thinking**

Providing any autonomy under such constraints is where things get tricky. The traditional JVM and Node.js are great for lots of things, but really are not the best options for devices with limited compute resources. If your IoT edge gateway is as powerful as my MacBook Pro, then leveraging any technology to accommodate your needs is probably acceptable. But as mentioned above, this isn't usually the case. You often see edge technologies built with the hope that compute resources will eventually become more abundantly available, but we still need to consider the limited resources available in the here and now. A framework that is designed specifically for edge compute is a requirement.

When developing for the lightweight requirements and resource restrictions of the edge, here are a few tips:

  * Native binaries are key.
  * Only the required dependencies should be built into the application binary.
  * A single application binary, statically linked at compile time, enables zero OS dependencies. Don't pre-install a run-time environment with hundreds of dependencies you have no intention of using.

## **Exploiting an Edge Engine **

I work on [Project Flogo](http://www.flogo.io/), a 100% open source ultra-lightweight process engine designed specifically for building edge microservices and functions. From within Flogo, you can embed machine learning (ML) within applications without any networking requirements -- all of the inferencing and required data aggregation is happening on the device. (Again, Flogo is open for use and contribution, and implementations can be leveraged with a BSD-style license, allowing developers to pursue edge microservice development with embedded machine learning without licensing implications.) By leveraging Golang, Flogo is ideally suited to run on the smallest IoT edge devices -- it's 20-50X lighter than could be achieved with Java or Node.js. Applications built with Flogo are compiled into purpose-built, native binaries for the target platform, providing improved performance versus interpreted technologies.

As well as the Golang produced binaries, a Flogo application can be constructed and compiled down to C to flash a microcontroller, and there's no need for a framework pre-installed on the target edge device. We've built a contribution model that enables developers in the open source community to add additional device-specific activities and triggers -- even platforms -- to shift autonomy to the device level. What does moving machine learning to edge devices mean? Well, in some cases, operational costs can be lowered by up to 85%(!) and you can implement use cases that were previously not possible due to the potential latency and network traffic required to stream and run models in the cloud.

## **TensorFlow Example**

We recently added support for Google's [TensorFlow](https://www.tensorflow.org/). With TensorFlow, you use Python to write your training code and export the saved model. Flogo supports the use the higher-level TensorFlow tf.estimator API to abstract away the low-level coding of the graph itself. The tf.estimator package exposes a model export method from Python, which will export the trained model protobuf (the file format used by TF) to a directory, that can be zipped up and passed directly to Flogo for native inferencing. Flogo takes the protobuf zip file (or path), decompresses and executes within the Golang runtime via a CGO wrapping for the dynamically linked libtensorflow.so. This means that you don't need Python on the edge device, nor do you need to have anything installed from TensorFlow other than the OS-specific dynamic library that is linked at runtime.

From within Flogo, you simply add the Flogo ML inferencing activity, where you specify the location of the compressed model file (or path itself). You'll also need to configure the activity with a few specifics -- the model location (a path on the edge device or a zip file location), the input tensor name, and finally a collection of features that are used to populate the graph for inferencing. An additional field titled 'framework' must be specified. Currently, 'Tensorflow' is the only available deep learning framework option, however, the activity has been developed with an extensible contribution model enabling additional backend deep learning frameworks to be plugged in so the activity should work just as it does today.

My colleague Matt Ellis put together a Flogo/Tensorflow demo with a Raspberry Pi and a DNN model built in TensorFlow to do classification of data from an accelerometer. The Flogo Flow aggregated the data over a period of 50ms and collected 11 aggregated results. Every 500ms, it passed this data to the TensorFlow model for scoring. The output of the TensorFlow model is various movement classifications (walking, jogging, running) along with the probabilities of each. The results were delivered in ~60ms with >99% accuracy.

![Image title](https://dzone.com/storage/temp/7280223-picture1.png)

> _Demo shown demonstrating on-device data classification with TensorFlow._

The demo along with the Python training code and sample training data sets will be made available on the Flogo GitHub page if you want to walk through the details.

Flogo was built from the ground up with edge-native design principles in mind, so I encourage you to experiment with it. The benefits and features discussed here can be leveraged in a much wider set of use cases and it's an exciting time to be exploring the power of computing at the edge, so long as you keep its unique constraints in mind.

[Build an open IoT platform](https://dzone.com/go?i=250322&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2Fintelligent-systems-solution-internet-things) with Red Hat--keep it flexible with open source software.

Opinions expressed by DZone contributors are their own.
