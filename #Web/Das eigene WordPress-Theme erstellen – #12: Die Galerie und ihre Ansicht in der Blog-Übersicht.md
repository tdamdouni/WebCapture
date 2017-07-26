# Das eigene WordPress-Theme erstellen – #12: Die Galerie und ihre Ansicht in der Blog-Übersicht

_Captured: 2015-12-04 at 16:46 from [t3n.de](http://t3n.de/news/eigene-wordpress-theme-erstellen-content-gallery-655685/)_

Nachdem wir die Einzelansicht eines Beitrags in den letzten Teilen der Reihe fertiggestellt haben, kommen wir noch mal auf die Blog-Übersicht zuruck. Bei einer Galerie soll da ein großes Bild gezeigt werden, das nach denselben Kriterien ermittelt wird wie das Bild [in der Einzelansicht einer Galerie](http://t3n.de/news/wordpress-theme-einzelansicht-single-php-651782/). Darunter sollen weitere Bilder aus der Galerie in kleinerem Format angezeigt werden - spater wird der Nutzer die Anzahl im Customizer einstellen konnen. Zudem wird die Anzahl der Bilder dargestellt, die den Besucher in der Einzelansicht erwarten. Wie das aussehen soll, konnt ihr in dem Screenshot sehen.

![Die Ansicht einer Galerie in der Blog-Übersicht. \(Screenshot: eigene Installation; Fotos: Dennis Brinkmann\)](http://t3n.de/news/wp-content/uploads/2015/11/wordpress-theme-erstellen-content-gallery-php-595x482.jpg)

> _Die Ansicht einer Galerie in der Blog-Übersicht. (Screenshot: eigene Installation; Fotos: Dennis Brinkmann)_

Die Anzeige der Galerie-Beitrage in der Übersicht ubernimmt die `content-gallery.php`. Im Bornholm-Theme sieht die folgendermaßen aus:
    
          1. <article id="post-<?php the_ID();?>" <?php post_class();?>>
      2. <headerclass="entry-header clearfix">
      3.         $images = bornholm_get_gallery_images( $post->ID );
      4.         bornholm_gallery_header('h1', $images,'bornholm_large_gallery_image_for_blog_view', $post );
      5.     $number_of_small_images =2;
      6. if( $number_of_small_images >0){
      7.         bornholm_small_gallery_thumbnails('thumbnail', $images, $number_of_small_images );
      8. <divclass="entry-content">
      9. <?php bornholm_gallery_image_number( $images );?>
      10. <footerclass="entry-meta">
      11. <?php bornholm_footer_meta()?>

Wie aus der normalen `content.php` [gewohnt](http://t3n.de/news/wordpress-theme-erstellen-content-php-643761/), geben wir dem `article`-Element Klassen und eine ID mit. Innerhalb des Headers holen wir uns mit der [bereits bekannten](http://t3n.de/news/wordpress-theme-einzelansicht-single-php-651782/) `bornholm_get_gallery_images()`-Funktion die Bilder der Galerie und geben mit der [ebenfalls bereits behandelten Funktion](http://t3n.de/news/wordpress-theme-einzelansicht-single-php-651782/) `bornholm_gallery_header()` das erste Bild oder - falls vom Nutzer festgelegt - das Beitragsbild aus.

Bei der Bildgroße handelt es sich um eine weitere Große, die das Theme anlegt. In der `functions.php` haben wir bereits diese Zeile stehen:
    
          1. add_image_size('bornholm_large_gallery_image_for_single_view',1592,9999,false);

Darunter fugen wir die neue Große mit dieser Zeile ein:
    
          1. add_image_size('bornholm_large_gallery_image_for_blog_view',951,9999,false);

Wie bereits angesprochen, mochten wir spater dem Nutzer die Moglichkeit geben, die Anzahl der kleinen Bilder zu verandern. Wenn der Nutzer eine Null eintragt, werden keine angezeigt. Diese Customizer-Funktion werden wir erst in einem kommenden Teil implementieren, weshalb die Zahl an dieser Stelle auf `2` festgelegt wird.

An die `bornholm_small_gallery_thumbnails()`-Funktion ubergeben wir die Große des Bildes, das Array mit den Galerie-Bildern sowie die Anzahl der Bilder, die angezeigt werden soll. Die Funktion kommt in die `functions.php` und sieht so aus:
    
          1. function bornholm_small_gallery_thumbnails( $size, $images, $number_of_small_images ){
      2. global $post;
      3. if( $images ){
      4.         $counter =0;
      5. if( has_post_thumbnail()){
      6. 	        bornholm_thumbnails_from_gallery_with_post_thumbnail( $post, $images, $counter, $size, $number_of_small_images );
      7. 	        bornholm_thumbnails_from_gallery_without_post_thumbnail( $images, $counter, $size, $number_of_small_images );

Zuerst muss das `$post`-Objekt zuganglich gemacht werden. Im Anschluss prufen wir, ob die `$images`-Variable uberhaupt Bilder enthalt und setzen einen Counter auf Null. Wenn der Beitrag ein Beitragbild hat, rufen wir `bornholm_thumbnails_from_gallery_with_post_thumbnail()` auf und ubergeben der Funktion das Post-Objekt, das Array mit Bildern, den Counter-Wert, die gewunschte Große der Bilder sowie die Anzahl, die angezeigt werden soll.

Diese Unterscheidung mussen wir machen, damit nicht das Beitragsbild als großes Bild angezeigt wird und als kleines darunter noch mal - das wurde beispielsweise passieren, wenn das zweite Bild der Galerie als Beitragsbild festgelegt wird.

Die Funktion kommt wieder in die `functions.php`:
    
          1.  * Displays the two first images from the gallery when a post thumbnail is set without displaying the
      2. function bornholm_thumbnails_from_gallery_with_post_thumbnail( $post, $small_images, $counter, $size, $number_of_small_images ){
      3.     $post_thumbnail = wp_get_attachment_image_src( get_post_thumbnail_id( $post->ID ));
      4.     $image_list     ='<ul class="gallery-thumbs clearfix">';
      5. foreach( $small_images as $single_image ){
      6.         $single_image_url = wp_get_attachment_image_src( $single_image->ID );
      7. if( $counter >= $number_of_small_images ){
      8. if( $post_thumbnail[0]== $single_image_url[0]){
      9. continue;
      10.         $image_list .='<li>'. wp_get_attachment_image( $single_image->ID, $size ).'</li>';
      11.     $image_list .='</ul>';

Zuerst holen wir uns mit `wp_get_attachment_image_src()` den Link zu dem Beitragsbild und speichern ihn in der Variable `$post_thumbnail`. Danach bereiten wir das Markup fur die Liste der Bilder vor, das wir innerhalb der Schleife weiter fullen und am Ende verfollstandigen. Die `foreach`-Schleife wird fur jedes Bild durchlaufen, das in dem Bild-Array an die Funktion ubergeben wurde. In der Schleife ermitteln wir die URL des aktuellen Bildes und prufen im Anschluss, ob der Counter schon großer oder gleich der Bildanzahl ist, die angezeigt werden soll. Ist das der Fall, wird die Schleife beendet.

Als nachste mussen wir prufen, ob die URL des aktuellen Bildes der URL des Beitragsbildes entspricht, das ja bereits als großes Bild angezeigt wird. Wenn das so ist, mochten wir den aktuellen Durchlauf der Schleife beenden und direkt zum nachsten springen. Wenn weder die Anzahl an Bildern erreicht ist noch das Beitragsbild dem aktuellen Bild entspricht, wird an das Markup der Bildliste ein Listenelement angehangt, das das `img`-Element enthalt. Dafur wird als erster Parameter an `wp_get_attachment_image()` die ID des Bildes und als zweiter die gewunschte Große ubergeben. Zuletzt wird der Counter um einen Wert erhoht.

Wenn die `foreach`-Schleife abgearbeitet ist, wird das schließende `ul`-Tag an die Bildliste gehangt und diese ausgegeben.

Zuruck in der `bornholm_small_gallery_thumbnails()`-Funktion sehen wir, dass im Fall keines Beitragsbildes die Funktion `bornholm_thumbnails_from_gallery_without_post_thumbnail()` aufgerufen wird. Die Parameter sind dieselben, nur das Post-Objekt wird nicht benotigt.

Auch diese Funktion schreiben wir wieder in die `functions.php`:
    
          1. function bornholm_thumbnails_from_gallery_without_post_thumbnail( $small_images, $counter, $size, $number_of_small_images ){
      2.     $image_list     ='<ul class="gallery-thumbs clearfix">';
      3. foreach( $small_images as $single_image ){
      4. if( $counter ==0){
      5. continue;
      6. if( $counter > $number_of_small_images ){
      7.         $image_list .='<li>'. wp_get_attachment_image( $single_image->ID, $size ).'</li>';
      8.     $image_list .='</ul>';

Die Funktion ist der mit dem Beitragsbild recht ahnlich. Hier mussen wir nicht auf die URL des Beitragsbildes prufen, sondern ob gerade das erste Bild durchlaufen wird - der Counter also den Wert Null hat. Ist das der Fall, wird die Counter-Variable erhoht und der aktuelle Durchlauf beendet. Vollstandig beendet wird die Schleife im Fall, dass der Wert von `$counter` großer ist als die Anzahl der Bilder, die angezeigt werden sollen - andernfalls wird wieder die Liste zusammengesetzt.

Zuruck in die `content.php`. Der noch ausstehende Teil sieht so aus:
    
          1. <divclass="entry-content">
      2. <?php bornholm_gallery_image_number( $images );?>
      3. <footerclass="entry-meta">
      4. <?php bornholm_footer_meta()?>

Die Funktion fur die Meta-Daten im Footer hatten wir bereits im [funften Teil der Reihe](http://t3n.de/news/wordpress-theme-erstellen-content-php-643761/), deshalb fehlt nur noch die Zahlung der Galerie-Bilder. Dafur rufen wir die Funktion `bornholm_gallery_image_number()` auf und ubergeben das Array mit den Bildern. Die Funktion findet wieder ihren Platz in der `functions.php`:
    
          1. function bornholm_gallery_image_number( $images ){
      2. if( $images ){
      3.         $total_images = count( $images );?>
      4. <em><?php
      5.                 printf( _n('This gallery contains <a %1$s>%2$s photo</a>.',
      6. 'This gallery contains <a %1$s>%2$s photos</a>.',
      7.                     $total_images,'bornholm'),
      8. 'href="'. esc_url( get_permalink())
      9. .'"',
      10.                     number_format_i18n( $total_images ));
      11. </em>
      12.         </p>
      13. <?php }

Zuerst prufen wir erneut, ob uberhaupt Bilder vorhanden sind. Wenn das der Fall ist, zahlen wir mittels der `count()`-Funktion einfach die Eintrage im Array. Da wir bei einer Galerie, die nur aus einem Bild besteht, eine etwas andere Beschriftung ausgeben mochten als bei einer Galerie mit mehreren Bildern, nutzen wir als Übersetzungsfunktion innerhalb von `printf()` die Funktion `_n()`. Dieser Funktion wird als erster Parameter die Singular-Form ubergeben, gefolgt von der Plural-Form und eine Zahl, anhand derer WordPress entweder den Singular oder Plural ausgibt. Zum Schluss kommt wie gewohnt die Text-Domain zum Einsatz.

Den ersten Platzhalter in den beiden Strings ersetzen wir mit dem Link zu der Einzelansicht, den zweiten mit der Anzahl der Bilder. Damit die Zahl abhangig von der Sprache der WordPress-Installation korrekt formatiert wird, ubergeben wir die Bild-Anzahl an die `number_format_i18n()`-Funktion. Damit wird beispielsweise das Tausendertrennzeichen eingefugt.

## Theme-Code auf GitHub

Damit waren wir bereits am Ende dieses Teils angelangt. Den Code findet ihr wie immer [im GitHub-Repo ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/) und Tag „[v0.10 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.10)" ist der aktuelle Stand nach diesem Beitrag.

