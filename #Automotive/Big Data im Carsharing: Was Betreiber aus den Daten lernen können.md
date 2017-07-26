# Big Data im Carsharing: Was Betreiber aus den Daten lernen können

_Captured: 2016-03-19 at 12:19 from [t3n.de](http://t3n.de/news/big-data-carsharing-daten-690284/)_

Schon 1999 grundeten Burger in Großstadten aus der Not an Parkplatzen, geringer Nutzungsquote und hohen Anschaffungs- und Unterhaltskosten heraus Initiativen wie ZIP-Car oder Stadtauto. War zu dieser Zeit der Ausloser eher im privaten Bereich zu finden, bieten mittlerweile Unternehmen Plattformen fur den Austausch oder das Teilen von vielerlei Objekten an. Die Mobilitat stellt die Betreiber aber vor ganz besondere Herausforderungen, bietet aber auch ungeahnte Chancen.

## Big Data

Allem voran stellt eine zukunftsweisende Geschaftsstrategie hohe Anforderungen an die Datenubertragung und -auswertung innerhalb des Systems. Hinter dem Begriff „Big Data" verbirgt sich alles, was fur den Betrieb einer Fahrzeugflotte aus Wartungs-, Kunden- und Forschungsperspektive notwendig ist.

![Tesla Motors: Geht es nach Elon Musk, könnten die Autos seines Unternehmens schon in zwei Jahren auch längere Strecken ohne Fahrer zurücklegen. \(Foto: Tesla Motors\)](http://t3n.de/news/wp-content/uploads/2016/01/tesla_elon_musk_selbstfahrende-autos-595x335.jpg)

> _Über Elektro-Fahrzeuge lassen sich viele Daten sammeln und auswerten. (Foto: Tesla Motors)_

Moderne Fahrzeuge sind rollende Computer und erfassen standig Daten aus der Umgebung und dem eigenen Innenleben. Diese werden mal mehr, mal weniger dem Fahrer angezeigt. An wichtige Erkenntnisse gelangt der Betreiber einer Flotte durch die intelligente Verknupfung der Daten, wobei unbekannte Datenkorrelationen zu interessanten Ergebnissen fuhren. Dies bedingt aber auch, dass die Daten in einer niedrigen Taktung erfasst und ubertragen werden, um Zusammenhange zu erkennen. So vollzieht man zum Beispiel einen Schaltvorgang im Auto in weniger als zwei Sekunden und betatigt dabei viele unterschiedliche Komponenten (Gas wegnehmen, Kuppeln, Gang wechseln, Kupplung kommen lassen, Gas geben). Um hier Ruckschlusse abzuleiten, mussen die Sensoren folglich auch in einem sehr kurzen Takt Daten liefern.

Beispiele fur Datenpunkte in einem Auto sind zum Beispiel Reifendruck, Reifentemperatur, GPS-Position, Lenkwinkel, Drehzahl, Drehmoment, Handbremse, Kupplung, Gaspedal, Geschwindigkeit, Neigung des Fahrzeugs oder die Motortemperatur. „Fur ein elektrisch betriebenes Fahrzeug sind das Ladeverhalten des Nutzers, sowie Außen- und Batterietemperatur entscheidend", erganzt Gotz Schmidt, Marketingleiter beim Munchner Elektroroller-Hersteller Govecs. Zu Kunden von Govecs zahlen Scooter-Sharing-Unternehmen wie Scoot networks (San Francisco) und cooltra (Barcelona).

## Neue Herausforderungen fur die IT-Infrastruktur

Hieraus ergeben sich fur die IT-Infrastruktur ganz neue Herausforderungen. Eine große Anzahl von Fahrzeugen sendet in einer extrem kurzen Taktung Daten an ein zentrales System, das dieses Datenvolumen aufnehmen und verarbeiten muss. Die Datenubertragung muss folglich leichtgewichtig bleiben. Die Übertragung der Informationen muss priorisiert werden. Und die Nachrichtenubertragung soll so einfach wie moglich sein, was die notwendige Bandbreite fur die Datenubertragung zwischen Fahrzeug und Backend minimiert und damit die Kosten fur den Mobilfunk gering halt.

Fur einige Nachrichten muss sichergestellt sein, dass sie den Empfanger erreichen. Das bedeutet, Verbindungsabbruche verursachen nur einen vorubergehenden Kommunikationsverlust zwischen den Parteien. „Hier empfehlen wir das Protokoll MQTT als zuverlassige und effiziente Kommunikation uber instabile Mobilfunknetze zwischen Tausenden vernetzten Geraten mit einem zentralen Backend", so Michael Bauer, Senior Software-Engineer bei der MaibornWolff GmbH in Munchen. Das Maschine-zu-Maschine- Protokoll ist inzwischen eines der wichtigsten Protokolle im Internet der Dinge. Implementierungen gibt es von verschiedenen Anbietern, sowohl als proprietare Losung (HiveMQ), wie auch als Open-Source-Losung (RabbitMQ). MQTT eignet sich, um Nachrichten mit geringem Netzwerk-Overhead zwischen Client und Server zu ubertragen und bietet drei Quality-of-Service-Levels, die eine Priorisierung der Nachrichtentypen erlauben. Ferner ist eine Verschlusselung der Daten moglich. Viel wichtiger ist die Flexibilitat des Protokolls, das mittels Schnittstellenadaptern mit unterschiedlichen Geraten und Gerateversionen sprechen kann.

![\(Grafik: Shutterstock\)](http://t3n.de/news/wp-content/uploads/2016/03/server-illustration-microservices-shutterstock_376067962-595x397.jpg)

> _Fur die IT-Infrastruktur gibt es einige Herausforderungen. (Grafik: Shutterstock )_

Ein weiterer Ansatz, die Datenmenge zu verwalten und zu verarbeiten, ist das Konzept der Datendrehscheibe in Form eines dem Backend vorgeschalteten Message Broker. Der nimmt Daten in einem Kanal entgegen und verteilt sie nach Bedarf an weitere Anwendungen wie zum Beispiel CRM- oder Buchhaltungssysteme. Der MQTT-Server verwendet dafur Regeln, die die Daten nach festgelegten Kriterien filtern und verteilen. Ruckblickend lassen sich Nachrichten uber die Sender-ID eindeutig einem Absender zuordnen, ohne Platz im Payload der Nachricht zu verbrauchen.

In unserem Fall ist der Hauptabnehmer fur Nachrichten der Datendrehscheibe das Backend fur das Flottenmanagement. Hier kommen alle Daten an, um die Flotte zu betreiben. Eine Big-Data-Anwendung muss eine schnelle und flexible sein. Dabei unterscheiden sich die Anforderungen an Berichte und Echtzeitdaten wesentlich. Wahrend Echtzeitdaten sehr schnell verfugbar sein mussen, brauchen ausfuhrliche Datenanalysen eine große Datenbasis. Im Tagesgeschaft durfen zum Beispiel die Positionsdaten fluchtiger aber prompt verfugbar sein. Im Gegensatz dazu bilden Berichte das Ruckgrat fur diverse Kennzahlen, konnen aber in betriebsarme Zeiten in der Nacht verlegt werden. „Fur eine belastbare Big-Data-Architektur, die aus den enormen Datenmengen im Internet der Dinge sinnvolle Informationen destilliert, eignet sich die sogenannte „[Lambda-Architektur ](http://lambda-architecture.net/)" als hybrider Ansatz fur Echtzeit-Anwendungen und Batch-Auswertungen besonders", meint Michael Bauer.

Der technische Aufwand ist folglich enorm und die Kurzzeitmieten stellen ein ideales Test-Umfeld fur die IT-Landschaft dar. So konnen Erkenntnisse fur das Datenvolumen, die Datenstruktur und -ubertragung fur den breitflachigen Einsatz gewonnen und uberarbeitet werden. Quasi agil entwickeln, verbessern und schließlich fur alle freischalten.

[Big Data at its best: Diese KI durchforstet das Netz und sagt dir, wann du investieren solltest

](http://t3n.de/news/startup-ki-investment-684864/)

## Wartung und Flottenmanagement

Die Position eines Fahrzeugs in einem Netzwerk ist der nahe liegende Datensatz. Gepaart mit dem Buchungsstatus kann das Service-Team entsprechend reagieren. Eine qualitativ hochwertige Business-Intelligence (Big Data) erlaubt Wartungsvorhersagen auf Basis von bekannten Zusammenhangen, sodass Verschleißteile schon fruhzeitig bestellt und das Fahrzeug fur den Werkstattbesuch eingeplant werden kann. Sie hilft aber auch bei ziemlich profanen Alltagsproblemen, wie zum Beispiel der Aufforderung zum Akkutausch wegen zu geringer Reichweite zur nachsten Station.

![Grafik: \(Max Griboedov / Shutterstock\)](http://t3n.de/news/wp-content/uploads/2015/08/dashboard-zahlen-shutterstock_232781677-595x338.jpg)

> _Auf Basis der gesammelten Daten und Zahlen kann das Service-Team reagieren. (Grafik: Max Griboedov / Shutterstock)_

Big Data laßt sich aber auch fur die Unternehmenssteuerung einsetzen. Der Flottenmanager uberwacht seine Kennzahlen in einem Cockpit in Echtzeit, wie zum Beispiel:

  * die Auslastung der Flotte
  * die durchschnittliche Fahrtdauer
  * Parkdauer
  * durchschnittlich gefahrene Distanz
  * und vergleicht auch die Kennzahlen der einzelnen Standorte oder gar Stadte miteinander

Beim Einsatz fur einen Lieferservice bietet die Kopplung eines Smartphones mit dem Roller automatisch ein elektronisches Fahrtenbuch. Auch die Routenoptimierung spielt hier eine wesentliche Rolle, vor allem wenn sich Beschwerden uber „kalte Essenslieferungen" haufen.

Der Einsatz von Fahrzeugen in einem Kurzzeit-Mietmodell ist deshalb so interessant, weil mehrmals taglich die Fahrprofile wechseln und so die Datenvielfalt exponentiell wachst. Die Fahrzeuge sind also im Gegensatz zum privaten Gebrauch im Dauereinsatz und lassen Ruckschlusse fur die Wartung aber auch die Entwicklungsabteilung zu.

Beispielsweise werden die Bremsklotze an einem Elektroroller alle 5.000 Kilometer gewechselt. Weichen die tatsachlichen Verschleißzyklen deutlich davon ab, bietet sich eine Datenanalyse an, um nach den Ursachen zu forschen - hier geben Fahrverhalten, geographische Indikatoren und das Wetter oder die Zuladung hinreichend Aufschlusse.

Oder die Nutzung von Seitenstander versus Hauptstander kann entscheidende Impulse fur die Produktion geben. Reichert man diese Daten noch mit dem Geschlecht des Fahrers an, ergeben sich wertvolle Erkenntnisse fur Marketing und Produktion.

Die Auswertung des Reifendrucks bietet gleich zweifach Vorteile, denn dieser ist ein wesentlicher Einflussfaktor fur die Reichweite. Zum Einen kann das Service-Team ausrucken und den Reifendruck anpassen. Zum Anderen konnen mit den Daten exakte Berechnungen erstellt werden, wie stark die Reichweite tatsachlich beeinflusst wird und ab wann sich der Einsatz des Service Teams lohnt.

## Kundenkommunikation

Zu guter Letzt dreht es sich um das Herzstuck des E-Rollers - und jedes Elektrofahrzeugs - die Batterie. Der sorgsame Umgang mit diesem teuren Bauteil sorgt fur eine lange Lebensdauer mit hoher Reichweite. Hier liefern die aus dem Protokoll ubertragenen Daten zahlreiche Ansatzpunkte. Schmidt: „Wie ist das Ladeverhalten? Lasst sich dieses optimieren? Welche Hilfestellungen konnen dem Nutzer/Operator systemseitig an die Hand gegeben werden? Wie lassen sich die schadlichen Tiefenentladungen vermeiden? Wie kann man die User bei der Batteriepflege unterstutzen?"

Die systemseitige Kommunikation hilft hierbei enorm und unterstutzt die Kunden in smarter Weise langer mehr Spaß und Freude an ihrem Produkt zu haben. Denn alle Faktoren konnen eigentlich leicht vermieden werden. „Dies ist ein perfekter Einsatz direkter Kundenansprache und -bindung", sagt Gotz Schmidt. „Der Besitzer eines Rollers ist dankbar fur hilfreiche Tipps fur eine lange Lebensdauer seines Fahrzeugs. Auf der anderen Seite konnen Verleiher mit gezielten Bonusprogrammen materialschonenden Umgang trainieren und fordern", so Schmidt weiter. Der Carsharing-Betreiber Car2go vergibt Kleeblatter mit einem Wert fur umweltschonendes Fahren am Ende jeder Miete. Somit wird die personliche Umweltbilanz sichtbar und der Spieltrieb um noch sparsameres Fahren gefordert. Denkt man dieses Modell weiter, kampfen alle Nutzer um die Auszeichnung als umweltfreundlichster Fahrer Munchens im Monat April und erhalten als Dankeschon Freiminuten oder ahnliches. Neben Adhoc-Informationen auf einem Smartphone konnen aber auch Berichte und Auswertungen bereitgestellt werden.

Kooperationen mit Partnern fuhren zu gelenkter Navigation. Ähnlich wie ich als Payback-Punktesammler vermutlich eher eine Aral-Tankstelle anfahre, kaufe ich als Nutzer von drive-now hochstwahrscheinlich bei Rewe ein, weil es Rabatte plus 10 Minuten kostenloses Parken gibt.
