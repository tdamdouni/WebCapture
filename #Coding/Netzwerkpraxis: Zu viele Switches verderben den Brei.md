# Netzwerkpraxis: Zu viele Switches verderben den Brei

_Captured: 2016-12-25 at 10:11 from [www.ifun.de](https://www.ifun.de/netzwerkpraxis-zu-viele-switches-verderben-den-brei-101966/?utm_source=dlvr.it&utm_medium=twitter)_

Als Diskussionsgrundlage hier mal ein kleiner Erfahrungsbericht zum Thema Netzwerkverkabelung. Kernthema: Handelsubliche Router haben in der Regel nur maximal vier Ethernet-Anschlusse - was wenn mehr Kabelverbindungen benotigt werden?

Die Empfehlung bei Ethernet-Verkabelung lautet stets sternformig. Im besten Fall ist also der Router die zentrale Einheit und daran hangen die Endgerate direkt oder vielleicht auch mit einem zwischengeschalteten Switch. Grundsatzlich sollte es auch kein Problem sein, an jeder der Ethernet-Buchsen der FritzBox einen Switch und damit dementsprechend mehr Gerate kabelgebunden zu betreiben.

Problematisch kann es sein, wenn mehrere Switches hintereinander betrieben werden. Unter Umstanden ist es dann besser, den Router selbst nur noch als Internet-Gateway zu betreiben und statt dessen einen großen Switch mit ausreichend Anschlussen daneben zu hangen. Zur Veranschaulichung mal ein Beispiel aus eigener Erfahrung:

## Nicht gut

![Netzwerk Falsch](https://images.ifun.de/wp-content/uploads/2016/12/netzwerk-falsch-1.jpg)

Die vier Anschlusse einer FritzBox waren nicht mehr ausreichend und daher wurde daneben ein zusatzlicher Switch platziert. Ein Ethernet-Anschluss der FritzBox war mit dem Switch verbunden, an den ubrigen hingen ein NAS-Laufwerk, ein WLAN-Accesspoint und ein weiterer Switch mit TV-Boxen und Konsolen. Am neuen Switch waren ein Rechner, eine Sonos-Bridge sowie verschiedene Buro- und Streaming-Komponenten angeschlossen.

Die beschriebene Konfiguration fuhrte zu permanenten Netzwerkfehlern und Performance-Problemen. Denkfehler war offenbar der Gedanke, „so viel wie moglich direkt an die FritzBox stecken ist am besten". FritzBox und der zusatzlich platzierte Switch hatten parallel ordentlich Traffic zu verarbeiten und das einzelne Verbindungskabel zwischen diesen Komponenten wurde vermutlich zum Flaschenhals.

## So lauft's besser

![Netzwerk Mit Switch](https://images.ifun.de/wp-content/uploads/2016/12/netzwerk-mit-switch.jpg)

Sofortige und dauerhafte Besserung brachte es in diesem Fall, auch die drei zuvor noch auf die FritzBox gelegten Ethernet-Leitungen auf den neuen Switch zu stecken (s. Grafik). Dieser arbeitet seither als zentrale Netzwerkeinheit und die FritzBox ist nur noch fur den Internetverkehr sowie die Vergabe der IP-Adressen zustandig. Auch wenn es auf den ersten Blick nicht ersichtlich ist, das allgemein empfohlene Konzept der [Stern-Topologie](https://de.wikipedia.org/wiki/Topologie_\(Rechnernetz\)#Stern-Topologie) wird hier mit dem neu angeschafften Switch im Zentrum eingehalten.

Ring frei fur die Netzwerker und Administratoren unter euch, die diese Praxiserfahrung um zusatzliche Infos und Hintergrundwissen erganzen konnen.
