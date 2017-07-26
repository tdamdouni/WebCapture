# Mit Siri und FHEM das gesamte Smart Home per Stimme steuern

_Captured: 2015-11-10 at 21:43 from [www.meintechblog.de](http://www.meintechblog.de/2015/10/mit-siri-und-fhem-das-gesamte-smart-home-per-stimme-steuern/)_

![Hey Siri schalte die Deckenlampe in der Kueche an](http://www.meintechblog.de/wordpress/wp-content/uploads/2015/10/Hey-Siri-schalte-die-Deckenlampe-in-der-Kueche-an-200x200.jpg)

> _Hey Siri schalte die Deckenlampe in der Kueche an_

"Hey Siri, schalte das Licht in der Kuche ein."

Wer einmal seine Stimme verwendet hat, um **Lampen**, **Rollos** oder auch die **Heizung** im eigenen Smart Home zu steuern, wird sich ein Schmunzeln kaum verkneifen konnen (kleiner Vorgeschmack [hier](https://youtu.be/TLoHhDcxxjs)). Damit das funktioniert, konnen entweder offizielle und HomeKit-kompatible Gerate angeschafft oder uber einen kleinen Umweg auch die bereits per **FHEM** angebundenen Devices mit der praktischen **Siri**-Funktion nachgerustet werden.

Welche Schritte dafur notwendig sind, um einen FHEM-Server auf Basis eines Raspberry Pi 2 mit dem HomeKit-Feature aufzurusten, der sich kunftig mit iPhone und Co. steuern lasst, wird in nachfolgendem Howto erklart.

### FHEM-Server auf RPI2 als Grundlage

Voraussetzung ist eine FHEM-Installation auf einem Raspberry Pi 2, wie im Artikel [FHEM-Server auf dem Raspberry Pi in einer Stunde einrichten](http://www.meintechblog.de/2013/05/fhem-server-auf-dem-raspberry-pi-in-einer-stunde-einrichten/) beschrieben. Grundsatzlich funktioniert die Einrichtung auch auf anderen Plattformen wie einem Intel NUC und Ubuntu, wie im Artikel [Intel NUC als Smart Home-Server - FHEM on steroids](http://www.meintechblog.de/2014/05/intel-nuc-als-smart-home-server-fhem-on-steroids/) erklart, hierbei konnen sich jedoch unter Umstanden einzelne Konsolenbefehle unterscheiden.

Daruber hinaus ist es naturlich sinnvoll bereits einige Aktoren und Sensoren am FHEM-Server angelernt sein, welche kunftig uber Siri angesteuert werden sollen. Wie man Lampen, Jalousien oder Heizungsadapter einbinden kann, wurde dabei bereits in mehreren Blogposts beschrieben, z.B. im den Artikeln [Philips hue - So klappt die Integration in FHEM](http://www.meintechblog.de/2014/11/philips-hue-so-klappt-die-integration-in-fhem/), [Die HUE-Alternative: Preiswert die Lichtstimmung im Smart Home pimpen](http://www.meintechblog.de/2014/05/die-hue-alternative-preiswert-die-lichtstimmung-im-smart-home-pimpen/), [HowTo: Elektrische Rolladen per FHEM und HomeMatic automatisieren](http://www.meintechblog.de/2015/07/howto-elektrische-rollaeden-per-fhem-und-homematic-automatisieren/) und [FHEM: Heizungssteuerung per Anwesenheitserkennung](http://www.meintechblog.de/2013/12/fhem-heizungssteuerung-per-anwesenheitserkennung/).

Bevor mit den weiteren Schritten gestartet wird, sollte die vorhandene FHEM-Installation am besten gesichert werden, um im Fall der Falle auf ein Backup mit den wichtigen Konfigurationsdateien zuruckgreifen zu konnen. Wie das umgesetzt werden kann, wird bspw. im Artikel [FHEM HowTo - Automatisches Backup auf externem NAS](http://www.meintechblog.de/2015/05/fhem-howto-automatisches-backup-auf-externem-nas/) erklart. Weiterhin sollte FHEM mit der eingebauten Update-Funktion auf den neuesten Stand gebracht werden, wie im Artikel [FHEM-Server updaten](http://www.meintechblog.de/2014/11/fhem-server-updaten/) beschrieben.

### FHEM-Server und Gerate fur Anbindung vorbereiten

Damit alle unterstutzten Gerate spater korrekt in der HomeKit-Datenbank korrekt erkannt werden, wird das bereits existierende "global userattr" in der fhem.cfg um den Eintrag "genericDeviceType:switch,outlet,light,blind,speaker,thermostat" erganzt.

In meinem Beispiel wird der bisherige Eintrag in der fhem.cfg:

erganzt und sieht nach der Änderung dann so aus:

Jetzt noch auf "Save fhem.cfg" klicken, um die Änderung dauerhaft zu speichern.

Um klein zu starten, sollten im ersten Schritt nur wenige Devices fur die Anbindung mit HomeKit ausgewahlt werde, um sich etwas mit der Materie vertraut zu machen und Anfangsfehler zu minieren. Dazu werden die ausgwahlten Gerate in den neuen FHEM-Raum namens "Homekit" platziert, um eine Auswahl zu treffen. Nur diese Gerate werden dann berucksichtigt.

In diesem Fall wird der [HomeMatic Unterputz-Schaltaktor (Affiliate-Link)](http://www.amazon.de/eQ-3-HomeMatic-Funk-Schaltaktor-Unterputzmontage-Universal/dp/B007VTYVSA?tag=meintechblog-151025-21) ausgewahlt, welcher fur die Ansteuerung der Deckenbeleuchtung in der Kuche zustandig ist und nun mit dem neuen Raum "Homekit" versehen wird.

![KU.Deckenlampe hinzufuegen zu room Homekit](http://www.meintechblog.de/wordpress/wp-content/uploads/2015/10/KU.Deckenlampe-hinzufuegen-zu-room-Homekit-550x437.jpg)

> _Alternativ lasst sich die Raumzuweisung auch direkt uber die FHEM-Kommandozeile uber den Befehl_

bewerkstelligen. Im Anschluss wird die geanderte Konfiguration uber den Button "Save config" gespeichert.

### RPI2 zum FHEM-HomeKit-Server aufrusten

Nach diesen vorbereiten Schritten geht es nun ans Eingemachte, da der FHEM-Server mit den notwendigen Softwarebibliotheken ausgestattet werden muss, welche fur den Betrieb des HomeKit-Servers namens Homebridge zustandig sind.

Dazu erfolgt der ssh-Login per Terminal (mehrfach in alteren Blogposts erklart) mit

Die IP-Adresse des Raspberry Pi 2 muss naturlich jeder selbst anpassen. Sofern nicht geandert, lautet das Standardpasswort gewohnlich "raspberry" (ohne Anfuhrungszeichen).

Jetzt werden die Softwarepaketliste geupdated und die notwendigen Unterpakete installiert, welche fur das Kompilieren des im Anschluss installierten node-gyp notwendig sind:

Im Anschluss wird NodeJS heruntergeladen und fur den Betrieb vorbereitet:

Sofern die Installation erfolgreich war, wird nach der Eingabe des Befehls

der Output "**v0.10.28**" in der Konsole angezeigt, welcher Auskunft uber die korrekt installierte Versionsnummer gibt.

Die auf github verfugbare Software [Homebridge](https://github.com/nfarina/homebridge), welche als HomeKit-Server fungiert, wird nun heruntergeladen und installiert:

Der auf NodeJS basierte Homebridge-Server emuliert spater das iOS HomeKit API, um eine Brucke zwischen HomeKit und Anwendungen von Drittherstellern (in diesem Fall FHEM) aufzuspannen.

Nach der mehrminutigen Installationszeit von Homebridge kann nun die Konfigurationsdatei des Homebridge-Dienstes gesetzt werden.

Dazu wird der nano-Editor genutzt und die benotigte Config-Datei mit dem Befehl

geoffnet.

Hier wird folgender Inhalt per Copy&Paste hineinkopiert:

Sofern der Homebridge-Server nicht auf dem selben Rechner wie der FHEM-Server betrieben wird, muss die Server-IP "127.0.0.1" (in diesem Fall sozusagen localhost) entsprechend angepasst werden.

Sofern weiterhin der http-Port "8083" von FHEM mit einem Benutzernamen und Passwort abgesichert ist, mussen die Eintrage "FHEMUser" und "FHEMPass" angespasst werden. Wer keine Authorisierung nutzt, kann die "auth"-Zeile einfach unverandert lassen oder ganz loschen, muss dann aber das Komma am Ende der vorherigen Zeile aus Syntaxgrunden ebenfalls entfernen. Welche Moglichkeiten es hier noch gibt (z.B. ssl-Zugriff), konnen z.B. in der Datei "~/homebridge/config-sample.json" eingesehen werden.

Sind die Anpassungen vollzogen, wird die Datei mit der Tastenkombination "STRG + o" gespeichert und der Editor wieder mit der Tastenkombination "STRG + x" geschlossen.

Nun ist der eigentlich Service bereits lauffahig und kann fur erste Tests genutzt werden. Dazu kann der Konsolenbefehl

zum manuellen Starten des Homebridge-Servers und entsprechend

zum manuellen Stoppen des Dienstes genutzt werden.

Damit der Dienst jedoch automatisch auch nach einem Neustart des RPI2 zur Verfung steht, sind noch einige weitere Anpassungen notwendig.

Zuerst wird Forever mit dem Befehl

installiert und anschließend das eigentlich Startscript uber den nano-Editor mit dem Befehl

erstellt. In der leeren Datei werden per Copy&Paste die Zeilen

eingefugt. Sind die Anpassungen vollzogen, wird die Datei wieder mit der Tastenkombination "STRG + o" gespeichert und der nano-Editor mit der Tastenkombination "STRG + x" geschlossen.

Jetzt erhalt die Datei mit dem Befehl

abschließend noch die notwendige Berechtigung verpasst.

Um den Autostart kunftig zu aktivieren, wird der Befehl

ausgefuhrt. Soll der Autostart wieder deaktiviert werden, kann der Befehl "sudo update-rc.d -f homebridge remove" (ohne Anfuhrungszeichen) verwendet werden.

Ab sofort kann der Homebridge-Service auch bequem im laufenden Betrieb zu Testzwecken mit

gestartet und uber den Befehl

beendet werden.

Wird Homebridge gestartet, werden alle im FHEM-Raum "Homekit" beheimateten Gerate - in diesem Beispiel der HomeMatic-Aktor KU.Deckenlampe - eingelesen und verfugbaren Services - in diesem Fall schlichtweg "An" und "Aus" \- fur die kunftige Nutzung von HomeKit zur Verfugung gestellt.

Sofern der Dienst ohne Fehlermeldungen gestartet werden konnte, geht es mit der Einrichtung auf dem iOS-Device weiter.

### iOS-Device fur HomeKit vorbereiten

Damit die vom Homebridge-Server bereitgestellten Gerate und Dienste mit Siri angesprochen werden konnen, mussen diese am iPhone uber eine HomeKit-kompatible App einmalig "angelernt" und in die HomeKit-Datenbank geschrieben werden. Da Apple hierfur (noch) keine eigene native App fur HomeKit anbietet, muss eine App eines Drittherstellers zuruckgegriffen werden. Hier gibt es grundsatzlich mehrere Moglichkeiten, wobei sich die kostenlose App "[Elgato Eve](http://www.meintechblog.de/wordpress/wp-content/plugins/appstore/AppStore.php?appid=917695792)" von Elgato Systems mehr oder weniger als Standardlosung etabliert hat.

Preis: Gratis [Download](http://www.meintechblog.de/wordpress/wp-content/plugins/appstore/AppStore.php?appid=917695792)

![App Elgato Eve im AppStore](http://www.meintechblog.de/wordpress/wp-content/uploads/2015/10/App-Elgato-Eve-im-AppStore-550x441.jpg)

> _Sobald die ca. 12 MB große App heruntergeladen, installiert und gestartet wurde, wird die Option "Gerat hinzufugen" gewahlt._

![App Elgato Eve Geraet hinzufuegen](http://www.meintechblog.de/wordpress/wp-content/uploads/2015/10/App-Elgato-Eve-Geraet-hinzufuegen-493x550.jpg)

> _[App Elgato Eve Geraet hinzufuegen](http://www.meintechblog.de/wordpress/wp-content/uploads/2015/10/App-Elgato-Eve-Geraet-hinzufuegen.jpg)_

Sofern die oben durchgefuhrte Installation des Homebridge-Services erfolgreich durchlaufen und der Dienst ordnungsgemaß gestartet wurde, sollte in der Eve-App nach kurzer Zeit der Eintrag "Homebridge" zur Auswahl stehen. Nach der Auswahl des Eintrags kann der abgefragte **PIN**-Code manuell eingegeben werden, welcher - sofern die obige Konfiguration nicht geandert wurde - standardmaßig **031-45-154** lautet.

![App Elgato Eve](http://www.meintechblog.de/wordpress/wp-content/uploads/2015/10/App-Elgato-Eve-550x326.jpg)

> _[App Elgato Eve](http://www.meintechblog.de/wordpress/wp-content/uploads/2015/10/App-Elgato-Eve.jpg)_

Ab sofort stehen die Gerate, welche vorher im FHEM-Raum "Homekit" hinterlegt wurden, direkt in der Eve-App zur Verfugung und konnen in die passenden Raume verschoben und je nach Wunsch umbenannt werden, damit die Siri-Befehle kunftig zuverlassig erkannt und den passenden Geraten zugewiesen werden.

Wichtig ist dabei das Gerat auszuwahlen (hier: KU.Deckenlampe) und unter dem Reiter "**Funktion**" den Namen "Kuchenlampe" zu setzen. Dieser vergebene Funktionsname ist besonders relevant, da Siri diesen **bei den Sprachbefehlen berucksichtigt**. Unter "Verwendet fur" kann dann bpsw. auch das Symbol fur die Deckenlampe ausgewahlt werden, wobei diese Einstellung wohl keine besonderen Auswirkungen auf die Spracheingabe zu haben scheint.

![App Elgato Eve Funktion Name anpassen](http://www.meintechblog.de/wordpress/wp-content/uploads/2015/10/App-Elgato-Eve-Funktion-Name-anpassen-550x470.jpg)

> _Jetzt sollten bereits die Siri-Befehle_

"**Schalte die Kuche ein/aus**"  
"**Schalte das Licht in der Kuche ein/aus**"

ordnungsgemaß erkannt und passende Aktionen ausgelost werden. Dabei kann es jedoch gerade anfangs auch etwas dauern, da die eingetragenen Gerateinformationen auch uber iCloud synchronisiert werden. Bei meinen Tests gab es jedoch bisher nie langere Wartezeiten.

So sieht das Ganze dann - recht unspektakular - per Apple-Watch aus:

Wie man erkennt, reagiert das Ganze ohne großere Verzogerung.

Beispiele fur weitere Sprachbefehle und Informationen zu HomeKit konnen als Anregung auf der [Apple-Website](https://support.apple.com/de-de/HT204893) eingesehen werden.

Um weitere in FHEM verfugbare Gerate fur HomeKit bzw. Homebridge verfugbar zu machen, werden diese - wie bereits oben beschrieben - in den FHEM-Raum "Homekit" gepackt. Anschließend wird der Homebridge-Dienst gestoppt und neugestartet, um die geanderte Konfiguration einzulesen. Sobald die iPhone-App zur Verwaltung der Gerate gestartet wird, sollten die neuen Devices automatisch auftauchen und konfiguriert werden.

Sofern keine neuen Gerate aus FHEM hinzugefugt sondern geloschte Gerate aus Homebridge entfernt werden sollen, muss dies manuell in den Dateien im Ordner "~/homebridge/persist/" erledigt werden.

### Weitere unterstutzte Gerate:

-Dimmer  
-Temperatur-Luftfeuchtigkeitssensor  
-HomeMatic Heizungsthermostat  
-Keymatic?!  
-Fenster-/Tursensor  
-Philips Hue  
-Harmony Remote  
-Sonos

An dieser Stelle wird der Artikel noch weiter ausgebaut werden, da ich die einzelnen FHEM-Gerate erst nach und nach uber die Homebridge einbinden werde.

### Aus meinem taglichen Leben

Immer mal wieder gibt es neue Technologien, die das Nutzungsverhalten von Anwendern grundlegend umkrempeln. Im Falle von Apple HomeKit konnte diese Zeit - zumindest fur Early Adopter - gekommen sein. Gerade wenn eine wachsende Gerateanzahl berucksichtigt werden soll, wird eine "konventionelle" Steuerung per App zunhemend unhandlich Dabei konnen einfache Sprachkommandos per Siri einen massiven Mehrwert generieren, um nicht nur schneller, sondern vorallem auch komfortabler einzelne Gerate und Gerategruppen anzusteuern. Mit der Apple Watch macht es jedenfalls mega Spaß "einfach so" per Sprachbefehl in Interaktion mit dem Smart Home treten zu konnen.

![Hey Siri Smart Home Steuerung per Apple Watch](http://www.meintechblog.de/wordpress/wp-content/uploads/2015/10/Hey-Siri-Smart-Home-Steuerung-per-Apple-Watch.jpg)

> _[Hey Siri Smart Home Steuerung per Apple Watch](http://www.meintechblog.de/wordpress/wp-content/uploads/2015/10/Hey-Siri-Smart-Home-Steuerung-per-Apple-Watch.jpg)_

An dieser Stelle ein großes Lob an alle Entwickler und Beteiligten, die eine Verzahnung der verschiedenen Dienste erst ermoglichen und nun einer breiten Masse zuganglich machen. Auf Seiten von FHEM naturlich die FHEM-Community selbst, welches das Thema bereits seit Monaten intensiv im [FHEM-Forum](http://forum.fhem.de/index.php/topic,32652.0.html) diskutiert und die Unterstutzung fur immer mehr Gerate erweitert. Daneben naturlich auch ein dickes Lob an einzelne Personen wie [Alex Skalozub](https://twitter.com/pieceofsummer), welcher das HomeKit-Protokoll reverseengineered hat und [KhaosT](https://github.com/KhaosT), der den HomeKit-Hilfsserver [HAP-NodeJS](https://github.com/KhaosT/HAP-NodeJS) daraus entwickeln konnte, welcher nun als Grundlage fur die FHEM-Integration dient. Weiterhin an [justme1968](https://github.com/justme-1968) (Andre), der maßgeblich fur das FHEM.js der Shim-Plattform verantwortlich ist.

Ich hoffe dabei sehr, dass Apple auch kunftig keinen Riegel fur diesen "Hack" vorschieben wird, wie vor einigen Jahren bei Siri-Proxy, der damals bereits eine rudimetare Steuerung von Smart-Home-Devices per Spracheingabe moglich machte. Gefuhlt stehen die Chancen gut, dass die jetzige Homebridge-Losung in dem hier vorgestellten Kontext auch weiterhin funktionieren wird, ich drucke jedenfalls alle Daumen, da ich die Sprachsteuerung per Siri nun nicht mehr missen mochte.

Du mochtest keine Blogbeitrage verpassen? Dann melde dich kostenlos zu unserem [Newsletter](http://www.meintechblog.de/newsletter) an oder folge meintechblog.de auf [Facebook](https://www.facebook.com/meintechblog) oder [Twitter](https://twitter.com/meintechblog).
