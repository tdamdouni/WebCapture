# Zugriff auf den eigenen Raspberry Pi aus dem Internet

_Captured: 2019-03-15 at 18:46 from [buyzero.de](https://buyzero.de/blogs/news/zugriff-auf-den-eigenen-raspberry-pi-aus-dem-internet?omnisendAttributionID=email_campaign_5c8bd2b58653ed3ba4882f58&omnisendContactID=597763cf47fbc0f7fccab6d8&omnisendScopeID=59776357597ed775e8ab6865_2_15601473&utm_campaign=campaign%3A+Portfreigabe+Internet+%285c8bd2b58653ed3ba4882f58%29&utm_medium=email&utm_source=omnisend)_

![Zugriff auf den eigenen Raspberry Pi aus dem Internet](https://cdn.shopify.com/s/files/1/1560/1473/articles/001_2048x.jpg?v=1552665277)

# Einleitung

Oft realisiert man mit dem Raspberry Pi Projekte, die man auch aus dem Internet aufrufen mochte.

Beispielsweise eine Webseite mit Statusinformationen - Sensoren, Kameras (zum Beispiel mit MotionEyeOS), ... oder man mochte einen eigenen kleinen Webserver auf Raspberry Pi Basis realisieren, um zum Beispiel owncloud laufen zu lassen.

**Wie kann ich also auf den eigenen Pi aus dem Internet zugreifen?** Es folgt eine Anleitung fur Anfanger, ich bemuhe mich hier die Technik sehr ausfuhrlich zu erklaren und einige bequeme Moglichkeiten vorzuschlagen. Wer sich also schon gut auskennt kann gerne einiges der Erklarung (**Grundlagen**) uberspringen.

# Grundlagen

## Das DNS System

Wenn ich bspw. die Webseite [duckduckgo.com](https://duckduckgo.com) (auch "Domain" genannt) in den Webbrowser (zum Beispiel Google Chrome) eingebe (eine Suchmaschine die die eigene Privatsphare respektiert), verbindet sich mein Webbrowser zu einem sogenannten DNS Server (Domain Name System). Dieser Server, also spezialisierter Computer, ist dafur zustandig den von Menschen lesbaren Namen duckduckgo.com in eine sogenannte IP Adresse umzuwandeln.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/002_medium.jpg?v=1552664018)

## IP Adressen

Die IP Adresse ist eine Reihe von Zahlen die mit Punkten getrennt sind. Diese schaut fur **duckduckgo.com** beispielsweise wie folgt aus:

46.51.179.90

Ist also fur einen durchschnittlichen Menschen schwerer in Erinnerung zu behalten als der Domain Name, oder?

## IPv4 Adressen, IPv6 Adressen

Das (46.51.179.90) ist ubrigens eine sogenannte IPv4 IP Adresse. Es gibt nicht nur sehr viele Menschen die online sind, sondern auch noch viel mehr Gerate ("Stichwort IoT, Internet of Things"), die alle idealerweise eine eigene IP Adresse haben wollen. Wenn Sie horen, dass die IP Adressen knapp werden, ist das Problem dass im modernen Internet die maximal vier Milliarden moglichen IP Adressen in diesem IPv4 Format heutzutage nicht ausreichen.

Daher wurden IPv6 Adressen eingefuhrt:

2001:0db8:0000:0000:0000:ff00:0042:8329

Diese sind noch komplizierter zu merken, aber man konnte mit ihnen **[jedem einzelnen Atom der gesamten Menschheit**](https://www.reddit.com/r/theydidthemath/comments/2qxgxw/self_just_how_big_is_ipv6/) 7 IPv6 Adressen zuteilen. Oder jedem Millimeter in einer geraden Linie von einer Seite des gesamten Universums zur anderen 3,6 Milliarden IPv6 Adressen. Diese IPv6 Adressen werden uns also nicht ausgehen (Stand 2019).

Diese IP v4 und IP v6 Adressraume existieren unabhangig nebeneinander, ich kann beim DNS Server fur meine Domain (bspw. **www.duckduckgo.com**) beide Adresstypen abfragen (falls der Administrator der Domain beide hinterlegt hat).

Im Moment werden von den meisten Nutzern und von fast allen Webseiten / Webservices noch die "herkommlichen" IPv4 Adressen verwendet und unterstutzt, daher spreche ich im folgenden nur von diesen IP-Adressen.

## Geografische Vergabe von IP Adressen

Alle Gerate die im Internet miteinander kommunizieren mochten benotigen eine IP Adresse. Genauso wie die Postadressen mussen diese Adressen einzigartig sein, damit die Nachrichten (bspw. Resultate meiner Google bzw. DuckDuckGo Suche) richtig zugestellt werden. Wie bereits erwahnt, da heutzutage sehr viele Menschen online sind, und auch viele Gerate eine eigene IP Adresse haben mochten, ist das aber leider nicht moglich. Zumindest nicht direkt.

IP-Adressen werden "geografisch" vergeben. D.h. in Afrika gibt es Adressen die anders beginnen als in Europa, in Leipzig gibt es andere IP-Adressen als in Munchen. Anhand der IP-Adresse kann man mit einer gewissen Genauigkeit bestimmen wo sich ein Mensch, Computer, oder Gerat befindet. Beispielsweise:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/003_large.png?v=1552664050)

![](https://cdn.shopify.com/s/files/1/1560/1473/files/004_large.png?v=1552664088)

In meinem - diesem - Fall ist die Genauigkeit nicht 100 %, ich bin deutlich naher an Markranstadt dran wahrend ich das schreibe - aber die Stadt in der ich mich befinde wurde schon mal korrekt bestimmt.

## Lokale IP Adressen, Router und Gateway

Wie bereits gesagt benotige ich wenn ich eine Webseite aufrufen mochte eine IP-Adresse.

Anfangs aus der Lust am Sparen der IP Adressen geboren, spater aus anderen (kommerziellen Grunden? oder geht es vielleicht gar um den Schutz unserer Privatsphare?) fortgefuhrt, weisen die Internet Provider (bspw. Vodafone, Telekom, Kabel Deutschland, M-NET, und wie sie alle heißen) jedem Haushalt bzw. Betrieb eine standig wechselnde "offentliche" IP-Adresse aus einem bestimmten Adressraum (stadtabhangig, siehe oben) zu. Damit kann nun ein Gerat "online" gehen. Üblicherweise ist das der Router - das Gerat was man vom Provider erhalt, also beispielsweise in Deutschland oft die Fritz!Box.

Die Aufgabe des Routers ist, die Gerate im lokalen Netzwerk mit dem Internet zu verbinden.

Nachdem jedes Gerat das mit anderen Computern (Servern, z.B. dem Webserver von duckduckgo.com) im Internet kommunizieren mochte eine IP-Adresse benotigt, haben auch die Gerate in unseren lokalen Heimnetzwerken alle eine IP-Adresse. Diese IP-Adresse stammt allerdings aus einem besonderen dafur reservierten Bereich:

  * 0.0.0 - 10.255.255.255 oder
  * 16.0.0 - 172.32.255.255 oder
  * 168.0.0 - 192.168.255.255

Vielleicht erkennen Sie die ubliche IP-Adresse der Fritz!Box hier wieder: 192.167.178.1?

In den meisten Fallen vergeben die Router zu Hause / auf der Arbeit auch diese lokalen oder "privaten" IP Adressen mit einem Service der sich DHCP nennt. Ich muss nichts konfigurieren - ich stecke einfach meinen Computer an das Netzwerk, und er verbindet sich mit dem Router und dann mit dem Internet.

Mein lokaler Computer, beispielsweise, auf dem ich den Web Browser ausfuhre hat naturlich auch eine IP Adresse von meinem Router bekommen.

In meinem Fall (Desktop Windows Rechner) beispielsweise 192.168.1.202

![](https://cdn.shopify.com/s/files/1/1560/1473/files/005_large.png?v=1552664127)

Wie man in dem Screenshot sieht ist der IPv4 **Standardgateway** 192.168.1.1

Was ist ein Gateway? Ein Gateway ist eine Moglichkeit, in ein anderes Netzwerk zu kommen. Der Computer oder das Gerat mit der IP Adresse 192.168.1.1 (in meinem Fall) - ublicherweise der Router - kann in andere IP-Adressbereiche vermitteln. Beispielsweise auf die vorhin als Beispiel angefuhrte IP Adresse von Duck Duck Go (46.51.179.90).

Wenn ich also die Webseite aufrufe, verbindet sich mein Computer mit dem Router (der sich selbst per DHCP als Gateway eingetragen hat), und dieser wiederum kann die Anfrage an die Webseite weiterleiten.

Es ist ubrigens auch moglich IP Adressen "statisch" zu konfigurieren. Das heißt, man weist dem Computer lokal eine feste IP Adresse zu, die sich in unserem eigenen Netzwerk nicht andert. Das ist ublicherweise eine fortgeschrittene Konfiguration, aber fur unsere Raspberry Pi's vielleicht sinnvoll, damit wir uns einfach zu ihnen verbinden konnen und sie spater ins Internet freigeben konnen (siehe Informationen weiter unten).

## NAT = Network address translation, TCP und UDP, Ports

Und ist Ihnen daran das Problem aufgefallen? Wir wissen zwar mit welchem Kommunikationspartner wir sprechen wollen, aber wenn der Router einfach unsere lokale IP Adresse weitergibt - also bspw. meine 192.168.1.202, dann weiß der Server im Internet nicht welcher Computer aus den Myriaden von Heimnetzwerken das ganze angefragt hat. Diese lokalen / privaten Adressen sind ja mehrfach im Einsatz, da man sonst dem IPv4 Adressmangel nicht mehr Herr werden konnte.

Um das Problem zu losen wurde eine Technologie namens NAT erfunden. Das steht fur Network address translation. Der Router nimmt die Anfragen von den lokalen Computern, Smartphones, Smart TVs und so weiter, entgegen, und bearbeitet diese so dass eine Zuordnung eindeutig moglich wird.

Ein Feature von TCP und UDP ist dabei hilfreich fur uns. TCP und UDP sind die zwei Kommunikations-Protokolle die besonders haufig im Internet eingesetzt werden. Wenn ich beispielsweise ein YouTube Video abspiele, werden die Daten vom Video in vielen vielen TCP-Paketen transportiert.

Diese TCP bzw. UDP Pakete haben jeweils eine Quell-(IP-)Addresse und Quell-Port, sowie eine Ziel-(IP-)Adresse und einen Ziel-Port. Der Router kann jetzt einfach verschiedene Quellports fur verschiedene Computer in seinem Netzwerk nutzen, um die Anfragen spater wieder richtig zuordnen zu konnen. Auch wenn YouTube Videos von zwei Computern aus angeschaut werden.

Spielen wir das fur eine Anfrage durch:

Ich rufe ein YouTube Video von Madonna auf, bspw. "Hung Up": <https://www.youtube.com/watch?v=EDwb9jOVRtU>

Mein Computer spricht mit einem DNS Server, findet die IP Adresse von YouTube heraus (z.B. 216.58.206.14) . Er schickt dann mittels des Routers eine Anfrage in Form eines oder mehrerer TCP Pakete an den Server von YouTube. Als Quell-IP gibt mein Computer seine eigene IP an, als Port einen beliebigen Port, bspw. 38556. In dem Paket ist in irgendeiner Form enthalten was mein Computer von dem Server will (also dass er die Daten fur das Video zuruckgibt), aber wie genau das geht sprengt den Rahmen dieses Artikels. Es funktioniert offensichtlich :-)

Ich mochte youtube.com aufrufen, also beispielsweise ist 216.58.206.14 die Ziel IP. (Große Seiten verteilen Anfragen oft uber viele Server und IPs). Der Ziel Port ist fur https (verschlusselter Webseitenaufruf) standardmaßig 443.

Der Router schreibt das TCP Paket um. Er wahlt einen beliebigen Port als Quellport aus, zum Beispiel 2020, die Quell-IP ist meine vom Provider zugewiesene offentliche IP, bspw. 95.90.37.99.

Der Server beantwortet meine Anfrage an den Quellport den ich ausgewahlt habe. Der Router erhalt diese Anfrage, und hat sich gemerkt dass er eine Antwort unter diesem Port an meinen Computer weiterleiten soll.

Er schreibt das Antwort-Paket mit der IP meines Computers um, und verschickt es im lokalen Netzwerk. Das Video kann jetzt dargestellt werden (oder ein winzig kleiner Teil davon, ein Video besteht aus Millionen von Paketen).

Da es bis zu 65.536 Ports gibt, kann der Router mehrere Anfragen mehrerer Computer / Endgerate aus dem lokalen Netzwerk gleichzeitig verarbeiten.

Übrigens funktioniert das ganze intern fur die Anfragen unserer Rechner an die DNS Server genauso. DNS nutzt primar UDP, in manchen Fallen aber auch TCP Pakete. Die Anfrage/Antwort-Pakete werden vom Router "genat'ed", falls ein externer DNS Server eingestellt ist. Mein Computer kommuniziert nicht direkt mit dem Internet - kann er auch gar nicht, falls er nicht zum Beispiel direkt an das DSL Modem angeschlossen ist.

In den meisten Fallen ist der Router als Nameserver (DNS Server) eingestellt, der dann wiederum anfragen die er nicht gespeichert hat an Internet-Server weitergibt. Das Pi Hole funktioniert beispielsweise auf dem Prinzip, dass es DNS Anfragen filtriert und selektiv Server blockiert die Werbung ausspielen.

## DS-Lite-Hinweis

Es ist wichtig zu wissen dass nicht alle IP-v4 Adressen die vom Provider fur mein Netzwerk / meinem Router zugewiesen werden wirklich "offentlich" sind. Mit anderen Worten, die IP-Adressen sind so knapp dass manche Provider dazu ubergegangen sind auf ihrer Seite ebenfalls ein NAT zu machen. D.h. ich erhalte in Wirklichkeit auch nur eine End-Adresse aus dem privaten Netzwerk das der Provider betreibt, die Daten werden zweimal ubersetzt / genatted. Einmal von meinem Router fur das Heimnetzwerk, einmal vom Router des Providers fur das Internet.

Das ganze wird als Dual-Stack Lite bezeichnet und ist eine Übergangstechnologie "bis wir komplett auf IPv6 umsteigen".

Der große Nachteil von DS Lite ist, dass ich nur noch offentliche IPv6 Adressen habe, und keine eigene IPv4 Adresse, auch keine "dynamische". Ich kann damit keine Ports in das Internet freigeben.

# Freigabe von Ports des Raspberry Pi fur das Internet

## Einleitung

**Nun mochten wir das ganze anders herum aufsetzen. Wir mochten aus dem Internet auf den Raspberry Pi zugreifen, um zum Beispiel den aktuellen Wert eines Sensors per Browser aufrufen zu konnen.**

Wenn ich uber den GPIO Port einen Sensor auslese, kann ich zum Beispiel in Python einen kleinen Webserver bauen (wie das geht sprengt leider auch den Rahmen dieses Artikels), der den Sensorwert ausgibt. Oder gleich ein Diagramm im Zeitverlauf. Ich kann die Daten auch erst nach einem Login bereitstellen - wobei hier empfehlenswert ware, eine verschlusselte https-Verbindung, unter Port 443 anzubieten bzw. zu erzwingen (da Passworter ubertragen werden).

Port 80 ist der Standard-Port fur http-Verbindungen (unverschlusselte Webseiten). Mein Programm stellt also am Raspberry diese Daten unter diesem Port bereit.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/006_large.png?v=1552664185)

Der Beispielscreenshot zeigt den Zugriff auf den Pi aus dem lokalen Netzwer - ein Webserver lauft auf Port 80, mein Pi hat die IP 192.168.1.57.

Ich kann die IP auf dem Pi herausfinden mittels **ip -4 addr show**:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/007_large.png?v=1552664207)

Viele weitere Ports sind fur andere Anwendungen interessant, beispielsweise Port 22 fur SSH (Terminalverbindungen zum Raspberry Pi, ...), Port 21 fur FTP, 587 fur SMTP, ...

Ich kann ohne weiteres, sofern ich weiß welche IP-Adresse der Raspberry Pi hat, im lokalen Netzwerk diese IP aufrufen. Der Browser offnet standardmaßig bei Eingabe von **http:// 192.168.1.57** (in meinem Fall - bei Ihnen sicher anders) die Verbindung zu Port 80. Wie kriege ich das aber von außen hin? Wie kann ich den Webservice auf meinem Raspberry Pi fur das Internet freigeben?

Dazu gibt es zwei grundsatzliche Moglichkeiten:

## DynDNS Service & Ports offnen

Das ist die klassische Methode, die mit mehr Aufwand verbunden ist, und in vielen Fallen heute leider nicht mehr funktioniert (da Sie keine "echte" eigene dynamische IPv4 mehr bekommen, bzw. Ihr Router nicht in der Lage ist Ports zu offnen).

Beispielsweise kann ich bei Vodafone / Kabel Deutschland mit dem von ihnen gestellten Router keine Ports von innen aus offnen, und muss auf die zweite Methode ausweichen. Es lohnt sich daher, den letzten Schritt (Freigabe der Ports) als erstes im Router anzuschauen, bzw. bei dem eigenen Internetprovider zu erfragen ob man eine dynamische IPv4 Adresse hat, oder einen DS-Lite oder ahnlichen Anschluss hat.

### Dynamischer DNS Service

Da die meisten Provider, wie oben erwahnt, uns wechselnde IP Adressen zuweisen, die man sich nicht merken / nicht vorhersagen kann, nutzen wir einen speziellen Service der uns eine eigene Subdomain gibt, die auf unsere jeweils aktuelle IPv4 Adresse fuhrt.

Beispielsweise ist NO-IP ein popularer Service der dafur benutzt wird. Im folgenden zeige ich, wie man damit seine eigene dynamische IP Adresse auf eine "statische" Subdomain (d.h. menschenlesbare Internet-Adresse) von No-IP legen kann.

No-IP bietet eine kostenlose Option, bei der man allerdings den DNS Namen alle 30 Tage neu bestatigen muss.

Legen Sie sich hier einen Account an, und notieren Sie sich die Zugangsdaten, sowie die ausgewahlte Subdomain. Diese werden gleich benotigt.

(Bitte beachten Sie, dass man nur einen kostenlosen Account anlegen darf gemaß den Geschaftsbedingungen von No-IP).

Nun installieren wir auf dem Pi den Dynamic Update Client (DUC) von No-IP.

Wir mussen auf dem Raspberry Pi dazu einige Kommandozeilen-Operationen durchfuhren, gemaß diesem Artikel:

<https://www.noip.com/support/knowledgebase/install-ip-duc-onto-raspberry-pi/>

  * wir verbinden uns per SSH zum Pi, oder nutzen das lokal angeschlossene Keyboard und Maus und offnen ein Terminal Fenster
  * anschließend geben wir folgende Kommandos ein:

**mkdir /home/pi/noip**

**cd /home/pi/noip**

**wget http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz**

**tar vzxf noip-duc-linux.tar.gz**

Das nachfolgende Kommando muss angepasst werden, wenn sich die Version von DUC geandert hat (man sieht in welches Verzeichnis ausgepackt wird anhand der Ausgabe von tar)

![](https://cdn.shopify.com/s/files/1/1560/1473/files/008_large.png?v=1552664243)

**cd noip-2.1.9-1**

Jetzt installieren wir das Programm:

**sudo make**

(es ist normal, dass hier einige Warnungen ausgegeben werden)

**sudo make install**

![](https://cdn.shopify.com/s/files/1/1560/1473/files/009_grande.png?v=1552664277)

Nach Eingabe von **sudo make install** muss man den No-IP account Benutzernamen und das Passwort angeben. Beantworten Sie die Fragen, die DUC an Sie stellt. Fur das Update-Intervall sollten **mindestens** 5 Minuten angegeben werden. Die Eingabe von 5 entspricht 5 Minuten, die Eingabe von 30 einem Updateintervall von 30 Minuten. (Eine Angabe von 5 Minuten ist empfehlenswert um das Zeitfenster nach Zwangs-IP-Wechsel durch den Provider klein zu halten, in dem man nicht auf die richtige IP zugreift.)

Anschließend starten wir den Service:

**sudo /usr/local/bin/noip2**

Wir verifizieren dass der Service korrekt lauft, mittels:

**sudo noip2 -S**

**![](https://cdn.shopify.com/s/files/1/1560/1473/files/010_grande.png?v=1552664321)**

Hinweis: standardmaßig wird der Service bei reboot nicht automatisch wieder gestartet.

Daher konnen wir das mit folgenden Kommandos nachrusten:

**sudo nano /etc/systemd/system/noip2.service**

hier geben wir folgendes ein:

[Unit]

Description=No-ip.com dynamic IP address updater

After=network.target

After=syslog.target

[Install]

WantedBy=multi-user.target

Alias=noip.service

[Service]

ExecStart=/usr/local/bin/noip2

Restart=always

Type=forking

Wir speichern mit Ctrl + O, und beenden Nano mit Ctrl + X.

Wir aktivieren den Service:

**sudo systemctl enable noip2.service**

Der Service kann jetzt mittels

**sudo systemctl start noip2.service**

gestartet werden. (manchmal wird zusatzlich ein _sudo systemctl daemon-reload_ benotigt). Der noip2 Daemon wird jetzt automatisch mit dem Pi gestartet, und er aktualisiert unsere bei No-IP hinterlegte IP Adresse.

Referenzen:

Wichtig: bei No-IP muss bei kostenlosen Accounts die Subdomain alle 30 Tage aktualisiert werden.

### Raspberry Pi statische IP Adresse zuweisen

Ref: <https://raspberrypi.stackexchange.com/questions/37920/how-do-i-set-up-networking-wifi-static-ip-address>

Der Pi benotigt eine statische IP Adresse, damit der Router im nachsten Schritt korrekt zur richtigen Weiterleitung des Ports eingestellt werden kann. (Sonst wurde evtl. der Port mit der Zeit an einen anderen Computer weitergeleitet werden, was naturlich ein Sicherheitsrisiko darstellt, und nicht im Sinne des Erfinders ist!)

Wir analysieren zunachst die IP die per DHCP automatisch eingestellt wurde:

**ip -4 addr show | grep global**

**![](https://cdn.shopify.com/s/files/1/1560/1473/files/012_grande.png?v=1552664404)**

Bei bestehender WLAN Verbindung wird statt eth0 wlan0 angezeigt, bzw. es konnten zwei Zeilen auftauchen.

192.168.1.57 ist in meinem Fall die IP des Pis, und /24 die Netzwerk Große.

192.168.1.255 ist die Broadcast Adresse des lokalen Netzwerks.

Nun finden wir die IP Adresse des Routers heraus:

**ip route | grep default**

die Standard-Route ist via 192.168.1.1, was die IP des Routers ist.

Und noch den Nameserver (lokaler DNS Server):

cat /etc/resolv.conf

![](https://cdn.shopify.com/s/files/1/1560/1473/files/014_grande.png?v=1552664460)

Der Nameserver ist 192.168.1.1

Um die statische IP einzurichten, beispielsweise 192.168.1.6, editieren wir /etc/dhcpcd.conf:

**sudo nano /etc/dhcpcd.conf**

und bearbeiten die Eintrage weiter unten in der Datei, dass sie so aussehen:

# Example static IP configuration:

interface eth0

static ip_address=192.168.1.6/24

static routers=192.168.1.1

static domain_name_servers=192.168.1.1 8.8.8.8

Hier mussen bei routers die IP Adresse des Routers (s.o.) eingetragen werden, und bei domain_name_servers ebenso. 8.8.8.8 ist Google's DNS Server, und kann zusatzlich eingetragen bleiben. Wichtig ist außerdem, dass der Adress-Pool des DHCP Servers des Routers außerhalb (bspw. oberhalb) dieser neuen statischen IP Adresse ist. Diesen Pool kann man im Webinterface des Routers nachschauen. Bei mir bspw:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/015_grande.png?v=1552664506)

Nach einem Neustart hat der Pi dann die neue statische IP Adresse:

sudo reboot

### Freigabe des Ports in das Internet

Das Vorgehen zur Freigabe in das Internet hangt von Router zu Router ab.

Es muss ein offentlicher Port auf der Box (bspw. Port 80 ) auf den von uns vorbereiteten Port des Raspberry Pis im lokalen Netzwerk weitergeleitet werden.

Ich verweise hier beispielhaft auf folgenden Artikel:

<https://avm.de/service/fritzbox/fritzbox-7590/wissensdatenbank/publication/show/893_Statische-Portfreigaben-einrichten/>

**Bei DS-Lite Anschlussen ist das leider nicht moglich.**

An meinem Anschluss habe ich es beispielsweise nicht geschafft, die Ports freizugeben.

## Weiterleitung mittels eines Services

Das ist die einfachere Variante, und die einzige die bei DS-Lite Anschlussen moglich ist (die keine echte IPv4 Adresse an Endkunden vergeben).

Bei dieser Variante verbindet sich der Raspberry Pi mit einem Anbieter, der die Verbindung auf seinem Server in das Internet freigibt. Es gibt mehrere verschiedene Anbieter, ich mochte hier zwei vorstellen die auch in begrenztem Maße kostenlosen Service mit anbieten.

Es ist keine Anlage von einem No-IP Account notig, die Subdomain wird in diesem Fall von den Services mit gestellt.

**Wichtig ist hier ebenfalls vorsichtig vorzugehen, und nur die Ports freizugeben die man freigeben mochte.** Standardmaßig ist beim Raspberry Pi fur den Nutzer "**pi**" das Passwort "**raspberry**" eingestellt. Da der Nutzer pi per sudo Administratorrechte auf dem Pi wahrnehmen kann, ist die Freigabe des SSH Zuganges ohne ein sicheres Passwort eine massive Sicherheitslucke.

Ich bespreche hier das Szenario, eine Webseite die auf dem Pi gehosted wird (bspw. mit Anzeige von ausgelesenen Sensordaten) freizugeben. Auch hier sollte man entsprechend mehr auf Absicherung achten, als man es beispielsweise im eigenen Heimnetzwerk tun wurde - ggf. konnen Sicherheitslucken von Angreifern ausgenutzt werden, um Zugriff auf das gesamte Heimnetzwerk zu bekommen.

### Dataplicity

Dataplicity verspricht, dass man den eigenen Pi "von uberall steuern" kann.

Die Freigabe erfolgt mittels eines Python Programms das als "PEX" Datei ausgeliefert wird (also eine Art virtueller Umgebung fur Python).

![](https://cdn.shopify.com/s/files/1/1560/1473/files/016_grande.png?v=1552664556)

Das Skript wird nach Eingabe der e-Mailadresse personalisiert, vermutlich um Konfigurationsarbeit sparen zu konnen:

Nun muss man auf dem Raspberry Pi unter der Konsole **die von Dataplicity angegebene Codezeile ausfuhren.** Das fuhrt zu folgender Ausgabe:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/018_grande.png?v=1552664629)

unter dem Link erhalt man sofort Zugriff auf eine Konsole, mit einem Benutzer dataplicity:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/019_grande.png?v=1552664664)

> _Rechts unten erhalt man folgende Nachricht:_

Hi there,

To run commands as superuser, you must first switch to an account with sudo privileges.

On a Raspberry Pi, you can usually do this by running 'su pi', and entering the 'pi' account password which, unless you have changed it, is normally "raspberry". From there you can run sudo as normal.

For more information, here is the tutorial: <http://docs.dataplicity.com/docs/superuser/>

Best,

Elliot.

**Spatestens jetzt sollte man das Passwort fur den Nutzer pi andern**.

Sonst hat man eine aus dem Web erreichbare Konsole, aus der der Nutzer zum root auf dem Pi werden kann, und somit Zugriff auf das lokale Netzwerk und am pi angeschlossene Gerate erhalt.

Rechts erhalt man einen Überblick uber den momentanen Speicherplatz, und kann per einem Klick den Port 80 auf dem Pi freigeben.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/020_grande.png?v=1552664713)

Freigabe von Port 80:

Und ich kann jetzt bequem auf den Webservice auf dem Pi zugreifen:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/022_grande.png?v=1552664769)

Mehr muss man nicht machen, hier ist noch das Tutorial von dataplicity zu dem Thema:

<https://docs.dataplicity.com/docs/host-a-website-from-your-pi>

Nginx ermoglicht auch als Reverse Proxy zu arbeiten, und weitere Services unter Port 80 zu kombinieren.

Dataplicity ist aus meiner Sicht einfach und empfehlenswert! Ich finde es vor allem super, dass man nicht erst Nutzer & Passwort anlegen muss, sondern quasi sofort starten kann.

Im Backend von Dataplicity sieht man die eigenen Raspberry Pi's und kann per Klick auf eine Konsole zugreifen:

Das einzige Problem das ich mit Dataplicity hatte war das eintragen meines initialen Passwortes im Webinterface - ich kannte das fur mich hinterlegte Passwort nicht, da ich es nie angelegt hatte. Daher musste ich mich ausloggen, und das Passwort mit dem _I forgot my password_ Link zurucksetzen:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/024_grande.png?v=1552664869)

![](https://cdn.shopify.com/s/files/1/1560/1473/files/025_grande.png?v=1552664897)

Nachdem ich das Passwort gesetzt habe, muss ich mich unter dem speziellen Link der beim Setup ausgegeben wird erst anmelden. Er scheint also nur fur die erste Anmeldung zu funktionieren.

Der Dataplicity Client (auf dem Raspberry Pi) **lauft auch nach Neustart**, ohne dass man weitere Konfiguration tatigen musste. Man sollte das im Hinterkopf behalten, falls man die Webseite nur fur eine Sitzung freigeben mochte.

**Wie schaut es mit den Kosten fur Dataplicity aus?**

Der Gratis-Plan auf ein Gerat beschrankt, man erhalt ein Terminal und kann SSH, VNC und Port 80 weiterleiten. Man kann dabei bis zu 512 MB pro Tag mit bis zu 10 MBps+ ubertragen, daruber hinaus 1.5 Mbps. Perfekt fur Hobbyisten, und vor allem komplett gratis!

3 $ pro Monat und Gerat kostet "Dataplicity Standard" mit weiteren Features, oder wenn man mehr als ein Gerat haben mochte, wobei es ab dem 51sten Gerat Rabatt gibt. "Dataplicity Pro" kostet 4 $ pro Gerat pro Monat, ebenfalls mit Staffelung ab dem 51sten Gerat. Der großte Vorteil des Pro Accounts ist dass man sein eigenes Prefix fur das "Wormhole" aussuchen kann (so heißt die Weiterleitung auf Port 80 vom Raspberry Pi bei Dataplicity).

Fur die meisten Anwender durfte Dataplicity Standard ausreichend sein, wenn man nicht mit dem Gratis-Plan bereits hinkommt.

**Dataplicity deinstallieren**

Eine Anleitung dafur findet man hier: <https://docs.dataplicity.com/docs/uninstalling>

### Pagekite

Pagekite ist primar darauf ausgerichtet, Webseiten einfach im Internet freizugeben. Es unterstutzt neben Linux auch Windows und Mac Systeme. Hier zeige ich den Weg fur den Raspberry Pi.

Wir offnen die Konsole, und geben folgendes ein (als Nutzer pi):

**sudo apt-get install pagekite**

**pagekite 80 _meinprefix_.pagekite.me**

Dabei sollten Sie meinprefix selbst aussuchen. Ich habe mich hier fur das Prefix **gagarin**, zu Ehren des ersten Astronauten der Welt entschieden.

Wir erhalten einen interaktiven Dialog:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/026_grande.png?v=1552664936)

![](https://cdn.shopify.com/s/files/1/1560/1473/files/027_grande.png?v=1552664969)

Durch Eingabe der e-Mailadresse meldet man sich bei pagekite an.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/028_grande.png?v=1552665004)

Nach Bestatigung startet pagekite:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/030_grande.png?v=1552665051)

Jetzt kann man einfach auf die Webseite unter der ausgesuchten Subdomain zugreifen:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/031_grande.png?v=1552665084)

Man sollte innerhalb von 15 Minuten den Account mit dem Link aus der zugeschickten e-Mail bestatigen, sonst wird der "Kite" (also die Web-Freigabe) beendet. Das ist um Mißbrauch des Service zu verhindern.

Negativ fallt mir auf: Pagekite schickt das Passwort im Klartext per e-Mail. Das ist aus Security-Sicht nicht gut, und sollte gleich geandert werden. Das Webinterface ist etwas altbacken und unubersichtlich.

Beenden kann man den Kite durch drucken von **Ctrl + C **(D.h. Strg und C). Eine Kontrolle unter gagarin.pagekite.me zeigt, dass tatsachlich der Kite / die Webfreigabe abgeschaltet wurde:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/032_grande.png?v=1552665114)

Pagekite.net hat ein Wiki mit vielen Tipps, unter anderem wie man per CNAME die eigene Domain auf den richtigen Server zeigen lassen kann:

Man sollte sich auch mit einigen Sicherheitstipps und Moglichkeiten von Pagekite (z.B: Passwortschutz) vertraut machen:

Um pagekite das nachste mal zu starten, kann man einfach

**pagekite**

eingeben, die Einstellungen werden aus der vorher erstellten Datei gelesen.

Hilfe erhalt man online, und durch eingabe von

**pagekite --help**

Um pagekite im Hintergrund laufen zu lassen, rufen wir folgendes auf:

**pagekite --daemonize**

Nach einem Neustart muss pagekite allerdings neu gestartet werden. Um es automatisch zu starten, legen wir (als User pi, falls pagekite als User pi konfiguriert wurde wie von mir vorgeschlagen) eine crontab Datei an:

**crontab -e**

Hier fugen wir folgende Zeile hinzu:

@reboot pagekite --daemonize &

pagekite wird jetzt mit den Voreinstellungen (in der Datei /home/pi/.pagekite.rc ) bei jedem Systemneustart ausgefuhrt. Um es wieder zu entfernen, loscht man diese Zeile wieder aus der Crontab (mit **crontab -e** bearbeitet man die Crontab jeweils).

Idealerweise konnte man einen komplett eigenen Nutzer fur pagekite hinzufugen, der kein sudoer ist, und die crontab Datei dort erstellen.

pagekite ist fur Anfanger vielleicht etwas schwieriger, vor allem um eine dauerhafte Freigabe zu erhalten. Es richtet sich an ein "technischeres" Publikum. Die Online Dokumentation ist nicht besonders aufgeraumt, ich konnte nicht auf Anhieb herausfinden wie man es dauerhaft freigibt (daher habe ich es weiter oben fur Sie aufgeschrieben.)

Positiv ist gegenuber Dataplicity, dass man sich sein prefix von Anfang an selbst aussuchen kann (und nicht den 4 $ Plan nehmen muss :-)) Auch kann man andere Ports freigeben.

Dataplicity hat gegenuber Pagekite den Vorteil, dass der Zugriff auf das Wormhole von Anfang an verschlusselt erfolgt (d.h. Dataplicity baut eine https Verbindung). Das ist mit pagekite auch moglich, allerdings musste man sich hier vermutlich um Zertifikate etc. kummern, und den Port 443 (https) freigeben.

**Zu den Kosten:**

Pagekite bietet gegenuber Dataplicity keinen dauerhaften kostenlosen Service fur alle fur ein Gerat. Man erhalt eine Trial-Periode fur ein Kite (d.h. eine Web-Freigabe) im Laufe von 31 Tagen, und kann insgesamt ca 2,5 GB ubertragen.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/034_large.png?v=1552665175)

Es hat einen interessanten "Pay what you want" Ansatz:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/035_grande.png?v=1552665193)

Je mehr man zahlt, desto mehr erhalt man (maximal 12 Monate Service, aber das Datenvolumen steigt auf bis zu 363 GB).

Es gibt auch Abo-Plane, bei denen man ab 5.99 $ pro Monat dabei ist:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/036_grande.png?v=1552665219)

Damit kann man auch mehrere Kites starten.

## Yaler.net

Ich will **[Yaler.net](https://Yaler.net) **nur kurz am Rande erwahnen. Diese Plattform bietet zwar keinen kostenlosen Testaccount oder Testperiode, allerdings ist der Preis bei CHF 10 netto pro Jahr (~ 8,81 € im Moment zzgl. Mehrwertsteuer) sehr gunstig.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/037_grande.png?v=1552665249)

Die Raspberry Pi Foundation listet auf Ihrer Seite noch einige weitere Alternativen auf, von denen ich Dataplicity (als meiner Meinung nach das Verstandlichste) bereits ausfuhrlich vorgestellt habe:

https://www.raspberrypi.org/documentation/remote-access/access-over-Internet/

# Fotos:

Photo by Ben White on Unsplash

[https://unsplash.com/photos/gEKMstKfZ6w?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText](https://unsplash.com/photos/gEKMstKfZ6w?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

Photo by Thomas Jensen on Unsplash

[https://unsplash.com/photos/qTEj-KMMq_Q?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText](https://unsplash.com/photos/qTEj-KMMq_Q?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

## Hinterlassen Sie einen Kommentar

Bitte beachten Sie, dass Kommentare vor der Veroffentlichung freigegeben werden mussen
