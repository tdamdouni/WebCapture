# Icon Fonts für WordPress: So bindet ihr Font Awesome ein

_Captured: 2017-04-23 at 11:03 from [pressengers.de](http://pressengers.de/tipps/icon-fonts-fuer-wordpress-so-bindet-ihr-font-awesome-ein/)_

**Die ideale Losung, um Symbole auf einer Webseite anzuzeigen: Icons Fonts! Endlos skalierbar, beliebig anpassbar, flexibel. Besonders beliebt ist die Icon-Schriftart Font Awesome. Wir erklaren euch, was es mit Icon Fonts auf sich hat und zeigen euch, wie ihr Font Awesome mit oder ohne Plugin in eure WordPress Seite integriert.**

![Das WordPress Logo als Symbol in der Schriftart Font Awesome](http://pressengers.de/wp-content/uploads/2016/10/WordPress-Icon-Font-Awesome.png)

> _Mit der Icon-Schriftart Font Awesome peppt ihr das Layout eurer WordPress Seite ordentlich auf_

Wer auf seiner WordPress Seite Symbole verwendet, kommt um Icon Fonts eigentlich nicht mehr herum. Langst ist es uberholt, jedes Icon als eigenes Bild einzubinden. Stattdessen sind Icon Fonts eine gute Losung: ihr integriert eine ganze Reihe an flexibel anpassbaren Symbolen in eure WordPress Seite, die auf jedem Endgerat super aussehen. Besser geht's nicht!

Im Bereich Webdesign hat sich eine Icon-Schriftart besonders etabliert: [Font Awesome](http://fontawesome.io/). Wir zeigen euch, wie ihr die schicken Symbole mit oder ohne Plugin in WordPress einbindet und erklaren euch, warum ihr das uberhaupt tun solltet.

## Was sind Icon Fonts uberhaupt?

Mit Icon Fonts sind Schriftarten gemeint, die aus Symbolen bestehen. Anstelle der Zeichen unseres Alphabets enthalten sie also Icons. Was fur Symbole das sind und wie sie aussehen, hangt von der jeweiligen Schriftart ab.

![Auszug aus Icons der Schriftart Font Awesome](http://pressengers.de/wp-content/uploads/2016/10/Font-Awesome-Icons-Auszug.png)

> _Aus diesen und vielen weiteren Symbolen besteht die Schriftart Font Awesome_

Sehr beliebt im Web ist die Icon-Schriftart Font Awesome. Sie enthalt uber 600 Symbole.

## Warum Icon Fonts statt Bildern?

Icon Fonts haben gegenuber einzelnen Bildern mehrere Vorteile. Anstatt zahlreiche, einzelne Bilder vom Server zu laden und entsprechend fur jede Grafik eine Anfrage zu senden, wird nur **eine einzige Datei geladen**: die Schriftart.

Außerdem sind die Icons im Gegensatz zu Bildern ohne Qualitatsverluste **beliebig skalierbar und somit responsive**. Damit sind sie ideal fur die Anzeige auf allen Endgeraten (auch Retina-Displays!) geeignet. Egal wie groß der Bildschirm ist, das Icon wird in top Qualitat angezeigt.

Neben der großentechnischen Anpassbarkeit konnt ihr naturlich per CSS eure Icons auch anders einfarben oder sonst **beliebig stylen**.

## Die beliebte Schriftart Font Awesome manuell in WordPress integrieren

Die wohl bekannteste Icon-Schriftart ist [Font Awesome](http://fontawesome.io/). Bereits mehr als 600 Icons bekommt ihr, wenn ihr sie in eure WordPress Seite einbindet.

Die Vektor-Icons konnen mithilfe von CSS nach allen Regeln der Kunst angepasst werden und fugen sich so perfekt in euer Design ein. Außerdem werden zahlreiche CSS-Klassen mitgeliefert, mit denen ihr die Icons zum Beispiel skalieren, animieren oder ubereinander legen konnt.

### Font Awesome ohne Plugin in WordPress einbinden: so geht's

Mochtet ihr Font Awesome in WordPress verwenden, integriert ihr die Schriftart am besten uber den Drittanbieter [BootstrapCDN](https://www.bootstrapcdn.com/fontawesome/). Das ist am einfachsten und ihr braucht keine zusatzlichen Daten auf eurem Server zu speichern.

Dafur fugt ihr einfach diesen Codeschnipsel in die _functions.php_ eures Themes ein:
    
    
    function stylesheet_von_fontawesome_einbinden() {
    wp_enqueue_style ('font-awesome', '//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css');
    }
    
    add_action('wp_enqueue_scripts', 'stylesheet_von_fontawesome_einbinden');

Naturlich konnt ihr die Schriftart auch downloaden, per FTP auf euren Server hochladen und obigen Schnipsel an euer Verzeichnis anpassen. Der Weg uber BootstrapCDN ist aber deutlich unkomplizierter, und bei einem Update braucht ihr bloß die Versionsnummer innerhalb der Funktion anzupassen, um die aktuellsten Icons einzubinden.

### Die Icons von Font Awesome in WordPress verwenden

Mochtet ihr eines der Icons benutzen, konnt ihr das uber den <i>-Tag machen:
    
    
    <i class="fa fa-wordpress" aria-hidden="true"></i>

Das ist zum Beispiel das WordPress Logo als Icon

Welche Icons es gibt und wie deren Klassen heißen, konnt ihr im [Font Awesome Cheatsheet](http://fontawesome.io/cheatsheet/) nachschauen. Anhand dieser Klassen konnt ihr die Icons dann auch in eurem CSS-Stylesheet anpassen.

Fur die Verwendung von Font Awesome und den dazugehoren Klassen gibt es [hier einige sehr anschauliche Beispiele](http://fontawesome.io/examples/).

## 3 Plugins, um Icons von Font Awesome in WordPress zu verwenden

Mochtet ihr lieber ein Plugin benutzen, statt im Code eurer WordPress Seite herumzubasteln, solltet ihr euch diese drei Plugins anschauen. Alle drei integrieren die Icon-Schriftart Font Awesome in WordPress.

### 1\. Better Font Awesome

Das Plugin [Better Font Awesome](https://wordpress.org/plugins/better-font-awesome/) integriert die beliebte Schriftart in eure WordPress Seite. Es verwendet stets die aktuelle Version von Font Awesome und passt auch bereits benutzte Shortcodes so an, dass sie weiterhin funktionieren.

Verwenden konnt ihr die Icons uber Shortcodes oder einen Icon-Picker im visuellen Editor. Auch per HTML konnen die Icons eingebunden werden.

### 2\. Font Awesome 4 Menus

Mit dem WordPress Plugin [Font Awesome 4 Menus](https://wordpress.org/plugins/font-awesome-4-menus/) konnt ihr Icons der Schriftart Font Awesome in Menus oder auch generell auf eurer Seite benutzen.

Einbinden konnt ihr die Icons entweder mithilfe von Shortcodes oder uber ihre Klassen.

### 3\. AGP Font Awesome Collection

Auch [AGP Font Awesome Collection](https://wordpress.org/plugins/agp-font-awesome-collection/) integriert die Icon-Schriftart Font Awesome in eure WordPress Seite.

Verwenden und anpassen konnt ihr die Icons uber Shortcodes oder den Icon-Konstruktor im visuellen Editor.

Außerdem konnt ihr mit dem Plugin Slider erstellen, die ein Icon und zugehorige Infos enthalten. Die konnt ihr dann flexibel per Shortcode oder uber ein Widget in eure WordPress Seite integrieren.

## Fazit

Die momentan umfangreichste und beste Icon Schriftart? Ganz klar Font Awesome! Sie in WordPress zu integrieren ist denkbar einfach: entweder bindet ihr das Stylesheet uber die _functions.php_ eures Themes ein, oder ihr installiert euch ein passendes Plugin.

**Nutzt ihr Icon Fonts bzw. Font Awesome im Speziellen auf eurer WordPress Seite?**
