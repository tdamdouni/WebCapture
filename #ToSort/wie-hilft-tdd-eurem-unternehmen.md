# Wie hilft TDD eurem Unternehmen?

_Captured: 2017-06-30 at 21:52 from [blogs.itemis.com](https://blogs.itemis.com/de/wie-hilft-tdd-eurem-unternehmen?utm_source=hs_email&utm_medium=email&utm_content=53657294&_hsenc=p2ANqtz-8LkGG5VVVQLoqmVuBHspeMz2Ot0VQBVKQzgMqThYjfdB7dqiwdEKRjcOnaH63WbGJ_0Zwsj1gzz1iLlTNFZr8ZYtOAgA&_hsmi=53657294)_

Wenn ich im Rahmen meiner Coachings die Konzepte der Testgetriebenen Entwicklung (TDD) vorstelle, stoße ich in vielen Unternehmen auf Skepsis: Steht der Nutzen in einem guten Verhaltnis zum Einfuhrungsaufwand? Die Benefits von TDD, wie Evolvierbarkeit und Wartbarkeit des Codes, wirken meist sehr abstrakt und sind daruber hinaus auch nur schwer quantifizierbar. Um den Effekt Testgetriebener Entwicklung dennoch greifbar zu machen, kann ein Blick auf eine typische Situation aus dem Entwicklungsalltag helfen.

![wie-tdd-ihrem-unternehmen-helfen-kann.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Agile/die-menschliche-glu%CC%88hbirne-hilft.jpg?t=1498831770942&width=2172&name=die-menschliche-glu%CC%88hbirne-hilft.jpg)

Donnerstagnachmittag: Der Product Owner trifft sich wie gewohnlich mit dem Entwicklungsteam zum Backlog Refinement, um neue User Stories zu erortern und Aufwande schatzen zu lassen. Den Anfang macht eine vermeintlich einfache, uberschaubare Anforderung. Nach kurzer Zeit schon haben die Entwickler ein gutes Verstandnis, was fachlich gewollt ist, und auch die Akzeptanzkriterien sind schnell gefunden. Beim abschließenden Scrum Poker kommt dann jedoch die Überraschung. Die Entwickler schatzen den Umsetzungsaufwand mit 13 Story Points enorm hoch ein. Der Product Owner ist uberrascht und hakt nach. Wie kommt das Team zu diesem Urteil?

## **Wenn ihr diese Satze hort, kann TDD euch helfen**

Hier wird es nun interessant zu horen, wie die Entwickler ihre Aussage begrunden. Drei alternative Antworten, bei denen ihr hellhorig werden solltet, mochte ich im Folgenden etwas naher betrachten.

**Variante 1: "Hierfur muss Komponente XY erweitert werden und nur der Ex-Kollege Z und der liebe Gott allein wissen, wie die genau funktioniert."**

Es gibt sie in fast jedem System; die beruchtigten Codestellen, welche die Entwickler nur mit großtem Strauben anfassen. Die genaue Funktionsweise ist unbekannt und man weiß auch nicht so recht, wie man nach der Änderung prufen soll, ob alles noch so funktioniert wie zuvor. Hinzukommt, dass man fur eine saubere Implementierung eigentlich den Code umstrukturieren musste, doch ohne das Sicherheitsnetz automatisierter Tests ware das mehr als mutig. Also erfolgt die Änderung an der risikoarmsten Stelle, meist mit der Folge, dass diese Komponente nachher noch schwerer zu verstehen ist.

**Variante 2: "Es muss zwar nur eine Zeile im Code verandert werden, aber der Aufwand fur die Regressionstests liegt bei mindestens einer Woche."**

Es gibt Änderungen, die haben einen weitreichenden Einfluss auf das gesamte Softwaresystem; man nehme nur mal die Umstellung auf das IBAN-Format fur Bankkontonummern. Um eventuelle Nebeneffekte ausschließen zu konnen, muss nach der Implementierung das gesamte System uberpruft werden. Ohne Testautomatisierung kann der Aufwand dafur immens hoch liegen. Im schlimmsten Fall existiert noch nicht einmal eine Testfalldokumentation und die Abdeckung aller Anwendungsfalle bleibt dem Zufall uberlassen. Nachbesserungen sind dann oft die Folge.

**Variante 3: "Da mussen wir erst einmal analysieren, an welcher Stelle wir ansetzen mussen."**

Diese Antwort taucht meist auf, wenn ein unerwunschtes Verhalten (aka Bug) behoben werden soll. Meist kann die Ursache fur einen beobachteten Fehler in mehreren Teilkomponenten des Systems liegen. Verfugen diese Module uber keine eigenen, dedizierten Tests, mit denen sich ihr Verhalten einzeln uberprufen lasst, bleibt den Entwicklern haufig nur der sehr zeitintensive Weg, die Wurzel des Übels am laufenden System mittels Debuggingwerkzeugen zu suchen. Je schwerer das Testszenario zu reproduzieren ist, umso aufwandiger wird dieses Verfahren. Eine einigermaßen stichhaltige Abschatzung des erwarteten Aufwandes ist meist nicht moglich.

## **Änderungen ohne Nebeneffekte dank TDD**

Fur alle diese Szenarien bietet die Testgetriebene Entwicklung eine Losung. Sie schafft es durch die hohe Testabdeckung einen Rahmen zu schaffen, in dem jede Komponente gefahrlos erweitert und umstrukturiert werden kann. Nebeneffekte von Änderungen konnen dank Testautomatisierung in kurzester Zeit entdeckt werden. Und last but not least konnen durch die komponentenbezogenen Testfalle Fehlerursachen schneller und einfacher lokalisiert werden.

Alle diese Effekte bewirken eine effizientere Produktentwicklung und sorgen dafur, dass Änderungen auch nach Jahren der Weiterentwicklung mit unveranderter Geschwindigkeit umgesetzt werden konnen.

Wenn ihr mehr uber [Trainings](https://www.eventbrite.de/e/isqi-certified-agile-test-driven-development-tickets-31152079709) und Einfuhrungskonzepten zur Testgetriebenen Entwicklung erfahren wollt, stehe ich euch gerne als Ansprechpartner zur Verfugung. Ich freue mich auf euer Feedback!

Christian Fischer ist Agile Software Craftsman bei der itemis AG und unterstutzt als Coach fur Agile Methoden und Prozesse Teams und Organisationen auf ihrem Weg zu einer effizienteren Produktentwicklung. Daneben ist er iSQI zertifizierter Trainer fur Agile Test Driven Development und regelmaßig Sprecher auf Konferenzen sowie Autor von Fachartikeln.
