# Das eigene WordPress-Theme erstellen – #6: Das Theme auf die Übersetzung vorbereiten

_Captured: 2015-12-04 at 16:40 from [t3n.de](http://t3n.de/news/wordpress-theme-uebersetzen-645450/)_

Wenn ein Theme in das [Theme-Directory von wordpress.org ](https://de.wordpress.org/themes) hochgeladen werden soll, mussen alle sichtbaren Strings englisch sein. Es ware naturlich schon, wenn unser Theme auch die Moglichkeit bietet, in andere Sprachen - etwa Deutsch - ubersetzt zu werden.

Um eine Übersetzung nach Fertigstellung des Themes zu ermoglichen, mussen samtliche Zeichenketten, die ubersetzbar sein sollen, innerhalb einer gettext-Funktion stehen. Dabei gibt es zwei Arten: mit und ohne Kontext fur den Übersetzer.

## Übersetzung ohne Kontext-Hilfe in eindeutigen Fallen

Bei einigen Zeichenketten braucht der Übersetzer keinen Kontext, um die richtige Übersetzung zu erstellen. Im [letzten Teil der Reihe](http://t3n.de/news/wordpress-theme-erstellen-content-php-643761/) haben wir beispielsweise fur Nutzer mit einer bestimmten Berechtigung im Footer einen Link fur die Bearbeitung eines Beitrags ausgegeben:
    
          1. edit_post_link( __('Edit','bornholm'),'<span class="edit-link"> · ','</span>');

Wichtig fur die Übersetzungsfahigkeit ist dabei dieser Teil:
    
          1. __('Edit','bornholm')

Die `__()`-Funktion (**mit zwei Unterstrichen**) ist ein Aufruf der `translate()`-Funktion. [Diese Funktion ](https://developer.wordpress.org/reference/functions/translate/) erwartet als ersten Parameter den zu ubersetzenden String und als zweiten die Angabe einer Domain. Die Domain muss innerhalb eines Themes immer gleich sein (eine Ausnahme davon ist beispielsweise ein Framework, das eine eigene Übersetzung mitbringt) und mit dem Wert fur `Text Domain` in der `style.css` ubereinstimmen. Das ist bei uns `bornholm`. Damit ist dieses Wort fur die Übersetzung vorbereitet.

Wenn ihr den String gleich ausgeben mochtet und nicht fur die weitere Verwendung benotigt, wie im Beispiel oben als Parameter fur eine Funktion, konnt ihr die `_e()`-Funktion nutzen:
    
          1. _e('Posted in ','bornholm');

In diesem Beispiel, ebenfalls aus dem funften Teil der Reihe, mochten wir die Zeichenkette `Posted in ` oder deren Übersetzung ausgeben. Wir ubergeben wieder ganz normal den zu ubersetzenden String und die Text-Domain. Der Unterschied zu der `__()`-Funktion ist, dass in der `_e()`-Funktion folgende Zeile steht:
    
          1. echo translate( $text, $domain );

Bei der Funktion mit den zwei Unterstrichen steht statt des `echo` ein `return`.

Als letzten Fall fur die Übersetzung ohne Kontext gibt es noch die Singular-/Plural-Form. Einige Strings verandern sich, je nach ubergebener Anzahl. Etwas vereinfacht haben wir da in unserem Theme das folgende Beispiel:
    
          1. _n('This gallery contains %1$s photo.','This gallery contains %1$s photos.', $total_images,'bornholm'),
      2. number_format_i18n( $total_images ));

In erster Linie geht es uns dabei um die mittlere Zeile. Die `_n()`-Funktion ruft die `translate_plural()`-Methode der `Translations`-Klasse auf. Als Parameter wird zuerst die Singular-Form ubergeben, gefolgt von der Plural-Form, einer Zahl und der Text-Domain. Wenn die Zahl in `$total_images` großer als 1 ist, wird die Plural-Variante ausgegeben.

## Übersetzung mit Kontext fur die Übersetzer

In einigen Fallen sollten die Übersetzer den Kontext der Übersetzung kennen, um eine Zeichenkette korrekt ubersetzen zu konnen. In unserem Theme ist das beispielsweise bei dem angepassten Weiterlesen-Link der Fall, da sich der Übersetzer nicht zangsweise erschließen kann, was fur `%s` eingesetzt wird:
    
          1. $text = _x('Continue reading “%s”','s = post title','bornholm');

Die Funktion `_x()` ruft die `translate_with_gettext_context()`-Funktion auf und gibt das Ergebnis mittels `return` zuruck. Als Parameter wird zuerst der String fur die Übersetzung ubergeben, gefolgt von einer Hilfe fur den Übersetzer und der Text-Domain. In dem Übersetzungsprogramm Poedit sieht das dann so aus:

![Übersetzung mit Kontext in Poedit. \(Screenshot: Poedit\)](http://t3n.de/news/wp-content/uploads/2015/10/wordpress-theme-erstellen-uebersetzung-595x234.jpg)

> _Übersetzung mit Kontext in Poedit. (Screenshot: Poedit)_

Neben dieser Funktion gibt es noch aquivalente Funktionen zu den weiteren Gettext-Funktionen ohne Kontext. Mit `_ex()` konnt ihr die Übersetzung sofort ausgeben lassen. Auch eine Version fur Singluar-/Plural-Versionen gibt es: `_nx()`. Zwischen den Nummer-Parameter und die Text-Domain kommt hier der Kontext.

Wenn ihr noch genauere Informationen haben mochtet, beispielsweise die nachtragliche Pluralisierung betreffend, werdet ihr auf der [Internationalization-Seite von developer.wordpress.org ](https://developer.wordpress.org/themes/functionality/internationalization/) fundig.

## Der Theme-Code auf GitHub

Auch, wenn in dieser Reihe kein neuer Code dazugekommen ist: [Hier findet ihr den Code unseres WordPress-Themes auf GitHub ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/).

