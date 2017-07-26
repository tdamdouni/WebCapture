# Local Interconnect Network

_Captured: 2015-10-18 at 12:47 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Local_Interconnect_Network)_

![](http://upload.wikimedia.org/wikipedia/commons/thumb/7/79/Logo_lin_bus.svg/220px-Logo_lin_bus.svg.png)

> _LIN-Logo_

LIN ist ein [De-facto-Standard](https://de.m.wikipedia.org/wiki/De-facto-Standard), speziell fur die kostengunstige Kommunikation intelligenter Sensoren und Aktoren in Kraftfahrzeugen. Es kommt dort zum Einsatz, wo die Bandbreite und Vielseitigkeit von [CAN](https://de.m.wikipedia.org/wiki/Controller_Area_Network) nicht benotigt wird. Die LIN-Spezifikation umfasst das LIN-Protokoll, ein einheitliches Format zur Beschreibung eines gesamten LIN, und die Schnittstelle zwischen einem LIN und der Applikation.

Ein LIN setzt sich aus einem Master und einem oder mehreren Slaves zusammen. Der Master hat Kenntnis uber die zeitliche Reihenfolge aller zu ubertragenden Daten. Diese Daten werden von den entsprechenden Slaves dann ubertragen, wenn sie vom Master dazu aufgefordert werden. Das tut er durch das Aussenden eines Headers, der durch eine bestimmte Nachrichtenadresse gekennzeichnet ist. Im Anschluss legt der Slave die Datenbytes auf den Bus.

Der Master ist typischerweise ein Mikrocontroller. Der LIN-Master kann auch als Gateway arbeiten, so dass LIN-Slaves uber den LIN-Master auch via CAN erreichbar sein konnen.

Üblicherweise wird die Zahl der Slaves auf 16 begrenzt.

Eine LIN-Botschaft besteht aus einem Header und Daten mit maximal acht Nutzbytes. Eine LIN-Botschaft steht grundsatzlich jedem LIN-Slave zum Empfang zur Verfugung; ihre Übernahme hangt einzig von der Entscheidung der Steuergerate ab (empfangerselektives System). Diese Entscheidung wird uber sogenannte Akzeptanz- bzw. Nachrichtenfilter durchgefuhrt. Es ist somit moglich, dass eine LIN-Botschaft von einem, mehreren oder allen Steuergeraten am Bus zur Weiterverarbeitung ubernommen wird.

Zu jedem Zeitpunkt wird immer nur eine LIN-Botschaft ubertragen. Dadurch ist kein Mechanismus zur Auflosung von Buskollisionen erforderlich, da keine Kollisionen entstehen konnen. Alle zu ubertragenden Botschaften werden einmal innerhalb eines Zyklus ubertragen. Die zeitliche Reihenfolge der Botschaften wird in einer Steuertabelle (Schedule Table) definiert. Diese kann je nach Bedarf gewechselt werden.

Um die Buslast durch Abfrageframes fur seltene Ereignisse zu reduzieren, besteht die Moglichkeit, dass mehrere Slaves auf denselben Identifier antworten, aber nur dann, wenn sie neue Daten mitzuteilen haben. Dabei werden mogliche Buskollisionen vom Master erkannt. In diesem Fall werden anschließend entsprechende Abfrageframes gesendet, auf die nur jeweils ein Slave antworten darf.

Die Spezifikation sieht zwei Netzknotenzustande vor: Sleep-Mode und Normal-Mode. Der Übergang zwischen den beiden Modi wird einerseits mit einem expliziten Kommando vom Master und andererseits uber ein _Wake-Up-Signal-Frame_ durch den Master oder einen der Slaves initiiert.

Die Diagnose wird bei LIN mit Hilfe von Kommando-Botschaften durchgefuhrt. Um einen Slave diagnostizieren zu konnen, ubertragt der Master ein bestimmtes Kommando. Die Datenubertragung innerhalb einer Diagnose zwischen Master und Slave basiert auf dem durch die ISO 15765-2 definierten Transportprotokoll.

LIN ist ein [Eindraht-Bus](https://de.m.wikipedia.org/wiki/1-Wire), der eine Signalleitung und das Autochassis als Bezugspotential verwendet. Die Signalzustande werden wie beim CAN rezessiv und dominant genannt. Im Gegensatz zum CAN stellt die Bordnetzspannung den rezessiven Zustand sowie den Ruhezustand dar und ca. 0 V den dominanten Zustand.

Die hochste spezifizierte [Bruttodatenrate](https://de.m.wikipedia.org/wiki/Daten%C3%BCbertragungsrate) sind 20.000 Bits pro Sekunde (bit/s). Empfohlene Datenraten sind 2.400 bit/s, 9.600 bit/s und 19.200 bit/s.

Das LIN-Protokoll sieht keine Fehlersignalisierung vor, aber zwei Mechanismen, um Übertragungsfehler erkennen zu konnen: Parity und Checksumme. Fehlerhafte Botschaften werden als nicht gesendet betrachtet und verworfen. Erkannte Fehler werden beim jeweiligen Steuergerat abgelegt und konnen vom Master ausgelesen werden. In einem LIN existiert keine Fehlersignalisierung, erkannte Fehler werden also nicht uber das Protokoll signalisiert. Einzige Ausnahme bildet das Kapitel 6 (_Status Management_) der LIN Spec 2.0. Es beschreibt _Error Detection_ im LIN mittels _Response-Error-Bit_ durch das der Master bestimmte Fehler erkennen kann. Die Fehlerbehandlung bei fehlerhaften Kommunikationen ist meistens abhangig von den Systemanforderungen und muss in der Anwendungsschicht definiert werden.

Die LIN-Spezifikation wurde vom LIN-Konsortium entwickelt und umfasst das LIN-Protokoll, ein einheitliches Format zur Beschreibung eines gesamten LIN sowie die Schnittstelle zwischen einem LIN und der Applikation.
