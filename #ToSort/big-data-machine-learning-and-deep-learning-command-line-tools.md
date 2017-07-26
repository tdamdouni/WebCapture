# Big Data, Machine Learning, and Deep Learning Command Line Tools

_Captured: 2017-02-14 at 21:15 from [dzone.com](https://dzone.com/articles/big-data-ml-dl-command-line-tools?edition=268944&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-14)_

Keep those hands on the keyboard! We can do a lot on OSX and Linux without touching a mouse or GUI. Awesome command line tools for *N*X derivatives have been around since day one, and have expanded to include Python, Go, NodeJS, and hybrid tools. Even if you are not only running your pipeline through the command line, you can call most of these tools from Apache NiFi for processing.

The book _[Data Science at the Command Line](http://datascienceatthecommandline.com/#tools) _and GitHub offer an amazing set of quality tools to do a lot of pre- and post-processing and allow for a lot of transformations. I highly recommend looking at all of these amazing tools.

[CSVKit](http://csvkit.readthedocs.io/en/749/) is amazing! [It does everything](https://github.com/wireservice/csvkit) you need with [comma-separated values](http://csvkit.readthedocs.org/). You can grab columns via `cvs cut`, filter by column with `cvsgrip`, extract data from Postgresql to CSV via `sql2csv`, grab a subset of columns with `cols` , and convert MS Excel to CSV with `in2cv`.

## **Quick Tool List**

  * [ImageMagick](http://www.imagemagick.org/script/command-line-processing.php) (edit, create, convert, flip, and alter images from the command-line).

  * [XML2JSON](https://github.com/Inist-CNRS/node-xml2json-command) via NodeJS.

  * [Gatling](http://gatling.io/#/resources/download) for Testing with Scala/JVM.

  * [MQTT CLI](https://www.npmjs.com/package/mqtt-cli) (NPM.JS).

You can also write some very short Python scripts to process data from the command line.

_Five line Python script for sentiment analysis._

You can even now [debug TensorFlow](https://www.tensorflow.org/versions/r1.0/how_tos/debugger/) via the command line (though this is really beta, so expect an occasional hiccup).
