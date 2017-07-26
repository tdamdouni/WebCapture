# Feature Driven Development

_Captured: 2015-10-23 at 18:23 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Feature_Driven_Development)_

FDD wurde als schlanke Methode von [Jeff De Luca](https://de.m.wikipedia.org/w/index.php?title=Jeff_De_Luca&action=edit&redlink=1) im Jahre 1997 definiert, um ein großes zeitkritisches Projekt (15 Monate, 50 Entwickler) durchzufuhren. Seitdem wurde FDD kontinuierlich weiterentwickelt. FDD stellt den [Feature](https://de.m.wikipedia.org/wiki/Funktionalit%C3%A4t)-Begriff in den Mittelpunkt der Entwicklung. Jedes Feature stellt einen Mehrwert fur den Kunden dar. Die Entwicklung wird anhand eines Feature-Plans organisiert. Eine wichtige Rolle spielt der Chefarchitekt (engl. Chief Architect), der standig den Überblick uber die Gesamtarchitektur und die fachlichen Kernmodelle behalt. Bei großeren Teams werden einzelne Entwicklerteams von Chefprogrammierern (engl. Chief Programmer) gefuhrt.

FDD definiert ein Prozess- und ein Rollenmodell, die gut mit existierenden klassischen Projektstrukturen harmonieren. Daher fallt es vielen Unternehmen leichter, FDD einzufuhren als [XP](https://de.m.wikipedia.org/wiki/Extreme_Programming) oder [Scrum](https://de.m.wikipedia.org/wiki/Scrum). Außerdem ist FDD ganz im Sinne der agilen Methoden sehr kompakt. Es lasst sich auf 10 Seiten komplett beschreiben.

FDD-Projekte durchlaufen funf Prozesse.

  1. Prozess #1: Entwickle ein Gesamtmodell (Rollen: alle Projektbeteiligte)
  2. Prozess #2: Erstelle eine Feature-Liste (Rollen: in der Regel nur die Chefprogrammierer)
  3. Prozess #3: Plane je Feature (Rollen: Projektleiter, Entwicklungsleiter, Chefprogrammierer)
  4. Prozess #4: Entwurf je Feature (Rollen: Chefprogrammierer, Entwickler)
  5. Prozess #5: Konstruiere je Feature (Rollen: Entwickler)
![Prozessmodell in FDD](http://upload.wikimedia.org/wikipedia/de/f/f4/FDD-Graphik.jpg)

> _[Prozessmodell in FDD](https://de.m.wikipedia.org/w/index.php?title=Datei:FDD-Graphik.jpg&filetimestamp=20070515101418&)_

Die ersten drei Prozesse werden innerhalb weniger Tage durchlaufen. Die Prozesse 4 und 5 werden in standigem Wechsel durchgefuhrt, weil jedes Feature in maximal zwei Wochen realisiert wird.

Im ersten Prozess definieren Fachexperten und Entwickler unter Leitung des Chefarchitekten Inhalt und Umfang des zu entwickelnden Systems. In Kleingruppen werden Fachmodelle fur die einzelnen Bereiche des Systems erstellt, die in der Gruppe vorgestellt, ggf. uberarbeitet und schließlich integriert werden. Das Ziel dieser ersten Phase ist ein Konsens uber Inhalt und Umfang des zu entwickelnden Systems sowie das fachliche Kernmodell.

Im zweiten Prozess detaillieren die Chefprogrammierer die im ersten Prozess festgelegten Systembereiche in Features. Dazu wird ein dreistufiges Schema verwendet: Fachgebiete (engl. Subject Areas) bestehen aus Geschaftstatigkeiten (engl. Business Activities), die durch Schritte (engl. Steps) ausgefuhrt werden. Die Schritte entsprechen den Features. Die Features werden nach dem einfachen Schema <Aktion> <Ergebnis> <Objekt> aufgeschrieben, z.B. „Berechne Gesamtsumme der Verkaufe". Ein Feature darf maximal zwei Wochen zu seiner Realisierung benotigen. Das Ergebnis dieses zweiten Prozesses ist eine kategorisierte Feature-Liste, deren Kategorien auf oberster Ebene von den Fachexperten aus Prozess #1 stammen.

Im dritten Prozess planen der Projektleiter, der Entwicklungsleiter und die Chefprogrammierer die Reihenfolge, in der Features realisiert werden sollen. Dabei richten sie sich nach den Abhangigkeiten zwischen den Features, der Auslastung der Programmierteams sowie der Komplexitat der Features.

Auf Basis des Plans werden die Fertigstellungstermine je Geschaftsaktivitat festgelegt. Jede Geschaftsaktivitat bekommt einen Chefprogrammierer als Besitzer zugeordnet. Außerdem werden fur die bekannten Kernklassen Entwickler als Besitzer festgelegt (engl. Class Owner List).

Im vierten Prozess weisen die Chefprogrammierer die anstehenden Features Entwicklerteams auf Basis des Klassenbesitztums zu. Die Entwicklerteams erstellen ein oder mehrere Sequenzdiagramme fur die Features und die Chefprogrammierer verfeinern die Klassenmodelle auf Basis der Sequenzdiagramme. Die Entwickler schreiben dann erste Klassen- und Methodenrumpfe. Schließlich werden die erstellten Ergebnisse inspiziert. Bei fachlichen Unklarheiten konnen die Fachexperten hinzugezogen werden.

Im funften Prozess programmieren die Entwickler die im vierten Prozess vorbereiteten Features. Bei der Programmierung werden Komponententests und Code-Inspektionen zur Qualitatssicherung eingesetzt.

  * Henning Wolf, Stefan Roock, Martin Lippert: _eXtreme Programming_ dpunkt, 2., uberarb. u. erw. Aufl., 2005, [ISBN 3-89864-339-5](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3898643395). Das Buch enthalt auch eine kurze Beschreibung von FDD. Teile dieses Wikipedia-Eintrages basieren mit freundlicher Genehmigung des dpunkt-Verlages auf der Beschreibung im Buch.
