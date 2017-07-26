# Server-Administration: Was zur Hölle sind eigentlich Container?

_Captured: 2016-10-18 at 17:36 from [t3n.de](http://t3n.de/news/was-sind-container-756373/)_

![Server-Administration: Was zur Hölle sind eigentlich Container?](http://img.t3n.sc/news/wp-content/uploads/2016/10/container.jpg?auto=compress%2Cenhance%2Cformat&fit=crop&fm=jpg&h=347&ixlib=php-1.1.0&q=65&w=620&s=c4f51795628f83570906a34881442630) (Foto: Shutterstock) 

18.10.2016, 16.50 Uhr

Entwickler-Konferenzen werden dieses Jahr von einem Buzzword dominiert: Container. Doch was genau ist das eigentlich? 

Docker, Google Kubernetes oder Mesos – Container-Systeme sind derzeit unter Entwicklern angesagt. Microsoft, Amazon und viele andere Unternehmen wollen ebenfalls von dem Trend profitieren. Obwohl diese Entwicklung schon seit dem vergangenen Jahr viel diskutiert wird, ist der Hype darum immer noch groß. Warum eigentlich?

Der Begriff stammt aus der klassischen Industrie, die seit Ende der 1950er Jahre auf Container für den Transport unterschiedlichster Güter setzt, schreibt [Techcrunch](https://techcrunch.com/2016/10/16/wtf-is-a-container/). LKW und Schiffe waren dafür zuständig, die Ware von einem Ort zum nächsten zu bringen. Das funktioniert vor allem deshalb, weil Container über eine ISO-Norm standardisiert sind. Durch die einheitlichen Standards weiß jedes Unternehmen, wie viel Platz für den Transport zur Verfügung steht.

## Was Software-Container mit Schiffscontainern gemein haben

Das Versprechen bei Containern als Software ist ähnlich: Ein Container fungiert als Behälter von Anwendungen, einschließlich benötigter Komponenten wie Frameworks oder Bibliotheken. Ähnlich wie bei der altbekannten Virtualisierung von verschiedenen Betriebssystemen auf einem [Server](http://t3n.de/tag/server), virtualisieren Container Anwendungen, die jeweils nichts von einander wissen. Alle virtualisierten Anwendungen laufen unter demselben Host-Betriebssystem – das spart gegenüber der klassischen Virtualisierung ganzer Betriebssysteme Overhead.

## Die Vorteile von Containern

Die Vorteile der Anwendungsvirtualisierung über Container sind eine verbesserte Sicherheit und eine leichtere Verwaltung der Software auf dem Server: Wird eine Anwendung gehackt, kann der Angreifer nur den Container manipulieren – nicht die anderen virtualisierten Anwendungen auf dem System. Zudem lassen sich Anpassungen eines Container-Betriebssystems umsetzen, ohne dass andere Anwendungen auf dem Server betroffen sind – das erleichtert auch die Entwicklung. Durch das Containter-Format können Anwendungen auch leichter zwischen Servern umziehen, da sie jeweils die passende Software-Umgebung mitbringen.

Container ermöglichen es zudem, Anwendungen in viele kleine Microservices aufzuspalten, die dann untereinander kommunizieren. Das erleichtert die Entwicklung: Programmierer können Änderungen an jedem einzelnen Container vornehmen, ohne dass diese die anderen Programmbestandteile beeinflussen – zumindest, so lange nichts an der Art, wie die Microservices untereinander kommunizieren, verändert wird. Damit wird es den Entwicklern einfacher gemacht, Software zu entwickeln, die funktioniert – egal in welcher Server-Umgebung sie eingesetzt wird. Auch das Testen auf Fehler wird damit vereinfacht.

Container sind schon lange ein Kernbestandteil von [Linux](http://t3n.de/tag/entwicklung-design) – aber erst die beliebte Software [Docker](http://t3n.de/magazin/ueber-container-technologie-wissen-musst-docker-gehts-240047/) bot Container, die einfach zu verwalten sind. Da die Container klein und einfach aufgebaut sind, können viele Container auf einem einzigen Computer ausgeführt werden.

Bevor Container existierten, wurden virtuelle Maschinen eingesetzt, um beispielsweise von der erhöhten Sicherheit zu profitieren, die Anwendungen mit sich bringen, die nichts von einander wissen. Das Betriebssystem glaubt hierbei, dass ein Hardware-Server existiert, in Wirklichkeit jedoch wird die Hardware mit vielen anderen virtuellen Maschinen geteilt. Alle Betriebssysteme lassen den Nutzer in dem Glauben, ihr Projekt würde priorisiert werden. Das kann zu einem Problem werden: Die Software läuft auf virtuellen Maschinen, der Overhead wird enorm hoch und die Prozesse werden sehr langsam. Nicht nur die Applikation selbst, sondern auch viele weitere Ressourcen werden benötigt. Dieses Problem besteht bei Containern nicht – das Host-Betriebssystem ist über alle Container-Anwendungen im Bilde.

## Der Aufstieg von Docker

Docker ist die derzeit beliebteste Container-Software. Das Unternehmen dahinter sammelte 2015 bereits 15 Millionen US-Dollar Risikokapital ein. Docker ist 2013 als Linux-Feature bekannt geworden und kann für die automatisierte Bereitstellung von Applikationen genutzt werden. Um diese Container zu verwalten, wird eine spezielle Software – wie zum Beispiel Docker – benötigt.

Container haben gegenüber dem klassischen Einsatz virtueller Maschinen viele Vorteile – aber zahlreiche Anwendungen und ältere Software, die in großen Unternehmen eingesetzt wird, lassen sich nicht so leicht auf das Container-Prinzip übertragen. So angesagt Container daher sind: Virtuelle Maschinen werden nicht allzu bald verschwinden. 

![](http://vg04.met.vgwort.de/na/cbadb2c216a64741924b40806b1518ea)

via [techcrunch.com](https://techcrunch.com/2016/10/16/wtf-is-a-container/)

