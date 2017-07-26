# Adaptive oder Responsive? Über die Vor- und Nachteile der beiden Design-Ansätze

_Captured: 2015-09-14 at 08:41 from [t3n.de](http://t3n.de/news/adaptive-responsive-design-637267/)_

Nach geschnitten Brot und Widescreen-Displays ist Responsive Design sicher das Beste, was Entwicklern passiert ist. Schon vor zwei Jahren habe ich versucht, in [einem ausfuhrlichem Guide](http://t3n.de/news/responsive-design-web-entwicklung-504906/) Licht in die verschiedenen Losungen zu bringen. Aber wie sieht es heute aus? Ist Adaptive Design besser als Responsive Design - oder umgekehrt? Spoiler: Die Wahrheit liegt irgendwo dazwischen.

Dabei gibt es mehr als nur die zwei oben genannten. Elastic und Fluid Design existieren zwar auch, sind aber nicht im 0815-Webdesign zu finden. Schade, denn obwohl sie aufwandiger umzusetzen sind, konnen Entwickler eine ganz [andere - und vielleicht bessere - UX ](http://t3n.de/news/ui-ux-sieht-vs-fuehlt-635734/)gestalten.

## Adaptive vs. Responsive: Wo liegen die Unterschiede?

![Adaptive oder Responsive Design? \(Grafik: Shutterstock\)](http://t3n.de/news/wp-content/uploads/2015/09/adaptive-responsive-design1-595x298.jpg)

> _Adaptive oder Responsive Design? (Grafik: Shutterstock )_

Aber wieder zuruck zur Frage, welcher Ansatz besser ist: Der Hauptunterschied ist, dass im adaptiven Ansatz via Breakpoints versucht wird, ein an ein spezielles Gerat angepasstes Design auszuliefern. Dabei wird das Gerat auf Seiten von CSS durch die Auflosung erkannt. Daruber hinaus gibt es noch andere Moglichkeiten, zum Beispiel uber den Browser-Agent, das Gerat zu erkennen.

Dieser Artikel dreht sich aber um die zwei Ansatze und nicht darum, wie sie implementiert werden konnen. Design lost Probleme - und auf die kommt es entsprechend an bei der Frage, fur welchen Ansatz man sich als Entwickler entscheidet.

## Adaptive Design: Breakpoints machen den Unterschied

Die Aussage, [Adaptive Design sei adaptive, nur weil der Server eine optimierte Darstellung ](http://thenextweb.com/dd/2015/09/01/is-adaptive-better-than-responsive-design/) fur ein vorher erkanntes Gerat ausliefert, ist nicht richtig - hier werden Adaptive Webdesign und RESS vermischt.

### Webdesign aus der Sicht des Servers

Mit [RESS (Responsive Design + Server-Side-Components) hat Luke Wroblwski ](http://www.lukew.com/ff/entry.asp?1392) sich schon 2013 uber eine eine serverseitige Alternative zu clientseitigem Adaptive Webdesign geaußert:

> „In a nutshell, RESS combines adaptive layouts with server side component (not full page) optimization. So a single set of page templates deﬁne an entire Web site for all devices but key components within that site have device-class speciﬁc implementations that are rendered server side."Luke Wroblwski

Die Moglichkeiten etwa in Bezug auf Adaptive Images wurden aber den Rahmen dieses Artikels sprengen - kurzum: Adaptive Design wird clientseitig ausgefuhrt - mithilfe von pixelgenauen Breakpoints. Eine Umsetzung mit Apdaptive Design kann aber auch serverseitig passieren.

## Responsive Design: 100% vs. 960px

Wahrend fixe Breakpoints pro Device-Große fur das richtige Adaptive Design entscheidend sind, verfolgt das Responsive Design den Ansatz, uber relative Großen (`%` oder `em`) die Ausgabe des Designs zu steuern.

## Adaptive oder Responsive? Kommt auf das Problem an

Beide Ansatze haben Vor- und Nachteile. Adaptive Design kann die optimale Erfahrung fur einen Nutzer auf einem spezifischen Gerat bedeuten, wird aber schnell zu aufwandig, wenn mehrere Gerate bedient werden mussen. Responsive Design hat den Vorteil, dass es schnell mit sehr vielen Geraten und Auflosungen genutzt werden kann, allerdings dann oft suboptimal.

Das beste Ergebnis kann eine Mischung aus beiden Ansatzen sein - muss es aber nicht. Denn ob ihr eine Mischform oder Adaptive beziehungsweise Responsive Design fur euer Projekt einsetzt, ist vom Projekt abhangig.

Mit wachsender oder schrumpfender Display-Große verandert sich auch das UX, das beispielsweise durch eine gekonnte Content-Strategy erganzt werden muss. Die Frage nach Responsive oder Adaptive Design allein ist also nicht die Losung.

**Wie setzt ihr eure Projekte um?**
