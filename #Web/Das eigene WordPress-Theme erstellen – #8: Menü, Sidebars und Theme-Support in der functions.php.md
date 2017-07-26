# Das eigene WordPress-Theme erstellen – #8: Menü, Sidebars und Theme-Support in der functions.php

_Captured: 2015-12-04 at 16:42 from [t3n.de](http://t3n.de/news/wordpress-theme-menue-und-sidebar-registrieren-650162/)_

Um unser [Theme](http://t3n.de/tag/templates) grundlegend funktionsfahig zu machen, fehlen nur noch ein paar Dinge. Bisher kann der Nutzer das Menu und die Sidebars nicht im Backend verwalten. Neben der Registrierung des Menus und der drei Sidebars werden wir aber auch den Support fur die Post-Formate et cetera hinzufugen.

## Unterstutzung fur WordPress-eigene Funktionen hinzufugen

Es gibt WordPress-Funktionen, die in einem Theme explizit aktiviert werden mussen. Von Haus aus unterstutzt ein Theme beispielsweise nicht die Moglichkeit, Featured Images zu setzen. All diese Funktionen lassen sich uber die `add_theme_support()`-Funktion hinzufugen, indem die jeweiligen Parameter ubergeben werden. Die Funktion dafur sieht in unserem Theme so aus und kommt an den Anfang unserer `functions.php`:
    
          1. /**
      2.  * Adds theme support for custom header, feed links, title tag, post formats, HTML5 and post thumbnails
      3. function bornholm_add_theme_support(){
      4. 	add_theme_support('custom-header');
      5. 	add_theme_support('automatic-feed-links');
      6. 	add_theme_support('title-tag');
      7. 	add_theme_support('post-formats', array(
      8. 	add_theme_support('html5', array(
      9. 	add_theme_support('post-thumbnails');
      10. add_action('after_setup_theme','bornholm_add_theme_support');

Da es hier immer wieder ein Aufruf derselben Funktion ist, werde ich die Auswirkung der verschiedenen Parameter erklaren.

  * `custom-header`. Durch Übergabe dieses Parameters kann der Nutzer im Customizer ein eigenes Header-Bild festlegen sowie die Textfarbe im Header andern. Das Bild wird in der `header.php` unseres Themes - sofern festgelegt - als Logo genutzt. [Beschrieben ist das im dritten Teil der Reihe](http://t3n.de/news/t3n-guide-wordpress-theme-teil-3-alternative-startseite-galerie-teaser-558172/).
  * `automatic-feed-links`. Wie ihr euch vermutlich bereits gedacht habt, werden durch diesen Aufruf automatisch Links zu Feeds in das `head`-Element eingefugt. Das ist beispielsweise immer der Link zum Blog-Feed.
  * `title-tag`. Seit WordPress 4.1 gibt es diese neue Moglichkeit, das `title`-Element zu erzeugen. Ab WordPress 4.4 wird die `wp_title()`-Funktion, die bis 4.1 dafur genutzt wurde, als veraltet gekennzeichnet.
  * `post-formats`. Mit diesem Parameter und dem Array als zweiten Parameter aktivieren wir die verschiedenen Beitragsformate wie Galerie, Link, Zitat et cetera. An dieser Stelle habt ihr die freie Wahl, ob ihr alle Formate in das Array schreibt, oder nur ein paar aktivieren mochtet.
  * `html5`. Wenn ihr die Standard-Ausgabe von einigen WordPress-Funktionen auf HTML5-Markup umstellen wollt, gibt es hier die Moglichkeit dazu. Seit WordPress 3.6 konnen die Werte `comment-list`, `comment-form` und `search-form` an das Array ubergeben werden. Fur `gallery` und `caption`, die seit WordPress 3.9 unterstutzt werden, wird dann von WordPress das `figure`\- und `figcaption`-Element fur Bilder und deren Beschriftungen genutzt. [Eigentlich sollte mit WordPress 4.2 die Unterstutzung fur Widgets eingefuhrt werden ](https://make.wordpress.org/core/2015/03/11/html5-widgets-in-wordpress-4-2/), was dann aber wegen Unklarheiten erstmal auf Eis gelegt wurde.
  * `post-thumbnails`. Durch Übergabe dieses Parameters lassen sich bei Beitragen und Seiten Featured Images hinzufugen. Optional konnt ihr als zweiten Parameter ein Array von Beitragstypen ubergeben, fur die diese Option nur gelten soll. Wenn ihr Featured Images nur fur Beitrage haben mochtet, sieht das so aus: `'post-thumbnails', array( 'post' )`.

Diese Funktion ubergeben wir an den Hook `after_setup_theme`. Wenn die Funktion an einen Hook ubergeben wurde, der spater ausgefuhrt wird, dann konnte das fur einige Features zu spat sein.

## Das Menu registrieren

Damit der Nutzer unseres Themes auch frohlich Menupunkte zum Menu hinzufugen kann, mussen wir es im Backend naturlich zuganglich machen. Die notwendige Funktion dafur sieht so aus und kann gleich nach der `bornholm_add_theme_support()`-Funktion eingefugt werden:
    
          1. function bornholm_menus(){
      2.     register_nav_menus( array(
      3. 'header-menu'=> __('Header Menu','bornholm'),
      4. add_action('init','bornholm_menus');

Über die `register_nav_menus()`-Funktion konnen - wie der Name sagt - Menus registriert werden. Theoretisch wurde uns an dieser Stelle auch die Funktion [fur ein einzelnes Menu ausreichen ](https://developer.wordpress.org/reference/functions/register_nav_menu/), aber so konnen wir spater schneller weitere hinzufugen, falls wir einen weiteren Menubereich brauchen.

In einem Array erwartet die Funktion Schlussel-Wert-Paare, die jeweils einem Menu entsprechen. Der Schlussel `header-menu` ist dabei der eindeutige Bezeichner der Menu-Position und `__( 'Header Menu', 'bornholm' )` der ubersetzbare Titel, der im Menubereich des Backends angezeigt wird, wie im Screenshot zu sehen. Mit diesem Code-Schnipsel hat der Nutzer jetzt im Backend den neuen Menupunkt „Menus" unter dem Oberpunkt „Design" und kann sein Menu verwalten und anpassen. Seit WordPress 4.3 ist das zusatzlich auch im Customizer moglich.

![Die Menü-Position ist der beschreibende Titel, der im Array von der register_nav_menus\(\)-Funktion steht. \(Screenshot: eigene WordPress-Installation\)](http://t3n.de/news/wp-content/uploads/2015/10/wordpress-theme-menue-position-595x332.jpg)

> _Die Menu-Position ist der beschreibende Titel, der im Array von der register_nav_menus()-Funktion steht. (Screenshot: eigene WordPress-Installation)_

Wenn wir uns nun an die `header.php` zuruck erinnern, in der wir das Menu ausgeben, dann war dafur dieser Teil verantwortlich:
    
          1. wp_nav_menu( array(
      2. 'theme_location'=>'header-menu',
      3. 'container'=>'',
      4. 'fallback_cb'=>'__return_false'

Dabei muss der Wert fur `theme_location` dem Schlussel in dem Array aus der `register_nav_menus()`-Funktion entsprechen - in diesem Fall `header-menu`.

## Die Sidebars registrieren

Wir haben [im letzten Teil der Reihe](http://t3n.de/news/wordpress-theme-erstellen-sidebar-und-footer-648235/) insgesamt drei Sidebars eingefugt. Eine in der Sidebar des Themes und zwei im Footer. Die Funktion fur die `functions.php`, die diese Sidebars in dem Bereich der Widget-Verwaltung sichtbar macht, sieht so aus:
    
          1. function bornholm_sidebars(){
      2. 	register_sidebar( array(
      3. 'name'=> __('Sidebar','bornholm'),
      4. 'id'=>'sidebar-1',
      5. 'description'=>'',
      6. 'before_widget'=>'<div class="widget clearfix %2$s">',
      7. 'after_widget'=>'</div>',
      8. 'before_title'=>'<h3 class="widget-title">',
      9. 'after_title'=>'</h3>'
      10. 	register_sidebar( array(
      11. 'name'=> __('Footer Widget Area (top)','bornholm'),
      12. 'id'=>'footer-widget-area-top',
      13. 'description'=> __('This widget area is shown on the top of the footer','bornholm'),
      14. 'before_widget'=>'<div class="widget %2$s">',
      15. 'after_widget'=>'</div>',
      16. 'before_title'=>'<h3 class="widget-title">',
      17. 'after_title'=>'</h3>'
      18. 'name'=> __('Footer Widget Area (bottom)','bornholm'),
      19. 'id'=>'footer-widget-area-bottom',
      20. 'description'=> __('This widget area is shown on the bottom of the footer','bornholm'),
      21. 'before_widget'=>'<div class="widget %2$s">',
      22. 'after_widget'=>'</div>',
      23. 'before_title'=>'<h3 class="widget-title">',
      24. 'after_title'=>'</h3>'
      25. add_action('widgets_init','bornholm_sidebars');

Wie unschwer zu erkennen, wird fur jede Sidebar die `register_sidebar()`-Funktion aufgerufen. Diese Funktion erwartet in einem Array die verschiedenen Angaben zu der Sidebar:

  * `name`. Dieser Wert ist der Name der Sidebar, der in der Widget-Verwaltung angezeigt wird.
  * `id`. Die eindeutige ID der Sidebar. Darauf greift unter anderem die `dynamic_sidebar()`-Funktion zu, um eine bestimmte Sidebar auszugeben. Beispielsweise mit `dynamic_sidebar( 'sidebar-1' );`, [wie im letzten Teil der Reihe gezeigt](http://t3n.de/news/wordpress-theme-erstellen-sidebar-und-footer-648235/).
  * `description`. Eine Beschreibung der Sidebar, damit der Nutzer weiß, wo sie ausgegeben wird.
  * `before_widget`. Der HTML-Code, der vor dem Widget ausgegeben wird. Mit dem `%2$s`-Platzhalter wird die Art des Widgets eingefugt. Bei dem Such-Widget ware das die Ausgabe `widget_search`. Mit `%1$s` konnte noch zusatzlich ein eindeutiger Bezeichner des Widgets als ID eingesetzt werden. Das wurde dann so aussehen: `id="%1$s"`.
  * `after_widget` enthalt entsprechend den Code, der nach dem Widget ausgegeben werden soll.
  * `before_title`. Der HTML-Code, der vor dem Titel des Widgets erscheinen soll.
  * `after_title` gibt entsprechende den Code hinter dem Titel aus.

Mit diesen vorgenommenen Änderungen sollten die drei Sidebars jetzt im Backend auftauchen. Der Nutzer kann nun also sein Menu verwalten und Widgets zu den Sidebars hinzufugen, die im Frontend auch bereits ausgegeben werden.

## Das Theme auf GitHub

Wie immer findet ihr den aktuellen Stand des Themes [auf GitHub ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe). Den Code, der bis nach diesem Teil fertig gestellt ist, gibt es unter dem Tag „[v0.6 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.6)".

