# Schreibe niemals Unit Tests!

_Captured: 2017-08-08 at 19:07 from [blogs.itemis.com](https://blogs.itemis.com/de/schreibe-niemals-unit-tests?utm_source=hs_email&utm_medium=email&utm_content=54639040&_hsenc=p2ANqtz--HWD6jpO1gm-E7sTyz5PnnTWeoUshIXphQpv2dR4Vag1lMdjdbkLnpGHEi338QMSxTWgsLPBdPGpQ0s45qMPnSAuLFwg&_hsmi=54639040)_

Keine Angst, ich mache nur Spaß. Schreib Unit-Tests! Immer! Fur alles! Ausrufezeichen!

Hier konnte der Artikel schon zu Ende sein. Alles, was man wissen muss, ist: Tests sind gut. Teste unbedingt!

Leider gibt es da draußen viele Entwickler, die eine große Abneigung gegen Tests haben oder sie sogar hassen. Diese Einstellung beruht auf einer Reihe von Missverstandnissen. Die popularsten davon durften die Folgenden sein:

  * „Wir haben keine Zeit fur Tests."
  * „Ich weiß doch, dass mein Code funktioniert."
  * „Ich hasse es, diese bescheuerten Tests zu pflegen."

Dysfunktionale Teams und schlechte Entwickler-Angewohnheiten sind dermaßen weit verbreitet, dass viele Menschen tatsachlich davon ausgehen, Tests wurden viel Zeit kosten, schwierig zu pflegen sein und nur das Offensichtliche zeigen. Dementsprechend werden sie als nutzlos, uberflussig, verzichtbar und nervig abgetan.  
Ich habe lange in dieser "Testholle" schmoren mussen, bis ich entschieden habe, dass sich daran etwas andern muss. Am liebsten hatte ich alle Tests einfach verworfen. Schlechte Tests bringen keinerlei Mehrwert, behindern aber den Projektfortschritt. Von daher ist Loschen eine durchaus realistische Alternative.   
Besser ist es aber, dem Gedanken des [Handwerks](http://manifesto.softwarecraftsmanship.org/) zu folgen und konsequent Qualitat als Handlungsmaxime zu setzen. Tests sind ein Werkzeug, um qualitativ hochwertige Software zu schreiben. Qualitativ hochwertige Software spart erheblich Kosten bei Betrieb, Wartung und Weiterentwicklung. Aus genau diesem Grund sollten sorgfaltig geschriebene Tests zur Denkweise eines jeden Entwicklers gehoren und nicht, weil Blogs, Bucher oder [Sonar](https://www.sonarqube.org/) es vorgeben.

## **Testgetriebene Entwicklung als Helfer in der Not**

An dieser Stelle fragen sich viele: Wie konnen Tests das leisten? Meine Tests helfen mir dabei gar nicht. [Testgetriebene Entwicklung](https://blogs.itemis.com/de/testgetriebene-entwicklung-mehr-als-nur-qualit%C3%A4tssicherung) (Test Driven Development - TDD) ist die Antwort. Im Internet findet man Unmengen an Informationen zu dieser Methode. Es gibt [Verfechter ](https://8thlight.com/blog/uncle-bob/2014/04/25/MonogamousTDD.html)und [Gegner](http://david.heinemeierhansson.com/2014/tdd-is-dead-long-live-testing.html). Auf das Wesentliche reduziert, funktioniert TDD so:

  * Schreibe einen fehlschlagenden Test, der genau eine einzige Sache testet (RED)
  * Schreibe genau so viel Geschaftslogik, um den Test zu bestehen (GREEN)
  * Refaktoriere den Code, um ihn aufzuraumen (REFACTOR)
  * Wiederhole diese Schritte, bis du fertig bist  
  

![Unit Tests – Refactor Kreislauf](https://blogs.itemis.com/hs-fs/hubfs/Refactor-Kreislauf.png?t=1502203378619&width=2172&name=Refactor-Kreislauf.png)

> _Unit Tests - Refactor Kreislauf_

Damit dieser Kreislauf aber tatsachlich Sinn macht, mussen die Tests einigen Regeln entsprechend - leicht zu merken mit dem Akronym [FIRST](http://agileinaflash.blogspot.de/2009/02/first.html):

  * Fast (schnell)
  * Independent / Isolated (unabhangig)
  * Repeatable (wiederholbar)
  * Self Verifying (sich selbst verifizierend)
  * Timely („rechtzeitig")

Mit diesen Regeln im Hinterkopf kann man jetzt einhergehen und "Argumente" gegen Tests entkraften.

## **Keine Zeit zum Testen**

Da Testen jetzt ein fester Bestandteil eines jeden Entwicklungsschrittes ist, kann gar nicht „keine Zeit dafur" sein. Zu sagen: „Wir haben keine Zeit, zu testen" ist wie zu sagen „Wir haben keine Zeit, zu entwickeln" - und mal ehrlich, aus diesem Blickwinkel betrachtet, zeigt sich schnell das eigentliche Problem.  
Gute Tests konnen gar keine Zeit rauben - sie konnen die Entwicklung sogar beschleunigen, denn:

  * Schnelle Test sind… nun ja, schnell.
  * Fehler fallen fruher auf.
  * Man weiß, wann man fertig ist: Keine goldenen Turklinken, kein Over-Engineering.
  * Mit FIRST entwickelte Tests sind leicht zu pflegen. Das spart Zeit.

## **Ich weiß doch, dass mein Code funktioniert**

Das mag sogar stimmen. Zumindest wenn der Code gerade frisch geschrieben wurde. Aber was, wenn der Code refaktoriert worden ist? Wie weiß man dann, dass er immer noch funktioniert? Was ist mit nachster Woche? Nicht immer kann man sich daran erinnern, was der Code genau macht und warum. Was ist mit den Kollegen? Woher sollen die das wissen?

Tatsachlich testen Tests nicht, ob der Code etwas tut, sondern sie spezifizieren, was er tun soll. Jetzt und in Zukunft. Man andert Tests nur, wenn sich die Spezifikation geandert hat. Dadurch wird der Test fehlschlagen und das wiederum ist der einzige Grund, warum man funktionale Änderungen am Produktivcode vornimmt.

Wenn man nicht den Test zuerst schreibt, woher weiß man dann, was sich andern muss und wo? Woher weiß man, dass die Änderung den gewunschten Effekt hat? Woher wissen es spater die Kollegen?

## **Ich hasse es, diese bescheuerten Tests zu pflegen**

Was das angeht, weiß ich genau, worum es geht. Wir alle haben schon so gedacht. Wir kennen alle diese "Was zur Holle haben die sich denn dabei gedacht?" Momente, wenn man die Tests anderer Leute wartet. Grunde dafur konnen sein:

  * Man testet Code, der nicht testfreundlich entwickelt wurde. 
    * Der Testaufbau ist entsprechend umfangreich, kompliziert und bruchig - die Ausfuhrung ist undurchsichtig.
  * Testcode ist kein Produktivcode und muss demzufolge auch nicht die gleichen Qualitatsvorgaben erfullen 
    * Aufgrund von irrefuhrenden Namen, Aufbau und Redundanzen, ist der Test schwierig zu lesen und zu verstehen.

Testgetrieben entwickelter Code macht keinen Unterschied zwischen Geschaftslogik und Tests. Fur jede Zeile Code gelten die gleichen Regeln - und naturlich ist Test-Code Bestandteil von Refaktorierung.   
Die Tests zuerst zu schreiben hilft dabei, genau das angemessene Design zu finden. Code wird nur geschrieben, um einen bestehenden Test zu erfullen - das macht ihn automatisch testfreundlich.

## **Man glaubt nur, was man sieht**

Leider hat aber eben alles auch seinen Preis und das bedeutet in diesem Fall: Um wirklich von TDD profitieren zu konnen, musst man sich die Hande schmutzig machen:

  * Recherche und Lekture sind Pflicht.

Zugegeben: Anfangs war ich selbst sehr skeptisch, was TDD betraf. Der Wendepunkt kam fur mich, als ich mit dem [WordWrap-Kata](http://codingdojo.org/kata/WordWrap/) ubte. Ich kam schneller als gedacht zu einer sehr einfachen Losung, viel einfacher, als es „meine" Losung gewesen ware, wenn ich nicht TDD angewandt hatte. Ich bemerkte, wie hinderlich meine bisherigen Testing-Angewohnheiten gewesen waren und wie schlecht sich das auf meine Geschaftslogik ausgewirkt hatte.

## **itemis hilft**

Als agiles Unternehmen bieten wir naturlich [Coding Dojos](https://www.meetup.com/de-DE/itemis/) und [TDD-Workshops](https://www.itemis.com/de/agile/scrum/coaching-consulting/) an. Ich hatte die Moglichkeit, an einem dieser Workshops teilzunehmen und kann sagen: Es war die Muhen wirklich wert. Der Workshop war anstrengend, hat sich aber absolut gelohnt. Mein Dank geht besonders an meinen Kollegen [Christian Fischer](https://www.itemis.com/de/agile/scrum/coaching-consulting/agile-coaches/), der ein sehr leidenschaftlicher und kompetenter Workshop-Leiter ist.  
Das Training geht uber drei Tage und beinhaltet jede Menge praktischer Übungen. Am Ende kann man optional an der Abschlussprufung teilnehmen. Besteht man diese, erhalt man das [iSQI Test Driven Development](https://www.eventbrite.de/e/isqi-certified-agile-test-driven-development-tickets-31152079709)-Zertifikat.

Also: Wie ware es, aus der Testholle zu entkommen? Melde dich einfach bei uns. Wir wurden uns freuen, von dir zu horen!
