# Funktionale Programmierung

_Captured: 2015-10-23 at 16:10 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Funktionale_Programmierung)_

**Funktionale Programmierung** ist ein [Programmierparadigma](https://de.m.wikipedia.org/wiki/Programmierparadigma), bei dem Programme ausschließlich aus Funktionen bestehen. Dadurch wird bewusst auf die aus der [imperativen Programmierung](https://de.m.wikipedia.org/wiki/Imperative_Programmierung) bekannten [Nebenwirkungen](https://de.m.wikipedia.org/wiki/Wirkung_\(Informatik\)) verzichtet.

Die funktionale Programmierung entspringt der akademischen Forschung. In den 1930er Jahren arbeiteten verschiedene Personen am [Lambda-Kalkul](https://de.m.wikipedia.org/wiki/Lambda-Kalk%C3%BCl). Hierbei geht es um Funktionen und deren Auswertung. Funktionale Sprachen sind Umsetzungen dieser Forschung.

Eine _funktionale Programmiersprache_ ist eine [Programmiersprache](https://de.m.wikipedia.org/wiki/Programmiersprache), die Sprachelemente zur Kombination und Transformation von Funktionen anbietet. Eine _rein funktionale Programmiersprache_ ist eine Programmiersprache, die die Verwendung von Elementen ausschließt, die im Widerspruch zum funktionalen Programmierparadigma stehen. Einige Autoren verwenden den Ausdruck „funktionale Programmiersprache" gleichbedeutend mit „rein funktionale Programmiersprache".

  * [Beispiele](https://de.m.wikipedia.org/wiki/Funktionale_Programmierung)

Der Begriff der Funktion wird in der Programmierung und der [Mathematik](https://de.m.wikipedia.org/wiki/Mathematik) mit unterschiedlicher Bedeutung verwendet (vergleiche [Funktion (Programmierung)](https://de.m.wikipedia.org/wiki/Funktion_\(Programmierung\)) und [Funktion (Mathematik)](https://de.m.wikipedia.org/wiki/Funktion_\(Mathematik\))). In der Mathematik wird eine Funktion als eine Abbildung der Funktionsargumente auf das jeweilige Funktionsergebnis betrachtet, so dass eine Funktion im mathematischen Sinne bei jeder Verwendung mit denselben Funktionsargumenten dasselbe Ergebnis liefert. Demgegenuber wird in der Informatik Funktion haufig als gleichbedeutend mit [Unterprogramm](https://de.m.wikipedia.org/wiki/Unterprogramm) verwendet. Anders als in der Mathematik brauchen in der Informatik Funktionen im allgemeinen Sprachgebrauch weder [werttreu](https://de.m.wikipedia.org/wiki/Werttreu) noch frei von einer [Wirkung](https://de.m.wikipedia.org/wiki/Wirkung_\(Informatik\)) (auch als Nebenwirkung oder Nebeneffekt bezeichnet) zu sein: Erstens kann das Ergebnis eines Aufrufs neben den beim Aufruf ubergebenen [Funktionsparametern](https://de.m.wikipedia.org/wiki/Funktionsparameter) auch von der Vorgeschichte der Funktionsaufrufe oder allgemeiner vom augenblicklichen Zustand des umgebenden [Computerprogramms](https://de.m.wikipedia.org/wiki/Computerprogramm) abhangen, und zweitens kann der Funktionsaufruf selbst Auswirkungen auf das zukunftige Verhalten anderer Funktionen haben.

Die Funktionen funktionaler Programmiersprachen verhalten sich hingegen wie mathematische Funktionen. Dies wird unter anderem erreicht, indem eine Zuweisung der Form

    `x = x + 1`

ausgeschlossen wird.

Mathematisch gelesen ergibt diese Zeile auch wenig Sinn, denn das ware eine Gleichung und es kame

heraus, was unwahr ist. Gemeint ist diese Zuweisung als

wobei das auf der linken Seite ein anderes ist, als das auf der rechten Seite. Das ist zwar fur die Programmierung nutzlich, entspricht aber nicht dem Verhalten von Variablen in der Mathematik, wo eine Variable , wenn sie einen Wert zugewiesen bekommen hat, genau diesen Wert immer behalt und nicht mal den einen und mal den anderen Wert im Verlauf einer Rechnung annimmt ([referenzielle Transparenz](https://de.m.wikipedia.org/wiki/Referenzielle_Transparenz)).

Ein Ansatz der funktionalen Programmierung ist, dass ihre Funktionen sich mehr wie mathematische Funktionen verhalten, damit die Rechen- und Beweismethoden der Mathematik besser auf Programme angewendet werden konnen (um vor allem ihre [Korrektheit](https://de.m.wikipedia.org/wiki/Korrektheit_\(Informatik\)) zu beweisen).

Sie vertritt weiter die Auffassung, dass Funktionen ein geeignetes Mittel zur [Modularisierung](https://de.m.wikipedia.org/wiki/Modularisierung) von Programmen darstellen, indem die Hauptfunktionen aus einer Vielzahl anderer Funktionen zusammengesetzt (komponiert) werden. Hierfur bieten funktionale Programmiersprachen verstarkte Unterstutzung, z. B. verhalten sich Funktionen weitestgehend wie andere Datentypen, konnen als Argumente und Ruckgabewerte verwendet werden ([Funktionen hoherer Ordnung](https://de.m.wikipedia.org/wiki/Funktionen_h%C3%B6herer_Ordnung)).

Der Programmierer legt fest, wie die Funktionen zusammengesetzt sind, es gibt jedoch noch Freiheiten in der Auswertung, die von Ü[bersetzern](https://de.m.wikipedia.org/wiki/Compiler) zu Optimierungszwecken genutzt werden konnen.

Im Gegensatz zu [imperativen Programmen](https://de.m.wikipedia.org/wiki/Imperative_Programmierung), die aus _Rechenanweisungen_ bestehen, sind funktionale Programme eine Menge von (Funktions)-_Definitionen_, die man mathematisch als [partielle Abbildungen](https://de.m.wikipedia.org/wiki/Partielle_Abbildung) von Eingabedaten auf Ausgabedaten auffassen kann.

Ein typisches Beispiel ist die Berechnung der [Fakultat](https://de.m.wikipedia.org/wiki/Fakult%C3%A4t_\(Mathematik\)) n! einer Zahl n (n! = 1 * 2 * 3 * ... * n), hier eine imperative Losung:

`Eingabe`
    `Zahl b (=1 * 2 * 3 * ... * n)`
`Algorithmus`
    `b := 1 (Zuweisung)`
    `**solange** n > 0 **fuhre aus**:`

    

    `b := n * b`

Charakteristisch fur die imperative Programmierung sind hier die Zuweisungen (Änderung von Werten, durch das Symbol „:=" im [Pseudocode](https://de.m.wikipedia.org/wiki/Pseudocode) reprasentiert). Zwar berechnet der Algorithmus die Fakultat der Zahl n, aber die Korrektheit dieses Rechenweges ist nicht offensichtlich.

Nun kann man die Fakultat jedoch auch mithilfe von [rekursiven Funktionen](https://de.m.wikipedia.org/wiki/Rekursion) definieren, was zur _funktionalen_ Losung fuhrt.

![n! = f\(n\) = \\begin{cases} n \\cdot f\(n-1\) &\\mathrm{f\\ddot ur}\\ \\ n > 0\\\\ 1 &\\mathrm{f\\ddot ur}\\ \\ n = 0\\end{cases}](http://upload.wikimedia.org/math/d/6/d/d6d903a8365a3ae2fcdca1761e90f4d0.png)

> _n! = f(n) = \begin{cases} n \cdot f(n-1) &\mathrm{f\ddot ur}\ \ n > 0\\\ 1 &\mathrm{f\ddot ur}\ \ n = 0\end{cases}_

`Funktion f(n)`
    `**wenn** n > 0 **dann**:`

    `_Ausgabe_: n*f(n-1)`
    `**sonst wenn** n = 0 **dann**:`

Die funktionale Programmierung kommt also ohne Schleifen und Zuweisungen aus, benotigt dafur aber Rekursion.

Die Machtigkeit einer Programmiersprache ist definiert durch die Menge an Problemen, die in dieser Programmiersprache entscheidbar sind. Die [theoretische Informatik](https://de.m.wikipedia.org/wiki/Theoretische_Informatik) hat gezeigt, dass eine reine funktionale Programmiersprache mit Rekursion gleich machtig ist wie eine imperative Programmiersprache, die Schleifen und Zuweisungen erlaubt (siehe [Turing-Vollstandigkeit](https://de.m.wikipedia.org/wiki/Turing-Vollst%C3%A4ndigkeit)). Dies zeigt, dass das Einhalten des funktionalen Paradigmas keinerlei Einschrankungen mit sich bringt, auch wenn dies auf den ersten Blick so scheinen mag.

Aus dem anderen Programmierparadigma ergibt sich im Vergleich zu den verbreiteteren imperativen Sprachen eine andere Herangehensweise bei der Konzeption von Programmen. Die wesentlichen Unterschiede manifestieren sich im Software-Engineering und in der Performance. Im Allgemeinen ergeben sich Vorteile bei der Konzeption und Wartbarkeit von Programmen, wahrend sich die hohe Abstraktion von der maschinellen Implementierung in performance-kritischen Anwendungen als Nachteil erweist.

Als historische theoretische Grundlage dient der λ[-Kalkul](https://de.m.wikipedia.org/wiki/Lambda-Kalk%C3%BCl) (Lambda-Kalkul) von [Alonzo Church](https://de.m.wikipedia.org/wiki/Alonzo_Church). Jeder Ausdruck und jeder Wert wird dabei als auswertbare Funktion betrachtet, so dass die ganze Programmierung auf der Übergabe von Funktionen als Parameter an Funktionen fußt.

Der Lambda-Kalkul erlaubt es, vollstandige Teilausdrucke separat auszuwerten. Dies ist der wichtigste Vorteil gegenuber der imperativen Programmierung. Dieses Konzept vereinfacht die [Programmverifikation](https://de.m.wikipedia.org/wiki/Verifikation) und [Programmoptimierung](https://de.m.wikipedia.org/wiki/Programmoptimierung), beispielsweise die Überfuhrung der Programme in eine [parallel auswertbare Form](https://de.m.wikipedia.org/wiki/Parallele_Programmierung).

Historisch ist [LISP](https://de.m.wikipedia.org/wiki/LISP) als die erste funktionale Programmiersprache aufzufassen; Sprachen der LISP-Familie (wie auch [Scheme](https://de.m.wikipedia.org/wiki/Scheme)) sind [dynamisch typisiert](https://de.m.wikipedia.org/wiki/Dynamische_Typisierung). Seit der Entwicklung von [Standard-ML (SML)](https://de.m.wikipedia.org/wiki/Standard_ML) konzentriert sich die Forschung auf dem Gebiet der funktionalen Programmiersprachen auch auf [statisch typisierte](https://de.m.wikipedia.org/wiki/Statische_Typisierung) Sprachen, insbesondere auf solche, die das Typsystem nach [Hindley und Milner](https://de.m.wikipedia.org/wiki/Hindley-Milner) verwenden. Der Vorteil dieses Typsystems ist die Verfugbarkeit von [parametrischem Polymorphismus](https://de.m.wikipedia.org/wiki/Polymorphie_\(Programmierung\)) zusammen mit [Typinferenz](https://de.m.wikipedia.org/wiki/Typinferenz): Programmierer mussen die Typen ihrer Funktionen und anderen Werte nicht angeben, sondern bekommen sie _gratis_ vom Übersetzer ausgerechnet, der zugleich noch wahrend der Übersetzung Typfehler monieren kann. Dies wird allgemein als wesentlicher Vorteil gegenuber dynamisch typisierten Sprachen ([LISP](https://de.m.wikipedia.org/wiki/LISP), [Python](https://de.m.wikipedia.org/wiki/Python_\(Programmiersprache\))) aufgefasst, die zwar ebenfalls keine Typannotationen benotigen (im Gegensatz z. B. zu [Java](https://de.m.wikipedia.org/wiki/Java_\(Programmiersprache\)) oder [C](https://de.m.wikipedia.org/wiki/C_\(Programmiersprache\))), dafur aber Typfehler erst zur Laufzeit anmahnen konnen. Letzteres hat jedoch wiederum den Vorteil einer breiteren Anwendbarkeit bereits definierter Funktionen auf ggf. zum Entwicklungszeitpunkt noch nicht vorhergesehene neue Einsatzgebiete.

Das Hindley-Milner-System erlaubt allerdings nur [Polymorphismus ersten Ranges](https://de.m.wikipedia.org/w/index.php?title=Polymorphismus_ersten_Ranges&action=edit&redlink=1); Erweiterungen fur Polymorphismus zweiten und allgemein k-ten Ranges sind inzwischen in dem [Haskell](https://de.m.wikipedia.org/wiki/Haskell_\(Programmiersprache\))-Übersetzer _GHC_ als Erweiterungen verfugbar, bedingen jedoch wieder explizite Annotationen (Typinferenz ab Polymorphismus zweiten Ranges ist [unentscheidbar](https://de.m.wikipedia.org/wiki/Entscheidbarkeit)).

Rein (engl. _pure_) funktionale Programmiersprachen fassen Programme als mathematische Funktion auf: Ein Ausdruck hat dort wahrend der Programmausfuhrung immer den gleichen Wert. Es gibt _keine Zustandsvariablen_, die wahrend einer Berechnung geandert werden. Um erwunschte Wirkungen (Benutzerinteraktion, Eingabe/Ausgabe-Operationen) beschreiben zu konnen, sind meist besondere Vorkehrungen notwendig. Die meisten funktionalen Programmiersprachen ([Standard ML](https://de.m.wikipedia.org/wiki/Standard_ML), [Caml](https://de.m.wikipedia.org/wiki/Caml), [Scheme](https://de.m.wikipedia.org/wiki/Scheme) und weitere) erlauben allerdings solche Wirkungen und sind daher keine reinen funktionalen Programmiersprachen.

Um Programmierung auch mit Wirkungen zu erlauben, ohne dabei zu einer sog. unreinen (engl. _impure_) Sprache zu werden, wurde bei der Entwicklung der Sprache [Haskell](https://de.m.wikipedia.org/wiki/Haskell_\(Programmiersprache\)) das aus der [Kategorientheorie](https://de.m.wikipedia.org/wiki/Kategorientheorie) stammende Konzept der [Monaden](https://de.m.wikipedia.org/wiki/Monade_\(Informatik\)) entwickelt (insbesondere von [Eugenio Moggi](https://de.m.wikipedia.org/w/index.php?title=Eugenio_Moggi&action=edit&redlink=1) und [Philip Wadler](https://de.m.wikipedia.org/w/index.php?title=Philip_Wadler&action=edit&redlink=1)), welches Wirkbehaftung durch [parametrische Typen](https://de.m.wikipedia.org/w/index.php?title=Parametrischer_Typ&action=edit&redlink=1) ausdruckt und somit das [Typsystem](https://de.m.wikipedia.org/wiki/Typsystem) dazu zwingt, zwischen Ausdrucken mit und Ausdrucken ohne Wirkungen zu unterscheiden. Auch in [Clean](https://de.m.wikipedia.org/wiki/Clean_\(Programmiersprache\)) und [Mercury](https://de.m.wikipedia.org/wiki/Mercury_\(Programmiersprache\)) wird das Typsystem verwendet, um solche Wirkungen zu kennzeichnen. Dort benutzt man allerdings das Konzept der "Uniqueness"-Typen.

Man unterscheidet Funktionen _erster Ordnung_ und Funktionen _hoherer Ordnung_. Bei Funktionen hoherer Ordnung sind Funktionen selbst Werte. Dies erlaubt es insbesondere, Funktionen als Ergebnisse oder Argumente anderer Funktionen zu verwenden. Ein typisches Beispiel ist der [Ableitungsoperator](https://de.m.wikipedia.org/wiki/Differentialrechnung): Eingabe ist eine differenzierbare Funktion, Ausgabe ist die Ableitung dieser Funktion. Ein weiteres Standardbeispiel ist die Funktion `map`, welche als Eingabe eine Funktion `f` und eine Liste `l` erhalt und die modifizierte Liste zuruckgibt, die dadurch entsteht, dass die Funktion `f` auf jedes Element der Liste `l` angewendet wird. Definition von `map` in [Haskell](https://de.m.wikipedia.org/wiki/Haskell_\(Programmiersprache\)):
    
    
     map f [] = []
     map f (x:xs) = f x : map f xs
    

    In der ersten Zeile wird das Ergebnis fur eine leere Liste [] zuruckgegeben; die zweite Zeile wendet die Funktion `f` auf das erste Listenelement _x_ an und fuhrt dann einen [Rekursionsschritt](https://de.m.wikipedia.org/wiki/Rekursion) fur die restliche Liste _xs_ durch.

Funktionale Sprachen kann man auch nach ihrer [Auswertungsstrategie](https://de.m.wikipedia.org/wiki/Auswertung_\(Informatik\)) unterscheiden: Bei _strikter Auswertung_ (engl. _eager_ bzw. _strict evaluation_) werden die Argumente von Funktionen zuerst ausgewertet. Dagegen werden bei der _nicht-strikten Auswertung_ zunachst die Ausdrucke als Ganzes ubergeben und dann ausgewertet.

Man kann zum Beispiel den Ausdruck auf zwei Arten berechnen:

Im ersten Fall wird der Ausdruck strikt ausgewertet, da erst die Argumente der Potenz-Funktion berechnet werden. Im zweiten Fall werden diese Argumente erst bei Bedarf ausgewertet, also nachdem die Potenzfunktion aufgelost wurde (nicht-strikte Auswertung).

Eine Variante der nicht-strikten Auswertung ist die _[Bedarfsauswertung](https://de.m.wikipedia.org/wiki/Bedarfsauswertung)_ (engl. _lazy evaluation_), bei der Ausdrucke erst ausgewertet werden, wenn deren Wert in einer Berechnung benotigt wird. Dadurch lassen sich z. B. unendlich große [Datenstrukturen](https://de.m.wikipedia.org/wiki/Datenstruktur) (die Liste aller naturlicher Zahlen, die Liste aller Primzahlen, etc.) definieren, und bestimmte Algorithmen vereinfachen sich.

Manche Berechnungen lassen sich mit strikter Auswertung, andere mit Bedarfsauswertung effizienter ausfuhren. Terminiert die strikte Auswertung eines Ausdruckes, so terminiert auch die nicht-strikte Auswertung. Hintergrund hiervon ist die [Konfluenz](https://de.m.wikipedia.org/wiki/Konfluenz_\(Informatik\))-Eigenschaft des jeder funktionalen Sprache zugrundeliegenden λ[-Kalkuls](https://de.m.wikipedia.org/wiki/Lambda-Kalk%C3%BCl), die aussagt, dass das Ergebnis der Berechnung nicht von der Reihenfolge der Auswertung abhangt.

[Algorithmen](https://de.m.wikipedia.org/wiki/Algorithmus) geben vorteilhafte Verfahren fur die Losung wichtiger Probleme an (z. B. [Sortieren](https://de.m.wikipedia.org/wiki/Sortieren)) und sind in der Regel gut analysiert, so dass ein Entwickler auf bewahrte, einschatzbare Losungen zuruckgreifen kann. Gleiches leisten [Datenstrukturen](https://de.m.wikipedia.org/wiki/Datenstruktur) fur die Organisation von Daten. Sammlungen von guten Algorithmen und Datenstrukturen haben somit eine große praktische Bedeutung.

Der Verzicht auf Zuweisungen fuhrt dazu, dass etliche klassische Algorithmen und Datenstrukturen, die regen Gebrauch von dieser Moglichkeit machen, so nicht fur funktionale Sprachen verwendet werden konnen und nach neuen Losungen gesucht werden muss.

[Chris Okasaki](https://de.m.wikipedia.org/w/index.php?title=Chris_Okasaki&action=edit&redlink=1) schreibt: _„Auch wenn die meisten dieser Bucher [uber Datenstrukturen] behaupten, dass sie unabhangig von einer bestimmten Programmiersprache sind, so sind sie leider nur sprachunabhangig im Sinne [Henry Fords](https://de.m.wikipedia.org/wiki/Henry_Ford): Programmierer konnen jede Programmiersprache benutzen, solange sie imperativ ist."_

Gerade rein funktionale Datenstrukturen sind von ihrer Natur her anders als die gewohnten Datenstrukturen, die meist nur eine Version ihrer Daten verwalten (ephemere Datenstrukturen), wohingegen funktionale Datenstrukturen mehrere Versionen verwalten (persistente Datenstrukturen).

Folgende Programme definieren eine Funktion `ringarea`, die die Flache berechnet, die zwischen den beiden konzentrischen Kreisen mit den [Radien](https://de.m.wikipedia.org/wiki/Radius) `R` und `r` bzw. `r1` und `r2` mit gemeinsamen Mittelpunkt liegt. Dazu werden die Konstante `pi` und die Hilfsfunktion `sq` definiert. Diese werden von `ringarea` dann fur die Berechnung benutzt.
    
    
     let ringarea (r1, r2) =
      let pi = 3.14 in
      let sq x = x*x in
      pi*(sq r1 - sq r2)
    
    
    
    sq :: (Floating a) => a -> a -- optionale explizite Typangabe
    sq x = x^2
    ringArea :: (Floating a) => a -> a -> a -- optionale explizite Typangabe
    ringArea r1 r2 = pi*(sq r1- sq r2)
    

Der Typ der Funktionen `sq, ringArea` ist polymorph und wird durch die Angabe der Typklasse `Floating` eingegrenzt. Die explizite Spezifikation des Typs ist optional und kann ebenso gut durch den Haskell-Compiler [inferenziert](https://de.m.wikipedia.org/wiki/Typableitung) werden. Pi ist in Haskell vordefiniert.

Hier eine komplexere Implementation, ausschließlich mit Hilfe von Funktionen hoherer Ordnung:
    
    
    ringArea' :: (Floating a) => a -> a -> a -- optionale explizite Typangabe
    ringArea' r1 r2 = foldr (-) 0 $ map ((*pi) . (^2)) [r1, r2]
    

    

    `pi == 3.14;`

[Joy](https://de.m.wikipedia.org/wiki/Joy_\(Programmiersprache\)) benutzt die [umgekehrte polnische Notation](https://de.m.wikipedia.org/wiki/Umgekehrte_polnische_Notation). Man beachte, dass hier alle Variablen Funktionen bezeichnen (auch _pi_ ist eine Funktion).

Jedes [Makefile](https://de.m.wikipedia.org/wiki/Make) stellt ein funktionales Programm dar.
    
    
      def pi: Double = 3.14
      def sq (x: Double) = x * x
      
      def ringarea(R: Double, r: Double) = pi * (sq(R) -  sq(r))
    
    
    
    (define (ringarea r1 r2)
     (define pi 3.14)
     (define (sq x) (* x x))
     (* pi (- (sq r1) (sq r2)))
    )
    

Alternativ mit Funktionen hoherer Ordnung:
    
    
    (define (ringarea r1 r2)
     (* 3.14 (foldr - 0 (map (lambda (x) (* x x)) (list r1 r2)))))
    

Der Typ von `x` muss hier explizit angegeben werden, da ein [SML97](https://de.m.wikipedia.org/wiki/SML97)-Übersetzer sonst den Typ _int_ inferieren wurde. Das zugrundeliegende Problem ist das der Ü[berladung](https://de.m.wikipedia.org/wiki/%C3%9Cberladen) von Operatoren; dieses Problem wurde erst mit Einfuhrung von Typklassen gelost, allerdings in Haskell und verwandten Sprachen.

[XSLT](https://de.m.wikipedia.org/wiki/XSLT) dient dem Transformieren von XML (insbesondere in XHTML) und hat zusammen mit XML stark an Bedeutung gewonnen. Sie ist funktional, wie Dimitre Novatchev gezeigt hat.[[1]](https://de.m.wikipedia.org/wiki/Funktionale_Programmierung) Die im folgenden Beispiel[[2]](https://de.m.wikipedia.org/wiki/Funktionale_Programmierung) definierte Funktion kehrt die Reihenfolge der Worter einer Zeichenkette um. Typisch fur funktionale Programmiersprachen ist der rekursive Aufruf. Der zweite Absatz zeigt, wie die Funktion verwendet wird.
    
    
    <xsl:function name="str:reverse" as="xs:string">
      <xsl:param name="sentence" as="xs:string"/>
      <xsl:choose>
        <xsl:when test="contains($sentence, ' ')">
          <xsl:sequence select="concat(str:reverse(
            substring-after($sentence, ' ')),
            ' ',
            substring-before($sentence, ' '))"/>
        </xsl:when>
        <xsl:otherwise>
          <xsl:sequence select="$sentence"/>
        </xsl:otherwise>
      </xsl:choose>
    </xsl:function>
    
    <xsl:template match="/">
    <output>
      <xsl:value-of select="str:reverse('DOG BITES MAN')"/>
    </output>
    </xsl:template>
    
    
    
    let pi = 3.14
    let square = {(x: Double) -> Double in x * x }
    let ringarea = {(r1: Double, r2: Double) -> Double in
        pi * (square(r1) - square(r2))
    }
    
