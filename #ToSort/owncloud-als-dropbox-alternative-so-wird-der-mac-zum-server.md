# Owncloud als Dropbox-Alternative: So wird der Mac zum Server

_Captured: 2017-04-02 at 22:08 from [www.macwelt.de](http://www.macwelt.de/a/owncloud-als-dropbox-alternative-so-wird-der-mac-zum-server,3293933)_

![Mit Owncloud können Sie Ihre ganz persönliche Cloud auf dem Mac oder beliebigen anderen Webservern aufsetzen.](http://bilder.macwelt.de/3958700_620x310.jpg)

> _Mit Owncloud konnen Sie Ihre ganz personliche Cloud auf dem Mac oder beliebigen anderen Webservern aufsetzen._

** Sie haben einen Mac Mini als Media-Center-PC oder anderweitig ubrig und benotigen eine Cloud, die nicht nur leistungsstark ist, sondern auch ausreichend Speicherplatz bietet? Mit Owncloud auf dem Mac besitzen Sie alle notigen Voraussetzungen - ohne Zusatzkosten! **

Jeder Mac mit OS X ist ein leistungsstarker Unix-Rechner - und damit auch grundsatzlich als Webserver geeignet. [Mit dem notigen Handwerkszeug lasst sich mit wenigen Handgriffen ein Apache-Webserver samt PHP und MySQL-Datenbank unter OS X einrichten](http://www.macwelt.de/ratgeber/Mac-Server-MAMP-Fritzbox-9928122.html) . Anschließend kann dieser Webserver als private Cloud zu Hause arbeiten, alles, was Sie dafur benotigen, ist die Software [Owncloud](http://www.macwelt.de/news/Owncloud-7-verfuegbar-8825068.html) , die sich naturlich auch auf beliebigen anderen Webservern mit Apache, MySQL und PHP einrichten lasst, etwa auf einem Webspace. Im Folgenden wollen wir aber den Weg beschreiben, um einen Mac zum Owncloud-Server zu machen - und Daten wirklich sicher vor den Augen von NSA und Co. im eigenen Wohnzimmer abzulegen.

Sicher: Viele NAS-Systeme bieten ahnliche Funktionen, Synology-Systeme erlauben sogar die Owncloud-Installation - doch warum ein zusatzliches Gerat kaufen, wenn ein ohnehin vorhandener Mac die Aufgabe ubernehmen kann? Insbesondere, wenn der Mac sowieso installiert, per Ethernet-Kabel angebunden und im Dauerbetrieb eingesetzt wird, weil es sich um einen Mediaserver-Mac-Mini oder einen Wohnzimmer-Mac handelt, kann Owncloud hier als kleine Zusatzfunktion jederzeit praktische Dienste leisten.

## Was Owncloud leistet

Owncloud ist eine vollumfangliche Opensource-Cloud, die auf allen Systemen lauft, auf denen ein Webserver installiert ist. Neben der bereits erwahnten [NAS](http://www.macwelt.de/handover/1182) sind das auch kleinere Rechner, selbst der gute, kostengunstige [Raspberry Pi](http://www.macwelt.de/tipps/Airprint-Server-mit-Raspberry-Pi-selbst-bauen-9709024.html) lasst sich mit ein wenig Handarbeit als Cloud-Rechner einrichten. Owncloud unterstutzt dabei alle nur denkbaren Cloud-Funktionen: Vom reinen Dateiaustausch uber die Synchronisation ganzer Ordner wie bei Dropbox bis hin zur eigenen Bildergalerie im Netz, der Synchronisation von Kontakten und Kalendern, kollaborativem Arbeiten, der Wiedergabe von Musik und Filmen. Der Vorteil gegenuber Diensten wie iCloud, Dropbox, Google und Co. liegt dabei vor allem in der Sicherheit der Daten, wenn man die Cloud zu Hause hostet: Wahrend typische Cloud-Dienste mit Sitz in den USA einerseits selten die Verschlusselung der Daten auf dem Rechner anbieten, andererseits aber durch den Patriot Act gezwungen sind, Daten preiszugeben, auf die sie zugreifen konnen, sollten hier wichtige Daten wenn uberhaupt nur verschlusselt abgelegt werden. Selbst dann kann man aber nicht sicher sein, ob nicht irgendwelche Hinterturen oder Entschlusselungsversuche stattfinden. Sicher ist man nur, wenn man die Cloud selber hostet; genau das leistet Owncloud, wenn man die Software auf einem eigenen Rechner in den eigenen vier Wanden installiert - naturlich nur, wenn die Passworter sicher und die Daten regelmaßig per Backup gesichert werden und der Mac idealerweise per Kensington-Lock oder mit einem anderen Sicherungssystem in der Wohnung oder im Buro verankert ist.

## Owncloud in MAMP installieren

![](http://api-img.billiger.de/dynimg/TJiY05UADuVoovTbYUaSDBrdKcf9ij4HHDrU21LmKOZAF4c0q9hDHXGbFmV-6LhJ0XuaaVfDnOfHhUpZtcLCjdJpezjPzRxB0rdUCsxqYq3/575370200.jpg)

Richten Sie zunachst den MAMP-Server, den Sie unter [www.mamp.info](https://www.mamp.info/de/) herunterladen konnen, unter OS X ein. ( [Lesen Sie hier: Alten Mac als Server einrichten](http://www.macwelt.de/ratgeber/Mac-Server-MAMP-Fritzbox-9928122.html) ). Das System ist denkbar einfach, weil es alle notigen Funktionen direkt an Bord hat. Zwar besitzt OS X selbst auch einen Apache-Server, der umstandslos mit PHP und MySQL ausgerustet werden kann, die MAMP-Losung sorgt jedoch fur eine deutliche Erleichterung und obendrein hohere Performance, weil es sich um die jeweils aktuellsten Versionen der Server-Umgebung handelt. Wie Sie es machen, steht Ihnen naturlich frei - Sie konnen sowohl auf MAMP, als auch auf den internen Mac-Apache setzen. Ist alles aufgesetzt, ist Ihr Webserver zunachst unter [http://localhost:8888 ](http://localhost:8888
) lokal erreichbar. Websites mussen im Verzeichnis htdocs, das im MAMP-Ordner im Programme-Verzeichnis liegt, aufgesetzt werden. Laden Sie daher den Owncloud-Installer von der [Owncloud-Website](https://owncloud.org/install/#) herunter, hier sollte der „Owncloud-Server" als Web-Installer geladen werden, da es sich hierbei um die einfachste Methode handelt, einen Owncloud-Server in MAMP aufzusetzen. Die setup-owncloud.php wird dann einfach in den MAMP-Ordner „htdocs" gelegt. Von dort aus konnen Sie die Installation der Owncloud-Software auf dem Apache-Server im Browser unter der Adresse [http://localhost:8888/setup-owncloud.php ](http://localhost:8888/setup-owncloud.php
) starten.

![Owncloud kann kostenlos von der Owncloud-Website geladen werden.](http://bilder.macwelt.de/3958603_620x310.jpg)

## Installationsroutine durchlaufen

Da das MAMP-Serverpaket fertig voreingestellt ist, mussen Sie nun nur noch die Installation durchlaufen lassen: Nach dem Aufruf des Installers starten Sie die Installation mit „Next".

![Mit dem Setup-Wizard ist die Owncloud-Installation ein Kinderspiel.](http://bilder.macwelt.de/3958607_620x310.jpg)

> _Mit dem Setup-Wizard ist die Owncloud-Installation ein Kinderspiel._

Anschließend mussen Sie nur noch angeben, ob Sie Owncloud direkt in htdocs oder lieber in einem Unterverzeichnis installieren mochten. Die Vorauswahl, das Verzeichnis „owncloud", ist sinnvoll und sollte verwendet werden. Anschließend dauert die eigentliche Installation je nach Geschwindigkeit der Internetverbindung - die Owncloud-Dateien werden vom Installer aus dem Netz geladen - kann das einige Minuten dauern.

![Die Setup-Routine lädt nun alle Dateien herunter, was eine Weile dauern kann.](http://bilder.macwelt.de/3958608_620x310.jpg)

> _Die Setup-Routine ladt nun alle Dateien herunter, was eine Weile dauern kann._

Das war es auch schon: Sobald die Installation abgeschlossen ist, ist Owncloud installiert. Praktischerweise verwendet die Software von selbst [die Datenbank SQLite](https://www.sqlite.org) , wodurch zunachst keine weiteren Einrichtungsschritte mit MySQL notig sind. Allerdings empfiehlt sich der Einsatz der solideren MySQL-Datenbank, sobald Sie etwas umfangreichere Projekte mit Owncloud starten. Fur einen Testlauf auf dem Mac reicht naturlich zunachst die Basisversion - wenn Sie mehr vor haben, sollten Sie jedoch direkt auf die MySQL-Datenbank wechseln. Wie das geht, wird im Folgenden erklart.

![Erfolg! Owncloud wurde auf dem Mac installiert!](http://bilder.macwelt.de/3958610_620x310.jpg)

> _Erfolg! Owncloud wurde auf dem Mac installiert!_

## Administratorkonto anlegen

Im nachsten Schritt warnt Owncloud, dass es von OS X nicht richtig unterstutzt wird - eine Fehlermeldung, die Sie jedoch ignorieren konnen. Fur die weitere Verwendung verlangt Owncloud das Anlegen eines Administrator-Kontos. Geben Sie einen Benutzernamen und ein [sicheres (!) Passwort](http://www.macwelt.de/ratgeber/Sicherheit-verstehen-Daten-schuetzen-7847121.html) ein, schließlich wird Owncloud moglicherweise in Kurze Ihre wichtigen Daten enthalten. Eine ausreichende Lange und Komplexitat - Sonderzeichen wie „#" und „$" nicht vergessen - sorgen dafur, dass Angreifer nur geringe Chancen haben, das Passwort zu knacken.

![Die Warnmeldung können Sie getrost ignorieren. Wenn Sie nicht auf MySQL setzen möchten, können Sie Owncloud nun schon verwenden.](http://bilder.macwelt.de/3958613_620x310.jpg)

> _Vergroßern Die Warnmeldung konnen Sie getrost ignorieren. Wenn Sie nicht auf MySQL setzen mochten, konnen Sie Owncloud nun schon verwenden._

## Optional: Datenbank-System auf MySQL wechseln

Wer vom Start weg eine solide Datenbankverbindung haben mochte, kann mit einem Klick auf „Speicher & Datenbank" bereits hier auf eine MySQL-Datenbank umschwenken, was empfehlenswert ist. Rufen Sie dazu in einem neuen Browserfenster noch einmal die MAMP-Startseite ( [http://localhost:8888/MAMP/?language=German ](http://localhost:8888/MAMP/?language=German
) ) auf und wahlen Sie hier phpMyAdmin ( [http://localhost:8888/MAMP/index.php?page=phpmyadmin&language=German ](http://localhost:8888/MAMP/index.php?page=phpmyadmin&language=German
) ): Sie werden in die MySQL-Umgebung weitergeleitet. Legen Sie hier im Reiter „Benutzer" einen neuen User namens „owncloud" auf Localhost an und vergeben Sie fur ihn ein Passwort. Haken Sie „Erstelle eine Datenbank mit gleichem Namen…" und „Gewahre alle Rechte auf Datenbanken…" sowie unter Globale Rechte „Alle auswahlen" an. Bestatigen Sie anschließend mit „OK".

Bei diesem Vorgang wird automatisch auch eine neue SQL-Datenbank namens „owncloud" angelegt - diese konnen Sie jetzt fur Owncloud verwenden. Wechseln Sie daher einfach zuruck auf das Browser-Tab mit der Owncloud-Einrichtung und klicken Sie auf „Speicher & Datenbank". Geben Sie hier den MySQL-Benutzernamen, den Sie oben angelegt haben, zusammen mit der gleichnamigen Datenbank und dem Passwort des Benutzers ein.

![Die Einrichtung einer MySQL-Datenbank für Owncloud ist, auch wenn sie komplex erscheint, recht einfach.](http://bilder.macwelt.de/3958614_620x310.jpg)

> _Die Einrichtung einer MySQL-Datenbank fur Owncloud ist, auch wenn sie komplex erscheint, recht einfach._

## Installation abschließen

Doch egal, ob Sie auf die einfachere Losung mit der SQLite-Datenbank setzen oder Ihr ganzes Owncloud-System lieber von vornherein mit einer eigenen MySQL-Datenbank auf solide Fuße stellen: Um die Installation fertig zu stellen, mussen Sie nun noch auf „Installation abschließen" klicken.

![Die Einrichtung der MySQL-Datenbank ist nicht zwingend, sorgt aber für einen stablieren Betrieb und erspart später den umständlichen Umbau des Owncloud-Systems.](http://bilder.macwelt.de/3958615_620x310.jpg)

> _Vergroßern Die Einrichtung der MySQL-Datenbank ist nicht zwingend, sorgt aber fur einen stablieren Betrieb und erspart spater den umstandlichen Umbau des Owncloud-Systems._

Die Installation der Owncloud-Systems auf dem Mac ist damit abgeschlossen: Wenn keine Fehlermeldung auftritt, sondern Sie die Owncloud-Startseite mit dem Hinweis auf die Owncloud-Apps fur OS X, iOS und Android sehen, ist Ihr Owncloud-Server nun eingerichtet und einsatzbereit - Sie mussen jetzt nur noch dafur sorgen, dass er auch von außen erreichbar ist und moglichst zuverlassig arbeitet. Wie das geht, erfahren Sie in den nachsten Schritten.

![Die Einrichtung über Localhost hat geklappt – nun muss die Cloud nur noch Ihren Weg nach draußen finden.](http://bilder.macwelt.de/3958616_620x310.jpg)

> _Die Einrichtung uber Localhost hat geklappt - nun muss die Cloud nur noch Ihren Weg nach draußen finden._

## Owncloud von außen erreichbar machen

Nun geht es ans Eingemachte: Ihr Owncloud-Server ist zwar aktiv, jedoch derzeit nur in Ihrem Netzwerk erreichbar. Sie mussen jetzt dafur sorgen, dass Sie auch von außen auf ihn zugreifen konnen, was Sie am einfachsten uber die Portfreigabe Ihres Routers erledigen konnen. Wir spielen diesen Schritt an dieser Stelle beispielhaft an einer Fritz!Box durch, allerdings funktioniert das naturlich auch mit besseren Routern anderer Hersteller. Öffnen Sie zunachst die Router-Administration in einem neuen Browser-Fenster, loggen Sie sich ein und wahlen Sie unter „Internet -> Freigaben" den Reiter „Portfreigaben". Hier mussen Sie die Ports 8888 und 8889 fur MAMP und MySQL an den Computer freigeben, auf dem das MAMP-System lauft. Zusatzlich konnen Sie noch unter „Internet -> Freigaben" im Router einen dynamischen DNS-Dienst wie [No-IP.com](http://www.noip.com) aufsetzen, um Probleme mit wechselnden IP-Adressen zu vermeiden. Dazu mussen Sie sich ein kostenloses Benutzerkonto bei dem Dyn-DNS-Dienst erstellen und die Daten anschließend im Reiter „Dynamic DNS" eintragen.

![Damit der Server überhaupt mit der Außenwelt kommunizieren kann, muss er per Portfreigabe ans Internet durchgereicht werden.](http://bilder.macwelt.de/3958622_620x310.jpg)

> _Vergroßern Damit der Server uberhaupt mit der Außenwelt kommunizieren kann, muss er per Portfreigabe ans Internet durchgereicht werden._

Nun konnen Sie bereits von außen unter der Adresse **http://(Ihre-externe-IP-Adresse):8888/owncloud/** per LTE vom iPhone/Smartphone aus auf Ihre Owncloud-Installation zugreifen, um zu testen, ob die Verbindung grundsatzlich funktioniert. Allerdings klappt das nun erst einmal nur halb: Zwar offnet sich eine Owncloud-Seite mit einem Warnhinweis, allerdings fuhrt jeder Klick ins Nirwana. Schuld ist Ownclouds Sicherheitseinstellung: Der Domainname beziehungsweise die IP-Adresse mussen erst als vertrauenswurdige Domains eingetragen werden. Das dient der Sicherheit der Owncloud, da sie nicht aus versehen durch falsche Domainnamen erreicht werden kann. Das spielt in Heimnetzwerken keine so große Rolle, auf Servern, die mehrere Websites hosten, ist diese Einstellung jedoch essentiell.

![Die Trusted-Domains-Funktion von Owncloud verhindert zunächst einen Zugriff von außen.](http://bilder.macwelt.de/3958621_620x310.jpg)

> _Die Trusted-Domains-Funktion von Owncloud verhindert zunachst einen Zugriff von außen._

Um diese Sperre zum Umgehen, mussen Sie die Datei „config.php" innerhalb des Config-Verzeichnisses des Owncloud-Ordners (der unter (/htdocs/ im MAMP-Ordner liegt) bearbeiten, etwa mit dem [kostenlosen und hervorragenden Text-Editor Tincta](http://www.mr-fridge.de/software/tincta/) . Richten Sie hier sowohl die aktuelle externe IP-Adresse, als auch eventuelle DynDNS-Weiterleitungen ein, indem Sie in der Zeile

in der Klammer hinter „array" die Domainnamen eintragen, etwa die Domain und die IP-Adresse, unter der Ihr Owncloud-Server von außen erreichbar ist, zum Beispiel „ owncloud.no-ip.com " oder „74.12.34.53". Die Zeile muss anschließend so aussehen, beachten Sie dabei die einfachen Anfuhrungszeichen:

![Mit dem Text-Programm Tincta lassen sich die Codezeilen für Owncloud eintippen.](http://bilder.macwelt.de/3958629_620x310.jpg)

> _Mit dem Text-Programm Tincta lassen sich die Codezeilen fur Owncloud eintippen._

Anschließend konnen Sie die config.php speichern und schließen. Die Domainnamen, unter denen Owncloud erreichbar ist, sind nun in der Konfigurationsdatei eingepflegt. Wenn Sie nun erneut Ihre IP-Adresse oder die DynDNS-Adresse per LTE mit dem Smartphone aufrufen, erscheint der Login-Bildschirm von Owncloud: Herzlichen Gluckwunsch, Ihre personliche Cloud ist jetzt vom Internet aus erreichbar und einsatzbereit. Sollte das nicht klappen, mussen Sie gegebenenfalls die Portnummer mit angeben, etwa: [http://owncloud.no-ip.com:8888/owncloud ](http://owncloud.no-ip.com:8888/owncloud
) oder ahnlich, basierend auf Ihrer individuellen Konfiguration. Owncloud auf dem Mac arbeitet und ist von außen erreichbar.

![Wenn die Domain richtig eingetragen ist, klappt auch der Zugriff von außen auf den Owncloud-Server. Wird ein Login-Fenster angezeigt, hat alles wie geplant funktioniert.](http://bilder.macwelt.de/3958628_620x310.jpg)

> _Vergroßern Wenn die Domain richtig eingetragen ist, klappt auch der Zugriff von außen auf den Owncloud-Server. Wird ein Login-Fenster angezeigt, hat alles wie geplant funktioniert._

## Wake-on-LAN am Router einstellen

Nun sind noch einige kleine Einrichtungsschritte am Mac notig, um den Owncloud-Server fur den Dauerbetrieb vorzubereiten: Sie mussen dafur sorgen, dass der Mac nicht einschlaft und, falls er es doch tut, wieder aufgeweckt wird, wenn Sie sich von außen mit der Cloud verbinden. Stellen Sie daher sicher, dass Sie in der Einstellung „Heimnetz" des Fritz-Routers am Owncloud-Rechner die Option „Wake on LAN" aktiviert haben. Auf diese Weise weckt der Router - vorausgesetzt, er ist per Ethernet-Kabel am Mac angebunden - den Rechner auf, sobald Sie von außen darauf zugreifen. Per WLAN funktioniert Wake-on-LAN nicht, außer, Sie setzen einen Airport-Router von [Apple](http://www.macwelt.de/handover/66) ein. Grundsatzlich ist die Anbindung eines Servers per WLAN aber nicht sinnvoll, die Kabelverbindung zwischen Server-Mac und Router ist also Pflicht.

![Mit der Wake-on-LAN-Funktion des Routers können Sie einen per Ethernet-Kabel angebundenen Rechner automatisch aufwecken, sobald vom Netzwerk aus auf ihn zugegriffen wird.](http://bilder.macwelt.de/3958658_620x310.jpg)

> _Vergroßern Mit der Wake-on-LAN-Funktion des Routers konnen Sie einen per Ethernet-Kabel angebundenen Rechner automatisch aufwecken, sobald vom Netzwerk aus auf ihn zugegriffen wird._

## Energiespar-Optionen am Mac einstellen

Zusatzlich sollten Sie den Mac aber so einstellen, dass er sich gar nicht erst schlafen legt. Öffnen Sie dazu auf dem Rechner die Systemeinstellungen und dort den Eintrag „Energie sparen". Hier mussen Sie einen Haken bei „Ruhezustand bei Netzwerkzugriff beenden" setzen, um dafur zu sorgen, dass der Router den Mac auch aufwecken darf.

![Allerdings setzt WOL voraus, dass die Option auch auf dem Mac aktiviert ist, sonst passiert nichts.](http://bilder.macwelt.de/3958660_620x310.jpg)

> _Allerdings setzt WOL voraus, dass die Option auch auf dem Mac aktiviert ist, sonst passiert nichts._

## MAMP-Autostart einrichten

Zuguterletzt mussen Sie noch dafur sorgen, dass auch der MAMP-Server bei jedem Rechnerstart automatisch gestartet wird. Das erreichen Sie, indem Sie zunachst in der MAMP-Oberflache die Einstellungen offnen und hier im Reiter „Start/Stopp" einen Haken bei „Beim Starten von MAMP: Starte Server" setzen. Zusatzlich mussen Sie MAMP aber noch bei den Anmeldeobjekten hinzufugen, damit der Apache-Server und die Datenbank auch automatisch starten, wenn der Rechner neu startet, etwa nach einem Stromausfall. Öffnen Sie dazu die Systemeinstellungen, wahlen Sie „Benutzer & Gruppen", rufen Sie Ihren Standardbenutzer auf und fugen Sie im Reiter „Anmeldeobjekte" mit dem „+"-Symbol die MAMP-App aus dem Programme-Ordner hinzu. Falls Sie statt auf MAMP lieber auf die interne OS-X-Losung fur Apache setzen, ist dieser Schritt ubrigens nicht notig, der Apache-Server ist aktiv und lauft nach jedem Neustart automatisch mit. Der Mac ist jetzt an die Anforderungen fur den Dauerbetrieb angepasst. Vergessen Sie auch nicht, eine externe Festplatte anzuhangen und [Time-Machine-Backups](http://www.macwelt.de/ratgeber/Time-Machine-OS-X-Backup-Mac-wiederherstellen-konfigurieren-8996407.html) einzurichten.

![Mit den richtigen Einstellungen startet MAMP/Owncloud nach einem Stromausfall oder Neustart automatisch zusammen mit dem Mac neu.](http://bilder.macwelt.de/3958661_620x310.jpg)

> _Vergroßern Mit den richtigen Einstellungen startet MAMP/Owncloud nach einem Stromausfall oder Neustart automatisch zusammen mit dem Mac neu._

![Die Einrichtung der App ist kinderleicht: Alles, was Sie tun müssen, ist die Owncloud-URL sowie Benutzername und Passwort des Owncloud-Nutzers anzugeben.](http://bilder.macwelt.de/3958674_620x310.jpg)

> _Vergroßern Die Einrichtung der App ist kinderleicht: Alles, was Sie tun mussen, ist die Owncloud-URL sowie Benutzername und Passwort des Owncloud-Nutzers anzugeben._

## Owncloud fertig einrichten

Nun, da alles fertig eingerichtet ist, konnen Sie sich unter **http://(meine-IP-Adresse oder DynDNS):8888/owncloud** mobil oder direkt von Ihrem Rechner aus auf Ihrer personlichen Cloud einloggen und ein wenig mit der Software herumspielen. Es gibt hier viele praktische Optionen, so konnen Sie zum Beispiel Benutzer anlegen, Dateien hoch und herunterladen oder Dateien freigeben. Sie konnen den Kalender-Sync einrichten, Musik hochladen und viele andere Dinge. Wichtig ist ubrigens noch, in den Einstellungen die serverseitige Verschlusselung zu aktivieren: Auf diese Weise sorgen Sie dafur, dass die Cloud-Daten selbst dann, wenn der Mac entwendet wird, nicht in fremde Hande geraten konnen. Naturlich durfen Sie dann Ihr Passwort nicht vergessen. Sinnvoll ist zudem die Einrichtung von zusatzlichen Benutzern mit eingeschranktem Zugriff: Der anfangs eingerichtete Nutzer ist der Administrator, der Vollzugriff auf alle Daten und Einstellungen hat: Der Sicherheit halber sollten Sie fur sich (und fur alle anderen, die den Owncloud-Server kunftig nutzen mochten) eigene Benutzer mit eingeschrankten Rechten anlegen. Zuguterletzt sollten Sie naturlich auch das Passwort fur den Standardnutzer Root Ihrer MySQL-Datenbank andern: Dieses lautet in der Standardkonfiguration ebenfalls „root" und ist dementsprechend unsicher. Wie Sie es andern konnen, finden Sie in der [Dokumentation des MAMP-Servers](https://www.mamp.info/de/dokumentation/) . Die Regeln zur Passwortsicherheit gelten naturlich auch fur alle anderen Passworter, die auf dem Mac oder dem Router verwendet werden.

![Es ist sinnvoll, die serverseitige Verschlüsselung der Owncloud zu aktivieren. Alle Passwörter auf dem System und dem Router sollten natürlich ausreichend sicher sein, um Fremdzugriff zu verhindern.](http://bilder.macwelt.de/3958659_620x310.jpg)

> _Vergroßern Es ist sinnvoll, die serverseitige Verschlusselung der Owncloud zu aktivieren. Alle Passworter auf dem System und dem Router sollten naturlich ausreichend sicher sein, um Fremdzugriff zu verhindern._

![Nach dem Login können Sie Ihre Owncloud ausgiebig ausprobieren.](http://bilder.macwelt.de/3958675_620x310.jpg)

> _Nach dem Login konnen Sie Ihre Owncloud ausgiebig ausprobieren._

## Apps auf Mobilgerat installieren

An diesem Punkt ist es ubrigens sinnvoll, [die 99 Cent fur die Owncloud-App fur iOS](https://itunes.apple.com/us/app/owncloud/id543672169?mt=8) beziehungsweise [79 Cent fur die Owncloud-App fur Android](https://play.google.com/store/apps/details?id=com.owncloud.android) auszugeben und diese auf dem Smartphone zu installieren und einzurichten. Auf diese Weise konnen Sie bequem von unterwegs Ihr eigenes Foto-Backup auf Ihre Owncloud laden, auf Dateien auf dem Server zugreifen oder Dateien hochladen und mit anderen Nutzern - auch offentlich - teilen.
