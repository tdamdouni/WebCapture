# Normalisierung ? logische Regeln zur Minimierung von Redundanz

_Captured: 2015-09-26 at 10:31 from [www.php-kurs.com](http://www.php-kurs.com/normalisierung.htm)_

Durch die Normalisierung und die strengen Regeln soll eine korrekte, relationale Datenbank aufgebaut werden bzw. diese erhalten bleiben. Dabei ist wichtig, dass Redundanzen vermieden werden, da diese sonst schnell bei Änderungen von Inhalten zu Inkonsistenzen fuhren.

Dabei bedeutet **Redundanz** (lateinisch redundare „im Überfluss vorhanden sein") auf Deutsch **Doppelung bzw. Überschneidungen**.

**Inkonsistenzen** bedeutet: **Widerspruchlichkeit oder Unbestandigkeit** der eingegebenen Daten.

**Als Beispiel:** Mitarbeiter pflegen die Daten der Kundendatenbank. Dazu kann bei jedem Kunden die PLZ und der Ort unabhangig voneinander eingetragen werden.

Der erste Mitarbeiter tragt nun einmal als PLZ „72070" und als Ort „Tubingen" ein. Der zweite Mitarbeiter als PLZ „72070" und als Ort „Tubingen am Neckar" ein ? es liegt schon eine Inkonsistenz vor. Der nachste Mitarbeiter tragt fur den nachsten Kunden als PLZ wieder „72070" ein und als Ort dann „Tuebingen". Und der vierte Mitarbeiter tragt (weil er eine Großschreiballergie hat, dann als Ort „tubingen" ein.

Am Abend kommt der Chef und lasst sich einer Statistik ausgeben, wie viele Kunden aus „Tubingen" eingetragen wurden ? er bekommt nur einen. Hatte er mit der PLZ „72070" die Statistik erstellt, hatte er 4 Kunden angezeigt bekommen.

Dieses Beispiel zeigt, wie schnell eine Datenbank (bedingt durch Ihren Aufbau) zu unbestandigen Daten (sprich Inkonsistenzen) und den entsprechenden Folgeproblemen fuhren kann. Ware hier die Redundanz (Eingabe von PLZ und zusatzlich Ort) unterbunden worden, waren Folgeprobleme vermieden worden.

Es gibt sechs Schritte, wobei in der Praxis die ersten drei umgesetzt werden.

Da die einzelnen Stufen der Normalisierung aufeinander aufbauen, muss die Reihenfolge der Anwendung der Normalisierung eingehalten werden. Es kann die 2. Normalisierung erst angewendet werden, wenn die 1. Normalisierung erfullt ist.

## Zweck der Normalisierung

Durch Anwendung der Normalisierung soll die Integritat der Daten sichergestellt werden.

  * Redundanzen unterbinden
  * Inkonsistenzen vermeiden

Die Wartung der Daten wird i.d.R. vereinfacht, die Programmierung allerdings aufwendiger.

## Erste Normalform (1 NF)

Jedes Datenfeld darf nur **gleichartigen Inhalt** enthalten (Beispiel: aus einem Datenfeld „Name" entstehen zwei Datenfelder: eines fur den Vornamen und eines fur den Nachnamen). Dies wurde im Kapitel „Daten strukturieren - Voruberlegungen zur Datenbankerstellung" als Inhalte trennen (atomisieren) bezeichnet.

Beispiel:

Aus dem Feld „name" mit dem Inhalt „Erika Schmiedt" werden die 2 Datenbankfelder „vorname" und „nachname". Das Feld „vorname" bekommt als Inhalt „Erika" und das Feld „nachname" den Inhalt „Schmiedt".

Mit gleichartig ist hier gemeint, dass im Feld „vorname" dann durchaus auch 2 Vornamen auftauchen: „Karl Heinz". Dies muss immer im Hinblick der zu erstellenden Anwendung geschehen ? die kleinsten sinnvoll erscheinenden Bestandteile konnen sehr unterschiedlich sein. Bei einem Handyhandler kann die Telefonnummer durchaus in 2er Gruppen aufgeteilt angebracht sein, weil er aus den 2er Zahlenkombinationen Ruckschlusse ziehen kann ? der Zoohandel ums Eck wird die Telefonnummer am Stuck belassen.

Fur die Tabelle muss ein Primarschlussel vorhanden sein, damit jeder Datensatz eindeutig angesprochen werden kann.

## Zweite Normalform (2 NF)

Die erste Normalform muss erfullt sein! Erst wenn die erste Normalform erfullt ist, kann man an die Anwendung der zweiten Normalform gehen.

Die 2. Normalform besagt: Jeder Datensatz bildet **nur einen Sachverhalt** ab. Liegen in einer Tabelle Daten vor, die nicht nur 1 Sachverhalt abbilden, werden diese Daten in einzelne thematische Tabellen unterteilt.

In unserem Beispiel liegt die Kundendatenbank vor Anwendung der zweiten Normalform mit folgenden Inhalten vor:

IdVornameNachnameAuftragsnummerArtikel

1
Axel
Pratzner
32482
Buch MySQL lernen

2
Axel
Pratzner
32482
DVD-Rohlinge

3
Elke
Schmidtz
32483
Buch MySQL lernen

Diese Tabelle bildet 3 Sachverhalte ab:

  1. Kundendaten
  2. Artikeldaten
  3. Auftragsdaten

Nach der 2. Normalform muss hier eine Trennung in thematische Tabellen stattfinden. Wir teilen also die Tabelle in die 3 thematischen Tabellen „Kundendaten", „Artikeldaten" und „Auftragsdaten"

### Tabelle Kundendaten:

Kunden-idVornameNachname

1
Axel
Pratzner

2
Elke
Schmidtz

### Tabelle Artikeldaten:

Artikel-idArtikel

1
Buch MySQL lernen

2
DVD-Rohlinge

### Tabelle Auftragsdaten:

Bestell-idAuftragsnummerKunden-idArtikel-id

1
32482
1
1

2
32482
1
2

3
32483
2
1

## Dritte Normalform (3 NF)

Die erste und zweite Normalform muss erfullt sein! Erst wenn die 1. und 2. Normalform erfullt ist, kann man an die Anwendung der 3. Normalform gehen.

Bei der dritten Normalform geht es den indirekten (transitiven) Abhangigkeiten an den Kragen. In der Fachliteratur wird von transitiven Abhangigkeiten gesprochen.

Im folgenden Beispiel haben wir in der Tabelle neben Namen auch PLZ und Ort. Zu jedem Namen gehort eine PLZ und zu jeder PLZ gehort ein Ort. Der Ort ist also indirekt vom Namen abhangig.

Mathematisch ausgedruckt sieht das so aus:

„wenn NAME -> PLZ" und „PLZ -> ORT" dann „Name -> ORT".

„Name -> ORT" ist also eine transitive Abhangigkeit

Wir wollen aber in der Tabelle nur direkte Abhangigkeiten (also intransitive).

Als Tabelle **vor der Anwendung der 3. Normalform** hat unser Beispiel folgendes Aussehen:

Schmidtz
72074
Tubingen

**Nach Anwendung der 3. Normalform** haben wir 2 Tabellen:

Schmidtz
72074

Und

72074
Tubingen
