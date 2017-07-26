# Das eigene WordPress-Theme erstellen – #5: Die content.php

_Captured: 2015-12-04 at 16:38 from [t3n.de](http://t3n.de/news/wordpress-theme-erstellen-content-php-643761/)_

Wie im [letzten Teil der Reihe](http://t3n.de/news/wordpress-theme-erstellen-index-php-637682/) besprochen, nutzen wir die `content.[php](http://t3n.de/tag/php)`, um das Markup von Beitragen auf der Blog-Übersicht auszugeben. Wenn keine andere `content-`-Datei wie die `content-gallery.php` angelegt sind, wird fur jedes Post-Format diese Datei gewahlt. Fur unser Theme sieht die Datei so aus:
    
          1. <article id="post-<?php the_ID();?>" <?php post_class();?>>
      2. <headerclass="entry-header">
      3. <?php bornholm_the_post_header('h1', $post );?>
      4. <divclass="entry-content">
      5. <?php bornholm_the_content();?>
      6. <footerclass="entry-meta">
      7. <?php bornholm_footer_meta()?>

Wir umschließen einen Beitrag mit einem `article`-Element und weisen diesem eine ID zu. Die besteht immer aus dem Prafix `post-`, gefolgt von der ID des Beitrags, die wir mittels der `the_ID()`-Funktion ausgeben. WordPress stellt noch nutzliche Klassen zur Verfugung, die mit `post_class()` ausgegeben werden. Beispielsweise gibt WordPress das Post-Format des Artikels aus, etwa in Form der `format-gallery`-Klasse. Nahere Informationen zu dieser Funktionn findet ihr [auf developer.wordpress.org ](https://developer.wordpress.org/reference/functions/get_post_class/).

## Der Header eines normalen Beitrags

Der Header eines normalen Beitrags soll die verlinkte Überschrift enthalten sowie gegebenenfalls das Featured Image. Da wir diese Funktionalitat haufiger brauchen, ist sie in die Funktion `bornholm_the_post_header()` ausgelagert. Als Parameter muss die Hierarchie der Überschrift und das `$post`-Objekt ubergeben werden. Diese Funktion schreiben wir in die `functions.php`, die ebenfalls in die oberste Ebene des Theme-Ordners gehort:
    
          1. <?php
      2. function bornholm_the_post_header( $heading, $post ){
      3. if( has_post_thumbnail()){
      4. if(! is_single()){?>
      5. 			<a href="<?php esc_url( the_permalink());?>">
      6. <?php }?>
      7. 		echo '<' . $heading . ' class="entry-title">';
      8. 		echo '</' . $heading . '>'; ?>
      9. <figureclass="featured-image">
      10. <?php the_post_thumbnail();?>
      11. <?php if(! is_single()){?>
      12. </a>
      13. <?php }
      14. 		bornholm_post_title( $heading, $post );

Zuerst wird mit der `has_post_thumbnail()`-Funktion gepruft, ob der Beitrag ein Featured Image hat. Da wir den Link auf die Detailseite nur setzen wollen, wenn wir uns nicht auf derselben befinden, und diese Funktion auch fur die Einzelansicht benutzt wird, prufen wir mit `! is_single()`, ob die angezeigte Seite **keine** Einzelseite ist. Befinden wir uns nicht auf einer Einzelseite, geben wir mit Hilfe der `the_permalink()`-Funktion einen Link auf die Einzelseite des Beitrags aus.

Anschließend mochten wir den Titel des Beitrags anzeigen. Wir setzen uns also das Überschriften-Element mit der ubergebenen Hierarchie zusammen und geben darin den Titel mit der `the_title()`-Funktion aus. Fur die Ausgabe des Featured Image in dem `figure`-Element nutzen wir die Funktion `the_post_thumbnail()`. Falls es sich nicht um eine Einzelansicht handelt, schließen wir das Link-Element wieder. Hat der Beitrag kein Featured Image, so rufen wir die `bornholm_post_title()`-Funktion auf und ubergeben die zwei bereits bekannten Parameter. Auch diese Funktion kommt in die `functions.php`:
    
          1. function bornholm_post_title( $heading, $post ){
      2. 	echo '<'. $heading .' class="entry-title">';
      3. if(! is_single()){?>
      4. <a href="<?php esc_url( the_permalink() ); ?>">
      5. <?php }
      6. if(! is_single()){?>
      7. </a>
      8. 	echo '</' . $heading . '>';
      9. }

Das sollte durch die Besprechung der vorherigen Funktion eigentlich selbsterklarend sein. Wir geben wieder das Überschriften-Element aus sowie gegebenenfalls den Link zu der Einzelseite. Darin kommt mit `the_title()` die Überschrift des Beitrags.

## Der Inhalt des Beitrags mit angepasstem Weiterlesen-Link

Kommen wir zuruck zur `content.php`. Um den Inhalt des Beitrags auf der Blog-Übersicht kummert sich dieser Abschnitt:
    
          1. <divclass="entry-content">
      2. <?php bornholm_the_content();?>

Und die `bornholm_the_content()`-Funktion - wieder anzusiedeln in der `functions.php` - sieht so aus:
    
          1. function bornholm_the_content(){
      2. 	$text = _x('Continue reading “%s”','s = post title','bornholm');
      3. 	$more = sprintf( $text, esc_html( get_the_title()));
      4. 	the_content( $more );

In WordPress kann ja bekanntlich ein Weiterlesen-Tag eingefugt werden. Der Standardtext, der dafur ausgegeben wird, ist „Read more…" oder in der deutschen Übersetzung „Weiterlesen …". Wir mochten aber gerne den Titel des Beitrags mit in diesen Weiterlesen-Link integrieren. Im Englischen soll das dann, wenn der Beitrag beispielsweise „WordPress-News" heißt, so aussehen: Continue reading "WordPress-News". Naturlich ubersetzbar. Die Übersetzbarkeit ermoglicht die die erste Zeile der Funktion. Um den Artikel hier nicht zu lang werden zu lassen, wird sich der nachste Beitrag damit beschaftigen, wie ein WordPress-Theme fur die Übersetzung vorbereitet werden kann.

Mit der `sprintf()`-Funktion wird in der nachsten Zeile in den Weiterlesen-Text der Titel eingefugt, der von der `get_the_title()`-Funktion bereitgestellt wird. Zuletzt ubergeben wir den modifizierten Text an die WordPress-eigene `the_content()`-Funktion, die den Inhalt des Beitrags ausgibt.

## Die Meta-Informationen im Footer

Zum Schluss braucht ein Beitrag noch einen Footer. In der `content.[php](http://t3n.de/tag/php)` ist dafur dieser Teil zustandig:
    
          1. <footerclass="entry-meta">
      2. <?php bornholm_footer_meta()?>

Die Funktion `bornholm_footer_meta()` kommt wieder in die `functions.php`:
    
          1. function bornholm_footer_meta(){?>
      2. <a href="<?php esc_url( the_permalink() ); ?>"><?php echo sprintf( _x('%1$s @ %2$s','1 = date, 2 = time','bornholm'), get_the_date(), get_the_time());?></a>
      3.         $show_sep =true;
      4.         bornholm_show_seperator( $show_sep );
      5.         $show_sep =false;
      6.         $category_list = get_the_category_list( _x(', ','term delimiter','bornholm'));
      7. if( $category_list ){
      8. 	        bornholm_category_list( $category_list );
      9. 	        $show_sep =true;
      10.         $tag_list = get_the_tag_list('', _x(', ','term delimiter','bornholm'));
      11. if( $tag_list ){
      12. 	        bornholm_show_seperator( $show_sep );
      13. 	        bornholm_tag_list( $tag_list );
      14. 	        $show_sep =true;
      15.         bornholm_show_seperator( $show_sep );?>
      16. <span class="author">
      17. <?php _e('Author:','bornholm');?><?php the_author();?>
      18. </span>
      19.         $show_sep = true;
      20.         if ( get_bornholm_comment_count() != 0 ) {
      21. 	        bornholm_show_seperator( $show_sep ); ?>
      22. 	        <a href="<?php echo esc_url( get_the_permalink() ) . "#comments-title"; ?>">
      23. 		        <?php echo get_bornholm_comment_count(); ?>
      24. 	        </a>
      25. <?php $show_sep =true;
      26. if( get_bornholm_trackback_count()!=0){
      27. 	        bornholm_show_seperator( $show_sep );?>
      28. <a href="<?php echo esc_url( get_the_permalink() ) . "#trackbacks-title"; ?>">
      29. <?php echo get_bornholm_trackback_count();?>
      30. </a>
      31.         edit_post_link( __( 'Edit', 'bornholm' ), '<span class="edit-link"> ·  ', '</span>' ); ?>

An erster Stelle im Footer steht das Datum und die Uhrzeit der Veroffentlichung, die wie der Titel auch auf die Einzelseite verlinken. Das Datum bekommen wir mit der `get_the_date()`-, die Uhrzeit mit der `get_the_time()`-Funktion. Das Datum und die Zeit wird dabei in dem Format angezeigt, das der Nutzer im Backend eingestellt hat. Die Anordnung kann von einem Übersetzer angepasst werden, doch dazu wie gesagt im nachsten Beitrag mehr.

Da es sein kann, dass kein Tag oder keine Kategorie angegeben werden, mussen wir das immer uberprufen, bevor wir das Trennzeichen zwischen den einzelnen Elementen des Footers ausgeben. Wir setzen also die Variable `$show_sep` auf `true` und rufen die `bornholm_show_seperator()`-Funktion auf. Diese Funktion sieht so aus:
    
          1. /**
      2. function bornholm_show_seperator( $show_sep ){
      3. if( $show_sep ){?>
      4. <span class="sep">·</span>
      5. <?php }

Es wird gepruft, ob `$show_sep` wahr ist und dann der Seperator ausgegeben. Da der Seperator nun ausgegeben wurde, setzen wir in der `bornholm_footer_meta()`-Funktion die `$show_sep`-Variable auf `false`. Als nachstes wollen wir die Liste der Kategorien ausgeben. Die holen wir uns uber die `get_the_category_list()`-Funktion, mit einem Komma als Trennzeichen. Wenn dieser Funktionsaufruf ein Ergebnis zuruckgibt, also Kategorien festgelegt wurden, ubergeben wir das Ergebnis an die `bornholm_category_list()`-Funktion, die so aussieht:
    
          1. function bornholm_category_list( $category_list ){?>
      2. <span class="cat-links">
      3. <?php _e('Posted in ','bornholm');
      4.         echo $category_list;?>
      5. </span>
      6. <?php }

Hier geben wir innerhalb eines `span`-Elements die Liste der Kategorien aus, mit einem ubersetzungsfahigen „Posted in " vorangestellt. Wieder zuruck in der `bornholm_footer_meta()`-Funktion setzen wir `$show_sep` auf `true` und verfahren in ahnlicher Weise mit der Liste der Tags. Die `bornholm_tag_list()`-Funktion sieht so aus:
    
          1. function bornholm_tag_list( $tag_list ){?>
      2. <span class="tag-links">
      3. <?php _e('Tagged ','bornholm');
      4.         echo $tag_list;?>
      5. </span>
      6. <?php }

Als nachstes geben wir in der Funktion fur die Footer-Metadaten den Autoren aus. Dafur zustandig ist die Funktion `the_author()`. Nun mochten wir noch getrennt voneinander die Anzahl der Kommentare und Trackbacks darstellen. WordPress kann standardmaßig nur eine Gesamtzahl der Reaktionen ausgeben. weshalb wir uns hier zwei kleine Funktionen bauen mussen, die sich recht ahnlich sind. Hier sind sie:
    
          1. function get_bornholm_comment_count(){
      2. global $post;
      3. 	$the_post_id = $post->ID;
      4. global $wpdb;
      5. 	$co_number = $wpdb->get_var( $wpdb->prepare("SELECT COUNT(*) FROM $wpdb->comments WHERE comment_type = %s
      6. AND comment_post_ID = %d AND comment_approved = %d",' ', $the_post_id,1));
      7. if( $co_number ==0){
      8. return $co_number;
      9. } elseif ( $co_number ==1){
      10. 		$co_number = $co_number . __(' Comment','bornholm');
      11. return $co_number;
      12. 		$co_number = $co_number . __(' Comments','bornholm');
      13. return $co_number;
      14. function get_bornholm_trackback_count(){
      15. global $post;
      16. 	$the_post_id = $post->ID;
      17. global $wpdb;
      18. 	$tb_number = $wpdb->get_var( $wpdb->prepare("SELECT COUNT(*) FROM $wpdb->comments WHERE comment_type != %s
      19. AND comment_post_ID = %d AND comment_approved = %d",' ', $the_post_id,1));
      20. if( $tb_number ==0){
      21. return $tb_number;
      22. } elseif ( $tb_number ==1){
      23. 		$tb_number = $tb_number . __(' Trackback','bornholm');
      24. return $tb_number;
      25. 		$tb_number = $tb_number . __(' Trackbacks','bornholm');
      26. return $tb_number;

Ich erklare euch den Code anhand der ersten Funktion, die die Anzahl der Kommentare ausgibt. Zuerst sorgen wir dafur, dass wir auf das `$post`-Objekt zugreifen konnen und speichern anschließend die ID des aktuellen Beitrags in der `$the_post_id`-Variable. Fur Datenbankabfragen gibt es in WordPress die `$wpdb`-Klasse. Da wir nur einen Wert aus der Datenbank holen mochten, nutzen wir die `get_var()`-Methode. Um die SQL-Abfrage fur eine sichere Ausfuhrung vorzubereiten, kommt die `prepare()`-Methode zum Einsatz.

Es folgt als erster Parameter die SQL-Abfrage. Mit `$wpdb->` konnen wir dabei dynamisch auf das Tabellenprafix zugreifen. Die anderen Parameter sind die Werte fur die jeweiligen Platzhalter in der `WHERE`-Klausel. Eine detaillierte Erklarung der Klasse und ihrer Methoden findet ihr wieder auf [developer.wordpress.org ](https://developer.wordpress.org/reference/classes/wpdb/). Danach prufen wir, ob keine Kommentare gefunden wurden und geben die Zahl `0` zuruck. Wenn ein Kommentar gefunden wurde, geben wir `1 Comment` zuruck und in allen anderen Fallen die Anzahl gefolgt von `Comments`. Sehr ahnlich ist die Funktion fur die Trackbacks aufgebaut.

Zuruck zu dem Abschnitt in der Footer-Meta-Funktion:
    
          1. if( get_bornholm_comment_count()!=0){
      2.         bornholm_show_seperator( $show_sep );?>
      3. <a href="<?php echo esc_url( get_the_permalink() ) . "#comments-title"; ?>">
      4. <?php echo get_bornholm_comment_count();?>
      5. </a>
      6.         bornholm_show_seperator( $show_sep ); ?>
      7.         <a href="<?php echo esc_url( get_the_permalink() ) . "#trackbacks-title"; ?>">
      8.                 <?php echo get_bornholm_trackback_count(); ?>
      9.         </a>
      10. <?php }

Wir prufen fur beide Falle, ob das Ergebnis ungleich Null ist. Ist das so, geben wir gegebenenfalls den Seperator aus und als Link auf den Titel des Kommentar- beziehungsweise Trackback-Bereichs die Anzahl der Kommentare oder Trackbacks. Zum Schluss geben wir mit der `edit_post_link()`-Funktion fur Nutzer mit den erforderlichen Rechten einen Link auf die Bearbeitungsseite im Backend aus.

Wenn ihr euch nun eure Installation mal anschaut, dann solltet ihr bereits Inhalte auf eurer Seite sehen. Als nachstes mussen wir uns jetzt um die Sidebar und den Footer kummern, die wir in der `index.php` im letzten Teil ja eingebunden aber noch nicht angelegt haben. Hier greift WordPress noch auf einen Fallback zuruck. Aber wie gesagt wird sich der nachste Teil erst mal als kleiner Exkurs um die Vorbereitung fur die Übersetzung kummern.

## Der Code auf GitHub

Wie immer findet ihr den Code im [GitHub-Repository zur Artikelreihe ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/). Den Code-Stand nach diesem Teil findet ihr in Tag „[v0.4 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.4)".

