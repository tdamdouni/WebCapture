# Fibonacci-Heap

_Captured: 2015-09-29 at 00:56 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Fibonacci-Heap)_

In der [Informatik](https://de.m.wikipedia.org/wiki/Informatik) ist ein **Fibonacci-Heap** ([englisch](https://de.m.wikipedia.org/wiki/Englische_Sprache) _heap_ ‚Halde') eine [Datenstruktur](https://de.m.wikipedia.org/wiki/Datenstruktur), ahnlich einem [Binomial-Heap](https://de.m.wikipedia.org/wiki/Binomial-Heap), die eine [Vorrangwarteschlange](https://de.m.wikipedia.org/wiki/Vorrangwarteschlange) realisiert. Das heißt, dass Elemente mit festgelegter Prioritat in beliebiger Reihenfolge [effizient](https://de.m.wikipedia.org/wiki/Effizienz_\(Informatik\)) im Heap gespeichert werden konnen und stets ein Element mit hochster Prioritat entnommen werden kann. Die Prioritat der Elemente wird diesen durch [Schlussel](https://de.m.wikipedia.org/wiki/Schl%C3%BCssel_\(Informatik\)) aufgepragt. Über der Menge der Schlussel muss daher eine [Totalordnung](https://de.m.wikipedia.org/wiki/Totalordnung) bestehen, wie sie zum Beispiel die Kleiner-Relation (<) uber den [ganzen Zahlen](https://de.m.wikipedia.org/wiki/Ganze_Zahl) darstellt. Fibonacci-Heaps wurden erstmals [1984](https://de.m.wikipedia.org/wiki/1984) von [Michael L. Fredman](https://de.m.wikipedia.org/w/index.php?title=Michael_L._Fredman&action=edit&redlink=1) und [Robert E. Tarjan](https://de.m.wikipedia.org/wiki/Robert_Tarjan) beschrieben. Ihr Name ruhrt von der Analyse der Datenstruktur her, bei der [Fibonacci-Zahlen](https://de.m.wikipedia.org/wiki/Fibonacci-Folge) eine große Rolle spielen.

  * [Implementierung der Operationen](https://de.m.wikipedia.org/wiki/Fibonacci-Heap)

Fibonacci-Heaps unterstutzen effizient die Operationen:

  * _insert_ - zum Einfugen eines Elementes,
  * _remove_ oder _delete_ - zum Entfernen eines Elementes,
  * _getMin_ - zum Finden des Elements mit dem minimalen Schlussel,
  * _extractMin_ - zur Ruckgabe und zum Entfernen eines Elementes mit minimalem Schlussel (=hochster Prioritat),
  * _decreaseKey_ - zum Verringern des Schlussels eines Elementes und
  * _merge_ oder _union_ - zum Verschmelzen zweier Heaps.

Alle Operationen lassen sich mit einer logarithmischen [Worst-Case-Laufzeit](https://de.m.wikipedia.org/wiki/Asymptotische_Laufzeit), also , implementieren, wobei _n_ die Zahl der aktuell im Heap befindlichen Elemente ist. Lediglich die Operationen _remove_, _extractMin_ und _decreaseKey_ benotigen im Worst-Case lineare Laufzeit, also . Amortisiert sind die Kosten fur fast alle anderen Operationen allerdings konstant, das heißt .

Folglich sind - bei [amortisierter Laufzeitanalyse](https://de.m.wikipedia.org/wiki/Amortisierte_Laufzeitanalyse) - Fibonacci-Heaps [binaren Heaps](https://de.m.wikipedia.org/wiki/Bin%C3%A4rer_Heap) oder [Binomial-Heaps](https://de.m.wikipedia.org/wiki/Binomial-Heap) bei der Ausfuhrung der Operationen _insert_ und _merge_ uberlegen. Allerdings eignen sie sich wegen der schlechten Worst-Case-Laufzeit von _remove_, _extractMin_ und _decreaseKey_ weniger fur [Online-Algorithmen](https://de.m.wikipedia.org/wiki/Online-Algorithmus), bei denen jede einzelne Operation effizient ausgefuhrt werden muss.

Laufzeiten im Vergleich:

Operation Lineare Liste Sortierte Liste (Min-)Heap Unbalancierter Binarbaum Fibonacci-Heap

insert
O(1)
O(n)
O(log n)
O(log n)*
O(1)

getMin
O(n)
O(1)
O(1)
O(1)
O(1)

extractMin
O(n)
O(1)
O(log n)
O(1)
O(log n)*

decreaseKey
O(1)
O(n)
O(log n)
O(log n)*
O(1)*

remove
O(n)
O(n)
O(log n)
O(1)¹
O(log n)*

merge
O(1)
O(n + m)
O(m log(n+m))
O(n + m)
O(1)

(*)Amortisierte Kosten (¹)Bei bekannter Position, sonst O(log n)*

Ein Fibonacci-Heap besteht aus einer Liste von Baumen mit geordneten Nachfolgern, deren Knoten Schlussel und moglicherweise eine Markierung enthalten. Die durch den Schlussel aufgepragte Prioritat jedes Knotens ist mindestens so groß wie die Prioritat seiner Kinder. Dies wird als [Heap-Bedingung](https://de.m.wikipedia.org/wiki/Heap_\(Datenstruktur\)) bezeichnet. Bei den hier dargestellten _Min-Heaps_ ist die großere Prioritat durch einen kleineren Schlussel dargestellt.

Sowohl fur die Liste der Baume als auch fur die Listen der Kindknoten in den Knoten der Baume werden zyklische [doppelt verkettete Listen](https://de.m.wikipedia.org/wiki/Doppelt_verkettete_Liste) verwendet.

Zusatzlich wird ein Zeiger auf das Element mit der großten Prioritat (dem kleinsten Schlussel) verwaltet.

Ein Fibonacci-Heap wird _normalisiert_ genannt, wenn alle Baume unterschiedlichen [Wurzelgrad](https://de.m.wikipedia.org/wiki/Grad_\(Graphentheorie\)) haben, d. h. wenn die Wurzeln der Baume in der Liste alle unterschiedlich viele Kindknoten haben.

Beim Einfugen eines Elementes mittels _insert_ wird dieses einfach als eigener Baum in die Liste der Baume eingefugt und ggf. der Zeiger auf das minimale Element aktualisiert, wenn der Schlussel des eingefugten Elementes kleiner als der des bisherigen minimalen Elementes ist. Die Laufzeit ist folglich konstant:

Ähnlich einfach gestaltet sich das Verschmelzen zweier Heaps mittels _merge_. Hier werden die Listen der zu verschmelzenden Baume einfach verkettet und der Zeiger auf das minimale Element ggf. umgesetzt, wenn der Schlussel des minimalen Elementes des hinzugefugten Heaps kleiner als der des bisherigen minimalen Elementes ist. Die Laufzeit ist wieder konstant:

Auch die Operation _decreaseKey_ wird in einem Fibonacci-Heap recht faul durchgefuhrt: Der Schlussel des zu aktualisierenden Elementes wird zuerst auf den neuen Wert gesetzt. Nun kann es sein, dass die Heapeigenschaft (alle Kinder großer als der Vater) nicht mehr erfullt ist. Um diese wiederherzustellen, loscht man das aktualisierte Element aus der Kindliste seines Vaterknotens und fugt ihn als eigenen Baum in die "Liste der Baume"/Wurzelliste ein.

Um zu vermeiden, dass durch solche Operationen der Heap zu sehr in die Breite wachst (dann wurde extractMin sehr lange dauern), stellt man nun die Bedingung, dass von jedem Knoten nur ein Kindknoten weggenommen werden darf, ansonsten muss der Knoten selbst aus der Kindliste seines Vaterknotens entfernt werden (Prozedur _Cut_) usw. Um dies zu realisieren tritt nun die oben erwahnte Markierung eines Knotens in Erscheinung: ein Knoten ist genau dann markiert, wenn er kein Knoten der Wurzelliste ist und ein Kind aus seiner Kindliste entfernt wurde. Wird nun ein Kind entfernt, dessen Vater markiert war, ruft man die Prozedur _Cut_ rekursiv auf den Vater auf. Es zeigt sich nach reiflicher mathematischer Analyse, dass die Anzahl an Knoten in einem Baum des [Grades](https://de.m.wikipedia.org/wiki/Grad_\(Graphentheorie\)) (also die Wurzel des Baumes hat Kinder) dann durch die -te Fibonaccizahl nach unten beschrankt ist, wobei der [goldene Schnitt](https://de.m.wikipedia.org/wiki/Goldener_Schnitt) ist. Dies ist fur die Funktion _extractMin_ von enormer Wichtigkeit.

Nun zu der zentralen Funktion: _extractMin_. Der Anfang dieser Funktion gestaltet sich recht einfach: Das minimale Element, auf das ja ein Zeiger zeigt, wird ausgegeben, all seine Kinder werden als einzelne Baume zur Wurzelliste hinzugefugt und das Element selbst wird aus dem Heap entfernt. Nun muss ein neues Minimum bestimmt werden. Da aber keine der bisherigen Funktionen den Heap in die Tiefe wachsen lasst, wurde dies eine lineare Zeit dauern. Daher wird der Heap vorher mit der Prozedur _cleanup_ „aufgeraumt". Danach werden alle Elemente der Wurzelliste durchgegangen, um ein neues Minimum zu finden.

Die Prozedur _cleanup_: Hierfur wird zuerst ein Array von bis initialisiert. In diesem soll nach dem _cleanup_ an Stelle ein Zeiger auf einen Baum stehen, wenn in der Wurzelliste ein Element mit Grad existiert. Es werden also alle Elemente der Wurzelliste in dieses Array eingeordnet. Kommt es dabei zu einer Überschneidung (zwei Elemente haben den gleichen Grad), so wird das Element mit dem kleineren Schlussel zum Vater des anderen gemacht, der Grad desselben wird erhoht und es wird in das Array einsortiert. Die obige mathematische Analyse versichert, dass hochstens Elemente im Array stehen. Schließlich muss die neue Wurzelliste aufgebaut werden. Dazu werden alle Elemente des Arrays durchgegangen und zu einer Liste verschmolzen. Die Laufzeit ist also .

Das Entfernen eines Elementes aus dem Heap mittels _remove_ erfolgt, indem zunachst mit _decreaseKey_ der Schlussel des zu entfernenden Elementes auf einen Wert kleiner als dem des bisherigen Minimums gesetzt wird. Dadurch wird dieses Element zum neuen minimalen Element. Anschließend kann es mit _extractMin_ entfernt werden. Die Laufzeit von _decreaseKey_ ist konstant, die von _extractMin_ betragt , also ergibt sich fur die Operation _remove_ eine Laufzeit von ebenfalls .

Die Operationen _remove_ und _decreaseKey_ setzen voraus, dass man die Position der entsprechenden Elemente im Heap kennt. Im Allgemeinen ist es namlich nicht moglich, effizient ein Element im Heap zu suchen. Daher muss die Operation _insert_ einen [Zeiger](https://de.m.wikipedia.org/wiki/Zeiger_\(Informatik\)) auf den Behalter fur das eingefugte Element zuruckliefern, den sich das aufrufende Programm im Bedarfsfall an geeigneter Stelle merkt.

Der [Algorithmus von Dijkstra](https://de.m.wikipedia.org/wiki/Algorithmus_von_Dijkstra) zum Finden eines kurzesten Pfades beziehungsweise der [Algorithmus von Prim](https://de.m.wikipedia.org/wiki/Algorithmus_von_Prim) zum Finden eines [minimal spannenden Baumes](https://de.m.wikipedia.org/wiki/Minimal_spannender_Baum) in einem [Graphen](https://de.m.wikipedia.org/wiki/Graph_\(Graphentheorie\)) mit _n_ Knoten und _m_ Kanten lassen sich mit Fibonacci-Heaps mit der [Laufzeit](https://de.m.wikipedia.org/wiki/Asymptotische_Laufzeit) von implementieren. Mit einem [binaren](https://de.m.wikipedia.org/wiki/Bin%C3%A4rer_Heap) oder [binomialen Heap](https://de.m.wikipedia.org/wiki/Binomial-Heap) waren hier nur Laufzeiten von moglich.
