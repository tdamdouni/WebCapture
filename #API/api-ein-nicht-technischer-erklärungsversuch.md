# API - Ein nicht-technischer Erklärungsversuch

_Captured: 2018-01-30 at 11:32 from [www.gruenderszene.de](https://www.gruenderszene.de/allgemein/web-apis-ein-nicht-technischer-erklarungsversuch)_

![stecker](https://cdn1.gruenderszene.de/wp-content/uploads/2009/11/stecker_1220x814_oc.jpg)

> _APIs als Grundstein der Softwareentwicklung_

APIs sind der Grundstein der Softwareentwicklung und spatestens seit dem Aufkommen des Web 2.0 auch vielen Nicht-Technikern ein Begriff geworden. Doch da hort es oft auf. Was steckt wirklich hinter dem Begriff? Was genau sind APIs, und welche Bedeutung haben sie im Web? Dieser Artikel ist ein praxisnaher Erklarungsversuch und eine Zusammenfassung fur alle Uneingeweihten, um kunftig selbstbewusst mitreden und -entscheiden zu konnen.

Wahrend die meisten noch wissen, dass sich hinter der Abkurzung „API" der englischsprachige Begriff „Application Programming Interface" (Programmierschnittstelle) verbirgt, so stapfen Nicht-Techniker dahinter meist arg im Dunkeln. Sowohl diese Tatsache, als auch die inflationare und falsche Nutzung des Begriffs uber die letzten Jahre mogen Ursache dafur sein, dass er zu einem waschechten Buzzword herangewachsen ist.

So wurden Web APIs zeitweise als Allheilmittel und Geheimwaffe einer jeden Website bepriesen, galten zu Web-2.0-Hochzeiten gar als einer jener Punkte auf dem Businessplan, die die Unternehmensbewertung um einige signifikante Prozente nach oben steigern konnte.

Nachdem sich diese anfangliche Euphorie mittlerweile etwas gelegt hat, werden wir hier nun mit Geruchten und Legenden aufraumen, die wahren Chancen und Risiken aufzeigen und fur etwas Durchblick im Dickicht der APIs sorgen.

## **Sinn und Zweck von Web APIs**

Obwohl wir weiter unten zwischen verschiedenen Arten von APIs zu differenzieren lernen, haben sie doch alle eins gemein: Sie dienen zum Austausch und der Weiterverarbeitung von Daten und Inhalten zwischen verschiedenen Websites, Programmen und Anbietern, und ermoglichen so Dritten den Zugang zu vorher verschlossenen Datenpools und Benutzerkreisen. Durch die gemeinsame Nutzung dieser Inhalte konnen so ganz neue Dienste (zum Beispiel Desktop-Clients), Mehrwerte (wie [Mash-Ups](http://de.wikipedia.org/wiki/Mashup_%28Internet%29)) oder gar ganze Ökosysteme - wie [Application Stores](http://de.wikipedia.org/wiki/App_Store) - entstehen.

## **Grundlagen**

Wie es dem Begriff bereits zu entnehmen ist, handelt es sich bei APIs ganz grundsatzlich um [Schnittstellen](http://de.wikipedia.org/wiki/Schnittstelle). Eine Schnittstelle ermoglicht die Kommunikation und Interaktion zwischen zwei Systemen. Nahezu alles in unserer Welt besteht aus Schnittstellen: Stecker und Buchse dienen als Schnittstelle zur Übertragung von Strom, Tastatur und Finger bei der Benutzung eines Computers zur Übertragung von Gedanken in digitale Zeichen.

Auch in der Computerwelt wimmelt es nur so von Schnittstellen und APIs - sie bilden seit jeher den Grundstein von Betriebssystemen und Programmen. Wenn jedoch in Internetkreisen von APIs geredet wird, sind meistens sogenannte Webservice APIs oder Web APIs gemeint, also Schnittstellen fur und von Websites und Webapplikationen. Obwohl wir uns in diesem Artikel vorrangig auf Web APIs beziehen, sind die meisten allgemeinen Fakten jedoch auch traditionellen APIs gemein.

## **User Interface vs. Application Programming Interface**

Bei Websites und Programmen dient die visuelle Oberflache, das sogenannte (Graphical) [User Interface](http://de.wikipedia.org/wiki/Benutzerschnittstelle) oder auch Frontend, als Schnittstelle zwischen dem Benutzer und der dahinterliegenden Softwarelogik, dem [Backend](http://de.wikipedia.org/wiki/Frontend_und_Backend). Das User Interface nimmt also Daten vom Benutzer entgegen, leitet diese zur Verarbeitung an die Software weiter, und gibt anschließend das Resultat wieder an den Benutzer zuruck.

Der Begriff des User Interface ist langst nicht nur unter Technikern weit verbreitet und bekannt - er gilt als der allgemein bezeichnende Begriff fur das Gesicht und die Oberflache einer Software. Es wird dabei im Detail designed, im Web mittels Technologien wie HTML, CSS oder Flash umgesetzt und auf Usability hin optimiert. Jede im Browser dargestellte Website ist also zunachst ein User Interface, uber das die Benutzer mit der eigentlichen Software interagieren.

![api-vs-ui](https://www.gruenderszene.de/wp-content/uploads/2009/11/api-vs-ui.png)

Das Äquivalent zum fur Menschen optimierten (menschenlesbaren) User Interface sind nun die fur Software zugeschnittenen (maschinenlesbaren) Application Programming Interfaces, die im Grunde genommen einen klarer abstrahierten und strukturierten Zugriff auf die Funktionen des Backends ermoglichen. Daruber konnen Daten beispielsweise in einer besonders gut weiterverarbeitbaren und reduzierten Form ausgetauscht werden.

## **API-Design und Standards**

Das alles bedeutet auch: Ebenso wie wir das Design einer Website entwerfen und gestalten, muss auch eine API konzipiert und gestaltet werden. Und da die Schnittstelle letztendlich zunachst von einem Menschen (einem Programmierer) implementiert und getestet werden muss, mussen wir optimalerweise auch noch eine fur Menschen (oder zumindest fur Programmierer) verstandliche Dokumentation beilegen.

Insbesondere die drei letzteren Aspekte sind bereits durch eine handvoll etablierte Standards, sogennante Protokolle, definiert und standardisiert, aus denen man als API-Designer wahlen sollte.

Zur Standardisierung der allgemeinen Struktur gibt es Protokolle wie [SOAP](http://de.wikipedia.org/wiki/SOAP), [XML-RPC](http://de.wikipedia.org/wiki/XML-RPC) oder [REST](http://de.wikipedia.org/wiki/Representational_State_Transfer), die die Struktur - von links nach rechts - je nach Wahl strikt bis weniger strikt vorgeben. Wahrend also SOAP ein sehr komplexer Standard ist, bietet das einfachere REST mehr Gestaltungsfreiraum. Aus diesem Grund gilt SOAP als Standard im Enterprise-Umfeld, wahrend REST den Markt der offentlichen Web APIs dominiert.

Fur das Datenformat schließlich kommen meist Standards wie [XML](http://de.wikipedia.org/wiki/XML) oder [JSON](http://de.wikipedia.org/wiki/JSON) zum Einsatz. Um wieder den Vergleich zu Websites zu ziehen: Sie stellen letztendlich das API-Äquivalent zu HTML dar.

## **Zur Differenzierung von Web APIs**

Nachdem die Grundlagen geklart sind, ist es sinnvoll zwischen verschiedenen Formen von Web APIs zu unterscheiden, um die dahinterliegenden Aspekte besser zu verstehen. In diesem Artikel unterscheiden wir zwischen vier verschiedenen Arten von Web APIs:

  * Interne APIs
  * Externe APIs
  * Plattform-APIs
  * Authentifizierungs- und Autorisierungs-APIs

**Interne APIs - Modularisierung und SOA**

![soa](https://www.gruenderszene.de/wp-content/uploads/2009/11/soa.png)

Streng genommen ist in der Welt der Softwareentwicklung fast alles eine interne API. Je klarer die Abgrenzung von Code gegenuber anderen Modulen stattfindet, desto eher ist von einer wirklichen Schnittstelle zu reden. Interne APIs gehoren zum guten Ton professioneller Softwareentwicklung und finden Einsatz, um Komponenten und Module der Software einerseits voneinander abzugrenzen und andererseits wieder miteinander zu verbinden. Das steigert die Modularitat und verringert dadurch die Gesamtkomplexitat.

Sogenannte Service-Orientated Architectures ([SOA](http://de.wikipedia.org/wiki/Serviceorientierte_Architektur)) gehen besonders weit, indem sie das Gesamtsystem in moglichst viele einzelne, unabhangige Teil-Systeme (Services) zerlegen, die untereinander zum Beispiel uber Webservice APIs kommunizieren.

Gute Beispiele fur ausgepragte Modularisierung abseits der Softwareindustrie sind zum Beispiel in den Automobil- und PC-Industrien zu finden, die dafur mit vielfaltigen Arbeitsteilungs-, Outsourcing- und Kombinationsmoglichkeiten belohnt werden.

## **Externe APIs - zum Beispiel Twitter, Flickr, YouTube**

![externe-api](https://www.gruenderszene.de/wp-content/uploads/2009/11/externe-api.png)

Wenn ganz allgemein von APIs geredet wird, sind meist externe APIs gemeint. Analog zur Darbietung bestimmter Funktionen gegenuber dem Benutzer uber das User Interface, konnen diese und andere Funktionen auch uber eine externe API ausgefuhrt werden. Das ist besonders interessant, um Inhalte weiterzuverarbeiten und Mash-Ups zu entwickeln. Ein typisches Beispiel ist das Versenden von Tweets uber Desktop-Anwendungen wie TweetDeck, wo die [externe Twitter-API ](http://apiwiki.twitter.com/)zum Einsatz kommt.

Bekannte Beispiele fur externe Web APIs neben Twitter sind auch die von [Flickr](http://www.flickr.com/services/api/) oder [YouTube](http://code.google.com/intl/de-DE/apis/youtube/overview.html). Mit diesen konnen die Inhalte der Websites automatisiert ausgelesen, hinzugefugt oder verandert werden, was sich heute in [unzahligenen frei verfugbaren Tools](http://www.flickrbits.com/) außert.

## **Plattform-APIs - zum Beispiel Facebook, OpenSocial**

![plattform-api](https://www.gruenderszene.de/wp-content/uploads/2009/11/plattform-api.png)

Plattform-APIs bieten Schnittstellen zur Integration in eine andere Website oder Plattform. Damit konnen Dritte Applikationen oder Plug-Ins entwickeln und diese im Rahmen der Plattform betreiben. Hierzu bietet eine Plattform-API inbesondere Funktionen, mit denen das User Interface einer entwickelten Application in das User Interface der Plattform integriert werden kann, aber auch bestimmte Funktionen zum Zugriff auf Benutzerdaten (zum Beispiel den Namen des eingeloggten Nutzers oder die seiner Freunde) oder andere zentrale Funktionen der Plattform.

Bekannte Beispiele aus der Web-Welt sind die [API von Facebook](http://developers.facebook.com/) oder der [OpenSocial-Standard](http://code.google.com/intl/de-DE/apis/opensocial/) fur Plattform-APIs. Solche Websites werden auch als „[Platform-Enabled Websites"](http://en.wikipedia.org/wiki/Platform-enabled_website) bezeichnet. Aber auch iPhone-, Android-, Windows-, Linux- oder Mac-Applikationen sind nur durch die Öffnung von Plattform-APIs moglich.

## **Authentifizierungs- und Autorisierungs-APIs**

Weiterhin gibt es noch einen Sondertyp von Web APIs, die immer starker an Bedeutung gewinnen: Schnittstellen zur [Authentifizierung](http://de.wikipedia.org/wiki/Authentifizierung) (Identifikation) und [Autorisierung](http://de.wikipedia.org/wiki/Autorisierung) (Zugriffsrechtsgewahrung) von Benutzern.

Bekannte Beispiele fur die Authentifizierung sind etwa [Facebook Connect](http://developers.facebook.com/connect.php), [Google FriendConnect ](http://www.google.com/friendconnect/)oder der [OpenID](http://openid.net/)-Standard, mit denen man sich den Aufbau eines eigenen User-Pools spart, indem sich die Nutzer uber andere Plattformen einloggen. Dies nennt man dann auch [Single Sign-On](http://de.wikipedia.org/wiki/Single_Sign-on).

Im Bereich der Autorisierung hat sich der [OAuth](http://oauth.net/)-Standard etabliert, uber den der Nutzer festlegen kann, ob seine Daten Dritten uber APIs zuganglich sind (beispielsweise ob eine externe Anwendung Tweets in seinem Namen posten darf).

## **Zusammenfassung**

APIs sind aus der heutigen Web-Welt nicht mehr wegzudenken. Die zunehmende Öffnung gegenuber Drittanbietern ist eine der spannendsten Entwicklungen im Web, und wird Plattformen und Inhalte zu einem noch dichteren Netz miteinander verweben.

Rund um die effektive Entwicklung und Nutzung von APIs entsteht außerdem ein ganz eigenes Ökosystem: So bieten Anbieter wie [Apigee](http://www.apigee.com/) beispielsweise umfangreiche Analyse- und Kontrollfunktionen fur eigene Web APIs an.
