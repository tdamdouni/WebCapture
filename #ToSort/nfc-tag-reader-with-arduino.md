# NFC Tag Reader With Arduino

_Captured: 2017-06-13 at 23:08 from [dzone.com](https://dzone.com/articles/nfc-tag-reader-with-arduino?edition=303098&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-13)_

I want to use the NFC tag reader module with my Arduino. The idea is to build a simple prototype to read NFC tags and validate them against a remote server (for example, a node TCP server). Depending on the tag, we'll trigger one digital output or another. In this example, we'll connect LEDs to those outputs, but in real life, we can open doors or do something similar to that.

We'll use an MFRC522 module. It's a cheap Mifare RFID/NFC tag reader and writer.

MFRC522 Connection:

  * **sda**: 10 (*) -> 8
  * **sck**: 13
  * **Mosi**: 11
  * **Miso**: 12
  * **Rq**: --
  * **Gnd**: Gnd
  * **Rst**: 9
  * **3.3V**: 3.3V

In this example, we'll use an ethernet shield to connect our Arduino board to the LAN. We must be careful doing this. If we use an ethernet shield with an MFRC522, there's an SPI conflict due to the ethernet shield's SD card reader. We need to use another SDA pin (here, I'm using pin 8 instead of 10) and disable w5100 SPI before configuring ethernet.

Here is the Arduino code:

Now, we only need to create a simple TCP server with a node to validate our NFC tags.

And that's all! Here's a video with the working example:

And the full code is available on my [GitHub](https://github.com/gonzalo123/arduino-nfc-reader) account.

References about RFID and Arduino can be found [here](https://www.luisllamas.es/arduino-rfid-mifare-rc522/), [here](http://hetpro-store.com/TUTORIALES/modulo-lector-rfid-rc522-rf-con-arduino/), and [here](https://forum.arduino.cc/index.php?topic=198768.0).
