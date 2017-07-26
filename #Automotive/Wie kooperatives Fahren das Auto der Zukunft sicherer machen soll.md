# Wie kooperatives Fahren das Auto der Zukunft sicherer machen soll

_Captured: 2015-11-12 at 09:13 from [www.computerwoche.de](http://www.computerwoche.de/a/wie-kooperatives-fahren-das-auto-der-zukunft-sicherer-machen-soll,3218955)_

![Testfahrt für kooperatives Fahren - hier ein Überholvorgang - auf der A9](http://images.computerwoche.de/images/computerwoche/bdb/2668998/522x294.jpg)

> _Testfahrt fur kooperatives Fahren - hier ein Überholvorgang - auf der A9 Foto: Deutsche Telekom_

Gefahrensituationen wie das plotzliche Ausscheren eines anderen Fahrzeugs aus der rechten Spur oder unerwartete Bremsmanover des Vordermanns sind nicht selten Ursachen fur schlimme Unfalle oder zumindest Staus. Um diese moglichst zu vermeiden, sollen in nicht allzu ferner Zukunft vernetzte Fahrzeuge miteinander kommunizieren und sich gegenseitig vor Gefahren warnen. Aus Sicht von Bundesverkehrsminister Alexander Dobrindt (CSU), der nun ein entsprechendes Pilotprojekt auf der A9 zwischen Munchen und Nurnberg gemeinsam mit Managern und Forschern vorstellte, handelt es sich dabei um einen "Sprung in das digitale Echtzeitalter".

Um eine Kommunikation zwischen den Fahrzeugen in Quasi-Echtzeit zu ermoglichen, musste allerdings ein riesiges Problem mit der Latenzzeit gelost werden. So arbeitet Kooperationspartner Continental im Rahmen des Projekts eHorizon zwar schon langer an einer digitalen Straßenkarte, die von Autos mit Sensordaten gespeist und damit aktualisiert wird. Mit diesen Informationen kann ein Auto quasi durch den vorausfahrenden Lastwagen schauen, uber die nachste Kuppe blicken und es weiß sogar, wenn ein anderes Fahrzeug zum Überholen ansetzen will.

### Mobile Edge Computing lost das Latenzzeit-Problem

Da sich die Karte in der Cloud befand, dauerte es vor einem Jahr allerdings noch sechs Sekunden, bis die von einem Auto gesendeten Daten an die anderen Verkehrsteilnehmer weitergegeben wurden. Wie Ralf Lenninger, Leiter Strategie und Innovation der Division Interior Continental, bei der Pressevorstellung erklarte, entsprach diese Latenzzeit bei einer Geschwindigkeit von 130 km/h 150 Metern Blindflug und war somit untragbar.

![Kathrin Buvac, Chief Strategy Officer von Nokia Networks, zeigt ein Einschubmodul zur Aufrüstung von LTE-Basisstationen.](http://images.computerwoche.de/images/computerwoche/bdb/2668945/522x294.jpg)

> _Kathrin Buvac, Chief Strategy Officer von Nokia Networks, zeigt ein Einschubmodul zur Aufrustung von LTE-Basisstationen._

Bei der nun umgesetzten Losung dauert ein Roundtrip der Daten unter 20 Millisekunden, was weniger als ein Meter mit dem Auto zuruckgelegter Wegstrecke entspricht. Moglich wurde dies durch die Übertragung per LTE und der von Nokia Networks mitentwickelten Technologie Mobile Edge Computing: Dabei ubernehmen Einschubmodule (so genannte Cloudlets), die direkt in den Mobilfunk-Basisstationen eingebaut werden, lokal die Verarbeitung der Sensordaten - die Kommunikation findet somit nicht uber ein Rechenzentrum in der Cloud, sondern in der jeweiligen Funkzelle statt.

Ohne die neue Technik - [beim Wettbewerber Cisco unter dem Namen Fog-Computing bekannt](http://www.computerwoche.de/a/cisco-will-iot-daten-direkt-im-netz-verarbeiten,3211891) \- dauert die Übertragung in LTE-Netzen bestenfalls knapp einhundert Millisekunden, unter ungunstigen Bedingungen sogar mehrere hundert Millisekunden. Erst durch die schnelle Übertragung werden Verkehrssicherheitsanwendungen uber Mobilfunknetze sinnvoll moglich.

### Zwei Testszenarien 

Wie das Ganze kunftig funktionieren konnte, zeigen die Experten von Deutsche Telekom, Nokia Networks, Continental und Fraunhofer ESK anhand zweier Anwendungsfalle bei Fahrten auf der A9 zwischen Pfaffenhofen und dem Autobahndreieck Holledau. Bei dem einen Szenario meldet das System in Quasi-Echtzeit, wenn ein vorausfahrendes (und moglicherweise nicht sichtbares) Auto bremst, und gibt dem Fahrer bzw. autonomen Fahrzeug ausreichend Zeit, die Geschwindigkeit zu reduzieren.

Beim zweiten, deutlich komplexeren Beispiel geht es darum, wie man mit vernetzten Autos fur mehr Sicherheit bei einem Überholvorgang sorgen kann: So wird ein Fahrer auf der Überholspur fruhzeitig (= unter 20 ms) gewarnt, wenn anderes Auto auf der rechten Spur den Blinker setzt und ausscheren mochte. Damit nicht genug, erhalt er auch einen Hinweis, ob er als Konsequenz die Geschwindigkeit reduzieren sollte oder es sicher ist, einfach weiterzufahren. Umgekehrt wird auch der Ausscherende daruber informiert, ob er ohne Gefahr die Spur wechseln kann (das nachfolgendes Fahrzeug ist mehr als 500 Meter entfernt) oder die Spur halten muss, bis das schnellere (gemessen an der Geschwindigkeit nur sechs Sekunden entfernte) Fahrzeug vorbeigefahren ist.

[Newsletter bestellen und ein iPad mini gewinnen!](http://www.computerwoche.de/p/newsletter,272?newsletter=Netzwerke&v465=newsletter_ipad_AugSept15_Aktion3_CW)

  


### Technische Zusammenarbeit

![Das Testequipment passt problemlos in den Kofferraum.](http://images.computerwoche.de/images/computerwoche/bdb/2668938/522x294.jpg)

> _Das Testequipment passt problemlos in den Kofferraum._

Bislang sind vier Testfahrzeuge auf der entsprechend ausgerusteten Teststrecke so vernetzt unterwegs. Die Deutsche Telekom stellt hier schnellen LTE-Mobilfunk zur Verfugung, Nokia hat drei an der Strecke liegende Funkmasten zu zentralen Datenstationen fur die gerade vorbeifahrenden Autos aufgerustet. Von Continental wiederum stammt die Anwendungssoftware sowie die grafische Oberflache fur die Anwendungsszenarien. Außerdem zeichnet der Automobilzulieferer fur die Integration der LTE-Technik mit den Signalen des Fahrzeugbus (CAN) verantwortlich.

Last, but not least hat das Fraunhofer ESK die GeoService-Software entwickelt, die dafur sorgt, dass die Positionsdaten der Fahrzeuge erfasst und direkt in der jeweils nachsten LTE-Basisstation verarbeitet werden. Auf Basis der dort vorgenommenen Berechnungen konnen Ereigniswarnungen fast verzogerungsfrei an alle Fahrzeuge gesendet werden, die sich im relevanten Bereich befinden.

Trotz der Vorabdemonstration des ersten Projektes im Rahmen der "Innovationscharta fur das Digitale Testfeld Autobahn" wird bis zur Realisierung noch einige Zeit vergehen. "Die Herausforderung ist, kunftig Hunderte Autos so zu vernetzen, alle Daten richtig zu bewerten und auch ohne Unterbrechung von einer Funkzelle zur nachsten zu wechseln", erklart Prof. Dr.-Ing. Rudi Knorr, Institutsleiter vom Fraunhofer ESK. Knorr schatzt daher, dass das Ganze erst in etwa zehn Jahren serienreif sein konnte.

### Wer soll das bezahlen?

Womit die Frage nach dem Preis fur die Vernetzung der Autos und Autobahnen bliebe: Der Autozulieferer Continental kalkuliert, dass die erforderliche Technik in den Autos nur wenige hundert Euro kostet. Der Aufbau des noch schnelleren, fur das automatisierte Fahren notigen LTE-Mobilfunknachfolgers 5G werde "teuer", sagte Telekom-Chef Timotheus Hottges auf der Pressekonferenz in Pfaffenhofen. Aber das musse nicht der Steuerzahler bezahlen: "Ich bin sicher, dass die Privatwirtschaft diese Netze baut." Vernetztes und spater autonomes Fahren werde auf jeden Fall kommen und die Mobilitat vollig verandern. "Wir sind froh, dass wir in Deutschland ein solches Projekt ausprobieren konnen."

Auch Dobrindt sieht die digitale Zukunft rundum positiv. Statt die Technik aus dem Ausland zu kaufen, konne die deutsche Industrie selbst daran verdienen. Und der Minister spart viel Geld, denn bald konnen fast doppelt so viele Autos unterwegs sein, ohne dass er neue Autobahnen bauen muss: "Wir konnen so 80 Prozent mehr Kapazitat auf die Autobahn bringen. Und ein paar Kilometer Autobahn kosten Milliarden." (mit Material von dpa)

[Newsletter bestellen und ein iPad mini gewinnen!](http://www.computerwoche.de/p/newsletter,272?newsletter=Netzwerke&v465=newsletter_ipad_AugSept15_Aktion3_CW)
