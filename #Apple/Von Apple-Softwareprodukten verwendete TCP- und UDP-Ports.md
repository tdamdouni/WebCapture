# Von Apple-Softwareprodukten verwendete TCP- und UDP-Ports

_Captured: 2015-10-23 at 15:46 from [support.apple.com](https://support.apple.com/de-de/HT202944)_

Dieser Artikel beschreibt die TCP- und UDP-Ports, die von Apple-Produkten wie zum Beispiel OS X, OS X Server, Apple Remote Desktop und iCloud verwendet werden. Viele davon werden haufig als "typische" Ports bezeichnet.

## Von Apple-Produkten verwendete Ports

Der unten stehenden Tabelle konnen Sie die TCP- und UDP-Ports entnehmen, die von Apple-Produkten verwendet werden. Der Netzwerkadministrator benotigt diese Informationen, um sicherzustellen, dass Ihr Computer oder Gerat eine Verbindung zu Diensten wie der [automatischen Softwareaktualisierung](http://support.apple.com/kb/HT1338?viewlocale=de_DE) oder dem App Store herstellen kann. Um zu erfahren, was ein TCP- oder UDP-Port ist, lesen Sie den Abschnitt "IP-Ports" des Artikels [OS X: Was ist ein Port?](http://support.apple.com/kb/HT4634?viewlocale=de_DE)

Nicht alle der genannten Ports und Dienste werden von allen Softwareprodukten verwendet. Einige Programme verwenden mehrere Ports und sind dementsprechend mehrfach aufgefuhrt. Netzwerkadministratoren konnen zusatzlich zu den Informationen in diesem Artikel auch Programme fur die Port-Überwachung verwenden, wenn sie Entscheidungen bezuglich der Konfiguration von Firewalls oder ahnlichen Systemen treffen mussen. Beachten Sie, dass in Mac OS X 10.5 und neuer eine [Programm-Firewall](http://support.apple.com/kb/HT1810?viewlocale=de_DE) integriert ist, die sich von einer portbasierten Firewall unterscheidet.

Dieser Artikel wird regelmaßig aktualisiert und enthalt die Informationen, die zum Zeitpunkt der Veroffentlichung verfugbar waren. Dieses Dokument soll als Kurzreferenz dienen und sollte daher nicht als vollstandig betrachtet werden. In der Tabelle aufgefuhrte Apple-Produkte sind Beispiele fur die am haufigsten verwendeten Produkte, stellen jedoch keine umfassende Liste dar.

## Informationen zu dieser Tabelle

In der Spalte "Dienst- oder Protokollname" sind Dienste aufgefuhrt, die bei der [Internet Assigned Numbers Authority](http://www.iana.org/) registriert sind, es sein denn, es wird der Hinweis "unregistrierte Nutzung" gegeben. Die Namen der Apple-Produkte, die diese Dienste oder Protokolle verwenden, sind in der Spalte "Verwendet von/Zusatzinformationen" angegeben.

In der Spalte "RFC" ist die Nummer des Request For Comment-Dokuments aufgefuhrt, das den speziellen Dienst oder das Protokoll definiert und als Referenz verwendet werden kann. RFC-Dokumente werden von [RFC Editor](http://www.rfc-editor.org) gepflegt. Wenn ein Protokoll von mehreren RFCs definiert wird, wird hier nur ein RFC aufgefuhrt.

Einige Dienste verwenden moglicherweise zwei oder mehr Ports. Wenn Sie ein Produkt in dieser Liste gefunden haben, sollten Sie nach dessen Namen suchen (Befehlstaste-F) und dann die Suche wiederholen (Befehlstaste-G), um alle Stellen zu finden, an denen das Produkt aufgefuhrt ist. Ein VPN-Dienst kann beispielsweise bis zu vier verschiedene Ports verwenden (500, 1701, 1723 und 4500).

Einige Firewalls ermoglichen eine selektive Konfiguration von UDP- und TCP-Ports mit derselben Nummer, sodass es wichtig sein kann, welcher Port-Typ konfiguriert wird. NFS kann z. B. die Ports TCP 2049 und UDP 2049 sowohl gemeinsam als auch getrennt verwalten. Wenn Ihre Firewall keine solchen speziellen Angaben ermoglicht, betrifft die Änderung an einem Port vermutlich beide Typen.

Die Ausgabe von Terminal-Befehlen kann die Portnummer durch die Bezeichnung ersetzen, die unter "/etc/services" aufgefuhrt ist. Sehen Sie in der Spalte "Dienstname" der Tabelle nach, um die entsprechende Bezeichnung nachzuschlagen.

**Port** **TCP oder UDP** **Dienst- oder Protokollname** **RFC** **Dienstname** **Verwendet von/Zusatzinformationen**

**7**
TCP/UDP
echo
792
echo
-

**20**
TCP
File Transfer Protocol (FTP)
959
ftp-data
-

**21**
TCP
FTP-Steuerung
959
ftp
-

**22**
TCP
Secure Shell (SSH)
4253
ssh
Xcode Server (gehostetes und entferntes Git+SSH; entferntes SVN+SSH)

**23**
TCP
Telnet
854
telnet
-

**25**
TCP
Simple Mail Transfer Protocol (SMTP)
5321
smtp

Mail (zum Senden von E-Mails); iCloud Mail (Senden)

**53**
TCP/UDP
Domain Name System (DNS)
1034
domain
MacDNS, FaceTime

**67**
UDP
Bootstrap Protocol Server (BootP, bootps)
951
bootps
NetBoot via DHCP

**68**
UDP
Bootstrap Protocol Client (bootpc)
951
bootpc
NetBoot via DHCP

**69**
UDP
Trivial File Transfer Protocol (TFTP)
1350
tftp
-

**79**
TCP
Finger
1288
finger
-

**80**
TCP
Hypertext Transfer Protocol (HTTP)
2616
http
World Wide Web, iCloud, QuickTime-Installationsprogramm, iTunes Store und Radio, OS X-Softwareaktualisierung (Mac OS X Lion und alter), Mac App Store, RAID-Admin, Backup, Kalender, WebDAV, Final Cut Server, AirPlay, OS X [Internetwiederherstellung](http://support.apple.com/kb/HT4718?viewlocale=de_DE), Profil-Manager, Xcode Server (Xcode-App, gehostetes und entferntes Git HTTP, entferntes SVN HTTP).

**88**
TCP
Kerberos
4120
kerberos
-

**106**
TCP
Passwortserver  
(Unregistrierte Nutzung)
-
3com-tsmux
Mac OS X Server-Passwortserver

**110**
TCP
Post Office Protocol (POP3)  
Authenticated Post Office Protocol (APOP)
1939
pop3
Mail (fur den Empfang von E-Mails)

**111**
TCP/UDP
Remote Procedure Call (RPC)
1057, 1831
sunrpc
Portmap (sunrpc)

**113**
TCP
Identification Protocol
1413
ident
-

**115**
TCP
Simple File Transfer Protocol (SFTP)
913
sftp
-

**119**
TCP
Network News Transfer Protocol (NNTP)
3977
nntp
Wird zum Lesen von Newsgroups verwendet.

**123**
UDP
Network Time Protocol (NTP)
1305
ntp
Einstellungen fur Datum und Uhrzeit. Wird fur die Netzwerkzeitserver-Synchronisierung und AppleTV Netzwerkzeitserver-Synchronisierung verwendet.

**137**
UDP
Windows Internet Naming Service (WINS)
-
netbios-ns
-

**138**
UDP
NETBIOS Datagram Service
-
netbios-dgm
Windows Datagram-Dienst, Windows-Netzwerkumgebung

**139**
TCP
Server Message Block (SMB)
-
netbios-ssn
Wird von Microsoft Windows-Datei- und -Druckdiensten verwendet, wie z. B. der Windows-Freigabe unter Mac OS X.

**143**
TCP
IMAP (Internet Message Access Protocol)
3501
imap
Mail (fur den Empfang von E-Mails)

**161**
UDP
Simple Network Management Protocol (SNMP)
1157
snmp
-

**192**
UDP
OSU Network Monitoring System
-
osu-nms
AirPort-Basisstation PPP-Status oder -Erkennung (bestimmte Konfigurationen), AirPort Admin-Dienstprogramm, AirPort Express-Assistent

**311**
TCP
Sichere Serververwaltung
-
asip-webadmin
Server-App, Server-Admin, Arbeitsgruppenmanager, Servermonitor, Xsan-Admin.

**312**
TCP
Xsan-Verwaltung
-
vslmp
Xsan Admin (OS X Mountain Lion 10.8 und neuer)

**389**
TCP
Lightweight Directory Access Protocol (LDAP)
4511
ldap
Wird von bestimmten Programmen wie Mail und Adressbuch zum Nachschlagen von Adressen verwendet.

**427**
TCP/UDP
Service-Location-Protocol (SLP)
2608
svrloc
Netzwerkbrowser

**443**
TCP
Secure Sockets Layer (SSL oder "HTTPS")
2818
https
TLS-Webseiten, iTunes Store, OS X-Softwareaktualisierung (Mountain Lion und neuer), Mac App Store, FaceTime, Game Center, iCloud-Authentifizierung und DAV-Dienste (Kontakte, Kalender und Lesezeichen), iCloud-Backup und -Programme (Kalender, Kontakte, Mein iPhone suchen/Freunde suchen, Mail, Dokumente und Fotostream), iCloud Key Value Store (KVS), iPhoto-Journale, AirPlay, OS X [Internetwiederherstellung](http://support.apple.com/kb/HT4718?viewlocale=de_DE), Profil-Manager, Zugang zu meinem Mac, Diktierfunktion, Xcode Server (gehostetes und entferntes Git HTTPS, entferntes SVN HTTPS, Apple Developer-Registrierung).

**445**
TCP
Microsoft SMB Domain Server
-
microsoft-ds
-

**464**
TCP/UDP
kpasswd
3244
kpasswd
-

**465**
TCP
Message Submission fur Mail (Authentifiziertes SMTP)
smtp (veraltet)
Mail (fur das Senden von E-Mails)

**500**
UDP
ISAKMP/IKE
2408
isakmp
OS X Server-VPN-Dienst, Zugang zu meinem Mac

**500**
UDP
Anrufe uber WLAN
5996
IKEv2
Anrufe uber WLAN 

**514**
TCP
shell
-
shell
-

**514**
UDP
Syslog
-
syslog
-

**515**
TCP
Line Printer (LPR), Line Printer Daemon (LPD)
-
printer
Wird fur das Drucken auf Netzwerkdruckern verwendet, z. B. uber die Druckerfreigabe in Mac OS X.

**532**
TCP
netnews
-
netnews
-

**548**
TCP
Apple Filing Protocol (AFP) uber TCP
-
afpovertcp
AppleShare, Personliche Dateifreigabe, AFP-Dateiserver

**554**
TCP/UDP
Real Time Streaming Protocol (RTSP)
2326
rtsp
QuickTime Streaming Server (QTSS), Streaming-Medien-Player, AirPlay

**587**
TCP
Message Submission fur Mail (Authentifiziertes SMTP)
4409
submission
Mail (zum Senden von E-Mails), iCloud Mail (SMTP-Authentifizierung)

**600-1023**
TCP/UDP
Mac OS X RPC-basierte Dienste
-
ipcserver
Wird z. B. von NetInfo verwendet.

**623**
UDP
Lights-Out-Monitoring
-
asf-rmcp
Wird von der LOM-Funktion (Lights-Out-Monitoring) von Intel Xserve und vom Servermonitor verwendet.

**625**
TCP
Open Directory Proxy (ODProxy) (Unregistrierte Nutzung)
-
dec_dlm
Open Directory, Server-App, Arbeitsgruppenmanager; DirectoryServices in Mac OS X Lion und alteren Versionen.** Hinweis:** Dieser Port ist fur DEC DLM registriert.

**626**
TCP
AppleShare Imap Admin (ASIA)
-
asia
IMAP Administration (Mac OS X Server 10.2.8 oder alter)

**626**
UDP
serialnumberd (Unregistrierte Nutzung)
-
asia
Registrierung der Server-Seriennummer (Xsan, Mac OS X Server 10.3 bis 10.6)

**631**
TCP
Internet Printing Protocol (IPP)
2910
ipp
Mac OS X-Druckerfreigabe, Drucken auf vielen gangigen Druckern

**636**
TCP
Gesichertes LDAP
-
ldaps
-

**660**
TCP
Serververwaltung
-
mac-srvr-admin
Serververwaltungstools fur Mac OS X Server 10.4 und altere Versionen, einschließlich AppleShare IP.

**687**
TCP
Serververwaltung
-
asipregistry
Serververwaltungstools fur Mac OS X Server 10.6 und altere Versionen, einschließlich AppleShare IP.

**749**
TCP/UDP
Kerberos 5 admin/changepw
-
kerberos-adm
-

**985**
TCP
NetInfo Static Port
-
-
-

**993**
TCP
Mail IMAP SSL
-
imaps
iCloud Mail (SSL IMAP)

**995**
TCP/UDP
Mail POP SSL
-
pop3s
-

**1085**
TCP/UDP
WebObjects
-
webobjects
-

**1099 & 8043**
TCP
Remote RMI- und IIOP-Zugriff auf JBOSS
-
rmiregistry
-

**1220**
TCP
QT Server-Admin
-
qt-serveradmin
Wird fur die Verwaltung von QuickTime Streaming Server verwendet.

**1640**
TCP
Certificate Enrollment Server
-
cert-responder
Profil-Manager, SCEP

**1649**
TCP
IP-Ausfallumschaltung
-
kermit
-

**1701**
UDP
L2TP
-
l2f
Mac OS X Server-VPN-Dienst

**1723**
TCP
PPTP
-
pptp
Mac OS X Server-VPN-Dienst

**1900**
UDP
SSDP
-
ssdp
Bonjour, Zugang zu meinem Mac

**2049**
TCP/UDP
Network File System (NFS) (Version 3 und 4)
3530
nfsd
-

**2195**
TCP
Apple Push-Benachrichtigungsdienst (APNS)
-
-
Push-Benachrichtigungen

**2196**
TCP
Apple Push-Benachrichtigungsdienst (APNS)
-
-
Feedback-Dienst

**2336**
TCP
Synchronisierung mobiler Accounts
-
appleugcontrol
Synchronisierung des Benutzerordners

**3004**
TCP
iSync
-
csoftragent
-

**3031**
TCP/UDP
Entfernte AppleEvents
-
eppc
Programmverbindungen, Entfernte Apple-Events

**3283**
TCP/UDP
Net Assistant
-
net-assistant
Apple Remote Desktop 2.0 oder neuer (Berichtsfunktion)

**3306**
TCP
MySQL
-
mysql
-

**3478-3497**
UDP
-
-
nat-stun-port - ipether232port
FaceTime, Game Center

**3632**
TCP
Verteilter Compiler
-
distcc
-

**3659**
TCP/UDP
Simple Authentication and Security Layer (SASL)
-
apple-sasl
Mac OS X Server-Passwortserver

**3689**
TCP
Digital Audio Access Protocol (DAAP)
-
daap
iTunes-Musikfreigabe, AirPlay

**3690**
TCP/UDP
Subversion
-
svn
Xcode Server (anonymes entferntes SVN)

**4111**
TCP
XGrid
-
xgrid
-

**4398**
UDP
-
-
-
Game Center

**4488**
TCP
Apple Wide Area Connectivity Service
awacs-ice
Zugang zu meinem Mac

**4500**
UDP
IPsec NAT-Traversal
4306
ipsec-msft

OS X Server-VPN-Dienst, Zugang zu meinem Mac. **Hinweis:** Durch Konfigurieren von "Zugang zu meinem Mac" auf einer AirPort-Basisstation oder Time Capsule im NAT-Modus wird die Konnektivitat zu einem OS X Server-VPN-Dienst hinter dieser NAT eingeschrankt.

**4500**
UDP
Anrufe uber WLAN
5996
IKEv2
Anrufe uber WLAN

**5003**
TCP
FileMaker - Namensbindung und Transport
-
fmpro-internal
-

**5009**
TCP
(Unregistrierte Nutzung)
-
winfs
AirPort-Dienstprogramm, AirPort Express-Assistent

**5060**
UDP
Session Initiation Protocol (SIP)
3261
sip
iChat

**5100**
TCP
-
-
socalia
Mac OS X Kamera- und Scannerfreigabe

**5190**
TCP/UDP
America Online (AOL)
-
aol
iChat und AOL Instant Messenger, Dateitransfer

**5222**
TCP
XMPP (Jabber)
3920
jabber-client
iChat- und Jabber-Nachrichten

**5223**
TCP
Apple Push-Benachrichtigungsdienst
-
-
iCloud DAV-Dienste (Kontakte, Kalender und Lesezeichen), APNS, FaceTime, Game Center, Fotostream, Zugang zu meinem Mac

**5269**
TCP
XMPP Server-zu-Server-Kommunikation
3920
jabber-server
iChat-Server

**5297**
TCP
-
-
-
iChat (lokaler Datenverkehr)

**5298**
TCP/UDP
-
-
-
iChat (lokaler Datenverkehr)

**5350**
UDP
NAT Port Mapping Protocol-Ankundigungen
-
-
Bonjour, Zugang zu meinem Mac

**5351**
UDP
NAT Port Mapping Protocol
-
nat-pmp
Bonjour, Zugang zu meinem Mac

**5353**
UDP
Multicast DNS (MDNS)
3927
mdns
Bonjour, AirPlay, Privatfreigabe, Printer Discovery, Zugang zu meinem Mac

**5432**
TCP
PostgreSQL
-
postgresql
Kann manuell auf Lion Server aktiviert werden. Vorher standardmaßig fur ARD 2.0-Datenbank aktiviert.

**5678**
UDP
SNATMAP-Server
-
rrac
Der SNATMAP-Dienst auf Port 5678 wird verwendet, um die externe Internetadresse von Hosts zu bestimmen, damit Verbindungen zwischen iChat-Benutzern hinter der NAT (Network Address Translation) korrekt funktionieren. Der SNATMAP-Dienst gibt einfach die mit ihm verbundene Internetadresse an Clients weiter. Dieser Dienst wird auf einem Apple-Server ausgefuhrt, sendet jedoch keine personlichen Daten an Apple. Wenn bestimmte iChat AV-Funktionen verwendet werden, wird Kontakt mit diesem Dienst aufgenommen. Das Blockieren dieses Dienstes kann bei iChat AV-Verbindungen mit Hosts auf Netzwerken, die NAT verwenden, zu Problemen fuhren.

**5897-5898**
UDP
(Unregistrierte Nutzung)
-
-
xrdiags

**5900**
TCP
Virtual Network Computing (VNC)  
(Unregistrierte Nutzung)
-
vnc-server
Apple Remote Desktop 2.0 oder neuer (Funktion "Beobachten/Steuern")  
Bildschirmfreigabe (Mac OS X 10.5 oder neuer)

**5988**
TCP
WBEM HTTP
-
wbem-http
Apple Remote Desktop 2.x (siehe <http://dmtf.org/standards/wbem>)

**6970-9999**
UDP
-
-
-
QuickTime Streaming Server

**7070**
TCP
RTSP (Unregistrierte Nutzung)  
Automatic Router Configuration Protocol (ARCP - Registrierte Nutzung)
-
arcp
QuickTime Streaming Server (RTSP)

**7070**
UDP
RTSP alternativ
-
arcp
QuickTime Streaming Server

**7777**
TCP
Dateiubertragungsproxy fur iChat-Server (unregistrierte Nutzung)
-
cbt
-

**8000-8999**
TCP
-
-
irdmi
Webserver, iTunes-Radio-Streams

**8005**
TCP
Tomcat - entferntes Ausschalten
-
-
-

**8008**
TCP
iCal-Dienst
-
http-alt
Mac OS X Server 10.5 und neuer

**8080**
TCP
Alternativer Port fur Apache-Webdienst
-
http-alt
Ebenso JBOSS HTTP in Mac OS X Server 10.4 und alter

**8085-8087**
TCP
Wiki-Dienst
-
-
Mac OS X Server 10.5 und neuer

**8088**
TCP
Softwareaktualisierungsdienst
-
radan-http
Mac OS X Server 10.4 und neuer

**8089**
TCP
Web-E-Mail-Regeln
-
-
Mac OS X Server 10.6 und neuer

**8096**
TCP
Web-Passwortrucksetzung
-
-
Mac OS X Server 10.6.3 und neuer

**8170**
TCP
HTTPS (Webdienst/Website)
-
-

Podcast-Aufzeichnung/Podcast-CLI

**8171**
TCP
HTTP (Webdienst/Website)
-
-

Podcast-Aufzeichnung/Podcast-CLI

**8175**
TCP
Pcast Tunnel
-
-
pcastagentd (fur Steuervorgange, Kamera usw.)

**8443**
TCP
iCal-Dienst (SSL)
-
pcsync-https
Mac OS X Server 10.5 und neuer. Fruher JBOSS HTTP in Mac OS X Server 10.4 und alter.

**8800**
TCP
Adressbuchdienst
-
sunwebadmin
Mac OS X Server 10.6 und neuer

**8843**
TCP
Adressbuchdienst (SSL)
-
-
Mac OS X Server 10.6 und neuer

**8821, 8826  
**
TCP
Gesichert
-
-
Final Cut Server

**8891**
TCP
ldsd
-
-
Final Cut Server (Datenubertragungen)

**9006**
TCP
Tomcat - eigenstandige Version
-
-
Mac OS X Server 10.6 und alter

**9100**
TCP
Drucken
-
-
Wird fur das Drucken auf bestimmten Netzwerkdruckern verwendet.

**9418**
TCP/UDP
Git-Paketubertragung
-
git
Xcode Server (entferntes Git)

**11211**
-
memcached (unregistriert)
-
-
Kalender-Server

**16080**
TCP
-
-
-
Webdienst mit Cache fur verbesserte Leistung

**16384-16403**
UDP
Real-Time Transport Protocol (RTP), Real-Time Control Protocol (RTCP)
-
connected, -
iChat AV (Audio-RTP, RTCP; Video-RTP, RTCP)

**16384-16387**
UDP
Real-Time Transport Protocol (RTP), Real-Time Control Protocol (RTCP)
-
connected, -
FaceTime, Game Center

**16393-16402**
UDP
Real-Time Transport Protocol (RTP), Real-Time Control Protocol (RTCP)
-
-
FaceTime, Game Center

**16403-16472**
UDP
Real-Time Transport Protocol (RTP), Real-Time Control Protocol (RTCP)
-
-
Game Center

**24000-24999**
TCP
-
-
med-ltp
Webdienst mit Cache fur verbesserte Leistung

**42000-42999**
TCP
-
-
-
iTunes-Radio-Streams

**49152-65535**
TCP
Xsan
-
-
Zugriff auf das Xsan-Dateisystem

**49152-65535**
UDP
-
-
-
Zugang zu meinem Mac

**50003**
-
FileMaker - Server-Dienst
-
-
-

**50006**
-
FileMaker - Hilfsdienst
-
-
-

Informationen zu nicht von Apple gefertigten Produkten sowie nicht von Apple gesteuerte oder geprufte unabhangige Websites werden ohne Empfehlung und Unterstutzung zur Verfugung gestellt. Apple ubernimmt keine Verantwortung fur die Auswahl, Leistung oder Nutzung von Websites und Produkten Dritter. Apple ubernimmt keine Garantie fur die Richtigkeit und Zuverlassigkeit von Drittanbieter-Websites. Die Nutzung des Internets birgt Risiken. [Kontaktieren Sie den Hersteller](https://support.apple.com/de-de/HT201777), um zusatzliche Informationen zu erhalten. Andere Produkt- und Firmennamen sind moglicherweise Marken ihrer jeweiligen Eigentumer.
