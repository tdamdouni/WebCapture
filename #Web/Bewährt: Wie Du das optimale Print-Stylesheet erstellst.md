# Bewährt: Wie Du das optimale Print-Stylesheet erstellst

_Captured: 2016-11-07 at 10:06 from [www.drweb.de](https://www.drweb.de/magazin/das-optimale-print-stylesheet-76873/)_

Auch heute gibt es noch viele Menschen, die sich das Internet ausdrucken mochten. Das kann verschiedene Grunde haben. Vielleicht will ein Team den Inhalt deines Beitrags im Meeting besprechen. Oder jemand mochte deinen Artikel dort lesen, wo er gewiss keinen Internet-Empfang hat. Um diese Menschen ansprechen zu konnen, benotigt jede Website immer noch eine CSS-Datei fur den Druck, das sogenannte Print-Stylesheet.

![Bewährt: Wie Du das optimale Print-Stylesheet erstellst](https://www.drweb.de/magazin/wp-content/uploads/2016/06/optimales-print-stylesheet-teaser.jpg)

Viele Menschen drucken sich auch heute noch etliche Artikel aus, um sie offline lesen zu konnen. Diesem Umstand solltest du Rechnung tragen, wenn du keine Leser verlieren willst. Allerdings stellen sich zwei Hurden in den Weg des Druckens.

Erstens: Kaum ein WordPress-Theme hat heute noch ein Print-Stylesheet. Die Entwickler der Themes machen sich diese Muhe nicht, obwohl ein solches Druck-CSS einfach fur mich zum guten Ton des Entwickelns zahlt. Zweitens: Da kein Druck-Stylesheet vorhanden ist, hat der Endverbraucher, der das Theme einsetzt, auch keinen Drucken-Button zur Verfugung.

Daher zeige ich dir in diesem Beitrag, wie du ein Print-CSS erstellst, wo es in das Theme integriert werden sollte und wie man sich einen Druck-Button erstellen kann.

## Das optimale Print-Stylesheet erstellen

Erstelle zuerst eine leere CSS-Datei mit einem reinen [Text- oder HTML-Editor](https://www.drweb.de/magazin/die-8-besten-kostenlosen-html-editoren-fuer-webentwickler-windows-edition-53187/). Benenne sie **print.css**. Kopiere im Anschluss folgendes hinein:

Alle CSS-Einstellungen, die du nun tatigen mochtest, kommen zwischen das offnende und das schließende Bracket.

### 1 - Seitenrander und Schriftgroßen festlegen

Zuerst legen wir die Abstande der Seitenrander fest, um ein optimales Ergebnis zu erhalten.

/* Inhaltsbreite setzen, Floats und Margins aufheben */

/* Achtung: Die Klassen und IDs variieren von Theme zu Theme. Hier also eigene Klassen setzen */

#content,#page {

width: 100%; 

margin: 0; 

float: none;

}

/** Seitenrander einstellen */ 

@page { margin: 2cm }

/* Oder aber: */

@page :left {

margin: 1cm;

}

@page :right {

margin: 1cm;

}

/* Auch die erste Seite eines Drucks kann manipuliert werden */

@page :first {

margin: 1cm 2cm;

}

Ich empfehle, die obere Einstellung zu verwenden und die Seitenrander auf 2 cm einzustellen. Nachdem das Geschehen ist, konnen die Einstellungen der Schriftgroßen vorgenommen werden. Hierbei ist zu beachten, dass der Drucker andere Einheiten fur die Schriftgroße benotigt, als ein Monitor. Daher muss von Pixel, Em und Rem in Points umgerechnet werden.

  * Pixels => Points
  * 6px => 5pt
  * 7px => 5pt
  * 8px => 6pt
  * 9px => 7pt
  * 10px => 8pt
  * 11px => 8pt
  * 12px => 9pt
  * 13px => 10pt
  * 14px => 11pt
  * 15px => 11pt
  * 16px => 12pt
  * 17px => 13pt
  * 18px => 14pt
  * 19px => 14pt
  * 20px => 15pt
  * 21px => 16pt
  * 22px => 17pt
  * 23px => 17pt
  * 24px => 18pt

Eine Schriftgroße von 12pt hat sich als optimal erwiesen. Nun hast du auch noch die Wahl, welchen Font du fur den Druck verwenden mochtest. Eine gute Lesbarkeit auf einem gedruckten Blatt Papier bilden Schriftarten mit Serifen, wie zum Beispiel die Georgia.

/* Font auf 16px/13pt setzen, Background auf Weiß und Schrift auf Schwarz setzen.*/

/* Das spart Tinte */

body {

font: 13pt Georgia, "Times New Roman", Times, serif;

line-height: 1.3;

background: #fff !important;

color: #000;

}

h1 {

font-size: 24pt;

}

h2, h3, h4 {

font-size: 14pt;

margin-top: 25px;

}

### 2 - Pagebreaks einsetzen - Seitenumbruche bestimmen

Mit den drei CSS-Eigenschaften **page-break-before**, **page-break-after** und **page-break-inside** kann man genau bestimmen, ob und wo eine Druckseite umgebrochen wird. Verhindert werden soll damit zum Beispiel, dass Bilder in zwei Teile umgebrochen werden.

  * **page-break-before **bestimmt dabei, ob und wie ein Seitenumbruch vor diesem Element stattfindet.
  * **page-break-after **wiederum kummert sich um Umbruche nach einem Element
  * **page-break-inside **kummert sich um einen eventuellen Umbruch innerhalb eines Elements, zum Beispiel der Bilder und Grafiken.

/* Folgende Einstellungen sind moglich: */

page-break-after : auto | always | avoid | left | right

page-break-before : auto | always | avoid | left | right

page-break-inside : auto | avoid

Auto ist der Standard des Druck-Elements, **always** setzt jedes Mal einen Umbruch, **avoid** verbietet den Umbruch und **left** und **right** ist gedacht fur Folgeseiten, die entsprechend links oder rechts formatiert werden. Geschickt fur den Druck eingesetzt sahen die Regeln so aus:

/* Alle Seitenumbruche definieren */

a {

page-break-inside:avoid

}

blockquote {

page-break-inside: avoid;

}

h1, h2, h3, h4, h5, h6 { page-break-after:avoid; 

page-break-inside:avoid }

img { page-break-inside:avoid; 

page-break-after:avoid; }

table, pre { page-break-inside:avoid }

ul, ol, dl { page-break-before:avoid }

### 3 - Der Umgang mit Links

Links sollten deutlich gekennzeichnet werden, damit sie auffallen. Da sich Links auf einem Blatt Papier nicht anklicken lassen, mussen wir die Link-Ziele visualisieren. Das machen wir mit den folgenden Notierungen:

/* Linkfarbe und Linkverhalten darstellen */

a:link, a:visited, a {

background: transparent;

color: #520;

font-weight: bold;

text-decoration: underline;

text-align: left;

}

a {

page-break-inside:avoid

}

a[href^=http]:after {

content:" <" attr(href) "> ";

}

$a:after > img {

content: "";

}

article a[href^="#"]:after {

content: "";

}

a:not(:local-link):after {

content:" <" attr(href) "> ";

}

### 4 - Videos und andere iframes ausblenden

Videos darzustellen auf einem ausgedruckten Papier ergibt keinen Sinn. Setzt man die iframes jedoch einfach nur auf display: none, dann bleiben hassliche Abstande ubrig. Mit dem folgenden Code setzt man die Abstande zuruck und blendet iframes, sowie Videos vollstandig aus.

/**

* Eingebundene Videos verschwinden lassen und den Whitespace der iframes auf null reduzieren.

*/

.entry iframe, ins {

display: none;

width: 0 !important;

height: 0 !important;

overflow: hidden !important;

line-height: 0pt !important;

white-space: nowrap;

}

.embed-youtube, .embed-responsive {

position: absolute;

height: 0;

overflow: hidden;

}

### 5 - Unnotige Elemente ausblenden

Viele Bereiche einer Website sollten nicht gedruckt werden. Zum ersten stellen sie keine wichtigen Informationen bereit, zum zweiten kostet der Ausdruck dieser Bereiche unnotig teure Tinte oder Toner. Daher blenden wir alle Bereiche aus, die nicht von Wert sind.

Fur dich bedeutet das, dass du in den Quellcode deiner Website eintauchen darfst, damit du die Bereiche findest, die nicht gedruckt werden sollten. Folgende Dinge bieten sich an, um sie auszublenden:

Der Header, die Navigationen, die Pagination, die Sidebar, die Tags und die Kategorien, die Kommentare, die Share-Buttons und weitere Elemente. Hier ein Auszug aus dem Print-Stylesheet meiner Website Techbrain.de:

/* Unnotige Elemente ausblenden fur den Druck */

#header-widgets, nav, aside.mashsb-container, 

.sidebar, .mashshare-top, .mashshare-bottom, 

.content-ads, .make-comment, .author-bio, 

.heading, .related-posts, #decomments-form-add-comment, 

#breadcrumbs, #footer, .post-byline, .meta-single, 

.site-title img, .post-tags, .readability 

{

display: none;

}

### 6 - Nachrichten vor und nach dem Druck-Content einfugen

Manchmal kann es sehr praktisch sein, vor und nach dem eigentlichen Druck-Inhalt Nachrichten einfugen zu konnen. Mit einer solchen Nachricht kannst du dich vielleicht auch bei deinem Leser bedanken, der deinen Artikel ausgedruckt hat. Oder aber du kannst eine Copyright-Nachricht einblenden. Auch hier gilt es wieder, die richtige CSS-Klasse von deinem Inhaltsbereich zu finden.

### Das komplette Druck-Stylesheet

## Die richtige Location: wo gehort das print.css denn hin?

Die folgenden Funktionen gehoren in die **functions.php** des Themes [oder in ein seitenspezifisches Plugin](https://www.drweb.de/magazin/wordpress-mit-eigenem-plugin-nutzen-68058/).

Die korrekte Antwort ware eindeutig in den Header. Folgende Funktion ist die richtige, wenn ein entwickeltes Theme in das offizielle Theme-Verzeichnis aufgenommen werden soll:

/* Die korrekte Funktion zum Hinzufugen des print.css */

function drweb_print_styles(){

wp_enqueue_style(

'drweb-print-style', 

get_stylesheet_directory_uri() . '/css/print.css', 

array(), 

'20130821', 

'print' // print styles only

);

}

add_action( 'wp_enqueue_scripts', 'drweb_print_styles' );

Solltest du jedoch dein eigenes Theme mit einem Druck-Stylesheet versorgen wollen, dann ist die oben beschriebene Art nicht unbedingt optimal. Erstens wird das CSS auf allen Seiten geladen, nicht nur auf den einzelnen Artikeln, zweitens blockiert es den Seitenaufbau und macht deine Website ein wenig langsamer. Daher:

**Jedes nicht zum Seitenaufbau im sichtbaren Bereich notige CSS gehort in den Footer!**

Zudem sollte es nur geladen werden, wenn die single.php mit den einzelnen Artikeln aufgerufen wird. Es durfte kaum jemanden geben, der deine Startseite drucken mochte.

Daher lassen wir das Stylesheet in den Fußbereich der Website laden.

### Benutzerfreundlichkeit: einen Druck-Button erstellen

Wenn du deinen Lesern ein gut gemachtes Druck-Stylesheet anbietest, dann ware es vorteilhaft, wenn du auch einen Button zum Ausdrucken in dein Theme einbauen wurdest. Die Vorgehensweise ist recht einfach, der Button kann mit CSS so designed werden, wie du es mochtest. Der Code auf meiner Website sieht so aus:

Im Theme kann dieser Button dann mit einem einfachen `<?php ah_print_button();?>` uberall aufgerufen werden, wo er erscheinen soll.

Wenn du eine Demo des Druck-Stylesheets und des Buttons mochtest, dann schaue vorbei auf [TechBrain.de](http://techbrain.de/). Dort findest du den Button unterhalb der Artikel und kannst dir anschauen, wie meine Druckansicht aussieht.

##### Der Artikel entstand als Erweiterungsidee zum Beitrag: [Webseiten druckerfreundlich machen und Druckkosten sparen](https://www.drweb.de/magazin/druckkosten-webseiten-druckerfreundlich-machen-76761/)

_(dpe)_
