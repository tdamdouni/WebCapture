# Primär- und Fremdschlüssel

_Captured: 2015-09-26 at 10:28 from [www.php-kurs.com](http://www.php-kurs.com/primaerschluessel-und-fremdschluessel.htm)_

## Primärschlüssel

Bei den Adressen haben wir die ID ? diese ist der Primarschlussel der Tabelle "Adressen". In dieser Spalte enthaltene Werte durfen nur ein einziges Mal vorkommen. Duplikate sind niemals erlaubt! Ein anderer Primarschlussel ist in der Tabelle "PLZ" die Spalte "plz" und in der Tabelle "Anrede" die Spalte "kuerzel".

Die primare Bedeutung des Primarschlussels kommt dann zum Tragen, wenn man 2 Tabellen verknupft (in Beziehung setzt).

## Fremdschlüssel

Was bei der Verknupfung in der einen Tabelle der Primarschlussel ist, ist in der zweiten Tabelle der Fremdschlussel. Der Fremdschlussel enthalt den gleichen Wert wie der Primarschlussel, kann aber ofters vorkommen (je nach Beziehungsart). So kann er einmal, keinmal oder mehrmals vorkommen.

In unserem Beispiel ist bei der Tabelle "PLZ" das Feld plz der Primarschlussel und in der Tabelle "Adressen" das Feld PLZ der Fremdschlussel (kann ofters vorkommen).

Bei der Tabelle "Anrede" ist das "akuerzel" der Primarschlussel und in der Tabelle "Adresse" die Spalte "akuerzel" der Fremdschlussel.

Zum Verleich nochmals unsere Tabellen, in dem die Schlusselfelder farblich hervorgehoben sind.

**Tabelle: Adresse**:

id nachname vorname akuerzel strasse plz telefon

1
Muller
Fritz
m
Hauptstr. 12
72070
07071-555-12312

2
Simmer
Susi
w
Herbstallee 1
72074
07071-555-654654

3
Sommer
Susi
w
72074
07071-555-64444

**Tabelle: Plz**:

plz ort

72070
Tubingen

72074
Tubingen

**Tabelle: anrede**:

akuerzel anrede

w
Frau

m
Herr

**Tabelle: anrede**:
