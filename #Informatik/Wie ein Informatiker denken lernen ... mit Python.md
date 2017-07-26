# Wie ein Informatiker denken lernen ... mit Python

by [Allen B. Downey](http://www.allendowney.com), [Jeffrey Elkner](mailto:jeff@elkner.net) and [Chris Meyers](mailto:cmeyers@guardnet.com)

Übersetzung der [englischen Fassung:](english/index.htm)   
How to Think Like a Computer Scientist  
von [Gregor Lingl](mailto:glingl@aon.at) und [Mike Muller](mailto:pyp@gmx.net)

_Captured: 2016-11-18 at 11:10 from [python4kids.net](http://python4kids.net/how2think/kap01.htm)_

# Über das Programmieren

## Kapitel 1

Das Ziel dieses Kurses ist es, dir beizubringen, wie ein Informatiker zu denken. Die Art wie Informatiker denken vereinigt die besten Zuge der Mathematik, der Ingenieur-Wissenschaften und der Naturwissenschaften. Wie Mathematiker benutzen Informatiker formale Sprachen um Ideen - insbesondere Berechnungen die von Computern ausgefuhrt werden sollen - aufzuschreiben. Wie Ingenieure entwerfen Informatiker Dinge, indem sie Komponenten zu Systemen zusammensetzen und Vor- und Nachteile von Alternativen uberdenken. Wie Wissenschaftler beobachten sie das Verhalten komplexer Systeme, formulieren sie Hypothesen und testen Voraussagen.

Die wichtigste einzelne Fahigkeit fur einen Informatiker ist **Problemlosen**. Damit ist die Fahigkeit gemeint, Probleme zu formulieren, kreativ uber Losungen nachzudenken und eine Losung klar und genau zu beschreiben. Programmieren lernen ist eine hervorragende Gelegenheit um Problemlosungs--Fertigkeiten zu entwickeln und zu uben. Deswegen heißt dieses Kapitel "Über das Programmieren"

Auf der einen Ebene wirst du lernen zu programmieren, was an sich eine nutzliche ertigkeit ist. Auf einer anderen Ebene wirst du Programmieren als Mittel zum Erreichen bestimmter Zwecke einsetzen. Im Verlauf des Lernens werden dir das Wie, Warum und Wozu klarer werden.

### 1.1 Die Programmiersprache Python

Die Programmiersprache, die du lernen wirst, ist Python. Python ist ein Beispiel fur eine **hohere Programmiersprache**; hohere Programmiersprachen werden oft auch **problemorientierte Sprachen** genannt. Andere hohere Programmiersprachen, von denen du vielleicht schon gehort hast sind C, C++, Perl und Java.

Wie du vielleicht schon aus dem Ausdruck "hohere Progammiersprache" schließt, gibt es auch Sprachen auf "niedrigerer Ebene", sogenannte **maschinenorientierte Sprachen**. Dazu gehoren Maschinensprachen und Assemblersprachen. Vereinfacht gesprochen konnen Computer nur Programme in Maschinensprache ausfuhren. D. h., dass Programme, die in einer hoheren Programmiersprache geschrieben sind, zunachst ubersetzt werden mussen, bevor sie ausgefuhrt werden konnen. Diese Übersetzung benotigt etwas Zeit, was einen kleinen Nachteil hoherer Programmiersprachen darstellt.

Aber ihre Vorteile sind gewaltig. Erstens ist es viel leichter in einer hoheren Programmiersprache zu programmieren; mit "leichter" meine ich: ein Programm zu schreiben benotigt weniger Zeit, es ist kurzer und leichter zu lesen und es ist mit hoherer Wahrscheinlichkeit korrekt. Zweitens sind hohere Programmiersprachen portierbar. D. h., dass sie auf verschiedenen Arten von Computern laufen konnen ohne - oder mit nur wenigen - Änderungen. Maschinenorientierte Sprachen konnen nur auf einer Art von Computer laufen und mussen fur andere Computertypen neu geschrieben werden.

Wegen dieser Vorteile werden heute fast alle Programme in hoheren Programmiersprachen geschrieben. Maschinenorienterte Sprachen werden nur fur wenige sehr spezielle Anwendungen verwendet.

Es gibt zwei Arten von Programmen, die hohere Programmiersprachen in maschinenorientierte Sprachen ubersetzen: **Interpreter** und **Compiler**. Ein Interpreter ist ein Programm, das ein Programm in einer hoheren Programmiersprache liest und ausfuhrt, was es sagt. Er ubersetzt das Programm zeilenweise, indem er abwechselnd eine Zeile liest und die Befehle, die dort stehen ausfuhrt.

Ein Compiler ist ein Programm, das ein Programm in einer hoheren Programmiersprache liest und als ganzes ubersetzt, bevor irgendwelche Befehle ausgefuhrt werden. In diesem Fall nennt man das in der hoherenProgrammiersprache geschriebene Programm den **Quellcode** und das ubersetzte Programm den **Objektcode** oder **executable**. ist ein Programm einmal kompiliert, kann man es wiederholt ohne weitere Übersetzung ausfuhren.

Python wird als eine Interpretersprache betrachtet, weil Python-Progamme von einem Interpreter ausgefuhrt werden. Es gibt zwei Arten, den Interpreter zu benutzen: den Kommandozeilen-Modus und den Script-Modus. Im Kommandozeilen-Modus tippst du Python-Anweisungen ein und der Interpreter gibt die Ergebnisse aus.

$ python

[GCC 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)] on linux2   
Type "copyright", "credits" or "license()" for more information.   
>>> print 1 + 1   
2   
>>>

Die erste Zeile dieses Beispiels ist der Befehl, der den Python-Interpreter startet. Die nachsten zwei Zeilen sind Meldungen des Interpreters. Die dritte Zeile beginnt mit >>>, das ist der "Prompt", mit dem der Interpreter anzeigt, das er bereit ist, Eingaben entgegenzunehmen. Wir haben print 1 + 1 eingetippt und der Interpreter antwortete mit 2.

Alternativ konnen wir ein Programm in eine Datei schreiben und den Interpreter dazu benutzen, den Inhalt dieser Programm-Datei auszufuhren. Eine solche Programm-Datei nennt man auch ein **Script**. Wir haben z. B. einen Texteditor benutzt, um eine Datei mit dem Namen latoya.py zu erzeugen, die folgenden Inhalt hat:

Vereinbarungsgemaß haben Dateien, die Python-Programme enthalten Namen, die mit .py enden.

Um das Programm auszufuhren, muss man dem Interpreter den Namen des Scripts mitteilen.

$ python latoya.py   
2

In anderen Programmierumgebungen konnen die Details der Programmausfuhrung etwas anders sein. Außerdem sind die meisten Programme interessanter als dieses hier.

Die meisten Beispiele in diesem Kurs werden von der Kommandozeile aus ausgefuhrt. Die Arbeit auf der Kommandozeile ist bequem fur die Programmentwicklung und fur das Testen, da man Pythonanweisungen eintippen und unmittelbar ausfuhren kann. Wenn man einmal ein funktionierendes Programm hat, wird man es in einem Script abspeichern, damit man es spater immer wieder ausfuhren oder auch abandern kann.

### 1.2 Was ist ein Programm?

Ein **Programm** ist eine Folge von Anweisungen, die angeben, wie eine "Berechnung" \- computation - durchzufuhren ist. Diese "Berechung" kann etwas mathematisches sein, wie z.B. das Losen eines Systems von Gleichungen oder die Berechnung der Nullstellen eines Polynoms, aber sie kann auch eine symbolische Berechnung sein, wie etwa suchen und ersetzen von Text in einem Dokument oder - seltsam genug - das Kompilieren eines Programms.

Die Details sehen in verschiedenen Progammiersprachen verschieden aus. Es gibt aber ein paar grundlegende Funktionen, die in jeder Programmiersprache vorkommen (mussen):

Ob du es glaubst oder nicht, das ist im Grunde alles was man braucht. Jedes Programm, das du jemals benutzt hast, ganz egal wie kompliziert es war, wird aus Funktionen aufgebaut, die mehr oder weniger wie diese aussehen. Daher kann man Programmieren so beschreiben: Programmieren ist ein Prozess, in dem man große, komplexe Aufgaben in kleine und immer kleinere Teilaufgaben zerlegt, bis schließlich die Teilaufgaben einfach genug sind, um mit einer dieser einfachen Funktionen ausgefuhrt werden zu konnen.

Das wird dir alles ein bisschen vage vorkommen. Aber wir kommen auf dieses Thema spater zuruck, wenn wir uber **Algorithmen** sprechen werden.

### 1.3 Was ist Debugging?

Programmieren ist ein komplexer Prozess; weil es von Menschen ausgefuhrt wird, treten haufig Fehler auf. Merkwurdigerweise werden Programmierfehler als **bugs** bezeichnet. Dementsprechend wird der Vorgang der Fehlersuche und der Fehlerbehebung als **debugging** bezeichnet.

Es gibt drei verschiedene Arten von Fehlern, die in einem Programm auftreten konnen. Um sie schneller auffinden zu konnen ist es nutzlich, zwischen ihnen zu unterscheiden.

#### Syntaxfehler

Python kann ein Programm nur ubersetzen, wenn das Programm syntaktisch korrekt ist; andernfalls schlagt der Vorgang fehl und es wird eine Fehlermeldung ausgegeben. **Syntax** bezieht sich auf die Struktur eines Programms und auf die Regeln fur diese Struktur. Zum Beispiel muss im Deutschen ein Satz mit einem Großbuchstaben beginnen und mit einem Punkt enden. dieser Satz enthalt einen **Syntaxfehler**. Und dieser auch

Fur die meisten Leser stellen ein paar Syntaxfehler kein Problem dar, weswegen wir auch moderne Lyrik, zum Beispiel von E. E. Cummings, lesen konnen ohne dauernd Syntaxfehlermeldungen auszuspucken (Siehe [Anhang E](http://python4kids.net/how2think/anh05.htm)). Python ist nicht so nachsichtig. Wenn auch nur ein einziger Syntaxfehler in deinem Programm ist, wird Python eine Fehlermeldung ausgeben und seine Tatigkeit - die Übersetzung - abbrechen. Dein Programm kann dann nicht ausgefuhrt werden. Wahrend der ersten Wochen deiner Programmierer-Karriere wirst du wahrscheinlich viel Zeit damit zubringen, deine Syntax-Fehler zu suchen (und hoffentlich zu finden). Mit zunehmender Erfahrung wirst du immer weniger Fehler machen und sie auch schneller finden.

#### Laufzeit-Fehler

Die zweite Art von Fehler sind Laufzeitfehler. Sie heißen so, weil sie erst auftreten, wenn das Programm ausgefuhrt wird. Diese Fehler werden auch **Ausnahmen** _(englisch: exceptions)_ genannt, weil sie normalerweise vorkommen, wenn etwas ungewohnliches _(englisch: exceptional)_ (und schlimmes) eingetreten ist.

Fur die einfache Art von Programmen, die wir in den nachsten paar Wochen schreiben werden, sind Laufzeitfehler selten. Daher wird es vielleicht noch eine Weile dauern, bis dir die ersten unterkommen.

#### Logische Fehler und Semantik

Der dritte Typ von Fehler ist der **logische** oder **semantische** Fehler. Wenn dein Programm einen logischen Fehler enthalt, wird es erfolgreich kompiliert und ausgefuhrt werden konnen in dem Sinn, dass der Computer keine Fehlermeldungen erzeugt. Aber es wird nicht das Richtige tun, sondern etwas anderes. Insbesondere wird es das tun, was du ihm aufgetragen hast zu tun.

Das Problem ist, dass das Programm, das du geschrieben hast nicht das Programm ist, das du schreiben wolltest (oder solltest). Die Bedeutung des Programms (seine Semantik) ist falsch. Logische Fehler zu identifizieren kann schwierig sein. Es erfordert, dass du ausgehend von der Ausgabe des Programms ruckwarts arbeitest und so versuchst herauszufinden, was es wirklich tut.

#### Experimentelles debugging

Eine der wichtigsten Fertigkeiten, die du dir wahrend dieses Kurses aneignen wirst ist debugging - die Fehlersuche. Obwohl es frustrierend sein kann, ist debugging eine der intellektuell anspruchsvollsten, herausforderndsten und interessantesten Teile des Programmierens.

In mancher Hinsicht ist debugging wie Detektivarbeit. Du hast einige Indizien (Hinweise) zur Verfugung und du musst auf die Vorgange zuruckschließen, die zu den Ergebnissen fuhren, die du siehst.

Debugging ist auch wie eine experimentelle Wissenschaft. Hast du erst einmal eine Idee, was falsch lauft, kannst du dein Programm abandern und neuerlich versuchen. War deine Hypothese korrekt, dann kannst du das Ergebnis der Abanderung voraussagen und du bist einen Schritt naher an einem korrekt arbeitenden Programm. War deine Hypothese falsch, musst du eine neue aufstellen. Wie Sherlock Holmes sagte: "When you have eliminated the impossible, whatever remains, however improbable, must be the truth." (A. Conan Doyle, _The Sign of Four_)

Fur manche Leute ist Programmieren und Debugging dieselbe Sache: Programmieren ist der Prozess ein Programm Schritt fur Schritt zu debuggen bis es das tut, was du willst. Dahinter steckt die Idee, dass du immer mit einem arbeitenden Programm beginnen solltest, das _irgendetwas_ tut, und dann kleine Änderungen ausfuhrst, die du wahrend des Programmierens von ihren Fehlern befreist, so dass du immer ein lauffahiges Programm hast.

So ist z. B. Linux ein Betriebssystem, das Tausende Zeilen von Code enthalt. Aber es begann als ein eifaches Programm, das Linus Thorvalds dazu benutzte, den Intel 80386-Chip zu erforschen. Larry Greenfield formulierte das so: "One of Linus's earlier projects was a program that would switch between printing AAAA and BBBB. This later evolved to Linux" (from _The Linux Users' Guide_ Beta Version 1).

In spateren Kapiteln werde ich weitere Anregungen uber Debugging und andere Programmiertechniken geben.

### 1.4 Formale und naturliche Sprachen

**Naturliche Sprachen** sind die Sprachen, die die Menschen sprechen, wie Englisch, Franzosisch und Deutsch. Sie sind nicht von Menschen entworfen worden (obwohl sie versuchen ihnen eine gewisse Ordnung aufzuerlegen); sie haben sich _naturlich_ entwickelt.

**Formale Sprachen** sind Sprachen, die von Menschen fur bestimmte Anwendungszwecke entworfen wurden. Z. B. ist die Formelschreibweise der Mathematik eine formale Sprache, die besonders gut geeignet ist, Beziehungen zwischen Zahlen und Symbolen auszudrucken. Chemiker benutzen eine formale Sprache um die chemische Struktur von Molekulen darzustellen. Und am wichtigsten fur uns:

> **Programmiersprachen sind formale Sprachen, die entworfen wurden um Berechnungen (computations) auszudrucken.**

Wie ich oben erwahnt habe, haben formale Sprachen ziemlich strikte Regeln fur ihre Syntax. Zum Beispiel ist 3+3=6 ein syntaktisch korrekter mathematischer Ausdruck, 3=+6$ aber nicht. H2O ist ein syntaktisch korrekter chemischer Name, im Gegensatz zu 2Zz.

Es gibt zwei Arten von Syntax-Regeln: solche, die sich auf sogenannte **token** beziehen und solche die sich auf die Struktur eines Programms beziehen. Token sind die Elementarbestandteile der Sprache, wie Worter und Zahlen und chemische Elemente. Eines der Probleme bei 3=+6$ ist, dass $ kein legales Token in der Mathematik ist (soweit ich weiß). Ähnlich ist 2Zz nicht legal, weil es kein Element mit der Abkurzung Zz gibt.

Die zweite Art von Syntax-Fehler bezieht sich auf die Struktur (die Gestalt) einer Anweisung; d. h. auf die Art und Weise, wie die Token angeordnet sind. Die Zeichenfolge 3=+6$ ist strukturell illegal, weil ein Plus-Zeichen nicht unmittelbar nach einem Gleichheitszeichen auftreten darf. Ähnlich mussen chemische Formeln ihre Indizes nach dem Elementnamen haben und nicht davor.

> _Als Übung erzeuge einen Satz der wie ein wohlstrukturierter deutscher Satz aussieht, der aber unerkennbare Token enthalt. Dann schreibe einen anderen Satz auf, mit ausschließlich gultigen Tokens, aber ungultiger Struktur._

Wenn du einen deutschen Satz liest oder eine Anweisung in einer formalen Sprache, musst du herausfinden, was die Struktur des Satzes ist (obwohl man das bei einer naturlichen Sprache in der Regel unbewusst tut). Dieser Vorgang heißt **parsen**.

Wenn du z. B. den Satz horst: "Der andere Schuh fiel, " so verstehst du, dass "der andere Schuh" das Subjekt ist und "fiel" das Pradikat. Wenn du einmal einen Satz "geparst" hast, also seine Struktur erkannt hast, kannst du seine Bedeutung ermitteln, d. h. seine Semantik. Angenommen, du weißt was ein Schuh ist, und was es bedeutet zu fallen, wirst du die allgemeine Aussage dieses Satzes verstehen.

Obwohl formale und naturliche Sprachen viele Eigenschaften gemeinsam haben -- Token, Struktur, Syntax, Semantik -- gibt es viele Unterschiede:

Alle Menschen wachsen mit naturlichen Sprachen auf, und vielen fallt es schwer sich an formale Sprachen zu gewohnen. In mancher Hinischt ist der Unterschied zwischen formaler und naturlicher Sprache wie der Unterschied zwischen Prosa und Lyrik:

Hier einige Anregungen fur das Lesen von Programmen (und anderer formaler Sprachen). Erstens bedenke, dass formale Sprachen viel dichter sind, als naturliche Sprachen; also braucht man langer, um sie zu lesen. Zweitens ist die Struktur sehr wichtig. Daher ist es im Allgemeinen keine gute Idee, ein Programm von oben nach unten und von links nach rechts zu lesen. Statt dessen lerne, das Programm in deinem Kopf zu "parsen", die Token zu identifizieren und die Struktur zu interpretieren. Drittens bedenke, dass es auf Details ankommt. Kleine Dinge, wie Tippfehler und falsche Zeichensetzung, die bei naturlicher Sprache keine große Rolle spielen, konnen in einer formalen Sprache einen großen Unterschied ausmachen.

### 1.5 Das erste Programm

Traditionellerweise ist das erste Programm, das man in einer neuen Sprache schreibt das "Hello, World!" \- Programm. Es tut nichts anderes, als die Worter "Hello, World!" auszugeben. In Python schaut dieses Programm so aus:

print "Hello, World!"

Das ist ein Beispiel einer **print - Anweisung**, die aber nichts auf Papier druckt. Sie zeigt einen **Wert** auf dem Bildschirm an. In diesem Beispiel besteht das Ergebnis aus den Worten

Hello, World!

Die Anfuhrungszeichen markieren in dem Programm nur den Beginn und das Ende des Wertes, sie werden im Ergebnis nicht dargestellt.

Manche Leute beurteilen die Qualitat einer Programmiersprache danach, wie einfach das "Hello, World." \- Programm ist. Gemessen an diesem Kriterium schneidet Python ziemlich optimal ab.

### 1.6 Glossary

**Problemlosen**
    Der Prozess, ein Problem zu formulieren, eine Losung zu finden und diese Losung darzustellen.
**problem solving**
    The process of formulating a problem, finding a solution, and expressing the solution.

**hohere Programmiersprache**
    Eine Programmiersprache wie Python, die so entworfen ist, dass sie fur Menschen leicht zu lesen und zu schreiben ist..
**high-level language**
    A programming language like Python that is designed to be easy for humans to read and write.

**maschinenorientierte Sprache**
    Eine Programmiersprache, die so entworfen ist, dass sie fur einen Computer leicht auszufuhren ist. (Maschinensprache oder Assemblersprache)
**low-level language**
    A programming language that is designed to be easy for a computer to execute; also called "machine language" or "assembly language."

**Portabilitat**
    Die Eigenschaft eines Programms, auf mehr als einer Art von Computern ausgefuhrt werden zu konnen.
**portability**
    A property of a program that can run on more than one kind of computer.

**interpretieren**
    Ein Programm in einer hoheren Programmiersprache zeilenweise ubersetzen und ausfuhren.
**interpret**
    To execute a program in a high-level language by translating it one line at a time.

**kompilieren**
    Ein Programm in einer hoheren Programmiersprache als Ganzes auf einmal ubersetzen, als Vorbereitung fur spatere Ausfuhrung.
**compile**
    To translate a program written in a high-level language into a low-level language all at once, in preparation for later execution.

**Quellcode**
    Ein Programm in einer hoheren Programmiersprache, bevor es kompiliert wird.
**source code**
    A program in a high-level language before being compiled.

**Objektcode**
    Der Output des Compilers nach der Übersetzung des Programms
**object code**
    The output of the compiler aftertranslating the program.

**executable**
    Ein anderer Name fur Objectcode, der fur die Ausfuhrung vorbereitet wurde.
**executable**
    Another name for object code that is ready to be executed.

**script**
    Ein Programm, das in einer Datei gespeichert ist. (Im allgemeinen eines, das interpretiert wird).
**Script**
    A program stored in a file (usually one that will be interpreted).

**Programm**
    Eine Folge von Anweisungen, die eine Berechnung festlegen.
**program**
    A set of instructions that specifies a computation.

**Algorithmus**
    Eine allgemeine Vorschrift um eine Klasse von Problemen zu losen.
**algorithm**
    A general process for solving a category of problems.

**bug**
    Ein Fehler in einem Programm.
**bug**
    An error in a program.

**debugging**
    Das Auffinden und Entfernen von jeder der drei Arten von Programmierfehlern.
**debugging**
    The process of finding and removing any of the three kinds of programming errors.

**Syntax**
    Die Struktur eines Programms.
**syntax**
    The structure of a program.

**Syntaxfehler**
    Ein Fehler in einem Programm, der es unmoglich macht, dieses zu parsen, und daher auch unmoglich es zu interpretieren.
**syntax error**
    An error in a program that makes it impossible to parse (and therefore impossible to interpret).

**Laufzeit-Fehler**
    Ein Fehler, der erst bei der Ausfuhrung eines Programms auftritt und der bewirkt, das die Programmausfuhrung nicht fortgesetzt werden kann.
**runtime error**
    An error that does not occur until the program has started to execute but that prevents the program from continuing.

**Ausnahme**
    Andere Bezeichnung fur einen Laufzeitfehler.
**exception**
    Another name for a runtime error.

**logischer Fehler**
    Ein Fehler in einem Programm, der bewirkt, dass dieses etwas anderes macht, als der Programmierer beabsichtigt hat.
**semantic error**
    An error in a program that makes it do something other than what the programmer intended.

**Semantik**
    Die Bedeutung (der Inhalt) eines Programms.
**semantics**
    The meaning of a program.

**naturliche Sprache**
    Eine von Menschen gesprochene Sprache, die sich naturlich entwickelt hat.
**natural language**
    Any one of the languages that people speak that evolved naturally.

**formale Sprache**
    Eine von Menschen fur bestimmte Zwecke entworfene Sprache, wie z.B. fur die Darstellung mathematischer Ideen oder von Computer-Programmen. Alle Programmiersprachen sind formale Sprachen
**formal language**
    Any one of the languages that people have designed for specific purposes, such as representing mathematical ideas or computer programs; all programming languages are formal languages.

**Token**
    Eines der grundlegenden Elemente der syntaktischen Struktur eines Programms, ahnlich etwa einem Wort in einer naturlischen Sprache.
**token**
    One of the basic elements of the syntactic structure of a program, analogous to a word in a natural language.

**parsen**
    Ein Programm auf seine syntaktische Struktur untersuchen und analysieren.
**parse**
    To examine a program and analyze the syntactic structure.

**print-Anweisung**
    Eine Anweisung, die den python-Interpreter veranlasst, einen Wert auf den Bildschirm zu schreiben.
**print statement**
    An instruction that causes the Python interpreter to display a value on the screen.
  


## Kapitel 2

### 2.1 Werte und Typen

Ein **Wert** ist eines der fundamentalen Dinge wie ein Buchstabe oder eine Zahl die ein Programm verarbeitet. Die Werte, die wir bisher gesehen haben, sind 2 (das Ergebnis unserer Addition 1 + 1) und "Hello, World!".

Diese Werte gehoren zu verschiedenen **Typen**: 2 ist eine ganze Zahl oder Ganzzahl und "Hello, World!" ist ein **String** (engl.: Kette, Folge) eine Zeichenkette, so genannt, weil sie eine "Kette" von "Zeichen" etwa: Buchstaben enthalt. Du kannst (wie auch der Interpreter) Strings daran erkennen, dass sie in Anfuhrungszeichen eingeschlossen sind.

Die print - Anweisung funktioniert auch fur Ganzzahlen.

Wenn du nicht sicher bist, welchen Typ ein Wert hat, kann dir das der Interpreter sagen.

>>> type("Hello, World!")   
<type 'string'>   
>>> type(17)   
<type 'int'>

Es ist kaum uberraschend, dass Strings zum Typ string gehoren. Ganzzahlen gehoren zum Typ int (die Abkurzung des englischen Worts integer fur ganze Zahl). Weniger offensichtlich ist es, dass Zahlen mit einem Nachkommaanteil zu einem Typ gehoren, der float heisst. Diese Zahlen werden im sogenannten **floating-point** \- Format Gleitkomma-Format dargestellt-

>>> type(3.2)   
<type 'float'>

Wie steht es mit Werten wie "17" und "3.2"? Sie schauen aus wie Zahlen, sind aber in Anfuhrungszeichen eingeschlossen, wie Strings.

>>> type("17")   
<type 'string'>   
>>> type("3.2")   
<type 'string'>

Sie sind Strings.

Wenn du eine große ganze Zahl schreibst, wirst du vielleicht probieren Kommas zwischen die Zifferngruppen zu schreiben, etwa wie in 1,000,000. Das ist keine korrekte Ganzzahl in Python, aber es ist ein legaler Ausdruck:

>>> print 1,000,000   
1 0 0

Gut, das ist wirklich nicht das, was wir erwartet haben. Es stellt sich heraus, dass 1,000,000 ein Tupel ist, etwas, zu dem wir in [Kapitel 9](http://python4kids.net/how2think/kap09.htm) kommen werden. Zunachst merke dir einfach, dass du keine Kommas in deinen Ganzzahlen verwenden darfst.

### 2.2 Variablen

Eine der nutzlichsten Eigenschaften von Programmiersprachen ist, dass sie mit **Variablen** arbeiten. Eine Variable ist ein Name, der auf einen Wert verweist.

Die **Wertzuweisung** erzeugt neue Variablen und versieht sie mit Werten:

>>> message = "What's up, Doc?"   
>>> n = 17   
>>> pi = 3.14159

Dieses Beispiel macht drei Wertzuweisungen. Die erste _weist_ den String "What's up, Doc?" einer neuen Variablen namens message _zu_. Die zweite _speichert_ die Ganzzahl 17 _in_ der Variablen n und die dritte _setzt den Wert_ von pi _auf_ die Gleitkomma-Zahl 3.14159. (Drei verschiedene Ausdrucksweisen fur dieselbe Sache!)

Ein ubliches Verfahren, Variablen auf Papier darzustellen, ist es, den Variablennamen mit einem Pfeil, der auf den Variablenwert zeigt, aufzuschreiben. Diese Darstellung nennt man Zustandsdiagramm, weil sie den Zustand zeigt, in dem sich jede Variable befindet. (Denk an etwas wie den "Geisteszustand" der Variablen). Das Diagramm zeigt das Ergebnis der Wertzuweisung.

Die print - Anweisung kann auch mit Variablen arbeiten.

>>> print message   
What's up, Doc?   
>>> print n   
17   
>>> print pi   
3.14159

In jedem Fall wird der Wert der Variablen ausgegeben. Variable haben auch einen Typ; wieder kann uns der Interpreter uber diesen Auskunft geben.

>>> type(message)   
<type 'string'>   
>>> type(n)   
<type 'int'>   
>>> type(pi)   
<type 'float'>

Der Typ einer Variablen ist der Typ des Werts, auf den sie verweist (der ihr zugewiesen wurde).

### 2.3 Variablennamen und Schlusselworter

Programmierer verwenden im allgemeinen Namen fur ihre Variablen, die eine Bedeutung haben so sie dokumentieren sie, wofur die Variable verwendet wird.

Variablennamen konnen beliebig lang sein. Sie konnen sowohl Buchstaben wie auch Ziffern enthalten, aber sie mussen mit einem Buchstaben beginnen. Obwohl es erlaubt ist, Großbuchstaben zu verwenden, vereinbaren wir, dass wir das nicht tun. Wenn du es doch tust, denke daran, dass Groß-/Kleinschreibung eine Rolle spielt. Bruce und bruce sind verschiedene Variablen.

Das Unterstrich-Zeichen (_) kann auch in Variablennnamen vorkommen. Es wird oft in Variablennamen verwendet, die aus mehreren Wortern bestehen, wie z. B. mein_name or preis_von_tee_in_china.

Wenn man einer Variablen einen illegalen Namen gibt, erhalt man einen Syntax-Fehler:

>>> 76trombones = "big parade"   
SyntaxError: invalid syntax   
>>> more$ = 1000000   
SyntaxError: invalid syntax   
>>> class = "Computer Science 101"   
SyntaxError: invalid syntax

76trombones ist nicht erlaubt, weil es nicht mit einem Buchstaben beginnt. more$ ist nicht erlaubt, weil es ein illegales Zeichen enthalt, das Dollar-Zeichen. Aber was ist verkehrt mit class?

Es stellt sich heraus, dass class eines der **keywords**, d. h. **Schlusselworter** oder **reservierten Worter** von Python ist. Schlusselworter definieren die Regeln und die Struktur der Sprache und sie konnen nicht als Variablennamen verwendet werden.

Python hat neunundzwanzig Schlusselworter:

and del for is raise   
assert elif from lambda return   
break else global not try   
class except if or while   
continue exec import pass yield   
def finally in print

Du solltest diese Liste bereit halten. Wenn der Interpreter uber einen deiner Variablennamen stolpert, und du weißt nicht warum, schau nach, ob er auf dieser Liste ist.

### 2.4 Anweisungen

Eine Anweisung ist ein Befehl, den der Python-Interpreter ausfuhren kann. Wir haben bisher zwei Arten von Anweisungen gesehen: print-Anweisungen und Wertzuweisungen.

Wenn du eine Anweisung auf der Kommandozeile eingibst, fuhrt Python sie aus und zeigt das Ergebnis auf dem Bildschirm an, wenn die Anweisung ein Ergebnis hat. Das Ergebnis einer print-Anweisung ist ein Wert. Wertzuweisungen erzeugen kein Ergebnis.

Ein Script enthalt normalerweise eine Folge von Anweisungen. Wenn mehr als eine Anweisung vorhanden ist, dann erscheinen die Ergebnisse eins nach dem anderen, in der Reihenfolge wie die Anweisungen ausgefuhrt werden.

Zum Beispiel erzeugt das Script

print 1   
x = 2   
print x

die Ausgabe

Wieder erzeugt die Wertzuweisung keine Ausgabe.

### 2.5 Die Auswertung von Ausdrucken

Ein Ausdruck ist eine Kombination von Werten, Variablen und Operatoren. Wenn du einen Ausdruck auf der Kommandozeile eingibst, fuhrt der Interpreter die **Auswertung** des Ausdrucks aus und stellt das Ergebnis auf dem Bildschirm dar:

>>> 1 + 1   
2

Ein Wert allein wird, ebenso wie eine Variable allein, auch als Ausdruck betrachtet

>>> 17   
17   
>>> x   
2

Verwirrenderweise ist die Auswertung eines Ausdrucks nicht genau dasselbe, wie die Ausgabe eines Werts mit der print-Anweisung.

>>> message = "What's up, Doc?"   
>>> message   
"What's up, Doc?"   
>>> print message

Wenn Python den Wert eines Ausdrucks ausgibt, benutzt es dasselbe Format, dass du auch benutzen wurdest um einen Wert einzugeben. Im Fall von Strings bedeutet das, dass auch die Anfuhrungszeichen eingeschlossen sind.

In einem Script, ist ein Ausdruck ganz allein eine legale Anweisung, aber sie tut uberhaupt nichts. Das Script

17   
3.2   
"Hello, World!"   
1 + 1

produziert uberhaupt keine Ausgabe. Wie wurdest du das Script andern, um die Werte dieser vier Ausdrucke auszugeben?

### 2.6 Operatoren und Operanden

**Operatoren** sind spezielle Symbole, die Rechenarten wie Addition und Multiplikation darstellen. Die Werte, die durch die Operatoren verknupft werden, heißen **Operanden**.

Die folgenden sind einige legale Python-Ausdrucke, deren Bedeutung mehr oder weniger klar ist:

20+32 hour-1 hour*60+minute minute/60 5**2 (5+9)*(15-7)

Die Symbole +, -, und /, und der Gebrauch von runden Klammern _(engl.: parenthesis)_ bedeuten in Python dasselbe wie in der Mathematik. Das Sternchen (*) ist das Symbol fur die Multiplikation und ** ist das Symbol fur Potenzieren.

Wenn ein Variablenname an der Stelle eines Operanden steht, wird er durch seinen Wert ersetzt, bevor die Operation ausgefuhrt wird.

Addition, Subtraktion, Multiplikation und Potenzieren machen alle das, was man erwartet, aber du wirst vielleicht uberrascht sein von der Division. Die folgende Operation hat ein unerwartetes Ergebnis.

>>> minute = 59   
>>> minute/60   
0

Der Wert von minute ist 59, und 59 dividiert durch 60 ist 0.98333, nicht 0. Der Grund fur diesen Widerspruch ist, dass Python eine **Ganzzahl-Division** durchfuhrt.

Wenn beide Operanden der Division Ganzzahlen sind, dann muss das Ergebnis auch eine Ganzzahl sein, und das ist so eingerichtet, dass die Ganzzahl-Division _immer abrundet_, auch in Fallen wie diesem, wo die nachste ganze Zahl ganz nahe daruber ist.

Eine mogliche Losung fur dieses Problem ist, einen Prozentsatz statt eine Dezimalbruchs auszurechnen:

>>> minute*100/60   
98

Wieder ist das Ergebnis abgerundet, aber wenistens ist die Antwort nun naherungsweise korrekt. Eine andere Alternative ware, Gleitkomma-Division zu verwenden; dazu kommen wir in [Kapitel 3](http://python4kids.net/how2think/kap03.htm).

### 2.7 Reihenfolge von Operationen

Wenn mehr als ein Operator ein einem Ausdruck vorkommt, dann hangt die Reihenfolge der Auswertung von den **Vorrangregeln** ab. Python verwendet dieselben Vorrangregeln fur seine mathematischen Operatoren wie die Mathematik ("Punkt- vor Strichrechnung").

  * **Klammern** haben den hochsten Vorrang und konnen dafur benutzt werden, die Reihenfolge der Auswertung nach belieben festzulegen. Weil Ausdrucke in Klammern zuerst ausgewertet werden, ergibt die Auswertung von 2 * (3-1) den Wert 4, und die von (1+1)**(5-2) den Wert 8. Man kann Klammern auch verwenden um einen Ausdruck leichter lesbar zu machen, eventuell ohne den Wert des Ausdrucks dadurch zu andern.
  * **Potenzieren** hat den nachst hoheren Vorrang, daher ergibt 2**1+1 den Wert 3 und nicht 4, und 3*1**3 den Wert 3 und nicht 27.
  * **Multiplikation** und **Division** haben denselben Vorrang, der hoher ist als der von **Addition** and **Subtraktion**, die untereinander ebenfalls denselben Vorrang haben. Daher ergibt 2*3-1 den Wert 5 (und nicht 4), und 2/3-1 den Wert -1, nicht 1 (erinnere dich: bei der Ganzzahldivision ist 2/3=0).
  * Operatoren mit demselben Vorrang werden von links nach rechts ausgewertet. So geschieht etwa im Ausdruck minute*100/60, die Multiplikation zuerst, was 5900/60 ergibt, was anschließend 98 ergibt. Wurden die Operationen von rechts nach links ausgewertet, ware das Ergebnis 59*1 und somit 59, was falsch ist.

### 2.8 Operationen mit Strings

Im Allgemeinen konnen keine mathematischen Operationen mit Strings ausgefuhrt werden, selbst dann, wenn die Strings wie Zahlen ausschauen. Das folgende ist nicht legal (unter der Annahme, dass message den Typ string hat):

message-1 "Hello"/123 message*"Hello" "15"+2

Interessanterweise kann + mit Strings verwendet werden, obwohl es ein anderes Ergebnis produziert, als du vielleicht erwartest. Fur Strings bedeutet der + Operator **Verkettung**, d. h. der zweite Oprand wird an den ersten angefugt. Zum Beispiel:

fruit = "banana"   
bakedGood = " nut bread"   
print fruit + bakedGood

Die Ausgabe dieses Programms ist banana nut bread.

Der * Operator arbeitet (in Python) auch mit Strings; er fuhrt Wiederholung aus. Zum Beispiel: 'Fun'*3 ist 'FunFunFun'. Einer der Operanden muß hier ein String sein, der andere eine ganze Zahl.

Auf der einen Seite scheint diese Interpretation von + und * sinnvoll in Analogie zu Addition und Multiplikation. Gerade wie 4*3 aquivalent mit 4+4+4 ist, erwarten wir, dass "Fun"*3 dasselbe ergibt wie "Fun"+"Fun"+"Fun", und das ist ja auch der Fall. Auf der anderen Seite sind String-Verkettung und String-Wiederholung in wesentlicher Weise verschieden von Ganzzahl-Addition und Ganzzahl-Multiplikation.

> _Als Übung nenne eine Eigenschaft von Addition und Multiplikation, die String-Verkettung und String-Wiederholung nicht haben._

### 2.9 Verknupfung

Bis jetzt haben wir die Grundbestandteile eines Programms betrachtet Variablen, Ausdrucke, Anweisungen ohne daruber zu sprechen, wie man sie kombinieren kann.

Eine der nutzlichsten Eigenschaften von Programmiersprachen ist ihre Fahigkeit zu ermoglichen, kleine Bausteine zu großeren **zu verknupfen**. Wenn wir z. B. wissen, wie man Zahlen addiert und wie man etwas auf den Bildschirm ausgibt, kann man auch beides "gleichzeitig" ausfuhren:

Ein Wirklichkeit geschieht die Addition naturlich vor der Ausgabe, so dass die beiden Aktionen in Wahrheit nicht "gleichzeitig" geschehen. Worauf es hier ankommt ist, dass jeder Ausdruck mit Zahlen, Strings und Variablen innerhalb einer print - Anweisung verwendet werden kann. Du hast schon ein Beispiel dafur gesehen:

print "Number of minutes since midnight: ", hour*60+minute

Ebenso kann man beliebige Ausdrucke auf die rechte Seite einer Wertzuweisung schreiben:

percentage = (minute * 100) / 60

Diese Moglichkeit wird dich vielleicht jetzt nicht beeindrucken, aber du wirst andere Beispiele sehen, wo "Verknupfung" es ermoglicht, komplexe Berechnungen klar und kompakt auszudrucken.

Warnung: Es gibt naturlich Grenzen dafur, wo die Anwendung von Ausdrucken erlaubt ist. Zum Beispiel muß die linke Seite einer Wertzuweisung ein _Variablenname_ sein und kein Ausdruck. So ist etwa das Folgende nicht erlaubt: minute+1 = hour.

### 2.10 Kommentare

Je großer und komplizierter Programme werden, desto schwieriger zu lesen sind sie. Formale Sprachen sind dicht, und oft ist es schwer ein Stuck Code anzuschauen und herauszufinden, was es tut oder warum.

Aus diesem Grund ist es eine gute Idee, Anmerkungen zu deinen Programmen hinzuzufugen, die in naturlicher Sprache erklaren, was das Programm macht. Diese Anmerkungen werden **Kommentare** genannt und sie werden mit dem # Symbol gekennzeichnet:

# berechne den Prozentanteil, der von der Stunde vergangen ist   
percentage = (minute * 100) / 60

In diesem Fall nimmt der Kommentar eine eigene Zeile ein. Man kann Kommentare auch an das Ende einer Zeile stellen:

percentage = (minute * 100) / 60 # Vorsicht: Ganzzahl-Division

Alles vom # bis zum Ende der Zeile wird vom Interpreter ignoriert. Es hat keine Auswirkung auf das Programm. Die Anmerkung ist gedacht fur den Programmierer oder fur zukunftige Programmierer die diesen Code einmal verwenden mochten. In diesem Fall erinnert es den Leser an das immer wieder uberraschende Verhalten der Ganzzahl-Division.

### 2.11 Glossar

**Wert**
    Eine Zahl oder eine Zeichenkette (oder etwas anderes, was spater zu besprechen ist), die in einer Variablen gespeichert oder mit einem Ausdruck berechnet werden kann.
**value**
    A number or string (or other thing to be named later) that can be stored in a variable or computed in an expression.

**Typ**
    Eine Menge von Werten. Der Typ eines Wertes entscheidet daruber, wie er verwendet werden kann. Typen, die wir bisher kennengelernt haben, sind Ganzzahlen (type int), Gleitkomma-Zahlen (type float), und Zeichenketten (type string).
**type**
    A set of values. The type of a value determines how it can be used in expressions. So far, the types you have seen are integers (type int), floating-point numbers (type float), and strings (type string).

**Gleitkomma**
    Ein Format zur Darstellung von Zahlen mit Nachkommastellen.
**floating-point**
    A format for representing numbers with fractional parts.

**Variable**
    Ein Name, der auf einen Wert verweist.
**variable**
    A name that refers to a value.

**Anweisung**
    Ein Code-Abschnitt, der einen Befehl oder eine Aktion darstellt. Bis jetzt haben wir Wertzuweisungen und print-Anweisungen kennengelernt.
**statement**
    A section of code that represents a command or action. So far, the statements you have seen are assignments and print statements.

**Wertzuweisung**
    Eine Anweisung, die einer Variablen einen Wert zuweist.
**assignment**
    A statement that assigns a value to a variable.

**Zustandsdiagramm**
    Eine graphische Darstellung eines Satzes von Variablen mit den Werten, auf die sie sich beziehen.
**state diagram**
    A graphical representation of a set of variables and the values to which they refer.

**Schlusselwort**
    Ein reserviertes Wort, das vom Compiler (oder Interpreter) benutzt wird, die Struktur eines Programms zu ermitteln (ein Programm zu parsen). Man kann Schlusselworter wie if, def, und while nicht als Variablennamen verwenden.
**keyword**
    A reserved word that is used by the compiler to parse program; you cannot use keywords like if, def, and while as variable names.

**Operator**
    Ein spezielles Symbol, das eine einfache "Berechnung" wie Addition, Multiplikation oder auch String-Verkettung darstellt.
**operator**
    A special symbol that represents a simple computation like addition, multiplication, or string concatenation.

**Operand**
    Einer der Werte, mit denen ein Operator arbeitet.
**operand**
    One of the values on which an operator operates.

**Ausdruck**
    Eine Kombination von Variablen, Operatoren und Werten, die einen einzigen Ergebniswert darstellen.
**expression**
    A combination of variables, operators, and values that represents a single result value.

**auswerten**
    Das Vereinfachen eines Ausdrucks, indem die Operationen der Reihe nach ausgefuhrt werden um einen einzigen Wert zu ergeben.
**evaluate**
    To simplify an expression by performing the operations in order to yield a single value.

**Ganzzahl-Division**
    Eine Operation, die eine Ganzzahl durch eine andere dividiert und eine Ganzzahl als Ergebnis liefert. Die Ganzzahl-Division ergibt nur die Anzahl wie oft der Divisor ganz im Dividenden enthalten ist; der Rest wird nicht berucksichtigt.
**integer division**
    An operation that divides one integer by another and yields an integer. Integer division yields only the whole number of times that the numerator is divisible by the denominator and discards any remainder.

**Vorrangregeln**
    Der Satz von Regeln, die angeben, in welcher Reihenfolge Ausdrucke mit mehrfachen Operatoren und Operanden ausgewertet werden.
**rules of precedence**
    The set of rules governing the order in which expressions involving multiple operators and operands are evaluated.

**verketten**
    Zwei Strings aneinander anfugen.
**concatenate**
    To join two operands end-to-end.

**Verknupfung**
    Die Fahigkeit, einfache Ausdrucke und Anweisungen zu zusammengesetzten Anweisungen zu kombinieren, um komplexe Berechnungen knapp darzustellen.
**composition**
    The ability to combine simple expressions and statements into compound statements and expressions in order to represent complex computations concisely.

**Kommentar**
    Information in einem Programm, die fur andere Programmierer (oder Leser des Quellcodes) gedacht ist und keine Wirkung auf die Ausfuhrung des Programms hat.
**comment**
    Information in a program that is meant for other programmers (or anyone reading the source code) and has no effect on the execution of the program.
  


## Kapitel 3

### 3.1 Funktionsaufrufe

Du hast bereits ein Beispiel fur einen **Funktionsaufruf** gesehen:

>>> type("32")   
<type 'string'>

Der Name der aufgerufenen Funktion ist type, und sie zeigt den Typ eines Werts oder einer Variablen an. Der Wert oder die Variable, die das **Argument** der Funktion genannt wird, muss in runde Klammern eingeschlossen werden. Man sagt ublicherweise, die Funktion "verlangt die Übergabe eines Arguments" (oder "ubernimmt ein Argument") und "gibt" ein Ergebnis "zuruck". Das Ergebnis wird auch **Ruckgabewert** genannt.

Anstatt den Ruckgabewert mit print auf dem Bildschirm darzustellen, konnen wir ihn auch einer Variablen zuweisen:

>>> betty = type("32")   
>>> print betty   
<type 'string'>

Ein anderes Beispiel ist die id Funktion. Sie ubernimmt einen Wert oder eine Variable als Argument und gibt eine Ganzzahl zuruck, die als eindeutige Kennzahl fur diesen Wert dient:

>>> id(3)   
134882108   
>>> betty = 3   
>>> id(betty)   
134882108

Jeder Wert hat eine id, d. i. eine eindeutige Zahl, die beschreibt, wo der Wert im Computer gespeichert ist. Die id einer Variablen ist die id des Wertes, auf den die Variable verweist.

### 3.2 Typumwandlung

Python stellt eine Sammlung von eingebauten Funktionen zur Verfugung, die Werte von einem Typ in einen anderen umwandeln. Die int Funktion ubernimmt einen Wert als Argument und verwandelt ihn in eine Ganzzahl, wenn das moglich ist, oder gibt eine Fehlermeldung aus:

>>> int("32")   
32   
>>> int("Hello")   
ValueError: invalid literal for int(): Hello

int kann auch Gleitkomma-Werte in Ganzzahlen umwandeln, aber beachte stets, dass dabei der Nachkommaanteil abgeschnitten wird:

>>> int(3.99999)   
3   
>>> int(-2.3)   
-2

Die float Funktion wandelt Ganzzahlen und Strings in Gleitkomma-Zahlen um:

>>> float(32)   
32.0   
>>> float("3.14159")   
3.14159

Schließlich wandelt die str Funktion in den Typ String um:

>>> str(32)   
'32'   
>>> str(3.14149)   
'3.14149'

Es mag dir merkwurdig vorkommen, dass Python den Ganzzahl-Wert 1 vom Gleitkommawert 1.0 unterscheidet. Sie mogen zwar die selbe Zahl darstellen, aber sie gehoren zu verschiedenen Typen. Der Grund dafur ist, dass sie im Computer verschieden dargestellt werden.

### 3.3 Erzwungene Typumwandlung

Nun, da wir Typen ineinander umwandeln konnen, haben wir eine andere Moglichkeit, mit der Ganzzahl-Division umzugehen. Kehren wir zu dem Beispiel aus dem vorigen Kapitel zuruck:

Angenommen, wir mochten den Bruchteil einer Stunde berechnen, der vergangen ist. Der naheliegendste Ausdruck, minute / 60, fuhrt Ganzzahl-Arithmetik aus, daher ist das Ergebnis immer 0, sogar 59 Minuten nach der vollen Stunde.

Eine Losung ist, die minute in eine Gleitkommazahl zu verwandeln und damit Gleitkommadivision zu erzwingen:

>>> minute = 59   
>>> float(minute) / 60   
0.983333333333

Alternativ konnen wir den Vorteil der Regeln fur die (automatische) **erzwungene Typumwandlung** nutzen, die auf englisch _type coercion)_ genannt wird. Fur mathematische Operatoren gilt: wenn einer der beiden Operanden vom Typ float ist, dann wird der andere automatisch in den Typ float umgewandelt:

>>> minute = 59   
>>> minute / 60.0   
0.983333333333

Indem wir den Nenner zu einem float - Typ machen, zwingen wir Python eine Gleitkomma-Division auszufuhren.

### 3.4 Mathematische Funktionen

In der Mathematik hast du vielleicht Funktionen wie sin und log gesehen, und gelernt, Ausdrucke wie sin(pi/2) und log(1/x) auszuwerten. Zuerst berechnest du den Ausdruck in den Klammern (das Argument). Zum Beispiel, pi/2 ist annahernd 1.571, und 1/x ist 0.1 (wenn x zufallig 10.0 ist).

Dann wertest du die Funktion selbst aus, entweder indem du in einer Tabelle nachschaust, oder verschiedene Berechnungen ausfuhrst. Der sin von 1.571 ist 1, und der log von 0.1 ist -1 (unter der Annahme, dass log den Logarithmus zur Basis 10 bezeichnet).

Dieser Vorgang kann wiederholt ausgefuhrt werden, um kompliziertere Ausdrucke auszuwerten, wie z. B. log(1/sin(pi/2)). Zuerst berechnest du das Argument der innersten Funktion, dann berechnest du den Wert der nachsten Funktion, und so weiter ...

Python hat einen math - Modul, der die meisten der uns vertrauten mathematischen Funktion zur Verfugung stellt. Ein **Modul** ist eine Datei, die eine ein Sammlung zu Gruppen zusammengefaßter verwandter Funktionen enthalt.

Bevor wir die Funktionen aus einem Modul verwenden konnen, mussen wir sie **importieren**:

>>> import math

Um eine dieser Funktionen aufzurufen, mussen wir den Namen des Moduls angeben, gefolgt von dem Namen der Funktion. Die beiden werden durch einen Punkt getrennt. Diese Schreibweise nennt man die **Punkt - Notation**.

>>> decibel = math.log10(17.0)   
>>> angle = 1.5   
>>> height = math.sin(angle)

Die erste Anweisung setzt decibel auf den Wert Logarithmus von 17, mit Basis 10. Es gibt in dem Modul auch eine Funktion mit dem Namen log die den Logarithmus mit der Basis e bezeichnet.

Die dritte Anweisung findet den sinus des Werts der Variablen angle. sin und die anderen Trigonometrischen Funktionen (cos, tan, etc.) nehmen ihre Argumente in Radiant entgegen. Um von Grad in Radiant umzuwandeln, muß man die Gradanzahl durch 360 dividieren und mit 2*pi multiplizieren. Zum Beispiel, um den Sinus von 45 Grad zu finden, berechnen wir zuerst den Winkel im Bogenmaß und nehmen dann davon den Sinus:

>>> degrees = 45   
>>> angle = degrees * 2 * math.pi / 360.0   
>>> math.sin(angle)

Die Konstante pi ist auch Teil des math-Moduls. Mit einfacher Mathematik kannst du das Ergebnis kontrollieren, indem du es mit Quadratwurzel von 2 dividiert durch 2 vergleichst:

>>> math.sqrt(2) / 2.0   
0.707106781187

### 3.5 Verknupfung

Gerade so wie mathematische Funktionen konnen auch Python-Funktionen verknupft werden, d. h. man kann einen Ausdruck als Teil von einem anderen verwenden. Zum Beispiel kann man beliebige Ausdrucke als Argument einer Funktion verwenden:

>>> x = math.cos(angle + pi/2)

Diese Anweisung dividiert den Wert von pi durch 2, und addiert das Ergebnis zu dem Wert von angle. Die Summe wird dann als Argument an die cos Function ubergeben.

Man kann auch das Ergebnis eines Funktionsaufrufs als Argument an eine andere Funktion weiterreichen:

>>> x = math.exp(math.log(10.0))

Diese Anweisung berechnet den naturlichen Logarithmus von 10 (log mit Basis e) und erhebt dann e zu dieser Potenz. Das Ergebnis wird der Variablen x zugewiesen.

### 3.6 Neue Funktionen definieren

Bis jetzt haben wir nur Funktionen verwendet, die zu Python gehoren. Es ist aber auch moglich, neue Funktionen hinzuzufugen. Das Erzeugen neuer Funktionen um spezielle Probleme zu losen ist eine der nutzlichsten Aspekte in hoheren universellen Programmiersprachen.

Im Zusammenhang mit dem Programmieren ist eine **Funktion** eine mit Namen versehene Folge von Anweisungen, die eine gewunschte Verarbeitung von Daten ausfuhrt. Diese Folge von Anweisungen wird in einer **Funktionsdefinition** festgelegt. Die Funktionen, die wir bisher benutzt haben, wurden fur uns definiert und diese Definitionen sind vor uns verborgen. Das ist eine gute Sache, denn es erlaubt uns, diese Funktionen zu verwenden ohne uns um die Details ihrer Definition kummern zu mussen.

Die Syntax fur eine Funktionsdefinition ist so:

def NAME( LIST OF ARAMETERLISTE ):   
ANWEISUNGEN

Man kann einer Funktion, die man erzeugt jeden gewunschten, gultigen Namen geben, ausgenommen die Schlusselworter von Python. (siehe [Kapitel 2.3](http://python4kids.net/how2think/kap02.htm).) Die Parameterliste gibt an, welche Information (falls uberhaupt erforderlich) man ubergeben muß, um die Funktion verwenden zu konnen.

Es kann eine beliebige Anzahl von Anweisungen im Inneren der Funktion (im "Funktionskorper") stehen, aber sie mussen vom linken Rand weg (alle gleich weit) eingeruckt sein. In diesem Buch, werden wir eine Einruckung von zwei Leerzeichen benutzen.

Die ersten paar Funktionen, die wir nun schreiben werden, haben keine Parameter. Daher sieht die Syntax so aus:

def newLine():   
print

Diese Funktion heißt newLine. Die leeren runden Klammern zeigen an, dass sie keine Parameter hat. Sie enthalt nur eine einzige Anweisung, die einen Zeilenvorschub auf dem Bildschirm ausgibt. (Das ist dasselbe, was geschieht, wenn man eine print-Anweisung ohne Argumente verwendet).

Die Syntax fur den Aufruf der neuen Funktion ist die gleiche, wie die Syntax fur eingebaute Funktionen:

print "First Line."   
newLine()   
print "Second Line."

Die Ausgabe dieses Programms ist:

First line.

Second line.

Beachte die Leerzeile zwischen den beiden Zeilen mit Text. Was konnen wir nun machen, wenn wir mehr Zwischenraum zwischen diesen Zeilen haben mochten? Wir konnen die selbe Funktion mehrmals aufrufen:

print "First Line."   
newLine()   
newLine()   
newLine()   
print "Second Line."

Oder wir konnen eine neue Funktion, sagen wir mit Namen threeLines schreiben, die drei leere Zeilen ausgibt:

def threeLines():   
newLine()   
newLine()   
newLine()

print "First Line."   
threeLines()   
print "Second Line."

Diese Funktion enthalt drei Anweisungen, die alle um zwei Leerzeichen eingeruckt sind. Da die nachste Anweisung nicht mehr eingeruckt ist, weiß Python dass sie nicht mehr Teil der Funktionsdefinition ist.

Man sollte sich ein paar Dinge von diesem Programm einpragen:

  1. Man kann dieselbe Prozedur wiederholt aufrufen. In der Praxis ist das ganz gebrauchlich und nutzlich.
  2. Eine Funktion kann eine andere aufrufen. In unserem Beispiel ruft threeLines() die Funktion newLine() auf.

_Anmerkung:_ Wir werden ab hier _Funktion_snamen immer mit einem paar leerer, runder Klammern nach dem Namen schreiben: type() bzw. newLine() usw. So erkennt man bereits am Namen, dass er ein Bezeichner fur eine Funktion ist.

Bis jetzt mag es noch nicht klar sein, wozu die Muhe mit der Definition all dieser neuen Funktionen gut sein soll. In der Tat gibt es dafur eine Menge Grunde, aber dieses Beispiel demonstriert zwei:

  * Eine neue Funktion zu erzeugen ist eine Gelegenheit eine Gruppe von Anweisungen zu benennen. Funktionen konnen so ein Programm vereinfachen, indem eine komplexe Berechnung hinter einem einzigen Befehl versteckt wird und indem dafur verstandliche Worter an Stelle von geheimnisvollem Code verwendet werden.
  * Eine neue Funktion zu erzeugen, kann ein Programm kurzer machen, in dem Code-Wiederholungen wegfallen. So ware zum Beispiel in kurzerer Weg um neun Leerzeilen hintereinander zu erzeugen die Funktion threeLines() drei Mal aufzurufen.

> _Als Übung schreibe eine Funktion nineLines(), die die Funktion threeLines() benutzt um neun Leerzeilen auszugeben. Wie wurdest du 27 Leerzeilen ausgeben?_

### 3.7 Definition und Anwendung

Setzt man die Programm-Fragmente aus Abschnitt 3.6 zusammen, dann sieht das ganze Programm so aus:

def newLine():   
print

def threeLines():   
newLine()   
newLine()   
newLine()

print "First Line."   
threeLines()   
print "Second Line."

Dieses Programm enthalt zwei Definitionen: newLine() und threeLines(). Funktionsdefinitionen werden ausgefuhrt gerade so wie andere Anweisungen auch. Aber die Wirkung ist, dass eine neue Funktion erzeugt wird. Die Anweisungen im Funktionskorper werden nicht ausgefuhrt, bis die Funktion aufgerufen wird und die Funktionsdefinition erzeugt keine Ausgabe.

Wie nicht anders zu erwarten, muss man eine Funktion erzeugen, bevor man sie ausfuhren kann. In anderen Worten: die Funktionsdefinition muß ausgefuhrt werden, bevor die Funktion zum ersten Mal aufgerufen wird.

> _Als weitere Übung beginne nun mit einer lauffahigen Version dieses Programms und verschiebe die Definition von newLine() hinter die Definition von threeLines(). Was geschieht, wenn du das Programm nun ausfuhrst?_

### 3.8 Programmablauf

Um sicherzustellen, dass eine Funktion definiert wird, bevor sie zum ersten Mal verwendet wird, musst du die Reihenfolge kennen, in der die Anweisungen ausgefuhrt werden. Diese Reihenfolge nennt man den **Programmablauf**

Die Programmausfuhrung beginnt immer mit der ersten Anweisung des Programms. Die Anweisungen werden eine nach der anderen ausgefuhrt, in der Reihenfolge von oben nach unten.

Funktionsdefinitionen andern nicht den Programmablauf. Wir erinnern uns daran, dass die Anweisungen im Funktionskorper nicht ausgefuhrt werden, bevor die Funktion aufgerufen wird. Obwohl es nicht ublich ist, kann man eine Funktion im Inneren einer anderen definieren. In diesem Fall wird die innere _Definition_ erst ausgefuhrt, wenn die außere Funktion aufgerufen wird.

Funktionsaufrufe kann man mit einem Umweg im Programmablauf vergleichen. Anstatt zur nachsten Anweisung weiterzugehen, setzt der Programmablauf mit der ersten Zeile der aufgerufenen Funktion fort, fuhrt alle Anweisungen dort aus und kommt dann zuruck um dort fortzusetzen, wo er vorher abgezweigt ist.

Das klingt ja noch einfach, bis man daran denkt, dass eine Funktion eine weitere aufrufen kann. Wenn er in der Mitte einer Funktion ist, muß der Programmablauf vielleicht zu Anweisungen einer weiteren Funktion springen, alle Anweisungen dort ausfuhren und moglicherweise von dort wieder zu den Anweisungen einer weiteren Funktion verzweigen ...!

Zum Gluck ist Python so gemacht, dass es Buch fuhrt daruber, wo die Programmausfuhrung gerade ist und woher sie kam. Daher kann das Programm immer dann, wenn eine Funktion fertig ausgefuhrt worden ist, die Ausfuhrung dort fortsetzen, wo es wegen des Funktionsaufrufs verzweigt hat: an der Stelle nach dem Funktionsaufruf. Wenn die Programmausfuhrung am Ende des Programms angekommen ist, endet die Programmausfuhrung.

Was ist die Moral von dieser verwirrenden Geschichte? Wenn du ein Programm liest, lies es nicht von oben nach unten. Folge vielmehr dem Programmablauf.

### 3.9 Parameter und Argumente

Einige der eingebauten Funktionen die du bisher benutzt hast, verlangen Argumente, das sind Werte, die dafur entscheidend sind, wie die Funktion ihre Arbeit tut. Wenn du z. B. den Sinuswert einer Zahl wissen willst, musst du der sinus-Funktion mitteilen, was diese Zahl ist. Daher braucht sin() einen numerischen Wert als Argument.

Einige Funktionen verlangen die Übergabe von mehr als einem Argument. Zum Beispiel braucht pow() zwei Argumente, die Basis und den Exponenten. Im inneren der Funktion werden die ubergebenen Argumente gewissen Variablen zugewiesen, die **Parameter** genannt werden.

Hier ist ein Beispiel einer benutzerdefinierten Funktion, die einen Parameter hat:

def printTwice(bruce):   
print bruce, bruce

Diese Funktion ubernimmt ein einziges Argument und weist es dem Parameter mit dem Namen bruce zu. Der Wert des Parameters (an dieser Stelle haben wir keine Idee, welcher das sein wird) wird zweimal auf dem Bildschirm ausgegeben, gefolgt von einem Zeilenende. Der Name bruce wurde gewahlt, um anzudeuten, dass der Name, den du einem Parameter gibst, ganz beliebig von dir ausgewahlt werden kann. Im allgemeinen wird man eine etwas illustrativeren Namen als bruce wahlen.

Die Funktion printTwice() arbeitet fur jeden Typ, der ausgegeben werden kann.

>>> printTwice('Spam')   
Spam Spam   
>>> printTwice(5)   
5 5   
>>> printTwice(3.14159)   
3.14159 3.14159

Im ersten Funktionsaufruf ist das Argument ein String. Im zweiten ist es eine Ganzzahl. Im dritten ist es vom Typ float.

Dieselben Reglen fur Zusammensetzung, die fur eingebaute Funktionen gelten, gelten auch fur benutzerdefinierte Funktionen. Daher konnen wir jede Art von Ausdruck als Argument fur printTwice() verwenden:

>>> printTwice('Spam'*4)   
SpamSpamSpamSpam SpamSpamSpamSpam   
>>> printTwice(math.cos(math.pi))   
-1.0 -1.0

Wie ublich wird der Ausdruck ausgewertet, bevor die Funktion ausgefuhrt wird, daher gibt printTwice hier SpamSpamSpamSpam SpamSpamSpamSpam und nicht 'Spam'*4 'Spam'*4.

> _Als Übung schreibe einen Funktionsaufruf von printTwice, der tatsachlich 'Spam'*4 'Spam'*4 auf den Bidschirm schreibt. Hinweis: Strings konnen entweder in einfache Anfuhrungszeichen oder in doppelte Anfuhrungszeichen gesetzt werden. Der Typ von Anfuhrungszeichen, der nicht den String einschließt, kann im String selbst als Teil des Strings verwendet werden._

Wir konnen auch eine Variable als Argument verwenden:

>>> latoya = 'Eric, the half a bee.'   
>>> printTwice(latoya)   
Eric, the half a bee. Eric, the half a bee.

Hier ist etwas sehr Wichtiges zu beachten. Der Name der Variablen, die wir als Argument ubergeben (latoya) hat nichts mit dem Namen des Parameters zu tun (bruce). Es spielt keine Rolle, wie der Wert in der aufrufenden Funktion genannt wurde; hier in printTwice(), nennen wir ihn auf jeden Fall bruce.

### 3.10 Variable und Parameter sind lokal

Wenn man eine **lokale Variable** im Inneren einer Funktion erzeugt, dann existiert sie nur innerhalb dieser Funktion und man kann sie außerhalb nicht verwenden.

def catTwice(part1, part2):   
cat = part1 + part2   
printTwice(cat)

Diese Funktion verlangt nach zwei Argumenten, verkettet sie und gibt das Ergebnis zweimal am Bildschirm aus. Wir konnen die Funktion mit zwei Strings aufrufen:

>>> chant1 = "Pie Jesu domine, "   
>>> chant2 = "Dona eis requiem."   
>>> catTwice(chant1, chant2)   
Pie Jesu domine, Dona eis requiem. Pie Jesu domine, Dona eis requiem.

Wenn die Ausfuhrung von catTwice() endet, wir die Variable cat zerstort. Wenn wir versuchen sie auszugeben, erhalten wir eine Fehlermeldung.

>>> print cat   
NameError: cat

Parameter sind auch lokal. Zum Beispiel gibt es außerhalb der Funktion printTwice keine Variable bruce. Wenn du versuchst sie zu verwenden, wird sich Python mit einer Fehlermeldung beklagen.

### 3.11 Stackdiagramme

Um besser verfolgen zu konnen, welche Variable wo verwendet werden kann, ist es manchmal nutzlich ein sogenanntes **Stackdiagramm** zu zeichnen. Wie Zustandsdiagramme zeigen Stackdiagramme den Wert jeder Variablen, sie zeigen aber auch die Funktion, zu der jede Variable gehort.

Jede Funktion wird durch einen **Rahmen** dargestellt. Ein Rahmen ist eine Kastchen mit dem Namen einer Funktion daneben und den Parametern und Variablen der Funktion im Inneren. Das Stack-Diagramm fur das vorhergehende Beispiel sieht so aus:

Die Anordnung des Stacks zeigt den Programmablauf. printTwice() wurde von catTwice() aufgerufen, und catTwice() wurde von __main__() aufgerufen; das ist ein spezieller Name fur die oberste Funktion. Wenn man eine Variable außerhalb jeder Funktion erzeugt, gehort sie zu __main__().

Jeder Parameter bezieht sich auf denselben Wert wie sein entsprechendes Argument. So hat part1 denselben Wert wie chant1, part2 hat denselben Wert wie chant2 und bruce hat denselben Wert wie cat.

Wenn ein Fehler wahrend eines Funktions-Aufrufs auftritt, gibt Python den Namen der Funktion aus und den Namen der Funktion, die sie aufgerufen hat und den Namen der Funktion, die _diese_ aufgerufen hat ..., den ganzen Weg zuruck bis __main__().

Wenn wir z. B. versuchen auf cat von innerhalb printTwice() zuzugreifen, erhalten wie einen NameError:

Traceback (innermost last):   
File "test.py", line 13, in __main__   
catTwice(chant1, chant2)   
File "test.py", line 5, in catTwice   
printTwice(cat)   
File "test.py", line 9, in printTwice   
print cat   
NameError: cat

Diese Liste der Funktionen nennt man **Ablaufverfolgung** (_engl.: traceback)_. Diese teilt dir mit, in welcher Programmdatei der Fehler auftrat, in welcher Zeile das war und welche Funktionen zu diesem Zeitpunkt in Ausfuhrung begriffen waren. Sie zeigt auch die Programmzeile an, die den Fehler verursacht hat.

Beachte die Ähnlichkeit zwischen dieser Ablaufverfolgung und dem Stackdiagramm. Diese ist kein Zufall!

### 3.12 Funktionen mit Ergebnissen

Vielleicht ist dir schon aufgefallen, dass einige Funktionen, die wir verwenden, wie etwa die mathematischen Funktionen, Ergebnisse liefern. Andere Funktionen, wie etwa newLine() fuhren zwar Aktionen aus, geben aber keinen Wert zuruck. Daraus ergeben sich einige Fragen:

  1. Was geschieht, wenn du eine Funktion aufrufst und nichts mit dem Ergebnis machst (d. h., du weist es keiner Variablen zu, du verwendest es nicht in einem umfassenderen Ausdruck und gibst es auch nicht auf dem Bildschirm aus)?
  2. Was geschieht, wenn du eine Funktion ohne Ergebnis als Teil eines Ausdrucks verwendest, z. B. so: newLine() + 7?
  3. Kann man selbst Funktionen schreiben, die Ergebnisse liefern, oder mussen wir uns mit einfachen Funktionen wie newLine() und printTwice() zufrieden geben?

Die Antwort auf die dritte Frage ist _ja_, und wir werden das in Kapitel 5 tun.

> _Als eine Übung beantworte die anderen beiden Fragen, indem du sie mit dem Python-Interpreter ausprobierst. Wenn du eine Frage hast in Bezug darauf, was in Python erlaubt ist und was nicht, dann ist immer ein guter Weg das herauszufinden, den Interpreter zu fragen._

### 3.13 Glossar

**Funktionsaufruf**
    Eine Anweisung, die eine Funktion ausfuhrt. Sie besteht aus dem Namen der Funktion gefolgt von einer in runde Klammern eingeschlossenen Liste von Argumenten.
**function call**
    A statement that executes a function. It consists of the name of the function followed by a list of arguments enclosed in parentheses.

**Argument**
    Ein Wert, der einer Funktion beim Aufruf ubergeben wird. Der Wert wird dem entsprechenden Parameter der Funktion zugewiesen.
**argument**
    A value provided to a function when the function is called. This value is assigned to the corresponding parameter in the function.

**Ruckgabewert**
    Das Ergebnis einer Funktion. Wenn ein Funktionsaufruf als Ausdruck benutzt wird, ist der Ruckggabewert der Funktion der Wert des Ausdrucks.
**return value**
    The result of a function. If a function call is used as an expression, the return value is the value of the expression.

**Typumwandlung**
    Eine explizite Anweisung, die einen Wert eines bestimmten Typs ubernimmt und den entsprechenden Wert eines anderen Typs berechnet.
**type conversion**
    An explicit statement that takes a value of one type and computes a corresponding value of another type.

**zwangsweise Typumwandlung**
    Eine Typumwandlung die automatisch entsprechend den dafur in Python eingebauten Regeln erfolgt.
**type coercion**
    A type conversion that happens automatically according to Python's coercion rules.

**Modul**
    Eine Datei die eine Gruppe zusammengehoriger Funktionen und Klassen enthalt.
**module**
    A file that contains a collection of related functions and classes.

**Punkt-Notation**
    Die Syntax fur Aufrufe von Funktionen aus einem anderen Modul, bestehend aus der Angabe des Modulnamens gefolgt von einem Punkt und dem Funktionsnamen.
**dot notation**
    The syntax for calling a function in another module, specifying the module name followed by a dot (period) and the function name.

**Funktion**
    Eine mit einem Namen versehene Folge von Anweisungen, die nutzliche Operationen ausfuhren. Funktionen konnen, mussen aber nicht, Parameter haben und sie konnen, mussen aber nicht, ein Ergebnis zuruckgeben.
**function**
    A named sequence of statements that performs some useful operation. Functions may or may not take parameters and may or may not produce a result.

**Funktionsdefinition**
    Eine Anweisung, die eine neue Funktion erzeugt, bestehend aus dem Namen, den Parametern und den Anweisungen die ausgefuhrt werden sollen.
**function definition**
    A statement that creates a new function, specifying its name, parameters, and the statements it executes.

**Progammablauf**
    Die Reihenfolge in der die Anweisung ausgefuhrt werden, wenn ein Programm lauft.
**flow of execution**
    The order in which statements are executed during a program run.

**Parameter**
    Ein Name der innerhalb einer Funktion benutzt wird um einen Wert zu bezeichnen, der ihr als Argument ubergeben wurde.
**parameter**
    A name used inside a function to refer to the value passed as an argument.

**lokale Variable**
    Eine Variable, die innerhalb einer Funktion definiert wird. Eine lokale Variable kann nur innerhalb ihrer Funktion benutzt werden.
**local variable**
    A variable defined inside a function. A local variable can only be used inside its function.

**Stack-Diagramm**
    Eine graphische Darstellung eines Stapels von Funktionen, ihrer Variablen und der Werte, die sie bezeichnen.
**stack diagram**
    A graphical representation of a stack of functions, their variables, and the values to which they refer.

**Rahmen**
    Ein Rechteck in einem Stack-Diagramm das einen Funktionsaufruf darstellt. Es enthalt die lokalen Variablen und die Parameter der Funktion.
**frame**
    A box in a stack diagram that represents a function call. It contains the local variables and parameters of the function.

**Ablaufverfolgung**
    Eine Liste der Funktionen, die gerade ausgefuhrt werden, wenn ein Laufzeitfehler auftritt.
**traceback**
    A list of the functions that are executing, printed when a runtime error occurs.
  


## Kapitel 4

### 4.1 Der Modulo-Operator

Der **Modulo-Operator** arbeitet mit Ganzzahlen (und ganzzahligen Ausdrucken) und ermittelt den Rest bei der Division des ersten Operanden durch den zweiten. In Python ist der Modulo-Operator ein Prozentzeichen (%). Die Syntax ist dieselbe wie fur andere Operatoren:

>>> print quotient   
2   
>>> remainder = 7 % 3   
>>> print remainder   
1

Also ist 7 dividiert durch 3 gleich 2 mit 1 Rest.

Es stellt sich heraus, dass der Modulo-Operator unerwartet nutzlich ist. Zum Beispiel kann man mit ihm uberprufen, ob eine Zahl durch eine andere teilbar ist ... wenn x % y null ist, dann ist x durch y teilbar.

Ebenso kann man mit ihm die am weitesten rechts stehende(n) Ziffer(n) einer Zahl ermitteln. Zum Beispiel liefert x % 10 die rechteste Ziffer von x (in der Basis 10). Ähnlich liefert x % 100 die letzten zwei Ziffern.

### 4.2 Boolesche Ausdrucke

Ein **boolescher Ausdruck** ist eine Ausdruck, der entweder wahr oder falsch ist. In Python hat ein Ausdruck, der wahr ist, den Wert True (in alteren Versionen: 1) und ein Ausdruck, der falsch ist, den Wert False (in alteren Versionen 0).

Der Operator == vergleicht zwei Werte und erzeugt einen booleschen Ausdruck:

>>> 5 == 5   
True   
>>> 5 == 6   
False   
>>>

In der ersten Anweisung sind die zwei Operanden gleich, daher wird der Ausdruck zu True (wahr) ausgewertet; in der zweiten Anweisung ist 5 nicht gleich 6, daher erhalten wir False (falsch).

Der == - Operator ist einer der **Vergleichsoperatoren**; die anderen sind:

x != y # x ist nicht gleich y   
x > y # x ist gro&szlig;er als y   
x < y # x ist kleiner als y   
x >= y # x ist gro&szlig;er oder gleich y   
x <= y # x is kleiner oder gleich y

Obwohl diese Operatoren dir vielleicht vertraut sind, sind doch die Symbole, die Python verwendet, verschieden von den mathematischen Symbolen. Ein haufiger Fehler ist es, eine einzelnes Gleichheitszeichen (=) anstatt eines doppelten Gleichheitszeichens (==) zu verwenden. Merke dir, dass = ein Zuweisungsoperator ist und => ein Vergleichsoperator. Des Weiteren gibt es (in Python) auch weder =< noch =>.

### 4.3 Logische 0peratoren

Es gibt drei **logische Operatoren**: and, or, und not. Die Semantik (Bedeutung) dieser Operatoren ist ahnlich ihrer Bedeutung in der Umgangssprache. Zum Beispiel ist x > 0 und x < 10 nur wahr, wenn x großer als 0 _und_ kleiner als 10 ist.

n%2 == 0 or n%3 == 0 ist wahr, wenn _eine der beiden_ Bedingungen wahr ist, d.h wenn die Zahl durch 2 oder durch 3 teilbar ist.

Schließlich liefert der not Operator die Negation eines booleschen Ausdrucks, so ist etwa not(x > y) wahr, wenn (x > y) falsch ist, d. h. wenn x kleiner oder gleich y ist.

Streng genommen sollten die Operanden eines logischen Operators boolesche Ausdrucke sein, aber Python ist hier nicht sehr streng. Jede Zahl ungleich null wird als "wahr" interpretiert.

>>> x = 5   
>>> x and True   
True   
>>> y = 0   
>>> y and True   
0 # (!) ist aquivalent zu False

Im allgemeinen werden Dinge dieser Art nicht als guter (Programmier-)stil betrachtet. Wenn du eine Zahl mit null vergleichen mochtest, dann tu es explizit.

### 4.4 Bedingte Ausfuhrung

Damit wir nutzliche Programme schreiben konnen, mussen wir fast immer im Stande sein, Bedingungen zu uberprufen und das Verhalten des Programms entsprechend zu andern. **Bedingte Anweisungen**, (oder **Verzweigungen**,) ermoglichen uns das. Die einfachste Form ist die if - Anweisung.

if x > 0:   
print "x is positive"

Den booleschen Ausdruck nach dem Schlusselwort if nennt man die **Bedingung**. Wenn sie wahr ist, dann werden die eingeruckten Anweisungen danach ausgefuhrt. Wenn nicht, dann geschieht nichts.

Wie andere zusammengesetzte Anweisungen, wird die if-Anweisung aus einem Kopf und einem Anweisungsblock gebildet:

KOPF:   
ERSTE ANWEISUNG   
...   
LETZTE ANWEISUNG

Der Kopf beginnt in einer neuen Zeile und endet mit einem Doppelpunkt (:). Die darauf folgenden eingeruckten Anweisungen werde ein **Block** genannt. Die erste nicht mehr eingeruckte Anweisung kennzeichnet das Ende des Blocks. Ein Anweisungs-Block im Inneren einer zusammengesetzten Anweisung wird der **Korper** dieser Anweisung genannt.

Es gibt keine Obergrenze fur die Anzahl der Anweisungen, die der Korper einer if-Anweisung enthalten kann, aber er muss mindestens eine Anweisung enthalten. Gelegentlich ist es nutzlich einen Korper ohne Anweisungen zu haben (im Allgemeinen als Platzhalter fur Code, der erst geschrieben werden muss). In diesem Fall, kann man die pass-Anweisung verwenden, die nichts tut (außer eine Anweisung zu sein).

### 4.5 Alternative Ausfuhrung

Eine zweite Form der if-Anweisung ist die alternative Ausfuhrung, bei der es zwei Moglichkeiten gibt und die Bedingung entscheidet, welche von beiden ausgefuhrt wird. Ihre Syntax schaut so aus:

if x%2 == 0:   
print x, "ist gerade"   
else:   
print x, "ist ungerade"

Wenn der Rest bei der Division von x durch 2 gleich 0 ist, dann wissen wir, dass x gerade ist und das Programm zeigt eine Meldung an, dass das so ist. Wenn die Bedingung falsch ist, wird der zweite Block ausgefuhrt. Da die Bedingung wahr oder falsch sein muss, wird genau eine dieser beiden Alternativen ausgefuhrt. Diese Alternativen heißen **Zweige**, weil sie Zweige in der Programmausfuhrung sind.

Nebenbei gesagt, wenn du die Eigenschaft einer Zahl, gerade oder ungerade zu sein, oft prufen musst, kannst du diesen Code in eine Funktion "verpacken":

def printParity(x):   
if x%2 == 0:   
print x, "ist gerade"   
else:   
print x, "ist ungerade"

Fur jeden Wert von x wird die Funktion printParity eine passende Meldung ausgeben. Wenn du sie aufrufst, kannst du ihr jeden beliebigen Ausdruck vom Typ int als Argument ubergeben.

>>> printParity(17)   
17 ist ungerade   
y = 99   
>>> printParity(y+1)   
100 ist gerade

### 4.6 Mehrfache Verzweigungen

Manchmal gibt es mehr als zwei Moglichkeiten und wir brauchen mehr als zwei Zweige. Ein Weg eine Berechnung dieser Art auszudrucken ist eine **Mehrfache Verzweigung**:

if x < y:   
print x, "ist kleiner als", y   
elif x > y:   
print x, "is gro&szlig;er als", y   
else:   
print x, "und", y, "sind gleich"

elif ist eine Abkurzung von "else if". Wieder wird genau ein Zweig ausgefuhrt. Es gibt keine Obergrenze fur die Anzahl von elif-Anweisungen, aber der letzte Zweig muss eine else-Anweisung sein.

if choice == 'A':   
functionA()   
elif choice == 'B':   
functionB()   
elif choice == 'C':   
functionC()   
elif choice == 'D':   
functionD()   
else:   
print "Invalid choice."

Alle Bedingungen werden der Reihe nach uberpruft. Wenn die erste falsch ist, wird die nachste gepruft und so weiter. Wenn eine wahre Bedingung angetroffen wird, wird der entsprechende Zweig ausgefuhrt und die ganze **if**-Anweisung beendet. Auch wenn mehr als eine Bedingung wahr ist, wird nur der erste wahre Zweig ausgefuhrt.

> _Als Übung formuliere diese Beispiele als Funktionen mit den Namen compare(x, y) und dispatch(choice). Um die zweite zu testen sind dann naturlich noch vier Funktionen functionA(), ... functionD() zu schreiben, die im einfachsten Fall vielleicht nur ausgeben, dass sie aufgerufen wurden. _

### 4.7 Verschachtelte Verzweigungen

Verzweigungsanweisungen konnen auch ineinander geschachtelt werden. Wir hatten das Beispiel mit der Dreifachverzweigung auch so schreiben konnen:

if x == y:   
print x, "und", y, "sind gleich"   
else:   
if x < y:   
print x, "ist kleiner als", y   
else:   
print x, "ist gro&szlig;er als", y

Die außere Verzweigung enthalt zwei Zweige. Der erste Zweig enthalt eine einfache Ausgabe-Anweisung. Der zweite Zweig enthalt eine weitere if-Anweisung, die selbst wieder zwei Zweige enthalt. Diese zwei Zweige sind beide Ausgabe-Anweisungen, obwohl sie ebensogut wieder Verzweigungs-Anweisungen hatten sein konnen.

Obwohl die Einruckung von Anweisungen die Struktur verdeutlicht, konnen verschachtelte Verzweigungen sehr schnell schwer lesbar werden. Im Allgemeinen ist es eine gute Idee, sie zu vermeiden, wo es geht.

Logische Operatoren ermoglichen es oft, geschachtelte Verzweigungen zu vereinfachen. Man kann zum Beispiel den folgenden Code auch mit einer Verzweigung schreiben:

if 0 < x:   
if x < 10:   
print "x is a positive single digit."

Die print-Anweisung im Korper der inneren bedingten Anweisung wird nur ausgefuhrt wenn beide Bedingungen wahr sind, daher konnen wir dafur den and - Operator verwenden:

if 0 < x and x < 10:   
print "x is a positive single digit."

Diese Art von Bedingungen kommt haufig vor, daher stellt Python dafur eine alternative Syntax zur Verfugung, die der mathematischen Schreibweise ahnlich ist:

if 0 < x < 10:   
print "x is a positive single digit."

Diese Bedingung ist semantisch die gleiche wie der zusammengesetzte boolesche Ausdruck und wie die geschachtelte bedingte Anweisung.

### 4.8 Die return Anweisung

Die return Anweisung ermoglicht dir, die Ausfuhrung einer Funktion zu beenden, bevor das Ende des Codes erreicht ist. Ein Grund, sie zu verwenden, ist das Eintreten einer Fehlerbedingung.

import math

def printLogarithm(x):   
if x <= 0:   
print "Nur positive Zahlen, bitte."   
return

result = math.log(x)   
print "Der log von x ist", result

Die Funktion printLogarithm hat einen Parameter mit Namen x. Die erste Sache, die sie tut, ist zu uberprufen ob x kleiner oder gleich 0 ist. In diesem Fall zeigt sie eine Fehlermeldung an und benutzt die return-Anweisung um die Funktion zu verlassen. Der Programmablauf kehrt unmittelbar zum aufrufenden Code zuruck und die restlichen Zeilen der Funktion werden nicht ausgefuhrt.

Denke daran: um eine Funktion aus dem math-Modul zu verwenden, musst du diesen importieren.

### 4.9 Rekursion

Wie erwahnten, dass es legal ist (also den Syntax-Regeln entspricht), dass eine Funktion eine andere aufruft und du hast mehrere Beispiel dafur gesehen. Wir vergaßen dabei zu erwahnen, dass es ebenso legal ist, dass eine Funktion sich selbst aufruft. Es mag vielleicht nicht offensichlich sein, warum das eine gute Sache ist, aber es wird sich als eines der geradezu magischsten und interessantesten Dinge herausstellen, die ein Programm tun kann.

Betrachten wir zum Beispiel folgende Funktion:

def countdown(n):   
if n == 0:   
print "Blastoff!"   
else:   
print n   
countdown(n-1)

countdown() erwartet, dass der Parameter n eine positive ganze Zahl ist.Wenn n gleich 0 ist, wird das Wort "Blastoff!" ausgegeben. Andernfalls wird n ausgegeben und dann and eine Funktion namens countdown() sie selbst aufgerufen, wobei ihr n-1 als Argument ubergeben wird.

Was geschieht, wenn wir diese Funktion in folgender Weise aufrufen:

>>> countdown(3)

Die Ausfuhrung von countdown() beginnt mit n=3 und weil n nicht gleich 0 ist, wird der Wert 3 ausgegeben und sie selbst aufgerufen ...

> Die Ausfuhrung von countdown() beginnt mit n=2 und weil n nicht gleich 0 ist, wird der Wert 3 ausgegeben und sie selbst aufgerufen ... 
>
>> Die Ausfuhrung von countdown() beginnt mit n=1 und weil n nicht gleich 0 ist, wird der Wert 3 ausgegeben und sie selbst aufgerufen ... 
>>
>>> Die Ausfuhrung von countdown() beginnt mit n=0 und weil n gleich 0 ist, wird das Wort "Blastoff!" ausgegeben und die Programmausfuhrung endet. 
>> 
>> Das countdown() das den Parameterwert n=1 erhalten hat, beendet seine Ausfuhrung. 
> 
> Das countdown() das den Parameterwert n=2 erhalten hat, beendet seine Ausfuhrung. 

Das countdown() das den Parameterwert n=3 erhalten hat, beendet seine Ausfuhrung.

Und dann sind wir zuruck in __main__ (was fur ein Trip!) Daher sieht die ganze Ausgabe so aus:

3   
2   
1   
Blastoff!

Als zweites Beispiel betrachten wir noch einmal die Funtionen newLine() and threeLines():

def newline():   
print

def threeLines():   
newLine()   
newLine()   
newLine()

Die funktionieren zwar, aber sie sind nur von maßigem Nutzen, wenn wir 2 oder 106 Leerzeilen ausgeben mochten. Eine bessere Alternative ware dies:

def nLines(n):   
if n > 0:   
print   
nLines(n-1)

Diese Programm ist ahnlich zu countdown(); solange n großer als 0 ist, gibt es eine Leerzeile aus und ruft dann sich selbst auf, um n-1 weitere Leerzeilen auszugeben. Daher ist die Gesamtzahl von ausgegebenen Leerzeilen 1 + (n - 1), was , wenn du deine Algebrakenntnisse richtig anwendest, n ergibt.

Der Prozess, der darin besteht, dass eine Funktion sich selbst aufruft heißt **Rekursion** und solche Funktionen nennt man rekursiv.

### 4.10 Stackdiagramme fur rekursive Funktionen

Im [Abschnitt 3.11](http://python4kids.net/how2think/kap03.htm), haben wir ein Stackdiagramm benutzt, um den Zustand eines Programms wahrend eines Funktionsaufrufs darzustellen. Dieselbe Art von Diagramm kann auch hilfreich sein, um eine rekursive Funktion zu interpretieren.

Jedesmal, wenn eine Funktion aufgerufen wird, erzeugt Python einen neuen Funktions-Rahmen, der die lokalen Variablen und die Parameter der Funktion enthalt. Fur eine rekursive Funktion, kann durchaus mehr als ein Rahmen gleichzeitig auf dem Stapel (stack) sein.

Die folgende Abbildung zeigt ein Stackdiagramm fur countdown aufgerufen mit n = 3:

Wie ublich, ist der oberste Rahmen des Stacks der Rahmen fur __main__(). Er ist leer, denn wir haben keine Variablen in __main__() erzeugt oder Parameter an es ubergeben.

Die vier countdown() Rahmen haben verschiedene Werte fur den Parametern n. Der unterste Rahmen des Stacks, wo n=0 steht, heißt der **Basis-Fall**. Er macht keinen rekursiven Aufruf, daher gibt es auch keine weiteren Rahmen.

> _Als Übung zeichne eine Stackdiagramm fur nLines(), das mit n=4 aufgerufen wurde._

### 4.11 Unendliche Rekursion

Wenn eine Rekursion nie einen Basis-Fall erreicht, dann fahrt sie ohne Ende fort, rekursive Aufrufe zu machen und das Programm endet niemals. Das ist als **unendliche Rekursion** bekannt, und wird im allgemeinen nicht als eine gute Idee betrachtet. Hier ist eine minimales Programm mit einer unendlichen Rekursion:

def recurse():   
recurse()

In den meisten Progammierumgebungen lauft ein Programm mit unendlicher Rekursion nicht wirklich endlos. Pythen gibt eine Fehlermeldung aus, wenn die maximale Rekursionstiefe erreicht ist.

File "<stdin>", line 2, in recurse   
(98 repetitions omitted)   
File "<stdin>", line 2, in recurse   
RuntimeError: Maximum recursion depth exceeded

Diese Zuruckverfolgung der Aufrufe ist etwas großer, als die, die wir im vorigen Kapitel gesehen haben. Der Fehler tritt auf, wenn 100 recurse-Rahmen auf dem Stack sind.

> _Als Übung schreibe eine Funktion mit unendlicher Rekursion und lasse sie vom Python-Interpreter ausfuhren._

### 4.12 Tastatureingabe

Die Programme, die wir bis jetzt geschrieben haben, sind insofern ein bißchen primitiv, als sie keine Eingaben des Benutzers verarbeiten konnen. Sie machen jedesmal dasselbe, wenn sie ablaufen.

Python stellt eingebaute Funktionen zur Verfugung, die Eingaben von der Tastatur entgegennehmen. Die einfachste heißt raw_input. Wenn diese Funktion aufgerufen wird, halt das Programm an und wartet darauf, dass der Benutzer etwas eintippt. Wenn der Benutzer danach die Eingabetaste durckt, fahrt das Programm fort und raw_input gibt aus, was der Benutzer als string eingetippt hat.

>>> input = raw_input ()   
What are you waiting for?   
>>> print input   
What are you waiting for?

Bevor man raw_input aufruft, ist es eine gute Idee, eine Meldung auf den Bildschirm zu schreiben, die dem Benutzer mitteilt, was er da eingeben soll. Eine solche Meldung nennt man **Prompt**. Wir konnen einen Prompt als Argument der raw_input-Funktion ubergeben:

>>> name = raw_input ("What...is your name? ")   
What...is your name? Arthur, King of the Britons!   
>>> print name   
Arthur, King of the Britons!

Wenn wir erwarten, dass die Antwort eine Ganzzahl sein wird, konnen wir auch die input-Funktion verwenden:

prompt = "Was ... ist die Fluggeschwindigkeit einer unbelasteten Schwalbe?\n"   
speed = input(prompt)

Wenn der Benutzer nun einen String von Ziffern eingibt, wird dieser in eine Ganzzahl umgewandelt und der Variablen speed zugewiesen. Leider wird das Programm aber absturzen, wenn der Benutzer einen Buchstaben eingibt, der keine Ziffer ist.

>>> speed = input (prompt)   
Was ... ist die Fluggeschwindigkeit einer unbelasteten Schwalbe?   
Meinst du eine afrikanische oder eine europaische Schwalbe?   
SyntaxError: invalid syntax

Um diese Art von Fehler zu vermeiden, ist es im Allgemeinen eine gute Idee, raw_input zu verwenden und damit einen String zu erhalten, der dann mit Umwandlungsfunktionen in andere Typen umgewandelt werden kann.

### 4.13 Glossar

**Modulo-Operator**
    Ein Operator, dargestellt durch das Prozent-Zeichen (%), der mit Ganzzahlen arbeitet und fur die Division einer Zahl durch eine andere den Rest berechnet.
**modulus operator**
    An operator, denoted with a percent sign (%), that works on integers and yields the remainder when one number is divided by another.

**boolescher Ausdruck**
    Ein Ausdruck, der entweder wahr oder falsch ist.
**boolean expression**
    An expression that is either true or false.

**Vergleichsoperator**
    Einer der Operatoren, die zwei Werte vergleichen: ==, !=, >, <, >=, und <=.
**comparison operator**
    One of the operators that compares two values: ==, !=, >, <, >=, and <=.

**logischer Operator**
    Einer der Operatoren, die boolesche Ausdrucke kombinieren: and, or, und not.
**logical operator**
    One of the operators that combines boolean expressions: and, or, and not.

**bedingte Anweisung**
    Eine Anweisung, die die Programmausfuhrung in Abhangigkeit von einer Bedingung kontrolliert.
**conditional statement**
    A statement that controls the flow of execution depending on some condition.

**Bedingung**
    Der boolesche Ausdruck in einer bedingten Anweisung, der entscheidet, welcher Zweig auszufuhren ist.
**condition**
    The boolean expression in a conditional statement that determines which branch is executed.

**zusammengesetzte Anweisung**
    Eine Anweisung, die aus einem Kopf und einem Korper besteht. Der Kopf endet mit einem Doppelpunkt (:). Der Korper wird relativ zum Kopf eingeruckt.
**compound statement**
    A statement that consists of a header and a body. The header ends with a colon (:). The body is indented relative to the header.

**Block**
    Eine Gruppe von aufeinanderfolgenden Anweisungen die gleich weit eingeruckt sind.
**block**
    A group of consecutive statements with the same indentation.

**Korper**
    Der Block in einer zusammengesetzten Anweisung, der dem Kopf folgt.
**body**
    The block in a compound statement that follows the header.

**geschachtelt**
    Eine Programm-Struktur innerhalb einer anderen, wie etwa eine bedingte Anweisung innerhalb eines Zweiges einer anderen bedingten Anweisung.
**nesting**
    One program structure within another, such as a conditional statement inside a branch of another conditional statement.

**Rekursion**
    Der Prozess, dass die Funktion aufgerufen wird, die gerade ausgefuhrt wird .
**recursion**
    The process of calling the function that is currently executing.

**Basis-Fall**
    Ein Zweig der bedingten Anweisung in einer rekursiven Funktion, der keinen rekursiven Aufruf enthalt.
**base case**
    A branch of the conditional statement in a recursive function that does not result in a recursive call.

**unendliche Rekursion**
    Eine Funktion, die sich selbst rekursiv aufruft, ohne jemals den Basis-Fall zu erreichen. Schließlich wird eine unendliche Rekursion einen Laufzeit-Fehler verursachen.
**infinite recursion**
    A function that calls itself recursively without ever reaching the base case. Eventually, an infinite recursion causes a runtime error.

**Prompt**
    Eine visuelles Signal, dass dem Benutzer anzeigt, dass er Daten eingeben soll.
**prompt**
    A visual cue that tells the user to input data.
  


## Kapitel 5

### 5.1 Ruckgabewerte

Einige der eingebauten Funktionen, die wir benutzt haben, wie z. B. die mathematischen Funktionen, haben Ergebnisse erzeugt. Der Aufruf solcher Funktionen erzeugt einen neuen Wert der an das aufrufende Programm "zuruckgegeben" und dort normalerweise einer Variablen zugeordnet oder als Teil von einem Ausdruck verwendet wird.

e = math.exp(1.0)   
height = radius * math.sin(angle)

Aber bis jetzt hat keine der Funktionen, die wir selbst geschrieben haben, einen Wert zuruckgegeben.

In diesem Kapitel werden wir Funktionen schreiben, die Werte zuruckgeben. Wir werden sie kurz **Funktionen mit Wert** nennen; wir suchen einen besseren Namen. Das erste Beispiel ist area(), das die Flache eines Kreises mit gegebenem Radius zuruckgibt.

import math

def area(radius):   
temp = math.pi * radius**2   
return temp

Wir haben die return-Anweisung schon fruher gesehen, aber in einer Funktion mit Wert enthalt die return-Anweisung einen **Ruckgabewert**. Diese Anweisung bedeutet: "Kehre sofort von dieser Funktion zuruck und benutze den folgenden Ausdruck als Ruckgabewert." Der dafur vorgesehene Ausdruck kann beliebig kompliziert sein. Wir hatten daher auch obige Funktion in knapperer Form schreiben konnen:

def area(radius):   
return math.pi * radius**2

Auf der anderen Seite erleichtern **Hilfsvariablen** wie temp das Auffinden von Fehlern.

Manchmal ist es nutzlich, mehrere return-Anweisungen zu haben, eine in jedem Zweig einer bedingten Anweisung.

def absoluteValue(x):   
if x < 0:   
return -x   
else:   
return x

Da die return-Anweisungen in einer alternativen Verzweigung stehen, wird nur eine davon ausgefuhrt. Sobald eine ausgefuhrt ist, endet die Ausfuhrung der Funktion, ohne dass irgendwelche folgenden Anweisungen ausgefuhrt werden.

Code, der nach einer return-Anweisung steht oder an irgendeiner anderen Stelle, die von der Programmausfuhrung niemals erreicht werden kann, nennt man **toten Code**.

In einer Funktion mit Wert ist es eine gute Idee, sicherzustellen, dass jeder mogliche Weg durch das Programm schließlich auf eine return-Anweisung trifft.

def absoluteValue(x):   
if x < 0:   
return -x   
elif x > 0:   
return x

Dieses Programm ist nicht korrekt, weil wenn x zufallig gleich 0 ist, ist keine der beiden Bedingungen wahr und die Funktion endet ohne dass eine return-Anweisung ausgefuhrt wird. In diesem Fall wird ein spezieller Wert zuruckgegeben: None.

>>> print absoluteValue(0)   
None

> _Als Übung schreibe eine Funktion compare, die 1 zuruckgibt, wenn x > y, 0 wenn x == y, und -1 wenn x < y ist._

### 5.2 Programmentwicklung

An dieser Stelle solltest du imstande sein, den Code kompletter Funktionen zu lesen und zu verstehen, was er tut. Wenn du die Übungen ausgefuhrt hast, hast du auch schon einige kleine Funktionen geschrieben. Sobald du großere Funktionen schreibst, wirst du wahrscheinlich mehr Schwierigkeiten haben, speziell mit Laufzeitfehlern und logischen Fehlern.

Um mit zunehmend komplexeren Programmen umzugehen, mochten wir eine Technik empfehlen, die wir **schrittweise Programmentwicklung** nennen. Das Ziel der schrittweisen Programmentwicklung ist es, lange Sitzungen zur Fehlersuche zu vermeiden, indem wir unserem Programm Code jeweils nur in kleinen Abschnitten hinzufugen und testen.

Als Beispiel: angenommen, du mochtest die Entfernung zwischen zwei Punkten, die durch die Koordinaten (x1, y1) und (x2, y2) gegeben sind, finden. Nach dem pythagoraischen Lehrsatz ist diese Entfernung:

Der erste Schritt ist zu uberlegen, wie eine distance-Funktion in Python ausschauen sollte. Mit anderen Worten, was sind die Eingaben (Parameter) und was ist die Ausgabe (Ruckgabewert)?

In dieserm Fall sind die zwei Punkte die Eingabewerte, die wir darstellen konnen, indem wir vier Parameter benutzen. Der Ruckgabewert ist die Entfernung, die eine Gleitkommazahl sein wird.

Wir konnen nun schon eine Struktur fur die Funktion aufschreiben:

def distance(x1, y1, x2, y2):   
return 0.0

Offenbar berechnet diese Version der Funktion noch keine Entfernungen; sie gibt immer null zuruck. Aber sie ist syntaktisch korrekt und sie ist lauffahig. Das heißt wir konnen sie testen, bevor wir sie weiterentwickeln.

Um die neue Funktoin zu testen, rufen wir sie mit Beispielwerten auf:

>>> distance(1, 2, 4, 6)   
0.0

Wir haben die Werte so gewahlt, dass die horizontale Entfernung 3 ist und die vertikale Entfernung 4; auf diese Weise sollte das Ergebnis 5 sein (die Hypotenuse eines 3-4-5 Dreiecks). Wenn man eine Funktion testet, ist es nutzlich, die richtige Antwort zu wissen.

An diesem Punkt haben wir bestatigt, dass die Funktion syntaktisch korrekt ist und wir konnen somit weitere Codezeilen hinzufugen. Nach jedem Änderungsschritt werden wir die Funktion wieder testen. Wenn ein Fehler an irgendeiner Stelle auftritt, wissen wir dann, wo er sein muss in der letzten Zeile, die wir hinzugefugt haben.

Ein logischer erster Schritt in der Berechnung ist es, die Differenzen der Koordinaten x2 \- x1 und y2 \- y1 zu finden. Wir werden diese Werte in Hilfsvariablen mit den Namen dx und dy speichern und sie auf den Bildschirm ausgeben.

def distance(x1, y1, x2, y2):   
dx = x2 - x1   
dy = y2 - y1   
print "dx is", dx   
print "dy is", dy   
return 0.0

Wenn die Funktion richtig arbeitet, sollten die Ausgaben 3 und 4 sein, Ist das der Fall, wissen wir, dass die Funktion die richtigen Argumente erhalt und die erste Berechnung richtig ausfuhrt. Wenn nicht, dann sind nur wenige Zeilen zu uberprufen.

Als nachstes berechnen wir die Summe der Quadrate von dx und dy:

def distance(x1, y1, x2, y2):   
dx = x2 - x1   
dy = y2 - y1   
dsquared = dx**2 + dy**2   
print "dsquared is: ", dsquared   
return 0.0

Beachte, dass wir die print-Anweisungen, die wir im vorigen Schritt geschrieben haben, wieder entfernt haben. Solchen Code nennt man **Gerustcode**, denn er ist hilfreich fur die Konstruktion eines Programms aber _nicht_ Teil der Endprodukts.

Wir lassen das Programm in dieser Entwicklungsstufe wieder laufen und uberprufen die Ausgabe (die hier 25 sein sollte).

Schließlich konnen wir, wenn wir den math-Modul importiert haben, die sqrt-Funktion verwenden um das Ergebnis zu berechnen und zuruckzugeben.

def distance(x1, y1, x2, y2):   
dx = x2 - x1   
dy = y2 - y1   
dsquared = dx**2 + dy**2   
result = math.sqrt(dsquared)   
return result

Wenn das richtig arbeitet, sind wir fertig. Andernfalls wirst du vielleicht den Wert von result vor der return-Anweisung auf den Bildschirm ausgeben wollen.

Wenn du beginnst zu programmieren, solltest du nur ein oder zwei Codezeilen auf einmal hinzufugen. Je mehr Erfahrung du gesammelt hast, desto eher wirst du großere Codeabschnitte schreiben, testen und debuggen. Jedenfalls kann dir die Methode der schrittweisen Programmentwicklung eine Menge Zeit fur die Fehlersuche einsparen helfen.

Die wesentlichen Elemente dieser Vorgangsweise sind:

  1. Beginne mit einem arbeitenden Programm und mache stets nur kleine Erweiterungen. An jeder Stelle wirst du dann wissen, wo ein auftretender Fehler steckt.
  2. Benutze Hilfsvariable um Zwischenergebnisse zu speichern. So kannst du diese ausgeben und uberprufen.
  3. Wenn das Programm einmal richtig arbeitet, wirst du Gerust-Code, falls noch vorhanden, entfernen oder mehrere Anweisungen in kompaktere Ausdrucke zusammenfassen wollen, aber nur, wenn dadurch das Programm nicht schwerer lesbar wird. 

> _Als eine Übung verwende nun die Methode der schrittweisen Programmentwicklung um eine Funktion mit Namen hypotenuse zu schreiben, die die Lange der Hypotenuse eines rechtwinkeligen Dreiecks zuruckgibt, wenn die Langen der zwei Katheten gegeben sind. (Notiere bei deiner Arbeit jede Entwicklungsstufe in dem schrittweisen Prozess)._

### 5.3 Verknupfung

Wie du wahrscheinlich schon erwartest, kann man eine Funktion von innerhalb einer anderen aufrufen. Diese Vorgangsweise nennt man **Verknupfung**

Als Beispiel werden wir eine Funktion schreiben, die zwei Punkte, den Mittelpunkt eines Kreises und einen Punkt auf seinem Umfang als Parameter hat und die Flache des Kreises berechnet.

Angenommen, dass der Mittelpunkt in den Variablen xc und yc gespeichert ist und der Punkt auf dem Umfang in den Variablen xp und yp. Der erste Schritt ist, den Radius des Kreises zu finden, d. h. den Abstand zwischen diesen beiden Punkten ist. Glucklicherweise gibt es eine Funktion distance(), die gerade das tut:

radius = distance(xc, yc, xp, yp)

Der zweite Schritt ist, die Flache des Kreises mit diesem Radius zu finden und diesen Wert zuruckzugeben:

result = area(radius)   
return result

Wenn wir das in eine Funktion verpacken, erhalten wir:

def area2(xc, yc, xp, yp):   
radius = distance(xc, yc, xp, yp)   
result = area(radius)   
return result

Wir haben diese Funktion area2() genannt, um sie von der area()-Funktion, die wir fruher definiert haben zu unterscheiden. Es kann nur _eine_ Funktion mit einem bestimmten Namen in einem gegebenen Modul geben.

Die Hilfsvariablen radius und result sind nutzlich fur die Entwicklung und die Fehlersuche, aber wenn das Programm einmal richtig funktioniert, konne wir es knapper gestalten, indem wir die Funktionsaufrufe verknupfen:

def area2(xc, yc, xp, yp):   
return area(distance(xc, yc, xp, yp))

> _Als eine Übung schreibe eine Funktion slope(x1, y1, x2, y2), die den Anstieg einer Geraden durch die Punkte (x1, y1) und (x2, y2) zuruckgibt. Benutze dann diese Funktion in einer weiteren Funktion namens intercept(x1, y1, x2, y2), die fur die Gerade durch die Punkte (x1, y1) und (x2, y2) den Anschnitt auf der y-Achse zuruckgibt._

### 5.4 Boolesche Funktionen

Funktionen konnen boolesche Werte zuruckgeben, was oft bequem ist, wenn man komplizierte Überprufungen in Funktionen verstecken mochte. Zum Beispiel:

def isDivisible(x, y):   
if x % y == 0:   
return 1 # it's true   
else:   
return 0 # it's false

Der Name dieser Funktion ist isDivisible(). Es ist gebrauchlich booleschen Funktioen Namen zu geben, die wie ja/nein - Fragen klingen. isDivisible gibt entweder 1 oder 0 zuruck um anzuzeigen ob der Parameter x durch den Parameter y teilbar ist oder nicht.

Wir konnen die Funktion wieder kanpper formulieren, wenn wir vorteilhaft die Tatsache benutzen, dass die Bedingung der if-Anweisung selbst ein boolescher Ausdruck ist. Wir konnen diesen direkt zuruckgeben und damit die if-Anweisung ganz vermeiden:

def isDivisible(x, y):   
return x % y == 0

Die folgende Sitzung zeift die neue Funktion in Aktion:

>>> isDivisible(6, 4)   
0   
>>> isDivisible(6, 3)   
1

Boolesche Funktionen werden oft in bedingten Anweisungen verwendet:

if isDivisible(x, y):   
print "x is divisible by y"   
else:   
print "x is not divisible by y"

Es mag verlockend sein, etwas wie das folgende zu schreiben:

if isDivisible(x, y) == 1:   
...

Aber dieser Extra-Vergleich ist unnotig.

> _Als eine Übung schreibe eine Funktion isBetween(x, y, z), die 1 zuruckgibt, wenn y < x < z oder 0 andernfalls._

### 5.5 Mehr Rekursion

Bis jetzt hast du erst eine kleine Teilmenge von Python gelernt, aber es wird dich vielleicht interessieren zu efahren, dass diese Teilmenge eine _vollstandige_ Programmiersprache ist. Das bedeutet, dass alles, was uberhaupt berechnet werden kann in dieser Sprache ausgedruckt werden kann. Jedes Programm, das jemals geschrieben wurde, konnte auch ausschließlich mit _den_ Sprachelementen formuliert werden, die du bis jetzt gelernt hast (genau genommen wurdest du noch ein paar Befehle brauchen, um Gerate wie die Tastatur, die Maus, Disks usw. anzusprechen, aber das ist alles).

Diese Behauptung zu beweisen ist eine nicht triviale Übung, die zuerst Alan Turing gelungen ist, einem der ersten Computerwissenschafter (manche wurde behaupten, dass er ein Mathematiker war, aber viele fruhe Computerwissenschafter begannen als Mathematiker). Dementsprechend wird sie als Turing-These bezeichnet. Wenn du dich mit theoretischer Informatik beschaftigst, wird dir der Beweis wahrscheinlich uber den Weg laufen.

Um dir eine Vorstellung davon zu geben, was du mit den Werkzeugen, die du bis jetzt gelernt hast, anstellen kannst, werden wir uns mit ein paar rekursiv definierten mathematischen Funktionen beschaftigen. Eine rekursive Definition ist in dem Sinn einer zirkularen Definition ahnlich, als die Definition einen Bezug auf die Sache enthalt, die definiert wird. Eine echt zirkulare Definition ist nicht sehr nutzlich:

Wurdest du diese Definition in einem Worterbuch finden, warest du wohl verargert. Wenn du andererseits die Defnition der mathematischen Funktion Faktorielle nachschaust, wirst du ungefahr folgendes finden:

Diese Definition besagt, dass die Faktorielle von 0 gleich 1 ist und dass die Faktorielle von jedem anderen Wert, n, gleich n multipliziert mit der Faktoriellen von n-1 ist. So ist 3! gleich 3 mal 2!, und das ist gleich 2 mal 1!, und das ist gleich 1 mal 0!. Setzt man das alles zusammen, so wird 3! gleich 3 mal 2 mal 1 mal 1 und das ergibt 6.

Wenn du eine rekursive Definition von etwas aufschreiben kannst, dann kannst du normalerweise auch ein Python-Programm schreiben, um das auszurechnen. Der erste Schritt ist zu entscheiden, was die Parameter fur diese Funktion sind. Mit nur geringer Anstrengung solltest du zu dem Schluß kommen, dass die Faktorielle, also die Funktion factorial(), nur einen einzigen Parameter hat:

def factorial(n):

Sollte das Argument 0 sein, so brauchen wir nur 1 zuruckgeben:

def factorial(n):   
if n == 0:   
return 1

Andernfalls, und das ist der interessantere Teil, mussen wir einen rekursiven Aufruf machen um die Faktorielle von n-1 zu finden und dann diese mit n multiplizieren:

def factorial(n):   
if n == 0:   
return 1   
else:   
recurse = factorial(n-1)   
result = n * recurse   
return result

Der Progammablauf fur dieses Programm ist ahnlich wie der Ablauf von countdown() in [Abschnitt 4.9](http://python4kids.net/how2think/kap04.htm). Wenn wir factorial() mit dem Wert 3 aufrufen, schaut er so aus:

Da 3 nicht gleich 0 ist, nehmen wir den zweiten Zweig und berechnen die Faktorielle von 3-1...

> Da 2 nicht gleich 0 ist, nehmen wir den zweiten Zweig und berechnen die Faktorielle von 2-1... 
>
>> Da 1 nicht gleich 0 ist, nehmen wir den zweiten Zweig und berechnen die Faktorielle von 1-1... 
>>
>>> Da 0 _gleich_ 0 ist, nehmen wir den ersten Zweig und geben 1 zuruck ohne weitere rekursive Aufrufe zu machen. 
>> 
>> Der Ruckgabewert (1) wird multipliziert mit n, welches hier 1 ist, und das Ergebnis, 1, wird zuruckgegeben. 
> 
> Der Ruckgabewert (1) wird multipliziert mit n, welches hier 2 ist, und das Ergebnis, 2, wird zuruckgegeben. 

Der Ruckgabewert (2) wird multipliziert mit n, welches hier 3 ist, und das Ergebnis, 6, wird zuruckgegeben als der Ruckgabewert des Funktionsaufrufes, der den ganzen Prozess ins Rollen gebracht hat.

Und so schaut das Stackdiagramm fur diese Folge von Funktionsaufrufen aus:

Dabei ist auch eingezeichnet, wie die Ruckgabewerte den Stack hinaufgereicht werden. In jedem Rahmen ist der Ruckgabewert der Wert von result, welches das Produkt von n und recurse ist.

Beachte, dass im letzten Stackelement die lokalen Variablen recurse und result nicht existieren, weil der Zweig, der sie erzeugt nicht ausgefuhrt wurde.

### 5.6 Vertrauensvorschuß

Den Programmablauf zu verfolgen ist ein Weg um Programme zu lesen, aber der kann schnell ziemlich muhsam werden. Eine Alternative ist das, was wir hier "Vertrauensvorschuß" nennen. Wenn du zu zu einem Funktionsaufruf kommst, dann vertraue darauf (anstatt dem Programmablauf zu folgen), dass die Funktion korrekt funktioniert und den passenden Wert zuruckgibt.

In der Tat brigst du ja schon dieses Vertrauen auf, wenn du eingabaute Funktionen verwendest. Wenn du math.cos() oder math.exp() aufrufst, uberprufst du ja auch nicht die Implementationen dieser Funktionen. Du nimmst einfach an, dass sie richtig funktionieren, weil die Leute, die diese eingebauten Funktionsbibliotheken geschrieben haben, gute Programmierer sind.

Dasselbe trifft auch zu, wenn du eine deiner eigenen Funktionen aufrufst. Wir haben zum Beispiel im Abschnitt [ 5.4](http://python4kids.net/how2think/kap05.htm), eine Funktion mit dem Namen isDivisible() geschrieben, die herausfindet, ob eine Zahl durch eine andere teilbar ist. Haben wir uns einmal uberzeugt, dass diese Funktion korrekt ist durch Testen und Überprufung des Codes konnen wir diese Funktion benutzen ohne jedesmal wieder den Code anzuschauen.

Dasselbe trifft auch auf rekursive Programme zu. Wenn du zum rekursiven Aufruf kommst, solltest du (anstatt dem Programmablauf zu folgen) annehmen, dass der rekuresive Aufruf richtig arbeitet (d. h. das korrekte Ergebnis liefert) und dich dann fragen: "Angenommen, ich kann die Faktorielle von n-1 finden, kann ich dann die Faktorielle von n berechnen?" In diesem Fall ist es klar, dass das geht, namlich durch Multiplikation mit n.

Naturlich ist es ein bißchen seltsam, anzunehmen, dass die Funktion korrekt arbeitet, wenn du sie noch nicht einmal fertig programmiert hast, und darum sagen wir hier dass du mit einem Vertrauens_vorschuß_ arbeitest.

### 5.7 Noch ein Beispiel

Im vorhergehenden Beispiel haben wie Hilfsvariable benutzt, um die Schritte genau hinzuschreiben und den Code so zu gestalten, dass wir Fehler leicht finden konnen. Aber wir hatten auch einige Zeilen einsparen konnen:

def factorial(n):   
if n == 0:   
return 1   
else:   
return n * factorial(n-1)

Von jetzt an werden wir hier eher die knappere Form benutzen, aber wir raten dir, eher die ausfuhrlichere Form zu benutzen, solange du Programmcode entwickelst. Wenn er einmal richtig arbeitet, kannst du ihn ja immer noch knapper gestalten, wenn du dazu Lust verspurst.

Nach der Faktoriellen ist das bekannteste Beispiel fur eine rekursiv definierte mathematische Funktion fibonacci(). Fibonacci hat die folgende Definition:

fibonacci(0) = 1   
fibonacci(1) = 1   
fibonacci(n) = fibonacci(n-1) + fibonacci(n-2); 

In Python ubersetzt schaut das so aus:

def fibonacci (n):   
if n == 0 or n == 1:   
return 1   
else:   
return fibonacci(n-1) + fibonacci(n-2)

Wenn du versuchst, hier dem Programmablauf zu folgen, wird dir dein Kopf schon fur ziemlich kleine Werte von n platzen. Aber entsprechend unserer Methode des Vertrauensvorschusses ist es klar, dass du, unter der Annahme dass die beiden rekursiven Aufrufe richtig funktionieren, das richtige Ergebnis erhaltst, wenn du ihre beiden Ruckgabewerte addierst.

### 5.8 Typ - Überprufung

Was geschieht, wenn wir factorial() mit dem Argument 1.5 aufrufen?

>>> factorial (1.5)   
RuntimeError: Maximum recursion depth exceeded

Schaut nach unendlicher Rekursion aus. Aber wie kann das sein? Es gibt doch einen Basis-Fall wenn n == 0. Das Problem ist hier, dass die Werte von n den Basis-Fall _verfehlen_.

Im ersten rekursiven Aufruf ist der Wert von n gleich 0.5. Im nachsten ist er -0.5. Von da weg wird er immer kleiner und kleiner, aber er wird niemals gleich 0.

Wir haben hier zwei Moglichkeiten zur Auswahl. Wir konnen versuchen, die factorial()-Funktion zu verallgemeinern, damit sie auch mit Gleitkommazahlen funktioniert; oder wir konnen factorial() dazu bringen, den Typ des ubergebenen Arguments zu uberprufen. Die erste Option fuhrt zur sogenannten Gamma-Funktion und ist ein bißchen außerhalb des Rahmens dieser Ausfuhrungen. So wahlen wir die zweite Option:

Wir konnen type() verwenden um den Typ des Parameters mit dem Typ einer bekannten ganzen Zahl (z. B. 1) zu vergleichen. Wenn wir schon dabei sind, stellen wir auch gleich sicher, dass der Parameter nicht negativ ist:

def factorial (n):   
if type(n) != type(1):   
print "Factorial is only defined for integers."   
return -1   
elif n < 0:   
print "Factorial is only defined for positive integers."   
return -1   
elif n == 0:   
return 1   
else:   
return n * factorial(n-1)

Nun haben wir drei Basis-Falle. Der erste fangt nicht ganzzahlige Argumente ab, der zweite negative ganze Zahlen. In beiden Fallen gibt das Programm eine Fehlermeldung auf den Bildschirm aus und einen speziellen Wert, -1, zuruck um anzuzeigen, dass irgendetwas falsch gelaufen ist.

>>> factorial ("fred")   
Factorial is only defined for integers.   
-1   
>>> factorial (-2)   
Factorial is only defined for positive integers.   
-1

Wenn wir einmal weiter als bis zu diesen beiden Überprufungen gekommen sind, dann wissen wir, dass n eine positive ganze Zahl ist und wir konnen zeigen, dass die Rekursion einmal abbricht.

Dieses Programm demonstriert ein Muster, dass manchmal als **Wachter** bezeichnet wird. Die ersten beiden Zweige spielen die Rolle von Wachtern, die den nachfolgenden Code vor Werten bewahren, die einen Fehler verursachen konnten. Die Wachter ermoglichen zu beweisen, dass der Code korrekt ist.

### 5.9 Glossary

**Funktion mit Wert**
    Eine Funktion, die einen Wert zuruckgibt.
**fruitful function**
    A function that yields a return value.

**Ruckgabewert**
    Der Wert der als Ergebnis eines Funktionsaufrufes bereitgestellt wird.
**return value**
    The value provided as the result of a function call.

**Hilfsvariable**
    Eine Variable, die benutzt wird, um eine Zwischenergebnis in einer komplexen Berechnung zu speichern.
**temporary variable**
    A variable used to store an intermediate value in a complex calculation.

**toter Code**
    Teil eines Programms, der niemals ausgefuhrt wird, oftmals weil er nach einer return-Anweisung steht.
**dead code**
    Part of a program that can never be executed, often because it appears after a return statement.

**None**
    Ein besonderer Python-Wert, der von Funktionen zuruckgegeben wird, die keine return-Anweisung oder nur return-Anweisungen ohne Argument haben.
**None**
    A special Python value returned by functions that have no return statement, or a return statement without an argument.

**schrittweise Entwicklung**
    Eine Methode der Programmentwicklung mit dem Ziel Fehlerbeseitigung weitgehend zu vermeiden indem jeweils nur ein kleiner Codeabschnitt hinzugefugt und getestet wird.
**incremental development**
    A program development plan intended to avoid debugging by adding and testing only a small amount of code at a time.

**Gerust-Code**
    Code, der wahrend der Programmentwicklung benutzt wird, aber nicht Teil der endgultigen Version des Programms ist.
**scaffolding**
    Code that is used during program development but is not part of the final version.

**Wachter**
    Eine Bedingung, die Bedingungen uberpruft und behandelt, die einen Fehler hervorrufen konnten.
**guardian**
    A condition that checks for and handles circumstances that might cause an error.
  


## Kapitel 6

### 6.1 Mehrfache Zuweisungen

Wie du vielleicht schon entdeckt hast, ist es legal, einer Variablen mehr als einmal einen Wert zuzuweisen. Eine neue Wertzuweisung bewirkt, dass eine schon existierende Variable nun auf einen neuen Wert verweist (und damit aufhort auf den fruheren Wert zu verweisen).

bruce = 5   
print bruce,   
bruce = 7   
print bruce

Die Ausgabe dieses Programms ist 5 7, weil das erste Mal, wenn bruce ausgegeben wird, ist der Wert dieser Variablen 5 und das zweite Mal ist ihr Wert 7. Das Komma am Ende der ersten print-Anweisung bewirkt, dass nach der Ausgabe des Strings keine neue Zeile begonnen wird. Deshalb erscheinen beide Ausgaben in einer Zeile.

Hier ist **mehrfache Zuweisung** in einem Zustandsdiagramm dargestellt:

Wenn man mit mehrfachen Zuweisungen arbeitet ist es besonders wichtig, zwischen Zuweisungsoperationen und Vergleichen zur Feststellung von Gleichheit zu unterscheiden. Weil Python das Gleichheitszeichen (=) fur Zuweisungen verwendet, verfallt man leicht in den Fehler eine Anweisung wie a = b als einen Ausdruck fur Gleichheit zu interpretieren. Das ist er aber nicht!

Zunachst ist Gleichheit kommutativ und Zuweisung nicht. Zum Beispiel gilt in der Mathematik, wenn a = 7 ist, dann ist auch 7 = a. Aber in Python ist die Anweisung a = 7 legal aber 7 = a ist (syntaktisch) nicht legal.

Außerdem ist in der Mathematik eine festgestellte Gleichheit immer wahr. Wenn _jetzt_ a = b gilt, dann wird _stets_ a gleich b sein. In Python kann eine Wertzuweisung zwei Variablen gleich machen, aber sie mussen deshalb nicht gleich bleiben:

a = 5   
b = a # a and b are now equal   
a = 3 # a and b are no longer equal

Die dritte Zeile andert den Wert von a, aber sie andert nicht den Wert von b, daher sind sie auch nicht mehr gleich. (In manchen Programmiersprachen wird ein anderes Symbol fur die Wertzuweisung verwendet, wie z. B. <\- oder :=, um diese Art von Verwechslung zu vermeiden.)

Obwohl mehrfache Wertzuweisungen haufig hilfreich sind, sollte man sie mit Vorsicht verwenden. Wenn die Werte von Variablen sich haufig andern, kann das den Code schwer lesbar und schwer zu debuggen machen.

### 6.2 The while statement

Computer werden oft verwendet, um immer wiederkehrende Aufgaben zu automatisieren. Die Wiederholung identischer oder ahnlicher Aufgaben ohne Fehler zu machen ist etwas, das Computer gut konnen, Menschen aber schlecht.

Wir haben zwei Programme gesehen, nLines() und countdown(), die Rekursion benutzen um Wiederholungen auszufuhren, was man auch **Iteration** nennt. Weil Iteration so haufig vorkommt, stellt Python mehrere Sprachelemente zur Verfugung, um ihre Verwendung zu erleichtern. Das erste davon, das wir jetzt betrachten werden, ist die while-Anweisung.

So schaut countdown() aus, wenn man eine while-Anweisung verwendet.

def countdown(n):   
while n > 0:   
print n   
n = n-1   
print "Blastoff!"

Da wir den rekursiven Aufruf entfernt haben, ist diese Funktion nicht rekursiv.

Denkt man sich fur das englische Wort while das deutsche Wort "solange", so kann man die while-Anweisung beinahe so lesen, als ware sie Umgangssprache. Sie bedeutet: "Solange n großer als 0 ist, fahre fort mit der Ausgabe von n auf den Bildschirm und anschließender Verminderung von n um 1. Wenn du bei 0 angekommen bist, dann gib das Wort "Blastoff!" aus.

Wir konnen das formaler darstellen als Programmablauf der while-Anweisung:

  1. Werte die Bedingung aus, die entweder 0 oder 1 ergibt.
  2. Wenn die Bedingung falsch ist (0), verlasse die while-Anweisung und fahre mit der Ausfuhrung bei der nachsten Anweisung fort.
Wenn die Bedingung wahr ist (1), fuhre jede Anweisung im Korper der while-Anweisung aus und gehe zuruck zu Schritt 1. 

Der Korper besteht aus all den Anweisungen unter dem Kopf, die die gleiche Einruckungstiefe haben.

Dieser Typ von Programmablauf wird **Schleife** genannt, weil der dritte Schritt wieder zuruck an den Anfang fuhrt. Beachte, dass wenn die Bedingung schon bei der ersten Prufung falsch ist, die Anweisungen im inneren der Schleife (im Schleifenkorper) niemals ausgefuhrt werden.

Der Korper der Schleife sollte den Wert von einer oder mehreren Variablen andern, sodass schließlich die Bedingung falsch wird und die Schleife endet. Andernfalls wird die Schleife endlos wiederholt, was man naturgemaß eine **Endlosschleife** nennt.

An dieser Stelle enthalt die englische Fassung dieses Kurses folgende Bemerkung:

An endless source of amusement for computer scientists is the observation that the directions on shampoo, "Lather, rinse, repeat," are an infinite loop.

Ob derart Treffendes auch auf deutsch beschrifteten Shampoo-Behaltnissen steht, entzieht sich meiner Kenntnis. Bitte um Nachricht an den Übersetzer.

Im Falle von countdown(), konnen wir beweisen, dass die Schleife endet, weil wir wissen, dass der Wert von n endlich ist und wir konnen sehen, dass der Wert von n bei jedem Schleifendurchgang kleiner wird. Daher kommen wir schließlich bei 0 an. In anderen Fallen kann das nicht so leicht gesagt werden:

def sequence(n):   
while n != 1:   
print n,   
if n%2 == 0: # n is even   
n = n/2   
else: # n is odd   
n = n*3+1

Die Bedingung fur diese Schleife ist n != 1, daher wird die Schleife solange ausgefuhrt, bis n gleich 1 ist, wodurch die Bedingung falsch wird.

Bei jedem Schleifendurchgang gibt das Progamm den Wert von n aus und pruft dann ob es gerade oder ungerade ist. Wenn er gerade ist wird der Wert von n durch 2 dividiert. Wenn er ungerade ist, wird der Wert ersetzt durch n*3+1. Wenn zum Beispiel der Startwert (das Argument, das der Funktion ubergeben wird) 3 ist, dann ist die resultierende Zahlenfolge 3, 10, 5, 16, 8, 4, 2, 1.

Da n manchmal ansteigt und manchmal fallt, gibt es keinen offensichtlichen Beweis dafur, dass n jemals 1 erreichen wird oder dafur, dass das Programm jemals endet. Fur einige spezielle Werte von n konnen wir beweisen, dass das Programm endet: z. B. wenn der Startwert eine Potenz von 2 ist, dann wird der Wert von n bei jedem Schleifendurchgang gerade bleiben, bis er schließlich 1 wird. Das vorangehende Beispiel endet mit einer solchen Folge, die mit 16 beginnt.

Abgesehen von speziellen Fallen ist es eine interessante Frage, ob wir beweisen konnen, dass dieses Programm fur _alle_ Werte von n endet. Bis heute ist niemand im Stande gewesen, das zu beweisen _oder_ zu widerlegen.

> _Als eine Übung, schreibe die Funktion nLines() aus [Abschnitt 4.9](http://python4kids.net/how2think/kap04.htm) neu, wobei du Iteration an Stelle von Rekursion benutzt._

### 6.3 Tabellen

Eines der Dinge, fur die Schleifen gut sind, ist die Erzeugung von tabellarischen Daten. Bevor Computer so leicht verfugbar waren, mussten die Leute mit Logarithmen, Sinus- und Cosinuswerte mit der Hand rechnen. Um das zu erleichtern, enthielten Mathematikbucher lange Tabellen mit den Werten dieser Funktionen. Die Erzeugung dieser Tabellen war langsam und langweilig und sie hatten die Tendenz voller Fehler zu sein.

Als die Computer aufkamen, war eine der ersten Reaktionen: "Das ist großartig! Wir konnen die Computer benutzen, um diese Tabellen zu erzeugen. Dann werden keine Fehler mehr drin sein." Das stellte sich als (weitgehend) wahr aber kurzsichtig heraus. Denn bald danach waren Computer und Taschenrechner so allgegenwartig, dass die Tabellen uberflussig wurden.

Gut, fast. Fur manche Operationen benutzen Computer selbst Tabellen von Werten um naherungsweise Antworten zu erhalten und sie fuhren dann Rechnungen aus, um die Naherungswerte z verbessern. In manchen Fallen traten auch Fehler in den zugrundeliegenden Tabellen auf, am beruhmtesten in der Tabelle, die der Intel Pentium benutzte um Gleitkomma-Divisionen durchzufuhren.

Obwohl also eine "Logarithmen-Tafel" nicht mehr so nutzlich ist, wie sie fruher einmal war, ergibt sie doch ein gutes Beispiel fur Iteration. Das folgende Programm gibt eine Folge von Werten in der linken Spalte aus und deren Logarithmen in der rechten Spalte:

x = 1.0   
while x < 10.0:   
print x, '\t', math.log(x)   
x = x + 1.0

Der String '\t'+ stellt ein **tab**-Zeichen dar.

Wenn Zeichen und Strings auf dem Bildschirm dargetellt werden, kontrolliert eine unsichtbare Schreibmarke, der sogenannte Cursor, wo jeweils der nachste Buchstaben hingeschrieben wird. Nach einer print-Anweisung z. B. geht der Cursor normalerweise an den Anfang der nachsten Zeile.

Das tab-Zeichen verschiebt den Cursor nach rechts bis zum nachsten sogenannten tab-Stop. Tabs sind nutzlich, um Spalten von Text gleichmaßig auszurichten, wie es die Ausgabe des vorstehenden Programms zeigt:

1.0 0.0   
2.0 0.69314718056   
3.0 1.09861228867   
4.0 1.38629436112   
5.0 1.60943791243   
6.0 1.79175946923   
7.0 1.94591014906   
8.0 2.07944154168   
9.0 2.19722457734

Wenn dir diese Werte merkwurdig vorkommen, denke daran, dass die log-Funktioin die Basis e benutzt. Da Zweierpotenzen in der Computerwissenschaft so wichtig sind, wollen wir oft Logarithmen zur Basis 2 finden. Um das zu erreichen, konnen wir folgende Formel verwenden:

log2 x = 

loge x

loge 2

Andern wir die Ausgabe-Anweisung zu:

print x, '\t', math.log(x)/math.log(2.0)

so erhalten wir:

1.0 0.0   
2.0 1.0   
3.0 1.58496250072   
4.0 2.0   
5.0 2.32192809489   
6.0 2.58496250072   
7.0 2.80735492206   
8.0 3.0   
9.0 3.16992500144

Wir konnen sehen, dass 1, 2, 4 und 8 Zweierpotenzen sind, weil ihre Logarithmen zur Basis 2 ganze Zahlen sind. Wollen wir Logarithmen von anderen Potenzen von 2 finden, konnen wir das Programm wie folgt modifizieren:

x = 1.0   
while x < 100.0:   
print x, '\t', math.log(x)/math.log(2.0)   
x = x * 2.0

Hier addieren wir nicht in jedem Schleifendurchgang etwas zu x, was eine arithmetische Folge erzeugt, sondern wir multiplizieren x jedesmal mit einem bestimmten Faktor, sodaß es eine geometrische Folge durchlauft. Das Ergebnis ist:

1.0 0.0   
2.0 1.0   
4.0 2.0   
8.0 3.0   
16.0 4.0   
32.0 5.0   
64.0 6.0

Wegen des tab-Zeichens zwischen den Spalten hangt die Poition der zweiten Spalte nicht von der Anzahl der Ziffern in der ersten Spalte ab.

Mogen Logarithmen-Tabellen auch nicht mehr besonders nutzlich sein, so ist es fur Computerwissenschaftler die Kenntnis der Potenzen von 2 sicherlich.

> _Als eine Übung andere das Programm so ab, dass es die Potenzen von 2 bis hinauf zu 65 536 (das ist 216) ausgibt. Drucke sie aus und lerne sie auswendig._

Das backslash-Zeichen in '\t' zeigt den Anfang einer **escape-Sequenz** an. Escape-Sequenzen gebraucht man, um unsichtbare Zeichen wie tabs und Zeilenvorschub-Zeichen usw. darzustellen. Die escape-Sequenz '\n' das newline-Zeichen bewirkt, dass auf dem Bildschirm eine neue Zeile begonnen wird.

Eine escape-Sequenz kann uberall in einem String auftreten; in dem Beispiel oben ist die tab-escape-Sequenz das einzige Ding in dem String.

Wie glaubst du wird man einen backslash in einem String darstellen?

> _Als eine Übung schreibe einen einzigen String, der_
> 
> diese   
Ausgabe   
erzeugt.   


### 6.4 Zweidimensionale Tabellen

Eine zweidimensionale Tabelle ist eine Tabelle, bei der man Werte an Schnittpunkten von Zeilen und Spalten abliest. Eine Multiplikationstafel ist ein gutes Beispiel. Angenommen du mochtest eine Multiplikationstafel fur die Zahlen von 1 bis 6 erstellen.

Ein guter Ausgangspunkt ist es, eine Schleife zu schreiben, die die Vielfachen von 2 alle in eine Zeile schreibt:

i = 1   
while i <= 6:   
print 2*i, ' ',   
i = i + 1   
print

Die erst Zeile initialisiert eine Variable namens i, die als Zahler oder **Zahlvariable**, auch **Schleifenvariable** fungiert. Wenn die Schleife ausgefuhrt wird, wird der Wert von i von 1 auf 6 erhoht. Wenn i 7 ist, endet die Schleife. Bei jedem Schleifendurchgang wird der Wert von 2*i, gefolgt von drei Leerzeichen ausgegeben.

Wiederum unterdruckt das Komma in der print-Anweisung dass eine neue Zeile begonnen wird. Nachdem die Schleife ferig ist, bewirkt die zweite print-Anweisung (nur), dass eine neue Zeile begonnen wird.

Die Ausgabe dieses Programms ist:

So weit, so gut. Der nachste Schritt ist, das was wir haben zu **kapseln** und zu **verallgemeinern**.

### 6.5 Kapselung und Verallgemeinerung

Der Prozeß der Kapselung besteht darin, ein Stuck Code in eine Funktion zu verpacken und somit zu gestatten, alle die Vorteile, die Funktionen haben, zu nutzen. Du hast bis jetzt zwei Beispiele von Kapselung gesehen: printParity() in [Abschnitt ](); und isDivisible() in [Abschnitt 5.4](http://python4kids.net/how2think/kap05.htm).

Verallgemeinerung bedeutet, ausgehend von etwas Spezifischem - wie etwa: die Vielfachen von 2 auszugeben - etwas allgemeiner Verwendbares zu erzeugen, z. B. Ausgabe der Vielfachen einer beliebigen Zahl.

Die folgende Funktion kapselt die oben betrachtete Schleife und verallgemeinert sie so, dass Vielfachen von n ausgegeben werden.

def printMultiples(n):   
i = 1   
while i <= 6:   
print n*i, '\t',   
i = i + 1   
print

Um zu kapseln, haten wir nur die erste Zeile hinzuzufugen, die den Namen der Funktion und die Parameterliste festlegt. Um zu verallgemeinern, mußten wir nur den Wert 2 durch den Parameter n ersetzen.

Wenn wir diese Funktion mit dem Argument 2 aufrufen, bekommen wir dieselbe Ausgabe wie vorher. Mit dem Argument 3 ist die Ausgabe:

Mit dem Argument 4, ist die Ausgabe:

Jetzt sind wir soweit, dass du wahrscheinlich schon erraten wirst, wie man eine Multiplikationstabellen ausgeben kann namlich durch wiederholten Aufruf von printMultiples() mit verschiedenen Argumenten. In der Tat konnen wir auch noch eine weitere Schleife verwenden:

i = 1   
while i <= 6:   
printMultiples(i)   
i = i + 1

Beachte, wie ahnlich diese Schleife zu der innerhalb von printMultiples() ist. Wir hatten nur die print-Anweisung durch einen Funktionsaufruf zu ersetzen.

Die Ausgabe dieses Programms ist eine Multiplikationstafel:

1 2 3 4 5 6   
2 4 6 8 10 12   
3 6 9 12 15 18   
4 8 12 16 20 24   
5 10 15 20 25 30   
6 12 18 24 30 36

### 6.6 Noch einmal: Kapselung

Um nocheinmal Kapselung vorzuzeigen, nehmen wir den Code vom Ende des [Abschnitts 6.5](http://python4kids.net/how2think/kap06.htm) und verpacken auch ihn in eine Funktion:

def printMultTable():   
i = 1   
while i <= 6:   
printMultiples(i)   
i = i + 1

Dieser Prozess ist eine ubliche **Entwicklungs-Methode**. Wir entwickeln Code, indem wir Codezeilen ausserhalb von Funktionen schreiben oder sie direkt in den interaktiven Interpreter schreiben. Sobald unser Code funktioniert, nehmen wir ihn heraus und verpacken ihn in eine Funktion.

Diese Vorgangsweise ist besonders nutzlich, wenn du am Angfang der Entwicklung deines Programms noch nicht genau weißt, wie es in Funktionen aufgeteilt werden kann. Dieser Zugang gestattet dir, das Programm zu entwerfen, wahrend du es entwickelst.

### 6.7 Lokale Variable

Vielleicht wundert es dich, wieso man dieselbe Variable, i, sowohl in printMultiples() als auch in printMultTable() verwenden kann. Verursacht es keine Probleme, wenn eine der Funktionen den Wert dieser Variablen verandert?

Die Antwort ist nein, denn das i in printMultiples() und das i in printMultTable() sind _nicht_ dieselbe Variable.

Variablen, die innerhalb einer Funktionsdefinition erzeugt werden sind **lokal**; man kann eine lokale Variable nicht von ausserhalb der Funktion, in der sie erzeugt wurde, ansprechen. Das bedeutet, dass man die Freiheit hat mehrerer Variablen mit demselben Namen zu verwenden, solange das nicht in derselben Funktion geschieht.

Das Stack-Diagramm fur dieses Programm zeigt, dass die zwei Variablen mit Namen i nicht dieselbe Variable sind. Sie konnen auf verschiedene Werte verweisen und eine Änderung von einer beinflusst nicht die andere.

Der Wert von i in printMultTable() geht von 1 bis 6. In dem Diagramm ist er gerade 3. Beim nachsten Schleifendurchgang wird er 4 sein. Bei jedem Schleifendurchgang ruft printMultTable() die Funktion printMultiples() mit dem aktuellen Wert von i als Argument auf. Dieser Wert wird dem Parameter n zugewiesen.

Innerhalb von printMultiples() geht der Wert von i von 1 bis 6. Im Diagramm ist er gerade 2. Änderung dieser Variablen hat keine Auswirkung auf den Wert von i in printMultTable().

Es ist ublich und auch vollkommen legal, verschiedene lokale Variable mit demselben Namen zu verwenden. Insbesondere werden Namen wie i und j haufig fur Schleifenvariable verwendet. Wurdest du vermeiden, sie in einer Funktion zu verwenden, nur weil du sie auch schon anderswo verwendet hast, wurde das wahrscheinlich dazu fuhren, dass das Programm schwerer lesbar wird.

### 6.8 Noch einmal: Verallgemeinerung

Als ein weiteres Beispiel fur Verallgemeinerung stelle dir nun vor, du hattest gerne eine Programm, das Multiplikationstabellen beliebiger Große ausgeben konnte, nich nur die 6x6-Tabelle. Du konntest einen Parameter zu printMultTable() hinzufugen:

def printMultTable(high):   
i = 1   
while i <= high:   
printMultiples(i)   
i = i + 1

Wir haben den Wert 6 durch den Parameter high ersetzt. Wenn wir printMultTable() mit dem Argument 7 aufrufen, erhalten wir folgende Ausgabe:

1 2 3 4 5 6   
2 4 6 8 10 12   
3 6 9 12 15 18   
4 8 12 16 20 24   
5 10 15 20 25 30   
6 12 18 24 30 36   
7 14 21 28 35 42

Das ist fein, außer das wir vielleicht lieber hatten, das die Tabelle quadratisch ist mit derselben Anzahl von Zeilen und Spalten. Um das auch noch zu erreichen, fugen wir einen weiteren Parameter zu printMultiples() hinzu um festzulegen, wieviele Spalten die Tabelle haben soll.

Jetzt sind wir ein bißchen ekelhaft und nennen diesen Parameter wieder high, was zeigen soll, dass verschiedene Funktionen Parameter mit gleichem Namen haben konnen (gerade so wie lokale Variable). Hier ist das ganze Programm:

def printMultiples(n, high):   
i = 1   
while i <= high:   
print n*i, '\t',   
i = i + 1   
print

def printMultTable(high):   
i = 1   
while i <= high:   
printMultiples(i, high)   
i = i + 1

Beachte: als wir einen neuen Parameter hinzugefugt haben, mussten wir die erste Zeile der Funktion (den Funktions-Kopf) andern _und_ auch die Stelle in printMultTable(), wo die Funktion aufgerufen wird.

Wie erwartet erzeugt dieses Programm eine quadratische 7x7-Tabelle:

1 2 3 4 5 6 7   
2 4 6 8 10 12 14   
3 6 9 12 15 18 21   
4 8 12 16 20 24 28   
5 10 15 20 25 30 35   
6 12 18 24 30 36 42   
7 14 21 28 35 42 49

Wenn du eine Funktion in geeigneter Weise verallgemeinerst, erhaltst du oft ein Programm mit Fahigkeiten, die du gar nicht geplant hattest. Zum Beispiel konnte dir aufgefallen sein, dass, weil ab = ba, alle Eintrage in der Tabelle zweimal vorkommen. Du konntest Tinte sparen, wenn du nur die Halfte der Tabelle ausdruckst. Um das zu erreichen, musst du nur eine Zeile von printMultTable() andern. Ändere

printMultiples(i, high)

zu

printMultiples(i, i)

und du erhaltst

1   
2 4   
3 6 9   
4 8 12 16   
5 10 15 20 25   
6 12 18 24 30 36   
7 14 21 28 35 42 49

> _Als eine Übung verfolge die Ausfuhrung dieser Version von printMultTable() und finde heraus, wie sie funktioniert._

### 6.9 Funktionen

Wir haben nun schon einige Male "all die Vorteile von Funktionen" erwahnt. Vielleicht fragst du dich immer noch, was denn all diese Vorteile sein sollen. Hier sind einige:

  * Indem du einer Folge von Anweisungen einen Namen gibst, wird dein Prgramm leichter zu lesen, zu verstehen und die Fehlersuche wird erleichtert.
  * Das Aufteilen eines langen Programms in Funktionen gestattet es dir, Teile des Programms herauszunehmen, sie isoliert zu debuggen und sie dann wieder zu einem ganzen zusammenzusetzen.
  * Funktionen erleichtern die Anwendung von Rekursion und Iteration
  * Gut entworfene Funktionen sind oft nutzlich fur viele Programme. Hast du einmal eine geschrieben, debugged und getestet, kannst du sie wiederverwenden.

### 6.10 Glossar

**mehrfache Zuweisung**
    Das Auftreten von mehr als einer Wertzuweisung an dieselbe Variable wahrend der Ausfuhrung von einem Programm.
**multiple assignment**
    Making more than one assignment to the same variable during the execution of a program.

**Iteration**
    Wiederholte Ausfuhrung einer Folge von Anweisungen, wobei man entweder einen rekursiven Funktionsaufruf oder eine Schleife benutzt.
**iteration**
    Repeated execution of a set of statements using either a recursive function call or a loop.

**Schleife**
    Eine Anweisung oder eine Gruppe von Anweisungen, die wiederholt ausgefuhrt werden bis eine Abbruchbedingung erfullt ist.
**loop**
    A statement or group of statements that execute repeatedly until a terminating condition is satisfied.

**Endlosschleife**
    Eine Schleife, bei der die Abbruchbedingung niemals erfullt ist.
**infinite loop**
    A loop in which the terminating condition is never satisfied.

**Korper**
    Die Anweisungen im Inneren einer Schleife
**body**
    The statements inside a loop.

**Schleifenvariable**
    Eine Variable, die als Teil der Abbruchbedigung einer Schleife benutzt wird.
**loop variable**
    A variable used as part of the terminating condition of a loop.

**tab**
    Ein spezielles (nichtdruckendes) Zeichen (auch: ein Steuerzeichen), das den Cursor an die nachste tab-Stop-Position der aktuellen Zeile verschiebt.
**tab**
    A special character that causes the cursor to move to the next tab stop on the current line.

**newline**
    Ein spezielles Zeichen, das den Cursor an den Anfang der nachsten Zeile verschiebt.
**newline**
    A special character that causes the cursor to move to the beginning of the next line.

**Cursor**
    Eine unsichtbare Marke, die kontrolliert, wo das nachste Zeichen ausgegeben wird.
**cursor**
    An invisible marker that keeps track of where the next character will be printed.

**escape-Sequenz**
    Ein escape-Zeichen (\\), gefolgt von einem oder mehreren druckbaren Zeichen, die dazu benutzt werden ein nicht druckbares Zeichen zu bezeichnen.
**escape sequence**
    An escape character (\\) followed by one or more printable characters used to designate a nonprintable character.

**kapseln**
    Ein großes komplexes Programm in Komponenten (wie Funktionen) zerlegen und die Komponenten voneinander isolieren (z. B. durch Gebrauch lokaler Variablen).
**encapsulate**
    To divide a large complex program into components (like functions) and isolate the components from each other (by using local variables, for example).

**verallgemeinern**
    unnotig spezielle Dinge (wie z. B. einen konstanten Wert) durch etwas in geeigneter Weise Allgemeineres (z. B. eine Variable oder einen Parameter) ersetzen. Verallgemeinerung macht Code vielseitiger, leichter wiederverwendbar und manchmal auch leichter lesbar.
**generalize**
    To replace something unnecessarily specific (like a constant value) with something appropriately general (like a variable or parameter). Generalization makes code more versatile, more likely to be reused, and sometimes even easier to write.

**Entwicklungs-Methode**
    Ein Verfahren zur Entwicklung eines Programms. In diesem Kapitel haben wir einen Entwicklungsstil demonstriert, der auf der Entwicklung von Code fur einfache, spezielle Dinge basiert und dann diesen Code kapselt und verallgemeinert.
**development plan**
    A process for developing a program. In this chapter, we demonstrated a style of development based on developing code to do simple, specific things and then encapsulating and generalizing.
  


## Kapitel 7

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [glingl@aon.at](mailto:glingl@aon.at) _

### 7.1 Ein zusammengesetzter Datentyp

Bis jetzt haben wir drei Datentypen kennengelernt: int, float und string. String ist qualitativ verschieden von den anderen beiden, weil Strings aus kleineren Bausteinen zusammengesetzt sind aus Zeichen (character).

Typen, die kleinere Bausteine umfassen werden **zusammengesetzte Datentypen** oder auch **strukturierte Datentypen** genannt. Je nach dem was man gerade tut, mochte man einen zusammengesetzten Datentyp entweder als einzelnes Ding behandeln oder auf seine Bestandteile zugreifen. Es ist daher nutzlich, hier beide Moglichkeiten zur Verfugung zu haben.

Der Eckige-Klammer-Operator wahlt ein einzelnes Zeichen aus dem String aus.

>>> fruit = "banana"   
>>> letter = fruit[1]   
>>> print letter

Der Ausdruck fruit[1] entnimmt das Zeichen Nummer 1 aus fruit. Die Variable letter verweist auf das Ergebnis. Wenn wir letter ausgeben, erleben wir eine Überraschung:

a

Der erste Buchstabe von "banana" ist nicht a. Außer man ist ein Informatiker. Aus perversen Grunden beginnen Informatiker immer bei 0 zu zahlen. Der 0.te ("nullte") Buchstabe von "banana" ist b. Der 1. ("erste") Buchstabe ist a und der 2. ("zweite") Buchstabe ist n.

Mochte man den nullten Buchstaben eines Strings haben, tut man einfach eine 0, oder irgendeinen Ausdruck, der den Wert null ergibt, in die eckigen Klammern.

>>> letter = fruit[0]   
>>> print letter   
b

Den Ausdruck in den eckigen Klammern nennt man einen **Index**. Ein Index legt ein Element einer geordneten Menge fest, in unserem Fall der Menge der Buchstaben in einem String. Der Index gibt einfach an, welchen man meint. Er kann ein beliebiger Ganzzahl-Ausdruck sein.

### 7.2 Lange

Die len Funktion gibt die Anzahl der Zeichen in einem String zuruck:

>>> fruit = "banana"   
>>> len(fruit)   
6

Um den letzten Buchstaben eines Strings zu erhalten, konnte man versucht sein etwa folgendes auszuprobieren:

length = len(fruit)   
last = fruit[length] # FEHLER!

Das wird aber nicht funktionieren. Es verursacht den Laufzeitfehler IndexError: string index out of range. Das liegt daran, dass es im Wort "banana" keinen 6. Buchstaben gibt. Weil wir bei 0 zu zahlen beginnen, werden die 6 Buchstaben von 0 bis 5 durchnummeriert. Um das letzte Zeichen zu erhalten, mussen wir 1 von der Lange abziehen:

length = len(fruit)   
last = fruit[length-1]

Alternativ konnen wir auch negative Indizes verwenden, die vom Ende des Strings zuruck zahlen. Der Ausdruck fruit[-1] liefert den letzten Buchstaben, fruit[-2] den vorletzten und so weiter.

### 7.3 Durchlauf mit der for Schleife

Viele Berechnungen beinhalten die buchstabenweise Verarbeitung von Strings. Oft beginnen sie am Anfang, wahlen ein Zeichen nach dem anderen aus, machen irgendetwas damit und fahren so bis zum Ende fort. Dieses Verarbeitungsmuster nennen wir einen **Durchlauf**. Ein Weg um einen Durchlauf zu kodieren ist, eine while-Schleife zu verwenden:

index = 0   
while index < len(fruit):   
letter = fruit[index]   
print letter   
index = index + 1

Diese Schleife durchlauft den String und schreibt jeden Buchstaben in eine eigene Zeile. Die Schleifenbedingung ist index < len(fruit), daher wird die Bedingung falsch, wenn index gleich der Lange des Strings ist und der Schleifenkorper wird dann nicht mehr ausgefuhrt. Der letzte Buchstabe, auf den zugegriffen wird, ist der mit dem Index len(fruit)-1, welcher ja der letzte Buchstabe in dem String ist.

> _Übung: schreibe eine Funktion, die einen String als Argument ubernimmt und die Buchstaben von hinten nach vorne, einen pro Zeile ausgibt_

Einen Index zu verwenden um einen Satz von Werten zu durchlaufen ist so gebrauchlich, dass Python dafur eine alternative, einfachere Syntax bereitstellt die for Schleife:

for char in fruit:   
print char

Bei jedem Schleifendurchgang wird der nachste Buchstabe im String der Variablen char zugewiesen. Die Schleife wird so lange fortgesetzt, bis keine Buchstaben mehr ubrig sind.

Das folgende Beispiel zeigt, wie man Verkettung und eine for Schleife benutzen kann um eine ABC-Reihe zu erzeugen."ABC-Reihe" meint eine Reihe (Folge) oder Liste, in der die Elemente in alphabetischer Ordnung auftreten. Da gibt es z. B. in Robert McCloskeys Buch _Make Way for Ducklings_ die Namen der ducklings Jack, Kack, Lack, Mack, Nack, Ouack, Pack, and Quack. Die folgende Schleife gibt diese Namen in der richtigen Reihenfolge aus:

prefixes = "JKLMNOPQ"   
suffix = "ack"

for letter in prefixes:   
print letter + suffix

Die Ausgabe des Programms ist:

Jack   
Kack   
Lack   
Mack   
Nack   
Oack   
Pack   
Qack

Ganz ok ist das naturlich nicht, weil "Ouack" und "Quack" nicht richtig geschrieben sind.

> _Übung: modifiziere das Programm, um diesen Fehler zu beheben_

### 7.4 String - Abschnitte

Einen Abschnitt eines Strings nennt man auch ein **slice** (eine Scheibe). Die Auswahl eines Abschnitts ist ahnlich der Auswahl eines einzelnen Zeichens:

>>> s = "Peter, Paul, and Mary"   
>>> print s[0:5]   
Peter   
>>> print s[7:11]   
Paul   
>>> print s[17:21]   
Mary

Der Operator [n:m] gibt den Teil des Strings zuruck, der vom n-ten Buchstaben bis zum m-ten Buchstaben geht - den ersten eingeschlossen und den lezten ausgeschlossen. Dieses Verhalten widerspricht ein bisschen der Intuition; Man stellt sich vielleicht besser vor, dass die Indizes _zwischen_ die Buchstaben zeigen, wie im folgenden Diagramm:

Wenn man den ersten Index (vor dem Doppelpunkt) weglaßt, beginnt der Abschnitt am Anfang des Strings. Laßt man den zweiten Index weg, geht der Abschnitt bis zum Ende des Strings. Somit:

>>> fruit = "banana"   
>>> fruit[:3]   
'ban'   
>>> fruit[3:]   
'ana'

Was glaubst du wird s[:] bedeuten?

### 7.5 Vergleich von Strings

Die Vergleichsoperatoren funktionieren auch mit Strings. So pruft man, ob zwei Strings gleich sind:

if word == "banana":   
print "Yes, we have no bananas!"

Andere Vergleichsoperationen kann man verwenden, um Worter in alphabetische Reihenfoge zu bringen:

if word < "banana":   
print "Your word," \+ word + ", comes before banana."   
elif word > "banana":   
print "Your word," \+ word + ", comes after banana."   
else:   
print "Yes, we have no bananas!"

Man sollte sich aber bewußt sein, dass Python Groß\- und Kleinbuchstaben nicht so behandelt wie wir das gewohnt sind. Alle Großbuchstaben kommen namlich vor allen Kleinbuchstaben. Das ergibt z. B.:

Your word, Zebra, comes before banana.

Normalerweise lost man dieses Problem, indem man Strings in ein Standardformat, z. B. nur Kleinbuchstaben, umwandelt bevor man den Vergleich durchfuhrt. Ein Programm dazu zu bringen, zu erkennen, dass Zebras keine Fruchte sind, ist schon schwierigeres Problem .

### 7.6 Strings sind unveranderbar

Es ware naheliegend, den [] - Operator auf der linken Seite einer Wertzuweisung mit der Absicht zu verwenden, einen Buchstaben in einem String zu andern. Zum Beispiel:

greeting = "Hello, world!"   
greeting[0] = 'J' # ERROR!   
print greeting

Anstatt die Ausgabe Jello, world! zu erzeugen, liefert dieser Code aber nur einen Laufzeitfehler TypeError: object doesn't support item   
assignment.

Strings are **immutable**, which means you can't change an existing string. The best you can do is create a new string that is a variation on the original: Strings sind **nicht veranderbar** (engl.: _immutable_), das heißt, man kann einen existierenden String nicht verandern. Das beste, was man tun kann, ist einen neuen String zu erzeugen, der eine Variante des alten ist:

greeting = "Hello, world!"   
newGreeting = 'J' + greeting[1:]   
print newGreeting

Die Losung wird hier so erreicht, dass wir einen neuen ersten Buchstaben mit einem Abschnitt von greeting verketten. Diese Operation bewirkt keine Veranderung der ursprunglichen Strings.

### 7.7 Eine Funktion namens find 

Was macht die folgende Funktion?

def find(str, ch):   
index = 0   
while index < len(str):   
if str[index] == ch:   
return index   
index = index + 1   
return -1

In gewissem Sinne ist find das Gegenteil des [] - Operators. Anstatt zu einem gegebenen Index den entsprechenden Buchstaben herauszusuchen, nimmt es einen Buchstaben und findet den Index, wo sich der Buchstabe befindet. Wenn der Buchstabe uberhaupt nicht vorkommt, gibt die Funktion -1 zuruck.

Das ist das erste Beispiel, in dem eine return Anweisung innerhalb einer Schleife auftritt. Wenn str[index] == ch, dann gibt die Funktion sofort den Wert von index aus und bricht die Schleife fruhzeitig ab.

Wenn der Buchstabe in dem String nicht vorkommt, beendet das Programm die Schleife normal und gibt danach -1 zuruck.

Dieses Code-Muster nennt man manchmal einen "eureka" \- Durchlauf, denn sobald wir gefunden haben, wonach wir suchen konnen wir "Eureka" rufen und aufhoren weiter zu suchen.

> _Übung. andere die find Funktion so ab, dass sie einen dritten Parameter hat: den Index im String, bei dem die Suche begonnen werden soll._

### 7.8 Schleifen und Zahler

Das folgende Programm zahlt ab, wie oft der Buchstabe a in einem String vorkommt:

fruit = "banana"   
count = 0   
for char in fruit:   
if char == 'a':   
count = count + 1   
print count

Diese Programm demonstriert ein anderes Code-Muster, einen sogenannten **Zahler**. Die Variable count wird mit 0 initialisiert und dann wird ihr Wert jedesmal um 1 erhoht, wenn ein a gefunden wurde. (Man sagt auch oft: die Variable wird **inkrementiert**. Das ist das Gegenteil von dekrementieren, wo der Wert der Variablen um 1 vermindert wird).

> _Übung: kapsle diesen Code in eine Funktion namens countLetters und verallgemeinere so, dass die Funktion zwei Parameter hat: den String und den Buchstaben_

> _Übung: formuliere diese Funktion so um, dass sie die Drei-Parameter-Version von find aus der Übung davor verwendet, anstatt den String mit einer Schleife zu durchlaufen._

### 7.9 Der string Modul

Der string Modul enthalt nutzliche Funktionen, die Strings bearbeiten. Wie ublich, mussen wir den Modul importieren, befor wir ihn verwenden konnen:

>>> import string

Der string Modul enthalt eine Funktion namens find, die das gleiche tut wie die Funktion die wir geschrieben haben. Um sie aufzurufen, mussen wir den Namen des Moduls angeben und den Namen der Funktion, wobei wir die Punkt-Schreibweise benutzen:

>>> fruit = "banana"   
>>> index = string.find(fruit, "a")   
>>> print index   
1

Dieses Beispiel demonstriert einen der Vorteile von Modulen sie helfen Konflikte zwischen den Namen eingebauter Funktionen und den Namen benutzerdefinierter Funktionen zu vermeiden. Indem man die Punkt-Schreibweise verwendet kannman festlegen, welche Version von find man verwenden will.

Tatsachlich ist string.find allgemeiner als unsere Version. Erstens kann es Teilstrings finden und nicht nur Buchstaben:

>>> string.find("banana", "na")   
2

Weiters ubernimmt es ein zusatzliches Argument, dass den Index festlegt, mit bei dem die Suche beginnen soll:

>>> string.find("banana", "na", 3)   
4

Oder es kann zwei zusatzliche Argumente ubernehmen, die einen Bereich von Indizes festlegen:

>>> string.find("bob", "b", 1, 2)   
-1

In diesem Beispiel schlagt die Suche fehl, weil der Buchstabe _b_ in dem Indexbereich von 1 bis 2 (der ja 2 nicht mehr enthalt) nicht vorkommt.

### 7.10 Klassifikation von Zeichen

Es ist oft erforderlich ein einzelnes Zeichen zu betrachten und zu prufen, ob es ein Klein- oder ein Großbuchstabe ist oder ob es ein Buchstabe oder eine Ziffer ist. Der string Modul stellt einige Konstanten zur Verfugung, die fur diese Zwecke nutzlich sind.

Der String string.lowercase enthalt alle Buchstaben, die das System als Kleinbuchstaben betrachtet. Ähnlich enthalt string.uppercase alle Großbuchstaben. Probiere folgendes aus und sieh nach welches Ergebnis du erhaltst:

>>> print string.lowercase   
>>> print string.uppercase   
>>> print string.digits

Wir konnen dieses Konstanten und find dazu benutzen, Buchstaben zu klassifizieren. Wenn zum Beispiel find(lowercase, ch) einen anderen Wert als -1 zuruckgibt, dann muß ch ein Kleinbuchstabe sein:

def isLower(ch):   
return find(string.lowercase, ch) != -1

Alternativ konnen wir auch vom in Operator Gebrauch machen, der feststellt ob ein Zeichen in einem String vorkommt:

def isLower(ch):   
return ch in string.lowercase

Eine weitere Alternative ist, den Vergleichsoperator zu benutzen:

def isLower(ch):   
return 'a' <= ch <= 'z'

Wenn ch zwischen _a_ und _z_ liegt, muss es ein Kleinbuchsabe sein.

> _Übung: uberlege, welche Version von isLower wohl die schnellste sein wird. Kannst du dir auch noch andere Grunde neben der Ausfuhrungsgeschwindigkeit fur die Bevorzugung dieser oder jener Version vorstellen? _

Eine andere Konstante, die im string Modul definiert ist, wird dich vielleicht uberraschen, wenn du sie dir ansiehst:

>>> print string.whitespace

**Whitespace** Zeichen bewegen den Cursor ohne etwas auszugeben. Sie erzeigen den "weißen Raum" zwischen den sichtbaren Zeichen (zumindest auf weißem Papier). Die Konstante string.whitespace enthalt alle solchen nicht sichtbaren Zeichen, darunter das Leerzeichen, tab (\t), und newline (\n).

Es gibt noch eine Reihe weiterer nutzlicher Funktionen im string Modul. aber dieses Buch soll ja kein Referenz-Handbuch sein, im Gegensatz zur _Python Library Reference_. Zusammen mit weiterer reichhaltiger Dokumentation ist es auf der Python Website verfugbar: [www.python.org](http://www.python.org)

### 7.11 Glossar

**zusammengesetzter Datentyp**
    Ein Datentyp, bei dem die Werte aus Komponenten bestehen, also aus Elementen, die selbst Werte sind.
**compound data type**
    A data type in which the values are made up of components, or elements, that are themselves values.

**durchlaufen**
    Fur alle Elemente einer Menge der Reihe nach eine ahnliche Operation ausfuhren.
**traverse**
    To iterate through the elements of a set, performing a similar operation on each.

**Index**
    Eine Variable oder ein Wert, der dazu benutzt wird, ein Element einer geordneten Menge auszuwahlen, z. B. ein Zeichen aus einem String
**index**
    A variable or value used to select a member of an ordered set, such as a character from a string.

**Abschnitt**
    Ein Teil eines Strings, der durch einen Breich von Indizes festgelegt wird.
**slice**
    A part of a string specified by a range of indices.

**veranderbar**
    Ein zusammengesetzter Datentyp, dessen Elementen neu Werte zugeordnet werden konnen.
**mutable**
    A compound data types whose elements can be assigned new values.

**Zahler**
    Eine Variable, die dazu benutzt wird, etwas zu zahlen. Normlalerweise wird sie mit Null initialisiert und dann inkrementiert.
**counter**
    A variable used to count something, usually initialized to zero and then incremented.

**inkrementieren**
    Den Wert einer Variablen um eins erhohen.
**increment**
    To increase the value of a variable by one.

**dekrementieren**
    Den wert einer Variablen um eins verringern.
**decrement**
    To decrease the value of a variable by one.

**Whitespace-Zeichen**
    Alle Zeichen, die den Cursor bewegen, ohne sichtbare Zeichen auszugeben. Die Konstante string.whitespace enthalt alle "whitespace" \- Zeichen.
**whitespace**
    Any of the characters that move the cursor without printing visible characters. The constant string.whitespace contains all the whitespace characters.
  


## Kapitel 8

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [Gregor Lingl](mailto:glingl@aon.at) _

Eine **Liste** ist eine geordnete Menge von Werten, wobei jeder Wert mit einem Index angesprochen wird. Die Werte, die die Liste bilden, werden ihre **Elemente** genannt. Listen haben Ähnlichkeiten mit Strings, die geordnete Mengen von Zeichen sind. Die Elemente von Listen konnen dagegen beliebige Objekte sein. Listen und Strings und andere Dinge, die sich wie geordnete Mengen verhalten werden als **Sequenzen** bezeichnet.

### 8.1 Werte in Listen

Es gibt mehrere Moglichkeiten, eine neue Liste zu erzeugen. Die einfachste ist, ihre Elemente in eckige Klammern einzuschließen ([ and ]):

["spam", "bungee", "swallow"]

Das erste Beispiel ist eine Liste von vier ganzen Zahlen. Das zweite ist eine Liste von drei Strings. Die Elemente einer Liste mussen nicht alle vom selben Typ sein. Die folgende Liste enthalt einen String, eine Gleitkommazahl, eine Ganzzahl und (mirabile dictu) eine weitere Liste:

["hello", 2.0, 5, [10, 20]]

Eine Liste innerhalb einer anderen Liste wird als geschachtelte Liste bezeichnet.

Listen mit aufeinanderfolgenden Ganzzahlen sind so gebrauchlich, dass es in Python eine einfache Art gibt, sie zu erzeugen:

>>> range(1,5)   
[1, 2, 3, 4]

Die range Funktion ubernimmt zwei Argumente und gibt eine Liste zuruck, die alle Ganzzahlen vom ersten Argument bis zum zweiten enthalt, das erste eingeschlossen, das zweite aber nicht mehr!

Es gibt noch zwei andere Formen von range. Mit nur einem Argument erzeugt es eine Liste, die bei 0 beginnt:

>>> range(10)   
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

Wenn ein drittes Argument ubergeben wird, gibt dieses den Abstand zwischen aufeinanderfolgenden Werten an, was man die **Schrittweite** nennt. Dieses Beispiel erzeugt Werte von 1 (inklusive) bis 10 (exklusive) mit einer Schrittweite von 2:

>>> range(1, 10, 2)   
[1, 3, 5, 7, 9]

Schließlich gibt es noch eine spezielle Liste, die keine Elemente enthalt. Sie wird die leere Liste genannt und folgendermaßen notiert: [].

Mit all diesen Moglichkeiten, Listen zu erzeugen, ware es enttauschend, wenn wir Listen nicht als Werte in Variablen speichern oder sie als Argumente an Funktionen ubergeben konnten. Naturlich geht das.

vocabulary = ["ameliorate", "castigate", "defenestrate"]   
numbers = [17, 123]   
empty = []   
print vocabulary, numbers, empty   
['ameliorate', 'castigate', 'defenestrate'] [17, 123] []

### 8.2 Zugriff auf die Listenelemente

Die Syntax fur den Zugriff auf die Listenelemente ist dieselbe wie die Syntax fur den Zugriff auf die Zeichen eines Strings der Eckige-Klammer-Operator []). Der Ausdruck innerhalb der eckigen Klammern gibt den Index an. Man beachte, dass die Indizes bei 0 beginnen.

>>> print numbers[0]   
17   
>>> numbers[1] = 5   
>>>

Der Eckige-Klammer-Operator kann an beliebigen Stellen in einem Ausdruck vorkommen. Wenn er auf der linken Seite einer Wertzuweisung erscheint, dann andert diese das entsprechende Element in der Liste. Damit ist das "erste" Element von numbers, das zuvor 123 war, nun 5.

Jeder Ganzzahl-Ausdruck kann als Index verwendet werden:

>>> numbers[3-2]   
5   
>>> numbers[1.0]   
TypeError: sequence index must be integer

Wenn man versucht ein Element zu lesen oder zu schreiben, das nicht existiert, erhalt man einen Laufzeitfehler:

>>> numbers[2] = 5   
IndexError: list assignment index out of range

Hat ein Index einen negativen Wert, dann wird er vom Ende der Liste zuruckgezahlt:

>>> numbers[-1]   
5   
>>> numbers[-2]   
17   
>>> numbers[-3]   
IndexError: list index out of range

numbers[-1] ist das letzte Element der Liste, numbers[-2] ist das vorletzte, and numbers[-3]existiert (in unserem Beispiel) nicht.

Es ist gebrauchlich, Schleifenvariable als Listenindex zu verwenden.

horsemen = ["war", "famine", "pestilence", "death"]

i = 0   
while i < 4:   
print horsemen[i]   
i = i + 1

Diese while Schleife zahlt von 0 bis 4. Wenn die Schleifenvariable i gleich 4 ist, wird die Auswertung der Bedingung falsch ergeben und die Schleife abbrechen. Daher wird der Schleifenkorper nur fur die Werte 0, 1, 2 und 3 von i ausgefuhrt.

Bei jedem Schleifendurchlauf wird die Variable i als ein Index fur ein Listenelement benutzt, sodass das i.te Element ausgedruckt wird. Dieses Code-Muster wird als **Listendurchlauf** bezeichnet.

### 8.3 Die Lange einer Liste

Die Funktion len gibt die Lange einer Liste zuruck. Es empfiehlt sich, diesen Wert als obere Grenze fur Schleifen an Stelle von Konstanten zu verwenden. Auf diese Weise braucht man, wenn sich die Große der Liste andert, nicht ein ganzes Programm durchschauen um all die betroffenen Schleifen zu andern; sie werden fur jede Listengroße korrekt arbeiten:

horsemen = ["war", "famine", "pestilence", "death"]

i = 0   
while i < len(horsemen):   
print horsemen[i]   
i = i + 1

Das letzte Mal wird der Schleifenkorper durchlaufen, wenn i gleich len(horseman) - 1 ist, und das ist ja auch der Index des letzten Listenelements. Wenn i gleich len(horseman) ist, wird die Bedingung nicht mehr erfullt sein und der Schleifenkorper nicht mehr ausgefuhrt werden. Das ist gut so, denn len(horsemen) ist kein legaler Index mehr.

Obwohl eine Liste eine andere Liste enthalten kann, zahlt eine solche geschachtelte Liste nur als ein einziges Element. Die Lange der folgenden Liste ist vier:

['spam!', 1, ['Brie', 'Roquefort', 'Pol le Veq'], [1, 2, 3]]

> _Übung: schreibe eine Schleife, die die obige Liste durchlauft und die Lange von jedem Element ausgibt. Was geschieht, wenn man eine Ganzzahl an len ubergibt?_

### 8.4 Zugehorigkeit zu einer Liste

in ist ein boole'scher Operator, der pruft ob ein Objekt Element von einer Sequenz ist. Wir haben ihn im [Abschnitt 7.10](http://python4kids.net/how2think/kap07.htm) mit Strings verwendet, aber er funktioniert auch mit Listen und anderen Sequenzen:

>>> horsemen = ['war', 'famine', 'pestilence', 'death']   
>>> 'pestilence' in horsemen   
1   
>>> 'debauchery' in horsemen   
0

Weil "pestilence" ein Element der Liste horsemen ist, gibt der in - Operator wahr zuruck. Weil "debauchery" nicht in der Liste ist, gibt in falsch zuruck.

Wir konnen auch not in Kombination mit in verwenden, um zu prufen, ob ein Element nicht zu einer Liste gehort:

>>> 'debauchery' not in horsemen   
1

### 8.5 Listen und for Schleifen

Die for Schleife, die wir in [Abschnitt 7.3](http://python4kids.net/how2think/kap07.htm) gesehen haben, funktioniert auch mit Listen. Die verallgemeinerte Syntax einer for Schleife ist:

for VARIABLE in LISTE:   
KÖRPER

Diese Anweisung ist gleichwertig mit:

i = 0   
while i < len(LISTE):   
VARIABLE = LISTE[i]   
KÖRPER   
i = i + 1

Hier ist die vorige Schleife nocheinmal, diesmal geschrieben als for Schleife. Die for Schleife ist eine knappere Forumlierung, weil wir mit ihr die Schleifenvariable i eliminieren konnen.

for horseman in horsemen:   
print horseman

Liest sich fast wie Deutsch. Na ja, sagen wir wie Englisch: "For (every) horseman in (the list of) horsemen, print (the name of the) horseman." Jeder Listen-Ausdruck kann in einer for Schleife verwendet werden.

for number in range(20):   
if number % 2 == 0:   
print number

for fruit in ["banana", "apple", "quince"]:   
print "I like to eat " \+ fruit + "s!"

Das erste Beispiel gibt alle geraden Zahlen zwischen eins und zwanzig aus. Das zweite Beispiel druckt Begeisterung fur verschiedene Fruchte aus.

### 8.6 Operationen mit Listen

Der + Operator verkettet (auch) Listen:

>>> a = [1, 2, 3]   
>>> b = [4, 5, 6]   
>>> c = a + b   
>>> print c   
[1, 2, 3, 4, 5, 6]

In ahnlicher Weise vervielfacht der * Operator eine Liste die gegebene Anzahl von Malen.

>>> [0] * 4   
[0, 0, 0, 0]   
>>> [1, 2, 3] * 3   
[1, 2, 3, 1, 2, 3, 1, 2, 3]

Das erste Beispiel vervielfacht [0] vier Mal. Das zweite Beispiel vervielfacht die Liste [1, 2, 3] drei Mal.

### 8.7 Listen Abschnitte

Die Abschnitt-Operationen, die wir in [Abschnitt 7.4](http://python4kids.net/how2think/kap07.htm) gesehen haben, funktionieren auch fur Listen:

>>> list = ['a', 'b', 'c', 'd', 'e', 'f']   
>>> list[1:3]   
['b', 'c']   
>>> list[:4]   
['a', 'b', 'c', 'd']   
>>> list[3:]   
['d', 'e', 'f']   
>>> list[:]   
['a', 'b', 'c', 'd', 'e', 'f']

### 8.8 Listen sind veranderbar

Im Unterschied zu Strings sind Listen veranderbar. Das bedeutet, dass wir ihre Elemente andern konnen. Indem wir den Eckige-Klammer-Operator auf der linken Seite einer Wertzuweisung verwenden, konnen wir ein Element der Liste durch ein anderes ersetzen:

>>> fruit = ["banana", "apple", "quince"]   
>>> fruit[0] = "pear"   
>>> fruit[-1] = "orange"   
>>> print fruit   
['pear', 'apple', 'orange']

Mit dem Abschnitt-Operator konnen wir mehrere Elemente auf einmal ersetzen:

>>> list = ['a', 'b', 'c', 'd', 'e', 'f']   
>>> list[1:3] = ['x', 'y']   
>>> print list   
['a', 'x', 'y', 'd', 'e', 'f']

Wir konnen auch Elemente aus einer Liste entfernen, indem wir ihnen die leere Liste zuweisen:

>>> list = ['a', 'b', 'c', 'd', 'e', 'f']   
>>> list[1:3] = []   
>>> print list   
['a', 'd', 'e', 'f']

Und wir konnen Elemente zu einer Liste hinzufugen, indem wir sie in einen leeren Abschnitt an der gewunschten Stelle hineinpressen.

>>> list = ['a', 'd', 'f']   
>>> list[1:1] = ['b', 'c']   
>>> print list   
['a', 'b', 'c', 'd', 'f']   
>>> list[4:4] = ['e']   
>>> print list   
['a', 'b', 'c', 'd', 'e', 'f']

### 8.9 Elemente einer Liste loschen

Die Verwendung von Abschnitten zu Loschen von Listenelementen kann umstandlich und daher fehleranfallig sein. Python stellt dafur eine besser lesbare Alternative zur Verfugung:

del entfernt ein Element von einer Liste:

>>> a = ['one', 'two', 'three']   
>>> del a[1]   
>>> a   
['one', 'three']

Wie zu erwarten, verarbeitet del negative Indizes und verursacht Laufzeitfehler wenn der Index außerhalb des erlaubten Bereichs liegt.

Man kann auch Abschnitte als Index fur del verwenden:

>>> list = ['a', 'b', 'c', 'd', 'e', 'f']   
>>> del list[1:5]   
>>> print list   
['a', 'f']

Wie ublich wahlen Abschnitte alle Elemente bis zum, aber ausschließlich des, letzten Index aus.

### 8.10 Objekte und Werte

Wenn man die folgenden Wertzuweisungen ausfuhrt,

a = "banana"   
b = "banana"

ist klar, dass a und b auf Strings mit den Zeichen banana verweisen werden. Aber man kann nicht sagen, ob sie auf _denselben_ String zeigen.

Es gibt da zwei mogliche Zustande:

Im einen Fall verweisen a und b auf zwei verschiedene Dinge, die denselben Wert haben. Im zweiten Fall verweisen sie auf dasselbe Ding. Diese "Dinge" haben Namen -- sie werden **Objekte** genannt. Ein Objekt ist etwas, auf das eine Variable verweisen kann.

Jedes Objekt hat eine eindeutige **Kennung**, die man mit der id Funktion erhalt. Indem man diese Kennungen von a und b ausgibt, kann man feststellen, ob sie auf dasselbe Objekt verweisen.

>>> id(a)   
135044008   
>>> id(b)   
135044008

In der Tat bekommen wir dieselbe Kennung zwei Mal, was bedeutet, dass Python nur einen String erzeugt hat, und sowohl a als auch b darauf verweisen.

Interessanterweise verhalten sich Listen anders. Wenn man zwei Listen erzeugt, erhalt man zwei verschieden Objekte:

>>> a = [1, 2, 3]   
>>> b = [1, 2, 3]   
>>> id(a)   
135045528   
>>> id(b)   
135041704

Somit schaut das Zustandsdiagramm so aus:

a und b haben denselben Wert, verweisen aber nicht auf dasselbe Objekt.

### 8.11 Alias - Namen

Da also Variablen auf Objekte verweisen, geschieht es, dass wenn man eine Variable einer anderen zuweist, beide Variablen auf dasselbe Objekt verweisen:

>>> a = [1, 2, 3]   
>>> b = a

In diesem Fall schaut das Zustandsdiagramm so aus:

Weil dieselbe Liste zwei verschiedene Namen hat, a und b, nennt man diese beiden Aliasnamen. Verandert man das Objekt, das zum einen gehort, ist der andere mitbetroffen:

>>> b[0] = 5   
>>> print a   
[5, 2, 3]

Obwohl dieses Verhalten nutzlich sein kann, ist es manchmal unerwartet oder unerwunscht. Im allgemeinen ist es sicherer, Aliasnamen zu vermeiden, wenn man mit veranderbaren Objekten arbeitet. Naturlich gibt es fur nicht veranderbare Objekte dieses Problem nicht. Deshalb kann sich der Python-Interpreter die Freiheit nehmen, Aliasnamen fur Strings zu verwenden, wenn er dabei die Gelegenheit zu okonomischerem Verhalten erkennt.

### 8.12 Klonen von Listen

Wenn wir eine Liste verandern mochten und auch ein Kopie der originalen Liste behalten mochten, mussen wir die Moglichkeit haben, eine Kopie der Liste zu erzeugen und nicht nur einen Verweis auf sie. Dieser Vorgang wird manchmal **Klonen** genannt, um die Zweideutigkeit des Wortes "kopieren" zu vermeiden.

Der einfachste Weg eine Liste zu klonen ist, den Abschnitt-Operator zu verwenden:

>>> a = [1, 2, 3]   
>>> b = a[:]   
>>> print b   
[1, 2, 3]

Wenn man einen beliebigen Abschnitt von a erzeugt, wird eine neue Liste erzeugt. In diesem Fall besteht der Abschnitt eben aus der ganzen Liste.

Wir konnen nun unbedenklich Änderungen in b vornehmen, ohne uns um a kummern zu mussen.

>>> b[0] = 5   
>>> print a   
[1, 2, 3]

> _Übung: Zeichne Zustandsdiagramme fur a und b vor und nach dieser Änderung._

### 8.13 Listen als Parameter

Wenn man eine Liste als Argument ubergibt, ubergibt man in Wahrheit einen Verweis auf diese Liste, nicht eine Kopie der Liste. Zum Beispiel ubernimmt die Funktion head eine Liste als Parameter und gibt deren erstes Element zuruck:

def head(list):   
return list[0]

So wird sie verwendet:

>>> numbers = [1, 2, 3]   
>>> head(numbers)   
1

Der Parameter list und die Varible numbers sind Aliasnamen fur dasselbe Objekt. Das Zustandsdiagramm sieht so aus:

Da das Listenobjekt von zwei Rahmen gemeinsam verwendet wird, haben wir es zwischen die beiden gezeichnet.

Wenn eine Funktion einen Listenparameter andert, dann sieht auch der Aufrufer diese Änderung. Zum Beispiel entfernt deleteHead das erste Element von einer Liste:

def deleteHead(list):   
del list[0]

Und so wird deleteHead verwendet:

>>> numbers = [1, 2, 3]   
>>> delete_head(numbers)   
>>> print numbers   
[2, 3]

Wenn eine Funktion eine Liste zuruckgibt, dann gibt sie genau genommen einen Verweis auf die Liste zuruck. Zum Beispiel gibt tail eine Liste zuruck, die alle Elemente der gegebenen Liste bis auf das erste enthalt.

def tail(list):   
return list[1:]

Und so wird tail verwendet:

>>> numbers = [1, 2, 3]   
>>> rest = tail(numbers)   
>>> print rest   
[2, 3]

Weil der Ruckgabewert mit dem Abschnitt-Operator erzeugt wird, ist er eine neue Liste. Die Erzeugung von Rest und jede folgende Änderung von Rest haben keine Auswirkung auf numbers.

### 8.14 Geschachtelte Listen

Eine geschachtelte Liste ist eine Liste, die als ein Element in einer anderen Liste auftritt. In der folgenden Liste ist das "dritte" Element eine geschachtelte Liste:

>>> list = ["hello", 2.0, 5, [10, 20]]

Wenn manlist[3] ausgibt, erhalt man [10, 20]. Um auf eine Element aus einer geschachtelten Liste zuzugreifen, kann man in zwei Schritten vorgehen:

>>> elt = list[3]   
>>> elt[0]   
10

Man kann diese beiden Schritte aber auch kombinieren:

>>> list[3][1]   
20

Eckige-Klammer-Operatoren werden von links nach rechts ausgewertet. Daher ergibt dieser Ausdruck das "dritte" Element von list und sucht das "erste" Element davon heraus.

### 8.15 Matrixes

Geschachtelte Liste werden oft verwendet um Matrizen darzustellen. Zum Beispiel kann

so dargestellt werden:

>>> matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

matrix ist eine Liste von drei Elementen, wobei jedes Element eine Zeile der Matrix ist. Wir konnen eine ganze Zeile der Matrix auf ubliche Weise auswahlen:

>>> matrix[1]   
[4, 5, 6]

Oder wir konnen auf ein einzelnes Element der Matrix zugreifen, indem wir die Doppelindex-Form verwenden:

>>> matrix[1][1]   
5

Der erste Index wahlt die Zeile aus und der zweite Index wahlt die Spalte aus. Obwohl diese Art Matrizen darzustellen gebrauchlich ist, ist sie nicht die einzige Moglichkeit. Eine leichte Variation davon ist, eine Liste von Spalten zu verwenden. Spater werden wir eine grundlegender Alternative sehen, die ein "Dictionary" verwendet.

### 8.16 Strings und Listen

Die beiden nutzlichsten Funktionen im string Modul betreffen Listen von Strings. Die split Funktion zerlegt einen String in eine Liste von Wortern. Wenn nichts anderes angegeben wird, wird jede beliebige Anzahl von Whitespace-Zeichen als Wortgrenze genommen:

>>> import string   
>>> song = "The rain in Spain..."   
>>> string.split(song)   
['The', 'rain', 'in', 'Spain...']

Ein optionales Argument, das als **Begrenzer** bezeichnet wird, kann verwendet werden um festzulegen, welche Zeichen als Wortgrenzen verwendet werden sollen. Das folgende Beispiel benutzt den String ai als Begrenzer.

>>> string.split(song, 'ai')   
['The r', 'n in Sp', 'n...']

Man beachte, dass der Begrenzer in der Liste nicht vorkommt.

Die join-Funktion ist die inverse zu split. Sie ubernimmt eine Liste von Strings und verkettet deren Elemente mit Leerzeichen zwischen jedem Paar.

>>> list = ['The', 'rain', 'in', 'Spain...']   
>>> string.join(list)   
'The rain in Spain...'

Ebenso wie split ubernimmt auch join einen optionalen Begrenzer, der zwischen die Elemente eingefugt wird:

>>> string.join(list, '_')   
'The_rain_in_Spain...'

> _Übung: Beschreibe die Beziehung zwischen string.join(string.split(song)) und song. Sind sie fur alle Strings gleich? Wann sind sie verschieden?_

### 8.17 Glossar

**Liste**
    Eine benannte Kollektion von Objekten, wobei jedes Objekt uber einen Index angesprochen wird.
**list**
    A named collection of objects, where each object is identified by an index.

**Index**
    Eine Ganzzahl-Variable oder ein Ganzzahl-Wert, der ein Element einer Liste bezeichnet.
**index**
    An integer variable or value that indicates an element of a list.

**Element**
    Einer der Werte in einer Liste (oder in einer anderen Sequenz). Der Eckige-Klammer-Operator wahlt Elemente der Liste aus.
**element**
    One of the values in a list (or other sequence). The bracket operator selects elements of a list.

**Sequenz**
    Einer der Datentypen, die aus einer geordneten Menge von Elementen bestehen, wobei jedes Element durch einen Index identifiziert wird.
**sequence**
    Any of the data types that consist of an ordered set of elements, with each element identified by an index.

**geschachtelte Liste**
    Eine Liste, die Element einer anderen Liste ist.
**nested list**
    A list that is an element of another list.

**Listen-Durchlauf**
    Der sequentielle Zugriff auf alle Elemente einer Liste.
**list traversal**
    The sequential accessing of each element in a list.

**Objekt**
    Ein Ding, auf das eine Variable verweisen kann.
**object**
    A thing to which a variable can refer.

**Alias-Namen**
    Verschieden Variablennamen, die Verweise auf dasselbe Objekt enthalten.
**aliases**
    Multiple variables that contain references to the same object.

**klonen**
    Ein _neues_ Objekt erzeugen, das denselben Wert wie ein existierendes Objekt hat. Das Kopieren eines Verweises auf ein Objekt erzeugt einen Aliasnamen und klont das Objekt nicht.
**clone**
    To create a new object that has the same value as an existing object. Copying a reference to an object creates an alias but doesn't clone the object.

**Begrenzer**
    Ein Zeichen oder String, der dazu benutzt wird, festzulegen, wo ein String aufgespaltet werden soll.
**delimiter**
    A character or string used to indicate where a string should be split.
  


## Kapitel 9

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [glingl@aon.at](mailto:glingl@aon.at) _

### 9.1 Veranderbarkeit und Tupel

Bis jetzt haben wir zwei zusammengesetzte Datentypen kennengelernt: Strings, die aus Zeichen zusammengesetzt sind; und Listen, die aus Elementen von beliebigem Typ aufgebaut sind. Einer der Unterschiede zwischen diesen beiden war der, dass die Elemente einer Liste geandert werden konnen, die Zeichen eines Strings aber nicht. Mit anderen Worten: Strings sind **unveranderbar** und Listen sind **veranderbar**.

Es gibt in Python noch einen weiteren Datentyp, **Tupel** genannt, der dem Typ Liste ahnlich ist, aber unveranderbar. Syntaktisch ist ein Tupel eine Komma-separierte Liste von Werten:

>>> tuple = 'a', 'b', 'c', 'd', 'e'

Obwohl es nicht unbedingt notwendig ist, ist es ublich Tupel in runde Klammern einzuschließen:

>>> tuple = ('a', 'b', 'c', 'd', 'e')

Um ein Tupel mit nur einem Element zu erzeugen, muss man das letzte Komma anfugen:

>>> t1 = ('a',)   
>>> type(t1)   
<type 'tuple'>

Ohne das Komma behandelt Python ('a') als einen String in runden Klammern.

>>> t2 = ('a')   
>>> type(t2)   
<type 'string'>

Abgesehen von Syntax-Fragen sind die Operationen mit Tupeln dieselben wie die Operationen mit Listen. Der Index-Operator wahlt ein Element aus einem Tupel aus.

>>> tuple = ('a', 'b', 'c', 'd', 'e')   
>>> tuple[0]   
'a'

Und der Abschnitt-Operator wahlt einen Bereich von Elementen aus:

>>> tuple[1:3]   
('b', 'c')

Wenn man aber versucht, ein Element des Tupels zu andern, erhalt man eine Fehlermeldung:

>>> tuple[0] = 'A'   
TypeError: object doesn't support item assignment

Auch wenn man die Elemente eines Tupels nicht andern kann, kann man es doch durch ein anderes Tupel ersetzen:

>>> tuple = ('A',) + tuple[1:]   
>>> tuple   
('A', 'b', 'c', 'd', 'e')

### 9.2 Tupel-Wertzuweisung

Gelegentlich ist es nutzlich, die Werte von zwei Variablen zu vertauschen. Mit konventionellen Wertzuweisungen muß man dazu eine temporare Variable verwenden. Um zum Beispiel a und b zu vertauschen:

>>> temp = a   
>>> a = b   
>>> b = temp

Wenn man das oft tun muß, ist es doch ein bißchen muhselig. Python stellt eine Art der Tupel-Wertzuweisung bereit, die dieses Problem elegant lost:

>>> a, b = b, a

Die linke Seite ist ein Tupel von Variablen, die rechte Seite ein Tupel von Werten. Jeder Wert wird der entsprechenden Variablen zugewiesen. Alle Ausdrucke auf der rechten Seite werden ausgewertet bevor eine Wertzuweisung ausgefuhrt wird. Dies macht Tupel-Wertzuweisung recht vielseitig.

Naturlich mussen die Anzahl der Variablen auf der linken Seite und die Anzahl der Werte auf der rechten Seite ubereinstimmen:

>>> a, b, c, d = 1, 2, 3   
ValueError: unpack tuple of wrong size

### 9.3 Tupel als Ruckgabewerte

Funktionen konnen Tupel als Werte zuruckgeben. Wir konnten zum Beispiel eine Funktion schreiben, die zwei Parameter vertauscht:

def swap(x, y):   
return y, x

Dann konnen wir den Ruckgabewert einem Tupel aus zwei Variablen zuweisen.

a, b = swap(a, b)

In diesem Fall hat es keinen großen Vorteil, eine swap Funktion zu definieren. Es liegt sogar eine Gefahr in dem Versuch, swap in einer Funktion zu kapseln, wenn man es namlich (naheliegenderweise) so versuchen wurde:

def swap(x, y): # fehlerhafte Version!   
x, y = y, x

Wenn wir diese Funktion folgendermaßen aufrufen:

swap(a, b)

dann sind a und x Aliasnamen fur denselben Wert. Wenn man x innerhalb von swap andert, wird x auf einen anderen Wert verweisen, das hat aber keine Auswirkung auf a in __main__. Ebenso hat die Änderung von y keine Auswirkung auf b.

Diese Funktion wird ausgefuhrt, ohne eine Fehlermeldung zu produzieren, aber sie tut nicht das, was beabsichtigt war. Dies ist ein Beispiel fur einen logischen, oder semantischen, Fehler.

> _Übung: Zeichne ein Zustandsdiagramm fur diese Funktion. um besser einzusehen, warum sie nicht richtig funktioniert._

### 9.4 Zufallszahlen

Die meisten Computerprogramme tun jedes Mal dasselbe, wenn sie ausgefuhrt werden. Man sagt, sie sind **deterministisch**. Determinismus ist normalerweise eine gute Sache, da wir doch erwarten, dass dieselbe Berechnung auch stets dasselbe Ergebnis liefert. Fur manche Anwendungen mochten wir allerdings, dass der Computer unvorhesehbar agiert. Spiele sind ein offensichtliches Beispiel dafur, aber es gibt auch noch andere.

Ein Programm wirklich nichtdeterministisch zu machen stellt sich als ziemlich schwierig heraus. Es gibt aber Moglichkeiten zu erreichen, dass sie wenigstens nichtdeterministisch aussehen. Eine davon ist die Erzeugung von Zufallszahlen und von ihnen das Ergebnis eines Programms abhangig zu machen. Python hat eine eingebaute Funktion, die **Pseudozufallszahlen** erzeugt, die zwar nicht wirkliche Zufallszahlen im mathematischen Sinn sind, aber fur unsere Zwecke ausreichen.

Der random Modul enthalt eine Funktion namens random, die eine Gleitkommazahl zwischen 0.0 und 1.0 zuruckgibt. Jedesmal, wenn man random aufruft, erhalt man die nachste Zahl einer langen Folge. Um ein Beispiel zu sehen, kann man folgende Schleife ausfuhren:

import random

for i in range(10):   
x = random.random()   
print x

Um Zufallszahlen zwischen 0.0 und einer oberen Grenze, etwa high zu erzeugen, multipliziert man x mit high.

> _Übung: Erzeuge Zufallszahlen zwischen low und high._

> _Übung: Erzeuge **ganze** Zufallszahlen zwischen low and high, einschließlich der beiden Endpunkte._

### 9.5 Listen von Zufallszahlen

Der erste Schritt ist die Erzeugung einer Liste von Zufallswerten. randomList ubernimmt eine ganze Zahl als Parameter, die die Lange der Liste angibt. Sie gibt eine Liste von Zufallszahlen mit dieser Lange zuruck. Sie beginnt mit einer Liste von n Nullen. Bei jedem Schleifendurchlauf wird eines ihrer Elemente durch eine Zufallszahl ersetzt. Der Ruckgabewert ist ein Verweis auf die vollstandige Liste.

def randomList(n):   
s = [0] * n   
for i in range(n):   
s[i] = random.random()   
return s

Wir testen jetzt diese Funktion mit einer Liste von acht Elementen. Fur den Zweck der Fehlersuche ist es besser, klein anzufangen-

>>> randomList(8)   
0.15156642489   
0.498048560109   
0.810894847068   
0.360371157682   
0.275119183077   
0.328578797631   
0.759199803101   
0.800367163582

Es wird angenommen, dass die von random erzeugten Zufallszahlen gleichmaßig verteilt sind. Das heißt, das jeder Wert gleich wahrscheinlich ist.

Wenn wir den Bereich der moglichen Werte in gleich große "Schachteln" aufteilen und abzahlen, wie oft eine Zufallszahl in jede Schachtel fallt, dann sollten wir etwa die gleichen Anzahlen fur jede erhalten.

Wir konnen diese Theorie uberprufen, indem wir ein Programm schreiben, das den Bereich in solche "Schachteln" aufteilt und die Anzahl der Werte in jeder abzahlt.

### 9.6 Abzahlen

Ein guter Zugang zu Problemen dieser Art ist, sie in Teilprobleme aufzuspalten und dabei insbesonderer nach solchen Ausschau zu halten, die zu einem Berechnungsmuster (Code-Muster) passen, das man schon kennt.

In diesem Fall wollen wir ein Liste von Zahlen durchlaufen und abzahlen, wie oft ein Wert in einen gegebenen Bereich fallt. Das klingt bekannt. In [Abschnitt ]() haben wir ein Programm geschrieben, das einen String durchlaufen hat und dabei abgezahlt hat, wie oft ein gegebener Buchstabe vorkam.

Wir werden also einmal das alte Programm kopieren und es fur unser neues Problem anpassen. Das ursprungliche Programm war:

count = 0   
for char in fruit:   
if char == 'a':   
count = count + 1   
print count

Im ersten Schritt ersetzen wir fruit durch list und char durch num. Das andert das Programm nicht, sondern macht es nur lesbarer.

Im zweiten Schritt andern wir die Überprufung. Wir wollen nicht Buchstaben finden. Wir wollen wissen, ob num zwischen den gegebenen Werten low und high liegt.

count = 0   
for num in list   
if low < num < high:   
count = count + 1   
print count

Im letzten Schritt kapseln wir diesen Code in einer Funktion namens inBox. Parameter sind die Liste und die Werte von low und high.

def inBox(list, low, high):   
count = 0   
for num in list:   
if low < num < high:   
count = count + 1   
return count

Indem wir ein existierende Programm kopieren und dann abandern, konnen wir diese Funktion schnell schreiben und sparen eine Menge Zeit furs debuggen. Man nennt dieses Verfahren der Programmentwicklung **pattern matching**, also: Verwenden passender Muster. Wenn man merkt, dass man ein Problem, das vorliegt, schon einmal gelost hat, dann verwende man diese Losung wieder.

### 9.7 Viele Schachteln

Wenn die Anzahl der Schachteln anwachst, wird inBox ein bisschen umstandlich. Mit zwei Schachteln geht es ja noch:

low = inBox(a, 0.0, 0.5)   
high = inBox(a, 0.5, 1)

Aber mit vier Schachteln ist es schon etwas muhselig:

box1 = inBox(a, 0.0, 0.25)   
box2 = inBox(a, 0.25, 0.5)   
box3 = inBox(a, 0.5, 0.75)   
box4 = inBox(a, 0.75, 1.0)

Es liegen da zwei Probleme vor: das erste besteht darin, dass wir fur jede Schachtel einen neuen Variablennamen erfinden mussen. Das andere darin, dass wir den Bereich fur jede Schachtel berechnen mussen.

Wir werden das zweite Problem zuerst losen. Wenn die Anzahl der Schachteln gleich numBoxes ist, dann ist die "Breite" jeder Schachtel gleich 1.0 / numBoxes.

Wir werden eine Schleife verwenden um den Bereich jeder Schachtel zu berechnen. Die Schleifenvariable i zahlt von 0 bis numBoxes-1:

boxWidth = 1.0 / numBoxes   
for i in range(numBoxes):   
low = i * boxWidth   
high = low + boxWidth   
print low, "to", high

Die untere Grenze fur jede Box berechnen wir, indem wir die Schleifenvariable mit der Breite der Schachtel multiplizieren. Die obere Grenze is nun gerade eine boxWidth entfernt.

Mit numBoxes = 8, erhalten wir folgende Ausgabe:

0.0 to 0.125   
0.125 to 0.25   
0.25 to 0.375   
0.375 to 0.5   
0.5 to 0.625   
0.625 to 0.75   
0.75 to 0.875   
0.875 to 1.0

Man uberzeugt sich, dass jede Schachtel gleich breit ist, dass sie sich nicht uberlappen und dass sie den ganzen Bereich von 0.0 bis 1.0 uberdecken.

Kommen wir nun zu unserem ersten Problem zuruck. Wir mussen acht ganze Zahlen speichern, wobei wir die Schleifenvariable abenutzen, um jeweils eine zu bezeichnen. Wahrscheinlich fallt einem jetzt ein: Liste!

Wir mussen unserer Liste von Schachteln außerhalb der Schleife erstellen, weil wir das ja nur einmal zu tun brauchen. Innerhalb der Schleife werden wir inBox mehrmals aufrufen und das i.te Element der Liste auf neuesten Stand bringen:

numBoxes = 8   
boxes = [0] * numBoxes   
boxWidth = 1.0 / numBoxes   
for i in range(numBoxes):   
low = i * boxWidth   
high = low + boxWidth   
boxes[i] = inBox(list, low, high)   
print boxes

Mit einer Liste von 1000 Werten produziert dieser Code beispielsweise folgende "Schachtel"-Liste:

[138, 124, 128, 118, 130, 117, 114, 131]

Diese Zahlen sind alle ziemlich nahe an 125, was wir gar nicht anders erwartet haben. Zumindest sind sie nahe genug, dass wir daran glauben konnen, dass der Zufallsgenerator funktioniert.

> _Übung: Teste diese Funktion mit einigen langeren Listen und prufe ob sich fur die Anzahl der Werte in jeder "Schachtel" Abweichungen ergeben._

### 9.8 Eine Losung in einem Durchlauf

Obwohl dieses Programm funktioniert, ist es nicht so effizient, wie es sein konnte. Bei jedem Aufruf von inBox durchlauft es die ganze Liste. Wenn man die Anzahl der Schachteln vergroßert, ergibt das eine ganze Menge Durchlaufe.

Es ware besser nur einen Durchlauf durch die Liste zu machen und dabei fur jeden Wert den Index der Schachtel zu berechnen, in die er hinein gehort. Dann kann man den entsprechenden Zahler um eins erhohen.

Im vorigen Abschnitt nahmen wir einen Index i und multiplizierten ihn mir der boxWidth um die untere Grenze fur eine gegebene Schachtel zu finden. Nun wollen wir einen Wert zwischen 0.0 und 1.0 nehmen und den Index der Schachtel finden, in die er hineingehort.

Da dieses Problem die Umkehrung des vorhergehenden Problems ist, werden wir wohl durch boxWidth dividieren mussen, anstatt damit zu multiplizieren.

Und weil boxWidth = 1.0 / numBoxes ist, ist die Division durch boxWidth gleichwertig mit der Multiplikation mit numBoxes. Wenn wir eine Zahl im Bereich von 0.0 bis 1.0 mit numBoxes multiplizieren, erhalten wir eine Zahl im Bereich von 0.0 bis numBoxes. Wenn wir das auf die nachstkleinere ganze Zahl abrunden, bekommen wir genau das, was wir suchen einen Box-Index:

numBoxes = 8   
boxes = [0] * numBoxes   
for i in list:   
index = int(i * numBoxes)   
boxes[index] = boxes[index] + 1

Dabei haben wir die int - Funktion benutzt, um eine Gleitkommazahl in eine Ganzzahl umzuwandeln.

Ware es moglich, dass diese Berechnung einen Index erzeugt, der außerhalb des gultigen Bereichs liegt (also entweder negativ ist, oder großer als len(boxes)-1)?

Eine solche Liste von "Schachteln", die die Anzahlen einer Menge von Werten den entsprechenden Bereichen enthalten, wird ein **Histogramm** genannt.

> _Übung: Schreibe eine Funktion namens histogramm, die eine Liste von Werten und eine Anzahl von "Schachteln" als Paramter hat und ein Histogramm mit der gegebenen Anzahl von "Schachteln" zuruckgibt._

### 9.9 Glossar

**unveranderbarer Typ**
    Ein Typ, dessen Elemente nicht verandert werden konnen. Wertzuweisungen zu Elementen oder Abschnitten verursachen fur unveranderbare Typen einen Fehler.
**immutable type**
    A type in which the elements cannot be modified. Assignments to elements or slices of immutable types cause an error.

**veranderbarer Typ**
    Ein Datentyp, dessen Elemente verandert werden konnen. Alle veranderbaren Typen sind zusammengesetzte Typen. Listen und auch der Typ Dictionary sind veranderbare Datentypen, Strings und Tupel sind nicht veranderbar.
**mutable type**
    A data type in which the elements can be modified. All mutable types are compound types. Lists and dictionaries are mutable data types; strings and tuples are not.

**Tupel**
    Ein Sequenz-Typ, der dem Typ der Liste ahnlich ist, außer dass er unveranderbar ist. Tupel konnen uberall dort verwendet werden, wo ein unveranderbarer Typ gebraucht wird, zum Beispiel als Schlussel in einem Dictionary.
**tuple**
    A sequence type that is similar to a list except that it is immutable. Tuples can be used wherever an immutable type is required, such as a key in a dictionary.

**Tupel-Zuweisung**
    Eine Zuweisung zu allen Elementen eines Tupels in einer einzigen Wertzuweisung. Tupel-Zuweisung geschieht parallel und nicht in Folge nacheinander. Sie ist daher z. B. nutzlich fur das Vertauschen von Werten.
**tuple assignment**
    An assignment to all of the elements in a tuple using a single assignment statement. Tuple assignment occurs in parallel rather than in sequence, making it useful for swapping values.

**deterministisch**
    Ein Programm, das bei jedem Aufruf dasselbe macht.
**deterministic**
    A program that does the same thing each time it is called.

**Pseudozufallszahlen**
    Ein Folge von Zahlen, die wie zufallig aussieht, obwohl sie in Wahrheit das Ergebnis einer deterministischen Berechnung ist.
**pseudorandom**
    A sequence of numbers that appear to be random but that are actually the result of a deterministic computation.

**Histogramm**
    Eine Liste von ganzen Zahlen, in der jedes Element angibt, wie oft igendetwas vorgekommen ist.
**histogram**
    A list of integers in which each element counts the number of times something happens.

**pattern matching**
    Ein Programmentwicklungsverfahren, bei dem bereits bekannt Berechnungsmuster indentifiziert und fur die Losung eines ahnlichen Problems angepasst werden.
**pattern matching**
    A program development plan that involves identifying a familiar computational pattern and copying the solution to a similar problem.

# Der Datentyp Dictionary

_Captured: 2016-11-18 at 11:12 from [python4kids.net](http://python4kids.net/how2think/kap10.htm)_

## Kapitel 10

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [glingl@aon.at](mailto:glingl@aon.at) _

Die zusammengesetzten Datentypen, die wir bisher behandelt haben Strings, Listen und Tupel verwenden Ganzzahlen als Indizes. Versucht man, einen anderen Datentyp als Index zu benutzen, erhalt man eine Fehlermeldung.

Der Datentyp **Dictionary** (deutscher Begriff: _assoziative Liste_, nicht sehr gebrauchlich) ist den anderen zusammengesetzten Datentypen ahnlich. Ein Unterschied besteht darin, dass man beliebige unveranderbare Datentypen fur die Indizes verwenden kann. Als Beispiel werden wir ein Dictionary erzeugen um deutsche Worter in englische Worter zu ubersetzen. Fur dieses Dictionary sind die Indizes strings.

Ein Moglichkeit, ein dictionary zu erzeugen, ist mit einem leeren Dictionary zu beginnen und dann Elemente hinzuzufugen.

>>> ger2eng = {}   
>>> ger2eng['eins'] = 'one'   
>>> ger2eng['zwei'] = 'two'

Die erste Wertzuweisung erzeugt ein Dictionary namens ger2eng; die anderen Wertzuweisungen fugen dem Dictionary weitere Elemente hinzu. Wir konnen den aktuellen Wert des Dictionary auf die ubliche Weise ausgeben:

>>> print ger2eng   
{'eins': 'one', 'zwei': 'two'}

Die Elemente des Dictionary erscheinen in Form einer Komma-separierten Liste. Jedes Element enthalt einen Index und einen Wert, die durch einen Doppelpunkt voneinander getrennt sind. In einem Dictionary nennt man die Indizes **Schlussel** und daher die Elemente **Schlussel-Wert Paare**.

Ein andere Moglichkeit, ein Dictionary zu erzeugen, ist eine Liste von Schlussel-Wert Paaren in genau der Syntax anzugeben, die wir in obiger Ausgabe gesehen haben:

>>> ger2eng = {'eins': 'one', 'zwei': 'two', 'drei': 'three'}

Wenn wir nun den Wert von ger2eng neuerlich ausgeben, erleben wir eine Überraschung:

>>> print ger2eng   
{'zwei': 'two', 'eins': 'one', 'drei': 'three'}

Die Schlussel-Wert Paare sind nicht in der eingegebenen Reihenfolge. Zum Gluck gibt es keinen Grund, sich um diese Reihenfolge uberhaupt zu kummern, da die Elemente dieses Dictionary niemals mit ganzen Zahlen indiziert werden. Wir benutzen ja statt dessen die Schlussel um die entsprechenden Werte zu ermitteln:

>>> print ger2eng['zwei']   
'two'

Der Schlussel 'zwei' ergibt den Wert 'two' obwohl er im ersten Schlussel-Wert Paar erscheint.

### 10.1 Dictionary Operationen

Die del Anweisung entfernt ein Schlussel-Wert Paar aus dem Dictionary. Zum Beispiel enthalt das folgende Dictionary die Namen verschiedener Fruchte und die Angabe, wieviele Fruchte jeder Art auf Lager sind:

>>> inventar = {'Aepfel': 430, 'Bananen': 312, 'Birnen': 217, 'Orangen': 525}   
>>> print inventar   
{'Aepfel': 430, 'Birnen': 217, 'Orangen': 525, 'Bananen': 312}

Wenn jemand alle Birnen kauft, konnen wir den Eintrag fur die Birnen aus dem Dictionary entfernen:

>>> del inventa['Birnen']   
>>> print inventar   
{'Aepfel': 430, 'Orangen': 525, 'Bananen': 312}

Oder, wenn wir annehmen, dass bald wieder Birnen kommen, konnen wir den Wert, der mit den Birnen assoziiert ist, andern:

>>> inventar['Birnen'] = 0   
>>> print inventar   
{'Aepfel': 430, 'Bananen': 312, 'Orangen': 525, 'Birnen': 0}

Die len Funktion funktioniert auch mit dem Typ Dictionary; sie gibt die Anzahl der Schlussel-Wert Paare zuruck.

>>> len(inventar)   
4

### 10.2 Dictionary Methoden

Eine **Methode** ist ahnlich einer Funktion sie ubernimmt Parameter und gibt einen Wert zuruck aber die Syntax ist anders. Die keys Methode ubernimmt z. B. ein Dictionary und gibt eine Liste von Schlusseln zuruck, die im Dictionary vorkommen. Aber anstatt der Syntax fur Funktionen keys(ger2eng) verwenden wir die Methoden-Syntax ger2eng.keys().

>>> ger2eng.keys()   
['zwei', 'eins', 'drei']

Diese Form, die sogenannte Punkt Notation gibt den Namen der Funktion, keys, und den Namen des Objekts, auf das die Funktion angewendet wird an, ger2eng. Die runden Klammern zeigen an, dass die Methode keine Parameter ubernimmt.

Wir sagen in diesem Fall: wir rufen die Methode keys fur das Objekt ger2eng auf.

Die values Methode ist ahnlich; sie gibt eine Liste der Werte in dem Dictionary zuruck:

>>> ger2eng.values()   
['two', 'one', 'three']

Die items Methode gibt beide zuruck, und zwar in der Form eine Liste von Tupeln eines fur jedes Schlussel-Wert Paar:

>>> ger2eng.items()   
[('zwei', 'two'), ('eins', 'one'), ('drei', 'three')]

Die Syntax liefert nutzliche Information uber die Typen: Die eckigen Klammern zeigen, dass das eine Liste ist. Die runden Klammern zeigen, dass die Elemente der Liste Tupel sind.

Wenn eine Methode ein Argument ubernimmt, wird dieselbe Syntax wie fur einen Funktionsaufruf verwendet: Zum Beispiel ubernimmt die Methode has_key einen Schlussel als Argument und gibt wahr (1) zuruck, falls der Schlussel im Dictionary vorkommt:

>>> ger2eng.has_key('eins')   
1   
>>> ger2eng.has_key('due')   
0

Versucht man eine Methode ohne das Objekt, zu dem sie gehort, aufzurufen, erhalt man eine Fehlermeldung. In diesem Fall ist die Fehlermeldung nicht sehr hilfreich:

>>> has_key('eins')   
NameError: has_key

### 10.3 Aliasnamen and Kopien

Weil der Datentyp Dictionary veranderbar ist, muss man auf Aliasnamen achten. Immer, wenn zwei Variablen auf dasselbe Objekt verweisen betreffen Änderungen der einen auch die andere.

Wenn man ein Dictionary andern will und eine Kopie des Originals aufbewahren will, muss man die copy - Methode verwenden. Zum Beispiel ist opposites ein Dictionary, das Paare von Gegensatzen enthalt:

>>> opposites = {'up': 'down', 'right': 'wrong', 'true': 'false'}   
>>> alias = opposites   
>>> copy = opposites.copy()

alias und opposites verweisen auf dasselbe Objekt; copy verweist auf eine neue Kopie desselben Dictionary. Wenn man nun alias verandert, wird opposites auch geandert:

>>> alias['right'] = 'left'   
>>> opposites['right']   
'left'

Wenn wir dagegen copy verandern, bleibt opposites ungeandert:

>>> copy['right'] = 'privilege'   
>>> opposites['right']   
'left'

### 10.4 Dunnbesetzte Matrizen 

In [Abschnitt ](), haben wir eine Liste von Listen benutzt, um Matrizen darzustellen. Das ist eine gute Wahl fur Matrizen, bei denen die meisten Elemente ungleich null sind. Betrachten wir nun aber eine Matrix wie die folgende:

Die Listendarstellung enthalt eine Menge Nullen:

matrix = [ [0,0,0,1,0],   
[0,0,0,0,0],   
[0,2,0,0,0],   
[0,0,0,0,0],   
[0,0,0,3,0] ]

Eine Alternative dazu ist eine Darstellung mit einem Dictionary: als Schlussel konnen wir Tupel verwenden, die die Zeilen- und Spaltenindizes enthalten. Hier ist die Dictionary-Darstellung derselben Matrix:

matrix = {(0,3): 1, (2, 1): 2, (4, 3): 3}

Wir brauchen nur drei Schlussel-Wert Paare, eines fur jedes Element der Matrix, das ungleich null ist. Jeder Schlussel ist ein Tupel und jeder Wert ist eine Ganzzahl.

Um auf ein Element der Matrix zuzugreifen, konnten wir den [] Operator verwenden:

matrix[0,3]   
1

Man beachte, dass die Syntax dafur bei der Dictionary-Darstellung anders ist als bei der Listen-Darstellung. Anstatt zweier Ganzzahl-Indizes benutzen wir nun nur einen Index, und der ist ein Tupel von Ganzzahlen.

Wenn wir ein Element angeben wollen, das null ist, erhalten wir eine Fehlermeldung, weil fur den zugehorigen Schlussel kein Eintrag in dem Dictionary vorhanden ist:

>>> matrix[1,3]   
KeyError: (1, 3)

Die get-Methode lost dieses Problem:

>>> matrix.get((0,3), 0)   
1

Das erste Argument ist der Schlussel; das zweite Argument ist der Wert, den get zuruckgeben soll, falls der Schlussel im Dictionary nicht vorkommt:

>>> matrix.get((1,3), 0)   
0

get verbessert definitiv den Elemetzugriff auf dunnbesetzte Matrizen. _Shame about the syntax._

### 10.5 Hinweise

Wer ein bisschen mit der fibonacci - Funktion aus [Abschnitt 5.7](http://python4kids.net/how2think/kap05.htm) herumgespielt hat, wird vielleicht bemerkt haben, dass die Funktion umso mehr Rechenzeit braucht, je großer das Argument ist, das man ihr ubergibt. Außerdem steigt die Laufzeit außerordentlich schnell an. Auf einer unserer Maschinen ist fibonacci(20) praktisch augenblicklich fertig, fibonacci(30) braucht etwa eine Sekunde und fibonacci(40) braucht grob gesprochen ewig.

Um zu verstehen, warum das so ist, betrachte folgendes **Aufruf-Diagramm** fur fibonacci mit n=4:

![](http://python4kids.net/how2think/illustrations/fibonacci.png)

Ein Aufrufdiagram zeigt eine Menge von Funktions-Rahmen, wobei jeder durch Linien mit den Rahmen der Funktionen verbunden ist, die er aufruft. An der Spitze des Diagramms ruft fibonacci mit n=4 fibonacci mit n=3 und n=2 auf. Gleicherweise ruft fibonacci mit n=3 fibonacci mit n=2 und n=1. Und so weiter.

Wenn man abzahlt, wie oft fibonacci(0) und fibonacci(1) aufgerufen wurde, bemerkt man, dass dies eine sehr ineffiziente Losung des Problems ist, und sie wird weit schlimmer, wenn die Argumente noch großer werden.

A good solution is to keep track of values that have already been computed by storing them in a dictionary. A previously computed value that is stored for later use is called a **hint**. Here is an implementation of fibonacci using hints: Eine gute Losung dieses Problems wird sein, sich die Werte zu merken, die bereits berechnet worden sind, etwa, indem man sie in einem Dictionary speichert. Ein fruher berechneter Wert, der fur spateren Gebrauch gespeichert wird, wird ein **Hinweis** genannt. Hier ist eine Implementation von fibonacci mit Verwendung von Hinweisen.

previous = {0:1, 1:1}

def fibonacci(n):   
if previous.has_key(n):   
return previous[n]   
else:   
newValue = fibonacci(n-1) + fibonacci(n-2)   
previous[n] = newValue   
return newValue

Das Dictionary namens previous speichert die Fibonacci-Zahlen, die wir bereits kennen. Wir beginnen mit nur zwei Paaren: Schlussel 0 erhalt den Wert 1; und Schlussel 1 erhalt den Wert 1.

Wann immer fibonacci aufgerufen wird, uberpruft es, ob das Dictionary das Ergebnis schon enthalt. Wenn das der Fall ist, wird es sofort zuruckgegeben, ohne weitere rekursive Aufrufe auszufuhren. Wenn nicht, muss der neue Wert berechnet werden. Er wird dann gleich dem Dictionary hinzugefugt, bevor er von der Funktion zuruckgegeben wird.

Mit dieser Version von fibonacci, konnen unsere Maschinen fibonacci(40) wahrend eines Lidschlags berechnen. Versuchet man aber fibonacci(50) zu berechnen, bekommt man ein anderes Problem:

>>> fibonacci(50)   
OverflowError: integer addition

Das Ergebnis ist, wie man gleich sehen wird, 20,365,011,074. Das Problem besteht darin, dass diese Zahl zu groß ist um in eine Python-Ganzzahl, int, hineinzupassen. Zum Gluck hat dieses Problem eine leichte Losung:

### 10.6 Lange Ganzzahlen

Python stellt einen Datentyp **lange Ganzzahl**, long int, zur Verfugung, der Ganzzahlen beliebiger Lange speichern und manipulieren kann. Es gibt zwei Moglichkeiten, um einen long int Wert zu erzeugen. Eine ist, eine Ganzzahl hinzuschreiben und dahinter gleich ein großes L anzufugen:

>>> type(1L)   
<type 'long int'>

Die andere Moglichkeit ist, die Funktion long zu benutzen, um einen Wert in den Typ long int zu konvertieren. long akzeptiert als Argument jeden numerischen Typ und auch strings, die nur aus Ziffern bestehen.

>>> long(1)   
1L   
>>> long(3.9)   
3L   
>>> long('57')   
57L

Alle Rechenoperationen funktionieren auch mit long ints, daher haben wir nicht viel zu tun, um fibonacci anzupassen:

>>> previous = {0:1L, 1:1L}   
>>> fibonacci(50)   
20365011074L

Indem wir gerade einmal die anfanglichen Inhalte von previous geandert haben, haben wir das ganze Verhalten von fibonacci geandert. Die ersten beiden Zahlen in der Folge sind nun long ints, und damit werden es alle anderen Zahlen in dieser Folge auch.

> _Übung: Ändere factorial so ab, dass es ein das Ergebnis vom Typ long int berechnet._

### 10.7 Buchstaben zahlen

Im [Kapitel 7](http://python4kids.net/how2think/kap07.htm) haben wir eine Funktion geschrieben, die die Anzahl des Auftretens eines Buchstabens in einem String abgezalt hat. Eine allgemeinere Version dieses Problems ist, ein Histogramm von Buchstaben in einem String zu erstellen, d. h. festzusztellen, wie oft jeder Buchstabe vorkommt.

Ein solches Histogramm kann etwa dazu benutzt werden, um eine Textdatei zu komprimieren. Da verschiedene Buchstaben mit verschiedenen Haufigkeiten auftreten, kann man eine Textdatei komprimieren, indem man kurzere Codes fur haufigere Buchstaben einsetzt und langere Codes fur Buchstaben, die weniger haufig vorkommen.

Der Datentyp Dictionary ermoglicht Histogramme auf elegante Weise zu erzeugen:

>>> letterCounts = {}   
>>> for letter in "Mississippi":   
... letterCounts[letter] = letterCounts.get (letter, 0) + 1   
...   
>>> letterCounts   
{'M': 1, 's': 4, 'p': 2, 'i': 4}

Man beginnt mit einem leeren Dictionary. Fur jeden Buchstaben im String finden wir die aktuelle Haufigkeit (eventuell 0) und inkrementieren sie. Am Ende enthalt das Dictionary Paare von Buchstaben und ihren Haufigkeiten.

Es mag ansprechender ausschauen, das Histogramm in alphabetischer Reihenfolge auszugeben. Wir konnen das mit den items und sort Methoden erreichen:

>>> letterItems = letterCounts.items()   
>>> letterItems.sort()   
>>> print letterItems   
[('M', 1), ('i', 4), ('p', 2), ('s', 4)]

Wir haben ja die items Methode schon fruher gesehen, aber sort ist die erste Methode fur Listen, der wir begegnen. Es gibt noch einige andere Methoden fur Listen, darunter append, extend, und reverse. Details kann man der Python-Dokumentation entnehmen.

### 10.8 Glossar

**Dictionary**
    (auch: assoziative Liste.) Eine Sammlung von Schlussel-Wert Paaren, die jedem Schlussel einen Wert zuordnet. Die Schlussel konnen von beliebigem unveranderbarem Typ sein, die Werte konnen von von ganz beliebigem Typ sein.
**dictionary**
    A collection of key-value pairs that maps from keys to values. The keys can be any immutable type, and the values can be any type.

**Schlussel**
    Ein Wert, der benutzt wird um einen Eintrag in einem Dictionary zu ermitteln.
**key**
    A value that is used to look up an entry in a dictionary.

**Schlussel-Wert Paar**
    Ein Eintrag in einem Dictionary.
**key-value pair**
    One of the items in a dictionary.

**Methode**
    Eine Art von Funktion, die mit einer anderen Syntax und _fur_ ein bestimmtes Objekt aufgerufen wird.
**method**
    A kind of function that is called with a different syntax and invoked "on" an object.

**Methode aufrufen**
    Aufruf einer Methode analog einem Funktionsaufruf, jedoch mit Angabe des Objekts, fur das die Methode aufgerufen wird (Punkt-Notation).
**invoke**
    To call a method.

**Hinweis**
    Vorubergehende Speicherung eines im Vorhinein berechneten Wertes um redundante Berechnungen zu vermeiden.
**hint**
    Temporary storage of a precomputed value to avoid redundant computation.

**Overflow**
    Ein numerisches Ergebnis, das zu groß ist, um mit einem bestimmten numerischen Typ dargestellt zu werden.
**overflow**
    A numerical result that is too large to be represented in a numerical format.
  


## Kapitel 11

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [glingl@aon.at](mailto:glingl@aon.at) _

Solange ein Programm lauft, befinden sich seine Daten im Arbeitsspeicher. Wenn das Programm endet oder der Computer heruntergefahren wird, dann verschwinden die Daten aus dem Arbeitsspeicher. Um Daten dauerhaft zu sichern, muss man sie in einer **Datei** abspeichern. Dateien werden ublicherweise auf einer Festplatte, Diskette oder CD-ROM gespeichert.

Wenn man es mit einer großen Zahl von Dateien zu tun hat, sind diese oftmals in sogenannten **Verzeichnissen** (auch "Ordner" genannt) organisiert. Jede Datei wird durch einen eindeutigen Namen oder durch eine Kombination von Dateinamen und Verzeichnisnamen identifiziert.

Programme konnen Information miteinander austauschen, indem sie Dateien lesen und schreiben und druckbare Formate, wie z. B. PDF, erzeugen.

Die Arbeit mit Dateien ist in mancher Hinsicht wie die Arbeit mit Buchern. Um ein Buch zu benutzen, muss man es offnen. Wenn man fertig ist, muss man es wieder schließen. Solange es offen ist, kann man entweder etwas hineinschreiben oder etwas herauslesen. In beiden Fallen weiß man, wo in dem Buch man gerade ist. Meistens liest man die Seiten eines Buchs in ihrer naturlichen Reihenfolge, aber man kann ebenso auch darin herumspringen.

All das trifft auch fur Dateien zu. Um eine Datei zu offnen, gibt man ihren Namen an und ob man darin lesen oder schreiben will.

Indem man eine Datei offnet, erzeugt man ein Datei-Objekt. Im folgenden Beispiel verweist die Variable f auf dieses neue Datei-Objekt.

>>> f = open("test.dat","w")   
>>> print f   
<open file 'test.dat', mode 'w' at fe820>

Der open Funktion werden zwei Argumente ubergeben. Das erste ist der Name der Datei und das zweite der Modus, in dem sie geoffnet wird. Modus "w" (fur write) bedeutet, dass die Datei zum Schreiben geoffnet wird.

Wenn keine Datei des Namens test.dat vorhanden ist, wird sie erzeugt werden. Wenn es sie bereits gibt, wird sie durch die Datei, die gerade erzeugt wird, ersetzt werden.

Wenn wir das Datei-Objekt ausgeben, sehen wir den Namen der Datei, den Modus und den Ort des Objekts.

Um Daten in die Datei zu schreiben, rufen wir die write Methode fur das Dateiobjekt auf:

>>> f.write("Now is the time")   
>>> f.write("to close the file")

Wenn man die Datei schließt, weiß das System, dass jetzt nichts mehr geschrieben wird und es bereitet die Datei furs Lesen vor.

>>> f.close()

Nun kann man die Datei neuerlich offnen, diesmal zum Lesen, und den Inhalt der Datei in einen String einlesen. Dazu muss man das Modus-Argument auf "r" (fur read), also auf Lesen, setzen.

>>> f = open("test.dat","r")

Wenn man versucht eine Datei zum Lesen zu offnen, die es nicht gibt, erhalt man eine Fehlermeldung:

>>> f = open("test.cat","r")   
IOError: [Errno 2] No such file or directory: 'test.cat'

Es ist wohl nicht besonders uberraschend, dass die read Methode Daten aus der Datei liest. Ohne Argument liest sie den ganzen Inhalt der Datei:

>>> text = f.read()   
>>> print text   
Now is the timeto close the file

Es ist da kein Leerzeichen zwischen "time" und "to", weil wir kein Leerzeichen zwischen diese beiden Strings geschrieben haben.

read kann auch ein Argument ubernehmen, das angibt, wieviele Zeichen gelesen werden sollen:

>>> f = open("test.dat","r")   
>>> print f.read(5)   
Now i

Wenn nicht mehr genug Zeichen in der Datei sind, dann gibt read die restlichen Zeichen zuruck. Wenn wir ans Ende der Datei kommen, dann gibt read den Leerstring zuruck:

>>> print f.read(1000006)   
s the timeto close the file   
>>> print f.read()

>>>

Die folgende Funktion kopiert eine Datei, indem sie bis zu funfzig Zeichen aufeinmal liest, bzw. schreibt. Das erste Argument ist der Name der urspunglichen Datei; das zweite ist der der neuen Datei:

def copyFile(oldFile, newFile):   
f1 = open(oldFile, "r")   
f2 = open(newFile, "w")   
while 1:   
text = f1.read(50)   
if text == "":   
break   
f2.write(text)   
f1.close()   
f2.close()   
return

Die break Anweisung ist hier neu. Wenn sie ausgefuhrt wird, springt die Programmausfuhrung aus der Schleife heraus und setzt bei der ersten Anweisung nach der Schleife fort.

In diesem Beispiel ist die while Schleife endlos, weil der Wert 1 immer wahr ist. Der _einzige_ Weg aus der Schleife geht uber die Ausfuhrung der break Anweisung, und diese geschieht, wenn text der Leerstring ist. Das wiederum geschieht, wenn wir am Ende der Datei angelangt sind.

### 11.1 Textdateien

Eine **Textdatei** ist eine Datei, die druckbare Zeichen und nicht sichtbare Zeichen ("whitespace") enthalt, die in einzelnen Zeilen organisiert sind , die durch "newline"-Zeichen voneinander getrennt sind. Da Python speziell in Hinblick auf die Verarbeitung von Textdateien entworfen worden ist, stellt es Methoden zur Verfugung, die diesbezuglicher Aufgaben ganz leicht machen.

Als Demonstration werden wir eine Textdatei mit drei Zeilen Text, getrennt durch "newline"-Zeichen, erzeugen:

>>> f = open("test.dat","w")   
>>> f.write("line one\nline two\nline three\n")   
>>> f.close()

Die readline Methode liest alle Zeichen bis zu und einschließlich dem nachsten "newline"-Zeichen:

>>> f = open("test.dat","r")   
>>> print f.readline()   
line one

>>>

readlines gibt alle verbleibenden Zeilen als eine Liste von Strings zuruck:

>>> print f.readlines()   
['line two\012', 'line three\012']

In diesem Fall ist die Ausgabe im Listen-Format, d. h. die Strings erscheinen mit Anfuhrungszeichen und das "newline" Zeichen erscheint als Escape-Sequenz <br>012.

Am Ende der Datei gibt readline den Leerstring zuruck, bzw. readlines die leere Liste.

>>> print f.readline()

>>> print f.readlines()   
[]

Das Folgende ist ein Beispiel fur ein Programm, das ein Textfile zeilenweise verarbeitet. filterFile erzeugt eine Kopie von oldFile, wobei alle Zeilen, die mit # beginnen, ausgelassen werden:

def filterFile(oldFile, newFile):   
f1 = open(oldFile, "r")   
f2 = open(newFile, "w")   
while 1:   
text = f1.readline()   
if text == "":   
break   
if text[0] == '#':   
continue   
f2.write(text)   
f1.close()   
f2.close()   
return

Die continue Anweisung beendet den aktuellen Schleifendurchlauf, nicht aber die Schleife insgesamt. Die Programmausfuhrung springt an den Anfang der Schleife, pruft die Bedingung und fahrt entsprechend fort.

Wenn nun text gleich dem Leerstring ist, wird die Schleife beendet. Wenn das erste Zeichen von text unser Kanalgitter ist, geht die Programmausfuhrung wieder an den Anfang der Schleife. Nur wenn beide Bedinungen nicht eintreten, wird text in die neue Datei kopiert.

### 11.2 Werte von Variablen schreiben

Das Argument von write muss ein String sein, d. h. wenn wir Werte anderer Typen in eine Datei schreiben wollen, mussen wir diese zuerst in einen String konvertieren. Das geht am einfachsten mit der str Funktion:

>>> x = 52   
>>> f.write (str(x))

Eine Alternative stellt der **Format-Operator** % dar. Wenn man ihn auf Ganzzahlen anwendet, dann ist % der modulus-Operator. Aber wenn der linke Operand ein String ist, dann ist % der Format-Operator.

Der linke Operand ist der **Format-String** und der rechte Operand ist ein Tupel von Ausdrucken. Das Ergebnis ist ein String, der die Werte der Ausdrucke enthalt und zwar formatiert entsprechend dem Format-String.

Ein einfaches Beispiel: die **Format-Sequenz** "%d" bedeutet, dass der erste Ausdruck in dem Tupel als eine Ganzzahl formatiert werden sollte. Hier steht der Buchstabe _d_ fur "dezimal":

>>> cars = 52   
>>> "%d" % cars   
'52'

Das Ergebnis ist der String '52', der nicht mit dem Gazzahlwert 52 verwechselt werden darf.

Eine Format-Sequenz kann uberall in einem Format-String auftreten. Somit konnen wir Werte in Satze einbetten:

>>> cars = 52   
>>> "In July we sold %d cars." % cars   
'In July we sold 52 cars.'

Die Format-Sequenz "%f" formatiert das nachste Element in dem Tupel als eine Gleitkommazahl und "%s" formatiert das nachste Element als einen String:

>>> "In %d days we made %f million %s." % (34,6.1,'dollars')   
'In 34 days we made 6.100000 million dollars.'

In der Voreinstellung druckt das Gleitkomma-Format sechs Dezimalstellen.

Die Anzahl der Ausdrucke in dem Tupel muss mit der Anzahl der Format-Sequenzen in dem String ubereinstimmen. Ebenso mussen die Typen der Ausdrucke mit den Typangaben in den Format-Sequenzen ubereinstimmen:

>>> "%d %d %d" % (1,2)   
TypeError: not enough arguments for format string   
>>> "%d" % 'dollars'   
TypeError: illegal argument type for built-in operation

Im ersten Beispiel sind nicht genug Ausdrucke vorhanden; im zweiten hat der Ausdruck den falschen Typ.

Um das Format von Zahlen besser kontrollieren zu konnen, kann man die Anzahl der Ziffern als Teil der Format-Sequenzen angeben:

>>> "%6d" % 62   
' 62'   
>>> "%12f" % 6.1   
' 6.100000'

Die Zahl nach dem Prozentzeichen ist die Minimalzahl von Stellen, die die Zahl einnehmen wird. Wenn der eingesetzte Wert weniger Ziffern hat, werden links fuhrende Leerzeichen eingefugt. Wenn die Anzahl der Stellen negativ ist, werden rechts abschließende Leerzeichen angefugt:

Fur Gleitkommazahlen konnen wir auch noch die Anzahl der Stellen nach dem Dezimalpunkt angeben:

>>> "%12.2f" % 6.1   
' 6.10'

In diesem Beispiel nimmt das Ergebnis 12 Stellen ein und dies schließt zwei Stellen hinter dem Komma ein. Dieses Format ist z.B. nutzlich fur die Ausgabe mehrerer Dollarbetrage mit stellenwertrichtig untereinander geschriebenen Dezimalpunkten.

Man stelle sich beispielsweise ein Dictionary vor, das die Namen von StudentInnen als Schlussel und Stundenlohne als Werte enthalt. Hier ist eine Funktion, die den Inhalt des Dictionary als formatierte Tabelle ausgibt.

def report (wages) :   
students = wages.keys()   
students.sort()   
for student in students :   
print "%-20s %12.02f" % (student, wages[student])

Um diese Funktion zu testen, werden wir ein kleines Dictionary erzeugen und den Inhalt ausgeben:

>>> wages = {'mary': 6.23, 'joe': 5.45, 'joshua': 4.25}   
>>> report (wages)   
joe 5.45   
joshua 4.25   
mary 6.23

Indem man den Platzbedarf jedes Wertes kontrolliert, kann man garantieren, dass die Spalten zusammenpassen, solange die Namen weniger als 21 Zeichen enthalten und die Lohne geringer sind als eine Milliarde Dollars pro Stunde.

### 11.3 Verzeichnisse

Wenn man eine neue Datei erzeugt, indem man sie offnet und schreibt, dann wird die Datei in das aktuelle Arbeitsverzeichnis geschrieben (in der Regel das Verzeichnis, von dem aus man das Programm gestartet hat). Ebenso ist es wenn man eine Datei zum Lesen offnet: Python sucht sie im aktuellen Arbeitsverzeichnis.

Mochte man eine Datei offnen, die irgendwo anders steht, dann muss man den **Pfad** zu dieser Datei angeben. Das ist der Name des Verzeichnisses (Ordners), wo die Datei ist. Auf einem Unix/Linux - System konnte das etwa so aussehen:

>>> f = open("/usr/share/dict/words","r")   
>>> print f.readline()   
Aarhus

Diese Beispiel offnet eine Datei namens words, die in einem Verzeichnis namens dict liegt, das sich in share befindet, welches sich seinerseits in usr befindet, welches wiederum im Wurzel-Verzeichnis des Systems genannt / zu finden ist.

Naturlich kann man / nicht als Teil eines Dateinamens verwenden; dieses Zeichen ist reserviert fur die Verwendung als Begrenzer zwischen Verzeichnis- bzw. Dateinamen.

Die Datei /usr/share/dict/words enthalt eine Liste von Wortern in alphabetischer Reihenfolge, von denen das erste der Namen einer danischen Universitat ist.

_Amerkung d. Ü._: Fur ein Windows-System mußte der obige Code etwa folgendermaßen modifiziert werden, weil dort der Begrenzer von Verzeichnis- und Dateinamen nicht der slash / sondern der backslash \ ist, der aber bei jedem Auftreten mittels eines weiteren backslash seiner Escape-Zeichen-Eigenschaft beraubt werden muss. daher zweimal \ :

>>> f = open("C:\\\user\\\share\\\dict\\\words","r")   
>>> print f.readline()   
Aarhus

### 11.4 Picklen

Um Werte in eine Datei zu schreiben, muss man sie in Strings verwandeln. Wir haben schon gesehen, wie man das mit str machen kann:

>>> f.write (str(12.3))   
>>> f.write (str([1,2,3]))

Das Problem ist aber dabei, dass man, wenn man die Werte wieder von der Datei einliest, jedenfalls einen String erhalt. Die ursprungliche Typinformation ist verloren gegangen. In der Tat kann man nicht einmal mehr sagen, wo ein Wert endet und der nachste beginnt:

>>> f.readline()   
'12.3[1, 2, 3]'

Die Losung fur dieses Problem ist das **Picklen** (sicherlich keine schlimmere Wortkreation als Downloaden man denke etwa an mixed pickles, wo ja auch verschiedenartigste Objekte zur spateren Verwendung durcheinander eingelegt werden (_Anm. d.Ü._)). Picklen wird so genannt, weil es Datenstrukturen "bewahrt". Der pickle Modul enthalt die notigen Kommandos. Um ihn zu benutzen, importieren wir pickle und offnen dann dei Datei in ublicher Weise:

>>> import pickle   
>>> f = open("test.pck","w")

Um eine Datenstruktur zu speichern, benutzt man die dump Methode und schließt dann die Datei wie ubliche:

>>> pickle.dump(12.3, f)   
>>> pickle.dump([1,2,3], f)   
>>> f.close()

Spater kann man die Datei zum Lesen offnen und die abgelegten Datenstrukturen wieder laden:

>>> f = open("test.pck","r")   
>>> x = pickle.load(f)   
>>> x   
12.3   
>>> type(x)   
<type 'float'>   
>>> y = pickle.load(f)   
>>> y   
[1, 2, 3]   
>>> type(y)   
<type 'list'>

Mit jedem Aufruf von load bekommen wir einen einzelnen Wert aus der Datei, vollstandig, mit seinem ursprunglichen Typ.

### 11.5 Ausnahmen

Wann immer ein Laufzeitfehler auftritt, wird eine **Ausnahme** erzeugt. Normalerweise stoppt dann das Programm und Python gibt eine Fehlermeldung aus.

Beispielsweise erzeugt die Division durch null eine Ausnahme:

>>> print 55/0   
ZeroDivisionError: integer division or modulo

Ebenso der Zugriff auf ein nicht existierendes Listenelement:

>>> a = []   
>>> print a[5]   
IndexError: list index out of range

Oder der Zugriff auf einen Schlussel, der in einem Dictionary nicht vorkommt:

>>> b = {}   
>>> print b['what']   
KeyError: what

In jedem Fall besteht die Fehlermeldung aus zwei Teilen: Der Typ des Fehlers steht vor dem Doppelpunkt Detailangaben uber den Fehler nach dem Doppelpunkt. Normalerweise gibt Python auch eine Beschreibung des Aufrufstacks an der Stelle wo das Programm war, als der Fehler auftrat, aus. Diesen Teil haben wir bei den folgenden Beispielen weggelassen.

Manchmal will man eine Operation ausfuhren, die eventuell eine Ausnahme, also einen Laufzeitfehler, versursachen kann, aber trotzdem verhindern, dass in diesem Fall das Programm abbricht. Man kann diese **Ausnahme behandeln**, indem man die try und except - Anweisungen verwendet.

Als Beispiel mochten wir den Benutzer um einen Dateinamen fragen und dann versuchen, die entsprechende Datei zu offnen. Wenn es die Datei nicht gibt, dann soll das Programm nicht abbrechen, sondern wir mochten diese Ausnahme abfangen:

filename = raw_input('Enter a file name: ')   
try:   
f = open (filename, "r")   
except:   
print 'There is no file named', filename

Die try Anweisung fuhrt die Anweisungen im ersten Block aus. Wenn keine Ausnahme auftritt, wird die except Anweisung ignoriert. Wenn doch eine Ausnahme auftritt, werden die Anweisungen im except Zweig und im Anschluß daran das Programm weiter ausgefuhrt.

Wir konnen diese Funktionalitat in einer Funktion kapseln: Der Funktion exists wird ein Dateinamen als Argument ubergeben und sie gibt wahr zuruck, falls die Datei existiert und falsch andernfalls:

def exists(filename):   
try:   
f = open(filename)   
f.close()   
return 1   
except:   
return 0

Man kann sogar mehrfache except Blocke verwenden, um verschiedene Arten von Ausnahmen zu behandeln. Im _Python Reference Manual_ stehen die Details.

Wenn ein Programm eine Fehlerbedingung erkennt, kann man mit der raise Anweisung erzwingen, dass eine **Ausnahme erzeugt** wird. Hier ist ein Beispiel, das eine Benutzereingabe einliest und feststellt, dass der Wert gleich 17 ist. Wir nehmen an, aus irgendwelchen Grunden ware 17 keine gultige Eingabe, daher erzeugen wir eine Ausnahme:

def inputNumber () :   
x = input ('Pick a number: ')   
if x == 17 :   
raise 'BadNumberError', '17 is a bad number'   
return x

Die raise Anweisung ubernimmt zwei Argumente: den Ausnahmetyp und eine spezifische Information uber den Fehler. BadNumberError ist eine neue Art von Ausnahme, die wir gerade fur diese Anwendung erfunden haben.

Wenn die Funktion, die inputNumber aufgerufen hat, den Fehler behandelt, dann kann das Programm weiter ausgefuhrt werden; anderfalls gibt Python eine Fehlermeldung aus und bricht die Programmausfuhrung ab:

>>> inputNumber ()   
Pick a number: 17   
BadNumberError: 17 is a bad number

Die Fehlermeldung enthalt den Ausnahmetyp und die Zusatzinformation, die man bereitgestellt hat.

> _Übung: schreibe eine Funktion, die inputNumber benutzt, um eine Zahl uber die Tastatur einzulesen und die den BadNumberError in geeigneter Weise abfangt._

### 11.6 Glossar

**Datei**
    Ein mit Namen versehenes Objekt, ublicherweise auf einer Festplatte, einer Diskette oder einer CD_ROM gespeichert, das einen Strom (eine Folge) von Zeichen enthalt.
**file**
    A named entity, usually stored on a hard drive, floppy disk, or CD-ROM, that contains a stream of characters.

**Verzeichnis**
    Eine mit Namen versehene Kollektion von Dateien, auch Ordner genannt.
**directory**
    A named collection of files, also called a folder.

**Pfad**
    Eine Folge von Verzeichnisnamen, die den exakten Speicherort einer Datei angeben.
**path**
    A sequence of directory names that specifies the exact location of a file.

**Textdatei**
    Eine Datei, die druckbare Zeichen, in Zeilen angeordnet, enthalt. Die Zeilen werden durch "newline"-Zeichen voneinander getrennt.
**text file**
    A file that contains printable characters organized into lines separated by newline characters.

**break Anweisung**
    Eine Anweisung, die bewirkt, dass die Programmausfuhrung eine Schleife verlaßt.
**break statement**
    A statement that causes the flow of execution to exit a loop.

**continue Anweisung**
    Eine Anweisung, die die aktuelle Ausfuhrung eines Schleifendurchganges beendet. Die Programmausfuhrung springt zum Schleifenkopf, wertet die Bedingung aus und fahrt entsprechend fort.
**continue statement**
    A statement that causes the current iteration of a loop to end. The flow of execution goes to the top of the loop, evaluates the condition, and proceeds accordingly.

**Format-Operator**
    Der % Operator. Der linke Operand ist ein Format-String, der rechte ein Tupel von Ausdrucken. Das Ergebnis der Operation ist ein String, der die Ausdrucke so formatiert enthalt, wie es der Format-String angibt.
**format operator**
    The % operator takes a format string and a tuple of expressions and yields a string that includes the expressions, formatted according to the format string.

**Format-String**
    Ein String, der druckbare Zeichen und Format-Sequenzen enthalt, die anzeigen, wie bestimmte Werte formatiert werden sollen.
**format string**
    A string that contains printable characters and format sequences that indicate how to format values.

**Format-Sequenz**
    Eine Folge von Zeichen, die mit % beginnt und angibt, wie ein Wert formatiert werden soll .
**format sequence**
    A sequence of characters beginning with % that indicates how to format a value.

**pickle**
    Einen Datenwert in eine Datei schreiben, zusammen mit seinen Typ-Informationen, sodass er spater rekonstruiert werden kann.
**pickle**
    To write a data value in a file along with its type information so that it can be reconstituted later.

**Ausnahme**
    Ein Fehler, der wahrend der Laufzeit auftritt.
**exception**
    An error that occurs at runtime.

**Fehlerbehandlung**
    Verhindern, dass wegen einer Ausnahme die Programmausfuhrung endet. Geschieht mit den try bzw. except Anweisungen.
**handle**
    To prevent an exception from terminating a program using the try and except statements.

**raise**
    Eine Ausnahme mit Hilfe der raise Anweisung erzeugen.
**raise**
    To signal an exception using the raise statement.
  


## Kapitel 12

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [glingl@aon.at](mailto:glingl@aon.at) _

### 12.1 Benutzerdefinierte zusammengesetzte Datentypen

Nachdem wir einige von Pythons eingebauten Datentypen benutzt haben, sind wir nun bereit einen benutzerdefinierten Datentyp zu erzeugen: den Punkt.

Betrachten wir zunachst den Begriff dess mathematischen Punktes. In zwei Dimensionen ist ein Punkt ein Paar von zwei Zahlen (Koordinaten) die zusammen als ein einziges Objekt behandelt werden. In der mathematischen Notation werden Punkte oft als Zahlenpaare in runden Klammern geschrieben, mit einem Komma zwischen den Koordinaten. Zum Beispiel stellt das Paar (0, 0) den Ursprung dar, und das Paar (x, y) stellt den Punkt mit x Einheiten nach rechts und y Einheiten nach oben, vom Ursprung aus gesehen, dar.

Eine naturliche Art einen Punkt in Python darzustellen ist mit zwei Gleitkommazahlen. Dabei erhebt sich die Frage, wie wir diese beiden zu einem zusammengesetzten Objekt zusammenfassen konnen. Eine rasche und einfallslose (quick and dirty) Losung ist es, eine Liste oder ein Tupel zu verwenden, und fur manche Anwendungen mag dies die beste Losung sein.

Eine Alternative dazu ist, einen neuen benutzerdefinierten zusammengesetzten Datentyp zu definieren, eine sogenannte **Klasse**. Dieser Zugang erfordert etwas mehr Muhe, bringt aber Vorteile, die bald zu sehen sein werden.

Eine Klassendefinition sieht so aus:

class Punkt:   
pass

Klassendefinitionen konnen in einem Programm an beliebiger Stelle auftreten, sie werden aber ublicherweise an den Anfang gestellt (hinter die import Anweisungen). Die Syntax-Regeln fur die Klassendefinition sind die selben wie fur andere zusammengesetzte Anweisungen (siehe [Abschnitt 4.4](http://python4kids.net/how2think/kap04.htm)).

Diese Definition erzeugt eine neue Klasse, genannt Punkt. Die **pass** Anweisung hat keine Wirkung; sie ist nur notwendig, weil eine zusammengesetzte Anweisung irgendwas in ihrem Korper stehen haben muss.

Indem wir die Point Klasse erzeugt haben, haben wir auch einen neuen Typ, Point genannt, erzeugt. Die Dinge, die diesen Typ haben, nennt man **Instanzen** dieses Typs oder **Objekte**. Das Erzeugen einer neuen Instanz - also eines Objekts dieses Typs - nennt man **Instanziierung**. Um ein Punkt Objekt zu instanziieren, rufen wir eine Funktion namens (du hast es vielleicht schon erraten) Punkt auf:

blank = Punkt()

Der Variablen blank wird ein Verweis auf ein neues Punkt Objekt zugewiesen. Eine Funktion wie Punkt, die ein neues Objekt erzeugt, nennt man **Konstruktor**.

### 12.2 Attribute

Wir konnen zu einer Instanz neue Daten hinzufugen, indem wir die Punkt-Notation anwenden:

>>> blank.x = 3.0   
>>> blank.y = 4.0

Diese Syntax ist ahnlich der, mit der man eine Variable aus einem Modul anspricht, wie z. B. math.pi oder string.uppercase. Im Gegensatz dazu wird hier aber ein Datenelement einer Instanz angesprochen. Solche benannten Datenelemente heißen **Attribute**.

Das folgende Zustandsdiagramm zeigt das Ergebnis dieser Zuweisungen:

Die Variable blank verweist auf ein Punkt Objekt, das zwei Attribute aufweist. Jedes Attribut verweist auf eine Gleitkommazahl.

Wir konne den Wert eines Attributes auch auslesen, indem wir die gleiche Syntax anwenden:

>>> print blank.y   
4.0   
>>> x = blank.x   
>>> print x   
3.0

Der Ausdruck blank.x bedeutet, "Gehe zum Objekt, auf das blank verweist und ermittle den Wert vvon x." In unserem Beispiel weisen wie diesen Wert einer Variablen namens x zu. Es gibt hier keinen Konflikt zwischen der Variablen x und dem Attribut x. Der Zweck der Punkt-Notation ist es, unzweideutig festzulegen, welche Variable gemeint ist.

Man kann die Punkt-Notation in jedem beliebigen Ausdruck verwenden. So sind beispielsweise auch die folgenden Anweisungen legal:

print '(' + str(blank.x) + ', ' + str(blank.y) + ')'   
distanceSquared = blank.x * blank.x + blank.y * blank.y

Die erste Zeile gibt (3.0, 4.0) aus; die zweite Zeile berechnet den Wert 25.0.

Du wirst vielleicht versucht sein, den Wert von blank selbst auszudrucken:

>>> print blank   
<__main__.Point instance at 80f8e70>

Das Ergebnis zeigt an, dass blank eine Instanz der Punkt Klasse ist und dass sie in __main__ definiert wurde. 80f8e70 ist die eindeutige Identitatsnummer dieses Objekts, geschrieben in Hexadezimaldarstellung. Das ist moglicherweise nicht die informativste Art, ein Punkt Objekt zu beschreiben. Wie man das andern kann, wirst du aber in Kurze sehen.

> _Übung: Erzeuge ein Punkt Objekt, und gib es mit der print Anweisung aus. Dann benutze id um die eindeutige Identitatsnummer dieses Objekts auszugeben. Übersetze die Hexadezimalform in die Dezimalform und uberzeuge dich, dass sie ubereinstimmen._

### 12.3 Instanzen als Parameter

Man kann eine Instanz auf die ubliche Weise als Parameter ubergeben. Zum Beispiel:

def printPoint(p):   
print '(' + str(p.x) + ', ' + str(p.y) + ')'

printPoint ubernimmt einen Punkt als Argument und stellt ihn im Standardformat dar. Wenn man printPoint(blank) aufruft, ist die Ausgabe (3.0, 4.0).

> _Übung: Schreibe die distance Funktion aus dem Abschnitt [ 5.2](http://python4kids.net/how2think/kap05.htm) um, so dass sie zwei Points als Parameter ubernimmt anstatt vier Zahlen._

### 12.4 Gleichheit

Die Bedeutung des Wortes "gleich" scheint absolut klar zu sein, aber nur so lang, bis man beginnt ein wenig daruber nachzudenken. Dann bemerkt man, dass mehr dahinter steckt, als man erwartet hatte.

Wenn du zum Beispiel sagst "Chris und ich haben das gleiche Auto", meinst du dass seines und deines Autos der gleichen Marke sind und auch das gleiche Modell, dass sie aber zwei verschiedene Autos sind. Sagst du hingegen "Chris und ich haben die gleiche Mutter", meinst du, dass seine Mutter und deine die gleiche Person sind. [* Note](javascript:fn\('Not all
languages have the same problem.  For example, German has different
words for different kinds of sameness.). Also ist die Bedeutung von "Gleichheit" verschieden, je nach Kontext.

Wenn man uber Objekte spricht, gibt es eine ahnliche Zweideutigkeit. Zum Beispiel, wenn zwei Points gleich sind, heisst das dass sie dieselben Daten (Koordinaten) haben? Oder sind sie in der Tat das gleiche Objekt?

Um heraus zu finden, ob zwei Verweise auf dasselbe Objekt verweisen, benutze den == Operator. Zum Beispiel:

>>> p1 = Point()   
>>> p1.x = 3   
>>> p1.y = 4   
>>> p2 = Point()   
>>> p2.x = 3   
>>> p2.y = 4   
>>> p1 == p2   
0

Obwohl p1 und p2 die gleichen Koordinaten haben, sind sie nicht das gleiche Objekt. Wenn wir dagegen p1 zu p2 zuweisen, dann sind die beiden Variablen Aliasnamen des gleichen Objekts:

>>> p2 = p1   
>>> p1 == p2   
1

Dieser Typ von Gleichheit wird **flache Gleichheit** (**shallow equality**) genannt, weil hier nur die Verweise, nicht die Inhalte der Objekte verglichen werden.

Um den Inhalt der beiden Objekte zu vergleichen **tiefe Gleichheit** (**deep equality**) konnen wir eine Funktion mit dem Namen samePoint schreiben:

def samePoint(p1, p2) :   
return (p1.x == p2.x) and (p1.y == p2.y)

Wenn wir nun zwei verschiedene Objekte erzeugen, die die gleichen Daten enthalten, konnen wir samePoint benutzen, um heraus zu finden, ob sie den gleichen Punkt darstellen:

>>> p1 = Point()   
>>> p1.x = 3   
>>> p1.y = 4   
>>> p2 = Point()   
>>> p2.x = 3   
>>> p2.y = 4   
>>> samePoint(p1, p2)   
1

Wenn die beiden Variablen auf dasselbe Objekt verweisen, gelten fur sie sowohl flache wie auch tiefe Gleichheit.

### 12.5 Rechtecke

Angenommen wir wollen eine Klasse programmieren um Rechtecke darzustellen. Die Frage ist nun, welche Informationen mussen wir bereitstellen, um ein Rechteck festzulegen? Um die Sache einfach zu halten, nehmen wir an, dass die Rechteckseiten alle vertikal oder horizontal orientiert sind, nicht unter einem Winkel (zu den Koordinatenachsen).

Es gibt hier ein paar Moglichkeiten: wir konnten den Mittelpunkt des Rechtecks (zwei Koordinaten) und seine Große (Breite und Hohe) festlegen; oder wir konnten eine Ecke und die Große festlegen; oder wir konnten zwei gegenuberliegende Ecken festlegen. Ein haufige Wahl ist die Festlegung der linken oberen Ecke und der Große des Rechtecks.

Wir definieren also wieder eine neue Klasse:

class Rectangle:   
pass

Und instanziieren sie:

box = Rectangle()   
box.width = 100.0   
box.height = 200.0

Dieser Code erzeugt ein neues Rectangle Objekt mit zwei Gleitkommazahlen als Attributen. Um die obere linke Ecke festzulegen, konnen wir ein Objekt in ein anderes Objekt einbetten!

box.corner = Point()   
box.corner.x = 0.0;   
box.corner.y = 0.0;

Der Punkt-Operator verbindet. Der Ausdruck box.corner.x bedeutet, "Gehe zu dem Objekt, auf das box verweist und wahle das corner genannte Attribut; dann gehe zu diesem Objekt und wahle das x genannte Attribut."

Das folgende Diagramm zeigt den Zustand dieses Objekts:

### 12.6 Instanzen und Ruckgabewerte

Funktionen konnen Instanzen zuruck geben. Zum Beispiel ubernimmt findCenter ein Rectangle als Argument und gibt einen Point, der die Koordinaten des Mittelpunkts des Rectangle hat, zuruck:

def findCenter(box):   
p = Point()   
p.x = box.corner.x + box.width/2.0   
p.y = box.corner.y + box.height/2.0   
return p

Wir rufen diese Funktion auf, wobei wir box als ein Argument ubergeben und das Ergebnis einer Variablen zuweisen:

>>> center = findCenter(box)   
>>> printPoint(center)   
(50.0, 100.0)

### 12.7 Objekte sind veranderbar

Wir konnen den Zustand eines Objekts andern, indem wir einem seiner Attribute etwas zuweisen. Um beispielsweise die Große eines Rechtecks zu andern ohne seine Position zu verandern, konnen wir die Werte von width und height andern:

box.width = box.width + 50   
box.height = box.height + 100

Wir konnen diesen Code in einer Funktion kapseln und so verallgemeinern, um die Große des Rechtecks um beliebig Werte abzuandern.

def growRect(box, dwidth, dheight) :   
box.width = box.width + dwidth   
box.height = box.height + dheight

Die Variablen dwidth und dheight geben an, wie viel die Rechteckgroße in jeder Richtung geandert werden soll. Ein Aufruf dieser Funktion (Methode) hat die Auswirkung, dass das Rechteck Objekt Rectangle geandert wird, das als Argument ubergeben wurde.

Als Beispiel konnen wir ein neues Rectangle genannt bob erzeugen und an growRect ubergeben:

>>> bob = Rectangle()   
>>> bob.width = 100.0   
>>> bob.height = 200.0   
>>> bob.corner = Point()   
>>> bob.corner.x = 0.0;   
>>> bob.corner.y = 0.0;   
>>> growRect(bob, 50, 100)

Wahrend der Ausfuhrung von growRect ist der Parameter box ein Aliasname fur bob. Jede Veranderung von box beeinflusst auch bob.

> _Übung: Schreibe eine Funktion namens moveRect, die ein Rechteck Rectangle als Argument ubernimmt und noch zwei weitere Parameter namens dx und dy besitzt. Sie soll die Position des Rechtecks verandern, indem sie dx zu der x Koordinate der Ecke corner addiert und ebenso dy zu der y Koordinate von corner._

### 12.8 Kopieren

Die Verwendung von Aliasnamen kann dazu fuhren, dass ein Programm schwer zu lesen ist, weil sich Änderungen, die an einer Stelle vorgenommen wurden unerwartete Effekte an anderen Stellen haben konnen. Es ist schwierig all die Variablen im Auge zu behalten, die auf ein gegebenes Objekt verweisen konnten.

Kopieren, oder Klonen, eines Objekts ist oft eine Alternative zur Verwendung von verschiedenen Namen fur ein Objekt. Das copy Modul enthalt eine Funktion namens copy, die von einem beliebigen Objekt eine Kopie herstellen kann:

>>> import copy   
>>> p1 = Point()   
>>> p1.x = 3   
>>> p1.y = 4   
>>> p2 = copy.copy(p1)   
>>> p1 == p2   
0   
>>> samePoint(p1, p2)   
1

Haben wir einmal das copy Modul importiert, konnen wir die copy Funktion verwenden um einen neuen Point zu erzeugen. p1 und p2 sind nicht der gleiche Punkt, aber sie enthalten die gleichen Daten.

Um ein einfaches Objekt zu kopieren, wie z. B. Point, das keine eingebetteten Objekte enthalt, ist copy ausreichend. Dies nennt man **flaches Kopieren**.

Fur Dinge wie ein Rectangle hingegen, das einen Verweis zu einem Point enthalt, tut copy leider nicht ganz das Richtige: Es kopiert den Verweis auf das Point Objekt, sodass beide, das alte Rectangle wie auch das neueauf den selben einzelnen Point verweisen.

Wenn wir auf die ubliche Weise ein Rechteck b1erzeugen und dann eine Kopie b2 erzeugen, indem wir copy benutzen, sieht das daraus resultierende Zustandsdiagramm so aus:

Das ist ziemlich sicher nicht das, was wir wollen. Denn rufen wir in dieser Situation growRect fur eines der beiden Rectangles auf, wird das andere dadurch nicht beeinflusst. Aber ein Aufruf von moveRect fur eines von beiden wurde beide betreffen. Dieses Verhalten ist verwirrend und fuhrt zu Fehleranfalligkeit.

Glucklicherweise enthalt das copy Modul auch noch eine Funktion namens deepcopy, die nicht nur das Objekt selbst, sondern auch jedes darin eingebettete Objekt kopiert. Es wird dich kaum uberraschen, dass diese Operation **tiefes Kopieren** heißt.

>>> b2 = copy.deepcopy(b1)

Nun sind b1 und b2 vollstandig verschiedene Objekte.

Wir konnen deepcopy verwenden, um growRect so umzuschreiben, dass sie, anstatt ein gegebenes Rechteck Rectangle zu verandern, ein neues Rectangle erzeugt, das die gleiche Position wie das alte hat, aber neue Abmessungen:

def growRect(box, dwidth, dheight) :   
import copy   
newBox = copy.deepcopy(box)   
newBox.width = newBox.width + dwidth   
newBox.height = newBox.height + dheight   
return newBox

> _Übung: schreibe die Funktion moveRect so um, dass sie ein neues Rectangle erzeugt und zuruckgibt, anstatt das alte zu verandern._

### 12.9 Glossar

**Klasse**
    Ein benutzerdefinierter zusammengesetzter Typ. Eine Klasse kann auch als Muster fur die Objekte betrachtet werden, die Instanzen von ihr sind.
**class**
    A user-defined compound type. A class can also be thought of as a template for the objects that are instances of it.

**instanziieren**
    Eine Instanz einer Klasse erzeugen.
**instantiate**
    To create an instance of a class.

**Instanz**
    Ein Objekt, das zu einer Klasse gehort.
**instance**
    An object that belongs to a class.

**Objekt**
    Ein zusammengesetzter Datentyp der oft dazu benutzt wird, ein Ding oder einen Begriff der realen Welt zu modellieren.
**object**
    A compound data type that is often used to model a thing or concept in the real world.

**Konstruktor**
    Eine Methode, die benutzt wird um neue Objekte zu erzeugen.
**constructor**
    A method used to create new objects.

**Attribut**
    Eines der benannten Datenelemente, die zusammen eine Instanz bilden.
**attribute**
    One of the named data items that makes up an instance.

**flache Gleichheit**
    Gleichheit von Verweisen, d. h. zwei Verweise, die auf das gleiche Objekt verweisen.
**shallow equality**
    Equality of references, or two references that point to the same object.

**tiefe Gleichheit**
    Gleichheit von Werten. Zwei Verweise, die auf Objekte verweisen, die den gleichen Wert haben.
**deep equality**
    Equality of values, or two references that point to objects that have the same value.

**flaches Kopieren**
    Kopieren des Inhalts eines Objekts, einschließlich aller Referenzen zu eingebetteten Objekten; durch die copy Funktion des copy Moduls implementiert.
**shallow copy**
    To copy the contents of an object, including any references to embedded objects; implemented by the copy function in the copy module.

**tiefes Kopieren**
    Kopieren des Inhalts eines Objekts sowie auch aller eingebetteter Objekte, in diese eingebetteter Objekte usw.; durch die deepcopy Funktion des copy Moduls implementiert.
**deep copy**
    To copy the contents of an object as well as any embedded objects, and any objects embedded in them, and so on; implemented by the deepcopy function in the copy module.
  


## Kapitel 13

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [glingl@aon.at](mailto:glingl@aon.at) _

### 13.1 Zeit

Als ein weiteres Beispiel eines benutzerdefinierten Datentyps werden wir eine Klasse Time definieren, die eine Tageszeit Angabe speichern kann. Die Klassendefinition sieht so aus:

class Time:   
pass

Nun konnen wir ein neues Time Objekt erzeugen und Attribute fur Stunden, Minuten und Sekunden hinzufugen:

time = Time()   
time.hours = 11   
time.minutes = 59   
time.seconds = 30

Das Zustandsdiagramm, fur das Time Objekt sieht so aus:

> _Übung: Schreibe eine Funktion printTime, die ein Time Objekt als Argument ubernimmt und die Zeit in der Form hours:minutes:seconds ausruckt._

> _(Noch eine) Übung: Schreibe eine bool'sche Funtion after, die zwei Time Objekte, t1 und t2, als Argumente ubernimmt und die True zuruckgibt, wenn t1 chronologisch auf t2 folgt. Andernfalls gibt sie False zuruck._

### 13.2 Reine Funktionen

In den nachsten Abschnitten werden wir zwei Versionen einer Funktion schreiben, die wir addTime nennen und die die Summe von zwei Zeiten, Time-Werten, berechnet. Diese beiden Versionen sollen als Beispiele fur zwei Arten von Funktionen dienen: reine Funktionen einerseits und modifizierende Funktionen andererseits.

Folgendes ist eine Rohfassung von addTime:

def addTime(t1, t2):   
sum = Time()   
sum.hours = t1.hours + t2.hours   
sum.minutes = t1.minutes + t2.minutes   
sum.seconds = t1.seconds + t2.seconds   
return sum

Diese Funktion erzeugt ein neues Time Objekt, initialisiert seine Attribute und gibt einen Verweis auf dieses neue Objekt zuruck. So etwas nennt man eine **reine Funktion**, weil sie keines der Objekte, die ihr als Argumente ubergeben werden verandert und weil sie keine Seiteneffekte, wie z. B. Ausgabe eines Wertes mit der print-Anweisung oder Einlesen einer Benutzereingabe hat.

Hier ein Beispiel, wie man diese Funktion benutzen kann: Wir erzeugen zwei Time Objekte: currentTime, welches die momentane Zeit enthalt und breadTime, welches jenes Zeitmaß enthalt, das ein Backer braucht, um Brot zu backen. Dann benutzen wir addTime um heraus zu finden, wann das Brot fertig sein wird. Wenn du noch nicht fertig bist mit dem Programmieren von printTime, sieh einmal weiter unten nach im Abschnitt_14.[2 ](), befor du folgendes versuchst:

>>> currentTime = Time()   
>>> currentTime.hours = 9   
>>> currentTime.minutes = 14   
>>> currentTime.seconds = 30

>>> breadTime = Time()   
>>> breadTime.hours = 3   
>>> breadTime.minutes = 35   
>>> breadTime.seconds = 0

>>> doneTime = addTime(currentTime, breadTime)   
>>> printTime(doneTime)

Die Ausgabe dieses Programms ist 12:49:30, und das ist korrekt. Andererseits gibt es aber Falle, bei denen das Ergebnis nicht korrekt ist. Fallt dir ein solcher Fall ein?

Das Problem ruhrt daher, dass diese Funktion nicht solche Falle berucksichtigt, wo die Anzahl der Sekunden (oder der Minuten) sich auf uber sechzig zusammen addiert. Wenn dies geschieht, haben wir 6o Extra-Sekunden, die wir auf die Minuten "ubertragen" mussen, oder (analog) 60 Extra-Minuten auf die Stunden .

Hier ein zweite korrigierte Fassung der Funktion:

def addTime(t1, t2):   
sum = Time()   
sum.hours = t1.hours + t2.hours   
sum.minutes = t1.minutes + t2.minutes   
sum.seconds = t1.seconds + t2.seconds

if sum.seconds >= 60:   
sum.seconds = sum.seconds - 60   
sum.minutes = sum.minutes + 1

if sum.minutes >= 60:   
sum.minutes = sum.minutes - 60   
sum.hours = sum.hours + 1

return sum

Diese Funktion ist zwar korrekt, der Funktionskorper wird aber schon ziemlich lang. Spater werden wir zu einer alternativen Losung raten, der einen kurzeren Code liefert.

### 13.3 Modifizierende Funktionen

Manchmal ist es nutzlich, wenn eine Funktion ein oder mehrere der Objekte verandert, die sie als Argumente ubergeben kriegt. Normalerweise behalt ja die aufrufende Funktion Verweise auf diese Objekte, sodass jede Veranderung dieser Objekte in der aufrufenden Funktion sichtbar sind. Funktionen, die auf diese Weise arbeiten, nennen wir **modifizierende Funktionen**.

Eine Funktion increment, die zu einem Time-Objekt eine gegebene Anzahl von Sekunden addiert, kann in naturlicher Weise als eine modifizierende Funktion geschrieben werden. Ein grober Entwurf dieser Funktion sieht so aus:

def increment(time, seconds):   
time.seconds = time.seconds + seconds

if time.seconds >= 60:   
time.seconds = time.seconds - 60   
time.minutes = time.minutes + 1

if time.minutes >= 60:   
time.minutes = time.minutes - 60   
time.hours = time.hours + 1

Die erste Zeile fuhrt die grundlegende Rechenoperation aus, der Rest sorgt fur die Behandlung der Spezialfalle, wie wir schon oben gesehen haben.

Ist diese Funktion korrekt? Was geschieht, wenn der Parameter secs viel großer als sechzig ist? In diesem Fall reicht ein Übertrag von 1 nicht, sondern wir mussen so oft 60 Sekunden als eine Minute ubertragen, bis seconds kleiner als sechzig ist. Eine Losung dafur ist, die if Anweisungen durch while Anweisungen zu ersetzen:

def increment(time, secs):   
time.seconds = time.seconds + secs

while time.seconds >= 60:   
time.seconds = time.seconds - 60   
time.minutes = time.minutes + 1

while time.minutes >= 60:   
time.minutes = time.minutes - 60   
time.hours = time.hours + 1

Diese Funktion ist nun korrekt, aber es ist nicht die effizienteste Losung.

> _Übung: Schreibe diese Funktion neu, so dass sie keine Schleifen mehr enthalt._

> _(Noch eine) Übung: Schreibe increment als reine Funktion, und schreibe dann auch Funktionsaufrufe fur beide Fassungen._

### 13.4 Welche Fassung ist besser?

Alles, was mit modifizierenden Funktionen gemacht werden kann, kann auch mit reinen Funktionen gemacht werden. In der Tat gibt es sogar einige Programmiersprachen, die nur reine Funktionen gestatten. Einiges spricht dafur, dass Programme, die nur reine Funktionen verwenden, schneller entwickelt werden konnen und weniger fehleranfallig sind, als Programme, die modifizierende Funktionen verwenden. Nichtsdestoweniger sind modifizierende Funktionen manchmal sehr praktisch. Auch sind in manchen Fallen funktionale Programme weniger effizient.

Wir empfehlen im allgemeinen, reine Funktione zu schreiben, wann immer es vernunftig erscheint. Zu modifizierenden Funktionen sollte man nur greifen, wenn es einen uberzeugenden Vorteil bringt. Diesen Zugang konnte man auch einen **funktionalen Programmierstil** nennen.

### 13.5 Prototyp Entwicklung oder Planung

In diesem Kapitel haben wir einen Zugang zur Programmentwicklung vorgefuhrt, den man **Prototyp Entwicklung** nennt. Wir haben in jedem Fall einen rohen Entwurf (oder Prototyp) erstellt, der die grundlegenden Berechnungen ausgefuhrt hat und ihn dann mit einigen speziellen Daten getestet. Dabei haben wir Schwachen und Fehler gefunden und korrigiert.

Dieser Zugang ist zwar effektiv, er kann aber zu Code fuhren, der unnotig kompliziert ist -- weil er viele Spezialfallen behandelt -- und unzuverlassig ist -- weil es schwer moglich ist, zu beurteilen ob man alle Fehler gefunden hat.

Eine Alternative dazu ist **geplante Entwicklung**. Fur sie muss man sich zunachst ein weitgehendes Verstandnis des Problems erarbeiten. Dafur wird dann das Programmieren viel leichter. In unserem Beispiel besteht dieses Verstandnis z. B. in der Einsicht, dass ein Time Objekt in Wirklichkeit eine dreistellige Zahl im Stellenwertsystem mit der Basis 60 ist. second, die Sekunden-Komponente ist die "Einer-Stelle", minute, die Minuten-Komponente ist die "Sechziger-Stelle" und hour, die Stunden-Komponente, ist die "Dreitausendsechshunderter-Stelle".

Wie wir addTime und increment geschreiben haben, haben wir in der Tat Additionen mit der Basis 60 ausgefuhrt, weshalb wir diese Übertrage von einer zur nachsten Stelle gebraucht haben.

Diese Beobachtung legt einen anderen Zugang zu dem ganzen Problem nahe wir konnen ein Time Objekt in eine einzige Zahl umwandeln und einen Vorteil aus dem Umstand ziehen, dass der Computer ja weiß, wie man mit Zahlen rechnet. Die folgende Funktion wandelt ein Time-Objekt in eine ganze Zahl um:

def convertToSeconds(t):   
minutes = t.hours * 60 + t.minutes   
seconds = minutes * 60 + t.seconds   
return seconds

Jetzt brauchen wir nur noch die Moglichkeit, eine ganze Zahl in ein Time Objekt umzuwandeln:

def makeTime(secs):   
time = Time()   
time.hours = secs/3600   
secs = secs - time.hours * 3600   
time.minutes = secs/60   
secs = secs - time.minutes * 60   
time.seconds = secs   
return time

Wahrscheinlich musst du ein wenig nachdenken, um dich davon zu uberzeugen, dass diese Technik der Umwandlung von einer Basis in eine andere Basis korrekt ist. Nehmen wir aber einmal an, du bis davon uberzeugt, dann kannst du nun diese Funktion dazu benutzen, um auch noch die addTime umzuschreiben:

def addTime(t1, t2):   
seconds = convertToSeconds(t1) + convertToSeconds(t2)   
return makeTime(seconds)

Diese Version ist viel kurzer als die ursprungliche, und es ist auch viel leichter zu zeigen, dass sie korrekt ist (wie gewohnt unter der Annahme, dass die Funktionen, die sie aufruft, korrekt sind.)

> _Übung: schreibe increment auf die selbe Weie um._

### 13.6 Verallgemeinerung

In einem gewissen Sinn ist dieses Umwandeln von Basis 60 nach Basis 10 und wieder zuruck schwieriger, als einfach mit Zeitangaben zu operieren. Basis-Umwandlung ist abstrakter; unsere Inuition fur den Umgang mit Zeiten ist besser.

Wenn wir aber die Einsicht haben, dass Zeitangaben als Basis-60-Zahlen behandelt werden konnen, und wenn wir uns fur die Investition entscheiden, diese Umwandlungsfunktionen (convertToSeconds und makeTime) zu schreiben, dann bekommen wir ein kurzeres, leichter lesbares Programm, das uberdies leichter von Fehlern zu befreien und zuverlassiger ist.

Zusatzlich ist es auch leichter, spater neue Programmerweiterungen hinzuzufugen. Stelle dir z.B. vor, du mochtest die Subtraktion zweier Zeiten implementieren, um die Dauer des Zeitintervalls zwischen ihnen heraus zu finden. Der naive Zugang ware, diese Subtraktion mit "Ausborgen von der nachsthoheren Stelle" zu implementieren. Mit unseren Umwandlungsfunktionen wurde die Sache aber leichter sein und auch mit hoherer Wahrscheinlichkeit korrekt.

Witzigerweise ist es manchmal so, das man ein Problem, wenn man es schwieriger (und allgemeiner) angeht, schließlich leichter macht. (Denn es sind dann weniger Spezialfalle zu beachten und weniger Gelegenheiten vorhanden, Fehler zu machen.)

### 13.7 Algorithmen

Wenn du eine allgemeine Losung fur eine Klasse von Problemen schreibst, im Gegensatz zu einer speziellen Losung fur ein einzelnes Problem, dann hast du einen **Algorithmus** geschrieben. Wir haben diesen Begriff schon fruher erwahnt, wir haben ihn aber nicht sorgfaltig definiert. Er ist namlich nicht leicht zu definieren. Wir werden daher ein paar Versuche machen:

Zuerst betrachten wir etwas, was kein Algorithmus ist. Wie du gelernt hast, wie man einstellige Zahlen multipliziert, hast du wahrscheinlich einfach die "Multiplikations-Tabelle" auswendig gelernt. Das heißt, du hast einfach 100 spezielle Ergebnisse auswendig gelernt. Diese Art von Wissen ist kein Algorithmus.

Wenn du aber "faul" warst, hast du dabei vielleicht ein wenig getrickst, indem du ein paar Abkurzungen geleernt hast. Um zum Beispiel das Produkt von n und 9 zu finden, kannst du n-1 als die erste Ziffer schreiben und 10-n als die zweite Ziffer. Dieser Trick ist eine allgemeine Losung fur die Multiplikation einer einziffrigen Zahl mit 9. Das ist ein Algorithmus!

In ahnlicher Weise sind die Techniken fur das Addieren (mit Übertrag), fur das Subtrahieren (mit Ausborgen) und fur das Dividieren alle Algorithmen. Eine chrakteristische Eigenschaft von Algorithmen ist, das man keinerlei Intelligenz braucht, um sie auszufuhren. Sie sind mechanische Vorgange, wo jeder Schritt auf den vorigen entsprechend einem einfachen Satz von Regeln folgt.

Unserer Meinung nach ist es erstaunlich, dass die Menschen in der Schule so viel Zeit damit verbringen, zu lernen, wie man Algorithmen ausfuhrt, die, buchstablich, keine Intelligenz erfordern.

Andererseits ist der Prozess des Entwurfs von Algorithmen durchaus interessant, intellektuell herausfordernd, und durchaus ein zentraler Bestandteil dessen, was wir Programmieren nennen.

Manches von dem, was die Leute ganz selbstverstandlich tun, ohne dabei Schwierigkeiten zu haben oder bewusst daruber nachzudenken, gehort zu den Vorgangen, die am Schwierigsten algorithmisch auszudrucken sind. Das Verstehen naturlicher Sprache ist ein gutes Beispiel dafur. Wir alle konnen das, aber bis heute war niemand in der Lage zu erklaren, _wie_ wir das tun, jedenfalls nicht in der Form eines Algorithmus.

### 13.8 Glossar

**reine Funktion**
    Eine Funktion, die keines der Objekte, die sie als Argumente ubernimmt, verandert. Die meisten reinen Funktionen haben Werte.
**pure function**
    A function that does not modify any of the objects it receives as parameters. Most pure functions are fruitful.

**modifizierende Funktion**
    Eine Funktion, die ein oder mehrere Objekte, die sie als Argumente ubernimmt, verandert. Die meisten modifizierenden Funktionen haben keine Werte.
**modifier**
    A function that changes one or more of the objects it receives as parameters. Most modifiers are void.

**funktionaler Programmierstil**
    Ein Stil des Programmentwurfs, bei dem der uberwiegende Anteil der Funktionen reine Funktionen sind.
**functional programming style**
    A style of program design in which the majority of functions are pure.

**Prototyp Entwicklung**
    Ein Verfahren der Programmentwicklung, das mit der Programmierung eines Prototyps beginnt und das Programm dann schrittweise testet und verbessert.
**prototype development**
    A way of developing programs starting with a prototype and gradually testing and improving it.

**geplante Entwicklung**
    Ein Verfahren der Programmentwicklung, das tiefere Einsicht in das Problem voraussetzt und mehr auf Planung als auf schrittweise Entwicklung oder Prototyp-Entwicklung setzt.
**planned development**
    A way of developing programs that involves high-level insight into the problem and more planning than incremental development or prototype development.

**Algorithmus**
    Ein Satz von Anweisungen, mit dem eine Klasse von Problemen durch einen mechanischem unintelligenten Prozess gelost wird. 
**algorithm**
    A set of instructions for solving a class of problems by a mechanical, unintelligent process.
  


## Kapitel 14

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [Gregor Lingl](mailto:glingl@aon.at) _

### 14.1 Objektorientierte Elemente

Python ist eine **objektorientierte Programmiersprache**. Das heißt, dass sie Sprachelemente enthalt, die **objektorientiertes Programmieren** unterstutzen.

Es ist nicht ganz leicht, objektorientiertes Programmieren zu definieren. Wir haben aber bereits einige charakteristische Eigenschaften davon gesehen.

  * Programme bestehen aus Objektdefinitionen und Funktionsdefinitionen, und die meisten Berechnungen werden durch Operationen auf Objekten ausgedruckt.
  * Jede Objektdefinition entspricht einem Objekt (Gegenstand) oder einem Begriff der wirklichen Welt. Die Funktionen, die auf einem Objekt operieren, entsprechen den Wechselwirkungen zwischen Objekten in der wirklichen Welt.

Zum Beispiel entspricht die Time-Klasse, die wir in [Kapitel 13](http://python4kids.net/how2think/kap13.htm) definiert haben, der Art und Weise, wie wir Menschen die Tageszeit festhalten. Die Funktionen, die wir dort definiert haben, entsprechen dem, was _wir_ mit solchen Zeitangaben machen. In ahnlicher Weise entsprechen die Point und Rectangle Klassen den mathematischen Begriffen von Punkt und Rechteck.

Bis jetzt haben wir von den Eigenschaften von Python, die objektorientiertes Programmieren unterstutzen, noch keinen Gebrauch gemacht. Ganz streng genommen sind diese Sprachelemente auch nicht notig. In der Hauptsache stellen sie nur eine alternative Syntax fur jene Dinge bereit, die wir bis jetzt schon gemacht haben, aber in vielen Fallen ist diese Alternative pragnanter und vermittelt eine genauere Darstellung der Programmstruktur.

Zum Beispiel gibt es in dem Time Programm keine offensichtliche Verbindung zwischen der Klassendefinition und den Funktionsdefinitionen, die darauf folgen. Schaut man aber genauer hin, so wird offenbar, dass jede Funktion mindestens ein Time Objekt als Argument ubernimmt.

Diese Beobachtung dient uns als Motivation fur die Einfuhrung von **Methoden**. Wir haben schon fruher einige Methoden gesehen, wie etwa keys und values, die fur Dictionaries aufgerufen wurden. Jede Methode gehort zu einer Klasse und ist dazu gedacht, fur Instanzen dieser Klasse aufgerufen zu werden.

Methoden sind etwas ganz ahnliches wie Funktionen, jedoch mit zwei Unterschieden:

  * Methoden werden innerhalb einer Klassendefinition definiert, um die Beziehung zwischen der Klasse und der Methode ausdrucklich herzustellen.
  * Die Syntax fur den Aufruf einer Methode ist verschieden von der Syntax fur einen Funktionsaufruf.

In den folgenden Abschnitten werden wir uns die Funktionen von den letzten beiden Kapiteln hernehmen und sie in Methoden umwandeln. Diese Umwandlung funktioniert ganz mechanisch; man kann sie durchfuhren, indem man einfach eine bestimmte Folge von Schritten ausfuhrt. Wenn man diese Umwandlung von einer Form in die andere gut beherrscht, ist man auch im Stande, die jeweils beste Form fur die gerade anstehende Aufgabe zu wahlen.

### 14.2 printTime

In [Kapitel 13](http://python4kids.net/how2think/kap13.htm), haben wir eine Time genannte Klasse definiert und du hast eine Funktion namens printTime geschrieben, die etwa so ausgesehen haben wird:

class Time:   
pass

def printTime(time):   
print str(time.hours) + ":" \+   
str(time.minutes) + ":" \+   
str(time.seconds)

Beim Aufruf dieser Funktion haben wir ihr ein Time Objekt als Argument ubergeben

>>> currentTime = Time()   
>>> currentTime.hours = 9   
>>> currentTime.minutes = 14   
>>> currentTime.seconds = 30   
>>> printTime(currentTime)

Um aus der Funktion printTime eine Methode zu machen, mussen wir nur die Funktionsdefinition in die Klassendefinition einfugen. Beachte dabei die Änderung bei der Einruckung.

class Time:   
def printTime(time):   
print str(time.hours) + ":" \+   
str(time.minutes) + ":" \+   
str(time.seconds)

Nun konnen wir printTime mit der Punkt-Notation aufrufen.

>>> currentTime.printTime()

Das Objekt, fur das die Methode aufgerufen wird, erscheint wie gewohnt vor dem Punkt und der Name der Methode steht nach dem Punkt.

Das Objekt, fur das die Methode aufgerufen wird, wird dem ersten Parameter zugewiesen. In diesem Fall wird also currentTime dem Parameter time zugewiesen.

Es gibt eine Vereinbarung, den ersten Parameter einer Methode self zu nennen. Der Grund fur diese Vereinbarung ist ein wenig verwickelt, aber ihre Grundlage ist eine nutzliche Metapher.

Die Syntax fur einen Funktionsaufruf, printTime(currentTime), legt die Idee nahe, dass die Funktion hier das aktive Element ist. Sie besagt etwa: "He, printTime! Hier ist ein Objekt, das du ausgeben sollst."

Beim objektorientierten Programmieren sind die Objekte die aktiven Elemente. Ein Aufruf wie currentTime.printTime() besagt "He, currentTime! Bitte gib dich selbst aus"

Dieser Wechsel der Perspektive ist vielleicht hoflicher, aber es ist nicht offensichtlich, dass er auch nutzlich ist. In den Beispielen, die wir bisher gesehen haben, ist es vielleicht nicht so. Aber manchmal erleichtert das Verschieben der Verantwortung von den Funktionen zu den Objekten das Schreiben von vielseitiger verwendbaren **versatile?** Funktionen und es erleichtert auch die Wartung und die Wiederverwendbarkeit von Code.

### 14.3 Noch ein Beispiel

Wir wollen jetzt increment (aus [Abschnitt 13.3](http://python4kids.net/how2think/kap13.htm)) in eine Methode umwandeln. Um Platz zu sparen, werden wir fruher definierte Methoden hier weglassen, aber du solltest sie in deiner Version stehen haben:

class Time:   
#fruher definierte Methoden hierher...

def increment(self, secs):   
self.secs = secs + self.seconds

while self.seconds >= 60:   
self.seconds = self.seconds - 60   
self.minutes = self.minutes + 1

while self.minutes >= 60:   
self.minutes = self.minutes - 60   
self.hours = self.hours + 1

Die Umwandlung geschieht rein mechanisch wir verschieben die Funktions**method**definition in die Klassendefinition, **rucken sie um eine Ebene weiter ein** und andern den Namen des ersten Parameters.

Nun konnen wir increment als Methode aufrufen.

currentTime.increment(500)

Wieder wird das Objekt, fur das die Methode aufgerufen wird, dem ersten Parameter, self, zugewiesen. Der zweite Parameter, secs bekommt den Wert 500.

### 14.4 Ein komplizierteres Beispiel

Die after Funktion ist etwas komplizierter, weil sie auf zwei Time Objekten operiert und nicht auf nur einem. Wir konnen nur einen der Parameter in self umwandeln; der andere bleibt gleich:

class Time:   
# fruher definierte Methoden hierher...

def after(self, time2):   
if self.hour > time2.hour:   
return 1   
if self.hour < time2.hour:   
return 0

if self.minute > time2.minute:   
return 1   
if self.minute < time2.minute:   
return 0

if self.second > time2.second:   
return 1   
return 0

Wir rufen die Methode fur ein Objekt auf und ubergeben das andere als Argument:

if doneTime.after(currentTime):   
print "The bread will be done after it starts."

Dieser Aufruf kann fast wie ein englischer Satz gelesen werden: "If the done-time is after the current-time, then..."

### 14.5 Optionale Argumente

Wir kennen schon eingebaute Funktionen, die eine variable Anzahl von Argumenten ubernehmen. Zum Beispiel kann string.find zwei, drei oder vier Argumente ubernehmen.

Es ist moglich, benutzerdefinierte Funktionen zu schreiben, die optionale Argumente haben. Zum Beispiel konnen wir unsere eigene Version von find in der Weise verbessern, dass sie so funktioniert wie string.find.

Das ist die originale Version aus dem [Abschitt 7.7](http://python4kids.net/how2think/kap07.htm):

def find(str, ch):   
index = 0   
while index < len(str):   
if str[index] == ch:   
return index   
index = index + 1   
return -1

Das ist die neue, verbesserte Verson:

def find(str, ch, start=0):   
index = start   
while index < len(str):   
if str[index] == ch:   
return index   
index = index + 1   
return -1

Der dritte Parameter, start, ist optional, weil fur ihn ein als Voreinstellung ein Standardwert *default value* angegeben wird. Wenn wir die Funktion find nur mit zwei Argumenten aufrufen, benutzt sie den Standardwert und beginnt die Suche vom Anfang der Zeichenkette an.

>>> find("apple", "p")   
1

Wenn wir ein drittes Argument ubergeben, **uberschreibt** es den voreingestellten Standardwert.

>>> find("apple", "p", 2)   
2   
>>> find("apple", "p", 3)   
-1

> _Übung: Fuge einen vierten Parameter,_ end_, hinzu, der angibt, wo die Suche beendet werden soll. _
> 
> _ Warnung: Diese Übung ist ein bißchen heikel, *tricky*. Der voreingestellte Standardwert fur_ end _sollte namlich_ len(str) _sein, aber das funktioniert nicht. Die voreingestellten Standardwerte werden namlich ermittelt, wenn die Funktion definiert wird und nicht, wenn sie aufgerufen wird. Wenn_ find _definiert wird, existiert aber_ str _noch gar nicht. Daher kannst du zu diesem Zeitpunkt seine Lange gar nicht ermitteln._

### 14.6 The Initialisierungsmethode

Die **Initialisierungsmethode** ist eine spezielle Methode, die (automatisch?) aufgerufen wird, wenn ein Objekt erzeugt wird. Der Name dieser Methode ist __init__ (zwei Unterstrich-Zeichen gefolgt von init und zwei weiteren Unterstrich-Zeichen). Eine Initialisierungsmethode fur die Time Klasse sieht so aus:

class Time:   
def __init__(self, hours=0, minutes=0, seconds=0):   
self.hours = hours   
self.minutes = minutes   
self.seconds = seconds

Es besteht kein Konflikt zwischen dem Attribut self.hours und dem Parameter hours. Durch die Punkt-Notation wird festgelegt, welche Variable jeweils gemeint ist.

Wenn wir den Time Konstruktor aufrufen, werden die Argumente, die wir ubergeben an init weiter gereicht:

>>> currentTime = Time(9, 14, 30)   
>>> currentTime.printTime()

Weil die Argumente optional sind, konnen wir sie weglassen:

>>> currentTime = Time()   
>>> currentTime.printTime()   
>>> 0:0:0

Oder nur das erste Argument ubergeben:

>>> currentTime = Time (9)   
>>> currentTime.printTime()   
>>> 9:0:0

Oder die ersten zwei Argumente:

>>> currentTime = Time (9, 14)   
>>> currentTime.printTime()   
>>> 9:14:0

Schließlich konnen wir auch eine Teilmenge der Argumente ubergeben, indem wir namentlich angeben, welchen Parametern sie zugewiesen werden sollen:

>>> currentTime = Time(seconds = 30, hours = 9)   
>>> currentTime.printTime()   
>>> 9:0:30

### 14.7 Nochmals Punkte

Schreiben wir nun die Point Klasse aus [Abschnitt 12.1](http://python4kids.net/how2think/kap12.htm) neu, nun in einem mehr objektorientierten Stil:

class Point:   
def __init__(self, x=0, y=0):   
self.x = x   
self.y = y

def __str__(self):   
return '(' + str(self.x) + ', ' + str(self.y) + ')'

Die Initialisierungsmethode ubernimmt die Werte x und y als optionale Argumente; die voreingestellten Standardwerte fur beide Argumente sind 0.

Die nachste Methode __str__, gibt eine String-Darstellung eines Point Objekts zuruck. Wenn eine Klasse eine Methode mit dem Namen __str__ enthalt, dann uberschreibt diese das voreingestellte Verhalten von Pythons eingebauter str Funktion.

>>> p = Point(3, 4)   
>>> str(p)   
'(3, 4)'

Die Ausgabe eines Point-Objektes mit der print-Anweisung ruft hinter den Kulissen die __str__-Methode fur das Objekt aus; somit andert die Definition von __str__ in einer Klasse auch das Verhalten von print:

>>> p = Point(3, 4)   
>>> print p   
(3, 4)

Wenn wir eine neue Klasse schreiben, beginnen wir fast immer damit __init__ zu schreiben, weil es dadurch leichter wird, Objekte zu instanziieren, und dann __str__, weil dies fast immer nutzlich furs Debuggen ist.

### 14.8 Überladen von Operatoren

In manchen Sprachen ist es moglich, die Definition der eingebauten Operatoren fur den Fall zu erweitern, dass sie auf benutzerdefinierte Typen angewendet werden. Dies nennt man **Überladen von Operatoren**. Das ist insbesondere nutzlich, wenn man neue mathematische Typen definiert.

Um etwa den Additionsoperator + zu uberladen, definieren wir eine Methode namens __add__:

class Point:   
#fruher definierte Methoden hierher...

def __add__(self, other):   
return Point(self.x + other.x, self.y + other.y)

Wie ublich ist der erste Parameter fur das Objekt reserviert, fur das die Methode aufgerufen wird. Der zweite Parameter heißt sinnigerweise other um ihn von self zu unterscheiden. Um zwei Points zu addieren, erzeugen wir einen neuen Point, der die Summen der x Koordinaten bzw. der y Koordinaten enthalt und geben diesen zuruck.

Wenn wir nun den + Operator auf Point Objekte anwenden, dann ruft Python hinter den Kulissen __add__ auf:

>>> p1 = Point(3, 4)   
>>> p2 = Point(5, 7)   
>>> p3 = p1 + p2   
>>> print p3   
(8, 11)

Der Ausdruck p1 + p2 ist gleichwertig mit p1.__add__(p2), aber offensichtlich eleganter.

> _Übung: Fuge eine Methode_ __sub__(self, other) _zur Klasse_ Point _hinzu, die den Subtraktionsoperator uberladt und teste sie anschließend._

Es gibt verschiedene Arten, das Verhalten des Multiplikationsoperators fur Punkte zu erweitern: durch Definition der Methoden __mul__, oder __rmul__, oder beide.

Wenn der linke Operand von * ein Point ist, ruft Python die Methode __mul__ auf, wobei der andere Operand ebenfalls ein Point Objekt sein muss. Sie berechnet das **innere Produkt** der zwei Punkte entsprechend den Regeln der linearen Algebra:

def __mul__(self, other):   
return self.x * other.x + self.y * other.y

Wenn der linke Operand von * ein *primitiver* Typ und der rechte Operand ein Point ist, ruft Python __rmul__ auf, welches eine **skalare Multiplikation** ausfuhrt:

def __rmul__(self, other):   
return Point(other * self.x, other * self.y)

Das Ergebnis ist ein neues Point Objekt, dessen Koordinaten ein Vielfaches der Koordinaten des ursprunglichen Punktes sind.

*** Nachdenken:

If other is a type that cannot be multiplied by a floating-point number, then __rmul__ will yield an error.

Wenn other ein Typ ist, der nicht mit einer Gleitkommazahl multipliziert werden kann, dann wird __rmul__ einen Fehler ergeben.

Nachdenken ***

Das folgende Beispiel zeigt beide Arten der Multiplikation:

>>> p1 = Point(3, 4)   
>>> p2 = Point(5, 7)   
>>> print p1 * p2   
43   
>>> print 2 * p2   
(10, 14)

Was geschieht, wenn wir versuchen p2 * 2 auszuwerten? Weil das erste Argument ein Punkt ist, ruft Python __mul__ mit 2 als zweitem Argument auf. Bei der Ausfuhrung von __mul__ versucht das Programm auf die x Koordinate von other zuzugreifen; das schlagt fehl, weil eine Ganzzahl keine Attribute hat:

>>> print p2 * 2   
AttributeError: 'int' object has no attribute 'x'

Leider ist die Fehlermeldung ein bißchen undurchsichtig. Dieses Beispiel demonstriert einige Schwierigkeiten der objektorientierten Programmierung. Manchmal ist es schon allein recht muhsam herauszufinden, welcher Code gerade ausgefuhrt wird.

Ein vollstandiger ausgefuhrtes Beispiel fur Überladen von Operatoren findest du in [Anhang ]().

### 14.9 Polymorphismus

Die meisten Methoden, die wir geschrieben haben, funktionieren nur fur einen speziellen Typ. Wenn man eine neue Klasse (**Objekt**) erzeugt, schreibt man Methoden, die fur diesen Typ aufgerufen werden.

Es gibt aber gewisse Operationen, die man auf viele Typen anwenden mochte, wie zum Beispiel die arithmetischen Operationen im vorigen Abschnitt. Wenn viele Typen die selbe Menge von Operationen aufweisen, kann man Funktionen schreiben, die auf all diesen Typen arbeiten.

Nehmen wir als Beispiel folgende multadd Operation mit drei Parametern (die in der linearen Algebra gebrauchlich ist). Sie multipliziert die ersten zwei und addiert zum Produkt den dritten. Wir konnen das in Python so schreiben:

def multadd (x, y, z):   
return x * y + z

Diese Methode wird fur alle Werte von x und y funktionieren, die multipliziert werden konnen und fur beliebige Werte von z, die zu dem Produkt addiert werden konnen.

Wir konnen sie mit numerischen Werten aufrufen:

>>> multadd (3, 2, 1)   
7

Oder mit Point-Objekten:

>>> p1 = Point(3, 4)   
>>> p2 = Point(5, 7)   
>>> print multadd (2, p1, p2)   
(11, 15)   
>>> print multadd (p1, p2, 1)   
44

Im ersten Fall wird der Point mit einem Skalar multipliziert und dann zu einem anderen Point addiert. Im zweiten Fall liefert das innere Produkt der Punkte einen Zahlenwert, daher muss das dritte Argument ebenfalls ein Zahlenwert sein.

Eine Funktion wie diese, die Argumente von verschiedenem Typ ubernehmen kann wird **polymorph** genannt.

Berachten wir als weiteres Beispiel die Methode frontAndBack, die eine Liste zwei Mal, vorwarts und ruckwarts, ausgibt:

def frontAndBack(front):   
import copy   
back = copy.copy(front)   
back.reverse()   
print str(front) + str(back)

Weil die reverse Methode eine modifizierende Methode ist, machen wir zuerst eine Kopie der Liste und kehren diese um. Auf diese Weise modifiziert diese Funktion nicht die Liste, die sie als Argument erhalt.

Hier ist ein Beispiel, das frontAndBack auf eine Liste anwendet:

>>> myList = [1, 2, 3, 4]   
>>> frontAndBack(myList)   
[1, 2, 3, 4][4, 3, 2, 1]

Naturlich, wir wollten diese Funktion auf Listen anwenden, daher ist es nicht uberraschend, dass sie da funktioniert. Überraschend ware es allerdings, wenn wir diese Funktion auch auf Punkte anwenden konnten.

Um heraus zu finden, ob eine Funktion auf einen neuen Typ angewendet werden kann, benutzen wir die Grundregel des Polymorphismus:

> **Wenn alle Operationen innerhalb einer Funktion auf einen Typ angewendet werden konnen, kann auch die Funktion auf diesen Typ angewendet werden.**

Die Operationen in dieser Funktion umfassen copy, reverse, und print.

copy arbeitet mit jedem Objekt, und wir haben auch schon eine __str__ Methode fur Point Objekte geschrieben. Daher ist alles was wir brauchen, eine reverse Methode in der Point Klasse:

def reverse(self):   
self.x , self.y = self.y, self.x

Jetzt konnen wir Point Objekte an frontAndBack ubergeben:

>>> p = Point(3, 4)   
>>> frontAndBack(p)   
(3, 4)(4, 3)

Die schonste Art des Polymorphismus ist die unbeabsichtigte: wenn man entdeckt, dass eine Funktion, die man bereits fertig geschrieben hat, auf einen Typ angewendet werden kann, fur den sie niemals geplant war.

### 14.10 Glossar

**objectorientierte Sprache**
    Eine Sprache mit Sprachelementen, die objektorientierte Programmierung unterstutzt, wie zum Beispiel benutzerdefinierte Klassen und Vererbung.
**object-oriented language**
    A language that provides features, such as user-defined classes and inheritance, that facilitate object-oriented programming.

**objektorientierte Programmierung**
    Ein Programmierstil, bei dem Daten und Operationen, die mit diesen Daten arbeiten, als Klassen und Methoden organisiert sind.
**object-oriented programming**
    A style of programming in which data and the operations that manipulate it are organized into classes and methods.

**Methode**
    Eine Funktion, die innerhalb einer Klassendefinition definiert wird und fur Instanzen dieser Klasse aufgerufen wird.
**method**
    A function that is defined inside a class definition and is invoked on instances of that class.

**uberschreiben**
    Einen Standardwert ersetzen. Zum Beispiel einen Standardwert fur einen Parameter durch ein bestimmtes Argument ersetzen, oder eine Standardmethode durch eine neue Methode mit demselben Namen ersetzen.
**override**
    To replace a default. Examples include replacing a default parameter with a particular argument and replacing a default method by providing a new method with the same name.

**Initialisierungsmethode**
    Eine spezielle Methode, die automatisch aufgerufen wird, wenn ein neues Objekt erzeugt wird und die die Attribute dieses Objekts mit Anfangswerten ausstattet.
**initialization method**
    A special method that is invoked automatically when a new object is created and that initializes the object's attributes.

**Überladung von Operatoren**
    Erweiterung eingabauter Operatoren (+, -, *, >, <, usw.), so dass sie auch mit benutzerdefinierten Typen arbeiten.
**operator overloading**
    Extending built-in operators (+, -, *, >, <, etc.) so that they work with user-defined types.

**Inneres Produkt**
    Eine Rechenoperation, die in der linearen Algebra definiert wird und die zwei Punkte, vom Typ Point, multipliziert und einen Zahlenwert als Ergebnis hat.
**dot product**
    An operation defined in linear algebra that multiplies two Points and yields a numeric value.

**skalare Multiplikation**
    Eine Rechenoperation, die in der linearen Algebra definiert wird, die jede Koordinate eines Punktes, vom Typ Point, mit einem Zahlenwert multipliziert.
**scalar multiplication**
    An operation defined in linear algebra that multiplies each of the coordinates of a Point by a numeric value.

**polymorph**
    Eine Funktion, die auf mehr als einen Typ angewendet werden kann. Wenn alle Operationen in einer Funktion auf einen Typ angewendet werden konnen, dann kann die Funktion auf diesen Typ angewendet werden.
**polymorphic**
    A function that can operate on more than one type. If all the operations in a function can be applied to a type, then the function can be applied to a type.
  


## Kapitel 15

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [Gregor Lingl](mailto:glingl@aon.at) _

### 15.1 Komposition

Bis hierher hast du schon etliche Beispiele fur Komposition gesehen. Eines der ersten war die Verwendung eines Methodenaufrufs als Teil eines Ausdrucks. Ein weiteres ist die geschachtelte Struktur von Anweisungen; man kann eine if Anweisung innerhalb einer while Schleife schreiben, innerhalb einer anderen if Anweisung, und so weiter.

Nachdem du dieses Muster kennst und auch schon einiges uber Listen und Objekte weißt, wirst du nicht uberrascht sein, zu erfahren, dass du auch Listen von Objekten erzeugen kannst. Oder auch Objekte, die Listen (als Attribute) enthalten; du kannst Listen erzeugen, die Listen enthalten und auch Objekte, die Objekte enthalten, und so weiter.

In diesem und im nachsten Kapitel werden wir uns einige Beispiele solcher Kompositionen ansehen. Zu diesem Zweck werden wir Spielkarten im Computer modellieren, also Objekte von Typ Karte erzeugen.

### 15.2 Spielkarten - Objekte von Typ Karte

Wenn du mit herkommlichen Spielkarten nicht vertraut bist, ist jetzt eine gute Gelegenheit, dir ein Paket davon zu besorgen. Andernfalls konnte es sein, dass dieses Kapitel fur dich nicht viel Sinn macht.

In einem Paket sind zweiundfunfzig Karten. Jede von ihnen gehort zu einer von vier Farben und jede hat einen von dreizehn Rangen. Die Farben sind Herz, Karo, Pik, Treff in (absteigender Reihenfolge). Die Range sind As, 2, 3, 4, 5, 6, 7, 8, 9, 10, Bube, Dame, Konig. Ja nach dem, welches Kartenspiel du spielst, kann der Rang des As kleiner als 2 oder auch großer als der Konig sein.

Wenn wir nun Objekte erzeugen wollen, die uns Spielkarten im Computer modellieren, ist klar welche Attribute wir brauchen: rang und farbe. Es ist aber keineswegs so klar, welchen Typ diese Attribute haben sollen. Eine Moglichkeit ware, Zeichenketten zu verwenden, mit Inhalten wie "Pik" fur eine Farbe oder "Dame" fur einen Rang. Ein Problem mit dieser Implementation ware aber, dass es nicht leicht ware Karten zu vergleichen, um herauszufinden, welche einen hoheren Rang oder eine hohere Farbe hat.

Eine Alternative dazu ist die Verwendung von ganzen Zahlen zur **Kodierung** von Rang und Farbe. Mit Kodierung meinen wir nicht, wie manche Leute glauben, die Verschlusselung in einen Geheimcode. Informatiker verstehen unter "Kodierung" die "Definition einer Abbildung zwischen einer Folge von Zahlen und den Elementen, die sie darstellen sollen". Zum Beispiel:

Eine offensichtliche Eigenschaft dieser Abbildung ist, dass die Farben auf Zahlen so abgebildet werden, dass man den Vergleich von Farben auf den Vergleich der zugehorigen Zahlen zuruckfuhren kann. Die Abbildung fur die Range ergibt sich ziemlich naturlich; numerische Range werden auf die entprechenden ganzen Zahlen abgebildet und fur die anderen Karten definieren wir:

Wir haben einen Grund, warum wir eine mathematische Notation fur diese Abbildungen verwenden: sie sind nicht Teil des Python Programms, das wir jetzt schreiben wollen. Sie gehoren zum Programmentwurf, aber sie erscheinen nicht explizit im Code. Die Klassendefinition fur den Typ Karte sieht so aus:

class Karte:   
def __init__(self, farbe=0, rang=2):   
self.farbe = farbe   
self.rang = rang

Wie gewohnt haben wir hier eine Initialisierungsmethode geschrieben, die ein optionales Argument fur jedes Attribut ubernimmt. Der Standardwert fur die farbe ist 0, was die Farbe Treff darstellt.

Um eine Karte zu erzeugen, rufen wir den Karte Konstruktor mit den Argumenten der Karte, die wir haben wollen auf:

treffDrei = Karte(0, 3)

Im nachsten Abschnitt werden wir heraus finden, welche Karte wir da gerade erzeugt haben.

### 15.3 Klassenattribute und die __str__ Methode

Damit wir Kartenobjekte so ausgeben konnen, dass sie leicht lesbar sind, wollen wir die ganzzahligen Codes auf Worter abbilden. Auf naturliche Weise geht das mit Listen von Zeichenketten. Wir weisen diese Listen sogenannten **Klassenattributen** am Anfang der Klassendefinition zu:

class Karte:   
farbListe = ["Treff", "Pik", "Karo", "Herz"]   
rangListe = ["nix", "As", "2", "3", "4", "5", "6", "7",   
"8", "9", "10", "Bube", "Dame", "Konig"]

#init Methode weggelassen

def __str__(self):   
return (self.farbListe[self.farbe] + " " \+   
self.rangListe[self.rang])

Klassenattribute werden außerhalb aller Methoden definiert. Auf sie kann von allen Methoden der Klasse aus zugegriffen werden.

In der Methode __str__ konnen wir farbListe und rangListe benutzen, um die numerischen Werte vonfarbe und rang auf Strings abzubilden. Zum Beispiel bedeutet der Ausdruck self.farbListe[self.farbe] "benutze das Attribut farbe des Objekts self als Index fur das Klassenattribut farbListe, und wahle den entsprechenden String aus."

Der Zweck des Eintrags "nix" als erstes Element in rangListe ist es, als Platzhalter fur das nullte Element der Liste zu fungieren, das nicht zur Verwendung gedacht ist. Nur die Range 1 bis 13 sind gultig. Dieses zusatzliche Element ist nicht zwingend notwendig. Wir hatten auch, wie ublich, mit Index 0 beginnen konnen. Wir finden es aber weniger verwirrend, 2 mit 2 zu kodieren, 3 mit 3 und so fort.

Mit den Methoden, die wir bis jetzt haben, konnen wir Karten erzeugen und ausgeben:

>>> karte1 = Karte(3, 11)   
>>> print karte1   
Herz Bube

Klassenattribute wie farbListe werden von allen Karte Objekten gemeinsam verwendet. Der Vorteil davon ist, dass wir ein beliebiges Objekt des Typs Karte verwenden konnen um auf Klassenattribute zuzugreifen:

>>> karte2 = Karte(3, 3)   
>>> print karte2   
Herz 3   
>>> print karte2.farbListe[3]   
Herz

Der Nachteil ist aber, dass eine Veranderung eines Klassenattributes jede Instanz der Klasse betrifft. Wenn wir beispielsweise finden, dass "Herz Bube" \- in irgend einem sonderbaren Kartenspiel - besser "Morder Bube" heißen sollte, konnen wir folgendes machen:

>>> karte1.farbListe[3] = "Morder"   
>>> print karte1   
Morder Bube

Das Problem dabei ist, dass _alle_ Herz dabei zu Mordern werden:

>>> print karte2   
Morder 3

Es ist normalerweise kein guter Einfall Klassenattribute zu verandern.

### 15.4 Karten vergleichen

Fur einfache Datentypen haben wir die Vergleichsoperatoren (<, >, ==, etc.) zum Vergleich von Werten kennengelernt. Sie stellen fest ob ein Wert großer oder kleiner als ein anderer oder gleich einem anderen ist. Fur benutzerdefinierte Datentypen konnen wir dieses Verhalten der eingebauten Operatoren erweitern, indem wir eine Methode namens __cmp__ bereit stellen (von _compare_, engl.: vergleichen). Es ist festgelegt, dass __cmp__ zwei Parameter self und other hat und 1 zuruckgibt, wenn das erste Objekt großer ist als das zweite, -1 wenn das zweite Objekt großer ist und 0 wenn beide gleich groß sind.

Manche Typen sind vollstandig geordnet. Das heißt, man kann zwei beliebige Elemente davon vergleichen und feststellen, welches großer ist. So sind zum Beispiel die ganzen Zahlen und die Gleitkommazahlen vollstandig geordnet. Manche Mengen sind ungeordnet. Das heißt, dass man nicht auf sinnvolle Weise angeben kann, dass ein Element großer als das andere ist. So sind zum Beispiel die Fruchte ungeordnet, weshalb wir nicht Äpfel mit Birnen vergleichen konnen.

Die Menge der Spielkarten ist teilweise geordnet. Das heißt, manchmal kann man zwei Karten vergleichen und manchmal nicht. Zum Beispiel ist es klar, dass Pik 3 hoher ist als Pik 2; ebenso ist Pik 3 hoher als Treff 3. Aber welche der Karten Treff 3 und Pik 2 ist hoher? Eine hat einen hoheren Rang, aber die andere eine hohere Farbe.

Um Spielkarten vergleichbar zu machen, muss man entscheiden, was wichtiger ist, Rang oder Farbe. Offen gesagt, die Wahl steht uns frei. Wahlen wir also etwas, indem fir festlegen, dass die Farbe wichtiger ist als der Rang, weil ein neu gekauftes Paket Karten sortiert daher kommt, alle Treff beisammen, dann alle Pik und so fort.

Nach dieser Entscheidung konnen wir __cmp__ schreiben:

def __cmp__(self, other):   
# Prufung der Farben   
if self.farbe > other.farbe: return 1   
if self.farbe < other.farbe: return -1   
# Farben sind gleich... Prufung der Range   
if self.rang > other.rang: return 1   
if self.rang < other.rang: return -1   
# Range sind gleich... unentschieden   
return 0

In dieser Ordnung gelten Asse weniger als Karten mit Rang 2.

> _Übung: andere_ __cmp__ _so ab, dass Asse einen hoheren Rang haben als Konige._

### 15.5 Pakete

Nun, da wir Objekte haben, die Karten reprasentieren, ist der nachste logische Schritt eine Klasse zu definieren, um ein Paket zu modellieren. Naturlich besteht ein Paket aus Karten, daher wird jedes Paket Objekt eine Liste von Karten als Attribut enthalten.

Es folgt nun eine Klassendefinition fur die Paket Klasse. Die Initialisierungsmethode erzeugt das Attribut karten mitsamt dem Standardset von zweiundfunfzig Karten:

class Paket:   
def __init__(self):   
self.karten = []   
for farbe in range(4):   
for rang in range(1, 14):   
self.karten.append(Karte(farbe, rang))

Der einfachste Weg, das Paket aufzufullen, verwendet eine geschachtelte Schleife. Die außere Schleife nummeriert die Farben von 0 bis 3. Die innere Schleife nummeriert die Range von 1 bis 13. Weil die außere Schleife vier mal durchlaufen wird und die innere Schleife dreizehn mal, wird der Schleifenkorper insgesamt 52 mal ausgefuhrt (dreizehn mal vier). Jede Iteration, also jeder Schleifendurchgang, erzeugt eine neue Instanz der Klasse Karte mit laufender Farbe und laufendem Rang und hangt diese Karte (mit der Methode append) an die karten Liste an.

Die append Methode funktioniert fur Listen, aber naturlich nicht fur Tupel.

### 15.6 (Bildschirm)ausgabe des Pakets

Wie ublich, wenn wir einen neuen Typ definieren, brauchen wir jetzt eine Methode, die uns den Inhalt eines Objekts auf dem Bildschirm darstellt. Um ein Paket auszugeben, durchlaufen wir die karten-Liste und geben jede Karte aus:

class Paket:   
...   
def printPaket(self):   
for karte in self.karten:   
print karte

Hier und im Folgenden sollen die Punkte (...) andeuten, dass wir die anderen Methoden der Klasse weggelassen haben.

Als Alternative zu printPaket, konnten wir eine Methode __str__ fur die Paket Klasse schreiben. Der Vorteil der __str__ Methode ist, dass sie flexibler ist. Anstatt nur den Inhalt des Objekts auszugeben, erzeugt sie namlich eine Stringdarstellung, die andere Teile des Programms gegebenenfalls manipulieren konnen, bevor sie ausgegeben wird oder auch fur spatere Verwendung abspeichern.

Hier ist eine Version von __str__ die eine Stringdarstellung von Paket zuruckgibt. Als kleines Schmankerl ordnet sie die Karten in Kaskadenform an, wobei jede Karte um ein Leerzeichen mehr eingeruckt wird, als die vorhergehende.

class Paket:   
...   
def __str__(self):   
s = ""   
for i in range(len(self.karten)):   
s = s + " "*i + str(self.karten[i]) + "\n"   
return s

An diesem Beispiel konnen wir einige Besonderheiten beobachten:

Erstens: Anstatt die Liste self.karten zu durchlaufen und jede Karte einer Variablen zuzuweisen, benutzen wir hier i als Schleifenvariable und als Index fur Elemente der Kartenliste.

Zweitens: Wir benutzen den Multiplikationsoperator fur Strings um jede Karte ein Leerzeichen mehr einzurucken als die letzte. Der Ausdruck " "*i liefert eine Anzahl von Leerzeichen gleich den laufenden Wert des Index i.

Drittens: Anstatt die print Anweisung zu verwenden um die Karten auszugeben, benutzen wir die str Funktion. Ein Objekt als Argument an str zu ubergeben ist gleichwertig mit dem Aufruf der __str__ Methode fur dieses Objekt.

Viertens: wir verwenden die Variable s als eine **Akkumulator-Variable**. Anfangs ist s der Leerstring. Bei jedem Schleifendurchgang wird ein neuer String erzeugt und mit dem alten Wert von s verkettet um den neuen Wert zu erhalten. Wenn die Schleife abgearbeitet ist, enthalt s die vollstandige Stringdarstellung des Pakets, die so aussieht:

>>> paket = Paket()   
>>> print paket   
Treff As   
Treff 2   
Treff 3   
Treff 4   
Treff 5   
Treff 6   
Treff 7   
Treff 8   
Treff 9   
Treff 10   
Treff Bube   
Treff Dame   
Treff Konig   
Pik As   
...

Und so fort. Obwohl das Ergebnis 52 Zeilen aufweist, ist es nur eine lange Zeichenkette, die 52 newline-Zeichen '\n' enthalt.

### 15.7 Das Paket mischen

Wenn ein Paket perfekt gemischt ist, dann kann jede Karte gleich wahrscheinlich an jeder Stelle des Pakets liegen und jede Stelle im Paket enthalt mit gleicher Wahrscheinlichkeit jede Karte.

Um das Paket zu mischen, werden wir die randrange Funktion aus dem random Module verwenden. Mit zwei ganzzahligen Argumenten a und b aufgerufen, gibt randrange ein zufallige ganze Zahl im Bereich a <= x < b zuruck. Da die obere Schranke streng kleiner als b ist, konnen wir die Lange einer Liste als zweiten Parameter verwenden und bekommen damit garantiert einen legalen Index. Der folgende Ausdruck liefert beispielsweise den Index einer Zufallskarte aus einem Paket:

random.randrange(0, len(self.karten))

Ein einfacher Weg, ein Paket zu mischen, ist die Karten zu durchlaufen und dabei jede Karte mit einer zufallig ausgewahlten zu vertauschen. Dabei ist es durchaus moglich, dass eine Karte mit sich selbst vertauscht wird, aber das passt schon. Wurden wir diese Moglichkeit ausschließen, so ware in der Tat nach dem Mischen die Reihenfolge der Karten nicht ganz zufallig:

class Paket:   
...   
def mischen(self):   
import random   
nKarten = len(self.karten)   
for i in range(nKarten):   
j = random.randrange(i, nKarten)   
self.karten[i], self.karten[j] = self.karten[j], self.karten[i]

Anstatt anzunehmen, dass zweiundfunfzig Karten in dem Paket sind, ermitteln wir die aktuelle Lange der Liste und speichern sie in nCards.

Fur jede Karte im Paket wahlen wir eine Zufallskarte aus den Karten aus, die bis jetzt noch nicht gemischt worden sind. Dann vertauschen wir die laufende Karte (i) mit der ausgewahlten Karte (j). Fur das Vertauschen der Karten verwenden wir eine Tupel-Wertzuweisung, wie im Abschnitt [ 9.2](http://python4kids.net/how2think/kap09.htm):

self.karten[i], self.karten[j] = self.karten[j], self.karten[i]

> _Übung: Schreibe diese Codezeile neu, ohne Tupel-Wertzuweisung zu benutzen._

### 15.8 Entfernen von Karten und Geben

Eine weitere nutzliche Methode der Paket Klasse ist entferneKarte. Sie ubernimmt eine Karte als Argument, entfernt sie und gibt wahr (1) zuruck, wenn die Karte im Paket war und falsch (0) andernfalls:

class Paket:   
...   
def entferneKarte(self, karte):   
if karte in self.karten:   
self.karten.remove(karte)   
return 1   
else:   
return 0

Der in Operator gibt wahr zuruck, wenn der erste Operand im zweiten enthalten ist, der eine Liste oder ein Tupel sein muss. Wenn der erste Operand ein Objekt ist, benutzt Python die __cmp__ Methode des Objekts um die Gleichheit mit den Elementen der Liste zu prufen. Weil __cmp__ in der Karte Klasse auf tiefe Gleichheit pruft, uberpruft auch die removeCard Methode auf tiefe Gleichheit.

Um die Karten zu geben, d. h. die Karten an die Spieler zu verteilen, benotigen wir eine Methode, die die oberste Karte entfernt und zuruckgibt. Die Listen-Methode pop ermoglicht etwas derartiges auf bequeme Weise:

class Paket:   
...   
def popKarte(self):   
return self.karten.pop()

Tatsachlich entfernt pop die _letzte_ Karte in der Liste, sodass wir in Wahrheit die Karten des Pakets von unten ausgehend austeilen.

Eine weitere Operation, die wir ziemlich sicher brauchen werden, ist die boole'sche Funktion istLeer, die wahr zuruckgibt, wenn das Paket keine Karten (mehr) enthalt.

class Paket:   
...   
def istLeer(self):   
return (len(self.karten) == 0)

### 15.9 Glossar

**kodieren**
    Eine Menge von Werten durch eine andere Menge von Werten darstellen, indem man eine Abbildung zwischen diesen beiden Mengen konstruiert.
**encode**
    To represent one set of values using another set of values by constructing a mapping between them.

**Klassenattribut**
    Eine Variable, die innerhalb einer Klassendefinition aber außerhalb aller Methoden definiert wird. Auf Klassenattribute kann von jeder Methode der Klasse aus zugegriffen werden. Sie werden von allen Instanzen einer Klasse gemeinsam benutzt.
**class attribute**
    A variable that is defined inside a class definition but outside any method. Class attributes are accessible from any method in the class and are shared by all instances of the class.

**Akkumulator-Variable**
    Eine Variable, die in einer Schleife dazu benutzt wird, eine Folge von Werten zu akkumulieren, beispielsweise durch Verkettung mit einem String oder durch Addition zu einer laufenden Summe.
**accumulator**
    A variable used in a loop to accumulate a series of values, such as by concatenating them onto a string or adding them to a running sum.
  


## Kapitel 16

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [Gregor Lingl](mailto:glingl@aon.at) _

### 16.1 Vererbung

Die Spracheigenschaft, die am haufigsten mit objektorientierter Programmierung in Verbindung gebracht wird, ist **Vererbung**. In Sprachen mit Vererbung besteht die Moglichkeit, eine neue Klasse zu definieren, die eine abgeanderte Version einer bereits existierenden Klasse ist.

Der wichtigste Vorteil von Vererbung ist die Moglichkeit, einer Klasse neue Methoden hinzuzufugen, ohne die existierende Klasse zu verandern. Die Bezeichnung "Vererbung" druckt aus, dass die neue Klasse alle Methoden der existierenden Klasse erbt. In Erweiterterung dieser Methapher, nennt man die existierende Klasse die **Eltern**-Klasse. Die neue Klasse wird manchmal **Kind**-Klasse genannt oder auch "Unterklasse".

Vererbung ist eine machtige Spracheigenschaft. Manche Programme, die ohne Vererbung kompliziert waren, konnen mit ihr einfach und knapp geschrieben werden. Außerdem kann Vererbung die Wiederverwendbarkeit von Code unterstutzen, da man das Verhalten von Eltern-Klassen an neue Anforderungen anpassen kann, ohne sie verandern zu mussen. In manchen Fallen spiegelt die Vererbungsstruktur die naturliche Struktur des Problems wider, sodass das Programm leichter verstandlich wird.

Auf der anderen Seite kann ein Programm durch Vererbung auch schwerer lesbar werden. Wenn eine Methode aufgerufen wird, ist es manchmal nicht klar, wo ihre Definition steht. Der relevante Code kann sogar uber mehrere Module verstreut sein. Außerdem konnen viele Dinge, die man mit Vererbung machen kann, ebenso elegant (oder sogar eleganter) ohne sie gemacht werden. Wenn die naturliche Struktur eines Problems nicht die Verwendung von Vererbung nahe legt, kann es sein, dass dieser Programmierstil mehr Schaden anrichtet als Nutzen bringt.

In diesem Kapitel werden wir vorfuhren, wie Vererbung in einem Programm genutzt werden kann, das das Kartenspiel "Old Maid" simuliert. Eines unserer Ziele wird dabei sein, Code zu schreiben, der weiter verwendet werden konnte, um andere Kartenspiele zu implementieren.

### 16.2 Ein Blatt

Fur nahezu jedes Kartenspiel benotigen wir eine Darstellung eines sogenannten Blatts, also jener Zusammenstellung von Karten, die sich in der Hand eines Spieler befinden. Ein Blatt ist naturlich einem Paket ahnlich. Beide bestehen aus Karten, beide benotigen Operationen wie beispielsweise Entfernen von Karten. Vielleicht ist es auch vorteilhaft ein Paket wie auch ein Blatt mischen zu konnen.

Ein Blatt ist aber auch verschieden von einem Paket. Je nach dem, welches Spiel gespielt wird, mochten wir mit einem Blatt bestimmte Operationen vornehmen, die fur ein Paket keinen Sinn haben. Fur das Poker-Spiel mochten wir zum Beispiel unser Blatt klassifizieren (Straße, Flush, usw.) oder es mit einem anderen Blatt vergleichen. In Bridge mochten wir vielleicht die Punktezahl fur ein Blatt berechnen um eine Ansage zu machen.

Diese Situation legt die Verwendung von Vererbung nahe. Wenn die Klasse Blatt als Unterklasse von Paket konzipiert ist, wird sie alle Methoden von Paket erben und wir konnen dann noch neue Methoden hinzufugen.

In der Klassendefinition folgt auf den Namen der Klasse der Name der Erltern-Klasse, eingeschlossen in runde Klammern:

class Blatt(Paket):   
pass

Diese Anweisung zeigt an, dass die neue Blatt Klasse von der existierenden Paket Klasse erbt.

Der Blatt Konstruktor initialisiert die Attribute fur das Blatt, namlich name und karten. Der String name bezeichnet das Blatt eindeutig, vielleicht durch den Namen des Spielers, der das Blatt halt. Der Name ist ein Parameter mit dem Leerstring als Standardwert und also mit optionalem Argument. karten ist die Liste von Karten, aus denen das Blatt besteht, initialisiert mit der leeren Liste.

class Blatt(Paket):   
def __init__(self, name=""):   
self.karten = []   
self.name = name

Fur fast alle Kartenspiele ist es notig, Karten vom Blatt zu entfernen und zum Blatt hinzuzufugen. Fur die Moglichkeit des Entfernens haben wir schon gesorgt, denn Blatt erbt entferneKarte von Paket. Aber gibKarteDazu mussen wir noch schreiben:

class Blatt(Paket):   
...   
def gibKarteDazu(self,karte) :   
self.karten.append(karte)

Wieder bedeuten die Punkte, dass wir andere Methode weggelassen haben. Die Listen-Methode append fugt die neue Karte an das Ende der Kartenliste an.

### 16.3 Die Karten Geben

Jetzt, da wir die Blatt Klasse haben, mochten wir die Karten des Pakets an die Spieler austeilen, sodass jeder Spieler sein Blatt bekommt. Es ist nicht unmittelbar klar, ob diese Methode geben in die Klasse Blatt oder in die Klasse Paket gehort. Aber weil die Karten eines Pakets gegeben werden und zwar im Allgemeinen an an mehrere Blatt Objekte, ist es wohl naturlicher, sie in die Klasse Paket zu schreiben.

geben sollte einigermaßen allgemein sein, denn verschiedene Spiele werden daran verschiedene Anforderungen haben. Vielleicht mussen wir das ganze Paket auf einmal ausgeben, oder wir wollen nur eine Karte an jedes Blatt geben, und so weiter.

geben hat zwei Parameter. Einen fur eine Blatt-Liste (oder ein Blatt-Tupel), den anderen fur die Gesamtanzahl an Karten, die zu geben sind. Wenn nicht genugend Karten im Paket sind, gibt die Methode alle vorhandenen Karten und stoppt dann.

class Paket :   
...   
def geben(self, blattListe, nKarten=999):   
nblatt = len(blattListe)   
for i in range(nKarten):   
if self.istLeer(): break # break wenn keine Karten mehr da sind   
karte = self.popKarte() # nimm die "oberste" Karte   
blatt = blattListe[i % nblatt] # wer ist der nachste?   
blatt.gibKarteDazu(karte) # gib die Karte zu Blatt

Das zweite Argument, nKarten, ist optional; der Standardwert ist eine große Zahl, was im Endeffekt bedeutet, dass alle Karten des Pakets gegeben werden.

Die Schleifenvariable i lauft von 0 bis nKarten-1. Bei jedem Schleifendurchgang wird dem Paket eine Karte mittels der Methode popKarte entnommen und der Variablen karte zugewiesen.

Der Modulo-Operator (%) gestattet uns Karten im Kreis zu verteilen (immer eine Karte auf einmal fur jedes Blatt). Wenn i so groß wie die Anzahl der Spieler (oder ein Vielfaches der Anzahl der Spieler), also der Elemente der Blatt-Liste ist, dann setzt das Geben beim Beginn der Blatt-Liste fort, weil der Index i % nblatt dann gleich 0 ist.

### 16.4 Ausgabe eines Blatts

Um den Inhalt eines Blatts auszugeben, konnen wir vorteilhafterweise die von Paket geerbten Methoden printDeck und __str__ verwenden. Zum Beispiel so:

>>> paket = Paket()   
>>> paket.mischen()   
>>> blatt = Blatt("Franz")   
>>> paket.geben([blatt], 5)   
>>> print blatt   
Das Blatt von Franz enthalt   
Herz 2   
Herz 3   
Herz 4   
Karo As   
Treff 9

Das ist kein großartiges Blatt, aber es konnte sich auf einen straight flush ausgehen.

Obwohl es vorteilhaft ist, die existierenden Methoden zu erben, ist doch noch eine zusatzliche Information in einem Blatt Objekt, die wir bei der Ausgabe eines Blatts mit ausgeben wollen. Um das zu erreichen, konnen wir auch fur die Klasse Blatt eine __str__ Methode bereit stellen, die die entsprechende Methode der Paket-Klasse uberschreibt.

class Blatt(Paket)   
...   
def __str__(self):   
s = "Das Blatt von " \+ self.name + ":"   
if self.istLeer():   
s = s + " ist leer.\n"   
else:   
s = s + ":\n"   
return s + Paket.__str__(self)

Zunachst ist s ein String der den Namen des Blatts (oder seines Besitzers) enthalt. Wenn das Blatt leer ist, hangt das Programm die Worte ist leer an und gibt s zuruck.

Andernfalls hangt das Programm einen Doppelpunkt an und dann eine Stringdarstellung, die berechnet wird, indem die __str__ Methode der Paket Klasse mit dem Argument self, das ist eben das Blatt, aufgerufen wird.

Es mag zunachst sonderbar erscheinen, self, das auf das aktuelle Blatt verweist, einer Paket Methode als Argument zu ubergeben, aber nur bis man sich daran erinnert, dass ein Blatt eine Art von Paket ist. Blatt-Objekte konnen alles, was Paket-Objekte konnen. Daher ist es ganz legal ein Blatt als erstes Argument fur eine Paket - Methode zu verwenden.

Allgemein gesprochen ist es stets legal, die Instanz einer Unterklasse an der Stelle einer Instanz der Eltern-Klasse zu verwenden.

### 16.5 Die KartenSpiel Klasse

Die KartenSpiel Klasse sorgt fur einige grundlegende Aufgaben, die allen Spielen gemeinsam sind, wie zum Beispiel das Erzeugen und das Mischen des Kartenpakets:

class KartenSpiel:   
def __init__(self):   
self.paket = Paket()   
self.paket.mischen()

Hier ist es erstmals der Fall, dass die Initialisierungsmethode nennenswerte Berechnungen ausfuhrt und nicht nur Attribute mit Werten initialisiert.

Um spezielle Kartenspiele zu implementieren, konnen wir von KartenSpiel erben und spezielle Zuge des neuen Spiels hinzufugen. Als Beispiel werden wir eine Simulation des Kartenspiels "Old Maid" programmieren.

Beim Kartenspiel "Old Maid" ist es das Ziel der Spielerin, die Karten, die in ihrem Blatt sind, los zu werden. Sie tut dies, indem sie entsprechend Rang und Farbe aus den Karten "passende Paare" bildet und ablegt. Zum Beispiel passt Treff 4 zu Pik 4, weil beide Farben schwarz sind. Der Herz Bube passt zum Karo Buben, weil beide rot sind.

Beim Beginn des Spiels wird die Treff Dame aus dem Paket entfernt, sodass die Pik Dame keine passende Partnerkarte hat. Die einundfunfzig verbleibenden Karten werden an die Spieler im Kreis herum verteilt. Nach dem Geben bilden alle Spieler so viele passende Paare, wie moglich und legen diese ab.

Wenn keine weiteren Paare mehr gebildet werden konnen, beginnt das Spiel. Der Reihe nach zieht jeder Spieler eine Karte (zufallig, ohne sie anzusehen) aus dem Blatt seines nachsten linken Nachbarn, der noch Karten hat. Wenn die gezogene Karte mit einer Karte seines Blatts ein passendes Paar bildet, wird dieses Paar abgelegt. Am Ende des Spiels sind alle moglichen passenden Paare abgelegt und es verbleibt nur mehr die Pik Dame in der Hand des Verlierers.

In unserer Computer-Simulation des "Old Maid" Spieles, wird jedes Blatt vom Computer gespielt. Leider gehen dabei einige wichtige Eigenheiten eines realen Spieles verloren. In einem Spiel mit richtigen Karten wird der Spieler mit der "Old Maid" \- der Pik Dame - einige Anstrengungen unternehmen, damit seine rechte Nachbarin diese Karte zieht. Vielleicht wird er diese Karte aus seinem Blatt ein bißchen deutlicher in den Vordergrund schieben, oder vielleicht auch das gerade Gegenteil davon, oder sogar dasselbe doppelt gemoppelt versuchen.

Der Computer zieht dagegen eine Karte des Nachbarn einfach mittels Zufallsgenerator.

### 16.6 Die OldMaidBlatt Klasse

Ein Blatt, mit dem man "Old Maid" spielt, braucht einige Fahigkeiten, die uber die allgemeinen Fahigkeiten eines Blattes hinausgehen. Daher werden wir eine neue Klasse OldMaidBlatt definieren, die eine Unterklasse von Blatt ist und eine zusatzliche Methode entfernePaare hat:

class OldMaidBlatt(Blatt):   
def entfernePaare(self):   
partnerFarbe = {0:1, 1:0, 2:3, 3:2}   
anzahl = 0   
blattKarten = self.karten[:]   
for karte in blattKarten:   
partner = Karte(partnerFarbe[karte.farbe], karte.rang)   
if partner in self.karten:   
self.karten.remove(karte)   
self.karten.remove(partner)   
print "Im Blatt %s ist das Paar %s, %s" % (self.name,karte,partner)   
anzahl = anzahl + 1   
return anzahl

Wir beginnen damit, in einem Dictionary festzulegen welche Farbe zu welcher anderen Farbe passt: Treff zu Pik (0 zu 1), Pik zu Treff (1 zu 0), und so weiter. Eine Zahlvariable, die die Anzahl der Paare im Blatt angeben soll, setzen wir auf 0.

Dann erzeugen wir eine Kopie der Kartenliste. Wir wollen die Karten dieser Kopie in einer Schleife durchlaufen, um jeweils passende Paare aus der originalen Kartenliste des Blatts, self.karten zu entfernen. Dabei wird diese naturlich geandert. Daher wollen wir nicht sie (sondern ihre Kopie) fur die Kontrolle der Schleifendurchlaufe verwenden. Python kann ziemlich durcheinander kommen, wenn es eine Liste durchlauft, die geandert wird.

Fur jede Karte im Blatt erzeugen wir die passende Partnerkarte. Diese hat denselben Rang und Karten eines Paares mussen entweder beide schwarz oder beide rot sein. Die Partnerfarbe liefert uns das Dictionary partnerFarbe. Wenn die Partnerkarte auch in dem Blatt ist, werden beide Karten der Paares entfernt.

Das folgende Beispiel zeigt, wie entfernePaare verwendet wird:

>>> spiel = KartenSpiel()   
>>> blatt = OldMaidBlatt("Franz")   
>>> spiel.paket.geben([blatt], 13)   
>>> print blatt   
Das Blatt von Franz:   
Pik 10   
Pik 6   
Karo Konig   
Pik 3   
Treff 5   
Pik Bube   
Karo Bube   
Treff 3   
Treff 10   
Karo 6   
Treff Dame   
Herz Konig   
Treff 8

>>> blatt.entfernePaare()   
Im Blatt Franz ist das Paar Pik 10, Treff 10   
Im Blatt Franz ist das Paar Karo Konig, Herz Konig   
Im Blatt Franz ist das Paar Pik 3, Treff 3   
3   
>>> print blatt   
Das Blatt von Franz:   
Pik 6   
Treff 5   
Pik Bube   
Karo Bube   
Karo 6   
Treff Dame   
Treff 8

Beachte, dass in der OldMaidBlatt Klasse keine __init__ Methode definiert wird. Wir erben sie von Blatt.

### 16.7 Die OldMaidSpiel Klasse

Nun konnen wir unsere Aufmerksamkeit auf das Spiel selbst lenken. OldMaidSpiel ist eine Unterklasse von KartenSpiel mit einer neuen Methode, genannt spielen, mit einem Parameter fur den beim Aufruf als Argument eine Liste von Spielern eingesetzt wird.

Weil __init__ von KartenSpiel geerbt wird, enthalt ein neues OldMaidSpiel Objekt ein neues gemischtes Paket:

class OldMaidSpiel(KartenSpiel):   
def spielen(self, namen):   
# entferne die Treff Dame   
self.paket.entferneKarte(Karte(0,12))

# erzeuge fuer jeden Spieler ein Blatt   
self.blattListe = []   
for name in namen :   
self.blattListe.append(OldMaidBlatt(name))

# die Karten geben   
self.paket.geben(self.blattListe)   
print "\---------- Die Karten sind gegeben!"   
self.printBlattListe()

# entferne anfangs vorhandene Paare   
paare = self.entferneAllePaare()   
print "\---------- Paare abgelegt - das Spiel beginnt!"   
self.printBlattListe()

# Spiel lauft bis alle 25 Paare abgelegt sind   
amZug = 0   
numBlattListe = len(self.blattListe)   
while matches < 25:   
paare = paare + self.einSpielerSpielt(amZug)   
amZug = (amZug + 1) % numBlattListe

print "\---------- Game is Over"   
self.printBlattListe()

Einige der Schritte, die in diesem Spiel vorkommen, sind dabei in eigene Methoden ausgelagert worde. entferneAllePaare durchlauft die Blattliste und ruft entfernePaare fur jedes Blatt auf:

class OldMaidSpiel(KartenSpiel):   
...   
def entferneAllePaare(self):   
anzahl = 0   
for blatt in self.blattListe:   
anzahl = anzahl + blatt.entfernePaare()   
return anzahl

anzahl ist eine Akkumulator-Variable, die die Anzahlen der in jedem Blatt auftretenden Paare aufsummiert. Am Ende wird diese Summe zuruckgegeben.

> _Übung: schreibe_ printBlattListe _als eine Methode, die_ self.blattListe _durchlauft und jedes Blatt ausgibt._

Wenn die Gesamtzahl der Paare funfundzwanzig erreicht hat, dann sind funfzig Karten von den Spielern abgelegt worden. Das heißt, es ist nur mehr eine Karte ubrig und das Spiel ist beendet.

Die Variable amZug enthalt jeweils die Nummer des Spielers, der gerade am Zug ist. Das Spiel beginnt mit dem Spieler 0 und bei jedem Zug wird diese Variable um eins erhoht. Wenn der Wert von amZug numBlattListe erreicht, sorgt der Modulo-Operator dafur, dass er auf Null zuruckgesetzt wird.

Die Methode einSpielerSpielt hat einen Parameter. Fur ihn wird die Nummer des Spielers, der an der Reihe ist als Argument eingesetzt. Der Ruckgabewert ist die Anzahl der Paare, die von diesem Spieler bei diesem Spielzug abgelegt werden.

class OldMaidSpiel(KartenSpiel):   
...   
def einSpielerSpielt(self, i):   
if self.blattListe[i].istLeer():   
return 0   
nachbar = self.findeNachbarn(i)   
gezogeneKarte = self.blattListe[nachbar].popKarte()   
self.blattListe[i].gibKarteDazu(gezogeneKarte)   
print "Blatt", self.blattListe[i].name, "hat", gezogeneKarte, "gezogen."   
anzahl = self.blattListe[i].entfernePaare()   
self.blattListe[i].mischen()   
return anzahl

Wenn das Blatt eines Spielers oder einer Spielerin leer ist, dann ist er oder sie aus dem Spiel ausgeschieden, daher tut er oder sie gar nichts mehr und gibt 0 zuruck.

Andernfalls muss er den/die erste SpielerIn links von ihm finden, der oder die Karten hat, ein Karte aus seinem/ihrem Blatt ziehen und prufen ob ein neues Paar vorliegt. Bevor sein Nachbar das Spiel fortsetzt, mischt er oder sie sein Blatt, damit die Wahl des nachsten Spielers zufallig ist.

Die Methode findeNachbarn beginnt die Suche mit dem Spieler umittelbar links und fahrt im Kreis fort, bis sie einen Spieler findet, der Karten hat:

class OldMaidSpiel(KartenSpiel):   
...   
def findeNachbarn(self, i):   
numBlattListe = len(self.blattListe)   
for naechste in range(1,numBlattListe):   
nachbar = (i - naechste) % numBlattListe ## original: i + naechste   
if not self.BlattListe[nachbar].istLeer():   
return nachbar

Wurde die Funktion findeNachbarn jemals den ganzen Spielerkreis absuchen, ohne Karten zu finden, so wurde sie None zuruckgeben und einen Fehler irgendwo im Programmablauf verursachen. Glucklicherweise konnen wir zeigen, dass das nicht geschehen kann (so lange das Programmende korrekt ermittelt wird.)

Wir haben die printBlattListe Methode weggelassen. Die kannst du dir selber schreiben.

Die folgende Ausgabe ist von einer gekappten Form des Spiels, wobei nur die obersten funfzehn Karten (Zehner und hohere Karten) an die Spieler ausgegeben werden. Mit diesem kleinen Paket hort das Spiel bereits auf, wenn 7 Paare gefunden wurden (an Stelle von funfundzwanzig).

>>> import karten   
>>> spiel = karten.OldMaidSpiel()   
>>> spiel.spielen(["Anton", "Franz", "Karl"])   
\---------- Die Karten sind gegeben!   
Das Blatt von Anton:   
Pik 10   
Treff 10   
Herz Bube   
Karo 10   
Herz Konig

Das Blatt von Franz:   
Pik Konig   
Karo Dame   
Treff Bube   
Karo Bube   
Treff Konig

Das Blatt von Karl:   
Pik Bube   
Herz Dame   
Herz 10   
Pik Dame   
Karo Konig

Im Blatt Anton ist das Paar Pik 10, Treff 10   
Im Blatt Franz ist das Paar Pik Konig, Treff Konig   
\---------- Paare abgelegt - das Spiel beginnt!   
Das Blatt von Anton:   
Herz Bube   
Karo 10   
Herz Konig

Das Blatt von Franz:   
Karo Dame   
Treff Bube   
Karo Bube

Das Blatt von Karl:   
Pik Bube   
Herz Dame   
Herz 10   
Pik Dame   
Karo Konig

Blatt Anton hat Karo Konig gezogen.   
Im Blatt Anton ist das Paar Herz Konig, Karo Konig   
Blatt Franz hat Karo 10 gezogen.   
Blatt Karl hat Karo Bube gezogen.   
Blatt Anton hat Pik Dame gezogen.   
Blatt Franz hat Pik Dame gezogen.   
Blatt Karl hat Karo 10 gezogen.   
Im Blatt Karl ist das Paar Herz 10, Karo 10   
Blatt Anton hat Pik Bube gezogen.   
Blatt Franz hat Pik Bube gezogen.   
Im Blatt Franz ist das Paar Treff Bube, Pik Bube   
Blatt Karl hat Pik Dame gezogen.   
Blatt Anton hat Herz Dame gezogen.   
Blatt Franz hat Herz Bube gezogen.   
Blatt Karl hat Herz Bube gezogen.   
Im Blatt Karl ist das Paar Karo Bube, Herz Bube   
Blatt Anton hat Pik Dame gezogen.   
Blatt Franz hat Herz Dame gezogen.   
Im Blatt Franz ist das Paar Karo Dame, Herz Dame   
\---------- Das Spiel ist aus!   
Das Blatt von Anton:   
Pik Dame

Das Blatt von Franz ist leer.

Das Blatt von Karl ist leer.

Also verlor Anton.

### 16.8 Glossar

**Vererbung**
    Die Moglichkeit, eine neue Klasse zu definieren, die eine abgeanderte Version einer vorher definierten Klasse ist.
**inheritance**
    The ability to define a new class that is a modified version of a previously defined class.

**Eltern-Klasse**
    Die Klasse, von der eine Kind-Klasse (Unterklasse) erbt.
**parent class**
    The class from which a child class inherits.

**Kind-Klasse**
    Eine neue Klasse, die dadurch erzeugt wird, dass sie von einer existierenden Klasse erbt. Wird auch "Unterllasse" genannt.
**child class**
    A new class created by inheriting from an existing class; also called a "subclass."
  


## Kapitel 17

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [Mike Muller](mailto:pyp@gmx.net) _

### 17.1 Eingeschlossene Verweise

Wir haben Beispiele fur Attribute gesehen, die sich auf andere Objekte beziehen. Diese nennt man **eingeschlossene Verweise** (siehe [Abschnitt ]()). Eine gebrauchliche Datenstruktur, die **verkettete Liste**, nutzt diese Eigenschaft.

Verkettete Listen bestehen aus **Knoten**, wobei jeder Knoten einen Verweis zum nachtsen Knoten der Liste enthalt. Weiterhin enthalt jeder Knoten eine bestimmte Menge Daten, die als **Inhalt** bezeichnet werden.

Eine verkettete Liste wird als **rekursive Datenstruktur** betrachtet, weil sie rekursiv definiert ist.

> Eine Liste ist entweder: 
> 
>   * eine leere Liste, reprasentiert durch None, oder
>   * ein Knoten, der ein Objekt als Inhalt und einen Verweis zu einer verkettete Liste enthalt.

Fur rekursive Datenstrukturen bieten sich rekursive Methoden an.

### 17.2 Die Klasse Knoten

Wie ublich beim Schreiben einer neuen Klasse beginnen wir mit der Intialisierung und der Methode __str__, damit wir die grundlegenden Mechanismen des Erstellens und Anzeigens eines neuen Datentyps testen konnen:

class Knoten:   
def __init__(self, inhalt=None, naechster=None):   
self.inhalt = inhalt   
self.naechster = naechster

def __str__(self):   
return str(self.inhalt)

Wie gewohnlich sind die Parameter bei der Initialisierung optional. Ausgangswerte fur Inhalt und die Verbindung, nachster, sind None.

Die Textreprasentation eines Knotens entspricht einfach der Textreprasentation des Inhalts. Da jeder beliebige Wert an die Funktion str weitergeben werden kann, konnen wir auch jeden Wert in der Liste speichern.

Um die Implementierung bis zu diesem Punkt zu testen, erstellen wir einen Knoten und drucken ihn aus:

>>> knoten = Knoten("Test")   
>>> print knoten   
Test

Um die Sache interessanter zu machen, brauchen wir eine Liste mit mehr als einem Knoten:

>>> knoten1 = Konten(1)   
>>> knoten2 = Konten(2)   
>>> knoten3 = Konten(3)

Es werden drei Knoten erzeugt. Aber wir haben noch keine Liste, da die Knoten noch nicht **verkettetet** sind. Das Zustandsdiagramm sieht so aus:

Um die Knoten zu verbinden, mussen wir den ersten Knoten dazu bringen, auf den zweiten zu verweisen. Der zweite muss wiederum auf den dritten Knoten verweisen:

>>> knoten1.naechster = knoten2   
>>> knoten2.naechster = knoten3

Der Verweis auf den dritten Knoten ist None, was anzeigt, dass es sich um das Ende der Liste handelt. Jetzt sieht das Zustandsdiagramm so aus:

Jetzt weißt du wie man Knoten erstellt und diese zu einer Liste verkettet. Bisher ist aber noch nicht richtig klar geworden warum wir dies tun.

### 17.3 Listen als Sammlungen

Listen sind nutzlich, weil sie eine Moglichkeit darstellen, mehrere Objekte zu einer Einheit zusammenzufassen, die manchmal **Sammlung** genannt wird. Im Beispiel dient der erste Knoten als Verweis fur die gesamte Liste.

Um die Liste als Parameter weiterzugeben, mussen wir nur einen Verweis auf auf den ersten Knoten weitergegeben. Zum Beispiel nimmt die Funktion druckeListe einen einzigen Knoten als Argument. Beginnend vom Kopf der Liste wird jeder Knoten gedruckt, bis das Ende der Liste erreicht ist:

def druckeListe(knoten):   
while knoten:   
print knoten,   
knoten = knoten.naechster   
print

Um diese Methode aufzurufen, geben wir ihr einen Verweis zum ersten Knoten mit:

>>> druckeListe(knoten1)   
1 2 3

Innerhalb von druckeListe haben wir einen Verweis auf den ersten Knoten der Liste, aber es gibt keine Variable, die auf die Anderen Knoten verweist. Wir mussen den Wert naechster von jedem Knoten nutzen, um zum nachsten Knoten zu kommen.

Es ist ublich eine Schleifenvariable wie knoten zu nutzen um hintereinander von einem Knoten zum andern zu verweisen und auf diese Weise eine verkettete Liste zu durchlaufen.

Dieses Diagramm zeigt die Knoten in der Liste und die Werte, die die Variable knoten annimmt:

> _Es ist gebrauchlich, Listen mit eckigen Klammern und mit Kommata zwischen den Elementen zu drucken, also beispielsweise [1, 2, 3]. Ändere bitte druckeListe so ab, das die Liste in diesem Format ausgedruckt wird._

### 17.4 Listen and Rekursion

Viele Listenoperationen bieten sich fur die Nutzung rekursiver Methoden an. Dies verdeutlicht der folgende rekursive Algorithmus zum Ruckwartsdrucken einer Liste:

  1. Teile die Liste in zwei Teile: den ersten Knoten (den Kopf); und den Rest (den Schwanz).
  2. Drucke den Schwanz ruckwarts.
  3. Drucke den Kopf.

Naturlich setzt der zweite Schritt, der rekursive Aufruf, voraus, dass wir eine Moglichkeit haben die Liste ruckwarts zu drucken. Aber wenn wir annehmen, dass der rekursive Aufruf funktioniert Vertrauensvorschuss , konnen wir uns davon uberzeugen, dass dieser Algorithmus funktioniert.

Wir brauchen nun nur einen Basis-Fall und einen Weg, der fur jede beliebige Liste garantiert, das dieser auch erreicht wird. Ausgehend von der rekursiven Definition einer Liste bietet sich als Basis-Fall eine leere Liste dargestellt durch None an:

def druckeRueckwaerts(liste):   
if liste == None: return   
kopf = liste   
schwanz = liste.naechste   
druckeRueckwaerts(schwanz)   
print kopf,

Die erste Zeile fangt den Basis-Fall ab, indem sie nichts tut. Die nachsten beiden Zeilen teilen die Liste in kopf und schwanz. Die letzten beiden Zeilen drucken die Liste aus. Das Komma am Ende der letzten Zeile halt Python davon ab nach jedem Knoten eine neue Zeile zu beginnen.

Wir rufen diese Methode genauso auf wie druckeListe:

>>> druckeRueckwaerts(knoten1)   
3 2 1

Das Ergebnis ist die Liste in umgekehrter Reihenfolge.

Vielleicht fragst du dich warum druckeListe und druckeRueckwaerts Funktionen und keine Methoden der Klasse Knoten sind. Der Grund liegt darin, dass wir None verwenden, um die leere Liste zu reprasentieren und es nicht erlaubt ist Methoden von None aufzurufen. Diese Einschrankung macht das Schreiben einer sauberen objektorientierten Listenverarbeitung umstandlich.

Konnen wir beweisen, dass druckeRueckwaerts immer zu einem Ende kommt? In anderen Worten, erreicht die Methode immer den Basis-Fall? In der Tat ist die Antwort nein. Bestimmte Arten von Listen bringen sie zum Absturz.

### 17.5 Unendliche Listen

Es gibt nichts, was einen Knoten davon abhalten wurde auf einen fruheren Knoten zruckzuverweisen, einschließlich sich selbst. Diese Abbildung zeigt ein Beispiel dafur: eine Liste mit zwei Knoten, von den einer auf sich selbst verweist:

Wenn wir druckeListe mit dieser Liste aufrufen, sind wir in einer unendlichen Schleife gefangen. Wenn wir druckeRueckwaerts aufrufen kommen wir in eine unendliche Rekursion. Dieses Verhalten erschwert das Arbeiten mit unendlichen Listen.

Wie dem auch sei, sie sind gelegentlich nutzlich. So konnen wir z.B. eine Zahl als Liste von Ziffern darstellen und eine unendliche Liste verwenden, um eine sich wiederholende Zahlenfolge abzubilden.

Ungeachtet dessen ist es problematisch, dass wir nicht beweisen konnen, das druckeListe und druckeRueckwaerts immer zu einem Ende kommen. Wir konnen bestenfalls die hypothetische Aussage "Wenn die Liste keine Schleifen enthalt, dann werden diese Methoden zu einem Ende kommen." machen. Diese Art von Behauptung nennt man eine **Vorbedingung**. Sie stellt eine Einschrankung fur einen der Parameter dar und beschreibt das Verhalten der Methode, wenn diese Einschrankung eingehalten wird. Du wirst bald mehr Beispiele dazu sehen.

### 17.6 Das grundlegende Theorem der Mehrdeutigkeit

Du bist vielleicht uber einen Teil der Funktion druckeRueckwaerts gestoplert:

kopf = liste   
schwanz = liste.naechste

Nach der ersten Zuweisung haben kopf und liste den gleichen Typ und den gleichen Wert. Warum haben wir dann eine neue Variable definiert?

Der Grund liegt darin, dass die beiden Variablen unterschiedliche Rollen spielen. Wir konnen uns kopf als Verweis auf einen einzelnen Knoten und liste als Verweis auf den ersten Knoten der Liste vorstellen. Diese "Rollen" sind nicht Teil des Programms sondern existieren nur in der Vorstellung des Programmierers.

Im Allgemeinen konnen wir aus dem bloßen Betrachten eines Programms nicht ableiten, welche Rolle eine Variable spielt. Diese Mehrdeutigkeit kann nutzlich sein. Sie kann aber gleichzeitig ein Programm schwer lesbar machen. Wir verwenden Variablennamen knoten und liste, um zu dokumentieren, wie wir die Varibale verwenden. Manchmal definieren wir zusatzliche Variablen, um Mehrdeutigkeiten zur vermeiden.

Wir hatten druckeRueckwaerts ohne kopf und schwanz schreiben konnen. Dadurch ware die Funktion kurzer aber aber moglicherweise auch schlechter verstandlich geworden:

def druckeRueckwaerts(liste) :   
if liste == None : return   
druckeRueckwaerts(liste.naechster)   
print liste,

Wenn wir uns die beiden Funktionsaufrufe ansehen, mussen wir wissen, dass druckeRueckwaerts seine Argumente als Sammlung und print sein Argument als einzelnes Objekt behandelt.

Das **grundlegende Theorem der Mehrdeutigkeit** beschreibt die Mehrdeutigkeit, die einem Verweis auf einen Knoten innewohnt:

> **Eine Variable, die auf einen Knoten verweist, kann den Knoten entweder als einzelnes Objekt oder als ersten Knoten in einer Liste von Knoten behandeln.**

### 17.7 Listen modifizieren

Es gibt zwei Arten eine verkettete Liste zu modifizieren. Offensichtlich konnen wir den Ladung eines Knoten andern, aber die interessanteren Operationen sind die zum Hinzufugen, Entfernen oder Umsortieren von Knoten.

Als Beispiel schreiben wir eine Methode, die den zweiten Knoten der Liste entfernt und einen Verweis zum entfernten Knoten liefert:

def entferneZweiten(liste):   
if liste == None: return   
erster = liste   
zweiter = liste.naechster   
# lasse den ersten Knoten auf den dritten verweisen   
erster.naechster = zweiter.naechster   
# trenne den zweiten Knoten vom Rest der Liste   
zweiter.naechster = None   
return zweiter

Wir nutzen wieder eine temporare Variable, um den Code lesbarer zu machen. So wird diese Methode verwendet:

>>> druckeListe(knoten1)   
1 2 3   
>>> entfernt = entferneZweiten(knoten1)   
>>> druckeListeList(entfernt)   
2   
>>> druckeListe(knoten1)   
1 3

Dieses Zustandsdiagramm zeigt den Effekt dieser Operation:

Was passiert, wen du diese Methode aufrufst und ihr eine Liste mit nur einem Element, einem so genannten **Singelton** ubergibst? Was passiert, wenn du eine leere Liste als Argument mitgibst? Gibt es eine Vorbedingung fur die Methode? Wenn ja, andere die Methode so, dass sie eine Verletzung dieser Vorbedingung auf sinnvolle Weise behandelt.

### 17.8 Hullen und Helfer

Es ist ist nutzlich eine Listenoperation auf zwei Methoden aufzuteilen. Zum Beispiel konnen wir, um eine Liste im normalen Format ruckwarts zu drucken [3, 2, 1], die druckeRueckwaerts-Methode verwenden. Da das Ergebnis so 3,   
2, aussieht, benotigen wir aber noch eine weitere Methode, um die Klammern und den ersten Knoten zu drucken. Nennen wir diese Methoden druckeRueckwaertsHuebsch:

def druckeRueckwaertsHuebsch(liste) :   
print "[",   
if liste != None :   
kopf = liste   
schwanz = liste.naechster   
druckeRueckwaerts(schwanz)   
print kopf,   
print "]",

Wieder ist es eine gute Idee Methoden wie diese zu kontrollieren, um herauszufinden, ob sie mit Spezialfallen wie leeren Listen or Singeltons umgehen konnen.

Wenn wir diese Methode an einer anderen Stelle im Programm verwenden, rufen wir die Methode druckeRueckwaertsHuebsch direkt, die wiederum die Method druckeRueckwaerts in unserem Auftrag ruft. In diesem Sinne handelt druckeRueckwaertsHuebsch wie eine **Hulle**, die druckeRueckwaerts als **Helfer** nutzt.

### 17.9 Die Klasse VerketteteListe

Mit der Art der Implementierung der Liste sind einige Probleme verbunden, die nicht gleich offensichtlich sind. In Umkehrung von von Ursache und Wirkung werden wir zuerst eine alternative Implementierung vorschlagen und dann das Problem erlautern.

Zuerst definieren wir eine neue Klasse VerketteteListe. Ihre Attribute sind eine Ganzzahl, die die Lange der Liste enthalt und ein Verweis auf den ersten Knoten. Objekte der Klasse VerketteteListe dienen als Zugriffspunkte zum Verandern der Listen mit Knoten-Objekten:

class VerketteteListe :   
def __init__(self) :   
self.laenge = 0   
self.kopf = None

Die VerketteteListe hat eine angenehme Eigenschaft, denn sie bietet einen naturlichen Platz fur Hullfunktionen wie druckeRueckwaertsHuebsch, die in eine Methode der Klasse VerketteteListe umgewandelt werden konnen:

class VerketteteListe:   
...   
def druckeRueckwaertsHuebsch(self):   
print "[",   
if self.kopf != None:   
self.kopf.druckeRueckwaerts()   
print "]",

class Knoten:   
...   
def druckeRueckwaerts(self):   
if self.naechster != None:   
schwanz = self.naechster   
schwanz.druckeRueckwaerts()   
print self.ladung,

Um die Sache ein wenig zu verwirren haben wir druckeRueckwaertsHuebsch umbenannt. Es gibt jetzt zwei Methoden, die druckeRueckwaerts heißen: eine in der Klasse Knoten (dem Helfer); und eine in der Klasse VerketteteListe (der Hulle). Wenn die Hulle self.kopf.druckeRueckwaerts ruft, wird wiederum der Helfer gerufen, da self.kopf ein Knoten-Objekt ist.

Ein weiter Nutzen der Klasse VerketteteListe liegt darin, dass es einfacher wird das erste Element zu entfernen. Zum Beispiel ist addiereErsten eine Methode fur VerketteteListe. Sie nimmt einen Inhalt als Argument und legt es am Beginn der Liste ab:

class VerketteteListe:   
...   
def addiereErsten(self, inhalt):   
knoten = Knoten(inhalt)   
knoten.naechster = self.kopf   
self.kopf = knoten   
self.laenge = self.laenge + 1

Wie gewohnlich solltest du Code wie diesen kontrollieren, ob er die Spezialfalle behandelt. Was passiert zum Beispiel wenn die Liste anfangs leer ist?

### 17.10 Unveranderliche

Manche Listen sind "wohlgeformt"; andere nicht. Zum Beispiel kann eine Liste, die eine Schleife enthalt viele unserer Methoden zum Absturz bringen. Eine Anforderung an eine Liste konnte deshalb sein, dass sie keine Schleifen enthalten darf. Eine andere Forderung bestunde darin, dass der Wert fur laenge im Objekt VerketteteListe gleich der aktuellen Anzahl von Listenknoten sein soll.

Solcherart Anforderungen werden **Unveranderliche** genannt, weil sie idealer Weise fur alle Objekte und fur alle Falle wahr sein sollten. Die Definition von Unveranderlichen fur Objekte ist eine nutzliche Programmierpraxis, weil sie die Korrektheitsprufung von Code vereinfacht, die Integritat von Datenstrukturen kontrolliert und Fehler aufspurt.

Manchmal werden diese Unveranderlichen verletzt, was zu Verwirrung fuhren kann. So ist zum Beispiel in der Mitte von addiereErsten, nach dem Hinzufugen eines Knotens aber noch vor dem Hochzahlen von laenge die Unveranderliche verletzt. Diese Art der Verletzung ist akzeptabel. In der Tat ist es oft unmoglich ein Objekt zu modifizieren, ohne eine Unveranderliche zumindest kurzzeitig zu verletzen. Normalerweise fordern wir, dass jede Methode, die eine Unveranderliche verletzt, diese wieder herstellen muss.

Wenn die Verletzung der Unveranderlich uber einen großeren Codebereich geht, ist es wichtig diese durch Kommentare klar zu verdeutlichen, so dass keine Operation ausgefuhrt wird, die von der Unveranderlichen abhangt.

### 17.11 Glossary

**eingeschlossener Verweis**
    Ein Verweis, der als Attribut eines Objektes gespeichert wird.
**embedded reference**
    A reference stored in an attribute of an object.

**verkettete Liste**
    Eine Datenstruktur, die eine Sammlung unter Nutzung von verketteten Knoten implementiert.
**linked list**
    A data structure that implements a collection using a sequence of linked nodes.

**Knoten**
    Ein Element einer Liste, das typischer Weise als Objekt implementiert ist, das einen Verweis auf ein anders Objet des gleichen Typs enthalt.
**node**
    An element of a list, usually implemented as an object that contains a reference to another object of the same type.

**Inhalt**
    Ein Datenelement, das in einem Knoten enthalten ist.
**cargo**
    An item of data contained in a node.

**Verkettung**
    Ein eingeschlossener Verweise, der als Verkettung zu einem anderen Objekt genutzt wird.
**link**
    An embedded reference used to link one object to another.

**Vorbedingung**
    Eine Aussage, die wahr sein muss, damit eine Methode richtig arbeitet.
**precondition**
    An assertion that must be true in order for a method to work correctly.

**Theorem der grundlegende Mehrdeutigkeit**
    Ein Verweis auf eine Liste kann sowohl als einzelnes Objekt als auch als als erster Knoten in einer Liste von Knoten behandelt werden.
**fundamental ambiguity theorem**
    A reference to a list node can be treated as a single object or as the first in a list of nodes.

**singleton**
    Eine verkettete Liste mit einem einzigen Knoten.
**singleton**
    A linked list with a single node.

**Hulle**
    Eine Methode, die als Mittelsmann zwischen rufender Methode und Helfermethode fungiert. Wodurch diese Methode oft weniger fehleranfallig gerufen werden kann.
**wrapper**
    A method that acts as a middleman between a caller and a helper method, often making the method easier or less error-prone to invoke.

**Helfer**
    Eine Methode, die nicht direkt durch den Rufenden, sondern durch eine andere Methode gerufen wird, um einen Teil der Operationen auszufuhren.
**helper**
    A method that is not invoked directly by a caller but is used by another method to perform part of an operation.

**Unveranderliche**
    Eine Aussage, die fur ein Objekt immer wahr sein sollte (moglicherweise mit Ausnahme wahrend der Modifikation dieses Objektes).
**invariant**
    An assertion that should be true of an object at all times (except perhaps while the object is being modified).
  


## Kapitel 18

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [Mike Muller](mailto:pyp@gmx.net) _

### 18.1 Abstrakte Datentypen

Bisher haben wir nur konkrete Datentypen kennengelernt, bei denen wir vollstandig spezifiziert haben, wie diese implementiert sind. So reprasentiert zum Beispiel die Klasse Karte eine Karte durch 2 Ganzzahlen. Wie wir damals diskutiert hatten, ist das nicht der einzige Weg eine Karte abzubilden; es existieren viele alternative Implementierungen.

Ein **abstrakter Datentyp** (ADT) spezifiziert eine Menge an Operationen, (oder Methoden) und die Semantik der Operationen (was diese tun), er spezifiziert nicht wie diese implementiert sind. Das macht ihn abstrakt.

Warum ist das nutzlich?

  * Die Spezifizierung eines Algorithmus wird einfacher, wenn man die notigen Operationen schon bezeichnen kann, ohne sie sich gleichzeitig um die auszufuhren Operationen kummern zu mussen.
  * Da es typischer Weise viele Wege gibt einen ADT zu implementieren, kann es nutzlich sein einen Algorithmus zu entwickeln, der mit jeder der moglichen Implementierungen verwendet werden kann.
  * Haufig genutzte ADT, wie der in diesem Kapitel behandelte Stack, sind haufig in Standardbibliotheken implementiert. Auf diese Weise konnen sie von vielen Programmieren verwendet werden.
  * Die Operationen auf ADT stellen eine allgemeine Hochsprache fur die Spezifizierung und der Kommunikation uber Algorithmen dar.

Wenn wir uber ADT sprechen, unterscheiden wir haufig zwischen Code, der die ADT nutzt, den so genannten **Clientcode** und dem Code, der den DT implemeniert, dem **Bibliothekscode**.

### 18.2 Der abstrakte Datentyp Stack

In diesem Kapitel werden wir uns mit einem gebrauchlichen ADT, dem **Stack** (eng. Stapel) , beschaftigen. Ein Stack ist eine Sammlung, also eine Datenstruktur, die mehrere Elemente enthalt. Andere Sammlungen, die wir kennengelernt haben sind u.a. Listen und Dictionaries.

Ein ADT wird durch die Operationen, die mit ihm ausgefuhrt werden konnen definiert. Diese werden **Interface** genannt. Das Interface fur den ADT Stack besteht aus diesen Operationen:

Ein Stack wird manchmal als "zuletzt rein zuerst raus" or LIFO (last in, first out) Datenstruktur bezeichnet, weil das Element, das zuletzt hinzugefugt wurde, zuerst entfernt wird.

### 18.3 Implementierung von Stacks mit Python-Listen

Die Listenoperationen, die Python zur Verfugung stellt sind denen ahnlich, die einen Stack definieren. Das Interface entspricht nicht genau dem wie es sein soll, aber wir konnen Code schreiben, der vom ADT Stack zur eingebauten Operationen ubersetzt.

Dieser Code wir **Implementierung** des ADT Stack genannt. Im Allgemeinen ist eine Implementierung eine Menge von Methoden, die den syntaktischen und semantischen Anforderungen eines Interfaces entsprechen.

Hier ist eine Implementierung des ADT Stack unter Nutzung einer Python-Liste:

class Stack :   
def __init__(self) :   
self.items = []

def push(self, item) :   
self.items.append(item)

def pop(self) :   
return self.items.pop()

def istLeer(self) :   
return (self.items == [])

Ein Objekt Stack enthalt ein Attribut, das mit items bezeichnet wird. Bei diesem handelte es sich um eine Liste mit Elementen im Stack. Die Initialisierungsmethode setzt items auf eine leere Liste.

Die Methode push (eng. schieben) hangt ein neues Element an items an und legt es damit auf den Stack. Um ein Element vom Stack zu nehmen nutzt die Methode pop die homonyme [* Note](javascript:fn\('gleichnamige'\)) Listenmethode, mit der das letzte Element der Liste entfernt und zuruckgegeben wird.

Schließlich vergleicht die Methode istLeer items mit einer leeren Liste, um zu kontrollieren, ob der Stack leer ist.

Eine Implementierung wie diese, in der die Methoden aus einfachen Aufrufen existierender Methoden besteht, wird als **Furnier** bezeichnet. Im realen Leben ist ein Furnier eine dunne Schicht Holz guter Qualitat, die bei der Mobelherstellung verwendet wird, um darunter liegendes Holz geringer Qualitat zu verbergen. Informatiker nutzen diese Metapher, um ein kleines Stuck Code zu beschreiben, das die Details einer Implementierung verbirgt und ein einfacheres oder mehr standardisiertes Interface zu bieten.

### 18.4 Legen und Holen

Ein Stack ist ein **generischer Datentyp**, was bedeutet, dass wir jeden beliebigen Typ als Element hinzufugen konnen. Das folgende Beispiel legt zwei Ganzzahlen und einen String auf den Stack:

>>> s = Stack()   
>>> s.push(54)   
>>> s.push(45)   
>>> s.push("+")

Wir konnen die Methoden istLeer und pop nutzen, um alle Elemente zu entfernen und auszudrucken.

while not s.isLeer() :   
print s.pop(),

Der Output sieht so aus + 45 54. Mit anderen Worten haben wir geraden einen Stack verwendet, um die Element ruckwarts zu drucken! Zugegeben ist das nicht das Standardformat zum Drucken einer Liste, aber durch Nutzung eines Stack, war es bemerkenswert einfach umzusetzten.

Du solltest diesen kurzen Code mit der Implementierung von druckeRueckwaerts in [Abschnitt ]() vergleichen.

Es gibt eine naturliche Parallele zwischen der rekursiven Version druckeRueckwaerts und hier den gezeigten Stackalgorithmen. Der Unterschied liegt darin, dass druckeRueckwaerts den Laufzeitstack von Python nutzt, um den Überblick uber die Knoten zu behalten wahrend es durch die Liste geht. Auf dem Ruckweg von der Rekursion werden die Knoten dann ausgedruckt. Der Stackalgorithums macht genau das Gleiche, mit dem Unterschied, dass er anstatt des Laufzeitstacks das Objekt Stack nutzt.

### 18.5 Nutzung eines Stacks fur die Auswertung von Postfix-Notationen

In den meisten Programmiersprachen werden mathematische Ausdrucke mit dem Operator zwischen den beiden Operanden zum Beispiel so 1+2 geschrieben. Dieses Format wird als **Infix-Notation** bezeichnet. Eine Alternative, die von einigen Rechner genutzt wird, wird **Postfix-Notation** genannt. In der Postfix-Notation folgt der Operator den Operanden wie in 1 2 +.

Der Grund, der die Postfix-Notation manchmal nutzlich macht besteht darin, dass es einen naturlichen Weg gibt Ausdrucke in Postfix-Notation mit einem Stack auszuwerten:

  * Beginnend am Anfang des Ausdruck nimm einen Term (Operator oder Operant) nach dem anderen.
    * Wenn der Term ein Operand ist, lege ihn auf den Stack.
    * Wenn der Term ein Operator ist, nimm zwei Operanden vom Stack, fuhre die Operationen an ihnen durch, und lege das Ergebnis zuruck auf den Stack.
  * When wir zum Ende des Ausdruck kommen, sollte genau ein Operand auf dem Stack ubrig sein. Dieser Operand ist das Endergebnis. 

> _Wende diesen Algorithmus als Übung auf den Ausdruck 1 2   
\+ 3 * an._

Dieses Beispiel demonstriert einen der Vorteile der Postfix-Notation es gibt keinen Bedarf Klammern zu verwenden, um die Reihenfolge der Operationen zu kontrollieren. Um das gleiche Ergebnis mit Infix-Notation zu erhalten mussen wir (1 + 2)*   
3 schreiben.

> _Schreibe als Übung einen Ausdruck in Postfix-Notation, der 1 + 2* 3 entspricht._

### 18.6 Parsen

Um den vorangegangen Algorithmus zu implementieren mussen wir durch den String gehen und ihn in Operanden und Operatoren aufteilen. Diese Vorgehen ist ein Beispiel fur das **Parsen**. Die Ergebnisse die individuellen Teile des Stings werden Token genannt. Du erinnerst dich vielleicht an diese Worte aus dem Kapitel 1.

Python bietet eine Methode split sowohl im Modul string als auch im Modul re (regulare Ausdrucke). Die Funktion string.split teilt einen String in eine Liste unter Verwendung eines einzelnen Zeichens als **Trennzeichen**. Zum Beispiel:

>>> import string   
>>> string.split("Jetzt ist die Zeit"," ")   
['Jetzt', 'ist', 'die', 'Zeit']

In diesem Fall wird das Leerzeichen als Trennzeichen gefordert. Der String wird folgerichtig an jedem Leerzeichen geteilt.

Die Funktion re.split bietet mehr, indem wir einen regularen Ausdruck anstatt eines Trennzeichens nutzen konnen. Ein regularer Ausdruck ermoglicht es eine Menge von Strings zu spezifizieren. Zum Beispiel ist [A-z] die Menge aller aller Buchstaben (ohne Umlaute und ß) and [0-9] die Menge aller Ziffern. Der Operator ^ negiert eine Menge, so dass [^0-9] die Menge von allen Zeichen darstellt, die keine Ziffern sind. Das ist genau die Menge, die wir benotigen, um Ausdrucke in Postfix-Notation zu zerteilen:

>>> import re   
>>> re.split("([^0-9])", "123+456*/")   
['123', '+', '456', '*', '', '/', '']

Beachte, dass die Reihenfolge der Argumente von in string.split abweicht; das Trennzeichen kommt vor dem String.

Die resultierende Liste enthalt die Operanden 123 und 456 und die Operatoren * und /. Sie enthalt auch zwei leere Strings, die nach den Operanden eingefugt wurden.

### 18.7 Auswerten von Postfix-Notationen

Zum Auswerten von Ausdrucken in Postfix-Notation werden wir den Parser des vorangegangenen Abschnitts und den Algorithmus des Abschnitts davor nutzen. Um das Ganze einfach zu halten, beginnen wir mit einem Auswerteprogramm, das nur die Operatoren + und * implementiert:

def evalPostfix(expr):   
import re   
tokenList = re.split("([^0-9])", expr)   
stack = Stack()   
for token in tokenList:   
if token == '' or token == ' ':   
continue   
if token == '+':   
sum = stack.pop() + stack.pop()   
stack.push(sum)   
elif token == '*':   
product = stack.pop() * stack.pop()   
stack.push(product)   
else:   
stack.push(int(token))   
return stack.pop()

Die erste Bedingung kummert sich um Leerzeichen und leere Strings. Die nachsten beiden Bedingungen behandeln die Operatoren. Wir nehmen vorerst an, dass alles andern ein Operand sein muss. Naturlich ware es besser auf fehlerhaften Input zu kontrollieren und eine Fehlermeldung auszugeben, aber dazu kommen wir erst spater.

Wir testen das Ganze indem wir den Postfix-Ausdruck (56+47)*2 auswerten:

>>> print evalPostfix ("56 47 + 2 *")   
206

Das is nah genug dran.

### 18.8 Nutzer und Anbieter

Eins der grundlegenden Ziele von ADT ist es Interessen vom Anbieter, der den Code schreibt, der der die ADT implementiert und dem Nutzer, der den ADT anwendet strikt voneinander zu trennen. Der Anbieter kummert sich nur darum, dass die Implementierung in Übereinstimmung mit der Spezifikation des ADT korrekt ist und nicht darum, wie er genutzt werden wird.

Umgekehrt _geht_ der Nutzer _davon aus_, dass die Implementierung korrekt ist und kummert sich nicht um die Details. Wenn du einen der eingebauten Typen von Python nutzt hast du den Luxus ausschließlich als Nutzer zu denken.

Wenn du einen ADT implementierst must du naturlich auch den Nutzercode schreiben, um diesen zu testen. In diesem Falle spielst du beide Rollen, was durchaus verwirrend sein kann. Du solltest dich bemuhen immer zu wissen, welche Rolle du gerade inne hast.

### 18.9 Glossary

**abstrakter Datentyp (ADT)**
    Ein Datentyp (ublicherweise eine Sammlung von Objekten), der durch eine Menge von Operationen definiert ist, aber auf unterschiedlichen Wegen implementiert werden kann.
**abstract data type (ADT)**
    A data type (usually a collection of objects) that is defined by a set of operations but that can be implemented in a variety of ways.

**Interface**
    Eine Menge von Operationen, die einen ADT definieren.
**interface**
    The set of operations that define an ADT.

**implementation**
    Code, der die syntaktischen und semantischen Anforderungen eines Interfaces erfullt.
**implementation**
    Code that satisfies the syntactic and semantic requirements of an interface.

**client**
    Ein Programm (oder dessen Autor), das einen ADT nutzt.
**client**
    A program (or the person who wrote it) that uses an ADT.

**provider**
    Der Code (oder dessen Autor), der einen ADT implementiert.
**provider**
    The code (or the person who wrote it) that implements an ADT.

**Furnier**
    Eine Klassendefinition, die einen ADT mit Methodendefinitionen definiert, die andere Methoden aufrufen und manchmal auch noch einfache Transformationen durchfuhren. Ein Furnier leistet selbst keine wesentliche Arbeit, aber es verbessert oder standardisiert Interface, das vom Nutzern gesehen wird.
**veneer**
    A class definition that implements an ADT with method definitions that are invocations of other methods, sometimes with simple transformations. The veneer does no significant work, but it improves or standardizes the interface seen by the client.

**generische Datenstruktur**
    Eine Art der Datenstruktur, die Daten beliebigen Typs enthalten kann.
**generic data structure**
    A kind of data structure that can contain data of any type.

**Infix-Notation**
    Eine Art des Schreibens mathematischer Ausdrucke, bei der die Operatoren zwischen den Operanden stehen.
**infix**
    A way of writing mathematical expressions with the operators between the operands.

**Postfix-Notation**
    Eine Art des Schreibens mathematischer Ausdrucke, bei der die Operatoren nach den Operanden stehen.
**postfix**
    A way of writing mathematical expressions with the operators after the operands.

**parsen**
    Das Lesen eines Strings mit Zeichen oder Token und das Analysieren seiner grammatikalischen Struktur.
**parse**
    To read a string of characters or tokens and analyze its grammatical structure.

**Token**
    Eine Menge von Zeichen, die zum Zwecke des Parsens als Einheit behandelt werden, so wie die Worte in einer naturlichen Sprache.
**token**
    A set of characters that are treated as a unit for purposes of parsing, such as the words in a natural language.

**Trennzeichen**
    Ein Zeichen, das verwendet wird, um Token voneinander zu trennen. Es ist mit den Interpunktionszeichen in naturlichen Sprachen vergleichbar.
**delimiter**
    A character that is used to separate tokens, such as punctuation in a natural language.
  


## Kapitel 19

_ **Rohubersetzung** \-- bitte um Ruckmeldungen uber Fehler und Unklarheiten an [Mike Muller](mailto:pyp@gmx.net) _

Diese Kapitel behandelt zwei ADT: die Queue und die Prioritatsqueue. In realen Leben ist eine **Queue** (eng. Warteschlange, [kju:]) eine Schlange von Kunden, die eine Dienstleistung warten. In den meisten Fallen, ist der erste Kunde in der Schlange auch der erste der bedient wird. Naturlich gibt es auch Ausnahmen. So werden an Flughafen Kunden, deren Flug bald geht auch aus der Mitte der Schlange nach vorn gerufen. Im Supermarkt lasst ein hoflicher Kunden jemanden mit nur wenigen eingekauften Stucken vor.

Die Regel, die bestimmt wer als nachstes dran ist wird als **Queueing Policy** bezeichnet. Die einfachste Queueing Policy nennt man **FIFO**, das beutet "first-in-first-out" (eng. fur zuerst rein zuerst raus). Die allgemeinste Queueing Policy ist die **Prioritatsqueue**, bei der jedem Kunden eine Prioritat zugewiesen wird, wobei der Kunde mit der hochsten Prioritat zuerst drankommt, unabhangig von der Anstellreihenfolge. Wir nennen das die allgemeinste Policy, weil die Prioritat durch beliebige Kriterien bestimmt werden kann: zu welcher Uhrzeit ein Flug geht; wie viele Lebensmittel ein Kunden im Wagen hat; oder auch wie bedeutend der Kunde ist. Naturlich sind nicht alle Queueing Policies "fair", aber Fairness ist subjektiv.

Der ADT Queue und der ADT Prioritatsqueue haben die gleiche Menge Operationen. Die Differenz besteht in der Semantik der Operationen: eine Queue nutzt die FIFO-Policy, wahrend die Prioritatsqueue (wie der Name andeutet) queueing nach der Prioritat nutzt.

### 19.1 The Queue ADT

Der ADT Queue wird durch folgende Operationen definiert:

### 19.2 Verkettet Queue

Die erste Implementierung des ADT Queue sieht so aus wie sie heißt, **verkette Queue**, da sie aus verketten Knoten-Objekten besteht. Die Klassendefinition sieht so aus:

class Queue:   
def __init__(self):   
self.laenge = 0   
self.kopf = None

def istLeer(self):   
return (self.leange == 0)

def einfuegen(self, inhalt):   
knoten = Knoten(inhalt)   
knoten.naechster = None   
if self.kopf == None:   
# Wenn die Liste leer kommt der neue Knoten zuerst.   
self.kopf = knoten   
else:   
# Finde den letzten Knoten in der Liste.   
letzter = self.kopf   
while letzter.naechster: letzter = letzter.naechster   
# Hange den neuen Knoten an.   
letzter.naechster = knoten   
self.laenge = self.laenge + 1

def entfernen(self):   
inhalt = self.kopf.inhalt   
self.kopf = self.kopf.naechster   
self.laenge = self.laenge - 1   
return inhalt

Die Methoden istLeer entsprcht der gleichnamigen in dem ADT Stack und entfernen ist analog zu entferneZweiten in der Klasse VerketteteListe. Die Methode einfuegen ist neue und etwas komplizierter.

Wir mochten neue Elemente am End e der Liste hinzufugen. Wenn die Queue leer ist, lassen wir einfach kopf auf den neue Knoten zeigen. Andernfalls gehen wird durch die Liste bis zum letzten Knoten und hangen den neuen Knoten am Ende an. Wir konnen den letzten Knoten darin erkenne, dass sein Attribut naechster None ist.

Ein ordentlich aufgebautes Objekt Queue hat zwei Unveranderliche. Der Wert von laenge soll der Anzahl der Knoten in der Queue entsprechen. Weiterhin sollte das Attribut naechster des letzten Knotens den Wert None besitzen. Überzeuge dich davon, dass dies Methode beide Unveranderliche im richtigen Zustand erhalt.

### 19.3 Leistungscharakteristiken

Wenn wir eine Methode rufen kummern wir uns normaler Weise nicht um die Details er Implementierung. Aber es gibt ein "Detail", das wir kennen sollten die Leistungscharakteristiken der Methode. Wie lange dauert es und wie andert sich die Laufzeit, wen die Anzahl der Element in der Sammlung steigt?

Sehen wir uns zuerst entfernen an. Es gibt keine Schleifen oder Funktionsaufrufe, so dass man davon ausgehen kann, dass die die Laufzeit der Methode jedes mal die gleiche ist. Eine solche Methode wird **zeitkonstante Methode** genannt. In der Realitat wird die Methode ein klein wenig schneller sein, wenn die Liste leer ist, da es den Inhalt der Bedingungsabfrage uberspringt. Der Unterschied ist aber nicht significant.

Die Leistung von von einfuegen ist da ganz anders. Im allgemeinen Fall mussen wird die Liste durchlaufen, um das letzte Element zu finden.

Diese Durchlaufen der Liste beansprucht Zeit, die der Lange der Liste Proportional ist. Da die Laufzeit eine linearen Funktion der Lange ist, wird diese Methode als zeitlich linear bezeichnet. Verglichen mit linearer Zeit ist das sehr schlecht.

### 19.4 Verbesserte verkettete Queue

Wir hatten gern eine Implementierung des ADT Queue, die alle Operationen in konstanter Zeit ausfuhren kann. Ein Weg dies zu erreichen ist die Klasse Queue so zu modifizieren, dass sie eine Referenz sowohl zum ersten als auch zum letzten Knoten aufrechterhalt, so wie in der Abbildung dargestellt:

Die Implementierung der Klasse VerbesserteQueue sieht nun so aus:

class VerbesserteQueue:   
def __init__(self):   
self.laenge = 0   
self.kopf = None   
self.letzter = None

def istLeer(self):   
return (self.laenge == 0)

Bis hierhin besteht die einzige Änderung das Attribut letzter. Es wird in den Methoden einfuegen und entfernen verwendet:

class VerbesserteQueue:   
...   
def einfuegen(self, inhalt):   
knoten = Knoten(inhalt)   
knoten.naechster = None   
if self.laenge == 0:   
# Wenn die Liste leer ist, ist der neue Knoten kopf und letzter   
self.kopf = self.letzter = knoten   
else:   
# Finde den letzten Knoten.   
letzter = self.letzter   
# Haenge den neuen Knoten an.   
letzter.naechster = knoten   
self.letzter = knoten   
self.laenge = self.laenge + 1

Da wir mit letzter den letzten Knoten referenzieren, mussen wir nicht mehr suchen. Als Ergebnis ist diese Methode zeitkonstant.

Es ist allerdings ein Preis fur diese Geschwindigkeit zu zahlen. Wir mussen einen Spezialfall in entfernen einfuhren, um letzter auf None zu setzten, wenn der letzte Knoten entfernt wird: There is a price to pay for that speed. We have to add a special case to remove to set last to None when the last node is removed:

class VerbesserteQueue:   
...   
def entfernen(self):   
inhalt = self.kopf.inhalt   
self.kopf = self.kopf.naechster   
self.laenge = self.laenge - 1   
if self.laenge == 0:   
self.letzter = None   
return inhalt

Diese Implementierung ist komplizierter als die der verketten Queue und es ist deshalb auch schwieriger zu zeigen, dass sie korrekt ist. Der Vorteil besteht darin, dass wir unser Ziel erreicht haben sowohl einfuegen als auch entfernen ins zeitkonstante Operationen.

> _Als eine Übung, schreibe eine Implementierung des ADT Queue unter Verwendung einer Python-Liste. Vergleiche die Leistung dieser Implementierung mit der von VerbesseretQueue fur unterschiedliche Langen der Queue._

### 19.5 Prioritatsqueue

Der ADT Prioritatsqueue hat das gleiche Interface wie der ADT Queue aber eine unterschiedliche Semantik. Hier nochmal das Interface:

Der Unterschied in der Semantik liegt, dass von der Queue entfernte Element nicht notwendiger Weise das zuerst hinzugefugte Element ist. Stattdessen ist es das Element, das die hochste Prioritat hat. Was die Prioritaten sind und wie sie miteinander verglichen werden, wird durch die Implementierung der Prioritatsqueue nicht spezifiziert. Es hangt davon ab welche Elemente in der Queue sind.

So konnte zum Beispiel eine alphabetische Reihenfolge gewahlt werden, wenn die Elemente in der Queue Namen sind. Wenn es sich um Bowling-Ergebnisse handelt, ware eine Reihenfolge vom hochsten zum niedrigsten Ergebnis sinnvoll. Wenn es dagegen Golf-Ergebnisse sind ware es eher die umgekehrte Reihenfolge. So lange wir die Element in der Queue vergleichen konnen, konne wir auch das Element mit der hochsten Prioritat finden und entfernen.

Diese Implementierung der Prioritatsqueue hat als Attribut eine Pythonliste, die die Elemente der Queue enthalt.

class PrioritaetsQueue:   
def __init__(self):   
self.items = []

def istLeer(self):   
return self.items == []

def einfuegen(self, item):   
self.items.append(item)

Die Intialisierungsmethode und die Methoden istLeer und einfuegen sind alle Furniere von Listenoperationen. Die einzige interessante Methode ist entfernen:

class PrioritaetsQueue:   
...   
def entfernen(self):   
maxi = 0   
for i in range(1,len(self.items)):   
if self.items[i] > self.items[maxi]:   
maxi = i   
item = self.items[maxi]   
self.items[maxi:maxi+1] = []   
return item

Am Anfang jeder Iteration wird in maxi der Index des großten Elements (mit der hochsten Prioritat) gespeichert, das _bisher_ betrachte wurde. Bei jedem Schleifendurchlauf vergleicht das Programm das i-te Element mit dem Spitzenreiter. Wenn das neue Element großer ist, wird der Wert von maxi auf i gesetzt.

Nachdem das die for-Schliefe vollstandig durchlaufen ist, ist maxi der Index des großten Elements. Dieses Element wird entfernt und als Ergebnis zuruckgegeben.

Testen wir die Implementierung:

>>> q = PrioritaetsQueue()   
>>> q.einfuegen(11)   
>>> q.einfuegen(12)   
>>> q.einfuegen(14)   
>>> q.einfuegen(13)   
>>> while not q.istLeer(): print q.entfernen()   
14 13 12 11

Wenn die Queue einfache Zahlen oder Strings enthalt, werden diese in numerischer oder alphabetischer Reihenfolge entfernt, immer vom hochsten zum niedrigsten. Python kann die großte Zahl oder den großten String finden, da es diese mit den eingebauten Vergleichsoperatoren vergleichen kann.

Wenn die Queue einen Objekttyp enthalt, muss sie eine Methode __cmp__ bereitstellen. Wenn die Methode entfernen den Operator > fur eien Vergleich nutzt, ruft es die Methode __cmp__ fur eins der Elemente auf und ubergibt das anders als Parameter. So lange die Methode __cmp__ richtig funktioniert funktioniert auch die PriorotatsQueue.

### 19.6 Die Klasse Golfer

Als Beispiel fur ein Objekt mit einer ungewohnlichen Definition der Prioritat implementieren wir eine Klasse namens Golfer, die den Überblick uber die Namen und Spielergebnisse der Golfer behalt.Wie gewohnlich starten wir mir der Definition von __init__ und __str__:

class Golfer:   
def __init__(self, name, ergebnis):   
self.name = name   
self.ergebnis= ergebnis

def __str__(self):   
return "%-16s: %d" % (self.name, self.ergebnis)

Die Methode __str__ nutzt den Formatoperator, um Namen und Spielergebnisse in ordentliche Spalten zu schreiben.

Als nachstes definieren wir eine Version von __cmp__ , dei der das niedrigste Ergebnis die hochste Prioritat bekommt. Wie immer gibt __cmp__ 1 als Ergebnis zuruck, wenn self "großer " als other ist und -1 wenn self "kleiner als" other ist oder 0 wenn sie gleich groß sind.

class Golfer:   
...   
def __cmp__(self, other):   
if self.score < other.score: return 1 # less is more   
if self.score > other.score: return -1   
return 0

Jetzt sind wir bereit die Prioritatsqueue mit der Klasse Golfer zu testen:

>>> tiger = Golfer("Tiger Woods", 61)   
>>> phil = Golfer("Phil Mickelson", 72)   
>>> hal = Golfer("Hal Sutton", 69)   
>>>   
>>> pq = PrioritaetsQueue()   
>>> pq.einfuegen(tiger)   
>>> pq.einfuegen(phil)   
>>> pq.einfuegen(hal)   
>>> while not pq.istLeer(): print pq.entfernen()   
Tiger Woods : 61 Hal Sutton : 69 Phil Mickelson : 72

> _als eine Übung, schreibe eine Implementierung des ADT Prioritatsqueue unter Verwendung einer verketteten Liste. Du solltest die Liste immer sortiert halten, so das das Entfernen eine Operation mit konstanter Zeit ist. Vergleiche die Leistung dieser Implementierung mit der der Implementierung mit der Pythonliste._

### 19.7 Glossar

**queue**
    Eine geordnete Menge an Objekten, die auf einen Dienst warten. some kind.
**queue**
    An ordered set of objects waiting for a service of some kind.

**Queue**
    Ein ADT der Operationen ausfuhrt, die auf eiener queue ausgefuhrt wurden. on a queue.
**Queue**
    An ADT that performs the operations one might perform on a queue.

**Queueing Policy**
    Die Regeln, die festlegen, welches Mitglied der Queue als nachstes entfernt wird.
**queueing policy**
    The rules that determine which member of a queue is removed next.

**FIFO**
    "zuerst rein, zuerst raus" ist eine Queueing Policy bei der das erste Mitglied, das ankommt zuerst entfernt wird.
**FIFO**
    "First In, First Out," a queueing policy in which the first member to arrive is the first to be removed.

**Prioritatsqueue**
    Eine Queueing Policy bei der jedes Mitglied eine Prioritat besitzt, die durch externe Faktoren bestimmt wird. Das Mitglied mit der hochsten Prioritat wird als erstes entfernt.
**priority queue**
    A queueing policy in which each member has a priority determined by external factors. The member with the highest priority is the first to be removed.

**Prioritats-Queue**
    Ein ADT, der die Operationen definiert, die auf eine Prioritatsqueue ausgefuhrt werden sollen.
**Priority Queue**
    An ADT that defines the operations one might perform on a priority queue.

**verkettete Queue**
    Eine Implementierung einer Queue unter Verwendung einer verketten Liste.
**linked queue**
    An implementation of a queue using a linked list.

**zeitkonstant**
    Eine Operation, deren Laufzeit nicht von der Große der Datenstruktur abhangig ist.
**constant time**
    An operation whose runtime does not depend on the size of the data structure.

**zeitlich linear**
    Eine Operation dessen Laufzeit eine lineare Funktion der Große der Datenstruktur ist.
**linear time**
    An operation whose runtime is a linear function of the size of the data structure.
