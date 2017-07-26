# Wie funktioniert eigentlich TCP/IP?

_Captured: 2016-10-17 at 09:30 from [t3n.de](http://t3n.de/news/tcp-ip-internet-grundlagen-755667/)_

![Wie funktioniert eigentlich TCP/IP?](http://img.t3n.sc/news/wp-content/uploads/2016/10/netzwerke-tcp-ip-internet.jpg?auto=compress%2Cenhance%2Cformat&fit=crop&fm=jpg&h=347&ixlib=php-1.1.0&q=65&w=620&s=94b5068b48bc3470b6264d51ac482a50)

(Foto: [Shutterstock](http://www.shutterstock.com/pic-433604629/stock-photo-fiber-optic-cables-connected-to-an-optic-ports-and-utp-network-cables-connected-to-ethernet-ports.html))

17.10.2016, 07.23 Uhr

Im Grunde basiert nahezu unsere gesamte Internet-Kommunikation auf den Netzwerkprotokollen TCP und IP. Aber wie funktionieren die eigentlich? 

## TCP/IP: Was heißt das und wofür brauche ich das?

Während die meisten von uns zumindest ein ungefähres Verständnis davon haben, wie Webseiten aufgebaut sind, dürfte es außerhalb von Fachzirkeln deutlich weniger Menschen geben, die sich mit den beiden wichtigsten Internetprotokollen TCP und IP beschäftigen. Dabei haben wir von der Übertragung von Webseiten an unseren Browser bis hin zum Versenden von E-Mails im Grunde ständig mit TCP/IP zu tun. Wir wollen euch mit diesem Text nicht zum Experten für Netzwerkprotokolle machen, aber euch zumindest einen groben Überblick geben, was TCP/IP eigentlich macht und in welchem Verhältnis es in Verbindung zu anderen bekannten Internet-Protokollen wie HTTP oder SMTP steht.

Beginnen wir mit den Namen: TCP steht für Transmission Control Protocol. IP wiederum ist die Kurzform von Internet Protocol. Es handelt sich also um zwei verschiedene Protokolle, die gemeinsam die Grundlage für das Internet bilden. Hierzu müsst ihr wissen, dass die Kommunikation über Computernetzwerke grundsätzlich über Protokolle geregelt wird. Die legen fest, nach welchen Regeln und in welchem Format miteinander kommuniziert werden soll. In etwa so, wie wir auch in unserer Gesellschaft eine Sprache und gewisse Kommunikationsgepflogenheiten festgelegt haben.

Der eigentliche Austausch von Nachrichten über das Internet erfordert das Zusammenspiel mehrerer Protokolle. Der Einfachheit halber werden die üblicherweise in Schichten organisiert. Jede Schicht dient der Erfüllung einer speziellen Aufgabe. Dabei verwenden die Protokolle aus höheren Schichten Dienste von tieferen Schichten.

![Das TCP-IP-Referenzmodell. \(Grafik: Shutterstock\)](http://t3n.de/news/wp-content/uploads/2016/10/tcp-ip-internet-protokolle-620x384.jpg) Das TCP-IP-Referenzmodell. (Grafik: [Shutterstock](http://www.shutterstock.com/pic-171603395/stock-vector-computer-networks-application-layer-of-tcpip-networking-model-work-of-http-protocol.html))

Mit diesem Wissen im Hinterkopf kommen wir zum TCP/IP-Referenzmodell: Das besteht aus vier Schichten, die wie erwähnt jeweils aus einem Protokoll bestehen. Es gäbe zwar eine ganze Reihe von möglichen Kombinationen nach dem TCP/IP-Schichtenmodell, aber wir wollen uns an dieser Stelle auf die aus Sicht eines Internet-Nutzers gängigste Variante konzentrieren.

### Die vier Schichten des TCP/IP-Referenzmodells:

  * **Anwendungsschicht**
    * Protokolle: HTTP, HTTPS, SMTP, POP3, Telnet, ...

  * **Transportschicht**
    * Protokoll: TCP

  * **Internetschicht**
    * Protokoll: IP

  * **Netzwerkschicht**
    * Protokoll: Ethernet

## Übertragung einer Webseite: Wer macht jetzt eigentlich was?

Im Folgenden wollen wir euch kurz und knapp erläutern, wie die vier Schichten zusammenarbeiten. Da wir alle das Ergebnis kennen, nehmen wir als Beispiel die Übertragung einer Webseite an einen Browser.

### Die Anwendungsschicht am Beispiel von HTTP

Beim Aufruf einer Webseite über euren Browser sendet dieser zunächst eine HTTP-GET-Anfrage. Darin steht, welche HTTP-Version verwendet wird und welche Webseite ihr gerne vom Server hättet. Der Server wiederum antwortet zunächst mit einer Header-Information. Die besteht aus verschiedenen Angaben zum Server selbst und zum übertragenen Inhalt. Anschließend wird die eigentliche Nachricht, sprich die Webseite im HTML-Format, übertragen.

![HTTP: Die oberste Schicht des Referenzmodells. \(Grafik: Shutterstock\)](http://t3n.de/news/wp-content/uploads/2016/10/tcp-ip-http-internet-protokolle-620x389.jpg) HTTP: Die oberste Schicht des Referenzmodells. (Grafik: [Shutterstock](http://www.shutterstock.com/pic-171603395/stock-vector-computer-networks-application-layer-of-tcpip-networking-model-work-of-http-protocol.html))

### TCP: Die Transportschicht

TCP sorgt dafür, dass es zwischen eurem Rechner und dem Web-Server zu einer Verbindung kommt. Sobald sich beide Seiten auf eine Verbindung geeinigt haben, gibt es aus Sicht des Protokolls keine Unterschiede zwischen den beiden. Browser und Server können demnach beide Informationen an ihr Gegenüber senden. Außerdem haben beide Seiten die Möglichkeit, die Verbindung wieder zu kappen. Damit es aber überhaupt zu einer Verbindung kommen kann, benötigen sie jeweils eine IP-Adresse.

### IP: Die Internetschicht

Dank der eindeutig zugeordneten IP-Adresse wird sichergestellt, dass Datenpakete an ihr richtiges Ziel kommen. Die eigentliche Sendung ist das IP-Paket, das wiederum aus Kopf- und Nutzdaten besteht. Die Kopfdaten enthalten alle wichtigen Informationen über das Ziel, die Quelle sowie eine mögliche Aufteilung der Informationen in mehrere Datenblöcke. Nutzdaten bezeichnen die eigentlichen Informationen. Darin enthalten ist auch das eine Schicht höher befindliche TCP.

### Ethernet: Netzwerkschicht

Die Netzwerkschicht ist im TCP/IP-Referenzmodell zwar spezifiziert, dient dort im Grunde aber nur als Platzhalter. Hier können verschiedene Protokolle zum Einsatz kommen, im Heimgebrauch dürften jedoch Ethernet oder 802.11 (WLAN) die häufigsten sein. Wie ihr euch vermutlich denken könnt, sorgen sie für die Kommunikation zwischen eurem Router und eurem PC.

## Fazit

Für unsere tägliche Arbeit mit dem Internet mag ein Verständnis der grundlegenden Netzwerkprotokolle zwar nicht so wichtig sein - trotzdem hoffen wir, dass der eine oder andere von euch die Informationen nützlich fand, und sich in Zukunft etwas besser vorstellen kann, worum es geht, wenn von TCP/IP die Rede ist.


