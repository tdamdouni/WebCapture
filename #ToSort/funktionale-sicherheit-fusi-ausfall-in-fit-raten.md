# Funktionale Sicherheit (FuSi) – Ausfall in FIT-Raten...

_Captured: 2018-03-25 at 12:12 from [www.i-q.de](https://www.i-q.de/leistungen/iso-26262-fsm-und-fusi/fusi-ausfallwahrscheinlichkeit/)_

Um **Ausfallwahrscheinlichkeiten** und **FIT-Raten** geht es in diesem Abschnitt aus dem Bereich Funktionaler Sicherheit. „Failure in Time" (FIT) beschreibt die Ausfallrate technischer Komponenten, insbesondere elektronischer Bauteile. Die Einheit FIT gibt dabei die Anzahl der Bauteile an, welche in 109 Stunden ausfallen (Ausfallrate bei 1 Fit also einmal in ca. 114.000 Jahren).

Bauteile mit einem hohen FIT-Wert fallen statistisch gesehen haufiger aus als solche mit einem niedrigen Wert. Mit Hilfe der FIT-Werte einzelner Bauteile lasst sich die Ausfallwahrscheinlichkeit komplexer Gerate bereits in der Konstruktions- oder Planungsphase berechnen (oder sagen wir besser: abschatzen). Hierbei geht man davon aus (falls keine Redundanzen vorliegen), dass der Ausfall eines beliebigen Einzelteils zum Versagen des ganzen Gerates fuhrt. Aus der Summe der Ausfallraten der Einzelteile ergibt sich somit die Ausfallrate des ganzen Gerates.

Wie alle statistischen Kenngroßen kann eine FIT-Berechnung keine Aussage uber Fehler eines bestimmten Einzelgerates liefern, sondern immer nur Anhaltspunkte fur eine großere Serie geben.

Oberflachenmontierte Bauteile (SMD - Surface Mounted Device) haben teilweise wesentlich gunstigere Werte. Diese Werte sind nur als Anhaltspunkte zu nehmen, da sie je nach Literaturquelle und Bauteil durchaus um den Faktor 10 unterschiedlich angegeben werden. Zusatzlich sind die Werte sehr stark von der Temperatur abhangig: eine Temperaturerhohung um 25 °C verzehnfacht die Ausfallrate (Gesetz von Arrhenius).Auch die Umgebung ist zu berucksichtigen (Feuchtigkeit, Hohe, Strahlung, Erschutterungen, usw.). Die MTTF (Mean Time To Failure - mittlere Zeit bis zum Auftreten eines Fehlers (an nicht reparierbaren technischen Systemen) - also die wahrscheinliche mittlere Lebensdauer) ist der Kehrwert der Ausfallrate. Mathematisch exakt gilt das jedoch nur fur eine zeitinvariante (=konstante) Ausfallrate.

### **Normen zu Ausfallwahrscheinlichkeiten:**

Die bekannteste und alteste Zusammenfassung von Ausfallwahrscheinlichkeiten ist das _US-Handbuch MIL-STD-217_. Dieses rechnet jedoch mit FpmH (Failures per million hours), also der Ausfallwahrscheinlichkeit nach einer Million Betriebsstunden. Der Wert ist durch Multiplikation mit 10³ in FIT umzurechnen.

Eine weitere eingefuhrte Ausfallwahrscheinlichkeitsquelle ist die _[Siemens-Norm SN 29500](https://www.i-q.de/leistungen/iso-26262-fsm-und-fusi/SN-29500-Norm/)_, die es ermoglicht, fur die gebrauchlichsten elektronischen und elektromechanischen Bauteile FIT-Werte anhand von bekannten Belastungsdaten zu errechnen. Diese Werks-Norm besitzt keinen offiziellen internationalen Status. Dennoch wird sie weltweit bevorzugt zur Berechnung der Kennzahlen sicherheitstechnischer Gerate sowie zur Ermittlung von Zuverlassigkeitsprognosen (Reliability Prognosis) herangezogen. Die damit gewonnenen Ausfallraten sind allesamt konservativer Natur, d.h. das Bauteil wird unabhangig von Hersteller und dessen Produktionsverfahren beurteilt, das Ergebnis befindet sich also auf der „sicheren Seite" und muss nicht zwangslaufig die physikalische Wirklichkeit widerspiegeln.

Weitere Beispiele fur Ausfallraten finden sich in der Anwendungsnorm _EN ISO 13849-1_, die als Nachfolger zur EN 954 diese im Jahre 2006 vollstandig ersetzte, sowie in der Anwendungsnorm _EN 62061_ zur funktionalen Sicherheit von Maschinen und Anlagen. Weniger verbreitet ist die ursprunglich franzosische Norm RDF 2000 (_IEC TR 62380_), die auch reale Betriebszustande, wie beispielsweise Temperatureinflusse oder Ein-/Ausschaltvorgange berucksichtigt.

Vielleicht haben Sie schon mal von folgendem Beispiel gehort, bei dem die Sicherheit bzw. der Versagenseintritt ganz bewußt minimiert werden sollte.

Vor einigen Jahren gab es einen Unfall auf dem Warschauer Flughafen, bei dem ein Airbus nicht rechtzeitig zum Stehen kam. Was war passiert?  
Die Ingenieure hatten Sicherheitsmechanismen in die Bordelektronik konstruiert, durch die der so genannte „Umkehrschub" erst dann aktiviert werden konnte, wenn „sicher gestellt" war, dass das Flugzeug auch tatsachlich Bodenkontakt hat. (Hintergrund: Falls der Umkehrschub eingeleitet wird, wenn sich das Flugzeug noch in der Luft befindet, dann hat das zur Folge, dass es einen Stromungsabriss gibt und das Flugzeug wie ein Stein vom Himmel fallt.) So weit, so gut!  
Woruber wurde sicher gestellt, dass das Flugzeug Bodenkontakt hat? Durch diese zwei unabhangige Mechanismen:

  1. Das Fahrwerk musste eingefedert sein
  2. Die Drehzahl der Rader musste uber einem ganz spezifischen Wert liegen

An diesem Tag in Warschau hatte es sehr stark geregnet und die Landebahn stand vollig unter Wasser => Aquaplaning! Aus diesem Grund konnten die Rader des Flugzeugs keine entsprechende Anfangsgeschwindigkeit aufnehmen, denn sie sind quasi uber den Wasserfilm ohne nennenswerte Reibung „gesurft"! Sehr wahrscheinlich stand auch der Pilot noch „auf der Bremse", so dass die Rader vielleicht sogar still gestanden haben. Die Sensoren sendeten ordungsgemaß, dass die Rader noch keine Drehzahl haben, die uber dem festgelegten Zielwert lagen und so wurde die Anforderung des Piloten nach Umkehrschub NICHT umgesetzt. Ergebnis: Keine Bremswirkung uber die Rader und naturlich auch keinerlei Bremswirkung uber den Umkehrschub! Die Auswirkung kann sich jeder vorstellen...

Einen Überblick uber mogliche Seminarinhalte ist auf der Seite [FuSi-Seminar ISO 26262](https://www.i-q.de/seminare-und-workshops/fusi-seminare-iso-26262/) zusammengestellt.

Feste Termine finden Sie auf der [Termineseite](https://www.i-q.de/termine-und-kalender/termine/).

Selbstverstandlich bringen wir den Experten auch inhouse zu Ihnen - fragen Sie uns einfach [per Formular](https://www.i-q.de/fragen-und-angebote/). Gerne berucksichtigen wir auch Ihre Vorschlage.

Sie haben Fragen dazu? Sie mochten uns Ihre Meinung, Ihre Erfahrungen mitteilen? Senden Sie uns einfach eine [E-Mail](https://www.i-q.de/kontakt/). Wir antworten per Mail, auf dem Postweg oder telefonisch.
