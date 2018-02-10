# Mobile Usability Testing – Erfahrungen bei der Software-Auswahl

_Captured: 2018-02-07 at 20:09 from [blogs.itemis.com](https://blogs.itemis.com/de/mobile-usability-testing-erfahrungen-bei-der-software-auswahl?utm_source=hs_email&utm_medium=email&utm_content=60515040&_hsenc=p2ANqtz-88yvD9NG3-mvOWRCCRaSOT6AY1cYjQU5gu2gOk62rjaQMOzjAdMZwB3ERnKCSySFkZfLrRBsUXF0GkCMFoVODyH8yanQ&_hsmi=60515040)_

Einen Usability Test vorzubereiten ist kein Hexenwerk - vor allem, wenn man das notige Equipment zur Hand hat und aus Erfahrung weiß, wie man damit umgehen muss. In unseren bisherigen Usability Tests evaluierten wir meist Desktop- oder Web-Anwendungen, weniger mobile Applikationen. Doch gerade beim Testen mit dem Smartphone oder Tablet sind andere technische Aspekte zu beachten als bei der Untersuchung von Desktop-Anwendungen.

Deshalb mochte ich euch gerne in diesem Blogbeitrag von unserer Erfahrung in Sachen Mobile Usability Testing mit den zwei Tools [Lookback](https://lookback.io/) und [Open Broadcaster Software (OBS)](https://obsproject.com/) sowie einer kleinen, aber feinen Dokumentenkamera berichten.

Im Internet finden man viele gute Gegenuberstellungen und Vergleiche von Usability-Testing-Tools, die sich besonders gut fur Remote- oder mobiles Testen eignen. Fuhrt man den Test vor Ort durch, dann konnte ein moglicher Aufbau beispielsweise so aussehen:

![Usability-Testing-Beobachtung.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Usability/Usability-Testing-Beobachtung.png?t=1518013911243&width=2133&height=2184&name=Usability-Testing-Beobachtung.png)

Jeder Usability Test hat allerdings andere Anforderungen, Voraussetzungen und Einschrankungen, die man beachten muss. Zum Testen von z. B. klassischen Enterprise-Anwendungen, die auf dem Desktop laufen, war bisher [Morae von TechSmith](https://www.techsmith.de/morae.html) das Tool unserer Wahl. Als es jedoch darum ging, eine mobile Webseite auf dem Smartphone zu testen, reichte Morae alleine nicht mehr aus. Da sowohl der Screen des Smartphones, als auch die Interaktionen des Probanden sowie seine Mimik festgehalten werden sollten, bedurfte es einer anderen Losung.

Prinzipiell ist so ein Setting mit Morae zwar moglich, da mehrere externe Kameras angeschlossen werden konnen, um unabhangig vom Bildschirmgeschehen aufzunehmen. Auch eine PIP- (Picture-in-Picture-) Variante ist moglich. Fur uns kam diese Moglichkeit der Testaufzeichnung allerdings nicht in Frage, da die Aufnahme- und Streaming-Qualitat von Morae fur unser Setting ungenugend war. Nachdem eine Dokumentenkamera sowie Webcam angeschlossen waren und Morae das Ganze in den Nebenraum ubertragen sollte, war die Qualitat einfach zu schlecht. Das Bild war trotz HD-Einstellungen verpixelt und die Interaktionen des Probanden mit dem Smartphone war nicht mehr synchron mit der Sprachubertragung. Nach einigen weiteren Recherchen erweckte das Tool "Lookback" unsere Neugierde.

## Vorteile von Lookback

Lookback wurde speziell fur Usability Tests entwickelt und ermoglicht es, sowohl moderierte, als auch selbst-moderierte Tests durchzufuhren. Die App lasst sich mittlerweile nicht mehr nur auf iOS, sondern auch auf Android Geraten installieren. Durch die benutzerfreundliche Bedienung gestaltet es sich sehr leicht, einen Mobile Usability Test aufzusetzen. Die gewonnenen Daten werden nach dem Test direkt in die Cloud geladen und sind unter einem zuvor angelegten Account einseh- und bearbeitbar. Lookback filmt den Bildschirm ab, nimmt zusatzlich Ton auf und die Frontkamera des Smartphones lasst sich als Face-Cam einsetzen. Es ist ebenfalls moglich, als Zuschauer an so einem Usability Test teilzunehmen. Dafur werden die Live-Aufnahmen ubertragen und sind durch einen speziellen Link abrufbar. Die Übertragungsqualitat war bei unseren Testdurchlaufen allerdings noch so schlecht, dass diese Option fur unseren Aufbau nicht in Frage kam.

## Nachteile von Lookback

Neben der unzureichenden Qualitat war fur uns die Variante, dass die aufgenommenen Videos direkt in die Cloud geladen werden, nicht ausreichend. Je nach Große des Videos kann dieser Vorgang auch sehr lange dauern. Zwar verspricht Lookback die Videos zwischenzuspeichern und den Upload-Prozess bei WLAN-Verbindung zu starten, doch kam es bei unserem Test zu einigen Fehlversuchen. Da das Hochladen nicht zu 100 % zuverlassig stattfand, konnten wir uns somit auf dieses Feature nicht verlassen. Ebenfalls nicht moglich ist das Einblenden von Testszenarien mit Hilfe der App. Die Testaufgaben fur die Probanden mussen demnach auf einen anderen Weg ubertragen werden, zum Beispiel im Vorfeld via E-Mail. Da es sich bei uns jedoch nicht um einen Remote Usability Test handelte und wir stattdessen die Probanden und den Moderator vor Ort hatten, war dieser Punkt fur uns zu vernachlassigen.

Ein weiteres Problem war, dass die App den Bereich, wo der Proband den Bildschirm beruhrt, nicht festhalt. Dies war der ausschlaggebende Punkt fur uns, auf eine andere Losung zuruckzugreifen.

Was ich jedoch sehr positiv hervorheben mochte, ist der Support bei Lookback. Durch direkten und vor allem sehr schnellen Kontakt mit den Verantwortlichen konnten wir viele wertvolle Informationen sammeln und unser Feedback an die Entwickler von Lookback geben.

## Mobile Usability Testing mit Open Broadcaster Software (OBS) und Dokumentenkamera

Eine Alternative zu Lookback oder anderen Applikationen, welche fur die Aufzeichnung von Mobile Usability Tests genutzt werden kann, ist die Dokumentenkamera. Hier hat man keine eigens fur diesen Zweck entwickelte Software auf dem Smartphone oder Tablet, sondern eine externe Kamera, die lediglich den Bildschirm abfilmt. Ein großer Vorteil hierbei ist, dass nicht nur der Bildschirminhalt, sondern auch die Fingerbewegungen des Probanden problemlos festgehalten werden konnen. Fur unseren anstehenden Usability Test haben wir uns die IPEVO Ziggi-HD Plus besorgt. Diese vergleichsweise gunstige Kamera konnte uns uberzeugen, da sie alles mitbringt, was man fur einen Mobile Usability Test braucht. Zusatzlich haben wir eine HD-Webcam angeschlossen, welche das Gesicht des Probanden filmen und seine Reaktionen festhalten sollte.

Um die beiden Bilder nun in einen Nebenraum streamen zu konnen, damit Zuschauer des Usability Tests alle Geschehnisse mitbekommen, haben wir uns das Tool Open Broadcaster Software (OBS) zu Hilfe genommen.

![OBS-Setting-Beispiel.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Usability/OBS-Setting-Beispiel.png?t=1518013911243&width=2124&height=1944&name=OBS-Setting-Beispiel.png)

OBS ubertragt Bildschirminhalte in Echtzeit uber eine Netzwerkverbindung ins Internet oder speichert sie auf der Festplatte. Die ubertragenen Inhalte konnen mittels verschiedener Szenen und Fenster vor der Übertragung angepasst und erganzt werden. Mit zahlreichen Einstellungsmoglichkeiten lassen sich beliebig viele Quellen anlegen, die gestreamt werden sollen. Diese konnen dann in OBS arrangiert oder Standbilder und Texte hinzugefugt werden.

Mittels HDMI-Kabel und Beamer haben wir schließlich die Aufnahmen im Nebenraum angezeigen, da wir so vor eventuellen Internet-Ausfallen sicher waren und wir die Daten lediglich lokal speichern und nicht ins Internet streamen wollten.

![Pretest-Usability-Testing.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Usability/Pretest-Usability-Testing.png?t=1518013911243&width=2172&height=1407&name=Pretest-Usability-Testing.png)

## Fazit

Wahrend unseres Tests gab es keine Komplikationen und die Qualitat der Videoergebnisse hatte kaum besser sein konnen. Gerade fur die Erstellung von Highlightvideos ist eine gute Aufnahme elementar. Die Dokumentenkamera macht gestochen scharfe Aufnahmen, fokussiert automatisch und bietet zusatzlich manuelle Helligkeitsanpassungen fur ein besseres Bild. Die Open Broadcaster Software bieten sich ebenfalls fur allerhand Usability Tests an, bei denen ihr mehrere Videoquellen verarbeiten wollt. Es braucht ein klein wenig Einarbeitungszeit in dieses Tool, um die richtigen Einstellungen herauszufinden, doch gibt es im Internet viele Tutorials oder Handbucher dazu.

Wie bei so vielen Dingen gibt es jedoch nicht die eine perfekte Losung. Warum sollte es also beim Mobile Usability Testing anders sein? Wir haben viel recherchiert und mit der Open Broadcaster Software und einer kleinen Dokumentenkamera die fur uns beste Losung gefunden, um einen Mobile Usability Test durchzufuhren.

Welche Erfahrungen habt ihr gemacht? Habt ihr euer Test-Setting schon gefunden oder seid ihr noch auf der Suche nach den perfekten Tools? Schreibt es uns in die Kommentare!
