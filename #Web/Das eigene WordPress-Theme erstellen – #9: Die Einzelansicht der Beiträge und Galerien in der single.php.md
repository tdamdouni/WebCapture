# Das eigene WordPress-Theme erstellen – #9: Die Einzelansicht der Beiträge und Galerien in der single.php

_Captured: 2015-12-04 at 16:43 from [t3n.de](http://t3n.de/news/wordpress-theme-einzelansicht-single-php-651782/)_

Bisher konnen wir die Anzeige eines einzelnen Beitrags noch nicht von der Übersichtsseite unterscheiden. Dafur gibt es die `single.php`-Datei. Diese Template-Datei wird von WordPress aufgerufen, wenn ein einzelner Beitrag angezeigt wird. Hier nehmen wir auch gleich die Anpassungen fur die Galerie-Ansicht vor, die ein großes Featured Image im Header des Beitrags anzeigen soll. Wie das aussieht, seht ihr im folgenden Screenshot. Oben ist die Einzelansicht einer Galerie abgebildet, unten die Einzelansicht eines ganz normalen Beitrags.

![Die zwei verschiedenen Anzeigemöglichkeiten in der single.php des WordPress-Themes: Oben eine Galerie, unten ein normaler Artikel. \(Screenshot: eigene WordPress-Installation; Fotos: Dennis Brinkmann\)](http://t3n.de/news/wp-content/uploads/2015/10/wordpress-theme-erstellen-single-php-595x793.jpg)

> _Die zwei verschiedenen Anzeigemoglichkeiten in der single.php des WordPress-Themes: Oben eine Galerie, unten ein normaler Artikel. (Screenshot: eigene WordPress-Installation; Fotos: Dennis Brinkmann)_

Da die `single.php` durch die Einruckungen hier im Gesamten nur schwer lesbar ware, poste ich sie gleich stuckweise. Den ersten Teil kennen wir schon aus [dem Artikel mit der `index.php`](http://t3n.de/news/wordpress-theme-erstellen-index-php-637682/). Wir binden die `header.php` ein und starten den Loop.
    
          1. <?php get_header();?>
      2. <mainrole="main">
      3. while( have_posts()){

Nun mussen wir fur die veranderte Anzeige im Header des Beitrags rausfinden, ob es sich um ein Galerie-Post-Format handelt. Dafur gibt es die `get_post_format()`-Funktion, der die ID des Beitrags ubergeben werden muss. Die ID ist im `$post`-Objekt gespeichert. Wir sichern also zuerst das Ergebnis dieser Abfrage in einer Variable und fuhren dann im `header`-Element die Fallunterscheidung durch:
    
          1. $format = get_post_format( $post->ID );?>
      2. <article id="post-<?php the_ID(); ?>"<?php post_class();?>>
      3. <header class="entry-header clearfix">
      4. <?php if( $format =='gallery'){
      5. 			$images = bornholm_get_gallery_images( $post->ID );
      6. 			bornholm_gallery_header('h1', $images,'bornholm_large_gallery_image_for_single_view', $post );
      7. 			bornholm_the_post_header('h1', $post );
      8. </header>

Die Funktion von `the_ID()` und `post_class()` haben wir schon [im Beitrag zur `content.php` besprochen](http://t3n.de/news/wordpress-theme-erstellen-content-php-643761/). Innerhalb des `header`-Elements prufen wir, ob das Ergebnis des `get_post_format()`-Aufrufs dem Wert `gallery` entspricht. Wenn das der Fall ist, mussen wir uns die Bilder aus der Galerie besorgen und das erste davon im Header anzeigen. Andernfalls geben wir den normalen Header mit der `bornholm_the_post_header()`-Funktion aus, die ebenfalls schon in dem Teil mit der `content.php` erlautert wurde.

Beschaftigen wir uns also naher mit dem Fall, dass eine Galerie angezeigt wird. Wir wollen die Galeriebilder in der `$images`-Variable speichern und rufen dafur die `bornholm_get_gallery_images()`-Funktion auf, der wir die ID des Beitrags ubergeben. An dieser Stelle vielen Dank an [Thomas Scholz ](http://toscho.de/), der mir den Großteil dieser Funktion geschrieben und mir bei der Überarbeitung des Theme-Codes einige hilfreiche Tipps gegeben hat. Diese Funktion kommt in die `functions.php` und sieht wie folgt aus:
    
          1. function bornholm_get_gallery_images( $post_id ){
      2.     $post = get_post( $post_id );
      3. // Den Beitrag gibt es nicht, oder er ist leer.
      4. if(! $post || empty ( $post->post_content )){
      5. return array();
      6.     $galleries = get_post_galleries( $post,false);
      7. if( empty ( $galleries )){
      8. return array();
      9.     $ids = array();
      10. foreach( $galleries as $gallery ){
      11. if(! empty ( $gallery['ids'])){
      12.             $ids = array_merge( $ids, explode(',', $gallery['ids']));
      13.     $ids = array_unique( $ids );
      14. if( empty ( $ids )){
      15.         $attachments = get_children( array(
      16. 'post_parent'=> $post_id,
      17. 'post_status'=>'inherit',
      18. 'post_type'=>'attachment',
      19. 'post_mime_type'=>'image',
      20. 'order'=>'ASC',
      21. 'orderby'=>'menu_order',
      22. ));
      23. if( empty ( $attachments )){
      24. return array();
      25.     $images = get_posts(
      26. 'post_type'=>'attachment',
      27. 'post_mime_type'=>'image',
      28. 'orderby'=>'post__in',
      29. 'numberposts'=>999,
      30. 'include'=> $ids
      31. if(! $images &&! $attachments ){
      32. return array();
      33. } elseif (! $images ){
      34. 	    $images = $attachments;
      35. return $images;

Zuerst holen wir uns mit der `get_post()`-Funktion das `$post`-Objekt. Dadurch konnen wir nun prufen, ob es den Beitrag uberhaupt gibt oder ob er leer ist. In beiden Fallen beenden wir den Durchlauf der Funktion und geben ein leeres Array zuruck. Anschließend wollen wir die Galerien des Beitrags ermitteln. Dafur bietet WordPress uns die `get_post_galleries()`-Funktion, die als ersten Parameter das Post-Objekt erwartet. Der zweite Parameter muss ein boolescher Wert sein und gibt an, ob die Ruckgabe als HTML oder als Array erfolgen soll. Da wir fur die weitere Verarbeitung ein Array benotigen, ubergeben wir hier `false`.

Im nachsten Schritt prufen wir, ob es Galerien in dem Beitrag gibt und geben andernfalls wieder ein leeres Array zuruck. Jetzt brauchen wir die IDs von den Bildern in einem Array. Das Ergebnis-Array aus dem `get_post_galleries()`-Aufruf sieht aber bei zwei Galerien in einem Beitrag beispielhaft so aus:
    
          1. [0]=>Array(
      2. [ids]=>769,768
      3. [src]=>Array(
      4. [0]=> http://example.com/2015/10/20/img.jpg 
      5. [1]=> http://example.com/2015/10/20/img-1.jpg 
      6. [1]=>Array(
      7. [ids]=>456,345
      8. [src]=>Array(
      9. [0]=> http://example.com/2015/10/20/img-2.jpg 
      10. [1]=> http://example.com/2015/10/20/img-3.jpg 

Wir mussen also die IDs aus dem `ids`-Eintrag des Arrays bekommen. Da ja mehrere Galerien in einem Beitrag verwendet werden konnen, mussen wir die einzelnen Ergebnisse zu einem langen ID-Array zusammensetzen. Das ist Aufgabe dieses Code-Teils:
    
          1. $ids = array();
      2. foreach( $galleries as $gallery ){
      3. if(! empty ( $gallery['ids'])){
      4.         $ids = array_merge( $ids, explode(',', $gallery['ids']));
      5. $ids = array_unique( $ids );

Wir erstellen zuerst ein leeres Array und speichern es in der `$ids`-Variable. Anschließend durchlaufen wir in einer `foreach`-Schleife alle Galerien aus dem Beitrag und prufen darin, ob wir uberhaupt IDs in dem Array haben. Ist das der Fall, mussen wir gedanklich die nachste Zeile von innen nach außen durchgehen. Damit haben wir zunachst diesen Teil:
    
          1. explode(',', $gallery['ids'])

Dadurch werden die Werte vom Array-Schlussel `$ids` an dem ubergebenen Trennzeichen `,` getrennt und als Array zuruckgegeben. Das sieht fur die erste Galerie aus unserem Beispiel so aus:

Dieses Array hangen wir mit der `array_merge()`-Funktion an das `$ids`-Array an. Hier wird also das lange Array von IDs gebildet. Sind alle Galerien abgearbeitet, werden mit der `array_unique()`-Funktion doppelte Werte aus dem Array entfernt.

Nun gibt es zwei Varianten, wie der `gallery`-Shortcode in WordPress eingesetzt werden kann. Einmal mit ubergebenen IDs der Bilder und einmal ohne. Wenn keine IDs angegeben werden, zeigt der Shortcode einfach alle Bilder an, die zu dem Beitrag hochgeladen wurden. In diesem Fall haben wir zwar keine IDs aus dem `foreach`-Durchlauf, wir wollen aber naturlich trotzdem ein Bild als Titelbild anzeigen.

Wenn also die `$ids`-Variable an dieser Stelle der Funktion leer ist, wurde ein `gallery`-Shortcode ohne IDs eingesetzt. In diesem Fall kommt folgender Code zum Einsatz:
    
          1. if( empty ( $ids )){
      2.     $attachments = get_children( array(
      3. 'post_parent'=> $post_id,
      4. 'post_status'=>'inherit',
      5. 'post_type'=>'attachment',
      6. 'post_mime_type'=>'image',
      7. 'order'=>'ASC',
      8. 'orderby'=>'menu_order',
      9. if( empty ( $attachments )){
      10. return array();

Mit der `get_children()`-Funktion konnen wir die Anhange eines Beitrag ermitteln - also alle Medien, die in einem Beitrag uber die Schaltflache „Dateien hinzufugen" hochgeladen wurden. Um die Dateien fur den richtigen Beitrag zu bekommen, ubergeben wir in dem Parameter-Array fur den Schlussel `post_parent` die ID des Beitrags. Als `post_status` geben wir `inherit` an, was dann dem Post-Status des Beitrags entspricht. Der Post-Type soll einem Anhang entsprechen und der Typ des Anhangs soll `image` sein. Das Ganze soll aufsteigend nach der Menu-Reihenfolge sortiert werden - das entspricht in diesem Fall der Reihenfolge des Hochladens.

Wenn das Ergebnis des Aufrufs leer ist, geben wir erneut ein leeres Array zuruck. Fur den Normalfall, dass ein `gallery`-Shortcode mit IDs der Bilder eingesetzt wird, nutzen wir den folgenden Code-Schnipsel, um die Post-Objekte der Bilder zu erhalten:
    
          1. $images = get_posts(
      2. 'post_type'=>'attachment',
      3. 'post_mime_type'=>'image',
      4. 'orderby'=>'post__in',
      5. 'numberposts'=>999,
      6. 'include'=> $ids

Wir rufen die `get_posts()`-Funktion auf und mochten nur Objekte, die von Typ `attachment` und gleichzeitig ein Bild sind. Daruber hinaus sollen sie so sortiert werden, wie sie in dem Array `$ids` vorkommen, das wir dem `include`-Schlussel ubergeben. Kurz gesagt bekommen wir hier als Ergebnis ein Array mit den Post-Objekten der Bilder, die zu den ermittelten IDs aus den `gallery`-Shortcodes gehoren.

Abschließend prufen wir, ob beide Aufrufe kein Ergebnis geliefert haben und geben in dem Fall ein leeres Array zuruck. Wenn hingegen nur der Aufruf der `get_posts()`-Funktion leer ist, weisen wir der `$images`-Variable das Ergebnis des `get_children()`-Aufrufs zu. Andernfalls behalt die `$images`-Variable den Wert des `get_posts()`-Aufrufs. Danach geben wir das Ergebnis zuruck:
    
          1. if(! $images &&! $attachments ){
      2. return array();
      3. } elseif (! $images ){
      4.     $images = $attachments;
      5. return $images;

Bleibe immer up-to-date. Sichere dir deinen Wissensvorsprung!

  


## Den Galerie-Header ausgeben

Nach dieser komplexeren Funktion mussen wir nun in die `single.[php](http://t3n.de/tag/php)` zuruck. Wir waren bei dieser Stelle im `header`-Element stehengeblieben:
    
          1. if( $format =='gallery'){
      2.     $images = bornholm_get_gallery_images( $post->ID );
      3.     bornholm_gallery_header('h1', $images,'bornholm_large_gallery_image_for_single_view', $post );

In der `$images`-Variable befinden sich jetzt die Post-Objekte der Galeriebilder. Um den Header der Galerie auszugeben, rufen wir die `bornholm_gallery_header()`-Funktion auf. Der erste Parameter ist die Ebene der Überschrift, der zweite die Variable mit den Post-Objekten der Bilder, der dritte die Große des Bildes, das wir ausgeben mochten, und der vierte das Post-Objekt des Beitrags.

Da diese Bildergroße keiner Standardgroße wie etwa `large` entsprechen soll, mussen wir die erst in der `functions.php` anlegen, bevor wir uns der `bornholm_gallery_header()`-Funktion widmen:
    
          1. add_image_size('bornholm_large_gallery_image_for_single_view',1592,9999,false);

Das wars schon. Wir ubergeben als ersten Parameter an die `add_image_size()`-Funktion den eindeutigen Bezeichner, anschließend die maximale Breite und Hohe und zum Schluss, ob das Bild auf diese Werte zugeschnitten werden soll. Um diese Große fur bereits hochgeladene Bilder zu erzeugen, mussen die Thumbnails neu erzeugt werden, beispielsweise mit dem [Regenerate-Thumbnails-Plugin ](https://de.wordpress.org/plugins/regenerate-thumbnails/).

Nun aber zu der Funktion fur den Galerie-Header:
    
          1. /**
      2.  * If there are $images, the function displays the title with an image.
      3. function bornholm_gallery_header( $heading, $images, $size, $post ){
      4. if( $images ){
      5.         bornholm_gallery_title( $heading, $images, $size, $post );
      6.         bornholm_post_title( $heading, $post );

Hier mussen wir wieder testen, ob in der `$images`-Variable uberhaupt Bilder enthalten sind oder nicht. Wenn wir Bilder haben, rufen wir die `bornholm_gallery_title()`-Funktion auf und geben die bekannten Parameter weiter. Gibt es keine Bilder, wird der Beitragstitel mit der `bornholm_post_title()`-Funktion ausgegeben, die wir [im Teil mit der `content.php`](http://t3n.de/news/wordpress-theme-erstellen-content-php-643761/) besprochen haben.

Die `bornholm_gallery_title()`-Funktion sieht folgendermaßen aus:
    
          1. function bornholm_gallery_title( $heading, $images, $size, $post ){
      2. if( $size !='bornholm_large_gallery_image_for_single_view'){?>
      3. <a href="<?php echo esc_url( get_permalink( $post->ID ) ); ?>">
      4. <?php }
      5. if(! $heading ==''){
      6.         echo '<'. $heading .' class="entry-title gallery-title">';
      7.         echo esc_html( $post->post_title );
      8.         echo '</'. $heading .'>';
      9.     bornholm_gallery_featured_image( $size, $images, $post );
      10. if( $size !='bornholm_large_gallery_image_for_single_view'){?>
      11. </a>
      12. <?php }

Wir prufen zuerst, ob die Große des Bildes der entspricht, die fur die Einzelansicht genutzt wird. Ist das nicht der Fall, geben wir einen Link zu dem Beitrag aus. Anschließend setzen wir das Überschriften-Element zusammen und geben darin den Titel des Beitrags aus. Um das Bild anzuzeigen, rufen wir die `bornholm_gallery_featured_image()`-Funktion auf, an die wir die Große des Bildes, die Variable mit den Bildern und das Post-Objekt ubergeben.
    
          1. function bornholm_gallery_featured_image( $size, $images, $post ){
      2.     $image         = array_shift( $images );
      3.     $image_img_tag = wp_get_attachment_image( $image->ID, $size );?>
      4. <figure class="gallery-thumb clearfix">
      5. <?php if( has_post_thumbnail( $post->ID )){
      6.             echo get_the_post_thumbnail( $post->ID, $size );
      7.             echo $image_img_tag;
      8. }?>
      9. </figure>

Da wir nur das erste Bild benotigen, speichern wir den ersten Eintrag des `$images`-Arrays in der `$image`-Varible. Im nachsten Schritt holen wir uns das `img`-Element dieses ersten Bildes durch den Aufruf der `wp_get_attachment_image()`-Funktion. Neben der ID des Bildes muss noch die Große ubergeben werden, in der das Bild ausgegeben werden soll.

Um dem Beitragsautoren die Moglichkeit zu geben, im Header ein anderes Bild als das erste Galerie-Bild anzuzeigen, prufen wir innerhalb des `figure`-Elements zuerst, ob ein Beitragsbild gesetzt ist und geben es aus. Auch hier ubergeben wir als zweiten Parameter an die `get_the_post_thumbnail()`-Funktion wieder unsere eigene Bildgroße. Wenn kein Beitragsbild festgelegt ist, geben wir das Ergebnis des `wp_get_attachment_image()`-Aufrufs aus.

Damit haben wir den Header in der `single.php` abgeschlossen und konnen uns dem nachsten Teil widmen:
    
          1. <divclass="entry-content">
      2. <?php the_content();
      3.         bornholm_paginated_posts_navigation();?>
      4. <footerclass="entry-meta">
      5. <?php bornholm_footer_meta();?>
      6. </article><!-- #post-<?php the_ID(); ?> -->

Wir geben mit der `the_content()`-Funktion den Inhalt des Beitrags aus und rufen anschließend die Funktion auf, die die Pagination von Beitragen mit dem `<\--nextpage-->`-Kommentar ermoglicht. Diese Funktion kommt wieder in die `functions.php` und sieht so aus:
    
          1. function bornholm_paginated_posts_navigation(){
      2.     wp_link_pages( array(
      3. 'before'=>'<ul class="page-link">',
      4. 'after'=>'</ul>',
      5. 'link_before'=>'<li>',
      6. 'link_after'=>'</li>',
      7. ));

Mit der `wp_link_pages()`-Funktion kann in WordPress eine Pagination ausgegeben werden. Als Parameter ubergeben wir die Code-Schnipsel, die vor und hinter der Pagination auftauchen sowie die Teile, die jeden Link umschließen. Die `bornholm_footer_meta()`-Funktion haben wir bereits [im funften Teil der Reihe besprochen](http://t3n.de/news/wordpress-theme-erstellen-content-php-643761/).

Im nachsten Code-Teil geben wir, falls es sich um eine Galerie handelt, eine Sidebar aus:
    
          1. <?php if( $format =='gallery'){
      2.     get_sidebar('gallery');

Die entsprechende `sidebar-gallery.php` legen wir erst mal nur an - die werden wir in einem spateren Teil besprechen. Der letzte Teil der `single.php` sieht folgendermaßen aus:
    
          1.             comments_template('',true);
      2. }?>
      3. </main>
      4. <?php if( $format =='gallery'){

Mit der `comments_template()`-Funktion lasst sich der Kommentarbereich einbinden. Mit dem ersten Parameter kann ein alternativer Pfad zu der Datei ubergeben werden, die die Kommentare handhabt. Der zweite Parameter ermoglicht die Trennung der verschiedenen Kommentar-Typen. Die Standard-Datei fur Kommentare in einem Theme ist die `comments.php`. Wenn nicht vorhanden, wird die von dem Standard-Theme geladen. Wir werden diese Datei erst mal nicht anlegen und uns darum ebenfalls in einem spateren Teil kummern.

Wenn der Beitrag nicht vom Typ `gallery` ist, wird vor dem Footer noch die normale Sidebar eingebunden.

## Der Theme-Code auf GitHub

Schon fast obligatorisch am Ende der Hinweis, dass ihr den Theme-Code [auf GitHub ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe) finden konnt. Der Stand nach diesem Teil ist in Tag „[v0.7 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.7)" festgehalten.

