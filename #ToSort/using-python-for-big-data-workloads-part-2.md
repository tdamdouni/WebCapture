# Using Python for Big Data Workloads (Part 2)

_Captured: 2017-06-08 at 21:22 from [dzone.com](https://dzone.com/articles/using-python-for-big-data-workloads-part-2?edition=304123&utm_source=weekly%20digest&utm_medium=email&utm_campaign=wd%202017-06-07)_

Why should you use Python for Big Data workloads? [We have discussed a few reasons](https://dzone.com/articles/using-python-for-big-data-workloads-part-1), but here, we'll talk about more. Some surveys on the internet are showing that Python is gaining near 50% penetration in the Machine Learning language of choice.

  1. Deep Learning: TensorFlow, Keras, and PyTorch.

  2. OpenCV Python bindings.

  3. NLTK.

  4. PySpark.

  5. Apache Arrow, Parquet, and other project support.

  6. Apache Beam 2.0 support for Python.

  7. Speech recognition.

  8. API support.

  9. Sci-Kit Learn and other cool Machine Learning libraries.

  10. Utilities abound -- a PiP away.

Here's a cool [GitHub](https://github.com/oarriaga/face_classification?imm_mid=0f2114&cmp=em-data-na-na-newsltr_ai_20170529) example of using Keras with OpenCV and Python for face detection.

Step one is to [install](http://www.pyimagesearch.com/2016/11/28/macos-install-opencv-3-and-python-2-7/) OpenCV with Python.

There's some big news from Google about a new release of [Apache Beam 2.0, and Python](https://beam.apache.org/get-started/quickstart-py/) is now supported. You can now do streaming with Flink, Spark, and more using Python:

`pip install apache-beam`

After a simple PiP install, you can run Beam jobs:

`python -m apache_beam.examples.wordcount --input MANIFEST.in --output counts`

Check out some details on [speech recognition with Python](https://pypi.python.org/pypi/SpeechRecognition/), Python support for upcoming [Apache Arrow and Parquet](https://arrow.apache.org/blog/2017/05/23/0.4.0-release/), and some [cool Spark SQL code and UDF with Python](https://databricks.com/blog/2017/05/24/working-with-nested-data-using-higher-order-functions-in-sql-on-databricks.html).

[OpenCV](http://www.pyimagesearch.com/2017/05/29/montages-with-opencv/) has a great Python library and tons of fun examples that work with robots, cars, and drones.

[Cool Python image utilities](https://github.com/jrosebr1/imutils) are very abundant for all types of graphic and image manipulation

APIs are everywhere for Python! Here's an example on [Spotify](https://github.com/plamere/spotipy). There's also libraries for Facebook, Twitter, Instagram, Google services, Amazon services, Microsoft services, and tons of other feeds and services.

TensorFlow, NLTK, and Stanford CoreNLP have a Python wrapper, and TextBlob has so many cool libraries, utilities, and helpers. They're all easy to install, and most are well-documented.

Python also has [SciKit-Learn](http://scikit-learn.org/stable/), which is great and has a ton of great Machine Learning goodies.

Python runs everywhere -- Windows, OSX, Linux, and lots of devices. Here's an example on an ASUS [Tinkerboard](https://community.hortonworks.com/articles/103863/using-an-asus-tinkerboard-with-tensorflow-and-pyth.html).

There's a lot of Python libraries that run everywhere. Here are a few I recommend installing on every platform:

  * Numpy.

  * SciPy.

  * NLTK.

  * Wheel.

  * Pandas.

  * MatPlotLib.

  * PyTorch.

  * TensorFlow.

  * TextBlob.

  * spACy.
