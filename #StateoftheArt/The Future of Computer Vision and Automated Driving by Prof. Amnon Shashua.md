# The Future of Computer Vision and Automated Driving by Prof. Amnon Shashua (MobileEye)

_Captured: 2016-10-31 at 23:45 from [www.cbcity.de](http://www.cbcity.de/the-future-of-computer-vision-and-automated-driving-by-prof-amnon-shashua-mobileeye)_

## Inkrementale Verbesserungen in der Computer Vision

![Quelle: Screenshot aus Vortrag Prof. Shashua auf dem Deutsche Bank Global
Auto Industry Conference 2015](http://www.cbcity.de/wp-content/uploads/2015/03
/History-of-Computer-Vision-for-Vehicles-770x432.jpg)

Quelle: Screenshot aus Vortrag Prof. Shashua auf dem Deutsche Bank Global Auto
Industry Conference 2015

Er spricht über die historische Entwicklung der Computer Vision für
Fahrerassistenzsysteme und auch die zukünftige. So wird beispielsweise dieses
Jahr ein automatischer Notbremsassistent bei Audi eingeführt, welcher nur mit
Computer Vision als Sensorik funktioniert. Bisher ein klassisches
Betätigungsfeld für [Radarsensorik oder Lidar](http://www.cbcity.de
/fahrzeugumfeldsensorik-ueberblick-und-vergleich-zwischen-lidar-radar-video).

Er spricht außerdem über False-Positive (d.h. es gibt kein Hindernis, das
System hat aber etwas erkannt und ausgelöst) und False-Negative (d.h. es gab
ein Hindernis, das Computer Vision System hat es aber nicht erkannt)
Auswirkungen für die Detektion von Ereignissen.

![Quelle: Screenshot aus Vortrag Prof. Shashua auf dem Deutsche Bank Global
Auto Industry Conference 2015](http://www.cbcity.de/wp-content/uploads/2015/03
/Object-by-Night-Computer-Vision-770x441.jpg)

Quelle: Screenshot aus Vortrag Prof. Shashua auf dem Deutsche Bank Global Auto
Industry Conference 2015

Außerdem wird auf die Fortschritte der Straßenverlaufs- und Hinderniserkennung
bei Nacht eingegangen.

Ebenfalls wird auf die Erkennung von Straßeneigenschaften, d.h. Schlaglöcher
oder Schwellen, eingegangen. Diese können relativ genau erkannt und das
Fahrwerk bzw. die Geschwindigkeit darauf angepasst werden. Dies wird
spätestens bei autonomer Fahrt interessant.

![Quelle: Screenshot aus Vortrag Prof. Shashua auf dem Deutsche Bank Global
Auto Industry Conference 2015](http://www.cbcity.de/wp-content/uploads/2015/03
/Road-Profile-Computer-Vision-770x427.jpg)

Videosensorik erkennt Straßenunebenheiten. Quelle: Screenshot aus Vortrag
Prof. Shashua auf dem Deutsche Bank Global Auto Industry Conference 2015

## Möglichkeiten der Umfeldwahrnehmung auf dem Weg zur vollautonomen Fahrt

Um das Fahrzeug in der Umgebung sicher bewegen zu können, gibt es verschiedene
Ansätze. Google beispielsweise fährt umher und scannt einfach die gesamte
Stadt mit 360° Laserscannern in riesigen Punktwolken ab, welche dann zu 3D
Modellen zusammen gesetzt werden. Daraus können Straßen, Hindernisse, Ampeln,
Bordsteine, Einfahrten etc. extrahiert werden.

Genau auf der anderen Seite der Möglichkeiten steht, gar keine Daten zu
sammeln, sondern nur Sensoren immer schauen zu lassen, wie es denn gerade
aussieht.

![Paradigms-for-Autonomous-Driving-Maps](http://www.cbcity.de/wp-
content/uploads/2015/03/Paradigms-for-Autonomous-Driving-Maps-500x375.png)

Doch all diese Step-by-Step Verbesserungen reichen nicht, um autonome Fahrt
realisieren zu können. Dafür muss ein großer, riesiger Schritt getan werden.

## Deep Learning für vollautonome Fahrt

Prof. Shashua spricht über Deep Learning und das MobileEye seit 2 Jahren an
der Nutzung von Deep Learning Algorithmen (genauer: [Deep Convolutional
Networks](http://www.cs.toronto.edu/~fritz/absps/imagenet.pdf)) für die
Umfeldsensorik arbeitet. Dabei war vor allem das Problem der vielen (kleinen)
Operationen (mathematischen Faltungen = Convolutions) die Herausforderung, was
aber mit dem neuen EyeQ3 Chip wohl gelöst sei.

![Quelle: Screenshot aus Vortrag Prof. Shashua auf dem Deutsche Bank Global
Auto Industry Conference 2015](http://www.cbcity.de/wp-content/uploads/2015/03
/FreeSpace-Neural-Netzwork-Deep-Learning-770x457.jpg)

Videosensorik, angelernt mit Deep Learning markiert Pixelgenau, was freier
Raum (grün), Fahrbahnbegrenzung (rot), Front/Heck anderer Fahrzeuge (blau)
oder Seite anderer Fahrzeuge (pink) ist. Quelle: Screenshot aus Vortrag Prof.
Shashua auf dem Deutsche Bank Global Auto Industry Conference 2015

Mit angelernten neuronalen Netzen war es möglich Fahrspuren zu erkennen,
selbst wenn keine Fahrbahnmarkierungen zu ‚sehen' waren. Außerdem erkennt das
Netz freie Fahrbahn, Fahrzeuge und Straßenbegrenzungen. Siehe auch ‚[Es
beginnt selbst zu lernen…](http://www.cbcity.de/rise-of-the-machines-es-
beginnt-selbst-zu-lernen)‚

Dies ist keine Zukunftsmusik, so Shashua, es wird dieses Jahr einen
Fahrzeughersteller geben, der dies in Serie heraus bringen wird. Und er sprach
viel über Tesla in diesem Vortrag. :)

[Deep Learning is likely to come to #Tesla as Computer Vision for Autonomous
Driving this Year!](https://twitter.com/share?text=Deep+Learning+is+likely+to+
come+to+%23Tesla+as+Computer+Vision+for+Autonomous+Driving+this+Year%21&url=ht
tp://www.cbcity.de/the-future-of-computer-vision-and-automated-driving-by-
prof-amnon-shashua-mobileeye)

[Click To Tweet](https://twitter.com/share?text=Deep+Learning+is+likely+to+com
e+to+%23Tesla+as+Computer+Vision+for+Autonomous+Driving+this+Year%21&url=http:
//www.cbcity.de/the-future-of-computer-vision-and-automated-driving-by-prof-
amnon-shashua-mobileeye)

Sein Fazit ist, dass die Computer Vision _die_ Sensorik für
Fahrerassistenzsysteme werden wird, Radar und Laserscanner nur zur Redundanz
bzw. Absicherung eingesetzt werden, falls der Fahrzeughersteller diese Kosten
auf sich nimmt. Denn Computer Vision Sensorik ist die mit Abstand günstigste.

Nungut, bei Nebel sieht ein Computer Vision System auch nichts, da muss das
Radar die Abstandsinformation liefern.

Lange Rede, kurzer Sinn, hier der Vortrag:

## Vortrag ‚Zukunft der Computer Vision und Autonomen Fahrt' von Prof. Amnon
Shashua von MobileEye



_Errata: In der ursprünglichen Fassung des Artikels war die Beschreibung für False-Positive und False-Negative vertauscht._

