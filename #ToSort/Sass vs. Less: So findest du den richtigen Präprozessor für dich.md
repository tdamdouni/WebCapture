# Sass vs. Less: So findest du den richtigen Präprozessor für dich

_Captured: 2015-12-08 at 17:34 from [t3n.de](http://t3n.de/news/sass-vs-less-636820/)_

## Warum gibt es Praprozessoren wie Sass und Less?

CSS ist eine sehr einfache Sprache, um hauptsächlich HTML zu formatieren. Diese Einfachheit ist die Ursache, warum CSS relativ viele Features vermissen lässt. Sogenannte Präprozessoren erweitern CSS mit verschiedensten Features und Funktionen, um die Arbeit mit CSS zu beschleunigen.

Zu den Funktionen von CSS-Präprozessoren gehoren unter anderem: Variablen, Verschachtelung, Mixins, Mathematische Funktionen und Manipulation von Farben. Sowohl Less als auch Sass bieten ganz ähnliche Funktionen, allerdings unterscheidet sich die Syntax - und ist damit wohl der Hauptgrund, warum sich Entwickler entweder für Sass oder Less entscheiden.

## Das kann Sass

Knapp zehn Jahre gibt es „Syntactically Awesome Stylesheets" - also Sass - bereits und ist der wohl bekannteste Präprozessor überhaupt. Obwohl Sass schon einige Jahre auf dem Buckel hat, wurde erst vor kurzem die Version 3.4 veroffentlicht. Die Grundidee hinter der Entwicklung von Sass war es, die Arbeit mit CSS einfacher zu machen, aber gleichzeitig auch den Funktionsumfang zu erhöhen. Daher wurden in Sass Klammern sowie Semikolons entfernt. Kann Schreibarbeit sparen - muss es aber nicht: [Auto-Complete sei Dank](http://t3n.de/news/sublime-text-liebeserklaerung-538707/).

Der größte Vorteil von Sass, neben der Erweiterung von CSS, ist, dass die Sprache von mächtigen Frameworks flankiert wird. [Bourbon ](http://bourbon.io) bietet neben Grids und einzelnen Komponenten sehr viel, was das Entwickler-Herz höher schlagen lässt.

Auch das CSS-Authoring-Framework [Compass ](http://compass-style.org) nutzt Sass und wird von LinkedIn sowie von Sencha eingesetzt. Wer also lieber mit einem komfortablen UI anstatt dem Terminal arbeiten möchte, der sollte sich Compass ansehen. Auch das CSS-Framework [Zurb Foundation](http://t3n.de/news/foundation-for-apps-frontend-framework-583390/) setzt auf Sass.

Das ist aber noch nicht alles: Mit SCSS existiert eine neue Syntax, die sich näher an der Vanilla-CSS-Syntax orientiert. Diese beschränkt sich im Gegensatz zu Sass nicht auf das Einrücken von Elementen, sondern verfolgt den selben Ansatz zur Strukturierung wie Plain-CSS, nämlich geschweifte Klammern. Der große Vorteil von SCSS ist, dass man sich keine neue Syntax aneigenen muss. Denn SCSS schreibt sich wie CSS. Aus meiner Perspektive ist das aber kein Vorteil, denn Sass lässt sich einfacher und schneller schreiben als SCSS - außer ihr nutzt natürlich VIM.

Hier der Unterschied zwischen Sass und SCSS:
    
    
    $blablubb: #333
    
    .navigation
      border-color: $blablubb
      color: darken($blablubb, 5%)

In SCSS sieht der selbe Code so aus:
    
    
    $blablubb: #333;
    
    .navigation {
      border-color: $blablubb;
      color: darken($blablubb, 5%);
    }

Weiterführend kann ich euch die [Sass-Dokumentation ](http://sass-lang.com/documentation/file.SASS_REFERENCE.html) sowie dieses Video von DevTips empfehlen:

## Das kann Less

Kurze Zeit nachdem Sass veröffentlicht wurde, erblickte 2009 der Präprozessor „Less" das Licht der Entwicklerwelt. Less ist stark von Sass beeinflußt worden, allerdings war es hier das Ziel, so nah wie möglich an Vanilla-CSS zu bleiben und nur den Funktionsumfang von CSS zu erweitern. Damals wurde Less noch mit Ruby genutzt - der Präprozessor wurde aber später völlig neu implementiert und nutzt heute JavaScript. Einer der bekanntesten Vertreter von Less ist wohl das Framework Twitter Bootstrap.

Variablen werden in Sass mit einem `$`-Zeichen dargestellt, Less nutzt dagegen das `@`-Zeichen. Das ist naturlich etwas verwirrend, denn Sass nutzt wiederum das `@`-Zeichen fur Mixins. Wenn ihr euch tiefer mit Less beschaftigen wollt, dann kann ich euch [die Dokumentation empfehlen ](http://lesscss.org/functions/).

Um euch einen direkten Überblick bezuglich der Schreibweise von Less beziehungsweise Sass zu ermoglichen, kann ich euch außerdem [diesen Link zu Less und Sass ](https://gist.github.com/chriseppstein/674726) empfehlen.

[Foundation 6 ist da: Das mussen Designer uber die neue Version wissen

](http://t3n.de/news/zurb-ui-framework-foundation-6-658539/)

## Fazit: Viel lernen du musst, junger Padawan

> „Tools beschleunigen eure Arbeit, sie machen sie aber nicht besser."

Bevor ihr euch aber um Sass, Less, Stylus oder Build-Tools wie Gulp oder Grunt Gedanken macht, musst ihr zuerst grundsolide in HTML, CSS und JavaScript schreiben konnen - es hilft nichts, wenn ihr coole Tools nutzen wollt und nicht zu 100 Prozent gutes CSS, HTML und JavaScript schreiben konnt.

Personlich ziehe ich Sass Less und SCSS vor. Ich finde der Code ist dadurch einfacher zu warten, und ich bin vor allem schneller, wenn es um kleinere Änderungen am Code geht.

Ich hasse es einfach sechs Klammern neu zu positionieren, nur weil ich eine minimale Änderungen durchfuhren mochte. Sass erweist sich fur meinen Workflow einfach als die bessere Moglichkeit Praprozessoren zu nutzen. Vergesst aber nicht, dass CSS bereits gewisse Funktionen von Praprozessoren (bald) nativ unterstutzt und [Postprozessoren wie Myth](http://t3n.de/news/css-variablen-postprozessor-myth-517612/) einen alternativen Weg gehen.

Wenn ihr eure Entscheidung an den Frameworks festmachen wollt: SCSS sowie Less akzeptieren reines CSS als valide Eingabe. Wenn ihr eure Entscheidung daran festmachen wollt, welcher Praprozessor von den meisten Agenturen eingesetzt wird, kann ich euch sagen: Es gab nach dem Auftauchen von Less einen regelrechten Hype um Less, da keine neue Syntax (die draus besteht, keine Klammern und Semikolons zu schreiben) erlernt werden musste. Fur mich personlich war das aber noch nie ein Grund mich gegen Sass zu entscheiden. Nach dem Less-Hype sehe ich inzwischen - auch im internationalen Umfeld - immer wieder mehr Sass als Less.

Ich habe meine Entscheidung damals getroffen, in dem ich eine vorhandene CSS-Datei konvertiert und dann damit weiter gearbeitet habe. Ein Demo-Projekt mit zwei Praprozessoren: Sass war uberzeugender.

Das Wichtigste: Tools beschleunigen eure Arbeit, sie machen sie aber nicht besser. Ich hoffe dieser Artikel hilft euch bei eurer Entscheidung.

**Welchen Praprozessor nutzt ihr?**

Mit dem DEVELOPER Tarif vom TYPO3 Spezialisten jweiland.net kannst du Web-Projekte 3 Monate in einer realen Hosting Umgebung entwickeln und testen - ohne jede Verpflichtung. Auf Wunsch kann der Tarif anschließend in ein regulares Hosting Paket umgewandelt werden.

[Fordere jetzt dein kostenloses Entwickler-Hosting an!](http://guruads.de/api/click/56542ba44979599b1c000039)
