# Das eigene WordPress-Theme erstellen – #13: Die Archiv-Ansichten

_Captured: 2015-12-04 at 16:47 from [t3n.de](http://t3n.de/news/eigene-wordpress-theme-erstellen-archiv-ansichten-660354/)_

## Allgemeine Archiv-Ansicht des WordPress-Themes anpassen

Um alle Archiv-Ansichten im gleichen Maße anders darzustellen, als die `index.php` vermag, genugt eine `archive.php`. Der Unterschied zur `index.php` ist, dass der Titel des Archivs sowie die gegebenenfalls festgelegte Beschreibung angezeigt wird. Die Datei sieht folgendermaßen aus:
    
          1. <?php get_header();?>
      2. <mainrole="main">
      3. <?php if( have_posts()){?>
      4. <headerclass="archive-header">
      5. <?php esc_html( the_archive_title());?>
      6. <?php the_archive_description();?>
      7. while( have_posts()){
      8.                 the_post();
      9.                 get_template_part('content', get_post_format());
      10.         the_posts_pagination( array('type'=>'list'));?>

Wenn mit `have_posts()` sichergestellt ist, dass Beitrage vorhanden sind, dann wird mit der `the_archive_title()`-Funktion der Titel des Archivs ausgegeben. Darunter folgt, ebenfalls noch in dem `header`-Element, die Ausgabe der Beschreibung mit `the_archive_description()`. Der Rest des Codes ist schon aus fruheren Teilen bekannt.

## Ansicht des Autoren-Archivs

Die Archiv-Ansicht der Autoren soll etwas anders sein. Statt der Beschriftung `Autor: Florian Brinkmann` soll `Alle Beitrage von Florian Brinkmann` als Überschrift angezeigt werden. Deshalb erstellen wir fur diese Archiv-Art die `author.php`, die folgendermaßen aussieht:
    
          1. <?php get_header();?>
      2. <mainrole="main">
      3. <?php if( have_posts()){?>
      4. <headerclass="archive-header">
      5. <?php printf( __('All posts by %s','bornholm'), get_the_author());?>
      6. <?php if( get_the_author_meta('description')){
      7.                     the_author_meta('description');
      8. }?>
      9. <?php
      10. while( have_posts()){
      11.                 the_post();
      12.                 get_template_part('content', get_post_format());
      13.         the_posts_pagination( array('type'=>'list'));?>

Der Anfang ist klar. Neu ist, dass wir als Titel nicht einfach `the_archive_title()` nutzen, sondern uns einen eigenen String zusammenbauen, in den der Name des Autors mit `get_the_author()` eingefugt wird. Anschließend prufen wir, ob der Autor eine Beschreibung angelegt hat und geben sie im Fall der Falle mit `the_author_meta( 'description' )` aus.

Danach wird wie gewohnt die Loop gestartet und die Beitrage ausgegeben.

## Ansicht der Suchergebnisse

Ein weiteres Archiv sind die Suchergebnisse. Auch hier mochten wir ein bisschen von dem Format der `the_archive_title()`-Funktion abweichen und als Titel so etwas ausgeben: `Suchergebnisse fur: Suchbegriff`. Die entsprechende search.php sieht so aus:
    
          1. <?php get_header();?>
      2. <mainrole="main">
      3. <?php if( have_posts()){?>
      4. <headerclass="archive-header">
      5. <?php printf( __('Search Results for: %s','bornholm'), esc_html( get_search_query()));?>
      6. <?php
      7. while( have_posts()){
      8.                 the_post();
      9.                 get_template_part('content', get_post_format());
      10.         the_posts_pagination( array('type'=>'list'));?>

Den Suchterm holen wir uns uber die `get_search_query()`-Funktion und den Rest des Codes kennen wir schon aus den anderen Archiv-Dateien.

## Theme-Code

Den Theme-Code findet ihr im Repository [auf GitHub ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/). Den Stand nach dem 13. Teil unserer Reihe findet ihr in Tag „[v0.11 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.11)".

