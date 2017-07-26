# Controller Area Network

_Captured: 2015-10-12 at 13:38 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Controller_Area_Network)_

Der **CAN-Bus** (**C**ontroller **A**rea **N**etwork) ist ein serielles [Bussystem](https://de.m.wikipedia.org/wiki/Bus_\(Datenverarbeitung\)) und gehort zu den [Feldbussen](https://de.m.wikipedia.org/wiki/Feldbus).

Um die [Kabelbaume](https://de.m.wikipedia.org/wiki/Kabelbaum) in Fahrzeugen (bis zu 2 km) zu reduzieren und dadurch Gewicht zu sparen, wurde der CAN-Bus 1983 von [Bosch](https://de.m.wikipedia.org/wiki/Robert_Bosch_\(Unternehmen\)) fur die Vernetzung von [Steuergeraten](https://de.m.wikipedia.org/wiki/Steuerger%C3%A4t) in Automobilen entwickelt und 1987 zusammen mit [Intel](https://de.m.wikipedia.org/wiki/Intel) vorgestellt. CAN ist als [ISO](https://de.m.wikipedia.org/wiki/ISO) 11898 international standardisiert und definiert die Layer 1 (physikalische Schicht) und 2 (Datensicherungsschicht) im [ISO/OSI-Referenzmodell](https://de.m.wikipedia.org/wiki/ISO/OSI-Referenzmodell). Die beiden gangigsten Realisierungen der physikalischen Schichten nach ISO 11898-2 (Highspeed-CAN) und ISO 11898-3 (Lowspeed-CAN) unterscheiden sich außer in der Datenrate in weiteren Eigenschaften und sind deshalb nicht zueinander kompatibel.

  * [Funktion](https://de.m.wikipedia.org/wiki/Controller_Area_Network)
  * [Hohere Protokolle](https://de.m.wikipedia.org/wiki/Controller_Area_Network)

Der CAN-Bus arbeitet nach dem [CSMA/CR](https://de.m.wikipedia.org/wiki/Carrier_Sense_Multiple_Access/Collision_Resolution)[[1]](https://de.m.wikipedia.org/wiki/Controller_Area_Network) (**C**arrier **S**ense **M**ultiple **A**ccess / **C**ollision **R**esolution)-Verfahren (nicht zu verwechseln mit [CSMA/CD](https://de.m.wikipedia.org/wiki/CSMA/CD) wie bei [Ethernet](https://de.m.wikipedia.org/wiki/Ethernet)). In der Literatur wird das Verfahren aus historischen Grunden auch [CSMA/CA](https://de.m.wikipedia.org/wiki/Carrier_Sense_Multiple_Access/Collision_Avoidance) genannt. Dabei werden Kollisionen beim Buszugriff durch die [Arbitrierung](https://de.m.wikipedia.org/wiki/Arbitrierung) oder Bit-Arbitrierung aufgelost (siehe unten). Die Daten sind [NRZ](https://de.m.wikipedia.org/wiki/Non_Return_to_Zero)-codiert. Des Weiteren kommt zur Datensicherung die [Zyklische Redundanzprufung](https://de.m.wikipedia.org/wiki/Zyklische_Redundanzpr%C3%BCfung) (engl. CRC fur Cyclic Redundancy Check) zum Einsatz. Zur fortlaufenden Synchronisierung der Busteilnehmer wird [Bitstopfen](https://de.m.wikipedia.org/wiki/Bitstopfen) (_bit stuffing_) verwendet (siehe unten). Der Bus ist entweder mit Kupferleitungen oder uber Glasfaser ausgefuhrt. Der CAN-Bus arbeitet nach dem „Multi-Master-Prinzip": Mehrere gleichberechtigte Steuergerate (= Busteilnehmer) sind durch eine topologische Anordnung (siehe unten) miteinander verbunden.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/Canbus_levels.svg/220px-Canbus_levels.svg.png)

> _Spannungspegel im Highspeed-CAN-Bus_

Im Falle von Kupferleitungen arbeitet der CAN-Bus bei hoheren Datenraten (s. u.) mit Differenzsignalen. Die Differenzsignale werden normalerweise mit zwei oder drei Leitungen ausgefuhrt: CAN_HIGH, CAN_LOW und optional CAN_GND (Masse). CAN_LOW enthalt den komplementaren Pegel von CAN_HIGH gegenuber einer Ruhespannung von etwa 2,5 V beim Highspeed-CAN. Die Differenzspannung bei einem dominanten Bit betragt mindestens 2 V. Dadurch konnen [Gleichtaktstorungen](https://de.m.wikipedia.org/wiki/Gleichtaktst%C3%B6rung) unterdruckt werden, da die Differenz gleich bleibt.

Beim Lowspeed-CAN betragen die Ruhespannungen und rezessiven Spannungen 5 V und 0 V, die dominanten Spannungen ca. 1,4 V (CAN_LOW) und 3,6 V (CAN_HIGH). Bei Ausfall einer der beiden Leitungen kann die Spannung der anderen Leitung gegen Masse ausgewertet werden. Bei langsameren Bussen (‚Komfort-Bus' z. B. zur Betatigung von Elementen durch den Benutzer) kann ein Eindrahtsystem mit der Karosserie als Masse deshalb reichen. Praktisch wird es meistens doch als Zweidrahtsystem ausgefuhrt, verwendet aber im Fehlerfall eines Aderbruchs den Eindrahtbetrieb als Ruckfallebene, um den Betrieb weiterfuhren zu konnen, das nennt sich dann „Limp-Home-Modus" („nach-Hause-humpeln-Modus"). Um Storungen zu vermeiden, wird es grundsatzlich [verdrillt](https://de.m.wikipedia.org/wiki/Verdrillung).

Die Übertragung der Daten erfolgt so, dass ein Bit - je nach Zustand - entweder _dominant_ oder _rezessiv_ auf den Busleitungen wirkt. Ein dominantes uberschreibt dabei ein rezessives Bit.

Es wird zwischen einem Highspeed- und einem Lowspeed-Bus unterschieden. Bei einem Highspeed-Bus betragt die maximale Datenubertragungsrate 1 Mbit/s, bei Lowspeed 125 kbit/s.

Die maximale (theoretische) Leitungslange betragt z. B. bei 1 Mbit/s 40 m, bei 500 kbit/s sind 100 m moglich und bei 125 kbit/s 500 m. Diese Maximalwerte beruhen darauf, dass die Zeit, die ein Signal am Bus anliegt (Bitzeit, bit/Sekunde), umso kurzer ist, je hoher die Übertragungsrate ist. Mit zunehmender Leitungslange steigt jedoch die Zeit, die ein Signal braucht, bis es am anderen Ende des Busses angekommen ist (Ausbreitungsgeschwindigkeit). Zu beachten ist, dass sich das Signal nicht nur ausbreitet, sondern auch innerhalb der Signalzeit der Empfanger auf den Sender reagieren muss (siehe ACK). Der Sender muss wiederum die eventuelle Buspegelanderung des/der Empfanger mitbekommen (siehe auch Arbitrierung). Deshalb ist die max. Leitungslange etwas komplexer zu berechnen. Es mussen Verzogerungszeiten auf der Leitung, des Transceivers (Sender und Empfanger), des Controllers (Sender und Empfanger), Oszillatortoleranzen und der gesetzte Abtastzeitpunkt (Sender und Empfanger) berucksichtigt werden. Die Formel zur Berechnung und nahere Informationen sind der Literatur entnehmbar.

Als Busmedium werden nach [ISO](https://de.m.wikipedia.org/wiki/International_Organization_for_Standardization) 11898-2 (High-Speed Medium Access Unit) von 1993 [Twisted-Pair-Kabel](https://de.m.wikipedia.org/wiki/Twisted-Pair-Kabel) mit einem [Wellenwiderstand](https://de.m.wikipedia.org/wiki/Wellenimpedanz) von 108-132 [Ohm](https://de.m.wikipedia.org/wiki/Ohm_\(Einheit\)) empfohlen. In der derzeit gultigen Ausgabe der ISO 11898-2 aus dem Jahr 2003 ist die Toleranz mit 95-140 Ohm spezifiziert (Abschnitt 7.5.1, Tabelle 9).

Die maximale Teilnehmeranzahl auf physikalischer Ebene hangt von den verwendeten Bustreiberbausteinen (Transceiver, physikalische Anschaltung an den Bus) ab. Mit gangigen Bausteinen sind 32, 64 oder bis zu 110 (mit Einschrankungen bis zu 128) Teilnehmer pro Leitung moglich (Erweiterungsmoglichkeit uber Repeater oder Bridge).

![](http://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/CAN-Bus_Elektrische_Zweidrahtleitung.svg/330px-CAN-Bus_Elektrische_Zweidrahtleitung.svg.png)

> _Linearer CAN-Bus_

Das CAN-Netzwerk wird als Linienstruktur aufgebaut. [Stichleitungen](https://de.m.wikipedia.org/wiki/Stichleitung) sind in eingeschranktem Umfang zulassig. Auch ein sternformiger Bus (z. B. bei der Zentralverriegelung im Auto) ist moglich. Diese Varianten haben allerdings im Vergleich zum linienformigen Bus Nachteile:

  * Der sternformige Bus wird meist von einem Zentralrechner gesteuert, da diesen alle Informationen passieren mussen, mit der Folge, dass bei einem Ausfall des Zentralrechners keine Informationen weitergeleitet werden konnen. Beim Ausfall eines einzelnen Steuergerats funktioniert der Bus weiter.
  * Fur Stichleitungen und sternformige Busarchitektur ist der [Leitungswellenwiderstand](https://de.m.wikipedia.org/wiki/Leitungswellenwiderstand) etwas aufwandiger zu bestimmen. Die Anzahl der Stichleitungen und ihre Gesamtlange wird durch empirische Richtformeln abgeschatzt. Der lineare Bus hat den Vorteil, dass alle Steuergerate parallel an einer zentralen Leitung liegen. Nur wenn diese ausfallt, funktioniert der Bus nicht mehr. Diese Topologie wird haufig in Kraftfahrzeugen eingesetzt.

An jedem Leitungsende sollte sich ein Abschlusswiderstand von 120 Ohm befinden. Fur einen einzelnen CAN-Bus-Teilnehmer an einer Stichleitung wirkt dies genauso wie ein einzelner 60-Ohm-Widerstand, der am Ort der Abzweigung eingefugt ist. Dieser Wert ist die zentrale Impedanz einer Sternarchitektur.

Der Objekt-Identifier kennzeichnet den Inhalt der Nachricht, nicht das Gerat. Zum Beispiel kann in einem Messsystem den Parametern Temperatur, Spannung und Druck jeweils ein eigener Identifier zugewiesen sein. Es konnen mehrere Parameter unter einem Identifier vereint sein solange die Summe der Daten die maximal mogliche Lange des Datenfeldes nicht uberschreitet. Die Empfanger entscheiden anhand des Identifiers, ob die Nachricht fur sie relevant ist oder nicht.

Zudem dient der Objekt-Identifier auch der Priorisierung der Nachrichten.

Die Spezifikation definiert zwei verschiedene Identifier-Formate:

  * 11-Bit-Identifier, auch „Base frame format" genannt (CAN 2.0A)
  * 29-Bit-Identifier, auch „Extended frame format" genannt (CAN 2.0B).

Ein Teilnehmer kann Empfanger und Sender von Nachrichten mit beliebig vielen Identifiern sein, aber umgekehrt darf es zu einem Identifier immer nur maximal einen Sender geben, damit die [Arbitrierung](https://de.m.wikipedia.org/wiki/Arbitrierung) funktioniert.

Der 29-Bit-Identifier ist in erster Linie fur das Umfeld von Nutzfahrzeugen, Schiffen, Schienenfahrzeugen und Landmaschinen definiert. Der CAN-Standard fordert, dass eine Implementierung das „Base frame format" akzeptieren muss, dagegen das „Extended frame format" akzeptieren kann, es aber zumindest tolerieren muss.

Die Liste der Objekt-Identifier einschließlich Sender und Empfanger ist Bestandteil der sog. _Kommunikationsmatrix_ oder _K-Matrix_, die außer fur den direkt an der Steuergerateentwicklung beteiligtem Personenkreis als besonders vertrauliches Dokument fur niemanden einsehbar ist.

Der Buszugriff wird verlustfrei mittels der bitweisen [Arbitrierung](https://de.m.wikipedia.org/wiki/Arbitrierung) auf Basis der Identifier der zu sendenden Nachrichten aufgelost. Dazu uberwacht jeder Sender den Bus, wahrend er gerade den Identifier sendet. Senden zwei Teilnehmer gleichzeitig, so uberschreibt das erste dominante Bit eines der beiden das entsprechend rezessive des anderen, was dieser erkennt und seinen Übertragungsversuch beendet. Verwenden beide Teilnehmer den gleichen Identifier, wird nicht sofort ein Error-Frame erzeugt (siehe Frame-Aufbau), sondern erst bei einer Kollision innerhalb der restlichen Bits, was durch die Arbitrierung ausgeschlossen sein sollte. Daher empfiehlt der Standard, dass ein Identifier auch nur von maximal einem Teilnehmer verwendet werden soll.

Durch dieses Verfahren ist auch eine Hierarchie der Nachrichten untereinander gegeben. Die Nachricht mit dem niedrigsten Identifier darf immer ubertragen werden. Fur die Übertragung von zeitkritischen Nachrichten kann also ein Identifier hoher Prioritat (= niedrige ID, z. B. 0x001; 0x000 fur Netzmanagement - NMT) vergeben werden, um ihnen so Vorrang bei der Übertragung zu gewahren. Dennoch kann selbst bei hochprioren Botschaften der Sendezeitpunkt zeitlich nicht genau vorher bestimmt werden, da gerade in Übertragung befindliche Nachrichten nicht unterbrochen werden konnen und den Startzeitpunkt einer Sendung so bis zur maximalen Nachrichtenlange verzogern konnen ([nichtdeterministisches Verhalten](https://de.m.wikipedia.org/wiki/Determinismus_\(Algorithmus\))). Lediglich die maximale Sendeverzogerung fur die hochstpriore Nachricht kann bei bekannter maximaler Nachrichtenlange errechnet werden. Fur niederpriore Nachrichten ist im Allgemeinen keine Aussage uber den Sendezeitpunkt moglich.

Sollte ein Teilnehmer kontinuierlich Nachrichten mit einer hohen Prioritat versenden, kann dies zur Blockade des Busses fuhren, da die Nachrichten der anderen Teilnehmer jeweils die Arbitrierung verlieren. Dieses Verhalten wird als [Babbling idiot](https://de.m.wikipedia.org/wiki/Babbling_idiot) beschrieben. Sollte dieses Verhalten auf einer Fehlfunktion basieren, kann es nur durch zusatzliche Hardware - sogenannte Buswachter ([Bus Guardians](https://de.m.wikipedia.org/w/index.php?title=Bus_Guardian&action=edit&redlink=1)) - gelost werden. [[2]](https://de.m.wikipedia.org/wiki/Controller_Area_Network)

![](http://upload.wikimedia.org/wikipedia/commons/thumb/5/5e/CAN-Bus-frame_in_base_format_without_stuffbits.svg/709px-CAN-Bus-frame_in_base_format_without_stuffbits.svg.png)

> _CAN-Daten-Frame mit elektrischen Pegeln ohne Stuffbits_

![](http://upload.wikimedia.org/wikipedia/commons/thumb/6/6f/CAN_telegramm_2.0A.svg/575px-CAN_telegramm_2.0A.svg.png)

> _CAN-Datentelegramm im Base Frame Format_

![](http://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Extended_can-dataframe.png/575px-Extended_can-dataframe.png)

> _CAN-Datentelegramm im Extended Frame Format_

Die Kommunikation erfolgt mit Telegrammen. Innerhalb eines Telegramms gibt es Steuerbits und Nutzbits (roter Bereich). Der genormte Aufbau eines solchen Telegrammrahmens wird als Frame bezeichnet.

Es gibt vier verschiedene Arten von Frames:

  * Daten-Frame, dient dem Transport von bis zu 8 Byte an Daten
  * Remote-Frame, dient der Anforderung eines Daten-Frames von einem anderen Teilnehmer
  * Error-Frame, signalisiert allen Teilnehmern eine erkannte Fehlerbedingung in der Übertragung
  * Overload-Frame, dient als Zwangspause zwischen Daten- und Remote-Frames

Ein Daten-Frame ist logisch wie folgt aufgebaut:

  * Start of Frame (SOF) = ein dominantes Bit
  * Arbitrierungsfeld, bestehend aus einem Identifier-Segment (11 Bit oder 29+2 Bit) plus einem RTR-Bit (Remote Transmission Request, siehe unten)
  * Kontrollfeld (CTRL) = 6 Bit 
    * Identifier Extension (IDE) = 1 Bit
    * reserved = 1 Bit
    * Data Length Code (DLC) = 4bit (Anzahl der Bytes im Datenfeld)
  * Datenfeld (DATA) = 0-64 Bit (in Einheiten von 8 Bit)
  * Prufsummenfeld ([CRC](https://de.m.wikipedia.org/wiki/Zyklische_Redundanzpr%C3%BCfung)) = 16 Bit (15 Bit CRC plus einem rezessiven CRC-Delimiter-Bit)
  * Bestatigungsfeld (ACK) 2 Bit, bestehend aus einem ACK-Slot (siehe untenstehende Erlauterung) plus einem rezessiven ACK-Delimiter
  * End of Frame (EOF) 7 Bit (rezessiv)
  * Intermission (IFS - Intermission Frame Space) = 3 Bit (= min. Anzahl der Bits, die aufeinanderfolgende Botschaften trennt)

Ein gesetztes RTR-Bit (Remote Transmission Request) kennzeichnet einen Remote-Frame (rezessiv). Mit Hilfe eines Remote-Frames kann ein Teilnehmer einen anderen auffordern, seine Daten zu senden.

Im Falle eines „Extended Identifiers" (siehe oben) wird das RTR-Bit durch das SRR-Bit (Substitute Remote Request) ersetzt und ebenfalls rezessiv gesendet. In diesem Fall wird das nachfolgende IDE-Bit ebenfalls rezessiv gesendet, wodurch ein „Extended Identifier" signalisiert wird. Im Anschluss werden die restlichen 18 Bit des Identifiers und anschließend das eigentliche RTR-Bit gesendet. Das IDE-Bit zahlt dabei logisch zum „Arbitrierungsfeld", wobei das Kontrollfeld aber weiterhin aus 6 Bit besteht.

Die Datenlange muss entsprechend der zu erwartenden Datenlange gesetzt werden (Fehlerquelle: Viele Entwickler setzen die Datenlange = 0 - dies ist falsch; ebenso sind CAN-Controller am Markt, welche RTR-Frames nur mit der Datenlange 0 senden konnen). Der Objektidentifier ist derselbe wie der der angeforderten Nachricht.

Der Error Frame besteht aus zwei Feldern:

Das erste Feld wird bestimmt durch die Überlagerung von ERROR FLAGS, die von den verschiedenen Stationen erzeugt werden konnen.  
Das folgende Feld ist der ERROR DELIMITER (8 rezessive Bits) .

Es gibt zwei Typen von Error Flags:

    6 dominante Bits, gesendet von einem Knoten, der einen Fehler im Netzwerk entdeckt hat und im Fehler-Status „error active" ist.
    6 rezessive Bits, gesendet von einem Knoten, der einen Fehler im Netzwerk entdeckt hat und im Fehler-Status „error passive" ist.

Der Overload Frame ist eine Zwangspause zwischen Daten- und Remote-Frames.  
Er beinhaltet zwei Felder: Overload Flag und Overload Delimiter.

Es gibt zwei Arten von Überlastung, die zur Generierung des Overload-Flag fuhren:

  1. Die Elektronik des Empfangers erfordert eine Verzogerung der Übertragung des nachsten Datenframes oder Remoteframes (bspw. aufgrund eines vollen Empfangspuffers).
  2. Erkennung eines dominanten Bits auf dem Bus wahrend einer Übertragungspause des eigenen Sendevorganges.

Ein Overload-Frame, verursacht aufgrund des ersten Falls, darf nur im ersten Bitintervall einer erwarteten Sendepause erzeugt werden, wahrend ein Overload-Frame, bedingt durch Fall 2, einen Takt nach der Erkennung des dominanten Bits gesendet wird.

  * Das Overload-Flag besteht aus sechs dominanten Bits.
  * Die allgemeine Form korrespondiert zu der des Active-Error-Flags: Die Form des Overload-Flags zerstort die festgelegte Übertragungsform, da das Bitstuffing verletzt wird. Als Konsequenz erkennen alle anderen Gerate ebenfalls die Überlastung und generieren selber wiederum auch ein Overload-Flag.
  * Der Overload-Delimiter besteht aus acht rezessiven Bits und entspricht der Form des Error-Delimiters.

Der Acknowledge-Slot wird verwendet, um den Empfang eines korrekten CAN-Frames zu quittieren. Jeder Empfanger, der keinen Fehler feststellen konnte, setzt einen dominanten Pegel an der Stelle des ACK-Slots und uberschreibt somit den rezessiven Pegel des Senders. Im Falle einer negativen Quittung (rezessiver Pegel) muss der fehlererkennende Knoten nach dem ACK-Delimiter ein Error-Flag auflegen, damit erstens der Sender vom Übertragungsfehler in Kenntnis gesetzt wird und zweitens um netzweite Datenkonsistenz sicherzustellen. Wird der rezessive Pegel von einem Empfanger durch einen dominanten uberschrieben, kann der Absender jedoch nicht davon ausgehen, dass das Telegramm von allen anderen Empfangern erhalten wurde.

![CAN-Frame mit Pegeln mit Stuffbits.svg](http://upload.wikimedia.org/wikipedia/commons/thumb/9/97/CAN-Frame_mit_Pegeln_mit_Stuffbits.svg/761px-CAN-Frame_mit_Pegeln_mit_Stuffbits.svg.png)

> _[CAN-Frame mit Pegeln mit Stuffbits.svg](https://de.m.wikipedia.org/wiki/Datei:CAN-Frame_mit_Pegeln_mit_Stuffbits.svg)_

Bitfolgen mit mehr als funf gleichen Bits werden im CAN-Protokoll fur Steuerungszwecke z.B. „End of Frame" benutzt. Es durfen also innerhalb des CAN-Frames nicht mehr als funf Bits mit dem gleichen Pegel hintereinander vorkommen. Um dies zu verhindern, wird nach funf Bits mit dem gleichen Pegel ein Bit mit dem inversen Pegel eingefugt. Dieses Bit nennt man „Stopf-Bit" oder „stuff bit". Das Bild zeigt den gleichen CAN-Frame vor und nach dem Einfugen von Stopf-Bits. Die Stopfbits sind lila eingefarbt. [Bitstopfen](https://de.m.wikipedia.org/wiki/Bitstopfen) (_bit stuffing_) kann die physikalische Lange eines Frames vergroßern. Bit stuffing wirkt auf Start of frame (SOF) bis einschließlich Prufsummenfeld (CRC) von Daten- sowie Remote-Frames und dient der Nachsynchronisation der Teilnehmer innerhalb eines Frames.

Ein Bit wird in sogenannten Zeitquanten unterteilt. Sie entsprechen einem Vielfachen des Controllertaktes. In jedem Zeitquantum wird nur einmal abgetastet. Eine Flanke wird erkannt, wenn der Abtastwert vor dem Zeitquantum einen anderen Wert hat als der Wert danach. Die Nachsynchronisierung synchronisiert somit nur auf ein Zeitquantum und nicht auf die Flanke.

Erkennt ein Empfanger eine Fehlerbedingung, sendet er einen Error-Frame und veranlasst so alle Teilnehmer, den Frame zu verwerfen. Sollten andere Teilnehmer diese Fehlerbedingung erkannt haben, senden sie ihrerseits direkt im Anschluss ein weiteres Error-Frame. Damit wird eine weitere Sicherheitsfunktion des CAN-Protokolls moglich. Um zu vermeiden, dass einzelne Teilnehmer durch irrtumlich erkannte Fehlerbedingungen dauerhaft den Nachrichtentransport blockieren, enthalt jeder Teilnehmer Fehlerzahler. Diese Zahler erlauben nach den Regeln der Spezifikation, einen fehlerhaft arbeitenden Teilnehmer in zwei Stufen des Betriebszustands vom Bus zu trennen, wenn er wiederholt Fehler erkennt, welche andere Teilnehmer nicht erkennen oder wiederholt fehlerhafte Frames versendet. Die Zustande nennen sich _error active_ (normal), _error passive_ (Teilnehmer darf nur noch passive - das heißt rezessive - Error-Frames senden) und _bus off_ (Teilnehmer darf nicht mehr senden).

Der Sender wiederholt nach dem Error-Frame seine Datenubertragung. Auch der Sender kann durch die zuvor erwahnten Fehlerzahler vom Bus getrennt werden, wenn die Datenubertragung dauerhaft fehlschlagt. Verschiedene Fehlerfalle fuhren zu einer unterschiedlich großen Erhohung des Fehlerzahlers.

  * ISO 11898-1:2003 Road vehicles -- Controller area network -- Part 1: Data link layer and physical signalling
  * ISO 11898-2:2003 Road vehicles -- Controller area network -- Part 2: High-speed medium access unit
  * ISO 11898-3:2006 Road vehicles -- Controller area network -- Part 3: Low-speed, fault-tolerant, medium dependent interface
  * ISO 11898-4:2004 Road vehicles -- Controller area network -- Part 4: Time-triggered communication
  * ISO 11898-5:2007 Road vehicles -- Controller area network -- Part 5: High-speed medium access unit with low-power mode
  * ISO/NP 11898-6 Road vehicles -- Controller area network -- Part 6: High-speed medium access unit with selective wake-up functionality

2012 wurde von [Bosch](https://de.m.wikipedia.org/wiki/Robert_Bosch_GmbH) ein Vorschlag zur Erhohung der verfugbaren Bandbreite namens CAN FD (Flexible Data Rate) vorgestellt.[[3]](https://de.m.wikipedia.org/wiki/Controller_Area_Network) Dies wird durch Verkurzung der Bit-Zeiten in der Datenphase und Vergroßerung des Datenfeldes auf bis zu 64 Byte erreicht. Insgesamt verspricht man sich zurzeit durch das „improved CAN"[[4]](https://de.m.wikipedia.org/wiki/Controller_Area_Network) genannte Verfahren einen bis zu 8-fach hoheren Datendurchsatz. Durch Änderungen der CRC-Sicherung erhoht sich die Datensicherheit gegenuber dem Classic CAN auf eine [Hammingdistanz](https://de.m.wikipedia.org/wiki/Hamming-Abstand) von 6.

CAN-Protokolle haben sich in verschiedenen, vor allem sicherheitsrelevanten Bereichen etabliert, bei denen es auf hohe Datensicherheit ankommt. Beispiele:

  * [Automobilindustrie](https://de.m.wikipedia.org/wiki/Automobilindustrie) (Vernetzung unterschiedlicher Steuergerate, Sensoreinheiten und Multimediaeinheiten)
  * [Automatisierungstechnik](https://de.m.wikipedia.org/wiki/Automatisierungstechnik) (zeitkritische Sensoren im Feld, Überwachungstechnische Einrichtungen)
  * [Aufzugsanlagen](https://de.m.wikipedia.org/wiki/Aufzugsanlage) (Vernetzung der Steuerung mit verschiedenen Sensoren, Aktoren und Aufzugsanlagen untereinander innerhalb einer Aufzugsgruppe)
  * [Beschallungsanlage](https://de.m.wikipedia.org/wiki/Beschallungsanlage) (wird fur die Steuerung von digitalen Endstufen verwendet)
  * [Schiffbau](https://de.m.wikipedia.org/wiki/Schiffbau) (Die [DGzRS](https://de.m.wikipedia.org/wiki/DGzRS) lasst in die neue Generation ihrer Seenotrettungskreuzer Bus-Systeme einbauen.)

[ISO 15765-2](https://de.m.wikipedia.org/wiki/ISO_15765-2), auch kurz **ISO-TP** ermoglicht den Transport von Botschaften, deren Lange die maximal 8 Bytes Nutzdaten eines CAN-[Frames](https://de.m.wikipedia.org/wiki/Datenframe) uberschreiten. Im [OSI-Modell](https://de.m.wikipedia.org/wiki/OSI-Modell) deckt es die Schichten 3 (Network Layer) und 4 (Transport Layer) ab und kann bis zu 4095 Bytes Nutzdaten pro Telegramm transportieren. ISO-TP segmentiert langere Botschaften auf mehrere Frames und erganzt die Datenpakete um Metadaten, die eine Interpretation der einzelnen Frames durch den Empfanger ermoglichen.

_[CANopen](https://de.m.wikipedia.org/wiki/CANopen)_ ist ein auf CAN basierendes [Schicht-7-Kommunikationsprotokoll](https://de.m.wikipedia.org/wiki/OSI-Modell), welches anfanglich in der [Automatisierungstechnik](https://de.m.wikipedia.org/wiki/Automatisierungstechnik) verwendet wurde, mittlerweile aber vorwiegend in Embedded Systemen eingesetzt wird.

CANopen wurde vorwiegend von deutschen klein- und mittelstandischen Firmen initiiert und im Rahmen eines [ESPRIT](https://de.m.wikipedia.org/w/index.php?title=ESPRIT_\(Forschung\)&action=edit&redlink=1)-Projektes unter Leitung von Bosch erarbeitet. Seit 1995 wird es von der _[CAN in Automation](https://de.m.wikipedia.org/wiki/CAN_in_Automation)_ gepflegt und ist inzwischen als Europaische Norm EN 50325-4 standardisiert. Der Einsatz erfolgt vorwiegend in Europa, gefolgt von Asien.

_[DeviceNet](https://de.m.wikipedia.org/wiki/DeviceNet)_ ist ein auf CAN basierendes [Schicht-7-Kommunikationsprotokoll](https://de.m.wikipedia.org/wiki/OSI-Modell), welches hauptsachlich in der [Automatisierungstechnik](https://de.m.wikipedia.org/wiki/Automatisierungstechnik) verwendet wird.

DeviceNet ist vorwiegend in Amerika verbreitet. Es wurde von [Allen-Bradley](https://de.m.wikipedia.org/wiki/Allen-Bradley) (gehort zu [Rockwell Automation](https://de.m.wikipedia.org/wiki/Rockwell_Automation)) entwickelt und spater als offener Standard an die _ODVA_ (Open DeviceNet Vendor Association) ubergeben.

[J1939](https://de.m.wikipedia.org/wiki/J1939) ist ein auf CAN basierendes Protokoll im Nutzfahrzeugbereich. Es wird von der [Society of Automotive Engineers](https://de.m.wikipedia.org/wiki/Society_of_Automotive_Engineers) (SAE) gepflegt. Eine Einfuhrung in J1939 findet sich in _Application Note Introduction J1939_[[6]](https://de.m.wikipedia.org/wiki/Controller_Area_Network)

[NMEA 2000](https://de.m.wikipedia.org/wiki/NMEA_2000) ist eine Erweiterung von SAE J1939 fur den maritimen Bereich. Das Protokoll der [NMEA-Organisation](https://de.m.wikipedia.org/wiki/National_Marine_Electronics_Association) breitet sich zunehmend aus. Vorganger ist [NMEA 0183](https://de.m.wikipedia.org/wiki/NMEA_0183).

In der Landwirtschaft und Kommunaltechnik kommt der [ISOBUS](https://de.m.wikipedia.org/wiki/ISOBUS) (ISO11783), der eine Erweiterung des J1939 darstellt, zur Steuerung und Überwachung von Anbaugeraten zum Einsatz.

Eine Arbeitsgruppe der _[CAN in Automation](https://de.m.wikipedia.org/wiki/CAN_in_Automation)_, die CANopen Special Interest Group (SIG) „Municipal Vehicles", entwickelt das CANopen-Anwendungsprofil fur Abfallsammelfahrzeuge ([CleANopen](https://de.m.wikipedia.org/w/index.php?title=CleANopen&action=edit&redlink=1)).

Eine in 2001 gegrundete Arbeitsgruppe der _[CAN in Automation](https://de.m.wikipedia.org/wiki/CAN_in_Automation)_, die CANopen Special Interest Group (SIG) „Lift Control", entwickelt das CANopen-Anwendungsprofil (CANopen CiA-417) fur [Aufzuge](https://de.m.wikipedia.org/wiki/Aufzugsanlage) ([CANopen-Lift](https://de.m.wikipedia.org/w/index.php?title=CANopen-Lift&action=edit&redlink=1)). Die erste Version wurde im Sommer 2003 veroffentlicht. Die Version 2.0 wurde als Draft-Standard verabschiedet und steht frei zur Verfugung. Aktuell (2013) wird an der Version 2.2 gearbeitet.

**[SafetyBUS p](https://de.m.wikipedia.org/wiki/SafetyBUS_p)** ist ein auf CAN basierendes sicheres Kommunikationsprotokoll, welches hauptsachlich in der [Automatisierungstechnik](https://de.m.wikipedia.org/wiki/Automatisierungstechnik) zur Übertragung sicherheitsgerichteter Daten verwendet wird. Alle Busteilnehmer sind 2- oder sogar 3-kanalig aufgebaut und prufen die Datenintegritat. Das Übertragungsmedium selbst ist nicht sicher, die Sicherheit wird durch das _SafetyBUS p_ eigene Datenprotokoll erreicht. Der _SafetyBUS p_ kann bis [SIL3](https://de.m.wikipedia.org/wiki/Sicherheitsanforderungsstufe) eingesetzt werden.

_Time-Triggered Communication on CAN_ setzt auf dem CAN-Bus auf und ermoglicht uber hohere Protokollebenen eine Echtzeitsteuerung.

[CANaerospace](https://de.m.wikipedia.org/wiki/CANaerospace) ist ein [Open-Source](https://de.m.wikipedia.org/wiki/Open_Source)-Kommunikationsprotokoll, welches 1998 insbesondere fur den Einsatz in der Luftfahrt mit ihren besonderen Zuverlassigkeits- und Leistungsanforderungen konzipiert wurde. Im Jahr 2000 hat die amerikanische [NASA](https://de.m.wikipedia.org/wiki/NASA) CANaerospace als eigenen Standard ubernommen. CANaerospace wird in zahlreichen Forschungsflugzeugen weltweit eingesetzt und hat sich als De-facto-Standard in der militarischen Flugsimulationstechnik etabliert.

[ARINC 825](https://de.m.wikipedia.org/wiki/ARINC_825) ist ein internationaler Luftfahrt-Kommunikationsstandard, welcher in einer Technischen Arbeitsgruppe (bestehend aus mehreren [Luftfahrtunternehmen](https://de.m.wikipedia.org/wiki/Luftfahrtunternehmen), darunter [Boeing](https://de.m.wikipedia.org/wiki/Boeing) und [Airbus](https://de.m.wikipedia.org/wiki/Airbus)) auf der Basis von CANaerospace entwickelt wurde.

[EnergyBus](https://de.m.wikipedia.org/wiki/EnergyBus) ist ein Kommunikations- und Energieubertragungs-Bus und dazugehoriges Steckersystem fur Leicht-[Elektrofahrzeuge](https://de.m.wikipedia.org/wiki/Elektrofahrzeug) wie Pedelecs und E-Bikes. EnergyBus wird von einem eingetragenen Verein, dem EnergyBus e.V. mit Sitz in Tanna gemeinsam mit dem CAN in Automation e.V. spezifiziert. Mitglieder sind sowohl Einzelpersonen wie auch Hersteller von Steckern, Batterien, Steuerungen und Antriebseinheiten (darunter [Bosch](https://de.m.wikipedia.org/wiki/Robert_Bosch_\(Unternehmen\)), [Panasonic](https://de.m.wikipedia.org/wiki/Panasonic), [Sanyo](https://de.m.wikipedia.org/wiki/Sanyo), [Deutsche Bahn AG](https://de.m.wikipedia.org/wiki/Deutsche_Bahn_AG), [Philips](https://de.m.wikipedia.org/wiki/Philips) und [Varta](https://de.m.wikipedia.org/wiki/VARTA)).[[7]](https://de.m.wikipedia.org/wiki/Controller_Area_Network)

Das Kommunikationsprotokoll ist im CANopen-Applikationsprofil 454 "energy management systems" definiert.

[FireCAN](https://de.m.wikipedia.org/w/index.php?title=FireCAN&action=edit&redlink=1) wurde durch Zusammenarbeit osterreichischer und deutscher Feuerwehraufbauhersteller im Jahr 2006 gegrundet und ist mittlerweile als Norm DIN 14700 vorhanden. Ursprunglich wurde FireCAN als freie Übereinkunft der wesentlichen am Markt befindlichen Hersteller, die redaktionelle Betreuung der gemeinsamen Spezifikation wird dabei durch die Firma [Rosenbauer](https://de.m.wikipedia.org/wiki/Rosenbauer_\(Unternehmen\)) ausgeubt. Die Vorstellung erfolgte im Zuge der [DIN](https://de.m.wikipedia.org/wiki/DIN)-Sitzung des Ausschusses NA 031-02-02 AA „Elektrische Betriebsmittel" am 29. Oktober 2009 in [Berlin](https://de.m.wikipedia.org/wiki/Berlin). Diese Datenbusfestlegung basiert auf einem vereinfachten [CANopen](https://de.m.wikipedia.org/wiki/CANopen)-Standard und regelt sowohl die physikalischen Eigenschaften (Stecker, Leitungen, Pinning), die Art und Anzahl der Teilnehmer, sowie die verwendeten Datenformate und Dateninhalte. Als wesentlicher Vorganger ist der in der Landwirtschaft erfolgreich eingefuhrte [ISOBUS](https://de.m.wikipedia.org/wiki/ISOBUS) zu verstehen.[[8]](https://de.m.wikipedia.org/wiki/Controller_Area_Network)

In [Personenkraftwagen](https://de.m.wikipedia.org/wiki/Personenkraftwagen) sehr verbreitet ist mittlerweile [Unified Diagnostic Services](https://de.m.wikipedia.org/wiki/Unified_Diagnostic_Services) gemaß der ISO 14229. In alteren Modellen verwendeten viele Hersteller eigene Standards, oft basierend auf der letztlich nicht standardisierten Norm fur [KWP](https://de.m.wikipedia.org/wiki/KWP2000) on CAN (Normentwurf ISO/DIS 15765).

  * Wolfhard Lawrenz (Hrsg.): _CAN Controller Area Network - Grundlagen und Praxis._, 5. Auflage, VDE, Berlin / Offenbach 2011, [ISBN 978-3-8007-3332-3](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/9783800733323).
  * Konrad Etschberger (Hrsg.): _CAN Controller Area Network - Grundlagen, Protokolle, Bausteine, Anwendungen._ Hanser, Munchen 1994, [ISBN 3-446-19431-2](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3446194312).
  * Horst Engels : _CAN-Bus - Technik einfach, anschaulich und praxisnah vorgestellt._ Franzis, Poing 2002, [ISBN 3-7723-5146-8](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3772351468).
  * Werner Zimmermann und Ralf Schmidgall: _Bussysteme in der Fahrzeugtechnik - Protokolle, Standards und Softwarearchitektur._ 5\. Auflage, Springer Vieweg, Wiesbaden 2014, [ISBN 978-3-658-02418-5](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/9783658024185).
  * Kai Borgeest: _Elektronik in der Fahrzeugtechnik._ 3\. Auflage, Springer-Vieweg, Wiesbaden 2013, [ISBN 978-3-8348-1642-9](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/9783834816429).
