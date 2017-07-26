# Code Review -- und dann?

_Captured: 2016-11-27 at 11:35 from [www.judithandresen.com](http://www.judithandresen.com/2016/07/15/code-review-und-dann/)_

Code Reviews gehoren zur gangigen Praxis in Entwicklungsteams. Ziel eines Code Reviews ist es, mogliche Fehler oder Vereinfachungen zu identifizieren, um langfristig die Codequalitat zu steigern.

Die grundsatzliche Code Review Regel ist schnell aufgestellt:

Bevor ein Ticket den Status "Fertig" erlangen darf,  
sieht die Definition of Done vor,  
dass der Software-Code durch ein anderes Teammitglied gepruft wird.

Nicht immer schreibt die Definition of Done ein grundsatzliches Code Review vor. Manchmal sind es auch nur gezielt ausgewahlte Tickets, die ein Code Review durchlaufen sollen.

Unabhangig von der Regelmaßigkeit des Code Reviews bleibt eine Frage im Vorfeld meist ungeklart:

Im Idealfall sind sich die Beteiligten einig: Der Code muss angepasst werden. Und der Zeitaufwand der Änderung steht in einem angemessenen Verhaltnis zum Ergebnis. Damit steht einer schnellen Anpassung nichts im Wege.

![](https://image.jimcdn.com/app/cms/image/transf/dimension=409x1024:format=png/path/sd4f720d6f8b65129/image/i8b2c8f695b58eced/version/1468594987/image.png)

Wahrend funktionale Fehler meist klar identifiziert werden konnen, stellt sich das Maß "Einfachheit" komplexer dar. Nicht immer kommen Entwicklerinnen und Entwickler in diesem Zusammenhang auf einen Nenner. Unterschiedliche Qualitatsanspruche an die Codequalitat sorgen an diesem Punkt fur einen intensiven Austausch zwischen den Beteiligten. Die optimale Vorstellung "Wir entscheiden gemeinsam, was der beste Weg ist" funktioniert nicht immer. Uneinigkeit uber den besten Weg eine Funktion umzusetzen, kann Euer Projekt blockieren.

Konsens kann hier zur Falle werden. Und das Ergebnis des Code Reviews blockiert. An Stelle, dass der Code besser wird, verheddert Ihr Euch in Ergebnis-Debatten.

## Was passiert, wenn sich die Beteiligten uber das Review-Ergebnis uneinig sind?

Angenommen der Reviewer beziehungsweise die Reviewerin findet etwas im Code, das aus deren Sicht angepasst werden sollte. Der Code-Ersteller oder die Code-Erstellerin ist in diesem Punkt anderer Meinung. Eine Diskussion uber die unterschiedlichen Standpunkte fuhrt nicht zu einem Konsens. Wer trifft die Entscheidung uber das weitere Vorgehen?

  * Lohnt es sich fur die Veranderung des Codes zusatzlichen Aufwand zu investieren und so die Codequalitat langfristig zu steigern? 
  * Oder ist davon auszugehen, dass die Funktion mittelfristig sowieso durch eine andere Losung abgelost wird? 

Gerade in Teams mit Fluktuation spielt leicht verstandlicher Code eine besondere Rolle. Neuen Team-Mitgliedern soll es moglichst einfach gemacht werden, sich in die neuen Themenbereiche einzuarbeiten und schnell dauerhaft produktiv zu werden. Gleichzeitig ist der Faktor "Zeit" in vielen Projekten eine entscheidende Metrik.

Die Entscheidungsfindung in Bezug auf Review-Ergebnisse sollte einer eindeutigen Regelung folgen. Mogliche Regeln konnen hierbei sein:

  * Die Entscheidung uber die erneute Code-Veranderung trifft der Code-Ersteller oder die Code-Erstellerin. 
  * Der Rezensent oder die Rezensentin des Codes trifft die Entscheidung daruber, ob Code-Zeilen verandert werden mussen. 
  * Eine dritte Person ubernimmt die endgultige Entscheidung, wie der Code fur die geplante Funktionalitat aussehen soll. 
  * In Streitfragen entscheidet das Team im Konsent, wie zu verfahren ist. 

Beim Festlegen der Regel sind zwei Faktoren von großer Bedeutung:

  1. Alle Beteiligten mussen die Regel kennen. 
  2. Alle mussen verstanden haben, wann und warum sie Anwendung findet. 

Einigungsregeln helfen aus der Konsensfalle und machen Pair Reviews zu dem, was sie sein sollen: zu einem ausgezeichnet effizienten Lernort fur alle Beteiligten.
