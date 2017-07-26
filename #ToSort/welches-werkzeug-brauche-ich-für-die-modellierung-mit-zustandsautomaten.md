# Welches Werkzeug brauche ich für die Modellierung mit Zustandsautomaten?

_Captured: 2017-05-10 at 21:54 from [blogs.itemis.com](https://blogs.itemis.com/de/welches-werkzeug-brauche-ich-f%C3%BCr-die-modellierung-von-zustandsautomaten?utm_source=hs_email&utm_medium=email&utm_content=51748968&_hsenc=p2ANqtz-8hawwg8DAepwoP2ciwX-htxnmPnEDY7ENH059VJgMrMnXq9apGaq8axqTRNijni3v_rACUwpHhY4l8ihsWCAvVi7s72A&_hsmi=51749262)_

In meinem letzten Artikel habe ich euch von Emil erzahlt. Er und sein Entwicklerteam kamen mit der [Weiterentwicklung in ihrem Projekt](https://blogs.itemis.com/de/brauchen-auch-werkzeugketten-ein-refactoring) nicht mehr weiter. Ihr Modellierungswerkzeug behinderte ihre Arbeit bei der Entwicklung einer selbstregulierenden Steuerung fur Ampelsysteme mehr als es sie unterstutzte.

Nun setzten sie sich zusammen und definierten die Anforderungen an ihr Modellierungswerkzeug neu - denn klar definierte Anforderungen sind die notwendige Grundlage fur die Wahl eines Modellierungswerkzeug, welches das Team unterstutzt und voranbringt.

Modellierungswerkzeuge gibt es reichlich. Es gibt die großen und teuren, die alles konnen (mochten). Kleinere Programme haben meist weniger Features. Doch wenn dies genau diejenigen Features sind, die unser Projekt braucht, was wollen wir mehr?

Fur Zustandsautomaten ist vielleicht [YAKINDU Statechart Tools](https://www.itemis.com/en/yakindu/state-machine/) das richtige Werkzeug. Diese Software bundelt Modellierung, Simulation und Codegenerierung von Finite-StateMachines zu einem schlanken, robusten Werkzeug. Sowohl UML-2.0-, Harel-, Mealy- und Moore-Automaten sind moglich. Die großen Starken der Statechart Tools sind der Simulator und die anpassbare Codegenerierung fur verschiedene Zielsprachen wie C, C++ oder Java. Auch ein selbst geschriebener Generator fur eine eigene Zielsprache (vgl. [domanenspezifische Sprachen](https://de.wikipedia.org/wiki/Dom%C3%A4nenspezifische_Sprache)) ist realisierbar.

## Was kann YAKINDU Statechart Tools, das andere nicht konnen?

Seit nunmehr zehn Jahren wird YAKINDU Statechart Tools entwickelt, so dass wir es zu den ausgereiften Werkzeugen zahlen durfen, ahnlich Enterprise Architect, Matlab Simulink oder Stateflow. Enterprise Architect besitzt jedoch keine formale Ausdruckssprache und als Konsequenz daraus keine Moglichkeit der Validierung, keine Code Completion und keine Typsicherheit bei allen formalen Ausdrucken. Die Fahigkeit der adaquaten [Simulation und Validierung wird dadurch ebenfalls beschrankt](https://blogs.itemis.com/en/eclipse-based-uml-validation-of-enterprise-architect-models). Hier liegt die Starke von YAKINDU Statechart Tools.

Fur Embedded-Entwickler bietet YAKINDU Statechart Tools die Moglichkeit, auf eigenen C-Variablen, -Konstanten oder -Funktionen direkt aus dem Zustandsautomaten heraus zuzugreifen. Arbeitet ein Team mit anderen Werkzeugen, die eine derart weitreichende C-Integration nicht bieten, werden sie zahlreiche Arbeitsstunden in die Verknupfung von Modell und C-Code stecken. Diese Zeit lasst sich sinnvoller nutzen…

Das Headless-Build-Feature ermoglicht es, den Codegenerator in den automatischen Build-Prozess einzubinden - ebenfalls ohne wertvolle Arbeitsstunden in das manuelle Anstoßen der Codegenerierung uber die grafische Oberflache des Werkzeugs stecken zu mussen. Die Codegenerierung erfolgt ohne weiteres Zutun automatisch innerhalb des Build-Prozesses.

## Welche Anforderungen mussen erfullt werden?

Ein Werkzeug muss nicht umfassend, groß und monolithisch sein. Es muss nur genau die richtigen Features bieten, welche die Entwicklung heute voranbringen. Was zahlt, ist die Entwicklung hier und jetzt, nicht Projekte und Themen, die vielleicht in Zukunft auch noch kommen werden.

Emils Team hat seine Anforderungen noch einmal uberarbeitet. Das großte Problem des Modellierungswerkzeugs ist der Generator. Er macht dem Team mehr Probleme, als er lost. Das fur Emils Team perfekte Modellierungstool…

… unterstutzt UML 2.0-Zustandsautomaten,

… kann verlasslich validieren und simulieren,

… besitzt einen leistungsstarken, konfigurierbaren Generator fur C, der vorhersehbaren Quellcode produziert,

… lasst sich einfach in den bestehenden Build-Prozess integrieren.

Wenn man sich die oben beschriebenen Features anschaut, konnte es sein, dass YAKINDU Statechart Tools eine passende Losung ist. Denn vor allem die Typsicherheit ermoglicht eine verlassliche Modellvalidierung. Sie bietet eine belastbare Basis fur Codegenerierung. Dass sich YAKINDU Statechart Tools einfach in den Build-Prozess integrieren lasst, spart Arbeitszeit der Entwickler und diese konnen sich auf das eigentliche Entwicklungsziel konzentrieren und sind weniger durch Aufgaben abgelenkt, die nicht direkt zum Produkt beitragen.

Ich bin gespannt, was mir Emil demnachst berichtet. Fur welches Werkzeug entscheidet sich das Team? Wie wird die Migration? Ich werde berichten.

Übrigens: Wenn ihr YAKINDU Statechart Tools selbst einmal ausprobieren mochtet, ladet es euch einfach auf unserer Website herunter.
