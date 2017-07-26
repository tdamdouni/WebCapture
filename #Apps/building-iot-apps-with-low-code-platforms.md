# Building IoT Apps With Low-Code Platforms

_Captured: 2017-04-19 at 21:30 from [dzone.com](https://dzone.com/articles/building-iot-apps-with-low-code-platforms)_

Low-code platforms provide a lot of value to IoT-driven applications. In this blog, we will show you how we created a complete building management application using a low-code platform-- [Progress Rollbase](https://www.progress.com/rollbase)--in a single day. This is the kind of productivity that enables IoT providers to accelerate solutions delivery and facilitate IoT deployments.

## Requirements

RequirementsThe building management application enables users to:

  1. View all buildings around the world

  2. View all rooms in each individual building

  3. Monitor important metrics for each room

Each room is equipped with a device that monitors temperature, carbon dioxide, humidity and VOC (volatile organic compound, these are toxic chemicals that cause skin or respiratory problems). Additionally, the temperature can be adjusted remotely with the application.

## Object Model

It is relatively simple: a building is the main object, and it can have _n_ rooms.

![Image title](https://d117h1jjiq768j.cloudfront.net/images/default-source/default-album/iot1.png?sfvrsn=0)

A building has a fair number of attributes, most notably a location to get automatic integration with Google Maps.

The room object is where the interesting part happens. With a generic REST trigger, we can get access to various metrics. With Rollbase no-code REST invocation, this is a very easy process to setup. You use our REST Mapper tool to store metrics of interest in the Room object. For more information on this, see these two blogs: [Low-Code REST Integration with Rollbase](https://www.progress.com/blogs/low-code-rest-integration-with-rollbase) and [Introduction to Rollbase V4.5--New UI Features & More](https://www.progress.com/blogs/an-introduction-to-rollbase-v45-new-ui-features-more).

## UI

UIHere are some screens from what we have built.

### Buildings List

![Image title](https://d117h1jjiq768j.cloudfront.net/images/default-source/default-album/iot2.png?sfvrsn=1)

### Drill Down Into Specific Buildings

Here, you can see integration with the weather REST service at [OpenWeatherMap](http://api.openweathermap.org/), as well as the built-in image carousel and integration to Google map thanks to the location attribute on the building object. See this blog for more information on built-in image carousel: [Easy Image Carousels with Rollbase and Kendo UI](https://www.progress.com/blogs/easy-image-carousels-with-rollbase-and-kendo-ui).

![Image title](https://d117h1jjiq768j.cloudfront.net/images/default-source/default-album/iot3.png?sfvrsn=1)

In a separate tab, we also show the list of rooms with various metrics as well as the capability to set the temperature on the fly. Notice how the room Fitness Center is flagged in red because the temperature is not adjusting to the set temperature.

![Image title](https://d117h1jjiq768j.cloudfront.net/images/default-source/default-album/iot4.png?sfvrsn=1)

Thanks to the automatic responsive UI, we immediately get support for smartphones and tablets without any additional effort. Here is how it looks:

![Image title](https://d117h1jjiq768j.cloudfront.net/images/default-source/default-album/iot5.png?sfvrsn=1)

![Image title](https://d117h1jjiq768j.cloudfront.net/images/default-source/default-album/iot6.png?sfvrsn=1)

For more information on the automatic responsive system, check out these blogs: [Build No-Code Responsive Apps with Rollbase](https://www.progress.com/blogs/build-no-code-responsive-apps-with-rollbase) and [Customizing Automatic Responsive UI in Rollbase](https://www.progress.com/blogs/customizing-automatic-responsive-ui-in-rollbase).

## Additional Values

You can, of course, leverage all the built-in features of the platform to accelerate your application development. For example, in our app, we wrote a simple email alert that notifies us when room temperature is not within the set range after one hour of changing the temperature. This took just a few minutes to implement as it was all point-and-click configuration and one line of JavaScript to test if the temperature was in range.

Another example is permission and roles. The platform provides an out-of-the-box security Model (Authentication/Authorization) and roles so you do not have to worry about designing, implementing and most importantly testing your own security model. Specifically, the Roles and Permissions system enables you to grant access to various operations and fields with simple configurations (no-coding). For example, one role can view temperatures and another can control the temperature. Now, for more advanced cases, you can even turn on auditing to track when and who does what to various objects with a simple configuration option.

You can also build dashboards with the built-in charts and gauges or build [completely customized ones using Kendo UI](https://www.progress.com/blogs/responsive-low-code-rollbase-dashboards-with-kendo-ui) or [Fusion Charts](https://www.progress.com/blogs/creating-rollbase-dashboards-with-custom-fusioncharts) without any additional cost.

The key point is that you do not need to reinvent, code, and test a lot of services.

## Rules for Intelligent Proactive Actions

When you monitor multiple rooms in multiple buildings around the world, you probably want to implement smart preventive rules.

As a simple example, you can imagine that if you detect a higher carbon dioxide level than average, you would want to run some maintenance. Depending on the reading, you would schedule the maintenance with different urgency. As Rollbase offers a built-in workflow engine as well as calendaring and scheduling operations, implementing proactive actions is mostly done via point-and-click configurations. Of course, your imagination is the limit--you could deploy more complex rules considering historical metrics, data collection, incident report metrics, current weather forecasts, and more.
