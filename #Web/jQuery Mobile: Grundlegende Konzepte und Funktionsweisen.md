# jQuery Mobile: Grundlegende Konzepte und Funktionsweisen

_Captured: 2015-11-15 at 15:48 from [t3n.de](http://t3n.de/news/jquery-mobile-grundlegende-konzepte-funktionsweisen-326279/)_

Wie wir vor kurzem berichtet haben, ist jQuery Mobile in der Beta 2 seiner Version 1.0 erschienen. Grund genug, sich das Framework einmal genauer anzuschauen.

## Voraussetzungen fur den Einsatz von jQuery Mobile

jQuery Mobile benotigt einen halbwegs modernen Smartphone- oder Tablet-Browser um seine Starken auszuspielen. Es funktioniert auf den meisten Geraten, die in den letzten Jahren erschienen sind. Eine grundlegende Voraussetzung ist ein aktiviertes JavaScript, da es auf dem JavaScript-Framework jQuery aufbaut.

Um zu starten brauchen wir nun eine vernunftige DOM-Struktur, am besten mit einem aktuellen Doctype. Wir nehmen dafur den HTML5-Doctype um zukunftssicher zu sein. Dazu mussen wir die JS-Dateien fur jQuery und jQuery-Mobile einbinden sowie die passende CSS-Dateien. Dabei greifen wir auf die jQuery CDN zu, um diese nicht extra runterladen zu mussen und gleich beginnen zu konnen. Jetzt muss nur noch der Viewport gesetzt werden und wir sind startbereit und haben ungefahr folgenden [Code](http://t3n.de/tag/webentwicklung).
    
    
    <!DOCTYPE html> <html> 
     <head> 
      <title>Seitentitel</title>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <link rel="stylesheet" href="http://code.jquery.com/mobile/1.0b2/jquery.mobile-   1.0b2.min.css" />
      <script type="text/javascript" src="http://code.jquery.com/jquery-1.6.2.min.js">    </script>
      <script type="text/javascript" src="http://code.jquery.com/mobile/1.0b2/jquery.mobile-1.0b2.min.js"></script>
     </head>
     <body>
     </body>
    </html>

## Die erste Seite in jQuery Mobile

Gluckwunsch, du hast jetzt deine erste Seite in jQuery-Mobile aufgesetzt. Nur leider ist da noch nicht all zu viel zu sehen. Tauchen wir nun einfach etwas tiefer in die Materie jQuery-Mobile ein.

Dazu andern wir den Bereich zwischen den `body`-Tags etwas ab mit folgendem Code:
    
    
    <div data-role="page"> <div data-role="header"><h1>Willkommen</h1></div> <div data-role="content"> <h2>Inhaltslos</h2> <p>Keiner denkt an den <strong>Inhalt</strong></p> </div> <div data-role="footer"><h4>Auf Wiedersehen</h4></div> </div> 

Wir haben jetzt also 4 DIV's erstellt. Ein Parent-DIV und 3 Child-DIV's. Jedem DIV weisen wir eine `data-role` zu, je nachdem welche `Rolle` das jeweilige DIV einnehmen soll. Das Parent-DIV ist sozusagen der Container in dem die erste Seite dargestellt werden soll. Die restlichen DIV's stehen fur folgende Rollen:

  * `header` fur die Kopfzeile am Anfang der Seite
  * `content` fur den Inhalt
  * `footer` fur eine Fußzeile am Ende

Zugegeben, das war nicht sonderlich kompliziert, aber das ist alles was wir brauchen um die erste Seite in jQuery Mobile zu erstellen. Den Beweis konnt ihr euch im Screenshot ansehen oder das Ganze einfach auf euren eigenen Smartphones testen.

![jQuery Mobile - die erste Seite](http://t3n.de/news/wp-content/uploads/2011/08/IMG_0604-400x600.png)

> _jQuery Mobile - die erste Seite_

## Viele Seiten in einer HTML-Datei

Das Problem vieler Smartphones ist die Verbindungsgeschwindigkeit und ihre Performance, wenn viele Seiten geladen werden mussen. jQuery Mobile lost dieses Problem indem ihr mehrere Seiten in einer HTML-Datei festlegen konnt, die nur ein Mal geladen werden muss. So kann ein User ziemlich schnell auf eurer Seite surfen. Mehrere Seiten anzulegen ist dabei nach wie vor ziemlich simpel.
    
    
    <div data-role="page" id="seite1"> <div data-role="header"><h1>Willkommen</h1></div> <div data-role="content"> <h2>Inhaltslos</h2> <p>Keiner denkt an den <strong>Inhalt</strong></p> </div> <div data-role="footer"><h4>Auf Wiedersehen</h4></div> </div> <div data-role="page" id="seite2"> <div data-role="header"><h1>Willkommen auf Seite 2</h1></div> <div data-role="content"> <h2>Lorem Ipsum</h2> <p>Wer ist eigentlich Lorem Ipsum ?</p> </div> <div data-role="footer"><h4>Auf Wiedersehen</h4></div> </div> 

## Navigation mit jQuery Mobile

Wir verfahren also genauso wie zuvor, nur dass wir in diesem Beispiel zwei `page's` anlegen und jeweils eine` ID` vergeben. Das Problem, welches noch besteht, ist die Navigation. Wir andern also unseren Footer mit folgenden Daten fur Seite 1:
    
    
    <div data-role="footer"> <div data-role="navbar"> <ul>  <li><a href="#seite1" data-iconpos="top" data-icon="home">Seite 1</a></li>  <li><a href="#seite2" data-iconpos="top" data-icon="search">Seite2</a></li> </ul> </div> 

Fur die Seite 2 verschieben wir die CSS-Klasse `ui-btn-active` in den Link fur die Seite 2:
    
    
    <div data-role="footer"> <div data-role="navbar">  <ul>  <li><a href="#seite1" data-iconpos="top" data-icon="home">Seite 1</a></li> <li><a href="#seite2" data-iconpos="top" data-icon="search">Seite2</a></li> </ul> </div> 

Eine Navigation erstellt man mit der Rolle `navbar`. Am besten geht das wie in vielen nativen Apps in der Fußzeile, damit erhohen wir auch die Usability und nahern uns dem Look & Feel einer nativen App. Verlinkungen zu anderen `page's` erstellt man, indem man einfach die Anchor-Tags auf die jeweilige `page-ID` verlinkt. Mit `data-icon` legt man ein Icon fur die Navigation fest. Das ist nicht zwingend notwendig, erhoht aber die Übersicht. Mit „data-iconpos" wird die Position des Icons festgelegt und wir weisen dem Link der jeweils aktiven Page noch die CSS-Klasse `ui-btn-active` zu. Die Navigationselemente selber stehen in einer Liste, man kann dazu auch Unterlisten anlegen um zum Beispiel breitere und schmalere Elemente erzeugen zu konnen.

![jQuery Mobile - Navbar](http://t3n.de/news/wp-content/uploads/2011/08/IMG_0607-400x600.png)

> _jQuery Mobile - Navbar_

## Dialogboxen mit jQuery Mobile

Um beispielsweise auf Nutzereingaben zu reagieren, bieten sich Dialoge an. Diese konnen entweder aus externen HTML-Dateien bestehen oder auch als eine weitere Page dargestellt werden, mussen aber explizit als Dialog aufgerufen werden. Wie das geht, mochte ich euch an einem Beispiel zeigen.

Als erstes fugen wir unserer Seite eine weitere Page hinzu:
    
    
    <div data-role="page" id="dialog"> <div data-role="header"><h2>Dialogbox</h2></div> <div data-role="content"><p>Inhalt des Dialoges</p>   <a href="#seite1" data-rel="back" data-role="button">Schliessen</a> </div> </div> 

Wir ihr seht, haben wir wirklich nur eine normale Page ohne Footer angelegt, weil wir diesen auch nicht benotigen. Dazu haben wir einen Button angelegt (Buttons bekommen die Rolle `button`) und haben ihm die Beziehung `back` zugewiesen und einen Link zu ersten Seite. Das ist der Befehl zum Schließen des Dialogs. Dann fugen wir auf Seite 1 im `Content`-Bereich einen Button zum Öffnen des Dialogs hinzu:
    
    
    <p><a href="#dialog" data-rel="dialog" data-transition="pop" data-role="button">Dialogbox</a></p>

Hier haben wir einfach nur einen Button mit der Beziehung `Dialog` mit dem Übergang (`transition`) `pop`, dieser Befehl ist ahnlich einer Animation zum Öffnen des Dialogs. Man kann zum Beispiel zwischen `pop`,`slidedown` oder `flip` wahlen.

Öffnet ihr nun den Dialog, konnt ihr diesen auch wieder mit dem Schließen-Button schließen.

![jQuery Mobile - Dialoge](http://t3n.de/news/wp-content/uploads/2011/08/IMG_0606-400x600.png)

> _jQuery Mobile - Dialoge_

## Quellcode und Aussichten

Abschließend hier noch einmal der gesamte Quellcode unserer HTML-Datei:
    
    
     <!DOCTYPE HTML>
     <html>
    
     <head>
    
     <title>Seitentitel </title>
     <meta charset="utf-8">
     <meta name="viewport" content="width=device-width", initial-scale=1>
     <link rel="stylesheet" href="http://code.jquery.com/mobile/1.0b2/jquery.mobile-1.0b2.min.css">
     <script type="text/javascript" src="http://code.jquery.com/jquery-1.6.2.min.js"> </script>
     <script type="text/javascript" src="http://code.jquery.com/mobile/1.0b2/jquery.mobile-1.0b2.min.js"> </script>
    
     </head>
     <body>
     <div data-role="page" id="seite1">
             <div data-role="header"> <h1>test </h1> </div>
             <div data-role="content"> <h3>TEST </h3>
                 <p> <a href="#dialog" data-rel="dialog" data-transition="pop" data-role="button">Dialogbox </a> </p>
             </div>
             <div data-role="footer"> <div data-role="navbar">
             <ul>
                     <li> <a href="#seite1" data-iconpos="top" data-icon="home">Seite1 </a> </li>
                     <li> <a href="#seite2" data-iconpos="top" data-icon="home">Seite2 </a> </li>
             </ul>
             </div> </div>
     </div>
     <div data-role="page" id="seite2">
             <div data-role="header"> <h1>test2 </h1> </div>
             <div data-role="content"> <h3>TEST </h3> </div>
             <div data-role="footer">
             <div data-role="navbar">
             <ul>
                     <li> <a href="#seite1" data-iconpos="top" data-icon="home">Seite1 </a> </li>
                     <li> <a href="#seite2" data-iconpos="top" data-icon="home">Seite2 </a> </li>
             </ul>
             </div>
             </div>
     </div>
         <div data-role="page" id="dialog">
             <div data-role="header"> <h2>Dialogbox </h2> </div>
             <div data-role="content"> <p>Inhalt des Dialoges </p>
                 <a href="#seite1" data-rel="back" data-role="button">Schliessen </a>
             </div>
         </div>
     </body>
     </html>

In den nachsten Ausgaben dieser How-To-Reihe erhaltet ihr Einblicke in die Zusammenarbeit von **jQuery Mobile mit HTML5-Elementen** wie die Geolocation oder Webstorage und wie ihr am Ende aus eurer Web-App mit Hilfe von Phone-Gap eine native App macht.

_Ich hoffe, ihr habt einen guten ersten Eindruck von der Arbeit mit jQuery Mobile bekommen und seht wie relativ einfach es tatsachlich ist, eine mobile Seite mit diesem Framework zu erstellen. Was sagt ihr? Hat jQuery Mobile bereits Einzug in euren Workflow erhalten oder bleibt ihr lieber doch bei Sencha-Touch ?_

**Weiterfuhrende Links zum Thema jQuery Mobile**:

  * [jQuery Mobile 1.0 erschienen](http://t3n.de/news/jquery-mobile-10-erschienen-344042/) \- t3n News November 2011
  * [jQuery-Plugins: 10 Helfer fur schonere Schriften](http://t3n.de/news/jquery-plugins-10-helfer-schonere-schriften-336545/) \- t3n News Oktober 2011

Wir lieben Shop- und Content-Management-Systeme seit uber 12 Jahren und bieten seither erstklassigen und kostenlosen Experten-Support. Jetzt legen wir noch einen drauf: In Webinaren und Telefonaten mit unseren Experten sowie CMS-Choryphaen aus den Communitys erhaltst du bei uns das geballte CMS-Know-how! [ Mehr erfahren!](http://guruads.de/api/click/56372fa1497959ee1600003e)
