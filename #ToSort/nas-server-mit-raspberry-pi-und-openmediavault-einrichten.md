# NAS-Server mit Raspberry Pi und OpenMediaVault einrichten

_Captured: 2017-03-05 at 11:50 from [www.heise.de](https://www.heise.de/download/blog/NAS-Server-mit-Raspberry-Pi-und-OpenMediaVault-einrichten-3468200)_

![](https://1.f.ix.de/scale/geometry/1000x1000/q85/hdl/blog/94/2/0/1/7/1/7/1/2016kw44-nas-mit-raspberry-pi-16zu9-banner-1-8e90cea00d314532.jpeg)

Gemaß dem alten Spruch "Viele Wege fuhren nach Rom" sind auch die Wege zum eigenen NAS vielfaltig und hangen zuerst einmal von den eigenen Wunschen und Bedurfnissen ab. Denn anstatt sich eine teure NAS-Box zu kaufen, reicht fur den Normalnutzer durchaus ein Raspberry Pi 2 oder besser 3 mit angeschlossenen USB-Festplatten, USB-Sticks und der NAS-Server-Software [OpenMediaVault](https://www.heise.de/download/product/openmediavault-95352).

### Wozu ein Network Attached Storage?

Heute sind in der Regel mehrere Gerate wie Desktop-Computer, Notebook, Tablet und Smartphone im Haushalt vorhanden. Damit man nicht standig die genutzten Dateien hin und her kopieren muss, bietet sich ein zentraler Speicherort an, auf den alle Gerate Zugriff haben. So einen Speicherort fur Dokumente, Bilder, Videos und Musik bietet ein NAS im Netzwerk.

NAS steht fur Network Attached Storage, der via LAN und WLAN von Computer-Hardware und Mobilgeraten genutzt werden kann. Je nach Umfang des NAS konnt ihr Dateien speichern, die automatisch auf eine zweite Festplatte kopiert und so gesichert werden. Die gespeicherten Daten sind entweder fur alle im Netzwerk lesbar oder nur fur berechtigte Nutzer zuganglich. Entsprechend kann jeder in der Familie dort seine privaten Daten speichern oder fur alle zugangliche Dateien wie Videos, Bilder und Musik ansehen und/oder anhoren.

### Was kann OpenMediaVault?

OpenMediaVault (OMV) bringt als Open Source NAS-Server-Software viele Funktionen zum Speichern und Verwalten von Dateien mit. Die Freeware unterstutzt den Fernzugriff uber FTP, TFTP, SMB, NFS und SNMP. Kurz gesagt, ihr kommt nahezu von jedem Gerat aus an eure Daten, wobei vor allem der Zugriff via SMB/[Samba](https://www.heise.de/download/product/samba-55734) wichtig ist, da das zugehorige SMB-Protokoll von Linux, Mac OS X, Windows und Android unterstutzt wird. Android-Nutzer konnen sich dafur den [ES Datei Explorer](https://www.heise.de/download/product/es-datei-explorer-93817) herunterladen.

![](https://1.f.ix.de/scale/geometry/700/q75/hdl/blog/94/2/0/1/7/1/7/1/9001--Bildschirmfoto_vom_2016-11-16_17-34-50--mod01-5734eb02d3475ff5.png)

OpenMediaVault bietet zur Datensicherung die Synchronisation mit Rsync an, wobei man Quell- und Zielordner vorgibt. Ihr konnt damit festlegen welche Verzeichnisse gesichert werden sollen und bei welchen es unnotig ist. Letzteres konnte zum Beispiel bei Mediendateien wie Fotos, Musik und Videos der Fall sein, wenn diese noch auf einer Backup-Festplatte vorhanden sind und ohnehin nicht verandert werden.

Alternativ zu Rsync unterstutzt OpenMediVault RAID, wobei mehrere Festplatten zu einem virtuellen Laufwerk zusammen geschaltet werden. Das RAID-System verteilt Dateien auf die angeschlossenen Festplatten, wobei es sich auch um die Datensicherung kummert. Deswegen sind auch mindestens zwei Festplatten erforderlich.

Neben den vorhandenen Funktionen lasst sich OpenMediaVault mit zusatzlichen Features erweitern. Einige Plug-ins sind unter den Erweiterungen zu finden, die nur noch installiert werden mussen. So konnt ihr OpenMediaVault um einen Medien Server oder Virenscanner erweitern. Zudem gibt es im Internet weitere Plug-ins fur OMV.

### OMV auf dem Raspberry Pi installieren 

Die Installation von OpenMediaVault lauft unkompliziert ab. Ihr musst lediglich das OpenMediaVault-Image fur den Raspberry Pi uber unseren Eintrag [OpenMediaVault](https://www.heise.de/download/product/openmediavault-95352) herunterladen, auf eine MicroSD-Karte kopieren, diese in den Mini-Computer stecken und dann starten.

Das Image von OpenMediaVault ist im GZ-Format komprimiert. Unter Linux lasst es sich mit dem Befehl `gunzip` oder uber den Dateimanager dekomprimieren. Unter Windows hilft beispielsweise [7-Zip](https://www.heise.de/download/product/7-zip-13139). Danach wird die erhaltene IMG-Datei unter Windows mit der Freeware [Win32 Disk Imager](https://www.heise.de/download/product/win32-disk-imager-92033) auf die MicroSD-Karte ubertragen. Unter [Ubuntu](https://www.heise.de/download/product/ubuntu-22040), [Knoppix](https://www.heise.de/download/product/knoppix-35154) und anderen Linux Distributionen lasst sich dies im Terminal durch den Befehl `dd if=omv_3.0.51_rpi2_rpi3.img of=/dev/sdc bs=1M `erledigen. bs=1M bedeutet, dass in einem Kopierschritt ein Megabyte ubertragen wird und /dev/sdc bezeichnet das Gerat fur die eingesteckte MicroSD-Karte, das bei euch anders heißen kann.

Über` sudo fdisk -l` oder `sudo blkid` oder `lsblk` bekommt ihr unter Linux alle angeschlossenen Gerate angezeigt. Relevant sind nur die, die mit "/dev/sd" beziehungsweise "sd" beginnen. /dev/sda beziehungsweise sda ist die interne Festplatte und /dev/sdb beziehungsweise sdb bezeichnet zum Beispiel eine SD-Karte mit dem laufenden Knoppix. Um nicht das falsche Gerat auszuwahlen, solltet ihr jedes unnotige Wechselmedium entfernen, denn dann ist die Auswahl einfacher. Gerate mit /dev/ram, /dev/sr oder /dev/mapper konnt ihr ignorieren, da sie nicht auf angeschlossene (Micro)SD-Karten, USB-Sticks oder USB-Festplatten verweisen. Meistens endet die Gerate-Bezeichnung mit einer Zahl, wodurch eine Partition auf dem Gerat angesprochen wird. Die Zahl fallt weg, da die gesamte MicroSD-Karte verwendet wird. Ist ein Partition auf der MicroSD-Karte vorhanden, wird diese zum Beispiel mit /dev/sdc1 bezeichnet und die gesamte MicroSD-Karte mit /dev/sdc -- also ohne die 1.

### Der erste Start von OpenMediaVault

Vor dem ersten Start musst ihr euren Router so einstellen, dass er dem Raspberry Pi bei jedem Start dieselbe IP-Adresse zuteilt. Denn dann konnt ihr das NAS nach einem Neustart uber dieselbe Adresse finden und musst sie nicht aufs Neue herausfinden.

Falls euer Router nicht die IP-Adresse des Raspberry Pi mit OpenMediaVault ausgibt, muss beim Erststart ein Monitor, eine Tastatur und Maus angeschlossen werden. Die USB-Festplatten und USB-Sticks fur die Daten, werden spater angeschlossen. Zuerst lauft die Installation automatisch ab, wenn der Raspberry Pi mit Strom versorgt wird. Anschließend musst ihr euch bei der Login-Aufforderung mit dem Benutzernamen "root" und dem Passwort "openmediavault" einloggen.

Bild 1 von 15

## OpenMediaVault installieren

![](https://1.f.ix.de/scale/geometry/711x500/q75/imgs/71/2/0/1/5/6/4/7/0010--VirtualBox_OpenMediaVault_15_11_2016_13_24_51-2dc3d19c7a16ea47.png)

Sind Monitor und Tastatur an den Raspberry Pi angeschlossen, konnt ihr die erste Schritte gleich hier ausfuhren. Ist der Bootvorgang abgeschlossen, loggt ihr euch mit dem Benutzernamen "root" und dem Passwort "openmediavault" ein.

Als Nachstes ist das Tastaturlayout auf Deutsch umzustellen. Gebt deswegen den Befehl `dpkg-reconfigure keyboard-configuration` ein. In der folgenden Oberflache, die mit Pfeiltasten, Tabulator- und Enter-Taste zu bedienen ist, wahlt ihr eine 105-Zeichen-Tastatur und als Sprache Deutsch. Dieses geht abschnittsweise und wird uber "OK" gespeichert. Andere Einstellungen konnt ihr so lassen und mit "OK" bestatigen, bis das schwarze Terminal wieder erscheint. Nun solltet ihr testen, ob die Zeichen der Tastatur erscheinen, die ihr verwendet. Ist das der Fall, ist alles ok. Ansonsten startet ihr am besten den Raspberry Pi uber den Befehl `shutdown -r now `neu und loggt euch wieder ein.

Jetzt sollte die Tastatur richtig erkannt werden. Dies ist wichtig, da ihr nun ein neues Passwort setzen musst, damit sich niemand mit dem bekannten Standardpasswort einloggen kann. Der Befehl zur Passwortanderung lautet `passwd`, wonach ihr zweimal das neue Passwort eingeben musst.

Die IP-Adresse eures Raspberry Pi findet ihr uber den Befehl `ifconfig` heraus. Er zeigt alle Netzwerkgerate an, wobei fur euch "eth0" relevant ist. Hier steht hinter "addr:" die vergebene IPv4-Adresse, die ihr euch notieren oder merken musst.

Die Arbeiten uber das Terminal sind fertig und ihr konnt den Raspberry Pi uber `shutdown -h now` herunterfahren, wenn ihr spater weitermachen wollt. Ansonsten lasst ihr ihn an.

### Die Web-Administration

Die Verwaltung von OpenMedaiVault findet uber ein Web-Frontend statt. Um die Login-Seite zu erhalten, gebt ihr die IP-Adresse des Raspberry Pi in die Adresszeile eines Browsers ein. Dabei musst ihr naturlich einen Computer nutzen, der sich im selben Netzwerk wie der Raspberry Pi befindet.

Nach dem Login mit dem Benutzernamen "admin" und dem Passwort "openmediavault" sind zunachst grundlegende Einstellungen vorzunehmen. Dazu gehort das Einstellen der richtigen Uhrzeit, die ihr uber das Internet beziehen musst, da der Raspberry Pi im Gegensatz zu Desktop-Rechnern keine Hardware-Uhr besitzt.

Wenn ihr das Netzwerk mit anderen teilt, bietet sich eine verschlusselte Verbindung an. Fur diese musst ihr euch unter dem Navigationspunkt "Zertifikate" selbst ein SSL-Zertifikat ausstellen. Dieses braucht man zum Aufbau einer sicheren Verbindung, die unter "Allgemeine Einstellungen" zu aktivieren ist. Der Port bleibt am besten unverandert. Denn wenn der Port vom Standard abweicht, muss er immer an die IP-Adresse angehangt werden.

Wichtig ist auch, dass ihr das Passwort fur den Nutzer "admin" andert, damit niemand sonst mit dem Standardpasswort unerlaubt die Einstellungen des NAS-Server verandern kann.

Bild 1 von 14

## Erste Schritte mit OpenMediaVault

![](https://1.f.ix.de/scale/geometry/711x500/q75/imgs/71/2/0/1/7/9/3/7/0090--Bildschirmfoto_vom_2016-11-07_15-00-24-XXX-a34d0ced11e33100.png)

> _Die Konfiguration von OpenMediaVault findet via Browser auf einem entfernten Computer im selben Netzwerk statt. In die Adresszeile musst ihr die IP-Adresse eingeben, die euer Router dem Raspberry Pi mit OpenMediaVault gegeben hat. Der Benutzername lautet "admin" und das Standardpasswort "openmediavault"._

Nach diesen grundlegenden Schritten schließt ihr die Festplatten fur die Daten an den Raspberry Pi an und richtet sein in OpenMediaVault ein. Denn der NAS-Server muss wissen, welche USB-Sticks und USB-Festplatten angeschlossen sind. Geht dazu in der Navigation auf "Reale Festplatten" und fuhrt eine Suche aus, die alle angeschlossenen Medien inklusive der eingesteckten MicroSD-Karte erkennt.

Danach musst ihr die auf den Datentragern enthaltenen Partitionen einbinden, was unter "Dateisysteme" geschieht. Hier zeigt OMV auch die Laufwerke "boot" und "omv" an, die fur das System verwendet werden und nicht verandert werden durfen. Schließt am besten nur Festplatten und USB-Sticks ohne Daten an, da OMV diese mit einem neuen Dateisystem versieht, wenn er das verwendete nicht kennt und somit die enthaltenen Daten loscht. Die Daten auf Partitionen, die mit EXT3, EXT4, BTRFS, XFS, JFS formatiert wurden, bleiben fur gewohnlich durchaus erhalten -- aber ohne Gewahr.

Unter "Freigegebene Ordner" fugt ihr nun zuerst das "Benutzerverzeichnis" hinzu. Der Name ist vorgegeben und muss mit dem Ordner "homes/" auf einem der angeschlossenen Speichermedien verknupft werden. Anschließend konnt ihr die Benutzer anlegen, die auf dem NAS-Server Schreibrechte haben. Sollen sie ein eigenes Benutzerverzeichnis bekommen, muss die unter "Benutzer > Einstellungen" aktiviert werden. Danach wird beim Anlegen eines Benutzer automatisch das zugehorige Benutzerverzeichnis angelegt.

Wenn ein Nutzer in einem anderen Verzeichnis Schreibrechte und/oder Leserechte haben soll, musst ihr dies als Admin unter "Zugriffskontrolle > Freigegebene Ordner > Privilegien" konkret erlauben. Bei offentlich zuganglichen Verzeichnisse, die ihr via SMB/Samba fur andere Rechner mit Windows-, Apple- oder Linux-Computer freigegeben habt, ist das unnotig. Aber dazu mehr in der folgenden Bildergalerie.

![](https://1.f.ix.de/scale/geometry/711x500/q75/imgs/71/2/0/3/3/6/2/2/0200--Bildschirmfoto_vom_2016-11-08_14-47-30-d922f40712ba8cc0.png)

> _Ein NAS braucht Speichermedien fur die Daten. Deswegen musst ihr USB-Sticks oder USB-Festplatten mit eigener Stromversorgung oder uber einen aktiven USB-Hub an den Raspberry Pi anschließen. Unter "Datenspeicher > Reale Festplatten" werden die vorhandenen angezeigt. Im Screenshot wird die MicroSD-Karte im Raspberry Pi zuerst und danach ein USB-Stick gelistet._

### Raspberry Pi und Hardware

Um den Raspberry Pi als NAS einzusetzen, braucht ihr neben dem Mini-Computer und Netzteil eine MicroSD-Karte sowie mindestens zwei USB-Sticks oder USB-Festplatten. Ob es sich bei den USB-Festplatten im Gehause um magnetische HDDs oder SSDs handelt ist egal. Selbst USB-Sticks konnen fur die Datenspeicherung und Sicherung genugen. Sie bietet heute auch schon 100 GB oder mehr Speicherplatz und konnen vom Raspberry Pi direkt mit Strom versorgt werden.

Fur 2,5"-USB-Festplatten, die uber das USB-Kabel auch ihren Strom beziehen, braucht ihr noch einen USB-Hub mit eigenem Netzteil. Steckt die USB-Festplatten zuerst in den USB-Hub und schließt ihn dann an den Raspberry Pi an. Das nachtraglich Anschließen von Festplatten im laufenden Betrieb kann ich aufgrund meiner Erfahrungen nicht empfehlen. Da eine 2,5"-USB-Festplatte beim Start mehr Strom braucht, kann sie bei schwach dimensionierten USB-Hubs einer bereits angeschlossenen 2,5"-USB-Festplatten den notigen Strom entziehen. Im laufenden Betrieb kann dies zu Datenverlust fuhren.

Alternativ lassen sich auch 3,5"-USB-Festplatten mit eigener Stromversorgung einsetzen. Sie sollten sich bei Untatigkeit automatisch in den Standby versetzen, was die Stromkosten reduziert.

### OpenMediaVault auf dem Desktop-Computer

Wer noch einen alten 32- und 64-Bit-Desktop-Computer hat, kann diesen ebenfalls als NAS mit OpenMediaVault nutzen. Allerdings brauchen sie mehr Strom als der Raspbery Pi, haben aber mehr Power. Dabei musst ihr beachten, dass OMV bei der Installation eine komplette Festplatte fur das System nutzt, die sich dann nicht als Daten-Platte verwenden lasst.

Wenn der Rechner das Booten von SD-Karte oder USB-Stick unterstutzt, konnt ihr OpenMediaVault dort installieren und die internen Platten fur die Daten lassen. Die internen Festplatten sollten erst nach der Installation angeschlossen werden, um mogliche Probleme und Verwechslungen zu vermeiden.

Der Raspberry Pi mit OpenMediaVault ist eine gute Losung, um zu Hause einen kostengunstigen NAS-Server im eigenen LAN einzurichten. Dieser Netzwerkspeicher reicht, um Musik zu horen, HD-Videos anzusehen und mit Dateien wie Fotos oder Texten zu arbeiten.

Aber der Raspberry Pi hat als Mini-Computer seine Grenzen. Will jeder in der Großfamilie gleichzeitig ein anderes Video sehen, wird es eng. Der Raspberry Pi kann nur 100 MBit/s an Daten uber das Netzwerkkabel senden und auch die Prozessor-Leistung kann bei starker Nutzung nicht reichen.

Fur den Einstieg in die Welt der Cloud-Speicher ist der Selbstbau NAS mit Raspberry Pi und OpenMediaVault meiner Meinung nach auf jeden Fall geeignet -- zumal, wenn ihr bereits die Hardware besitzt.

Ich wunsche euch viel Spaß beim Bauen!

**[➤ OpenMediaVault kostenlos herunterladen](https://www.heise.de/download/product/openmediavault-95352) **

**Auf welche NAS-Losung setzt ihr? Verratet es uns in den Kommentaren!  
**
