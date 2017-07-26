# Ist deklarativ wirklich instruktiv?

_Captured: 2015-11-30 at 01:26 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/entwicklung/methoden/deklarative-programmierung-ist-deklarativ-wirklich-instruktiv.html)_

**Wenn es darum geht, die Vorteile von Sprachelementen wie Closures oder Stream-Processing herauszustellen, wird sehr oft darauf verwiesen, dass sie einen deklarativ geprägten Programmierstil erlauben. Deklarative Programmierung wird dabei per se erstrebenswert und generell positiv bewertet. Ist diese Annahme richtig? Und was ist deklarative Programmierung überhaupt? Im Folgenden wird zunächst eine praktikable Abgrenzung des Begriffs versucht. Darauf aufbauend werden die sich ergebenden Problemfelder genauer betrachtet.  
**

![Ist deklarativ wirklich instruktiv? © iStock.com / loops7](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720-405-iStock-com-loops7_e28f561f5f.jpg)Ist deklarativ wirklich instruktiv? © iStock.com / loops7

Der Begriff Deklarative Programmierung ist nicht neu. Das Thema ist inzwischen über 40 Jahre alt, hat seine suggestive Kraft aber offensichtlich nicht verloren. Es scheint, dass insbesondere die Diskussionen um die Spracherweiterungen für Java 8 ihm neues Leben eingehaucht haben. Nicht alle sind darüber glücklich, etwas polemisch schreibt zum Beispiel Robert Haper in einem Blog-Beitrag „..I was surprised by the declarative zombie once again coming to eat our brains.” ![undefined](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[1]](entwicklung/methoden/deklarative-programmierung-ist-deklarativ-wirklich-instruktiv.html#c3096) Aber Lamentieren hilft nicht, wenn es darum geht, ein tieferes Verständnis für die Problematik dieses Begriffs zu erreichen. 

## Was ist deklarative Programmierung?

Wie so oft bei Schlagworten zeigt sich auch hier, dass eine klare und allgemein anerkannte Begriffsbildung fehlt. Teilweise werden logische und funktionale Programmierung dazu gerechnet, manchmal auch mathematische Modelle und domänenspezifische Fachsprachen. 

Gemeinsam ist allen Definitionsansätzen, dass sie als wichtiges Kennzeichen die Beschreibung des _Was _anstelle des _Wie _hervorheben. Während ein prozedurales Programm den Weg beschreibt, auf dem das gewünschte Ziel (=Ergebnis) erreicht werden kann, ist ein deklaratives Programm die genaue Beschreibung (Spezifikation) eben dieses Ergebnisses. Die deklarative Sicht ist daher vorwiegend statisch und entspricht am ehesten der Verwendung von Blaupausen als Produktvorlage. 

Wenn auf die Spezifizierung der Ausführung verzichtet wird, öffnet das Chancen für deren Optimierung. Im Idealfall kann der deklarative Code später einmal durch ein Verfahren ausgeführt werden, dass zum Zeitpunkt des Schreibens noch gar nicht bekannt war. Gern wird dabei auf die implizite Parallelisierung verwiesen. Doch wie im normalen Leben begegnet einem auch in der Programmierung der Idealfall höchst selten. 

Für die weitere Diskussion soll als Beispiel für eine eher deklarativ geprägte Programmiersprache SQL benutzt werden. Ein anderer prominenter Kandidat für diese Rolle ist HTML. Als typischer Vertreter prozeduraler Sprachen dient Java. 

Das Beispiel 1 stellt die beiden Paradigmen gegenüber. Während das (deklarative) SQL-Statement nur die Ergebnismenge definiert, beschreibt der Java-Code genau, wie das Ergebnis erzeugt werden soll. (Zu einer vollständigen Beschreibung fehlt noch der Code der verwendeten toString-Methode.)

**Beispiel 1: Vergleich prozedurale und deklarative Programmierung**

    
    
    **Java:**  
    for (datensatz: datensaetze) {  
      if (datensatz.id == 0)  
         System.out.println(datensatz.toString());  
     }
    
    
    **SQL: **  
    SELECT * FROM datensaetze WHERE id=0

Die Tatsache, dass deklarative Programme das _Was_, aber nicht das _Wie _einer Problemlösung beschreiben, macht es notwendig, dieses _Wie_ automatisch zu ermitteln. Die Implementierung einer deklarativen Programmiersprache erfordert daher zwingend die Existenz eines Algorithmus für das Finden und Zuordnen eines Ausführungsverfahrens. Diese Zuordnung wird Operationalisierung genannt. Sie setzt voraus, dass jedem korrekten Ausdruck in der Programmiersprache eine eindeutige Bedeutung zugeordnet werden kann. Die Definition der Bedeutung erfolgt dabei durch ein formales Modell des Objektbereichs. 

## Operationalisierung

In diesem Abschnitt werden einige wichtige Fragen, die bei der Implementierung deklarativer Programmiersprachen auftreten, diskutiert. 

### Existenz eines effektiven Verfahrens

Dies ist die Grundbedingung. Es muss mindestens ein Verfahren existieren, welches unter allen denkbaren Bedingungen einen zulässigen Ausgangszustand in den gewünschten (deklarierten) Endzustand überführt, d. h. effektiv ist. Das setzt ein gutes Verständnis und die Modellierbarkeit der zugrunde liegenden Domäne voraus. Für das Beispiel SQL ist diese theoretische Basis durch das relationale Datenmodell gegeben. Man sieht auch, dass es sich um einen klar beschränkten Objektbereich handelt. 

In semantisch reicheren Modellen zeigt sich leider oft, dass wichtige Fragen prinzipiell unentscheidbar sind. Dann bleibt zum einen der Rückgriff auf heuristische Verfahren und das Risiko einer unvollständigen Operationalisierung. Ein anderer Weg mit dieser Situation fertig zu werden ist, die formale Sprache zusätzlichen Restriktionen zu unterwerfen. Ein typisches Beispiel für diesen Weg liefern Parser für kontextfreie Sprachen. Sie werden üblicherweise durch die Regeln einer Grammatik beschrieben – ein klassischer Fall von deklarativer Programmierung. Die Form der zulässigen Regeln wird jedoch fast immer durch den verwendeten Algorithmus eingeschränkt. Genau genommen widersprechen solche Restriktionen dem deklarativen Charakter der Beschreibung. Aber während sich für Parser diese zusätzlichen Bedingungen auf der Ebene des Formalismus (als rechts- bzw. linksrekursive, LL(n), LR(n) usw.) beschreiben und überprüfen lassen, ist das in anderen Anwendungsbereichen selten der Fall. 

### Effizienz des Verfahrens

Wenn ein effektives Verfahren existiert, d. h. die Lösung prinzipiell möglich ist, stellt sich als nächstes die Frage nach der Effizienz dieses Verfahrens. Trotz der rasanten Entwicklung der Computertechnik wird die Verarbeitungsleistung immer ein Thema bleiben, weil dadurch u. a. Grenzen der Anwendbarkeit bestimmt werden. Grundsätzlich wird ein Verfahren umso effizienter gestaltet werden können, je besser es an die ganz konkrete Aufgabe angepasst wird. Es ist ein prinzipielles Dilemma der deklarativen Programmierung, dass bei der Operationalisierung besondere Eigenschaften des konkreten Anwendungsfalls nur begrenzt berücksichtigt werden können. 

Aufgaben mit einem begrenzten Lösungsraum können durch systematisches Durchprobieren aller Möglichkeiten gelöst werden. Dieser Ansatz ist jedoch wenig effizient und schränkt die mögliche Größe der behandelbaren Probleme stark ein. Auch bei speziellen Verfahren kann es vorkommen, dass die allgemeine Effizienz nicht den Anforderungen der Praxis genügt. Wenn kein besserer Algorithmus bekannt ist, gibt es unterschiedliche Wege, trotzdem akzeptable Implementierungen zu erreichen: 

  * Der deklarative Formalismus wird um operative Elemente erweitert, die helfen, den Suchraum einzuschränken. Um sie richtig zu verwenden sind gute Kenntnisse des (eigentlich verborgenen) Verfahrens unerlässlich. In diese Kategorie fallen die Indizes in SQL. Sie können – richtig angewandt – die Laufzeit erheblich beeinflussen, haben aber auch das Potential, aus einem (deklarativ) korrekten Statement eines zu machen, das (operativ) einen Deadlock erzeugt.
  * Für die Implementierung wird ein „besserer“ Algorithmus ausgewählt, der jedoch weitere Einschränkungen für den deklarativen Formalismus erfordert. Das muss keine schlechte Lösung sein. In vielen Fällen ist es allerdings schwierig, diese Einschränkungen in den Kategorien des Formalismus zu definieren ![undefined](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[1*](entwicklung/methoden/deklarative-programmierung-ist-deklarativ-wirklich-instruktiv.html#c3095). Muss man aber das unterliegende Ausführungsmodell zu genau kennen, entfällt ein wichtiger Vorteil des deklarativen Paradigmas.

Weil auf andere Weise die erforderliche Effizienz nicht erreicht werden kann, endet allerdings der praktische Einsatz eines deklarativen Programmiermodells viel zu oft in einer schwer zu beherrschenden Mischform mit zahlreichen prozeduralen Erweiterungen. 

Noch deutlicher als bei den Ergänzungen, die SQL zu einer mehr oder weniger „normalen“ Programmiersprache machen sollen, zeigt sich diese Konsequenz, wenn HTML durch JavaScript erweitert wird. 

### Implizite Abhängigkeiten

Deklarative Programme sollen effiziente Implementationen dadurch unterstützen, dass sie bewusst Freiheiten lassen. Festlegungen der Art „In diesem Fall ist das Ergebnis undefiniert.“ haben sich in der Praxis allerdings nicht bewährt. Das hat folgende Ursache: Die Richtigkeit eines formalen Ausdrucks wird häufig nicht durch eine abstrakte Prüfung, sondern durch einen Test mit einer konkreten Implementierung ermittelt. Ob dabei das undefinierte Verhalten adäquat berücksichtigt wird, ist praktisch nicht verifizierbar. Das Gefährliche an solchen verdeckten Implementationsabhängigkeiten ist, dass sie schwer oder gar nicht zu erkennen sind und dadurch kaum vermieden werden können. 

Neben solchen funktionalen Abhängigkeiten können auch nichtfunktionale auftreten, zum Beispiel in Bezug auf Laufzeit oder Speicherplatzbedarf. 

Dieser Punkt ist keine akademische Spitzfindigkeit, wie jeder bestätigen wird, der schon einmal SQL-Skripte von einem auf ein anderes DBMS migriert hat. 

## Das Basismodell

Das Modell, welches wie bereits erwähnt, die Bedeutung der deklarativen formalen Sprache definiert, ist der Dreh- und Angelpunkt. Es entscheidet sowohl über die Operationalisierbarkeit als auch die Anwendbarkeit in der Praxis. 

### Das semantische Modell

Deklarativen Ausdrücken liegt eine im Vergleich zu prozeduralen reichhaltigere Semantik zugrunde. Das ermöglicht auf der einen Seite kompaktere Beschreibungen, erfordert auf der anderen jedoch, dass dieses semantische Modell von allen gleichermaßen verstanden wird. 

Das ist eine wesentliche Restriktion des deklarativen Paradigmas: Es setzt voraus, dass ein hinreichend bekanntes Basismodell existiert. In der Informatik trifft das für viele einfache Strukturen zu, aber es fällt schwer, Beispiele zu finden, die mit der Komplexität des relationalen Datenmodells vergleichbar sind. 

Wichtig ist, dass die Konzepte des semantischen Modells möglichst orthogonal sind, wie das im Fall von SQL für Relationen und Datentypen gilt. Denn da es sich beim semantischen Modell um eine letztlich frei gewählte Abstraktion handelt, ist auch die Definition der Interaktionen der beteiligten Konzepte frei wählbar. Die Erfahrung zeigt, dass abhängig vom jeweiligen Modellierungsziel, solche Interaktionen verschieden interpretiert werden können und auch werden. Semantische Modelle mit Varianten, besonders wenn sich diese nur auf Details beziehen, sind jedoch eine denkbar schlechte Basis. Schließlich ist Programmtext immer auch Kommunikationsmedium zwischen Menschen. Diese Rolle kann eine deklarative Sprache nur erfüllen, wenn ihr semantisches Modell eindeutig verstanden wird und klar abgegrenzt ist. 

Aus diesen Überlegungen folgt weiter, dass das semantische Modell nicht zu komplex sein darf, weil die (lesende) Interpretation der deklarativen Beschreibung erfordert, alle jeweils für das Verständnis relevanten Konzepte parat zu haben. 

### Modellbeschränkungen

Ein Modell repräsentiert stets nur einen Teilaspekt, der durch die Mengen der modellierten Objekte und Operationen beschränkt wird. Leider halten sich die Wünsche der Anwender nicht an die Grenzen der Modelle. Ein einfaches Beispiel soll die Problematik illustrieren: Gefordert sei ein SQL-Select mit fortlaufender Nummerierung der Ergebnisdatensätze. Diese scheinbar triviale Funktion ist nicht einfach zu realisieren. Das liegt nicht an der Unzulänglichkeit von SQL, sondern daran, dass das Konzept Nummerierung kein Bestandteil der Relationentheorie ist. Wenn die Ergebnismenge vor der Nummerierung nicht sortiert wird, ist die Menge der Datensätze einschließlich Zeilennummer nicht mehr unabhängig von Implementationsdetails, wie z. B. der physischen Anordnung. D. h., eine einfache Nummerierung, wie sie bei prozeduraler Programmierung mittels einer Indexvariablen realisiert würde, führt aus dem Definitionsbereich des Modells hinaus. 

Wie eine modellkonforme Nummerierung aussehen könnte, zeigt das Beispiel 2 (entnommen aus ![undefined](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[2]](entwicklung/methoden/deklarative-programmierung-ist-deklarativ-wirklich-instruktiv.html#c3096)). Man sieht deutlich, dass an den Grenzen des Modells die Vorteile der deklarativen Beschreibung verschwinden. 

**Beispiel 2: MS SQL-Server – Ausgabe einer alphabetisch geordneten Liste von Autorennamen und –vornamen mit vorangestellter laufender Nummer**

    
    
    SELECT rank=count(*), a1.au_lname, a1.au_fname   
    FROM authors a1, authors a2   
    WHERE a1.au_lname + a1.au_fname >= a2.au_lname + a2.au_fname   
    GROUP BY a1.au_lname, a1.au_fname   
    ORDER BY rank 

## Handhabbarkeit 

Neben den erwähnten eher technischen und konzeptionellen Fragen wirft die deklarative Programmierung in ihrem Gebrauch durch den Menschen Probleme auf. 

### Menschen denken nur sehr eingeschränkt deklarativ

Die meisten Menschen sind in ihrem Denken stark handlungsorientiert, insbesondere wenn es um das Erreichen eines Ziels geht. Deklarative Beschreibungen werden, wie die schon erwähnten Blaupausen, vorrangig für die Darstellung statischer Objekte eingesetzt. Nur in Fällen, wo eine standardisierte Darstellungsform existiert und genügend Erfahrungen vorliegen, reicht eine solche Beschreibung als Handlungsanweisung aus. 

Wie schwer es Menschen fällt, deklarativ zu denken, kann man leicht am Beispiel von Zeitungsanzeigen demonstrieren. Selbst bei lauterstem Bemühen klafft zwischen implizit Vorgestelltem und explizit Spezifiziertem oft eine erhebliche Lücke. 

### Beeinflussbarkeit der Ausführung

Es ist gerade der größere Abstand zwischen Programmcode und Ausführung, der die anwendungsorientierte Beschreibung ermöglicht. Kein Vorteil ohne Preis: Durch diesen größeren Abstand kann der auf der Maschine ausgeführte Code weniger beeinflusst werden. In der Theorie ist das ein Vorteil. Auftretende Performanceprobleme sind durch andere oder bessere Operationalisierungen zu beheben und keine Aufgabe für Anwendungsentwickler. In der Praxis muss man oft mit dem Vorhandenen auskommen. Das heißt nicht selten, statt der kurzen und klaren Formulierung auf eine solche mit trickreichen Umwegen auszuweichen, um das Performanceziel doch noch zu erreichen. Die möglichen Vorteile deklarativen Programmierens werden dadurch gleich in zweierlei Hinsicht konterkariert: 

  1. Dadurch, dass die Sprachmittel, die zur Beschreibung des _Was _entworfen wurden, zur Beschreibung des _Wie _missbraucht werden, wird die Lesbarkeit zerstört. 
  2. Es wird genau das erreicht, was vermieden werden sollte: Die Beschreibung wird von einer speziellen Implementierung abhängig.

### Fehlersuche, Debugging

Der große Abstand zwischen Beschreibung und Ausführung erschwert die Analyse von Fehlern oder anderen unerwarteten Effekten. Spezielle Tools müssen gebaut und gewartet werden. Außerdem steigt die Wahrscheinlichkeit, dass die Implementierung der beteiligten Software selbst fehlerhaft ist, weil diese relativ komplizierter ist und wegen der höheren Spezialisierung weniger häufig verwendet wird. 

### Modellgrenzen

Im Zusammenhang mit dem Basismodell wurde bereits auf dessen Grenzen hingewiesen. Wenn das Modell die jeweilige Anwendungsdomäne nur teilweise überdeckt, wird man früher oder später an dessen Grenzen stoßen. Denn Software lebt. Erfolgreiche Anwendungen wachsen und werden erweitert. Beim Erreichen der Grenzen stellt sich die Frage: Wie weiter? Die logisch konsequente Antwort müsste sehr oft lauten: komplette Neuentwicklung auf allgemeinerer Basis. Praktisch ist das nur selten umsetzbar. Als Ausweg wird deshalb häufig versucht, die deklarative Sprache so zu erweitern, dass sie den zusätzlichen Anforderungen entspricht. Diese Erweiterungen werden sehr wahrscheinlich den deklarativen Charakter der Beschreibung zerstören. Es stellt sich die Frage, ob eine solche hybride Sprache überhaupt noch Vorteile bietet. 

Am Beispiel SQL lässt sich das gut zeigen. Für Anwendungsfälle, die sich nicht mehr im Rahmen des Relationenmodells beschreiben lassen, gibt es prozedurale Erweiterungen (PL – Procedural Language). Sie sind für fast jede Datenbank verfügbar. Die damit verfassten Skripte stehen allerdings nicht in dem Ruf gut wartbar zu sein, da schon bei einfachen Dingen Fallen lauern (vgl. z. B. für PL/SQL: „Types in PL/SQL can be tricky. … variable assignments and comparisons may not work the way you expect.” ![undefined](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[3]](entwicklung/methoden/deklarative-programmierung-ist-deklarativ-wirklich-instruktiv.html#c3096)). 

### Die verbleibende Unbestimmtheit

Ein deklaratives Programm beschreibt die unbedingt notwendigen Eigenschaften der gewünschten Implementierung. Im Allgemeinen ist es nicht möglich, die Vollständigkeit einer Spezifikation zu beweisen. Unterschiedliche Sichten auf das Anwendungsgebiet können zu unterschiedlichen Interpretationen dessen führen, was als vermeintlich unstrittig oder selbstverständlich nicht explizit festgelegt wird. Andererseits kann der Versuch, jedes Detail explizit erfassen zu wollen, zu einer unhandlichen Überspezifikation führen und damit die Wahrscheinlichkeit, dass Fehler passieren, erhöhen. 

An diesen Problemen ist schon vor mehr als 20 Jahren die automatische Verifikation von Programmen gescheitert. Deren Ziel war es, zu zeigen, dass ein zu prüfender Code, d. h. das Ergebnis der Operationalisierung, der Spezifikation, also der deklarativen Beschreibung entspricht. Obwohl die ursprünglichen technischen Probleme weitgehend gelöst werden konnten, spielt dieses Thema heute nur noch eine untergeordnete Rolle. 

Die verbleibende Unbestimmtheit kann zu einer Bremse für die Weiterentwicklung werden. Um eine bestehende Code-Basis nicht völlig zu entwerten, muss unter Umständen die Kompatibilität auf die bereits erwähnten impliziten Abhängigkeiten ausgedehnt werden. Radikale Wechsel der Implementationsstrategie werden somit erschwert, selbst wenn sie deutliche Verbesserungen bringen würden. 

## Schlussfolgerungen

Auch wenn hier vorrangig die problematischen Seiten thematisiert wurden, ist deklarative Programmierung nicht prinzipiell abzulehnen. Für den sinnvollen Einsatz müssen aber einige Voraussetzungen erfüllt sein. 

### Eine geeignete Aufgabe

Wenn es um ein Verfahren selbst geht, das beschrieben werden soll, ist der deklarative Weg ungeeignet. Programmiersprachen sind aus dem Bemühen heraus entstanden, Algorithmen exakt formulieren zu können. Man brauchte diese Ergänzung der viel älteren deklarativen mathematischen Formalismen einfach für die Steuerung von Computern. 

### Hinreichende Bekanntheit des Basismodells

Nur wenn das semantische Modell ausreichend präzise definiert und in dieser Definition bekannt ist, kann ein darauf basierender deklarativer Formalismus sinnvoll für die Beschreibung von Programmieraufgaben eingesetzt werden. 

### Existenz von Verfahren zur Operationalisierung

Deklarative Programmierung kann erfolgversprechend nur für Domänen und Modelle eingesetzt werden, für die hinreichend allgemeine Algorithmen für die effiziente Operationalisierung existieren. Sobald es notwendig ist, die deklarativen Ausdrücke um Hinweise für die Operationalisierung zu ergänzen, muss gefragt werden, ob ein prozeduraler Ansatz nicht geeigneter wäre. 

### Kombinierbarkeit

Wegen der unvermeidbaren Beschränkungen sind klare Schnittstellen wichtig. Anforderungen, die nicht im modellierten Bereich liegen, können dann sauber abgetrennt beschrieben werden. Allerdings müssen sich die zu lösenden Aufgaben sinnvoll in entsprechende Teile zerlegen lassen, um häufige Wechsel der Beschreibungsebene zu vermeiden. 

Der Umgang mit Grenzen der deklarativen Beschreibung muss von Anfang an Bestandteil des Entwurfs sein, um der späteren Degeneration des Formalismus vorzubeugen. 

Wenn diese prinzipiellen Beschränkungen beachtet werden, ein kommunizierbares Basismodell existiert und ausreichend viele Anwendungsfälle vollständig innerhalb dieses Modells formalisiert werden können, ist das deklarative Paradigma ein sehr nützliches Werkzeug. Wenn diese Voraussetzungen nicht erfüllt sind, ist es ein ziemlich sicherer Weg in die Probleme, die man eigentlich vermeiden wollte. 

Das bedeutet speziell für die eingangs erwähnten Java-Erweiterungen, dass sie sorgsam und nicht nur unter dem Gesichtspunkt kompakteren Codes verwendet werden sollten. Ein Lambda-Ausdruck verbessert die Lesbarkeit nur dann, wenn seine Bedeutung unmittelbar einsichtig ist. Andernfalls ist die explizite Schreibweise instruktiver.

**Quellen**

[1] [What, If Anything, Is A Declarative Language?](https://existentialtype.wordpress.com/2013/07/18/what-if-anything-is-a-declarative-language/)  
[2] [Dynamisches Nummerieren von Zeilen in einer SELECT Transact-SQL-Anweisung](http://support.microsoft.com/kb/186133/de)  
[3] [Using Oracle PL/SQL](http://infolab.stanford.edu/~ullman/fcdb/oracle/or-plsql.html)

1* Ein Beispiel dafür ist die bei naiver Implementierung von Parsern mittels rekursiven Abstiegs anzutreffende Bedingung, dass Alternativen so geordnet sein müssen, dass bei gemeinsamen Präfixen der längere immer vor dem kürzeren stehen muss, also nicht (int|integer), sondern umgekehrt, was bei Beteiligung von Nichtterminalen schwierig zu erkennen ist.

