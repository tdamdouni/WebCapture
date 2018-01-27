# Home Assistant – Plot a Graph with Object’s Attributes

_Captured: 2017-11-07 at 16:25 from [www.hiscorebob.lu](http://www.hiscorebob.lu/2017/11/home-assistant-plot-a-graph-with-objects-attributes/)_

![](https://i1.wp.com/www.hiscorebob.lu/wp-content/uploads/HA-Graph-3.jpg?resize=850%2C450)

> _History Graph of a TP-Link HS100 Smart Wifi Plug_

[Home Assistant ](https://home-assistant.io/)is a great Home Automation Software. It provides features and benefits that surpasses the software provided by the Hardware Manufacturers by far. One such example are my [TP-Link HS110 Smart WiFi Plugs with Energy Monitoring](http://www.tp-link.de/products/details/cat-5258_HS110.html). The provided App by TP-Link (Kasa) is limited:

  * only one Smartphone or Tablet can manage the plugs (I do not want to use their cloud solution)
  * it does not provide any history graph, only displays average values

This is where Home Assistant kicks in. Not only I can control my devices with any Browser enabled device, I can also keep track of my power consumption.

In Home Assistant, each device is an object. An Object can have attributes. The [TP-Link Switch Component](https://home-assistant.io/components/switch.tplink/) in Home Assistant provides following attributes:

  * Total Consumption
  * Current
  * Current Consumption
  * Voltage
  * Daily Consumption

A typical setup of a Device would look like this:
    
    
    # Example configuration.yaml entry of a TP-Link Switch
    switch:
      - platform: tplink
        name: Bureau
        host: IP_ADDRESS

In the Example above, we name our Switch "**Bureau**", the object's name in Home Assistant will become "**switch.bureau**"

Once setup, it will show up in Home Assistant, with it's current state (on or off), and it's attibutes :

![Pop up Window in Home Assistant with the state and attributes](https://i0.wp.com/www.hiscorebob.lu/wp-content/uploads/HA-Graph-1.jpg?w=1280)

> _Pop up Window in Home Assistant with the state and attributes_

For a better understanding, I recommend checking the proper attribute name used by Home Assistant by going into the "**states**" section of the "**Developer Tools**"

![Developer View of Object's Attributes](https://i2.wp.com/www.hiscorebob.lu/wp-content/uploads/HA-Graph-2.jpg?w=1280)

> _Developer View of Object's Attributes_

In this example, I want to plot a graph from attribute "**current_consumption**" from object "**switch.bureau**"

Ok, so now that we know the name of the attribute, we need to tell Home Assistant how to get it. For this, we are going to use the "[Template Sensor](https://home-assistant.io/components/sensor.template/)" Component. It's important to use the sensor variant, although our object is a "switch" component.
    
    
    # Example configuration.yaml entry
    sensor:
      - platform: template
        sensors:
          bureau_power_sensor:
            value_template: {{states.switch.bureau.attributes.current_consumption}}        
            unit_of_measurement:  W
            
    

In the Example above, we define the sensor's name (**bureau_power_sensor**) and which attribute (**current_consumption**) to read from a specific object (**switch.bureau**)

Now that we have the attribute defined as a Data Source it's time to..

Introduced in version 0.55, the [History Graph Component](https://home-assistant.io/components/history_graph/) does exactly what we want.
    
    
    # Example configuration.yaml entry
    history_graph:
      power:
        name: Power Graph
        entities:
          - sensor.bureau_power_sensor

The Graph is placed into the group "**power**" (handy if you have multiple plugs) and it's name is "**Power Graph**" (which will become the entity / object **history_graph.power_graph** in Home Assistant)

If you have grouped your view, an example groups.yaml would look like this:
    
    
    # Example groups.yaml entry
    graphs:
      name: Graphs
      view: yes
      entities:
        - history_graph.power_graph

Here's the Result:

![History Graph of a TP-Link HS100 Smart Wifi Plug](https://i1.wp.com/www.hiscorebob.lu/wp-content/uploads/HA-Graph-3.jpg?w=1280)

> _History Graph of a TP-Link HS100 Smart Wifi Plug_
