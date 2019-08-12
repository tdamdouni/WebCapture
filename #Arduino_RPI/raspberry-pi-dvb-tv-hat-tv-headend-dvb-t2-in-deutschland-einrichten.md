# Raspberry Pi DVB TV HAT: TV Headend & DVB-T2 in Deutschland einrichten

_Captured: 2019-03-16 at 12:12 from [buyzero.de](https://buyzero.de/blogs/news/raspberry-pi-dvb-tv-hat-tv-headend-dvb-t2-in-deutschland-einrichten)_

![Raspberry Pi DVB TV HAT: TV Headend & DVB-T2 in Deutschland einrichten](https://cdn.shopify.com/s/files/1/1560/1473/articles/dvb-t-28_2048x.png?v=1545150482)

> _Anleitung fur DVB-TV HAT DVB-T2 Sender finden_

Die mitgelieferten Kanalllisten / Presets bei TVHeadend sind leider noch auf DVB-T ausgerichtet, so dass trotz funktionierendem Raspberry Pi DVB-TV HAT keine Sender gefunden werden.

Wir haben eine Software entwickelt, die unter [www.picockpit.com/dvb-t-tools](http://www.picockpit.com/dvb-t-tools) zur Verfugung steht, um das Problem zu beheben.

Hier eine kurze Anleitung, ausgehend von einem bereits missgluckten Scanversuch mit TVHeadend, bei dem keine Sender gefunden wurden. Falls bislang kein Versuch unternommen wurde, kann man einfach **Schritt 4** auslassen, alle anderen Schritte sind erforderlich.

# Schritt 1: Rufe DVB-T-Tools aus Picockpit auf

Gehen Sie im Webbrowser auf:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/picockpit-first-impression_large.png?v=1545149269)

Setzen Sie das Hackchen bei "Add all DVB-T2 frequencies (Germany)", und klicken Sie auf **Submit**

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-2_large.png?v=1545149266)

Es wird eine **aa-All.txt** heruntergeladen, die DVB-T2 Kanaldefinitionen enthalt, die die Suche mit TVHeadend ermoglichen werden.

**_Hinweis:_**_ es ist nicht notwendig, eine **w_scan** output file hochzuladen - das wurde zusatzlichen Aufwand bedeuten, und ist nur fur fortgeschrittene Nutzer, die sich ggf. auch nicht in Deutschland befinden, gedacht. Hilfe zum Vorgang mit w_scan kriegt man unter dem Knopf "_Help with w_scan_". In allen Fallen empfehlen wir Nutzern aus Deutschland das Hackchen bei "Add all DVB-T2 frequencies" zu setzen, da w_scan in unseren Tests bei weitem nicht alle Sender identifizieren konnte._

# Schritt 2: Lade aa-All.txt auf den Raspberry Pi hoch

Die Datei aa-All.txt muss in ein bestimmtes Verzeichnis auf dem Raspberry Pi.

Mogliche Vorgehensweisen:

  * Datei auf USB Stick kopieren, und dann am Raspberry Pi in das Verzeichnis schieben.
  * SSH am Raspberry Pi aktivieren, Datei per WinSCP auf Raspberry Pi kopieren
  * Datei in Schritt 1 mit Webbrowser am Raspberry Pi generieren und direkt herunterladen

Die Datei muss in den Ordner **/usr/share/dvb/dvb-t** gelegt werden. Sie konnen die Datei auch umbenennen, bspw. zu _de-DVBT2_ (de fur Deutschland). Im folgenden lassen wir den Dateinamen so wie er ist.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-4_large.png?v=1545149266)

Wichtig: der Ordner gehort root, daher mussen Sie das Kommando "mv" zum Verschieben als root ausfuhren (sudo mv)

Hinweis: ein Nutzer informierte mich dass bei ihm die Datei in den folgenden Ordner gelegt werden muss: **/usr/share/tvheadend/data/dvb-scan/dvb-t/** \- bitte probieren Sie diesen alternativen Ort aus, falls es nicht mit dem von mir getesteten funktioniert.

# Schritt 3: Neustart des Pi's

sudo reboot

# Schritt 4: TVHEADEND's Bisherige Kanal-Konfiguration Loschen

gehe in TVHeadend als admin Nutzer auf **Configuration**:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-5_large.png?v=1545149267)

Hinweis: TVHeadend ist unter der IP des Raspberry Pis und dem Port 9981 erreichbar (der Port wird bei IPv4 Adressen mit einem Doppelpunkt hinten angestellt)

klicke **DVB Inputs**

**![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-6_large.png?v=1545149267)**

Klicke **Networks**

![](https://cdn.shopify.com/s/files/1/1560/1473/files/tvheadend-networks_large.png?v=1545149941)

Markiere die vorhandenen Networks, und klicke **Delete**:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-8_large.png?v=1545149267)

Bestatige mit **Yes**:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-9_large.png?v=1545149267)

# Schritt 5: Neue Kanale anlegen und Suche starten

Klicke **Configuration -> General -> Base**.

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-10_large.png?v=1545149267)

Klicke **Start Wizard**:

Stellen Sie die Einstellungen entsprechend Ihrer Vorlieben ein:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-12_large.png?v=1545149267)

Klicke **Save & Next**

**![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-13_large.png?v=1545149267)**

Hinweis: hier werden Zugriffsrechte auf TVheadend gesetzt, insbesondere sollte man bei Pi's mit offentlichen IP-Adressen und ohne Firewall die erste Zeile ubearbeiten.

Die Admin und User logins sollten Sie nach eigenem Gutdunken einfullen, und sich die Daten notieren.

Klicke **Save & Next**

**![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-14_large.png?v=1545149268)**

Das ist ein wichtiger Dialog, bei dem aus den Drop Downs die richtigen Dinge ausgewahlt werden sollten.

Falls Network 2 (DVB-T) nicht auftaucht, prufen Sie bitte ob Sie die Networks in Schritt 4 korrekt geloscht haben.

Wahlen Sie aus den Dropdowns die Optionen wie folgt aus:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-15_large.png?v=1545149267)

Network type: DVB-T Network bei Sony CXD2880 #0 : DVB-T #0

Es ist **kein** Problem dass hier DVB-T und nicht DVB-T2 ausgewahlt wird, sondern ist so beabsichtigt.

Klicke **Save & Next**

**![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-16_large.png?v=1545149268)**

In diesem Dialog mussen die Muxe richtig ausgewahlt werden.

Dazu diente die Datei die wir in Schritt 1 und 2 richtig positioniert haben. Man kann sie ganz unten aus dem Dropdown auswahlen:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-17_large.png?v=1545149268)

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-18_large.png?v=1545149268)

Falls man die Datei in Schritt 2 umbenannt hat, sollte man entsprechend nach dem anderen Namen suchen.

Wichtig: die vordefinierten Muxe fur Deutschland (de-xxx) funktionieren NICHT fur DVB-T2, da hier uberall DVB-T Definitionen drinstehen. aa-All.txt hat DVB-T2 Definitionen!

Klicke **Save & Next**

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-19_large.png?v=1545149268)

In diesem Dialog sollte man etwas Geduld mitbringen, wahrend TVheadend die Services findet.

Es sollten idealerweise mit wachsendem Fortschritt mehr services gefunden werden:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-20_large.png?v=1545149268)

Wichtiger Hinweis:

Sollten hier keine Services gefunden werden, sollten Sie die Antenne / Verbindung zum Pi prufen. Und idealerweise mit einem vorhandenen DVB-T2 Tuner vergleichen.

Wir haben gute Erfahrungen mit der Amazon Basics Antenne gemacht:

**<https://www.amazon.de/gp/product/B078HF3NM2/>**

Nach Abschluss des Scans sollten eine Reihe Services gefunden worden sein:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-21_large.png?v=1545149268)

Klicke **Save & Next**

**![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-22_large.png?v=1545149268)**

Hier sollten alle Hackchen gesetzt werden:

Klicke **Save & Next**

**![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-24_large.png?v=1545149268)**

Klicke **Finish**

# Schritt 6: TV Schauen

Es ist jetzt moglich Fernsehen zu schauen.

Beispielsweise so: **Configuration -> DVB Inputs -> Services**

**![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-25_large.png?v=1545149268)**

Klick auf das Play Icon:

es wird eine Datei heruntergeladen:

Diese Datei kann mit einem aktuellen VLC (ab Version 3.0.0) geoffnet werden:

![](https://cdn.shopify.com/s/files/1/1560/1473/files/dvb-t-28_large.png?v=1545149270)

Der PC sollte entweder Hardware Codecs fur H.265 besitzen, oder uber entsprechend Leistung (altere Gerate).

# Hinweise

In Deutschland wurde, im Gegenzug zu vielen anderen Landern, bei DVB-T2 auf H.265 als Videocodec gewechselt. Das hat leider zur Folge, dass der Raspberry Pi die deutschen Videostreams in den meisten Fallen nicht direkt wiedergeben kann (der Raspberry Pi hat nur H.264 / MPEG-4 und MPEG-2 in Hardware als Codecs eingebaut). Die CPU des Pi 3B+ reicht nur fur ca. SD Auflosungen zum Dekodieren.

**D.h. der Raspberry Pi ist in Deutschland leider nur zum Streamen und Aufzeichnen von DVB-T2 Fernsehen geeignet.**

Im Netzwerk kann mit jedem geeigneten Gerat auf den Stream zugegriffen werden.

## 0 Kommentare
