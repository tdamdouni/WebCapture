# Portable WiFi Scanner with OLED Display (ESP8266): signal strength, connection test to a server

_Captured: 2017-11-08 at 23:43 from [diyprojects.io](https://diyprojects.io/portable-wifi-scanner-oled-display-esp8266-signal-strength-connection-test-server/#.WgOHg0q1Kf0)_

In this project, we will develop a **portable WiFi scanner with an OLED display** based on an **ESP8266** (Wemos D1 mini). It is very easy and very economical to manufacture its own sensors and connected objects based on ESP8266. Only small problem, one always wonders whether the quality of the WiFi signal will be sufficient in the area where the object will be connected. We all have the SLR to draw his mobile phone to check the WiFi signal. This is a very good solution but the hardware used does not necessarily work identically. With this scanner (which holds in the hand), it will be possible to test in real situation the reception of the signal. A small server running Nodejs will also test whether communication is possible.

In this project, we will manufacture a small portable WiFi scanner based on Wemos D1 mini. The Wemos will be powered by a LiPo battery (here a 3.7 Volts - 150 mAh) using the Shield Battery presented here. We will finish stacking with the Shield OLED SSD1306 (64×48 pixels) previously presented in this article. If your battery is not equipped with a JST XH2-2.54mm connector, you can [change the cable](http://s.click.aliexpress.com/e/7eiuvbm) or use [Dupont connectors to crimp](http://www.banggood.com/search/dupont-connector.html?p=RA18043558422201601Y).

Wire with [JST XH2-2.54mm](http://s.click.aliexpress.com/e/7eiuvbm) connector

What is magic with the Wemos … is that there is no circuit! We simply stack the modules one above the other and it works. I simply soldered a 1.5MΩ resistor between the positive battery pin and the analog input A0 to monitor the charge level of the battery. The method has already been presented in this paper.

Here is the stack obtained. From bottom to top, we find the Wemos then the Shield Battery and finally we finish the battery with the Shield OLED. I used a small LiPo battery of 150 mAh that I slipped between the Wemos and the Shield Battery.

![](https://www.projetsdiy.fr/wp-content/uploads/2017/03/wemos-d1mini-shield-battery-oled-wifi-scanner.jpg)

To use the 64×48 pixel OLED screen, the easiest way is to use the Adafruit_ssd1306 library modified by [Mike Causer](https://github.com/mcauser). It is available on Github [here](https://github.com/mcauser/Adafruit_SSD1306/tree/esp8266-64x48). The program is very simple:

  * The list of available networks (SSIDs) is first retrieved.
  * For each network in the list 
    * The strength of the signal is recovered and the number of bars to be displayed (from 0 to 5) is determined.
    * A request is sent to the test server. The server must respond within a time-limit imposed by the **http.setTimeout (duration)** function.

```
#include <SPI.h>
#include <Wire.h>
#include <Adafruit_GFX.h>
#include "Adafruit_SSD1306.h"
#include <ESP8266WiFi.h>
#include <ESP8266HTTPClient.h>

// SSID et mot de passe des réseaux à tester - SSID and password of the networks to check
// Ajoutez autant de réseau que désiré - Add as network as desired
String ssids[3] = {"yourSSID1","yourSSID2","yourSSID3"};
String passwords[3] = {"pwdSSID1","pwdSSID2","pwdSSID3"};

// IP du serveur de test - Test server IP
const char* host = "xxx.xxx.xxx.xxx";
// Port du serveur - Server Port
const int port = 8080;

#define OLED_RESET 0  // GPIO0
Adafruit_SSD1306 display(OLED_RESET);
 
// Initialisation des Objets - Init objects
WiFiClient wifi;
HTTPClient http;

// Fonction de connexion au réseau WiFi 
void setup_wifi(String ssid, String password) {
  delay(10);
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);

  // Il faut convertir la String en char* - need to convert String to char*
  WiFi.begin(ssid.c_str(), password.c_str());
  // Connexion au réseau WiFi - connecting to WiFi network
  int count = 0;
  while (WiFi.status() != WL_CONNECTED) {
    count++;
    delay(500);
    Serial.print(".");
    if ( count > 10 ) { return; }
  }

  Serial.print("IP Address: ");
  Serial.println(WiFi.localIP());
}

void setup() {
  pinMode(A0, INPUT);  // Le convertisseur A/N A0 sera utilisé pour mesurer la tension de la batterie - Set A0 converter as input to measure the battery tension
  Serial.begin(115200);
  
  display.begin(SSD1306_SWITCHCAPVCC, 0x3C);  // initialize with the I2C addr 0x3C (for the 64x48)
  display.display(); 
}

float getLevel(){
  float raw = analogRead(A0);
  int level = map(raw, 140, 227, 0, 100);     // Avec une résistance 1M5 - With a 1M5 resistor
  Serial.print("A0 "); Serial.println(raw);
  
  if ( level < 0 ) { level = 0; }
  if ( level > 100 ) { level = 100; }
  Serial.print("Level: "); Serial.println(level);
  return level;
}

float getVoltage(){
  float raw = analogRead(A0);                      
  float volt = map(raw, 140, 227, 338, 511);  // Avec une résistance 1M5 - With a 1M5 resistor
  volt = volt / 100;
  Serial.print("A0 "); Serial.println(raw);
  Serial.print("Voltage "); Serial.println(volt);
  return volt;
}

void loop() {
  byte available_networks = WiFi.scanNetworks();
  if ( available_networks > 0 ) {
    for (int network = 0; network < available_networks; network++) {
      //delay(1000);
      int level = getLevel();
      long rssi = WiFi.RSSI(network);
      int bars = getBarsSignal(rssi);
      Serial.print("RSSI:");
      Serial.println(rssi);
  
      display.clearDisplay();
      display.setTextSize(1);
      display.setTextColor(WHITE);
      display.setCursor(0,0);

      // Affiche le nom du réseau, la qualité du signal et le niveau de la batteri - display network name, signal Strength and battery level
      display.print("SSID "); display.println(WiFi.SSID(network));
      display.print("RSSI:"); display.println(rssi); 
      display.print("Bat."); display.print(level); display.println("%");
      
      // Affiche les barres de réception du signal - display signal quality bars
      for (int b=0; b <= bars; b++) {
        // display.fillRect(59 + (b*5),33 - (b*5),3,b*5,WHITE); 
        display.fillRect(10 + (b*5),48 - (b*5),3,b*5,WHITE); 
      }
      
      display.display();
      delay(2000);

      // Vérifie si la connexion au serveur fonctionne - Check if connexion is correct with the server
      for ( int i = 0 ; i < 3 ; i++ ) {
        String _ssid = ssids[i];
        String _pwd = passwords[i];
        String _currentSSID = WiFi.SSID(network);
        if ( _currentSSID == _ssid) { 
          checkServerConnexion(_ssid,_pwd);
        }
      }    
    }  
  } else {
    displayMessage("No Signal !", 1000, 1);
  }
}

void checkServerConnexion(String ssid, String password){
  Serial.println("Checking server connexion...");
  displayMessage("Checking server connexion...", 250, 1);
  setup_wifi(ssid, password);
  String _status = ssid;
  http.setTimeout(1000);
  http.begin(host,port, "/checkconnexion");
  int httpCode = http.GET();
  Serial.print("HTTP Code "); Serial.println(httpCode);
  if (httpCode) {
    if (httpCode == 200) {
      Serial.println("Connexion OK");
      _status += " OK";
      displayMessage(_status, 2000,2);
    } else {
      Serial.println("Connexion KO");
      _status += " KO!";
      displayMessage(_status, 2000, 2);
    }
  } else {
    Serial.println("Connexion KO");
    _status += " KO!";
    displayMessage(_status, 2000, 2);
  }
  Serial.println("closing connection");
  http.end();
}

void displayMessage(String message, int duration, int Size){
  display.clearDisplay();
  display.setTextSize(Size);
  display.setTextColor(WHITE);
  display.setCursor(0,0);
  display.println(message);
  display.display();
  delay(duration);
}

int getBarsSignal(long rssi){
  // 5. High quality: 90% ~= -55db
  // 4. Good quality: 75% ~= -65db
  // 3. Medium quality: 50% ~= -75db
  // 2. Low quality: 30% ~= -85db
  // 1. Unusable quality: 8% ~= -96db
  // 0. No signal
  int bars;
  
  if (rssi > -55) { 
    bars = 5;
  } else if (rssi < -55 & rssi > -65) {
    bars = 4;
  } else if (rssi < -65 & rssi > -75) {
    bars = 3;
  } else if (rssi < -75 & rssi > -85) {
    bars = 2;
  } else if (rssi < -85 & rssi > -96) {
    bars = 1;
  } else {
    bars = 0;
  }
  return bars;
}
```

Here is a small test server developed with Nodejs. It starts a server that listens for requests from the route /checkconnection on port 8080. If port 8080 is already in use on your computer, just change it at the end of the program. The server responds just to the client by returning a 200 (OK) status.

Follow [this tutorial](https://www.diyprojects.io/esp8266-web-server-fast-development-of-html-js-with-node-js-and-pug/) to install Nodejs on your computer and discover some notions. You will need to install the expressjs package to run the server

Ouvrez un editeur de texte et collez le code ci-dessous.

```
/*
*   Serveur de test pour scanner WiFi portable à base d'ESP8266
*   Test server for portable ESP8266 WiFi Scanner
*   http://www.projetsdiy.fr - 2017
*/
var express = require('express');
var app = express();
 
app.get('/', function(req, res) {
  res.send('Test Server for ESP8266 WiFi scanner');
});
 
app.use('/checkconnexion', function (req, res, next) {
  console.log("check server connexion received");
  res.sendStatus(200);
 
});
 
// Port du serveur - Server Port 
app.listen(8080);
```

Save the file by giving it the name of **server.js** for example.

Open a Terminal (MacOS, Linux), Power Shell, or the command prompt (on Windows). Navigate to the directory where the server was registered and run the following command to start it.

At each request of the WiFi scanner, a new message will be displayed

You can go hunting WiFi network!

Once the server is started and the Arduino program is uploaded to the ESP8266, you are ready to map WiFi reception in your home and garden. Networks are tested one after the other.

![esp8266 scanner wifi portable ssid1](https://www.projetsdiy.fr/wp-content/uploads/2017/03/1-esp8266-scanner-wifi-portable-ssid1.jpg)

As soon as a network corresponds to a private network, the program tries to connect to it and then sends a request to the server

![esp8266 scanner wifi portable ssid connexion](https://www.projetsdiy.fr/wp-content/uploads/2017/03/2-esp8266-scanner-wifi-portable-ssid-connexion.jpg)

If the server has responded within the time limit, the reception quality is sufficient to place a connected object running in WiFi

![esp8266 scanner wifi portable ssid1 test serveur ok](https://www.projetsdiy.fr/wp-content/uploads/2017/03/3-esp8266-scanner-wifi-portable-ssid1-test-serveur-ok.jpg)

Otherwise, the network does not offer sufficient quality. In this case, you can install a [WiFi repeater ](http://www.banggood.com/search/wifi-repeater.html?p=RA18043558422201601Y)that plugs into a power outlet.

![esp8266 scanner wifi portable ssid2 test server ko](https://www.projetsdiy.fr/wp-content/uploads/2017/03/5-esp8266-scanner-wifi-portable-ssid2-test-server-ko.jpg)

A small demonstration video
