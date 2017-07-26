# So installierst du Kodi auf dem Raspberry Pi 3 – Die ultimative Schritt-für-Schritt Anleitung

_Captured: 2017-05-22 at 11:08 from [powerpi.de](http://powerpi.de/so-installierst-du-kodi-auf-dem-raspberry-pi-2-die-ultimative-schritt-fuer-schritt-anleitung/comment-page-1/)_

![Raspberry Pi 2 Kodi \(XBMC\) Installation Anleitung](http://powerpi.de/wp-content/uploads/2015/02/header_installation_raspberry_pi2_kodi-700x329.jpg)

**Mit dem neuen Raspberry Pi 3 wird das Media-Center System Kodi jetzt noch besser!  
**

Auf dem Raspberry Pi 2 lief Kodi bereits sehr flussig und stabil, dank dem neuen leistungsstarkeren Quad-Core-Prozessor der 64-Bit-Architektur sowie dem integrierten WLAN und Bluetooth wird Kodi auf dem Pi 3 zu einem noch schoneren Erlebnis.

Da man sich jetzt einen separaten WLAN Adapter sparen kann, wird das ganze System zudem auch noch gunstiger.

Kodi lauft auf dem Raspberry Pi 3 butterweich und spielt so gut wie jede Videodatei absolut flussig ab. Das mag man vielleicht fur selbstverstandlich halten doch haben viele Android-Boxen (z.B. FireTV Stick) so ihre Probleme mit einer wirklich flussigen Video-Wiedergabe. Der Raspberry Pi ist also ideal auch fur anspruchsvolle Benutzer geeignet, die viel Wert auf eine ruckelfreie Video-Wiedergabe legen.

In diesem Tutorial zeige ich dir wie du Kodi in wenigen einfachen Schritten auf deinem Pi 3 installierst und welche Grundeinstellungen man zu Beginn vornehmen sollte.

Besondere Kenntnisse sind nicht von noten, diese Anleitung richtet sich an all diejenigen die Spaß an der Technik haben und gerne basteln.

Als Betriebssystem verwenden wir [OpenELEC](http://openelec.tv/), da dieses das einzige System ist, dass ausschließlich fur den Einsatz als Media Center optimiert wurde. Das bedeutet, dass dort wirklich nur Funktionen enthalten sind, die du fur dein Media Center benotigst, unnotiger Ballast entfallt. Das hat Performance Vorteile und ist auch dadurch auch weniger fehleranfallig.

Genug geredet, legen wir los!

## Was wird benotigt?

![](http://powerpi.de/wp-content/uploads/2015/02/kodi_raspberry_pi_3_installation.jpg)

Hardware Empfehlung

Raspberry Pi 3 Model B
[45,00 €](http://powerpi.de/raspberry-pi-3)

hochwertiges Netzteil (5V, 2A)
[ 11,39 €](http://www.amazon.de/gp/product/B00GM0305Y/ref=as_li_tl?ie=UTF8&camp=1638&creative=19454&creativeASIN=B00GM0305Y&linkCode=as2&tag=pow07-21)

Micro SD-Karte (mindestens 1GB)
[ 6,49 €](http://www.amazon.de/gp/product/B00M55C0VU/ref=as_li_tl?ie=UTF8&camp=1638&creative=19454&creativeASIN=B00M55C0VU&linkCode=as2&tag=pow07-21&linkId=4ZK63R5KYS5Y7Q5L)

HDMI-Kabel mit CEC Unterstutzung
[ 5,99 €](http://www.amazon.de/gp/product/B014I8SIJY/ref=as_li_tl?ie=UTF8&camp=1638&creative=19454&creativeASIN=B014I8SIJY&linkCode=as2&tag=pow07-21)

**[Optional]** beliebiges Gehause
[zur Übersicht](http://powerpi.de/der-grosse-raspberry-pi-2-gehaeuse-test-vom-guenstigen-china-case-bis-zum-zum-high-end-aluminium-gehaeuse/)

**[Optional]** Micro SD Kartenleser
[ 6,99 €](http://www.amazon.de/gp/product/B00JO9RJS4/ref=as_li_tl?ie=UTF8&camp=1638&creative=19454&creativeASIN=B00JO9RJS4&linkCode=as2&tag=pow07-21&linkId=QLVIBKBRJEFDBYRR)

**[Optional]** Funk-Tastatur oder Fernbedienung
[14,90 €](http://www.amazon.de/gp/product/B001DZOMI2/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&camp=1638&creative=6742&creativeASIN=B001DZOMI2&linkCode=as2&tag=pow07-21)

Da der Raspberry Pi 3 uber die Fahigkeit „CEC" verfugt, kannst du auch deine Fernbedienung vom Fernseher nutzen um Kodi zu steuern. Dabei werden die Signale deiner Fernbedienung uber das HDMI Kabel an den Pi 3 ubergeben. Vorausgesetzt du hast das richtige HDMI-Kabel mit CEC Unterstutzung und auch einen Fernseher der ebenfalls diese Technik beherrscht.

Falls du gerne bastelst und dir deine Fernbedienung perfekt nach deinen Vorstellungen einrichten mochtest, dann empfehle ich dir diesen Artikel „[Jede Fernbedienung nutzen und perfekt einrichten"](http://powerpi.de/jede-infrarot-fernbedienung-am-raspberry-pi-2-nutzen-so-installierst-du-guenstig-einen-ir-empfaenger-teil-1/).

Es gibt aber auch noch smartere Wege deinen Pi zu steuern wie z.B. mit [dieser App](https://play.google.com/store/apps/details?id=org.leetzone.android.yatsewidgetfree&hl=de) fur Android.

Bei der Micro SD-Karte sollte man auf eine schnelle Class 10 Karte setzen da, sich eine langsamere Karte negativ auf die Bootzeit auswirkt kann.

Auch beim Netzteil sollte man auf Qualitat achten. Billige Netzteile liefern oft nicht die angegebene Leistung und haben auch mal Stromschwankungen die zur Instabilitat deines Pi's fuhren kann. Erspare dir unnotigen Stress und Fehlersuche und setze auf ein hochwertiges Netzteil.

## 1\. OpenELEC Image herunterladen

Auf der Downloadseite von OpenELEC kannst du dir das Image fur den Raspberry Pi 3 herunterladen. Du musst auf der Seite ein wenig runter scrollen um es zu finden.

Achte darauf, dass du das Diskimage auswahlst, wie auf dem unteren Screenshot zu sehen.

![](http://powerpi.de/wp-content/uploads/2015/02/openelec_image_download_raspberry_pi_3.png)

> _Entpacke anschließend die .gz Datei um eine .img Datei zu erhalten, denn nur diese konnen wir flashen._

**Wichtig: **

## 2\. Disk Image Tool herunterladen

Dieses kleine Programm benotigst du um das OpenELEC Image auf deine SD-Karte zu schreiben.

Es erstellt automatisch 2 Partitionen auf deiner SD-Karte.

Lade es dir herunter und installiere das Tool.

## 3\. OpenELEC auf die Micro SD-Karte schreiben

Starte den Disk Imager, wahle die OpenELEC Image-Datei aus und wahle den Laufwerksbuchstaben deiner SD-Karte aus. Drucke anschließend auf „Write", bestatige die darauf kommende Warnmeldung mit „Yes" und warte bis der Kopiervorgang abgeschlossen wurde.

![](http://powerpi.de/wp-content/uploads/2015/02/win32_disk_imager_kodi_flashen.png)

## 4\. Installation abschließen

Du hast das Media-Center Betriebssystem OpenELEC erfolgreich auf deine SD-Karte geschrieben.

Nun kannst du die Karte sicher vom PC entfernen und sie an deinem Raspberry Pi in Betrieb nehmen.

Beim ersten Start wird noch die volle Große deiner SD-Karte nutzbar gemacht, danach startet der Pi noch einmal neu und es erscheint Kodi.

## Optimale Einstellungen vornehmen

### Erster Start, Grundeinstellungen vornehmen

Beim aller ersten Start wirst du gebeten einige Voreinstellungen vorzunehmen. Um dich mit deinem WLAN-Netzwerk verbinden zu konnen, musst du eine USB Tastatur anschließen. Beachte dabei, dass deine Tastatur standardmaßig das englische Layout benutzt. Sonderzeichen sind dadurch anders belegt und die Buchstaben Z&Y sind vertauscht. Falls du damit nicht zurecht kommst, kannst du den Schritt mit der WLAN-Verbindung vorerst uberspringen und das Tastaturlayout in den [Openelec-Einstellungen auf deutsch](http://powerpi.de/wp-content/uploads/2015/02/screenshot_tastaturlayout_englisch_deutsch_stellen.jpg) stellen.

Im letzten Schritt wirst du noch gefragt welche Dienste aktiviert werden sollen. Es ist empfehlenswert den SSH-Dienst zu aktivieren damit wir spater vollen Zugriff auf unser System haben. Der Samba Dienst sorgt dafur dass du uber das Netzwerk auf die freigegebenen Ordner auf dem Raspberry zugreifen kannst.

![openelec_ssh_aktivieren](http://powerpi.de/wp-content/uploads/2015/02/openelec_ssh_aktivieren.jpg)

### Kodi auf deutsch stellen

Du benotigst fur diesen Schritt eine aktive Internetverbindung da Kodi die Sprachdateien erst nach dem auswahlen herunterladt.

Unter **System -> Appearance -> International **->** Language **kannst du die Sprache auf deutsch stellen.

![kodi_auf_deutsch_stellen](http://powerpi.de/wp-content/uploads/2015/02/kodi_auf_deutsch_stellen.jpg)

### Zeitzone einstellen damit die Uhrzeit stimmt

Im selben Menu wo wir die Sprache geandert haben, stellen wir jetzt auch gleich die richtige Zeitzone ein, damit die Uhrzeit richtig angezeigt wird.

Unter **„Zeitzonen-Region"** wahlst du **„German" **aus, dann stimmt auch die Uhrzeit wieder.

![kodi_zeitzone_uhrzeit_einstellen](http://powerpi.de/wp-content/uploads/2015/02/kodi_zeitzone_uhrzeit_einstellen.jpg)

### Flussiges Menu bei Videowiedergabe

Wenn ein Video lauft und man zuruck ins Kodi Menu geht und das Video im Hintergrund weiter laufen lasst, dann ruckelt das Menu stark. Warum das standardmaßig so eingestellt ist weiß ich nicht genau, doch es stort sehr und der Raspberry hat genug Power um das Menu auch wahrend einer Videowiedergabe flussig darzustellen. Selbst der Pi 2 konnte das bereits problemlos.

Stellen wir diese Limitierung also einfach ab. Unter **Optionen -> Video -> Beschleunigung -> Aktualisierung der Benutzeroberflache begrenzen **wahlen wir „unbeschrankt" aus. Damit du diesen Menupunkt siehst, musst du wie im Screenshot zu sehen unter Punkt 1, die Einstellungsebene auf „Fortgeschritten" stellen.

![kodu_menu_ruckelt_abstellen_raspberry_pi](http://powerpi.de/wp-content/uploads/2015/02/kodu_menu_ruckelt_abstellen_raspberry_pi.jpg)

## Wie geht es weiter?

Der Anfang ist gemacht, Kodi ist installiert und die wichtigsten Einstellungen wurden vorgenommen doch der Spaß beginnt jetzt erst.

Wenn du Kodi das erste mal nutzt dann mache dich mit dem System erst einmal vertraut. Schaue dir einfach alles mal an, installiere Video-Addons wie z.B. Youtube, Twitch & Co. Schließe eine Festplatte mit Videoinhalten an und spiele sie ab. Du kannst auch ganz einfach auf freigegebene Ordner in deinem Netzwerk zugreifen und Video/Musik-Material von dort aus abspielen.

Mit Openelec und dem Raspberry Pi hast du soeben auch den Grundstein fur ein wunderschones[ Ambilight System](http://powerpi.de/atemberaubendes-ambilight-am-eigenen-tv-selber-bauen-raspberry-pi-2-tutorial-teil-1/) gelegt.

Mochtest du deine Filme und Serien auch so schon prasentieren wie [hier in den Screenshots](http://powerpi.de/screenshots/) zu sehen, dann empfehle ich dir als nachstes diese Anleitung:
