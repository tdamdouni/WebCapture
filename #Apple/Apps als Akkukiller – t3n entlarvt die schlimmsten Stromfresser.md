# Apps als Akkukiller – t3n entlarvt die schlimmsten Stromfresser

_Captured: 2015-11-19 at 18:17 from [t3n.de](http://t3n.de/news/apps-akkukiller-482374/)_

Nachdem die Facebook-App ja schon als [Akku-Fresser entlarvt ist](http://t3n.de/news/facebook-app-saugt-iphone-akku-468492/), habe ich mir noch einige weitere Apps angeschaut. Die meisten verhalten sich zum Gluck vernunftig und laufen uberhaupt nicht im Hintergrund, benutzen fur ihre Benachrichtigungen Apples Push-Notifications.

Offensichtliche Akku-Fresser wie Navigations-Apps habe ich ebenfalls nicht getestet. Da ist klar, dass sie viel Akku brauchen: die ganze Zeit GPS aktiv, Display immer an und dann auch noch Ton ausgeben, das kann ja nur Akku fressen. Bei Spielen durfte das auch klar sein: Je aufwendiger und hubscher die Grafik, desto schneller ist der Akku leer. Also lieber ein einfaches 2D-Spiel anstatt der 3D-Variante.

Man konnte ja denken: Wenn [Facebook](http://t3n.de/tag/facebook) so viel Akku braucht, wie sieht es denn dann bei anderen [Social-Networks](http://t3n.de/tag/social-media) aus?

## **Google+ und Twitter - Akkukiller wie die Facebook-Apps?**

Die Google+-App verhalt sich absolut vorbildlich und lauft nur, wenn sie aktiv im Vordergrund ist - sonst verwendet sie Push-Nachrichten. Auch [Twitter](http://t3n.de/tag/twitter) lauft nicht im Hintergrund und bietet uberhaupt keine Benachrichtigungen an. Wie konnen diese Apps aber Benachrichtigungen anzeigen, wenn sie uberhaupt nicht im Hintergrund aktiv sind? Das liegt an der Art und Weise, wie Apple diese Benachrichtigungen gelost hat. Dazu muss ich aber erst einmal erklaren, wie es normalerweise lauft.

Auf einem Computer gibt es keine Multitasking-Beschrankungen, dort kann jedes Programm alles mogliche im Hintergrund machen - naturlich auch auf das Internet zugreifen. So hat zum Beispiel die Twitter-App eine Verbindung zu den Twitter-Servern und fragt dort nach, ob es neue Tweets gibt. Daruber kann die Twitter-App den Nutzer auf alle erdenklichen Arten informieren: eine Benachrichtigung anzeigen, ein Icon andern oder auch ein riesiges blinkendes Fenster vor allen anderen offnen.

Android macht das genauso. Dort laufen die Apps munter im Hintergrund, kommunizieren mit ihren Servern und wenn es etwas Neues gibt, melden sie sich und zeigen eine Benachrichtigung an. Das ist vor allem fur die Entwickler von Vorteil, weil es fur sie weniger Arbeit ist (der Code ist ja im Prinzip der, der auch sonst fur sie Server-Kommunikation verwendet wird). Fur den Nutzer aber zeigen sich die Nachteile in Form von reduzierter Akku-Laufzeit und verbrauchtem Datenvolumen.

Apple hat sich da etwas anderes ausgedacht. Bei [iOS](http://t3n.de/tag/ios) werden die Benachrichtigungen zentral von Apple an die Gerate geschickt. Damit das funktioniert, muss der Server eines Dienstes Benachrichtigungen an Apple schicken, damit die sie dann an den Nutzer schicken konnen:

![](http://t3n.de/news/wp-content/uploads/2013/07/apps_akkukiller_apple.png)

## Wie Apples Benachrichtungssystem fur Apps funktioniert

Die Vorteile sind klar: Die Apps mussen nicht laufen, damit der Nutzer benachrichtigt wird, also gibt es keine verringerte Akkulaufzeit und nicht jede App hat eine eigene Verbindung zu ihrem Server. Stattdessen gibt es nur eine einzige Verbindung zu Apples Servern, uber die die kleinen Push-Nachrichten geschickt werden. Das spart massiv Datenvolumen.

Der Nachteil liegt hier klar auf der Entwicklerseite, denn diese Art der Benachrichtigungen ist wesentlich komplizierter umzusetzen. Das ist besonders problematisch, wenn einem der Server, mit dem man kommuniziert, nicht gehort. Populares Beispiel: diverse Twitter-Clients, die naturlich auf Twitters offizielle Server zugreifen, den Nutzer aber trotzdem uber neue Tweets informieren wollen. Einzige Losung: einen eigenen Server betreiben, der anstelle der Twitter-Server die Push-Nachrichten an Apple schickt. Das kann und will naturlich nicht jeder Entwickler leisten.

Seit iOS 4 gibt es auch lokale Benachrichtigungen, die genauso ausssehen wie die Push-Nachrichten. Der Nutzer hat also keine Moglichkeit, die beiden Varianten zu unterscheiden. Lokale Benachrichtigungen wurden eingefuhrt, damit zum Beispiel Timer-Apps den Nutzer mit einer Benachrichtigung informieren konnen, dass ihr Tee fertig ist. Fruher hatte man die App dafur geoffnet lassen oder eben extra dafur einen Server aufstellen mussen, der dann Push-Nachrichten verschickt.

## VoIP-Apps machen eine Ausnahme

Eine App-Kategorie, die diese akkuschonende Moglichkeit nicht nutzt, sind [VoIP](http://t3n.de/tag/voip)-Apps. Laut Apples Programmier-Richtlinien funktioniert eine VoIP-App unter iOS folgendermaßen: Sie sagt dem System, in welchem Intervall sie aufgeweckt werden will (kleinstes Intervall sind zehn Minuten). Innerhalb dieses Intervalls wird sie dann vom System geweckt und darf maximal zehn Sekunden etwas tun - dann wird sie automatisch wieder eingefroren. Diese Zeit ist vorgesehen, um ein kurzes Lebenszeichen an den VoIP-Server zu senden, damit die Verbindung aktiv bleibt. Außerdem gibt die App einen Socket (eine Serververbindung) an das System ab. iOS uberwacht nun diesen Socket, wahrend die App schlaft. Werden Daten auf dem Socket empfangen, wird die App geweckt und der Socket an die App zurucktransferiert.

Damit man uber eine VoIP-App immer erreichbar ist, startet das System sie direkt nach Systemstart, damit sie ihre Verbindung aufbauen kann. Das heißt nicht nur, dass VoIP-Apps regelmaßig im Hintergrund aktiv sind und potentiell Status-Infos senden, sondern auch, dass das System eine Verbindung zum Server des VoIP-Anbieters aufrechterhalt, was sicher auch Datenvolumen verbraucht. Außerdem wird diese Verbindung immer wieder neu aufgebaut, wenn man mal kein Netz hat. Und das verbraucht garantiert Daten.

VoIP-Apps werden automatisch neu gestartet, wenn das System sie wegen Speichermangels beenden muss. Dabei geht auch die Verbindung verloren und muss von der App wiederhergestellt werden. Interessanterweise werden sie nicht neu gestartet, wenn sie vom Nutzer beendet werden. Gut fur uns, weil wir sonst uberhaupt keine Handhabe gegen solche Apps (außer dem Loschen) hatten.

Immerhin fasst das System mehrere dieser VoIP-Hintergrund-Aktionen zusammen, damit der Prozessor nur kurzzeitig viel zu tun hat und nicht durchgangig immer ein bisschen. Hat man also Skype und Facebook installiert, sind diese gleichzeitig im Hintergrund aktiv. So tritt nicht der Fall ein, dass Facebook immer genau in der Zeit aktiv ist, wo Skype schlaft. Also: Hat man erstmal eine VoIP-App installiert, schaden weitere kaum noch. Naturlich aber ist die Prozessor-Last umso hoher, je mehr Apps zur gleichen Zeit im Hintergrund aktiv sind.

## Auch Facebook nutzt den VoIP-Trick

![©iStockphoto.com/ymgerman](http://t3n.de/news/wp-content/uploads/istockphoto/13-04/facebook_ipad-230x153.jpg)

> _Die Facebook-Apps saugen den Akku schneller leer als andere. (Foto: (C) iStockphoto.com/ymgerman)_

Das erklart auch das Verhalten der [Facebook-App aus meinem letzten Test](http://t3n.de/news/facebook-app-saugt-iphone-akku-468492/). Sie nutzt die Standard-VoIP-Vorgehensweise, wird dadurch alle zehn Minuten aktiv, nutzt dann die ganzen zehn Sekunden aus und schlaft wieder ein. Da sie als offizielle VoIP-App durchgeht, wird sie auch automatisch beim iPhone-Start mitgestartet und lauft ab da im Hintergrund - einzig das harte Beenden halt sie wohl davon ab. Mein Kritikpunkt weiterhin: Macht das konfigurierbar (Die wenigsten werden wohl uber Facebook telefonieren) oder lost es mit einer schnoden Push-Nachricht!

Die Vorteile einer solchen Methode wurden uberwiegen: Sie verbraucht keinen extra Akku und keine extra Daten. Sobald man die App dann uber die Push-Nachricht offnen wurde, konnte sie die Verbindung herstellen und alles ware gut. Eventuell verpasst man dann einige Anrufe, weil das dadurch ein paar Sekunden langer dauert, aber wenn der Akku dadurch langer halt, konnte ich damit leben.

Als positives Beispiel mochte ich hier [Google-Hangouts](http://t3n.de/tag/hangouts) anfuhren. Die App erlaubt zwar das Telefonieren (inklusive Video), lauft dafur aber nicht standig im Hintergrund, sondern nutzt exakt das eben beschriebene Verfahren. [Skype](http://t3n.de/tag/skype) als wohl bekannteste und beliebteste VoIP-App ist leider kein ganz so positives Beispiel, aber immerhin besser als die Facebook-App. Sie ist genau wie Facebook alle zehn Minuten im Hintergrund aktiv. Im Gegensatz zu Facebook kann man aber in der App „Offline" gehen und damit die Hintergrund-Aktivitat ausschalten.

## Messenger sind die großten Akkukiller unter den Apps

[Viber](http://t3n.de/news/viber-sagt-whatsapp-skype-kampf-464787/), ein Messenger wie WhatsApp, uber den man aber auch telefonieren kann, verhalt sich als VoIP-App ahnlich wie Facebook - mit dem kleinen, aber bedeutenden Unterschied, dass Viber nicht alle zehn Minuten im Hintergrund aktiv ist, wie es vorgesehen ist, sondern alle drei Minuten!

![apps_akkufresser_viber-3-min](http://t3n.de/news/wp-content/uploads/2013/07/apps_akkufresser_viber-3-min.jpg)

> _Viber ist ein echter Akkukiller unter den Apps._

Die App umgeht dabei keine von Apples Vorgaben, sondern benutzt einen vollig legalen Trick. Erinnern wir uns daran, dass das System Apps aufweckt, sobald Daten uber den Socket ankommen. Eigentlich ist das so gedacht, dass dort eingehende Anrufe signalisiert werden. Viber aber sendet offensichtlich alle drei Minuten ein kleines Datenpaket vom Server aus uber diesen Socket. Das merkt iOS und startet die App. Und schon kann die alle drei statt alle zehn Minuten aktiv sein.

Um das herauszufinden, bedurfte es einer Traffic-Analyse mit [Wireshark ](http://www.wireshark.org). Wireshark ist ein Tool um Netzwerkverkehr aufzuzeichnen und auszuwerten. Das funktioniert auf einem Computer sehr einfach, da man dort vollen Zugriff auf alle Netzwerk-Interfaces hat - auf dem iPhone geht das nicht. Das Smartphone von Apple ist abgeschottet und erlaubt Apps keinen Zugriff darauf, sodass es auch kein Wireshark unter iOS gibt. Die einzige offensichtliche Moglichkeit ist, einen HTTP-Proxy in den WLAN-Einstellungen des iPhones einzutragen.

## Apps: Akkukiller durch Wireshark enttarnt

Das war auch mein erster Versuch. Man installiert sich einen Proxy-Server wie [Burp ](http://portswigger.net/burp/proxy.html) auf seinem Rechner, erlaubt dort den Zugriff auch von anderen Rechnern und tragt dann die IP-Adresse des Rechners, auf dem Burp lauft, in den WLAN-Einstellungen des iPhones ein. Damit kann man sich dann wunderbar den Verkehr des iPhones anzeigen lassen und mit einem [hier ](http://www.heise.de/artikel-archiv/ct/2012/07/120_Gut-App-geschaut) beschriebenen Verfahren sogar SSL-verschlusselten Verkehr anzeigen. Das Problem dabei: Viber taucht dort nicht auf, weil es nicht per HTTP kommuniziert, sondern ein eigenes Protokoll verwendet. Burp aber ist ein reiner HTTP-Proxy. Und selbst, wenn Burp mehr konnte, gabe es auf dem iPhone keine Moglichkeit, etwas anderes als einen HTTP-Proxy einzutragen.

Da kommt Wireshark ins Spiel. Zum Gluck bietet Mac OS X von Haus eine einfache Losung fur das Problem: die Internet-Freigabe. Dabei wird die Internet-Verbindung (die in dem Fall uber eine andere Schnittstelle als WLAN erfolgen muss), uber WLAN freigegeben. Dafur bietet der Mac dann ein WLAN an, in das man sich vom iPhone aus einloggen kann. Nun lauft der gesamte Netzwerkverkehr uber die WLAN-Schnittstelle des Macs. Diese Schnittstelle kann man jetzt in Wireshark auswahlen und aufzeichnen lassen. Dann erhalt man diese Liste:

![apps_akkufresser_viber_analyse](http://t3n.de/news/wp-content/uploads/2013/07/apps_akkufresser_viber_analyse-595x425.jpg)

> _Mit Wireshark lassen sich Apps wunderbar als Akkukiller enttarnen._

In der linken Spalte sieht man die Uhrzeit, zu der etwas gesendet wurde. Die weiteren Spalten zeigen Absender, Empfanger und Art der Datenpakete an. Dort kann man dann sehr schon sehen, dass (fast) immer zu dem Zeitpunkt, zu dem Viber im Hintergrund aktiv ist, ein TCP-Paket vom Viber-Server (54.225.248.253) an das iPhone (192.168.2.2) gesendet wird. Daraufhin sendet Viber auf dem iPhone etwas zuruck, was dann noch vom Viber-Server bestatigt wird. Hieran kann man gut sehen, dass es der Server ist, der zuerst sendet. So umgeht Viber also die Einschrankung, nur alle zehn Minuten aktiv sein zu durfen.

Hier kann man nun wieder die gleiche Methode anwenden, die auch bei Facebook half: die App komplett beenden. Dass man das getan hat, merkt Viber beim nachsten Start und prasentiert einem diese hubsche Meldung:

![apps_akkukiller_viber-meldung](http://t3n.de/news/wp-content/uploads/2013/07/apps_akkukiller_viber-meldung-230x345.png)

Das ist glatt gelogen! Die App verbraucht sehr wohl Akku (und zwar mehr als notig) und Speicher verbraucht sie naturlich auch. So kann man seine Nutzer auch fur dumm verkaufen. Und wie bei Facebook gibt es in der App keine Moglichkeit, das abzustellen. Angespornt durch diesen Fund hab ich mir noch weitere Messenger angeschaut.

Zuerst die positiven Beispiele: [Threema](http://t3n.de/news/whatsapp-alternativen-blick-430632/), [Hike](http://t3n.de/news/whatsapp-alternativen-blick-430632/), [LINE](http://t3n.de/news/whatsapp-alternativen-blick-430632/) und [ChatON](http://t3n.de/news/whatsapp-alternativen-blick-430632/) sind harmlos, denn sie laufen uberhaupt nicht im Hintergrund. Alles wird mit normalen Push-Nachrichten gelost. imo, [KakaoTalk](http://t3n.de/news/whatsapp-alternativen-blick-430632/) und joyn laufen alle funf Minuten im Hintergrund. Die [joyn-App](http://t3n.de/news/joyn-telekom-startet-447587/) hingegen ist eine richtige Akku-Sau, beziehungsweise ziemlich „kaputt". joyn lauft normalerweise auch alle funf beziehungsweise zehn Minuten im Hintergrund.

Manchmal verhalt sie sich aber auch komplett merkwurdig und lauft wesentlich ofter. Ich habe mehrmals beobachtet, dass joyn sofort, nachdem sie nicht mehr aktiv ist, sofort wieder neu startet und wild mit seinem Server kommuniziert, was naturlich viel CPU-Last erzeugt.

![apps_akkufresser_joyn](http://t3n.de/news/wp-content/uploads/2013/07/apps_akkufresser_joyn.png)

> _Unter den iPhone-Apps Akkukiller Nummer 1: joyn._

Die App ist dann merkwurdigerweise manchmal auch langer als die erlaubten zehn Sekunden aktiv. Wie sie das bewerkstelligt, ist unklar. Es ist aber logisch, dass haufige Aktivitat mit hoher CPU-Last eine kurzere Akku-Laufzeit bedeutet. Und so sieht der CPU-Time-Graph auch noch extremer aus als bei der Facebook App.

![apps_akkufresser_joyn_cpu](http://t3n.de/news/wp-content/uploads/2013/07/apps_akkufresser_joyn_cpu.png)

Es ist also nicht nur wichtig, wie oft eine App im Hintergrund aktiv ist, sondern auch, was sie dort macht, also wie rechenintensiv ihre Aktivitat ist. Da joyn leider nicht mehr funktioniert, wenn man die App manuell beendet, kann man daher wohl nur sagen: Schmeißt die App von eurem iPhone!

## **iPhone-Apps: Akkukiller und iOS 7**

Mit dem im Herbst erscheinenden [iOS 7](http://t3n.de/tag/ios-7) erhalten die Push-Nachrichten eine praktische Aufwertung. Aktuell ist es so, dass eine Push-Nachricht empfangen wird und dem Nutzer angezeigt wird. Erst, wenn der Nutzer die Nachricht offnet, startet die App und kann neue Inhalte (wie zum Beispiel die letzten Chat-Nachrichten) runterladen. Das kostet naturlich Zeit und ist nervig fur den Nutzer.

iOS 7 bringt stumme Push-Nachrichten. Sie werden an das iPhone geliefert, aber nicht angezeigt. Stattdessen startet im Hintergrund automatisch die App und darf fur kurze Zeit Daten runterladen. Danach konnte sie den Nutzer mit einer lokalen Benachrichtigung informieren. Startet man nun die App, muss nichts mehr geladen werden und alles ist aktuell. Vielleicht halt das manche Messenger-Hersteller ja dann davon ab, standig als VoIP-App im Hintergrund aktiv zu sein.

**Und welche App habt ihr im Verdacht, ein Akkukiller zu sein? Diskutiert mit - in den Kommentaren!**

### Über den Autor

Sebastian Duvel ist [iOS- und Mac-Entwickler ](http://www.jumpingfish.de) und Blog-Urgestein - seinen Blog findet ihr unter [blog.hagga.net ](http://blog.hagga.net/). Hauptberuflich ist er Azubi zum Anwendungsentwickler bei t3n.

### Weiterfuhrende Links zum Thema „Akkukiller" und „Messenger"

_Bildnachweis fur die Newsubersicht: (C) hocus-focus - iStockphoto.com_

Bleibe immer up-to-date. Sichere dir deinen Wissensvorsprung!
