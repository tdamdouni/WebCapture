# Normierte Programmierung

_Captured: 2015-10-23 at 16:07 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Normierte_Programmierung)_

Die **normierte Programmierung** (NP) beschreibt eine standardisierte Ablaufsteuerung eines Datenverarbeitungsprogramms. Sie war in DIN 66220 genormt und wurde mit DIN 66260 in Richtung [strukturierte Programmierung](https://de.m.wikipedia.org/wiki/Strukturierte_Programmierung) weiterentwickelt. Beide Ansatze unterstutzten die [modulare Programmierung](https://de.m.wikipedia.org/wiki/Modulare_Programmierung).

Normierte Programmierung ist eine verallgemeinerte Programmablaufsteuerung, die die Teilaufgaben eines [Stapelprogrammes](https://de.m.wikipedia.org/wiki/Stapelverarbeitung) wie Dateneingabe, Gruppenkontrolle, Verarbeitung / Ausgabe in ein einheitliches, logisch klares, funktionelles Schema gliedert. Fur Programme mit solchen Aufgaben lasst sich dieses Schema unabhangig von der fachinhaltlichen Aufgabenstellung und „technologieneutral" (z. B. in jeder [imperativen](https://de.m.wikipedia.org/wiki/Imperative_Programmierung)/[prozeduralen](https://de.m.wikipedia.org/wiki/Prozedurale_Programmierung) [Programmiersprache](https://de.m.wikipedia.org/wiki/Programmiersprache)) anwenden.

  * [Die normierte Programmierung](https://de.m.wikipedia.org/wiki/Normierte_Programmierung)
    * [Der Aufbau der Blocke](https://de.m.wikipedia.org/wiki/Normierte_Programmierung)

Zur Zeit der Entstehung der normierten Programmierung Ende der 1960er Jahre fur die kommerzielle [Datenverarbeitung](https://de.m.wikipedia.org/wiki/Datenverarbeitung) gab es lediglich Stapelprogramme: [sequentielle](https://de.m.wikipedia.org/wiki/Sequentieller_Zugriff) Dateien, in denen je nach Aufgabenstellung unterschiedliche 'Satzarten' [gemischt/hintereinander](https://de.m.wikipedia.org/wiki/Lochkartenmischer) auftraten, weil z. B. nur eine [Magnetbandstation](https://de.m.wikipedia.org/wiki/Magnetband) oder ein [Lochkartenleser](https://de.m.wikipedia.org/wiki/Lochkartenleser) fur die Eingabe verfugbar war. Ein Mischen im Programm war so nicht erforderlich und ware bei Arbeitsspeichern von z. B. 64 KB inkl. Betriebssystem auch zu aufwandig gewesen. So las das Programm 'seine' Eingabedatei und verarbeitete einen [Datensatz](https://de.m.wikipedia.org/wiki/Datensatz) nach dem anderen. Über ein Datenfeld 'Satzart' wurden die Datenarten (Kunde, Bestellung …) inhaltlich unterschieden und uber Ordnungsbegriffe einander zugeordnet. Das Programm 'lief' (mit [GOTO](https://de.m.wikipedia.org/wiki/Sprunganweisung)) je nach Datenkonstellation zu bestimmten Stellen, zum Beispiel zu Rechenvorgangen, zum Drucken einer Listenzeile, um Daten nachzulesen und ebenfalls zu verarbeiten - und letztlich zum Programmende. Die Programme waren oft '[Spaghetticode](https://de.m.wikipedia.org/wiki/Spaghetticode)', folgten kaum einheitlichen Strukturvorgaben und waren deshalb intransparent, fehleranfallig und anderungsunfreundlich.

Leistungsfahigere Rechner, neue Programmiersprachen, aber auch Fortschritte in den Methoden zur [Softwareentwicklung](https://de.m.wikipedia.org/wiki/Methode_\(Softwaretechnik\)) fuhrten sukzessive zu besseren Losungen: Es entstanden Vorschlage fur eine standardisierte Struktur von Stapelprogrammen. Darin war die gesamte Steuerung des Programms in eindeutig definierte 'Routinen' zergliedert, die die aufgabenspezifischen Verarbeitungsteile des Programms aufrufen - die 'Normierte Programmierung'.

Allerdings werden in der Praxis der ([individuellen](https://de.m.wikipedia.org/wiki/Individualsoftware)) [Softwareentwicklung](https://de.m.wikipedia.org/wiki/Softwareentwicklung) derart standardisierte Verfahren oft nicht angewendet - mit der Folge, dass das Erstellen des [Programmcodes](https://de.m.wikipedia.org/wiki/Quellcode) zur Programmsteuerung in vielen Fallen eine besondere Herausforderung bzw. 'Problemstellung' fur die Entwickler blieb, die nicht selten hohen Entwicklungsaufwand verursacht und beim [Softwaretest](https://de.m.wikipedia.org/wiki/Softwaretest) Fehler zutage fordert.

Laut einem kleinen Lehrbuch eines großen [BUNCH](https://de.m.wikipedia.org/wiki/BUNCH)-Computerherstellers von 1971 mit dem Titel _Logik der Programmierung, Normierte Programmierung_, mit dem damals angehende [Programmierer](https://de.m.wikipedia.org/wiki/Programmierer) und [Systemanalytiker](https://de.m.wikipedia.org/wiki/Systemanalytiker) ausgebildet wurden, wurden _„Vereinheitlichung und Standardisierung der Programmerstellung, Verkurzung der Programmierzeit, Ausschaltung moglicher Fehlerquellen und damit Verkurzung der Testzeit und Senkung der Kosten fur die Programmierer"_ als Ziele der normierten Programmierung bezeichnet. Dementsprechend sind diese Ziele dann von Bedeutung, wenn in einer [Organisation](https://de.m.wikipedia.org/wiki/Organisation) mehrere/viele [Entwickler](https://de.m.wikipedia.org/wiki/Softwareentwickler) Software mit [Entwicklungswerkzeugen](https://de.m.wikipedia.org/wiki/Entwicklungswerkzeug) herstellen, in denen die Steuerungsfunktionen der Normierten Programmierung nicht als integrierter Bestandteil enthalten sind.

Kernstuck der normierten Programmierung ist die Programmablaufsteuerung. Die normierte Programmierung erzwingt die logische und funktionelle Ordnung eines Programms durch eine vereinheitlichte Programmablaufsteuerung, die unabhangig vom jeweiligen Programmierer ist. Da die Ablaufsteuerung explizit vom Programmierer festgelegt wird, lasst sich die [Softwareentwicklung](https://de.m.wikipedia.org/wiki/Softwareentwicklung) nach der normierten Programmierung dem [Programmierparadigma](https://de.m.wikipedia.org/wiki/Programmierparadigma) der [imperativen/prozeduralen Programmierung](https://de.m.wikipedia.org/wiki/Imperative_Programmierung) zuordnen.

Stapelprogramme haben dabei unabhangig von ihrer individuellen Aufgabenstellung immer _dieselbe Struktur_. Das heißt: Identische Bezeichnungen fur die Verarbeitungsprozeduren; identische Steuerungslogik (die Blocke B bis E sind nur auf die konkrete Aufgabenstellung wie Anzahl Dateien, Gruppenbegriffe … eingestellt). Die _aufgabenspezifische_ Verarbeitung ist ausschließlich in Prozeduren der Blocke G bis J, ggf. A und F enthalten.

![Blockunterteilung der normierten Programmierung](http://upload.wikimedia.org/wikipedia/de/b/b0/Blockunterteilung_der_normierten_Programmierung.png)

> _[Blockunterteilung der normierten Programmierung](https://de.m.wikipedia.org/w/index.php?title=Datei:Blockunterteilung_der_normierten_Programmierung.png&filetimestamp=20051023164849&)_

Der Programmablauf ist in Blocke unterteilt, wobei jeder Block einen funktional zusammengehorigen Teil eines Programmes darstellt. Die Unterteilung stellt sozusagen den „naturlichen" Aufbau eines kommerziellen Programms dar: Vor Beginn der eigentlichen Verarbeitung sind Anfangswerte zu setzen und Steuerinformationen auszuwerten, dann sind Eingabedaten zu lesen, der nachste Satz zur Verarbeitung ist auszuwahlen, eventuell mussen [Gruppenwechsel](https://de.m.wikipedia.org/wiki/Gruppenwechsel) behandelt werden, schließlich ist der Datensatz zu verarbeiten und gegebenenfalls sind Daten auszugeben. Jeder Block stellt eine in sich geschlossene Einheit dar. Ein Block kann zur besseren Übersicht aus mehreren Unterblocken bestehen. Der abgebildete [Programmablaufplan](https://de.m.wikipedia.org/wiki/Programmablaufplan) zeigt folgende Blocke:

  * **A**: Vorprogramm fur alle einmalig durchzufuhrenden Programmschritte
  * **B**: Eingabe; sie besteht aus soviel Unterblocken wie es serielle Eingabedateien gibt. In jedem dieser Blocke wird nicht nur die eigentliche Eingabe abgehandelt sondern auch Plausibilitatsprufungen und Reihenfolgekontrolle.
  * **C**: Satzfreigabe; aus den gelesenen Satzen je Datei wird ausgewahlt, welcher Datensatz als nachster zu verarbeiten ist - und (vorher) zur Feststellung von Gruppenwechseln verwendet wird.
  * **D**: Gruppenkontrolle und Aufruf der Gruppenwechsel-Unterprogramme fur alle Gruppenstufen.
  * **E**: Einzelverarbeitung; sie ist wiederum entsprechend der Anzahl Eingabedateien in Unterblocke unterteilt.
  * **F**: Schlussprogramm fur alle einmalig nach dem eigentlichen Programmablauf zu durchlaufenden Programmbefehle.
  * **G**: Unterprogramme der Gruppenverarbeitung; es gibt soviele Unterprogramme wie es Gruppenstufen gibt, jeweils fur Vorlaufe und Nachlaufe getrennt.
  * **H**: Unterprogramme der Einzelverarbeitung; diese Unterprogramme sollten moglichst klein und ubersichtlich sein.
  * **J**: Unterprogramme der sequentiellen Ausgabe und der wahlfreien Ein-/Ausgabe; fur jede der genannten Dateien gibt es ein Unterprogramm.

Eine wesentliche Teilfunktion in der Normierten Programmierung ist die Automatik der ‚Datenzufuhr'. Aus jeder Eingabedatei wird jeweils genau ein Datensatz gelesen - bis zum Dateiende inklusive. Aus den aktuellen (zuletzt gelesenen) Satzen aller Dateien wird der nachste zu verarbeitende Satz ermittelt und der Verarbeitung zugefuhrt. Anschließend wird exakt aus dieser Datei wieder nachgelesen. Umgesetzt wird diese Art der Datenzufuhr in den Blocken _Eingabe_ und _Satzfreigabe_.

![Gruppenbegriffsfelder Normierte Programmierung](http://upload.wikimedia.org/wikipedia/de/e/ec/Gruppenbegriffsfelder_Normierte_Programmierung.png)

> _[Gruppenbegriffsfelder Normierte Programmierung](https://de.m.wikipedia.org/w/index.php?title=Datei:Gruppenbegriffsfelder_Normierte_Programmierung.png&filetimestamp=20051023170554&)_

Der zentrale Schlussel fur die Steuerung des Programmablaufs ist der Gruppenbegriff, der in jedem Satz der Eingabedateien enthalten sein muss. Da die Gruppenbegriffe an unterschiedlichen Positionen der Eingabedateien liegen konnen, werden bei der normierten Programmierung die Gruppenbegriffe aus den Datensatzen herausgeholt und in separaten dateibezogenen Gruppenbegriffsfeldern von links nach rechts nach der Gruppenstufenhierarchie absteigend gespeichert. Es gibt fur jede Eingabedatei ein solches, bei allen Dateien gleich großes und gleich-formatiges Gruppenbegriffsfeld - deshalb _dateibezogen_. Im Beispiel besteht das Gruppenbegriffsfeld der Eingabedatei 2 von rechts nach links aus der Dateinummer L2D („2"), den Gruppenbegriffen L21 (Untergruppenbegriff), L22 (Hauptgruppenbegriff), L23 (Übergruppenbegriff), L24 (ein nochhoherer Gruppenbegriff) und aus dem Feld L2S fur den Dateistatus. Die Felder Ln1 bis Ln4 konnen gemeinsam als LnM zur Paarigkeitsprufung herangezogen werden. Die Namen der Felder wurden in Anlehnung an die damals weit verbreitete Terminologie von [RPG](https://de.m.wikipedia.org/wiki/RPG_\(Programmiersprache\)) (Report Program Generator) vergeben (L fur Level, Gruppenstufe).

Neben den dateibezogenen Gruppenbegriffsfeldern gibt es zwei weitere, dateineutrale Felder, die fur die Gruppenkontrolle verwendet werden:

  * LA enthalt den Gruppenbegriff des letzten verarbeiteten Satzes
  * LN enthalt den Gruppenbegriff des nachsten zu verarbeitenden Satzes

Die Große stimmt mit der Große der dateibezogenen Felder L0, L1, … voll uberein. Lediglich die Definition der Felder ist aus Zweckmaßigkeitsgrunden fur die Gruppenkontrolle anders gewahlt worden. Im Beispiel dient das Feld LN1 zur Kontrolle der Untergruppe, das Feld LN2 der Kontrolle der Hauptgruppe usw.

Nach Eingabe eines Satzes von jeder Datei muss von allen Satzen jener ausgewahlt werden, der als Nachstes verarbeitet werden soll. Bei unterschiedlichen Gruppenbegriffen ist die Losung einfach, der Satz mit dem kleinsten Gruppenbegriff ist als nachster zu verarbeiten. Sind die Gruppenbegriffe jedoch gleich (paarig), muss entschieden werden, welche Datei die hohere Prioritat hat, d. h. die Dateinummer bestimmt die Prioritat. Bei dem klassischen Fall einer Gegenuberstellung von Stamm- (z. B. Teilestamm) und Bewegungsdaten (z. B. Lagerbewegungen) bestimmen die Bewegungsdaten, ob die Stammdaten bearbeitet werden mussen oder nicht, der Bewegungssatz muss also als erster verarbeitet werden. Die Dateinummer - eine Konstante - bestimmt bei Paarigkeit der restlichen Gruppenbegriffe die Reihenfolge (Prioritat) der Verarbeitung.

Der Dateistatus unterscheidet vier Zustande:

  * 0 = Satz nachziehen
  * 1 = Satz nicht nachziehen
  * 2 = Datei abgeschlossen
  * 3 = Datei nicht vorhanden

Am Anfang stehen die Zustande aller Eingabedateien auf 0 („Satz nachziehen"). Nach dem Nachziehen einer Datei wird ihr Status auf 1 gesetzt. Erst wenn sie zur Verarbeitung freigegeben wird, wird der Status wieder auf 0 gesetzt. Der Status 3 kann z. B. auf Grund von Vorlaufdaten Ablaufvarianten mit unterschiedlichen oder vorhandenen/nicht vorhandenen Dateien steuern.

Die Steuerung des Programms geschieht (grob) nach der Logik wie sie im Schaubild 'Blockunterteilung der normierten Programmierung' dargestellt ist. Von hier aus werden alle Subroutinen der Verarbeitung (A bis G) angesteuert. Grundlage dazu sind die dateibezogenen und die dateineutralen Gruppenbegriffsfelder, wie sie beim Lesen und in der Satzfreigabe bereitgestellt werden.

Hier werden Aktionen durchgefuhrt, die zu _Beginn des Programms_ erforderlich sind. Beispiele: Einlesen von [Parametern](https://de.m.wikipedia.org/wiki/Parameter_\(Informatik\)) (z. B. als 'Vorlaufkarten' zur Festlegung des Laufdatums oder von Laufvarianten); Initialisieren/Laden von [Lookup-Tabellen](https://de.m.wikipedia.org/wiki/Lookup-Tabelle) und anderen Datenbereichen; Dateien eroffnen (OPEN); Schalter setzen; einmalige Ausgabe von Titelzeilen; kurz alle einmaligen Arbeiten vor Beginn des von den Eingabedaten abhangigen Verarbeitungszyklus.

Der Block B ist je nach der Anzahl der sequentiellen Eingabedateien in Unterblocke B0, B1, B2, … unterteilt, die nacheinander durchlaufen werden. Je nach Dateistatus wird ein _Satz gelesen_ oder nicht. Direkt nach dem Lesen erfolgt die Prufung auf Dateiende. Falls ja, wird der Dateistatus auf „Dateiende" gesetzt, andernfalls auf „nicht nachziehen" und die dateispezifischen Gruppenbegriffsfelder werden gefullt.

Wenn nicht gesichert ist, dass eine Eingabedatei immer in der richtigen _Sortierfolge_ vorliegt, sollten in diesem Block eine Reihenfolgekontrolle oder andere Plausibilitatsprufungen stattfinden - ggf. mit vorzeitigem Programmabbruch.

Auch kann hier evtl. ein _Filtern_, d.h. Überlesen bestimmter Datensatze stattfinden - die damit auch keine Gruppenwechsel auslosen.

![](http://upload.wikimedia.org/wikipedia/de/thumb/3/38/NP-Satzlogik.png/220px-NP-Satzlogik.png)

> _Datenzufuhrsteuerung und Gruppenwechselverarbeitung_

Im Block C erfolgt auf Grund der Inhalte der Gruppenbegriffsfelder je Datei die Auswahl und Freigabe des _nachsten zu verarbeitenden Satzes_. Der nachste zu verarbeitende Datensatz ist bei 'aufsteigender Folge' aller Gruppenbegriffe der mit dem niedrigsten Gesamt-Ordnungsbegriff. Ist fur einen oder mehrere Ordnungsbegriffe 'absteigende Folge' festgelegt (Beispiel: Neuestes Datum zuerst verarbeiten), so muss dies bei der Satzfreigabe in geeigneter Weise berucksichtigt werden. Durch die prioritatssteuernd definierte Dateinummer wird auch bei aufgabenspezifisch gleichen Gruppenbegriffen in mehreren Dateien der richtige Datensatz zuerst ausgewahlt.

Die [Gruppenkontrolle](https://de.m.wikipedia.org/wiki/Gruppenkontrolle) erfolgt mit Hilfe der dateineutralen Gruppenbegriffsfelder LN und LA. Zur _Prufung eines Gruppenwechsels_ der niedrigsten Stufe wird LN1 gegen LA1 (siehe Schaubild 'Dateineutrales Gruppenbegriffsfeld') verglichen, fur einen Wechsel der zweitniedrigsten Stufe LN2 gegen LA2 usw. - bis zur hochsten Gruppenstufe.

Fur festgestellte Gruppenwechsel werden die Unterprogramme des Blocks G aufgerufen, und zwar zunachst die _Gruppen-Nachlaufe_ (außer nach dem ersten Lesen; von der niedrigsten Stufe bis zur festgestellten Wechselstufe) und danach die _Gruppen-Vorlaufe_ (außer nach der Verarbeitung aller Datensatze; von der festgestellten Wechselstufe bis zur niedrigsten).

Hier wird _aufgabenspezifisch_ verarbeitet, was am Ende bzw. am Anfang eines jeden Gruppenbegriffs zu tun ist. Die Verarbeitung erfolgt in den Unterblocken G1, G2 usw. (Nummernteil identisch mit der Gruppenstufe, z. B. LN1, LN2). Durch zusatzliche Unterblocke wie G1V, G2N … wird nach Gruppen-Vorlauf (Beispiel: Ausgabe einer Listen-Kopfzeile) und Gruppen-Nachlauf (Beispiel: Ausgabe von Summen) unterschieden. Die Aufrufe erfolgen aus Block D nur fur die dort festgestellten Gruppenstufen.  
Beachte: Die Ausfuhrung des Vorlaufs und des Nachlaufs fur einen konkreten Gruppenbegriff (z. B. PLZ 12345) liegt zeitlich weit auseinander; dazwischen liegt mindestens eine Einzelverarbeitung, ggf. auch die Gruppenverarbeitung fur niedrigere Gruppenstufen.

In den Unterroutinen des Blocks E werden die Datensatze aus den steuernden _Eingabedateien verarbeitet_. In den Unterblocken E1, E2 usw. wird genau der Datensatz verarbeitet, der in der Satzfreigabe (Block C) ausgewahlt wurde - und dessen Dateinummer im Feld LND steht. Evtl. erforderliche (alte) Gruppen-Nachlaufe und (neue) Gruppen-Vorlaufe sind zu diesem Zeitpunkt bereits verarbeitet.

Je nach Aufgabenstellung, Satzart etc., werden z. B. Daten zwischengespeichert, Summen berechnet und kumuliert, Daten / Einzelzeilen ausgegeben (durch Aufruf eines Unterprogrammes des J-Blockes), Schalter gesetzt (z. B. QL1, QL2, QG1, QG2, … auf die Schalter der normierten Programmierung wird hier nicht eingegangen) usw.

„Die haufige Verwendung von Unterprogrammen ist sehr zu empfehlen. Selbst wenn ein bestimmter Verarbeitungsteil im Programm nur einmal vorkommt, kann es sinnvoll sein, diesen Teil in ein Unterprogramm auszulagern, um die Ablauflogik des Verarbeitungsprogramms entsprechend klar und ubersichtlich herauszuarbeiten." (SPERRY UNIVAC: _Logik der Programmierung - Normierte Programmierung._ um 1970)

Es wird empfohlen, alles was zur _Ausgabe_ im weiteren Sinn gehort, in diese Unterprogramme auszulagern, um die die Ausgabe veranlassenden Verarbeitungsroutinen von den dazu erforderlichen (oft formalen) Details zu 'entlasten'. Das kann (neben der eigentlichen Satzausgabe) z. B. sein: Druckbereiche loschen, bei Randomdateien die Satzadresse berechnen, Steueranweisungen fur bestimmte Gerate absetzen usw.

Hierzu gehort das Schließen von Dateien, die Ausgabe von z. B. Gesamtsummen und die _Beendigung_ des Programms.

Die Programmierzeit wurde im Vergleich zur „wilden" Programmierung wesentlich verkurzt, ebenso die Testzeit. Das System ist relativ einfach zu erlernen, ist unabhangig von Maschinentypen und Programmiersprachen und unabhangig von den jeweiligen Programmierern (entsprechend wurde es von „Kunstlern" auch gerne abgelehnt). Jemand, der die Methode der normierten Programmierung kennt, kann sich schnell in ein fremdes Programm, das dieser Methodik folgt, einarbeiten.

Ob eine Datei in der NP-Verarbeitung als steuernd behandelt wird, kann im Zweifel unterschiedlich entschieden werden. Von Bedeutung ist dies zum Beispiel, wenn in bestimmten Dateien die Daten nur verkurzte Gruppenbegriffe aufweisen. So konnten z. B. in einer Aufgabenstellung die Daten fur Kunden, fur Bestellungen und fur Mahnungen aus drei Dateien stammen. Behandelt man die Kundendatei als steuernd, so entstehen Gruppenwechsel ohne Rucksicht darauf, ob Bestellungen oder Mahnungen vorliegen oder nicht. Alternativ konnten die Kundendaten als Teil der individuellen Verarbeitung (z. B. im Vorlauf_Kunde, sich aus Bestellungen ergebend) gezielt mit [Direktzugriff](https://de.m.wikipedia.org/wiki/Direktzugriff) oder sequentiell 'nachgelesen' werden.

Alternativ zur Steuerung uber mehrere Eingabedateien konnen Daten im Lesezugriff (z. B. bei Nutzung der Datenbanksprache [SQL](https://de.m.wikipedia.org/wiki/SQL)) oder durch eigene Vorverarbeitungsprogramme zu nur einem gemeinsamen Datenbestand zusammengefasst werden.

Gruppenbegriffe (auch Gruppierungsbegriff oder Ordnungsbegriff genannt) sind Inhalte von Datenfeldern, nach denen die zu verarbeitenden Daten zu Gruppen zusammengefasst werden, ggf. auch mehrstufig. Dies bedeutet zum Beispiel, dass zu Beginn eines Teilbegriffs Überschrifts-/Kopfzeilen und/oder am Ende Summenzeilen ausgegeben werden. Üblich sind solche Gruppierungen im [Reporting](https://de.m.wikipedia.org/wiki/Reporting), aber auch zu anderen Verarbeitungszwecken. Welche Feldinhalte als Gruppenbegriff(e) verwendet werden, wird stets durch den Verarbeitungszweck bestimmt.

Die nachfolgend beschriebenen besonderen Eigenschaften von Gruppenbegriffen (Beispiele) mussen ggf. im Rahmen der Programmentwicklung durch besondere Implementierungsmaßnahmen berucksichtigt werden:

  * Gruppenbegriffe konnen _einstufig_ (nur Postleitzahl) oder _mehrstufig_ (PLZ und Altersgruppe …) sein.
  * Sie treten _einheitlich_ in allen Eingabedateien auf oder zum Teil _nur verkurzt_. Beispiel: Kundendaten mit nur Kundennummer, Bestelldaten zusatzlich mit Bestellnummer.
  * Sie stammen aus _direkt gespeicherten_ Informationen oder sind _abgeleitete_ Informationen (wie Alter oder Altersgruppe (aus Geburtsdatum) oder Betrags-Großenklasse). Ableitungen mussen im Rahmen einer _Vorverarbeitung_ hergestellt werden. Bei einfachen Ableitungen ist dies im Lesevorgang selbst moglich, ggf. sind vorgeschaltete Verarbeitungsprogramme erforderlich.
  * Sie konnen dem _vollstandigen_ Inhalt eines Felds entsprechen oder _Teil eines Feldes_ sein (wie Stelle 1 und 2 der Postleitzahl)
  * Die _Sortierung_ kann aufsteigend oder absteigend (neuestes Datum vorne) sein.
  * Gruppenbegriffe konnen _fur den Datenbestand ubliche_ Begriffe sein (Land, Postleitzahl bei Adressdaten) und/oder Begriffe, die zu _besonderen Zwecken_ ausgewertet werden sollen (Anzahl Monate seit letzter Bestellung; Geburtstag MMTT). Derselbe Datenbestand kann so nach vielen unterschiedlichen Kriterien verarbeitet werden.
  * Die Gruppenbegriffe stammen aus _einem_ (1) oder _mehreren_ Datenbestanden (Postleitzahl und Alter aus Kundendaten, Herstellerland aus Artikeldaten).
  * Die Gruppenbegriffe weisen ggf. unterschiedliche _Datenformate_ auf - entweder die einzelnen Teilbegriffe und/oder identische Begriffe aus unterschiedlichen Eingabedateien sind unterschiedlich formatiert.
  * Die Datensatze mussen zur Verarbeitung in der definierten _Reihenfolge_ sortiert sein oder so gelesen werden konnen. Meist wird diese Reihenfolge bei der Verarbeitung uberpruft.
  * Über die Gruppenbegriffe hinaus ist eine _zusatzliche Sortierung_ der Datensatze ublich, zum Beispiel fur die Rechnungserstellung nach Artikelnummer, obwohl in der Rechnung die Bestellungen nur je Kundennummer zusammengefasst sind.
![](http://upload.wikimedia.org/wikipedia/de/thumb/6/6d/Muster_Rahmen_66220.pdf/page1-220px-Muster_Rahmen_66220.pdf.jpg)

> _Muster-Programmrahmen als Kopiervorlage_

Zur Erstellung eines Programms nach Normierter Programmierung sollten Hilfsmittel angewendet werden, mit denen der Aufwand zur Programmerstellung minimiert und die Qualitat der erstellten Programme (z. B. bezuglich Richtigkeit, Testbarkeit, Einheitlichkeit) erhoht bzw. gesichert werden kann. Hierzu zahlen:

  * [Programmgeneratoren](https://de.m.wikipedia.org/wiki/Codegenerator): Im Systemsoftwaremarkt sind Generatoren verfugbar, mit denen auf der Basis zu definierender Vorgaben ein Programmrahmen erzeugt werden kann. Dieser enthalt i. d. R. die komplette Programmsteuerung mit allen dazu erforderlichen Datenfeldern und den von der Hauptsteuerung angesprochenen Unterroutinen (Eingabe, Gruppenkontrolle und -Verarbeitung, Verarbeitung usw.). Oft unterstutzen diese Generatoren nur bestimmte Programmiersprachen. Auch werden die Datenfelder und Unterroutinen in der Regel generator-spezifisch nach anderen als den hier verwendeten Namenskonventionen erzeugt.
  * Programmtemplates: Wenn kein Generator verfugbar ist, ist ein Muster-Programmrahmen hilfreich, der ahnliche Strukturen wie unter 'Programmgeneratoren' genannt - und weitere Unternehmensstandards berucksichtigend - bereitstellt. Zum Erstellen eines neuen Programms wird der Rahmen kopiert und individuell auf die Aufgabenstellung (Anzahl Dateien und Gruppenbegriffe) angepasst.

In beiden Fallen liegt nach den vorgenannten vorbereitenden Aktivitaten die gesamte Ablaufsteuerung fertig vor, der Programmierer muss 'nur noch' die aufgabenspezifischen Verarbeitungsdetails in den noch leeren Unterroutinen (wie Gruppenvorlauf_1, Einzelverarbeitung_A usw.) einstellen.

Eine wortliche Auslegung von 'Normierte Programmierung' konnte alle normierenden / standardisierenden Aspekte der Programmierung (= das Erstellen eines Computerprogramms im engeren Sinn) umfassen. Dazu konnen, neben der normierten Ablaufsteuerung (wie in diesem Artikel beschrieben) folgende Aspekte gehoren:

  * Namenskonventionen: HIER im Wesentlichen als Vorschlag fur die Benennung der Funktionsblocke beschrieben. Regeln fur die Benennung von Datendefinitionen sollten ebenfalls im Detail vorgegeben sein.
  * GOTO-freie Programmierung: Abhangig von der verwendeten Programmiersprache werden hierfur Schleifenkonstrukte angeboten. Ziel hierbei ist eine ubersichtliche Programmlogik. Zumindest sollten direkte Sprunge in fremde Subroutinen niemals erlaubt sein, d.h. jede Subroutine springt zu ihrem Aufrufpunkt zuruck.
  * Standard-Funktionen: In vielen Unternehmen existieren fur bestimmte Aufgaben (technisch / fachlich) vorgefertigte Routinen (Unterprogramme, Makros, Codesequenzen, …), die in individuellen Programmen zu verwenden sind. Beispiele: Open / Close, Datumsberechnung, Druckausgabe, …
  * Standard-Datendefinitionen: Die Struktur von Datensatzen (ihre Feldfolge, Lange, Formate, …) sollte immer in einer Form vorliegen, die in allen diese Dateien verarbeitenden Programmen verwendet wird. Hierbei sollte es z. B. moglich sein, fur die Eingabe einen anderen Prafix zu verwenden als fur die Ausgabe.
  * Gestaltung von Bildschirminhalten: Farben, Position von Eingabefeldern und Fehlermeldungen, …
  * Gestaltung von Listen: Anordnung von Kopf- und Fußzeilen, …
  * Programmkommentare: In einigen Unternehmen ist vorgeschrieben, die erstellten Befehle sehr detailliert zu kommentieren. Hierbei besteht die Gefahr von Redundanz zu anderen schriftlichen Vorgaben.
  * …

Die Misserfolge bei den zahlreichen Versuchen nationaler oder gar weltweiter Standardisierung sollte die Unternehmen nicht davon abhalten, entsprechende Vorgaben als innerbetriebliche Regeln aufzustellen - und deren Einhaltung (als Teil der Qualitatssicherung) zu uberprufen.

Normierung / Standardisierung ist ein wesentlicher Aspekt von [Qualitat](https://de.m.wikipedia.org/wiki/Softwarequalit%C3%A4t). Siehe auch [Programmierstil](https://de.m.wikipedia.org/wiki/Programmierstil).

Ende der 1960er und in den 1970er Jahren waren 'Top-down-Vorgehensweise, schrittweise Verfeinerung und [modulare Programmierung](https://de.m.wikipedia.org/wiki/Modulare_Programmierung)' Diskussionsthemen zur Softwareentwicklung. Insbesondere die Vorschlage von [Edsger W. Dijkstra](https://de.m.wikipedia.org/wiki/Edsger_W._Dijkstra) zur [strukturierten Programmierung](https://de.m.wikipedia.org/wiki/Strukturierte_Programmierung) wirken bis heute, konnten aber schon damals innerhalb von normierten Programmen realisiert werden. Einer schrittweisen Verfeinerung vor allem der Blocke E, H und J stand die normierte Programmierung nicht im Wege. Die elementaren Grundstrukturen waren z. B. in [COBOL](https://de.m.wikipedia.org/wiki/COBOL) umsetzbar, ein „GO TO"-freies Programm mit normierter Programmierung war moglich, das Blockkonzept war also auch mit Sprachen wie COBOL und [PL/I](https://de.m.wikipedia.org/wiki/PL/I), ja sogar mit [Assembler](https://de.m.wikipedia.org/wiki/Assemblersprache) moglich. Allerdings wird die Lesbarkeit der Programme bis heute von manchen Programmierern kritisiert, im Besonderen wenn der [Quellcode](https://de.m.wikipedia.org/wiki/Quellcode) von NP-Generatoren erzeugt wurde und z. B. ungewohnte Feld- und Prozedurbezeichnungen, zum Teil sogar „GO TO"-Befehle enthielt.

Den Ansatz der 'Normierten Programmierung' wird auch durch die Tatsache bestatigt, dass viele [Reportgeneratoren](https://de.m.wikipedia.org/wiki/Reportgenerator) und Datenbank-Auswertungssprachen strukturell nahezu identische Konstrukte verwenden: Der Benutzer kennt und definiert hier z. B. _Listenkopf und -Fuß_ (entsprechend Programmvorlauf und -Ende), _Gruppenkopf und Gruppenfuß_ (entsprechend Gruppenvorlauf und Gruppennachlauf) fur mehrere, hierarchisch definierte Gruppenstufen. Die _Einzelzeile_ (auch Detailbereich genannt) zeigt Informationen uber den einzelnen Datensatz, was der Einzelverarbeitung entspricht.

In ihrem vollen Umfang enthalt das Schema der normierten Programmierung Teilfunktionen, die unter gewissen Umstanden uberflussig sein oder vereinfacht implementiert werden konnen. So kann z. B. im Block 'Satzfreigabe' die Auswahl des nachsten zu verarbeitenden Datensatzes entfallen, wenn nur ein Eingabebestand vorliegt.
