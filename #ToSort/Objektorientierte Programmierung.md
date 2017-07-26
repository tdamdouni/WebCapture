# Objektorientierte Programmierung

_Captured: 2015-09-23 at 12:36 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung)_

Die **objektorientierte Programmierung** (kurz **OOP**) ist ein auf dem Konzept der [Objektorientierung](https://de.m.wikipedia.org/wiki/Objektorientierung) basierendes [Programmierparadigma](https://de.m.wikipedia.org/wiki/Programmierparadigma). Die Grundidee besteht darin, die [Architektur](https://de.m.wikipedia.org/wiki/Softwarearchitektur) einer Software an den [Grundstrukturen](https://de.m.wikipedia.org/wiki/Ontologie) desjenigen Bereichs der Wirklichkeit auszurichten, der die gegebene Anwendung betrifft. Ein Modell dieser Strukturen wird in der [Entwurfsphase](https://de.m.wikipedia.org/wiki/Softwaredesign) aufgestellt. Es enthalt Informationen uber die auftretenden Objekte und deren Abstraktionen, ihre [Typen](https://de.m.wikipedia.org/wiki/Abstrakter_Datentyp). Die Umsetzung dieser Denkweise erfordert die Einfuhrung verschiedener Konzepte, insbesondere [Klassen](https://de.m.wikipedia.org/wiki/Klasse_\(Objektorientierung\)), [Vererbung](https://de.m.wikipedia.org/wiki/Vererbung_\(Programmierung\)), [Polymorphie](https://de.m.wikipedia.org/wiki/Polymorphie_\(Programmierung\)) und spates Binden.

## Definition

Die Definition, was _objektorientierte Programmierung_ ist und im Kern ausmacht, variiert und ist auch Veranderungen unterworfen.

[Alan Kay](https://de.m.wikipedia.org/wiki/Alan_Kay), der Erfinder der Programmiersprache [Smalltalk](https://de.m.wikipedia.org/wiki/Smalltalk_\(Programmiersprache\)) und des Begriffs „object oriented", definierte ihn im Kontext von Smalltalk folgendermaßen:

> _1\. Everything is an object, 2. Objects communicate by sending and receiving messages (in terms of objects), 3. Objects have their own memory (in terms of objects), 4. Every object is an instance of a class (which must be an object), 5. The class holds the shared behavior for its instances (in the form of objects in a program list), 6. To eval a program list, control is passed to the first object and the remainder is treated as its message_

> „1\. Alles ist ein Objekt, 2. Objekte kommunizieren durch das Senden und Empfangen von Nachrichten (welche aus Objekten bestehen), 3. Objekte haben ihren eigenen Speicher (strukturiert als Objekte), 4. Jedes Objekt ist Instanz einer Klasse (welche ein Objekt sein muss), 5. Die Klasse beinhaltet das Verhalten aller ihrer Instanzen (in der Form von Objekten in einer Programmliste), 6. Um eine Programmliste auszufuhren, wird die Ausfuhrungskontrolle dem ersten Objekt gegeben und das Verbleibende als dessen Nachricht behandelt"

Jedoch druckte Alan Kay spater seine Unzufriedenheit uber den von ihm gewahlten Begriff „Objektorientierung" aus, dieser wurde den eigentlichen Kernaspekt aus seiner Sicht, das _Messaging_, zu kurz kommen lassen.[[2]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung) 2003 gab Alan Kay folgende Definition von objektorientierter Programmierung:

> „_OOP to me means only messaging, local retention and protection and hiding of state-process, and extreme late-binding of all things._"

> „OOP bedeutet fur mich nur Messaging, lokales Beibehalten und Schutzen und Verbergen des Prozesszustands sowie [spatestmogliche Bindung](https://de.m.wikipedia.org/wiki/Dynamische_Bindung) aller Dinge."

Der [ISO/IEC 2382-15](https://de.m.wikipedia.org/wiki/Internationale_Organisation_f%C3%BCr_Normung)-Standard von 1999 definiert den Begriff _object-oriented_ dagegen wie folgt:

> „_Pertaining to a technique or a programming language that supports objects, classes, and inheritance._"

> „Bezieht sich auf eine Technik oder Programmiersprache, welche Objekte, Klassen und Vererbung unterstutzt."

Die ISO-Definition gilt inzwischen im Allgemeinen als zu vereinfachend, da auch klassenlose objektorientierte Sprachen existieren und auch der Vererbung inzwischen weniger Bedeutung beigemessen wird als noch in den 1990ern.

## Konzepte

Im Vergleich mit anderen Programmiermethoden verwendet die objektorientierte Programmierung neue, andere Begriffe.

Die einzelnen Bausteine, aus denen ein objektorientiertes Programm wahrend seiner Abarbeitung besteht, werden als Objekte bezeichnet. Die Objekte werden dabei in der Regel auf Basis der folgenden [Paradigmen](https://de.m.wikipedia.org/wiki/Programmierparadigma) konzipiert:

    Jedes Objekt im System kann als ein abstraktes Modell eines _Akteurs_ betrachtet werden, der Auftrage erledigen, seinen Zustand berichten und andern und mit den anderen Objekten im System kommunizieren kann, ohne offenlegen zu mussen, wie diese Fahigkeiten implementiert sind (vgl. [abstrakter Datentyp (ADT)](https://de.m.wikipedia.org/wiki/Abstrakter_Datentyp)). Solche Abstraktionen sind entweder Klassen (in der klassenbasierten Objektorientierung) oder Prototypen (in der prototypbasierten Programmierung). 

    Die Datenstruktur eines Objekts wird durch die [Attribute](https://de.m.wikipedia.org/wiki/Attribut_\(Objekt\)) (auch _Eigenschaften_) seiner Klassendefinition festgelegt. Das Verhalten des [Objekts](https://de.m.wikipedia.org/wiki/Objekt_\(Programmierung\)) wird von den [Methoden](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung) der Klasse bestimmt. Klassen konnen von anderen Klassen _abgeleitet_ werden ([Vererbung](https://de.m.wikipedia.org/wiki/Vererbung_\(Programmierung\))). Dabei erbt die Klasse die Datenstruktur (_Attribute_) und die Methoden von der _vererbenden_ Klasse ([Basisklasse](https://de.m.wikipedia.org/wiki/Basisklasse)).
    Objekte werden durch das Klonen bereits existierender Objekte erzeugt und konnen anderen Objekten als Prototypen dienen und damit ihre eigenen Methoden zur Wiederverwendung zur Verfugung stellen, wobei die neuen Objekte nur die Unterschiede zu ihrem Prototyp definieren mussen. Änderungen am Prototyp werden dynamisch auch an den von ihm abgeleiteten Objekten wirksam.

    Als Datenkapselung bezeichnet man in der Programmierung das Verbergen von Implementierungsdetails. Auf die interne Datenstruktur kann nicht direkt zugegriffen werden, sondern nur uber definierte Schnittstellen. Objekte konnen den internen Zustand anderer Objekte nicht in unerwarteter Weise lesen oder andern. Ein Objekt hat eine Schnittstelle, die daruber bestimmt, auf welche Weise mit dem Objekt interagiert werden kann. Dies verhindert das Umgehen von [Invarianten](https://de.m.wikipedia.org/wiki/Invariante_\(Informatik\)) des Programms.

    Verschiedene Objekte kommunizieren uber einen Nachricht-Antwort-Mechanismus, der zu Veranderungen in den Objekten fuhrt und neue Nachrichtenaufrufe erzeugt. Dafur steht die [Kopplung](https://de.m.wikipedia.org/wiki/Kopplung_\(Softwareentwicklung\)) als Index fur den Grad des Feedbacks.

    Objektvariablen existieren, solange die Objekte vorhanden sind und „verfallen" nicht nach Abarbeitung einer Methode.

    Fahigkeit eines [Bezeichners](https://de.m.wikipedia.org/wiki/Bezeichner), abhangig von seiner Verwendung unterschiedliche Datentypen anzunehmen. Verschiedene Objekte konnen auf die gleiche Nachricht unterschiedlich reagieren. Wird die Zuordnung einer Nachricht zur Reaktion auf die Nachricht erst zur [Laufzeit](https://de.m.wikipedia.org/wiki/Laufzeit_\(Informatik\)) aufgelost, wird dies auch [spate Bindung](https://de.m.wikipedia.org/wiki/Sp%C3%A4te_Bindung) genannt.

    Vererbung heißt vereinfacht, dass eine abgeleitete Klasse die Methoden und Attribute der Basisklasse ebenfalls besitzt, also „erbt". Somit kann die abgeleitete Klasse auch darauf zugreifen. Neue Arten von Objekten konnen auf der Basis bereits vorhandener Objektdefinitionen festgelegt werden. Es konnen neue Bestandteile hinzugenommen werden oder vorhandene uberlagert werden.

Zur besseren Verwaltung gleichartiger Objekte bedienen sich die meisten Programmiersprachen des Konzeptes der Klasse. Klassen sind Vorlagen, aus denen [Instanzen](https://de.m.wikipedia.org/wiki/Instanz_\(Informatik\)) genannte Objekte zur Laufzeit erzeugt werden. Im Programm werden nicht einzelne Objekte, sondern eine Klasse gleichartiger Objekte definiert. Existieren in der gewahlten Programmiersprache keine Klassen oder werden diese explizit unterdruckt, so spricht man zur Unterscheidung oft auch von [objektbasierter Programmierung](https://de.m.wikipedia.org/wiki/Objektbasierte_Programmierung).

Man kann sich die Erzeugung von Objekten aus einer Klasse vorstellen wie das Fertigen von Autos aus dem Konstruktionsplan eines bestimmten Fahrzeugtyps. Klassen sind die Konstruktionsplane fur Objekte.

Die Klasse entspricht in etwa einem komplexen [Datentyp](https://de.m.wikipedia.org/wiki/Datentyp) wie in der prozeduralen Programmierung, geht aber daruber hinaus: Sie legt nicht nur die Datentypen fest, aus denen die mit Hilfe der Klassen erzeugten Objekte bestehen, sie definiert zudem die [Algorithmen](https://de.m.wikipedia.org/wiki/Algorithmus), die auf diesen Daten operieren. Wahrend also zur Laufzeit eines Programms einzelne Objekte miteinander interagieren, wird das Grundmuster dieser Interaktion durch die Definition der einzelnen Klassen festgelegt.

**Beispiel:**

    Die Klasse „Auto" legt fest, dass das Auto vier Reifen, funf Turen, einen Motor und funf Sitze hat.
    Das Objekt „Automodell1" hat schließlich vier Reifen mit dem Durchmesser 60 cm und der Breite 20 cm, funf rote Turen, einen Motor mit 150 kW und funf Ledersitze.
    Ein weiteres Objekt „Automodell2" hat vier Reifen mit dem Durchmesser 40 cm und der Breite 15 cm, funf blaue Turen …
    Beide Objekte sind unterschiedlich, gehoren aber zu der gemeinsamen Klasse Auto.

Die einer Klasse von Objekten zugeordneten Algorithmen bezeichnet man auch als [Methoden](https://de.m.wikipedia.org/wiki/Methode_\(Programmierung\)).

Haufig wird der Begriff _Methode_ synonym zu den Begriffen [Funktion](https://de.m.wikipedia.org/wiki/Funktion_\(Programmierung\)) oder [Prozedur](https://de.m.wikipedia.org/wiki/Prozedur_\(Programmierung\)) aus anderen Programmiersprachen gebraucht. Die Funktion oder Prozedur ist jedoch eher als Implementierung einer Methode zu betrachten. Im taglichen Sprachgebrauch sagt man auch „_Objekt _A _ruft Methode _m _von Objekt _B _auf."_

Eine besondere Rolle spielen Methoden fur die [Kapselung](https://de.m.wikipedia.org/wiki/Datenkapselung_\(Programmierung\)), insbesondere die [Zugriffsfunktionen](https://de.m.wikipedia.org/wiki/Zugriffsfunktion). Spezielle Methoden zur Erzeugung und _Zerstorung_ von Objekten heißen [Konstruktoren beziehungsweise Destruktoren](https://de.m.wikipedia.org/wiki/Konstruktoren_und_Destruktoren).

Methoden konnen [Parameter](https://de.m.wikipedia.org/wiki/Parameter_\(Informatik\)) erhalten, die beim Aufruf ubergeben werden mussen, und einen Ruckgabewert besitzen, den sie am Ende dem Aufrufer zuruckgeben. Beispielsweise hat die Methode _Addition_ die Parameter _Zahl 1_ und _Zahl 2_ und gibt als Ruckgabewert die Summe der Zahlen zuruck.

In vielen objektorientierten Programmiersprachen lasst sich festlegen, welche Objekte eine bestimmte Methode aufrufen durfen. So wird meist zwischen folgenden vier Zugriffsebenen unterschieden, die bereits zur Ü[bersetzungszeit](https://de.m.wikipedia.org/wiki/Kompilierung) gepruft werden.

  1. _Öffentliche_ (_public_) Methoden durfen von allen Klassen aufgerufen werden.
  2. _Geschutzte_ (_protected_) Methoden durfen von Klassen im selben Paket und [abgeleiteten Klassen](https://de.m.wikipedia.org/wiki/Abgeleitete_Klasse) aufgerufen werden.
  3. Methoden auf _Paket-Ebene_ konnen nur von Klassen aufgerufen werden, die sich im selben [Paket](https://de.m.wikipedia.org/wiki/Java-Syntax) befinden - diese Zugriffsebene ist nur bei Programmiersprachen vorhanden, die Pakete bzw. Namespaces kennen.
  4. _Private_ Methoden konnen nur von anderen Methoden derselben Klasse aufgerufen werden.

Analog zu diesen vier Zugriffsebenen sind in der [Unified Modeling Language](https://de.m.wikipedia.org/wiki/Unified_Modeling_Language) (UML) vier Sichtbarkeiten fur [Operationen](https://de.m.wikipedia.org/wiki/Operation_\(UML\)) definiert.

Objekte (Fenster, Buttons, Laufleisten, Menus, …) besitzen verschiedene Eigenschaften (Farbe, Große, Ausrichtung, …). Diese Eigenschaften eines Objekts heißen _Attribute_.

Unter bestimmten Voraussetzungen konnen Algorithmen, die auf den Schnittstellen eines bestimmten Objekttyps operieren, auch mit davon abgeleiteten Objekten zusammenarbeiten.

Geschieht dies so, dass durch Vererbung uberschriebene Methoden an Stelle der Methoden des vererbenden Objektes ausgefuhrt werden, dann spricht man von Polymorphie. Polymorphie stellt damit eine Moglichkeit dar, einer durch ahnliche Objekte ausgefuhrten Aktion einen Namen zu geben, wobei jedes Objekt die Aktion in einer fur das Objekt geeigneten Weise implementiert.

Diese Technik, das so genannte _Overriding_, implementiert aber keine universelle [Polymorphie](https://de.m.wikipedia.org/wiki/Polymorphie_\(Programmierung\)), sondern nur die sogenannte Ad-hoc-Polymorphie.

Die Begriffe der objektorientierten Programmierung haben teilweise unterschiedliche Namen. Folgende Bezeichnungen werden synonym verwendet:

Bezeichnungen in der objektorientierten Programmierung 

Deutscher Begriff Alternativen Englisch

[Abgeleitete Klasse](https://de.m.wikipedia.org/wiki/Abgeleitete_Klasse)
Kindklasse, Unterklasse, Subklasse
child class, subclass

[Attribut](https://de.m.wikipedia.org/wiki/Attribut_\(Objekt\))
Objektvariable, Instanzvariable, Datenelement, Eigenschaft
member, property

[Basisklasse](https://de.m.wikipedia.org/wiki/Basisklasse)
Elternklasse, Oberklasse, Superklasse
parent class, superclass

[Instanz](https://de.m.wikipedia.org/wiki/Instanz_\(Informatik\))
Exemplar, Objekt
instance

[Methode](https://de.m.wikipedia.org/wiki/Methode_\(Programmierung\))
Elementfunktion
method

Statische Methode
Klassenfunktion, Metafunktion
static method

## Objektorientierte Programmiersprachen

Objektorientierte [Programmiersprachen](https://de.m.wikipedia.org/wiki/Programmiersprache) unterstutzen die Programmstrukturierung mit einem speziellen [Datentyp](https://de.m.wikipedia.org/wiki/Datentyp) - dem [Objekt](https://de.m.wikipedia.org/wiki/Objekt_\(Programmierung\)), der die Objektorientierung ermoglicht. Die _rein_ objektorientierten Sprachen, wie [Smalltalk](https://de.m.wikipedia.org/wiki/Smalltalk_\(Programmiersprache\)), folgen dem Prinzip: „Alles ist ein Objekt." Auch elementare Typen wie [Ganzzahlen](https://de.m.wikipedia.org/wiki/Integer_\(Datentyp\)) werden dabei durch Objekte reprasentiert - selbst Klassen sind hier Objekte, die wiederum Exemplare von Metaklassen sind. Die verbreiteten objektorientierten Programmiersprachen, unter anderem [C#](https://de.m.wikipedia.org/wiki/C-Sharp), [C++](https://de.m.wikipedia.org/wiki/C%2B%2B) und [Java](https://de.m.wikipedia.org/wiki/Java_\(Programmiersprache\)), handhaben das Objektprinzip nicht alle so streng. Bei ihnen sind elementare Datentypen keine vollwertigen Objekte, da sie auf Methoden und Struktur verzichten mussen. Sie stellen dem Entwickler auch frei, wie stark er die [Kapselung](https://de.m.wikipedia.org/wiki/Datenkapselung_\(Programmierung\)) objektinterner Daten einhalt.

Die erste bekannte objektorientierte Programmiersprache war [Simula](https://de.m.wikipedia.org/wiki/Simula)-67. Spater wurden die Prinzipien der Kapselung in einer Klassenhierarchie dann in [Smalltalk](https://de.m.wikipedia.org/wiki/Smalltalk_\(Programmiersprache\)) weiter ausgebaut. Mit dem [ANSI](https://de.m.wikipedia.org/wiki/ANSI)/X3.226-1994-Standard wurde [Common Lisp](https://de.m.wikipedia.org/wiki/Common_Lisp)/[CLOS](https://de.m.wikipedia.org/wiki/Common_Lisp_Object_System) zur ersten standardisierten objektorientierten Programmiersprache und mit [ISO](https://de.m.wikipedia.org/wiki/International_Organization_for_Standardization) 8652:1995 wurde [Ada 95](https://de.m.wikipedia.org/wiki/Ada_\(Programmiersprache\)) als erste nach dem internationalen ISO-Standard normierte objektorientierte Programmiersprache festgelegt.

Gangige moderne Programmiersprachen (z. B. [Python](https://de.m.wikipedia.org/wiki/Python_\(Programmiersprache\))) unterstutzen sowohl die OOP als auch den prozeduralen Ansatz, der in den ublichen Programmiersprachen der 1970er und 1980er Jahre wie [Pascal](https://de.m.wikipedia.org/wiki/Pascal_\(Programmiersprache\)), [Fortran](https://de.m.wikipedia.org/wiki/Fortran) oder [C](https://de.m.wikipedia.org/wiki/C_\(Programmiersprache\)) vorherrschte. Im Gegensatz dazu setzt [Smalltalk](https://de.m.wikipedia.org/wiki/Smalltalk-80), die alteste heute noch bedeutsame OOP-Sprache, auf kompromisslose Objektorientierung und hatte damit starken Einfluss auf die Entwicklung popularer OOP-Sprachen, ohne selber deren Verbreitung zu erreichen, weil keine kostengunstig allgemein verfugbare Implementierung angeboten wurde. Auch wenn der Durchbruch der OOP erst in den 1990ern stattfand, wurde die objektorientierte Programmierung bereits Ende der sechziger Jahre mit Simula-67 als Losungsansatz fur die Modularisierung und die Wiederverwendbarkeit von Code entwickelt.

In einigen objektorientierten Programmiersprachen wie [JavaScript](https://de.m.wikipedia.org/wiki/JavaScript), [NewtonScript](https://de.m.wikipedia.org/wiki/NewtonScript) und [Self](https://de.m.wikipedia.org/wiki/Self_\(Programmiersprache\)) wird auf die Deklaration von Klassen ganzlich verzichtet. Stattdessen werden neue Objekte von bestehenden Objekten, den so genannten [Prototypen](https://de.m.wikipedia.org/wiki/Prototypenbasierte_Programmierung), abgeleitet. Die Attribute und Methoden des Prototyps kommen immer dann zum Einsatz, wenn sie im abgeleiteten Objekt nicht explizit uberschrieben wurden. Dies ist vor allem fur die Entwicklung kleinerer Programme von Vorteil, da es einfacher und zeitsparend ist.

In manchen Programmiersprachen, beispielsweise in [Objective C](https://de.m.wikipedia.org/wiki/Objective_C), gibt es zu jeder Klasse ein bestimmtes Objekt ([Klassenobjekt](https://de.m.wikipedia.org/w/index.php?title=Klassenobjekt&action=edit&redlink=1)), das die Klasse zur Laufzeit reprasentiert; dieses Klassenobjekt ist dann auch fur die Erzeugung von Objekten der Klasse und den Aufruf der korrekten Methode zustandig.

Klassen werden in der Regel in Form von [Klassenbibliotheken](https://de.m.wikipedia.org/wiki/Klassenbibliothek) zusammengefasst, die haufig thematisch organisiert sind. So konnen Anwender einer objektorientierten Programmiersprache Klassenbibliotheken erwerben, die zum Beispiel den Zugriff auf Datenbanken ermoglichen.

Die Wortarten einer sprachlichen Problembeschreibung konnen hilfreiche Hinweise dafur geben, eine Objekt-basierte Modellierung zu konzipieren (sogenannte _Verb-Substantiv-Methode_).[[5]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung) Dabei werden Objekte und Klassen in der Regel sprachlich durch [Substantive](https://de.m.wikipedia.org/wiki/Substantiv) beschrieben, wobei Eigennamen auf Objekte und [Appellative](https://de.m.wikipedia.org/wiki/Appellativ) wie _Haus_ und _Tier_ auf Klassen hindeuten.[[6]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung) [Verben](https://de.m.wikipedia.org/wiki/Verb) stehen in der Regel fur Methoden, wobei [Adverbien](https://de.m.wikipedia.org/wiki/Adverb) und Substantive erganzende Charakterisierungen der Methoden geben konnen. Die Werte von Objektattributen entsprechen haufig [Numeralien](https://de.m.wikipedia.org/wiki/Numeral) oder [Adjektiven](https://de.m.wikipedia.org/wiki/Adjektiv).[[7]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung)

Es gibt inzwischen auch Verfeinerungen der objektorientierten Programmierung durch Methoden wie [Entwurfsmuster](https://de.m.wikipedia.org/wiki/Entwurfsmuster), [Design By Contract](https://de.m.wikipedia.org/wiki/Design_By_Contract) und grafische [Modellierungssprachen](https://de.m.wikipedia.org/wiki/Modellierungssprache) wie die [Unified Modeling Language](https://de.m.wikipedia.org/wiki/Unified_Modeling_Language).

Einen immer hoheren Stellenwert nimmt die [aspektorientierte Programmierung](https://de.m.wikipedia.org/wiki/Aspektorientierte_Programmierung) ein, bei der Aspekte von Eigenschaften und Abhangigkeiten beschrieben werden. Erste Ansatze sind beispielsweise in Java mit [J2EE](https://de.m.wikipedia.org/wiki/J2EE) oder der abstrakten Datenhaltung uber Persistenzschichten sichtbar.

## Grenzen der OOP

Das objektorientierte Paradigma hat Vor- und Nachteile je nach Anwendungsfeld in der Softwaretechnik oder konkreter Problemstellung.

### Abbildung von Problemstellungen auf OOP-Techniken

Die OOP kann, wie auch andere Programmierparadigmen, verwendet werden, Probleme aus der realen Welt abzubilden. Als ein typisches Beispiel fur Problemstellungen, die sich einer geschickten Modellierung mit OOP-Techniken entziehen, gilt das [Kreis-Ellipse-Problem](https://de.m.wikipedia.org/wiki/Kreis-Ellipse-Problem).

### Objektorientierte Programmiersprachen und naturliche Sprachen

Objektorientierte Programmiersprachen konnen auch unter sprachwissenschaftlichen Aspekten mit naturlichen Sprachen verglichen werden. OO-Programmiersprachen haben ihren Fokus auf den Objekten, welche sprachlich [Substantive](https://de.m.wikipedia.org/wiki/Substantiv) sind. Die [Verben](https://de.m.wikipedia.org/wiki/Verb) (_Aktionen_) sind sekundar, fest an Substantive gebunden (_gekapselt_) und konnen im Allgemeinen nicht fur sich allein stehen. Bei naturlichen Sprachen und z. B. prozeduralen Sprachen existieren Verben eigenstandig und unabhangig von den Substantiven (Daten), z. B. als Imperativ und [Funktion](https://de.m.wikipedia.org/wiki/Funktion_\(Programmierung\)). Es kann argumentiert werden, dass diese sprachliche Einschrankung in einigen Anwendungsfallen zu unnotig komplizierten Beschreibungen von Problemen aus der realen Welt mit objektorientierten Sprachen fuhrt.[[8]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung)[[9]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung)

Haufig genannte Vorzuge des OOP-Paradigmas sind eine verbesserte [Wartbarkeit](https://de.m.wikipedia.org/wiki/Wartbarkeit) und [Wiederverwendbarkeit](https://de.m.wikipedia.org/wiki/Wiederverwendbarkeit) des statischen Quellcodes.[[10]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung) Hierzu werden jedoch die Kontrollflusse und das dynamische Laufzeitverhalten den Daten/Objekten im Allgemeinen untergeordnet, abstrahiert und weggekapselt. Die [Kontrollflusse](https://de.m.wikipedia.org/wiki/Kontrollfluss) bilden sich nicht mehr fur den Entwickler transparent direkt in den Codestrukturen ab (wie z. B. bei [prozeduralen Sprachen](https://de.m.wikipedia.org/wiki/Prozedurale_Programmierung)), eine Umsetzung in dieser Hinsicht wird dem Compiler uberlassen. Hardware-nahere Sprachen wie das prozedurale [C](https://de.m.wikipedia.org/wiki/C_\(Programmiersprache\)) oder [Assembler](https://de.m.wikipedia.org/wiki/Assemblersprache) bilden den echten Kontrollfluss und das Laufzeitverhalten transparenter ab.[[11]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung) Mit der wachsenden Bedeutung von paralleler Hardware und [nebenlaufigem Code](https://de.m.wikipedia.org/wiki/Parallele_Programmierung) wird jedoch eine bessere Kontrolle und Entwickler-Transparenz der komplexer werdenden Kontrollflusse immer wichtiger - etwas, das schwierig mit OOP zu erreichen ist.[[12]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung)[[13]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung)

Ein haufig genannter Bereich, in dem OOP-Techniken als unzureichend gelten, ist die Anbindung von [relationalen Datenbanken](https://de.m.wikipedia.org/wiki/Relationale_Datenbank). OOP-Objekte lassen sich nicht direkt in allen Aspekten mit relationalen Datenbanken abbilden. Umgekehrt konnen uber OOP die Starken und Fahigkeiten von relationalen Datenbanken ebenfalls nicht vollstandig ausgeschopft werden. Die Notwendigkeit, eine Brucke zwischen diesen beiden Konzeptwelten zu schlagen, ist als [object-relational impedance mismatch](https://de.m.wikipedia.org/wiki/Object-relational_impedance_mismatch) bekannt. Hierzu existieren viele Ansatze, beispielsweise die haufig verwendete [objektrelationale Abbildung](https://de.m.wikipedia.org/wiki/Objektrelationale_Abbildung), jedoch keine allgemeingultige Losung ohne den einen oder anderen Nachteil.[[14]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung)

Die Effektivitat des Laufzeitverhaltens von Anwendungen, die auf OOP-Techniken basieren, wird seit jeher kontrovers diskutiert. Alexander Chatzigeorgiou von der [Universitat Makedonien](https://de.m.wikipedia.org/wiki/Universit%C3%A4t_Makedonien) verglich die Laufzeiteffektivitat und die Energieeffizienz von typischen Algorithmen ([Gauß-Jordan-Algorithmus](https://de.m.wikipedia.org/wiki/Gau%C3%9F-Jordan-Algorithmus), [Trapez-Integration](https://de.m.wikipedia.org/wiki/Trapez-Integration) und [QuickSort](https://de.m.wikipedia.org/wiki/Quicksort)) von [prozeduralen Ansatzen](https://de.m.wikipedia.org/wiki/Prozedurale_Programmierung) und OOP-Techniken, implementiert als C- und C++-Software. Auf dem verwendeten [ARM-Prozessor](https://de.m.wikipedia.org/wiki/ARM-Architektur) ergab sich fur drei Algorithmen im Mittel eine um 48,41 % bessere Laufzeiteffektivitat mit den prozeduralen C-Algorithmusvarianten. Es ergab sich außerdem eine im Mittel um 95,34 % hohere Leistungsaufnahme der C++-Varianten zu den C-Varianten.[[15]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung) Fur Anwendungen auf mobilen Geraten, wie Handys oder MP3-Spielern mit begrenzten Leistungs- und Energiespeichervermogen, sind derartige Unterschiede signifikant, allerdings machen derartige Algorithmen in der Regel nur einen Bruchteil der Applikationen aus. Als Grund fur den Unterschied in Effektivitat und Energieeffizienz werden in dem Artikel generelle Abstraktions-Leistungseinbußen und die deutlich großere Anzahl von Zugriffen auf den Arbeitsspeicher durch OOP-Techniken genannt.

Luca Cardelli untersuchte 1996 fur das [DEC](https://de.m.wikipedia.org/wiki/Digital_Equipment_Corporation) Systems Research Center die Effizienz von OOP-Ansatzen in dem Artikel _Bad Engineering Properties of Object-Oriented Languages_ mit den Metriken Programmablaufgeschwindigkeit (_economy of execution_), Kompilationsgeschwindigkeit (_economy of compilation_), Entwicklungseffizienz fur große und kleine Teams (_economy of small-scale development_ und _economy of large-scale development_) und die Eleganz des Sprachumfangs selbst (_economy of language features_). Er kam zu dem Schluss, dass das objektorientierte Sprachdesign noch viel aus dem prozeduralen Sprachendesign lernen musste, insbesondere im Bereich der guten Modularisierung, der Datenabstraktion und des Polymorphismus, um die hochgesteckten Erwartungen zu erfullen.[[16]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung)

### Keine Erhohung der Produktivitat gegenuber prozeduralen Ansatzen

Eine Studie von Potok et al. aus dem Jahre 1999 zeigte keine signifikanten Produktivitatsunterschiede zwischen OOP und prozeduralen Ansatzen.[[17]](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung)

Die Autoren definieren „Produktivitat" in der Einheit „Entwickelte/Geanderte [Programmzeilen](https://de.m.wikipedia.org/wiki/Lines_of_Code) pro Zeiteinheit" und untersuchen insbesondere den Einfluss von [Code Reuse](https://de.m.wikipedia.org/wiki/Wiederverwendbarkeit) auf diese Metrik. Sie weisen darauf hin, dass eine Konzentration auf Code Reuse unter Umstanden der objektorientierten Programmierung nicht gerecht wird, da sie sich noch auf andere Weisen positiv auf die Produktivitat auswirken konnte (beispielsweise durch ein einfacheres Design).

Die Autoren fuhren mehrere Grunde an, weshalb die Ergebnisse ihrer Studie verzerrt sein konnten:

  * Es konnte sein, dass als „objektorientiert" deklarierte Software in Wirklichkeit prozedural entwickelt wurde.
  * Sie analysierten nur zwei Generationen objektorientierter Software, was ihrer Aussage nach zu wenig sein konnte.
  * Es konnte sein, dass die Qualifikation der verschiedenen Entwicklungsteams unterschiedlich war. Insbesondere ware es moglich, dass die objektorientierte Software von geringer qualifizierten Teams entwickelt wurde.

Die Autoren vertreten die Meinung, diese Punkte trafen nicht zu.
