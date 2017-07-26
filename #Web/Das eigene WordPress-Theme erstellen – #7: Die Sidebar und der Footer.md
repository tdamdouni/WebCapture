# Das eigene WordPress-Theme erstellen – #7: Die Sidebar und der Footer

_Captured: 2015-12-04 at 16:41 from [t3n.de](http://t3n.de/news/wordpress-theme-erstellen-sidebar-und-footer-648235/)_

Nachdem wir uns [im letzten Teil](http://t3n.de/news/wordpress-theme-uebersetzen-645450/) um die Übersetzungsfahigkeit des Themes gekummert haben, mussen wir uns nun um die Standard-Sidebar sowie den Footer kummern. Wenn wir auf die `index.php` zuruckblicken, endet die Datei mit folgenden zwei Zeilen:

## Die Sidebar in der `sidebar.php`

Diese beiden Funktionen arbeiten nach demselben Prinzip wie `get_header()` - sie binden die `sidebar.php` beziehungsweise `footer.php` ein. Wir mochten auf den meisten Seiten, außer der Einzelansicht einer Galerie, eine ganz normale Sidebar einbauen. Unsere `sidebar.php` sieht so aus:
    
          1. <asideid="sidebar"role="complementary">
      2. <divid="sidebar-content">
      3. <?php if( is_active_sidebar('sidebar-1')){
      4.             dynamic_sidebar('sidebar-1');

Wir packen die Sidebar in ein `aside`-Element und ein `div`. Mit der `is_active_sidebar()`-Funktion prufen wir, ob die Sidebar mit dem Bezeichner `sidebar-1` aktiv ist. Wenn das der Fall ist, geben wir sie mit der `dynamic_sidebar()`-Funktion aus, der wir wieder den eindeutigen Bezeichner der Sidebar als Parameter ubergeben. Um die Registrierung der Sidebar in der `functions.php` werden wir uns im nachsten Teil kummern - gemeinsam mit der Registrierung des Menus.

## Der Footer des WordPress-Themes

Kummern wir uns jetzt um die `footer.php`:
    
          1. <?php get_sidebar('footer-top');
      2. get_sidebar('footer-bottom');
      3. wp_footer();?>

Wir mochten in unserem Footer zwei Widget-Bereiche - also quasi Sidebars - unterbringen. Dafur nutzen wir wieder die `get_sidebar()`-Funktion, ubergeben aber als Parameter den Slug fur die Datei. `get_sidebar( 'footer-top' );` bindet die Datei `sidebar-footer-top.php` ein, der zweite Aufruf mit dem Parameter `footer-bottom` entsprechend die Datei `sidebar-footer-bottom.php`. Vor dem schließenden `body`-Tag mussen wir noch die `wp_footer()`-Funktion aufrufen. Hier werden dann Skripte ausgegeben, die am Ende der Seite eingebunden werden sollen.

Kommen wir nun noch zu den beiden Widget-Bereichen des Footers. Die `sidebar-footer-top.php` hat den folgenden Inhalt:
    
          1. <footerid="footer"role="contentinfo">
      2. if( is_active_sidebar('footer-widget-area-top')){?>
      3. <asideid="footer-top"class="clearfix">
      4. <?php dynamic_sidebar('footer-widget-area-top');?>

Wir offnen zuerst das `footer`-Element. Danach prufen wir, ob die Sidebar `footer-widget-area-top` aktiv ist und nutzen dafur wieder die `is_active_sidebar()`-Funktion. Wenn die Sidebar mindestens ein Widget enthalt, wird innerhalb eines `aside`-Elements die Sidebar ausgegeben. Und das war's auch schon.

Die `sidebar-footer-bottom.php` ist ahnlich ubersichtlich:
    
          1. if( is_active_sidebar('footer-widget-area-bottom')){?>
      2. <asideid="footer-bottom"class="clearfix">
      3. <?php dynamic_sidebar('footer-widget-area-bottom');?>
      4. <pclass="theme-author"><?php _e('Theme: Bornholm by <a rel="nofollow" href="http://florianbrinkmann.de">Florian Brinkmann</a>','bornholm')?></p>

Hier prufen wir, ob die Sidebar `footer-widget-area-bottom` aktiv ist. Wenn das der Fall ist, geben wir auch diese Sidebar aus. Direkt vor dem schließenden `footer`-Element platzieren wir noch einen Hinweis auf den Ersteller des Themes.

Im nachsten Teil werden wir dann die Grundeinstellungen in der `functions.php` vornehmen, wie etwa Sidebars und Menus registrieren, damit sie im Backend auch genutzt werden konnen.

## Das Theme auf GitHub

Den aktuellen Stand des Themes findet ihr wie immer im [GitHub-Repository ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe) zu der Artikelserie. Den Stand des Themes nach diesem Teil gibt es im [Tag v0.5 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.5).
