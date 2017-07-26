# Framework jQuery: die Vorteile und Nachteile

_Captured: 2017-05-30 at 13:35 from [www.drweb.de](https://www.drweb.de/magazin/framework-jquery-vorteile-nachteile-83398/)_

![](https://www.drweb.de/magazin/wp-content/uploads/2017/05/jquery-nein.jpg)

Frameworks wie jQuery gehoren zu den bekanntesten und weit verbreitetsten Helfer, die auf Websites eingesetzt werden. Das Framework ermoglicht es, schnell und unkompliziert auf HTML-Elemente zuzugreifen und diese zu manipulieren oder [per CSS zu gestalten](https://www.drweb.de/magazin/typografische-animationen-mit-blast-js-52459/). Ich selbst bin kein großer Freund von solchen Frameworks und versuche, sie - wo immer es geht - zu vermeiden. Das funktioniert nicht immer, ist aber haufig problemlos machbar.

### jQuery und Co. und der große Ballast

Gerade jQuery hat sich in den letzten Jahren zu einer Art Schweizer Taschenmesser fur JavaScript entwickelt. Das Frameworks bietet unzahlige Methoden, Eigenschaften und Ereignisse, von denen die Meisten wohl nur ein Bruchteil benotigen.

Auch wenn jQuery in der aktuellen komprimierten Fassung auf gerade einmal 85 Kilobyte kommt, bliebe ein Großteil des Frameworks in meinen Projekten ungenutzt. Man kann es kleinlich nennen, dass mir 85 Kilobyte solch Kopfzerbrechen bereiten. Aber als Webentwickler ist mir ein schlanker Code, der nur das beinhaltet, was auch tatsachlich gebraucht wird, wichtig.

Jetzt ist jQuery mittlerweile zu einer Art Standard in der Webentwicklung geworden. Daher sind viele andere Frameworks mittlerweile als [Plugins fur jQuery](https://www.drweb.de/magazin/animsition-benutzerfreundliches-jquery-plugin-fuer-animierte-seitenuebergaenge-52867/) entwickelt. Will ich diese nutzen, muss ich auch jQuery nutzen. Hier zeigt sich im besonderen Maße, was solche Frameworks fur Nachteile mit sich bringen.

Denn letztlich benotige ich jQuery dann nur, um das Plugin nutzen zu konnen. Da sind mir 85 Kilobyte dann in der Tat zu viel.

![](https://www.drweb.de/anzeigen/honeypot/2017-05-native-ad/250-250-1.png)

Auf Honeypot bewerben sich Firmen bei dir, inklusive Gehaltsangabe und Tech Stack. [Melde dich bei Honeypot an](https://auslieferung.commindo-media-ressourcen.de/www/delivery/ck.php?oaparams=2__bannerid=14415__zoneid=96__OXLCA=1__cb=1a60cb5c2c__oadest=https%3A%2F%2Fwww.honeypot.io%2Flp%2Fjoin%3Futm_source%3Ddrweb%26utm_medium%3Dpaid%26utm_term%3Ddrweb-de_de-none%26utm_content%3Dbear-de%26utm_campaign%3Dnone-de) und [lass dir Jobangebote zukommen](https://auslieferung.commindo-media-ressourcen.de/www/delivery/ck.php?oaparams=2__bannerid=14415__zoneid=96__OXLCA=1__cb=1a60cb5c2c__oadest=https%3A%2F%2Fwww.honeypot.io%2Flp%2Fjoin%3Futm_source%3Ddrweb%26utm_medium%3Dpaid%26utm_term%3Ddrweb-de_de-none%26utm_content%3Dbear-de%26utm_campaign%3Dnone-de).

### Doppelt gemoppelt: Was jQuery kann, kann JavaScript oft auch

Mit der Einfuhrung von HTML5 hat auch JavaScript einen großen Sprung gemacht. Viele Funktionen, die bislang nur per jQuery moglich waren, sind nun auch ebenso einfach als native JavaScript-Methoden vorhanden.

Das gilt zum Beispiel fur das Hinzufugen und Entfernen von JavaScript-Klassen. Mit der "classList"-API kannst du dies ahnlich wie in jQuery realisieren.

Eine der wichtigsten Funktionen in jQuery ist die Moglichkeit, per "$()" auf beliebige Elemente zuzugreifen - und zwar in Anlehnung an CSS-Selektoren. Selbst dieses Alleinstellungsmerkmal von jQuery ist mittlerweile mit der Methode "querySelector()" in JavaScript aufgegriffen worden.
    
    
    document.querySelector("ol li").classList.add("new");

Im Beispiel wird allen "<li>"-Elementen, die Kinder eines "<ol>"-Elementes sind, die Klasse "new" zugewiesen. In jQuery ist ein entsprechender Aufruf kaum kurzer - vor allem aber nicht weniger kompliziert.
    
    
    $("ol li").addClass("new");

In vielen Fallen benotige ich jQuery also gar nicht, sondern kann mit JavaScript auf ahnlich einfachem Wege arbeiten.

### Performance vs. Einfachheit

jQuery und seine weniger bekannten Freunde machen es einem in vielen Fallen sehr viel einfacher, mit JavaScript zu arbeiten. Aber nicht immer ist der einfach Weg auch der Beste - gerade wenn es um die Performance geht.

Denn sowohl die jQuery-Methode "$()" als auch die JavaScript-Methode "querySelector()" schneiden in Sachen Performance schlechter ab als die Methoden "getElementsByTagName()" oder "getElementsByID()". Denn bei "$()" und "querySelector()" wird zunachst der komplette [DOM](https://www.drweb.de/magazin/codemirror-macht-aus-dom-objekten-vollwertige-code-editoren-36734/)-Baum eines Dokumentes nach entsprechenden zutreffenden Elementen durchsucht.

Die beiden Methoden "getElementsByTagName()" oder "getElementsByID()" kommen deutlich schneller ans Ziel. Naturlich sind die letztgenannten Methoden fur Entwickler zuweilen mit mehr Aufwand verbunden. Auch hier mag der geringe Unterschied bei der [Performance](https://www.drweb.de/magazin/wir-stellen-vor-das-e-book-wordpress-performance/) vernachlassigbar sein. Man sollte sich dessen jedoch bewusst sein.

### Vorteil: einheitliche Browser-Kompatibilitat

Jetzt will ich naturlich auch nicht so tun, als sei jQuery durch und durch uberflussig. Denn es hat ja seinen Grund, warum es immer noch sehr erfolgreich und beliebt ist. Ein Vorteil ist naturlich die einfache Anwendung.

Daruber hinaus haben solche Frameworks naturlich den Vorteil, dass sie eine breite Browser-Kompatibilitat mit sich bringen. Wahrend ich bei nativen Methoden immer schauen muss, welcher Browser ab welcher Version sie unterstutzt, macht jQuery mir das einfacher.

Denn fur jede jQuery-Version weiß ich, welche Browser und Versionen unterstutzt werden. Gerade wer fur altere Versionen des Internet Explorers entwickelt, hat mit jQuery in der aktuellen Version die Sicherheit, dass dieser ab Version 9 unterstutzt wird.

Und wer altere Browser noch unterstutzen mochte, kann auf altere Versionen von jQuery zuruckgreifen. Das erleichtert die Entwicklung von Websites, da man schon im Vorfeld weiß, welche Browser denn mit an Bord sind.

### Frameworks furs Spezielle

Jetzt bin ich also jemand, der - wenn immer es moglich und sinnvoll ist - auf Frameworks verzichtet. Moglich ist es eigentlich immer. Denn grundsatzlich kann man ja alles selbst in JavaScript programmieren. Nur sinnvoll ist es naturlich nicht immer.

Es gibt naturlich Situationen, in denen der Aufwand, eine komplexe JavaScript-Programmierung selbst zu entwickeln, in keiner Relation zum Ergebnis steht. Wer mit JavaScript zum Beispiel 3D-Animationen erstellen mochte, kann sich naturlich selbst sein eigenes 3D-Framework bauen.

Hier ist es hingegen mehr als sinnvoll, auf ein stabiles und moglichst leichtes Framework zuruckzugreifen. In solchen Fallen ist es mir aber immer wichtig, dass dieses Framework nicht auf andere Frameworks wie jQuery aufbaut, sondern unabhangig verwendet werden kann.

### Fazit

Naturlich ist die Frage, ob man auf Frameworks setzt oder nicht, durchaus eine ideologische. Denn der Gewinn an Schnelligkeit ist in vielen Fallen marginal. Aber man sollte als Entwickler nicht aus bloßer Bequemlichkeit auf jQuery und Co. zuruckgreifen.

Denn natives JavaScript kann haufig all das, was jQuery kann, selbst auch abdecken. Gerade wer fur zeitgemaße Browser entwickelt und die Abwartskompatibilitat eh in Grenzen halt, kommt gut ohne dieses Framework aus.
