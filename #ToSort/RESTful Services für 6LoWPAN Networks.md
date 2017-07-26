# RESTful Services für 6LoWPAN Networks

_Captured: 2015-11-09 at 09:44 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/betrieb/netzwerke/restful-services-fuer-6lowpan-networks.html)_

![REST bezeichnet einen Architekturstil für verteilte Anwendungen. © depositphotos.com / srecko80](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720_Depositphotos_6424811_s_srecko80_f29ff1d63e.png)

> _REST bezeichnet einen Architekturstil fur verteilte Anwendungen. (C) depositphotos.com / srecko80_

**Die Verknupfung netzwerkfahiger Sensoren und Aktoren zum Internet der Dinge ist momentan ein wichtiger Trend, der die Forschung und Entwicklung im Netzwerkbereich beeinflusst. Die fortschreitende Vernetzung von elektrisch steuerbaren Geraten ermoglicht neuartige Nutzungs- und Interaktionsszenarien. Die Entwicklung von Softwareanwendungen fur diese Anwendungen sollte auf etablierte Entwurfsmuster verteilter Anwendungen zuruckgreifen. Dabei muss allerdings beachtet werden, dass aufgrund der stark eingeschrankten Ressourcen der Gerate eine verstarkte Integration und Anpassung der Softwarekomponenten notig ist. **

Die Vernetzung intelligenter Gerate, so genannter Smart Objects, bringt einige neue Herausforderungen mit sich. Anders als bei Computern und Smartphones stellt die Netzwerkfahigkeit keine Hauptanforderung dar, sondern wird als Zusatznutzen zur eigentlichen Geratefunktion implementiert. Die Produktlebenszyklen, Support- und Installationsanforderungen an solche Gerate sind teilweise sehr verschieden von bekannten Anwendungsszenarien fur Netzwerktechnik. So sollen sich zum Beispiel Sensornetze mit tausenden von Sensoren automatisch konfigurieren, Netzwerkverkehr automatisch nach Kriterien der Energieeffizienz routen und im Batteriebetrieb mehrere Jahre einsatzfahig sein. Daruberhinaus sollen die einzelnen Gerate nur wenige Euro kosten.

Diese Anforderungen haben in der Vergangenheit dazu gefuhrt, dass solche Netzwerke anwendungsspezifische Protokolle einsetzen, die einen reduzierten Funktionsumfang bereitstellen und eine sehr starke vertikale Integration aufweisen (Zigbee, Bluetooth). Die typischen Erfolgsmerkmale eines vollstandigen Internet-Protokoll Stacks, wie globale Adressierbarkeit und Erreichbarkeit, Bereitstellung einer abstrakten Socket-Schnittstelle fur die Netzwerkintegration von Anwendungen und der Einsatz unterschiedlicher Transportprotokolle lassen sich in solchen Netzen nur sehr eingeschrankt realisieren und setzen in der Regel den Einsatz von Gateways voraus.

Fortschritte auf dem Gebiet der Mikrocontroller, der Übertragungstechnik und des Netzprotokolldesigns haben es mittlerweile aber moglich gemacht, die oben genannten Anforderungen auf Basis kostengunstiger und energieeffizienter Mikrocontroller zu realisieren, welche uber eine standardkonforme Implementierung des Internet-Protokolls verfugen. Als Softwarebasis fur die Entwicklung eines netzwerkfahigen Gerats bietet sich zum Beispiel Contiki an [[1]](http://www.informatik-aktuell.de/betrieb/netzwerke/restful-services-fuer-6lowpan-networks.html). Contiki ist ein lizenzfreies, minimales Betriebssystem, welches in C geschrieben ist und auf verschiedenen 8-, 16- und 32-bit-Mikrocontrollern, als auch nativ als Linux-Prozess lauffahig ist.

Der Einsatz eines Betriebssystems fur leistungsschwache Mikrocontroller ist heutzutage noch nicht weit verbreitet, bietet aber eine Reihe von Vorzugen. So lassen sich Entwicklungszyklen verkurzen, da Anwendungen nicht direkt auf dem Mikrocontroller entwickelt und getestet werden mussen, der spater zum Einsatz kommt. Die Entwicklergemeinde des Betriebssystems sorgt dafur, dass Basisfunktionen bereitgestellt werden und die Dokumentation aktuell gehalten wird.

## Vernetzung auf Basis von IEEE 802.15.4

Internetfahige Gerate mussen uber eine geeignete Netzwerkschicht verfugen um IP-Pakete transportieren zu konnen. Auch hier fuhren die erwahnten Anforderungen dazu, dass etablierte Protokolle und Netzzugriffsverfahren aus dem PC-Bereich ungeeignet sind, weil ihr Energiebedarf zu hoch ist oder bestimmte Netztopologien voraussetzt.

IEEE 802.15.4 ist ein Funkstandard fur Home Networks, Industrie- und Gebaudeautomatisierung. Der Standard wurde Anfang der 2000er Jahre entworfen und hat das Ziel, kostengunstige, niedrig-bitratige Vernetzung fur Gerate zu ermoglichen, die bisher nicht netzwerkfahig waren. Dafur musste insbesondere der Energiebedarf optimiert werden. Die Anforderungen an Datenrate und Latenz sind dagegen gering und sollten fur einfache Kontroll- und Steuerungsfunktionen ausreichen. Gegenuber alternativen Technologien wie Bluetooth-LE bieten Netze auf Basis von IEEE 802.15.4 weiterhin den Vorteil der großeren Zahl adressierbarer Knoten (16-bit MAC-Adressen) und der moglichen Vollvermaschung (Mesh-Network). Knoten mit Routingfunktionalitat konnen Nachrichten weiterleiten und mit wenigen Edge-Routern ein weitflachiges Netzwerk aufspannen.

Der Standard definiert mehrere Übertragungsverfahren in verschiedenen lizenzfreien Übertragungsbandern:

  * 20 kbit/s bei 868 MHz
  * 40 kbit/s bei 915 MHz
  * 250 kbit/s bei 2.4 GHz (DSSS)

Die Netze konnen im Beacon-Modus betrieben werden. Dabei sendet ein Koordinator Beacon-Frames aus, welche der Synchronisation aller Netzknoten dienen. Inaktive Knoten konnen ihr Funkinterface fur langere Zeit in den Ruhemodus versetzen ohne dabei Nachrichten zu verpassen. Der verwendete hybride TDMA-CSMA-Algorithmus kann weiterhin auch eine Kanalreservierung realisieren. Verbreiteter ist allerdings der Beacon-lose Modus. Hier kommt ein einfacher CSMA-CA-Algorithmus zum Einsatz, bei dem auf eine Synchronisierung der Knoten verzichtet wird.
