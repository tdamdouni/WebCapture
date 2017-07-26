# Die eigene Cloud für Mac-Anwender in 45 Minuten einrichten mit Owncloud

_Captured: 2017-04-02 at 22:05 from [www.maclife.de](http://www.maclife.de/ratgeber/eigene-cloud-mac-anwender-45-minuten-einrichten-owncloud-10088952.html)_

Sie wollen jederzeit von uberall Zugriff auf Ihre Daten? Das ist kein Problem mit ownCloud am Mac! Wir zeigen Ihnen im Workshop, wie es funktioniert. Es dauert nur knapp 45 Minuten und Sie lernen, wie Sie "Back to my Mac" und ownCload einrichten und nutzen. Sie benotigen außerdem eine AirPort Extreme oder Time Capsule mit externer Festplatte oder ein NAS beziehungsweise Raspberry Pi mit ownCloud.

  * ![ownCloud am Mac einrichten](http://www.maclife.de/media/maclife/styles/tec_frontend_large/public/images/editors/2017_07/image-88952--170525.jpg?itok=tTaxi31-)

> _ownCloud am Mac einrichten_

Sie nutzen Apples iCloud Drive, Microsofts OneDrive, sind Kunde beim Cloud-Speicher-Platzhirschen Dropbox oder bei einem der zahlreichen Konkurrenten? Dann wissen Sie schon, was die großen Vorteile der Datensammlung in der Cloud sind. Zunachst einmal werden Ihre Daten an einem anderen Ort aufbewahrt und sind sicher, selbst wenn Ihr Mac beschadigt oder gestohlen wird. Außerdem sorgen Cloud-Speicher dafur, dass Sie Ihre Daten auf mehreren Systemen ohne großen Aufwand synchron halten konnen und dafur, dass Sie von praktisch uberall darauf zugreifen konnen.

Naturlich gibt es auch Schattenseiten. Wenn Sie große Datenmengen auf diese Weise sichern wollen, bezahlen Sie unter Umstanden viel Geld dafur. Außerdem steht die Vertrauensfrage im Raum: Wem konnen Sie Ihre Daten wirklich anvertrauen, ohne dass Sie fruher oder spater in die Hande Dritter gelangen? Und: Wie lange wird es den Dienst uberhaupt geben, bevor der Anbieter ihn wieder einstellt oder geschluckt wird - und dann vielleicht dazu gezwungen wird, den eigenen Dienst in einem Produkt der neuen Mutterfirma aufgehen zu lassen?

Falls Sie die Pro-Argumente verlockend finden, die Kontra-Argumente Sie aber bislang vom Schritt in die Cloud abhalten, dann lautet die Antwort: betreiben Sie doch einfach Ihre eigene Cloud!

Wenn sie eine AirPort Extreme oder eine AirPort Time Capsule besitzen, bietet die Funktion „Back to my Mac" einen einfachen Weg, um von unterwegs an Ihre Daten zu gelangen. Wenn Sie die Funktionen von iCloud replizieren mochten, kann ein fertig gekaufter Netzwerkspeicher (NAS) oder eine Eigenkonstruktion mit dem Mini-Computer [Raspberry Pi](http://www.maclife.de/thema/raspberry-pi) die Losung sein.

Zwar werden Ihre Daten dann nicht an einem anderen Ort, sondern bei Ihnen zuhause aufbewahrt, aber auch dort lassen sich sichere Platze finden.

![DS216+ von Synology ist ein NAS](http://www.maclife.de/media/maclife/styles/tec_frontend_large/public/images/editors/2017_07/021680b5-0541-3287-98da-99a34c7cf3ec-4584.jpg?itok=fp4TJfCL&c=09b2401b2e42f38dc62d7aca8ddd65b5)

> _DS216+ von Synology ist ein NAS_

## Die Apple-Losung

Unsere erste Alternative fur die private Cloud ist vor allem dann interessant fur Sie, wenn Sie bereits uber einen von Apples Routern (AirPort Extreme oder AirPort Time Capsule) verfugen. Diese Losung verhilft Ihnen zwar nicht zu allen Funktionen, die man von einer Cloud erwartet, lasst Sie aber immerhin von uberall auf eine an den AirPort-Router angeschlossene externe Festplatte zugreifen. Zum Beispiel mittels freigegebener Ordner. Standardmaßig limitiert Apple den Datenzugriff auf Rechner, die sich im selben Netzwerk befinden. Nach der Aktivierung von „Back to my Mac", das Apple auf dem deutschen Markt inzwischen „Zugang zu meinem Mac" nennt, funktioniert das aber auch von außerhalb.

Die notigen Schritte um dieses Ziel zu erreichen sind - Apple-typisch - denkbar einfach: Wenn Sie die Festplatte eines Macs freigeben wollen, besuchen Sie auf diesem Mac die „Systemeinstellungen" und aktivieren Sie den Dienst unter „iCloud". Falls Sie eine Fehlermeldung erhalten, mussen Sie gegebenenfalls Ihren Router entsprechend konfigurieren, respektive die angeforderten Netzwerk-Ports freigeben.

„Back to my Mac" funktioniert aber auch mit Festplatten, die an einem AirPort-Router angeschlossen sind. Die Festplatte muss dafur mit Apples „Extended File System" formatiert werden (das erledigen Sie mit dem Festplattendienstprogramm Ihres Macs). Nachdem Sie die Festplatte mit Ihrem AirPort-Router verbunden haben, starten Sie das AirPort-Dienstprogramm, klicken Sie auf das Symbol Ihres Gerats. Auf dem Reiter „Basisstation" verbinden Sie „Back to my Mac" mit Ihrer Apple ID (bei Bedarf geht das auch mit mehreren Apple IDs). Als nachstes wahlen Sie den Reiter „Laufwerke" und aktivieren Sie die Dateifreigabe und die Freigabe ubers Internet (WAN) durch Setzen der entsprechenden Haken. Als letztes aktivieren Sie den Schutz des Laufwerks „Mit Accounts", um Nutzernamen und Passworter vergeben zu konnen.

Zum Schluss klicken Sie zwecks Sicherung der Änderungen auf „Aktualisieren". Der [AirPort-Router](http://www.maclife.de/thema/airport) startet neu und Sie konnen ab sofort auch von unterwegs auf die Daten der Festplatte zugreifen.

## Die Losung fur Profis und Bastler

Die Freigabe von Festplatten ist schon ganz nett. Wenn Sie mehr wollen, kommen Sie mit Apples AirPort-Losung jedoch nicht weiter und werden sich stattdessen mit der Cloud-Server-Losung „ownCloud" auseinandersetzen mussen. Mit ownCloud lassen sich viele der Dienste, die iCloud, Dropbox und Co. im Angebot haben, verhaltnismaßig einfach auf einem eigenen Server nachbilden - und das ganz ohne lastige monatliche Abo-Gebuhren.

Sie brauchen allerdings einen Computer, der Ihr Server wird. Das kann entweder ein NAS, das ownCloud unterstutzt (zum Beispiel die Gerate von Synology), ein alter PC mit Linux oder ein bei einem Webhoster wie Strato gemieteter Server sein. Als Linux-PC kann dabei auch ein einfacher Raspberry Pi 3 fungieren, den man auch mit kleinem Budget erstehen kann. Damit die Heim-Losung auch unterwegs gut funktioniert, brauchen Sie noch einen entsprechend breitbandigen Internetanschluss.

Wenn Ihr NAS ownCloud unterstutzt, konnen Sie den Dienst einfach uber den Paket-Manager installieren. Gleiches gilt fur gewohnliche Linux-PCs. Etwas anders lauft die Installation auf dem Raspberry PI. Sollte dies Ihr erstes Raspberry-Pi-Projekt sein, empfehlen wir diese Anleitung: bit.ly/owncloudpi. Stellen Sie dabei in jedem Fall sicher, dass Sie die Festplatte an Ihrem Raspberry Pi mit dem Dateiformat „ext3" versehen!

![Dynamische IP-Adresse beziehen Sie zum Beispiel bei Noip.](http://www.maclife.de/media/maclife/styles/tec_frontend_large/public/images/editors/2017_07/6ee7a01c-428d-9d4e-1293-4acd4d9dd8ff-4584.jpg?itok=sPZahNGQ)

> _Dynamische IP-Adresse beziehen Sie zum Beispiel bei Noip._

## Dateien synchronisieren

Nachdem Sie ownCloud erfolgreich installiert haben, folgen Sie einfach unserem Workshop auf dieser Seite, um den Server-Dienst zu konfigurieren. Außerdem sollten Sie den ownCloud-Client fur den Mac herunterladen, um einfacher auf Ihre Dateien zugreifen zu konnen und die standige Synchronisierung zu gewahrleisten.

ownCloud funktioniert im Wesentlichen so wie man es erwarten wurde, wenn man Dropbox kennt. Einige hilfreiche Tipps und Tricks zur Benutzen finden Sie trotzdem auf der vorherigen Doppelseite.

## Workshop: So richten Sie Ihren eigenen ownCloud-Server ein

![Die eigene Cloud für Mac-Anwender in 45 Minuten einrichten mit Owncloud](http://www.maclife.de/media/maclife/styles/tec_frontend_large/public/images/editors/2017_07/image-88952--170531.jpg?itok=6YM0mr3K)

## Schritt 1: 

Starten Sie einen Webbrowser Ihrer Wahl und geben Sie die IP-Adresse Ihres Linux-PC oder NAS gefolgt von einem „/owncloud" in die Adresszeile ein. Also beispielsweise 192.168.1.24/owncloud.

> _Die eigene Cloud fur Mac-Anwender in 45 Minuten einrichten mit Owncloud_
