# Swift: So leicht gelingt der Einstieg in Apples neue Programmiersprache

_Captured: 2015-11-25 at 16:43 from [t3n.de](http://t3n.de/news/swift-tutorials-apple-starter-guide-554269/)_

## Apples Swift im Überblick

Die Idee hinter Swift ist schnell erklart: Apple will es Entwicklern leichter machen, fur OS X und iOS zu programmieren. Derzeit erweitert Swift Objective-C, mittelfristig ist es allerdings nicht abwegig, dass die Programmiersprache aus den 80ern komplett ersetzt wird.

Bei [Swift](http://t3n.de/news/swift-apples-neue-548908/) handelt es sich um eine neue Programmiersprache fur Cocoa und Cocoa Touch - die beiden Frameworks fur OS X, respektive iOS. Swift-Apps werden mit Apples IDE Xcode 6 erstellt. Dadurch, dass die neue Programmiersprache sich mit aktuellen Objective-C-Anwendungen versteht, konnen Entwickler schon jetzt ihre bestehenden Anwendungen um Swift-Code erganzen.

![xxx](http://t3n.de/news/wp-content/uploads/2014/06/apple-swift-cheatsheet-595x290.jpg)

> _Das Cheatsheet zu Swift von Ray Wenderlich ist sowohl Anfangern als auch Fortgeschrittenen zu empfehlen. (Bild: Ray Wenderlich)_

## Darum solltet ihr mit Swift programmieren

Swift weist gegenuber Objective-C eine ganze Reihe an Vorteilen auf. So mussen sich Entwickler beispielsweise nicht mehr um die Arbeitsspeicherzuweisung kummern, denn Swift verwaltet den Speicher automatisch. Auch der Umgang mit Strings gestaltet sich mit Swift deutlich einfacher.

Nehmt ihr in Xcode 6 Änderungen an eurem Code vor, konnt ihr das Ergebnis dank eines Live-Previews namens „Playgrounds" sofort sehen - auch ohne Kompilierung. Außerdem lasst sich mit der neuen Sprache nicht nur leichter coden, sondern der Code selbst lasst sich auch leichter lesen. Als Beispiel dafur eignet sich der obligatorische Hello-World-Code:
    
    
    **Objective-C:**
    #import <stdio.h>
    
    int main (void)
    {
    printf ("Hello world!\n");
    }
    
    
    **Swift:**
    println("Hello, world!")

Semikola konnen, mussen aber nach Anweisungen nicht gesetzt werden, außer ihr schreibt mehrere Anweisungen hintereinander und in einer Zeile. Hervorzuheben ist auch, dass Swift Type-Inference bietet. Das heißt, dass ihr euren Variablen bei der Deklaration keinen Typ zuordnen musst. Vielmehr schließt der Compiler basierend auf dem ubergebenen Wert einen Ruckschluss darauf, welchen Typs die entsprechende Variable ist. Bei Swift weiß der Compiler dank Type-Safety auch viel mehr uber die Typen, die beim Aufruf einer Methode im Spiel sind, als das bei Objective-C der Fall ist. Erfahrene Entwickler begrußen zudem die Unterstutzung von Generics. Dabei handelt es sich vereinfacht gesagt um ein Pendant zu Templates in C++ oder den generischen Typen in Java.

Viele Entwickler sind sich einig, dass Apple mit Swift viel richtig gemacht hat. Die neue Programmiersprache ahnelt Python in vielen Bereichen und durfte damit besonders fur Anfanger wesentlich leichter zu erlernen sein als Objective-C. Kritische Stimmen geben allerdings zu bedenken, dass Swift es Entwicklern erschwert, ihren Code auf andere Plattformen außerhalb des Apple-Universums zu portieren.

## Erste Schritte mit Swift

Wer sich dafur interessiert, Apples neue Programmmiersprache zu erlernen, findet im Netz eine ganze Reihe empfehlenswerter Anlaufstellen fur entsprechende Informationen. Im iBooks-Store findet sich mit [The Swift Programming Language ](https://itunes.apple.com/de/book/swift-programming-language/id881256329) ein kostenloses und offizielles Buch als Einfuhrung in die Entwicklung fur OS X. Die im Buch enthaltenen Informationen finden sich auf der Apple-Entwicklerseite. Neben einer u[bersichtlichen Einfuhrung in Swift ](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/) findet ihr dort auch eine Tour, eine [umfangreiche Beschreibung der Programmiersprache ](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/TheBasics.html#//apple_ref/doc/uid/TP40014097-CH5-XID_399) und eine [Swift-Referenz ](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/AboutTheLanguageReference.html#//apple_ref/doc/uid/TP40014097-CH29-XID_453).

![Swift-Tutorial mit Spaßgarantie: Ein Flappy-Bird-Klon mit Apples neuer Programmiersprache entwickelt. \(Bild: GitHub\)](http://t3n.de/news/wp-content/uploads/2014/06/apple-swift-flappy-birds-ios8-595x415.jpg)

> _Swift-Tutorial mit Spaßgarantie: Ein Flappy-Bird-Klon mit Apples neuer Programmiersprache entwickelt. (Bild: GitHub)_

Neben der offiziellen Einfuhrung braucht ihr naturlich die Xcode-6-IDE, um loslegen zu konnen.

## Weitere Referenzen und Swift-Libraries

Neben den schon genannten offiziellen Referenzen von Apple finden sich online einige zusatzliche nutzliche Informationsquellen rund um Swift. Ray Wenderlich stellt beispielsweise eine [Schnellreferenz und ein Cheatsheet fur Swift ](http://www.raywenderlich.com/73967/swift-cheat-sheet-and-quick-reference) zum Download zur Verfugung, die er regelmaßig aktualisiert. Bei LearnSwiftOnline finden sich dagegen eine [Kurzanleitung fur Strings in Swift ](http://www.learnswiftonline.com/reference-guides/string-reference-guide-for-swift/), eine fur [Variablen und Konstanten ](http://www.learnswiftonline.com/reference-guides/variables-constants/) und eine fur [Arrays ](http://www.learnswiftonline.com/reference-guides/array-reference-guide-for-swift/). Wer auf der Suche nach [angesagten Swift-Repositories ](https://github.com/trending?l=swift&since=monthly) ist, wird unter anderem bei GitHub fundig.

Eine tolle Anlaufstelle fur iOS- und OS-X-Libraries, die in Swift geschrieben sind, ist die [Swift Toolbox ](http://www.swifttoolbox.io). Ebenfalls einen Blick wert ist Dollar.$wift - eine [Swift-Library, die Hilfsmethoden bundelt ](http://www.dollarswift.org). Auch GitHub hat in Sachen Swift - wie schon erwahnt - einiges zu bieten. Empfehlenswert ist beispielsweise XCGLogger - ein [Debug-Log-Framework, das sich fur mit Swift umgesetzte Projekte eignet ](https://github.com/DaveWoodCom/XCGLogger).

## Swift-Tutorials fur Anfanger

Blutige Anfanger sollten sich eine kurzere Einfuhrung als das 500 Seiten starke Buch von Apple zu Swift durchlesen. Dharani Kumar umreißt beispielsweise [die wichtigsten Aspekte von Swift ](http://dharaniiosdeveloper.blogspot.de/2014/06/getting-started-with-swift-language_25.html). Fabio Rocha beginnt bei seinem [Swift-Tutorial fur Anfanger auf Medium ](https://medium.com/swift-tutorial-for-begginers/swift-tutorial-for-begginers-part-1-da3392051de) ganz vorne und leitet euch auch durch die notigen Schritte in Xcode 6. Ä[hnlich einsteigerfreundlich sind auch das Tutorial ](http://hayageek.com/ios-swift-tutorial/) von Ravishanker Kusuma sowie der [Swift-Guide von Amit Bijlani ](http://blog.teamtreehouse.com/an-absolute-beginners-guide-to-swift). Beginner werden auch beim selben Mann, der auch die schon angesprochene Schnellreferenz verfasst hat, fundig. Das [Swift-Tutorial von Ray Wenderlich ](http://www.raywenderlich.com/74438/swift-tutorial-a-quick-start) setzt keinerlei Swift- oder Objektive-C-Kenntnisse voraus und fuhrt euch behutsam in 15 Minuten in die Thematik ein. Das [Swift-Blog ](http://www.swift-blog.de) bietet ebenfalls viele empfehlenswerte Videos, von denen einige auch deutschsprachig sind.

![Optionals sind nur eine der Neuerungen in Swift gegenüber Obejctive-C. \(Bild: Matt Bridges / Medium\)](http://t3n.de/news/wp-content/uploads/2014/06/swift-optionals-matt-bridges-medium-595x357.jpg)

> _Optionals sind nur eine der Neuerungen in Swift gegenuber Obejctive-C. (Bild: Matt Bridges / Medium)_

Kleinteiligere [Tutorials zu einzelnen Aspekten von Swift ](http://www.weheartswift.com) findet ihr beispielsweise bei weheartswift. Wer es lieber visuell hat, findet auf YouTube ebenfalls einige Videos, die sich explizit an Anfanger richten - so zum Beispiel diese [Playlist ](https://www.youtube.com/playlist?list=PLnEt5PBXuAmvm6UTzqakPF5CO39DiKr5A). Etwas weiter in die Tiefe geht Brian Advent mit einem [Swift-Tutorial fur iOS ](https://www.youtube.com/watch?v=sxDSc2Z2W4g), in dessen Rahmen ihr eine kleine ToDo-Listen-App entwickelt. Einen [umfassenden Videokurs zu Swift ](https://www.udemy.com/swift-learn-apples-new-programming-language-by-examples/) mit insgesamt 68 kleinen und informativen Filmen hat udemy live gestellt.

Wer auf der Suche nach aufeinander aufbauenden und entsprechend mehrteiligen Tutorials ist, findet online die ein oder andere fur Anfanger geeignete Serie. Jameson Quave bietet beispielsweise ein [sechsteiliges Tutorial fur Swift ](http://jamesonquave.com/blog/developing-ios-apps-using-swift-tutorial/), in dem man lernt, eine iOS-8-App zu entwickeln. Quave startet ganz harmlos mit einem Hello-World-Programm und steigert den Schwierigkeitsgrad nach und nach. Ebenfalls zu empfehlen ist die [App Swifty ](http://swifty-app.com/?utm_source=designernews), mit der ihr auch unterwegs auf eurem iPhone die Programmiersprache erlernen konnt.

In dem folgenden offiziellen Video-Tutorial zeigt Apple, wie ihr mit Hilfe von Xcode und Swift in nur sechs Minuten eure eigene Foto-App entwickeln konnt:

[http://devstreaming.apple.com/videos/swift/assets/xcode-hd.mp4 ](http://devstreaming.apple.com/videos/swift/assets/xcode-hd.mp4)

## Swift: Tutorials fur Fortgeschrittene

Viele konzeptionelle Aspekte von Swift korrespondieren mit Objective-C. Eine Ausnahme bilden Optionals. Was es damit auf sich hat und wie sich diese Art von Variablen einsetzen lasst, erklart ein [Blogbeitrag auf learnswift ](http://www.learnswift.io/blog/2014/6/5/lets-talk-about-optionals). Etwas tiefer in die Materie geht ein [Medium-Artikel von Matt Bridges ](https://medium.com/@rrridges/swift-optionals-a10dcfd8aab5). Wer sich dafur interessiert, wie der Apple-Debugger funktioniert und wie die Bug-Analyse vonstatten geht, sollte sich das [offizielle Video zu LLDB-Video auf YouTube ansehen ](https://www.youtube.com/watch?v=IPhgcbuDk_k).

Fur den [Einsatz von Swift mit Cocoa und Objective-C ](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/BuildingCocoaApps/index.html#) stellt Apple entsprechende Informationen zur Verfugung. Ein knapp einstundiges, offizielle Video von der WWDC 2014 widmet sich der [Integration von Swift mit Objective-C ](https://www.youtube.com/watch?v=j25syxcIZLQ) ausfuhrlich. Wie sich [Objective-C-Klassen in Swift fur iOS-8-Apps ](http://ios-blog.co.uk/tutorials/ios8-how-to-use-objective-c-classes-in-swift/) nutzen lassen, erklart Mark Petherbridge in einem siebenteiligen Tutorial. [Wie Swift und Objective-C auf unterschiedlichen Ebenen zusammenarbeiten ](https://www.youtube.com/watch?v=-vXMF4_uwdQ) zeigt ein WWDC-Video, das sich Core-Foundation und C im Swift-Code widmet.

![Auch ein Tutorial für das Entwickeln eines Candy-Crush-Klons mit Swift findet sich unter unseren Empfehlungen. \(Bild: Matthijs Hollemans\)](http://t3n.de/news/wp-content/uploads/2014/06/apple-swift-tutorial-candy-crush-clone-matthijs-hollemans-595x369.jpg)

> _Auch ein Tutorial fur das Entwickeln eines Candy-Crush-Klons mit Swift findet sich unter unseren Empfehlungen. (Bild: Matthijs Hollemans)_

Nicht wenige der genannten, kleinteiligeren Tutorials von weheartswift richten sich an Fortgeschrittene. So halt das Blog beispielsweise ein [Tutorial zu Swift-Funktionen hoherer Ordnung ](http://www.weheartswift.com/higher-order-functions-map-filter-reduce-and-more/) wie Karten und Filter vor. Fur fortgeschrittene Entwickler gibt es daruber hinaus eine Reihe von Tutorials mit echtem Praxisnutzen. Wir haben beispielsweise schon uber ein Tutorial berichtet, mit dem sich das Spiel [Flappy Bird mit Swift nachbauen](http://t3n.de/news/flappy-bird-swift-programmierst-549325/) lasst. In eine ahnliche Kerbe schlagt das Tutorial von Matthijs Hollemans, in dem er euch zeigt, wie ihr [mit Swift einen Candy-Crush-Klon programmieren ](http://www.raywenderlich.com/75270/make-game-like-candy-crush-with-swift-tutorial-part-1) konnt. Ein weiteres schones Projekt bietet Chris Chares mit seinem Swift-Tutorial, mit dem ihr eine [App mit Geolocation-basierten Benachrichtigungen ](http://chares.ghost.io/lets-make-a-swift-app/) entwickelt.

Weitere [Tutorials, Referenzen und Videos rund um Swift ](http://www.sososwift.com) finden sich unter anderem in der empfehlenswerten Sammlung von SoSoSwift.

**Kennt ihr noch weitere empfehlenswerte Swift-Tutorials fur Anfanger und Fortgeschrittene?**

_Letztes Update des Artikels: 11. September 2015_

Am Freitag den 27. November schenkt Mittwald allen Bestellern eines vServers ein besonderes Angebot: Neben einem Rabatt erwartet euch ein exklusives Geschenk. Merkt euch den Freitag jetzt vor und freut euch auf die Weihnachtszeit!

[ Mehr erfahren!](http://guruads.de/api/click/564b2c79497959fa46000028)
