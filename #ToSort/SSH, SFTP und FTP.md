# SSH, SFTP und FTP

_Captured: 2015-11-06 at 14:18 from [wiki.schokokeks.org](https://wiki.schokokeks.org/SSH,_SFTP_und_FTP)_

## Was ist der Unterschied

Das SSH-Protokoll (**s**ecure **sh**ell) beschreibt eine Methode zum verschlusselten Zugriff auf entfernte Rechner. Mittels SSH ist die Bedienung eines fremden Rechners so moglich als wurde man selbst an diesem sitzen (»remote console«). Dabei ist sowohl die Übertragung als auch die Anmeldung stark verschlusselt und nicht von Dritten mitlesbar. Als zusatzlichen Komfort, besteht die Moglichkeit, sich mit [SSH-Key](https://wiki.schokokeks.org/Key-Login_\(OpenSSH\)) anzumelden.

SFTP ist eine Datei-Übertragungs-Technik, die direkt auf dem SSH-Zugriff aufbaut und daher die Verschlusselung von SSH mitbenutzt.

Das traditionelle FTP-Zugriffs-Verfahren bietet dagegen von Haus aus keine Moglichkeit einer Verschlusselung. Die Konzeption des FTP-Protokolls erschwerte es lange Zeit, eine sinnvolle Verschlusselung nachzurusten. Auch daher haben wir zu Beginn bewusst vollstandig auf FTP-Zugriffe verzichtet. Zwischenzeitlich wurde mit der _FTPES_ genannten Technik eine vollumfangliche Verschlusselung in das FTP-Protokoll eingebaut. Daher bestehen jetzt keine weiteren Bedenken, FTP einzusetzen. Der Zugriff muss aber zuerst aktiviert werden und es muss ein Programm eingesetzt werden, das wirklich auch FTPES beherrscht.

## FTP-Zugriff

Bitte beachten Sie: Wir erlauben nur verschlusselten Zugriff mittels des FTPES-Protokolls (_FTP explicit security_). Nicht alle FTP-Programme beherrschen dieses Verfahren. Es wird jedoch nur bei diesem Verfahren sicher gestellt, dass sowohl Ihre Anmeldedaten als auch die ubertragenen Dateien zuverlassig geschutzt werden.

Eine Liste der FTPES-fahigen Client-Programme befindet sich z.B. [in der Wikipedia](http://de.wikipedia.org/wiki/FTP_%C3%BCber_SSL). Im Zweifel versuchen Sie es bitte mit dem Programm _[FileZilla_](http://www.filezilla.de/download.htm), das fur alle verbreiteten Plattformen frei verfugbar ist, und der Angabe _ftpes://[hostname]_ im Feld _Host_ (z.B. _ftpes://zucker.schokokeks.org_).

Bevor Sie Ihren Zugang uber FTP benutzen konnen, mussen Sie dies aktivieren. Im Webinterface steht Ihnen diese Einstellung zur Verfugung. Es ist auch moglich, zusatzliche FTP-Benutzer anzulegen, die dann nur auf einzelne Unterverzeichnisse Zugriff erhalten.

Sofern Sie lediglich selbst auf Ihre Dateien zugreifen, sollten Sie auf FTP verzichten und das SFTP-Protokoll nutzen. Bei der Bedienung bzw. dem Komfort mittels FileZilla macht dies keinen Unterschied. Eine Anleitung zur Nutzung von FileZilla mittels SFTP befindet sich [auf einer separaten Wiki-Seite](https://wiki.schokokeks.org/FileZilla).

## SSH- / SFTP-Clients

### Portabel (verfugbar fur Windows, Linux und Mac OS X)

[FileZilla](http://filezilla.sourceforge.net) ist ein freies und sehr einfaches und ubersichtliches Dateiubertragungs-Programm, das mehrere Zugangsformen unterstutzt. FileZilla beherrscht auch SFTP und FTPES, welche wir bei schokokeks.org anbieten.

[Anleitung zur Nutzung von FileZilla](https://wiki.schokokeks.org/FileZilla).

### Linux (teilweise auch Mac OS X)

scp ist das Standard-Programm auf jedem Unix-System mit OpenSSH.
    
    
    scp quelldatei.txt server:pfad
    scp server:pfad/quelldatei.txt /lokaler/pfad
    scp -r quellordner/ server:
    scp -r server:/home /tmp
    

Eine der bequemsten Moglichkeiten, die eigene Homepage aktuell zu halten, ist _[rsync](http://samba.org/rsync/)_. _rsync_ ist ein Programm zum Synchronisieren von beliebigen Verzeichnissen und es kann genauso lokal oder uber eine SSH-Verbindung arbeiten.

Angenommen, die lokale Kopie der Homepage (die man bearbeitet) liegt unter _/var/www/blablub.de_ und die offentliche Version (die synchronisiert werden soll) liegt unter _zucker.schokokeks.org:websites/blablub.de_, dann konnte der rsync-Befehl so aussehen:
    
    
    rsync --quiet --recursive --links --safe-links --perms --rsh="ssh -q" --delete \
          --compress  /var/www/blablub.de/ zucker.schokokeks.org:websites/blablub.de/
    

Damit wurde die Seite exakt so gespiegelt wie sie lokal vorliegt.

Wenn man nun online bestimmte Daten hat, die beim update nicht geloscht oder uberschrieben werden sollen, dann kann man diese _\--exclude [pattern]_ explizit ausschließen. Die Hilfeseite, die man mit _man rsync_ lesen kann, gibt noch einige weitere Beispiele und Informationen dazu her.

[lftp](http://lftp.yar.ru/) ist ein sehr machtiges FTP Programm fur die Konsole. Es unterstutzt SFTP und viele andere FTP Protokolle. Um sich zu schokokeks.org zu verbinden einfach den folgenden Befehl verwenden ("benutzername" durch den eigenen Benutzernamen ersetzen):

Ähnlich wie rsync verfugt lftp uber gute Mirror (Spiegeln von Daten) Funktionen.

lftp kann auch mit ftpes umgehen. Allerdings gilt das nur, wenn lftp gegen gnutls oder gegen eine aktuelle Beta-Version von openssl 1.0.0 gelinkt ist. Mit einer aktuellen openssl-version (0.9.8) funktioniert ftpes nicht. Die Debian-Pakete von lftp sind gegen gnutls gelinkt, fur Gentoo-Nutzer empfielt es sich, lftp mit USE="gnutls" zu kompilieren.

Die Dateimanager von [GNOME](http://www.gnome.org/) und [KDE](http://www.kde.org/) beherrschen ebenso SFTP/SCP. Wenn man **sftp://zucker.schokokeks.org/** in der Adresszeile eingibt, verbinden sich die Dateimanager auf schokokeks.org.

Nautilus bringt seit der Version 2.6 den _spacial mode_ mit. Das bedeutet, dass keine Adresszeile vorhanden ist. Entweder man tippt nun jedes mal **ctrl + l** und dann **sftp://zucker.schokokeks.org** oder man wahlt **Datei ---> Server verbinden** und enthalt hernach ein Icon auf dem Desktop, mit welchem man sich per Doppelklick auf den Keks verbinden kann.

Beim Konqueror besteht ebenfalls die Moglichkeit, per **fish://zucker.schokokeks.org/** zuzugreifen. Dabei wird dann kein SFTP sondern SSH direkt genutzt. Fur unseren Server ist es egal (SFTP ist im Zweifel zu bevorzugen), bei anderen konnte SFTP deaktiviert sein.

Leider gibt es fur die Windows-Welt noch nicht so den Drang nach erhohter Sicherheit, daher ist die Nachfrage (und damit wiederum das Angebot) an SSH-Clients nicht allzu groß. Dennoch gibt es auch hier vernunftige Clients, die eine Benutzung genau so einfach machen wie mit FTP.

[WinSCP](http://winscp.sourceforge.net/eng/) ist ein SFTP/SCP-only-Client, der Keylogin unterstutzt und einen SSH-Agent mitbringt. Wir haben auch eine [Anleitung zur Benutzung](https://wiki.schokokeks.org/WinSCP).

Der wohl bekannteste SSH-Client fur Windows ist [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/).

Im Unterschied zu den oben genannten ist Putty kein Client um Dateien zu kopieren sondern zum besagten Fernzugriff mit einer Konsole. Der ganze Komfort, den eine Linux-Konsole bietet, ist mit Putty nutzbar, es lassen sich damit aber keine Dateien ubertragen.

Es gibt auch das Programm PSCP (vom selben Autor) zum Kopieren von Dateien, da es aber (siehe oben) bessere Alternativen gibt, sei davon abgeraten.
