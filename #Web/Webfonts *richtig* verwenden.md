# Webfonts *richtig* verwenden

_Captured: 2015-12-09 at 12:15 from [maddesigns.de](http://maddesigns.de/webfonts-richtig-verwenden-2216.html)_

Da fragt sich jetzt der ein oder andere Webentwickler „Was kann man da falsch machen? Man bindet den [(new) Bulletproof @font-face Syntax](http://www.fontspring.com/blog/the-new-bulletproof-font-face-syntax) ein und gut ist". Problem hierbei wie immer unser geliebte OldIE, der Webfonts zwar schon im zarten Alter von Version 5.5 beherrschte, aber immer noch einen „alten" Syntax braucht.

**Das Problem:** faux-bold

![faux bold text](http://maddesigns.de/wp-content/uploads/2014/03/faux-bold-360x202.jpg)

> _faux bold text_

Das Problem ist nicht neu, 2012 schrieb Alan Stearns bei A List Apart den Artikel „[Say No to Faux Bold](http://alistapart.com/article/say-no-to-faux-bold)" und erst kurzlich Gerrit van Aaken im Artikel „[Webfonts: Fette Fehlerquelle](http://praegnanz.de/weblog/webfonts-fette-fehlerquelle)".

Abhilfe soll die Eigenschaft ‚[font-synthesis](http://www.w3.org/TR/css-fonts-3/#font-synthesis-prop)‚ schaffen:
    
    
    .say-no-to-faux-bold {
      font-synthesis: none;
    }

leider wird die Eigenschaft von keinem Browser unterstutzt

## @font-face Einbindung fur moderne Browser

Um die Fehldarstellungen zu vermeiden, bindet man den Font wie folgt ein:
    
    
    @font-face {
      font-family: Fontname; /* regular font */
      src: url("Fontname-Regular.woff") format("woff");
      font-weight: normal; font-style: normal; }
    
    @font-face {
      font-family: Fontname; /* bold font */
      src: url("Fontname-Bold.woff") format("woff");
      font-weight: bold; font-style: normal; }
    
    @font-face {
      font-family: Fontname; /* light font */
      src: url("Fontname-Light.woff") format("woff");
      font-weight: 300; font-style: normal; }
    
    @font-face {
      font-family: Fontname; /* italic font */
      src: url("Fontname-Italic.woff") format("woff");
      font-weight: normal; font-style: italic; }
    
    @font-face {
      font-family: Fontname; /* bolditalic font */
      src: url("Fontname-BoldItalic.woff") format("woff");
      font-weight: bold; font-style: italic; }

**fur Android zusatzlich TTF/OTF einbinden**
    
    
    @font-face {
      font-family: Fontname; /* regular font */
      src: url("path/Fontname-Regular.ttf") format("ttf"),
           url("path/Fontname-Regular.woff") format("woff");
      font-weight: normal;
      font-style:  normal; }

**Zuweisung in Überschrift:**
    
    
    h1 {
      font-family: Fontname, sans-serif;
    }

## @font-face fur Old-IE (IE8)

Fur die alteren Internet Explorer, die das WOFF-Format nicht unterstutzen, kann man die Schrift im EOT-Format einbinden. Hier denke ich auch immer an die Performance und an das Rendering der Schriften und empfehle meist, fur die Browser keine Webfonts zu verwenden. Zudem sollte man die Zugriffsstatistik fur die Versionen prufen, bevor man sich die Muhe macht. Zugegeben bisher wollten noch nicht sehr viele Kunden der Empfehlung, die Schriften fur IE8 weg zu lassen, folgen.

Fur IE8 muss die Schriften wie folgt eingebunden werden:
    
    
    /* ie-specific.css */
    @font-face {
      font-family: Fontname-regular; /* regular IE font */
      src: url("Fontname-Regular.eot"); }
    
    @font-face { /* bold IE font */
      font-family: Fontname-bold;
      src: url("Fontname-Bold.eot"); }
    
    @font-face { /* italic IE font */
      font-family: Fontname-italic;
      src: url("Fontname-Italic.eot"); }
    
    @font-face { /* bold italic IE font */
      font-family: Fontname-bolditalic;
      src: url("Fontname-BoldItalic.eot"); }

**uber Conditional Comments in die Seite einbinden**
    
    
    <!--[if lt IE 9]>
      <link rel="stylesheet" href="ie-specific.css" media="screen" />
    <![endif]-->

## Font-Loading Performance

Text der mit Webfonts ausgezeichnet ist, wird in einigen Browsern solange nicht angezeigt, bis die Schrift heruntergeladen ist, um den „FOUT" (flash of unstyled text) zu vermeiden. Besonders nachteilig ist dieses Verhalten in mobilen Browsern, z.B. Mobile Safari (iOS), da das Laden im Mobilnetz haufig langsamer ist (Stichwort Latenz). Hier wartet man oftmals lange bis man endlich den Text lesen kann. Besonders argerlich ist das meiner Meinung nach bei Schriften, die nicht großartig anders aussehen als vorhandene Systemschriften. _(Typonazis werden mich jetzt steinigen)_

![font-loading-ala](http://maddesigns.de/wp-content/uploads/2014/03/font-loading-ala.jpg)

> _Webfont Loading Performance (FOUT)_

**Randnotiz:** Moderne Browser laden Schriften erst, wenn sie im CSS zugewiesen sind. Bedeutet also man konnte mehrere Schriften uber @font-face verknupfen, das Laden der Schrift erfolgt erst, wenn im CSS die Zuweisung uber `font-family` geschieht.

_In Firefox fur Android kann man Webfonts uber about:config deaktivieren (geht auch beim Desktop Firefox)_
    
    
    gfx.downloadable_fonts.enabled = false

Auch die Zeit, wann ein Fallback-Font geladen wird, kann eingestellt werden, der Defaultwert ist aktuell 3000ms fur die Anzeige des Fallback-Font.
    
    
    gfx.downloadable_fonts.fallback_delay = 1000

> _fallback-delay auf 1sek kurzen._

Paul Irish hat fur Chrome (Blink) letztens [eine Umfrage unter den Entwicklern gestartet](https://plus.google.com/+PaulIrish/posts/MeoUmZxNRZB), wie das Browserverhalten beim Laden von Schriften sein sollte. Ilya Grigorik beschreibt [auf Google+](https://plus.google.com/+IlyaGrigorik/posts/hEhRubu9za7) wie die Ladeperformance in Chrome verbessert wurde und sich Chrome in Zukunft wie Firefox verhalt.

### Fonts base64 decodieren

Fonts sollten nicht mit base64 codiert in CSS eingebunden werden, da das das Stylesheet unnotig aufblast und somit das Rendering der Seite verzogert.

## Webfontloader - Webfonts asynchron laden

[Webfontloader](https://github.com/typekit/webfontloader) ist ein Open-Source-Script von Typekit, mit dem man die Schriften von Typekit, Google, Fontdeck, Fonts.com und weiteren Foundries asynchron laden kann. Zu dem kann man auch selbst gehostete Fonts uber den Webfontloader laden.

**Einbindung des Webfontloader**
    
    
    <script>
    WebFontConfig = {
      typekit: { id: 'xxxxxx' }
    };
    (function() {
      var wf = document.createElement('script');
      wf.src = ('//ajax.googleapis.com/ajax/libs/webfont/1.4.7/webfont.js';
      wf.type = 'text/javascript';
      wf.async = 'true';
      var s = document.getElementsByTagName('script')[0];
      s.parentNode.insertBefore(wf, s);
    })();
    </script>

### Font-Events

Bindet man das Script ein, stellt Webfontloader beim Aufruf Klassen fur die erfolgten Font-Events bereit. Das Script meldet also, was der aktuelle Zustand des Ladevorgangs ist. Die Klassen werden wie bei Modernizr zum  
<html> Class-Attribut hinzugefugt.

**Klassen, die Webfontloader hinzufugt:**
    
    
    .wf-loading
    .wf-active
    .wf-inactive
    .wf-<familyname>-<fvd>-loading
    .wf-<familyname>-<fvd>-active
    .wf-<familyname>-<fvd>-inactive

**Verwendung im CSS:**
    
    
    h1, h2, h3 {
      font-family: sans-serif;
    }
    
    .wf-active h1, .wf-active h2, .wf-active h3 {
      font-family: "webfont", sans-serif;
    }

Beispiel: Einbindung der „Source Sans Pro" mit Webfontloader uber GoogleFonts.com:
    
    
    //= require webfonts.js
    
    WebFont.load({
        google: { families: [ 'Source+Sans+Pro:400,300,600:latin' ] }
        // load Source Sans Pro: light, normal, bold, light italic, normal italic, bold italic : latin subset
        // google: { families: [ 'Source+Sans+Pro:400,300,700,700italic,400italic,300italic:latin' ] }
    });

Wie sich vielleicht erahnen lasst, kann man in der Konfiguration mehrere Schriftschnitte, die man laden mochte, definieren.

  * 400 == normal
  * 700 == bold
  * 300 == light
  * 400italic == normal kursiv
  * 500 == medium

Mit dem Zusatz `:latin` kann man den Zeichenumfang steuern, hier waren es alle lateinischen Schriftzeichen. Welche Schriftzeichen wirklich vorhanden sind, sollte man genau prufen manchmal fehlen Schriftzeichen (skandinavische).

### native HTML5 Font-Events

… gibt es noch nicht, sind aber bereits in einer [ersten Version spezifiziert](http://www.w3.org/TR/css-font-loading/). Dafur gibt es aber bereits einen Polyfill: [Polyfill fur native Font-Events](https://github.com/bramstein/fontloader)

### lokale System-Fonts bevorzugen

Nicht immer muss ein Webfont geladen werden, in Mac OSX ist z.B. seit Mavericks ‚PT Sans' im System verfugbar, den Font extra zu laden ware unnotig. Mit dem Keyword ‚local' werden Systemfonts bevorzugt.
    
    
    @font-face {
      font-family: 'PT Sans';
      src: local('PT Sans'), local('PTSans-Regular'), url('fonts/ptsans-regular.woff') format('woff'),
           local('PT Sans'), local('PTSans-Regular'), url('fonts/ptsans-regular.ttf') format('truetype');
      font-weight: normal;
      font-style: normal;
    }

Auch die in [iOS7](http://iosfonts.com/) hinzugekommene ‚Helvetica Neue Condensed Bold' kann uber den [Post-Script Namen](http://stackoverflow.com/questions/5612506/how-can-i-use-helvetica-neue-condensed-bold-in-css#comment30950211_5612781) verwendet werden.
    
    
    @font-face { 
      font-family: Helvetica; 
      font-weight: bold; 
      src: local(HelveticaNeue-CondensedBold); 
    }

## Fallback-Font auf mobilen Geraten

Wenn man responsive Webseiten erstellt, sollte man sich bewusst sein, dass nicht alle Schriften, die verwendet werden sollen, auch auf dem Endgerat vorhanden ist. Android hat nur wenige Schriften vorinstalliert. Jordan Moore hat eine Ü[bersichttabelle der Systemfonts auf mobilen Systemen](http://www.jordanm.co.uk/tinytype) bereit gestellt. Allerdings fehlt dort noch ein iOS7 Update.

![fallback-fonts2](http://maddesigns.de/wp-content/uploads/2014/03/fallback-fonts2.png)

Auf Android sind weder Arial, noch Helvetica oder Times installiert, die Standard-Schrift ist Droid (Sans/Serif). Man sollte meinen, wenn man `font-family: 'Times New Roman', Times, serif;` angibt, dass Android dann auf den Serif Font zuruck fallt. Anscheinend kann das Android ganz schon verwirren und fuhrt zu Fehldarstellungen.

![fallback-fonts4](http://maddesigns.de/wp-content/uploads/2014/03/fallback-fonts4.png)

> _Samsung GT-I9300 (Android 4.1.2)_

![fallback-fonts3](http://maddesigns.de/wp-content/uploads/2014/03/fallback-fonts3.png)

> _Samsung GT-S5830 (Android 2.3.3)_

Als Fix, damit alle getesteten Androids den Fallback-Font anzeigen, musste ‚Droid Serif' explizit angegeben werden. (HT [@closingtag](https://twitter.com/closingtag))
    
    
    font-family: 'Serif Webfont', 'Droid serif', 'Times New Roman', Times, serif;

Wer noch Erganzungen hat, bitte einfach kommentieren.
