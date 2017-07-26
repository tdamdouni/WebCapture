# Das eigene WordPress-Theme erstellen – #2: Die style.css und die Metadaten eures Themes

_Captured: 2015-12-04 at 16:33 from [t3n.de](http://t3n.de/news/grosse-t3n-guide-eigenen-wordpress-theme-das-grundgeruest-555808/)_

Die `style.css` ist eine der wichtigsten Dateien, wenn es um die Erstellung eines [WordPress-Themes](http://t3n.de/tag/wordpress-themes) geht. Ein funktionierendes Theme kann theoretisch nur aus `style.css` und `index.php` bestehen - mehr Dateien braucht es im Grunde nicht. In die `style.css`-Datei kommen namlich die sogenannten Header-Informationen eures Themes.

## Notwendige Angaben fur ein WordPress-Theme

Fur ein funktionierendes Theme reicht die Angabe des Namens. Fur das Hochladen im Theme-Directory mussen allerdings mehr Informationen eingetragen werden. Zwingend notwendig sind die folgenden Angaben:

  * `Theme Name` - der Name des Themes.
  * `Description` - eine kurze Beschreibung des Themes.
  * `Author` - der Name des Entwicklers.
  * `Version` - die Versionsnummer des Themes.
  * `Licence` - die Lizenz, unter der das Theme steht.
  * `Licence URI` - der Link zu der Lizenz.

Die ersten Punkte sollten selbsterklarend sein. Zum Thema Lizenz: Alle Themes, die in das Theme-Directory von WordPress aufgenommen werden sollen, mussen zu 100 Prozent der GPL oder einer kompatiblen Lizenz entsprechen. Darauf musst ihr auch bei eingebundenen Skripten oder ahnlichem achten.

Wenn ihr euch mal unsicher seid, ob eine Lizenz kompatibel ist, konnt ihr beispielsweise im #themereview-Channel des [offiziellen WordPress-Slack ](https://wordpress.slack.com/) fragen. Wie ihr euch dafur registrieren konnt, zeigt [eine Seite auf make.WordPress.org ](https://make.wordpress.org/chat/).

## Kurz und ubersichtlich: Die style.css-Datei unseres Themes

Neben diesen vorgeschriebenen Angaben gibt es noch ein paar weitere. So sieht die `style.css`-Datei unseres Themes aus:
    
          1. /*
      2. Description: Bornholm is great for your photoblog or portfolio website. The theme comes with two page templates. One template shows the last galleries from your categories and the other shows all your galleries on one page. Furthermore, it brings two widgets that allow you to display the last galleries and to display featured galleries. If you already have images on your blog, you should regenerate the thumbnails.
      3. Tags: white, light, two-columns, right-sidebar, custom-menu, post-formats, sticky-post, translation-ready, threaded-comments, photoblogging

Zusatzlich haben wir hier noch die `Theme URI` eingefugt, die auf eine Seite mit genaueren Details zum Theme verweisen muss. Eine Demo-Version sollte hier nicht verlinkt werden. Die Zeile `Author URI` ist ebenfalls neu und enthalt eine URL zur Website des Entwicklers. Mit der Angabe von `Tags` konnt ihr euer Theme im Theme-Directory besser auffindbar machen. Die verfugbaren Begriffe konnt ihr unter dem Punkt „Feature Filter" auf der [Theme-Seite von WordPress.org ](https://wordpress.org/themes/) einsehen. Zum Schluss folgt noch die Angabe der Text-Domain, die fur die Übersetzung des Themes notwendig ist.

Mehr werden wir in diese Datei nicht eintragen. Naturlich konnte hier auch der CSS-Code des Themes Platz finden. [Dagegen spricht aber ](http://wordpress.stackexchange.com/questions/111228/do-i-actually-need-to-link-my-themes-style-css-in-the-theme-files/111505#111505), dass sich die Datei dann nicht komplett komprimieren ließe.

## Der Code zur Serie auf GitHub

Den Quelltext zu der Serie gibt es auf GitHub. Im [dazugehorenden Repository ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe) findet ihr Tags, die jeweils dem Stand des Themes nach einem Teil der Reihe entsprechen. Den Tag zum Stand dieses Artikels findet [ihr hier ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.1).

