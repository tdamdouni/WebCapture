# Abenteuer Installation Samsung ML-2525W

_Captured: 2015-10-09 at 09:33 from [spacewater.blogspot.de](http://spacewater.blogspot.de/2010/08/abenteuer-installation-samsung-ml-2525w.html)_

Der Samsung ML-2525W ist ein s/w-Laserdrucker mit USB 2.0-, LAN- und WLAN-Schnittstelle. Eigentlich ein optimale Losung, wenn man von verschiedenen Rechnern aus drucken mochte, ohne Kabel zu verlegen, und auch kein Kabel zwischen Router und Drucker sein soll. Der Drucker kann im Empfangsbereich des WLANs praktisch uberall stehen, wo es eine Steckdose gibt.

Im vorliegenden Fall wollte ich den ML-2525W uber eine FRITZ!Box Fon WLAN 7270 installieren, so dass er von allen Rechnern, die mit der Fritz-Box uber LAN oder WLAN verbunden sind, erreichbar sind. Der Drucker sollte ausschließlich uber WLAN mit der Fritz-Box kommunizieren, da er in einem anderen Raum aufgestellt werden soll und eine Kabelverbindung nicht moglich ist. Leider lasst sich die Installation weder mit der beigefugten Gebrauchsanleitung noch mit der beiliegenden Installations-Software durchfuhren.

Zuerst einmal habe ich mir eine vollstandige Gebrauchsanleitung gesucht, diese ist nach einer kleinen Recherche [hier](http://downloadcenter.samsung.com/content/UM/201003/20100305152415656/DE/german/start_here.htm) zu finden. Leider ist die Anleitung wenig hilfreich und nur fur jemanden geeignet, der Erfahrungen mit Netzwerken und der Installation von Druckern hat. Wer kennt beispielsweise den Unterschied zwischen dem Infrastrukturmodus und dem Ad-hoc-Modus? Das wird in der Anleitung zwar kurz erklart, aber so, dass es fur Laien nicht verstandlich ist. Das schrittweise Abarbeiten der Anleitung bringt aber uberhaupt nichts, weil sich so der Drucker mit der beiliegenden Installationssoftware nicht installieren lasst.  
[**Update **16.03.2014: Die Gebrauchsanleitung kann [hier](http://www.samsung.com/de/support/model/ML-2525W/SEE-downloads#aManual) heruntergeladen werden.]

Deswegen hier ein paar Tipps, wie ich es trotzdem geschafft habe:

1\. Ggf. muss bei dem Computer, von dem aus die Installation vorgenommen wird, die Firewall vorubergehend deaktiviert werden.

2\. Beim Recherchieren habe ich den [Tipp](http://nuetzlichesundwenigernuetzliches.blogspot.com/2010/07/samsung-ml-2525w-und-fritzbox-fon-wlan.html) gefunden, dass die SSID (der Name des WLAN) keine Leer- oder Sonderzeichen enthalten darf. Leider enthalt die SSID bei der Fritz-Box standardmaßig sowohl Leerzeichen als auch ein Ausrufezeichen. Nach dem Umbenennen mussen alle Gerate im WLAN neu gestartet und der WLAN-Netzwerkschlussel eingegeben werden.

3\. Damit der Drucker funktioniert, muss er eine IP-Adresse aus dem Bereich des WLAN haben, also bei der Fritz-Box normalerweise 192.168.178.XXX (XXX steht fur eine beliebige Zahl zwischen 21 und 255). Dazu steht auf der Installations-CD wie in der Anleitung beschrieben, im Ordner das Programm SetIP zur Verfugung. Man kommt an das Programm, wenn man im Arbeitsplatz mit der rechten Maustaste "Öffnen" wahlt. Bei mir hat SetIP nicht uber die USB-Verbindung, mit der ansonsten die Verbindung vorgenommen wird, funktioniert. Erst als ich den Drucker uber LAN-Kabel mit der Fritz-Box verbunden habe, konnte ich die Änderungen wie in der Anleitung beschrieben vornehmen. Dazu sind folgende Angaben notwendig:  
Die MAC-Adresse des Druckers. Diese lasst sich ermitteln, indem man ca. 5 sec. auf die Taste "Abbrechen" (rotes Dreieck) druckt. Hier sieht man auch die bestehende IP-Adresse, die standardmaßig nicht 192.168.178.XXX lautet. Die MAC-Adresse des Druckers ist ohne Doppelpunkte nur mit den Hexadezimal-Zeichen 0123456789ABCDEF einzugeben.  
Die IP-Adresse, die dem Drucker zugewiesen werden soll. Hier kann man in der Fritz-Box nachsehen, ob der Drucker bereits angemeldet ist (der Geratename enthalt die MAC-Adresse). Wenn beispielsweise der Drucker bereits die 192.168.178.31 hat, kann man diese Adresse eintragen. Dazu einfach auf der Startseite der Konfigurationssoftware der Fritz-Box auf "WLAN" klicken. Wenn noch keine IP-Adresse zugeordnet ist, kann man beispielsweise 192.168.178.99 nehmen. Eine relativ hohe IP-Adresse ist deswegen ratsam, weil IP-Adressen eindeutig sein mussen. Hat der Drucker die IP-Adresse 192.168.178.25 und ist ausgeschaltet, konnte es sein, dass ein neues Notebook im WLAN diese Adresse uber DHCP zugewiesen bekommt. Soll anschließend gedruckt werden und der Drucker wird eingeschaltet, gibt es einen Konflikt mit den IP-Adressen.  
Als Subnetzmaske 255.255.255.0 eintragen.  
Standard-Gateway ist die IP-Adresse der FritzBox, also normalerweise 192.168.178.1. Theoretisch konnte jetzt schon gedruckt werden, allerdings noch nicht uber WLAN.

4\. Fur den folgenden Schritt muss die LAN-Verbindung zwischen Drucker und Fritz-Box bestehen bleiben. Auf einem Computer im Browser die IP-Adresse des Druckers aufrufen. Es offnet sich das Programm SyncThru Web Service. Das Programm wird in der Anleitung unter "Verwaltungsprogramme" beschrieben. Hier muss jetzt unter "Netzwerkeinstellungen" das WLAN aktiviert werden. Dazu gibt es einen Assistenten, der die notwendigen Einstellungen vornimmt. Anschließend kann das LAN-Kabel entfernt werden.

5\. Der folgende Schritt muss auf jedem Compunter ausgefuhrt werden, von dem aus gedruckt werden soll: Über die Systemsteuerung einen neuen lokalen Drucker hinzufugen. Bei "Plug & Play-Drucker automatisch ermitteln und installieren" darf kein Hakchen gesetzt sein. Nach Klick auf "Weiter" einen neuen Anschluss erstellen, und zwar "Standard TCP/IP Port". Als Druckername oder IP-Adresse kann einfach die IP-Adresse des Druckers eingetragen werden. Anschließend wird der Druckertreiber von der Installations-CD installiert. Um beim den automatischen Start der Installations-Software beim Einlegen der CD zu verhindern, die SHIFT-Taste (Umschalter) gedruckt halten. Anschließend sollte sich eine Testseite drucken lassen.  
[**Update **16.03.2014: Der letzte Schritt lasst sich inzwischen automatisiert erledigen, wenn der Treiber "Win 2000/XP/2003/ Vista/2008/Win 7(32,64bit)" [hier](http://www.samsung.com/de/support/model/ML-2525W/SEE-downloads#aDriver) heruntergeladen und installiert wird.]

6\. Zum Schluss nicht vergessen, die Firewall wieder einzuschalten!

FAZIT: Der ML-2525W sieht gut aus und druckt schnell und in guter Qualitat zu einem vernunftigen Preis. Die Installation ist allerdings mit mit der beigefugten Gebrauchsanleitung und der beiliegenden Installations-Software nicht moglich. Wenn ich meine Arbeitszeit rechne, bis der Drucker uber WLAN lief, betragt diese deutlich mehr als der Kaufpreis des Druckers. Mir ist unverstandlich, wieso Samsung bei diesem an sich guten Gerat bei Dokumentation und Software spart. Deswegen: Klare Kaufempfehlung - aber nur fur Experten! 