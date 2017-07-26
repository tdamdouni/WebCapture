# So programmierst du einen RSS-Reader in 30 Minuten

_Captured: 2015-11-03 at 18:48 from [t3n.de](http://t3n.de/news/programmierst-rss-reader-30-464628/)_

Im Rahmen zweier Tutorials erklare ich, wie man von Grund auf einen kleinen RSS-Reader programmiert - und zwar mit HTML5, CSS3 und WinJS, dem Microsoft-JavaScript-Framework fur Windows 8. Wir werden anschließend eine Windows-RT-App fur den Windows-Store erstellen, die den Gestaltungsprinzipien von Windows-8-UI folgt und Expression Blend 5 verwendet. An und fur sich sollte das Durcharbeiten dieser beiden Artikel in 30 Minuten erledigt sein.

Der erste Artikel erklart das Erstellen des Startbildschirms, der ein WinJS-ListView-Steuerelement verwenden wird. Dieses Element wird alle kurzlich veroffentlichten Blog-Posts durch hubsche Thumbnails anzeigen. Der zweite Artikel geht auf die Detailansicht ein, die ihr nach dem Klick auf einen der Listeneintrage seht. Am Ende des Tutorials findet ihr die fertige Losung zum Download. Betrachtet den Quellcode als hilfreiche, kostenlose Referenz, falls einige Teile des Artikels weiterer Klarung bedurfen.

Voraussetzungen: Um diesen Artikeln folgen zu konnen, musst ihr zuerst Folgendes tun:

Anmerkung: Keine Panik, wenn ihr einen Mac habt. Dank BootCamp funktioniert trotzdem alles perfekt oder ihr konnt es auch in einer virtuellen Maschine, zum Beispiel in Parallels, laufen lassen.

Anmerkung 2: Dieser Artikel wurde am 21. August 2012 uberarbeitet, um die Änderungen in der UI und dem Code zwischen Windows 8 Release Preview und RTM zu berucksichtigen. Wollen Sie eine eigene Anwendung von der Release Preview migrieren, sollten Sie dieses Dokument lesen: „[braking changes document ](http://go.microsoft.com/fwlink/p/?LinkID=258744)". In unserem Fall waren lediglich Teile betroffen, die mit der neuen UI und Benennungen in Visual Studio zu tun hatten.

Anmerkung 3: Ich habe noch einen extra Beitrag veroffentlicht, der [WordPress](http://t3n.de/tag/entwicklung) und Community gewidmet ist: „[Windows 8 HTML5 Metro Style App: RSS reader in 30min - building your WordPress version ](http://blogs.msdn.com/b/davrous/archive/2012/07/06/windows-8-html5-metro-style-app-rss-reader-in-30min-the-wordpress-version.aspx)"

Hier ist ein kurzer Überblick des Inhalts des ersten Teils:

  * Schritt 1: Eine leere Anwendung erstellen
  * Schritt 2: Das HTML & CSS Grundgerust unserer Hauptseite erstellen
  * Schritt 3: Erster Kontakt mit Blend
  * Schritt 4: Daten mit XHR laden und diese an das ListView-Steuerelement binden
  * Schritt 5: Ein Template benutzen und das Design mit Blend verandern
  * Schritt 6: Quellcode zum Herunterladen

Beachtet bitte: Diese Tutorials basieren auf der BUILD-Session „[Tools for building Metro style apps ](http://channel9.msdn.com/events/BUILD/BUILD2011/BPS-1006)" mit Chris Sell und Kieran Mockford. Ich habe den Inhalt lediglich fur Windows 8 RTM aktualisiert.

## Schritt 1: Eine leere Anwendung erstellen

Ruft Visual Studio 2012 auf, geht auf File -> New Project und erstellt ein neues JavaScript -> Windows Store -> Blank-App-Projekt:

![BU fehlt](http://t3n.de/news/wp-content/uploads/2013/05/neues-projekt-595x370.jpg)

> _BU fehlt_

Benennt euer Projekt „SimpleChannel9Reader", da wir den RSS-Feed aus dem Coding4Fun-Bereich auf Channel9 herunterladen werden. Hier ist die URL: [http://channel9.msdn.com/coding4fun/articles/RSS ](http://channel9.msdn.com/coding4fun/articles/RSS)

## Schritt 2: Das HTML & CSS Grundgerust unserer Hauptseite erstellen

Öffnet die Datei „default.html". Sie beschreibt die erste Seite , die beim Start der Anwendung angezeigt wird. Anstelle des folgenden HTML-Teils:
    
    
    <p>Content goes here</p>

Fugt ihr diesen Teil ein:
    
    
    <div id="main">
        <header id="banner">
            <button id="backbutton"></button>
            <h1 id="maintitle">Welcome to Channel 9!</h1>
        </header>
        <section id="content"></section>
    </div>

Wir haben jetzt einen globalen <div>-Container mit der ID „main" und zwei inneren Containern genannt „banner" und „content". Der <header> wird naturlich oben auf der Seite dargestellt und die <section> mit dem Inhalt direkt darunter. Lasst uns hierzu ein wenig CSS hinzufugen, indem wir die Datei „default.css" offnen, die im „css"-Ordner liegt. Ihr werdet sehen, dass es schon einige vordefinierte CSS-Regeln gibt, um die verschiedenen verfugbaren Windows-8-Ansichten uber Media Queries zu formatieren. In diesen beiden Artikeln konzentriere ich mich auf die "fullscreen-landscape"-Ansicht. Also springt direkt zu diesem Bereich und fugt das folgende CSS ein:
    
    
    #main {
        width: 100%;
        height: 100%;
    }
    
    #banner {
        width: 100%;
        height: 100%;
    }
    
    #backbutton {
    }
    
    #maintitle {
    }
    
    #content {
        width: 100%;
        height: 100%;
    }

Dies sorgt dafur, dass der verfugbare Platz fur die drei Hauptcontainer verwendet wird.

Lasst eure Anwendung laufen, indem ihr die F5-Taste druckt oder auf den folgenden Button klickt:

Ihr solltet nun dieses Bild sehen:

![Erste Ausführung des Programms](http://t3n.de/news/wp-content/uploads/2013/05/erste-ausfuehrung.jpg)

> _Erste Ausfuhrung des Programms_

Und ihr solltet auch ein offensichtliches Gestaltungsproblem erkennen: Der Zuruck-Button und der Titel sind nicht nebeneinander angeordnet. Losen lasst sich das Problem mit Blend 5!

## Schritt 3: Erster Kontakt mit Blend

Startet Blend und geht zum Ordner, wo sich euer SimpleChannel9Reader-Projekt befindet. Blend wird dann Folgendes anzeigen:

![Die Anwengund in Blend](http://t3n.de/news/wp-content/uploads/2013/05/blend-595x319.jpg)

> _Die Anwengund in Blend_

Das Ziel ist, zwei Raster (Grid) zu erstellen. Das erste ist fur den main-Container. Es umfasst eine Spalte, die die volle Breite einnimmt sowie zwei Zeilen. Das zweite Raster ist definiert durch eine Zeile und zwei Spalten fur den Zuruck-Button und den Titel.

Beginnen wir mit der Auswahl des main-Elements, indem wir das Live-DOM-Fenster verwenden:

![](http://t3n.de/news/wp-content/uploads/2013/05/live-dom-fenster.jpg)

> _"Live DOM"-Fenster_

Geht zu "CSS Properties", wahlt die #main-Regel im Layout-Fenster aus und andert den Wert fur display auf „-ms-grid":

![CSS-properties-Fenster](http://t3n.de/news/wp-content/uploads/2013/05/css-properties.jpg)

Wir werden die CSS-Grid-Layout-Spezifikation verwenden, die zurzeit nur vom IE10 unterstutzt wird, aber bald auch von anderen Browsern beherrscht werden sollte. Wenn ihr mehr uber die Art von Layout erfahren wollt, die im Metro-Mode unterstutzt wird, konnt ihr diesen Artikel lesen: [Choosing a CSS3 layout for your app ](http://msdn.microsoft.com/en-us/library/windows/apps/hh465327.aspx).

Wenn ihr die Moglichkeiten in der CSS3-Grid-Spezifikation entdecken wollt, dann spielt ein wenig mit dieser IE Test Drive Demo: [Hands On: CSS3 Grid Layout ](http://ie.microsoft.com/testdrive/Graphics/hands-on-css3/hands-on_grid.htm)

Nach dem Zuweisen des notwendigen grid-Werts zur Eigenschaft display mussen wir nun unser Raster definieren. Springt hierfur zu dem Bereich „Grid" und setzt die folgenden Eigenschaften:

Wir werden eine einzige Spalte uber die gesamte Breite des Displays (was auch immer die Auflosung sein wird) und zwei Zeilen haben. Die erste Zeile wird eine feste Hohe von 132px haben und die andere wird die restliche verfugbare Hohe einnehmen. Ihr konnt dies in der Blend-Designeroberflache sehen:

![Blend-Designeroberfläche](http://t3n.de/news/wp-content/uploads/2013/05/blend-designeroberfläche-595x366.jpg)

Nun werden wir das content-Element in die zweite Zeile packen. Wahlt dazu im „Live DOM" aus, klickt auf die #content-Regel und geht dann zu dessen Grid-Eigenschaften. Ändert den Wert von „-ms-grid-row" auf 2. Ihr konnt auch das banner-Element in die Zeile 1 packen; dies ist ohnehin die Voreinstellung, auch wenn ihr es nicht ausdrucklich setzt.

Nun werden wir unsere erste Zeile in zwei Spalten teilen, um jedes der beiden Elemente an seinen richtigen Platz zu setzen. Wahlt das banner-Element aus, andert seine display-Eigenschaft auf „-ms-grid" und definiert eine 1fr breite Zeile und zwei Spalten, die erste 120px breit und die zweite 1fr:

Setzt das maintitle-Element in die Spalte 2 und zentriert es vertikal, indem ihr die Eigenschaft „-ms-grid-row-align" auf center stellen:

![Grid-Fenster 3](http://t3n.de/news/wp-content/uploads/2013/05/grid-fenster-3.jpg)

> _Grid-Fenster 3_

Wahlt das backbutton-Element aus und geht zum Layout-Teil. Setzt den oberen Abstand (top margin) auf 54px und den linken Abstand (left margin) auf 40 px. Wenn ihr bisher nichts vergessen habt, solltet ihr jetzt Folgendes auf der Designoberflache sehen:

![Blend-Designoberfläche 2](http://t3n.de/news/wp-content/uploads/2013/05/blend-designoberflaeche-2-595x357.jpg)

> _Blend-Designoberflache 2_

Speichert alle Änderungen mit File -> Save All und kehrt zu Visual Studio zuruck. Öffnet die Datei „default.css" und ihr werdet sehen, dass Blend bei den richtigen CSS-Regeln einige „saubere" Erganzungen vorgenommen hat:
    
    
    @media screen and (-ms-view-state: fullscreen-landscape)
    {
    
        #main {
            width: 100%;
            height: 100%;
            display: -ms-grid;
            -ms-grid-columns: 1fr;
            -ms-grid-rows: 132px 1fr;
        }
    
        #banner {
            width: 100%;
            height: 100%;
            display: -ms-grid;
            -ms-grid-columns: 120px 1fr;
            -ms-grid-rows: 1fr;
        }
    
        #backbutton {
            margin-top: 54px;
            margin-left: 40px;
        }
    
        #maintitle {
            -ms-grid-column: 2;
            -ms-grid-row-align: center;
        }
    
        #content {
            width: 100%;
            height: 100%;
            -ms-grid-row: 2;
        }
    }

Checkt kurz, ob die Anwendung wie erwartet funktioniert, indem ihr einfach F5 druckt.

[Weiter auf Seite 2: „Schritt 4: Daten mit XHR laden und diese an das ListView-Steuerelement binden" »](http://t3n.de/news/programmierst-rss-reader-30-464628/2/)

Wir lieben Shop- und Content-Management-Systeme seit uber 12 Jahren und bieten seither erstklassigen und kostenlosen Experten-Support. Jetzt legen wir noch einen drauf: In Webinaren und Telefonaten mit unseren Experten sowie CMS-Choryphaen aus den Communitys erhaltst du bei uns das geballte CMS-Know-how! [ Mehr erfahren!](http://guruads.de/api/click/56372fa1497959ee1600003e)

  


## Schritt 4: Daten mit XHR laden und diese an das ListView-Steuerelement binden

Nun geht's an den Programmcode: Als erstes mussen wir das Steuerelement einfugen, das die Thumbnails unserer Artikel auf dem Startbildschirm anzeigt. Wir werden hierzu WinJS verwenden.

Die WinJS Library oder „Microsoft Windows Library for JavaScript SDK" hilft JavaScript-Entwicklern beim Umgang mit der neuen UI von Windows 8. Es stellt eine Reihe von Steuerelementen zur Verfugung, eine Templating-Engine, eine Binding-Engine, Promises um asynchrone JavaScript-Aufrufe zu verarbeiten, Hilfsfunktionen die sich um Namensraume kummern und so weiter.

Mehr Details uber die Steuerelemente finden sich in diesem Artikel: „[Quickstart: adding WinJS controls and styles ](http://msdn.microsoft.com/en-us/library/windows/apps/hh465493)".

In Windows-Store-Projekten findet ihr die WinJS Library im „Solution Explorer" unter References.

![Solution-Explorer](http://t3n.de/news/wp-content/uploads/2013/05/solution-explorer.jpg)

Darunter werdet ihr die Standard-Stylesheets mit den zwei dunklen und einem hellen Theme sehen sowie den Javascript-Code. Das Studieren des Codes lohnt sich auf jeden Fall, man kann dadurch immer etwas lernen.

In unserem Fall werden wir das ListView-Steuerelement verwenden, das zur Anzeige der Elementliste ein Raster-Layout erstellt.

Öffnet die Datei „default.html" und fugt diese HTML-Zeile in den <section>-Tag ein:
    
    
    <div id="articlelist" data-win-control="WinJS.UI.ListView"></div>

Momentan ist es nur ein einfacher, klassischer <div>. In ihm ist jedoch bereits das Attribut data-win-control gesetzt. Dies deutet an, dass wir die WinJS-Library benutzen mochten, um diesen einfachen <div> in ein JavaScript-ListView-Steuerelement umzuwandeln.

Dies wird ausgefuhrt mithilfe einer Zeile JavaScript-Code, die ihr in der „default.js" finden konnt:
    
    
    WinJS.UI.processAll();

Diese asynchrone Funktion verarbeitet die gesamte DOM-Struktur, um Elemente zu finden, die mit dem Attribut „data-win-control" markiert sind und wandelt diese in echte WinJS-Steuerelemente um. Fur den [Entwickler](http://t3n.de/tag/entwicklung) bedeutet das den einfachen Zugang zur neuen Windows-8-UI. Wenn ihr diese Zeile aus Versehen loscht, wandeln sich alle eure <div>-Elemente wieder zuruck in einen einfachen <div>-Tag.

Nun mussen wir diesen ListView mit Daten des RSS-Feeds futtern. Fugt dazu in der bind-Funktion zum Event „onactivated" direkt oberhalb der processAll()-Zeile folgenden Code ein:
    
    
    articlesList = new WinJS.Binding.List();
    var publicMembers = { ItemList: articlesList };
    WinJS.Namespace.define("C9Data", publicMembers);

Nun musst ihr die Variable "articlesList" am Anfang der Funktion deklarieren, zum Beispiel gleich nach der Variable "app".

Wir deklarieren hier eine Variable vom Typ Binding.List(). Diesen Typen benutzen wir, um eure Daten an die WinJS-Steuerelemente zu binden. Er enthalt beispielsweise einige Methoden, die euch helfen werden, einige Daten im Hintergrund hinzuzufugen und dank des Binding-Mechanismus spiegeln sich diese Änderungen automatisch in der Ansicht wider.

Daruberhinaus ist euch vielleicht aufgefallen, dass wir sauberen JavaScript-Code verwenden, indem wir moderne Muster anwenden, wie das "Modulmuster". Hierfur haben wir eine anonyme selbst-ausfuhrende JS Funktion in „default.js". Dann mussen wir einen Weg finden, um offentliche (public) Daten fur externe Funktionen verfugbar zu machen. Deswegen implementieren wir Namensraume fur die entsprechenden WinJS-Hilfsfunktionen. Dadurch konnen wir ganz einfach definieren, was wir verfugbar machen wollen. In unserem Fall werden wir ein offentliches (public) Objekt namens "C9Data" verfugbar machen, das eine ItemList-Eigenschaft besitzt, die wiederum unsere spater anzuzeigenden Elemente enthalt.

Jetzt brauchen wir eine Funktion, die sich die Daten vom RSS-Feed holt, sie verarbeitet und on-the-fly ein paar JS-Objekte erstellt, um sie in die beruhmte Binding-Liste zu schieben:
    
    
    function downloadC9BlogFeed() {
        WinJS.xhr({ url: "http://channel9.msdn.com/coding4fun/articles/RSS" }).then(function (rss) {
    
        });
    }

Diese Funktion beginnt damit, einen asynchronen XmlHttpRequest zu der angegebenen URL zu senden. Der Code, der in der Promise (dem .then()-Teil) definiert ist, wird dann ausgefuhrt - aber nur, wenn der Request abgeschlossen und die Daten erhalten wurden. An dieser Stelle mussen wir dann die Daten filtern, indem wir den folgenden Code in die anonyme Funktion einfugen:
    
    
    var items = rss.responseXML.querySelectorAll("item");
    
    for (var n = 0; n < items.length; n++) {
        var article = {};
        article.title = items[n].querySelector("title").textContent;
        var thumbs = items[n].querySelectorAll("thumbnail");
        if (thumbs.length > 1) {
            article.thumbnail = thumbs[1].attributes.getNamedItem("url").textContent;
            article.content = items[n].textContent;
            articlesList.push(article);
        }
    }

Ich hoffe, dieser Code ist selbsterklarend. Er sucht alle item-Knoten, greift auf ihre interessanten Eigenschaften zu, um diese auf ein article-Objekt abzubilden, das on-the-fly mit den Eigenschaften title, thumbs und content erstellt wird. Bitte merkt euch die Namen dieser Eigenschaften; wir werden sie spater wieder verwenden. Zum Schluss fugt die Funktion das neue Objekt der Binding-Sammlung hinzu.

Jetzt mussen wir diese Funktion wahrend der Startphase unserer Anwendung aufrufen. Dieser Code sollte nur nach dem Verarbeiten der DOM-Struktur ausgefuhrt werden, um die WinJS-Steuerelemente zu erstellen:
    
    
    WinJS.UI.processAll().then(downloadC9BlogFeed);

Wir mussen dem Steuerelement seine Datenquelle ubergeben. Springen wir also zuruck zum HTML-Code und andern die Optionen des <div>, der dem ListView-Element entspricht:
    
    
    <div id="articlelist" data-win-control="WinJS.UI.ListView" 
     data-win-options="{ itemDataSource: C9Data.ItemList.dataSource }"></div>

Zum Schluss benotigen wir noch ein wenig grundlegendes CSS, damit das Steuerelement weiß, wie es jeden seiner Eintrage formatieren soll. Geht also zur Datei „default.css" und fugt diese beiden Regeln hinzu:
    
    
    #articlelist {
        width: 100%;
        height: 100%;
    }
    
    #articlelist .win-item {
        width: 150px;
        height: 150px;
    }

Das CSS beschreibt, dass unser ListView-Steuerelement den ganzen verfugbaren Platz in seinem Container in Anspruch nehmen soll und dass jeder seiner Eintrage (durch die „.win-item"-Klasse) 150px mal 150px groß sein soll.

Fuhrt den Code durch Drucken von F5 aus. Ihr werdet etwas sehen, dass so hasslich ist, wie das hier:

![Die Anwendung nach Schritt 4](http://t3n.de/news/wp-content/uploads/2013/05/anwendung-nach-schritt-4-595x334.jpg)

> _Die Anwendung nach Schritt 4_

Aber keine Sorge, der hassliche Output ist das zu erwartende Verhalten. Wir haben noch ein bisschen Designarbeit vor uns. Aber ihr konnt bereits sehen, dass das Binding korrekt ist und dass die Bedienung des Steuerelements sowohl per Touch als auch mit Mausklicks ordnungsgemaß funktioniert. Daruberhinaus passt sich die Großenverteilung des Steuerelements automatisch an samtliche Auflosungen an. In diesem Fall werdet ihr nicht das exakt selbe Layout (Anzahl der angezeigten Spalten und Zeilen) zu sehen bekommen, wie oben im Bild dargestellt.

## Schritt 5: Ein Template benutzen und das Design mit Blend verandern

Jetzt musst ihr die Darstellung der Elemente andern. Genau das ist der Zweck einer Template-Engine. Ein Template ist nichts Anderes als ein wenig HTML, das mit einigen WinJS-Attributen versehen ist.

Geht zur „default.html"-Seite und fugt das folgende HTML direkt uber dem main-Teil ein:
    
    
    <div id="C9ItemTemplate" data-win-control="WinJS.Binding.Template" style="display: none;">
        <div>
            <div>
                <img data-win-bind="src: thumbnail" />
            </div>
            <div data-win-bind="innerText: title"></div>
        </div>
    </div>

Es ist ein HTML-Template, markiert mit dem Wert „WinJS.Binding.Template". Dies wird WinJS beim Umgang mit diesem speziellen HTML-Teil nach dem Ausfuhren von processALL() helfen. Ihr werdet auch den Einsatz von „data-win-bind" bemerkt haben. Hiermit werden Ausdrucke definiert, die der Binding-Engine sagen, welche JavaScript-Eigenschaften von der Datenquelle auf welchen HTML-Knoten abgebildet werden sollen. Der Rest ist ganz normaler HTML-Code.

Nun mussen wir das WinJS-Steuerelement so konfigurieren, dass es nicht mehr das Standard-Template verwendet, sondern das neue oben gezeigte Template. Dazu andert man einfach die Optionen:
    
    
    <div id="articlelist" data-win-control="WinJS.UI.ListView" 
     data-win-options="{ itemDataSource: C9Data.ItemList.dataSource, itemTemplate: C9ItemTemplate }"> 
    </div>

Wenn ihr die Anwendung jetzt laufen lasst, solltet ihr folgendes sehen:

![Die Anwendung in Schritt 5](http://t3n.de/news/wp-content/uploads/2013/05/anwendung-in-schritt-5-595x334.jpg)

> _Schon besser, aber wir sind noch nicht fertig. Um das Design noch weiter zu verfeinern holen wir wieder Blend zu Hilfe._

Gehen wir also zuruck zu Blend. Blend wird euch bitten, alle Änderungen, die ihr in Visual Studio vorgenommen habt, neu zu laden. Sobald Sie das getan haben, seht ihr folgendes:

![Blend nach dem Import der Änderungen aus Visual Studio](http://t3n.de/news/wp-content/uploads/2013/05/blend-nach-import-595x319.jpg)

> _Blend nach dem Import der Änderungen aus Visual Studio_

Ihr seid nicht uberrascht? Das solltet ihr aber sein. Denn ihr seht tatsachlich die selbe visuelle Darstellung, die nach dem Drucken von F5 in Visual Studio zu sehen ist. Das bedeutet, dass Blend den JavaScript-Teil eurer Anwendung innerhalb des Designers dynamisch ausfuhrt. Das ist eine erstaunliche Funktion.

Dank dieser Fahigkeit konnt ihr direkt mit echten Daten arbeiten. Ihr musst also anstelle der echten Daten nicht erst mit „Pseudoinhalten" gestalten. Das ist das Coole an JavaScript. Blend ist in der Lage, den JS-Code auszufuhren, der die XHR-Anfrage absetzt und die WinJS-Objekte zu erstellen.

Unter „default.css" konnen wir jetzt noch zwei neue CSS-Regeln hinzufugen. Klickt auf den +-Button des Haupt-Media-Query:

![Eine neue CSS-Regel hinzufügen](http://t3n.de/news/wp-content/uploads/2013/05/neue-css-regel.jpg)

> _Eine neue CSS-Regel hinzufugen_

Und fugt diese neuen Selektoren hinzu:
    
    
    .listItemTemplate
    
    
    .listItemTemplate img

Wahlt die Regel #articlelist .win-item, die jedes Element im ListView hervorhebt, welches die ID "articlelist" hat.

Ändert die Große dieser Elemente von 150px mal 150px auf 250px mal 250px. Ihr braucht dazu nur in der rechten Leiste in den Sizing-Bereich gehen.

Das Layout sollte dynamisch aktualisiert werden. Wenn nicht, konnt ihr ein Aktualisieren des Designs forcieren, indem ihr auf den dafur vorgesehenen Button klickt:

Und hier ist das Ergebnis, das ihr sehen solltet:

![Die Anwendung nach dem Design-Änderungen](http://t3n.de/news/wp-content/uploads/2013/05/anwendung-nach-design-aenderungen-595x363.jpg)

> _Die Anwendung nach dem Design-Änderungen_

Jetzt werden wir die Große der Bilder im Template andern. Verwendet hierzu das Auswahl-Werkzeug (Pfeil) und klickt auf eines der Bilder:

![Die Größe der Bilder ändern](http://t3n.de/news/wp-content/uploads/2013/05/bildgroesse-aendern-595x219.jpg)

> _Die Große der Bilder andern_

Ihr konnt die aktuell angewendeten CSS-Regeln im Bereich „Applied Rules" sehen. Klickt auf „.listItemTemplate img" und verandert mit der Maus die Große des momentan ausgewahlten Bildes. Alle anderen Bilder, die vom selben Selektor angesprochen werden, werden sich dann dynamisch in Echtzeit mitverandern. Die passende Große in diesem Fall erzielt ihr durch Eingabe von 234px Breite und 165px Hohe im Sizing-Bereich.

Um das Design noch ein wenig zu verbessern, brauchen wir noch mehr Abstand zwischen den einzelnen Elementen und wir wollen unser ListView-Steuerelement am Titel ausrichten.

Klickt auf den Selektor „.listItemTemplate", dann geht zum Layout-Bereich und klickt auf das Lock-Symbol (Sperrschloss) rechts neben dem Margin-Bereich. Wahlt irgendeinen Abstand, dann tippt 8px ein.

Um das Raster des ListView-Steuerelements am Titel auszurichten, mussen wir ihn schließlich noch 120px von links einrucken, minus 8px, wegen des Element-Abstands, den wir gerade gesetzt haben.

Druckt dazu wieder den +-Button, fugt noch einen neuen Selektor hinzu und nennt ihn „.win-surface". Setzt einen linken Abstand (margin) von 112px.

Kehrt zuruck zu Visual Studio, akzeptiert die vorgenommenen Änderungen und druckt F5. Jetzt solltet ihr das folgende Layout sehen:

![Die Anwendung nach Schitt 5](http://t3n.de/news/wp-content/uploads/2013/05/anwendung-nach-schritt-5-595x334.jpg)

> _Die Anwendung nach Schitt 5_

## Schritt 6: Quellcode zum Herunterladen

Wir haben große Fortschritte gemacht. Jetzt mussen wir nur noch die Details eines Artikels anzeigen, um sowohl weitere Fahigkeiten von Blend zu demonstrieren, als auch einige neue coole CSS3-Funktionen. Ihr konnt den kompletten Quellcode zu den in diesem ersten Artikel besprochenen Losungen hier herunterladen: [Simple Channel9 Reader Article1 ](http://david.blob.core.windows.net/win8/SimpleChannel9ReaderArticle1.zip)

Lest weiter im nachsten Artikel zum Thema: [Windows 8 HTML5 WinRT App: Wie man einen kleinen RSS-Reader in 30 Minuten erstellt. (Teil 2/2) ](http://blogs.msdn.com/b/davrous/archive/2012/05/14/windows-8-html5-metro-style-app-how-to-create-a-small-rss-reader-in-30min-part-2-2.aspx)

### Weiterfuhrende Links

### Über den Autor

David Rousset arbeitet bei [Microsoft](http://t3n.de/tag/microsoft) Frankreich als „Windows 8 & HTML5 Microsoft Developer Evangelist". Sein Twitter-Profil findet ihr unter [@davrous ](http://twitter.com/davrous).

Wir lieben Shop- und Content-Management-Systeme seit uber 12 Jahren und bieten seither erstklassigen und kostenlosen Experten-Support. Jetzt legen wir noch einen drauf: In Webinaren und Telefonaten mit unseren Experten sowie CMS-Choryphaen aus den Communitys erhaltst du bei uns das geballte CMS-Know-how! [ Mehr erfahren!](http://guruads.de/api/click/56372fa1497959ee1600003e)
