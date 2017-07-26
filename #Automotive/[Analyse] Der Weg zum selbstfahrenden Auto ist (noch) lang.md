# [Analyse] Der Weg zum selbstfahrenden Auto ist (noch) lang

_Captured: 2016-10-31 at 23:32 from [www.cbcity.de](http://www.cbcity.de/analyse-der-weg-zum-selbstfahrenden-auto-ist-noch-lang)_

Seit circa zwei Jahren mischt Google medial massiv im Business der
selbstfahrenden Autos mit. Man hat praktisch den Eindruck, als ob es nur noch
eine Frage des äußeren Erscheinungsbildes ist, welches Fahrzeug Google nun als
Taxiersatz auf die Straßen dieser Welt los lässt.

Ersatz für den privaten PKW, für das Taxigewerbe sowieso und auch Waren- und
Dienstleistungen werden alsbald durch die Self Driving Cars ersetzt, so die
mediale Darstellung. Journalisten und Blogger geben jedes noch so schön
aussehende Foto von selbstfahrenden Autos zum besten und wiederholen Aussagen
über die dinosaurierartige Entwicklungsgeschwindigkeit der deutschen
Automobilhersteller.

Ich möchte mit diesem Beitrag eine kleine Einschätzung zu der aktuellen und
zukünftigen Situation der selbst fahrenden Autos machen.

## Definition des selbstfahrenden Autos

Ein Hauptproblem in der aktuellen medialen Debatte ist sicherlich das pure
Durcheinanderwerfen der Begrifflichkeiten. Ab wann fährt denn ein Auto
‚selbst'?

  1. **Assistiertes Fahren**: Der Fahrer übernimmt dauerhaft Lenken oder Gas/Bremse , das Auto die jeweils andere Funktion, welche der Fahrer aber überwachen muss
  2. **Teilautomatisiertes Fahren**: Der Fahrer muss das Auto dauerhaft überwachen, das Auto übernimmt aber Lenken & Gas/Bremse in einem spezifischen Anwendungsfall, z.B. auf der Autobahn ohne Baustelle oder Sondersituationen.
  3. **Hochautomatisiertes Fahren**: Der Fahrer muss das Auto nicht mehr dauerhaft überwachen, muss aber im Notfall übernehmen können. Das Auto übernimmt aber Lenken & Gas/Bremse in einem spezifischen Anwendungsfall, z.B. auf der Autobahn ohne Baustelle oder Sondersituationen, es erkennt Systemgrenzen selbstständig und fordert den Fahrer zur Übernahme auf.
  4. **Vollautomatisiertes Fahren**: Kein Fahrer erforderlich im speziellen Anwendungsfall, z.B. auf der Autobahn ohne Baustelle oder Sondersituationen, da das System diese definierten Szenarien selbst lösen kann
  5. **Fahrerlose Fahrt**: Von Start bis zum Ziel die vollständig selbstständige Fahrt bei allen Straßentypen und Sondersituationen.

![Schematische Darstellung des Schwierigkeitsgrades nach
Automatisierungsgrad](http://www.cbcity.de/wp-content/uploads/2016/01
/Schwierigkeitsgrad-Automatisierte-Fahrt-770x405.png)

Schematische Darstellung des Schwierigkeitsgrades nach Automatisierungsgrad

Die Vision, die oftmals transportiert wird, ist sicherlich die Stufe 5, in
welcher das Google Auto der Pulsschlag der Großstadt ist und jedermann vor der
Haustür abgeholt und am Arbeitsort abgesetzt wird. „Kein Bedarf mehr an einem
Privat-PKW!", so der Tenor.

## Aktueller Stand der Technik

Genau genommen fahren Autos schon seit den 1980er Jahren vollautonom (siehe
[Projekt
Prometheus](https://de.wikipedia.org/wiki/Prometheus_\(Forschungsprogramm\))),
d.h. ohne das ein Mensch eingreifen muss. Dies allerdings nur in definierten
Szenarien.

Die Welt ist allerdings nicht so einfach, wie man sie gern hätte. Chris Urmson
hat dazu einen schönen TED Talk gegeben, in dem er zeigt, welche Dinge im
Alltag auf so ein Computersystem zukommen.

So lange man auf Autobahnen unterwegs ist, d.h. alle Fahrzeuge in die gleiche
Richtung fahren, es keine engen Kurven gibt, keine Radfahrer oder Fußgänger,
kein kreuzender Verkehr, und vieles mehr nicht, mag die Situation gewissen
Gesetzmäßigkeiten folgen, die man relativ gut in Algorithmen festhalten kann.

  * halte Abstand zum Vordermann größer als Sicherheitsabstand
  * fahre in der Mitte der Spur, welche durch 2 Linien gekennzeichnet ist
  * fahre Geschwindigkeit gemäß Verkehrszeichen, sonst Richtgeschwindigkeit
  * wechsle nicht die Spur, wenn dort ein Fahrzeug ist oder sich mit hoher Geschwindigkeit von hinten eines nähert
  * …

Diese Funktionen finden dieser Tage ihren Weg in Serienfahrzeuge der
Oberklasse. Auf Autobahnen können Fahrzeuge aktuellen Baujahres gemäß Stufe 3
hochautomatisiert fahren. Die begrenzenden Szenarien bleiben allerdings. Eine
Missachtung dieser Anwendungsfälle führt zum Ausfall des Systems, d.h. der
Fahrer muss jederzeit die Situation übernehmen können.

Bleibt die Frage, wann Stufe 4 und 5 erreicht wird?

Im erst kürzlich veröffentlichten Bericht „[Google Self-Driving Car Testing
Report on Disengagements of Autonomous Mode December 2015](http://static.googl
eusercontent.com/media/www.google.com/de//selfdrivingcar/files/reports/report-
annual-15.pdf)" kann man ein paar Zahlen zu Ausfällen der aktuellen Google
Testflotte nachlesen. Auch hier wird deutlich, dass die autobahnähnlichen
Szenarien nicht das größte Problem sind. Nimmt man die Fahrfehler auf
Interstate+Freeway+Highway zusammen (37), so waren diese trotzdem nur knapp
1/10 der Ausfälle im innerstädtischen Verkehr (304 zwischen Sep. 2014 und Nov.
2015) gewesen. Google sagt allerdings, dass hauptsächlich in städtischen
Szenarien gefahren wurde, eben weil dies noch zu verbessern ist.

## Komplexität und Schwierigkeit

Ein Computer, auch wenn er neuerdings mit ‚Artificial Intelligence'
ausgestattet wird, ist nicht sehr schlau. Er kann bestimmte Situationen extrem
gut und wesentlich besser als der Mensch meistern (Abstand zum Vordermann
konstant halten), andere wiederum überhaupt nicht. Nehme man als Parameter für
die Komplexität des Straßenverkehrs nur folgende 5, so versteht man schon, wo
das Problem liegt:

**Parameter**
**Autobahn**
**Stadt**

**Fahrspur**
breit, geradeaus

eng und nicht exclusiv

**Fahrtrichtung**
alle gleich

von und in alle Richtungen

**Verkehrszeichen**
wenige an definierten Stellen

Ampeln, Vorfahrt, … an undefinierten Stellen

**Verkehrsteilnehmer**
nur Kraftfahrzeuge

Kraftfahrzeuge, Fußgänger, Radfahrer, Gruppen, Tiere, Bierbikes, Rollstühle, …

**Sicht**
weit

eingeschränkt/verdeckt



Noch nicht mitbedacht sind alltägliche Situationen, wie Blickkontakt an
Fußgängerüberwegen oder Fahranfänger, die einen ‚durch winken' oder Autos, die
ohne Blinken unlogische Manöver fahren. Normaler Großstadt-Berufsverkehr, wie
ihn jeder, jeden Tag meistert.

Die Fehlerquote würde exponentiell nach oben schnellen, wenn man die auf
Autobahn funktionierenden Systeme im innerstädtischen Berufsverkehr fahren
lässt.

## Fehlerquote und 100% Sicherheit

Chris Urmson spricht das Thema in seinem TED Talk an: Einfach bestehende
Technik zu nehmen und etwas an den Algorithmen zu optimieren wird schwerlich
die nächste Stufe im Automatisierungsgrad erreichen.

### Beispiel Spurerkennung

Ein kleines Beispiel: Eine Spurverlassenswarnung, d.h. ein System was die
Fahrspur erkennt und gegenlenkt, sobald man diese verlässt, verhindert
vielleicht alle 100.000km einen Unfall. Fällt sie in dem Moment aus, hat sie
eine Fehlerrate von 1/100.000km. Man sagt auch: 10 DPMO ([Defects per Million 
Opportunities](https://en.wikipedia.org/wiki/Defects_per_million_opportunities
)). Dies entspricht einem korrekten Verhalten in 99,999% der Fälle! Eigentlich
ziemlich überzeugend, oder?

* * *

Menschen sind aber sehr schlecht, wenn es um die Einschätzung von
Wahrscheinlichkeiten oder statistischen Risiken geht. Beispiel:
[Geburtstagsparadoxon](https://de.wikipedia.org/wiki/Geburtstagsparadoxon)!

* * *

Möchte man dieses Spurerkennungssystem mit 10 DPMO nun nutzen, um damit
vollautonom zu fahren, wird es kritisch. Bei autonomer Fahrt muss es
vielleicht 1000x pro Kilometer die Fahrspur korrekt erkennen und das Auto
lenken. Hat man hier 10 defects per million opportunities, würde es
durchschnittlich alle 100km versagen. Bei Autobahntempo also circa jede
Stunde.

Die Fehlerrate muss demzufolge runter! Massiv runter! Die Grafik sieht
eigentlich ganz simpel aus:

![DPMO vs. Fehlerfreiheit: 100% Fehlerfrei bedeutet 0 Unfälle pro 1mio
Kilometer](http://www.cbcity.de/wp-content/uploads/2016/01/DPMO-Fehlerrate-
Selbstfahrende-Autos-770x475.png)

DPMO vs. Fehlerfreiheit: 100% Fehlerfrei bedeutet 0 Unfälle pro 1mio Kilometer

Nun wird hoffentlich jedem klar sein, dass es keine 100% fehlerfreien Systeme
gibt. Schaut man in den von Google veröffentlichten Bericht „[Google Self-
Driving Car Testing Report on Disengagements of Autonomous Mode December 2015]
(http://static.googleusercontent.com/media/www.google.com/de//selfdrivingcar/f
iles/reports/report-annual-15.pdf)„, so findet man Angaben zu Fehlerquoten.

### Google Self-Driving Car Fehlerquoten

Im Berichtszeitraum (September 2014 bis November 2015, also 14 Monate) wurden
683.000km von der Testflotte zurück gelegt. Dabei hat das Fahrzeug 272x aus
verschiedenen Gründen die sofortige Übernahme vom Fahrer angefordert und 69x
musste der Fahrer eingreifen. Die Fehler verteilten sich vor allem auf
Erkennungsschwächen, Softwarefehler und auch Hardwarefehler, wie in
nachfolgender Abbildung zu sehen ist.

![Deaktivierungsgründe der Google Self Driving Car Flotte im
Beobachtungszeitraum](http://www.cbcity.de/wp-content/uploads/2016/01
/Deaktivierung-Google-Self-Driving-Car-770x481.png)

Deaktivierungsgründe der Google Self Driving Car Flotte im
Beobachtungszeitraum

Das macht eine Fehlerquote von 499 DPMO, d.h. das Google-Self-Driving Car
konnte 99,95% der Situationen lösen.

Der zeitliche Verlauf mit durchaus positiver Tendenz ist:

![Datenquelle: Google Self-Driving Car Testing Report on Disengagements of
Autonomous Mode December 2015, Eigene Darstellung](http://www.cbcity.de/wp-
content/uploads/2016/01/Fehlerfreiheit-Google-Self-Driving-Car-770x486.png)

Datenquelle: Google Self-Driving Car Testing Report on Disengagements of
Autonomous Mode December 2015, Eigene Darstellung

Bleibt die Frage: Wie gut ist der Mensch?

## Menschen und Verkehrsunfälle

Status Quo ist, dass der Mensch die Fahrzeuge steuert. Dabei wurden in
Deutschland 735mrd. Kilometer zurück gelegt, wobei 2,4mio. Unfälle polizeilich
registriert wurden [Quelle: [ADAC Zahlen, Fakten, Wissen](https://www.adac.de/
_mmm/pdf/statistik_zahlen_fakten_wissen_0615_46600.pdf)]. Das sind 3,27
Unfälle pro Millionen Kilometer.

![Vergleich von 99,95% Fehlerfreiheit mit aktueller Unfallquote von
menschlichen Fahrern in Deutschland](http://www.cbcity.de/wp-
content/uploads/2016/01/Fahrfehler-Quote.png)

Vergleich von 99,95% Fehlerfreiheit mit aktueller Unfallquote von menschlichen
Fahrern in Deutschland

3,27 Unfälle pro 1mio km entspricht einer Fehlerfreiheit von 99,999673%.

[Menschen fahren zu 99,999673% fehlerfrei. Trotzdem sterben jährlich 4000
Menschen im…](https://twitter.com/share?text=Menschen+fahren+zu+99%2C999673%25
+fehlerfrei.+Trotzdem+sterben+j%C3%A4hrlich+4000+Menschen+im...&url=http://www
.cbcity.de/analyse-der-weg-zum-selbstfahrenden-auto-ist-noch-lang)

[Click To Tweet](https://twitter.com/share?text=Menschen+fahren+zu+99%2C999673
%25+fehlerfrei.+Trotzdem+sterben+j%C3%A4hrlich+4000+Menschen+im...&url=http://
www.cbcity.de/analyse-der-weg-zum-selbstfahrenden-auto-ist-noch-lang)

In einer aktuellen Studie der Universität Michigan [Schoettle & Sivak: [A
Preliminary Analysis of Real-World Crashes Involving Self-Driving
Vehicles](http://www.umich.edu/~umtriswt/PDF/UMTRI-2015-34.pdf), University of
Michigan] wurde die Unfallhäufigkeit von konventionellen und selbst fahrenden
Fahrzeugen verglichen. Dabei kommen normal gesteuerte Fahrzeuge in den USA auf
4,1 Crashes per million miles (2,5 Unfälle pro Millionen-km). Die selbst
fahrenden Fahrzeuge (Google inklusive) erreichen eine Quote von 9,1 (5,7
Unfälle pro Millionen-km).

![Unterschrift](http://www.cbcity.de/wp-content/uploads/2016/01/Crashes-per-
million-miles-770x564.png)

Unfälle pro millionen Meilen von konventionell gefahrenen Fahrzeugen und
selbstfahrenden Fahrzeugen in den USA. Quelle: Schoettle & Sivak: A
Preliminary Analysis of Real-World Crashes Involving Self-Driving Vehicles,
University of Michigan

_Es wird ausdrücklich darauf hingewiesen, dass die zurückgelegten Kilometer
der selbst fahrenden Flotten noch so gering ist, dass das Konfidenzintervall
für diese Aussage sehr groß ist. Außerdem waren die Fahrzeuge nicht im Winter
oder bei Nebel unterwegs und auch hauptsächlich auf exakt 3D-vermessenen
Straßen._

[Selbst fahrende Autos haben noch doppelt so hohe Unfallzahlen, wie vom
Menschen gelenkte.](https://twitter.com/share?text=Selbst+fahrende+Autos+haben
+noch+doppelt+so+hohe+Unfallzahlen%2C+wie+vom+Menschen+gelenkte.&url=http://ww
w.cbcity.de/analyse-der-weg-zum-selbstfahrenden-auto-ist-noch-lang)

[Click To Tweet](https://twitter.com/share?text=Selbst+fahrende+Autos+haben+no
ch+doppelt+so+hohe+Unfallzahlen%2C+wie+vom+Menschen+gelenkte.&url=http://www.c
bcity.de/analyse-der-weg-zum-selbstfahrenden-auto-ist-noch-lang)

Im Google Bericht „[Google Self-Driving Car Testing Report on Disengagements
of Autonomous Mode December 2015](http://static.googleusercontent.com/media/ww
w.google.com/de//selfdrivingcar/files/reports/report-annual-15.pdf)" findet
man die Information, dass nachträgliches Playback von kritischen Situationen
in denen ein Fahrer eingreifen musste, ergeben haben, dass es in 10 Fällen zu
Kollisionen mit anderen Objekten gekommen wäre, wovon 2 nur mit kleinen
Objekten gewesen wären. Rechnet man mit 8 ernsthaften Kollisionen auf
683.000km, so ergibt sich eine Fehlerfreiheit für 99,9988% der Kilometer
(DPMO=12).

![Logarithmische Darstellung von Defects per Million Opportunities als
Funktion der Fehlerfreiheit in % mit aktuellem menschlichem Niveau, Google
Niveau und Richtung der Entwicklung](http://www.cbcity.de/wp-
content/uploads/2016/01/DPMO-logFehlerrate-Google-Humans-770x533.png)

Logarithmische Darstellung von Defects per Million Opportunities als Funktion
der Fehlerfreiheit in % mit aktuellem menschlichem Niveau, Google Niveau und
Richtung der Entwicklung

Die Self-Driving-Cars (auch nicht die von Google) spielen noch lange nicht in
der Liga der menschlichen Fahrer_innen mit. Nur durch die Anwesenheit eines
Google-Testfahrers wurden Unfälle verhindert. Ohne diese, wäre es, als ob man
sich bei einem betrunkenen Fahrer in's Auto setzt.

[Self-Driving-Taxis sind nicht sicherer als betrunken nach Haus zu
fahren](https://twitter.com/share?text=Self-Driving-Taxis+sind+nicht+sicherer+
als+betrunken+nach+Haus+zu+fahren&url=http://www.cbcity.de/analyse-der-weg-
zum-selbstfahrenden-auto-ist-noch-lang)

[Click To Tweet](https://twitter.com/share?text=Self-Driving-Taxis+sind+nicht+
sicherer+als+betrunken+nach+Haus+zu+fahren&url=http://www.cbcity.de/analyse-
der-weg-zum-selbstfahrenden-auto-ist-noch-lang)

Das Fahren und selbstständige Agieren ist ein extrem komplexes Zusammenspiel
von [Sensoren](http://www.cbcity.de/fahrzeugumfeldsensorik-ueberblick-und-
vergleich-zwischen-lidar-radar-video), Datenübertragung- und Verarbeitung,
Algorithmen und Aktoren. Überall lauern im Detail Fehlermöglichkeiten, die das
Gesamtsystem ausfallen lassen können.

## Step-by-Step zu Fail Operational Systemen

Die Fehlermöglichkeiten-Einfluss-Analyse liefert für hochautomatisierte Fahrt
erhebliche Risiken, sodass ein Qualitätsniveau von Sensoren und Steuergeräten
und Aktoren erreicht werden muss, welcher den Six-Sigma BlackBelts in den
Qualitätsabteilungen schlaflose Nächte bereitet. Die ISO 26262 fordert für
Sensoren und Systeme Ausfallraten, die je nach Automotive Safety Integrity
Level entsprechend kompliziert zu erreichen sind.

Für die letzte Stufe der autonomen Fahrt, muss die gesamte Architektur so
ausgelegt sein, dass sie als so genannte fail operational Systeme
(Weiterbetrieb trotz Fehler) funktionieren und nicht, wie bei den meisten
heutigen Systemen, ‚nur' fail safe (es wird ein sicherer Zustand eingenommen,
meist Abschalten des Systems). Es wird also auf Systeme, die denen von
Flugzeugen ähnlich sind, hinaus laufen.

## Blick in die Zukunft

> „Prognosen sind äußerst schwierig, vor allem wenn sie die Zukunft betreffen"

Es gibt durchaus Ingenieure aus dem Fachgebiet, welche eine Stufe 5 für
überhaupt nicht realisierbar halten. Zumindest nicht so, dass die Gesellschaft
die damit einhergehende Fehlerquoten akzeptiert. Die Diskussion um die Ethik
der selbstfahrenden Autos ist seit einiger Zeit in vollem Gange. Damit gemeint
ist allerdings die einfache Frage, wie wir Menschen reagieren, wenn ein selbst
fahrendes Fahrzeug ein Menschenleben auslöscht. Natürlich passiert es jeden
Tag von Menschen verschuldet, aber was, wenn die Maschine ‚schuld' ist? Können
wir darüber hinweg sehen, weil es ja gesamtgesellschaftlich (statistisch)
sicherer geworden ist oder verteufeln wir jedes Fahrzeug? Ähnliche
Diskussionen gibt es ja auch zum Thema Impfen vs. Impfgegner. Die Faktenlage
ist eigentlich eindeutig, trotzdem gibt es reichlich Diskussion.

### Technik & Recht & Gesellschaft

Die Daimler und Benz Stiftung hat in ihrer „Villa Ladenburg"-Studie genau
diese Rahmenbedingungen aufgegriffen. Sehr empfehlenswerte Lektüre unter
OpenAccess: „[Autonomes Fahren - Technische, rechtliche und gesellschaftliche
Aspekte](http://link.springer.com/book/10.1007%2F978-3-662-45854-9)„, außerdem
dazu der [Forschergeist Podcast FG003 „Autonomer
Verkehr"](http://forschergeist.de/podcast/fg003-autonomer-verkehr/).

Wie reagieren die anderen, (noch) vom Menschen gelenkten Fahrzeuge auf völlig
emotionslos fahrende Vehikel? Es hat sich gezeigt, dass beispielsweise ein
Überschreiten der zulässigen Höchstgeschwindigkeit mit implementiert werden
muss, da es sonst zu kritischen Überholmanövern von anderen Fahrzeugen kommt,
was insgesamt wieder zu einer erhöhten Unfallwahrscheinlichkeit führte.

Viele Fragen, welche in den nächsten Jahren auf uns zukommen. Ich bin froh, in
diesem Zeitalter Fahrzeugtechnik-Ingenieur zu sein, welcher in diesem
interessanten Kapitel ‚Auto' mitarbeiten darf.
