# Testen in der Softwareentwicklung: Klassisch oder agil?

_Captured: 2017-04-25 at 12:14 from [blogs.itemis.com](https://blogs.itemis.com/de/testen-in-der-softwareentwicklung-klassisch-oder-agil?utm_campaign=Agile&utm_medium=email&_hsenc=p2ANqtz-8QxTH1dKxvOzZhORnNJRXDZjpJyIJLeMRhi_v1ZhkrdiblQzrT9I5ofWVYN6VNAsEKmWgjiJ1IYTBaE5UI5CF3fbJLSQ&_hsmi=51139874&utm_content=51139874&utm_source=hs_email&hsCtaTracking=cf257a07-68ba-48e2-b5dd-f8531c263f49%7Ce847cc06-63c5-40e2-b726-b278fc0f0959)_

Tests sind in der Softwareentwicklung unumganglich. Doch welche Moglichkeiten gibt es, die Testphase ins Projekt einzubinden - oder spart ganz auf Test zu verzichten Ende doch am meisten Zeit?

## Quality Assurance im klassischen Wasserfall-Modell

Als ich nach meinem Studium angefangen habe, zu arbeiten, wurde die Rolle _Tester_ nicht gerade als Traumrolle im Projekt bezeichnet - trotzdem habe ich sie ubernommen. In dem Projekt, in dem ich mitarbeitete waren mehrere Teams (insgesamt uber 100 Personen) von unterschiedlichen Lieferanten fur einzelne Module - Datenbank, Business Logik, Workflow Engine, usw. - verantwortlich.

An meinem ersten Arbeitstag habe ich eine kurze Einarbeitung zum Thema „Testen" erhalten: Es gab eine Web-Oberflache, uber die ich eine XML-Nachricht an einen Service schicken musste. Daraufhin wurde eine Exception ausgeworfen, die per Mail (Bugzilla war noch nicht vorhanden bzw. wurde nicht benutzt) an einen Architekten und Leiter eines Entwicklungsteams geschickt wurde. Mir war allerdings absolut nicht klar, was durch das Verschicken dieser XML-Nachricht uberhaupt passierte. Was testete ich eigentlich?

Das Projekt, in dem ich arbeitete, folgte dem klassischen Wasserfall-Modell. Zu Beginn des Projektes wurde nichts automatisiert. Die meistens Tests wurden wiederholt, sobald ein neuer Fix geliefert wurde. Durch die Fixes tauchten jedoch zum Teil neue Fehler auf. Die Quality Assurance-Phase war demzufolge nicht fest planbar.

Die Phasen in einem klassischen Projekt sehen wie folgt aus:

![Testphase-Wasserfall-Modell-klassisch.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Agile/Testphase-Wasserfall-Modell-klassisch.png?t=1493109075743&width=316&height=37&name=Testphase-Wasserfall-Modell-klassisch.png)

Wie auch in "meinem" Projekt findet die Testphase erst nach der Entwicklung statt. In dieser hat das Testteam in erster Linie die Aufgabe, alle Fehler - so genannte Bugs - im System zu identifizieren. Allein hier hat man laut der IBM Sciences Systems Institute ungefahr den dreifachen Aufwand im Vergleich zur Entwicklungsphase. Liegen gravierende Fehler - sogenannte Blocker Bugs - vor, muss man sogar davon ausgehen, dass die gesamte Testphase nach deren Fix erneut gestartet wird. Je spater ein Bug in der Softwareentwicklung entdeckt wird, desto hoher sind die Kosten - und die Wahrscheinlichkeit, dass das Projekt scheitert.

![Wasserfall-modell-klassisch-kosten.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Agile/Wasserfall-modell-klassisch-kosten.png?t=1493109075743&width=261&height=146&name=Wasserfall-modell-klassisch-kosten.png)

## Quality Assurance in agilen Projekten

Die meiste Zeit verbrachte ich als Tester also damit, Bugs zu finden, diese zuruckzumelden und auf eine Ruckmeldung zu warten - um erneut testen zu konnen, ohne zu verstehen, was ich eigentlich testete. Da mich dieser Ablauf nicht zufrieden stellte, anderte ich meine Vorgehensweise. Nachdem ich einen Bug gefunden hatte, begab ich mich direkt auf die Entwicklungsebene und ubernahm die Analyse der Fehlerursache selbst. Erst danach gab ich meine Ergebnisse dann an das die Kollegen im Workflow-Management- oder Entwicklungsteam weiter. Fixes wurden entsprechend viel schneller geliefert, da die Entwickler sich nicht erst mit der Analyse auseinandersetzen mussten.

Ohne es zu wissen, hatte ich den Weg Richtung Agilitat eingeschlagen. Der Fokus in der agilen Softwareentwicklung liegt unter anderem auf der Qualitat des Systems. Das [Manifesto fur Software-Craftmanship](http://manifesto.softwarecraftsmanship.org/) geht dabei noch einen Schritt weiter als [das Manifest fur agile Software-Entwicklung](http://agilemanifesto.org/iso/de/manifesto.html) und besagt:

_Not only working software, but also **well-crafted software**_

Kein Wunder, dass sich die Phasen eines agilen von denen eines klassischen Software-Projektes unterscheiden:

![Testphase-agile-software-entwicklung.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Agile/Testphase-agile-software-entwicklung.png?t=1493109075743&width=291&height=99&name=Testphase-agile-software-entwicklung.png)

Die Quality-Assurance-Phase wird wie in klassischen Projekten nach der Entwicklung geplant, allerdings werden die Quality Engineers (Tester) bereits in den fruheren Phasen mit einbezogen. Wahrend der Planning-Phase setzen sie sich mit den einzelnen Fachbereichen zusammen und definieren Akzeptanzkriterien, anhand derer spater getestet werden kann.

Wahrend der Entwicklung sind sie ein Teil des Entwicklungsteams. Das Entwicklungsteam schreibt so viele [Unit (Komponenten-) Tests](https://de.wikipedia.org/wiki/Modultest) wie moglich, um die vorab gemeinsam definierten Akzeptanzkriterien zu prufen. Diese Unit Tests sind zeitsparend und liefern schnelle Ergebnisse.

Dadurch, dass die Quality Engineers bereits wahrend der Entwicklungsphase eingebunden sind, bringen sie das erforderliche technische Know-How mit. Dieses Know-How ermoglicht es ihnen festzustellen, welcher Fachlichkeit bereits uber die Unit Tests gepruft wurde. Die Fachlogik, die durch Unit Tests bereits abgedeckt ist, muss nicht auch uber [Integrationstests](https://de.wikipedia.org/wiki/Integrationstest) oder sogar uber UI Tests erneut gepruft werden. Dies lasst sich nur gut vermeiden, wenn die Quality Engineers die bereits realisierten Tests verstehen und darauf aufbauend die weiteren Testfalle automatisieren.

Weitere End-To-End Tests - die ggf. sehr zeitaufwendig sind und dazu neigen sehr fragile zu sein - werden dann in die Quality-Assurance-Phase automatisiert oder falls nicht automatisierbar, manuell durchgefuhrt. Die nicht-automatisierbaren Tests sollten einem Testkatalog hinzugefugt werden, so dass diese bei jedem Release sorgfaltig durchgefuhrt werden konnen.   
Bestimmte Tests, z.B. nicht-funktionale Tests, konnen am besten nur in einer produktionsreife Umgebung durchgefuhrt werden. Auch hier gibt es die Moglichkeit diese zu automatisieren.

Mit diesem Vorgehen lasst sich die Testphase gut einplanen. Die Risiken, dass die Planung nicht passt, lassen sich dadurch vermeiden, dass zum einen die Testdurchfuhrung bereits in fruhen Phasen des Projektes stattfindet und zum anderen schnelles Feedback aufgrund von agilem Vorgehen ermoglicht wird.

## Vielleicht sparen keine Tests doch am meisten Zeit?

Das regelmaßige Testen in agilen Software-Projekten mag auf den ersten Blick aufwandig und zeitfressend erscheinen - die Versuchung, die Test doch halbherzig ans Ende des Projektes zu verbannen, ist entsprechend hoch. Wie [Robert C. Martin ](https://8thlight.com/blog/uncle-bob/2013/03/05/TheStartUpTrap.html)schon sagte: „Anybody who thinks they can go faster by not writing tests is smoking some pretty serious shit."

Die Illusion, dass man Zeit spart, in dem man keine Tests schreibt, holt einen also sehr schnell ein - kostet es doch weit mehr Zeit, Fehler, die fruhzeitig entdeckt hatten werden konnen, wieder auszubugeln.

Du willst mehr zum Thema Testen in der Softwareentwicklung erfahren? Dann schau dich weiter in unserem Blog um und informiere dich zum Beispiel uber das Prinzip der testgetriebenen Softwareentwicklung.
