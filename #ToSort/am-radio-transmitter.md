# AM Radio Transmitter

_Captured: 2018-04-07 at 09:59 from [bitluni.net](http://bitluni.net/am-radio-transmitter/)_

## Work principle

AM Radio transmissions are based on a carrier signal which is modulated by the audio signal. It's a very basic principle but prone to noise from the environment. Using the ESP32 it is really simple to generate an analog signal using the built-in DACs. With the provided code here just a wire as an antenna has to be connected to the pin 25 of the ESP32. The transmission will end up on the AM frequency ~835kHz.

## ![](http://bitluni.net/wp-content/uploads/2018/01/am-modulation.png)

## Parts

The parts used here are the LOLIN32 and the ESP32 MiniKIT. But Any ESP32 board can be used.

![](http://bitluni.net/wp-content/uploads/2017/11/lolin32-front.jpg)

![](http://bitluni.net/wp-content/uploads/2017/11/lolin32-back.jpg)

![](http://bitluni.net/wp-content/uploads/2017/12/esp32-front-1306x1524.jpg)

![](http://bitluni.net/wp-content/uploads/2017/12/esp32-back-1464x1524.jpg)

  * ## Where to get them

These links are the cheapest I could find and also supporting our work (affiliate). I also ordered my modules there  
[LOLIN32 Board (~$6.90)  
](http://s.click.aliexpress.com/e/jYvJIEi)[ESP32 Mini KIT (~$7.98)](http://s.click.aliexpress.com/e/FQ7mQRJ)

But there are also cheap modules on Amazon and eBay:  
[Amazon.com](http://amzn.to/2Gk0hIH) [.ca](http://amzn.to/2BtUoF8) [.de](http://amzn.to/2DCcDdk) [.fr](http://amzn.to/2ndQLxG)  
[Ebay ](http://rover.ebay.com/rover/1/711-53200-19255-0/1?icep_ff3=9&pub=5575230344&toolid=10001&campid=5337966422&customid=&icep_uq=esp32&icep_sellerId=&icep_ex_kw=&icep_sortBy=12&icep_catId=&icep_minPrice=&icep_maxPrice=&ipn=psmain&icep_vectorid=229466&kwid=902099&mtid=824&kw=lg) [.de](http://rover.ebay.com/rover/1/707-53477-19255-0/1?icep_ff3=9&pub=5575230344&toolid=10001&campid=5337966422&customid=&icep_uq=esp32&icep_sellerId=&icep_ex_kw=&icep_sortBy=12&icep_catId=&icep_minPrice=&icep_maxPrice=&ipn=psmain&icep_vectorid=229487&kwid=902099&mtid=824&kw=lg) [.fr](http://rover.ebay.com/rover/1/709-53476-19255-0/1?icep_ff3=9&pub=5575230344&toolid=10001&campid=5337966422&customid=&icep_uq=esp32&icep_sellerId=&icep_ex_kw=&icep_sortBy=12&icep_catId=&icep_minPrice=&icep_maxPrice=&ipn=psmain&icep_vectorid=229480&kwid=902099&mtid=824&kw=lg)

The oscilloscope came quite handy this project. I really like it, check it out:  
[Amazon.com](http://amzn.to/2GiZvLV) [.de](http://amzn.to/2ncJY8w) [.ca](http://amzn.to/2ndXtny) [.fr](http://amzn.to/2GiZ7gr)

## Code

All projects and files can be found here:  
<https://github.com/bitluni/ESP32AMRadioTransmitter>

## Audio to header converter

You can prepare your sounds using [Audacity](http://www.audacityteam.org/download/)

Open an audio file supported by the browser to convert it to a c++ header file (8Bit signed).

Export: normalize resample

## Datasheets

## Similar Projects

Send me a message if you know of any similar projects
