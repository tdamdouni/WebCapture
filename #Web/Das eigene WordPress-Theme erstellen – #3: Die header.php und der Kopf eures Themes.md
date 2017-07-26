# Das eigene WordPress-Theme erstellen – #3: Die header.php und der Kopf eures Themes

_Captured: 2015-12-04 at 16:35 from [t3n.de](http://t3n.de/news/t3n-guide-wordpress-theme-teil-3-alternative-startseite-galerie-teaser-558172/)_

In der `header.php` sind die Angaben zu finden, die auf jeder Seite der Website benotigt werden. Das ist naturlich zuallererst der Doctype, gefolgt vom offnenden `html`-Tag sowie dem `head`-Element mit Meta-Tags, Skripten und Stylesheets. Auch der sichtbare Header findet hier seinen Platz.

Wir legen also erst mal in unserem Theme-Ordner auf oberster Ebene die Datei `header.php` an. Ich zeige euch gleich einmal die komplette `header.php`. Anschließend werde ich sie in kleinere Teile zerlegen und erklaren.
    
          1. <html <?php language_attributes();?> class="no-js">
      2.     <meta charset="<?php bloginfo('charset');?>">
      3. <metaname="viewport"content="width=device-width, initial-scale=1"/>
      4. <?php if( is_singular()&& pings_open()){?>
      5.         <link rel="pingback" href="<?php bloginfo('pingback_url');?>">
      6.     wp_head();?>
      7. <body <?php body_class();?>>
      8. <headerid="header"class="clearfix"role="banner">
      9. <h1class="site-title">
      10.             <a href="<?php echo esc_url( home_url('/'));?>">
      11. <?php if( get_header_image()){?>
      12.                     <img src="<?php echo esc_url( get_header_image());?>" alt="<?php echo esc_html( get_bloginfo('title'));?>" />
      13. <?php }else{
      14.                     bloginfo('title');
      15. }?>
      16. </a>
      17. <?php if( get_bloginfo('description')!=''){?>
      18. <h2class="blog-description">
      19. <?php bloginfo('description');?>
      20. <?php }?>
      21. <buttonclass="menu-button show-menu">≡</button>
      22. <navrole="navigation">
      23. <buttonclass="hide-menu menu-button">×</button>
      24. <?php wp_nav_menu( array(
      25. 'theme_location'=>'header-menu',
      26. 'container'=>'',
      27. 'fallback_cb'=>false
      28. ));?>
      29. <buttonclass="hide-menu menu-button">×</button>
      30. <divid="wrapper"class="clearfix">

## Unverzichtbare Bestandteile fur ein valides und funktionierendes WordPress-Theme

Widmen wir uns zuerst dem Teil, der in keinem WordPress-Theme und auch keiner anderen Seite fehlen sollte: Doctype, `html`\- und `head`-Element.
    
          1. <html <?php language_attributes();?> class="no-js">
      2.     <meta charset="<?php bloginfo('charset');?>">
      3. <metaname="viewport"content="width=device-width, initial-scale=1"/>
      4. <?php if( is_singular()&& pings_open()){?>
      5.         <link rel="pingback" href="<?php bloginfo('pingback_url');?>">
      6. <?php }
      7.     wp_head();?>
      8. <body <?php body_class();?>>

### Doctype und Meta-Tags

Wir beginnen mit dem Einfugen des HTML5-Doctype. Dem `html`-Tag geben wir mit der `language_attributes()`-Funktion das gefullte `lang`-Attribut mit. Wenn ihr eure WordPress-Seite auf Deutsch eingestellt habt, sieht die Ausgabe so aus: `lang="de-DE"`. Die `no-js`-Klasse brauchen wir fur ein paar CSS-Fallback-Angaben, wenn JavaScript nicht aktiviert sein sollte.

Innerhalb des `head`-Elements wird die Zeichenkodierung durch die `bloginfo()`-Funktion ausgegeben, der als Parameter `charset` ubergeben wird. Fur responsive Webdesign unerlasslich ist naturlich der `viewport`-Meta-Tag.

### Pingbacks ermoglichen und `wp_head()` nicht vergessen

Um Pingbacks moglich zu machen, muss ein `link`-Tag integriert werden. Das mochten wir aber nur laden, wenn eine Einzelseite aufgerufen ist und Pingbacks im Backend auch aktiviert sind. Wir prufen also mit `is_singular() && pings_open()`, ob diese beiden Bedingungen gegeben sind. Wenn das der Fall ist, geben wir das `link`-Tag aus. Das `href`-Attribut nutzt wieder die `bloginfo()`-Funktion, diesmal mit dem Parameter `pingback_url`.

**Sehr wichtig** ist die Nutzung der `wp_head()`-Funktion. Daruber bindet WordPress beispielsweise das `title`-Element, jQuery und den `canonical`-Tag ein. Außerdem wird er fur Styles und Skripte von Plugins genutzt. Die Funktion `body_class()` im offnenden `body`-Tag fugt abhangig von der dargestellten Seite unterschiedliche Klassen ein. Wenn wir uns auf der Startseite befinden, wird beispielsweise unter anderem die `home`-Klasse eingefugt.

## Der sichtbare Header des Themes

### Header-Bild oder Titel als Link auf die Startseite
    
          1. <headerid="header"class="clearfix"role="banner">
      2. <h1class="site-title">
      3.             <a href="<?php echo esc_url( home_url('/'));?>">
      4. <?php if( get_header_image()){?>
      5.                     <img src="<?php echo esc_url( get_header_image());?>" alt="<?php echo esc_html( get_bloginfo('title'));?>" />
      6. <?php }else{
      7.                     bloginfo('title');
      8. }?>

Wir umschließen den Inhalt des Headers mit einem `header`-Element. Innerhalb eines `div`-Elements und einer Überschrift erster Ordnung mochten wir den Titel des Blogs darstellen und auf die Startseite verlinken. Wenn allerdings ein Header-Bild im WordPress-Backend festgelegt ist, soll das statt des Titels angezeigt werden. Fur die Verlinkung auf die Startseite nutzen wir die `home_url()`-Funktion und escapen diese zur Sicherheit mittels `esc_url()`.

Hier ein kleiner Hinweis zu den Escape-Funktionen mit `esc_`-Prafix: Wahrend des Theme-Reviews bei WordPress.org wurde ich darauf hingewiesen, dass ich diese Funktionen an einigen Stellen vergessen hatte. Euch wird diese Funktionen also noch an einigen Stellen begegnen. Nun prufen wir, ob die `get_header_image()`-Funktion etwas zuruckgibt. Wenn dem so ist, wurde ein Header-Bild festgelegt.
    
          1. <img src="<?php echo esc_url( get_header_image());?>" alt="<?php echo esc_html( get_bloginfo('title'));?>" />

Die URL des Header-Bildes liefert uns einfach die `get_header_image()`-Funktion. Wir nutzen hierfur wieder die Escape-Funktion `esc_url()`. Als Alternativtext geben wir den Titel des Blogs aus, den wir uns wieder mit der `get_bloginfo()`-Funktion ausgeben lassen konnen. Hier nutzen wir die Escape-Funktion `esc_html()`. Wenn kein Header-Bild festgelegt wurde, wird einfach der Titel der Website ausgegeben.

### Die Beschreibung der Website
    
          1. <?php if( get_bloginfo('description')!=''){?>
      2. <h2class="blog-description">
      3. <?php bloginfo('description');?>
      4. <?php }?>

Wenn eine Beschreibung fur die Website festgelegt wurde, wollen wir diese in Form einer `h2`-Überschrift ausgeben. Wir prufen mit `get_bloginfo( 'description' ) != ''`, ob die Beschreibung nicht leer ist. Wenn etwas eingetragen wurde, dann geben wir die Überschrift aus und als Inhalt - wiederum mit der `bloginfo()`-Funktion - die Beschreibung.

### Wichtig fur einen guten Benutzerfluss: Das Menu
    
          1. <buttonclass="menu-button show-menu">≡</button>
      2. <navrole="navigation">
      3. <buttonclass="hide-menu menu-button">×</button>
      4. <?php wp_nav_menu( array(
      5. 'theme_location'=>'header-menu',
      6. 'container'=>'',
      7. 'fallback_cb'=>'__return_false'
      8. ));?>
      9. <buttonclass="hide-menu menu-button">×</button>
      10. <divid="wrapper"class="clearfix">

Um ein Menu auszugeben, braucht es nicht sehr viel. Fur kleine Viewports erstellen wir zuerst einen Button mit dem altbekannten `≡`-Symbol. Innerhalb des `nav`-Elements kommt zuerst und am Schluss jeweils ein weiterer Button, der das aufgeklappte Menu auf kleineren Viewports wieder schließt.

Dazwischen wird es interessant: Um ein WordPress-Menu anzuzeigen, gibt es die `wp_nav_menu()`-Funktion, der [alle moglichen Parameter ](https://developer.wordpress.org/reference/functions/wp_nav_menu/) ubergeben werden konnen. Mit dem Parameter `theme_location` bestimmen wir, welche Menuposition wir anzeigen wollen. Den Namen dieser Menuposition, die ihr im Backend bei der Menuverwaltung auswahlen konnt, legen wir in einem spateren Teil in der `functions.php` fest.

Normalerweise wird die Menuliste von einem `div`-Element umschlossen. Das brauchen wir nicht, weshalb wir einen leeren Wert fur den `container`-Parameter ubergeben. Einen Fallback dafur, dass dieser Position kein Menu zugeordnet ist, mochten wir nicht. Standardmaßig wurden die `wp_page_menu()`-Funktion genutzt werden, die eine Linkliste der WordPress-Seiten ausgibt. Wir schließen danach noch unser `header`-Element und offnen einen Wrapper.

## Der Code zu Teil 3 auf GitHub

Den Code zu dem [Theme](http://t3n.de/tag/templates) gibt es [auf GitHub ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe). Ihr findet den aktuellen Stand des Themes nach diesem Teil im Tag „[v0.2 ](https://github.com/FlorianBrinkmann/Bornholm-Artikelreihe/tree/v0.2)".

