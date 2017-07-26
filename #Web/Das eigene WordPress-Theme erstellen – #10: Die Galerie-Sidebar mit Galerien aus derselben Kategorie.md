# Das eigene WordPress-Theme erstellen – #10: Die Galerie-Sidebar mit Galerien aus derselben Kategorie

_Captured: 2015-12-04 at 16:45 from [t3n.de](http://t3n.de/news/eigene-wordpress-theme-erstellen-653702/)_

Im [letzten Teil der Reihe](http://t3n.de/news/wordpress-theme-einzelansicht-single-php-651782/) haben wir bereits die `sidebar-gallery.php` angelegt, die dann angezeigt wird, wenn wir uns auf der Einzelansicht einer Galerie befinden:
    
          1. <?php if( $format =='gallery'){

![Die Links zu Galerien derselben Kategorie. \(Screenshot: eigene WordPress-Installatio; Fotos: Dennis Brinkmann\)](http://t3n.de/news/wp-content/uploads/2015/11/wordpress-theme-erstellen-sidebar-gallery-595x470.jpg)

> _Die Links zu Galerien derselben Kategorie. (Screenshot: eigene WordPress-Installatio; Fotos: Dennis Brinkmann)_

In dieser Sidebar, die unter den Galerie-Bildern angezeigt wird, mochten wir weitere Galerien aus der Kategorie anzeigen, aus der die aktuell angezeigte Galerie stammt. Daruber hinaus soll gegebenenfalls ein Link auf die Kategorie ausgegeben werden. Wie das aussehen soll, seht ihr in dem Screenshot oben. Zudem binden wir darunter noch eine richtige Sidebar ein, die der Nutzer ganz normal mit Widgets befullen kann. Spater mochten wir ermoglichen, dass der Nutzer im Customizer die Anzahl der Galerien aus derselben Kategorie einstellen und die Anzeige auch deaktivieren kann, indem er eine Null eintragt.

Diesen Teil klammern wir jetzt aber noch aus und die `sidebar-gallery.php` sieht nach Entfernung dieser Teile so aus:
    
          1. <asideid="sidebar-gallery"role="sidebar"class="clearfix">
      2. <divid="sidebar-content">
      3. <?php $number_of_galleries =3;
      4.         $category_ids = bornholm_get_the_category_ids( $post->ID );
      5.         $args         = array(
      6. 'orderby'=>'name',
      7. 'include'=> $category_ids,
      8.         $categories   = get_categories( $args );
      9.         $exclude_id   = $post->ID;
      10. foreach( $categories as $cat ){
      11.             $title = sprintf( _x('More galleries from %1$s','1 = name of category','bornholm'), $cat->name );
      12.             bornholm_get_galleries_from_category( $cat, $exclude_id, $number_of_galleries,'h3', $title,false);
      13. if( is_active_sidebar('sidebar-gallery')){?>
      14. <divclass="widgets">
      15. <?php dynamic_sidebar('sidebar-gallery');?>
      16. <?php }?>

Zuerst legen wir die Zahl der Galerien, die spater angepasst werden kann, auf drei fest. Im Anschluss benotigen wir die IDs von den Kategorien, die dem Beitrag zugewiesen wurden. Dafur nutzen wir die `bornholm_get_the_category_ids()`-Funktion und ubergeben die ID des Beitrags. Diese Funktion kommt, wie ihr vermutlich bereits erwartet habt, in die `functions.php`, und sieht folgendermaßen aus:
    
          1. function bornholm_get_the_category_ids ( $post_id ){
      2.     $category_ids = get_the_category( $post_id );
      3.     $counter =0;
      4. foreach( $category_ids as $category_id ){
      5. if( $counter ==0){
      6.             $category_ids = $category_id->cat_ID;
      7.             $category_ids .=", $category_id->cat_ID";
      8. return $category_ids;

Zuerst holen wir uns die Kategorien mit der `get_the_category()`-Funktion, die ein Array von Objekten zuruckgibt - fur jede Kategorie ein Objekt. Da wir aber fur die weitere Verarbeitung eine kommaseparierte Liste der Kategorien brauchen, mussen wir uns die jetzt zusammenbauen. Dafur setzen wir einen Counter auf `0` und durchlaufen die Kategorie-Objekte in einer `foreach`-Schleife.

Wenn der Counter den Wert `0` hat, weisen wir der Variable `$category_ids` die ID des gerade behandelten Kategorie-Objekts zu. Danach erhohen wir den Counter. Fur die eventuellen nachfolgenden Durchlaufe fugen wir der Variable mit der ersten ID die weiteren IDs hinzu und stellen der ID ein Komma vor. Wenn alle Kategorie-Objekte durchlaufen sind, geben wir die Liste zuruck.

Als nachstes legen wir in der `sidebar-gallery.php` die Argumente fest, die wir an die `get_categories()`-Funktion ubergeben mochten. Das Ergebnis soll nach dem Namen sortiert sein und nur die Kategorien enthalten, die wir gerade als Liste zusammengesetzt haben. Im Anschluss holen wir uns die Kategorie-Objekte mit `get_categories()` und legen die ID des aktuell angezeigten Galerie-Beitrags als ID fest, die bei der Anzeige ausgespart werden soll. Wir mochten ja nicht den Beitrag empfehlen, den sich der Besucher gerade ansieht:
    
          1. $args         = array(
      2. 'orderby'=>'name',
      3. 'include'=> $category_ids,
      4. $categories   = get_categories( $args );
      5. $exclude_id   = $post->ID;

Ihr fragt euch jetzt vermutlich, warum wir uns zweimal die Kategorien holen - einmal mit `get_the_category()` und das andere Mal mit `get_categories()`. Theoretisch konnten wir auch mit dem Ergebnis-Array aus `get_the_category()` direkt arbeiten, ohne den „Umweg" uber `get_categories()`. Allerdings haben wir in der ` get_the_category()`-Funktion keine Moglichkeit, das Ergebnis zu sortieren.

Der nachste Schritt ist, die erhaltenen Kategorien zu durchlaufen und jeweils die Galerien auszugeben. Dafur ist in der `sidebar-gallery.php` dieser Teil verantwortlich:
    
          1. foreach( $categories as $cat ){
      2.     $title = sprintf( _x('More galleries from %1$s','1 = name of category','bornholm'), $cat->name );
      3.     bornholm_get_galleries_from_category( $cat, $exclude_id, $number_of_galleries,'h3', $title,false);

Zuerst legen wir in der `foreach()`-Schleife einen ubersetzbaren Titel fest, der uber den Galerien einer Kategorie angezeigt werden soll. Danach rufen wir die `bornholm_get_galleries_from_category()`-Funktion auf und ubergeben als Parameter das Kategorie-Objekt des aktuellen Durchlaufs, die ID des Beitrags, der ausgespart werden soll, die Nummer der anzuzeigenden Galerien, die Titel-Hierarchie, den Titel und als letztes einen booleschen Operator, der angibt, ob das Ergebnis hierarchisch angezeigt werden soll. Das benotigen wir spater, wenn wir die Funktion fur die alternative Startseite einsetzen und Unterkategorien direkt unter der Oberkategorie anzeigen wollen.

Diese Funktion kommt wieder in die `functions.php` und sieht wie folgt aus:
    
          1.  * @param $cat, $exclude_id ,$number_of_galleries, $heading, $title, $show_child_category_hierarchy
      2. function bornholm_get_galleries_from_category ( $cat, $exclude_id, $number_of_galleries, $heading, $title, $show_child_category_hierarchy ){
      3.     $galleries_args = bornholm_galleries_args( $cat, $exclude_id );
      4.     $galleries      = get_posts( $galleries_args );
      5. if( $galleries ){
      6.         $total_galleries = count( $galleries );
      7.         $gallery_counter =0;?>
      8. <div class="gallery-category clearfix">
      9. <?php if( $title !=''){?>
      10. <<?php echo $heading;?>class="category-title"><?php echo $title;?></<?php echo $heading;?>>
      11. <?php }?>
      12. <?php bornholm_loop_galleries_from_category( $galleries, $total_galleries, $number_of_galleries, $gallery_counter, $cat );
      13. if( $show_child_category_hierarchy ){
      14.                 bornholm_get_child_category_galleries( $cat, $number_of_galleries, $exclude_id, $title, $heading );
      15. </div>
      16. <?php }

Zuerst speichern wir die Argumente, anhand derer wir anschließend die Beitrage abrufen, in der `$galleries_args`-Variable. Das ist die Funktion `bornholm_galleries_args()`:
    
          1. function bornholm_galleries_args( $cat, $exclude_id ){
      2.     $args = array(
      3. 'category__in'=> $cat->cat_ID,
      4. 'exclude'=>"$exclude_id",// for the sidebar on a single gallery
      5. 'tax_query'=> array(
      6. 'relation'=>'AND',
      7. 'taxonomy'=>'category',
      8. 'field'=>'slug',
      9. 'terms'=> $cat->slug
      10. 'taxonomy'=>'post_format',
      11. 'field'=>'slug',
      12. 'terms'=>'post-format-gallery'
      13. return $args;

Wir mochten nur Beitrage, die der Kategorie zugewiesen sind, die wir mit `$cat` ubergeben haben. Zudem soll der Beitrag, der gerade angezeigt wird, ausgeschlossen werden. Dafur ubergeben wir dessen ID an den `exclude`-Schlussel. Nun wird es interessant: Wir mochten Beitrage, die zugleich der Kategorie angehoren, die wir gerade behandeln und die vom Post-Format „Galerie" sind. Dafur nutzen wir den `tax_query`-Schlussel und verbinden die beiden Bedingungen mit dem logischen `AND`-Operator. Wir prufen in beiden Fallen das Feld `slug`, das im Fall der Kategorie-Prufung mit dem Slug der aktuellen Kategorie und beim Post-Format mit `post-format-gallery` ubereinstimmen muss.

Zuruck in der `bornholm_get_galleries_from_category()`-Funktion ubergeben wir diese Parameter an `get_posts()`. Wenn wir hier ein Ergebnis erhalten, es also weitere Galerien in dieser Kategorie gibt, dann mochten wir sie ausgeben.
    
          1. if( $galleries ){
      2.     $total_galleries = count( $galleries );
      3.     $gallery_counter =0;?>
      4. <div class="gallery-category clearfix">
      5. <?php if( $title !=''){?>
      6. <<?php echo $heading;?>class="category-title"><?php echo $title;?></<?php echo $heading;?>>
      7. <?php }?>
      8. <?php bornholm_loop_galleries_from_category( $galleries, $total_galleries, $number_of_galleries, $gallery_counter, $cat );
      9. if( $show_child_category_hierarchy ){
      10.             bornholm_get_child_category_galleries( $cat, $number_of_galleries, $exclude_id, $title, $heading );
      11. </div>

Zuerst zahlen wir die gefundenen Galerien und setzen einen Counter auf `0` - wir mochten ja nur eine bestimmte Anzahl Galerien ausgeben. Im nachsten Schritt geben wir den Titel aus, falls er festgelegt wurde. Danach rufen wir die `bornholm_loop_galleries_from_category()`-Funktion auf und ubergeben die Galerien, die Anzahl derselben, die Anzahl, die ausgegeben werden soll, den Galerie-Counter und das Kategorie-Objekt. Da wir an dieser Stelle keine hierarchische Darstellung mochten und beim aktuellen Stand des Themes diese Bedingung nie wahr sein wird, lassen wir die `bornholm_get_child_category_galleries()` in diesem Teil komplett außen vor.

Die `bornholm_loop_galleries_from_category()`-Funktion kommt gewohnheitsgemaß ebenfalls in die `functions.php` und sieht folgendermaßen aus:
    
          1.  * Loops through the galleries of the given category and calls the functions for displaying the teaser
      2. function bornholm_loop_galleries_from_category( $galleries, $total_galleries, $number_of_galleries, $gallery_counter, $cat ){
      3.     foreach ( $galleries as $post ){
      4. if( $number_of_galleries >0){
      5. if( $total_galleries > $number_of_galleries ){
      6. if( $gallery_counter > $number_of_galleries ){
      7.                     bornholm_alternative_front_page_more_link( $cat );
      8.         bornholm_alternative_front_page_gallery_teaser( $post );

Zunachst starten wir eine `foreach()`-Schleife und durchlaufen damit die Galerien. Im Anschluss prufen wir, ob uberhaupt Galerien ausgegeben werden sollen. Wenn das der Fall ist, prufen wir, ob die Anzahl der vorhandenen Galerien großer ist als die, die angezeigt werden sollen und erhohen in dem Fall den Galerie-Counter. Wenn dieser Counter großer ist als die Anzahl der Galerien, die angezeigt werden sollen, geben wir mit der Funktion `bornholm_alternative_front_page_more_link()` einen Link zu der Kategorie aus und brechen die `foreach()`-Schleife ab. Solange das nicht passiert, geben wir bei jedem Durchlauf mit der `bornholm_alternative_front_page_gallery_teaser()`-Funktion das Bild und den Titel der Galerie aus.

Die Funktion fur den Weiterlesen-Link sieht so aus und wird, wie der Name verrat, auch fur die alternative Startseite gebraucht:
    
          1. function bornholm_alternative_front_page_more_link( $cat ){
      2.     $text = _x('Display all galleries from “%s”','s = category title','bornholm');
      3.     $more = sprintf( $text, esc_html( $cat->name ));?>
      4. <article class="read-more">
      5. <a href="<?php echo esc_url( get_category_link( $cat->cat_ID ) ) ?>"><?php echo $more ?></a>
      6. </article>

Die ersten zwei Zeilen erinnern an die Funktion fur den normalen Weiterlesen-Link: Wir erstellen einen ubersetzbaren String, der im Englischen beispielsweise so aussieht: Display all galleries from "Sports". Danach geben wir diesen als Link innerhalb eines `article`-Elements aus.

Die Funktion zur Anzeige der Galerien sieht folgendermaßen aus. Wie die `gallery-sidebar.php` ist auch diese Funktion noch nicht im Endzustand, da wir dem Nutzer ermoglichen mochten, den Titel der Galerie zu verstecken:
    
          1. function bornholm_alternative_front_page_gallery_teaser ( $post ){?>
      2. <?php $images_child = bornholm_get_gallery_images( $post->ID );
      3.             bornholm_gallery_header('h3', $images_child,'thumbnail', $post );
      4. }?>
      5. </article>

Innerhalb des `article`-Elements holen wir uns [auf altbekannte Weise](http://t3n.de/news/wordpress-theme-einzelansicht-single-php-651782/) die Bilder des aktuellen Beitrags aus der `foreach()`-Schleife. Auch die Ausgabe des Galerie-Headers durch die `bornholm_gallery_header()`-Funktion [war Teil des letzten Artikels](http://t3n.de/news/wordpress-theme-einzelansicht-single-php-651782/) - der Unterschied ist hier lediglich die andere Überschriften-Ebene und die Bildgroße `thumbnail`.

Nach diesem langeren Ausflug in die `functions.php` konnen wir nun zuruck in die `sidebar-gallery.php`. Nach der Kategorie-Schleife kommt noch dieser Teil, der gegebenenfalls die Sidebar aus dem Backend ausgibt:
    
          1. if( is_active_sidebar('sidebar-gallery')){?>
      2. <div class="widgets">
      3. <?php dynamic_sidebar('sidebar-gallery');?>
      4. </aside>

Diese Sidebar haben wir [im achten Teil](http://t3n.de/news/wordpress-theme-menue-und-sidebar-registrieren-650162/) noch nicht registriert - das holen wir jetzt noch schnell nach. In die `bornholm_sidebars()`-Funktion aus der `functions.php` fugen wir folgenden Teil ein:
    
          1. register_sidebar( array(
      2. 'name'=> __('Gallery Sidebar','bornholm'),
      3. 'id'=>'sidebar-gallery',
      4. 'description'=> __('This sidebar is shown on single gallery pages','bornholm'),
      5. 'before_widget'=>'<div class="widget clearfix %2$s">',
      6. 'after_widget'=>'</div>',
      7. 'before_title'=>'<h3 class="widget-title">',
      8. 'after_title'=>'</h3>'

Damit hatten wir diesen Part geschafft. Unter Galerie-Beitragen sollten jetzt die weiteren Galerien aus der Kategorie angezeigt werden - gegebenenfalls mit einem Link auf die Kategorie-Übersicht.

## Der Code auf GitHub

Wie immer findet ihr den Code des Themes [auf GitHub ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/). Der Stand nach diesem Teil ist festgehalten in dem Tag „[v0.8 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.8)".

