# Web-Apps entwickeln mit HTML, CSS3 und JavaScript

_Captured: 2015-11-15 at 15:02 from [t3n.de](http://t3n.de/magazin/web-apps-entwickeln-native-app-effekt-228688/)_

![](http://t3n.de/magazin/wp-content/uploads/2011/11/tec_web_apps_bild-596x283.jpg)

> _Foto: kimberrywood/iStock_

Eine Web-App ist eine Website, die fur mobile Endgerate aufbereitet wird und dank der kommenden Internet-Standards HTML5 und [CSS3](http://t3n.de/tag/css3) sowie der Skriptsprache [JavaScript](http://t3n.de/tag/javascript) Eigenschaften einer nativen App erhalt. Sie wird gewohnlich mit dem internen Browser geoffnet und auf dem Homescreen verknupft.

Die Entwicklung kann dabei auf verschiedene Arten erfolgen: Entweder entwickelt man eine Web-App programmatisch und hat die volle Kontrolle uber den Quellcode. Oder man verwendet Frameworks, die durch ihre vordefinierten Templates und Funktionen die Entwicklung erheblich erleichtern (konnen).

## Web-App in Handarbeit

Ein Vorteil der Web-App-Programmierung ist der einfache Einstieg fur Web-Entwickler, da sie keine neue Programmiersprache erlernen mussen, sondern ihr bisheriges Wissen in die Entwicklung einer mobilen Website einfließen lassen konnen. So sieht eine einfache App, die ein Bild und eine Überschrift anzeigt, kaum anders aus als eine herkommliche HTML-Seite. Allerdings wird diese spater auch offline verfugbar sein.

## Only for iPhone

Ruft man diese Website mit dem iPhone (ab iOS 3.0) auf, so wird, wahrend die Inhalte der Startseite geladen werden, ein so genannter Splashscreen, also ein Lade-Bild, angezeigt („apple-touch-startup-image"). Das Meta-Tag „viewport" legt die Auflosung fest, mit der die Seite vom Browser gerendert werden soll. Im Beispiel soll die Auflosung des Gerats verwendet werden. Zusatzlich wird die initiale Skalierung der Seite festgelegt und ob der Inhalt der Seite durch den User skaliert werden darf (etwa durch „Pinch to Zoom").

Eine einfache Web-App
    
    
    <?xml version=„1.0“ encoding=„utf-8“?>
    <!DOCTYPE html>
    <[html](http://t3n.de/tag/html) manifest=„config/cache.manifest“>
    <head>
     <title>A simple Web-App</title>
     <meta name=„viewport“ content=„width=device-width, initial-scale=1.0, user-scalable=no“ />
     <meta name=„apple-mobile-web-app-capable“ content=„yes“ />
     <meta name=„apple-mobile-web-app-status-bar-style“ content=„black“ />
     <link rel=„apple-touch-icon“ href=„images/icon.png“ />
     <link rel=„apple-touch-startup-image“ href=„images/splashscreen.png“ />
     <link rel=„stylesheet“ href=„css/simple.css“ type=„text/css“ media=„screen,mobile“ />
     <script type=„text/javascript“ xsrc=„js/simple.js“></script>
    </head>
    <body>
     <header>
     <h1>Eine einfache Web-App</h1>
     </header>
     <section id=„content“>
     <img xsrc=„images/picture.jpg“ />
     </section>
    </body>
    </html>

Listing 1

![Im Grunde ist eine Web-App nichts anderes als eine optimierte Webseite.](http://t3n.de/magazin/wp-content/uploads/2011/11/dms_de1420a307b4342fd911d5b7f1337275-113x170.jpg)

> _Im Grunde ist eine Web-App nichts anderes als eine optimierte Webseite._

Die drei Meta-Tags in Listing 1 werden derzeit nur von iOS interpretiert. Alle anderen mobilen Betriebssysteme ignorieren diese Tags, sodass sich keine Komplikationen dadurch ergeben.

Setzt man das Attribut „content" beim Meta-Tag „apple-mobile-web-app-capable" auf „yes", so wird die Web-App nach dem Aufruf uber den Homescreen im Vollbild-Modus ohne Browser-Leiste angezeigt. „apple-mobile-web-app-status-bar-style" definiert das Aussehen der Status-Leiste und kann einen der folgenden Werte annehmen:

  * default (grau)
  * black (schwarz)
  * black-translucent (schwarz, transparent)

## App-Icon

Um die Web-App mit dem Homescreen des iPhones zu verknupfen, wird ein Icon in der Große 114x114 Pixel im Format PNG benotigt. An dieser Stelle besteht die Moglichkeit, mehrere „apple-touch-icons" mit unterschiedlichen Großen anzugeben. Fur das Beispiel wird die Icon-Große des iPhone 4 verwendet, da die alteren iPhones dieses Icon in einer akzeptablen Qualitat herunterrechnen konnen.

Android unterstutzt App-Icons ab Version 2.1, das passende Tag heißt „apple-touch-icon-precomposed". Wird ausschließlich dieses Tag verwendet, stellt das iPhone das App-Icon allerdings ohne die Standard-Effekte wie abgerundete Ecken, Schattierungen und Reflexionen dar; das Icon gilt dann als „precomposed".

Icon fur Android
    
    
    <link rel=„apple-touch-icon-precomposed“ href=„icon_android.png“ />

Listing 2

## Offline arbeiten

Eine wichtige Eigenschaft von Web-Apps ist es, Inhalte auch offline verfugbar machen zu konnen. HTML5 stellt Webseiten dafur einen sogenannten Application Cache zur Verfugung, mit dessen Hilfe Inhalte auch ohne Netzverbindung verwendet werden konnen. Die Einbindung dieses Caches ist recht einfach, da es sich hierbei um ein Manifest handelt, das in Form einer Textdatei vorliegen muss.

Application-Cache-Manifest
    
    
    CACHE MANIFEST
    # 2011-10-26 Version 1.0
    
    CACHE:
    index.html
    css/simple.css
    js/simple.js
    images/splashscreen.png
    images/picture.jpg
    
    NETWORK:
    
    FALLBACK:
    *.html /offline.html

![Die Web-App unterscheidet sich auf dem Homescreen nicht von den nativen Apps.](http://t3n.de/magazin/wp-content/uploads/2011/11/dms_5f884d2352a5b4ffdf32075586289f2c-113x170.jpg)

> _Die Web-App unterscheidet sich auf dem Homescreen nicht von den nativen_

Im CACHE-Bereich des Manifests werden alle Ressourcen angegeben, die vom Browser zwischengespeichert werden sollen. Unter NETWORK werden alle Ressourcen aufgelistet, die nicht speicherbar sind. Dazu zahlen etwa Schnittstellen wie jene der Twitter-API. Sollten bestimmte Resourcen nicht verfugbar sein, so konnen im FALLBACK-Bereich Alternativen festgelegt werden. Im Beispiel wird festgelegt, dass fur jede nicht vorhandene HTML-Seite die Datei „offline.html" angezeigt werden soll.

Der Application Cache wird durch das Attribut „manifest", das den Pfad zum Manifest enthalt, im HTML-Tag aktiviert. Damit der Browser das Cache-Manifest interpretieren kann, muss dieses mit dem MIME-Type „text/cache-manifest" vom Server ausgeliefert werden.

## Cache aktualisieren

Um den Cache einer Web-App zu aktualisieren, leert der Benutzer entweder den Browser-Cache oder der Inhalt des Cache-Manifests andert sich. Es reicht also nicht aus, dass sich der Inhalt einer Datei andert. Im Beispiel-Manifest wird deshalb ein Datum und eine Versionsnummer in Form eines Kommentars verwendet. Ändert sich eine Datei, reicht es, im Manifest das Datum und die Version anzupassen, um der Web-App Änderungen mitzuteilen.

## Design, Layout und UX

Um der Web-App einen nativen App-Look zu verpassen, kommen diverse CSS3-Eigenschaften zum Einsatz. CSS3 erfahrt eine breite Unterstutzung unter den mobilen Browsern, daher stellt es fur Web-App-Entwickler ein außerst nutzliches Werkzeug dar. Einige der Eigenschaften im Überblick:

  * Eigene Schriftarten in eine Webseite zu integrieren ist eigentlich kein neues Feature von CSS3, denn „@font-face" wurde bereits mit CSS2 eingefuhrt. In der neuen Version unterstutzt „@font-face" jedoch beliebige TrueType- oder OpenType-Schriftarten.

TrueType- und OpenType-Schriftarten mit CSS3
    
    
    @font-face {
     font-family: Monospace;
     src: url('fonts/own_monospace.otf');
    }

Listing 4

  * Dank CSS3 konnen Texte und Boxen mit einem Schatten versehen werden, ohne dafur spezielle Grafiken laden zu mussen. Das Rendering der Schatten ist allerdings sehr rechenintensiv, daher sollte sparsam mit diesen optischen Elementen umgegangen werden.
  * Auch abgerundete Kanten und Verlaufe konnen mit CSS3-Bordmitteln realisiert werden. Aufgrund der neuen Tags sind auch hier die Grafiken uberflussig, was die Performance verbessert und damit die Ladezeit verkurzt.
  


## Jetzt kommt Bewegung ins Spiel

Animationen und Transformationen zwischen zwei Seiten werden in nativen [Apps](http://t3n.de/tag/apps) sehr gerne verwendet und sind mit [CSS3](http://t3n.de/tag/css3) auch innerhalb des Browsers moglich. Dieses Thema ist jedoch verhaltnismaßig komplex und wird etwa von [Rich Bradshaw ](http://css3.bradshawenterprises.com/) [1] und im [Webstandard-Blog ](http://webstandard.kulando.de/) [2] ausfuhrlich behandelt.

## Fur jeden das richtige Stylesheet

Von vielen nativen Apps ist man gewohnt, dass sich das Aussehen der App an die Orientierung des Gerats anpasst. Seit iOS 4.0 verstehen iPhone, iPod Touch und das iPad das „orientation"-Attribut beim Einbinden der CSS-Dateien im Head-Bereich der Seite. Auch Android-Gerate verarbeiten dieses Attribut korrekt.

Orientierungs-abhangiges Einbinden der Stylesheets
    
    
    <!-- Einbinden im Hochformat -->
    <link rel=„stylesheet“ href=„css/simple_portrait.css“ type=„text/css“ media=„screen and (orientation:portrait)“ />
    
    <!-- Einbinden im Querformat -->
    <link rel=„stylesheet“ href=„css/simple_landscape.css“ type=„text/css“ media=„screen and (orientation:landscape)“ />

Listing 8

Es ist auch moglich, das Stylesheet von der Display-Große, respektive der Breite, abhangig zu machen.

Breiten-abhangiges Einbinden der Stylesheets
    
    
    <!-- Einbinden, wenn das Display schmaler als 480 Pixel ist -->
    <link rel=„stylesheet“ href=„simple_mobile.css“ type=„text/css“ media=„screen and (max-width: 480px)“ />
    
    <!-- Einbinden, wenn das Display breiter als 480 Pixel ist -->
    <link rel=„stylesheet“ href=„simple_default.css“ type=„text/css“ media=„screen and (min-width: 481px)“ />

Listing 9

## Beruhren erlaubt

Was „touchbar" sein soll, sollte eine gewisse Große haben, damit es keine Rolle spielt, ob ein Benutzer große oder kleine Finger hat. Laut Apple hat ein „Tap" eine Auflageflache von 44x44 Pixeln. Daher sollten Icons und Buttons eine Mindest-Große von 32x32 Pixeln haben, um inklusive Padding auf diese Große zu kommen.

![Mit jQuery Mobile erhält man bereits mit ein paar Zeilen Code imposante Ergebnisse.](http://t3n.de/magazin/wp-content/uploads/2011/11/dms_50a8cbcfa12bd8f51f53d8a9ce4afe3b-113x170.jpg)

> _Mit jQuery Mobile erhalt man bereits mit ein paar Zeilen Code imposante Ergebnisse._

Es geht auch anders: Dank zahlreicher Frameworks muss man das Rad nicht standig neu erfinden. Da sich die Frameworks in ihrer Handhabung nur maßig voneinander unterscheiden, wird an dieser Stelle jedoch nicht auf alle eingegangen.

## jQuery Mobile

jQuery Mobile basiert auf dem bekannten JavaScript-Framework jQuery. jQuery Mobile optimiert die Seiten fur die verschiedenen Gerate und Betriebssysteme und kummert sich um die Darstellung im Hoch- und Querformat.

Um das Framework mit all seinen Eigenschaften verwenden zu konnen, mussen sowohl jQuery als auch jQuery Mobile uber die entsprechenden CSS-Dateien im HTML-Template eingebunden werden. Anschließend kann die Seite in Abschnitte eingeteilt und jedem Abschnitt konnen bestimmte Funktionen zugewiesen werden. Das folgende Beispiel enthalt einen Header, eine horizontale Navigationsleiste, einen Inhaltsbereich und einen Footer mit zwei Buttons.

Der Nachteil bei der Verwendung von Frameworks liegt meistens in der Große. Initial werden alle Funktionen und Styles geladen, auch wenn diese in der [Web-App](http://t3n.de/tag/web-app) nicht verwendet werden. Bei jQuery Mobile betragt die Große des Frameworks inklusive CSS aktuell rund 60 KByte; dafur werden wiederum alle wichtigen mobilen Betriebssysteme unterstutzt, darunter iOS, Android, Windows Phone und BlackBerry.

jQuery Mobile verwenden
    
    
    <!DOCTYPE html>
    <html>
    <head>
     <title>A much simpler Web-App</title>
     <meta name=„viewport“ content=„width=device-width, initial-scale=1.0, user-scalable=no“ />
     <meta name=„apple-mobile-web-app-capable“ content=„yes“ />
     <meta name=„apple-mobile-web-app-status-bar-style“ content=„black“ />
     <link rel=„stylesheet“ href=„css/jquery.mobile-1.0rc2.css“ />
      <link rel=„stylesheet“ href=„css/simple.css“ />
     <script type=„text/javascript“ xsrc=„js/jquery-1.6.4.min.js“></script>
     <script type=„text/javascript“ xsrc=„js/jquery.mobile-1.0rc2.min.js“></script
    </head>
    <body>
     <div data-role=„page“>
     <div data-role=„header“>
     <h1>jQuery Mobile</h1>
     </div>
     <div data-role=„navbar“>
      <ul>
     <li><a href=„index.html“>Start</a></li>
     <li><a href=„contact.html“>Kontakt</a></li>
     </ul>
     </div>
     <div data-role=„content“>
     <img xsrc=„images/picture.jpg“ />
     </div>
     <div data-role=„footer“>
     <a href=„index.html“ data-role=„button“ data-icon=„arrow-u“>Hoch</a>
     <a href=„index.html“ data-role=„button“ data-icon=„arrow-d“>Runter</a>
     </div>
     </div>
    </body>
    </html>

Listing 10

## Gerate-spezifische Funktionen

Der Zugriff auf Gerate-spezifische Funktionen via Browser ist derzeit noch stark eingeschrankt. Durch [HTML5](http://t3n.de/tag/html) ist es zwar schon jetzt moglich, Daten in einer Datenbank abzulegen, die Koordinaten eines Benutzer durch die Geo-Location-Funktion zu bestimmen oder Videos direkt im Browser abzuspielen. Viele Funktionen, wie der Zugriff auf die Kontakte oder die integrierte Kamera, sind jedoch nativen Apps vorbehalten.

## Hybrid-Apps

Um mit einer Web-App dennoch auf die Gerate-APIs zugreifen zu konnen, muss aus einer Web-App eine sogenannte Hybrid-App gemacht werden. Das ist nichts anderes, als eine Web-App, die in eine native App eingebettet ist.

Eine solche Hybrid-App wird mithilfe eines Frameworks wie PhoneGap erstellt. PhoneGap ist ein JavaScript-Framework, das den Zugriff auf Geratefunktionen bereitstellt. PhoneGap benotigt zur Erstellung einer Hybrid-App naturlich das jeweilige SDK des mobilen Betriebssystems, unterstutzt dafur aktuell auch alle gangigen Systeme - Android, BlackBerry, iOS und andere.

Framework
Anmerkungen

jQTouch
jQuery-Erweiterung fur Android und iOS

jQuery Mobile
jQuery-Derivat fur Android, iOS, BlackBerry etc.

PhoneGap
Hybrid-App-Framework fur Android, iOS, BlackBerry etc.

Rhodes
App-Framework fur Ruby on Rails und HTML5

Sencha Touch
Web-App-Framework fur Android, iOS und BlackBerry

Titanium Mobile
Hybrid-App-Framework fur Android und iOS

## Vertriebsmoglichkeiten

Aktuell besteht die Moglichkeit, Web-Apps uber den [OpenAppMkt](http://t3n.de/magazin/web-apps-entwickeln-native-app-effekt-228688/2/www.openappmkt.com) [3] anzubieten. Der Entwickler kann seine Web-App dort entweder kostenlos anbieten oder kommerziell vertreiben. Von den Verkaufserlosen behalt der Anbieter der Plattform allerdings 20 Prozent ein.

Um seine Web-App kommerziell und/oder reichweitenstark zu vertreiben, muss man den Weg uber die oben genannte Hybrid-App gehen. Allerdings sind die Nutzer bei Hybrid-Apps sehr kritisch; es gilt daher, darauf zu achten, dass die dahinter liegende Web-App bei Leistung und Usability mit einer nativen App konkurrieren kann.

## Fazit

Dank HTML5 und CSS3 lassen sich bereits heute Web-Apps bauen, die mit ihren nativen Konkurrenten problemlos mithalten konnen. Es gibt Bereiche, in denen die nativen Apps noch unschlagbar sind, etwa bei 3D-Spielen. Durch den rasanten Fortschritt in der mobilen Welt und Techniken wie WebGL kann aber vielleicht schon bald auch dieser Bereich von den Web-Apps erobert werden.

Großtes Manko der Web-Apps ist momentan noch der Vertrieb, denn eine zentrale Plattform im Internet gibt es aktuell nicht. Dieser Nachteil lasst sich aber durch das Erstellen einer Hybrid-App wettmachen.

Ebenfalls fur Web-Apps spricht die Wartung: Im Gegensatz zur nativen App konnen Änderungen direkt und ohne Review-Prozess durchgefuhrt und implementiert werden. Sogar bei Apple.

Es bleibt abzuwarten, ob sich Web-Apps tatsachlich bei den Nutzern durchsetzen. Fur Entwickler sind sie in jedem Falle ein Gewinn. Und zahlreiche Firmen und Verlage sind bereits auf den Zug der plattformunabhangigen Anwendungen aufgesprungen.

Der Autor

**Jochen Block **ist als Head of Innovation bei der Hamburger Full-Service-Agentur CELLULAR tatig. Er ist seit mehreren Jahren in der mobilen Welt zu Hause und entwickelt neben mobilen Portalen Apps fur iOS und Android. Aktuell arbeitet er an Smart-TV-Losungen und entwickelt Apps fur die Windows-Phone-7-Plattform.

Anzeige

Wir lieben Shop- und Content-Management-Systeme seit uber 12 Jahren und bieten seither erstklassigen und kostenlosen Experten-Support. Jetzt legen wir noch einen drauf: In Webinaren und Telefonaten mit unseren Experten sowie CMS-Choryphaen aus den Communitys erhaltst du bei uns das geballte CMS-Know-how! [ Mehr erfahren!](http://guruads.de/api/click/56372fa1497959ee1600003e)
