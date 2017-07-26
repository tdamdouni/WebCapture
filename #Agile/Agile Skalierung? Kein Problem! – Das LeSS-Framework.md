# Agile Skalierung? Kein Problem! – Das LeSS-Framework

_Captured: 2016-05-28 at 23:33 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/management-und-recht/projektmanagement/agile-skalierung-kein-problem-das-less-framework.html)_

![Statt zu versuchen, viele Scrum-Teams zu koordinieren, machen wir einfach das Entwicklungs-Team größer. © Fabian Schiller](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720_Less_2_One-PO-Multiple-Dev-Teams_1aec314c28.jpg)

> _Statt zu versuchen, viele Scrum-Teams zu koordinieren, machen wir einfach das Entwicklungs-Team großer. (C) Fabian Schiller_

**Bis vor einiger Zeit hatten agile Methoden noch den Ruf, nur im Kleinen zu funktionieren. Noch Anfang 2015 habe ich in einem Statement einer Professorin einer deutschen Hochschule gelesen, wie wir alle wussten, "eignen sich agile Methoden hochstens unter ganz bestimmten Voraussetzungen, etwa im Hinblick auf die begrenzte Große der Teams bzw. der Zuverlassigkeitsanforderungen sowie der raumlichen Nahe der Beteiligten."**

**Statements dieser Art sind glucklicherweise inzwischen zumeist Geschichte. Langst haben zahlreiche Großkonzerne und Vorhaben gezeigt, dass sich agile Prinzipien und Prozesse durchaus auch fur Softwareentwicklung im Großen eignen. Trotzdem geistert nach wie vor die Mar vom "agilen Skalierungsproblem" durch die Welt. Zahlreiche Skalierungs-Modelle kummern sich um diesen lukrativen Markt (z. B: SAFe, Nexus, LeSS, die ScALeD Principles, das Spotify-Modell, etc.).**

Ich mochte hier die folgende Hypothese in den Raum stellen: "Es gibt kein agiles Skalierungs-Problem." Warum glaube ich das? Ganz einfach: Ein Unternehmen, das es geschafft hat, 5.000 einzelne Mitarbeiter zu koordinieren und mit diesen Produkte auszuliefern, sollte es doch auch schaffen, 500 Teams zu koordinieren. Die Komplexitat der Koordination nimmt mit agilen Methoden doch eigentlich erst einmal ab! Die Methoden von "fruher" werden ja nicht plotzlich unbrauchbar. Es stellen sich dann naturlich die Fragen: "Ist das dann noch agil?" und "Geht das nicht auch besser?". Beide Fragen sind berechtigt und die Antworten naheliegend. Trotzdem meine ich, dass es wichtig ist, sich bewusst zu machen, dass wir mit Agilitat nicht ein neues Problem verursachen, sondern Potential fur eine deutliche Verbesserung der Koordination schaffen. Wir sollten also vielleicht lieber von einem "agilen Skalierungs-Potential" sprechen.

Nur, wie soll man dieses Potential heben? Hierfur gibt es zahlreiche Ansatze. Einige davon sind oben bereits genannt. Es sei vorab gesagt: Es gibt keinen richtigen und keinen falschen Ansatz, das agile Skalierungs-Potential zu heben. Es gibt Ansatze, die funktionieren fur das einen Unternehmen besser und andere, die anderen Unternehmen wertvolle Impulse fur Skalierungsfragen liefern. Im vorliegenden Artikel beschaftigen wir uns mit dem LeSS (Large Scale Scrum) Ansatz, der von Bas Vodde und Craig Larman aus der Taufe gehoben wurde [[1]](http://www.informatik-aktuell.de/management-und-recht/projektmanagement/agile-skalierung-kein-problem-das-less-framework.html).

## Warum LeSS? 

![Abb.1: Der Sweet Spot. © Fabian Schiller](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_Less_1_Sweet-Spot_Selbstorganisation_ae318f13a0.png)

> _Abb.1: Der Sweet Spot. (C) Fabian Schiller_

Aber warum nehmen wir ausgerechnet LeSS unter die Lupe? Zum einen habe ich personlich sehr gute Erfahrungen mit diesem Ansatz gemacht. Zum anderen hat mir Bas Vodde einmal gesagt, dass er und Craig Larman glauben, dass LeSS ein sehr guter Ansatz ist, weil er genau den Sweet Spot trifft, bei so vielen Vorgaben wie notig und so wenigen wie moglich. Ähnlich wie Scrum selbst stellt es nur einen Prozessrahmen dar, der von den Teams, die ihn verwenden, noch sehr individuell und vielfaltig ausgestaltet werden kann. Dieses Argument scheint mir personlich plausibel und hebt LeSS tatsachlich von manch anderem Skalierungs-Framework ab.

## Was ist LeSS? 

![Abb.2: Skalierung Entwicklungs-Team. © Fabian Schiller](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_Less_2_One-PO-Multiple-Dev-Teams_f2a250bc8c.png)

> _Abb.2: Skalierung Entwicklungs-Team. (C) Fabian Schiller_

Nicht umsonst gibt es den Slogan "Large Scale Scrum is Scrum". Und tatsachlich ist der Grundgedanke des LeSS-Frameworks einfach: Statt zu versuchen, viele Scrum-Teams zu koordinieren - also mehrere Entwicklungs-Teams, ScrumMaster und Product Owner - machen wir doch einfach das Entwicklungs-Team "großer". Das bedeutet, dass es in LeSS grundsatzlich nur einen Product Owner gibt! Dieser kummert sich um ein zentrales Backlog, aus dem sich dann mehrere Entwicklungs-Teams bedienen. Wir werden spater sehen, dass es hier eine kleine Ausnahme gibt wenn wir mit mehr als acht Teams arbeiten (LeSS Huge). Die Entwicklungs-Teams sind Feature-Teams, die idealerweise beliebige Backlog-Items aus einem zentralen Product Backlog bearbeiten konnen.

## Wie koordiniert man viele Entwicklungs-Teams?

Die Koordination der Teams funktioniert also uber den zentralen Backlog und gemeinsame Sprint-Planung und Review. "Gemeinsam" bedeutet in diesem Fall tatsachlich, dass alle Teams zur gleichen Zeit im gleichen Raum an der Planung beteiligt sind. Das hort sich erst einmal sehr aufwandig und schwer koordinierbar an. Ist in der Praxis aber ein wichtiger und zentraler Bestandteil der Abstimmung zwischen den Teams. Bei kleineren Projekten sollte man hier alle Teammitglieder beteiligen. Ab einer gewissen Große ist es sinnvoller, mit Stellvertretern aus den Teams zu arbeiten.

Bei der Sprint-Planung stellt der Product Owner einfach der Reihenfolge im Backlog nach die Backlog-Items vor. Die Teams entscheiden dann selbstandig, welches Team welche Items ubernimmt und bearbeitet.

Fur ein Sprint-Review mit sehr vielen Beteiligten sollte man sich ein wenig mehr Gedanken machen. Eine klassische Frontal-Prasentation ist hier sicherlich nicht das wertvollste, was man dem Kunden anbieten kann. Mehr Raum fur Dialog und Ideen zum Produkt bieten beispielsweise Vorgehen wie der Sprint-Review Basar, bei dem in einem großen Raum verschiedene Stande zu verschiedenen Themen aufgebaut werden, an denen die Teams ihre Ergebnisse prasentieren.

## LeSS als Organisations-Entwicklungs-Framework

In LeSS geht es aber im Kern nicht darum, einen bestimmten Prozess zu etablieren, sondern organisatorische Dysfunktionen zu erkennen und anzugehen. Das bedeutet auch, dass LeSS nicht nur ein Skalierungs-Framework ist. Man kann es auch oder vielleicht sogar vielmehr als Organisations-Entwicklungs-Framework verstehen. Es gibt daher außer den oben genannten zentralen Merkmalen im wesentlichen drei Grundelemente, die das LeSS-Framework definieren:

  1. Die Prinzipien
  2. Die Regeln
  3. Die Experimente
  
  ## Prinzipien

![Abb.3: Das Lean-Gebäude. © Fabian Schiller](fileadmin/_processed_/csm_Less_3_Das-Lean-Gebaeude_8d9990947c.png)Abb.3: Das Lean-Gebäude. © Fabian Schiller

Wenn man genau hinsieht, handelt es sich bei den LeSS-Prinzipien gar nicht um Prinzipien. Es sind nur teilweise Prinzipien, wie "Kundenfokus", oder "Fokus auf das gesamte Produkt". In den LeSS-Prinzipien verstecken sich zusätzlich sehr wertvolle Denkmodelle und Theorien wie das Lean-Gedankengut, systemisches Denken oder die Warteschlangentheorie ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[2] ](management-und-recht/projektmanagement/agile-skalierung-kein-problem-das-less-framework.html#c16340)aus der Welt der Algorithmentheorie. Das ist deshalb wertvoll, weil diese Gedanken enorme Auswirkungen auf die Art und Weise haben, wie wir Organisationen aufbauen und gestalten sollten. Ich möchte hier selektiv einige Beispiele vorstellen: 

Bei** Lean Thinking** handelt es sich um das Gedankengebäude, das vermutlich einen großen Teil des Erfolgs von Toyota in den letzten Jahrzehnten erklärt. Nun ist das grundsätzlich kein neuer Gedanke, im Gegenteil: bereits in den siebziger und achtziger Jahren gab es eine Welle von "Lean"-Adoptionen im produzierenden Gewerbe. Mit nachhaltigen Folgen wie beispielsweise der dramatischen Reduktion von Lagerhaltung und der inzwischen üblichen Just-in-time-Produktion. Allerdings haben sich diese Prinzipien in der Softwarewelt noch nicht wirklich etabliert. Hier gibt es noch enormes Potential und einige Schätze zu heben. Allerdings ist Vorsicht geboten: Auch bei Lean Thinking handelt es sich nicht einfach um eine Menge von Prozessen und Tools. Es ist vielmehr ein Mindset, in dem ein zentraler Bestandteil der Respekt vor den Menschen ist. Dieser wurde und wird leider häufig bei Change-Initiativen zu häufig über Bord geworfen. Die Ergebnisse sind dann entsprechend suboptimal. 

Auch in der **Warteschlangentheorie** finden sich viele Forschungsergebnisse und Gedanken, die sich auf die Softwareentwicklung übertragen lassen und einiges an Potential freilegen können. Der Grundgedanke ist, dass wir in der Softwarewelt sehr viele unsichtbare Warteschlangen aufbauen (z. B. Anforderungsdokumente, ungetestete Software) und uns kaum um die optimale Behandlung dieser Warteschlangen kümmern. Wussten Sie beispielsweise, dass bei der Steigerung der Auslastung einer Ressource von 50% auf 90%, die Wartezeit für neue Aufgaben sich nicht ungefähr verdoppelt, sondern vervielfacht? In der Warteschlangentheorie finden sich viele Ideen und Forschungsergebnisse dazu, wie man mit derartigen Problemen umgehen sollte. Die Basis dafür bilden natürlich wieder agile Methoden wie Scrum und vor allem das Sichtbarmachen der Warteschlangen. 

In den weiteren "Prinzipien" hinter Large Scale Scrum verstecken sich viele Ideen, die für Ihr Unternehmen hilfreich und nützlich sein können. Das Verständnis dieser Prinzipien ist eine der fundamentalen Säulen für eine erfolgreiche LeSS-Adaption. Denn es geht, wie gesagt, nicht darum, vielen Teams einen neuen Prozess überzustülpen, sondern vorhandene Probleme und Potentiale in der Organisation aufzudecken und zu optimieren.

## Regeln

Trotz dem LeSS auf Prinzipien basiert gibt es auch einige Regeln. Nicht jeder, der die Prinzipien kennt und mit mehreren Teams arbeitet, sollte davon sprechen, dass er LeSS adoptiert. Die LeSS-Regeln machen Aussagen zu den folgenden Punkten:

  * **Struktur: **Die LeSS-Regeln zur Struktur geben vor, dass die große Mehrheit der Teams selbstorganisierte Feature-Teams sein müssen. Das bedeutet, dass sie selbständig komplette Features für Kunden bauen können. Außerdem werden Rollen wie ScrumMaster und Manager genauer beschrieben.
  * **Produkt: **Es gibt in LeSS immer genau einen Product Owner und ein Product Backlog. Es gibt eine gemeinsame Definition of Done, die von allen Teams geteilt wird.
  * **Sprint: **Es gibt einen gemeinsamen Sprint für alle Teams. In den Regeln zum LeSS-Sprint wird auch genauer festgelegt, wer an welchen Meetings teilnehmen muss und was dort passiert.

## LeSS Huge 

Gerade die Idee, nur einen Product Owner zu haben, stößt oft auf großes Unverständnis. Kennen wir doch die Product Owner für einzelne Teams bereits schon als stark geforderte und belastete Personen. Hier gilt es allerdings, zwei Dinge zu beachten: 

Zum einen ist der Product Owner in LeSS sicherlich nicht der "Requirements Engineer", zu dem er fälschlicherweise in vielen Scrum-Adoptionen verkommen ist. Er ist vielmehr derjenige, der die wesentlichen Entscheidungen zum Produkt trifft. Zum Beispiel auch die, ob die Entwicklung am Produkt eingestellt wird. Der Product Owner in LeSS (wie eigentlich auch in Scrum) ist also tatsächlich der Besitzer des Produktes – wie es der Name schon sagt. Damit arbeitet er natürlich auf einer sehr viel abstrakteren Ebene als das der Product Owner tut, den wir häufig in Ein-Team-Scrum-Implementierungen sehen. Viele der Aufgaben dieser Ausprägung der Rolle liegen in LeSS im selbstorganisierten crossfunktionalen Team. 

Zum zweiten hat es sich in der Praxis tatsächlich als unpraktikabel erwiesen, einen Product Owner mit mehr als acht Teams arbeiten zu lassen. Aus diesem Grund gibt es LeSS Huge für Kontexte, in denen sehr viele Teams am gleichen Produkt arbeiten. In LeSS Huge gibt es ein Konzept, dass Feature-Areas genannt wird. Für jede dieser Feature-Areas gibt es dann zusätzlich zum zentralen Product Owner einen Area Product Owner, der eine spezielle Sicht auf das zentrale Product Backlog verwaltet, die "Area Product Backlog" genannt wird. In dieser Sicht trifft er die Priorisierungs-Entscheidungen für die entsprechende Feature Area. Feature Areas sind also Spezialisierungen auf Aspekte des Produkts, die aber immer noch eigenständig lieferbar sind. 

Außer dieser Erweiterung unterscheidet sich LeSS-Huge (mit mehr als acht Teams) nur in der Erweiterung einiger LeSS-Regeln, die im Wesentlichen die Requirements-Areas genauer beschreiben, von LeSS in kleineren Kontexten. 

## Experimente

Wir haben also gelernt, dass LeSS einen groben Rahmen für die Zusammenarbeit mehrerer Entwicklungs-Teams vorgibt. Außerdem gibt es eine Menge von Denkmodellen, auf denen dieser Rahmen aufbaut. Was aber tun wir jetzt konkret, um besser zu werden? Um die Organisation in Richtung Agilität zu entwickeln? 

Hier liegt aus meiner Sicht die größte Stärke von LeSS. Es gibt – außer dem groben Rahmen – keine konkreten Regeln und Vorgaben, was als nächstes zu tun ist. Vielmehr geht LeSS davon aus, dass eine agile Skalierung für jedes Unternehmen anders aussieht. Insofern kann man über den bereits genannten Rahmen hinaus nicht einfach "Best Practices" anwenden um erfolgreich zu werden. Vielmehr muss man ab jetzt in Hypothesen und Experimenten denken. Das bedeutet: Ich habe eine Idee, wie wir unser Unternehmen verbessern können. Ich werde mir zuerst dessen bewusst, dass es sich bei dieser Idee um eine Hypothese handelt und formuliere darauf aufbauend ein Experiment, mit dem ich diese Hypothese validieren oder falsifizieren kann. Das hört sich erst einmal wenig hilfreich an, wenn man konkrete Ratschläge sucht. Aber auch hier lässt LeSS uns nicht im Stich. In den Büchern von Bas Vodde und Craig Larman sind in Summe über 600 solcher Experimente beschrieben. Diese kann man nachschlagen und überlegen, welches in der aktuellen Situation hilfreich sein könnte. Die Stärke ist aber eben, dass wir nicht ein Standard-Template nehmen und der Organisation überstülpen, sondern aus bekannten Good Practices etwas entwickeln, was auch zu unserer Organisation und unserem Kontext passt. 

## Scrum ist für Produkte, nicht für Projekte 

Einen wichtigen Punkt möchte ich an dieser Stelle noch erwähnen: Scrum wird häufig als Projektmanagement-Framework betrachtet. Tatsächlich haben wir es hier mit einem Produkt-Entwicklungs-Framework zu tun. Das bedeutet, dass sich der gesamte Prozess darauf fokussiert, ein Produkt wachsen zu lassen, das den Wert für den Kunden maximiert. Scrum ist nicht dafür optimiert, Laufzeit, Budget und Ressourcen zu managen, was ja die Kernelemente des Projektmanagements sind. 

Und ähnlich verhält es sich also – Large Scale Scrum is Scrum – mit LeSS. Es ist ein Framework, das Produktentwicklung im Fokus hat und nicht Portfoliosteuerung. Bevor Sie jetzt also anfangen, LeSS "umzusetzen", sollten Sie sich dringend Gedanken machen, welche Produkte Sie eigentlich an welchen Kunden liefern. Viel Erfolg auf diesem Weg!

Quellen

  1. LeSS – ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[More with LeSS](http://less.works/)  

C. Larman, B.Vodde, 2016: Large Scale Scrum  
C. Larman, B.Vodde, 2008: Scaling Lean & Agile Development: Thinking and Organizational Tools for Large-Scale Scrum  
C. Larman, B.Vodde, 2010: Practices for Scaling Lean and Agile Development: Large, Multisite, and Offshore Product Development with Large-Scale Scrum

  2. Wikipedia: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Warteschlangentheorie](https://de.wikipedia.org/wiki/Warteschlangentheorie)

