# Das eigene WordPress-Theme erstellen – #1: Vorbesprechung und Vorbereitung

_Captured: 2015-12-04 at 16:31 from [t3n.de](http://t3n.de/news/grosse-guide-wordpress-theme-555618/)_

Einige von euch werden sich vielleicht noch daran erinnern, dass ich vor etwa einem Jahr schon ein paar Stucke dieser Reihe begonnen habe. Aus verschiedenen Grunden ist das nicht zuende gefuhrt worden: Zum einen bin ich mit der Programmierung nebenbei nicht hinterher gekommen und zum anderen habe ich nach dem dritten Teil den Code des Themes noch mal komplett uberarbeitet. Das soll dieses Mal nicht passieren und deshalb habe ich erst in Ruhe das Theme fertiggestellt. Jetzt kann es also noch mal losgehen.

Bevor wir mit den Vorbereitungen beginnen, konnt ihr euch [hier eine Demo des fertigen Themes anschauen ](http://bornholm.florianbrinkmann.de/): Da werden wir am Ende der Reihe landen.

## Besonderheiten des Themes

![Ansicht der alternativen Startseite des WordPress-Themes. \(Screenshot: Eigene Installation\)](http://t3n.de/news/wp-content/uploads/2014/07/wordpress-theme-erstellen-screenshot-595x446.jpg)

> _Ansicht der alternativen Startseite des WordPress-Themes. (Screenshot: Eigene Installation)_

Das Theme richtet sich an Fotografen und bietet zwei Seiten-Templates: Das eine ist fur eine alternative Startseite, auf der die neuesten Galerien aus den verschiedenen Seitengalerien angezeigt werden. Das andere [Template](http://t3n.de/tag/templates) zeigt alle Galerien der Seite und bietet sich fur eine Art Portfolio-Seite an.

Des Weiteren gibt es noch zwei eigene Widgets, um die neuesten Galerien anzuzeigen und bestimmte Galerien hervorzuheben. Auf der Einzelseite einer Galerie werden unterhalb des Beitrags Galerien angezeigt, die in derselben Kategorie veroffentlicht wurden. Anpassen lasst sich das alles uber den Customizer.

## Vorbereitungen fur die Erstellung des eigenen WordPress-Themes

Bevor wir beginnen, mussen wir ein paar Vorbereitungen treffen. Zuerst mussen wir uns naturlich WordPress installieren. Wie das funktioniert, [konnt ihr in diesem Beitrag nachlesen](http://t3n.de/news/testen-ausprobieren-5-einfache-wege-lokale-wordpress-installation-600360/).

Nachdem wir jetzt eine WordPress-Installation vorliegen haben, konnen wir uns schnell ein paar Beitrage, Seiten und andere Inhalte anlegen, indem wir die Testdaten von [WP Test ](http://wptest.io/) importieren. Geht dafur im WordPress-Backend auf „Werkzeuge" > „Import" und wahlt dort den Punkt „WordPress" in der Tabelle aus. Anschließend werdet ihr aufgefordert, das entsprechende Plugin zu installieren und konnt danach die XML-Datei importieren, die sich in dem ZIP-Archiv befindet.

Um das Theme wahrend der Entstehung immer mal wieder auf Fehler zu uberprufen, installieren wir uns jetzt noch das Plugin „[Theme Check ](https://de.wordpress.org/plugins/theme-check/)". Alle anderen Plugins solltet ihr deaktivieren, wenn es sich nicht um weitere Entwickler-Plugins handelt. In eurer `wp-config.php`-Datei setzen wir jetzt noch die Konstante `WP_DEBUG` auf `true` (die entsprechende Zeile sieht dann so aus:

`define('WP_DEBUG', true);`

Im nachsten Teil kummern wir uns dann um die `style.css`-Datei.


