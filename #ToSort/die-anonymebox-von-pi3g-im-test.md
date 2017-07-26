# Die AnonyMeBox von Pi3g im Test

_Captured: 2017-05-20 at 00:45 from [www.raspberry-pi-geek.de](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test)_

![](http://www.raspberry-pi-geek.de/var/rpg/storage/images/magazin/2015/02/die-anonymebox-von-pi3g-im-test/aa-123rf-29634797-christian_fischer-123rf_resized.jpg/15583-1-ger-DE/AA-123RF-29634797-Christian_Fischer-123RF_resized.jpg_large.jpg)

> _(C) Christian Fischer, 123RF_

Das Tor-Netzwerk sorgt fur Anonymitat im Internet: Aufgrund des verschlungenen Pfades der Daten durch das Tor-Netz konnen Webseitenbetreiber den Nutzer nicht mehr anhand seiner IP-Adresse erkennen. Die AnonyMeBox, ein vorkonfigurierter Tor-Router auf Basis eines Raspberry Pi, leitet samtliche Daten der angeschlossenen Rechner durch Tor und sorgt so ohne großen Aufwand fur mehr Privatsphare.

Nicht erst seit den Snowden-Veroffentlichungen wissen wir, dass so gut wie jeder unserer Schritte im Internet unter Beobachtung steht. Schon die Webserver der Seitenanbieter protokollieren ublicherweise alle Zugriffe mitsamt der Zeit und Herkunfts-IP. Kaum ein Webmaster verzichtet auf Analysewerkzeuge wie Google Analytics, und die in vielen Webseiten eingebetteten "Gefallt-mir"-Buttons lassen bei Facebook, Google oder Twitter ausfuhrliche Nutzerprofile entstehen. Bei vielen Anwendern wachst daher im gleichen Maß der Wunsch nach mehr Anonymitat im Internet - doch der lasst sich gar nicht so einfach erfullen.

#### Anonymitat per Tor

Einer der einfachsten Wege zu mehr Privatsphare fuhrt uber den sogenannten Onion-Router Tor [[1]](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test/\(offset\)/2). Die Software leitet Anfragen in das Internet uber eine per Zufall bestimmte Route durch einen Wald von Servern, den Aktivisten betreiben - im Tor-Jargon heißen diese Zwischenstationen "Knoten" oder englisch "Node". Die Anonymisierungsstrecke lauft immer uber drei Knoten: Vom eigenen Rechner geht es verschlusselt zu einem Eintrittsknoten, der die Daten wieder verschlusselt zu einem weiteren Tor-Knoten innerhalb des Verbunds weiterleitet. Von dort fuhrt die Route dann uber einen Exit-Node wieder ins Internet.

Die beteiligten Server kennen jeweils nur ihren Vorganger und den Nachfolger. Somit lasst sich aus den theoretisch moglichen Logdateien des identifizierbaren Exit-Nodes nicht der eigentliche Initiator der Verbindung ermitteln. Arbeitet mindestens einer der Tor-Server vertrauenswurdig - speichert also keine Verbindungsdaten -, dann lasst sich uber Tor der komplette Netzwerkverkehr anonymisieren. Bei der Verbindung kommt es generell auf eine sichere Ende-zu-Ende-Verschlusselung an, da der Ausgangsknoten theoretisch in der Lage ware, samtliche ubertragenen Daten einzusehen. Dementsprechend konnte er Zugangsdaten oder Passworter aus dem Datenstrom fischen.

Was sich nun auf den ersten Blick sehr kompliziert und umstandlich anhort, lasst sich recht einfach umsetzen. Die Entwickler von Tor bieten mit dem Tor-Browser [[2]](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test/\(offset\)/2) ein Paket aus dem Tor-Client und einem auf Firefox basierenden Webbrowser an, das Sie nur auf den eigenen Rechner herunterladen, entpacken und starten mussen. Die Voreinstellungen des Browsers sorgen dafur, dass er keine Daten im Cache ablegt, Cookies entsorgt, Plugins wie Adobe Flash aussperrt und auch aktive Webinhalte wie Javascript ignoriert - uber diese ließen sich trotz Tor Informationen uber den Anwender erlangen. Mit Tails [[3]](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test/\(offset\)/2) gibt es gar ein Live-Linux, das Tor und eine Reihe kryptografische Werkzeuge voll integriert.

#### Tor in a Box

Noch einfacher macht es die AnonyMeBox des Raspberry-Pi-Vertreibers Pi3g [[4]](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test/\(offset\)/2). Sie ermoglicht es angeschlossenen Rechnern, uber Tor ins Internet zu gehen, ohne dass auf diesen ein Tor-Client laufen muss. So surfen Sie dann zum Beispiel auch mit mobilen Geraten wie Smartphones oder Tablets anonym. Dabei gibt es allerdings ein paar Dinge zu beachten.

Die AnonyMeBox kostet 99*Euro. Das Kit besteht aus einem Raspberry Pi Model B mitsamt Gehause, einer 16 GByte großen SD-Karte mit vorinstalliertem System, Netzteil und zusatzlichen USB-Netzwerkkarten fur WLAN- und Kabelnetzwerk ([Abbildung 1](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test)). Zur Inbetriebnahme schließen Sie die Box mit dem mitgelieferten Netzwerkkabel an Ihren Router an, stecken das USB-WLAN-Modul in eine der beiden USB-Buchsen des RasPi, setzen die Speicherkarte ein und verbinden die Box schließlich mit dem Steckernetzteil.

![](http://www.raspberry-pi-geek.de/var/rpg/storage/images/magazin/2015/02/die-anonymebox-von-pi3g-im-test/abbildung-1/15586-1-ger-DE/Abbildung-1_large.jpg)

> _Abbildung 1: Die AnonyMeBox schalten Sie uber die USB-Netzwerkkarte zwischen Rechner und Router. Alternativ loggen Sie sich in den WLAN-Access-Point der Box ein._

Die nun fertig aufgebaute AnonyMeBox erreichen Sie anschließend unter der Adresse <http://anonymebox.local> ([Abbildung 2](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test)). Die Zugangsdaten fur das Webfrontend lauten in der Voreinstellung _admin_ und `password`. Die Vorgabe sollten Sie nach Ihren ersten Tests in den _Settings_ umgehend andern. Weitere Einstellungsmoglichkeiten bietet das Frontend nicht, lediglich der Name des AnonyMeBox-WLANs lasst sich hier noch anpassen.

![](http://www.raspberry-pi-geek.de/var/rpg/storage/images/magazin/2015/02/die-anonymebox-von-pi3g-im-test/abbildung-2/15589-1-ger-DE/Abbildung-2_large.png)

> _Abbildung 2: Das Webfrontend der AnonyMeBox dient lediglich dazu, die Zugangsdaten zur Admin-Oberflache und den WLAN-Zugang zu andern._

Die WLAN-Karte arbeitet in der AnonyMeBox im Access-Point-Modus. Sie dient also nicht dazu, die AnonyMeBox drahtlos mit dem Router zu verbinden - das geht nur uber die Netzwerkschnittstelle des RasPi. Stattdessen spannt sie ein neues WLAN-Netz auf. Haben Sie die Grundeinstellung im Webfrontend nicht geandert, dann buchen Sie sich nun mit Ihrem Rechner und dem Passwort _password_ in das `anonymebox.com` benannte WLAN der Box ein ([Abbildung 3](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test)) und rufen die Tor-Testseite auf [[5]](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test/\(offset\)/2). Diese sollte melden, dass Ihr _Browser konfiguriert wurde, um Tor zu benutzen_ ([Abbildung 4](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test)).

![](http://www.raspberry-pi-geek.de/var/rpg/storage/images/magazin/2015/02/die-anonymebox-von-pi3g-im-test/abbildung-3/15592-1-ger-DE/Abbildung-3_large.png)

> _Abbildung 3: Die AnonyMeBox spannt ein eigenes WLAN auf, uber das auch mobile Gerate wie Smartphones oder Tablets anonym surfen konnen._

![](http://www.raspberry-pi-geek.de/var/rpg/storage/images/magazin/2015/02/die-anonymebox-von-pi3g-im-test/abbildung-4/15595-1-ger-DE/Abbildung-4_large.png)

> _Abbildung 4: Steht die Verbindung zur AnonyMeBox, sollte der Tor-Browser-Check melden, dass Sie anonym uber das Tor-Netzwerk surfen._

Ist Ihr Rechner per Kabelnetzwerk mit dem Router und per WLAN mit der AnonyMeBox verbunden, dann meldet die Tor-Prufseite eventuell mit _Entschuldigung. Sie benutzen nicht Tor._, dass die Verbindung nicht durch das Tor-Netzwerk fuhrt - obwohl eigentlich alles richtig eingerichtet wurde. Deaktivieren Sie in diesem Fall die Kabelnetzwerk-Schnittstelle, sodass Ihr System auf jeden Fall alle Datenpakete uber die AnonyMeBox leitet.

Egal, welche Anwendung Sie nun starten: Die AnonyMeBox leitet samtliche Datenpakete durch die Tor-Kaskade. Webseiten wie etwa Ipinfo.io [[6]](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test/\(offset\)/2) oder Ipleak.net [[7]](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test/\(offset\)/2) melden jetzt, dass Sie (beziehungsweise Ihre Internet-IP) in Hamburg, Berlin oder gar im Ausland ansassig waren. Die gemeldete Adresse entspricht der des aktuell genutzten Tor-Exit-Nodes. Steht dieser beispielsweise in Holland, dann kommt fur den angesprochenen Webserver die Anfrage eben aus den Niederlanden; Tor leitet die Daten dann weiter zu Ihnen. Dies gilt auch fur mobile Gerate wie Smartphones oder Tablets: Gehen diese uber das WLAN der AnonyMeBox ins Netz, surfen auch diese anonym ([Abbildung 5](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test)).

![](http://www.raspberry-pi-geek.de/var/rpg/storage/images/magazin/2015/02/die-anonymebox-von-pi3g-im-test/abbildung-5/15598-1-ger-DE/Abbildung-5_large.png)

> _Abbildung 5: Besonders bei mobilen Geraten wie Smartphones oder Tablets erleichtert die AnonyMeBox den anonymen Internetzugang, da diese keine speziellen Tor-Apps mehr benotigen._

Die erzielbaren Datenraten mussen sich heutzutage nicht mehr verstecken - nicht zuletzt dank leistungsfahiger Exit-Nodes wie jenen des Chaos Computer Clubs [[8]](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test/\(offset\)/2). Tropfelten die Daten in den Anfangszeiten von Tor oft nur mit 50 kbit/s durch das Netz, so leitet der Anonymisierungsverbund inzwischen Daten mit Geschwindigkeiten im einstelligen Mbit/s-Bereich durch das Internet ([Abbildung 6](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test)). Selbst Filesharing ware uber die AnonyMeBox und Tor moglich: Transmission erzielte in unserem Test beim Herunterladen diverser Linux-Distributionen eine Datenrate von bis zu 1 Mbit/s ([Abbildung 7](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test)).

![](http://www.raspberry-pi-geek.de/var/rpg/storage/images/magazin/2015/02/die-anonymebox-von-pi3g-im-test/abbildung-6/15601-1-ger-DE/Abbildung-6_large.png)

> _Abbildung 6: Vor wenigen Jahren tropfelten die Daten noch mit geringer Geschwindigkeit durch das Tor-Netzwerk. Inzwischen lassen sich Datenraten im Mbit/s-Bereich erzielen._

![](http://www.raspberry-pi-geek.de/var/rpg/storage/images/magazin/2015/02/die-anonymebox-von-pi3g-im-test/abbildung-7/15604-1-ger-DE/Abbildung-7_large.png)

> _Abbildung 7: Sogar P2P-Filesharing-Downloads, wie hier mit Transmission, lassen sich bei Geschwindigkeiten von bis zu 1 Mbit/s uber das Tor-Netzwerk abwickeln._

Nicht jede Route durch die Tor-Schichten erlaubt allerdings solch hohe Bandbreiten. Da Tor die Route alle 10 Minuten andert, kommt es durchaus vor, dass sich zwischendurch kaum eine Webseite abrufen lasst. Je nach Exit-Node weigern sich ab und an auch einige Seiten oder Server, mit Ihrem anonymen Internetzugang zusammenzuarbeiten. Google blockiert zum Beispiel einige auffallige Tor-Knoten ([Abbildung 8](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test)), und auch viele IRC-Server lassen Verbindungen aus dem Tor-Netz nicht zu.

![](http://www.raspberry-pi-geek.de/var/rpg/storage/images/magazin/2015/02/die-anonymebox-von-pi3g-im-test/abbildung-8/15607-1-ger-DE/Abbildung-8_large.png)

> _Abbildung 8: Google sperrt zahlreiche Exit-Nodes des Tor-Netzwerks aus, da uber diese in der Vergangenheit Missbrauch getrieben wurde._

  


#### Verhaltensregeln fur Tor

Bevor Sie Tor aktiv nutzen, sollten Sie allerdings ein paar Grundregeln im Umgang mit dem Anonymisierungsdienst beherzigen: Bevor Sie sich mit dem Tor-Netzwerk verbinden, sollten Sie alle Programme beenden, die im Hintergrund Daten ins Internet ubertragen. Dazu gehoren zum Beispiel E-Mail-Anwendungen oder Instant-Messaging-Clients. Auch aus Webmailern wie Gmail und Outlook.com oder Social Networks wie Facebook sollten Sie sich ausloggen, sonst ließe sich nach wie vor eine Verbindung zwischen den von Ihnen besuchten Webseiten und Ihren Online-Accounts herstellen.

Zudem ist es sinnvoll, einen ansonsten nicht genutzten Webbrowser zu installieren und diesen so zu konfigurieren, dass er großtmogliche Privatsphare bietet - ahnlich wie es der vorkonfigurierte Tor-Browser macht. Ihr anonymer Browser sollte keinen Verlauf schreiben, Cookies spatestens beim Beenden loschen und Plugins wie Adobe Flash deaktivieren. In Firefox erreichen Sie dies in den _Einstellungen_ unter _Datenschutz_ | _Firefox wird eine Chronik niemals anlegen_ und unter _Add-Ons_ | _Plugins_ | _Shockwave Flash_ | _Nie aktivieren_.

Tor verschlusselt innerhalb des Serververbunds Ihre Daten - spatestens aber der Exit-Node konnte jedes unverschlusselt ubermittelte Datenpaket einsehen. Login-Daten und sogar Passworter waren fur unserios arbeitende Exit-Node-Betreiber eine leichte Beute. Daher sollten Sie darauf achten, wo immer moglich verschlusselte HTTPS-Verbindungen zu nutzen. Mit dem von der Electronic Frontier Foundation entwickelten Browser-Addon HTTPS Everywhere [[9]](http://www.raspberry-pi-geek.de/Magazin/2015/02/Die-AnonyMeBox-von-Pi3g-im-Test/\(offset\)/2) erzwingen Sie fur viele Webseiten eine Umleitung auf das verschlusselte Angebot.

#### Fazit

Die AnonyMeBox erweitert Ihr Netzwerk auf einfache Weise um einen anonymen Internetzugang. Mit einem Notebook mussen Sie sich lediglich in das WLAN der AnonyMeBox einloggen - schon bleiben Sie fur den Betreiber der aufgerufenen Webseite anonym. Um allerdings zu surfen, ohne jegliche Spuren zu hinterlassen, mussen Sie auch den Webbrowser entsprechend einrichten und sich an gewisse Verhaltensregeln halten - diese Arbeit nimmt Ihnen auch die AnonyMeBox nicht ab. (cla)

Dies gilt besonders fur mobile Gerate: Deren Internetverbindungen lassen sich zwar uber das WLAN der AnonyMeBox schnell durch das Tor-Netz jagen. Die Gerate tauschen jedoch fortwahrend Daten mit den Server-Diensten der Hersteller (also Google, Apple oder Microsoft) aus. Zumindest diese konnen also trotz Tor jederzeit eine Verbindung zwischen Ihnen und dem gerade genutzten Exit-Node herstellen. Fur anonymes mobiles Surfen sollten Sie daher auf einen entsprechenden Account auf Ihrem Gerat verzichten.

Pi3g bietet die Software der AnonyMeBox auf der Webseite auch zum Herunterladen an. Liegt ein Raspberry Pi ungenutzt bei Ihnen im Regal, verwandeln Sie ihn mithilfe der per NOOBS installierbaren Software in Ihre eigene AnonyMeBox, ohne dass Sie zwingend das Set des Herstellers kaufen mussen.

  1. Tor-Projekt: <https://www.torproject.org>
  2. Tails: <https://tails.boum.org>
  3. AnonyMeBox: <https://anonymebox.com/de/>
  4. Ipinfo.io: <http://ipinfo.io>
  5. Ipleak.net: <http://ipleak.net>
  6. Anonymizer des Chaos Computer Clubs: <http://www.ccc.de/de/anonymizer>
