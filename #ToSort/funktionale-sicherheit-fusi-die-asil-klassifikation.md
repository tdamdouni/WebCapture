# Funktionale Sicherheit (FuSi) – die ASIL-Klassifikation ...

_Captured: 2018-03-25 at 12:10 from [www.i-q.de](https://www.i-q.de/leistungen/iso-26262-fsm-und-fusi/fusi-asil-klassifikationen/)_

Was sich anhort wie ein Waschmittel, hat eine wichtige Bedeutung innerhalb der Funktionalen Sicherheit. Worum geht es bei der **ASIL-Klassifikation**? Grundsatzliches ist als Antwort auf diese Frage in einer kleinen Übersicht zusammengestellt.

Die ASIL-Klassifikation setzt sich ahnlich wie die RPZ in der FMEA-Betrachtung aus drei verschiedenen Faktoren (in diesem Fall besser Summanden) zusammen. Dabei handelt es sich um:

  * **„Severity - S" **(Schwere des Fehlers, Gefahrdung des Nutzers oder der Umgebung)
    * S0: keine Verletzungen (unverletzt)
    * S1: leichte bis mittelschwere Verletzungen (Arm verletzt)
    * S2: schwere Verletzungen, Überleben aber sehr wahrscheinlich (Arm ab)
    * S3: schwerste Verletzungen, Überleben unwahrscheinlich (Kopf ab)
  * **„Exposure - E"** (Eintrittswahrscheinlichkeit, d.h. Haufigkeit und / oder Dauer des Betriebszustands)
    * E1: seltenes Auftreten (Liegenbleiber auf dem Bahnubergang)
    * E2: gelegentliches Auftreten (Fahren mit Anhanger oder Dachgepacktrager)
    * E3: haufiges Auftreten (Tanken des Fahrzeugs, nasse Straße)
    * E4: standiges Auftreten (Beschleunigen, Bremsen, Lenken)

Außerdem wird beim Faktor Exposure noch nach zwei Parametern unterschieden: **Duration** (Dauer des Auftretens der Fahrsituation) und **Frequency** (Frequenz des Auftretens der Fahrsituation).

  * **„Controllability - C" **(Beherrschbarkeit des Fehlers)
    * C0: sichere Beherrschung (alle Fahrer beherrschen diese Situation, z.B. ungewollte Erhohung der Radiolautstarke)
    * C1: einfache Beherrschbarkeit (mehr als 99% der Fahrer konnen die Situation beherrschen, z.B. Lenksaule beim Start des Fahrzeugs eingerastet)
    * C2: normale Beherrschbarkeit (mehr als 90% der Fahrer konnen die Situation beherrschen, z.B. Ausfall des ABS wahrend einer Notfallbremsung)
    * C3: schwierige Beherrschbarkeit (weniger als 90% der Fahrer beherrschen die Situation, z.B. plotzlich auftretende hohe Lenkkrafte)

Diese drei Summanden sind weiter aufgegliedert uber Parameter (z.B. S0, S1 etc.). Über einen Risikographen ergibt sich aus allen drei Summanden die **„ASIL-Klassifikation"**: die Bestimmung der ASIL-Level (Tabelle).

[Tabelle gemaß ISO 26262-3, - Herleitung der ASIL-Levels uber den Risikograph]

Die Rechenanleitung dafur ist recht einfach: Man zahle die Zahlen nach den Buchstaben (zum Beispiel S3 / E4 / C3) zusammen und erhalt in diesem Fall 10 Punkte. Da es sich um den schlimmsten Fall handelt (in allen drei Kategorien die hochste Punktzahl), steht diese Bewertung fur ASIL D.

  * 10 Punkte => ASIL D
  * 9 Punkte => ASIL C
  * 8 Punkte => ASIL B
  * 7 Punkte => ASIL A

Dabei gilt es allerdings eine Ausnahme zu berucksichtigen: S0 / E4 / C3 ergibt nach dieser Rechnung auch 7 Punkte, ist aber im Grafen nur als QM eingestuft. Das resultiert daraus, dass bei einem S0 keine FuSi-Relevanz vorliegt, denn S0 steht fur "keine Verletzungen".

Aus den ASIL-Levels werden nun verschiedene Klassen abgeleitet, die sich unter anderem auf die zulassigen Ausfallwahrscheinlichkeiten beziehen:

  * **ASIL A:**
    * **empfohlene** Ausfallwahrscheinlichkeit kleiner 10-6 / Stunde, entspricht einer Rate von 1.000 Fit
  * **ASIL B:**
    * **empfohlene** Ausfallwahrscheinlichkeit kleiner 10-7 / Stunde, entspricht einer Rate von 100 Fit
  * **ASIL C:**
    * **geforderte** Ausfallwahrscheinlichkeit kleiner 10-7 / Stunde, entspricht einer Rate von 100 Fit
  * **ASIL D:**
    * **geforderte** Ausfallwahrscheinlichkeit kleiner 10-8 / Stunde, entspricht einer Rate von 10 Fit

Hinzu kommen noch fur alle Entwicklungsdisziplinen wie System, Hardware, Software die ASIL-abhangigen Anforderungen fur Architektur, Coding, Test usw. Dabei gilt zu beachten, dass der Sprung in den Anforderungen zwischen B und C besonders groß ist, da ab ASIL C in der Regel zweikanalige Architekturen erforderlich werden und die Zuverlassigkeitsanforderungen verpflichtend sind. Das QM-Kriterium bedeutet, dass in diesem Falle die Maßnahmen ausreichend sind, die in einem normalen Qualitatsmanagement-System (ISO/TS 16949) gefordert werden.

Aus den ASIL-Levels A, B, C oder D ergeben sich dann die Anforderungen an das zu entwickelnde Produkt / Baugruppe / Einzelteil.  
Sehen Sie hier einige kleine Beispiele (hangt immer vom konkreten Einsatzbereich ab!):

  * keine Beschleunigung bei Fahreranforderung  
==>** ASIL A**
  * Selbstbeschleuniger  
==>** ASIL C**
  * Bremsversagen ==> **ASIL D**
  * Selbstlenker ==> **ASIL D**
