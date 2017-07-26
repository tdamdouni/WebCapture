# 5 Best Practices für sichere Open-Source-Integration

_Captured: 2017-06-01 at 20:18 from [www.maschinenmarkt.vogel.de](http://www.maschinenmarkt.vogel.de/5-best-practices-fuer-sichere-open-source-integration-a-612803/?cmp=beleg-mail&utm_campaign=Sharing%20Security%20Stories&utm_content=55163245&utm_medium=social&utm_source=twitter)_

![Open-Source-Komponenten sind nicht zwingend unsicher, aber ihre Schwachstellen sind weitaus besser dokumentiert.](http://images.vogel.de/vogelonline/bdb/1236900/1236938/41.jpg)

> _[Open-Source-Komponenten sind nicht zwingend unsicher, aber ihre Schwachstellen sind weitaus besser dokumentiert.](http://www.maschinenmarkt.vogel.de/index.cfm?pid=11048&pk=1236938&type=article&fk=612803)_

Open Source Code ist nicht zwingend anfalliger als poprietarer Code. Bei quelloffenen Komponenten sind aber viele Informationen uber Schwachstellen vorhanden, was sie fur Angreifer durchaus interessant macht. Mit diesen funf Best Practices wird Open Source sicher.

Kurzlich hat ein Forrester Research-Report die Aufmerksamkeit auf Open-Source-Kompoenten in der Anwendungsentwicklung gelenkt: lediglich zehn bis 20 Prozent des Codes in Anwendungen seien demnach maßgeschneidert, der Rest basiert auf frei verfugbarem Code.

Obwohl traditionelle Sicherheitstools fur Anwendungen wie DAST (Dynamic Application Security Testing) oder SAST (Static Application Security Testing) effektiv Bugs in maßgeschneidertem Anwendungscode finden, konnen sie Schwachstellen in Open-Source-Komponenten nicht identifizieren - oft auch nicht nach Monaten oder Jahren, nachdem die Bugs offentlich bekannt wurden.

Tatsachlich werden die meisten Open-Source-Schwachstellen von Sicherheitsexperten entdeckt und nicht etwa durch DAST oder SAST. Seit dem Jahr 2004 wurden mehr als 74.000 Schwachstellen von der National Vulnerability Database (NVD) bekanntgegeben, davon resultiert jedoch nur eine Handvoll aus kommerziellen Sicherheitstools wie DAST, SAST oder Fuzzers.

Anzeige

Mehr als 80 Prozent aller [Cyber-Attacken erfolgen auf Applikationsebene](https://www.blackducksoftware.com/sites/default/files/images/Downloads/Guides/USA/DIYGuide_Gd_UL.pdf). Kombiniert man nun die Fakten, dass Anwendungen das Hauptziel von Cyberattacken sind, Open Source andererseits ein wesentlicher Bestandteil von Code heutzutage ist und schließlich traditionelle Sicherheitstools nicht effektiv in der Identifikation von Open Source sind, kommt man zu folgendem Schluss: Schwachstellen in Open Source gehoren zu den großten Risiken fur die Sicherheit von Anwendungen.

Unsere Forschung zeigt, dass eine kommerzielle Anwendung im Durchschnitt aus mehr als 140 diskreten Open-Source-Komponenten besteht. Im vergangenen Jahr wurden mehr als 3.600 neue Schwachstellen in Open-Source-Komponenten gemeldet - das sind im Schnitt zehn pro Tag sowie ein Anstieg um zehn Prozent gegenuber 2015.

Anzeige

Vor diesem Hintergrund wird klar, dass effektive Open-Source-Sicherheit und -Verwaltung dringend benotigt werden. Allerdings zeigen unsere Untersuchungen von Code konsequent, dass sich viele Organisationen der Sicherheits- und Lizenzvereinbarungsrisiken, denen sie sich mit der Verwendung von Open Source moglicherweise aussetzen, nicht bewusst sind.

### Warum mogen Angreifer Open-Source-Schwachstellen?

Es gibt keinen Beweis dafur, dass Open Source mehr oder weniger sicher ist als maßgeschneiderte Software. Beides ist Software, die potenziell Bugs enthalt. Aufgrund der Allgegenwartigkeit von beliebten Open-Source-Komponenten jedoch sehen Angreifer diese als attraktive Umgebung mit offentlich verfugbaren Informationen uber Schwachstellen sowie detaillierten Informationen und Beispiele daruber, wie man sie ausnutzt.

Open Source ist nur schwer manuell nachzuverfolgen, so dass Organisationen oft nicht wissen, welche Open-Source-Komponenten sie nutzen. Im Unterschied zu kommerzieller Software, bei der dem Kunden Updates und Bug-Fixes mitgeteilt werden, ist Open Source ein „Pull"-Support-Modell.

Das heißt, die Nutzer sind selbst dafur verantwortlich, sich uber Schwachstellen, Fixes und Updates fur den verwendeten Open-Source-Code zu informieren. Auch wenn sich eine Organisation der verwundbaren Open-Source-Komponenten bewusst ist, die sie nutzt, ist es dennoch sehr wahrscheinlich, dass die Komponenten ungepatched bleiben.

### Best Practice, um Open-Source-Risiken zu umgehen

**1\. Erstellung und Durchsetzung von Richtlinien fur den Gebrauch von Open Source**

Viele Organisationen tun sich bereits bei der Dokumentation von Open-Source-Richtlinien schwer. Es sollte einen Verantwortlichen oder ein verantwortliches Komitee geben, das den Gebrauch von Open Source uberwacht, Richtlinien dokumentiert und Entwickler darin schult, wie man verantwortungsvoll mit Open Source umgeht.

**2\. Erstellung und Unterstutzung einer umfassenden Inventarauflistung uber genutzte Open-Source-Elemente**

Es sollten alle Open-Source-Komponenten aufgelistet werden, die zur Erstellung einer Software genutzt werden. Ein vollstandiges Inventar umfasst alle Open-Source-Komponenten, die verwendeten Versionen sowie die Downloadquellen fur jedes Projekt, das genutzt oder entwickelt wird. Zudem sollten Abhangigkeiten darin enthalten sein, also die Bibliotheken, die der Code aufruft, beziehungsweise die Bibliotheken, auf die die Abhangigkeiten verlinken.

Sollten externe Entwickler beteiligt sein, sollte man sichergehen, dass diese ebenso gewissenhaft mit dem Inventar umgehen wie das eigene Team. Denn je großer das Team ist und je mehr Teams man hat, desto unhandlicher wird der Inventarprozess und desto anfalliger ist man fur Fehler und Versaumnisse.

**3\. Überblick uber bekannte Sicherheitsschwachstellen von Open Source**

Quellen wie die NVD bieten Informationen zu offentlich bekannten Schwachstellen in Open-Source-Software; jedoch werden nicht alle Schwachstellen der NVD gemeldet und oft es ist schwer zu erkennen, welche Version einer angegebenen Open-Source-Komponente betroffen ist. Man sollte sich daher nicht nur auf die NVD als Informationsquelle fur Schwachstellen stutzen. Weitere hilfreiche Informationsquellen sind Projektverteilungsseiten, wie sie beispielsweise von [Debian](https://www.debian.org/security/)\- oder [Python](http://bugs.python.org/)-Projekten gepflegt werden. Security-Blogs und Message Boards wie die [US-CERT Alerts Page](https://www.us-cert.gov/ncas/alerts) oder das [Security Weblog von Google](https://security.googleblog.com/) sollten ebenfalls Teil der Informationsquellen zu Schwachstellen sein.

**4\. Identifizierung weiterer Open-Source-Risiken**

Die Nichteinhaltung von Open-Source-Lizenzierungen kann fur Organisationen ein Risiko fur Rechtsstreitigkeiten oder eine Verletzung des geistigen Eigentums darstellen. Ebenso kann die Verwendung von veralteten oder schlechten Komponenten die Qualitat der Anwendungen beeintrachtigen.

**5\. Standige Überwachung von neuen Open Source Risiken**

Mit uber 3.600 neuen Schwachstellen, die jedes Jahr bekannt werden, endet das Tracking von Schwachstellen nicht, wenn eine Anwendung die Entwicklungsphase verlasst. Organisationen mussen stetig Ausschau nach neuen Bedrohungen halten, solange die Anwendung in Gebrauch ist.

### Ein Schritt in Richtung Open-Source-Sicherheit

![Mike Pittenger](http://images.vogel.de/vogelonline/bdb/1236900/1236939/27.jpg)

> _Mike Pittenger (Bild: Black Duck Software)_

Auch wenn es einfacher scheint, wie bisher weiter zu machen und auf das Beste zu hoffen, ist der wichtigste Schritt, einen Open-Source-Security-Management-Prozess zu etablieren. Denn Anwendungsschwachstellen sind die großte Sicherheitsbedrohung fur die eigene Organisation; und der Gebrauch von Komponenten mit bekannten Schwachstellen zahlt zu den [OWASP Top 10](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project). Ohne Inventarisierung, Verwaltung und Sicherung der Open-Source-Komponenten, die in den Anwendungen enthalten sind, ist man fur Angreifer leichte Beute.

_* Mike Pittenger ist Vice President Security Strategy bei Black Duck Software und verfugt uber 30 Jahre Erfahrung in Technik und Wirtschaft, mehr als 25 Jahre Fuhrungserfahrung und 15 Jahre im Security-Bereich. Bei Black Duck ist er verantwortlich fur die strategische Leitung von Sicherheitslosungen, einschließlich Produktausrichtung. _
