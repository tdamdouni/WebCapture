# Content-Delivery mit GitHub: So nutzt du den Hosting-Dienst als passives CDN

_Captured: 2015-11-30 at 09:55 from [t3n.de](http://t3n.de/news/content-delivery-github-nutzt-660501/?utm_source=feedburner+t3n+News+12.000er&utm_medium=feed&utm_campaign=Feed%3A+aktuell%2Ffeeds%2Frss+%28t3n+News%29)_

Auf GitHub werden viele der Projekte, Frameworks und Toolkits gehostet, die wir taglich benutzen. Egal ob jQuery, AngularJS oder [Polymer](http://t3n.de/news/power-project-polymer-639425/) - alle finden wir auf GitHub wieder. GitHub bietet auch die Auslieferung „Raw" an - hier wird eine Datei im Raw-Format direkt uber eine URL ausgeliefert. Wofur dann noch ein CDN?

## Was sind die konkreten Vorteile von einem CDN?

Ein CDN ist dafur konzipiert, dem Endverbraucher Daten auf dem schnellsten und okonomischsten Weg bereitzustellen. Die sogenannten CDN-Knoten sind uber die ganze Welt verteilt, abhangig vom Anbieter, und liefern Inhalte auf dem bestmoglichen Weg aus. Das Network, und somit die CDN-Server, sind darauf getrimmt, einen schnellen Response zu ermoglichen. Benutzer sollen die Daten in kurzester Zeit erhalten. Das ist naturlich essentiell wichtig bei einer guten Webseite. Sollte zum Beispiel jQuery nicht schnell genug vom Server abgerufen werden konnen, muss der Rest auch warten - und damit auch der Besucher.

Außerdem soll ein CDN Server-Ausfalle kompensieren. Fallt unser Webhosting-Server aus, sind meist alle Daten nicht mehr erreichbar. Bei einem CDN wurde in diesem Fall ein anderer CDN-Knoten einspringen, um die Gewahrleistung der Auslieferung sicherzustellen. Der weitere große Vorteil eines CDN ist das Caching. Umso mehr Entwickler das gleiche CDN, zum Beispiel fur jQuery, benutzen, umso hoher ist die Wahrscheinlichkeit, dass der Endverbraucher diese Datei schon im Cache hat. Sollte der Browser entdecken, dass das bei einer angeforderten Datei schon der Fall ist, brauch sie nicht noch mal geladen zu werden. Der Einsatz eines CDN ist also definitiv zu empfehlen. Was aber tun, wenn unsere benotigte Datei nicht auf einem CDN bereitgestellt ist? Ganz einfach: Mit RawGit losen wir das Problem.

## Mit RawGit und dem Max-CDN Licht ins Dunkel bringen

Auf GitHub konnen wir Code in einem Repository bereitstellen, es als CDN zu benutzen, ist aber nicht vorgesehen. Alle Dateien, die uber die [GitHub-Raw-Funktion ](https://raw.githubusercontent.com/jquery/jquery/master/test/jquery.js)eingebettet werden, erzeugen meist Fehler. Egal ob HTML, CSS oder JavaScript - GitHub lasst alle Dateien mit dem Content-Type `text/plain` ausliefern. Probieren wir, JavaScript mit einem solchen Content-Type einzubetten, erhalten wir direkt einen Fehler in der Console. Zudem ist eine der wichtigsten Funktionen eines echten CDN deaktiviert - das Caching. Alle Dateien, die uber die Raw-Funktion erzeugt werden, haben nur eine Lebensdauer von funf Minuten im Cache. Diese Einstellung ist von GitHub bewusst gewahlt worden, um den Missbrauch als CDN zu unterbinden.

Trotzdem bleibt weiterhin der Punkt, dass auf GitHub die meisten Frameworks bereitgestellt werden. Damit wir trotzdem die Moglichkeit haben, bestimmte Libraries, die nicht in einem Open-CDN bereitgestellt sind, nutzen zu konnen, gibt es RawGit. RawGit macht nichts anderes, als die gewahlte Datei in einem GitHub-Repository zu parsen und uber den beliebten [Max-CDN ](https://www.maxcdn.com/) auszuliefern. Damit wird automatisch das Caching aktiviert, der richtige Content-Type angehangt und ermoglicht, dass alle Dateien auf GitHub uber ein CDN kostenfrei und einfach ausgeliefert werden konnen.

Fur die Generierung muss nur die ausgewahlte Datei mit dem GitHub-Link in das oberen Input-Feld von [RawGit ](https://rawgit.com/) kopiert werden und wir erhalten direkt unseren CDN-Link. Einfacher und schneller geht es nicht.

**Benutzt ihr auch regelmaßig einen CDN-Service?**
