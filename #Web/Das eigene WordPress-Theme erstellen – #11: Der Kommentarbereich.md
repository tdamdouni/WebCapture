# Das eigene WordPress-Theme erstellen – #11: Der Kommentarbereich

_Captured: 2015-12-04 at 16:46 from [t3n.de](http://t3n.de/news/eigene-wordpress-theme-erstellen-2-655718/)_

In den letzten zwei Teilen der Reihe haben wir die `[single.php](http://t3n.de/news/wordpress-theme-einzelansicht-single-php-651782/)` erstellt und [die Sidebar fur Galerien in der Einzelansicht](http://t3n.de/news/eigene-wordpress-theme-erstellen-653702/). Um die Einzelansicht zu vervollstandigen, fehlt uns noch der Kommentarbereich, der in der `single.php` mit folgender Zeile eingebunden wurde:
    
          1. comments_template('',true);

Diese Zeile bindet entweder die `comments.php` des Themes ein oder, wenn nicht vorhanden, das Kommentar-Template des Standard-Themes. In unserem Kommentarbereich sollen zuerst die Kommentare und anschließend die Pingbacks angezeigt werden - gefolgt vom Kommentarformular.

Die `comments.php` unseres Themes sieht folgendermaßen aus:
    
          1. if( post_password_required()){
      2. <divid="comments"class="comments-area">
      3. <?php if( have_comments()){
      4. if(! empty( $comments_by_type['comment'])){?>
      5. <h2id="comments-title">
      6. <?php echo get_bornholm_comment_count();?>
      7. </h2>
      8. <olclass="commentlist">
      9. <?php wp_list_comments( array(
      10. 'callback'=>'bornholm_comment',
      11. 'style'=>'ol',
      12. 'type'=>'comment'
      13. ));?>
      14. <?php }
      15. if(! empty( $comments_by_type['pings'])){?>
      16. <h2id="trackbacks-title">
      17. <?php echo get_bornholm_trackback_count();?>
      18. </h2>
      19. <olclass="commentlist">
      20. <?php wp_list_comments( array('callback'=>'bornholm_comment','type'=>'pings'));?>
      21. </ol>
      22. <?php }
      23. if( get_comment_pages_count()>1&& get_option('page_comments')){?>
      24. <navid="comment-nav-below"class="navigation"role="navigation">
      25. <h2class="screen-reader-text"><?php _e('Comment navigation','bornholm');?></h2>
      26. <divclass="nav-previous">
      27. <?php previous_comments_link( __('← Older Comments','bornholm'));?>
      28. <divclass="nav-next">
      29. <?php next_comments_link( __('Newer Comments →','bornholm'));?>
      30. <?php }
      31. if(! comments_open()&& get_comments_number()){?>
      32. <pclass="nocomments"><?php _e('Comments are closed.','bornholm');?></p>
      33. <?php }
      34.     comment_form( array('comment_notes_after'=>'','label_submit'=> __('Submit Comment','bornholm')));?>

Zuerst prufen wir mit `post_password_required()`, ob ein passwortgeschutzter Beitrag angezeigt wird und das korrekte Passwort nicht eingegeben wurde. Wenn das icht der Fall ist, starten wir die Ausgabe des Kommentarbereichs. Innerhalb des `div` wird gepruft, ob zu dem Beitrag Kommentare vorhanden sind. Von der `have_comments()`-Funktion werden sowohl Kommentare als auch Pingbacks berucksichtigt. Als nachstes prufen wir, ob Kommentare vorhanden sind - hier aber wirklich nur auf Kommentare, nicht auf Pingbacks:
    
          1. if(! empty( $comments_by_type['comment'])){

Dieses Array `$comments_by_tpye` konnen wir deshalb nutzen, weil wir beim Aufruf der `comments_template()`-Funktion als zweiten Parameter `true` ubergeben haben. Durch diese Angabe wird der folgende Code innerhalb der `comments_template()`-Funktion ausgefuhrt und stellt uns die Kommentare getrennt nach Typ zur Verfugung:
    
          1. if( $separate_comments ){
      2.     $wp_query->comments_by_type = separate_comments($comments);
      3.     $comments_by_type =&$wp_query->comments_by_type;
      4. }

Zuruck in die `comments.php`. Wenn wir Kommentare gefunden haben, geben wir mit der [schon bekannten](http://t3n.de/news/wordpress-theme-erstellen-content-php-643761/) `get_bornholm_comment_count()`-Funktion die Anzahl aus. Anschließend folgt die Liste der Kommentare, die wir uber `wp_list_comments()` ausgeben konnen. Wichtig ist hier vor allem die Angabe `comment` fur den `type`. Um die Ausgabe der Kommentare verandern zu konnen, geben wir fur `callback` als Wert `bornholm_comment` an, was der `bornholm_comment()`-Funktion entspricht, die in die `functions.php` gehort:
    
          1. function bornholm_comment( $comment, $args, $depth ){
      2.     $GLOBALS['comment']= $comment;
      3. switch( $comment->comment_type ):
      4. case'pingback':
      5. case'trackback':?>
      6. <li <?php comment_class();?> id="comment-<?php comment_ID(); ?>">
      7. <?php _e('Trackback:','bornholm');?>
      8. <?php esc_url( comment_author_link());?>
      9. <?php esc_url( edit_comment_link( __('(Edit)','bornholm'),
      10. '<span class="edit-link">',
      11. '</span>'));?>
      12. </p>
      13.         <li <?php comment_class(); ?> id="li-comment-<?php comment_ID(); ?>">
      14.                     <?php echo get_avatar( $comment, 100 ); ?>
      15.                         <?php esc_url( comment_author_link() ); ?>
      16.                     </cite>
      17. <?php printf(
      18. '<a href="%1$s"><time datetime="%2$s">%3$s</time></a>',
      19.                         esc_url( get_comment_link( $comment->comment_ID )),
      20.                         get_comment_time('c'),
      21.                         sprintf(
      22.                             _x('%1$s @ %2$s','1=date 2=time','bornholm'),
      23.                             get_comment_date(),
      24.                             get_comment_time()
      25. );?>
      26. </header>
      27.                 <?php if ( '0' == $comment->comment_approved ) { ?>
      28.                     <p class="comment-awaiting-moderation">
      29.                         <?php _e( 'Your comment is awaiting moderation.', 'bornholm' ); ?>
      30.                     </p>
      31. <?php }?>
      32. <section class="comment-content comment">
      33. <?php comment_text();?>
      34. <?php esc_url(
      35.                         edit_comment_link( __('Edit','bornholm'),
      36. '<p class="edit-link">','</p>')
      37. );?>
      38. </section>
      39.                 <div class="reply">
      40.                     <?php esc_url( comment_reply_link(
      41.                             'reply_text' => __( 'Reply', 'bornholm' ),
      42.                             'depth'      => $depth,
      43.                             'max_depth'  => $args['max_depth']
      44.                 </div>
      45. </article>
      46.     endswitch; //end comment_type check

Diese Funktion kummert sich sowohl um die Anzeige der Kommentare als auch um die Pingbacks. Diese Fallunterscheidung tatigen wir in einer `switch`-Anweisung, in der wir den Kommentar-Typ uberprufen. Wenn es sich um einen Ping- oder Trackback handelt, geben wir ein Listenelement aus und darin den Trackback. Mit `comment_author_link()` wird dabei der Titel der Website als Link ausgegeben. Über die `edit_comment_link()`-Funktion fugen wir hinter den Trackback einen Link zum Bearbeiten ein, der nur fur berechtigte Nutzer sichtbar ist. Das schließende `li`-Tag setzt WordPress selbst!

Wenn es sich nicht um einen Ping- oder Trackback handelt, geben wir einen Kommentar aus. Auch hier beginnen wir wieder mit einem offnenden `li`-Tag und reichern das Element durch `comment_class()` mit hilfreichen Klassen an - ahnlich wie bei `body_class()`. Innerhalb des `header`-Elements soll der Gravatar des Nutzers mit einer Breite von 100 Pixeln angezeigt werden. Dafur sorgt die `get_avatar()`-Funktion, die als ersten Parameter das Kommentar-Objekt ubergeben bekommt und als zweiten die Große des Bildes. Den Namen des Kommentierenden geben wir wieder mit der `comment_author_link()`-Funktion aus.

Es folgt das Datum und die Zeit des Kommentars:
    
          1. <?php printf(
      2. '<a href="%1$s"><time datetime="%2$s">%3$s</time></a>',
      3.     esc_url( get_comment_link( $comment->comment_ID )),
      4.     get_comment_time('c'),
      5.         _x('%1$s @ %2$s','1=date 2=time','bornholm'),
      6.         get_comment_time()

Als ersten Parameter ubergeben wir an die `printf()`-Funktion das HTML-Markup mit den entsprechenden Platzhaltern. Der zweite Parameter ist der Permalink des Kommentars, der mit der `get_comment_link()`-Funktion ermittelt wird. Als nachstes ermitteln wir fur das `datetime`-Attribut den Zeitpunkt, an dem der Kommentar geschrieben wurde. `get_comment_time()` gibt mit dem Parameter `c` einen String dieses Formats zuruck: `2015-06-11T12:48:09+00:00`.

Zuletzt bauen wir den Zeit-String zusammen, der angezeigt werden soll. Wir holen uns das Datum und die Zeit uber die entsprechenden Funktionen und ubergeben diesmal keinen Parameter. So wird das Format gewahlt, das der Nutzer im Backend eingestellt hat. Damit ware der `header` eines Kommentars fertig. Als nachstes geben wir einen Hinweis fur den Autor eines Kommentars aus, wenn der Kommentar noch freigeschaltet werden muss:
    
          1. <?php if('0'== $comment->comment_approved ){?>
      2. <pclass="comment-awaiting-moderation">
      3. <?php _e('Your comment is awaiting moderation.','bornholm');?>

Wir prufen zuerst, ob der Wert `comment_approved` des Kommentar-Objekts `0` ist. In dem Fall geben wir eine kurze Nachricht aus, dass der Kommentar noch nicht freigeschaltet ist. Danach kommt der eigentliche Kommentar an die Reihe.
    
          1. <sectionclass="comment-content comment">
      2. <?php comment_text();?>
      3. <?php esc_url(
      4.         edit_comment_link( __('Edit','bornholm'),
      5. '<p class="edit-link">','</p>')
      6. );?>
      7. <divclass="reply">
      8. <?php esc_url( comment_reply_link(
      9. 'reply_text'=> __('Reply','bornholm'),
      10. 'depth'=> $depth,
      11. 'max_depth'=> $args['max_depth']
      12. ));?>

Innerhalb des `section`-Elements wird mit der `comment_text()`-Funktion der Inhalt des Kommentars ausgegeben. Daruber hinaus wird wieder ein Link zur Bearbeitungsseite integriert. In einem eigenen `div` geben wir im Anschluss einen Link zum direkten Beantworten des Kommentars aus. Dafur ubergeben wir an `comment_reply_link()` die Parameter, die wir verandern wollen. Als Text fur den Link geben wir `Reply` an und die Verschachtelungstiefe soll so ubernommen werden, wie der Nutzer es im Backend eingestellt hat.

Nachdem wir uns durch diese Funktion gewuhlt haben, kommen wir zuruck zur `comments.php`. Die Ausgabe der Pingbacks lauft dabei nach demselben Schema ab, wie die Ausgabe der Kommentare. Wir geben wieder als Callback-Funktion `bornholm_comment` an. Im Anschluss mussen wir eventuell eine Kommentar-Navigation ausgeben:
    
          1. if( get_comment_pages_count()>1&& get_option('page_comments')){?>
      2. <nav id="comment-nav-below"class="navigation" role="navigation">
      3. <h2 class="screen-reader-text"><?php _e('Comment navigation','bornholm');?></h2>
      4. <div class="nav-previous">
      5. <?php previous_comments_link( __('← Older Comments','bornholm'));?>
      6.             <?php next_comments_link( __( 'Newer Comments →', 'bornholm' ) ); ?>
      7.         </div>
      8. </nav>
      9. <?php }

Wir prufen zuerst, ob mehr als eine Kommentarseite vorhanden ist und ob Kommentare uberhaupt nach einer bestimmten Anzahl auf eine neue Seite umgebrochen werden sollen. Ist das der Fall, geben wir innerhalb eines `nav`-Elements zuerst eine Überschrift fur Screen-Reader-Nutzer aus. Im Anschluss werden mit `previous_comments_link()` und `next_comments_link()` die entsprechenden Links ausgegeben. Ab WordPress 4.4 wird es dafur die `the_comments_navigation()`-Funktion geben, die diesen Schritt vereinfacht.
    
          1. if(! comments_open()&& get_comments_number()){?>
      2. <p class="nocomments"><?php _e('Comments are closed.','bornholm');?></p>
      3. <?php }
      4.     comment_form( array('comment_notes_after'=>'','label_submit'=> __('Submit Comment','bornholm')));?>
      5. </div>

Zum Abschluss geben wir einen Hinweis auf die deaktivierte Kommentarfunktion aus, wenn Kommentare deaktiviert aber davor schon Kommentare geschrieben wurden. Zuletzt folgt das Kommentarformluar, das uber die `comment_form()`-Funktion ausgegeben wird. Ab WordPress 4.4 wird hier die gewohnte Reihenfolge vertauscht und das Feld fur den Kommentartext ganz oben stehen.

## Der Code auf GitHub

Wie immer gibt es den Code [im Repository auf GitHub ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/). Den aktuellen Stand nach diesem elften Teil findet ihr unter dem Tag „[v0.9 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.9)".

