# Fibonacci-Baum

_Captured: 2015-09-29 at 00:57 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Fibonacci-Baum)_

Der **Fibonacci-Baum** ist Gegenstand der [Graphentheorie](https://de.m.wikipedia.org/wiki/Graphentheorie), vor allem aber eine [Datenstruktur](https://de.m.wikipedia.org/wiki/Datenstruktur) in der [Informatik](https://de.m.wikipedia.org/wiki/Informatik). Er stellt einen Spezialfall des [AVL-Baums](https://de.m.wikipedia.org/wiki/AVL-Baum) dar, und zwar zu gegebener [Hohe](https://de.m.wikipedia.org/wiki/H%C3%B6he_\(Graphentheorie\)) denjenigen AVL-Baum mit der kleinsten Anzahl Knoten. Der Name deutet an, dass Fibonacci-Baume ahnlich den [Fibonacci-Zahlen](https://de.m.wikipedia.org/wiki/Fibonacci-Folge) [rekursiv](https://de.m.wikipedia.org/wiki/Rekursiv) definiert werden konnen.

Entfernt man einen beliebigen Knoten eines Fibonacci-Baums, so entsteht bei den Stufen ≥ 3 ein Baum, der nicht mehr Fibonacci-Baum ist. Im Beispiel unten ist er auch nicht mehr AVL-Baum, wenn z. B. eine _1_, die nicht die linkeste ist, entfernt wird.

Eine Art „Basis des Logarithmus" ist wie bei den Fibonacci-Zahlen die Zahl des [goldenen Schnittes](https://de.m.wikipedia.org/wiki/Goldener_Schnitt). Ideal ware fur einen [Binarbaum](https://de.m.wikipedia.org/wiki/Bin%C3%A4rbaum) naturlich die Basis , das Aufrechterhalten scharferer Balancekriterien, z. B. der Hohenausgewogenheit beim [vollstandig balancierten Binarbaum](https://de.m.wikipedia.org/wiki/Bin%C3%A4rbaum), ist aber nach Modifikationen des Baums so aufwandig, dass im Mittel die Gesamtkosten solcher Baume hoher werden, es sei denn die Anwendung ist ganz extrem vom Suchen dominiert. Das [AVL-Kriterium](https://de.m.wikipedia.org/wiki/AVL-Baum) erscheint als attraktiver Kompromiss.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/e/ea/Fibonacci_Tree_5.svg/240px-Fibonacci_Tree_5.svg.png)

> _Fibonacci-Baum der Stufe 5_

Fibonacci-Baume werden vor allem bei Effizienzuberlegungen zu [hohen-balancierten Baumen](https://de.m.wikipedia.org/wiki/Balancierter_Baum), insbesondere AVL-Baumen, als Extremfalle und Vergleichsobjekte herangezogen.
