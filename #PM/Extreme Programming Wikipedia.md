# Extreme Programming

_Captured: 2015-10-23 at 00:47 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Extreme_Programming)_

![](http://upload.wikimedia.org/wikipedia/commons/thumb/1/19/XP-Life.png/400px-XP-Life.png)

> _XP Lebenszyklus_

XP ist ein durch fortlaufende [Iterationen](https://de.m.wikipedia.org/wiki/Iteration) und den Einsatz mehrerer Einzelmethoden strukturierendes Vorgehensmodell. XP entstand durch die [Synthese](https://de.m.wikipedia.org/wiki/Synthese) verschiedener Disziplinen der [Softwareentwicklung](https://de.m.wikipedia.org/wiki/Softwareentwicklung) und basiert auf in der Praxis bewahrten Methoden, auch [Best Practices](https://de.m.wikipedia.org/wiki/Best_Practice) genannt.

XP folgt einem strukturierten Vorgehen und stellt die Teamarbeit, Offenheit und stete Kommunikation zwischen allen Beteiligten in den Vordergrund. Kommunikation ist dabei eine Grundsaule.

Die Methode geht davon aus, dass der Kunde die [Anforderungen](https://de.m.wikipedia.org/wiki/Anforderung) an die zu erstellende [Software](https://de.m.wikipedia.org/wiki/Software) zu Projektbeginn noch nicht komplett kennt und nicht hinreichend strukturieren kann beziehungsweise das mit der Realisierung betraute Entwicklerteam nicht uber alle Informationen verfugt, um eine verlassliche [Aufwandsschatzung](https://de.m.wikipedia.org/wiki/Aufwandssch%C3%A4tzung_\(Softwaretechnik\)) uber die notwendige Dauer bis zum Abschluss zu geben. Im Laufe eines Projektes andern sich nicht selten Prioritaten und Gewichte. Zu Beginn geforderte Funktionen der Software werden moglicherweise in einer anderen Form benotigt oder im Laufe der Zeit sogar komplett hinfallig.

Bei einer konsequenten Ausrichtung an XP soll die zu erstellende Software schneller bereitgestellt werden sowie eine hohere Softwarequalitat und Zufriedenheit des Kunden als mit traditionellen Ansatzen zu erreichen sein. Der Kunde soll ein einsatzbereites Produkt erhalten, an dessen Herstellung er aktiv teilgenommen hat.

Neue Funktionalitat wird permanent entwickelt, integriert und getestet. Um zu der zu entwickelnden Funktionalitat zu gelangen, werden jeweils die Schritte Risikoanalyse, Nutzenanalyse, die Bereitstellung einer ersten ausfuhrbaren Version ([Prototyping](https://de.m.wikipedia.org/wiki/Prototyping_\(Softwareentwicklung\))) und ein Akzeptanztest durchgefuhrt.

Nach Vertretern dieses Vorgehensmodells ist XP [Risikomanagement](https://de.m.wikipedia.org/wiki/Risikomanagement). Es bejaht das Risiko, geht aktiv darauf ein und versucht, es zu minimieren. Dieser implizite Umgang mit dem Faktor _Risiko_ steht im Gegensatz zu eher expliziten Vorgehensweisen, wie der Aufstellung einer _Risikoliste_.[[1]](https://de.m.wikipedia.org/wiki/Extreme_Programming) Softwareentwicklungsprojekte sind unterschiedlichen Gefahren ausgesetzt, fur die Extreme Programming Losungen anbieten soll.

Dem Kunden bietet XP, gerade durch seine kurzen Entwicklungszyklen, jederzeit die Moglichkeit, steuernd auf das Projekt einzuwirken. Dadurch soll erreicht werden, dass sich das Produkt aktuellen Anforderungen anpasst, statt uberholten Anforderungen aus einer langst vergangenen Analysephase zu genugen und damit bereits bei Einfuhrung veraltet zu sein. Zudem kann der Kunde bereits nach kurzer Zeit ein unvollstandiges aber zumindest funktionstuchtiges Produkt einsetzen. Der Kunde ist im besten Fall jederzeit auf demselben aktuellen Informationsstand bezuglich des Projektes wie das Entwicklerteam.

Ein haufiger Ansatz traditioneller Softwareerstellung ist: _„Vielleicht brauchen wir irgendwann einmal diese oder jene Programmfunktionen"_, auch [Feature](https://de.m.wikipedia.org/wiki/Feature-Request) genannt. XP stellt dem gegenuber: _Lass es!_ (vgl. auch [YAGNI](https://de.m.wikipedia.org/wiki/YAGNI) -„You Ain't Gonna Need It"). Vor jedem der kurzen Entwicklungsschritte wird zusammen mit dem Kunden genau festgelegt, was wirklich sinnvoll ist entwickelt zu werden. Die so genannte „[Featuritis](https://de.m.wikipedia.org/wiki/Featuritis)" soll damit vermieden werden.

Eines der großten Risiken der Softwareentwicklung ist, dass dem Kunden ein Produkt bereitgestellt wird, das er in dieser Form nicht mochte. XP mochte dem durch standige, aktive Einbeziehung des Kunden in den Entwicklungsprozess vorbeugen. Er kann sich Zwischenversionen ansehen und direkt Änderungswunsche außern.

Um diese Vorteile nutzen zu konnen, muss der Kunde im Gegenzug auch eine Reihe von Einschrankungen und Forderungen hinnehmen. So fordert XP von ihm, dass er wahrend der gesamten Entwicklungszeit mit dem Entwicklungsteam zusammenarbeitet. Des Weiteren muss er auf eine formale Festlegung der Projektinhalte (Spezifikation) verzichten (siehe auch _[Der ideale Kunde](https://de.m.wikipedia.org/wiki/Extreme_Programming)_).

Es existiert keine strikte Rollentrennung, da die Aufgabenverteilung abhangig von Situation und Fahigkeiten geschieht. Der allgemeine Wissensaustausch und die stetige Kommunikation beugen einem Wissens[monopol](https://de.m.wikipedia.org/wiki/Monopol) vor. Dies soll den Einzelnen entlasten, wohingegen der Druck auf einer Person lastet, wenn diese sich als Einzige in einem [Modul](https://de.m.wikipedia.org/wiki/Modul_\(Software\)) auskennt.

Um Unbenutzbarkeit aufgrund von Programmfehlern sowie fehlerhafte Integration einzelner [Komponenten](https://de.m.wikipedia.org/wiki/Komponente_\(Software\)) zu vermeiden, werden bei XP viele und moglichst fruhe Tests angestrebt. Jede Komponente besitzt einen [Modultest](https://de.m.wikipedia.org/wiki/Modultest) (Unit-Test); in [Java](https://de.m.wikipedia.org/wiki/Java_\(Programmiersprache\)) beispielsweise mit [JUnit](https://de.m.wikipedia.org/wiki/JUnit). Bei Feststellung eines Fehlers in einer Komponente wahrend der Entwicklung wird ein Test entwickelt, der diesen lokalisiert. Eine tagliche Einbeziehung der einzelnen am Projekt beteiligten Entwickler mit automatischer Ausfuhrung der Tests ([Regressionstest](https://de.m.wikipedia.org/wiki/Regressionstest)) soll zu einer erheblichen Qualitatssteigerung fuhren. Fehler sollen so fruher gefunden werden, denn je spater ein Fehler gefunden wird, desto teurer ist meist dessen Korrektur. Außerdem soll die [testgetriebene Entwicklung](https://de.m.wikipedia.org/wiki/Testgetriebene_Entwicklung) zu einem leichter wartbaren Programmcode mit besserem Design fuhren.

Da die meisten Einzelmethoden gerade auf den Alltag der Programmierer ausgerichtet sind, bedeutet XP zugleich auch ein hohes Maß an Herausforderung und ggf. Umstellung der Beteiligten. Auf diese Aspekte wird ausfuhrlicher im Abschnitt _[Der ideale Programmierer](https://de.m.wikipedia.org/wiki/Extreme_Programming)_ eingegangen.

Dem Projekt bietet XP die Moglichkeit, Risiken zu minimieren. Unter richtiger Anwendung von XP soll der Kunde Software erhalten, deren Umfang ihn nicht uberrascht. Das Team soll ferner gegen Ausfall (Krankheit, Unfall, Stellenwechsel) Einzelner nicht mehr so anfallig sein. Ein ehrlicher Umgang mit dem Kunden soll die Glaubwurdigkeit und Zufriedenheit steigern und die [Angst](https://de.m.wikipedia.org/wiki/Angst) minimieren, die unter Umstanden zwischen Kunde („Haben die mich verstanden?", „Was werden sie wohl liefern?") und Entwicklung („Was will er eigentlich genau?", „Ob er zufrieden sein wird mit dem, was wir liefern?") vorherrscht.

Aufwandsabschatzungen werden verlasslicher, da sie im Team getroffen und standig einer kritischen Überprufung ([Review](https://de.m.wikipedia.org/wiki/Review_\(Softwaretest\))) unterzogen werden. [Teamgeist](https://de.m.wikipedia.org/wiki/Teamgeist) wird laut XP gefordert. Jedem im Team sollte klar sein, dass das Ziel nur als Einheit erreichbar ist. Sollte ein Projekt, zum Beispiel aus Kostengrunden, vorzeitig eingestellt werden, besteht durch die regelmaßigen Iterationen dennoch ein zumeist einsatzfahiges Produkt.

In vielen Projekten gelingt es nicht, das Produkt in der gewunschten Zeit im gewunschten Umfang und mit den geplanten Ressourcen fertigzustellen. In XP soll nur das verwirklicht werden, was tatsachlich einen Nutzen fur den Kunden hat. Durch standigen Austausch mit dem Kunden sowie Prioritatsanalysen sollen die unbedingt zu erstellenden Funktionen identifiziert werden. Dabei sollte mit den Funktionen begonnen werden, die den großten Nutzen haben und das großte (technische) Risiko beinhalten.

Extreme Programming stellt aus wirtschaftswissenschaftlicher Sicht eine Form der [Organisation](https://de.m.wikipedia.org/wiki/Organisation) dar, die direkt die Prozesse der [Wertschopfung](https://de.m.wikipedia.org/wiki/Wertsch%C3%B6pfung_\(Wirtschaft\)) beschreibt. In den Wirtschaftswissenschaften werden zur Bewertung von Extreme Programming auch Erkenntnisse anderer [Sozialwissenschaften](https://de.m.wikipedia.org/wiki/Sozialwissenschaften), insbesondere der [Soziologie](https://de.m.wikipedia.org/wiki/Soziologie), genutzt.

Dem [Risikomanagement](https://de.m.wikipedia.org/wiki/Risikomanagement) dient diese Alternative vor allem zur Steuerung von [Risiken](https://de.m.wikipedia.org/wiki/Risiko). Wie bei vielen Prozessen der Wertschopfung sind besonders in der Softwareentwicklung Risiken meist operative Risiken: Die Wertschopfung ist [ineffektiv](https://de.m.wikipedia.org/wiki/Effektivit%C3%A4t), wenn die Kundenwunsche nicht getroffen und gesteckte Ziele somit verfehlt wurden. Die Wertschopfung ist ineffizient, wenn zum Erreichen des Ergebnisses ein zu hoher Aufwand entstand. Risikoverminderung, und dadurch Effektivitat und Effizienz, soll bei Extreme Programming durch die Art des Umgangs mit Fehlern, mit Mitarbeitern und mit Kunden erreicht werden:

  * Kompensation von Krankheitsausfallen
  * Kundennahe Entwicklung
  * Weniger Fehler im Ergebnis

Ein moglichst genaues Erkennen von Risiken durch das Verfahren selbst soll uber angepasste Aufwandsschatzungen eine Bewertung des zu akzeptierenden Risikos ermoglichen. Extreme Programming kann dagegen eine Risikoverlagerung erschweren. Aus der Sicht des Risikomanagements ist Extreme Programming also _nur_ eine Moglichkeit, mit Risiken umzugehen, und zwar eine Moglichkeit, die Vor- und Nachteile besitzt.

Das [Personalwesen](https://de.m.wikipedia.org/wiki/Personalwesen) in Unternehmen betrachtet Extreme Programming insbesondere im Hinblick auf seine Auswirkungen auf die Mitarbeiterzufriedenheit. Extreme Programming soll dabei bewusst oder unbewusst zum [kooperativen Lernen](https://de.m.wikipedia.org/wiki/Kooperatives_Lernen) beitragen. Fur das Personalwesen ist dieses Verfahren also besonders aus Sicht der [Personalentwicklung](https://de.m.wikipedia.org/wiki/Personalentwicklung) interessant. Durch hohere Mitarbeiterzufriedenheit und durch die Vermeidung von Überstunden soll die gesamte Produktivitat erhoht werden. Die Praktik des Pair-Programming lasst allerdings - rein mathematisch betrachtet - Gegenteiliges vermuten. Die Vermeidung von Spezialistentum und individuellem Besitz von Wissen uber Teile der Software dient der [kollektiven Wissenskonstruktion](https://de.m.wikipedia.org/wiki/Kollektive_Wissenskonstruktion) und kann die Ersetzung von Entwicklern vereinfachen.

Die gesamte Betriebswirtschaftslehre ist in den letzten Jahren von der prozess- bzw. wertschopfungsorientierten zur kunden- bzw. marktorientierten Unternehmensfuhrung ubergegangen. Auch wenn Extreme Programming die Wertschopfung beschreibt, bietet es Moglichkeiten zu kundennaher Vorgehensweise. Über Extreme Programming soll - wie in anderen Branchen schon langer ublich - eine großere Einbindung des Kunden in den Wertschopfungsprozess moglich sein. Wichtig wird dies umso mehr, wenn Software weniger als [Faktorgut](https://de.m.wikipedia.org/wiki/Faktormarkt), sondern mehr als [Vorprodukt](https://de.m.wikipedia.org/wiki/Halbfabrikat) erstellt und vertrieben wird.

Ebenfalls betrachtet werden muss Extreme Programming und dessen Aufwand aus Sicht des [Informationsmanagements](https://de.m.wikipedia.org/wiki/Informationsmanagement), das den Aufwand fur den unbedingt notwendigen Informationsaustausch festlegt und okonomisch bewertet. Genutzt werden dazu Erkenntnisse der [Informations-](https://de.m.wikipedia.org/wiki/Informationswissenschaft) und [Kommunikationswissenschaft](https://de.m.wikipedia.org/wiki/Kommunikationswissenschaft). Dabei kann insbesondere die [Medienreichhaltigkeitstheorie](https://de.m.wikipedia.org/wiki/Medienreichhaltigkeitstheorie) eingesetzt werden: Weil die zu diskutierenden und kommunizierenden Sachverhalte in der Regel komplex sind, werden auch komplexe, reichhaltige [Kommunikationsmedien](https://de.m.wikipedia.org/wiki/Massenmedien) gewahlt: direkte, personliche Gesprache. Kritisch zu hinterfragen ist hierbei die schwierige raumliche Verteilbarkeit der Entwicklungsprozesse sowie die Einbindung des Kunden, da unter Umstanden eine raumliche Trennung zwischen Entwicklern und Kunden besteht.

Vereinzelt wird Extreme Programming als informelle (und damit unverbindliche) Methode bezeichnet. Das trifft jedoch weder den Ansatz noch das Ziel. Tatsachlich ist die Formalisierung der Methode des Extreme Programming bewusst flach und schlank gehalten. Hingegen muss ein Einvernehmen zwischen Kunden und Programmierern hinsichtlich der Verbindlichkeit der erstellten Unterlagen hergestellt werden, solange diese noch nicht durch neuere Fassungen ersetzt wurden. Weiter muss der Vorgang des Ersetzens einer Fassung einer Unterlage durch eine neuere Fassung dieser Unterlage soweit formalisiert sein, dass beide Parteien Kenntnis von dieser Ersetzung haben und diese Ersetzung annehmen.

Neben dem Entwicklungsteam gibt es im Wesentlichen den Kunden und den _Product-Owner_. Innerhalb des Entwicklerteams soll es keine Rollentrennung geben. So wird nicht unterschieden, wer im Team welches Spezialgebiet hat, beziehungsweise welche besonderen Fahigkeiten er mitbringt. Jede Person im Team wird als [Entwickler](https://de.m.wikipedia.org/wiki/Software-Entwickler) (_Developer_) bezeichnet. Ein [Manager](https://de.m.wikipedia.org/wiki/Manager_\(Wirtschaft\)) ist gewohnlich eine Person mit Fuhrungsbefugnis, also ein disziplinarischer Vorgesetzter. Dieser hat in XP weniger Wichtigkeit. Dagegen gibt es einen „Leiter" des Teams, also jemand, der die Kommunikation mit Kunden oder untereinander koordiniert. Auch der Nutzer der zu erstellenden Software kann das Team durch das Projekt fuhren. Die Unterscheidung zwischen Manager und „Leiter" ist fur agile Vorgehensmodelle typisch. Der Product-Owner, der uber die genaue Vorgehensweise entscheidet, tragt die Verantwortung. Product-Owner im Sinne von XP kann beispielsweise ein Vertreter des Produktmanagements, ein Kunde oder ein Nutzer des Produktes sein. Die Rollen sind je nach Projekt und Umgebung unterschiedlich, haufig auch in Personalunion, verteilt.

Die Rollen bei XP 

Rolle Beispiel Aufgaben

Produktbesitzer
Produktmanagement, Marketing, ein Benutzer, Kunde, Manager des Benutzers, Analyst, Sponsor
Hat Verantwortung, setzt Prioritaten, Entscheider fur bestes [ROI](https://de.m.wikipedia.org/wiki/Return_on_Investment)

Kunde
Auftraggeber, kann auch der Produktbesitzer sein, kann, muss aber nicht der Benutzer sein
Entscheidet, was gemacht wird, gibt regelmaßig Ruckmeldung, Auftraggeber

Entwickler
Bestandteil des Teams, das ganze Entwicklungsteam besteht aus Entwicklern: Programmierer, Tester, DB-Experten, Architekt, Designer
Entwickelt das Produkt

Projektmanager
Ist gewohnlich der Produktbesitzer. Kann auch Entwickler aber nicht Manager des Teams sein
Fuhrung des Teams

Benutzer
Der Nutzer des zu erstellenden Produktes
Wird das zu erstellende Produkt nutzen

Der [Umgang mit den Anforderungen und deren Verwirklichung](https://de.m.wikipedia.org/wiki/Anforderungserhebung) ist eine zentrale Komponente XPs. Durch eine Mischung verschiedener, in den folgenden Abschnitten dargestellter Maßnahmen soll die Qualitat und Flexibilitat der Software gesteigert werden, so dass sich der Zusammenhang zwischen dem Zeitpunkt der Anforderungsstellung und den damit entstehenden Kosten weitgehend linear darstellt.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/6/60/Xpkurve.png/400px-Xpkurve.png)

> _Änderungskostenkurve in Abhangigkeit vom Zeitpunkt der Änderung_

Bei einem weitgehend linearen Verlauf einer ableitbaren Ä[nderungskostenkurve](https://de.m.wikipedia.org/wiki/Kostenaufl%C3%B6sung) wird auf eine vollstandige Erhebung aller Anforderungen zu Beginn des Projektes verzichtet. Stattdessen werden die sich erst im Laufe der Umsetzung ergebenden Anforderungen berucksichtigt. Dieses Vorgehen resultiert aus den Beobachtungen, dass einerseits der Kunde zu Beginn des Projektes noch gar nicht genau weiß, was er mochte, andererseits sich diese Anforderungen im Laufe eines Projektes andern. Daruber hinaus sind Fehler umso teurer, je spater man sie findet. Im schlimmsten Fall erhalt der Kunde nach einem langen Projekt etwas geliefert, was er in dieser Form gar nicht haben mochte. Standiger Gedankenaustausch mit dem Kunden, Offenheit fur Änderungen und stetige Integration wirken diesen Risiken entgegen. Anforderungen werden nicht selten zunachst als [Prototypen](https://de.m.wikipedia.org/wiki/Prototyping_\(Softwareentwicklung\)) bereitgestellt. Dabei handelt es sich um Versionen, die noch nicht die volle, endgultige Funktionalitat besitzen.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/c/ca/Release3.png/400px-Release3.png)

> _Release, Iterationen, User-Storys und Tasks_

Im Rahmen der Planung wird gewohnlich folgende Unterscheidung vorgenommen: ein [Release](https://de.m.wikipedia.org/wiki/Versionierung) beinhaltet die Funktionen, die insgesamt und fur sich geschlossen die Bereitstellung einer neuen Version des Produktes rechtfertigen. Um zu dem Release zu kommen, ist ein Release-Plan aufzustellen, der im Wesentlichen aus [Iterationen](https://de.m.wikipedia.org/wiki/Iteration) besteht. Unter anderem abhangig von der geschatzten Entwicklungsdauer des Release werden die Iterationen in Anzahl und Dauer festgelegt. Iterationen dauern ublicherweise zwischen einer und vier Wochen. Der Zeitpunkt der Fertigstellung wird als Zeitintervall diskutiert, dessen Große im Laufe des Release aufgrund gewonnener Erkenntnisse und des durchgefuhrten Fortschritts standig abnimmt.

![](http://upload.wikimedia.org/wikipedia/commons/b/bc/Risk-value-priorisierung.png)

> _Risiko-Wert Gegenuberstellung und Verteilung der Prioritaten_

Die innerhalb der Iterationen umzusetzenden einzelnen Neuerungen werden mit dem Kunden durch _[User-Storys](https://de.m.wikipedia.org/wiki/User-Story)_ beschrieben.

Das ganze Team ist bei der Erstellung beteiligt. Die abzuarbeitenden Anforderungen werden auf einzelnen Karten (_Story Cards_) geschrieben und fur alle sichtbar platziert. Neben diesem Vorgehen ist es auch ublich _Class Responsibility Collaboration Models_ auf _CRC Cards_ zu verfassen. _CRC Models_ nehmen sich dabei einen Akteur im System vor und beschreiben dessen Verantwortlichkeiten und Interaktionen mit anderen Akteuren.

Den _User-Storys_ werden Prioritatswerte zugeordnet. Dazu muss das Team zusammen mit dem Kunden zunachst Klarheit gewinnen, welche _User-Storys_ das hochste Risiko bezuglich Zeitplan, Kosten oder Funktionalitat besitzen und welche _User-Storys_ dem [Produkt](https://de.m.wikipedia.org/wiki/Produkt_\(Wirtschaft\)) den hochsten, respektive den niedrigsten Mehrwert bieten, wobei ein Diagramm hilfreich sein kann. Das Release sollte mit den _User-Storys_ begonnen werden, die das hochste Risiko und den hochsten Nutzen auf sich vereinen. Danach sind diejenige _User-Storys_ zu verwirklichen, die geringes Risiko aber hohen Nutzen haben. Anschließend geht das Team die _User-Storys_ an, die geringes Risiko und geringen Nutzen auf sich vereinen. Die Fertigstellung von User-Storys mit geringem Nutzen aber hohem Risiko ist zu vermeiden.

![](http://upload.wikimedia.org/wikipedia/commons/8/87/Kano-modell.png)

> _Kundenzufriedenheit_

Neben einer Abschatzung nach Nutzen und Risiko ist fur die Entscheidung, welche _User-Storys_ in dem Release beziehungsweise in den ersten Iterationen umgesetzt werden sollen, noch eine Analyse der Kundenwunsche von Bedeutung. Dabei bedient sich ein XP-Projekt haufig des [Kano-Modells](https://de.m.wikipedia.org/wiki/Kano-Modell). Dabei werden in einer systematischen Kundenbefragung Fragen in _funktionaler Form_ und in _dysfunktionaler Form_ gestellt. Es lasst sich anschließend bestimmen, welche _User-Storys_ unbedingt fertiggestellt werden mussen (_Must-haves_), welche linearer Natur sind (je mehr, desto besser; siehe _[linear](https://de.m.wikipedia.org/wiki/Linearit%C3%A4t)_.) und welche _Exciters_ sind (Der Kunde rechnet nicht mit diesen Merkmalen, nutzt das Produkt auch ohne. Es lasst sich dadurch der Preis erhohen.). Die so gewonnenen Erkenntnisse werden diskutiert.

XP zeichnet sich dadurch aus, dass die Betrachtung der Große einer Einheit, wie Release oder Iteration, unabhangig von ihrer Dauer ist.

Bei der Release-Planung sind User-Storys noch recht grobkornig. Beschaftigt sich ein Team mit einer User-Story genauer, so wird sie, zusammen mit dem Kunden, detaillierter beschrieben. User-Storys werden gewohnlich in _Story-Points_ abgeschatzt, wobei auch eine Abschatzung in _idealen Tagen_ moglich ist. Story-Points sind relative [Aufwandsabschatzungen](https://de.m.wikipedia.org/wiki/Aufwandssch%C3%A4tzung_\(Softwaretechnik\)), also der Entwicklungsaufwand fur eine Story im Vergleich zu anderen. Dabei kann es sein, dass erste Abschatzungen im Verlaufe des Projektes geandert werden. Es wird vom ganzen Team, in mehreren Runden, in einem _Planning-Game_ eine Punkteanzahl fur die User-Storys geschatzt.

Nachdem User-Storys abgeschatzt, priorisiert und einer Iteration zugewiesen wurden, beginnt das Team mit der Umsetzung. User-Storys werden zu Beginn der Iteration in feinkornige, technische Arbeitspakete ([Tasks](https://de.m.wikipedia.org/wiki/Aufgabe_\(Pflicht\))) zerlegt, die gewohnlich einen Umfang von Stunden besitzen. Das Team fuhrt diese Zerlegung durch und schatzt die Dauer eines jeden Tasks. Es wird allerdings noch nicht festgelegt wer den Task zugeteilt bekommt. Zu Beginn der Arbeiten nehmen sich die Entwickler jeweils ein Arbeitspaket vor, gewohnlich nach Fahigkeiten. Dieser Vorgang wird im Team kurz diskutiert. Nach der anfanglichen Zuweisung der Arbeitspakete wird ein weiterer Task begonnen, wenn ein Teammitglied Zeit dafur findet, also seinen vorangegangenen Task abgeschlossen hat. Die Implementierung einer User-Story, also der Funktionalitat, ist erst abgeschlossen, wenn alle einzelnen Tasks dieser User-Story abgearbeitet und die Tests geschrieben und alle erfolgreich durchlaufen sind.

Der Demonstration dieser Vorgehensweise soll eine Tabelle mit Aufwandsabschatzungen in einer fiktiven Arztpraxis dienen. Jeder Arzt hat eine Software, die ihm hilft, seine Patienten und die Termine zu verwalten:

User-Storys mit Aufwandsabschatzung in Story-Points 

Story No. Story Abschatzung  
(Story Points)

1
Als Arzt kann ich alle Patienten sehen, die ich am Tage habe.
3

2
Als Arzt kann ich uber die Gesundheitsgeschichte meiner Patienten Auskunft geben.
5

3
Als Assistentin kann ich einem Patienten einen Termin geben.
2

4
Als Assistentin kann ich einem Patienten eine Verschreibung ausdrucken.
1

Der Begriff _Velocity_ (Geschwindigkeit) beschreibt den Durchsatz des Teams, also die Anzahl der innerhalb einer Iteration erreichten Story-Points. Die Bestimmung der Velocity hilft abzuschatzen, wie lange die Entwicklung der gewunschten Funktionalitat fur ein Release dauert, beziehungsweise wie viele Iterationen notwendig sind. Es ist normal, dass die Geschwindigkeit des Teams nicht immer die gleiche ist.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/2/28/Extreme_Programming_Planungs-_und_Feedback-Schleifen.svg/400px-Extreme_Programming_Planungs-_und_Feedback-Schleifen.svg.png)

> _Zeitlicher Abstand der Schritte._

Es gibt eine tagliche kurze Besprechung _(Stand-up Meeting)_, bei der jeder Entwickler berichtet, was er am Vortag geleistet hat, wo es gegebenenfalls Probleme gab und was er heute leisten mochte. Ferner werden situationsabhangig Arbeitspaare gebildet _(Pair-Programming)_. Im Laufe des Tages findet, wahrend die Entwickler die Funktionalitat und die Tests programmieren, weiterer stetiger Austausch _(Pair-Negotiations)_ statt.

Kann eine User-Story in einer Iteration nicht abgeschlossen werden, zum Beispiel weil die Tests nicht erfolgreich waren oder sich die Abschatzung als zu knapp beziehungsweise der Umfang als zu groß herausgestellt hat, so wird sie gewohnlich in mehrere kleinere aufgeteilt oder komplett in die nachste Iteration verschoben. Auch wahrend einer Iteration kann sich, durch sich andernde Prioritaten des Kunden oder durch neue Erkenntnisse, an der Zusammenstellung der Iteration etwas andern. Ist die Iteration abgeschlossen, schauen sich Vertreter des [Managements](https://de.m.wikipedia.org/wiki/Unternehmensf%C3%BChrung), der Kunde ([Akzeptanztest](https://de.m.wikipedia.org/wiki/Akzeptanztest_\(Softwaretechnik\))) oder andere Personen, die an dem Produkt Interesse haben, das Produkt in der aktuellen Ausbaustufe an und geben Ruckmeldungen. So ist es denkbar, dass der Kunde wahrend des Akzeptanztests neue Prioritaten setzt oder weitere Ideen einbringt.

Technische Unterstutzung muss differenziert betrachtet werden. Einerseits wird bewusst auf technische [Hilfsmittel](https://de.m.wikipedia.org/wiki/Hilfsmittel) verzichtet, so etwa bei der Erstellung von User-Storys. Diese werden gewohnlich manuell erstellt. Andererseits wird die Technik aber auch exzessiv genutzt, so etwa bei der automatisierten Integration und der automatisierten Durchfuhrung von Tests. Daruber hinaus existieren Projektmanagement-Werkzeuge, die sich auf die speziellen Rahmenbedingungen und Anforderungen XPs konzentriert haben.

Die zu entwickelnde Funktionalitat wird kurz und formlos in User-Storys beschrieben. Das meiste Wissen uber die Funktionalitat ihrer Entwicklung befindet sich in den Kopfen der Beteiligten. User-Storys werden gewohnlich nur relativ zueinander geschatzt. Zu Beginn einer Iteration wird deren Inhalt festgelegt. Anschließend kommt erst die Aufteilung der gewahlten User-Storys in Tasks. Neuartig an dem XP-Ansatz ist ebenfalls, dass nicht nur einzelne Personen, sondern das ganze Team den jeweiligen Aufwand schatzt. Auch das Verfahren der Schatzung ist neu. Der Zeitpunkt, wann und wie die Tasks den einzelnen Entwicklern zugeteilt werden, ist ebenfalls ein Abgrenzungskriterium. Erst im Laufe der Iteration nehmen sich die einzelnen Entwickler, je nach ihrer Verfugbarkeit, eines Tasks an. Zu allen User-Storys gibt es zahlreiche Tests. Eine User-Story ist erst komplett abgeschlossen, wenn alle Tests erfolgreich abgelaufen sind. Der tagliche kurze Austausch ist fur die [agile Methodik](https://de.m.wikipedia.org/wiki/Agile_Softwareentwicklung) ublich.

XP besteht aus Werten, Prinzipien und Praktiken. Obwohl es auch andere maßgebliche Quellen gibt (siehe [Weblinks](https://de.m.wikipedia.org/wiki/Extreme_Programming) und [Literatur](https://de.m.wikipedia.org/wiki/Extreme_Programming)), orientiert sich die Zusammenstellung der Werte, Prinzipien und Praktiken an Kent Beck,[[2]](https://de.m.wikipedia.org/wiki/Extreme_Programming) dessen noch recht neue, evolutionare Weiterentwicklungen XPs hier ebenfalls Berucksichtigung finden.[[3]](https://de.m.wikipedia.org/wiki/Extreme_Programming) Es existiert keine eindeutige Definition von XP, wobei allerdings die Diskussionen und Ausfuhrungen der drei Originalverfasser XP am signifikantesten pragen.

XP definiert funf zentrale Werte, abstrakte Elemente, die von zentraler Bedeutung sind: _Kommunikation_, _Einfachheit_, _Ruckmeldung_, _Mut_ und _Respekt_, wobei Respekt erst spater dazukam. Ohne stetige Beachtung dieser zentralen Werte ist es laut XP nicht moglich, erfolgreich Software zu entwickeln.

![](http://upload.wikimedia.org/wikipedia/commons/c/c9/XP-Werte.png)

> _Die zentralen XP-Werte_

Das Team kommuniziert stetig, um Informationen auszutauschen. Der Prozess selbst erfordert hohe Kommunikationsbereitschaft. Es gibt einen stetigen Austausch aller Beteiligten, also auch zwischen dem Entwicklungsteam und dem Kunden. Es kommen auch Personen zu Wort, die in einer gerade diskutierten technischen Aufgabenstellung keine Experten sind. So werden sie miteinbezogen, es gibt zusatzliche Ruckmeldungen und jeder fuhlt sich dem Team und dem Produkt verpflichtet. Stetige Kommunikation mit dem Kunden, Aufnahme seines Feedbacks und Erfullung seiner Wunsche, also auch eines lauffahiges Produktes, das seinen Wunschen voll entspricht, ist wichtiger als [Vertragsverhandlungen](https://de.m.wikipedia.org/wiki/Vertrag). Die Kommunikation zeichnet sich ferner durch einen respektvollen Umgang aus, sowohl im Team untereinander als auch mit dem Kunden. Unterschiedliche Meinungen werden akzeptiert.

Die Entwickler sollen mutig sein und die Kommunikation offen gestalten. Falls eine Anforderung nicht in einer Iteration umgesetzt werden kann, wird in offener und ehrlicher Art und Weise direkt darauf hingewiesen. Es muss eine Atmosphare geschaffen werden, die herkommliche Storungen (wie unnaturlichen Konkurrenzkampf innerhalb des Teams zu Lasten des Produktes) minimiert. Um die Offenheit und den Mut zu fordern und [gruppendynamischen](https://de.m.wikipedia.org/wiki/Gruppendynamik), [psychologischen](https://de.m.wikipedia.org/wiki/Psychologie) Schwierigkeiten entgegenzutreten, kann bewusst ein _Doomsayer_ zur offenen, zeitnahen Aussprache von schlechten Nachrichten oder moglichen Schwierigkeiten oder auch ein [Advocatus Diaboli](https://de.m.wikipedia.org/wiki/Advocatus_Diaboli) eingesetzt werden.

Es soll die einfachste Losung fur eine Problemstellung umgesetzt werden. In jeder Iteration konzentriert sich das komplette Team genau auf die momentan umzusetzenden Anforderungen. Die Losungen sind technisch immer moglichst einfach zu halten.

Es gibt 14 Prinzipien, die eine Brucke bilden zwischen den abstrakten Werten und den konkret anwendbaren Praktiken. Diese Prinzipien sollten immer Berucksichtigung finden. Sie sind _Menschlichkeit_, _Wirtschaftlichkeit_, _Beidseitiger Vorteil_, _Selbstgleichheit_, _Verbesserungen_, _Vielfaltigkeit_, _Reflexion_, _Lauf_, _Gelegenheiten wahrnehmen_, _Redundanzen vermeiden_, _Fehlschlage hinnehmen_, _Qualitat_, _Kleine Schritte_ sowie _Akzeptierte Verantwortung_.

Software wird von Menschen entwickelt. Menschen bilden also den Faktor, dem laut XP besondere Aufmerksamkeit gilt. Durch Schaffung einer menschlichen Atmosphare soll den Grundbedurfnissen der Entwickler (Sicherheit, Vollendung, Identifikation mit der Gruppe, Perspektive und Verstandnis) entsprochen werden.

Die erstellte Software beziehungsweise eine einzelne Funktionalitat muss einerseits wirtschaftlich sein und dennoch einen echten Wert bringen. Andererseits muss sie fur beide Seiten von Vorteil sein und alle Beteiligten (Entwicklungsteam und Kunde) zufriedenstellen.

![](http://upload.wikimedia.org/wikipedia/commons/2/22/XP-Evolution-Prinzipien.png)

> _Die Prinzipien XPs_

Die Wiederverwendung bestehender Losungen, wozu beispielsweise die zahlreichen unterschiedlichen Tests gehoren, die stetig automatisiert durchlaufen werden, ist wichtig. Es ist jedem klar, dass erste Losungen meist nicht optimal sind. Aus Feedback und selbst gewonnenen, neuen Erkenntnissen wird die Losung stetig verbessert. Immer bessere Losungen zu erkennen, gelingt nur durch stetige Reflexion und ein kontinuierliches Hinterfragen der jeweiligen Vorgehensweisen im Team. Die Produktivitat dieses Verfahrens steigt proportional zur Uneinheitlichkeit des aus Personen mit unterschiedlichen Fahigkeiten und [Charakteren](https://de.m.wikipedia.org/wiki/Pers%C3%B6nlichkeit) bestehenden Teams. Verschiedene Meinungen werden nicht nur geduldet, sondern sogar gefordert. Dazu muss ein [Konfliktmanagement](https://de.m.wikipedia.org/wiki/Konfliktmanagement) etabliert werden.

Die Lauffahigkeit der Software muss zu jedem Zeitpunkt garantiert sein. Obwohl kurze Iterationen mit permanentem Feedback dabei helfen, das Projekt in einem Lauf zu halten, mussen Fehlschlage dennoch miteinkalkuliert werden. Es ist durchaus ublich und wird akzeptiert, eine Umsetzung durchzufuhren, die zunachst nicht optimal oder sogar fehlerhaft sein kann. Diese Schwierigkeiten mussen als Gelegenheit und Chance begriffen werden, das Produkt und das Team noch weiter reifen zu lassen. Ein offener, konstruktiver Umgang mit den Herausforderungen der Softwareentwicklung gelingt umso besser, je mehr alle Beteiligten bereit sind, ihre Verantwortung zu akzeptieren. Einem Entwickler eine Aktivitat und Verantwortung nur disziplinarisch aufzutragen, reicht nicht aus, da er die Verantwortung aktiv annehmen und leben muss.

Ein weiterer wichtiger Punkt ist die hohe [Qualitat](https://de.m.wikipedia.org/wiki/Qualit%C3%A4t), die gemaß XP im Gegensatz zu anderen Faktoren wie Ressourcen, Funktionsumfang oder Endtermin nicht zur Diskussion steht. Diese Grundeinstellung unterscheidet sich von vielen anderen Methoden der Softwareerstellung, bei denen Software zu einem bestimmten Zeitpunkt und in einem definierten Funktionsumfang fertiggestellt werden soll, worunter fast immer die Softwarequalitat leidet. Gerade die Qualitat ist allerdings wichtig, um das Produkt einsatzfahig, fehlerfrei und erweiterbar zu halten. Software mit gutem Design und hoher Qualitat ist mittelfristig kostengunstiger, erweiterbarer und weniger fehlerbehaftet als schnell erstellte, sogenannte _Quick-and-dirty-Software_.

Zu guter Qualitat gehort auch die Vermeidung von Redundanzen (unnotig mehrfach oder wiederholt ausgefuhrte oder auch manuell ausgefuhrte automatisierbare Schritte).

Durch schnelle, kleine Schritte bleibt das Team flexibel und kann sich schnell neuen Rahmenbedingungen anpassen und auf Feedback eingehen. Die negativen Folgen eines einzelnen kleinen, nicht erfolgreichen Schrittes konnen wesentlich schneller durch einen neuen Schritt kompensiert werden, als dies bei einem einzelnen großeren Schritt der Fall ware.

Es lassen sich traditionelle und evolutionare Praktiken unterscheiden. Die traditionellen sind in der XP-Welt weit verbreitet und genutzt. Die evolutionaren nehmen verschiedene neue Erkenntnisse aus der jahrelangen Anwendung XPs auf. Sie verfeinern oder modifizieren die ursprunglichen Praktiken geringfugig und machen damit die Nutzung klarer und verstandlicher.

XP wird haufig mit den traditionellen Praktiken verbunden, beziehungsweise darauf reduziert.

    Bei der [Paarprogrammierung](https://de.m.wikipedia.org/wiki/Paarprogrammierung) teilen sich zwei [Programmierer](https://de.m.wikipedia.org/wiki/Programmierer) einen Computer - einer codiert (der _Driver_) und der andere denkt mit und hat das Gesamtbild im Kopf (der _Partner_). Die Rollen werden regelmaßig getauscht. Dieses Vorgehen steigert den Wissenstransfer. Anfanger sollen schneller von der Arbeit eines Spezialisten lernen. Das Wissen wird verteilt. Das Projekt ist nicht mehr so anfallig gegen den Ausfall eines Einzelnen. Durch standigen [Codereview](https://de.m.wikipedia.org/wiki/Codereview) der Entwicklung und Kommunikation wird das [Design](https://de.m.wikipedia.org/wiki/Design) verbessert und Fehler schneller gefunden (siehe auch [Vier-Augen-Prinzip](https://de.m.wikipedia.org/wiki/Vier-Augen-Prinzip)).
    Aktivitaten werden zunachst nicht an einzelne Personen verteilt, sondern an das ganze Team. Es existiert laut Methodik das Bewusstsein und die Verpflichtung nur als Team erfolgreich sein zu konnen. Einzelne Teammitglieder besitzen kein Wissens[monopol](https://de.m.wikipedia.org/wiki/Monopol). Pair-Programming und wechselhafte Einsatzgebiete sollen der Stromung entgegenwirken, dass einzelne Personen Teile als ihren Besitz betrachten.
    [Kontinuierliche Integration](https://de.m.wikipedia.org/wiki/Kontinuierliche_Integration) der einzelnen [Komponenten](https://de.m.wikipedia.org/wiki/Komponente_\(Software\)) zu einem lauffahigen Gesamtsystem in kurzen Zeitabstanden. Je haufiger integriert wird, desto hoher wird laut XP die eintretende Routine. Fehler werden damit fruh aufgedeckt. Die mit der Integration verbundenen Kosten sollen fast auf Null minimiert werden, da die Integration zu einem taglichen Schritt gehort, der weitestgehend vollautomatisiert und selbst stabil und durchgetestet sein muss.
    Bei der [testgetriebenen Entwicklung](https://de.m.wikipedia.org/wiki/Testgetriebene_Entwicklung) werden erst die [Modultests](https://de.m.wikipedia.org/wiki/Modultest) (Unit-Test) geschrieben, bevor die eigentliche Funktionalitat programmiert wird. Der Entwickler befasst sich dadurch fruh mit dem Design des Codes und uberdenkt seine Programmierarbeit genau. Die Tests werden nach jedem Programmierschritt ausgefuhrt und liefern Ruckmeldung uber den Entwicklungsstand. Man spricht in diesem Zusammenhang auch von [Grey-Box-Tests](https://de.m.wikipedia.org/wiki/Grey-Box-Test). Die Tests sind automatisiert. Im Laufe einer Integration werden Integrationstests durchgefuhrt. Es wird zwischen [Regressionstest](https://de.m.wikipedia.org/wiki/Regressionstest) und [Modultest](https://de.m.wikipedia.org/wiki/Modultest) unterschieden. Wahrend Modultests (Unit-Tests) einzelne Module testen, ist ein Regressionstest die kollektive Ausfuhrung aller Tests, um die unveranderte Lauffahigkeit der _alten_, bereits vor der Iteration existenten Funktionalitat zu uberprufen. Auch [Performancetests](https://de.m.wikipedia.org/wiki/Leistung_\(Informatik\)), bei denen die Leistungs- und Geschwindigkeitsmerkmale in Bezug auf die geforderten Werte gemessen werden, sind ublich. Der Entwickler bekommt Ruckmeldung (Feedback), wie viele und welche Tests nicht erfolgreich waren. Ein [Akzeptanztest](https://de.m.wikipedia.org/wiki/Akzeptanztest_\(Softwaretechnik\)) ist die Prasentation des Standes des Produktes, um die Zufriedenheit des Kunden und die Nutzbarkeit zu validieren.
![](http://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Xp-kreis.png/400px-Xp-kreis.png)

> _XP Best Practices_

    Enge Einbeziehung des Kunden, das heißt, der Kunde gibt das [Iterationsziel](https://de.m.wikipedia.org/wiki/Iteration) mit einer Auswahl der zu realisierenden _User-Storys_ vor und hat kurz danach die Moglichkeit, [Akzeptanztests](https://de.m.wikipedia.org/wiki/Akzeptanztest_\(Softwaretechnik\)) durchzufuhren. _[Story-Cards](https://de.m.wikipedia.org/wiki/Story-Card)_ dienen als Medium, um die kurzen Anwendungsfalle in Form von _User-Storys_ aufzunehmen. Der Kunde muss immer anwesend oder zumindest erreichbar sein. Neben User-Storys auf Story-Cards existiert noch der Ansatz, _CRC-Modelle_ auf [CRC-Karten](https://de.m.wikipedia.org/wiki/Class-Responsibility-Collaboration-Karten) zu verfassen.
    Laufendes [Refactoring](https://de.m.wikipedia.org/wiki/Refactoring), standige [Architektur](https://de.m.wikipedia.org/wiki/Softwarearchitektur)-, [Design](https://de.m.wikipedia.org/wiki/Design)\- und [Code](https://de.m.wikipedia.org/wiki/Code)-Verbesserungen, auch um [Anti-Patterns](https://de.m.wikipedia.org/wiki/Anti-Pattern) umgehend erkennen und beseitigen zu konnen. XP bejaht die Existenz von Code, der am Beginn nicht perfekt ist. Stattdessen sind samtliche Teile einem stetigen Review unterworfen. Gefundene, optimierungsfahige Stellen werden gewohnlich sofort verbessert oder als Fehler ([Bugs](https://de.m.wikipedia.org/wiki/Programmfehler)) definiert, die in einer spateren Iteration behoben werden.
    _40-Stunden-Woche_, d. h. Überstunden sind zu vermeiden, weil darunter die Freude an der Arbeit, mittelfristig die Konzentrationsfahigkeit der Programmierer und somit auch die Qualitat des Produktes leidet. Nachweislich sinkt die [Produktivitat](https://de.m.wikipedia.org/wiki/Produktivit%C3%A4t) eines Entwicklers durch Überstunden. Arbeit außerhalb der regularen Arbeitszeit wird im Einzelfall zwar geduldet, aber auf keinen Fall besonders entlohnt oder erwartet. Überstunden zeugen gewohnlich einfach nur von falscher [Planung](https://de.m.wikipedia.org/wiki/Planung).
    Kurze [Iterationen](https://de.m.wikipedia.org/wiki/Iteration), um dem Kunden in regelmaßigen Zeitabstanden einen lauffahigen Zwischenstand des Produkts zu liefern. Eine Iteration ist eine zeitlich und fachlich in sich abgeschlossene Einheit. Kurze Iterationen und damit verbundene Akzeptanztests erlauben schnelle Feedbackschleifen zwischen Entwicklung und Kunde.
    Da in traditionell aufgesetzten Softwareprojekten ein latentes Missverstandnis zwischen Kunde und Entwicklungsteam ein haufiges Problem darstellt - der Entwickler hat Schwierigkeiten mit der Fachsprache des Kunden und umgekehrt -, werden die Anforderungen im fachlichen [Vokabular](https://de.m.wikipedia.org/wiki/Vokabular) des Kunden, idealerweise auch von ihm selbst, in Form von _User-Storys_ beschrieben. Alle sprechen eine Sprache, was durch ein [Glossar](https://de.m.wikipedia.org/wiki/Glossar) noch verstarkt werden kann. Es wird eine _Metapher_ gewahlt, eine inhaltlich ahnliche, fur beide Seiten verstandliche Alltagsgeschichte.
    Das Team halt sich bei der Programmierarbeit an [Standards](https://de.m.wikipedia.org/wiki/Coding_standards), welche erst die gemeinschaftliche Verantwortung des Teams bei dieser Aufgabe ermoglichen. Wechselnder Einsatz der Entwickler in allen Bereichen der Software ist laut XP nur durch gemeinsame Standards sinnvoll moglich.
    Es soll die einfachste Losung angestrebt werden, also diejenige, die genau das Gewunschte erreicht (und nicht mehr). Bewusst allgemein ([generisch](https://de.m.wikipedia.org/wiki/Generisch)) gehaltene Losungen oder vorbereitende Maßnahmen fur potentiell zukunftige Anforderungen werden vermieden. Zum Thema Einfachheit sind die [umgangssprachlichen](https://de.m.wikipedia.org/wiki/Umgangssprache) [Akronyme](https://de.m.wikipedia.org/wiki/Akronym) [KISS](https://de.m.wikipedia.org/wiki/KISS-Prinzip) („Keep it small and simple") und [YAGNI](https://de.m.wikipedia.org/wiki/YAGNI) („You Ain't Gonna Need It") verbreitet.
    Neue Versionen der Software werden in einem _Planning-Game_, auch als _Planning-Poker_ bekannt, spezifiziert und der Aufwand zu deren Umsetzung abgeschatzt. An diesem iterativen Prozess sind sowohl Entwicklungsmannschaft als auch Kunde beteiligt.

Die evolutionaren Praktiken wurden funf Jahre nach den ursprunglichen publiziert und ersetzen diese. Sie lassen sich unterteilen in _Hauptpraktiken_ und erganzende _Begleitpraktiken_. Inhaltlich sind die neuen Praktiken mit den alten, traditionellen Praktiken vergleichbar. Die Bezeichnungen der alten Praktiken wurden teilweise modifiziert oder in einzelne Unterpraktiken aufgeteilt. Zwei Praktiken sind weggefallen: die Praktik _Metapher_ war zu schwer zu vermitteln und hat sich laut Literatur nicht durchgesetzt. _Coding-Standards_ werden als selbstverstandlich vorausgesetzt und nicht mehr explizit erwahnt.

Die Hauptpraktiken sind: _Raumlich zusammen sitzen_, _Informativer Arbeitsplatz_, _Team_, _Pair-Programming_, _Energievolle Arbeit_, _Entspannte Arbeit_, _Storys_, _Wochentlicher Zyklus_, _Quartalsweiser Zyklus_, _10-Minuten-Build_, _[Kontinuierliche Integration](https://de.m.wikipedia.org/wiki/Kontinuierliche_Integration)_, _Test-First-Programmierung_ und _Inkrementelles Design_.

Durch offene, gemeinsame Anordnung der Arbeitsplatze soll die Kommunikation optimiert werden. Diese Form ist aufgrund der besseren Kommunikationsmoglichkeiten einer raumlichen Trennung der Beteiligten vorzuziehen. Der Arbeitsplatz muss ferner „informativ" sein, indem zum Beispiel aktuelle Tasks, der Stand des Projektes und andere wichtige Informationen vom Arbeitsplatz aus immer gut sichtbar sind. Empfehlenswert ist es hier zum Beispiel, die User-Storys zentral an einer Wand anzubringen.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/1/14/XP-Evolution-Hauptpraktiken.png/400px-XP-Evolution-Hauptpraktiken.png)

> _Die Hauptpraktiken des evolutionaren XPs_

Das Team ist laut XP wichtiger als die [Individuen](https://de.m.wikipedia.org/wiki/Individuum). Es fallt, im Bewusstsein, nur als Gemeinschaft erfolgreich zu sein, gemeinsame Entscheidungen. Dies wird dadurch gefordert, dass die einzelnen technischen Aktivitaten in der Planung nicht einzelnen Personen, sondern dem Team zugeordnet werden. Probleme lost das Team ohne den Eingriff eines Managers von außen. Mit dem Thema _selbstregulierendes Team_ befasst sich auch der Essay _[Die Kathedrale und der Basar](https://de.m.wikipedia.org/wiki/Die_Kathedrale_und_der_Basar)_. _Pair-Programming_ mit abwechselnden Partnern soll diese Grundeinstellung weiter fordern.

Die Arbeit soll mit voller Motivation und gleichzeitig in einer entspannten, kollegialen Atmosphare ablaufen, da die Entwickler ohne Überstunden arbeiten und somit maximale Produktivitat erreicht wird. Es werden Sicherheitspuffer einkalkuliert. Nicht einhaltbare Versprechen werden vermieden.

Die zu entwickelnde Funktionalitat wird in Form von Storys beschrieben, beispielsweise User-Storys. In wochentlichem Zyklus wird entschieden, welche Kundenwunsche als Nachstes in Angriff genommen werden. Das Projekt selbst wird in einem quartalsweisen Zyklus geplant. Die vorgegebenen Zyklen sind Richtwerte, deren Großen im taglichen Einsatz variieren konnen.

Die Software zu [erstellen](https://de.m.wikipedia.org/wiki/Erstellungsprozess) und alle Testlaufe durchzufuhren soll in maximal zehn Minuten abgeschlossen sein. Durch diesen _10-Minuten-Build_ werden die Kosten fur Erstellung und das Testen der Software minimiert. Alle von einem Entwickler gemachten Änderungen sollten circa alle zwei Stunden bereitgestellt werden. Diese kontinuierliche Integration soll einem potentiellen Chaos vorbeugen, das entstehen konnte, wenn die Entwickler ihre Änderungen und Erweiterungen am Produkt selten in das zentrale Datenhaltungssystem ([Repository](https://de.m.wikipedia.org/wiki/Repository)) einstellen wurden. Alle Mitarbeiter haben so die Änderungen rasch zur Verfugung. Sowohl die zehn Minuten beim Build als auch die zwei Stunden bei der Integration sind Zielvorgaben, die in konkreten Projekten variieren konnen. Gerade bei großen Projekten mit einer großen Menge an [Quelltext](https://de.m.wikipedia.org/wiki/Quelltext) und Entwicklern wird ein Build deutlich langer dauern, und die Integrationsintervalle werden oft großer sein. Die Praktiken betonen nur die Richtung und geben einen Idealwert vor, der angestrebt werden sollte. Durch Automatisierung lasst sich die Build-Zeit weitestgehend minimieren.

Die Entwicklung ist gekennzeichnet durch den Test-First-Programmieransatz: vor der Realisierung der Funktionalitat muss der Test geschrieben werden. Ein inkrementelles Design, das neue Erkenntnisse und Feedback aufnimmt, verbessert das Design der Software stetig.

Die Begleitpraktiken sind:

  * richtige Kundeneinbeziehung
  * inkrementelles Deployment
  * Team-Konstanz
  * schrumpfende Teams
  * ursachliche Analysen
  * geteilter Code
  * Codierung und Testen
  * tagliches Deployment
  * verhandelbarer, vertraglicher Funktionsumfang
  * Zahlen-pro-Nutzung.

Der Kunde nimmt aktiv an der Entwicklung teil. Er ist Teilnehmer an den regelmaßigen Treffen und wird aktiv miteinbezogen. Die Einbeziehung zeigt sich auch beim zu entwickelnden Funktionsumfang, der verhandelbar bleiben muss. Mehrere kleinere Vertrage anstatt eines großen Vertrags konnen in derartig betriebenen Projekten Risiken minimieren und die Flexibilitat erhohen. Da iterativ stetig neue Versionen bereitgestellt werden, mussen die [Zahlungen](https://de.m.wikipedia.org/wiki/Zahlung) des Kunden unabhangig von der Anzahl der bereitgestellten Versionen sein. Der Kunde zahlt nicht fur jede Version der Software, sondern pro Nutzung.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/8/85/XP-Evolution-Nebenpraktiken.png/400px-XP-Evolution-Nebenpraktiken.png)

> _Die Nebenpraktiken des evolutionaren XPs_

Das Team soll einerseits von seiner Konstanz leben, kann aber auch personell verkleinert werden. Das Entwicklerteam muss uber mehrere Projekte hinweg das gleiche sein. Es erwirbt im Rahmen der Produktentwicklung die Fahigkeiten, als Team zusammenzuarbeiten, welche fur weitere Projekte genutzt werden kann. Sobald das Team leistungsstarker und produktiver wird, sollte seine Arbeitslast, trotz einer Verlagerung von Ressourcen zu anderen Teams, konstant bleiben.

Dem Code als dem im Zentrum stehenden Medium kommt eine zentrale Rolle zu. Er wird in einer zentralen, datenbankahnlichen Struktur ([Repository](https://de.m.wikipedia.org/wiki/Repository)) gehalten. Es existiert nur eine offizielle Version (Codebasis) des Systems. Dieser Code wird, bildlich gesprochen, zwischen den Entwicklern geteilt. Jeder Entwickler im Team muss in der Lage sein, auch „fremden" Code jederzeit andern zu konnen (Collective-Code-Ownership). Neben dem Code existieren immer die Tests, die zusammen mit dem Code die einzigen zu erstellenden, durch die Entwicklungsarbeit bereitgestellten Medien („Artefakte") sind. Alle anderen Medien, zum Beispiel die Dokumentation, werden allein aus Code und Tests generiert.

Um Schwierigkeiten fruh zu identifizieren, wird inkrementelles [Deployment](https://de.m.wikipedia.org/wiki/Deployment) (die Überfuhrung der Anwendung auf das Zielsystem) durchgefuhrt. Wenn [Altsysteme](https://de.m.wikipedia.org/wiki/Legacy-System) durch neue Software ersetzt werden sollen, muss ein Teil nach dem anderen ersetzt werden. Dieses Vorgehen soll die Umstellung planbarer machen. Das Deployment ist taglich inkrementell durchzufuhren. Jeden Tag soll eine neue Version der Software produktiv gestellt werden. Dies macht das Deployment zur Routine, minimiert dessen Kosten und Fehler und ermoglicht stetige Integrations- und Akzeptanztests. Falls einmal ein technisches Fehlverhalten eintritt, muss eine ursachliche Analyse durchgefuhrt werden.

Eine der theoretischen Grundlagen des Extreme Programming ist der Flexibilitatsgrad des zu entwickelnden Softwaresystems. XP geht von einem mindestens proportionalen Zusammenhang zwischen dem Gegenteil der Flexibilitat, der sogenannten _Steifheit_, und den Pflegekosten zur Fehlerbehebung oder Erweiterung des Systems aus. Je flexibler ein Softwaresystem, desto geringer sind die Pflegekosten, je steifer, desto hoher.

Einige Steifheitskriterien:

  * Die Anzahl uberflussiger bzw. ungenutzter Merkmale
  * Eine schlechte, fehlende, schwer verstandliche oder zu umfangreiche Dokumentation
  * Ein schwer verstandlicher oder unflexibler Entwurf
  * Fehlende Regressionstests
  * Ein schwerfalliges Gesamtsystem

Die Flexibilitatskriterien sind das Gegenteil der Steifheitskriterien, zum Beispiel ein leicht verstandlicher und flexibler Entwurf.

Einige der als Bestandteil des Extreme Programming definierten Mechanismen dienen laut XP der Erhohung der Flexibilitat:

  * Die testgetriebene Entwicklung sorgt fur ein ausreichendes Vorhandensein von Regressionstests und eine verbesserte [Testbarkeit](https://de.m.wikipedia.org/wiki/Testbarkeit) der Software
  * Das standige Refactoring fuhrt zur Fehlerbeseitigung, einem leicht verstandlichen und flexiblen Entwurf sowie guter Dokumentation
  * Die kontinuierliche Integration erfordert zwangslaufig ein leichtgewichtiges Gesamtsystem
  * Um die zu entwickelnde Funktionalitat zu bestimmen, und zwischen Kunde und Entwicklungsteam auszuarbeiten, werden User-Storys eingesetzt

XP ist ein Vertreter der agilen Softwareentwicklung. Im Vergleich zu traditionellen [Vorgehensmodellen](https://de.m.wikipedia.org/wiki/Vorgehensmodell_\(Software\)) wahlt es alternative Ansatze, um Herausforderungen wahrend der Softwareentwicklung zu adressieren.

In aus heutiger Sicht _traditionellen_ Vorgehensmodellen ist der Softwareentwicklungsprozess in aufeinanderfolgenden [Phasen](https://de.m.wikipedia.org/wiki/Projektphase) organisiert. Nach Jahren der Anwendung von traditionellen Vorgehensmodellen, wie dem ab 1970 genutzten [Wasserfallmodell](https://de.m.wikipedia.org/wiki/Wasserfallmodell), haben es, aus Sicht der XP-Vertreter, Projektverantwortliche nur unzureichend verstanden, die Probleme und Risiken der Softwareentwicklung in den Griff zu bekommen. Viele Projekte kamen nie zu einem Abschluss oder uberstiegen zeitlich und/oder kostenmaßig die Planung. Viele, gerade uber lange Zeitraume laufende Projekte deckten mit Abschluss zwar die zu Beginn spezifizierten Anforderungen ab, berucksichtigten allerdings unzureichend, dass Anforderungen sich andern konnen oder erst im Laufe eines Projektes dem Kunden wirklich klar ist, wie das Endergebnis aussehen soll. Über Erfolg und Schwierigkeiten von Softwareprojekten liefert der _[Chaos-Report](https://de.m.wikipedia.org/wiki/Chaos-Studie)_ von _The Standish Group_ regelmaßig fundierte Untersuchungen, wie beispielsweise 1994.[[4]](https://de.m.wikipedia.org/wiki/Extreme_Programming)

In Abgrenzung zu traditionellen Vorgehensmodellen durchlauft der Entwicklungsprozess in XP immer wieder iterativ in kurzen Zyklen samtliche Disziplinen der klassischen Softwareentwicklung (zum Beispiel [Anforderungsanalyse](https://de.m.wikipedia.org/wiki/Anforderungsanalyse), [Design](https://de.m.wikipedia.org/wiki/Design), [Implementierung](https://de.m.wikipedia.org/wiki/Implementierung), [Test](https://de.m.wikipedia.org/wiki/Test)). Durch diese inkrementelle Vorgehensweise werden nur die im aktuellen Iterationsschritt benotigten [Merkmale](https://de.m.wikipedia.org/wiki/Merkmal) verwirklicht (implementiert). XP ist dadurch _leichtgewichtiger_: Es wird keine komplette technische [Spezifikation](https://de.m.wikipedia.org/wiki/Spezifikation) der zu entwickelnden Losung vorausgesetzt (so gibt es beispielsweise kein [Pflichtenheft](https://de.m.wikipedia.org/wiki/Pflichtenheft)).

_Extreme Programming_, und damit einher [Standards](https://de.m.wikipedia.org/wiki/Industriestandard) wie JUnit, wurden von [Kent Beck](https://de.m.wikipedia.org/wiki/Kent_Beck), [Ward Cunningham](https://de.m.wikipedia.org/wiki/Ward_Cunningham) und [Ron Jeffries](https://de.m.wikipedia.org/wiki/Ron_Jeffries) wahrend ihrer Arbeit im [Projekt](https://de.m.wikipedia.org/wiki/Projekt) Comprehensive Compensation System bei [Chrysler](https://de.m.wikipedia.org/wiki/Chrysler_Corporation) zur Erstellung von Software entwickelt. Die Arbeiten am sogenannten C3-Projekt begannen 1995 und wurden 2000 nach der Übernahme durch Daimler eingestellt. Die dabei entwickelte Software wurde im Bereich der [Lohnabrechnung](https://de.m.wikipedia.org/wiki/Lohnabrechnung) eingesetzt und basierte hauptsachlich auf [Smalltalk](https://de.m.wikipedia.org/wiki/Smalltalk_\(Programmiersprache\)). Das C3-Projekt wurde ursprunglich nach dem Wasserfallmodell umgesetzt. Nachdem nach knapp einem Jahr kein wesentlicher Fortschritt zu verzeichnen war, wurde der Entwicklungsansatz geandert. Das Projekt zeichnete sich aus durch haufig wechselnde Anforderungen und einer hohen Mitarbeiterfluktuation. [[5]](https://de.m.wikipedia.org/wiki/Extreme_Programming)[[6]](https://de.m.wikipedia.org/wiki/Extreme_Programming)[[7]](https://de.m.wikipedia.org/wiki/Extreme_Programming)

XP ist ein agiles Vorgehensmodell. Die folgende Tabelle stellt den von XP identifizierten Kerndisziplinen den historischen, weitverbreiteten Ansatz mitsamt seinen Risiken der Softwareentwicklung gegenuber. Unternehmen, die XP nicht einsetzen, konnen Vorgehensmodelle verwenden, die sich - bewusst oder unbewusst - mit diesen Disziplinen positiv auseinandersetzen.

Verbreitete XP-Kerndisziplinen und Risiken bei herkommlicher Herangehensweise 

Praktik Richtiges Vorgehen nach XP Traditionelles oder falsches Vorgehen/Risiko nach XP

Kommunikation
Stetiger Austausch wird gefordert und erwartet.
Jeder muss zunachst mal seine Aufgaben losen.

Mut
Offene Atmosphare.
Angst vor versaumten Terminen und Missverstandnissen mit Kunden.

Kollektives Eigentum
Programmcode, Dokumente etc. gehoren dem Team.
Jeder fuhlt sich nur fur seine Artefakte verantwortlich.

Pair-Programming
Zu zweit am Rechner.
Jeder will und muss zunachst auf seine ihm zugewiesenen Aufgaben schauen.

Integration
Stetige Integrationen erlauben Feedback und erhohen Qualitat.
Selten Integrationen, da vermeintlich unnutz und Zeitverschwendung.

Testgetriebene Entwicklung
Testen hat einen hohen Stellenwert.
Testen kostet nur Zeit. Wenige manuelle Tests.

Kundeneinbeziehung
Der Kunde wird zur aktiven Mitarbeit aufgerufen.
Der Kunde ist selten wirklicher Partner, sondern nur die „andere Seite des Vertrages".

Refactoring
Suboptimales Design und Fehler werden akzeptiert.
Fehler sind verpont. Erstellte Artefakte laufen angeblich immer direkt perfekt.

Keine Überstunden
Einhaltung der regularen Arbeitszeit.
Stetige, regelmaßige Überschreitung der regularen Arbeitszeit.

Iterationen
Ein Release wird in viele handliche Iterationen unterteilt.
Iterationen sind nicht notig, es wird an einem Release gearbeitet.

Stand-up-Meeting
Taglicher, strukturierter Austausch.
Große, lange, seltenere Projektmeetings. Die Personenanzahl und der Inhalt sind haufig zu aufgeblaht.

Dokumentation
Wo es sinnvoll ist.
Wichtiges Artefakt. Alles muss standardisiert dokumentiert sein. Dokumentation wird aber nicht genutzt.

Metapher
Ein gemeinsames Vokabular.
Kunde und Entwicklung sprechen in zwei Sprachen, haufig aneinander vorbei.

Team
Das Team ist wichtig. Es existieren keine Rollen. Feedback wird von jedem erwartet.
Spezialistentum. Abschottung. Wissensmonopole.

Standards
Standards, wo es sinnvoll erscheint.
Überregulierung. Starrer Prozess.

Qualitat
Inharenter Bestandteil.
Der Faktor, der als erster vernachlassigt wird, wenn Zeit oder Geld knapp werden.

Aufgrund der wachsenden Nutzung wird XP weiter optimiert: je mehr Projekte gemaß XP entwickelt werden, desto mehr Erfahrungen fließen in die Weiterentwicklung von XP ein. Da es auch eine Summe von [Best Practices](https://de.m.wikipedia.org/wiki/Best_Practice) ist, lasst sich somit sagen: „Es wird in der Praxis fur die Praxis angepasst".

Der kleinste gemeinsame Nenner aller agilen Vorgehensmodellen ist das „Agile Manifest":[[8]](https://de.m.wikipedia.org/wiki/Extreme_Programming)

  * _Individuen und Interaktionen haben Vorrang vor Prozessen und Werkzeugen_
  * _Lauffahige Software hat Vorrang vor ausgedehnter Dokumentation_
  * _Zusammenarbeit mit dem Kunden hat Vorrang vor Vertragsverhandlungen_
  * _Das Eingehen auf Änderungen hat Vorrang vor strikter Planverfolgung_

Neben XP hat auch [Scrum](https://de.m.wikipedia.org/wiki/Scrum) einen gewissen Bekanntheitsgrad erlangt. Neben vielen Ähnlichkeiten mit XP gibt Scrum in bestimmten Bereichen Vorgaben bezuglich Iterationslange, [Protokollierung](https://de.m.wikipedia.org/wiki/Protokoll) und Verfahren. Scrum nutzt ein eigenes Vokabular.

Eine weitere gerne in diesem Zusammenhang angefuhrte Disziplin ist das [Feature Driven Development](https://de.m.wikipedia.org/wiki/Feature_Driven_Development), eine Methodik, die den Schwerpunkt ebenfalls auf die bereitzustellende Funktionalitat legt.

Ähnlichkeiten zwischen XP und [Kaizen](https://de.m.wikipedia.org/wiki/Kaizen), einem in Japan vor allem in der Autoindustrie entwickelten Konzept ([Kontinuierlicher Verbesserungsprozess](https://de.m.wikipedia.org/wiki/Kontinuierlicher_Verbesserungsprozess)) zur Sicherung der Qualitat im Fertigungsprozess und einer Optimierung der Fertigungs- und Managementkosten mittels „schlankerer" Ansatze ([Schlanke Produktion](https://de.m.wikipedia.org/wiki/Schlanke_Produktion)), sind nicht zu ubersehen.

Ein weiteres agiles Vorgehensmodell ist [Crystal](https://de.m.wikipedia.org/wiki/Crystal_Family), eine Familie von Methoden, deren Mitglieder meist mit Farben gekennzeichnet werden.

Auch traditionelle Vorgehensmodelle, wie das [V-Modell](https://de.m.wikipedia.org/wiki/V-Modell_\(Entwicklungsstandard\)), wurden zwischenzeitlich um neue Erkenntnisse in der Softwareentwicklung angereichert. Als Ergebnis bedient sich der Nachfolger, das _V-Modell XT_, agiler Ansatze. So gibt das V-Modell XT keine strikte Sequenz an zu durchlaufenden Phasen mehr vor.

Heute, uber zehn Jahre nach den ersten XP-Schritten, erfreuen sich XP und andere agile Methoden wachsender Beliebtheit. Untersuchungen von „Forrester Research" ergaben, dass in Nordamerika und Europa 2005 circa 14 Prozent aller Projekte mit agilen Methoden durchgefuhrt wurden[[9]](https://de.m.wikipedia.org/wiki/Extreme_Programming) (von denen XP die verbreitetste ist) und viele andere einen Einsatz prufen.

Zu den Nutzern XPs zahlen sowohl Unternehmen, die kommerziell Software herstellen und vertreiben, als auch Unternehmen, deren eigentliches Geschaft nicht die Erstellung von Software ist: _Dresdner Kleinwort Wasserstein_, _[Encyclopaedia Britannica](https://de.m.wikipedia.org/wiki/Encyclopaedia_Britannica)_, _Fidelity_, _Progressive_, _Capital One_, _Royal & Sunalliance_, _Channel One_, _Daedalos International_, _Gemplus_, _it-agile_, _Qwest_ und _O&O Services_.[[10]](https://de.m.wikipedia.org/wiki/Extreme_Programming)[[11]](https://de.m.wikipedia.org/wiki/Extreme_Programming)

Viele Unternehmen berichten offentlich von ihren Erfahrungen mit XP. Sie schildern, wie sie XP im Detail eingesetzt haben, welche Schwierigkeiten dabei auftraten und wie der Erfolg einzuschatzen war. _[Symantec](https://de.m.wikipedia.org/wiki/Symantec)_ hat seine Änderung des Vorgehensmodells hin zu XP publiziert[[12]](https://de.m.wikipedia.org/wiki/Extreme_Programming). _Sabre Airline Solutions_ hat mit XP sowohl die Fehler in ihrer Software als auch die Entwicklungszeit reduziert:[[13]](https://de.m.wikipedia.org/wiki/Extreme_Programming)

Gemaß einiger Protagonisten des XP-Ansatzes wirken die einzelnen Methoden so eng zusammen, dass diese ohne Ausnahme eingesetzt werden sollen. Bereits der Verzicht auf einzelne Methoden soll die Wirksamkeit des Gesamtansatzes massiv einschranken. Da jedoch der Einsatz der Methoden oftmals auf zahlreichen Voraussetzungen basiert (siehe z. B. die Abschnitte [Der ideale Kunde](https://de.m.wikipedia.org/wiki/Extreme_Programming) und [Der ideale Programmierer](https://de.m.wikipedia.org/wiki/Extreme_Programming)), ist es wahrscheinlich, dass in konkreten Projekten einzelne Methoden eben gerade nicht angewandt werden konnen. Das liefert dann auch auf einfache Weise eine Erklarung fur das Scheitern von XP-Projekten: Meist durfte sich eine vernachlassigte Methode finden lassen, so dass das Scheitern nicht auf XP als Gesamtansatz, sondern auf die Vernachlassigung dieser Methode zuruckgefuhrt werden kann. Mittlerweile ist es umstritten, ob tatsachlich alle Methoden angewendet werden mussen, um durch XP die Wahrscheinlichkeit auf einen erfolgreichen Projektverlauf zu erhohen.

Ein Hauptgrund fur die Spezifikation von Anforderungen besteht bei klassischen Vorgehensmodellen in der Schaffung einer verlasslichen Basis fur die Entwicklungsarbeit, so dass spater notwendige Änderungen an der Realisierung moglichst gering bleiben. Die implizite Annahme dieser Haltung ist, dass Änderungen umso teurer werden, je spater sie durchgefuhrt werden mussen. Obwohl sich diese Annahme in vielen Projekten bestatigt hat, geht XP gewissermaßen davon aus, dass Änderungen grundsatzlich „billig" sind, wenn man sie kontinuierlich durchfuhrt. Auch verneint XP implizit die Annahme, dass spatere Änderungen teurer werden, und begrundet dies damit, dass die Änderungen dann nicht - wie in anderen Ansatzen - in mehreren Artefakten zugleich (Spezifikation, Dokumentation, Quellcode) umgesetzt werden mussen.

Die diesbezuglichen Annahmen von XP treffen sicher dann zu, wenn die Anforderungen _unvermeidlich_ Änderungen unterworfen sein werden. In diesem Fall kann eine Spezifikation der Anforderungen unter Umstanden großeren Aufwand nach sich ziehen als das Auslassen der Spezifikation - schon allein deswegen, weil die Spezifikation immer mitgeandert werden muss. Es ist jedoch unklar, warum es schadlich sein sollte, Anforderungen zumindest dann zu spezifizieren, wenn sie mit einiger Sicherheit bis zum Projektende Bestand haben werden. Durch den Verzicht auf eine Spezifikation lauft man Gefahr, Anforderungen zu ubersehen oder hinsichtlich ihrer Bedeutung falsch einzuschatzen. Auch ist denkbar, dass der Kunde im Projektverlauf seine Anforderungen bewusst andert, jedoch gegenuber dem Entwicklungsteam bekundet, seine Auffassung sei bislang nur falsch verstanden worden. Hinsichtlich der Einschatzung, dass spatere Änderungen nicht teurer sind als fruhe, ist einzuwenden, dass spate Änderungen dann sehr teuer sein konnen, wenn sie das Design der Anwendung in grundlegender Weise betreffen. So ist die Änderung der Architektur einer Anwendung nicht ohne erheblichen Aufwand durchzufuhren, ja sie kann ggf. teurer sein als eine Neuimplementierung. Es ist nicht ersichtlich und erscheint daher als eine Glaubensfrage, ob XP durch den Einsatz seiner Methoden derartige Situationen verhindern kann.

Der Einsatz von XP verlangt einen experimentierfreudigen Kunden, der nicht nur auf eine Reihe von ublichen Vorgehensweisen verzichten, sondern zudem selbst erhebliche Ressourcen aufwenden muss. Zu den Aspekten, auf die ein Kunde ungern verzichtet, gehoren:

    Software kann in komplexen Systemlandschaften eingefuhrt werden, so dass unterschiedlichste Beteiligte (z. B. Schnittstellenverantwortliche, Mitarbeiter von externen Providern usw.) Kenntnis von technischen Details erlangen mussen. In solchen Umgebungen verbieten meist schon die Firmenrichtlinien den Verzicht auf eine ausfuhrliche Dokumentation. Aber selbst wenn dies nicht der Fall ist, bleibt zu klaren, wie die Kenntnisse uber technische Details an die Betroffenen vermittelt werden sollen, wenn keine Dokumentation existiert, und mehr noch, wenn davon ausgegangen werden muss, dass kunftige Änderungen die relevanten technischen Einzelheiten betreffen.
    Insbesondere beim Abschluss von Werkvertragen stellt sich fur den Kunden die Frage, worin prazise eigentlich das Gewerk besteht, das durch den vereinbarten Preis erworben wird. Des Weiteren konnen firmenweite Richtlinien die Erstellung einer Spezifikation verlangen.
    Da der projektleitende Vertreter des Kunden oftmals selbst den Projektfortschritt berichten muss, stellt die Fertigstellung bestimmter Funktionen zu festgelegten Terminen, somit also die Aufstellung eines Projektplans, oftmals einen unverzichtbaren Bestandteil der gemeinsamen Vorgehensweise dar.

Über diese Punkte hinaus stellt das „Kunde vor Ort"-Prinzip eine Anforderung dar, die in der Realitat nur außerst selten umsetzbar ist. Um seine Aufgabe erfullen zu konnen, muss der Mitarbeiter offensichtlich uber einen erheblichen Wissensumfang verfugen. Ist dies aber der Fall, so ist der Mitarbeiter sehr wahrscheinlich auch in seinem eigenen Unternehmen nicht fur mehrere Monate entbehrlich. Nicht selten werden IT-Projekte zudem gerade deshalb an externe Dienstleister vergeben, um den eigenen Ressourcenaufwand zu beschranken. Das Kunde-vor-Ort-Prinzip stellt somit eine der am schwierigsten erfullbaren Anforderungen des Extreme Programming dar.

XP stellt zahlreiche Anforderungen an die beteiligten Programmierer.

  * Die Programmierer mussen uber sehr gute Fahigkeiten verfugen, da der auf haufigen Änderungen basierende Ansatz unter Verwendung von Refactorings nicht ohne umfangreiche Programmiererfahrung und ohne den Einsatz von dafur geeigneten Werkzeugen realisiert werden kann.
  * Programmierer weisen oftmals ein recht ausgepragtes Ego auf, das sich in großer Überzeugung von „richtigen Losungen" und einem gewissen Besitzdenken hinsichtlich des geschriebenen Codes außert. Nicht alle Programmierer konnen damit umgehen, dass - gemaß XP - jeder den Code aller anderen modifizieren darf.
  * XP weist eine Reihe von Merkmalen auf, die hohe Disziplin erfordern (wie z. B. der Test-first-Ansatz, das permanente Durchfuhren von Refactorings, Programmieren in Paaren usw.), und einige andere, die eine gewisse Disziplinlosigkeit fordern (z. B. das Auslassen von Spezifikation und Dokumentation). Es besteht die Gefahr, dass die letzteren Ansatze gegenuber den Ersteren betont werden. Die Einhaltung der Ansatze mit hoher Disziplin erfordert fahige Beteiligte und eine funktionierende Selbstregulierung des Teams. Da aber unter Umstanden kein Projektverantwortlicher benannt wurde, fragt sich, wer letztlich fur die konsequente Einhaltung aller Aspekte sorgt.

Die Anforderungen zeigen, dass XP nicht auf beliebige Teams angewandt werden kann.

Mehrere XP-Methoden erfordern einen hohen Grad an gegenseitiger Informiertheit und somit ein hohes Maß an Kommunikation zwischen den Beteiligten. So bedingt das kontinuierliche Refactoring unter Umstanden Änderungen gemeinsam genutzter Komponenten, uber die moglichst das gesamte Team unterrichtet sein muss. Das Fehlen eines Projektmanagers erfordert gemeinsame Absprachen zur Arbeitsteilung. Da zudem eine prazise Spezifikation und Dokumentation fehlt, mussen alle Informationen zur Umsetzung in den Kopfen der Beteiligten verfugbar sein. Mit der Große des Teams steigt jedoch der Kommunikationsaufwand quadratisch an, so dass XP-Projekten eine naturliche Grenze hinsichtlich der Teamgroße gesetzt ist. Die maximale Große wird gemeinhin bei zehn Teammitgliedern angesetzt.

Ein weiterer haufiger Kritikpunkt ist, dass XP fur [Festpreisprojekte](https://de.m.wikipedia.org/wiki/Festpreis) nicht geeignet sei. Da der Kunde einen festen Preis zahlt, muss der Auftragnehmer in irgendeiner Form sicherstellen, dass er fur diesen Preis auch nur eine festgelegte Leistung erbringen muss. Die Leistungserbringung so lange bis der Kunde zufrieden ist kann in immer neuen Kundenanforderungen munden, so dass die Aufwande fur die Realisierung nicht abzusehen sind. Die Festlegung der Festleistung als Inhalt des Werkvertrages entsprache jedoch einer Spezifikation und ist somit in XP verpont. Es gibt einige Ansatze, XP dennoch mit Festpreisprojekten kompatibel zu machen:

  * Versicherungspramien auf die Schatzung
  * User-Storys (bzw. die Story-Cards) werden zum Vertragsgegenstand
  * besondere Preismodelle wie _Aufwandspreis mit Obergrenze_, _Phasenfestpreis_ oder _Anforderungseinheitspreis_.

Die Wirksamkeit dieser Ansatze ist jedoch unklar. User-Storys konnen zu unprazise sein, um das Gewerk gegen unerwartete technische Anforderungen abzusichern. Die angesprochenen Preismodelle entsprechen nur noch bedingt einem Festpreis und damit Werkvertrag, so dass fraglich ist, ob ein Kunde mit der Vorgabe eines Festpreises darauf eingehen wurde. Selbiges gilt auch fur Versicherungspramien.

Die iterative Vorgehensweise von XP und der fehlende Projektplan legen bereits nahe, dass die Fertigstellung eines fachlich gewunschten Funktionsumfangs zu einem gesetzten Termin nicht ohne weiteres garantiert werden kann. Zwar wird zu dem gesetzten Termin _etwas_ fertig sein (da der Fokus jeder Iteration auf einer ausfuhrbaren, ggf. sogar produktionsfahigen Software liegt), welche fachlichen Aspekte dies jedoch tatsachlich sind, kann nicht vorherbestimmt werden - umso weniger als Überstunden verpont sind und das Ausmaß notiger Refactorings auf Grund beweglicher Anforderungen nur schwer abgeschatzt werden kann.

XP gilt in verteilten Umgebungen als schwerer einsetzbar als herkommliche Modelle. Der direkte Kontakt der Entwickler untereinander und zum Kunden ist problematisch, falls verschiedene Kunden existieren oder die Beteiligten raumlich getrennt arbeiten, so zum Beispiel bei teilweise ausgelagerten Entwicklungen ([Outsourcing](https://de.m.wikipedia.org/wiki/Outsourcing)).

Die stets erneute Erstellung von Testfallen und die automatisierte, permanente Ausfuhrung der Tests kann in komplexen oder [nebenlaufigen](https://de.m.wikipedia.org/wiki/Nebenl%C3%A4ufigkeit) Anwendungen und [verteilten Systemen](https://de.m.wikipedia.org/wiki/Verteiltes_System) aufwandig sein. Wenn sich keine Rollen ausbilden, muss jeder alles wissen, statt einzelne Schwerpunkte im Team zu setzen (klassisches Beispiel: GUI-Entwicklung und Datenbank-Entwicklung), was die Gesamtleistung des Teams vermindern kann.

Da das Team im Vordergrund steht, durfen einzelne Entwickler nicht nach dem Umfang ihrer entwickelten Funktionalitat honoriert werden. Insbesondere der Honorarvertrag ist kein geeignetes Vergutungsmodell bei Anwendung des Vorgehensmodells der XP.

  * Scott W. Ambler, Ronald E. Jeffries: _Agile Modeling: Effective Practices for eXtreme Programming and the Unified Process_, Wiley, John & Sons, [ISBN 0-471-20282-7](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/0471202827)
  * Kent Beck, Cynthia Andres: _Extreme Programming Explained, Embrace Change_, Addison-Wesley, 2. Auflage, 2004, [ISBN 0-321-27865-8](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/0321278658)
  * Henning Wolf, Stefan Roock, Martin Lippert: _eXtreme Programming: eine Einfuhrung mit Empfehlungen und Erfahrungen aus der Praxis_ dpunkt, 2., uberarb. u. erw. Aufl., 2005, [ISBN 3-89864-339-5](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3898643395).
  * Michael Huttermann: _Agile Java-Entwicklung in der Praxis_ (mit intensiver Diskussion agiler Entwicklung insbesondere Extreme Programming): O'Reilly, 2007, [ISBN 3-89721-482-2](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3897214822).
