# Einführung in UART, RS232 und RS485 - Grundlagen

_Captured: 2019-04-20 at 20:34 from [buyzero.de](https://buyzero.de/blogs/news/einfuhrung-in-uart-rs232-und-rs485-grundlagen?omnisendAttributionID=email_campaign_5cbb3dcb8653ed144ceddfbc&omnisendContactID=597763cf47fbc0f7fccab6d8&omnisendScopeID=59776357597ed775e8ab6865_2_15601473&utm_campaign=campaign%3A+RS232_Keyboards+%285cbb3dcb8653ed144ceddfbc%29&utm_medium=email&utm_source=omnisend)_

![Einführung in UART, RS232 und RS485 - Grundlagen](https://cdn.shopify.com/s/files/1/1560/1473/articles/uart_002_putty_2048x.png?v=1555685612)

> _Einleitung_

In diesem Artikel geht es um serielle Kommunikation mit dem Raspberry Pi, inklusive Hintergrunde und Grundlagen. [Ein zweiter Artikel ](https://buyzero.de/blogs/news/praktische-kommunikation-per-uart-und-rs485-am-raspberry-pi)zeigt wie man das ganze praktisch anwendet - UART zu UART, und RS485 als Schnittstelle zwischen zwei Pi's.

Der Raspberry Pi hat dazu zwei spezielle Hardwareeinheiten, die uber die GPIO Pins zuganglich sind: den PL011 UART und den miniUART. Ich erlautere, wie man diese Pins ansteuert und nutzt, sowie wie man einen RS485 Transceiver daran anbindet.

Ich spreche im folgenden vom Empfanger und Sender. Die Kommunikation ist meistens (außer bei Halfduplex RS485) bidirektional, d.h. beide Partner sind jeweils Sender UND Empfanger gleichzeitig. Dabei erfolgt die Kommunikation im sogenannten Vollduplex Modus. Das was ich schreibe gilt also fur beide Kommunikationspartner, jeweils in unterschiedliche Richtung. Es reicht dass wir uns eine Seite der Kommunikation anschauen, da die andere genau gleich lauft (einfach nur in die Gegenrichtung).

# Grundlagen

Bei serieller Kommunikation nutzen wir eine Datenleitung, um seriell Daten zu ubermitteln. Die einzelnen Bits werden nacheinander, also in Serie, ubermittelt. Die alternative dazu ware parallele Kommunikation - wie beispielsweise bei den fruher benutzten Parallelports fur Drucker. Die meisten modernen Schnittstellen sind seriell (bspw. USB, SPI, I2C, SATA, CAN usw. usf. ...), da es bei hoheren Geschwindigkeiten sehr schwierig ware, parallele Pins zu synchronisieren. Serielle Kommunikation bietet auch den Vorteil, dass wir weniger Leitungen benotigen, was die Kabel dunner und gunstiger macht.

In Computern liegen die Daten intern als Bytes vor - 1 Byte besteht aus 8 bit. Mit 1 Byte (8 bits) kann man 256 Zeichen darstellen. Üblicherweise fangt man die Nummerierung bei 0 an, d.h. es gibt Zeichen 0 - 255.

Auf folgender Webseite kann man bspw. die Belegung dieser Zeichen, falls sie als ASCII interpretiert werden einsehen:

Einige davon sind nicht-druckbare Zeichen (bspw. fur neue Zeile, etc.); andere sind Sonderzeichen - bspw. Umlaute, usw. Die Zeichen ab 128 konnen je nach Codepage anders interpretiert werden. Damit kann man beispielsweise kyrillische Zeichen, usw. darstellen (die richtige Codepage vorausgesetzt). Die Codepage bedeutet einfach, man einigt sich darauf, was die Zeichen darstellen.

UTF-8 nutzt hingegen ein bis vier bytes zum Kodieren von einem Zeichen. Es ist zu ASCII abwarts kompatibel: die Zeichen 0-127 entsprechen dem ASCII Encoding.

Was ich damit sagen mochte ist, dass ein Byte, oder 8 bit, die Grundeinheit fur Kommunikation darstellt. Wir ubertragen, speichern und "denken" in Bytes am Computer.

Über die serielle Schnittstelle ubertragen wir bit-weise, aber jeweils 1 byte am Block. Die Aufgabe des UARTs im Raspberry Pi, Mikrocontroller, PC, Arduino oder was auch immer wir einsetzen, ist die Daten aus dem Byte in bits umzuwandeln und nacheinander zu senden. Dabei kommt typischerweise eine Sendeleitung je Richtung zum Einsatz - der UART hat einen Sendeteil (TX fur Transmit), und einen Empfangsteil (RX fur Receive). Die serielle Kommunikation uber einen UART hat im Gegensatz zu SPI und I2C keine zusatzliche Takt/Clockleitung fur den Sendetakt. Auf der Gegenseite empfangt der UART der Gegenseite die einzelnen Bits und setzt sie wieder zu einem Byte zusammen.

UART steht dabei fur Universal Asynchronuous Receiver Transmitter.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/uart_001_framing_grande.png?v=1555685154)

> _Bildquelle: Wikipedia, CC-BY-SA, by IngenieroLoco_

Wie man in dem Bild sieht, werden bit0 bis bit7 (also insgesamt 8 bits) nacheinander ubertragen.

**Aber was ist das start bit und das stop bit? **

Dabei handelt es sich um das sogenannte "Data framing". Die Nutzdaten (unser zu ubertragendes Byte) werden dabei von dem start bit und dem stop bit eingerahmt. Das Start bit ist immer "0" bzw. low, das stop bit immer "1" bzw. high. Das passiert bei jedem einzelnen Byte das wir ubertragen.

Es geht hier darum, dass der Empfanger merken soll, wann gesendet wird, bzw. wann keine Kommunikation erfolgt, und wann die Leitung unterbrochen ist ("break detection"), sowie dass der Empfanger sicher mehrere hintereinander gesendete Zeichen unterscheiden kann und sich nicht desynchronisiert.

**Der Reihe nach:**

Als Relikt aus der Telegrafie ist der Standard-Zustand im Leerlauf ohne Kommunikation beim UART "high", d.h. eine logische 1. Der UART zieht also auf Senderseite den GPIO Pin (TX) des Raspberry Pi's auf +3,3 V. Dieser Pin ist normalerweise mit dem Eingangspin (RX) auf der Empfangerseite verbunden, so dass hier dauerhaft +3,3V anliegen.

Falls die Leitung unterbrochen ist, d.h. am RX-pin der Empfangerseite der Zustand dauerhaft eine logische 0 bzw. GND ist, kann der UART der Empfangerseite das detektieren und dem System melden.

_Hinweis: nur der PL011 UART ist zur "break detection" imstande. Da der miniUART das stop bit **nicht pruft**, wurde er bei kaputter Leitung falschlicherweise 0x00 ausgeben, da er wiederholt low von der "Leitung" liest. Siehe: [https://www.raspberrypi.org/app/uploads/2012/02/BCM2835-ARM-Peripherals.pdf ](https://pi3g.myshopify.com/admin/articles/new)Seite 10-11_

Wenn der Sender ein Byte senden mochte, zieht er die Leitung auf GND - das ist das Start Bit. Danach werden die einzelnen Bits nacheinander ubermittelt (0 als low, d.h. Leitung liegt auf GND und 1 als high, d.h. Leitung auf +3,3V im Falle des Pi). Anschließend zieht der Sender fur das stop bit die Leitung wieder auf high, +3,3V - den Ursprungszustand. Das ganze zusammen nennt man ein **Frame**.

Damit wird außerdem sichergestellt, dass zumindest ein Übergang in der Übertragung passiert. Wenn wir eine lange Reihe von 0en ubertragen wurden, waren das ohne die Start und Stop bits alles Zustande mit 0 V. Dann konnte es leicht sein dass Sender und Empfanger sich desynchronisieren - der Sender wurde beispielsweise 800 Nullen senden, und der Empfanger 798 zahlen, da er nicht genau weiß wann sie jeweils anfangen sondern sich ausschließlich auf seine eingebaute Uhr verlassen muss. Durch das Start und Stop Bit kann der Empfanger sich immer wieder synchronisieren, mindestens ein Übergang der Leitung pro gesendetem Byte ist garantiert.

Da das Senden des Start-Bits jederzeit erfolgen kann, mit beliebigen Pausen zwischen dem letzten Stop bit und dem neuen Start-Bit, wird diese Art der Kommunikation als asynchron bezeichnet.

# Erweiterte Grundlagen

Die gerade besprochene Basis wird jetzt konkretisiert und erweitert.

![PuTTY Serial Line Konfiguration](https://cdn.shopify.com/s/files/1/1560/1473/files/uart_002_putty_grande.png?v=1555685201)

_PuTTY, zum Beispiel, gibt einem die Moglichkeit fur Kommunikation uber die serielle Schnittstelle die notigen Parameter zu setzen. Diese Parameter werden im folgenden erklart._

Es gibt fur serielle Kommunikation uber den UART folgende Parameter, die auf beiden Seiten (Empfanger und Sender) eingestellt werden mussen:

## Geschwindigkeit

Bit Rate in bit/s, bspw. 115200 bit/s - jedes Bit "dauert" dann 8,68 microsec.

## Zahl der Datenbits

In der Einleitung habe ich vom Standard gesprochen, in welchem Fall wir bei jedem gesendeten Frame ein Byte, also 8 bit an Nutzdaten ubertragen. Es gibt jedoch auch andere Moglichkeiten:

  * 5 bit - zum Beispiel als Baudot Code
  * 6 bit - selten genutzt
  * 7 bit - fur das "echte" ASCII (nur mit den ersten 0-127 Zeichen)
  * 8 bit - am weitesten verbreitet
  * 9 bit - selten genutzt

## Zahl der Stop Bits

Die Stop bits werden am Ende jedes Zeichens bzw. als Abschluss des Frames gesendet. Sie erlauben dem Empfanger das Ende zu detektieren, und sich zu synchronisieren. Üblicherweise wird ein Stop Bit verwendet, es gibt aber auch 1 1/2 oder 2 Stop bits. Das war zum Beispiel fur die langsamen elektromechanischen Teleprinter notwendig.

## Parity

Die Parity ist eine einfache Moglichkeit, Fehler bei der Übertragung zu prufen. (Aber nicht korrigieren zu konnen!) Diese Fehler konnen beispielsweise durch außere Storeinwirkungen (elektromagnetische Storungen auf schlecht geschirmten Leitungen) erfolgen, der Empfanger detektiert falschlicherweise eine 1 wo eine 0 sein sollte oder umgekehrt.

Bei der Parity wird dabei die Zahl der logischen 1er im ubertragenen Byte, inklusive des Paritybits gezahlt. Das Paritybit wird so gesetzt (also 0 oder 1) dass die Zahl der logischen 1er **immer entweder gerade oder ungerade ist** (je nachdem ob ODD oder EVEN Parity eingesetzt wird). Falls ein "Bitflip" vorliegt, und eine vorher nicht dagewesene 1 detektiert wird, bzw. eine 1 zu einer 0 geworden ist, kann der Empfanger das also merken. Leider werden zwei bzw. andere gerade Anzahlen an Bitflips nicht gemerkt!

Falls ein Parity Bit vorgesehen wird, wird es zusatzlich nach dem letzten Daten-Bit, und vor dem Stop-Bit im Frame mit ubertragen:

![UART Parity](https://cdn.shopify.com/s/files/1/1560/1473/files/uart_003_parity_stop_etc_large.png?v=1555685246)

> _Bildquelle Wikipedia: CC-BY SA 4.0 User: Chris828 (leicht modifiziert - ohne Spannungen)_

Es gibt folgende Moglichkeiten die Parity zu konfigurieren:

  * None: es wird kein Parity Bit mitgesendet
  * Odd: die Zahl der "logischen 1er" muss ungerade sein
  * Even: die Zahl der "logischen 1er" muss gerade sein
  * Mark: das Parity Bit wird immer auf 1 gesetzt
  * Space: das Parity Bit wird immer auf 0 gesetzt

Mark und Space werden normalerweise nicht eingesetzt, da sie nicht zur Fehlererkennung beitragen.

Unabhangig vom Parity bit konnen wir auf einer hoheren Schicht der Kommunikation weitere Fehlermechanismen, bzw. Mechanismen zur Wiederanforderung der Daten vereinbaren.

## Flow Control

Ebenfalls am besten aus der historischen Sicht zu verstehen ist Flow Control.

Es geht hier darum, dass der Empfanger den Sender informiert, wann er bereit ist fur weitere Daten. Beispielsweise konnte der Empfanger eine gewisse Zeit benotigen, um die Daten zu verarbeiten, oder sein Empfangsbuffer ist voll, und er kann keine weiteren Daten annehmen ohne welche zu verlieren. Zum Beispiel ein Drucker, der Zeile fur Zeile langsam druckt - und nicht nachkommt, wenn die Daten zu schnell geschickt werden.

Es gibt Hardware Flow Control und Software Flow Control, oder Flow Control kann abgeschaltet werden.

Fur Hardware Flow Control werden zwei zusatzliche Steuerleitungen benotigt:

  * RTS = Ready to send
  * CTS = Clear to send

am Pi sind diese zwei zusatzlichen Pins fur beide UARTs (PL011 und miniUART) verfugbar.

Die Idee dahinter ist, dass der Sender RTS auf GND herunterzieht, wenn er senden mochte. Der Empfanger zieht im Gegenzug CTS auf GND, und signalisiert damit dass er bereit ist Daten vom Sender zu akzeptieren.

Moglich ist auch, statt RTS den Pin als RTR zu verwenden. In diesem Fall wird RTS immer als "gesetzt" angenommen (d.h. der Empfanger sollte immer sich empfangsbereit halten). RTR dient jetzt als Indikation fur die Empfangsbereitschaft des Senders (fur die Kommunikation in die Gegenrichtung).

**_Hinweis:_**_ Ich nutze hier das Wort Sender fur den Computer ("DTE, Data Terminal Equipment"), da die Terminologie dem Computer das RTR bzw RTS Signal zuweist, wahrend der Empfanger/ DCE = Data Communication Equipment das CTS Signal zugewiesen hat._

Im einfachsten Kommunikationsfall konnen wir auf Flow Control verzichten.

**Software Flow Control: **

Beim Software Flow Control werden zwei besondere Zeichen vereinbart, bspw. die ASCII Kontrollzeichen XON/XOFF.

Standardmaßig startet der Empfanger im "bereit" Modus, und empfangt Daten. Falls seine Buffer uberfullt zu werden drohen, sendet er dem Sender (auf der anderen Leitung, bei der der Empfanger selbst der Sender ist) ein XOFF Zeichen. Sobald er wieder empfangen kann, sendet er ein XON Zeichen.

Software Flow Control benotigt weniger Kabel, allerdings muss sichergestellt sein, dass die XON/XOFF Zeichen nur fur diesen Zweck verwendet werden, und falls bspw. binare Daten ubertragen werden entsprechend "escaped" werden.

![PuTTY flow control Möglichkeiten](https://cdn.shopify.com/s/files/1/1560/1473/files/uart_004_flow_large.png?v=1555685339)

> _Putty's Flow Control Einstellungsmoglichkeiten._

  * None: es wird kein Flow Control verwendet. Sinnvoll ist daher die Datenrate so zu setzen, dass der Empfanger die Daten sicher empfangen und verarbeiten kann, bzw. mit Pausen von Senderseite zu arbeiten, oder in hoheren Protokollschichten Mechanismen fur erneuten Versand vorzusehen
  * XON/XOFF: Software Flow Control
  * RTS/CTS: Hardware Flow Control mit RTS und CTS
  * DSR/DTR: Hardware Flow Control mit DSR und DTR (nicht Standard, aber bei manchen Geraten) - am Pi **nicht** verfugbar.

# RS232

RS232 ist ein Standard fur serielle Kommunikation zwischen Geraten (bspw. Computer und Modem). Bei diesem Standard wird die elektrische Schnittstelle definiert, und es gibt Übereinkunfte uber die Steckverbinder.

Die entsprechende aktuelle Norm stammt aus dem Jahr 1997 und heißt EIA/TIA-232-F. Das RS von RS-232 steht fur "Recommended Standard". Diese fruher weit verbreitete Schnittstelle wurde u.a. von USB abgelost und wird in moderne Computer nicht mehr eingebaut. Sie ist aber in vielen Geraten als bspw. Diagnoseschnittstelle verbaut, und spielt gerade in der Industrie immer noch eine Rolle.

Wichtig ist, dass der Pi mit seinen UART Pins nicht direkt mit einem RS232 Gerat verbunden werden darf, wegen anderer Signalpegel! Mehr dazu gleich.

Heutzutage gebrauchlich ist bei RS232 der SUB-D 9-pin Stecker, beim Computer mannlich:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/uart_005_subd_large.jpg?v=1555685368)

> _CC-BY-SA von Afrank99, via Wikipedia_

Der Stecker ist auf eine bestimmte Art und Weise belegt - wobei nicht alle Pins geschaltet werden mussen:

![SUB-D Pinout](https://cdn.shopify.com/s/files/1/1560/1473/files/uart_006_subd_pinout_large.png?v=1555685378)

> _CC-0 von En3rGy via Wikipedia_

Wichtig ist, dass die RX und TX Pins bei Sender (Computer) und Empfanger (bspw. Modem oder zweiter Computer) jeweils gekreuzt sein mussen, damit die Daten empfangen werden. Falls zwei Computer miteinander verbunden werden, werden daher sogenannte Nullmodem-Kabel eingesetzt. (Nullmodem, weil kein Modem dazwischen hangt), bei denen die RX und TX Leitungen gekreuzt sind.

Pinbelegung am Computer / Sender 1:

  * 1: DCD (Data Carrier Detect)
  * 2: RxD / RX (Receive Data) - Empfang an Computer 1, Sendelinie fur Computer 2, bzw. Empfanger
  * 3: TxD / TX (Transmit Data) - Senden fur Computer 1, Empfang fur Computer 2 bzw. Empfanger
  * 4: DTR (Data Terminal Ready)
  * 5: GND - Die Signale werden gegen diese Referenz gemessen
  * 6: DSR (Data Set Ready)
  * 7: RTS oder RTR (siehe oben, Hardware Flow Control) - Computer 1 ist bereit Daten zu empfangen
  * 8: CTS (Clear To Send) - Empfanger bzw. Computer 2 ist bereit Daten zu empfangen (Hardware Flow Control, siehe oben)
  * 9: RI (Ring Indicator)

In allen Fallen benotigt werden zur Kommunikation RX, TX und GND.

Die digitalen Signale werden durch den UART erzeugt, mussen allerdings durch einen RS232 Transceiver-Chip auf die richtigen Pegel gebracht werden.

RS232 nutzt dabei fur die Datenleitungen (RX und TX) fur eine logische 1 eine Spannung zwischen -3 V und -15 V, und fur eine logische 0 eine Spannung von +3 V bis +15V.

Signale zwischen -3V und +3V gelten als undefiniert.

Bei den Steuerleitungen (RTS, CTS, etc.) ist der **aktive** Zustand (d.h. asserted) +3V bis +15V und der inaktive -3V bis -15V. Das entspricht einem Ziehen auf "GND" bzw. eine logische 0 des UARTs, entsprechend einer logischen 0 auf den Datenleitungen.

Um diese bereits erwahnten Spannungen am Sender auch bei Spannungsabfallen uber das Kabel, Stecker usw. zu erreichen, muss der Empfanger mindestens eine Spannung von +5V bzw. -5V aufbauen. Üblich sind sogar +12V bzw. -12V.

Solche Spannungen wurden die empfindlichen GPIO Pins am Pi grillen.

Diese sind nur fur 0 - 3.3V ausgelegt.

Es muss daher ein spezieller Chip angeschlossen werden, um Kommunikation uber RS232 zu ermoglichen.

Dazu gibt es entweder spezielle HATs, oder man kann sich einen Chip auf einem Breadboard aufbauen.

Interessanterweise ist es nicht unbedingt notig eine 12 V Spannungsquelle zu haben, da manche Chips bereits integrierte Ladungspumpen haben. Ein solcher Chip ist der MAX3225E. Im sogenannten DIP Package ist dieser Chip auch verfugbar (breadboard freundlich).

Hier ist ein Schaltdiagramm fur den MAX3225E:

![Maxim MAX3225E Diagramm](https://cdn.shopify.com/s/files/1/1560/1473/files/uart_007_maxim_large.png?v=1555685412)

> _Quelle: Datenblatt von Maxim_

Dabei wird T1OUT als TxD Pin auf der RS-232 Seite genutzt, und T2OUT als RTS bzw RTR Signal.

R1IN ist RxD auf RS232 Seite, R2IN CTS.

Auf der Pi Seite werden die Pins entsprechend an die UART Pins beschaltet:

T1IN = TXD & T2IN = RTS (die zwei Sendesignale)

R1OUT = RXD & R2OUT = CTS (die zwei Empfangssignale)

Der Chip kann mit 3,3V versorgt werden und generiert sich die benotigten Spannungen fur die RS232 Schnittstelle mittels Ladungspumpe selbst. Dazu benotigt er externe Kondensatoren als Zwischenspeicher fur die Ladungen. Details siehe Datenblatt von Maxim.

Der Nachteil von RS232 ist dass die Signale nicht differentiell, sondern asymmetrisch ("unbalanced") ubertragen werden. Sie sind auf sogenannte **Gleichtaktstorungen** empfindlich, die beispielsweise durch elektromagnetische Storer auf den Leitungen entstehen konnen. Damit ist unter anderem die maximale Lange der Leitungen limitiert. Mehr Storsicherheit bietet durch differenzielle Signale RS485.

RS232 ist eine Punkt-zu-Punkt Verbindung. Es werden genau zwei Gerate miteinander verbunden.

# RS485

RS-485 auch als EIA/TIA-485 bekannt adressiert einige der Probleme mit RS232 fur eine erhohte Stabilitat der Übertragung. Daher kommt es vor allem in Industrieanwendungen zum Einsatz.

Es kommen differentielle ("balanced") Signale zum Einsatz, und es konnen mehrere Kommunikationspartner auf dem gleichen Netzwerk miteinander sprechen. Fur die differenziellen Signale werden zwei Leitungen benotigt (A und B). Eine weitere Leitung (SC / G / reference pin) als GND-Referenz ist in manchen Fallen ebenso vorhanden.

Die Signalpegel (Spannungen) sind dabei auch niedriger als bei RS-232. Spannungen zwischen -7 und +12 V sind erlaubt, der minimale Spannungslevel um ein Signal zu erkennen liegt fur den Empfanger bei +/- 200 mV. Die tatsachlich auf dem Bus anliegende Spannung hangt typischerweise von der Betriebsspannung des Treibers ab (bspw. 5 V oder 3,3 V beim Pi.)

RS-485 unterstutzt Datenraten von bis zu 10 Mbit/s uber kurze Entfernungen (typischerweise bis zu 12 m), und bei geringeren Datenraten bis zu 1,2 km Entfernung. Als Faustregel gilt: die Geschwindigkeit in bit/s * Lange in m sollte 10^8 nicht uberschreiten, ein 50 m langes Kabel kann also mit maximal 2 Mbit/s betrieben werden. Es sind standardmaßig bis zu 32 Teilnehmer auf der Leitung moglich, bei Einsatz spezieller Transceiver-Bausteine auch mehr.

Auch RS-485 benutzt UARTs als Eingang fur RS-485 Treiber, die das UART Signal in RS-485 konforme differentielle Signale umsetzen. **Dabei ist der binare Zustand der Leitung 1 oder "MARK", wenn die Leitung A **(auch: TX-/RX-/D-)** im Hinblick auf die Leitung B **(auch: TX+/RX+/D+)** negativ ist, und 0 oder "SPACE" wenn B im Hinblick auf A negativ ist.** Der RS-485 Empfanger wandelt das Eingangssignal entsprechend wieder um.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/uart_008_rs485_large.png?v=1555685445)

> _Bild: Wikipedia, CC-BY-SA 3.0 Royvegard_

Das Bild zeigt die Zustande der Leitungen fur asynchrone Kommunikation mit Hilfe von zwei UARTs, an denen auf beiden Seiten RS-485 Transceiver angeschlossen sind. Aus dem Idle Modus ("Mark") wird die Leitung, wie beim UART diskutiert, auf den SPACE Zustand gezogen (eine 0) - das Start Bit. Anschließend erfolgt eine Übertragung von in diesem Fall 8 bits, und das Stop Bit (auch als Mark - der Zustand der logischen 1, wie beim UART). Danach ist die Leitung erneut im Ruhezustand. Durch mindestens einen Übergang pro gesendeten Frame kann sichergestellt werden, dass der Empfanger-UART nicht mit dem Zahlen der empfangenen gleichen Bits durcheinander kommt und verrutscht.

Da die Treiber bei RS-485 selektiv auf die gemeinsame Leitung aufgeschaltet werden konnen (bspw. Pin "Driver Enable" beim Texas Instruments SN65HVD1782 ), ist bidirektionale Kommunikation auch uber nur ein Leitungspaar moglich (sogenannter "Half-Duplex"-Modus bei RS485). Diese zwei Leitungen werden ublicherweise, um Storungen zu minimieren, miteinander verdrillt - "Twisted Pair".

Es gibt auch Implementationen wo zwei Leitungspaare genutzt werden, dabei wird eine Master / Slave Architektur (ein Master, mehrere Slaves) aufgebaut.

RS-485 spezifiziert nur den physikalischen Layer. Es gibt kein Kommunikationsprotokoll und keine Stecker vor, nur ein elektrisches Interface. Einige andere Protokolle, beispielsweise Modbus, und Profibus, basieren auf RS-485 und definieren Stecker, Datenubertragungsformate, etc.

Ein wichtiger Punkt ist bei dem Bus die Topologie. Es werden hier am Hauptbus uber kurze Stichleitungen die einzelnen Teilnehmer angeschlossen. Der Bus sollte zur Vermeidung von Reflexionen an beiden Seiten mit Abschlusswiderstanden versehen werden. Typischerweise werden dazu 120 Ω zwischen A und B geschaltet. Bei sehr kurzen Leitungslangen (z.B. fur Testversuche auf dem Breadboard) oder sehr geringen Datenraten kann man den Abschlusswiderstand weglassen, da die fehlerfreie Datenubertragung durch die Reflexionen in diesen Fallen weniger stark behindert wird.

Die DMX-Schnittstelle, die zur profesionellen Lichtsteuerung in zum Beispiel Theatern benutzt wird, basiert auf RS-485.

[Im zweiten Artikel der sich an diesen anschließt, zeige ich praktische Kommunikation mit UART und RS485.](https://buyzero.de/blogs/news/praktische-kommunikation-per-uart-und-rs485-am-raspberry-pi)

# Further Reading

## 0 Kommentare
