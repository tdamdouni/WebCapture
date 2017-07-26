# Building a Web-Based Sensor App With a Raspberry Pi 3 and the Azure IoT Hub

_Captured: 2017-04-10 at 01:09 from [dzone.com](https://dzone.com/articles/building-a-web-based-sensor-app-with-a-raspberry-p?edition=288887&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-09)_

I was planning to build a web-based temperature/humidity monitoring app with a Raspberry Pi 3 and Windows 10 IoT Core. I have been playing around with Raspbian for a while now, and this time, I wanted to try something different. I have been using Python to write applications for my Raspberry Pi, so Windows IoT Core with C# will be something new for me. Therefore, this time, I choose to go with Windows 10 IoT Core.

> _Here is the list of things you'll need to get started:_

  * Raspberry Pi 3 with Windows 10 IoT Core

  * Adafruit BME280 Temperature Humidity Pressure sensor

  * Jumper wires

  * Power Bank

  * Visual Studio 2015/2017

  * Azure account

Setting up the Pi with Windows 10 IoT Core is a very straightforward process. You can read more about it [here](https://developer.microsoft.com/en-us/windows/iot/docs/iotdashboard). I recommend connecting the device to your Wi-Fi network. This will give you the benefit of moving your device around. The problem for the first time users will be that the device will not auto-connect to the Wi-Fi network. To solve this problem, you need to use a wired LAN connection from the network or from a local computer. Once it's plugged in, you will be able to see the device in the IoT dashboard. From there, you can go to the Device Portal and connect to the Wi-Fi network. After the connection is successful, you can then remove the LAN cable. To follow the exact steps, head over to the [documentation](http://www.opentechguides.com/how-to/article/windows-iot/111/windows-iot-wifi.html). This is how your device will be displayed in the IoT dashboard.

## Getting Things Ready in Azure

You can set up things in the cloud from the Azure Portal as well as from the IoT Dashboard itself. From the dashboard, you can create and provision a new IoT Hub and register the device in that Hub. First, sign into your Azure account by clicking the Sign-In option on the left-hand sidebar. After the sign-in is successful, you will be prompted with the screen below, where you can provision a new IoT Hub and add your current device to it.

I am skipping the step for setting up the IoT Hub from the Azure Portal, as there is [good documentation](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-create-through-portal) already available. Pushing data to the IoT Hub with the SDK is easy, but you can't make use of the IoT Hub alone to read that data and do your work. Therefore, you also need to set up a Queue to read that data. As of now, you cannot create a Queue from the new Azure Portal. Instead, you have to head toward the old portal at manage.windowsazure.com and create a Queue from there. To create a Queue, click New > App Services > Service Bus > Queue > Quick Create. Fill in the details to create a new queue.

Make sure that the region you are selecting here for the queue is the same as your IoT Hub region. If you select a different region, you will not be able to associate this queue with the Hub endpoint.

In the Azure Portal, to associate this queue with the IoT Hub endpoint, click Endpoints and then click Add to add the queue to the endpoint.

## Setting Up the Circuit

Now, as you have the device and the OS ready, you can build the circuit. The BME280 sensor can be used with both I2C and SPI. For the project, I am using I2C. Below is the Fritzing diagram for your reference. You can download the [Fritzing sketch file on GitHub repo](https://github.com/prashantkhandelwal/Pi-Code/raw/master/BME280-PI3-Win10IoT-Azure/BME280.fzz).

## Creating the Device Application

I am using Visual Studio 2017 Enterprise Edition to build the device application and the web monitor application, which I will be hosting in the cloud. To create the device application, start with the Windows Universal Project templates and select the Blank App (Universal) template.

There is a project template available for Visual Studio that will let you build applications for Raspberry Pis. The problem with that project type is that you will not be able to make use of the libraries or the SDK available for .NET yet. You can still build applications with this project type, but you have to make use of the REST API, and using REST APIs is not as straightforward as SDKs.

After the project creation is successful, you need to add the dependencies below, which will let you connect to IoT Hub and have device-to-cloud communication. Below are the NuGet packages you need to install.

This package will enable device-to-cloud communication:

This package is the wrapper for the BME280 sensor:

Add the below namespaces in the Main.xaml.cs file:

Declare the variables:

The iothuburi is the URL for the IoT Hub created in the Azure Portal or from the IoT dashboard. You can get the device key from the Device Explorer section in the IoT Hub. You can see how to get the Key from the Device Explorer from the screenshot below. I am using the Primary Key as a devicekey in my code.

In the constructor, initialize the DeviceClient and BME280Sensor objects. I have commented out the InitializeComponent(), but if you want, you can keep it as it is.

Now, add a function named DeviceToCloudMessage, which will connect to the IoT Hub using the device key, read the sensor data, serialize the data in JSON format, and send it to the IoT Hub. Add this to the very bottom of the constructor.
    
    
                                     DateTime.Now.ToLocalTime().TimeOfDay.Seconds),
    
    
            var message = new Message(Encoding.ASCII.GetBytes(messageString));

The date property in the sensorData type is being set in this specific way because we want to see the graph continuously moving. I can also read Pressure from the sensor, but as I am not interested in showing this data, I am skipping it. If you want, you can use it, but you also have to change the web app to show it. Before I can send this data to the IoT Hub, I am serializing the sensorData object and using ASCII encoding to get the byte[] to pass it to the Message class constructor. The last step is to send the message to the Hub by using the DeviceClient class' SendEventAsync method. In the last line, I am adding a delay of 5 seconds between each reading. You can increase the time and see how the chart renders. I recommend not going below this time delay, as this might give you some false readings from the sensor.

I took this code from the documentation here and tweaked it to have the real data from the sensor connected to the device. Press Ctrl+Shift+B to build the solution. Navigate to Project, then click <project> Properties. Under the Debug section, set the Start Options as shown below. Notice that the Platform is set to ARM and Configuration is Active (Debug). When you are done debugging the code and ready to deploy the code to the device, you need to change it to Release.

Unlike Raspbian, where we ssh or RDP into the device and compile or build the code, Windows 10 IoT works in a different way. You need to remote deploy the application from Visual Studio. Also, if you have enabled remote debugging on the device, you have to add the port number to the Remote Machine value and set the Authentication Mode to None.

> NOTE: When you make changes to device application, you also need to change/increment the version of the application in the Package.appxmanifest file. If you miss this step, then the application deployment will fail.   
  


To deploy the app to the device, click the Build menu and select Deploy <Project Name>. If you are deploying the application for the first time, it will take some time to get deployed. After the deployment is successful, you will see the application under the App section.

At this moment, the application is stopped. To start the application, click the Play button in the list. The App Type shows the type of application, or you can state the mode it is running on. When I created the application, I selected the UWP application and, therefore, it will always run in the Foreground type. The reason I chose this application type (UWP) is because I can then use the SDK to communicate with the IoT Hub. If you want to create a Background application type, then you can download [this](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplatesforVS15) Visual Studio Extension for 2017 and [this](https://marketplace.visualstudio.com/items?itemName=MicrosoftIoT.WindowsIoTCoreProjectTemplates) for Visual Studio 2015, which will let you build the background application. Keep in mind that you cannot use any SDK library with this project type. All you have now is the power of a REST API, which is not very easy to use.

## Setting Up the Web App

You can build any kind of app to visualize data, but because the SDK support for .NET is good, I am going to set up a simple MVC application using the .NET Framework. As of now, you cannot use the Azure SDK with .NET Core applications, and it also looks like the team does not have any plans to shift their focus to releasing the SDK for .NET Core anytime soon.

Start by installing the NuGet packages. First, grab the package that will let you read data from the Queue.

Because this is a real-time application, you also need to install SignalR:

After these packages are installed, You need a way to visualize the temperature and humidity received from the queue. To do this, you can use any Jquery chart plugin or any other library of your choice. I will be using [Google Charts](https://developers.google.com/chart) in my app, [Line Charts](https://developers.google.com/chart/interactive/docs/gallery/linechart) to be precise. Installation is straightforward for the charts, and you can play around with different options to tweak the look and feel of the chart. I am going to add the chart code in the Index.cshtml file. Below is the complete code for the chart to render.
    
    
    <script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
    
    
        google.charts.load('current', { packages: ['corechart', 'line'] });
    
    
            var time = pi.date.split(',');
    
    
            data.addRows([[[parseInt(time[0]), parseInt(time[1]), parseInt(time[2])], temp, humid]]);
    
    
            chart = new google.visualization.LineChart(document.getElementById('chart_div'));

I made use of the sample code from the examples at Google Charts and used it along with some minor tweaks to suit my needs. The loadChart() function is called for the first time when the page is loaded, and then I have a SignalR hub, which updates the chart with the same option sets that I have in the loadChart() function. I added three data columns to display the data in the chart.

There are a few things that I would like to talk about in the above code. First, the timeofday is displayed on the X-axis because time is continuous and I want to update the chart over time. Second, the gridlines property of the vAxis lets you set how many horizontal rows you want to see in the graph. I have increased it to quite a significant number because I want to see the graph in more detail. You can play around with these settings and see what looks better for you. Third, the response I receive in the Hub is in string format and, therefore, I have parsed that string to JSON in order to read it and set to the rows. Also note that I have left the console.log in the above code so that when you run the web app, you can see the raw data in the console.

In HomeController.cs, first, I will set the connection string to the Queue, which I have associated with the IoT Hub endpoint in Azure, and set the Queue name along with the IHubContext for SignalR communication.

In the constructor, initialize the IHubContext object.

Here is the code for the IoTHub class:

And the code for Startup class (Startup.cs)

In the Index ActionResult, I will start a task that will read the messages from the Queue, and then SignalR will broadcast it to the client side, which, in turn, updates the chart with the latest data or temperature/humidity readings.

First, I created a QueueClient object with the connection string and Queue name along with the ReceiveMode. I have set ReceiveMode to ReceiveAndDelete, as I want to delete the data from the Queue once it has been read, although you have an option to have the data in the queue for a maximum of seven days in Azure. The QueueClient has an OnMessage event, which processes a message in an event-driven message pump. That means that as soon as the something is being added to the Queue, this event is fired. I get the message body in the form of a Stream, read the message to the end, and pass the message to the SignalR hub, which updates my chart in real time. Here is the final output I have now.

If you look closely, you will notice that the temperature line is not as smooth as you thought it would be. This is because every time the Raspberry Pi reads the data from the sensor, there is a slight change in the temperature -- only a few decimal places. If you don't like this, then you can change the gridlines property of the vAxis in the chart. Also, you can try changing the time delay on the device to see if that impacts the lines on the chart. Try changing both the time delay in the device application and the gridlines in the web application to see how the chart renders.

The complete source code is available [on GitHub.](https://github.com/prashantkhandelwal/Pi-Code/tree/master/BME280-PI3-Win10IoT-Azure)
