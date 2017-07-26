# Das eigene WordPress-Theme erstellen – #14: Einzelansicht einer Seite und das 404-Template

_Captured: 2015-12-04 at 16:48 from [t3n.de](http://t3n.de/news/eigene-wordpress-theme-erstellen-seite-404-template-662322/)_

Von den Standard-Dateien fehlen in unserem Theme noch die `page.php` und `404.php`. Erstere wird fur die Anzeige einer Seite genutzt und sieht folgendermaßen aus.
    
          1. <?php get_header();?>
      2. <mainrole="main">
      3. while( have_posts()){
      4.             the_post();?>
      5.             <article id="post-<?php the_ID();?>" <?php post_class();?>>
      6. <headerclass="entry-header">
      7. <?php bornholm_the_post_header('h1', $post )?>
      8. <divclass="entry-content">
      9. <?php the_content();
      10.                     bornholm_paginated_posts_navigation();?>
      11. <?php }?>

Die Datei gleicht einer Mischung aus `index.php` und `single.php`. Der einzige Unterschied ist, dass wir keine Metadaten ausgeben, da bei einer Seite wie dem Impressum meist nicht relevant ist, welcher Nutzer sie wann erstellt hat.

Mit der `404.php`-Datei kann ein Template festgelegt werden, das bei 404-Fehlern angezeigt wird - also dann, wenn eine Seite nicht gefunden werden konnte.
    
          1. <?php get_header();?>
      2. <mainrole="main">
      3. <articleid="post-0"class="post no-results not-found">
      4. <headerclass="entry-header">
      5. <h1class="entry-title"><?php _e('Nothing Found','bornholm');?></h1>
      6. <divclass="entry-content">
      7. <p><?php _e('Apologies, but no results were found for the requested archive. Perhaps searching will help find a related post.','bornholm');?></p>
      8. <?php get_search_form();?>
      9. </article>

In diesem Fall mochten wir einen kleinen Hinweis ausgeben um dem Nutzer mitzuteilen, was Sache ist. Darunter soll das Suchformular eingebunden werden, damit der Nutzer sein Gluck erneut versuchen kann. Das lasst sich ganz einfach mit der `get_search_form()`-Funktion einbinden. Der Rest des Codes ist auch hier wieder bereits aus alteren Teilen der Serie bekannt.

Wenn ich den Überblick behalten habe, mussten nun alle wichtigen Dateien erstellt worden sein. Jetzt fehlen uns noch die alternative Startseite, die die ersten Galerien aus jeder Kategorie anzeigt sowie die Portfolio-Seite, die alle Arbeiten ausgibt. Daruber hinaus werden wir noch den Customizer benutzen, um ein paar kleine Einstellungen zu realisieren, mit denen der Nutzer das Theme anpassen kann.

## Der Code

Wie immer findet ihr den Code zum Theme [auf GitHub ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/). Den aktuellen Stand nach Teil 14 gibt es beim Tag „[v0.12 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.12)".

