# C-Programmierung: Speicherverwaltung

_Captured: 2015-10-08 at 22:28 from [de.m.wikibooks.org](https://de.m.wikibooks.org/wiki/C-Programmierung:_Speicherverwaltung)_

Zum Teil bestimmt der Ort eines Speichers die Zugriffsmoglichkeiten und -geschwindigkeiten, zum Teil wird der Zugriff aber auch von Compiler, Betriebssystem und Hardware kontrolliert.

Mogliche physikalische Speicherorte sind in erster Linie die Register der CPU und der Arbeitsspeicher.

Um eine Variable explizit in einem Register abzulegen, deklariert man eine Variable unter der Speicherklasse register, z.B.:
    
    
    register int var;
    

Von dieser Moglichkeit sollte man allerdings, wenn uberhaupt, nur außerst selten Gebrauch machen, da eine CPU nur wenige Register besitzt, und einige von diesen stets fur die Abarbeitung von Maschinenbefehlen benotigt werden. Die meisten Compiler verfugen zudem uber Optimierungs-Algorithmen, die Variablen in der Regel dann in Registern ablegen, wenn es am sinnvollsten ist.

Die Ablage im Arbeitsspeicher kann grundsatzlich in zwei verschiedenen Bereichen erfolgen.

Zum einen innerhalb einer Funktion, die Variable hat dann zur Ausfuhrungszeit der Funktion eine Position im Stack oder wird vom Optimierungs-Algorithmus in einem Register platziert. Bei erneutem Aufruf der Funktion hat die Variable dann nicht den gleichen Wert, wie zum Abschluss des letzten Aufrufs. Bei rekursivem Aufruf erhalt sie einen neuen, eigenen Speicherplatz, auch mit einem anderen Wert. Deklariert man eine Variable innerhalb einer Funktion ohne weitere Angaben zur Speicherklasse innerhalb eines Funktionskorpers, so gehort sie der Funktion an, z.B:
    
    
    int fun(int var) {
        int var;
    }
    

Zum anderen im allgemeinen Bereich des Arbeitsspeichers, außerhalb des Stacks. Dies erreicht man, indem man die Variable entweder außerhalb von Funktionskorpern, oder innerhalb unter der Speicherklasse static deklariert:
    
    
    int fun(int var) {
        static int var;
    }
    

In Bezug auf Funktionen hat static eine andere Bedeutung, siehe ebenda. Ebenfalls im allgemeinen Arbeitsspeicher landen Variablen, deren Speicherort zur Laufzeit alloziert wird, s.u.

Insbesondere bei eingebetteten Systemen gibt es oft unterschiedliche Bereiche des allgemeinen Adressbereichs des Arbeitsspeichers, hauptsachlich unterschieden nach RAM und ROM. Ob eine Variable in direktem Zugriff nur gelesen oder auch geschrieben werden kann, hangt dann also vom Speicherort ab. Der Speicherort einer Variable wird hier durch zusatzliche Compiler-Direktiven, Pragmas, deklariert, deren Syntax sich zwischen den jeweiligen Compilern stark unterscheidet.

Wenn Speicher fur Variablen benotigt wird, z.B. eine skalare Variable mit
    
    
    int var;
    

oder eine Feld-Variable mit
    
    
    int array[10];
    

deklariert werden, wird auch automatisch Speicher auf dem Stack reserviert.

Wenn jedoch die Große des benotigten Speichers zum Zeitpunkt des Kompilierens noch nicht feststeht, muss der Speicher dynamisch reserviert werden.

Dies geschieht meist mit Hilfe der Funktionen malloc() oder calloc() aus dem Header [stdlib.h](https://de.m.wikibooks.org/wiki/C-Programmierung:_stdlib.h), der man die Anzahl der benotigten Byte als Parameter ubergibt. Die Funktion gibt danach einen void-Zeiger auf den reservierten Speicherbereich zuruck, den man in den gewunschten Typ casten kann. Die Anzahl der benotigten Bytes fur einen Datentyp erhalt man mit Hilfe des sizeof() -Operators.

Beispiel:
    
    
    int *zeiger;
    zeiger = (int *) malloc(sizeof(*zeiger) * 10); /* Reserviert Speicher für 10 Integer-Variablen
                                              und lässt 'zeiger' auf den Speicherbereich zeigen. */
    

Nach dem malloc() sollte man testen, ob der Ruckgabewert NULL ist. Im Erfolgsfall wird malloc() einen Wert ungleich NULL zuruckgeben. Sollte der Wert aber NULL sein ist malloc() gescheitert und das System hat nicht genugend Speicher allokieren konnen. Versucht man, auf diesen Bereich zu schreiben, hat dies ein undefiniertes Verhalten des Systems zur Folge. Folgendes Beispiel zeigt, wie man mit Hilfe einer Abfrage diese Falle umgehen kann:
    
    
    #include <stdlib.h>
    #include <stdio.h>
    int *zeiger;
    
    zeiger = (int *) malloc(sizeof(*zeiger) * 10);           // Speicher anfordern
    if (zeiger == NULL) {
        perror("Nicht genug Speicher vorhanden."); // Fehler ausgeben
        exit(EXIT_FAILURE);                        // Programm mit Fehlercode abbrechen
    }
    free(zeiger);                                  // Speicher wieder freigeben
    

Wenn der Speicher nicht mehr benotigt wird, muss er mit der Funktion free() freigegeben werden, indem man als Parameter den Zeiger auf den Speicherbereich ubergibt.
    
    
    free(zeiger); // Gibt den Speicher wieder frei
    

Wichtig: Nach dem free steht der Speicher nicht mehr zur Verfugung, und jeder Zugriff auf diesen Speicher fuhrt zu undefiniertem Verhalten. Dies gilt auch, wenn man versucht, einen bereits freigegebenen Speicherbereich nochmal freizugeben. Auch ein free() auf einen Speicher, der nicht dynamisch verwaltet wird, fuhrt zu einem Fehler. Einzig ein free() auf einen NULL-Zeiger ist moglich, da hier der ISO-Standard ISO9899:1999 sagt, dass dieses keine Auswirkungen haben darf. Siehe dazu folgendes Beispiel:
    
    
    int *zeiger;
    int *zeiger2;
    int *zeiger3;
    int array[10];
    
    zeiger = (int *) malloc(sizeof(*zeiger) * 10);  // Speicher anfordern
    zeiger2 = zeiger;
    zeiger3 = zeiger++;
    free(zeiger);                           // geht noch gut
    free(zeiger2);                          // FEHLER: DER BEREICH IST SCHON FREIGEGEBEN
    free(zeiger3);                          /* undefiniertes Verhalten, wenn der Bereich 
                                               nicht schon freigeben worden wäre. So ist
                                               es ein FEHLER                             */
    free(array);                            // FEHLER: KEIN DYNAMISCHER SPEICHER
    free(NULL);                             // KEIN FEHLER, ist laut Standard erlaubt
    
