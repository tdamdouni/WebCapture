# Canonical Ubuntu: Sicherheitsoptimierten FTP-Server unter Ubuntu einrichten

_Captured: 2016-05-06 at 08:57 from [workshop.tecchannel.de](http://workshop.tecchannel.de/a/sicherheitsoptimierten-ftp-server-unter-ubuntu-einrichten,3277761?qle=rssfeed_)_

Der FTP-Server, der den erhohten Sicherheitsanforderungen Rechnung tragt, nennt sich _vsftpd_. Die Abkurzung steht fur _Very Secure File Transfer Protocol Daemon_. Das Programm gilt nicht nur als besonders resistent gegenuber Angriffen, sondern soll selbst hohe Last muhelos schultern.

Der FTP-Server ist in den offiziellen Ubuntu-Paketquellen enthalten und lasst sich uber das Software-Center oder in der Konsole mit dem Befehl _sudo apt-get install vsftpd_ installieren. Anschließend ist vsftpd uber den Aufruf von ftp://<IP-Adresse des Rechners oder localhost> erreichbar. Standardmaßig konnen sich alle lokalen User mit ihrem Ubuntu-Passwort anmelden, wohingegen ein anonymes Einloggen deaktiviert ist.

  1. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818)  
Die komfortabelste Moglichkeit, vsftpd zu installieren, fuhrt uber das Software-Center von Ubuntu.
  2. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,2)  
Dort geben Sie in die Suchmaske den Name des Tools ein, markieren den Treffer und klicken auf "Installieren".
  3. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,3)  
Um zu sehen, ob der Server auch lauft, melden Sie sich einfach mit einem lokalen User-Account an.
  4. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,4)  
Anschließend sehen Sie alle Dateien und Ordner, auf die Ihr Account zugreifen darf. Besitzt das Konto Root-Rechte, konnen Sie frei auf dem Rechner navigieren.
  5. **[Ubuntu**](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,5)  
Anpassen lasst sich der FTP-Server uber die Konfigurationsdatei "vsftpd.conf". Laden Sie sie mit Admin-Berechtigung in einen Editor, wie hier in den Gnome-Editor gedit.
  6. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,6)  
Fur die Anpassung der zahlreichen Optionen sollten Sie sich Zeit nehmen. Per Default ist das Login lokaler Nutzer gestattet, wahrend eine anonyme Anmeldung deaktiviert ist.
  7. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,7)  
Alle Optionen inklusive kurzer Erklarungen finden Sie auf der vsftpd-Homepage.

Jetzt gilt es noch, die Einstellungen des Servers gemaß den eigenen Wunschen anzupassen. Das geschieht uber eine Konfigurationsdatei, die Sie in einen Editor Ihrer Wahl laden. Wenn Sie Gnome bevorzugen, geben Sie in ein Terminal den Befehl _sudo gedit /etc/vsftpd.conf_ ein. Dadurch offnen Sie das File mit Admin-Berechtigung, sodass Sie es auch andern konnen.

Der Aufbau von vsftpd.conf ist recht einfach. Jede Zeile ist entweder eine Anweisung oder ein Kommentar. Letzeren erkennen Sie an dem vorangestellten Nummernzeichen #. Anweisungen besitzen hingegen das Format _Option=Wert_. Eine Aufstellung aller Konfigurationsmoglichkeiten samt Erlauterungen finden Sie auf der offiziellen [Webprasenz](https://security.appspot.com/vsftpd/vsftpd_conf.html) von vsftpd.

Nachdem Sie die gewunschten Änderungen durchgefuhrt haben, denken Sie daran, den Server neu zu starten. Dazu dient das Kommando _sudo service vsftpd restart_.

  


Der FTP-Server, der den erhohten Sicherheitsanforderungen Rechnung tragt, nennt sich _vsftpd_. Die Abkurzung steht fur _Very Secure File Transfer Protocol Daemon_. Das Programm gilt nicht nur als besonders resistent gegenuber Angriffen, sondern soll selbst hohe Last muhelos schultern.

Der FTP-Server ist in den offiziellen Ubuntu-Paketquellen enthalten und lasst sich uber das Software-Center oder in der Konsole mit dem Befehl _sudo apt-get install vsftpd_ installieren. Anschließend ist vsftpd uber den Aufruf von ftp://<IP-Adresse des Rechners oder localhost> erreichbar. Standardmaßig konnen sich alle lokalen User mit ihrem Ubuntu-Passwort anmelden, wohingegen ein anonymes Einloggen deaktiviert ist.

  1. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818)  
Die komfortabelste Moglichkeit, vsftpd zu installieren, fuhrt uber das Software-Center von Ubuntu.
  2. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,2)  
Dort geben Sie in die Suchmaske den Name des Tools ein, markieren den Treffer und klicken auf "Installieren".
  3. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,3)  
Um zu sehen, ob der Server auch lauft, melden Sie sich einfach mit einem lokalen User-Account an.
  4. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,4)  
Anschließend sehen Sie alle Dateien und Ordner, auf die Ihr Account zugreifen darf. Besitzt das Konto Root-Rechte, konnen Sie frei auf dem Rechner navigieren.
  5. **[Ubuntu**](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,5)  
Anpassen lasst sich der FTP-Server uber die Konfigurationsdatei "vsftpd.conf". Laden Sie sie mit Admin-Berechtigung in einen Editor, wie hier in den Gnome-Editor gedit.
  6. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,6)  
Fur die Anpassung der zahlreichen Optionen sollten Sie sich Zeit nehmen. Per Default ist das Login lokaler Nutzer gestattet, wahrend eine anonyme Anmeldung deaktiviert ist.
  7. **[Ubuntu **](http://workshop.tecchannel.de/g/ubuntu-sicherheitsoptimierten-ftp-server-einrichten,38818,7)  
Alle Optionen inklusive kurzer Erklarungen finden Sie auf der vsftpd-Homepage.

Jetzt gilt es noch, die Einstellungen des Servers gemaß den eigenen Wunschen anzupassen. Das geschieht uber eine Konfigurationsdatei, die Sie in einen Editor Ihrer Wahl laden. Wenn Sie Gnome bevorzugen, geben Sie in ein Terminal den Befehl _sudo gedit /etc/vsftpd.conf_ ein. Dadurch offnen Sie das File mit Admin-Berechtigung, sodass Sie es auch andern konnen.

Der Aufbau von vsftpd.conf ist recht einfach. Jede Zeile ist entweder eine Anweisung oder ein Kommentar. Letzeren erkennen Sie an dem vorangestellten Nummernzeichen #. Anweisungen besitzen hingegen das Format _Option=Wert_. Eine Aufstellung aller Konfigurationsmoglichkeiten samt Erlauterungen finden Sie auf der offiziellen [Webprasenz](https://security.appspot.com/vsftpd/vsftpd_conf.html) von vsftpd.

Nachdem Sie die gewunschten Änderungen durchgefuhrt haben, denken Sie daran, den Server neu zu starten. Dazu dient das Kommando _sudo service vsftpd restart_.
