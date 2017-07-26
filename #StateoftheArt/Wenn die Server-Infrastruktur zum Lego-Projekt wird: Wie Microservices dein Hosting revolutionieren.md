# Wenn die Server-Infrastruktur zum Lego-Projekt wird: Wie Microservices dein Hosting revolutionieren

_Captured: 2016-03-20 at 12:53 from [t3n.de](http://t3n.de/news/server-infrastruktur-lego-projekt-688231/)_

Der Einstieg in die Welt der „Microservices" ist komplex: Die technische Infrastruktur muss geschaffen werden, eine gewisse Lernphase durchlaufen und die Projektplanung, Kundenkommunikation und Teamzusammenstellung reorganisiert werden. Dennoch lohnt sich die Transformation von einem „monolithischen System" hin zu einer flexiblen „Landschaft der kleinen Dienste", denn die meisten monolithischen Anwendungen leiden fruher oder spater an den gleichen Krankheitssymptomen.

So ist es bei stark gewachsenen Projekten oft schwer, veraltete Komponenten wie Libraries, Binaries oder gar Datenbanken zu aktualisieren. Alte Frameworks oder Build-Tools werden oft erst angefasst, wenn es keine andere Option mehr gibt. Hinzu kommt, dass mit hoherer Komplexitat des Projekts die Fehleranfalligkeit steigt oder Ausfalle teils dominoartige oder unvorhersehbare Zuge annehmen. Das hat auch Einfluss auf die Rollouts, die auf Grund ihres Umfangs eher selten durchgefuhrt werden, oft lange dauern und haufig von allen Beteiligten mit einer gewissen Sorge betrachtet werden. Das kann so weit fuhren, dass einzelne Projektmitarbeiter nur zogerlich Änderungen umsetzen weil sie befurchten, die Folgen nicht ganzlich uberschauen zu konnen und Fehler im System zu verursachen. Notwendiges Refactoring findet aus den gleichen Grunden in der Regel nicht mehr statt. Die Software droht zu erodieren. Im Worst Case kann das zur Unwartbarkeit fuhren, das heißt die Pflege und Weiterentwicklung verursacht so hohe Kosten, dass der Aufwand in keiner Relation mehr zum Nutzen steht.

Microservices helfen, viele dieser Probleme zu vermeiden und sie bieten einen Weg, Monolithen sukzessive abzubauen. Zentrale Voraussetzungen fur die Entwicklung von Microservices sind der Ausbau der Kommunikation zwischen Software- und System-Entwicklern, die umfangreiche Automatisierung und eine klare Vision der zu erstellenden Dienste.

## Impact I - Entwicklungsteam & Deployment

Die Cycle-Time - die Zeit von Beauftragung bis Lieferung eines Features - ist eines der Kernargumente fur den Einsatz von Microservices. Auf dem Grundsatz, dass ein Service nur eine Aufgabe erfullen sollte, werden Komponenten einer Plattform gekapselt und somit deren Funktionsumfang klar definiert. Entwicklern fallt es dadurch viel leichter, den Umfang einer Änderungen zu uberschauen. In der Folge reduziert sich nicht nur der Aufwand fur die jeweilige Implementierung, sondern auch die Zeit, die fur nachgelagerte Tests benotigt wird.

Bei Microservices mit Docker rutscht zudem ein großer Teil der Infrastruktur in den Code. Als klassische Server-Infrastruktur existieren am Ende nur noch dedizierte oder virtuelle Hosts, die Rechenpower, RAM, Storage und einen Docker-Daemon zur Verfugung stellen. Beim Rollout wird das Starten oder Ersetzen der gewunschten Container automatisiert.

![Docker-Logo. \(Grafik: Docker\)](http://t3n.de/news/wp-content/uploads/2015/11/docker-google-cloud-platform-595x397.jpg)

> _Bei Docker rutscht ein Großteil der Infrastruktur in den Code. (Grafik: Docker)_

Auf dieser Basis macht es am Ende keinen Unterschied, ob Anpassungen an einer Datenbank-Konfiguration oder an einer Web-Applikation vorgenommen werden. Alle Änderungen mussen den gleichen Weg durch Versionsverwaltung, Review-Prozess und die Continuous-Delivery-Pipeline gehen. Nur so lasst sich sicherstellen, dass bei der Implementierung neuer Features Fehler vermieden und alle Qualitatstandards eingehalten werden. Neofonie realisiert Reviews unter anderem mit Hilfe von Pull-Requests, die das Versionierungs-System Stash (Git) zur Verfugung stellt. Als Build-System kommt Go CD zum Einsatz.

Nach einer gewissen Reifephase, die alle derartigen Prozesse durchlaufen, ist der Weg frei zum Continuous Deployment - dem automatischen Ausrollen auf den Live-Systemen. Das erfordert die Automatisierung aller Schritte in der Delivery-Kette und ein hohes Maß an Testabdeckung, damit keine defekte Software ausgerollt wird. Neofonie verwendet fur den Test von REST-APIs beispielsweise das Test-Framework Aiko - eine Open-Source-Eigenentwicklung die auch [auf GitHub veroffentlicht wurde ](https://github.com/Neofonie/aiko).

Fur die Entwickler und Systems-Engineers andert sich die Art der Zusammenarbeit. Wo sich zuvor die Spezialisten unterschiedlicher Abteilungen gegenseitig den Ball uber den Zaun geworfen haben, trifft jetzt ein cross-funktionales Team selbststandig Entscheidungen. So kann es anstehende Aufgaben bestmoglich losen. Diese Form von Empowerment wirkt sich motivierend auf alle aus, da es nicht nur langwierige und teils muhselige Kommunikation uber den Umfang von Auftragsteilen eliminiert, sondern auch Ausdruck von Vertrauen aller Stakeholder ist. Trotzdem - oder gerade darum - ist eine enge Abstimmung innerhalb des Teams notwendig, denn es gilt der Grundsatz: „You build it, you run it". Auch in der Neofonie waren die Entwicklungs- und Betriebs-Abteilungen strikt getrennt. Diese Trennung lost sich jedoch zunehmend auf, ganz im Sinne des DevOps-Gedanken und der Kunden.

![Neofonie testet seine REST-APIs mit dem eigens entwickelten Open-Source-Framework Aiko. \(Screenshot: GitHub\)](http://t3n.de/news/wp-content/uploads/2016/03/aiko-test-framework-595x347.jpg)

> _Neofonie testet seine REST-APIs mit dem eigens entwickelten Open-Source-Framework Aiko. (Screenshot: GitHub)_

Mitglieder eines solchen Teams bauen automatisch uber die Zeit hinweg neben ihren Kernkompetenzen Fahigkeiten außerhalb ihrer bisherigen Tatigkeiten auf. Erfahrenere Kollegen validieren die Entscheidungen von weniger erfahrenen Kollegen. Das minimiert das Risiko, dass Wissensinseln entstehen und dass durch den manchmal unvermeidlichen Weggang einzelner Kollegen kostbare Informationen zum Projektaufbau verloren gehen.

Eine weitere, uber die gesamte Projektlaufzeit hinweg integrale Rolle im Team ist die des Product-Owners, der die Produktvision der umzusetzenden Dienste aufrecht erhalt und bei Ruckfragen zur Verfugung steht. Denn wo sich schnell Arbeitspakete aus der laufenden Entwicklung ergeben, braucht es jemanden, der das finale Ziel stets vor Augen hat.

Er ist das kommunikative Bindeglied im Team und ermoglicht durch schnelle Informationsbeschaffung und klare Kommunikation die eigentliche Performance bei der Umsetzung der Komponenten.

## Impact II - Betrieb

Die Sicherstellung des storungsfreien Betriebs fur Services, deren Komponenten potenziell in jedem Moment im Rahmen eines automatischen Rollouts durch andere ersetzt werden konnen, stellt nochmal andere Anforderungen, als das bei konventionellen Architekturen der Fall ist.

Das offensichtlichste ist das Monitoring. Statische Konfigurationen sind nur bedingt einsetzbar. Die Systemuberwachung selbst muss Teil der Microservice-Infrastruktur werden. Nur so konnen valide Informationen zum Soll-Zustand der Dienste ermittelt werden. Eine hohere, erstrebenswerte Ausbaustufe dessen ist ein proaktives System. Dort werden die eingesetzten Kontrollen selbst in die Lage versetzt, korrektive Maßnahmen zu ergreifen und einzelne Ausfalle zu verhindern, wenn nicht gar zu beheben.

Das reduziert jedoch nicht die Notwendigkeit eines Incident-Response-Teams, das in der Nacht auf einen Zwischenfall im System reagieren kann, denn eine einhundertprozentige Automatisierung gibt es auch in komplexen Microservice-Infrastrukturen nicht. Dessen Aktivitaten allerdings beschranken sich normalerweise nur noch auf den bewusst entschiedenen oder unterlassenen Neustart oder das Hochskalieren von Instanzen. Fur alles andere ist das Projektteam verantwortlich, das den Service gebaut hat.

![\(Grafik: Shutterstock\)](http://t3n.de/news/wp-content/uploads/2016/03/server-illustration-microservices-shutterstock_376067962-595x397.jpg)

> _Stockt ein Microservice, sollten die anderen auf dem Server ohne Probleme weiterlaufen. (Grafik: Shutterstock )_

Zum Anderen ist Resilience ein wichtiger Punkt. Gemaß des Prinzips „Everything fails, all the time!" darf der Ausfall eines Servers im Rechenzentrum oder der Absturz einer Anwendung zu keiner Beeintrachtigung der verbleibenden Services fuhren. Wenn ein Service ausfallen sollte, mussen dessen Konsumenten graceful damit umgehen. Sie durfen auch bei Timeouts und invaliden Antworten keine Fehler werfen und mussen großtenteils weiter funktionieren. Das Wegbrechen einer einzelner Funktionalitaten hat in diesem Moment keine Folgen mehr fur die Verfugbarkeit der Webseite. Es arbeitet dann lediglich der betroffene Teil der Seite nicht mehr, beispielsweise eine Suche. So konnen unschone Fehlermeldungen vermieden und im Fall der Falle eine konsumierende Komponente - wie ein Suchfeld oder eine Ergebnisliste - ausgegraut oder deaktiviert werden.

## Impact III - Management & Sales

Wo zuvor Key-Account- und Projektmanager in regelmaßigen Abstimmungsrunden mit den Kunden Change-Requests und Milestones produzierten, um daraus formulierte Tickets am Ende in die Entwicklungsteams zu kippen, entsteht jetzt ein fließender Prozess. Große Change-Requests machen vielleicht noch Sinn, wenn es darum geht, einen großen Monolithen um- oder weiterzustricken. Änderungen an Microservices hingegen sind inharent uberschaubar und in der Regel deutlich schneller umsetzbar. Das Rollout setzt keine Downtime fur andere Komponenten der Infrastruktur voraus. Das bedeutet fur den Auftraggeber einen kurzeren Time to Market, Ausfallsicherheit, Stabilitat, Resilience, Skalierbarkeit, sowie einen reduzierten Abstimmungs- und Planungs-Overhead.

Anfragen zum Status von Beauftragungen konnen schneller beantwortet werden und Zwischenzustande sind einfacher zu prasentieren. Die großste Herausforderung ist es, agile Konzepte firmenweit zu etablieren. Die Unterstuzung der Geschaftsfuhrung und von externen Coaches ist dazu so gut wie unerlasslich.

## Fazit

Die Vorteile, die Microservices gegenuber konventionellen Strukturen bieten, liegen klar auf der Hand.

  * Kurzere Time To Market und Cycle-Time
  * Bessere Wartbarkeit durch austauschbare Teile
  * Reduzierte Downtimes durch Incidents
  * Keine Downtime bei Rollouts
  * Resilientes Verhalten - ein einzelner Ausfall produziert keinen Domino-Effekt
  * Jeder Dienst lauft im Cluster und kann im Bedarfsfall problemlos skaliert werden
  * Technologie-Agnostisch - durch die Kommunikation via REST-Calls kann letztlich fur jede Komponente die optimale Technologie verwendet werden, zum Beispeil Java oder Go, was mit einem Monolithen nicht moglich ist
  * Zukunftssicherer Betrieb - alte Technologien ersetzt man ohne großen Aufwand Stuck fur Stuck durch Neue
  * Bugs und Fehlentscheidungen sind vom Umfang begrenzt und konnen mit vertretbaren Kosten korrigiert werden
  * Schnelle Reaktion auf (Business-)Anforderungen - ein neuer Service ist innerhalb von Minuten erstellt und auf der Produktions-Umgebung ausgerollt (wir brauchen zur Zeit etwa 30 Minuten dafur)

### Über die Autoren:

**Timo Sellin** ist Senior Software-Entwickler und beschaftigt sich unter anderem mit DevOps und Docker. (Foto: Malte Cornils / Neofonie)
