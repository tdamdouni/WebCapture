# Pocket Sized Portable WiFi Deauther

_Captured: 2017-11-16 at 15:28 from [www.instructables.com](http://www.instructables.com/id/Pocket-Sized-Portable-WiFi-Deauther/)_

![](https://cdn.instructables.com/FBC/DEG0/J9JFWL52/FBCDEG0J9JFWL52.MEDIUM.jpg)

Today i'll be telling you how to make your own Pocket Sized Portable WiFi Deauther.

WiFi deauther attacks local access points and cuts them off from using internet services.

so lets get started .

## Step 1: Materials Required

![](https://cdn.instructables.com/FPV/O0M6/J9JFRXZE/FPVO0M6J9JFRXZE.MEDIUM.jpg)

![](https://cdn.instructables.com/F4B/IMJY/J9JFRXZZ/F4BIMJYJ9JFRXZZ.SMALL.jpg)

![](https://cdn.instructables.com/FXU/VGUD/J9JFRY88/FXUVGUDJ9JFRY88.SMALL.jpg)

![](https://cdn.instructables.com/FTB/F52E/J9JFRYFM/FTBF52EJ9JFRYFM.SMALL.jpg)

You'll require the following components to make yourself a WiFi Deauther.

>Node MCU ESP8266

>Connecting wires

>LED (any color of your choice)

>Micro USB cable designed specially for Node MCU unit.

## Step 2: Update From Boards Manaager

![](https://cdn.instructables.com/FXO/0BZ0/J9JG0JR5/FXO0BZ0J9JG0JR5.MEDIUM.jpg)

> Install Arduino and open it.

> Go to File > Preferences

> Add [ http://arduino.esp8266.com/stable/package_esp8266...](http://arduino.esp8266.com/stable/package_esp8266com_index.json) to the Additional Boards Manager URLs. (source:

> Go to Tools > Board > Boards Manager> Type in esp8266 > Select version 2.0.0 and click on Install (must be version 2.0.0!)

## Step 4: 

![](https://cdn.instructables.com/FFV/EYP0/J9JG0NHJ/FFVEYP0J9JG0NHJ.MEDIUM.jpg)

![](https://cdn.instructables.com/FTT/BN6A/J9JG0PJ6/FTTBN6AJ9JG0PJ6.MEDIUM.jpg)

> Go to File > Preferences

> Open the folder path under More preferences can be edited directly in the file

> Go to packages > esp8266 > hardware > esp8266 > 2.0.0 > tools > sdk > include

> Open user_interface.h with a text editor

>Scroll down and before #endif add following lines:

typedef void (*freedom_outside_cb_t)(uint8 status); int wifi_register_send_pkt_freedom_cb(freedom_outside_cb_t cb); void wifi_unregister_send_pkt_freedom_cb(void); int wifi_send_pkt_freedom(uint8 *buf, int len, bool sys_seq);

## Step 6: Upload Code to Node MCU

> Open esp8266_deauther > esp8266_deauther.ino in Arduino

> Select your ESP8266 board at Tools > Board and the right port at Tools > PortIf no port shows up you may have to reinstall the drivers.

> Depending on your board you may have to adjust the Tools > Board > Flash Frequency and the Tools > Board > Flash Size. I use a 160MHz flash frequency and a 4M (3M SPIFFS) flash size.

>use a micro USB cable to connect your Node MCU with your Arduino IDE.

## Step 7: WARNING

![](https://cdn.instructables.com/F5H/IECD/J9JG0RRR/F5HIECDJ9JG0RRR.SMALL.jpg)

## Step 8: Scan for Access Points

![](https://cdn.instructables.com/F2D/74K5/J9JG0SOZ/F2D74K5J9JG0SOZ.SMALL.jpg)

## Step 9: Select Network

![](https://cdn.instructables.com/FVB/YCE0/J9JG0SYL/FVBYCE0J9JG0SYL.SMALL.jpg)

## Step 10: Start Deauth Attack

![](https://cdn.instructables.com/FV8/6C58/J9JG0TMK/FV86C58J9JG0TMK.SMALL.jpg)

## Step 11: Create a Casing

![](https://cdn.instructables.com/F46/237Z/J9JG0WYJ/F46237ZJ9JG0WYJ.MEDIUM.jpg)

## Step 12: Add Visual Indications

![](https://cdn.instructables.com/FZ9/3WPS/J9JFWN5K/FZ93WPSJ9JFWN5K.MEDIUM.jpg)

Connect a LED to indicate that the device is powered up.

LED Node MCU

anode ----> D0

cathode ----> GND

Hope you liked this instructable. Feel free to drop in your comments and suggestions.

Happy Making !!!

## Comments
