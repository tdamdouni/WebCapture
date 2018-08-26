# Anomaly Detection in Mobile Sensor Data Using ML

_Captured: 2018-02-27 at 16:00 from [dzone.com](https://dzone.com/articles/anomaly-detection-in-mobile-sensor-data-using-ml?edition=365193&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-02-27)_

This post is an excerpt from our solution tutorial - **[Gather, visualize, and analyze IoT data](https://console.bluemix.net/docs/tutorials/gather-visualize-analyze-iot-data.html#data_experience)**. The tutorial walks you through setting up an IoT device, gathering mobile sensor data in the [Watson](https://vmacwrites.wordpress.com/category/cloud/cognitive/) IoT Platform, exploring data and creating visualizations and then using advanced machine learning services to analyze data and detect anomalies in the historical data.

## So, What Is Anomaly Detection?

> Anomaly detection is a technique used to identify unusual patterns that do not conform to expected behavior, called outliers. It has many applications in business, from intrusion detection (identifying strange patterns in network traffic that could signal a hack) to system health monitoring (spotting a malignant tumor in an MRI scan), and from fraud detection in credit card transactions to fault detection in operating environments.

In our day-to-day life, knowingly or unknowingly, We carry an IoT device. It is our mobile phone with inbuilt sensors which provides data from accelerometer and gyroscope. How about saving this sensor data somewhere and detect anomalies in that data?

That sounds like a cool idea. How can we achieve this? Do I need to code an app and ask users to download it from the store? Not required. A simple Node.js application running on a mobile browser will provide us with the sensor data.

![recent_events_with_phone](https://vmacwrites.files.wordpress.com/2018/02/recent_events_with_phone.png?w=1480)

This tutorial uses the following IBM [Cloud](https://vmacwrites.wordpress.com/category/cloud/) products:

Here's the flow or architecture diagram,

![Architecture-2](https://vmacwrites.files.wordpress.com/2018/02/architecture-2.png)

So, you will create a Node.js application,**[ run that on a browser](https://console.bluemix.net/docs/tutorials/gather-visualize-analyze-iot-data.html#confignodered)**, store the accelerometer, and gyroscope **[data to Cloudant NoSQL DB](https://console.bluemix.net/docs/tutorials/gather-visualize-analyze-iot-data.html#store-historical-data-in-cloudant-db)**. So, how do I detect anomalies?

Here's where IBM Data Science Experience comes handy. You will use the Jupyter Notebook that is available in the IBM Data Science Experience service to load your historical data and detect anomalies using z-score. You will start by creating a new project and then import the Jupyter notebook(.ipynb) through a URL.

> Anomaly detection will be performed using z-score. Z-score is a standard score that indicates how many standard deviations an element is from the mean. A z-score can be calculated from the following formula: `z = (X - µ) / σ` where z is the z-score, X is the value of the element, µ is the population mean, and σ is the standard deviation.

## Create a New Project

  1. **Create** the service and launch it's dashboard by clicking **Get Started**
  2. Create a **New Project** and enter `Detect Anomaly` as the **Name**.
  3. Create and select **Object Storage** and **Spark** services. **Refresh**![define_storage](https://vmacwrites.files.wordpress.com/2018/02/define_storage.png)

  4. Create.

## Connection to CloudantDB for data

  1. Click on **Assets** > **\+ Add to Project** > **Connection**
  2. Select the **iot-db** Cloudant DB where the device data is stored.
  3. Check the **Credentials** then click **Create**

## Create a Jupyter(ipynb) Notebook

  1. Click **New notebook** > **From URL**
  2. Enter `Anomaly-detection-sample` for the **Name**.
  3. **Create Notebook**. Check that the notebook is created with metadata and code.![jupyter_notebook_dsx](https://vmacwrites.files.wordpress.com/2018/02/jupyter_notebook_dsx.png?w=1480)

The recommended version for this notebook is `Python 2 with Spark 2.1`. To update, **Kernel** > Change kernel. To **Trust** the notebook, **File** > Trust Notebook.

## Run the Notebook and Detect Anomalies

  1. Select the cell that starts with `!pip install --upgrade pixiedust,` and then click **Run** or **Ctrl + Enter** to execute the code.
  2. When the installation is complete, restart the Spark kernel by clicking the **Restart Kernel** icon.
  3. In the next code cell, Import your Cloudant credentials to that cell by completing the following steps: 
    * Click
    * Select the **Connections** tab.
    * Click **Insert to code**. A dictionary called credentials_1″ is created with your Cloudant credentials. If the name is not specified as "credentials_1", rename the dictionary to `credentials_1`. `credentials_1` is used in the remaining cells.
    * Name that is required for the notebook code to run.
  4. In the cell with the database name (`dbName`), enter the name of the Cloudant database that is the source of data, for example, _iotp_yourWatsonIoTPorgId_DBName_Year-month-day_. To visualize data of different devices, change the values of `deviceId` and `deviceType`accordingly. You can find the exact database by navigating to your **iot-db **CloudantDB instance you created earlier > Launch Dashboard.
  5. Save the notebook and execute each code cell one after another or run all (**Cell** > Run All) and by end of the notebook you should see anomalies for device movement data (oa, ob, and og). You can change the time interval of interest to desired time of the day. Look for `start` and `end` values.![anomaly_detection_dsx](https://vmacwrites.files.wordpress.com/2018/02/anomaly_detection_dsx.png?w=1480)

> _Along with anomaly detection, the key findings or takeaways from this section are_

  6.     * Usage of Spark to prepare the data for visualization.
    * Usage of Pandas for data visualization
    * Bar charts, Histograms for device data.
    * Correlation between two sensors through a Correlation matrix.
    * A box plot for each devices sensor, produced with the Pandas plot function.
    * Density Plots through kernel density estimation (KDE).![density_plots_sensor_data.png](https://vmacwrites.files.wordpress.com/2018/02/density_plots_sensor_data.png?w=1480)
