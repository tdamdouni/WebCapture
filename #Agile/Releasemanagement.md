# Releasemanagement

_Captured: 2015-10-23 at 18:05 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Releasemanagement)_

Dieser Artikel oder nachfolgende Abschnitt ist nicht hinreichend mit [Belegen](https://de.m.wikipedia.org/wiki/Wikipedia:Belege) (beispielsweise [Einzelnachweisen](https://de.m.wikipedia.org/wiki/Hilfe:Einzelnachweise)) ausgestattet. Die fraglichen Angaben werden daher moglicherweise demnachst entfernt. Bitte hilf der Wikipedia, indem du die Angaben recherchierst und gute Belege einfugst. Naheres ist eventuell auf der [Diskussionsseite](https://de.m.wikipedia.org/wiki/Diskussion:Releasemanagement) oder in der Versionsgeschichte angegeben. Bitte entferne zuletzt diese Warnmarkierung.  

![](http://upload.wikimedia.org/wikipedia/de/8/8d/Releasemngt.jpg)

> _Zusammenhange verschiedener Prozesse im Release Management_

Das **Releasemanagement** (auch **Release-Management**, [englisch](https://de.m.wikipedia.org/wiki/Englische_Sprache) _release management_) ist ein Prozess, der sich ursprunglich aus den Erfahrungen des [Produktmanagements](https://de.m.wikipedia.org/wiki/Produktmanagement) der [Software-Industrie](https://de.m.wikipedia.org/wiki/Software-Industrie) ableitete, welcher die Bundelung von Konfigurations-Änderungen zu einem Release oder Versionspaket und deren ordnungsgemaße Eingliederung in der Infrastruktur sicherstellte. Releasemanagement bedeutet die Planung und Durchfuhrung der Veroffentlichung, von der Idee bzw. den ersten Anforderungen bis zum Erreichen des Endbenutzers. Es interagiert somit zwischen [Change-](https://de.m.wikipedia.org/wiki/%C3%84nderungswesen) und [Konfigurationsmanagement](https://de.m.wikipedia.org/wiki/Konfigurationsmanagement). Es ist Teil des [ITSM](https://de.m.wikipedia.org/wiki/ITSM) bzw. des [ITIL](https://de.m.wikipedia.org/wiki/ITIL)-[Service Managements](https://de.m.wikipedia.org/wiki/Service_Management).

Das Releasemanagement hat zur Aufgabe, sicherzustellen, dass eine erwartete Anforderung an eine Veranderung in einem Prozess mit einem vertretbaren Risiko in der geforderten Zeit erfolgreich umgesetzt werden kann. Anpassungen im Geschaftsbereich auf sich standig verandernde außere Anforderungen erfordern eine permanente Neukonfiguration der Systeme, die die zugrunde liegenden Prozesse steuern. Gleichzeitig erhoht in einer komplexen Umgebung dieser evolutive Prozess der dauerhaften Neukonfiguration von Systemen das Risiko, lebenswichtige Geschaftsprozesse durch Fehlkonfiguration zu storen, unvorhergesehen zu beeinflussen oder ganz zum Stillstand zu bringen. Ein Unternehmen rechtfertigt den Einsatz eines Releasemanagement mit der Reduktion der teilweise erheblichen Kosten durch etwaige Prozess-Storungen, die durch notwendige konfigurative Veranderungen hervorgerufen werden konnen. Das Releasemanagement hat die Aufgabe, die Risiken der Unterbrechung von Geschaftsprozessen bei Konfigurationsanderungen bestehender Systeme, die durch schlecht geplante oder nicht ausreichend getestete Systemkonfigurationen hervorgerufen werden, zu mindern.

Das Releasemanagement hat folgende Aufgaben:

  * Festlegung des funktionellen Umfangs
  * Festlegung des genauen Zeitplans einer Releasefreigabe in Abstimmung mit dem Change- bzw. [Produktmanagement](https://de.m.wikipedia.org/wiki/Produktmanagement)
  * [Qualitatskontrolle](https://de.m.wikipedia.org/wiki/Qualit%C3%A4tskontrolle) zur Überwachung der Einhaltung der Kriterien, die im Rahmen des Change- bzw. Produktmanagements fur eine Releaseerstellung festgelegt wurden
  * Dokumentation des Umfangs und der Änderungen, dabei insbesondere Beschreibung der fur die Ruckwarts[kompatibilitat](https://de.m.wikipedia.org/wiki/Kompatibilit%C3%A4t_\(Technik\)) relevanten Eigenschaften

Releaseanforderungen werden zunachst vom [Change-Management](https://de.m.wikipedia.org/wiki/Change_Management_\(ITIL\)) erfasst. Das Change-Management formuliert in der Regel auch den 'Use Case' und kummert sich auch um den (je nach Risiko-Relevanz teilweise recht komplexen) Genehmigungsprozess. Anschließend wird die eigentliche Aufgabe der Durchfuhrung eines Changes, also die 'Executive', an das Releasemanagement ubergeben. Daraus resultiert oft die Meinung, das Releasemanagement sei ein Teilbereich des Change-Managements. Das Releasemanagement ist jedoch nach Praxis-Erfahrung aus dem [ITIL](https://de.m.wikipedia.org/wiki/ITIL)-Bereich bewusst kein Teilbereich des Change-Managements. Unternehmen, die dies nicht berucksichtigen und Releasemanagement im Change-Management integrieren, werden recht schnell in interne Konfliktsituationen der Verantwortlichkeiten kommen, in denen die wichtigen Elemente der Risikoeinschatzung, der Planung und Qualitatskontrolle meistens aus dem notwendigen Gleichgewicht kommen. Somit stellt das Releasemanagement auch sicher, dass ein Release die erwartete Anforderung mit einem vertretbaren Risiko in der geforderten Zeit umsetzen kann. Die aktuelle [ITIL](https://de.m.wikipedia.org/wiki/ITIL) Version 3 berucksichtigt diesen Umstand und hat deshalb das Releasemanagement explizit als eigenstandige Prozesseinheit definiert.

Die Planung erstellt das Kerngerust, die eigentliche Blaupause eines gesamten Releaseprojektes.

Der Releasemanager entscheidet, wann ein System als Release zur Weitergabe freigegeben werden kann. Er muss dabei darauf achten, dass das System frei von schwerwiegenden Fehlern, also produktionssicher ist. In der traditionellen [Softwareentwicklung](https://de.m.wikipedia.org/wiki/Entwicklungsstadium_\(Software\)) ist dies der Fall, wenn der Entwicklungsprozess das Stadium [Release Candidate](https://de.m.wikipedia.org/wiki/Entwicklungsstadium_\(Software\)) erreicht.

Risiken sind immer mit Geschaftsperspektiven abzugleichen. Dabei wird ein Restrisiko teilweise bewusst in Kauf genommen um z. B. aufgrund von zu spaten Releases mit hoherer Qualitat keinen geschaftlichen Vorteil, den man durch ein fruheres Releasedatum erreicht, zu verlieren.

Die Qualitatskontrolle eines Releases ist eines der wichtigsten Elemente der Sicherstellung der Change Objectives, also der Frage

  * was will man ursprunglich mit der Änderung einer Konfigurationsanderung aus der Geschaftsperspektive erreichen und
  * stimmt das Ergebnis auch mit den Anforderungen uberein?

Realisiert wird dies durch entsprechende Testplane, durch Simulationen und Entwicklung und Test der Strategien zu Notfallsituationen.

Wenn die reine Entwicklung abgeschlossen ist, bedeutet das aber nicht gleichzeitig eine Veroffentlichung. Dazu mussen oft noch weitere Schritte erfolgen:

  * Erstellung der Konfigurationsstande, welche alle Komponenten beinhaltet
  * Zusammenstellung und Bezeichnung sowohl des Quellcodes als auch samtlicher Datendateien
  * Bereitstellung von Konfigurationsdateien, Benutzerhandbuchern, technischer Dokumentation, ...
  * Ausbildung und Vorbereitung der Mitarbeiter, die das System nutzen
  * Ausbildung und Vorbereitung der Mitarbeiter, die das System pflegen

Die Dokumentation von Releases ist z. B. zur spateren Nachproduktion oder [Ruckverfolgung](https://de.m.wikipedia.org/wiki/R%C3%BCckverfolgbarkeit_\(Anforderungsmanagement\)) von speziellen Releases fur einzelne Kunden oder Plattformen sehr wichtig.

Die [Dokumentation](https://de.m.wikipedia.org/wiki/Dokumentation) sollte eine komplette Beschreibung der gesamten [Entwicklungsumgebung](https://de.m.wikipedia.org/wiki/Entwicklungsumgebung) und des zugrunde liegenden Systems (Programme, Versionen, Dokumente, Beschreibungen, [Anleitungen](https://de.m.wikipedia.org/wiki/Anleitung), ...) enthalten, um eine spatere Wiederherstellung zu vereinfachen.

Die Archivierung zur Logistischen Verwaltung der technischen Komponenten eines Unternehmens.
