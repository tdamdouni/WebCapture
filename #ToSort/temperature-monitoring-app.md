# Temperature Monitoring App

_Captured: 2017-05-21 at 10:56 from [www.jeffgeerling.com](https://www.jeffgeerling.com/project/temperature-monitoring-app)_

![Temperature Monitor Graph Screenshot](https://www.jeffgeerling.com/sites/jeffgeerling.com/files/styles/project-thumbnail/public/images/temperature-monitor-screenshot.png?itok=IYZ5KoI7)

![DS18B20 1-wire temperature sensor wired into Raspberry Pi A+](https://www.jeffgeerling.com/sites/jeffgeerling.com/files/styles/project-thumbnail/public/images/temperature-sensor-ds18b20-pi-aplus.jpg?itok=Ja3jmREr)

I've created a Raspberry Pi-based temperature monitoring application to power a network of temperature and environmental monitors in my home.

The architecture uses one 'master' Pi to aggregate and display log data, and many 'remotes' place around a house to send log data back to the 'master'. The app was originally built in 2015 to help monitor my home environment, and is continuously developed and improved as my monitoring needs change.

Other articles about the Temperature Monitoring system:
