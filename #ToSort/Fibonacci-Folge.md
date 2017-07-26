# Fibonacci-Folge

_Captured: 2015-09-29 at 00:53 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Fibonacci-Folge)_

![](http://upload.wikimedia.org/wikipedia/commons/thumb/9/95/FibonacciBlocks.svg/220px-FibonacciBlocks.svg.png)

> _Kachelmuster aus Quadraten, deren Kantenlangen der Fibonacci-Folge entsprechen_

Die **Fibonacci-Folge** ist die unendliche [Folge](https://de.m.wikipedia.org/wiki/Folge_\(Mathematik\)) von [naturlichen Zahlen](https://de.m.wikipedia.org/wiki/Nat%C3%BCrliche_Zahl), die mit zweimal der Zahl 1 beginnt und in der die Summe zweier aufeinanderfolgender Zahlen die unmittelbar danach folgende Zahl ergibt:

Die darin enthaltenen Zahlen heißen **Fibonacci-Zahlen**. Benannt ist die Folge nach [Leonardo Fibonacci](https://de.m.wikipedia.org/wiki/Leonardo_Fibonacci), der damit im Jahr 1202 das Wachstum einer Kaninchenpopulation beschrieb. Die Folge war aber schon in der Antike sowohl den [Griechen](https://de.m.wikipedia.org/wiki/Antikes_Griechenland) als auch den [Indern](https://de.m.wikipedia.org/wiki/Indien) bekannt.[[2]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge)

  * [Berechnung](https://de.m.wikipedia.org/wiki/Fibonacci-Folge)

Die Fibonacci-Folge ist durch das [rekursive](https://de.m.wikipedia.org/wiki/Rekursion) Bildungsgesetz

mit den Anfangswerten

definiert. Das bedeutet in Worten:

  * Fur die beiden ersten Zahlen wird der Wert _eins_ vorgegeben.
  * Jede weitere Zahl ist die Summe ihrer beiden Vorganger in der Folge.

Daraus ergibt sich:

    

n _f_n n _f_n n _f_n n _f_n n _f_n

1
1
11
89
21
10 946
31
1 346 269
41
165 580 141

2
1
12
144
22
17 711
32
2 178 309
42
267 914 296

3
2
13
233
23
28 657
33
3 524 578
43
433 494 437

4
3
14
377
24
46 368
34
5 702 887
44
701 408 733

5
5
15
610
25
75 025
35
9 227 465
45
1.134.903.170

6
8
16
987
26
121 393
36
14 930 352
46
1 836 311 903

7
13
17
1 597
27
196 418
37
24 157 817
47
2 971 215 073

8
21
18
2 584
28
317 811
38
39 088 169
48
4 807 526 976

9
34
19
4 181
29
514 229
39
63 245 986
49
7 778 742 049

10
55
20
6 765
30
832 040
40
102 334 155
50
12 586 269 025

Aus der Forderung, dass die Rekursion

auch fur ganze Zahlen gelten soll, erhalt man eine eindeutige Fortsetzung auf den Index 0 und auf negative Indizes. Es gilt

Die so erweiterte Fibonacci-Folge lautet dann

Daruber hinaus ist eine [Verallgemeinerung der Fibonacci-Zahlen](https://de.m.wikipedia.org/wiki/Verallgemeinerte_Fibonacci-Folge) auf [komplexe Zahlen](https://de.m.wikipedia.org/wiki/Komplexe_Zahl) und auf [Vektorraume](https://de.m.wikipedia.org/wiki/Vektorraum) moglich.

[Identitaten](https://de.m.wikipedia.org/wiki/Identit%C3%A4tsgleichung):

[Teilbarkeit](https://de.m.wikipedia.org/wiki/Teilbarkeit):

  * Je zwei benachbarte Fibonaccizahlen sind teilerfremd, d. h. .
  * ; falls ist, gilt auch die Umkehrung. Insbesondere kann fur nur dann eine [Primzahl](https://de.m.wikipedia.org/wiki/Primzahl) sein, wenn eine Primzahl ist.
  * (genau jede dritte Fibonacci-Zahl ist durch 2 teilbar)
  * (genau jede vierte Fibonacci-Zahl ist durch 3 teilbar)
  * (genau jede sechste Fibonacci-Zahl ist durch 4 teilbar)
  * (genau jede funfte Fibonacci-Zahl ist durch 5 teilbar)
  * (genau jede achte Fibonacci-Zahl ist durch 7 teilbar)

    Fur die Teilbarkeit durch Primzahlen p gilt unter Verwendung des [Jacobi-Symbols](https://de.m.wikipedia.org/wiki/Quadratischer_Rest):

[Reihen](https://de.m.wikipedia.org/wiki/Reihe_\(Mathematik\)):

Es gibt noch zahlreiche weitere derartige Formeln.

Wie von [Johannes Kepler](https://de.m.wikipedia.org/wiki/Johannes_Kepler) festgestellt wurde, nahert sich der [Quotient](https://de.m.wikipedia.org/wiki/Quotient) zweier aufeinander folgender Fibonacci-Zahlen dem [Goldenen Schnitt](https://de.m.wikipedia.org/wiki/Goldener_Schnitt) Φ an. Dies folgt unmittelbar aus der [Naherungsformel](https://de.m.wikipedia.org/wiki/Fibonacci-Folge) fur große _n_:

Diese Quotienten zweier aufeinander folgender Fibonacci-Zahlen haben eine bemerkenswerte [Kettenbruchdarstellung](https://de.m.wikipedia.org/wiki/Kettenbruch)

    ![\\frac{1}{1} = 1 \\qquad \\frac{2}{1} = 1+\\frac{1}{1} \\qquad \\frac{3}{2} = 1+\\frac{1}{1+ \\frac{1}{1}} \\qquad \\frac{5}{3} = 1+\\frac{1}{1+ \\frac{1}{1+ \\frac{1}{1}}} \\qquad \\frac{8}{5} = 1+\\frac{1}{1+ \\frac{1}{1+ \\frac{1}{1+ \\frac{1}{1}}}}](http://upload.wikimedia.org/math/5/e/c/5ec9e81a45182c04df3560660b6a9449.png)

> _\frac{1}{1} = 1 \qquad \frac{2}{1} = 1+\frac{1}{1} \qquad \frac{3}{2} = 1+\frac{1}{1+ \frac{1}{1}} \qquad \frac{5}{3} = 1+\frac{1}{1+ \frac{1}{1+ \frac{1}{1}}} \qquad \frac{8}{5} = 1+\frac{1}{1+ \frac{1}{1+ \frac{1}{1+ \frac{1}{1}}}}_

Da diese Quotienten im Grenzwert gegen den goldenen Schnitt konvergieren, lasst sich dieser als der unendliche Kettenbruch

    ![\\Phi = 1+\\cfrac{1}{1+ \\cfrac{1}{1+ \\cfrac{1}{1+ \\cfrac{1}{1+\\dotsb}}}}](http://upload.wikimedia.org/math/2/9/3/2939b6d71c0b7aae0a53a8e343f4bd3f.png)

> _\Phi = 1+\cfrac{1}{1+ \cfrac{1}{1+ \cfrac{1}{1+ \cfrac{1}{1+\dotsb}}}}_

darstellen.

Die Zahl Φ ist [irrational](https://de.m.wikipedia.org/wiki/Irrationale_Zahl). Das bedeutet, dass sie sich nicht durch ein Verhaltnis zweier ganzer Zahlen darstellen lasst, ein Umstand, der wesentlich zu ihrer Bedeutung in Kunst und Natur beitragt. Am besten lasst sich Φ durch Quotienten zweier aufeinander folgender Fibonacci-Zahlen approximieren. Dies gilt auch fur verallgemeinerte Fibonaccifolgen, bei denen und beliebige naturliche Zahlen annehmen.

Das nach [Edouard Zeckendorf](https://de.m.wikipedia.org/wiki/Edouard_Zeckendorf) benannte Zeckendorf-Theorem besagt, dass jede naturliche Zahl _n_ großer Null eindeutig als Summe voneinander verschiedener, nicht direkt aufeinanderfolgender Fibonacci-Zahlen geschrieben werden kann. Das heißt, es gibt fur jedes eine eindeutige Darstellung der Form

Die entstehende Folge von Nullen und Einsen wird Zeckendorf-Sequenz genannt. Da aufeinanderfolgende Fibonacci-Zahlen ausgeschlossen sind, konnen keine zwei Einsen in einer Zeckendorf-Sequenz unmittelbar hintereinander stehen.

Allgemeiner ist die verwandte Aussage, dass sich jede _ganze_ Zahl _z_ eindeutig als Summe verschiedener, nicht direkt aufeinanderfolgender _negaFibonacci_-Zahlen ( mit ) darstellen lasst.

So ware zum Beispiel als Binarsequenz `1001` darstellbar.[[5]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge)

![](http://upload.wikimedia.org/wikipedia/commons/thumb/b/b6/Goldener_Schnitt_Bluetenstand_Sonnenblume.jpg/180px-Goldener_Schnitt_Bluetenstand_Sonnenblume.jpg)

> _Sonnenblume mit 34 und 55 Fibonacci-Spiralen_

![](http://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Fibonacci_numbers.jpg/180px-Fibonacci_numbers.jpg)

> _Anordnung gleich großer Kreise im Abstand des goldenen Winkels mit farblicher Markierung der Fibonacci-Spiralen 8, 13, 21, 34._

Viele Pflanzen weisen in der [Anordnung ihrer Blatter](https://de.m.wikipedia.org/wiki/Phyllotaxis) und anderer Teile [Spiralen](https://de.m.wikipedia.org/wiki/Spirale) auf, deren Anzahlen durch Fibonacci-Zahlen gegeben sind, wie beispielsweise bei den Fruchten in Fruchtstanden. Das ist dann der Fall, wenn der Winkel zwischen architektonisch benachbarten Blattern oder Fruchten bezuglich der Pflanzenachse der [Goldene Winkel](https://de.m.wikipedia.org/wiki/Goldener_Schnitt) ist. Hintergrund ist der Umstand, dass die rationalen Zahlen, die den zugrunde liegenden [Goldenen Schnitt](https://de.m.wikipedia.org/wiki/Goldener_Schnitt) am besten [approximieren](https://de.m.wikipedia.org/wiki/Approximation), Bruche von aufeinanderfolgenden Fibonacci-Zahlen sind. Die Spiralen werden daher von Pflanzenelementen gebildet, deren Platznummern sich durch die Fibonacci-Zahl im Nenner unterscheiden und damit fast in die gleiche Richtung weisen. Durch diese spiralformige Anordnung der Blatter um die Sprossachse erzielt die Pflanze die beste Lichtausbeute. Der Versatz der Blatter um das [irrationale](https://de.m.wikipedia.org/wiki/Irrationale_Zahl) Verhaltnis des Goldenen Winkels sorgt dafur, dass nie Perioden auftauchen, wie es z. B. bei 1/4 der Fall ware (0° 90° 180° 270° | 0° 90° …). Dadurch wird der denkbar ungunstigste Fall vermieden, dass ein Blatt genau senkrecht uber dem anderen steht und sich so die jeweils ubereinanderstehenden Blatter maximalen Schatten machen oder maximale ‚Lichtlucken' entstehen.

Beispielsweise tragen die [Korbe](https://de.m.wikipedia.org/wiki/Korb_\(Bl%C3%BCtenstand\)) der [Silberdistel](https://de.m.wikipedia.org/wiki/Silberdistel) (_Carlina acaulis_) hunderte gleichgestaltiger Bluten, die in kleineren Korben in einer 21-zu-55-Stellung, in großeren Korben in 34-zu-89- und 55-zu-144-Stellung in den Korbboden eingefugt sind.[[6]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge) Auch die Schuppen von Fichtenzapfen wie auch von Ananasfruchten bilden im und gegen den Uhrzeigersinn Spiralen, deren Schuppenanzahl durch zwei aufeinanderfolgende Fibonaccizahlen gegeben ist.[[7]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge)

Wissenschaftshistorisch sei hier auf das Buch _On Growth and Form_ von [D'Arcy Wentworth Thompson](https://de.m.wikipedia.org/wiki/D%E2%80%99Arcy_Wentworth_Thompson) (1917) verwiesen.

Ein weiterer interessanter Aspekt ist, dass die Fibonacci-Folge die Ahnenmenge einer mannlichen (_n_=1) Honigbiene ([Apis mellifera](https://de.m.wikipedia.org/wiki/Apis_mellifera)) beschreibt. Das erklart sich dadurch, dass Bienendrohnen sich aus unbefruchteten Eiern entwickeln, die in ihrem [Genom](https://de.m.wikipedia.org/wiki/Genom) dem Erbgut der Mutter (_n_=2) entsprechen, welche wiederum zwei Eltern besitzt (_n_=3), usw.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/5/55/Fibonacci_explicit_%28detail%29.png/175px-Fibonacci_explicit_%28detail%29.png)

> _Die Fibonacci-Folge (rot) als Differenz zweier Folgen mit irrationalen Gliedern (schwarz)._

Das explizite Bildungsgesetz fur die Glieder der Fibonacci-Folge wurde unabhangig voneinander von den franzosischen Mathematikern [Abraham de Moivre](https://de.m.wikipedia.org/wiki/Abraham_de_Moivre) im Jahr 1718 und [Jacques Philippe Marie Binet](https://de.m.wikipedia.org/wiki/Jacques_Philippe_Marie_Binet) im Jahr 1843 entdeckt. Dazwischen war sie aber auch den Mathematikern [Leonhard Euler](https://de.m.wikipedia.org/wiki/Leonhard_Euler) und [Daniel Bernoulli](https://de.m.wikipedia.org/wiki/Daniel_Bernoulli) bekannt, letzterer lieferte 1728 auch den vermutlich ersten Beweis.[[8]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge)

Die Fibonacci-Zahlen lassen sich direkt mittels

berechnen, wobei die beiden Losungen der [charakteristischen Gleichung](https://de.m.wikipedia.org/wiki/Charakteristische_Gleichung) sind und somit auch und gilt. Setzt man

ein, erhalt man die explizite Formel von Moivre-Binet

    ![f_n = \\frac{\\varphi^n-\\psi^n}{\\sqrt5}
           = \\frac1{\\sqrt 5} \\left\[\\Phi^n- \\left\(-\\frac1{\\Phi}\\right\)^n\\right\]
           = \\frac1{\\sqrt 5} \\left\[ \\left\(\\frac{1+\\sqrt 5}2\\right\)^n - \\left\(\\frac{1-\\sqrt 5}2\\right\)^n \\right\].](http://upload.wikimedia.org/math/6/3/5/63538d23d71ad955cc33058502ed8d0b.png)

> _f_n = \frac{\varphi^n-\psi^n}{\sqrt5} = \frac1{\sqrt 5} \left[\Phi^n- \left(-\frac1{\Phi}\right)^n\right] = \frac1{\sqrt 5} \left[ \left(\frac{1+\sqrt 5}2\right)^n - \left(\frac{1-\sqrt 5}2\right)^n \right]._

Bemerkenswert ist das Zusammenspiel zweier [irrationaler](https://de.m.wikipedia.org/wiki/Irrationale_Zahlen) Zahlen _φ_ und _ψ_, das zu einem ganzzahligen Ergebnis fuhrt. Die Abbildung zeigt die beiden Teilfolgen mit _φ_ und _ψ_ sowie deren Differenz. Der Einfluss von _ψn_ geht rasch gegen Null. Das kann man verwenden, um die Berechnung zu beschleunigen, indem man den Term ignoriert und das Ergebnis zur nachstgelegenen naturlichen Zahl rundet.

Einer der einfachsten Beweise gelingt induktiv. Wegen und ist der Induktionsanfang erfullt. Angenommen die Formel gelte fur alle Werte bis _n_. Wir zeigen nun, dass sie dann notwendigerweise auch fur n+1 gelten muss:

    ![f_{n-1}+f_n = \\frac{\\varphi^{n-1}-\\psi^{n-1}+\\varphi^n-\\psi^n}{\\sqrt5}
                   = \\frac{\\varphi^n\(1+\\frac1{\\varphi}\)-\\psi^n\(1+\\frac1{\\psi}\)}{\\sqrt5}
                   = \\frac{\\varphi^{n+1}-\\psi^{n+1}}{\\sqrt5}
                   = f_{n+1}
](http://upload.wikimedia.org/math/0/c/1/0c164c00d651de5744af685bfc652e3d.png)

> _Dabei haben wir benutzt, dass und der charakteristischen Gleichung bzw. genugen._

Nach dem Prinzip der vollstandigen Induktion muss nun die Formel fur alle _n_ gelten.

Die Formel von Binet kann mit Matrizenrechnung und dem [Eigenwertproblem](https://de.m.wikipedia.org/wiki/Eigenwertproblem) in der [Linearen Algebra](https://de.m.wikipedia.org/wiki/Lineare_Algebra) hergeleitet werden mittels folgendem Ansatz:

Nun transformiert man die Matrix in eine Diagonalmatrix durch Betrachtung als [Eigenwertproblem](https://de.m.wikipedia.org/wiki/Eigenwertproblem).

Es gilt , wobei die Matrix der Eigenvektoren und die Diagonalmatrix mit den Eigenwerten ist. Damit folgt:

![
\\begin{align}
\\begin{pmatrix}
0 & 1 \\\\
1 & 1
\\end{pmatrix}^n
\\begin{pmatrix}
f\(0\) \\\\
f\(1\)
\\end{pmatrix}
& = A^n
\\begin{pmatrix}
f\(0\) \\\\
f\(1\)
\\end{pmatrix}
= \\left\(TDT^{-1}\\right\)^n
\\begin{pmatrix}
f\(0\) \\\\
f\(1\)
\\end{pmatrix}
= TD^nT^{-1}
\\begin{pmatrix}
0 \\\\
1
\\end{pmatrix}\\\\
&=
\\begin{pmatrix}
\\frac{-1-\\sqrt{5}}{2} & \\frac{-1+\\sqrt{5}}{2}\\\\
1 & 1
\\end{pmatrix}
\\begin{pmatrix}
\\frac{1-\\sqrt{5}}{2} & 0 \\\\
0 & \\frac{1+\\sqrt{5}}{2}
\\end{pmatrix}^n
\\begin{pmatrix}
-\\frac{1}{\\sqrt{5}} & \\frac{\\sqrt{5}-1}{2\\sqrt{5}} \\\\
\\frac{1}{\\sqrt{5}} & \\frac{\\sqrt{5}+1}{2\\sqrt{5}}
\\end{pmatrix}
\\begin{pmatrix}
0 \\\\
1
\\end{pmatrix}\\\\
&=
\\begin{pmatrix}
\\frac{-1-\\sqrt{5}}{2} & \\frac{-1+\\sqrt{5}}{2}\\\\
1 & 1
\\end{pmatrix}
\\begin{pmatrix}
\\left\(\\frac{1-\\sqrt{5}}{2}\\right\)^n & 0 \\\\
0 & \\left\(\\frac{1+\\sqrt{5}}{2}\\right\)^n
\\end{pmatrix}
\\begin{pmatrix}
-\\frac{1}{\\sqrt{5}} & \\frac{\\sqrt{5}-1}{2\\sqrt{5}} \\\\
\\frac{1}{\\sqrt{5}} & \\frac{\\sqrt{5}+1}{2\\sqrt{5}}
\\end{pmatrix}
\\begin{pmatrix}
0 \\\\
1
\\end{pmatrix}\\\\
&=
\\begin{pmatrix}
\\frac{-1-\\sqrt{5}}{2}\\left\(\\frac{1-\\sqrt{5}}{2}\\right\)^n & \\frac{-1+\\sqrt{5}}{2}\\left\(\\frac{1+\\sqrt{5}}{2}\\right\)^n\\\\
\\left\(\\frac{1-\\sqrt{5}}{2}\\right\)^n & \\left\(\\frac{1+\\sqrt{5}}{2}\\right\)^n
\\end{pmatrix}
\\begin{pmatrix}
\\frac{\\sqrt{5}-1}{2\\sqrt{5}} \\\\
\\frac{\\sqrt{5}+1}{2\\sqrt{5}}
\\end{pmatrix}\\\\
&=
\\begin{pmatrix}
- \\frac{1}{\\sqrt{5}} \\left\(\\frac{1-\\sqrt{5}}{2}\\right\)^n + \\frac{1}{\\sqrt{5}} \\left\(\\frac{1+\\sqrt{5}}{2}\\right\)^n\\\\
- \\frac{1}{\\sqrt{5}} \\left\(\\frac{1-\\sqrt{5}}{2}\\right\)\\left\(\\frac{1-\\sqrt{5}}{2}\\right\)^n + \\frac{1}{\\sqrt{5}} \\left\(\\frac{1+\\sqrt{5}}{2}\\right\) \\left\(\\frac{1+\\sqrt{5}}{2}\\right\)^n
\\end{pmatrix}
\\\\
&=
\\begin{pmatrix}
\\frac{1}{\\sqrt{5}} \\left\[\\left\(\\frac{1+\\sqrt{5}}{2}\\right\)^n - \\left\(\\frac{1-\\sqrt{5}}{2}\\right\)^n\\right\]\\\\
\\frac{1}{\\sqrt{5}} \\left\[\\left\(\\frac{1+\\sqrt{5}}{2}\\right\)^{n+1} - \\left\(\\frac{1-\\sqrt{5}}{2}\\right\)^{n+1}\\right\]
\\end{pmatrix}
\\\\
&=
\\begin{pmatrix}
f\(n\) \\\\
f\(n+1\)
\\end{pmatrix}
\\end{align}](http://upload.wikimedia.org/math/e/a/c/eac55a1533f2c59cbf8ff9c1f975c9b3.png)

> _ \begin{align} \begin{pmatrix} 0 & 1 \\\ 1 & 1 \end{pmatrix}^n \begin{pmatrix} f(0) \\\ f(1) \end{pmatrix} & = A^n \begin{pmatrix} f(0) \\\ f(1) \end{pmatrix} = \left(TDT^{-1}\right)^n \begin{pmatrix} f(0) \\\ f(1) \end{pmatrix} = TD^nT^{-1} \begin{pmatrix} 0 \\\ 1 \end{pmatrix}\\\ &= \begin{pmatrix} \frac{-1-\sqrt{5}}{2} & \frac{-1+\sqrt{5}}{2}\\\ 1 & 1 \end{pmatrix} \begin{pmatrix} \frac{1-\sqrt{5}}{2} & 0 \\\ 0 & \frac{1+\sqrt{5}}{2} \end{pmatrix}^n \begin{pmatrix} -\frac{1}{\sqrt{5}} & \frac{\sqrt{5}-1}{2\sqrt{5}} \\\ \frac{1}{\sqrt{5}} & \frac{\sqrt{5}+1}{2\sqrt{5}} \end{pmatrix} \begin{pmatrix} 0 \\\ 1 \end{pmatrix}\\\ &= \begin{pmatrix} \frac{-1-\sqrt{5}}{2} & \frac{-1+\sqrt{5}}{2}\\\ 1 & 1 \end{pmatrix} \begin{pmatrix} \left(\frac{1-\sqrt{5}}{2}\right)^n & 0 \\\ 0 & \left(\frac{1+\sqrt{5}}{2}\right)^n \end{pmatrix} \begin{pmatrix} -\frac{1}{\sqrt{5}} & \frac{\sqrt{5}-1}{2\sqrt{5}} \\\ \frac{1}{\sqrt{5}} & \frac{\sqrt{5}+1}{2\sqrt{5}} \end{pmatrix} \begin{pmatrix} 0 \\\ 1 \end{pmatrix}\\\ &= \begin{pmatrix} \frac{-1-\sqrt{5}}{2}\left(\frac{1-\sqrt{5}}{2}\right)^n & \frac{-1+\sqrt{5}}{2}\left(\frac{1+\sqrt{5}}{2}\right)^n\\\ \left(\frac{1-\sqrt{5}}{2}\right)^n & \left(\frac{1+\sqrt{5}}{2}\right)^n \end{pmatrix} \begin{pmatrix} \frac{\sqrt{5}-1}{2\sqrt{5}} \\\ \frac{\sqrt{5}+1}{2\sqrt{5}} \end{pmatrix}\\\ &= \begin{pmatrix} - \frac{1}{\sqrt{5}} \left(\frac{1-\sqrt{5}}{2}\right)^n + \frac{1}{\sqrt{5}} \left(\frac{1+\sqrt{5}}{2}\right)^n\\\ - \frac{1}{\sqrt{5}} \left(\frac{1-\sqrt{5}}{2}\right)\left(\frac{1-\sqrt{5}}{2}\right)^n + \frac{1}{\sqrt{5}} \left(\frac{1+\sqrt{5}}{2}\right) \left(\frac{1+\sqrt{5}}{2}\right)^n \end{pmatrix} \\\ &= \begin{pmatrix} \frac{1}{\sqrt{5}} \left[\left(\frac{1+\sqrt{5}}{2}\right)^n - \left(\frac{1-\sqrt{5}}{2}\right)^n\right]\\\ \frac{1}{\sqrt{5}} \left[\left(\frac{1+\sqrt{5}}{2}\right)^{n+1} - \left(\frac{1-\sqrt{5}}{2}\right)^{n+1}\right] \end{pmatrix} \\\ &= \begin{pmatrix} f(n) \\\ f(n+1) \end{pmatrix} \end{align}_

Eine andere Herleitungsmoglichkeit folgt aus der Theorie zu [linearen Differenzengleichungen](https://de.m.wikipedia.org/wiki/Lineare_Differenzengleichung):

Sei eine [geometrische Folge](https://de.m.wikipedia.org/wiki/Geometrische_Folge), so ergibt sich:

Wenn also so gewahlt wird, dass die charakteristische Gleichung erfullt ist (also oder ), wird , d. h., erfullt die Fibonacci-Rekursion mit dem Rekursionsanfang und .

Die rekursive Folge , , hat die explizite Darstellung . Ebenso , , .

Mit und genugt durch die [Superpositionseigenschaft](https://de.m.wikipedia.org/wiki/Superposition_\(Mathematik\)) auch jede [Linearkombination](https://de.m.wikipedia.org/wiki/Linearkombination) der Fibonacci-Rekursion . Mit Hilfe eines linearen Gleichungssystems ergibt sich und , damit und . Folglich ergibt sich explizit .

Fur ergibt sich und , d. h. die klassische [Lucas-Folge](https://de.m.wikipedia.org/wiki/Lucas-Folge) mit explizit .

Die [erzeugende Funktion](https://de.m.wikipedia.org/wiki/Erzeugende_Funktion) der Fibonacci-Zahlen ist

Die auf der linken Seite stehende [Potenzreihe](https://de.m.wikipedia.org/wiki/Potenzreihe) konvergiert fur . Über die [Partialbruchzerlegung](https://de.m.wikipedia.org/wiki/Partialbruchzerlegung) erhalt man wiederum die Formel von Moivre-Binet.

Durch Entwicklung der obigen Erzeugenden Funktion in eine Potenzreihe um ergibt sich durch Koeffizientenvergleich ein Zusammenhang zwischen den Fibonacci-Zahlen und den Binomialkoeffizienten. Dies gelingt durch Einsetzen des Polynoms in die Potenzreihe fur mit und somit .

Nach Multiplikation mit _z_ ergibt sich , nach Umformen dieser Summe zu einer [Binomialreihe](https://de.m.wikipedia.org/wiki/Binomialreihe).

Die letzte Summe kann mittels Umbenennung der Summationsindizes vereinfacht werden zu .

Koeffizientenvergleich liefert schließlich .

Alternativ ergibt sich uber die Definition die Darstellung

Die Fibonacci-Zahlen tauchen auch als Eintrage der Potenzen der [Matrix](https://de.m.wikipedia.org/wiki/Matrix_\(Mathematik\)) auf:

Aus der Relation ergibt sich beispielsweise die erste oben angegebene Formel fur . beschreibt zugleich die Summationsvorschrift der Fibonacci-Folge, denn ihr Produkt mit einem Paar aufeinanderfolgender Fibonacci-Zahlen (als Spaltenmatrix geschrieben) ergibt das nachste Paar; entsprechend erzeugt das -te Paar aus dem Startpaar . Dies und die Tatsache, dass die Eigenwerte von gerade der [Goldene Schnitt](https://de.m.wikipedia.org/wiki/Goldener_Schnitt) und dessen Kehrwert (letzterer mit negativem [Vorzeichen](https://de.m.wikipedia.org/wiki/Vorzeichen_\(Zahl\))) sind, fuhren wieder auf die oben genannte Formel von Binet.

Fur große Werte von _n_ wird in der Formel von Binet immer kleiner, da der Ausdruck in der Klammer vom [Betrag](https://de.m.wikipedia.org/wiki/Betragsfunktion) ist. Deshalb erhalt man die Naherungsformel

Der Absolutbetrag des Quotienten ist fur alle n kleiner als 0,5. Demnach beschreibt die Naherungsformel das exakte Ergebnis mit einem Fehler von weniger als 0,5. Durch Runden kommt man daher wieder zu einer exakten Formel:

Die klassische („kanonische") Fibonacci-Folge ist durch drei Kriterien charakterisiert:

  * Eine lineare Iteration, welche die beiden vorangehenden Folgenglieder einbezieht
  * Eine Linearkombination dieser Folgenglieder, in der beide Vorganger den Koeffizienten +1 tragen
  * Beide Startglieder gleich +1

Jedes dieser Kriterien erlaubt eine Verallgemeinerung:

  * Die Wahl _anderer Startglieder_ und liefert eine Folge , die mit der kanonischen Folge nach der Beziehung zusammenhangt. Ein Beispiel hierfur ist die [Lucas-Folge](https://de.m.wikipedia.org/wiki/Lucas-Folge) .

    Fur die Glieder einer solchen Folge gilt ein gegenuber der Formel von Moivre-Binet verallgemeinertes explizites Bildungsgesetz: 
    Die kanonische Folge stellt sich hier als Spezialfall mit u=v=1 dar, was wegen der charakteristischen Gleichung sofort k=1 und l=1 liefert.

  * Die Wahl _anderer Koeffizienten_ fur die Linearkombination liefert eine Folge, fur die eine andere charakteristische Gleichung gilt. Eine Folge mit der Iterationsvorschrift

    besitzt die charakteristische Gleichung . Die Wurzeln dieser Gleichung bestimmen das explizite Bildungsgesetz. Wenn die charakteristische Gleichung die Wurzeln und hat, dann lautet das Bildungsgesetz 
    wobei k und l wieder durch die Startglieder bestimmt sind.

  * Eine Iteration, die _mehr als zwei vorangehende Folgenglieder_ einbezieht, besitzt dementsprechend ein Polynom hoheren Grades als charakteristische Gleichung, wobei die Wurzeln dieser Gleichung wieder im Bildungsgesetz auftauchen und die Koeffizienten durch die Anfangswerte bestimmt sind. Es gilt dann

    Eine Iteration, die nur das unmittelbar vorhergehende Glied verwendet, liefert in diesem Zusammenhang als entartete Fibonacci-Folge eine reine Potenzfolge.
![](http://upload.wikimedia.org/wikipedia/commons/thumb/0/04/Liber_abbaci_magliab_f124r.jpg/180px-Liber_abbaci_magliab_f124r.jpg)

> _Liber abbaci_

Ihre fruheste Erwahnung findet sich unter dem Namen _maatraameru_ („Berg der Kadenz") in der _Chhandah-shāstra_ („Kunst der [Prosodie](https://de.m.wikipedia.org/wiki/Versma%C3%9F)") des [Sanskrit](https://de.m.wikipedia.org/wiki/Sanskrit)-Grammatikers [Pingala](https://de.m.wikipedia.org/wiki/Pingala_\(Grammatiker\)) (um 450 v. Chr. oder nach anderer Datierung um 200 v. Chr.).[[9]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge) In ausfuhrlicherer Form behandelten spater auch [Virahanka](https://de.m.wikipedia.org/w/index.php?title=Virahanka&action=edit&redlink=1) (6. Jh.) und besonders dann [Acharya Hemachandra](https://de.m.wikipedia.org/w/index.php?title=Acharya_Hemachandra&action=edit&redlink=1) (1089-1172) diese Zahlenfolge, um die rechnerische Moglichkeit der Bildung von Metren durch regelmaßige Verteilung kurzer und langer Silben zu beschreiben.

In der westlichen Welt war diese Reihe ebenfalls schon in der Antike [Nikomachos von Gerasa](https://de.m.wikipedia.org/wiki/Nikomachos_von_Gerasa) (um 100 n. Chr.) bekannt.[[10]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge) Sie ist aber mit dem Namen des italienischen Mathematikers [Leonardo da Pisa](https://de.m.wikipedia.org/wiki/Leonardo_Fibonacci), genannt Fibonacci (_„figlio di Bonacci"_, Sohn des Bonacci), verbunden, der in seinem _Liber abbaci_ („Buch der Rechenkunst", Erstfassung von 1202 nicht erhalten, zweite Fassung von ca. 1227) diese Zahlenfolge mit dem Beispiel eines Kaninchenzuchters beschrieb, der herausfinden will, wie viele Kaninchenpaare innerhalb eines Jahres aus einem einzigen Paar entstehen, wenn jedes Paar ab dem zweiten Lebensmonat ein weiteres Paar pro Monat zur Welt bringt:[[11]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge)

Fibonacci illustrierte diese Folge durch die einfache [mathematische Modellierung](https://de.m.wikipedia.org/wiki/Mathematisches_Modell) des [Wachstums](https://de.m.wikipedia.org/wiki/Wachstum_\(Mathematik\)) einer [Population](https://de.m.wikipedia.org/wiki/Population_\(Biologie\)) von [Kaninchen](https://de.m.wikipedia.org/wiki/Kaninchen) nach folgenden Regeln:

  1. Jedes Paar Kaninchen wirft pro Monat ein weiteres Paar Kaninchen.
  2. Ein neugeborenes Paar bekommt erst im zweiten Lebensmonat Nachwuchs (die Austragungszeit reicht von einem Monat in den nachsten).
  3. Die Tiere befinden sich in einem abgeschlossenen Raum („in quodam loco, qui erat undique pariete circundatus"), so dass kein Tier die Population verlassen und keines von außen hinzukommen kann.

Fibonacci begann die Reihe, nicht ganz konsequent, nicht mit einem neugeborenen, sondern mit einem trachtigen Paar, das seinen Nachwuchs bereits im ersten Monat wirft, so dass im ersten Monat bereits 2 Paare zu zahlen sind. In jedem Folgemonat kommt dann zu der Anzahl der Paare, die im Vormonat gelebt haben, eine Anzahl von neugeborenen Paaren hinzu, die gleich der Anzahl derjenigen Paare ist, die bereits im vorvergangenen Monat gelebt hatten, da der Nachwuchs des Vormonats noch zu jung ist, um jetzt schon seinerseits Nachwuchs zu werfen. Fibonacci fuhrte den Sachverhalt fur die zwolf Monate eines Jahres vor (2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377) und wies auf das Bildungsgesetz der Reihe durch Summierung jeweils zweier aufeinanderfolgender Reihenglieder (2+3=5, 3+5=8, 5+8=13 usw.) hin. Er merkte außerdem an, dass die Reihe sich nach diesem Prinzip fur eine unendliche Zahl von Monaten fortsetzen lasst, was dann allerdings unsterbliche Kaninchen voraussetzt: _„et sic posses facere per ordinem de infinitis numeris mensibus."_ Weitere Beachtung hatte er dem Prinzip in seinen erhaltenen Werken nicht geschenkt.

Nachdem spatere Mathematiker wie [Gabriel Lame](https://de.m.wikipedia.org/wiki/Gabriel_Lam%C3%A9) (1795-1870) die Entdeckung dieser Zahlenfolge fur sich beansprucht hatten, brachten É[douard Lucas](https://de.m.wikipedia.org/wiki/%C3%89douard_Lucas) (1842-1891)[[12]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge) und andere wieder in Erinnerung, dass der zu dieser Zeit alteste bekannte Beleg von Leonardo da Pisa stammte, und unter dem Namen „Fibonacci-Folge" („suite de Fibonacci", „Fibonacci sequence", „successione di Fibonacci") ist sie seither in den meisten westlichen Sprachen gelaufig.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/4/43/Fibonaccis_Traum.jpg/220px-Fibonaccis_Traum.jpg)

> _Martina Schettina: Fibonaccis Traum, 2008, 40×40 cm_

![](http://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Diepholz_Skulpturenpfad_Fibonacci.JPG/170px-Diepholz_Skulpturenpfad_Fibonacci.JPG)

> _Petra Paffenholz: Fibonacci Cubes (Teil des Skulpturenpfades „Diepholz | Dummer"), 2014, 10 cm bis 5,50 m_

  * Das [Systemgedicht](https://de.m.wikipedia.org/wiki/Lyrik) _alfabet_ (1981) der danischen Schriftstellerin [Inger Christensen](https://de.m.wikipedia.org/wiki/Inger_Christensen) basiert auf der Fibonacci-Folge.
  * Das Cover des Debutalbums der kanadischen Band _The Organ_, [Grab That Gun](https://de.m.wikipedia.org/w/index.php?title=Grab_That_Gun&action=edit&redlink=1), wurde von [David Cuesta](https://de.m.wikipedia.org/w/index.php?title=David_Cuesta&action=edit&redlink=1) mithilfe eines auf der Fibonacci-Folge basierenden Rasters entworfen.[[13]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge)
  * Die Kunstler [Mario Merz](https://de.m.wikipedia.org/wiki/Mario_Merz) und Petra Paffenholz setzten sich in ihren Installationen mit der Fibonacci-Folge auseinander.
  * [Dan Brown](https://de.m.wikipedia.org/wiki/Dan_Brown) verwendet in seinem Thriller _The Da Vinci Code_ (2003) (deutsch: [Sakrileg](https://de.m.wikipedia.org/wiki/Sakrileg_\(Roman\)), 2004) die Fibonacci-Folge als geheime Botschaft.
  * Im Film _π[ - System im Chaos](https://de.m.wikipedia.org/wiki/Pi_\(Film\))_ von Darren Aronofsky, in dem der Protagonist nach dem „Muster der Welt" in den Kursdaten von Aktien und in der Zahl π sucht, wird die Fibonacci-Folge erwahnt.
  * In der Serie [Criminal Minds](https://de.m.wikipedia.org/wiki/Criminal_Minds) (Staffel 4, Folge 8) entfuhrt ein Killer seine Opfer anhand der Fibonacci-Folge.
  * In Lars von Triers Film _[Nymphomaniac](https://de.m.wikipedia.org/wiki/Nymphomaniac)_ wird im Kapitel 5 - kleine Orgelschule - die Fibonacci-Folge mit einem Bach-Orgelsatz in Verbindung gebracht.
  * In dem Videospiel [Watch Dogs](https://de.m.wikipedia.org/wiki/Watch_Dogs) von [Ubisoft](https://de.m.wikipedia.org/wiki/Ubisoft), in der Serienkiller-Mission als Zahlen, die an den einzelnen Tatorten der Opfer aufzufinden sind.[[17]](https://de.m.wikipedia.org/wiki/Fibonacci-Folge)
  * Richard A. Dunlap: _The Golden Ratio and Fibonacci Numbers_. 2. Auflage. World Scientific, Singapur, 1999, [ISBN 981-02-3264-0](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/9810232640).
  1. ↑ In manchen Buchern wird fur de Moivres Entdeckung auch 1730 angegeben oder auch die Entdeckung nur Binet zugeschrieben. Fur de Moivre, Bernoulli und Binet siehe dazu Beutelspacher (Albrecht Beutelspacher, Bernhard Petri: _Der Goldene Schnitt._ Spektrum, Heidelberg, Berlin, Oxford 1988. [ISBN 3-411-03155-7](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3411031557), S. 90) und Schroder (u. a. in: Herbert Schroder: _Wege Zur Analysis: Genetisch - Geometrisch - Konstruktiv._ Gabler 2001, [ISBN 3540420320](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3540420320), S. 12 ([Auszug (Google)](//books.google.de/books?id=jPQJIOzPcKkC&pg=PA12#v=onepage))). Dass die Formel zudem auch Euler bekannt war, findet man z. B. bei Winkler (Peter Winkler: _Mehr mathematische Ratsel fur Liebhaber._ Gabler 2010, [ISBN 9783827423498](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/9783827423498), S. 46 ([Auszug (Google)](//books.google.de/books?id=qyqJVjyW3k0C&pg=PA46#v=onepage))) oder Ben-Menahem (Ari Ben-Menahem: _Historical Encyclopedia of Natural and Mathematical Sciences. Band 1._ Springer 2009, [ISBN 9783540688310](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/9783540688310), S. ([Auszug (Google)](//books.google.de/books?id=9tUrarQYhKMC&pg=PA611#v=onepage)))
  2. ↑ Baldassare Boncompagni (Hrsg.): _Scritti di Leonardo Pisano matematico del secolo decimoterzo._ Bd. I, Tipografia delle scienze matematiche e fisiche, Rom, 1857, S. 283-284 (Kap. XII, 7: „Quot paria coniculorum in uno anno ex uno pario germinentur").
  3. ↑ Edouard Lucas: _Recherches sur plusieurs ouvrages de Leonard de Pise et sur diverses questions d'arithmetique superieure._ In: _Bulletino di bibliografia e di storia delle scienze matematiche e fisiche 10._ (1877), S. 129-193, S. 239-293.
