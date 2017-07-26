# Objekt (Programmierung)

_Captured: 2015-10-24 at 09:51 from [de.wikipedia.org](http://de.wikipedia.org/w/index.php?curid=1293910)_

Ein **Objekt** (auch **Instanz** genannt) bezeichnet in der [objektorientierten Programmierung](https://de.wikipedia.org/wiki/Objektorientierte_Programmierung) (OOP) ein Exemplar eines bestimmten [Datentyps](https://de.wikipedia.org/wiki/Datentyp) oder einer bestimmten [Klasse](https://de.wikipedia.org/wiki/Klasse_\(Programmierung\)) (auch „Objekttyp" genannt). Objekte sind konkrete Auspragungen („Instanzen") eines Objekttyps und werden wahrend der [Laufzeit](https://de.wikipedia.org/wiki/Laufzeit_\(Informatik\)) erzeugt (_Instanziierung_). Sie sind nicht nur zu ihren eigenen Klassen, sondern auch zu den entsprechenden [Basisklassen](https://de.wikipedia.org/wiki/Basisklasse) [zuweisungskompatibel](https://de.wikipedia.org/wiki/Zuweisungskompatibilit%C3%A4t).

## Pragmatische Definition in C[[Bearbeiten](https://de.wikipedia.org/w/index.php?title=Objekt_\(Programmierung\)&action=edit&section=1)]

In [C](https://de.wikipedia.org/wiki/C_\(Programmiersprache\)) gibt es eine sehr pragmatische Definition, was dort als Objekt gilt:

> **object**  
region of data storage in the execution environment, the contents of which can represent values  
Note: When referenced, an object may be interpreted as having a particular type; see 6.3.2.1

C gilt allerdings nicht als objektorientierte Programmiersprache. Die Konzepte der objektorientierten Softwareentwicklung, wie Vererbung, Polymorphie und Kapselung fehlen im Sprachkern und mussen uber selbstdefinierte Funktionen nachgebaut werden. Hierfur existieren verschiedene Bibliotheken von Drittanbietern. Sofern _ausschließlich_ uber diese Funktionen auf ein Objekt zugegriffen wird, erfullt es die Kriterien eines Objektes aus OO-Sicht.

Jedes Objekt hat einen Zustand, ein Verhalten und eine Identitat. Der Zustand des Objektes setzt sich aus seinen Eigenschaften ([Attribute](https://de.wikipedia.org/wiki/Attribut_\(Objekt\))) und Verbindungen zu anderen Objekten zusammen. Das Verhalten des Objektes wird durch die Menge seiner [Methoden](https://de.wikipedia.org/wiki/Methode_\(Programmierung\)) beschrieben. Die Identitat unterscheidet ein Objekt von anderen Objekten, auch wenn diese anderen Objekte den gleichen Zustand und das gleiche Verhalten haben.[[1]](https://de.wikipedia.org/w/index.php)

Durch Konstruktion (siehe auch [Konstruktoren und Destruktoren](https://de.wikipedia.org/wiki/Konstruktoren_und_Destruktoren)) wird aus einer Klasse ein Objekt oder Exemplar ([Instanz](https://de.wikipedia.org/wiki/Instanz_\(Informatik\))) erzeugt. Diese Instanz besitzt dann zur [Laufzeit](https://de.wikipedia.org/wiki/Laufzeit_\(Informatik\)) seinen eigenen [Datentyp](https://de.wikipedia.org/wiki/Datentyp), Eigenschaften und Methoden.

Als Instanziierung bezeichnet man in der [objektorientierten Programmierung](https://de.wikipedia.org/wiki/Objektorientierte_Programmierung) das Erzeugen eines konkreten Objekts einer bestimmten [Klasse](https://de.wikipedia.org/wiki/Klasse_\(Programmierung\)). Wahrend der Instanziierung eines Objekts wird in vielen [Programmiersprachen](https://de.wikipedia.org/wiki/Programmiersprache) ein sogenannter [Konstruktor](https://de.wikipedia.org/wiki/Konstruktoren_und_Destruktoren) ausgefuhrt.

Die Instanz einer Klasse ist ein konkretes Exemplar mit konkreten Auspragungen, mit dem bis zu dessen Zerstorung gearbeitet werden kann. Zum Beispiel konnte es in einem Programm, das mit Autos arbeitet (beispielsweise eine Shopsoftware), eine Klasse „Auto" geben, in der moglichst abstrakt beschrieben wird, welche Eigenschaften ein Auto hat. Wenn in einem solchen Programm ein konkretes Auto, zum Beispiel „Porsche, schwarz, Fahrzeugnummer X", erstellt wird, das dann dem Programm zur weiteren Verwendung zur Verfugung steht, so nennt man dieses nun eine Instanz der Klasse „Auto", und der Vorgang der Objekterstellung heißt Instanziierung.

## Herkunft des Begriffs _Instanz_[[Bearbeiten](https://de.wikipedia.org/w/index.php?title=Objekt_\(Programmierung\)&action=edit&section=4)]

Es gibt die Annahme, dass der heutige Sprachgebrauch „Ein Objekt ist eine Instanz einer Klasse" auf einer Fehlubersetzung der englischen Bezeichnung „instance" = „Beispiel", „Auftreten" oder „Fall" beruht. Als Begrundung dient die Beobachtung, dass Instanzen im juristischen Kontext zueinander immer in einem uber- oder untergeordneten Verhaltnis liegen. Diese Annahme wird jedoch von Kritikern als _falsch_ bezeichnet: Die lateinische [Wurzel](https://de.wikipedia.org/wiki/Wortwurzel) „instantia" = „das Daraufbestehen" enthalt keine solche Hierarchie von Instanzen untereinander. Vielmehr mussen Instanzen auf anderen Dingen bestehen, was Exemplare von Klassen tun (sie bestehen auf Klassen oder genauer, sie werden in der [Programmierung](https://de.wikipedia.org/wiki/Objektorientierte_Programmierung) zur [Laufzeit](https://de.wikipedia.org/wiki/Laufzeit_\(Informatik\)) aus einer [Klasse](https://de.wikipedia.org/wiki/Klasse_\(Programmierung\)) erzeugt). Auch [Goethe](https://de.wikipedia.org/wiki/Johann_Wolfgang_von_Goethe) nutzte den Begriff „Instanz" schon in der Bedeutung „[Exemplar](https://de.wikipedia.org/wiki/Exemplar)": „Eine Instanz aus dem Tierreich der niedrigsten Stufe fuhren wir noch zu mehrerer Anleitung hier vor."[[2]](https://de.wikipedia.org/w/index.php)

### Beispiel[[Bearbeiten](https://de.wikipedia.org/w/index.php?title=Objekt_\(Programmierung\)&action=edit&section=5)]

Der [Quelltext](https://de.wikipedia.org/wiki/Quelltext) zum Objekttyp (die Klasse) „Buch" mit der identifizierenden Eigenschaft „Inventarnummer" (im Falle einer Bibliothek und als einzelne Instanz) enthalt die zugehorigen Eigenschaften (Inventarnummer, Ausleihstatus, Beschaffungsdatum, ...) und die Beschreibung zur Bearbeitung der Eigenschaften (die Methoden, wie z. B. die Veranderung des Ausleihstatus im Falle einer Ausleihe durch einen Kunden).

Ein Objekt ist dann eine reale Auspragung der Klasse, also ein bestimmtes Buch, wie z. B. mit der Inventarnummer 4711. [Objektorientierte Programmiersprachen](https://de.wikipedia.org/wiki/Objektorientierte_Programmierung) erlauben die gleichzeitige Koexistenz verschiedener Objekte, also ein Buch mit der Nummer 4711 und 1234.

Der Zustand eines Objektes (im Sinne der o.g. Definition) ist durch die Werte seiner Attribute vollstandig bestimmt. Unbenannte Attribute sowie Fullbits und -bytes (Padding) tragen dabei nichts zum definierten Zustand des Objektes bei, ihr Inhalt ist undefiniert.

C kennt keine Methoden. Diese mussen uber Funktionen, die einen Zeiger auf das Objekt als ersten Parameter bekommen, nachgebildet werden. Polymorphie wird uber Funktionszeiger, die als Attribute im Objekt gespeichert werden, realisiert.

Die eindeutige Identitat eines Objektes wird durch seine Adresse definiert. Somit muss jedes Objekt eine eigene Adresse haben. Dies wird sichergestellt, indem jede Datenstruktur mindestens 1 Byte Speicher belegt. Wird die Adresse eines Objektes im Programm jedoch nicht benotigt und kann der Compiler dies erkennen, ist es moglich, dass fur dieses Objekt kein Speicher reserviert wird, da die Semantik des Programmes sich hierdurch nicht andert.

## Unterschied zwischen Entitat und Objekt[[Bearbeiten](https://de.wikipedia.org/w/index.php?title=Objekt_\(Programmierung\)&action=edit&section=7)]

Der Begriff „Objekt" ist in der Programmierung mit dem Begriff „[Entitat](https://de.wikipedia.org/wiki/Entit%C3%A4t_\(Informatik\))" verwandt. Die Begriffe Entitat(styp) und Objekt(typ) gelten in ihrer jeweiligen Welt, der Welt der [Datenmodellierung](https://de.wikipedia.org/wiki/Datenmodellierung) und der Welt der [Objektorientierten Programmierung](https://de.wikipedia.org/wiki/Objektorientierte_Programmierung). Sie entsprechen einander, sind aber nicht identisch oder synonym. So hat z. B. Objekt eine Reihe ihm eigener Funktionen, Eigenschaften und Methoden, was bei einer Entitat nicht der Fall ist. Anders ausgedruckt: Objekttyp = programmtechnische Reprasentation des Entitatstyps plus zugehorige Bearbeitungsfunktionen (Methoden).
