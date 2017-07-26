# C++ Module

_Captured: 2015-10-28 at 08:33 from [www.namespace-cpp.de](http://www.namespace-cpp.de/std/doku.php/kennen/module)_

## Organisation

[Modularisierung](http://www.namespace-cpp.de/std/doku.php/kennen/begriffe) ist eine Technik zum Aufbrechen und Beherrschen der [Komplexitat](http://www.namespace-cpp.de/std/doku.php/kennen/begriffe) von Programmieraufgaben. Die Abgrenzung von Programmteilen kann

Inhaltlich zusammengehorige [Datentypen](http://www.namespace-cpp.de/std/doku.php/kennen/typen) und [Funktionen](http://www.namespace-cpp.de/std/doku.php/kennen/funktion) lassen sich als [Modul](http://www.namespace-cpp.de/std/doku.php/kennen/begriffe) in einer Quelltextdatei bundeln. Vorspanndateien ([Header](http://www.namespace-cpp.de/std/doku.php/kennen/module)) enthalten [Deklarationen](http://www.namespace-cpp.de/std/doku.php/kennen/begriffe) und [Definitionen](http://www.namespace-cpp.de/std/doku.php/kennen/begriffe), z.B. [Funktionsprototypen](http://www.namespace-cpp.de/std/doku.php/kennen/funktion), die zur Nutzung der Moduls notwendig sind. Die Kommunikation mit dem Modul sollte nur uber die dadurch festgelegte [Schnittstelle](http://www.namespace-cpp.de/std/doku.php/kennen/begriffe) erfolgen ([Geheimnisprinzip](http://www.namespace-cpp.de/std/doku.php/kennen/begriffe)).

Bei der Ü[bersetzung](http://www.namespace-cpp.de/std/doku.php/kennen/module) entstehende [Objektdateien](http://www.namespace-cpp.de/std/doku.php/kennen/begriffe) konnen mit [Bibliotheken](http://www.namespace-cpp.de/std/doku.php/kennen/begriffe) zum ausfuhrbaren Programm (Binardatei) zusammengefuhrt werden. Das Modul kann als Objektdatei oder als Bibliothek weitergegeben und in mehrere Programme eingebunden werden, ohne geandert oder neu ubersetzt werden zu mussen. Bibliotheken sind Sammlungen von Objektdateien, die mit einem Bibliothekar oder Archivar genannten Programm zusammengestellt und gepflegt werden. Auf der Ebene der Objektdateien und Bibliotheken sind Programmteile aus unterschiedlichen Programmiersprachen kombinierbar.

Die Dateinamen besitzen je nach System typische Endungen:

Headerdatei 
`*.h, *.hpp, *.hxx`

Quelltext 
`*.cc, *.cpp, *.cxx`

Objektdatei 
`*.o, *.obj`

Bibliothek 
`lib*.a, lib*.so, *.lib, *.dll`

Programm 
`a.out, *.exe`

## Namensraume

Namenskonflikte konnen die Integration von Modulen vereiteln, wenn derselbe Name in ihnen mehrfach definiert wird. Namensraume (Schlusselwort [namespace](http://www.namespace-cpp.de/std/doku.php/kennen/keywords)) begrenzen die Verschmutzung des globalen Namensraumes.

Syntax:

> `namespace` Namensraumbezeichner  
`{`
> 
> `}`

Namensbereiche sind schachtelbar. Ein Namensraum darf mehrfach, auch in verschiedenen Dateien, geoffnet, erweitert und geschlossen werden. Der Namensraum `std` ist jedoch als abgeschlossen zu betrachten. Unbenannte Namensraume kapseln globale Namen, die nur innerhalb eines Moduls sichtbar sein sollen (ohne externe [Bindung](http://www.namespace-cpp.de/std/doku.php/kennen/module)).

Namen sind außerhalb ihres Namensraumes qualifiziert mit dem Namensraumbezeichner anzugeben. Einzelne Namen und ganze Namensraume konnen mit der [using](http://www.namespace-cpp.de/std/doku.php/kennen/keywords)-Anweisung in einen Block oder global importiert werden.
    
    
    std::cout << "Hallo" << std::endl;
     
    using std::cout;
    using namespace std;
    cout << "Hallo" << endl;  // nun ohne std:: nutzbar

## Header

Modulschnittstellen werden vor der Nutzung durch Einbinden von Deklarationsdateien (Header) bekannt gemacht. [Standard-Header](http://www.namespace-cpp.de/std/doku.php/kennen/header) werden in spitzen Klammern angegeben. Eigene Header in Gansefußchen werden zuerst bei den Quelltexten (im aktuellen Projekt-Verzeichnis) gesucht, danach in den Standard-Include-Verzeichnissen.
    
    
    #include <Standardheader>
    #include "mein_header.h"

Syntaktisch korrekte Header konnen in beliebiger Folge angegeben werden. Abhangigkeiten zwischen den Headern sollten in den Headern geregelt werden. Erfordern Deklarationen eines Headers die Kenntnis anderer Schnittstellen, muss dieser die anderen Header einbinden. Eventuelles mehrfaches Einbinden soll nicht zu Übersetzungsfehlern fuhren. Header werden deshalb mit "Include-Wachtern" versehen, deren eindeutige Namen dies durch bedingte Übersetzung verhindern:
    
    
    #ifndef MEIN_HEADER_H
    #define MEIN_HEADER_H
    // ... Abhängigkeiten 
    // ... Deklarationen
    #endif // MEIN_HEADER

## Bindung

In einer Quelltextdatei definierte Funktionen und globale Variablen haben interne Bindung, wenn sie mit dem [Spezifizierer](http://www.namespace-cpp.de/std/doku.php/kennen/typen) [static](http://www.namespace-cpp.de/std/doku.php/kennen/keywords) oder in einem namenlosen [Namensraum](http://www.namespace-cpp.de/std/doku.php/kennen/module) [deklariert](http://www.namespace-cpp.de/std/doku.php/kennen/typen) wurden. Auf Bezeichner mit interner Bindung kann nur innerhalb dieses Quelltextes Bezug genommen werden. Definierte gleichnamige Bezeichner mit interner Bindung existieren in verschiedenen Übersetzungseinheiten unabhangig voneinander.

Alle anderen Funktionen und globalen Variablen haben externe Bindung. Sie durfen im Programm nur ein einziges Mal definiert sein (one definition rule). Funktionen mit externer Bindung konnen aus anderen Quelltexten heraus aufgerufen werden. Lediglich ihr Prototyp muss zum Aufruf bekannt sein. In anderen Dateien definierte globale Variablen mit externer Bindung sind nutzbar, nachdem sie mit dem [Spezifizierer](http://www.namespace-cpp.de/std/doku.php/kennen/typen.htm) [extern](http://www.namespace-cpp.de/std/doku.php/kennen/keywords) angemeldet wurden.
    
    
    extern int global;      // modul1.h
    int minimum(int, int);
    
    
    int global;             // modul1.cpp
     
    int minimum(int x, int y) 
    {
      return x<y ? x : y;
    }
    
    
    #include "modul1.h"
     
    int main()              // main.cpp
    {
      global = minimum(0, 1);
      return global;
    }

Anmerkung: Im allgemeinen sollten globale Variablen vermieden werden. Sie stellen ein Problem bei der Wartung und bei der Parallelisierung von Programmen dar.

Sollen Funktionen aus / in anderen Programmiersprachen aufgerufen werden, muss der Compiler darauf vorbereitet werden, weil unterschiedliche Sprachen unterschiedliche Konventionen der Parameterubergabe, Wertruckgabe und Stackbereinigung haben. Da andere Programmiersprachen bestimmte Merkmale von C++ nicht unterstutzen, sind Überladen u.a. fur solche Funktionen nicht nutzbar.
    
    
    extern "C" int minimum(int, int);

## Übersetzungsprozess
    
    
    <...> \
    *.h    => Präprozessor => Compiler => *.o  => Linker => Programm
    *.cpp /                                |        ^
                                     Archivar <=> Bibliotheken

Ein Programm entsteht in einem mehrstufiger Prozess, auch wenn dieser mit einem einzigen Befehl angestoßen wird.

## Projektverwaltung

### Übersetzen an der Kommandozeile

Ein Programm aus 2 Quelltexten wird erstellt:
    
    
    g++ -o progname main.cpp modul1.cpp

Fehlt die Angabe `-o progname` (o wie output), findet sich die ausfuhrbare Datei als `a.out` ("Assembler Output").

Die Übersetzung einzelner Quelltexte erfolgt mit dem Schalter `-c` (compile):
    
    
    g++ -c main.cpp
    g++ -c modul1.cpp

Die entstehenden Objektdateien werden zum Programm zusammengefuhrt (gelinkt):
    
    
    g++ -o progname main.o modul1.o

Erfordert ein Programm bestimmte Bibliotheken (`lib*.a` oder `lib*.so`), ist beim Linken `-l name` anzugeben, Der `name` ist dabei der nach code|lib| stehende Teil des Bibliotheksnamens, z.B. ist `libm.a` die Mathematik-Bibliothek.
    
    
    g++ prog.cpp -lm

Die Kombination unterschiedlichster Übersetzungsstufen ist erlaubt:
    
    
    g++ -o progname main.cpp modul1.o -lm

### Archivieren in Bibliotheken

Mit dem Archivar `ar` lassen sich Bibliotheken aus Objektdateien zusammenstellen, pflegen und bereinigen. Die Symboltabelle fur den Linker wird mit dem Befehl `ranlib` erzeugt. Zur Dokumentation siehe `man ar` bzw. `man ranlib`.

### Automatisieren mit make

Das Werkzeug `make` unterstutzt die Automatisierung. Mit einem einfachen Kommando
    
    
    make

kann ein Projekt aktualisiert werden. Der Aufruf
    
    
    make test

konnte einen Regressionstest (Fehlerprufung nach Wartung) veranlassen. Mit der Zielangabe
    
    
    make clean

konnten Zwischendateien beraumt werden. Voraussetzung ist eine Datei `Makefile` im (aktuellen) Projektverzeichnis. Beim Anlegen der Datei ist darauf zu achten, dass Tabulatoren auch wirklich als Tabs in der Datei gespeichert werden. Im `Makefile` werden die verschiedenen Ziele definiert.

Syntax:

> Ziel : Tabulator Voraussetzung  
Tabulator Befehl

Zu jedem Ziel wird angegeben, welche Voraussetzungen oder Abhangigkeiten erfullt sein mussen, um die nachfolgenden Befehle ausfuhren zu konnen.

Zuerst versucht `make`, alle Voraussetzungen zu erfullen. Voraussetzungen sind Teilziele oder Dateien. Ist eine Ausgangsdatei junger als die Zieldatei, mussen die zu dem Ziel angegebenen Befehle ausgefuhrt werden. Bei aktuellen Dateien unterbleibt die Ausfuhrung der Befehle, und das Ziel gilt als erfullt. Tritt irgendwo ein Fehler auf, bricht `make` den Aktualisierungsprozess ab.
    
    
    # Kommentar - Beispiel Makefile
     
    all :   progname
     
    progname :      main.o modul1.o
            g++ -o progname main.o modul1.o
     
    main.o :        main.cpp
            g++ -c main.cpp
     
    modul1.o :      modul1.cpp
            g++ -c modul1.cpp
     
    # Regressionstest
    test :  progname input.txt soll.txt
            progname < input.txt > output.txt
            diff output.txt soll.txt
     
    # Saubermachen
    clean :  
            rm *.o output.txt

Der `make`-Aufruf ohne Parameter fuhrt das oberste Ziel aus. Bei unbekannten Zielen gibt sich `make` sprode:
    
    
    make love
    make: *** No rule to make target 'love'. Stop.
