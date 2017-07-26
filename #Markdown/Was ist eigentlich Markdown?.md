# Was ist eigentlich Markdown?

_Captured: 2015-11-30 at 19:55 from [t3n.de](http://t3n.de/news/eigentlich-markdown-478610/)_

Man kennt das - als ambitionierter Internet-User stoßt man fast taglich auf Begriffe, die man schon tausendmal gelesen, bei denen man aber noch nie wirklich verstanden hat, was genau sich dahinter verbirgt. Oder man hat nur eine ungefahre Ahnung, worum es geht und mochte durch das eigene Halbwissen nicht unangenehm auffallen. Wir bringen Licht ins Dunkel und erklaren die Begriffe und Plattformen auf leicht verstandliche Weise. In der Vergangenheit haben wir uns schon [reddit](http://t3n.de/news/anleitung-funktioniert-442793/), [Tumblr](http://t3n.de/news/anleitung-funktioniert-2-457561/), [GitHub](http://t3n.de/news/eigentlich-github-472886/) und [Medium.com](http://t3n.de/news/eigentlich-mediumcom-473932/) gewidmet. Heute erklaren wir euch, was es mit Markdown auf sich hat.

## Computersprachen: Schlechter Ruf eilt ihnen voraus

Computersprachen gelten weithin als kompliziert und schwierig zu erlernen. Auch wenn dem tatsachlich nicht so ist, gibt es doch eine hohe Einstiegshurde, um sich zum ersten Mal mit einer Programmier- oder Auszeichnungssprache zu beschaftigen. Andererseits aber werden solche Kenntnisse immer haufiger gefordert - beruflich wie privat. Wer heutzutage einen eigenen Blog oder eine Webseite betreiben mochte, muss sich entweder mit nervigen WYSIWYG-Editoren (What You See Is What You Get) herumschlagen oder zumindest ein Grundmaß an HTML beherrschen - oder eben Markdown verwenden.

![Inzwischen gibt es sogar ein Markdown-Logo, das vielerorts anerkannt und eingesetzt wird, auch wenn es nicht von den Markdown-Erfindern stammt.](http://t3n.de/news/wp-content/uploads/2013/07/markdown_vorschau.jpg)

> _Inzwischen gibt es sogar ein Markdown-Logo, das vielerorts anerkannt und eingesetzt wird, auch wenn es nicht von den Markdown-Erfindern stammt. (Bild:_

## Markdown: Eigentlich eine Anti-Computersprache

Markdown hat Ähnlichkeiten mit einer Computersprache, ist aber wesentlich einfacher konzipiert und soll so fur jeden verstandlich sein. Markdown ermoglicht es, Texte im Web zu formatieren, ohne das betreffende Dokument dazu mit eckigen Klammern, Befehlen und sonstigen Kommandos zu uberfluten, wie man sie fur ein gestyltes HTML-Dokument normalerweise benotigt. Ein Markdown-Dokument soll ubersichtlich bleiben, und auch im Rohformat angenehm zu lesen sein. Deswegen verwendet Markdown einfache Zeichen zur Formatierung von Text, zum Beispiel Sternchen und Unterstriche anstelle von eckigen Klammern und langen Befehlen. In gewisser Weise kann man Markdown also auch als eine Anti-Computersprache bezeichnen, weil es dazu da ist, um Computersprachen in gewissen Nutzerkreisen uberflussig zu machen.

## Markdown-Beispiel: Nur 8 statt 49 Zeichen fur die Formatierung notig

Am besten zeigen sich die Vorteile von Markdown in einem Praxisbeispiel. Zwei Absatze mit Text und einer Überschrift sollen gestylt werden - der erste kursiv, und der Zweite gefettet. In klassischem HTML musste man eigentlich folgenden Code verfassen:

` <h2>Markdown-Test</h2>  
<p><strong>Dieser Text soll fett geschrieben werden.</strong></p>  
<p><em>Und dieser Absatz soll kursiv angezeigt werden.</em></p>  
`

Das sieht nicht sonderlich schon aus, und lasst einen Leser ohne HTML-Verstandnis sofort wieder zuruckschrecken. In Markdown wurde das obere Beispiel wie folgt aussehen:

` ## Markdown-Test  
**Dieser Text soll fett geschrieben werden.**  
  
*Und dieser Absatz soll kursiv angezeigt werden.*  
`

Im HTML-Format werden ganze 49 Zeichen zur Formatierung benotigt. In Markdown wird fur die gesamte Formatierung nur ein Bruchteil der Zeichen benotigt, namlich acht Stuck, und außerdem ist der Text deutlich angenehmer zu lesen.

Das Beispiel zeigt bereits einige der wichtigsten Markdown-Auszeichnungen:

  * **Überschriften:** Überschriften werden einfach mit Rauten ausgezeichnet. Die Anzahl der Rauten entspricht der Ordnung der Überschriften. Eine Headline dritter Ordnung wurde also so aussehen: `### Headline 3`
  * **Fettschreibung und Kursivierung:** Um einen Text fett oder kursiv zu setzen, genugt es in Markdown, den entsprechenden Abschnitt in Sternchen zu setzen. Ein Sternchen bedeutet „kursiv", zwei Sternchen bedeuten „fett". `*Kursiv* bzw. **Fett**`
  * Markdown unterstutzt deutlich mehr Formatierungen, etwa das Setzen von Links oder Einbinden von Bildern. Alle Details dazu findet man in der sehr u[bersichtlichen Markdown-Dokumentation von Daring Fireball ](http://daringfireball.net/projects/markdown/).

## Markdown: gemacht fur Nicht-Programmierer

Das Beispiel zeigt, wie sinnvoll der Einsatz von Markdown ist, gerade in Bereichen, wo auch Menschen ohne Code-Hintergrund in Kontakt mit den betroffenen Texten kommen. Aus diesem Grund gibt es inzwischen viele Content-Management Systeme, die auch mit Markdown-Inhalten bestuckt werden konnen. Ein solcher Editor kombiniert die Vorteile eines Reintext-Editors (ressourcenschonend und keine Probleme bei der Darstellung einer Vorschau) mit der guten Lesbarkeit und Übersichtlichkeit eines WYSIWYG-Editors. CMS, die von Haus aus mit Markdown umgehen konnen sind zum Beispiel: [Anchor ](http://anchorcms.com/), [Kirby ](http://getkirby.com/) und [Dropplets ](http://dropplets.com/).

![Neuere CMS können häufig bereits von Haus aus mit Markdown umgehen. So zum Beispiel das Anchor CMS.](http://t3n.de/news/wp-content/uploads/2013/07/markdown_anchor1.jpg)

> _Neuere CMS konnen haufig bereits von Haus aus mit Markdown umgehen. So zum Beispiel das Anchor-CMS._

Auch immer mehr bekannte Webdienste springen auf den Markdown-Zug mit auf. So konnen Nutzer inzwischen bei [StackOverflow ](http://stackoverflow.com/), [GitHub ](https://github.com/), [reddit ](http://www.reddit.com) und mehr Beitrage und Beschreibungen in Markdown verfassen. Sogar Google+ verwendet zum Verfassen von Beitragen eine Markdown-ahnliche Syntax. Auch außerhalb von CMS gibt es inzwischen [nutzliche Online-Editoren](http://t3n.de/news/schreiben-browser-5-456365/), die Markdown verstehen. Und sogar der CMS-Veteran WordPress lasst sich [mittels Plugin Markdown-kompatibel ](http://wordpress.org/plugins/wp-markdown/) machen.

### Weiterfuhrende Links

Mit ECMAScript6 wird Webentwicklung noch besser. Microsoft Edge und andere moderne Browser unterstutzen den offenen Standard bereits. Lerne jetzt das Konzept von Klassen und Vererbung in ECMAScript6 kennen und teste die nachste Evolutionsstufe direkt in deinem lokalen Browser.  
[ECMAScript6 kennenlernen](http://guruads.de/api/click/564b334f497959bf2600003c)
