# OpenCV + Apache MiniFi for IoT

_Captured: 2018-01-13 at 19:10 from [dzone.com](https://dzone.com/articles/opencv-apache-minifi-for-iot?edition=352117&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-13)_

[Download Red Hat's blueprint for building an open IoT platform](https://dzone.com/go?i=250323&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2Fintelligent-systems-solution-internet-things)--open source from cloud to gateways to devices.

Let's learn how to ingest camera data from a NanoPi Duo with a helping hand from Apache MiniFi, Hadoop, and some Python. We'll then add image recognition through OpenCV Face Detection.

Let's start by examining our NanoPi Duo.

![](https://community.hortonworks.com/storage/attachments/45695-nanopi1.jpg)

![](https://community.hortonworks.com/storage/attachments/45696-nanopi2.jpg)

This is pretty close to a Raspberry Pi Zero. This inexpensive box is another useful IoT device for ingesting some data very inexpensively.

## **Machine Browsing**

The source code for the Python and shell script we'll be using [can be found here](https://github.com/tspannhw/nifi-nanopi-duo).

![](https://community.hortonworks.com/storage/attachments/45698-nanopisplash.png)

## **Hardware**

  * The FA-CAM202 is a 200M USB camera.

  * 512MB RAM

  * Ubuntu 16.04.3 LTS 4.11.2

  * Similar SBC to Raspberry Pi

  * ARM

## **Software Setup**

## **inferred.avro.schema**

## **hive.ddl**

## **Apache NiFi**

![](https://community.hortonworks.com/storage/attachments/45732-nanopiduosuccessfulingest.png)

![](https://community.hortonworks.com/storage/attachments/45733-nanopiduoschema.png)

![](https://community.hortonworks.com/storage/attachments/45734-nanopiduoprocessingflow.png)

The flow in Apache NiFi is pretty simple. We receive the flowfiles from the remote Apache MiniFi box.

1\. **RouteOnAttribute**: Send images to the file system, continue processing the JSON

2\. **AttributeCleanerProcessor**: Clean up the attributes not really needed for this dataset.

3\. **UpdateAttribute**: Set the schema name to reference the registry

4\. **SplitJSON**: Split JSON into one array per flowfile

5\. **ConvertRecord**: Convert JSON tree to AVRO with embedded schema

6\. **ConvertAvroToORC**: Build an Apache ORC file (we could add a step before for MergeContent)

7\. **PutHDFS**: Store in Hadoop File System forever

![](https://community.hortonworks.com/storage/attachments/45735-nanopiduoflowoverview.png)

## **Apache MiniFi**

![](https://community.hortonworks.com/storage/attachments/45730-nanoduominififlow.png)

> _We have a simple flow in Apache MiniFi._

  1. **ExecuteProcess**: run a shell script to grab a timestamp filenamed image from the USB webcam. Then call a Python script that does OpenCV Face Detection and adds some local variables to a JSON array with facial squares.

  2. **GetFile**: retrieve all the images from the box and send them to Apache NiFi.

## **Example Data**

## **Face**

![](https://community.hortonworks.com/storage/attachments/45729-nanopiduo2018-01-04-2023jpgfaces.jpg)

[Build an open IoT platform](https://dzone.com/go?i=250322&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2Fintelligent-systems-solution-internet-things) with Red Hat--keep it flexible with open source software.

Topics:

apache nifi ,apache minifi ,python ,opencv ,big data ,iot ,nanopi duo ,tutorial
