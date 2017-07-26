# Tests erst in Produktion? – Was wir von Tests bei Microservices lernen können

_Captured: 2016-08-18 at 08:17 from [www.informatik-aktuell.de](https://www.informatik-aktuell.de/entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html)_

![Microservices sind unabhängige Prozesse, die einen kleinen Teil der Funktionalität einer Anwendung abbilden und untereinander lose gekoppelt sind. © Konstantin Yuganov / Fotolia.com](fileadmin/_processed_/csm_720_Fotolia_101916285_Konstantin_Yuganov_27e9e5da8f.jpg)© Konstantin Yuganov / Fotolia.com

**Microservices sind der meistdiskutierte Architekturstil der letzten Jahre. Für die erhöhte Reaktionsgeschwindigkeit auf Veränderungen zahlen Sie jedoch den Preis einer komplexer zu entwickelnden und zu betreibenden Applikation. Schnell stellt sich die Frage, wie diese Komplexität beim Testen der Anwendung beherrscht wird. Nach ehrlichen Antworten gefragt, räumen viele Projekte ein Defizit bei diesem Thema ein – unabhängig vom gewählten Architekturstil. Wieso werden diese Stimmen rund um Microservices nicht lauter? Was machen die Teams anders, die diese komplexen verteilten Anwendungen entwickeln und betreiben?**

**Dieser Artikel beleuchtet Konzepte und Methoden, die dabei helfen, die zusätzliche Komplexität in den Griff zu bekommen. Sie funktionieren in der Microservice-Welt und lassen sich auch bei anderen Architekturstilen anwenden. So können Sie die hier vorgestellten Mittel direkt nutzen um die Tests in Ihrem Projekt zu verbessern.**

## Was sind Microservices eigentlich genau?

Microservices beschreiben einen Architekturstil, der in den letzten 5 Jahren massiv an Bedeutung gewonnen hat. Viele große Web-Anwendungen basieren heute auf Microservices. Für den Microservices-Begriff gibt es verschiedene Definitionen. Die Basis aller bildet die unabhängige Entwicklung, Release und Deployment eines Microservices durch das für diesen Service zuständige Team. Die einzelnen Microservices sind unabhängige Prozesse, die einen kleinen Teil der Funktionalität einer Anwendung abbilden und untereinander lose gekoppelt sind – meist über REST-Schnittstellen. Durch diese Unabhängigkeit kann man die einzelnen Microservices besser skalieren und auch unterschiedliche Technologien in der Entwicklung einsetzen. Die lose Kopplung und die Größenbeschränkung ermöglichen es, einzelne Services schneller zu ersetzen oder auch neue Funktionalitäten schnell zu entwickeln. Für den Anwender ist diese Aufteilung des Systems in einzelne Microservices nicht spürbar. Auf oberster Ebene findet eine Integration statt ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[1] [2] [3]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495). 

Mit den Systemen haben sich in den letzten Jahren die Konzepte zur Entwicklung und Betrieb von Microservices weiterentwickelt und so sind Microservices heute auch für viele kleinere Systeme eine attraktive Alternative zu klassischen Architekturstilen wie Schichtenarchitekturen. 

## Klassische Architekturstile

In diesem Artikel schauen wir in den folgenden Abschnitten nacheinander auf die Konzepte und Methoden, die sich beim Testen von Microservices bewährt haben und wie diese in anderen Architekturstilen Anwendung finden können. Als Beispiele für andere Architekturstile betrachten wir die weit verbreitete Schichtenarchitektur und die Service Oriented Architecture (SOA).

![Abb.1: Übersicht Architekturstile. © Harm Gnoyke](fileadmin/_processed_/csm_Tests_Abb1_Gnoyke_5a879ee149.png)Abb.1: Übersicht Architekturstile. © Harm Gnoyke

Mit einer Schichtenarchitektur bezeichnen wir eine monolithisch deployte Anwendung, die sich in mehrere horizontale Schichten unterteilen kann (z. B. GUI-, Business-Logik- und Persistenzschicht). 

Eine SOA ist die Verbindung mehrer Services über einen Enterprise Service Bus (ESB). Der ESB hat dabei die Aufgabe der Orchestrierung der Services. Dazu gehören das Routing und die Transformation zwischen verschiedenen Datenformaten. Eine SOA wird meist auf Ebene einer Systemlandschaft angewendet. Die einzelnen Services sind also deutlich größer als die Microservices und können wiederum mit anderen Architekturstilen umgesetzt sein, z. B. Schichtenarchitektur. Abb.1 zeigt den schematischen Aufbau der drei beleuchteten Architekturstile. 

Die folgenden Abschnitte beschreiben jeweils ein Thema rund ums Testen und wie es speziell bei Microservices angewendet wird. Am Ende eines jeden Abschnitts folgt die Übertragung auf die anderen Architekturstile.

## Bereit zum Testen

![Abb.2: Testpyramide. © Harm Gnoyke](fileadmin/_processed_/csm_Tests_Abb2_Gnoyke_cbe4fab289.png)Abb.2: Testpyramide. © Harm Gnoyke

Die Testpyramide (s. Abb.2) war schon allgegenwärtig bevor Microservices als Begriff aufkamen ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[4]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495). Zur Erklärung liest sich die Pyramide am besten wie sie gebaut wird: von unten nach oben. An der Basis stehen die automatisierten Unit-Tests, welche die kleinsten Einheiten einer Software (z. B. Klassen) testen. Auf der mittleren Schicht fortgesetzt wird in drei Kategorien unterschieden: Komponenten-Tests, Integrations-Tests und API-Tests. Technisch gesehen laufen diese Tests meist im selben Schritt. 

An der Spitze der Pyramide stehen die automatisierten GUI-Tests, die eine laufende Anwendung benötigen. Dies setzt natürlich voraus, dass Tests auf den unteren Ebenen existieren und erfolgreich durchlaufen wurden. Wenn nämlich eine instabile Applikation (= nicht gut getestet auf den unteren Ebenen) auf dieser Stufe getestet wird, kommt es zu vielen Fehlern oder die Tests können nur mit sehr viel Aufwand am Laufen gehalten werden. Passiert das, kann ein Projekt schnell das Vertrauen in diese Teststufe verlieren und aufhören, den nötigen Aufwand zu investieren. Langfristig führt dies leider zu erhöhten manuellen Testaufwänden, die in der Testpyramide in der Wolke an der Spitze dargestellt sind. Diese explorativen, d. h. nicht einem festen Muster folgenden Tests bilden den Abschluss der Pyramide. Diese sind im Gegensatz zu den anderen Tests nicht automatisiert. Die automatisierten Tests auf den Ebenen darunter verfeinern Projektteams durch die gewonnenen Erkenntnisse dieser Teststufe. 

## Gefahren beim Pyramidenbau

Die ideale Testpyramide sieht eine breite Basis von Unit-Tests und immer weniger Tests auf dem Weg nach oben vor. Wie bei der Erklärung der Testpyramide schon angedeutet, kann es zu Problemen kommen, wenn die Tests auf den verschiedenen Stufen nicht richtig ausbalanciert sind. Am besten stellen zwei Anti-Pattern bei der Anwendung der Testpyramide diese Probleme dar:

  * **Ice Cream Cone** ("Eistüte" ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[5]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495)): Die Pyramide ist auf den Kopf gestellt. Es gibt wenige Tests an der Basis und mehr Tests je weiter man sich nach oben bewegt, also genau das Gegenteil der idealen Testverteilung. Das Projekt scheitert daran, die Tests an der Basis nachzuziehen und steckt vermehrt Aufwände in die oberen Stufen. Langfristig verlängern sich so die Feedback-Schleifen zur Entwicklung und das Projekt wird ausgebremst.
  * **Cupcake** ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[6]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495): Hier finden sich viele Tests auf allen Ebenen, die aber nicht aufeinander abgestimmt sind. Die Folge sind mehrfach geleistete Aufwände und viele Fehler in späten Phasen. Ursache dafür ist, dass unterschiedliche Teams sich um die unterschiedlichen Stufen kümmern und nicht miteinander kollaborieren.

Bei Microservices ist die gesamte Software in kleinere Einheiten zerlegt, die für die Teams besser zu kontrollieren sind. Dies wirkt sich auch auf die Testpyramide aus: Jedes Team kümmert sich um die gesamte Pyramide für seinen Teilbereich und hat einen guten Überblick, an welchen Stellen gearbeitet werden muss, um die Tests auszubalancieren und die Pyramide stabil zu halten. 

Für andere Architekturstile ist es genauso hilfreich, die Testpyramide nicht nur für das Gesamtprojekt zu betrachten, sondern diese auch auf kleinerer Ebene anzuwenden. Die fachliche Aufteilung einer Applikation bietet die beste Orientierung dafür.

![IT-Tage 2016 - Microservices](fileadmin/templates/wr/pics/Banner/ITT16_Themen_Banner/ITT16_Themen_Banner_Micorservices.png)

## Consumer Driven Contract Tests als Gegenmittel

Die Aufteilung der Testpyramide bietet den Vorteil des besseren Überblicks im Kleinen. Es bleibt die Herausforderung, auf oberster Ebene das Gesamtprojekt zu testen. Bei Microservices ist dies schwieriger als in klassischen Ansätzen, weil die einzelnen Services unabhängig voneinander deployt werden können und daher gar nicht klar ist, in welcher Version ein benutzter Service gerade vorliegt. 

Dieser Unsicherheit wird einerseits dadurch begegnet, dass die Schnittstellen eines Services sich nur kompatibel ändern dürfen oder aber beim Aufruf einer Schnittstelle die angeforderte Version mit angegeben wird ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[7]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495). Die zusätzliche Sicherheit beim Testen erhält ein Service andererseits durch Einführung des sogenannten _Consumer Driven Contract Testing_. Dabei stellt ein Team den von ihm aufgerufenen Services diejenigen Tests zur Verfügung, die die Nutzung der aufgerufenen Services aus seiner Sicht zeigen. Diese zusätzliche Teststufe unterstützt die Stabilität eines Services, da er das erwartete Nutzungsverhalten schon in seinen eigenen Tests simuliert. 

Diese Art von Tests ist auch in anderen Architekturansätzen lohnenswert. In vielen Systemen gibt es außerdem Teile, die als API zur Verfügung gestellt werden und für die eine Unsicherheit existiert, da die Art und Weise der Verwendung durch die Aufrufer nicht einschätzbar ist. Eine frühzeitige Einbindung der Nutzer der API hilft, diese Teststufe nicht nur bei Microservices zu nutzen. 

Um einzelne Microservices zu testen schlägt Martin Fowler ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[8]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495) vor, sich an den verschiedenen Verantwortlichkeiten eines Microservices zu orientieren:

  * Fachliche Logik des Services
  * Ressourcen, die zwischen der Innen- und Außensicht eines Services mappen
  * Logik zum Nachrichtenaustausch mit anderen Services
  * Persistenzlogik für den eigenen Service

Während der letzte Punkt als der zentrale Zweck eines Services bei den Tests den Hauptanteil ausmacht, dürfen die anderen Themen nicht vernachlässigt werden. Für ein stark verteiltes System wie Microservices sind diese Schnittstellen nach außen eben genauso wichtig wie die Erbringung der Fachlichkeit. 

Auch bei anderen Architekturstilen ist diese Betrachtung der unterschiedlichen Zwecke innerhalb eines Bausteins hilfreich. Die interne Funktionalität ist meistens gut getestet, an den Schnittstellen nach außen hängt jedoch ein größeres Risiko und umso schmerzhafter ist es, wenn diese Tests nicht angegangen werden. Die Betrachtung der verschiedenen Verantwortlichkeiten ist eine sinnvolle Verfeinerung der Testpyramide bei der Betrachtung der Tests eines Systems.

> Monitoring ist das neue Testen! – Und sonst wird nichts getan?

Der Blick auf die internen Tests hat schon hilfreiche Anregungen gebracht. Es bleibt die Herausforderung, dass die Microservices auch zusammen getestet werden müssen. In diesem Zusammenhang ist hin und wieder die Aussage "_Monitoring ist das neue Testen_" zu hören. Nachdem wir die Teststrategien schon genauer angeschaut haben, wissen wir, dass diese Aussage nicht komplett der Realität entspricht. Es steckt aber doch etwas Wahres dahinter, denn Microservice-Systeme werden in Produktion verstärkt mit Monitoring überwacht. 

Eine Begründung dafür ist, dass es zu aufwändig und teuer wäre, Testumgebungen mit allen verschiedenen denkbaren Versionskombinationen der Microservices auszustatten. Eine Integration auf dieser Ebene würde auch die Unabhängigkeit der Entwicklungsteams stören. Komplette Sicherheit bietet aus den genannten Gründen also erst der Blick auf das Monitoring in Produktion. Dadurch erfahren die Entwicklungsteams, welcher Microservice Fehler verursacht oder unter zu großer Last steht. Die oben erwähnten zusätzlichen Testansätze helfen nur dies abzufedern, vermeiden es aber nicht. 

Das Monitoring eines stark verteilten Microservice-Systems benötigt andere Tools als das Monitoring eines monolithisch deployten Systems. Bei Letzterem kann direkt das Deployment-Artefakt mit einem Monitoring-Tool untersucht werden. Für Java-Anwendungen gibt es für diesen Zweck viele verschiedene Tools unterschiedlicher Hersteller. Eine Übertragung eines dieser Tools auf ein Microservice-System ist nicht einfach möglich, weil die Tools einen einzelnen Microservice in den Mittelpunkt stellen würden. Details aus den anderen beteiligten Microservices werden auf den ersten Blick verborgen. Eine Gesamtübersicht über das System mit der Möglichkeit, in bestimmte Teilbereiche reinzuzoomen ist jedoch sehr wichtig. Um Microservices gut zu überwachen, müssen die Daten der verschiedenen Microservices in einem Tool integriert vorliegen. Die zwei am meisten verbreiteten Ansätze dafür sind:

  * Logging der einzelnen Services in einem einheitlichen Format (Aggregation z. B. mit Hilfe des ELK-Stacks ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[9]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495))
  * Tracing von Daten aus den Microservices durch Nutzung einer Bibliothek (z. B. Zipkin ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[10]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495) oder Prometheus ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[11]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495))

Die beiden Ansätze eint, dass sie ein Tool mitliefern, um die Daten aus den verschiedenen Microservices gesammelt darzustellen und so eine Analyse ermöglichen. Für eine gute Übersicht im Monitoring muss auch für die Microservices eine Festlegung zumindest auf das gleiche Logging- oder Tracing-Format erfolgen. Die Nutzung der gleichen Bibliothek kann Aufwände einsparen, bleibt am Ende jedoch die Entscheidung der einzelnen Microservice-Teams. 

Mit einem so aufgesetzten Monitoring erreichen wir also einen guten Überblick über das Gesamtsystem sowie die einzelnen Services. In einem System, das ähnliche Verteilungsaspekte aufweist wie z. B. ein Monolith mit vielen Fremdsystemen oder eine SOA, kann sich das Team diese Überwachungstechniken ebenso zu Nutze machen um nicht nur Ausschnitte des Systems zu betrachten oder das Bild erst außerhalb der Monitoring-Tools zusammenzufügen.

## Fehlerbehandlung von Anfang an

Eine weitere Eigenschaft von Microservice-Systemen ist das "Design for Failure" ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[12]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495). Grundlage dafür sind die "Fallacies of Distributed Computing" (etwa: "Trugschlüsse bei verteilten Systemen" ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[13]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495). In Kürze besagen diese, dass Fehler in verteilten Systemen früher oder später garantiert auftreten – auf jeder möglichen Ebene. Um sich dagegen zu schützen, ist eine Möglichkeit, die MTTF (Mean Time To Failure – Durchschnittliche Zeit bis zur Fehlfunktion) seiner Applikation zu optimieren. Die Folge sind zusätzliche Sicherheitsnetze, die in komplexen Systemen sehr aufwändig herzustellen sind. Und am Ende passiert Folgendes: Kaum ist der Ausfall eines Fremdsystems kompensiert, fällt ein anderes Fremdsystem aus, für das (noch) kein Sicherheitsnetz vorhanden ist. 

Microservice-Systeme optimieren deshalb die MTTR (Mean Time To Recovery – Durchschnittliche Zeit bis zur Erholung), um die Verfügbarkeit und Zuverlässigkeit des Systems zu erhöhen. Ein Teil der Lösung sind redundante Knoten mit vorgeschaltetem Load Balancer, wie sie auch bei anderen Systemen zum Einsatz kommen. Damit wird auf den Ausfall kompletter Knoten reagiert. Für eine große Menge Microservices ist eine Bereitstellung dieser Redundanzen jedoch sehr teuer. In diesen Systemen helfen spezielle Resilience-Muster ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[14]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495), die einen Microservice robust auf unerwartete Antworten von anderen Microservices reagieren lassen. Unerwartete Antworten können dabei sowohl zu lange Latenzen sein, als auch fachlich nicht interpretierbare Antworten, z. B. auf Grund geänderter Schnittstelle. 

Für andere Architekturstile ist die Anwendung dieser Resilience-Muster wertvoll, um die Verfügbarkeit des Systems zu erhöhen. Speziell bei Anwendungen, die einen starken Verteilungsaspekt aufweisen, bieten diese Muster gute Ansatzpunkte. Beispiele sind wiederum ein Monolith mit vielen Fremdsystemen oder eine SOA. Auch bei einer Schichtenarchitektur helfen die Muster, um sich an den Schnittstellen stärker zu entkoppeln. 

## Armee der Affen: Monkey Testing 2.0

Zur Erhöhung der MTTR trägt ebenso das Konzept der "_Simian Army_" von Netflix bei ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[15]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495). Aufgeteilt in verschiedene Kategorien werden Bots auf die Umgebung losgelassen, die Microservices manipulieren und so die Robustheit der gesamten Umgebung zu prüfen. Der "Chaos Monkey" schaltet zum Beispiel einzelne Instanzen eines Service gezielt ab, der "Latency Monkey" erhöht die Latenzen für Requests zu einem Microservice. Über das Monitoring wird überwacht, dass die anderen Microservices und damit die gesamte Applikation geeignet auf diese Manipulationen reagieren. Es gibt auch noch größere Ausprägungen dieser Affen, über Gorilla bis zu Kong (es ist tatsächlich eine Affenarmee!). Je größer der Affe, umso größere Teile der Umgebung werden manipuliert. Im Falle von Netflix in der Amazon Cloud bedeutet das simulierte Ausfälle von einzelnen Datacenters bis hin zu ganzen Regionen. 

Diese Teststufe findet also eindeutig in der Produktionsumgebung statt. Das Konzept bei Netflix sieht eine Vorbereitung in den Test-Stufen vor und ein "Monkey" wird erst dann in Produktion für einen Service aktiv, wenn das verantwortliche Team seinen Service damit auch ausprobiert hat und sich sicher ist, dass dadurch kein Schaden in Produktion entstehen wird. So werden die einzelnen "Monkeys" getestet und damit auch die Reaktion der Services in einer Teststufe und nicht erst in Produktion. 

Auch dieser Ansatz kommt in Frage, wenn keine Microservices im Einsatz sind. Ob die Tests für Ausfälle einer Komponente oder eines Subsystems automatisiert werden wie bei der "Simian Army" oder sie erst einmal manuell ausgeführt werden: Solche Tests bieten einen großen Erkenntnisgewinn über das eigene System. Die eingangs dieses Abschnitts erwähnten "Fallacies of Distributed Computing" gelten doch zweifellos für alle Anwendungen. 

## Enduser als Tester eingesetzt

Zum Abschluss richten wir den Blick noch auf das Konzept des Canary Releasing, das in Produktion Anwendung findet und als Voraussetzung weitestgehend automatisierte Deployment-Prozesse hat ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[16]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495). Hierbei bekommen unterschiedliche Benutzergruppen per Load Balancing verschiedene Versionen der gleichen Anwendung zu Gesicht. So wird ermöglicht, dass ein neues oder verändertes Feature zuerst an eine kleine Benutzergruppe ausgerollt wird um das Verhalten in Produktion zu testen. Dieses Konzept ist auch hilfreich, wenn schon vorherige Teststufen durchlaufen wurden, aber z. B. auf Grund der Komplexität der Anwendung noch keine vollständige Sicherheit über die neue Funktionalität vorhanden ist. 

In vielen Systemen wird dieses Verfahren zusätzlich genutzt, wenn sich in den Teststufen nicht feststellen lässt, welche Funktionalität in Produktion für die Anwender attraktiver ist. Das ist dann ein Spezialfall, das sogenannte A/B-Testing ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[17]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495). Das Entwicklungsteam rollt hierbei parallel zwei verschiedene Funktionalitäten (die Versionen A und B der Software) aus und beobachtet, ob diese sich in der Interaktion mit den Nutzern der Anwendung unterschiedlich verhalten. Version A kann dabei auch die bestehende Version der Anwendung sein. Besonders beliebt ist dieser Ansatz, wenn man keinen direkten Zugriff auf die Benutzer seiner Anwendung zum vorherigen Testen hat. Die Aktionen von kleinen, zufällig ausgewählten Benutzergruppen werden dabei durch Monitoring beobachtet, um zu kontrollieren, ob die Version B im Vergleich zur Version A z. B höhere Klickraten, eine längere Verweildauer auf der Webseite oder gar höhere Verkaufszahlen generiert. Für unterschiedliche Anwendungen kommen dabei diverse Kennzahlen zum Einsatz. Bei statistisch signifikanter Überlegenheit ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[18]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495) der neuen Version wird diese auf alle Anwender ausgerollt. Ist dies nicht der Fall, bleibt die bestehende Version in Produktion bestehen. Das Canary Releasing ermöglicht dabei wiederum ein reibungsloses Zurückrollen auf die bestehende Version. 

Das Canary Releasing ist gewissermaßen die Weiterentwicklung von Blue-/Green-Deployments ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[19]](entwicklung/methoden/tests-erst-in-produktion-was-wir-von-tests-bei-microservices-lernen-koennen.html#c16495), die ihren Ursprung in den Zeiten vor Microservices haben. Voraussetzung für solche Releases sind automatisierte Deployment-Prozesse um Continuous Delivery zu ermöglichen. Für Microservices sind diese Automatisierungen essenziell, um die Anwendung überhaupt betreiben zu können, während Anwendungen mit anderen Architekturstilen dieses Mittel einsetzen können, um besser belastbare Aussagen zur Anwendung zu erhalten. Das geschieht einerseits durch kürzere Entwicklungszyklen oder eben die aufgezeigten Möglichkeiten des Canary Releasing oder A/B-Testing. 

## Zusammenfassung und Fazit

Tabelle 1 fasst die im Artikel erklärten Konzepte und Methoden bei Microservices und die Übertragung auf andere Architekturstile tabellarisch zusammen.

### Tabelle 1: Konzepte und Methoden bei Microservices und die Übertragung auf andere Architekturstile

Konzept / Methode bei Microservices Was hilft es bei anderen Architekturstilen?

Aufteilung der Testpyramide pro Microservice

Betrachtung von Testpyramiden für jeden funktionalen Baustein hilft bei der Balance der Tests und führt zu erhöhter Sicherheit für das Gesamtsystem.

Consumer Driven Contract Tests

Die Unabhängigkeit von Bausteinen oder ganzen Services erhöht sich mit dieser Art von Tests.

Aufteilung der Tests nach technischen Verantwortlichkeiten

Die technisch risikohaften Bereiche werden frühzeitig mit Tests abgesichert.

Ganzheitliches Monitoring von verteilten Systemteilen

Bietet einen Gesamtüberblick über den Zustand des Systems und führt schneller zur Analyse der Fehlerursache.

Design for Failure / Resilience Muster

Die Auseinandersetzung mit möglichen Fehlerfällen verbessert die Behandlung von Ausnahmefällen im System. Langfristig erhöht sich die Sensibilisierung für Fehlerfälle zu einem frühen Zeitpunkt.

Simian Army

Die Simulation von Fehlern erhöht die Robustheit der Anwendung.

Monitoring in Produktion

Die Betrachtung von sinnvollen KPIs hilft die Anwendung gezielt weiter zu entwickeln.

Canary Releasing und A/B-Testing

Mit Continuous Delivery als Voraussetzung können Varianten von Funktionen von Benutzern direkt in Produktion getestet werden.

Wir haben gesehen, dass Vieles aus der Microservice-Welt gut auf andere Architekturstile übertragbar ist. Auffällig ist, dass einige der beleuchteten Konzepte schon entwickelt wurden, bevor es Microservices gab. In dem neuen Kontext haben diese Themen jedoch eine Entwicklung erfahren. 

Selbst wenn die eigene Anwendung nicht in eine Microservice-Anwendung überführt werden soll oder eine Microservice-Anwendung auf Grund der Anforderungen und Rahmenbedingungen nicht sinnvoll ist, lohnt sich der Blick auf die genannten Konzepte, die sich in den nächsten Jahren sicher noch weiter entwickeln werden.

Quellen

  1. S. Newman, 2015: Building Microservices, O’Reilly
  2. Informatik Aktuell – Eberhard Wolff: ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[Microservice-Architekturen nicht nur für agile Projekte](https://www.informatik-aktuell.de/entwicklung/methoden/microservice-architekturen-nicht-nur-fuer-agile-projekte.html)
  3. Architektur-Spicker #3: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Microservices  ](http://www.embarc.de/spicker/#spicker3)
  4. A. Scott: Blogbeiträge zur ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Testing Pyramid](https://watirmelon.com/tag/testing-pyramid/)
  5. A. Scott, 2012: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Introducing the software testing ice-cream cone (anti-pattern)](https://watirmelon.com/2012/01/31/introducing-the-software-testing-ice-cream-cone/)
  6. F. Pereira, 2014: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Introducing the Software Testing Cupcake (Anti-Pattern) ](https://www.thoughtworks.com/de/insights/blog/introducing-software-testing-cupcake-anti-pattern)
  7. J. Vester, 2016: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[REST API Versioning - Is There a Right Answer?](https://dzone.com/articles/rest-api-versioning-is-there-a-right-answer)
  8. T. Clemson, 2014: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Testing Strategies in a Microservice Architecture ](http://martinfowler.com/articles/microservice-testing/#anatomy-modules)
  9. elastic: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[ELK-Stack](https://www.elastic.co/products)
  10. ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Zipkin](http://zipkin.io/)
  11. ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Prometheus](https://prometheus.io/)
  12. J. Lewis, M. Fowler, 2014: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Microservices - a definition of this new architectural term](http://martinfowler.com/articles/microservices.html)
  13. Wikipedia: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Fallacies of distributed computing](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)
  14. U. Friedrichsen, 2014: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Patterns of resilience](http://www.slideshare.net/ufried/patterns-of-resilience) 
  15. Y. Izrailevsky, A. Tseitlin, 2011: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[The Netflix Simian Army ](http://techblog.netflix.com/2011/07/netflix-simian-army.html)
  16. A. Brooke, 2013: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Use Canary Deployments to Test in Production ](http://www.infoq.com/news/2013/03/canary-release-improve-quality)
  17. B. Christian, 2012: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[The A/B Test: Inside the Technology That’s Changing the Rules of Business ](http://www.wired.com/2012/04/ff_abtesting/)
  18. Amazon AWS Dokumentation: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[The Math Behind A/B Testing ](https://developer.amazon.com/public/apis/manage/ab-testing/doc/math-behind-ab-testing)
  19. Martin Fowler, 2010: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[BlueGreenDeployment ](http://martinfowler.com/bliki/BlueGreenDeployment.html)

![nach Oben](fileadmin/templates/wr/images/LinkToTop.png)

