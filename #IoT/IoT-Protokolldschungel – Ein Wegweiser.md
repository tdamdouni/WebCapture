# IoT-Protokolldschungel – Ein Wegweiser

_Captured: 2015-11-20 at 17:52 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html)_

![Jedes Protokoll hat seine Vor- und Nachteile. © depositphoto.com / nmedia](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720-Depositphotos_35902947_m-2015_nmedia_643034fc16.jpg)© depositphoto.com / nmedia

**Selten wurde ein Thema so heiß in der IT-Branche diskutiert wie das Thema "Internet of Things" (IoT). Das Internet der Dinge birgt sowohl Risiken als auch Chancen. Entwickler stehen vor einer Vielzahl an Entscheidungen um sichere und effiziente Software für IoT-Anwendungsfälle zu entwickeln. Eine der vielen Fragen ist: "Welches Protokoll soll für die IoT-Kommunikation im Projekt verwendet werden?" Eine erste Recherche zeigt dann, dass es eine Vielzahl von Möglichkeiten gibt: HTTP, CoAP, XMPP und MQTT. Dieser Artikel ist ein Wegweiser durch den IoT-Protokolldschungel und gibt einen Überblick über die populärsten Protokolle und deren Anwendungsfälle.**

Jedes hier diskutierte Protokoll hat seine Vor- und Nachteile und es gibt leider keine Lösung, die für jeden Anwendungsfall optimal geeignet ist. Folgende Fragen sollten bei der Wahl eines IoT-Protokolls je nach Anwendungsfall u. a. berücksichtigt werden:

  * Ist das Protokoll skalierbar?
  * Ist das Protokoll für mobile Anwendungen und/oder ressourcenbeschränkte Geräte geeignet?
  * Kann eine Echtzeitkommunikation mit dem Protokoll abgebildet werden?
  * Ist der Protokolloverhead klein?
  * Gibt es Client- und Serverimplementierungen in hoher Qualität?
  * Ist Sicherheit im Protokoll mit berücksichtigt?

## HTTP

HTTP ist das Urgestein unter den Protokollen. Seit 1991 wird das auf dem Request/Response-Pattern basierende Protokoll für das World Wide Web eingesetzt, um Webseiten auszuliefern. Seit geraumer Zeit genießen HTTP RESTful APIs eine hohe Popularität, um Daten an Clients auszuliefern. Für Request/Response-basierte IoT-Kommunikation ist HTTP nach wie vor die erste Wahl von vielen Entwicklern und eine hohe Zahl an Frameworks für viele Programmiersprachen erlauben eine schnelle Entwicklung mittels HTTP. Das Protokoll-Urgestein kommt jedoch mit einem sehr hohen Protokolloverhead daher, da es komplett textbasiert ist und bei jedem Request sogenannte HTTP-Header übertragen werden. Für Anwendungsfälle, bei denen die Menge der übertragenen Daten eine Rolle spielt (z. B. wenn mobile Netzwerke im Spiel sind), sollte HTTP daher nicht immer gleich die erste Wahl sein. Das Request/Response-Pattern erlaubt eine 1/1-Kommunikation, nicht jedoch eine 1/N-Kommunikation und ist daher nicht geeignet, wenn eine Nachricht an viele Empfänger gleichzeitig versendet werden soll. Die Kommunikation ist bei HTTP immer unidirektional und es gibt keinen Weg, um echte Push-Kommunikation skalierbar und nur mit HTTP-Bordmitteln abzubilden (ohne z. B. Websockets zu benutzen). Die kommende HTTP/2-Version adressiert einige dieser Probleme, aktuell gibt es noch wenig Server- und Clientimplementierungen für HTTP/2 und deshalb auch noch wenig Erfahrungswerte. 

**Vorteile:**

  * Bibliotheken für fast alle Programmiersprachen vorhanden.
  * Einfach zu erlernen.

**Nachteile:**

  * Viel Protokolloverhead.
  * Keine Server-Push-Kommunikation nativ möglich (nur mittels Long-Polling, Server Sent Events oder Websockets).
  * Keine Möglichkeit, 1/N-Kommunikation abzubilden.

**Typische Anwendungsfälle:**

  * REST-APIs.
  * Downloads von großen Datenmengen an den Client (z. B. Firmware Update).
  * IoT-Devices mit sehr guter und stabiler Internetanbindung, welche keine sekunden-/ minutenaktuellen Daten vom Server benötigt.

## CoAP

Das Constrained Application Protocol (CoAP) ist ein auf UDP basiertes IoT-Protokoll, welches oft als das "HTTP für IoT" bezeichnet wird. CoAP implementiert das Request/Response-Pattern und ist im Gegensatz zu HTTP dafür optimiert, sehr effizient zu sein, weshalb das Protokoll inklusive aller Header binär ist. Es ist ohne weiteres möglich, REST-APIs mit CoAP zu realisieren, da CoAP die gleichen Verben wie HTTP kennt und sogar HTTP-/CoAP-Proxies existieren. CoAP besitzt noch weitere Protokoll-Erweiterungen, wie z. B. "Observe", welches einen serverseitigen Push bei Änderung von Ressourcen definiert. Die größte Herausforderung mit CoAP ist, dass das Protokoll auf UDP basiert, also keine bidirektionale, stehende Verbindung  – wie etwa bei TCP – vom Client initiiert werden kann, was speziell bei Anwendungsfällen mit NATing ein Problem ist. CoAP wird in der Praxis hauptsächlich für Wireless Sensor Networks benutzt, hierbei spielen NATs im Gegensatz zur Kommunikation über das Internet meist keine Rolle. 

**Vorteile:**

  * Sehr effizient
  * Leichter Umstieg von HTTP auf CoAP möglich

**Nachteile:**

  * Herausforderungen bei der Network Address Translation (NAT) durch UDP
  * Wenig Client- und Server-Implementierungen im Vergleich zu den anderen Protokollen. 

**Typische Anwendungsfälle:**

  * Wireless Sensor Networks

## XMPP

Das Extensible Messaging and Presence Protocol (XMPP), früher auch Jabber genannt, ist ein Kommunikationsprotokoll, welches vor allem bei Instant Messengern als Chat-Protokoll verwendet wird. Es basiert auf XML und ist erweiterbar. XMPP wird vergleichsweise selten als IoT-Protokoll eingesetzt, was unter anderem an dem großen Protokolloverhead, welcher durch die XML-Basis entsteht, liegt. Große Popularität hat das Protokoll unter anderem durch den Einsatz bei Google und Facebook bei deren Chat-Applikationen erreicht. Beide Firmen haben jedoch mittlerweile den Support von XMPP eingestellt, Facebook benutzt nun MQTT für den Facebook-Chat ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[1]](betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html#c13751). 

Es gibt eine Fülle an XMPP-Servern und -Clients, jedoch mit stark unterschiedlichen Features, da die meisten Features als Erweiterungen nachrüstbar sind und daher nicht immer interoperabel sind. Es gibt Erweiterungen, welche speziell für IoT-Anwendungsfälle konzipiert wurden, zum aktuellen Zeitpunkt werden diese aber noch von wenigen Servern und Clients unterstützt. Eine Liste der Erweiterungen für IoT kann unter diesem Link ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[2]](betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html#c13751) eingesehen werden. 

**Vorteile:**

  * Clients sind in vielen Programmiersprachen verfügbar.
  * Sehr viele Features, viele davon sind für Instant Messenger-Anwendungsfälle optimiert.

**Nachteile:**

  * Hoher Protokolloverhead durch XMPP.
  * Hohe Fragmentierung bei den Server- und Client-Features.

**Typische Anwendungsfälle:**

  * Instant Messenger / Chats.

## MQTT

MQTT ist ein extrem effizientes IoT-Protokoll mit wenig Protokolloverhead und wurde speziell für Machine-to-Machine-Anwendungsfälle (M2M) konzipiert. Das Protokoll wurde 1999 entwickelt und ist seit 2011 offen verfügbar. Mittlerweile wird MQTT beim Standardisierungskommittee "OASIS" weiterentwickelt. MQTT implementiert das Publish/Subscribe-Pattern und glänzt durch eine hohe Skalierbarkeit und echte Push-Kommunikation. Neben vielen quelloffenen Implementierungen (z. B. mosquitto ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[3]](betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html#c13751)) gibt es auch für den kommerziellen Einsatz konzipierte Server (z. B. den in Deutschland entwickelten HiveMQ ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[4]](betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html#c13751)). Client-Implementierungen sind in allen gängigen Programmiersprachen verfügbar, z. B. unter dem Eclipse-Projekt "Paho" ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[5]](betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html#c13751). Das Protokoll wurde entwickelt, um eine zuverlässige Übertragung von Nachrichten über unzuverlässige Netzwerke (z. B. Mobile Netzwerke) zu ermöglichen und ist selbst auf Geräten mit wenig Speicher und Rechenleistung mit hoher Performance leicht einzusetzen. 

Ein Einführungsartikel in MQTT kann man bei Informatik Aktuell  ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[6]](betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html#c13751) nachlesen. 

**Vorteile:**

  * Minimaler Protokolloverhead.
  * Hochskalierbar bis zu mehreren hunderttausenden Clients pro Server.
  * Viele Protokollfeatures die speziell für IoT-Anwendungsfälle entwickelt wurden.
  * Für ressourcenbeschränke Geräte geeignet.
  * Clientimplementierungen sind für alle gängigen Programmiersprachen verfügbar.

**Nachteile:**

  * Reine Request/Response-Architekturen sind mit MQTT nur mit zusätzlichem Aufwand umsetzbar.

**Typische Anwendungsfälle:**

  * Connected Car.
  * M2M Kommunikation.
  * Instant Messenger / Chat.

## Fazit

![Abb.1: Google Trends vom 02.11.2015. © Google Trends](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_iot_protokkolle_google_trends_1154aa3b04.png)Abb.1: Google Trends vom 02.11.2015. © Google Trends

Ein erster Überblick über die Popularität der einzelnen hier diskutierten Protokolle findet sich in der Grafik von Google Trends vom 02.11.2015 (Abb.1). Die tagesaktuelle Popularität bei Google-Suchen kann unter diesem Link ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[7]](http://www.informatik-aktuell.de/betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html#c13751) eingesehen werden. 

Jedes der hier vorgestellten Protokolle hat seine Anwendungsfälle und es gibt keine "One-Size-Fits-All"-Lösung. Jedes Protokoll hat Vorteile und Herausforderungen, daher muss für jeden Anwendungsfall genau definiert werden, welche Anforderungen man an ein IoT-Protokoll stellt. Sowohl HTTP, CoAP, XMPP als auch MQTT sollten daher als ein weiteres Tool für die Toolbox von Entwicklern betrachtet werden und es muss genau abgewägt werden, für welches Protokoll man sich schlussendlich entscheidet. Leser, die sich tiefer mit der Materie beschäftigen wollen, finden u. a. hier ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[8]](http://www.informatik-aktuell.de/betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html#c13751), hier ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[9]](http://www.informatik-aktuell.de/betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html#c13751) und hier ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[10]](http://www.informatik-aktuell.de/betrieb/netzwerke/iot-protokolldschungel-ein-wegweiser.html#c13751) weiterführende Informationen.

Quellen

  1. Facebook: ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Building Facebook Messenger    ](https://www.facebook.com/notes/facebook-engineering/building-facebook-messenger/10150259350998920)
  2. Github: ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[XMPP-IoT   ](https://github.com/joachimlindborg/XMPP-IoT)
  3. ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Mosquitto](http://mosquitto.org/)
  4. ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[HiveMQ](http://www.hivemq.com)
  5. Eclipse-Projekt ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)"[Paho"](http://www.eclipse.org/paho/)
  6. Informatik Aktuell: ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[Internet der Dinge: Leichtgewichtiges Messaging](betrieb/netzwerke/internet-der-dinge-protokolle-verfahren-und-integration-von-mqtt.html)
  7. Google Trends: ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Tagesaktuelles Interesse an den Protokollen](https://www.google.de/trends/explore#q=mqtt%2C%20coap%2C%20xmpp)
  8. Christian Götz: ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[How Do ‘Things’ Talk?    ](http://de.slideshare.net/goetzchr/how-dothingstalkio-texpo2014)
  9. Toby Jaffey: ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[MQTT and CoAP, IoT Protocols](http://www.eclipse.org/community/eclipse_newsletter/2014/february/article2.php)
  10. Paolo Patierno: ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[IoT protocols landscape](http://www.slideshare.net/paolopat/io-t-protocols-landscape)
