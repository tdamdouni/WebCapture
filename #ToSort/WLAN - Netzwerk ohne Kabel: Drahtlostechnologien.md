# WLAN - Netzwerk ohne Kabel: Drahtlostechnologien

_Captured: 2015-11-06 at 15:46 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/betrieb/netzwerke/wlan-drahtlosnetzwerke-eine-einfuehrung-in-die-technologie.html)_

![Drahtlostechnologien © Depositphotos.com / PirenX](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720-405-Depositphotos-PirenX_b8fd805e20.jpg)

> _Drahtlostechnologien (C) Depositphotos.com / PirenX_

![Drahtlostechnologien © Depositphotos.com / PirenX](fileadmin/_processed_/csm_720-405-Depositphotos-PirenX_b8fd805e20.jpg)Drahtlostechnologien © Depositphotos.com / PirenX

**Ein Wireless Local Area Network (WLAN) ist eine gute Lösung, um Rechner mit wenig Aufwand zu vernetzen. Die meisten Hersteller liefern inzwischen einfach zu verwendende Hard- und Software. Doch wer in dieses Thema tief einsteigen will, der muss einiges wissen. Markus Kammermann erklärt die Interna und Standards drahtloser Funktnetzwerke.**

Jedes drahtlose Funknetzwerk wird in Funkzellen eingeteilt. Eine Funkzelle besteht im Minimum aus einem Sender/Empfänger-Paar und wird als der Raum definiert, in dem alle Sender und Empfänger dieselbe Frequenz und/oder denselben Code benutzen. Je nach Ausdehnung der einzelnen Funkzellen unterscheidet man zwischen Pico-Funkzellen, Mikro-Funkzellen (WLAN) und Makro-Funkzellen (Mobilfunk). 

Die Spread-Spectrum-Technologie („Spreizbandtechnik“) nutzt Frequenzbänder im Bereich von 2,4 GHz (später auch 5 GHz). Dieser Frequenzbereich ist lizenzfrei zugänglich und wird für Forschung und Industrieanwendungen genutzt, daher auch die Bezeichnung „ISM-Band“ (Industrial, Scientific, Medical). Dies zeigt zugleich an, dass die Frequenzen in diesem Bereich von vielen Geräten genutzt werden, was das Einrichten von Netzwerken eindeutig erschweren kann. 

Im ISM-Frequenzband stehen zwischen 60 bis 80 Kanäle mit einer Übertragungsrate von jeweils 1 Mbit/s zur Verfügung. WLANs können zwei unterschiedliche Topologien haben: die Stern-Topologie oder die Netz-Topologie. Bei der Stern-Topologie agiert ein zentraler Sendepunkt (Access Point) als Schaltstelle im LAN, beim Netzsystem sendet jede Station unmittelbar an alle anderen (so genanntes Ad Hoc Netzwerk). 

Bei allen drahtlosen Systemen wird die Gesamtleistung maßgeblich von ihrer physikalischen Umgebung bestimmt. Generell sind bei dem Einsatz von drahtlosen LANs bautechnische und physikalische Gegebenheiten, die die Übertragung und die Ausdehnung der LANs beeinträchtigen, zu berücksichtigen. 

Klassische Stör- und Dämpfungsfelder für Funknetze sind:

  * Andere Access Points in Reichweite (Störung durch Kanalüberlappung)
  * Mikrowellengeräte (Arbeiten im selben Frequenzbereich, aber mit viel mehr Leistung)
  * Halogen (Dämpfung aufgrund der starken Magnetfelder)
  * Wasser, z.B. große Aquarien oder feuchte Wände (mittelstarke Dämpfung)
  * Massive Mauern, Beton und Stahlbetonwände (starke Signaldämpfung)
  * Massive Metallkörper (sehr starke Signaldämpfung)

Bei drahtlosen Netzen besteht darüber hinaus ein direkter Zusammenhang zwischen dem erreichbaren Durchsatz und der maximalen Entfernung zwischen den Knoten: je größer die Entfernung, desto kleiner der erreichbare Durchsatz. Zudem ist die verfügbare Bandbreite immer als Gesamtheit zu verstehen, die durch die Anzahl aktiver Benutzer zu teilen ist! 

## Aller Anfang ist IEEE 802.11

Der IEEE-Arbeitskreis 802.11 definiert seit 1996 Standards für Wireless LAN (WLAN). Der Standard 802.11 definiert die physikalische Schicht (PHY) und die MAC-Schicht (WMAC). Die Funkverfahren nach 802.11 arbeiten im Frequenzbereich zwischen 2,4 GHz und 2,483 GHz mit einer maximalen Sendeleistung von 1 Watt. Typische Vertreter dieser Sendetechnik waren die ersten WLAN-Sets Ende der 90er-Jahre mit 2 Mbit/s Übertragungsraten, etwa das Gigaset von Siemens. 

Als MAC-Protokoll setzt 802.11 auf ein sendergestütztes Verfahren mit Kollisionsvermeidung. Dieses Verfahren nennt sich dann CSMA/CA. Im Unterschied zum Ethernet-Verfahren der Kollisionserkennung wird hier vor dem Versenden der eigentlichen Daten ein RTS-Frame (Request To Send) versandt, das der Empfänger mit einem CTS-Frame (Clear To Send) beantwortet. Stationen in der Nähe nehmen dies zur Kenntnis und wissen, dass sie so lange nicht senden können, wie die Datenübertragung nach diesem Signalaustausch andauert. 

###  Der nächste Entwicklungsschritt: IEEE 802.11b/g

1999 wurde entsprechend der fortschreitenden technischen Möglichkeiten der Standard 802.11b verabschiedet. Dieser brachte neben höheren Geschwindigkeiten von bis zu 11 Mbit/s auch erste Sicherheitsmerkmale wie die WEP-Verschlüsselung mit sich, was verhindern soll, dass andere Stationen die Signale abhören und entschlüsseln können. 

Die USA entwickelte darüber hinaus den Standard 802.11a mit Übertragungsraten von bis zu 54 Mbit/s. Da dieser aber im (von der öffentlichen Hand verwalteten) 5-GHz-Band arbeitet, wurde er in Europa vorerst verboten und erst nach Einrichtung eines zweiten ISM-Bandes im Frequenzbereich von 5,15 GHz bis 5,725 GHz im Jahre 2003 zur Nutzung freigegeben. Parallel dazu erarbeiteten die Europäer einen zu 802.11b kompatiblen, aber schnelleren Standard, der sich letztlich 802.11g nannte und bis Ende 2009 den aktuellen Standard für drahtlose Netzwerke bildete. Erst danach wurde er offiziell abgelöst. IEEE 802.11h ist die „Harmonisierung“ des Standards 802.11a für europäische WLAN-Anwendungen. 

Die gesetzlich (!) zulässige effektive Strahlungsleistung beträgt in Deutschland für 802.11 b/g/n-Netzwerke 100 mW (2,4 GHz-Bereich) bzw. bei 802.11a/n-Netzwerken 500 mW (5,4 GHz-Bereich). Dies lässt eine durchschnittliche Reichweite von 30 bis 100 Meter Reichweite auf freier Fläche erwarten. Im Vergleich dazu: Ein Mobiltelefon hat eine Strahlungsleistung von 1000 bis 2000 mW. 

Um bestehende lokale Netzwerke durch ein drahtloses Netz zu erweitern oder um größere drahtlose Netze zu bauen, bedient man sich der sogenannten Infrastrukturmethode. Hier vermittelt eine Basisstation (Access Point) zwischen den Endgeräten und dient als Sende- und Empfangsstation. Jede Funkzelle benötigt mindestens einen Access Point. 

Der Access Point sendet seine Identifikation (SSID) zusammen mit der MAC-Adresse als Management-Frame regelmäßig aus. Das Frame wird auch Beacon-Frame genannt (frei übersetzt Signalfeuer). Der Access Point kann zudem für einen gültigen Verbindungsaufbau zusätzliche Sicherheitsmerkmale - wie eine Verschlüsselung oder Authentifizierung vom sich anmeldenden Client - anfordern. Dadurch werden infrastrukturgestützte Netzwerke sicherer als Ad-hoc-Netzwerke. Durch das Verwenden mehrerer Access Points mittels Repeating-Funktion kann die Reichweite zudem beträchtlich vergrößert werden. 

###  Der Standard IEEE 802.11n

Der Standard IEEE 802.11n nutzt als zentrales Element zur Datenübertragung eine Technik, welche Multiple Input Multiple Output (MIMO) genannt wird. Diese setzt zwei bis maximal vier Antennen zur Übertragung ein. Dies ermöglicht es, einen Funkkanal im selben Frequenzbereich räumlich mehrfach zu nutzen und somit eine parallele Datenübertragung zu erlauben. Dadurch sollen in bestehenden Netzen die bisherigen Datenraten über größere Distanzen erreicht oder aber auf gleicher Distanz eine höhere Datenrate als bisher ermöglicht werden. Das Netzwerk kann dabei entweder im gemischten Modus (802.11a/b/g + n) oder im reinen 802.11n-Modus betrieben werden (sogenannter Greenfield-Modus). Der Standard 802.11n unterstützt sowohl die bisherigen 2.4 GHz-Frequenzen als auch das 5 GHz-ISM-Band. 802.11n ist abwärtskompatibel zu älteren Standards, aber nur wenn der gemischte Modus aktiv eingestellt ist. Zudem können 802.11n-Netzwerke neben den bisherigen 20-MHz-Datenkanälen auch 40 MHz breite Frequenzbänder nutzen.  
   
Dies ist ein Unterschied zu den bisherigen 802.11er-Standards, welche nur 20-MHz breite Frequenzbänder nutzten. Die Anzahl der verfügbaren Subkanäle steigt damit von 52 auf 108, was etwas mehr als eine reine Verdoppelung darstellt. Ein Datenstrom (Stream) bringt es damit auf eine maximale Bruttoleistung von 150 Mbit/s. Durch die Kombination mittels MIMO können maximal 4 solcher Streams die 600 Mbit/s erbringen – wie gesagt als Bruttoleistung, nicht als Datenübertragungsrate. Geräte, welche nur einen Stream unterstützen, werden demgegenüber als N-Lite-Geräte verkauft. 

Es gibt aber auch Fragen und Hindernisse in Bezug auf die anstehenden 802.11n-Migrationen:

  * Das neue Modulationsverfahren kann zur Verknappung der verfügbaren Kanäle im 2,4 Gigahertz-Band führen, da mehr Kanäle verwendet werden.
  * Mit 802.11n steigt der Datendurchsatz bis auf das Zehnfache – verkraften die WLAN-Switches diesen Verkehrszuwachs?
  * Schnelle Access Points erfordern Gigabit-Ethernet-Anschlüsse im Backbone, damit die Übertragungen nicht im verdrahteten Netz stecken bleiben.

Hier eine Übersicht der wichtigsten Eckwerte für drahtlose Standards:

Standard Frequenzen Übertragungsrate Kanäle

802.11a

5,15 – 5,825 GHz   
(nicht durchgehend)

54 Mbit/s

In den USA 19, alle überlappungsfrei nutzbar

802.11b

2,4 – 2,484 GHz

11 Mbit/s

13 (Europa) oder 11 (USA). Es sind maximal 3 Kanäle überlappungsfrei nutzbar.

802.11g

2,4 – 2,484 GHz

54 Mbit/s

13 (Europa) oder 11 (USA). Maximal 3 Kanäle überlappungsfrei nutzbar.

802.11h

5,15 – 5,825 GHz   
(nicht durchgehend)

54 Mbit/s

19 (Europa) oder 24 (USA). Überlappungsfrei

802.11n

2,4 – 2,484 GHz / 5,15 – 5,825 GHz   
(nicht durchgehend)

bis zu 600 Mbit/s

13 (Europa) oder 11 (USA). Maximal 4 Kanäle überlappungsfrei nutzbar.

**Tabelle 1: WLAN-Standards im Vergleich**

Mit „überlappungsfrei“ wird der Umstand bezeichnet, dass drei Kanäle parallel betrieben werden können, ohne dass sie sich stören. Theoretisch kann auf jedem Kanal, der freigegeben ist, ein WLAN betrieben werden. Da jeder Kanal für sich aber 20 MHz beansprucht (oder auch 40 MHz – siehe oben), sind nur drei Kanäle gleichzeitig in diesem Frequenzband ohne Störung nutzbar. In den USA sind das die Kanäle 1, 6 und 11, in Europa und Japan die Kanäle 1, 7 und 13. 

Wichtig: Obwohl die Standards international sind, gelten für etliche Bereiche wie beispielsweise die präzisen Frequenzbänder oder die zur Verfügung stehende Kanäle in Europa, Asien und den USA unterschiedliche Werte, die zum Teil sogar national gesetzlich geregelt werden. In Deutschland ist dafür die Bundesnetzagentur zuständig. Auf der Internetseite www.bundesnetzagentur.de können Sie die national zulässigen Werte nachlesen! 

Weitere Entwicklungen in diesem 802.11-Standard sind etwa 802.11p, W.A.V.E. genannt (Wireless Access in Vehicular Environments) im 5,9-GHz-Band. Diese Entwicklung dient der Datenkommunikation zwischen Fahrzeugen bis 200 km/h und auf Distanzen bis 1000 Meter. Es zeichnet sich durch eine extrem kurze Zugriffszeit (4-50 ms) aus, aber auch dadurch, dass nur kleine Datenmengen übertragen werden können. Der Standard ist noch nicht verabschiedet. 

Eine weitere interessante Entwicklung ist 802.11s. Hierbei handelt es sich um ein drahtloses Maschennetzwerk (Wireless Mesh Network). Das Ziel ist eine sich selber konfigurierende Multi-Hop-Technologie mit WLAN-fähigen Geräten als Relaisstationen (Hops) bis zum nächsten Access Point. 

### Was bringt 802.11ac?

Wie gerade erwähnt, bleibt die Entwicklung auch bei IEEE 802.11n nicht stehen. Der nächste Standard 802.11ac befindet sich zu Beginn im Jahr 2014 noch im „Draft“, also im Entwurfsstatus. 

Die wesentlichen Merkmale hierzu sind:

  * Nur noch 5-GHz-Band als Trägerfrequenz
  * 80 MHz und 160 MHz breite Kanäle (statt 20 MHz und 40 MHz bisher)
  * Bis zu acht MIMO-Antennen (anstelle von bisher vier)
  * MIMO kann über die gleichen Kanäle auch mehrere Benutzer gleichzeitig unterstützen
  * Abwärtskompatibilität zu 802.11n-5-GHz-Standard

Die erreichbaren Übertragungsraten liegen zumindest in der Theorie bei bis zu 433 Mbps pro Antenne bei Nutzung von 80-MHZ-Bändern und dem doppelten von 866 Mbps bei der Nutzung von 160-MHZ-Bändern, was dann in einer maximalen Übertragungsrate von bis zu 6, 93 Gbps bei acht Antennen enden könnte. 

Erste Hersteller sind mit Draft-Geräten auch schon auf dem Markt (Broadcom, Qualcom, Buffalo, D-Link, Netgear etc.), allerdings wird dort noch nicht mit so hohen Zahlen argumentiert, sondern nach dem Motto „wesentlich schneller als 802.11n“ – wohl wissend, dass man sich eben erst im Draft-Stadium befindet, und die Hersteller haben auch gewisse Lehren aus dem letzten Durcheinander bei der 802.11n-Entwicklung gezogen. 

## WLAN und Sicherheit

Das IEEE-Komitee hat bei der Entwicklung der WLAN-Sicherheitsstandards ursprünglich kein ‚perfektes’ Verschlüsselungsverfahren mit eingeplant. Man nahm an, dass die Verschlüsselung auf Anwendungsebene (z.B. elektronischer Zahlungsverkehr) realisiert würde und es darüber hinaus nicht notwendig ist, weitere Verschlüsselungen zu definieren. Mit dem WEP-Standard (Wired Equivalent Privacy) kam daher lediglich ein – aus heutiger Sicht – unsicherer Sicherheitsmechanismus zum Tragen, welches „Sicherheit wie bei einem Kabelnetz“ bieten wollte. Diese Technik benutzt entweder einen 40 Bit, einen 64 Bit oder in letzter Ausführung einen 128 Bit statischen Schlüssel, um die Kommunikation zu verschlüsseln. Bald zeigte sich, dass dieser Schlüssel relativ einfach geknackt werden kann und daher zumindest aus heutiger Sicht als nicht mehr sicher gilt. 

Erst nach lauter Kritik an diesem Verfahren entwickelte die IEEE unter dem Standard 802.11i einen besseren Sicherheitsstandard. Da dies aber zu viel Zeit in Anspruch nahm, hatten die Hersteller zwischenzeitlich den Pseudo-Standard Wi-Fi Protected Access (WPA) entwickelt. Mit dem Standard 802.11i von 2004, der mittlerweile im Standard 802.11-2007 aufgegangen ist, wurde das WEP-Verfahren durch neue Verfahren zur Erhöhung der Sicherheit abgelöst. Die wesentlichen Neuerungen von WPA sowie dem später folgenden Standard 802.11i waren:

  * WPA: WPA mit Temporal Key Integrity Protocol (TKIP) als Ersatz für WEP (allerdings immer noch auf der Verschlüsselung RC4 basierend)
  * 802.11i: CCMP (Counter Mode with Cipher Block Chaining Message Authentication Code Protocol) zur Behebung der Schwächen von TKIP. Daher auch die Bezeichnung WPA2. CCMP basiert im Unterschied zu TKIP auf der AES-Verschlüsselung.
  * Ein standardisiertes Handshake-Verfahren zwischen Client und Access Point zur Ermittlung/Übertragung der Sitzungsschlüssel
  * Ein vereinfachtes Verfahren zur Ermittlung des Master Secrets, das ohne einen RADIUS-Server auskommt

Das WPA-Protokoll ersetzt die statischen Codes von WEP durch dynamische Schlüssel, die schwerer zu manipulieren sind. Je länger der benutzte Schlüssel ist und je häufiger er in kurzen Abständen gewechselt wird, desto zuverlässiger der Schutz. Hier kommt allerdings nach wie vor eine symmetrische Verschlüsselung zum Einsatz. 

Zwischen WPA und WPA2 ergibt sich durch die Verwendung von CCMP anstelle von TKIP immer noch ein großer Unterschied in der Sicherheit zugunsten von WPA2. 

Der wie gesagt erst nach WPA verabschiedete Standard 802.11i wurde danach in WPA2 implementiert. Damit kann die Wireless-Sicherheit in zwei verschiedenen Funktionsmodi betrieben werden.

  * **WPA Personal:** Der Modus „WPA Personal“ ermöglicht die Einrichtung einer gesicherten Infrastruktur basierend auf WPA, allerdings ohne die Einrichtung eines Authentifizierungsservers. WPA Personal beruht auf der Verwendung eines gemeinsamen Schlüssels namens PSK für Pre-Shared Key, der im Access Point und den Clientstationen eingegeben wird. Im Gegensatz zu WEP ist es nicht notwendig, einen Schlüssel mit einer vordefinierten Länge zu verwenden. WPA erlaubt die Verwendung einer passphrase (Geheimphrase), die durch einen Hash-Algorithmus in einen PSK übersetzt wird. Je länger diese ist, umso sicherer ist der generierte Schlüssel.
  * **WPA Enterprise:** Der Enterprise-Modus verlangt die Verwendung einer 802.1x-Authentifizierungsinfrastruktur, die auf der Verwendung eines Authentifizierungsservers basiert, normalerweise ein RADIUS-Server und ein Netzwerk-Controller (der Access Point).

Auch WPA/WPA2 ist nicht frei von Schwachstellen: Die Verschlüsselung von WPA2 wurde aber bisher noch nicht geknackt. Es gibt aber auch eine Ausnahme: Wenn ein zu einfacher Pre-Shared Key verwendet wird, kann auch WPA2 gehackt werden. Hier liegt die Verantwortung daher primär beim Administrator, der diese Schlüssel einrichtet. PSKs sollten nicht unter 28 Zeichen lang sein. Da dieses Passwort nur während der Einrichtung des WLANs und beim Hinzufügen weiterer Clients eingegeben werden muss, nicht aber bei jedem Anmelden eines Gerätes, spielt diese Länge für den administrativen Aufwand nur eine untergeordnete Rolle, für die Sicherheit gegenüber Angriffen aber eine große. 

## Aufbau des drahtlosen Netzwerks

Bei der Einrichtung geht es zunächst um die Frage der geeigneten Geräte und Standorte. Abhängig vom Standort kann der Sendebereich der Access Points stark variieren, die bereits erwähnten Hindernisse baulicher oder geografischer Natur sind darum im Vorfeld zu berücksichtigen. Und nicht zu vergessen sind die Endgeräte, denn ein Notebook empfängt nicht nur Signale, sondern hat auch eine Antenne, um Daten zu senden – was für den Access Point gilt, gilt daher im Wesentlichen auch für die (mobilen) Endgeräte. 

Ein wesentlicher Aspekt für die Sendeleistung ist die Art und Ausrichtung der Antennen. Deren Leistung hängt von mehreren Faktoren ab:

  * **Der Standort:** Im optimalen Fall sehen sich alle Antennen eines WLAN, zumindest erhöht dies deren Leistungsfähigkeit. Zumindest sollten Wände und Hindernisse weiter entfernt sein von den Antennen, um die Ausbreitung des Signals nicht zu unterbrechen (Grundsatz des Richtfunks: Halte die erste Fresnelzone frei).
  * **Der Wirkungsgrad:** Wie viel der eingespeisten elektrischen Energie die Antenne wirklich in Sendestrahlung umwandelt. Hier gilt: Gute Antennen sind mindestens eine halbe Wellenlänge lang – bei einer Sendefrequenz von 2,4 GHz und einer Wellenlänge von daher rund 12 cm heißt das: keine Antennen unter sechs Zentimeter. Stichwort: WLAN-Stecker im Miniformat oder USB-WLAN-Sticks.
  * **Verbindungskabel:** Gerade bei Access Points werden gerne Verbindungskabel zur Ausrichtung der Antennen eingesetzt: je länger das Kabel ist, desto größer ist die Dämpfung (also der Signalverlust). Wenn Sie also anstelle der im Access Point eingebauten 3-dBi-Antenne eine externe 7-dBi-Antenne anschließen und diese mit einem 2 Meter langen Kabel verbinden, ist der eigentliche Gewinn schon um rund die Hälfte (ca. 2 dBi) verloren. Dabei gilt: je dünner das Kabel, desto größer der Verlust.
  * **Latenzprobleme** gibt es in erster Linie dann, wenn Funkstörungen vorliegen (benachbartes WLAN, drahtlose Sender, Bluetooth, Reflektionen). Hier helfen die Kontrolle der Umgebung, allenfalls ein Kanalwechsel oder ein Umstellen des AccessPoints.
  * **Die Konzentration der Strahlung:** Eine Rundstrahlantenne sendet in alle Richtungen, eine Richtantenne dagegen kann bei gleicher Sendeleistung eine wesentlich höhere Reichweite erzielen, weil die Strahlung in eine bestimmte Richtung gelenkt wird (sogenannter Antennengewinn). Dafür ist die Abdeckung bei einer Rundstrahlantenne größer. Hier ist also der Einsatzzweck gefragt, um zu bestimmen, welche Antenne die richtige ist.
  * **Typ der Antenne:** Gebräuchliche Typen für WLAN sind Rundstrahlantennen, Richtantennen (Yagi) oder BiQuad-Antennen. Der Antennengewinn dieser Typen ist sehr unterschiedlich. Er kommt dadurch zustande, dass die Strahlung auf einen bestimmten Strahlungswinkel konzentriert wird. Jeweils 3 dBi entsprechen dabei einer Verdoppelung der Leistung, immer bezogen auf den sogenannten Isostrahler, einer nur theoretisch existierenden omnidirektionalen Antenne mit 360 Grad Rundstrahlung. Eine doppelte Leistung erhält man also dadurch, dass man die Richtung halbiert. Eine vierfache Leistung mündet also in einen maximalen Sendebereich von 90 Grad Ausdehnung usw. mehr an Energie kommt ja nirgendwo her, es ist schließlich kein elektronischer Verstärker in die Antenne eingebaut.

![Abbildung. 1:  WLAN-Antennen für den Innen- und Außeneinsatz. Von links nach rechts folgende WLAN-Antennen: OMNI, Yagi-Direktional, Dipol, Richtantenne. © Markus Kammermann](fileadmin/_processed_/csm_Kammermann-WLAN-Antennen-Innen-und-Aussen_3fd4afafa0.png)Abbildung. 1: WLAN-Antennen für den Innen- und Außeneinsatz. Von links nach rechts folgende WLAN-Antennen: OMNI, Yagi-Direktional, Dipol, Richtantenne. © Markus Kammermann

Die Sendeleistung dürfen Sie dabei nicht über das gesetzliche Maß von je nach Frequenzband und Landesbestimmung hinaus verstärken. Zusätzliche Antennengewinne müssen also mitunter durch Reduktion der Sendeleistung wieder ausgeglichen werden, um die zulässige Feldstärke von 20 dBm nicht zu überschreiten. Dazu bieten gute Access Points entsprechende Einstellungsmöglichkeiten an. 

Die Empfängerempfindlichkeit ist gesetzlich nicht begrenzt, aber physikalisch bei etwa -97 dBm. Ein gutes bzw. „stabiles“ Signal erhalten Sie bis etwa einem Leistungspegel von -75 dBm. Darunter ist zwar eine Verbindungsherstellung bis zum Grenzwert der Empfindlichkeit möglich, die eigentliche Datenübertragungsrate sinkt aber gegen 0 Mbps ab oder es kommt immer wieder zu Unterbrechungen.

![Abbildung 2: Gemessener Leistungspegel eines WLAN-Signals \(Quelle: inSSIDer von Metageek\)](fileadmin/_processed_/csm_Kammermann-WLAN-Sendeleistung_426723709a.png)Abbildung 2: Gemessener Leistungspegel eines WLAN-Signals (Quelle: inSSIDer von Metageek)

Wenn Sie ein Feld abdecken möchten, das größer ist, als es ein einzelner Access Point abdecken kann, empfiehlt sich der Einsatz von WLAN-Repeatern. Diese können das Signal entsprechend in verschiedene Richtungen verstärken und damit die Abdeckung vergrößern. 

Auszug aus: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[CompTIA Network+](http://www.it-fachportal.de/shop/buch/CompTIA%20Network+/detail.html,b152220), MITP-Verlag, Nachdruck der 5. Auflage, 2014, Autor: Markus Kammermann ISBN: 978-3-8266-9437-0

![nach Oben](fileadmin/templates/wr/images/LinkToTop.png)
