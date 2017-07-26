# Von Continuous Integration zu Continuous Delivery mit Jenkins Workflow

_Captured: 2017-02-05 at 13:40 from [www.informatik-aktuell.de](https://www.informatik-aktuell.de/entwicklung/methoden/von-continuous-integration-zu-continuous-delivery-mit-jenkins-workflow.html)_

![Leistungsfähige Workflow-Funktionalität in Jenkins nutzen: Von Continuous Integration \(CI\) zu Continuous Delivery \(CD\). © Jenkins logo with title von The Jenkins project. Lizenziert unter](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_720-Jenkins_13882ad843.jpg)

> _Leistungsfahige Workflow-Funktionalitat in Jenkins nutzen: Von Continuous Integration (CI) zu Continuous Delivery (CD). (C) Jenkins logo with title von The Jenkins project. Lizenziert unter_

**Die großen Internethandler und Social Media-Giganten reden heute alle von Continuous Delivery. Fur alle anderen findet eine stille Revolution statt, da Unternehmen aller Art vom Startup bis zum Autohersteller und zum mittelstandischen Betrieb nach Moglichkeiten suchen, um ihre Software schneller als die Konkurrenz zu optimieren. Jeder sagt, dass man es tun soll, aber wie fangt man es am besten an?**

Ich selbst habe von der Pike auf und auf die harte Tour gelernt, wie man PaaS- und SaaS-Frameworks baut, und vielleicht gibt es keinen wirklich bequemen Weg. Trotzdem kann ich ein paar Tipps geben, wie Entwicklungsteams von Continuous Integration (CI) zu Continuous Delivery (CD) gelangen konnen, indem sie die leistungsfahige Workflow-Funktionalitat in Jenkins [[1]](https://www.informatik-aktuell.de/entwicklung/methoden/von-continuous-integration-zu-continuous-delivery-mit-jenkins-workflow.html) nutzen.

![Abb.1: CI -Pipeline. © Bernhard Cygan](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_Jenkins-Abb1-Cygan_c7e6ebd242.png)

> _Abb.1: CI -Pipeline. (C) Bernhard Cygan_

Continuous Integration (CI) ist das Verfahren, mit dem die Arbeitskopien aller Entwickler mehrmals taglich mit einer gemeinsamen Mainline-Version gemerged werden. Dies gibt den Entwicklern ein schnelleres Feedback fur den Fall, dass ihr Code einen Fehler verursacht. Der Ablauf wird in Abb.1 veranschaulicht.

Dieser typische CI-Prozess liefert den Entwicklern ein Feedback, wenn ihr Code bei einem der Integrationstests durchfallt. Was jedoch CD grundlegend von CI unterscheidet, ist, dass CD nicht nur den Code validiert, sondern auch die Applikation fur den Einsatz unter den realen Einsatzbedingungen vorbereitet und dabei sogar berucksichtigt, wie sich das Benutzerverhalten auf die Applikation "im echten Einsatz" auswirken kann.

Vor der Behandlung weiterer Einzelheiten sollte an dieser Stelle mit einem haufigen Missverstandnis aufgeraumt werden. Es ist zu beachten, dass bei Continuous Delivery die Entscheidung, ob und wann eine Software in der Produktivumgebung eingesetzt wird, nicht automatisch getroffen wird. Auf Wunsch kann jedoch manuell ein vollstandig automatischer Prozess angestoßen werden.

![Abb.2 © Bernhard Cygan](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_Jenkins-Abb2-Cygan_f941c099cf.png)

> _Abb.2 (C) Bernhard Cygan_

Dies ist der Wirkungsbereich von "Continuous Deployment", eines DevOps-Verfahrens, bei dem Artefakte automatisch fur verschiedene Stadien einer Build-Pipeline freigegeben werden. Wenn alle Stadien zufriedenstellend durchlaufen werden, wird die Software letztendlich in die Produktivumgebung entlassen. Wenn ein automatisierter Test in einer "Quasi-Produktivumgebung" positiv verlauft, fuhren die automatisierten Freigaben fur die generierten Artefakte letztendlich dazu, dass die Software ohne menschliches Zutun in den Produktiveinsatz gelangt. Dies ist wie Continuous Delivery, aber vollstandig automatisiert.

Dies kann fur manche Teams sinnvoll sein und fur andere nicht. In jedem Fall muss man eine klare Unterscheidung treffen, wenn man intern die Notwendigkeit von Continuous Delivery befurwortet. Technisch gesehen stellt die Einfuhrung von Continuous Deployment keinerlei Risiko dar; auf organisatorischer Ebene kann sich das Projekt jedoch als etwas kniffelig erweisen, da es einen gefuhlten Kontrollverlust mit sich bringt - was sich im einen oder anderen Fall als Hemmschwelle erweisen kann.

![Abb.6: Definition der Variablen. © Bernhard Cygan](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_Jenkins-Abb6-Cygan_0eceb27d70.png)

> _Abb.6: Definition der Variablen. (C) Bernhard Cygan_
