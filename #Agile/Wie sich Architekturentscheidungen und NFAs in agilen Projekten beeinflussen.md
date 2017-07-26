# Wie sich Architekturentscheidungen und NFAs in agilen Projekten beeinflussen

_Captured: 2016-07-21 at 20:03 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/entwicklung/methoden/wie-sich-architekturentscheidungen-und-nfas-in-agilen-projekten-beeinflussen.html)_


![Gute Architektur braucht enge und kontinuierliche Abstimmung. © Romolo Tavani / Fotolia.com](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720_Fotolia_81895775_Romolo_Tavani_f47d0d0f3f.jpg)© Romolo Tavani / Fotolia.com

**Die Architektur von Softwaresystemen kann schon lange nicht mehr ausschließlich am Reißbrett entstehen. Sie muss während der Fertigstellung durch enge und kontinuierliche Abstimmung mit Entwicklern sowie den Partnerdisziplinen Anforderungsanalyse und Test verfeinert werden. Insbesondere die nichtfunktionalen Anforderungen haben signifikante Auswirkungen auf die Architektur.  
**

Architektur entsteht aus einer Vielzahl bewusster Entscheidungen, sowie aus der Reaktion auf unabänderliche Gegebenheiten. Solche Randbedingungen sind meist finanzielle, technische oder organisatorische Vorgaben, die außerhalb des Einflussbereiches von Anforderungsanalyse, Entwicklung und Test liegen, aber signifikante Auswirkungen auf das Produkt und dessen Erstellung haben können. Beispielsweise kann die Entscheidung, Java als Programmiersprache und Laufzeitumgebung zu nutzen, sowohl eine bewusste Entscheidung des Architekten als auch eine Vorgabe des Auftraggebers sein. Gleiches gilt für die Anzahl der Schichten, die verwendete User Interface-Technologie, sowie Implementierungsrichtlinien. Während der Herstellung eines Systems muss die Architektur viele Fragen beantworten, zum Beispiel:

  * Wie werden Fremdsysteme angebunden?
  * Wie helfe ich, einen reibungslosen Betrieb sicherzustellen? 
  * Wie kann ich das System tolerant gegenüber Änderungen der Ablaufumgebung gestalten?
  * Wie mache ich die Anwendung stabil und performant?
  * Wie sorge ich für eine gute Bedienbarkeit und Toleranz bei Fehleingaben? 

Einige davon kann der Architekt selbständig klären. Andere bedürfen der Unterstützung. Wichtige Inputgeber sind die Disziplinen Anforderungsanalyse und Test. Die Anforderungsanalyse erhebt und dokumentiert funktionale und nichtfunktionale Anforderungen sowie Randbedingungen. Der Test überprüft Architekturentscheidungen, indem er ihre Auswirkungen auf das laufende System bewertet und dokumentiert. In der agilen Softwareentwicklung bilden Anforderungsanalyse, Entwicklung und Test ein Team. Das gemeinsame Produkt entsteht in kurzen Zyklen. Hierbei wird ein priorisiertes Backlog abgearbeitet. Es enthält Userstories, die von den Beteiligten umgesetzt und getestet werden. Ziel ist, in regelmäßigen Abständen eine potenziell releasefähige Version fertig zu stellen. Aufgabe der Architektur ist, sich nahtlos in diesen natürlichen Arbeitsfluss zu integrieren. Eine Voraussetzung hierfür ist ein kontinuierlicher Strom von funktionalen und nichtfunktionalen Anforderungen sowie Randbedingungen. 

## Randbedingungen 

Randbedingungen entziehen sich dem Einflussbereich von Anforderungsanalyse, Entwicklung und Test. Sie sind vom Auftraggeber gesetzt und nicht verhandelbar. Randbedingungen definieren den organisatorischen, finanziellen und technischen Rahmen, in dem sich ein Projekt bewegt, zum Beispiel:

  * Die Umsetzung darf maximal 10 Millionen Euro kosten.
  * Die IT-Produktionsumgebung des Unternehmens ist auf zwei Standorte verteilt.
  * Die Produktion findet gleichberechtigt an beiden statt.
  * Die Fachabteilung ist gegenüber der Entwicklung weisungsberechtigt.
  * Die Mitarbeiter-PCs verwenden Windows 10.

Randbedingungen ändern sich während des Projekts üblicherweise nicht. Was geschieht, falls doch, soll anhand des folgenden Szenarios erläutert werden. Stellen Sie sich vor, eine JEE-Anwendung muss in Produktion auf dem Host laufen. Aus organisatorischen Gründen hat der Auftraggeber aber festgelegt, in entwicklungsnahen Umgebungen Linux zu verwenden. Im Verlauf des Projekts stellt sich heraus, dass sich Application Server und Datenbank auf dem Host und unter Linux unterschiedlich verhalten. Die Folge: Konfigurationsdateien und DDL-Skripte müssen ständig angepasst werden. Problematisch an der Situation ist zusätzlich, dass die Entwicklung Artefakte liefert, die sie selbst nicht testen kann. Der Grund: sie hat aus Compliance-Gründen keinen Zugriff auf höhere Stages. Um das Dilemma aufzulösen, wird nach einiger Zeit entschieden, auch in entwicklungsnahen Umgebungen auf den Host zu wechseln. Hierzu müssen die Entwicklungsumgebungen umgebaut und zahlreiche Berechtigungen sowie Firewall-Freischaltungen beantragt werden. Dies bedeutet ein kostenintensives "Stop the world" für die Entwicklung, bis die Umstellung abgeschlossen ist.

> Randbedingungen machen es dem Architekten leicht – sie gewähren Planungssicherheit.

Auch eine nicht genannte oder nicht beachtete Randbedingung kann ein Projekt selbst kurz vor Fertigstellung ernsthaft in Gefahr bringen. Stellen Sie sich vor, der Auftraggeber hat entschieden, ausschließlich Open Source-Bibliotheken zu nutzen. Diese Information erreicht die Entwicklung aber nicht. Der Architekt entscheidet sich deshalb für eine Komponente, die in der Entwicklung kostenfrei zu nutzen ist, für die in Produktion aber Lizenzgebühren anfallen. Wenn der Auftraggeber nicht bereit ist, diese Kosten zu tragen, muss die Bibliothek durch eine andere ersetzt werden, was zumindest für erneuten Testaufwand sorgt. Fallen Änderungen am Code an, gerät der Projektzeitplan möglicherweise aus den Fugen. 

Anders als die im Folgenden diskutierten nichtfunktionalen Anforderungen machen es Randbedingungen dem Architekten eigentlich leicht, nachhaltige Entscheidungen zu treffen. Denn sie stehen, sofern sie ordnungsgemäß erhoben und dokumentiert wurden, zu Projektbeginn fest und ändern sich während des Projektverlaufs nicht. Sie gewähren also Planungssicherheit. Die Folgen einer Änderung können für das Projekt aber fatal sein.

## Nichtfunktionale Anforderungen

Nichtfunktionale Anforderungen werden im Projektalltag leider oft als fünftes Rad am Wagen wahrgenommen: zu Projektbeginn erfasst, während des Projektverlaufs vergessen und am Projektende hektisch hervorgekramt. Dabei sind sie für mehrere Zielgruppen von fundamentalen Interesse:

  * für den Architekten, weil sie die Säulen seiner Architektur bestimmen,
  * für die Entwicklung, weil sie die technische Umsetzung nachhaltig beeinflussen und
  * für den Test, weil sie aufgrund ihrer nicht ganz einfachen Prüfbarkeit einer sorgfältigen Planung bedürfen.

Nichtfunktionale Anforderungen sind wie die zwei Seiten einer Medallie. Sie wirken nach innen, indem sie die Struktur, den Aufbau und die Funktionsweise eines Systems steuern. Sie wirken aber auch nach außen, indem sie den Einfluss eines Systems auf die IT-Landschaft des Unternehmens und die Wahrnehmung durch Betreiber und Anwender beeinflussen. 

Zum Beispiel prüft die NFA Wartbarkeit, wie leicht sich Anpassungen an einem System vornehmen lassen. Dies ist wichtig, um zu einem späteren Zeitpunkt mit vertretbarem Aufwand Funktionen hinzufügen oder Änderungen vornehmen zu können. Um ein System wartbar zu machen, muss es der Architekt sinnvoll strukturieren, indem er Schichten, Komponenten und Services definiert und dokumentiert. Auch das Datenmodell sowie der Fluss der Daten muss vollständig und nachvollziehbar beschrieben sein. Gleiches gilt für Entwicklungsvorgaben und Architekturentscheidungen. Was geschieht, wenn beispielsweise die Entwicklung Kodierrichtlinien ändert, aber nicht dokumentiert oder kommuniziert? Die NFA Wartbarkeit wird üblicherweise durch Dokumentations- und Codereviews überprüft. Der Test geht bei einem Codereview also von falschen Annahmen aus. Welche weitere – falsche – Architekturentscheidung könnte Auswirkungen auf die Testbarkeit der NFA Wartbarkeit haben? Ein Klassiker: die Nutzung einer zentralen Komponente, für die es keinen Quelltext oder keine prüfbare Dokumentation gibt. Falls Sie das in der heutigen Zeit für abwegig halten, suchen Sie in Google Trends doch einmal nach dem Software-Typ Documentation Generator. 

Die NFA Performanz definiert akzeptable Antwort- bzw. Reaktionszeiten. Zum Beispiel: 90 Prozent aller Serviceaufrufe müssen nach spätestens 500 Millisekunden beantwortet werden. Sie wird üblicherweise mit Last- und Performancetests geprüft. Um ein System performant zu gestalten, nutzt der Architekt etablierte Konzepte wie Caches, Verteilung über mehrere Instanzen und Nebenläufigkeit oder setzt auf Mechanismen, die von der IT-Landschaft zur Verfügung gestellt werden. Die Herausforderung dabei: nicht alles ist in jeder stage vorhanden. Messergebnisse sind also umgebungs- bzw. stageabhängig. Architektur, Entwicklung und Test müssen deshalb gemeinsam Metriken erarbeiten, die das Laufzeitverhalten eines Systems umgebungsübergreifend bewertbar macht. Aus diesem Grund ist es unabdingbar, jede Architekturänderung an Test zu kommunizieren, damit die Auswirkungen auf Messungen bewertet werden können. 

Ähnliches gilt für die nichtfunktionale Anforderung Verfügbarkeit. Sie lässt sich nur in bestimmten Umgebungen sinnvoll testen – manche Teilaspekte möglicherweise überhaupt nicht, da sie nur in Produktion vorhanden sind. Hierzu gehört der Test auf standortübergreifendes Failover. Ist die Infrastruktur auf mehrere Standorte verteilt, soll die Anwendung oder der Service bei Ausfall eines Standortes ggf. mit längeren Antwortzeiten weiter funktionieren. Allerdings ist ein solcher Test üblicherweise nicht Aufgabe eines Entwicklungsprojekts. Dann aber muss es freilich ein Betriebskonzept für die Standortverteilung geben, auf das beim Test der NFA-Bezug genommen werden kann. 

Ein abschließendes Beispiel: Stellen Sie sich eine Anwendung mit komplexer Rechenlogik vor. In der agilen Softwareentwicklung werden die Berechnungsalgorithmen Stück für Stück hinzugefügt und verfeinert. Die Performance dieser Anwendung wird deshalb vom Implementierungsstand abhängig sein. Die Prüfung der NFA-Performanz nur zu Beginn nützt also nichts. Eine Prüfung zum Schluss kann hingegen viel zu spät erfolgen. Stellt sich nämlich heraus, dass das Programm nicht schnell genug rechnet, ist ein Umbau vielleicht nicht mehr möglich. Es ist also im Sinne des Projekts, die Performance regelmäßig zu betrachten und zu bewerten. Dies erfolgt idealerweise in enger Abstimmung zwischen Architektur, Entwicklung und Test.

## Finale

Wie also hängen Architekturentscheidungen und die Testbarkeit von nichtfunktionalen Anforderungen voneinander ab? NFAs werden im Rahmen der Anforderungsanalyse erhoben und dokumentiert, und danach durch Architekturentscheidungen umgesetzt. NFAs können sich während des Projekts ändern. Sie müssen deshalb regelmäßig durch den Test überprüft werden. Solange es für eine NFA keine Umsetzung z. B. durch Architekturentscheidungen gibt, kann die NFA nicht sinnvoll getestet werden. Ändert sich eine NFA, müssen korrespondierende Architekturentscheidungen überprüft werden. Wird eine Architekturentscheidung revidiert, müssen die korrespondierenden NFAs neu getestet werden.

> Ohne Umsetzung und Überprüfung ist die schönste Anforderung wertlos.

Der kontinuierliche Austausch zwischen Anforderungsanalyse, Entwicklung und Test ist sehr wichtig. Die Entwicklung lebt von der Anforderungsanalyse. Denn sie kann nur dann kontinuierliche Entscheidungen treffen, wenn sie regelmäßig mit neuen Erkenntnissen (funktionale und nichtfunktionale Anforderungen) versorgt wird. Die Entwicklung lebt aber auch vom Test. Denn Testergebnisse können dazu führen, dass getroffene Entscheidungen korrigiert, oder neue – bis dahin unbekannte – Fragen geklärt werden müssen. Der Test wiederum lebt von Anforderungsanalyse und Entwicklung: er überprüft Anforderungen sowie deren Umsetzung. Auch die Anforderungsanalyse braucht beide Partner. Ohne Umsetzung und Überprüfung ist die schönste Anforderung wertlos.  
  
NFAs und Randbedingungen sind der Motor für Architekturentscheidungen. Sie haben nicht nur Auswirkungen auf die Architektur, sondern auch auf die Planung und Durchführung von Tests. Die Qualität von Tests ist von der Qualität der Anforderungen abhängig. Um NFAs testen zu können, müssen Architekturentscheidungen sauber dokumentiert sein. Die drei Disziplinen Anforderungsanalyse, Entwicklung und Test stehen in einem fruchtbaren Spannungsverhältnis. Die Anforderungsanalyse steht nicht am Anfang. Der Test steht nicht am Schluss. Beide sind gleichberechtigte Partner der Entwicklung.


