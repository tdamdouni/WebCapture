# Mein Weg in das IoT (20): Ein eigenes WLAN-Netzwerk mit dem ESP32

_Captured: 2017-11-15 at 16:24 from [www.elektormagazine.de](https://www.elektormagazine.de/news/mein-weg-in-das-iot-20-ein-eigenes-wlan-netzwerk-mit-dem-esp32)_

![Die RGB-LED leuchtet grün: Die Zugangsdaten zum Router-Netzwerk stimmen.](https://cdn.xingosoftware.com/elektor/images/fetch/w_300/https:/www.elektormagazine.de/assets/upload/images/26/20171114181447_20171012-171012RS.jpg)

> _Die RGB-LED leuchtet grun: Die Zugangsdaten zum Router-Netzwerk stimmen._

In der [letzten Folge](https://www.elektormagazine.de/news/mein-weg-in-das-iot-19-einfacher-webserver-mit-dem-esp32) haben wir mit dem [ESP32 DevKitC](https://www.elektor.de/esp32-devkitc) einen kleinen Webserver verwirklicht. Auf Anfrage eines Webbrowsers liefert der ESP32 ein kleines Formular mit mehreren Textfeldern aus, in die der Nutzer Werte eintragen kann. Ein anschließender Klick auf die Schaltflache „Submit" lasst den Webbrowser eine erneute HTTP-Anfrage starten, bei der die Werte in den Textfeldern in den URL (der Ausdruck in der Browser-Adresszeile) eincodiert werden. Der Embedded-Webserver wertet den URL innerhalb der Anfrage aus, veranlasst eine entsprechende Aktion und sendet wiederum eine Webseite zum Browser zuruck. Als kleine Demo hatte ich mir ausgedacht, dass man mit einer „00" oder „FF" im ersten Textfeld eine rote, an das Board angeschlossene LED schalten kann. Die Werte in allen drei Textfeldern werden außerdem in einem kleinen String-Array gespeichert. Prinzipiell hatten wir uber die Webseite also mehrere Konfigurationswerte unseres kleinen Gerats einstellen konnen - man denke an Zugangsdaten fur ein Cloud-Portal.

Das Ganze demonstrierte schon, dass ein Webbrowser auf dem Smartphone oder dem PC als User-Interface fur ein IoT-Gerat dienen kann, das sich im selben Netzwerk befindet. Es sind jetzt aber noch zwei entscheidende Haken an der Sache. Erstens werden die Konfigurationswerte noch nicht dauerhaft gespeichert, nach einem Reset des Controllers musste man alles noch einmal neu eingeben. Und zweitens entziehen sich gerade die SSID und das Passwort fur das WLAN-Netzwerk dieser Einstellmoglichkeit. Denn das Konfigurieren funktioniert ja nur, wenn das ESP32-Board schon im heimischen Netzwerk eingebucht ist. Lastigerweise mussten wir in allen [bisherigen Folgen](https://www.elektormagazine.de/search?query=mein+weg) immer noch die Zugangsdaten fur das Netzwerk in den Arduino-Sketch schreiben, das Programm danach neu kompilieren und dann hochladen - bei einem Netzwerkwechsel geht das Spiel von neuem los.

## ESP32 als Access Point

Praktischerweise bietet der ESP32 (genauso wie sein kleiner Bruder, der ESP8266) aber auch die Moglichkeit an, ein eigenes WLAN-Netzwerk aufzuspannen, namlich im Modus „_Access Point_". Das geht sogar parallel zur Funktion als „_Station_" in einem Router-Netzwerk, den Modus, den wir bisher genutzt haben. PC oder Smartphone kann man dann in das vom ESP32 selbst aufgespannte Netzwerk einloggen (ein Passwort muss man per default nicht angeben). Der ESP32 ist im eigenen Netzwerk unter der Adresse „192.168.4.1" per Webbrowser erreichbar. Man kann nun wie gehabt auf dem Controller einen Webserver anwerfen und ein Formular ausliefern, in das der Nutzer die Zugangsdaten fur das heimische Router-Netzwerk (SSID, Passwort) eintragen kann. Nach Empfang der Daten loggt sich der ESP32 dort ein und kommt damit schließlich ins Internet.

Fur das erstgenannte Problem gibt es ebenfalls eine Losung: Der ESP32 bringt sogenannten _Non-volatile storage_ _(NVS)_ mit, der im externen Flash untergebracht ist und Konfigurationswerte und ahnliches dauerhaft speichern kann. Fur einen bequemen Zugriff darauf haben die Entwickler von Espressif die Library _Preferences_ geschrieben.

Um das Ganze auszuprobieren, habe ich mir wieder eine einfache Demo-Anwendung ausgedacht; die Hardware bleibt die gleiche wie in der letzten Folge. Nach dem erstmaligen Hochladen des Programms kennt der ESP32 die Zugangsdaten zum Router-Netzwerk noch nicht. In der Setup-Funktion versucht er trotzdem, sich wie in den vergangenen Folgen ins Netzwerk einzuloggen, was naturlich nicht gelingt. In der Folge leuchtet die RGB-LED rot. Im Code wurde der ESP32 aber mit

in den Modus _Access Point + Station_ versetzt, mit

wirft man den Access Point an. Der Parameter dieser Funktion ist die SSID des selbst aufgespannten Netzwerks, unter der dieses bei einer WLAN-Suche gefunden werden kann.

Wenn man den PC hier einloggt und im Browser „192.168.4.1" eingibt, dann wird statt der normalen Webpage zum Steuern der LED nun ein Formular ausgeliefert, in das sich die SSID (zweites Textfeld) und das Passwort (drittes Textfeld) des Router-Netzwerks eintragen lassen. Zum Testen lasst sich uber das erste Textfeld auch die rote LED schalten, wie gehabt mit „00" oder „FF".

![](https://cdn.xingosoftware.com/elektor/images/fetch/w_451,h_327,c_fit/https:/www.elektormagazine.de/assets/upload/images/26/20171114180626_WebserverConfig.png)

Nach dem Abschicken des Formulars wird die HTTP-Anfrage vom Arduino-Sketch ausgewertet. Die SSID und das Passwort werden in den NVS eingetragen, stehen also auch nach einer Trennung von der Stromversorgung wieder zur Verfugung. Daruber hinaus versucht der ESP32 gleich, sich mit den ubermittelten Zugangsdaten in das Router-Netzwerk einzuloggen. Bei Erfolg leuchtet die RGB-LED kurz gelb und dann grun (stimmen die Zugangsdaten nicht, dann lautet die Farbfolge gelb - rot). Auf der vom ESP32 nun erneut ausgelieferten Konfigurations-Webpage ist die IP-Adresse eingetragen, mit der Sie den ESP32 nun im Router-Netzwerk erreichen konnen (siehe Screenshot). Vorzugsweise machen Sie das mit einem anderen Gerat als dem PC, zum Beispiel einem Smartphone (denn der PC ist ja gerade im ESP32-Netzwerk eingeloggt). Geben Sie die genannte Adresse in einem Browser ein, dann erhalten Sie vom ESP32 eine Webseite, mit der man die rote LED wie gehabt schalten kann.

Nach einem Reset startet der Controller erneut mit der Setup-Funktion. Wenn die richtigen Zugangsdaten im NVS gespeichert sind, wird die RBG-LED nach ein paar Sekunden grun leuchten. Sonst bleibt der Programmablauf aber der gleiche - im vom ESP32 aufgespannten Netzwerk ist die Konfigurations-Webseite wieder uber die Adresse „192.168.4.1" zu erreichen.

## WLAN-Bibliothek

Den Arduino-Sketch finden Sie im Download - er ist nun direkt verwendbar. Wenn Sie den Code mit demjenigen aus der letzten Folge vergleichen, werden Sie sehen, dass ich die WiFi-Funktionalitat in eine kleine Library ausgelagert habe. Meine eigenen Funktionen tragen sprechende Namen wie WiFi_SetBothModesNetworkStationAndAccessPoint(), WiFi_RouterNetworkConnect(…) und WiFi_GetOwnIPAddressInRouterNetwork().

Beide Webseiten verwenden das gleiche Array mit Konfigurationswerten (siehe letzte Folge). Die normale Webpage zum Steuern der LEDs nutzt nur den ersten Wert, die Konfigurations-Webpage die ersten drei Werte. Das macht den Code einfacher. Man hatte naturlich noch mehr Aufwand treiben und jeweils eigene Funktionen fur das Zusammenstellen der Webpages und die Auswertung der Ruckgabe schreiben konnen.

Damit der Webserver entscheiden kann, welche Art von Anfrage vorliegt, wird diesmal uber die HTTP-Anfrage auch ausgewertet, welche Adresse im Browser eingegeben wurde. Im HTTP-Request, der vom Browser zum ESP32 lauft, findet man diese Adresse in der Zeile „Host: …". Die HTTP-Anfrage kann wie in der letzten Folge im seriellen Monitor betrachtet werden:

![](https://cdn.xingosoftware.com/elektor/images/fetch/w_720/https:/www.elektormagazine.de/assets/upload/images/26/20171114180750_WebserverRequestHost.png)

Um den Programmablauf verstandlicher zu lassen, habe ich auch dieses Mal wieder darauf verzichtet, alles zu abstrahieren. Es gibt also noch einiges zu tun. In den nachsten Folgen wollen wir dann auch wieder in die Cloud gehen!
