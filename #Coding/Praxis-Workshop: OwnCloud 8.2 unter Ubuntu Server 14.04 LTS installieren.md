# Praxis-Workshop: OwnCloud 8.2 unter Ubuntu Server 14.04 LTS installieren

_Captured: 2015-12-28 at 11:20 from [workshop.tecchannel.de](http://workshop.tecchannel.de/a/owncloud-8-2-unter-ubuntu-server-14-04-lts-installieren,3277676?qle=rssfeed_)_

## 01Vorbereitung und Installation von Ubuntu Server 14.04 LTS

Auch wenn es bereits Ubuntu Server 15.10 gibt, haben wir uns dennoch fur Ubuntu Server 14.04 LTS entschieden. Das liegt ganz einfach am LTS, das fur Langzeitunterstutzung steht. Wahrend Version 15.10 lediglich neun Monate mit Updates versorgt wird, bekommen Sie fur Ubuntu Server 14.04 funf Jahre lang Aktualisierungen - das Betriebssystem wird bis 2019 unterstutzt. Bei einer produktiven ownCloud-Umgebung wollen Sie mit Sicherheit ein Betriebssystem einsetzen, das Sie so lange wie moglich nicht mehr anfassen mussen. Aus diesem Grund wurden sich auch die aktuellen Versionen von Red Hat oder SUSE eignen. Die nachste LTS-Version von Ubuntu gibt es laut Zeitplan im April 2016. Ubuntu 16.04 LTS Xenial Xerus wird ebenfalls wieder funf Jahre unterstutzt.

  1. **[LAMP**](http://workshop.tecchannel.de/g/installation-von-ubuntu-server-14-04-lts,113546)  
Wahrend der Installation des Ubuntu Servers konnen Sie neben LAMP auch gleich OpenSSH auswahlen. 
  2. **[MySQL Server**](http://workshop.tecchannel.de/g/installation-von-ubuntu-server-14-04-lts,113546,2)  
Wahlen Sie LAMP, setzen Sie wahrend der Installation auch gleich das Passwort fur den Datenbank-Server. 
  3. **[Aktualisieren**](http://workshop.tecchannel.de/g/installation-von-ubuntu-server-14-04-lts,113546,4)  
Nach der Installation sollten Sie erst einmal die Updates einspielen. 

Laden Sie sich im ersten Schritt den Ubuntu Server herunter und installieren Sie das Betriebssystem. Wahrend der Installation konnen Sie bereits angeben, dass das System als LAMP-Server betrieben werden soll. Weiterhin empfehlen wir die Installation des Pakets OpenSSH-Server. Ubuntu Server betreiben Sie in der Regel "headless", also ohne Bildschirm. Mit OpenSSH erleichtern Sie sich spater die Administration.

Wahlen Sie LAMP aus, verlangt das System ebenfalls ein root-Passwort fur den MySQL-Server. Weiterhin sollte der Host-Rechner mit dem Internet verbunden sein. Ist die Installation durchgefuhrt, aktualisieren Sie das System online. Melden Sie sich dafur auf dem System an und fuhren Sie die fur Debian-basierte Systeme ubliche Routine aus:

`sudo apt-get update`

`sudo apt-get upgrade`

Dem Ubuntu Server wurde via DHCP eine IP-Adresse zugewiesen. Das ist fur einen Server nicht ganz optimal. Eine feste IP-Adresse eignet sich an dieser Stelle wesentlich besser. Entweder erledigen Sie das uber den DHCP-Server oder Sie vergeben eine fixe IP-Adresse im Betriebssystem selbst. Editieren Sie dazu die Datei /etc/network/interfaces. Dort finden Sie zum Beispiel eine Sektion fur die primare Netzwerkkarte, die in unserem Fall eth0 ist. Wir haben die Sektion wie folgt geandert:

`auto eth0`

`address 192.168.100.80`

`gateway 192.168.100.3`

`iface eth0 inet static`

`netmask 255.255.255.0`

Diese Werte passen Sie naturlich so an, dass sie entsprechend in Ihre Netzwerkumgebung passen. In unserem Beispiel hort der Server nun auf die IP-Adresse 192.168.100.80.

Konfigurieren Sie die IP-Adresse manuell, verlieren Sie allerdings die DNS-Auflosung fur das System. Editieren Sie aus diesem Grund die Datei /etc/resolvconf/resolv.conf.d/base und tragen Sie dort gultige DNS-Server ein. Die Datei ist leer, schreiben Sie die DNS-Server einfach in unterschiedliche Zeilen. Mit OpenDNS wurde das so aussehen:

`nameserver 208.67.222.222`

`nameserver 208.67.220.220`

Die Google-DNS-Server wurden 8.8.8.8 und 8.8.4.4 lauten. Diese setzt man ebenfalls gerne ein.

Starten Sie im Anschluss resolvconf neu:

`sudo service resolvconf restart`

## 02Apache Webserver fur https konfigurieren

Auch wenn Sie die ownCloud moglicherweise intern einsetzen, wollen Sie mit Sicherheit verschlusselt mit dem Apache Webserver kommunizieren. Dazu ist es allerdings notwendig, dass Sie ein Zertifikat fur den Ubuntu Server erstellen. Weiterhin muss das Modul ssl fur Apache aktiviert sein. Dies sollte nach einer LAMP-Installation bereits der Fall sein. Zur Sicherheit fuhren Sie aber folgenden Befehl aus:

  1. **[Schlussel**](http://workshop.tecchannel.de/g/apache-webserver-fuer-https-konfigurieren,113547,3)  
Um https nutzen zu konnen, mussen Sie ein selbst signiertes Zertifikat anlegen. 
  2. **[Nicht vertrauenswurdig?**](http://workshop.tecchannel.de/g/apache-webserver-fuer-https-konfigurieren,113547,4)  
Da das Zertifikat nicht aus einer offiziellen Zertifizierungs-Stelle stammt, bekommen SIe diese Warnung. 
  3. **[https**](http://workshop.tecchannel.de/g/apache-webserver-fuer-https-konfigurieren,113547,5)  
Haben Sie alle notwendigen Schritte erledigt, funktionieren auch verschlusselte Seiten.

`sudo a2enmod ssl`

und starten danach den Apache Webserver neu:

`sudo service apache2 restart`

Im Anschluss erstellen Sie ein neues Verzeichnis:

`sudo mkdir /etc/apache2/ssl`

und nachfolgend das selbst unterzeichnete Zertifikat, das Sie in das eben erstellte Verzeichnis legen:

`sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt`

Fuhren Sie diesen Befehl aus, fragt die Software nach diversen Angaben. Dazu gehoren Land, Stadt, E-Mail-Adresse und so weiter. Hier tragen Sie entsprechend ein, was zu Ihrem Unternehmen passt.

Nun editieren Sie die Datei /etc/apache2/sites-available/default-ssl.conf. Dort finden Sie eine Zeile, die mit SSLEngine on beginnt. Fugen Sie darunter die beiden eben angelegten Zertifikate ein:

`SSLCertificateFile /etc/apache2/ssl/apache.crt`

`SSLCertificateKeyFile /etc/apache2/ssl/apache.key`

Weiter unten finden Sie noch einmal zwei Zeilen, die mit SSLCertificateFile und SLCertificateKeyFile beginnen. Kommentieren Sie diese mit einem # aus oder loschen Sie diese Zeilen. Ansonsten fuhrt das beim Apache-Neustart zu einem Fehler. Speichern Sie die Datei und aktivieren diesen mit SSL versehenen virtuellen Host:

`sudo a2ensite default-ssl.conf`

Fur den weiteren Verlauf dieses Artikels andern Sie außerdem die Zeile

`DocumentRoot /var/www/html`

in

`DocumentRoot /var/www`

Um spater eine Security-Warnung zu vermeiden, aktivieren Sie noch mod_headers:

`sudo a2enmod headers`

Editieren Sie die Datei /etc/apache2/sites-available/default-ssl.conf abermals und fugen Sie zum Beispiel unter der Zeile mit ServerAdmin diese Sektion ein:

`<IfModule mod_headers.c>`

`Header always set Strict-Transport-Security "max-age=15768000; includeSubDomains; preload"`

`</IfModule> `

Im Anschluss starten Sie den Apache Webserver neu:

`sudo service apache2 restart`

Besuchen Sie nun die Seite https://192.168.100.80, bekommen Sie zwar eine Warnung wegen eines nicht vertrauenswurdigen Zertifikats, aber die Seite ist verschlusselt. Die Warnung ist normal, da das Zertifikat von Ihnen selbst und nicht von einer autorisierten Zertifizierungsstelle ausgestellt wurde. Fugen Sie eine Ausnahme hinzu und vertrauen Sie dem Zertifikat. Ab sofort ist Ihr Apache Webserver https-fahig.

Wollen Sie die Warnung umgehen, konnten Sie alternativ auch auf Let's Encrypt setzen. Daruber bekommen Sie ein vertrauenswurdiges, kostenloses Zertifikat.

## 03Vorbereitungen fur die ownCloud

Die Voraussetzungen fur die Installation von ownCloud 8.2 sind vereinfacht gesagt mindestens PHP 5.4 und eine Datenbank, wobei hierfur SQLite, MySQL/MariaDB oder PostgreSQL infrage kommen. Wahrend sich ownCloud 7 noch mit PHP 5.3 zufrieden gab, benotigen Sie fur ownCloud 8 mindestens eine Version hoher. Das ist wichtig, da diverse langzeitunterstutzte Distributionen per Standard diese Mindestvoraussetzung nicht erfullen. Ubuntu Server 12.04 LTS ist zum Beispiel bis 2017 unterstutzt, bringt aber nur PHP 5.3 mit sich. Entweder kompilieren Sie in diesem Fall PHP 5.4 oder hoher selbst oder Sie setzen auf ein sogenanntes PPA.

![Weitere Pakete: Für optimale Funktionaität sind noch ein paar weitere Pakete notwendig. ](http://images.cio.de/images/computerwoche/bdb/2708414/840x473.jpg)

> _Weitere Pakete: Fur optimale Funktionaitat sind noch ein paar weitere Pakete notwendig._

Weiterhin ist ownCloud 8.2 die erste ownCloud-Variante, die zu PHP 7 kompatibel ist. Vorgangerversionen horen bei PHP 7 zu funktionieren auf, da diese Konstellation nicht unterstutzt und getestet ist. Die Entwickler wollen somit Schaden vermeiden.

Wir empfehlen, von SQLite komplett die Finger zu lassen. In der Datenbanksektion der Dokumentation raten die Entwickler ebenfalls davon ab, außer es handelt sich um Einzelanwender. Haben Sie aber sehr viele Dateien, ist SQLite auch fur Einzelne nicht geeignet. Die Performance ist sehr unbefriedigend - vielleicht fur ein Testszenario geeignet, aber fur eine produktive Umgebung auf keinen Fall.

Haben Sie LAMP bei der Ubuntu-Installation ausgewahlt, ist MySQL bereits auf dem Server installiert. In unserem Beispiel haben wir MySQL verwendet. Sollte der Datenbankserver noch nicht installiert sein, holen Sie das nach:

`sudo apt-get install mysql-server`

Weiterhin benotigen Sie diverse zusatzliche Pakete, wobei einige davon optional sind. Wir raten dennoch zur Installation aller Pakete, da sonst einige Funktionen moglicherweise nicht verfugbar sind. Sie finden die Liste mit den notwendigen Softwarekomponenten im Administrations-Handbuch. Im ersten Befehl befindet sich Apache2, falls Sie diesen noch nicht eingespielt und wie oben beschrieben konfiguriert haben. Sollte das der Fall sein, ignoriert das System das Paket einfach. Wollen Sie SQLite gar nicht verwenden, konnen Sie im zweiten Befehl php-sqlite außen vor lassen:

`sudo apt-get install apache2 php5 php5-gd php-xml-parser php5-intl`

`sudo apt-get install php5-sqlite php5-mysql smbclient curl libcurl3 php5-curl`

Hinweis: Die beiden Befehle sind moglicherweise nicht zwingend notwendig, wenn Sie die ownCloud nicht uber das offizielle Repository installieren, sondern sich die Quellen direkt holen. Schaden konnen die beiden Befehle aber auch nicht, denn daruber installierte Komponenten brauchen Sie ohnehin.

## 04Installation von ownCloud 8.2

Die ownCloud befindet sich in den Repositories von Ubuntu 14.04 LTS. Es handelt sich dabei allerdings nicht um die neueste Version. Sie konnten das Paket installieren und dann im Administrations-GUI der ownCloud aktualisieren. Allerdings ist das bedenklich. Denn sollte ein Paket-Update uber die Repositories kommen, sind die Folgen schwer abzusehen. Außerdem gibt es in der Zwischenzeit schon mehrere Punkt-Versionen. Das bedeutet, dass die Kinderkrankheiten einer .0-Ausgabe ausgemerzt sein sollten. Installieren Sie sowieso neu, wollen Sie moglicherweise die aktuellste Version haben, die einige neue und interessante Funktionen mit sich bringt. Daruber hinaus drehen die Entwickler bei jeder neuen Version in der Regel an der Performance-Schraube.

  1. **[Offizielles Repository**](http://workshop.tecchannel.de/g/installation-von-owncloud-8-2,113548)  
Die Entwickler der ownCloud stellen Pakete fur Ubuntu zur Verfugung. 
  2. **[Mit apt-get zu Ziel**](http://workshop.tecchannel.de/g/installation-von-owncloud-8-2,113548,2)  
Die aktuelle Version der ownCloud lasst sich wie alle anderen Pakete installieren. 
  3. **[Funktioniert**](http://workshop.tecchannel.de/g/installation-von-owncloud-8-2,113548,3)  
Nach der Installation lasst sich die ownCloud bereits aufrufen, muss aber noch konfiguriert werden.

Wir raten deshalb, dass Sie die ownCloud entweder von der offiziellen Website herunterladen und manuell einspielen oder das offizielle Repository der ownCloud-Entwickler verwenden. Fur Ubuntu 14.04 LTS geht das so:

`sh -c "echo 'deb http://download.owncloud.org/download/repositories/stable/Ubuntu_14.04/ /' >> /etc/apt/sources.list.d/owncloud.list"`

`wget -nv https://download.owncloud.org/download/repositories/stable/Ubuntu_14.04/Release.key -O Release.key`

`sudo apt-key add - < Release.key`

`sudo apt-get update`

`sudo apt-get install owncloud`

Sind Sie dem bisherigen Verlauf dieses Artikels gefolgt, erreichen Sie die ownCloud nun via https://192.168.100.80/owncloud/. Die Dateien der privaten Cloud haben sich im Verzeichnis /var/www/owncloud installiert.

Wollen Sie lieber die Quellen der ownCloud verwenden, packen Sie die Dateien aus und kopieren sie einfach in das Verzeichnis /var/www/owncloud. Die ownCloud wird uber den Apache Webserver ausgeliefert und verwendet die Standard-Ports. Das sind fur http Port 80 und fur https Port 443.

## 05Ersteinrichtung und Konfiguration der Datenbank

Beim Erstaufruf der ownCloud-WebGUI fordert Sie das System auf, ein Administratorkonto einzurichten. Weiterhin konfigurieren Sie an dieser Stelle, welche Datenbank Sie verwenden mochten. Klicken Sie hierfur auf Speicher & Datenbank. Wir wollen fur unser Beispiel die Option MySQL/MariaDB einsetzen und nicht das per Standard ausgewahlte SQLite.

  1. **[Datenbank-Konfiguration**](http://workshop.tecchannel.de/g/ersteinrichtung-und-konfiguration-der-datenbank,113549)  
Am einfachsten geht das mit einer Software, die sich phpMyAdmin nennt.
  2. **[Datenbank anlegen**](http://workshop.tecchannel.de/g/ersteinrichtung-und-konfiguration-der-datenbank,113549,2)  
Wir geben unserer DB einen sprechenden Namen und nennen sie owncloud82.
  3. **[Konfiguration abschließen**](http://workshop.tecchannel.de/g/ersteinrichtung-und-konfiguration-der-datenbank,113549,3)  
Sind alle vorherigen Schritte erfolgreich, konnen Sie die ownCloud in Betrieb nehmen.

Die MySQL-Konfiguration verlangt unter anderem einen Datenbanknamen und einen Anwendernamen fur die Datenbank. Als Anwender konnten Sie root verwenden, obwohl das eher unschon ist. Dafur hatten wir allerdings ein Passwort, das wahrend der LAMP-Installation festgelegt wurde. Der Datenbankname ist hingegen noch nicht erschaffen. Entweder verwenden Sie die Kommandozeile dafur oder Sie installieren phpMyAdmin auf dem Server. Haben Sie wenig mit Datenbanken zu tun, raten wir zu Letzterem:

`sudo apt-get install phpmyadmin`

Wahrend der Installation fragt phpMyAdmin, welchen Webserver Sie verwenden wollen. In unserem Fall ist das apache2. Weiterhin brauchen Sie das Passwort fur den administrativen Benutzer von MySQL. Sie konnen die Datenbankkonfiguration so aufrufen: https://192.168.100.80/phpmyadmin.

Das GUI lasst sich auf Deutsch umstellen, und hier durfen Sie nun eine Datenbank einrichten. Klicken Sie dazu auf Datenbanken und wahlen am besten einen sprechenden Namen. Wir haben unsere Datenbank owncloud82 genannt. Sind Sie mit dem Benutzer root als Datenbankbenutzer nicht glucklich, konnen Sie das an dieser Stelle ebenfalls andern.

Nun haben wir alle Informationen, die wir zur Ersteinrichtung der ownCloud brauchen. Verwenden Sie die entsprechenden Parameter. Der Datenbankname ist in unserem Fall owncloud82 und der Host ist localhost, weil der MySQL-Server auf dem gleichen Host wie die ownCloud selbst lauft. Haben Sie alles eingetragen, klicken Sie auf Installation abschließen.

## 06Die Oberflache der ownCloud erkunden

Haben Sie die erste Einrichtung uberstanden, konnen Sie sich nun als Administrator unter https://192.168.100.80/owncloud/ anmelden, was nach der ursprunglichen Konfiguration automatisch geschieht. Ein Begrußungsbildschirm weist Sie darauf hin, wo Sie die Desktop-Clients und die Mobile-Apps finden. Weiterhin gibt es Hinweise, wie Sie sich mit Kalender (CalDAV), Kontakten (CardDAV) und WebDAV verbinden konnen.

  1. **[Willkommen**](http://workshop.tecchannel.de/g/die-oberflaeche-der-owncloud-erkunden,113550)  
Beim ersten Anmelden bekommen Sie eine kurze Einfuhrung prasentiert.
  2. **[Einstellungen**](http://workshop.tecchannel.de/g/die-oberflaeche-der-owncloud-erkunden,113550,2)  
Unter Personlich konnen Sie unter anderem die Sprache andern und ein Profilbild hochladen.
  3. **[Benutzer**](http://workshop.tecchannel.de/g/die-oberflaeche-der-owncloud-erkunden,113550,3)  
Der Administrator darf neue Anwender hinzufugen und entsprechend Gruppen zuweisen.
  4. **[Administration**](http://workshop.tecchannel.de/g/die-oberflaeche-der-owncloud-erkunden,113550,4)  
Hier bestimmt der Systemverwalter mitunter, auf welche Weise Cron ausgefuhrt wird.
  5. **[Cron**](http://workshop.tecchannel.de/g/die-oberflaeche-der-owncloud-erkunden,113550,5)  
Am besten ist es, den Cronjob uber das Betriebssystem ausfuhren zu lassen.

Der Administrator beziehungsweise die Admin-Gruppe hat die komplette Kontrolle uber die ownCloud. Nur Anwender mit diesen Sonderrechten durfen neue Benutzer anlegen, Apps hinzufugen und so weiter.

Sollte die ownCloud nicht Deutsch sprechen, dann stellen wir aber zunachst die Sprache um. Klicken Sie dafur rechts oben auf Ihren Anwendernamen, in unserem Fall owncloudadmin. Im sich aufklappenden Menu klicken Sie dann auf Personal oder Personlich. In dieser Maske finden Sie alle personlichen Einstellungen. Dazu gehoren auch Profilbild, E-Mail-Adresse und so weiter.

Klicken Sie oben rechts auf den Benutzernamen, in unserem Fall owncloudadmin und danach Benutzer, durfen Sie neue Anwender und Gruppen hinzufugen. Selbst wenn Sie Anwender und Administrator sind, sollten Sie sich einen normalen Nutzer anlegen. Es gilt wie uberall, dass Administration und Nutzung aus Grunden der Security getrennt sein sollten. In der Benutzermaske legen Sie auch die Quotas fur die Anwender fest und konnen Administratoren fur Gruppen bestimmen.

Mit einem Klick auf owncloudadmin und danach Administration konnen Sie gewisse Systemeinstellungen vornehmen. Weiterhin konfigurieren Sie dort, wie Cron gehandhabt werden soll. Haben Sie die ownCloud auf einem eigenen Server, der sich ebenfalls in Ihrer Kontrolle befindet, sollten Sie den Cron des Linux-Rechners verwenden. Öffnen Sie dazu auf dem Linux-Server als root die Crontab des Webserver-Anwenders:

`crontab -u www-data -e`

und fugen dann diese Zeile ein:

`*/15 * * * * php -f /var/www/owncloud/cron.php`

Im Administrationsfenster finden Sie auch das Log, falls Sie auf Fehlersuche gehen mussen. Hier aktivieren Sie außerdem die serverseitige Verschlusselung, was naturlich der Security sehr zugute kommt. Allerdings mussen Sie damit rechnen, dass die Dateien dann zirka 35 Prozent großer sind. Vor einer Aktivierung der Verschlusselung sollten Sie sich die entsprechende Sektion im Anwenderhandbuch grundlich durchlesen.

## 07Weitere Apps aktivieren

Links oben neben der Wolke finden Sie in einem Dropdown-Menu ein Pluszeichen und das Wort Apps. In dieser Maske bestimmt der Adminstrator, welche Apps aktiviert sein sollen und welche nicht. Interessant ist zum Beispiel die App External Storage Support. Damit konnen Anwender externe Storage-Quellen einbinden. Moglich sind unter anderem Amazon S3, Dropbox, OpenStack Object Storage, FTP, SFTP oder SMB / CIFS. Es funktionieren allerdings nicht alle gleich gut. Aktivieren Sie eine App, finden Sie die Einstellungen dafur normalerweise im bereits erwahnten Administrationsbereich.

  1. **[Apps**](http://workshop.tecchannel.de/g/weitere-apps-aktivieren,113551)  
Über das Menu klicken Sie sich zu den zusatzlich verfugbaren Modulen.
  2. **[Externes Storage**](http://workshop.tecchannel.de/g/weitere-apps-aktivieren,113551,2)  
In unserem Beispiel haben wird die Unterstutzung fur externe Massenspeicher aktiviert.
  3. **[Externe Speicher**](http://workshop.tecchannel.de/g/weitere-apps-aktivieren,113551,3)  
Der Administrator kann bestimmen, welches Storage zusatzlich benutzt werden darf.
  4. **[Kalender und Kontakte**](http://workshop.tecchannel.de/g/weitere-apps-aktivieren,113551,4)  
Fruher gehorten diese Apps zum Kern der ownCloud. Heutzutage mussen sie erst aktiviert werden.
  5. **[Nicht fur alle**](http://workshop.tecchannel.de/g/weitere-apps-aktivieren,113551,5)  
Der Administrator darf konfigurieren, dass nur gewisse Gruppen bestimmte Apps verwenden durfen.

Fruher waren Kalender und Kontakte per Standard aktiviert. Diese Komponenten werden aber nun wie andere Dritt-Apps behandelt. Wollen Sie diese verwenden, mussen Sie sie zunachst aktivieren. Beachten Sie, dass bei einem Update alle Dritt-Apps deaktiviert werden. Nach der Aktualisierung muss der Administrator diese manuell wieder aktivieren.

Seit Version 7 hat der Administrator die Moglichkeit, Apps nur fur bestimmte Gruppen zu aktivieren. Das ist sehr angenehm, da sich vor der kompletten Freischaltung bestimmter Erweiterungen diese erst in einem ausgewahlten Kreis testen lassen.

Weiterhin ist sogenanntes Server-zu-Server-Sharing moglich. Das muss der Administrator bei den externen Storage-Optionen aktivieren. Nun kann ein Nutzer einem Anwender einer anderen ownCloud-Instanz einen Link schicken oder eine Freigabe erteilen. Nimmt dieser die Freigabe an, bindet sie sich in die ownCloud-Instanz der zweiten Partei ein. Nehmen Sie zur Kenntnis, dass die andere Partei dabei kein Nutzerkonto auf der ersten ownCloud-Instanz haben muss. Es handelt sich tatsachlich um serverubergreifendes Sharing und gibt der ownCloud die Charakteristik einer Public Cloud. Wie das genau funktioniert, finden Sie in dieser Schritt-fur-Schritt-Anleitung.

## 08Upload-Limits konfigurieren

Neben dem Quota der Anwender gibt es noch eine weitere Komponente, die das Limit der Uploads bestimmt. Dafur ist der Webserver beziehungsweise die PHP-Einstellung zustandig. Sind Sie unserer Anleitung gefolgt, konnen Sie per Standard Dateien hochladen, die maximal 513 MByte groß sind.

![Maximaler Upload: Sie konfigurieren in der Datei .htaccess die maximal akzeptable Größe für hochzuladende Dateien. ](http://images.cio.de/images/computerwoche/bdb/2708431/840x473.jpg)

> _Maximaler Upload: Sie konfigurieren in der Datei .htaccess die maximal akzeptable Große fur hochzuladende Dateien._

Die Einstellungen werden an dieser Stelle nicht uber eine Konfigurationsdatei php.ini festgelegt. Sie befinden sich in der Datei .htaccess im ownCloud-Ordner oder in unserem Fall /var/www/owncloud/.htaccess in der Sektion<IfModule mod_php5.c>.

## 09Vollstandiges Backup der ownCloud

Haben Sie eine funktionierende ownCloud im Einsatz, ist naturlich ein Backup zwingend notwendig. Sprechen wir vom Backup, mussen wir an zwei Komponenten denken: die Dateien der Anwender und die Datenbank. Bei der Verwendung von SQLite liegt die Datenbank im ownCloud-Ordner, und Sie mussen lediglich das komplette Verzeichnis sichern. In unserem Fall befindet sich dieses Verzeichnis unter /var/www/owncloud.

![Datensicherung: Komprimierte Backups dauern länger, können aber enorm Platz sparen.](http://images.cio.de/images/computerwoche/bdb/2708432/840x473.jpg)

> _Datensicherung: Komprimierte Backups dauern langer, konnen aber enorm Platz sparen._

Verwenden Sie MySQL, MariaDB oder PostgreSQL, ist neben dem ownCloud-Ordner auch ein Sichern der Datenbank notwendig. MySQL konnten Sie auch uber phpMyAdmin sichern. Allerdings lasst sich das nicht automatisieren und verlangt umstandliche Handarbeit.

Geschickter ist es, diesen Prozess zu automatisieren. Sie konnen das auf der Kommandozeile mithilfe des Tools mysqldump erledigen. Am besten fugen Sie der Datei noch einen Zeitstempel an. Die Syntax dafur sieht so aus:

`mysqldump -u<Benutzer> -p<Passwort> <Datenbank> > backup$(date +%Y-%m-%d-%H.%M.%S).sql`

oder in unserem Fall:

`mysqldump -uroot -pStrengGeheim owncloud82 > backup$(date +%Y-%m-%d-%H.%M.%S).sql`

Noch besser ist es, wenn Sie das Backup der Datenbank gleich komprimieren lassen. Selbst nach der anfanglichen Installation lasst sich der Platz von 37 KByte auf 5,1 KByte schrumpfen.

`mysqldump -uroot -pStrengGeheim owncloud82 | bzip2 -c > backup$(date +%Y-%m-%d-%H.%M.%S).sql.bz2`

Das Ganze konnen Sie nun noch in einen Cronjob packen und je nach Wunsch ausfuhren lassen. Ob das einmal in der Stunde, einmal pro Tag oder in einem anderen Rhythmus stattfindet, mussen Sie selbst entscheiden.

## 10ownCloud 8.2 und PHP 7

Ab ownCloud 8.2 unterstutzt die private Cloud PHP 7 offiziell. Aus Sicherheitsgrunden halten Vorgangerversionen bei PHP 7 an, da dies nicht getestet ist. Man will somit eventuelle Schaden vermeiden. Die Entwickler haben Performance-Tests mit ownCloud 8.2 und PHP 7 durchgefuhrt und enorme Steigerungen geegnuber PHP 5.x verzeichnet. Allerdings ist PHP 7 noch sehr jung.

![PHP 7: Mit der neueste PHP-Version lässt sich die Performance deutlich verbessern ](http://images.cio.de/images/computerwoche/bdb/2708434/840x473.jpg)

> _PHP 7: Mit der neueste PHP-Version lasst sich die Performance deutlich verbessern_

PHP 7 ist allerdings in Ubuntu 14.04 LTS per Standard nicht enthalten. Entweder konnen Sie den Quellcode selbst kompilieren oder ein sogenanntes PPA verwenden. Beide Herangehensweisen sind allerdings mit Risiken verbunden. Sie sollten auf jeden Fall ausgiebige Tests durchfuhren, bevor Sie sich fur einen solchen Schritt entscheiden. Bei einem produktiven Einsatz ist es vernunftiger, konservativ zu sein. Das bedeutet, fur den Moment auf die Pakete aus den offiziell unterstutzten Repositories setzen und weiterhin PHP 5.x verwenden.
