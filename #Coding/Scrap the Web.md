# Scrap the Web

_Captured: 2015-12-05 at 11:29 from [ini20.de](http://ini20.de/2014/04/scrab-the-web/)_

![image01](http://ini20.de/wp-content/uploads/2014/04/image01.png)

Das Internet, unendliche Weiten. Wir befinden uns zwar nicht in einer fernen Zukunft oder Galaxie und doch sind wir bereits seit einiger Zeit an einem Punkt, besser auf einem Weg, in dem Technologie eine sehr große Rolle in unserem Leben eingenommen hat. Das Internet als Vorzeigeprimus an Informationstechnologie und Vernetzung wird jederzeit genutzt, um Informationen auszutauschen. Aus den unterschiedlichsten Grunden werden dabei viele Informationen nicht nur kurzfristig ubertragen, sondern fur lange Zeit gespeichert.

„Das Internet vergisst nie". Diese Aussage ist im Grunde nur die halbe Wahrheit, denn das Internet selbst ist kein zentraler Computer und hat auch im eigentlichen Sinne kein Gedachtnis, also Speicherung und Auswertung von Daten. Es sind die TeilnehmerInnen, die alle einzeln diese Aufgaben ubernehmen. TeilnehmerInnen sind wie vom Wortstamm zu erkennen, alle, die im Internet irgendwie aktiv sind, jeder Privatnutzer und jede Firma. Jede/r TeilnehmerIn generiert und konsumiert Daten als Information.

Viele dieser Informationen werden in großen Mengen gesammelt. Durch Synergieeffekte sind die Datenhaufen mehr wert als jede Information einzeln fur sich genommen. Der Wert dieser Datenhaufen ist fur Unternehmen bares Geld, welches sie direkt (z.B. durch Abos) oder indirekt (z.B. durch Werbung) einnehmen konnen.

# Strukturierte Daten im Internet

Die Daten sind dabei allerdings nicht bloß wahllos aneinander gereiht, sondern werden durch verschiedene Techniken in Struktur gebracht bzw. gehalten. Das typische Beispiel sind Datenbanken, wo Informationen als einzelne Eintrage in Tabellen, Graphen oder Objekten miteinander verknupft werden und somit sowohl technisch als auch fachlich miteinander verbunden sind. Erst durch diese Strukturierung konnen die meisten Daten sinnvoll verwendet werden. Diese Struktur steht jedoch nicht direkt im Internet zur Verfugung, da sie meist sehr technisch und selbst von versierten Nutzern nur unbequem zu lesen ist. Vielmehr werden die Daten mit HTML-Code umstrukturiert und aufbereitet und uber das Internet versendet. Der Browser interpretiert dann diesen Code, um eine optisch ansprechende Anzeige zu erzeugen. Die meisten Informationen sind dabei nach wie vor vorhanden, aufgeteilt auf verschiedene Seiten.

Ziel von Web Scraping ist es, die verfugbaren Daten wieder in eine Struktur zu bringen, um sie danach weiter zu verwenden. Hierbei ist es meist unerheblich, dass wieder exakt die alte Struktur hergestellt wird, sondern vielmehr, dass nach dem Scraping die Daten weiter verwendbar sind.

![](https://lh3.googleusercontent.com/bCnYslkf2jR7VBNCyaSpSTJLZhQo6uClErCvE5tEz4CDtoukEU-0H-hYlIaB8WZq05E5qypLd3aKqmJOFQ3vy4mfrzZ6nD-QkQBjbVYCTD6hszURkGncStzQlOLCcY-jluvt3g)

Der Vorgang des Web Scraping besteht aus zwei Teilaufgaben. Erst werden Daten gesammelt, um sie danach in irgendeiner sinnvollen Art zur weiteren Verwendung aufzubereiten. Beide Aufgaben konnen dabei sehr unterschiedlich bewaltigt werden. Aufgrund der Masse an Informationen sind diese meist auf verschiedene Webseiten aufgeteilt, die dann einzeln abgearbeitet werden mussen.

# Moglichkeiten das Web zu scrapen

Die einfachste Variante zum Sammeln von Informationen ist das Kopieren per Hand/Maus (aka. Copy & Paste) in eine Textdatei. Dies ist technisch bedingt auf jeder Webseite moglich, da auch der Browser immer Lesezugriff auf den Code haben muss. Dies taugt jedoch nur fur kleinere Bereiche und skaliert aufgrund des Bedarfs an „Humankapital" schlecht in Bereichen wie Big Data.

Alternativ dazu ist es moglich, sich eigene Programme zu schreiben, die ebenfalls das Web durchsuchen. Hier sind die Moglichkeiten nahezu unbegrenzt. Einsteiger konnen direkt mit Programmen wie „cURL" anfangen, um automatisiert Dateien aus dem Internet zu laden und danach selbststandig zu analysieren. Weitaus komplexer sind Programme, die direkt den Browser fernsteuern und damit einen echten Menschen simulieren. Dies hat zum Vorteil, dass die Webseite nicht direkt erkennen kann, ob sie gerade von einem Menschen oder einem Programm betrachtet wird und somit auch Informationen nicht ohne weiteres verstecken kann. Auch hier muss das Rad nicht neu erfunden werden. Es gibt bereits fertige Frameworks und Bibliotheken fur Webentwickler zum Testen der eigenen Seiten. So kann „WebDriver" von [Selenium](http://www.seleniumhq.org/projects/webdriver/) bereits alle gangigen Browser automatisiert fernsteuern und nach Inhalten abfragen. Diese Inhalte werden nicht wie vorgesehen zum Testen verwendet, sondern direkt abgespeichert.

Zu guter Letzt gibt es bereits auf dem Markt vorgefertigte Software, um Web Scraping auch ohne technischen Sachverstand durchfuhren zu konnen. Fur kleinere Projekte ist z.B. der „[Visual Web Ripper](http://www.visualwebripper.com/)" geeignet. Dieser bietet dem Anwender einen integrierten Browser an und uberwacht darin dessen Aktionen. Der Benutzer demonstriert dem Programm dann einmalig per Hand, wie eine bestimmte Webseite zu scrapen ist. Es ist moglich, direkt anzugeben, an welchen Stellen Wiederholungen erfolgen mussen und nach welchen Daten gesucht werden soll. Daraus erstellt „Visual Web Ripper" dann eine Vorschrift und analysiert automatisch eine komplette Webseite und speichert diese in verschiedene Dateiformate.

# Informationen speichern

Je nach Art und Weise des Sammelns gibt es unterschiedliche Moglichkeiten, die Informationen abzuspeichern. Bei fertiger Software sind bereits ein oder mehrere Varianten vorgegeben, aus denen man auswahlen muss. Hier ist naturlich nicht ausgeschlossen, die Daten danach erneut in ein anderes Format oder eine andere Struktur zu bringen. Fur die meisten Scraper ist es sinnvoll, die Daten in irgendeine Art von Datenbank zu stecken. Datenbanken haben den Vorteil, dass sie gewisse Strukturen vorgeben, Verlinkungen von Datensatze ermoglichen und das Abfragen und Auswerten der Daten erleichtern.

Im Allgemeinen gibt es unterschiedliche Datenbankmanagementsysteme. Der Klassiker sind [relationale Datenbanken](http://de.wikipedia.org/wiki/Relationale_Datenbank), basierend auf einfachen Tabellen, wobei die Daten durch technische Schlussel in Relation zueinander stehen. Durch die Verbindung dieser Schlussel konnen so die Daten beim Abfragen verknupft und ausgewertet werden.

Eine Weiterentwicklung zu relationalen Datenbanken sind [Graph-Datenbanken]( http://de.wikipedia.org/wiki/Graphdatenbank). Statt vorgegebener Tabellen werden hier die Daten in Graphen mit Knoten und Kanten gespeichert. Jeder Knoten kann dabei unterschiedlich sein. Durch die Kanten sind die Knoten direkt miteinander vernetzt und der Anwender muss sich nicht selbst um die technische Verknupfung kummern. Bei der Abfrage von Daten setzen Graph-Datenbanken auf bereits bekannte Suchalgorithmen aus der [Graphentheorie](http://de.wikipedia.org/wiki/Suchverfahren#Suche_in_Graphen). Diese durchsuchen den Graphen dann nach passenden Daten. Eine Abfrage ist typischerweise in drei Teilen aufgebaut. Es gibt einen (oder mehrere) Einstiegspunkte in den Graphen, ein Beschreibung zum Abwandern des Graphen und eine Information, welche Daten im Muster gesucht wurden. Graph-Datenbanken eigenen sich aufgrund ihrer einfachen Erweiterbarkeit sehr gut fur Daten, die stark zueinander in Beziehung stehen und sich standig verandern, bzw. erweitern.

Nachdem die beiden Schritte im Web Scraping, Daten sammeln und aufbereiten, abgeschlossen sind, konnen die Daten fur die vorgesehenen Zwecke verwendet werden. Dieser letzte Schritt ist dabei vollkommen abhangig von Zweck der weiteren Datenauswertung und -verwendung und wird daher an dieser Stelle nicht weiter erlautert.

# Schluss

In diesem Artikel wurde nur auf technischen Moglichkeiten des Web Scrapings als Datensammeltool eingegangen. Mit diesen ist es moglich, unterschiedlichste Webseiten nach Informationen zu durchsuchen, zu sammlen und auszuwerten. Denkbar ware z.B. das Sammeln von Fahrplanen des ÖPNV, um eine verbesserte Verbindungssuche bereit zu stellen. Eine weiteres Beispiel ware, Preise von Produkten von verschiedenen Anbietern & Plattformen zu sammeln und zu vergleichen, um ein Produkt moglichst gunstig zu erwerben. Leider ist es nicht immer moglich, die Herkunft einer Information zu bestimmen, da Informationen auch auf andere Weise bereit gestellt werden konnen.

Rechtlich kann Web Scraping als Straftatbestand angesehen werden, wenn die Informationen nicht dazu freigegeben sind, gesammelt und ausgewertet zu werden. Ferner kann das Recht auf [informationelle Selbstbestimmung](http://de.wikipedia.org/wiki/Informationelle_Selbstbestimmung) verletzt sein, wenn der Eigentumer der Daten nicht uber das Web Scraping informiert wird und so nicht in das Geschehen eingreifen kann. Hier ist es aufgrund der Technik derzeit nicht moglich, dies effektiv zu verhindern. Vielmehr ist es notwendig, durch andere Maßnahmen auf gesellschaftlicher, rechtlicher und politischer Ebene vernunftig mit Web Scraping umzugehen.

Autor: Aaron S.
