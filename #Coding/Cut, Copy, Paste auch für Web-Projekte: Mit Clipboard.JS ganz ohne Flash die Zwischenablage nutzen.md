# Cut, Copy, Paste auch für Web-Projekte: Mit Clipboard.JS ganz ohne Flash die Zwischenablage nutzen

_Captured: 2015-10-04 at 21:33 from [t3n.de](http://t3n.de/news/clipboardjs-643989/?utm_source=feedburner+t3n+News+12.000er&utm_medium=feed&utm_campaign=Feed%3A+aktuell%2Ffeeds%2Frss+%28t3n+News%29)_

Jeder benutzt das Clipboard taglich, es ist wohl eines der meist genutzten System-Funktionen die es gibt - Copy, Cut, Paste. Dabei sollte man meinen, dass dieser jahrelange Begleiter schon eine fundamentale Integration im Web erhalten haben muss. Mit einem einfachen Klick auf ein DOM-Element direkt einen gewissen Bereich in das Clipboard speichern? Sollte kein Problem sein - ist es aber. Der Teufel steckt im Detail und somit gab es lange keine einheitliche Methode, ein solches Feature umzusetzen.

## Aktuelle Möglichkeiten auf das Clipboard zuzugreifen

Die Frage nach der besten Losung geistert schon lange durch das Netz, besonders auf [Stackoverflow ](http://stackoverflow.com/questions/400212/how-do-i-copy-to-the-clipboard-in-javascript) wurde diese Frage heiß diskutiert. Umwege uber einen Prompt-Dialog wurden als indirekte Losung gezeigt. Die weitverbreitete Losung, die auch weiterhin [GitHub ](https://github.com/) einsetzt, ist [ZeroClipboard ](http://zeroclipboard.org/).

Leider aber ist ZeroClipboard keine reine JavaScript-Losung. Hier wird eine Flash-Applikation gestartet, die im Hintergrund den Zugriff auf das System-Clipboard ermoglicht. Angesteuert wird es zwar uber JavaScript, was wiederum die Flash-Aktion auslost, doch ohne Flash funktioniert es nicht.

Da wir langsam [das No-Flash-Zeitalter erreichen](http://t3n.de/news/bye-bye-flash-html5-standard-627815/) und schon große [Browser und Unternehmen](http://t3n.de/news/facebook-flash-firefox-623274/), unter anderem auch [Chrome](http://t3n.de/news/chrome-flash-strom-614450/), den Flash-Support runterfahren oder initial blockieren, wird es Zeit fur eine neue Losung. Auch [HTML5-Animationen](http://t3n.de/news/html5-animationen-tumult-hype-3-623206/) und [HTML5-Werbe-Banner](http://t3n.de/news/bye-bye-flash-html5-standard-627815/) halten schon großen Einzug ins Web.

## Die Umsetzung mit Clipboard.js

Mit [Clipboard.js ](http://zenorocha.github.io/clipboard.js/) haben wir jetzt eine reine JavaScript-Umsetzung, die ohne jeglichen Abhangigkeiten direkt auf das System-Clipboard zugreifen kann. Somit wird auch kein Flash mehr benotigt, das im Hintergrund ausgefuhrt wird. Fur die Einrichtung wird das Framework nur runtergeladen und in der jeweiligen Webseite initialisiert. Darauf folgend konnen Elemente direkt mit der Funktionalitat ausgerustet werden:
    
          1. <inputid="foo"value="https://github.com/zenorocha/clipboard.js.git">
      2. <buttonclass="btn"data-clipboard-target="#foo">
      3. <imgsrc="assets/clippy.svg"alt="Copy to clipboard">
      4. <scriptsrc="dist/clipboard.min.js"></script>
      5. newClipboard('.btn');

Der Button wird mit der Klasse `btn` initialisiert und erhalt uber `data-clipboard-target="#foo"` das mogliche Ziel. Das Ziel wiederum beinhaltet die Daten, in diesem Fall ein Input-Tag, die im Clipboard gespeichert werden sollen. Sobald jetzt auf den Button gedruckt wird, wurde "https://github.com/zenorocha/clipboard.js.git" im Clipboard gespeichert werden.

Wenn der Button das weitere Attribut `data-clipboard-action="cut"` erhalt, wird der Inhalt ausgeschnitten und nicht nur kopiert. Sollte es darum gehen, einen reinen Copy-Button zu erstellen, ohne ein Ziel anzugeben, kann der Inhalt auch direkt im Button hinterlegt werden. Das funktioniert mit `data-clipboard-text=""`. Events und weitere Optionen durfen naturlich auch nicht fehlen. In der [Dokumentation ](http://zenorocha.github.io/clipboard.js/#usage) konnt ihr alle wichtigen Informationen nachschlagen.

Naturlich ware es zu schon um wahr zu sein, wenn es kein Haken an der Sache geben wurde. Das nur moderne Browser Clipboard.js unterstutzen, sollte eine Selbstverstandlichkeit sein. Doch leider unterstutzt der Safari die Funktionalitat nur teilweise. Eingesetzt wird die Web-API [Selection ](https://developer.mozilla.org/en-US/docs/Web/API/Selection) und [execCommand ](https://developer.mozilla.org/en-US/docs/Web/API/Document/execCommand). Wobei die vollstandige execCommand-Unterstutzung im Safari fehlt und somit das Kopieren in das Clipboard nicht funktioniert. Als Fallback fur den Safari wird der Text markiert und eine Info-Box angezeigt, die den Nutzer auffordert, `STRG/CMD-C` auszufuhren.

![Der Browser-Support von execCommand. \(Screenshot: clipboard.js\)](http://t3n.de/news/wp-content/uploads/2015/09/clipboard-js-browser-support.png)

> _Der Browser-Support von execCommand. (Screenshot: clipboard.js )_

Naturlich wurde es uns besser gefallen, wenn der Browser-Support vollstandig ware. Trotzdem lost das Framework [Clipboard.js ](http://zenorocha.github.io/clipboard.js/#browser-support) unser Problem elegant und einfach. Insgesamt uberzeugt Clipboard.js durch das schlanke Framework und die zukunftsorientierte Denkweise. Flash ist tot und es muss eine neue Alternative her. Wunschen wir uns fur die Zukunft nur eine noch bessere Abstimmung zwischen den Browsern.

**Wurdet ihr Clipboard.js auch einsetzen oder ist es euch noch zu experimentell?**
