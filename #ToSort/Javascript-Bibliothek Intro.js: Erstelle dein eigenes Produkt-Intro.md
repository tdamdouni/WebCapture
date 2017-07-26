# Javascript-Bibliothek Intro.js: Erstelle dein eigenes Produkt-Intro

_Captured: 2015-11-15 at 15:42 from [t3n.de](http://t3n.de/news/produkt-tour-web-applikationen-642246/)_

Als Entwickler kennt man seine Idee und sein Ziel, Funktion und Bedienung sind selbstverstandlich und benotigen wenig oder keine Erklarung. Das ist oftmals der großte Fehler, welches einem Projekt widerfahren kann. Endkonsumenten konnen den Mehrwert nicht nutzen, sind eher frustriert und verstehen die Web-Applikation, bedingt durch Informationsuberfluss, nicht. Damit das nicht mehr passiert, zeigen wir euch Intro.js.

## Was steckt unter der Haube von Intro.js?

![Einführung in den Step-by-Step-Guide von Intro.js \(Screenshot: Intro.js\)](http://t3n.de/news/wp-content/uploads/2015/09/step-1-introjs-595x211.jpg)

> _Einfuhrung in den Step-by-Step-Guide von Intro.js (Screenshot: Intro.js )_

Mit Intro.js konnen wir mit wenig Aufwand einen Step-by-Step-Guide fur unsere Web-Applikation erstellen. Jeder Schritt wird visuell hervorgehoben und erhalt somit die volle Aufmerksamkeit des Betrachters. Ein kleiner Tooltip kann den Schritt erlautern und Hinweise zu der jeweiligen Benutzung geben. Die Schritte konnen mit der Maus und der Tastatur gesteuert oder sogar ubersprungen werden.

Der Übergang zu den nachsten Schritten ist animiert und somit leicht erfassbar fur den Endkonsumenten. Wird ein Schritt nicht direkt verstanden, kann jederzeit zuruck gesprungen werden. Das erstellte Overlay passt sich automatisch nach einem Windows-Resize an und kann somit auch fur Fluid-Elemente benutzt werden.

Sollten ein Schritt nicht im aktuellen Viewport liegen, wird automatisch zu diesem Punkt gescrollt oder bei Bedarf eine neue Seite geladen. Damit ihr einen Überblick uber die Moglichkeiten von Intro.js erhaltet, konnt ihr euch die [Examples ](http://usablica.github.io/intro.js/example/index.html) angucken.

[Jetzt zugreifen: 20 x t3n-Abo inklusive „Professionell entwickeln mit JavaScript" [t3n-Aktion]

](http://t3n.de/news/zugreifen-20-t3n-abo-inklusive-651293/)

## Den eigenen Step-By-Step-Guide mit Intro.js erstellen

Bevor wir Intro.js verwenden konnen, mussen wir dies zuerst auf der [offiziellen Seite ](http://usablica.github.io/intro.js/) herunterladen. In dem folgenden Paket benotigen wir die intro.js- und introjs.css-Datei. Folgend konnen wir noch uns ein Theme aussuchen. Damit wir einen Überblick der verschiedenen Themes erhalten, konnen wir uns eine [Preview ](https://github.com/usablica/intro.js/wiki/IntroJs-templates) angucken.
    
          1. <linkhref="introjs.css"rel="stylesheet">
      2. <linkhref="introjs-royal.css"rel="stylesheet">
      3. <ahref="javascript:void(0);"onclick="javascript:introJs().start();">Tour starten</a>
      4. <h1data-step="1"data-intro="Step 1">Hallo Welt</h1>
      5. <h2data-step="2"data-intro="Step 2">Test 123</h2>
      6. <scripttype="text/javascript"src="intro.js"></script>

Sobald wir das Grundgerust angelegt haben, konnen wir jedes HTML-Element mit einem Schritt belegen. Über das Attribut data-step wird die Reihenfolge definiert und uber data-intro jeweils der Hinweis-Text. Weitere Attribute konnen auf der [GitHub-Seite ](https://github.com/usablica/intro.js#attributes) nachgeschlagen werden.

Intro.js liefert uns aber nicht nur Custom-Data-Elemente sondern auch [JavaScript-Funktionen ](https://github.com/usablica/intro.js#api), die wir direkt aufrufen konnen. Schon im Beispiel, benutzen wir introJs().start(); um den Guide zu starten. Viele weitere Funktionen stehen bereit, um zu einem [Step zu springen ](https://github.com/usablica/intro.js#introjsgotostepstep), [Optionen zu hinterlegen ](https://github.com/usablica/intro.js#introjssetoptionsoptions) oder den [Guide zu verlassen ](https://github.com/usablica/intro.js#introjsexit).

Naturlich durfen auch Events nicht fehlen, die es ermoglichen auf gewisse Prozesse zu lauschen. Sollte unser Guide abgeschlossen sein und wir wollen dem Endbenutzer unsere Gluckwunsche aussprechen, wurde sich [oncomplete ](https://github.com/usablica/intro.js#introjsoncompleteprovidedcallback) eignen. Geht es aber eher darum, dass unser Endbenutzer den Guide plotzlich verlassen hat, ware das Event [onexit ](https://github.com/usablica/intro.js#introjsonexitprovidedcallback) besser geeignet.

Intro.js ist eine ausgereifte Javascript-Bibliothek, die es uns ermoglicht, benutzerfreundliche Einsteiger-Guides zu erstellen. Damit wir sicherstellen konnen, dass unser Produkt nicht durch Informationsuberfluss den Bach heruntergeht.

**Habt ihr eine solche Javascript-Bibliothek schon in einem Projekt eingesetzt?**

Wir lieben Shop- und Content-Management-Systeme seit uber 12 Jahren und bieten seither erstklassigen und kostenlosen Experten-Support. Jetzt legen wir noch einen drauf: In Webinaren und Telefonaten mit unseren Experten sowie CMS-Choryphaen aus den Communitys erhaltst du bei uns das geballte CMS-Know-how! [ Mehr erfahren!](http://guruads.de/api/click/56372fa1497959ee1600003e)
