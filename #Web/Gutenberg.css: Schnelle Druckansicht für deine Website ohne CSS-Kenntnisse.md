# Gutenberg.css: Schnelle Druckansicht für deine Website ohne CSS-Kenntnisse

_Captured: 2016-11-07 at 10:04 from [t3n.de](http://t3n.de/news/gutenbergcss-schnelle-757654/)_

![    Gutenberg.css: Schnelle Druckansicht für deine Website ohne CSS-Kenntnisse
](http://img.t3n.sc/news/wp-content/uploads/2016/10/gutenbergcss-featured.jpg?auto=compress%2Cenhance%2Cformat&fit=crop&fm=jpg&h=347&ixlib=php-1.1.0&q=65&w=620&s=bfba936ee2eaa90953d600d6632f5730)

> _Gutenberg.css nimmt dir die manuelle Arbeit komplett ab. (Bild: Pixabay.com)_

Mit der Hilfe von Gutenberg.[css](http://t3n.de/tag/css) definierst du mit wenig Zeitaufwand eine nahezu perfekte Druckausgabe fur deine Website. Dazu benotigst du nicht mal Kenntnisse im Umgang mit CSS. Der Erfinder des Buchdrucks hatte vermutlich seine wahre Freude daran gehabt.

## Gutenberg.css: Drei Themes, drei verschiedene Ergebnisse

Fabien Sa, Entwickler bei [Quarkdev](https://quarkdev.com/) aus der Schweiz, stellt eine CSS-Losung fur das immer noch aktuelle Problem der Print-Darstellung deiner Website vor. [Gutenberg.css](https://github.com/BafS/Gutenberg), so der Titel der Projekts, kannst du auf Github kostenlos herunterladen und vollig frei verwenden, da es unter der liberalen MIT-Lizenz steht.

Um es zu verwenden, bindest du die zentrale Datei Gutenberg.css in deine Dokumente ein und lasst ihr noch eines der drei mitgelieferten Themes folgen. Das sieht dann etwa so aus:
    
    
    <link rel="stylesheet" href="dist/gutenberg.css" media="print">
    <link rel="stylesheet" href="dist/themes/oldstyle.css" media="print">

Sa gibt seinem knapp 11 Kilobyte schlankem Stylesheet drei unterschiedliche Layouts mit, die er als `book.css`, `modern.css` und `oldstyle.css` bezeichnet. Du kannst dir anhand der Namensgebung eine Vorstellung davon machen, was dich optisch jeweils erwartet.

Da die Stylesheets mit dem Zusatz `media="print"` eingebunden werden, ist klar, dass sie sich lediglich dann auswirken, wenn der Besucher deiner Website die Druckfunktion des Browsers nutzt, um die Informationen auszudrucken.

![Links ohne Gutenberg.css, Mitte und rechts mit Gutenberg.css. \(Screenshot: Github\)](http://t3n.de/news/wp-content/uploads/2016/10/gutenbergcss-620x559.png)

> _Links ohne Gutenberg.css, Mitte und rechts mit Gutenberg.css. (Screenshot: Github)_

Zusatzliche Eingriffe deinerseits sind nicht erforderlich, aber moglich. So wirst du mit einiger Sicherheit einzelne Elemente deiner Seite von der Druckdarstellung ausnehmen wollen. Das gelingt ganz einfach unter Verwendung der Klasse `no-print`. Bei langeren Texten wirst du Einfluss darauf nehmen wollen, wann der Seitenumbruch auf eine neue Druckseite erfolgt. Dazu fugst du dem Element, das auf der neuen Seite ganz oben erscheinen soll die Klasse `page-break` hinzu.

Sollte es im Ausnahmefall mal erforderlich sein, auch den Hintergrund deiner Website in den Druck mit aufzunehmen, so kannst du sogar das erreichen. Du musst hierzu jedoch eine Erganzung im [CSS](http://t3n.de/tag/css) vornehmen:
    
    
    -webkit-print-color-adjust: exact;
    print-color-adjust: exact;

## Es gibt sie noch, die Internetausdrucker

Generell versucht Gutenberg.css die semantische Logik in der Darstellung zu erhalten, egal fur welches Theme du dich entscheidest. Formatierungen, die im Standarddruckprozess verloren gingen, erhalt Gutenberg.css, was der Lesbarkeit des Ausdrucks deutlich zugutekommt. Sa verwendete SCSS zur Entwicklung seiner Losung.

Gutenberg.css befindet sich in reger Entwicklung. Die letzten Updates datieren von vor etwas mehr als zwei Wochen. Der Bedarf an Losungen fur das stilsichere Ausdrucken digitaler Inhalte ist ungebrochen.

Worauf setzt du, wenn es um die Druckdarstellung deiner Website geht? Druben bei Dr. Web stellte Andreas Hecht vor einiger Zeit seinen eigenen diesbezuglichen [Vorschlag](https://www.drweb.de/magazin/das-optimale-print-stylesheet-76873/) vor.
