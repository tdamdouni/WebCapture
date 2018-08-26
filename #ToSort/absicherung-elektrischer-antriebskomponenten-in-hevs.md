# Absicherung elektrischer Antriebskomponenten in (H)EVs

_Captured: 2018-03-07 at 16:36 from [www.all-electronics.de](http://www.all-electronics.de/absicherung-elektrischer-antriebskomponenten-in-hevs/)_

![Abb. 1: Komponenten des elektrischen Antriebsstrangs](http://www.all-electronics.de/wp-content/uploads/migrated/image/artikel/163664_1-220x165.jpg)

> _Abb. 1: Komponenten des elektrischen Antriebsstrangs_

Die Elektrifizierung des Antriebsstrangs fuhrt zu neuen und strengeren Anforderungen aufgrund der notwendigen Hochvoltkomponenten, die nationalen und internationalen Vorschriften (zum Beispiel ECE-R 100) und Normen (zum Beispiel IEC 61851) unterliegen. E/E-Systeme im Fahrzeug mussen funktional, sicher, robust, kompakt, leicht und effizient im Hinblick auf Leistung und Kosten sein - und zwar gleichzeitig. Diese Anforderungen fuhren zu einer hohen Systemkomplexitat, die bei einzelnen Controller-Bausteinen beginnt und bis hin zum Gesamtfahrzeug reicht.

Jede Komponente besteht aus mechanischen Elementen (Gehause, Kontaktierung, Kuhlung), elektrischen/elektronischen Komponenten und Software, die aufeinander abgestimmt sein und als System funktionieren mussen. Diese Subsysteme werden in der Regel in einer fruhen Phase spezifiziert und von verschiedenen Abteilungen parallel entwickelt, so dass sie zur selben Zeit unterschiedliche Reifegrade aufweisen konnen. Bild 2 zeigt die Hauptkomponenten eines elektrischen Antriebsstrangs. Abhangig von der Fahrzeugklasse und der Antriebsvariante (rein elektrisch, Hybrid, Range-Extender), variiert die konkrete Ausfuhrung von E-Maschine, Batterie, Wechselrichter und Ladegerat im Hinblick auf Leistung, Große und angestrebte Stuckzahl.

Die einzelnen Hochvoltkomponenten erfordern geeignete Testmethoden und -mittel, die sehr unterschiedlich sein konnen und doch die selbe Motivation besitzen, eine fruhzeitige und aussagekraftige Prufung zu ermoglichen. Diese garantiert eine hohe Produktqualitat, reduziert die Produkteinfuhrungszeit und die Entwicklungskosten.

Das Ziel sollte darin bestehen, einen geeigneten Prufstand zu nutzen, der die Verifikation und Validation aller Komponenten im elektrifizierten Antriebsstrang auf Komponenten- und Systemebene abdeckt. Dadurch lasst sich die abschließende und kostenintensivste Validationsphase, in welcher der Test des Pruflings in seiner realen Umgebung innerhalb eines Prototypfahrzeugs erfolgt, auf ein Minimum reduzieren.

## Auslegung eines HV-Prufstands

Ein Hochvolt-Prufstand (HV-Prufstand) ist eine nicht unerhebliche Investition, weshalb vor der Anschaffung einige Fragen beantwortet werden sollten. Die beiden offensichtlichsten betreffen die Testapplikation und das verfugbare Budget. Dabei sollte klar sein, welche Abteilungen den Prufstand nutzen werden und welche Testfalle abgedeckt werden sollen.

![Abb. 2: V-Modell. ](http://www.all-electronics.de/wp-content/uploads/migrated/image/artikel/163664_2-220x165.jpg)

> _Abb. 2: V-Modell. Scienlab electronic systems_

Die Komponenten des elektrischen Antriebsstrangs (Bild 1) lassen sich zwar entsprechend ihrer Funktion in die Bereiche Energiespeicher, Ladetechnologie, Bordnetz und Antrieb gruppieren, aber die Testanforderungen einer jeden Gruppe unterscheiden sich deutlich voneinander.

## Energiespeicher

Es gibt verschiedene technologische Ansatze. Am weitesten verbreitet sind heute jedoch elektrochemische Energiespeicher wie Lithium-Ionen-Batterien. Ein Batteriepack besteht aus mehreren Modulen, die jeweils aus vielen Batteriezellen aufgebaut sind. Daher gibt es bei der Entwicklung einer HV-Batterie Prufungen auf Zell-, Modul- und Pack-Ebene. Letzteres beinhaltet das Belasten und Laden der Batterie entsprechend echter Fahrzyklen (zum Beispiel ARTEMIS), die Absicherung und Optimierung des Batteriemanagementsystems (BMS) sowie Untersuchungen in Hinblick auf Bestandigkeit, Temperaturmanagement, Lebensdauer und Sicherheit.

Ein entsprechender Prufstand sollte eine sichere Testumgebung (bis EUCAR Gefahrenstufe 6), Werkzeuge zum Importieren und Editieren von Lastzyklen sowie eine Kommunikationsschnittstelle zur Messung und Manipulation von BMS-Daten zur Verfugung stellen. Aus wirtschaftlicher Sicht sind neben der Anschaffung vor allem die Betriebskosten zu berucksichtigen. Die verwendeten Batterie-Testsysteme sollten effizient und ruckspeisefahig sein, was sich insbesondere bei Mehrkanalprufstanden rechnet.

## Ladetechnologie

Die Ladetechnologie im und außerhalb des Fahrzeugs ist in der E-Mobilitat von zentraler Bedeutung, da ihre Umsetzung die Kundenakzeptanz maßgeblich beeinflusst. Die sich weltweit unterscheidenden Versorgungsnetze, Vorschriften und Normen erschweren dabei die Entwicklung. Das Laden bezieht nicht nur in sich geschlossene Fahrzeugkomponenten ein sondern auch Kunde, Fahrzeug-Infrastruktur sowie das offentliche Versorgungsnetz, das wiederum regionale EMV-Richtlinien geltend macht (in Deutschland DIN EN 61000-3/4).

![Abb. 3: EV-Komponenten und geeignete Prüfansätze](http://www.all-electronics.de/wp-content/uploads/migrated/image/artikel/163664_3-220x165.jpg)

> _Abb. 3: EV-Komponenten und geeignete Prufansatze_

Derzeit sind vier standardisierte Lademodi spezifiziert (IEC 61851-1), die AC- und DC-Laden mit unterschiedlichen Stromen erlauben. Die dazugehorigen elektrischen Kontaktierungen und deren Sicherung hangen jeweils von dem Lademodus und der Region ab (IEC 62196). Aufgrund der genannten Abhangigkeiten sollte ein Ladetechnologieprufstand modular und flexibel aufgebaut sein.

AC-Leistungsquellen in der Leistungsklasse von 30 bis 60 kW eignen sich zur Netznachbildung, in bidirektionaler Ausfuhrung auch zur Nachstellung von Vehicle-to-Grid-Szenarien. Ein modulares Stecker-/Steckdosen-System kann die Kompatibilitat zu den heute und zukunftig verfugbaren Ladesteckern gewahrleisten. Die Integration und Validation der Ladekommunikation setzt eine vielseitige HiL voraus, die es Entwicklern erlaubt, die diversen Kommunikationssignale aufzunehmen, zu manipulieren und auch zu simulieren.

## Bordnetz

Das Bordnetz eines Elektrofahrzeugs ist aufgrund der beiden DC-Busse und des dazugehorigen DC/DC-Wandlers deutlich komplexer als das eines herkommlichen Fahrzeugs. Hier konnen Bordnetztopologie, Spannungspegel auf der LV-Seite (12 V / 24 V / 48 V) und HV-Seite (90 bis 800 V), Anforderungen an Last und Dynamik, Batteriekapazitat sowie die zulassigen Ladestrome von Fahrzeug zu Fahrzeug variieren. Dabei erfolgt eine Untersuchung der jeweiligen Konfiguration unter anderem in Hinblick auf das Batterielademanagement. Ein entsprechender Prufstand benotigt die erforderlichen dynamischen LV/HV-Spannungsquellen und -Lasten, um gezielt einzelne Energiespeicher und Verbraucher nachbilden zu konnen. Zu den Prufthemen gehoren die dynamische Bordnetznachbildung (beispielsweise gemaß LV123 oder VW-Norm 80BOJ), die funktionale Absicherung, das Energiemanagement sowie das Nachstellen von moglichen Anwendungs- und Fehlerfallen.

## Antrieb

Zum Antrieb gehoren die E-Maschine und eine Antriebselektronik, der Traktionswechselrichter. Da sich Storungen im Antriebsstrang unweigerlich auf das Gesamtfahrzeug auswirken, steht die funktionale Sicherheit gemaß ISO 26262 im Vordergrund. Testfalle und funktionale Sicherheitsbeschrankungen variieren je nach Ausfuhrung des Antriebsstrangs. Am Automobilmarkt dominieren derzeit PMSM- und ASM-Maschinen, aber es gibt auch Projekte rund um fremderregten Synchronmaschinen und geschalteten Reluktanzmaschinen.

![Abb. 4: V-Modell begleitende Verifikations-/Validationsmethoden. ](http://www.all-electronics.de/wp-content/uploads/migrated/image/artikel/163664_4-220x165.jpg)

> _Abb. 4: V-Modell begleitende Verifikations-/Validationsmethoden._

Die Schwierigkeit besteht darin, ein ideales Verhaltnis aus Kosten und Wirkungsgrad zu erzielen. Die Validierung von E-Maschinen findet an mechanischen Prufstanden statt und ist aus verschiedenen Industriebereichen bekannt. Traktionswechselrichter fur automobile Zwecke unterliegen jedoch anderen Aspekten als industrielle Umrichter. Diese sind fur andere Maschinentypen und Betriebsbereiche ausgelegt als etwa Radnabenanwendung oder Hybridantriebe, die aus einem Verbrennungs- und E-Motor bestehen.

## Entwicklungs- und Testansatze

Das V-Modell ist in der Automobilindustrie das gangigste Entwicklungsmodell (Bild 2). Es umfasst im Wesentlichen eine Definitionsphase, eine Realisierungsphase und schließlich eine Validierungsphase. Wahrend der Definitionsphase werden haufig Modelle entwickelt und offline simuliert, um das Systemdesign so fruh wie moglich zu verifizieren. In der Realisierungsphase kommt in der Regel Rapid Control Prototyping (RCP) zum Einsatz, meistens innerhalb eines HiL-Systems (HiL: Hardware in the Loop). Die genannten Ansatze sind Standard bei der Entwicklung von elektronischen Steuergeraten (ECUs).

Der rechte Flugel des V-Modells enthalt die Integration der einzelnen Subkomponenten sowie die Prufung des zu entwickelnden Systems. In dieser Phase finden Verifikation und Validation statt, die sich stark vereinfacht folgendermaßen beschreiben lasst: Die Verifikation stellt sicher, dass die implementierten Funktionen der wahrend der Definitionsphase erarbeiteten Spezifikation entsprechen. Die Validation soll dagegen sicherstellen, dass das Produkt die Hersteller- und Kundenerwartungen erfullt. Im Zuge der vielen Pruffalle sind verschiedene Tests erforderlich: Im einfachsten Falle ist nur die Überprufung eines speziellen Code-Zweigs erforderlich, aber oft auch Tests individueller elektronischer Komponenten (wie Sensoren oder IGBT-Treiber) bis hin zu Zyklusfahrten im Versuchsfahrzeug.

## Testansatze

Der Detaillierungsgrad unterscheidet sich von Test zu Test. Um den Testaufwand zu verringern und den Reifegrad des Pruflings zu maximieren, sollten Prufungen zu einem fruhestmoglichen Zeitpunkt stattfinden - und das mit dem jeweils erforderlichen Detaillierungsgrad.

Der einfachste Testansatz ist das Open-Loop-Verfahren. Dabei werden alle vom Prufling erwarteten Schnittstellen und Signale (zum Beispiel Temperatursignal) durch den Prufstand elektrisch nachgebildet. So lasst sich der Prufling isoliert betreiben und auf seine generelle Funktionsfahigkeit untersuchen. Beim Open-Loop-Betrieb wird die Reaktion des Pruflings allerdings nicht berucksichtigt, so dass anwendungsnahe Prufablaufe kaum moglich sind.

Daher kommt zusatzlich das Closed-Loop-Verfahren zur Anwendung, bei dem sich auch die Wechselwirkungen von Komponenten auswirken. Im einfachsten Fall pruft das Team dazu benachbarte Komponenten eines Systems im Verbund. Aus den zuvor genannten Grunden stehen die einzelnen Komponenten aber meist nicht gleichzeitig zur Verfugung oder besitzen unterschiedliche Reifegrade, so dass eine Validierung im Verbund nur bedingt oder erst spat realisierbar ist, was eingeschrankte Analyse- und Debugging-Moglichkeiten sowie hohere Kosten zur Folge hat.

![Abb. 5: Power-HiL Architektur.](http://www.all-electronics.de/wp-content/uploads/migrated/image/artikel/163664_5-220x165.jpg)

> _Abb. 5: Power-HiL Architektur. Scienlab electronic systems_

Demnach ist es wunschenswert, die Komponenten einzeln und unabhangig voneinander testen zu konnen und dabei realitatsnahe Betriebssituationen nachzubilden, beispielsweise Lastwechsel aus aufgenommenen Fahrzyklen unter verschiedenen Klimabedingungen. Dank moderner Signalverarbeitung und Leistungselektronik ist es heute moglich, die dazu erforderlichen elektrischen Schnittstellen dynamisch nachzubilden. Dazu muss die Umwelt eines Pruflings in Modellen definiert und dann in Echtzeit am Prufstand ausgefuhrt werden.

So benotigt zum Beispiel ein Traktionswechselrichter unter anderem ein Batterie- und Maschinenmodell. Der Detaillierungsgrad des Modells stellt in diesem Fall einen Kompromiss aus Realitatsnahe und den dabei entstehenden Entwicklungskosten dar.

Die folgenden Prufstands-Arten eignen sich fur Closed-Loop-Tests:

  * LV-HiL: An einem LV-HiL-Prufstand erfolgt der Test von Steuergeraten auf Signalebene mit LV (Low-Voltage, Niederspannung). Dazu erfasst der HiL-Prufstand uber Sensoren vom Prufling ausgehende Signale, um sie dann in Echtzeit zu verarbeiten. Umgekehrt emuliert der HiL-Prufstand die am Prufling eingehenden Großen elektrisch - und zwar mit Spannungen unter 50 V. Dazu gehoren auch die Kommunikationsbusse wie CAN und Flexray, durch die der Prufling mit weiteren simulierten Steuergeraten Informationen austauscht.
  * Maschinenprufstande … sind anwendbar auf mechatronische Systeme wie etwa eine E-Maschine oder einen Traktionswechselrichter fur Hybridfahrzeuge. Im Falle des Wechselrichters wird eine HV-Batterie beziehungsweise eine aquivalente Emulation davon, eine E-Maschine sowie eine Lastmaschine und die dazugehorigen Antriebselektronik benotigt.
  * Power HiL: Im Gegensatz zur gewohnlichen HiL-Losung erfolgt hierbei auch die Nachbildungen der elektrischen Schnittstellen, die mit Spannungen uber 50 V arbeiten. Hierzu kommen HV-Emulatoren zum Einsatz, die im Testaufbau fehlende Realkomponenten ersetzen. Diese erzeugen die system- und arbeitspunktabhangigen Spannungen oder Strome gemaß eines Modells. Im Falle des Wechselrichtertests lasst sich so nicht nur die Steuerelektronik sondern auch die Leistungsendstufe als System testen - und zwar unabhangig von der Verfugbarkeit und der Restriktion eines Energiespeichers sowie der E-Maschine.

## Vergleich von Verifikations- und Validationsverfahren

Tabelle 1 zeigt einen Vergleich der zuvor genannten Verifikations- und Validationsverfahren, unter anderem im Hinblick auf die Nutzbarkeit der jeweiligen Methode zu bestimmten Entwicklungsphasen.

![ Tabelle 1: Vergleich von Verifikations- und Validationsverfahren. Die Bewertungsskala reicht von ++ für sehr gut geeignet bis zu – für schlecht oder gar nicht geeignet.](http://www.all-electronics.de/wp-content/uploads/migrated/image/artikel/163664_7-220x165.jpg)

> _Tabelle 1: Vergleich von Verifikations- und Validationsverfahren. Die Bewertungsskala reicht von ++ fur sehr gut geeignet bis zu - fur schlecht oder gar nicht geeignet._

Die Simulation ist sehr gut wahrend der Definitions- und auch bedingt wahrend der Realisierungsphase geeignet, aber nicht zum Testen von Hardware. Den Bereich zwischen der Offline-Simulation und Verifikation auf elektrischer Ebene schließt zunachst die LV-HiL, die begleitend zur Implementierung sowie bei Funktionstests Anwendung findet. Dem gegenuber steht der Prototypenaufbau, bei dem die aus der Entwicklung kommenden Systeme im Verbund und unter realer Beanspruchung abgesichert werden. Ein derart geschlossener Aufbau ist allerdings erst dann ausreichend aussagekraftig, wenn alle betroffenen Komponenten mit dem entsprechenden Reifegrad verfugbar sind, so dass dies bei komplexeren Systemen entwicklungsbegleitend nicht in Betracht kommt.

Dazwischen finden sich der mechanische Prufstand sowie die Power-HiL ein. Beide erlauben das Testen von leistungselektronischen Fahrzeugkomponenten als System inklusive der verbauten Elektronik, Sensorik und Aktorik. Sie eignen sich so auch fur End-Of-Line Tests. Lasst man zunachst die E-Maschine als Prufling unberucksichtigt, so besitzt die Power-HiL zwei entscheidende Vorteile. Zum einen entfallt das zeit- und kostenintensive Umrusten der Maschine. Der zweite und wahrscheinlich wichtigste Vorteil besteht darin, dass die zuvor gestellte Bedingung nach einem von der Verfugbarkeit der anderen zu entwickelnden Einzelteile unabhangigen Test erfullt wird, so dass sich die Komponenten des elektrischen Antriebsstrangs simultan entwickeln und testen lassen. Bild 3 veranschaulicht die drei vorgestellten Prufstandsarten und deren Testfokus.

Die genannten Vorteile ergeben sich durch Anwendung eines frei parametrierbaren Testsystems mit der erforderlichen Leistungsendstufe zur elektrischen Nachbildung einer HV-Batterie oder einer E-Maschine sowie eines adaquaten Modells. Die sich daraus ergebenden Freiheitsgrade erlauben einerseits einfache Testablaufe zur Absicherung essentieller Funktionen mit geringem Aufwand. Andererseits lassen sich sehr detaillierte Versuchsablaufe durchfuhren, beispielsweise zur Optimierung der Regelungsstrategie. Bild 4 zeigt die vorgestellten Verifikations- und Validationsansatze im Bezug zum V-Modell.

## Applikationsbeispiel Wechselrichtertest

Traktionswechselrichter sind hoch integrierte Systeme, die gemeinsam mit einem Hochvolt-Speicher und einer E-Maschine betrieben werden. Das Testspektrum reicht von einfachen ESD-Tests am Stecker (Komponentenlevel) bis hin zur Nachstellung eines Batterieabwurfs im Moment einer Rekuperation mit maximaler Leistung (Systemlevel). Der folgende Teil des Beitrags vergleicht drei fundamental unterschiedliche Prufstandsarten: Maschinenprufstand, Drosselprufstand und Power-HiL.

## Vergleich von Wechselrichtertest-Prufstanden

Maschinenprufstande sind - elektrisch gesehen - der tatsachlichen Applikation am nachsten. Bis auf die Belastung, dargestellt durch eine separate Lastmaschine, entspricht der Aufbau dem aus dem Fahrzeug. Dadurch sind aussagekraftige Testergebnisse zu erwarten und fur die Identifikation der Parameter der im Antriebssystem einzusetzenden Maschine oder Messungen hinsichtlich EMV unabdingbar. Der Nachteil dieses Prufstands ist jedoch die Voraussetzung, dass die E-Maschine verfugbar ist. Dies ist allerdings in fruhen Entwicklungsphasen haufig nicht der Fall. Wahrend sowohl die Mechanik des Antriebssystems als auch das Fahrzeug, die Straße und der Fahrer durch Modelle abgebildet werden konnen, hangt die Aussagekraft der Messergebnisse von den elektrischen und magnetischen Eigenschaften der verfugbaren E-Maschinen ab. Selbiges gilt fur die Flexibilitat bei der Parametervariation. Eine Fehleremulation ist zudem nur mit großem Aufwand moglich.

Das Testen von Traktionswechselrichtern an Drosselprufstanden ist fur einige Applikationen eine gute Alternative. Der passive Ansatz bringt die niedrigsten Gesamtkosten und das einfachste Handling mit sich. Allerdings limitieren ein konstanter Leistungsfaktor, die fehlende Variabilitat und die niedrigste Applikationsnahe die durchfuhrbaren Tests deutlich.

![Tabelle 2: Vergleich von drei Wechselrichtertest-Prüfständen](http://www.all-electronics.de/wp-content/uploads/migrated/image/artikel/163664_8-220x165.jpg)

> _Tabelle 2: Vergleich von drei Wechselrichtertest-Prufstanden_

In den meisten Fallen bietet ein emulations-basierter Prufstand die besten Testbedingungen. Es ist der variabelste Ansatz, da sich alle wichtigen Parameter wie Maschinen- und Batterietyp oder Leistung auf Knopfdruck verandern lassen. Jeder Prufdurchlauf ist zu 100% reproduzierbar und trotz getakteter Endstufen mit der realen Anwendung gut vergleichbar. Einstellbare Abschaltgrenzen garantieren eine sofortige Unterbrechung des Leistungsflusses und schutzen so Bediener, Prufstand und Prufling. Material- und fertigungsbedingte Streuung (etwa in der Strangimpedanz oder dem Sattigungsverhalten), Maschinenfehler (zum Beispiel Phasenkurzschlusse) und Resolverfehler (zum Beispiel Leitungsbruche) lassen sich ohne weiteres nachbilden. Alle im vorherigen Kapitel genannten Vorteile der modellbasierten Emulation kommen hier zur Geltung. Tabelle 2 zeigt die wesentlichen Unterschiede zwischen den drei genannten Prufstandsarten im Überblick.

Jeder der vorgestellten Prufstandsarten hat individuelle Vor- und Nachteile. Beispielsweise eignet sich der gunstige Drosselprufstand gut fur beschleunigte Alterungstests, sofern die Leistungsteilung zwischen IGBT und Diode nicht von Interesse ist. Der Maschinenprufstand dagegen eignet sich fur den abschließenden Systemtest, bei dem der gemeinsame Betrieb von Wechselrichter und E-Maschine erfolgt.

Fur die Prufszenarien dazwischen bietet der Power-HiL-Ansatz ein optimales Verhaltnis aus Applikationsnahe, Reproduzierbarkeit, Variabilitat, Fehleremulation und Sicherheit .

## Power HiL-Prufstand

Eine typische Prufstandskonfiguration besteht aus einem Batterie-Emulator auf der DC-Seite sowie einem Maschinen-Emulator auf der AC-Seite des Inverters. Der Einsatz von Leistungselektronik erweitert den Aufbau eines konventionellen HiL-Systems um die Vorteile, die HV-Komponenten des Pruflings mit Hardware-In-The-Loop-Methoden verifizieren zu konnen. Bedienung und Steuerung des Power-HiL entsprechen denen eines herkommlichen Systems. Bild 5 zeigt die Power-HiL-Architektur, die vertikal in die vier Bereiche Benutzerschnittstelle, Modellsimulation, HV-Emulation und Sicherheit unterteilt ist.

![Abb. 6: Power-HiL-Prüfstand \(für Wechselrichter\) bei Scienlab electronic systems. ](http://www.all-electronics.de/wp-content/uploads/migrated/image/artikel/163664_6-220x165.jpg)

> _Abb. 6: Power-HiL-Prufstand (fur Wechselrichter) bei Scienlab electronic systems._

Eine hohe Sinus-Grundfrequenz ist notwendig fur Betriebspunkte bei hohen Drehzahlen; die Emulation einer PMSM-Maschine im Feldschwachebetrieb bedingt dazu deutlich hohere Spannungen auf der Emulator-Seite als im Inverter. Testfalle außerhalb des Inverter-Betriebsbereichs erfordern zudem hohere Strome als dessen spezifizierte Spitzenstrome. Die daraus resultierenden Anforderungen an den Maschinen-Emulator in Bezug auf Spannungen und Strome sind damit hoher als die Leistungsgrenzen des Pruflings.

Die Induktivitat der E-Maschine wird durch eine Kombination aus physikalisch vorhandenen Drosseln und emulierten Widerstanden nachgebildet. Die resultierende Induktivitat lasst sich in nahezu analoger Genauigkeit im Bereich Mikrohenry bis Millihenry in Echtzeit einstellen und erweitern damit die Betriebsgrenzen, denn schließlich varriert die optimale Drosseleinstellung bei den Betriebsbedingungen unterschiedlicher Test-Cases.

Der Maschinen-Emulator emuliert auch die Signale des Rotorlagegebers sowie der notwendigen Temperatursensoren. Am Markt haben sich diverse Lagesensorarten etabliert: Impuls-Encoder oder sinus-basierte Resolver. Diese sowie unterschiedliche Messprinzipien und Sensortypen zur Temperaturerfassung deckt der parametrierbare Sensor-Emulator ebenfalls ab.

Der vorgestellte Power-HiL fur den Wechselrichtertest ist bereits in diversen Varianten bei uber 20 internationalen OEMs und Tier-1-Zulieferern im gesamten Applikationsspektrum erfolgreich im Einsatz. Die Messergebnisse weisen eine hohe Übereinstimmung zwischen Power-HiL-Prufstand und realer E-Maschine auf.

## Fazit

Power-HiL-Prufstande unterstutzen die simultane Entwicklung und Absicherung von Antriebskomponenten durch ein weites Spektrum an Verifikations- und Validationsmitteln. Sie schließen die Lucke zwischen der LV-HiL und dem Versuchsfahrzeug, die sich aus den Einschrankungen eines Maschinenprufstandes ergibt. Die selektive Emulation von Hochvolt-Komponenten ermoglicht die parallele Entwicklung und Validation von HV-Batterie, Traktionswechselrichter, E-Maschine, DC/DC-Wandler sowie Ladesystemen und beschleunigt dadurch die Systemintegration.

## Auf einen Blick

Power-HiL-Prufstande

… unterstutzen die simultane Entwicklung und Absicherung von Antriebskomponenten durch ein weites Spektrum an Verifikations- und Validationsmitteln. Sie schließen die Lucke zwischen der LV-HiL und dem Versuchsfahrzeug, die sich aus den Einschrankungen eines Maschinenprufstandes ergibt. Die selektive Emulation von Hochvolt-Komponenten ermoglicht die parallele Entwicklung und Validation von HV-Batterie, Traktionswechselrichter, E-Maschine, DC/DC-Wandler sowie Ladesystemen und beschleunigt dadurch die Systemintegration.
