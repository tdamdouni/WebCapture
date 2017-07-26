# C++11-Standard: Was ist neu?

_Captured: 2015-11-09 at 09:42 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/entwicklung/programmiersprachen/c-uebersicht-der-neuerungen-des-standards-in-der-version-11.html)_

![C++11 © Hannes Hafenbrack](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720-405-C__11_d20b42cbae.jpg)

> _C++11 (C) Hannes Hafenbrack_

**C++11 fuhrt anonyme Funktionen ein, sogenannte Lambdas, sowie erleichterte Typbehandlung mit Typinferenz uber das Schlusselwort auto. Letzeres ist daher nun nicht mehr ein Speicherklassen-Specifier. Ein for-Statement erleichtert die Arbeit mit STL-Containern und Arrays. Zudem durfen direkt aufeinanderfolgende spitze Klammern bei Templates benutzt werden: map<int, vector<int>>. Streng typisierte enums (enum class) beseitigen Probleme mit Namenskollisionen. Zudem wurden einige Features aus C11 ubernommen, beispielsweise 64 Bit-Integer mit long long oder Zusicherungen zur Übersetzungszeit mittels static_assert.**

Die aktuelle Fassung von C++ aus dem Juli 2012 ist ISO/IEC 14882:2011, auch bekannt als _C++11_. Sie bietet einige Neuerungen. Ob eine Neuerung die Qualitat von Programmcode aus softwaretechnischer Sicht erhoht, ist ein wichtiges Kriterium. Dazu gehoren etwa Maßnahmen zur Erhohung der Typsicherheit, um mogliche Fehler bereits zur Compilationszeit erkennen zu konnen, wie auch Maßnahmen zur Vereinfachung der Programmierung. Ein weiteres Kriterium kann die Verbesserung der Performance sein. Hier werden die Neuerungen nur kurz angerissen; im Buch "C++: Einfuhrung und professionelle Programmierung", das im Carl Hanser Verlag erscheint, finden Sie ausfuhrliche Erklarungen und Beispiele dazu.

Im alten C++ waren die **doppelten spitzen Klammern** >>, etwa in der Deklaration
    
    
    vector<vector<int>> vvi;

oft ein Ärgernis, weil sie vom Compiler als Shift-Operator interpretiert wurden und er somit eine Fehlermeldung ausgab. Es fehlte ein Leerzeichen dazwischen. C++11 versteht, dass es sich um geschachtelte Templates handelt.

**constexpr** ist ein neues Schlusselwort, das anzeigt, dass ein konstanter Ausdruck bereits zur Compilationszeit berechnet werden kann. Es ersetzt nicht const: Zum Beispiel kann ein const-Wert in einer Funktion von einem ubergebenen Parameter, der erst zur Laufzeit bekannt ist, abhangen.

**auto** kennzeichnete in vergangenen Zeiten Variablen, die auf dem Laufzeitstack abgelegt wurden (lokale "automatische" Variable). In C++11 hilft es, den Typ eines Ausdrucks automatisch zu bestimmen, etwa
    
    
    auto wert = function();

Der Vorteil besteht nicht nur in der Arbeitserleichterung beim Schreiben des Programms, weil man sich nicht um den Typ kummern muss, sondern auch in der verbesserten Wartbarkeit des Programms bei Typanderungen.

Eine **for-Schleife mit Bereichsangabe** (engl. range-for statement) ist eine kurze Variante einer for-Schleife uber alle Werte eines Containers (Vektor, Liste, …). Statt etwa
    
    
    for(size_t i = 0; i < container.size(); ++i) { cout << container[i] << '\n'; }

kann nun geschrieben werden:
    
    
    for(auto wert : container) { cout << wert << '\n'; }

Der Vorteil besteht in der einfacheren Schreibweise und damit der Vermeidung von Schreibfehlern wie "<=" statt "<". Mit der neuen Schreibweise ist eine Überschreitung des gultigen Bereichs (Indexfehler) ausgeschlossen.

**nullptr** ist ein Schlusselwort, das einen Zeiger auf "nichts" (Null-Zeiger) bezeichnet. Im vorhergehenden C++-Standard wurde die Zahl 0 dazu benutzt; dies konnte jedoch zu Typproblemen fuhren. So ist nicht klar, ob ein Aufruf f(0) zur Funktion f(int) gehort oder zur uberladenen Funktion f(void*). f(nullptr) gehort eindeutig zur zweiten genannten Funktion.

**static_assert** pruft bereits zur Compilationszeit, ob eine Bedingung gultig ist. Zum Beispiel kann es im Einzelfall notwendig sein, dass der Typ long mehr Bits als der Typ int haben muss, wenn das Programm korrekt funktionieren soll. In manchen Systemen haben sowohl int wie auch long die Bitbreite 32. Die Anweisung
    
    
    static_assert(sizeof(long) > sizeof(int), "long hat nicht mehr Bits als int!");

pruft das schon zur Compilationszeit, sodass sich ein Test zur Laufzeit mit assert() erubrigt.

**long long** ist ein Typ, der die mogliche Beschrankung von manchen long-Implementationen auf 32 Bit aufhebt, weil er mindestens 64 Bit hat. Damit ist C++ konform zum aktuellen C-Standard.

Bisher wurden Objekte und Arrays auf verschiedene Arten initialisiert. Zur Vereinfachung bietet C++11 eine **einheitliche Syntax fur die Initialisierung** mit Hilfe der geschweiften Klammern an. In diesem Zusammenhang ist die Klasse initializer_list eingefuhrt worden, mit deren Hilfe die in den geschweiften Klammern angegebenen Elemente abgearbeitet werden. Die Anweisung
    
    
    vector vs {"gute", "Idee"};

initialisiert den Vektor mit zwei Strings. Dabei wird der Konstruktor vector(initializer_list) aufgerufen. Die Klasse initializer_list kann auch in eigenen Klassen benutzt werden, wie im Buch gezeigt wird.

Fur Enumerationen (Aufzahlungen) ist das Schlusselwort enum zustandig. Dabei ist die Typumwandlung eines Werts nach int moglich. Im Sinne einer besseren Typsicherheit gibt es nun die Moglichkeit, **enum class** zu schreiben. Mit diesem Typ ist eine versehentliche Typumwandlung nach int nicht mehr moglich. Wenn doch eine Typumwandlung beabsichtigt ist, muss man static_cast bemuhen.

**Lambda-Funktionen** oder -Ausdrucke sind anonyme (unbenannte) Funktionen, die direkt an der Stelle ihrer Verwendung definiert werden. Die Funktionen haben ihren Namen vom sogenannten Lambda-Kalkul, einem formalen System zur Erforschung einiger theoretischer Grundlagen der Mathematik und Informatik. Lambda-Funktionen werden wie ein Funktionsobjekt benutzt, nur dass man sich das Schreiben einer Klasse und der zugehorigen Funktion operator()() sparen kann. Sie sind immer dann sinnvoll, wenn eine Funktion nur ein einziges Mal aufgerufen werden soll. Im Beispiel werden die Elemente des Vektors v nach dem Absolutbetrag sortiert:
    
    
    sort(v.begin(), v.end(), [](int x, int y) { return abs(x) < abs(y);});

Die Kennzeichnung der Funktion einer Klasse mit **override** erlaubt es dem Compiler, eine Warnung bei Schreibfehlern auszugeben (das zweite 'virtual' darf entfallen):
    
    
    class Basis { virtual void func(); }; class Abgeleitet { virtual void Func() override; // versehentlich großgeschrieben: // Fehlermeldung! };

Die Kennzeichnung der Funktion einer Klasse mit **final** verhindert das Überschreiben in einer abgeleiteten Klasse:
    
    
    class Basis { virtual void func() final; }; class Abgeleitet { virtual void func(); // Fehler! func() darf nicht überschrieben werden. };

**Variadic Templates** sind Templates mit einer variablen Anzahl von Template-Parametern. Sie werden unter anderem in der Bibliotheksklasse tuple (Tupel) verwendet. Ein Tupel-Objekt speichert eine feste, zur Compilationszeit festgelegte Anzahl von Elementen auch unterschiedlichen Typs. Wegen der Variadic Templates muss die Anzahl der Elemente in der Deklaration von tuple jedoch nicht bekannt sein. Im Buch werden Variadic Templates beispielhaft bei der Auswertung von Matrix-Rechenoperationen benutzt.

C++ basiert auf der Wertsemantik. C++11 stellt zusatzlich die **Move-Semantik** einschließlich unterstutzender Datentypen und Funktionen zur Verfugung. Programme konnen damit bei einigen Problemstellungen erheblich schneller gemacht werden.

**Der Text ist ein Auszug aus: **

**Ulrich Breymann  
[Der C++-Programmierer: C++ lernen   
- professionell anwenden - Losungen nutzen](http://www.amazon.de/Der-Programmierer-professionell-anwenden-L%C3%B6sungen/dp/3446438947/ref=as_sl_pc_tf_til?tag=wwwinformatik-21&linkCode=w00&linkId=7B6UTP265MRPU5ED&creativeASIN=3446438947)**

3\. uberarbeitete und erweiterte Auflage. 01/2014  
Hanser Fachbuch  
ISBN-13: 978-3446438941
