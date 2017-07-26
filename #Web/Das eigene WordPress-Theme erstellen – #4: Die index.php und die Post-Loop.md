# Das eigene WordPress-Theme erstellen – #4: Die index.php und die Post-Loop

_Captured: 2015-12-04 at 16:37 from [t3n.de](http://t3n.de/news/wordpress-theme-erstellen-index-php-637682/)_

## Kein WordPress-Theme ohne `index.php`

Die `index.php` ist wie die `style.css` aus [unserem zweiten Teil](http://t3n.de/news/grosse-t3n-guide-eigenen-wordpress-theme-das-grundgeruest-555808/) eine Pflicht-Datei fur ein WordPress-Theme - ohne geht es nicht. In der [Template-Hierarchie eines WordPress-Themes ](https://developer.wordpress.org/themes/basics/template-hierarchy/#visual-overview) ist die `index.php` die allerletzte Fallback-Datei. Wenn also beispielsweise eine Seite angezeigt wird, euer Theme aber keine `page.php` und keine Datei fur eine bestimmte Seite enthalt, so wird auf die `index.php` zuruckgegriffen.

In erster Linie ist die `index.php` aber fur die Darstellung der Blog-Übersicht gedacht. Als Alternative fur den Fall, dass das Blog als Startseite fungiert, gibt es noch die `home.php`. Ihr konntet also die Darstellung verandern, wenn das Blog als Startseite genutzt wird. So sieht unsere `index.php` aus:
    
          1. <?php get_header();?>
      2. <mainrole="main">
      3. <?php if( have_posts()){
      4. while( have_posts()){
      5. 				the_post();
      6. 				get_template_part('content', get_post_format());
      7. 		the_posts_pagination( array('type'=>'list'));?>

Ziemlich ubersichtlich, oder? Mit der `get_header()`-Funktion wird die `header.php`, [die wir im letzten Teil der Reihe behandelt haben](http://t3n.de/news/t3n-guide-wordpress-theme-teil-3-alternative-startseite-galerie-teaser-558172/), eingebunden. Innerhalb des `main`-Elements findet ihr einen elementaren Teil von WordPress: Die Loop. Das ist das Standard-Prozedere, wie in WordPress eine Reihe von Beitragen ausgegeben wird. Mit `if ( have_posts() )` prufen wir, ob Beitrage gefunden wurden.

Wenn das so ist, starten wir die Schleife und lassen sie so lange laufen, bis `have_posts()` nicht mehr wahr ist, es also nicht noch mehr Beitrage gibt. `the_post()` holt die Daten zu dem aktuellen Beitrag aus der Datenbank. Innerhalb dieser `while`-Schleife stehen uns jetzt nach dem `the_post()`-Aufruf Funktionen zur Verfugung, um Informationen zu dem Beitrag anzuzeigen, der gerade durchlaufen wird - zum Beispiel `the_title()` fur die Ausgabe des Titels.

Theoretisch konnten wir uns jetzt bereits in der `index.php` um die Ausgabe des Beitrags fur die Blog-Seite kummern. Da wir aber eine unterschiedliche Darstellung fur Beitrage vom Typ „Bild" und „Galerie" erreichen wollen, gehen wir einen anderen Weg:
    
          1. get_template_part('content', get_post_format());

Mit dieser Zeile sorgen wir dafur, dass eine Datei mit dem Prafix `content-` gefolgt von der Bezeichnung des Post-Formats eingebunden wird. Im Fall einer Galerie ware das die `content-gallery.php`. Fur Standard-Beitrage und solche, fur die keine besondere `content-`-Datei angelegt wurde, wird die Datei `content.php` eingebunden. In diesen Dateien, die wir in spateren Teilen besprechen werden, findet dann die Ausgabe der Beitrage fur die Blog-Seite statt.

Mit dem Aufruf der `the_posts_pagination()`-Funktion geben wir bei Bedarf eine Pagination aus, damit auch altere Beitrage angesehen werden konnen. Mit der `get_sidebar()`-Funktion binden wir die `sidebar.php` und mit `get_footer()` die `footer.php` ein.

## Der Code auf GitHub

Im [GitHub-Repository zu dieser Reihe ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe) gibt es den Tag „[v0.3 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.3)". Dort findet ihr den Stand des Themes nach diesem Artikel.

