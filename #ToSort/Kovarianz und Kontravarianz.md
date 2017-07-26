# Kovarianz und Kontravarianz

_Captured: 2015-10-25 at 22:54 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Invarianz_(Informatik))_

In der [objektorientierten Programmierung](https://de.m.wikipedia.org/wiki/Objektorientierte_Programmierung) bedeutet **Kovarianz** und **Kontravarianz**, ob ein Aspekt (d. h. eine Typdeklaration) gleichartig der [Vererbungsrichtung](https://de.m.wikipedia.org/wiki/Vererbung_\(Programmierung\)) (kovariant) oder entgegengesetzt zu dieser (kontravariant) ist. Liegt in der [Unterklasse](https://de.m.wikipedia.org/wiki/Subklasse) keine Änderung gegenuber der [Oberklasse](https://de.m.wikipedia.org/wiki/Basisklasse) vor, wird das als _Invarianz_ bezeichnet.

Den Begriffen liegen die Überlegungen des [Ersetzbarkeitsprinzips](https://de.m.wikipedia.org/wiki/Liskovsches_Substitutionsprinzip) zugrunde: Objekte der Oberklasse mussen durch Objekte einer ihrer Unterklassen ersetzbar sein. Das bedeutet zum Beispiel, dass die [Methoden](https://de.m.wikipedia.org/wiki/Methode_\(Programmierung\)) der Unterklasse mindestens die Parameter akzeptieren mussen, die die Oberklasse auch akzeptieren wurde (Kontravarianz). Die Methoden der Unterklasse mussen ebenfalls Werte zuruckliefern, die mit der Oberklasse vereinbar sind, also nie allgemeineren Typs sind, als der Ruckgabetyp der Oberklasse (Kovarianz).

Die Begriffe Kontravarianz und Kovarianz leiten sich in der Objektorientierung davon ab, dass sich die Typen der betrachteten Parameter mit der Vererbungshierarchie der Ersetzung (kovariant) bzw. entgegengesetzt zur Vererbungshierarchie (kontravariant) verhalten.

Man kann zwischen Ko-, Kontra- und Invarianz bei

  * Methoden 
    * Argumenttypen (die Typen der ubergebenen Parameter)
    * Ergebnistypen (die Typen des Ruckgabewertes)
    * sonstige Signaturerweiterungen (z. B. Exceptiontypen in der _throws_-Klausel in [Java](https://de.m.wikipedia.org/wiki/Java_\(Programmiersprache\)))
  * generischen Klassenparametern

unterscheiden.

Durch das Substitutionsprinzip ergeben sich in der Vererbungshierarchie der objektorientierten Programmierung folgende Auftrittsmoglichkeiten fur Varianzen:

Kontravarianz
Eingabeparameter

Kovarianz
Ruckgabewert und Ausnahmen

Invarianz
[Ein- und Ausgabeparameter](https://de.m.wikipedia.org/wiki/Referenzparameter)

Kovarianz bedeutet, dass die Typhierarchie _mit_ der Vererbungshierarchie der zu betrachtenden Klassen die gleiche Richtung hat. Wenn man also eine ererbte Methode anpassen will, so ist die Anpassung kovariant, wenn der Typ eines Methodenparameters in der Oberklasse ein Obertyp des Parametertyps dieser Methode in der Unterklasse ist.

Wenn die Typhierarchie _entgegengesetzt_ zur Vererbungshierarchie der zu betrachtenden Klassen lauft, so spricht man von Kontravarianz. Wenn die Typen in der Ober- und Unterklasse nicht geandert werden durfen, spricht man von Invarianz.

In der Objektorientierten Modellierung ist es oft wunschenswert, dass auch die Eingabeparameter von Methoden kovariant sind. Dadurch wird allerdings das Substitutionsprinzip verletzt. Das Ü[berladen](https://de.m.wikipedia.org/wiki/%C3%9Cberladen) wird in diesem Fall von den verschiedenen Programmiersprachen unterschiedlich gehandhabt.

  * Kovarianz, Kontravarianz und Invarianz im Überblick
  * ![](http://upload.wikimedia.org/wikipedia/commons/thumb/d/d6/Vererbung_T.svg/120px-Vererbung_T.svg.png)

  * ![](http://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Kontravarianz_Vererbung.svg/120px-Kontravarianz_Vererbung.svg.png)

  * ![](http://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Kovarianz_Vererbung.svg/120px-Kovarianz_Vererbung.svg.png)

  * ![](http://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Invarianz_Vererbung.svg/120px-Invarianz_Vererbung.svg.png)

  * ![TypunsichereKovarianz Vererbung.svg](http://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/TypunsichereKovarianz_Vererbung.svg/113px-TypunsichereKovarianz_Vererbung.svg.png)

> _[TypunsichereKovarianz Vererbung.svg](https://de.m.wikipedia.org/wiki/Datei:TypunsichereKovarianz_Vererbung.svg)_

Grundsatzlich gilt in Programmiersprachen wie C++, Java und C#, dass Variablen und Parameter kontravariant sind, wahrend Methodenruckgaben kovariant sind:

Beispiel in C# 

Kontravarianz Kovarianz Invarianz
    
    
    public abstract class Animal
    {
       public abstract string Name { get; }
    }
    
    public class Giraffe : Animal
    {
       public Giraffe(string name)
       {
          Name = name;
       }
       public string Name { get; private set; }
    }
    
    public string GetNameFromAnimal(Animal animal)
    {
       return animal.Name;
    }
    
    [Test]
    public void Contravariance()
    {
        var herby = new Giraffe("Herby");
        // kontravariante Umwandlung von Giraffe nach Animal
        var name = GetNameFromAnimal(herby); 
        Assert.AreEqual("Herby", name);
    }
    
    
    
    public abstract class Animal
    {
       public abstract string Name { get; }
    }
    
    public class Giraffe : Animal
    {
       public Giraffe(string name)
       {
          Name = name;
       }
       public string Name { get; private set; }
    }
    
    public string GetNameFromGiraffe(Giraffe animal)
    {
       return animal.Name;
    }
    
    [Test]
    public void Covariance()
    {
        var herby = new Giraffe("Herby");
        // kovariante Umwandlung des Rückgabewerts von String nach Object
        object name = GetNameFromGiraffe(herby);
        Assert.AreEqual((object)"Herby", name);
    }
    
    
    
    public abstract class Animal
    {
       public abstract string Name { get; }
    }
    
    public class Giraffe : Animal
    {
       public Giraffe(string name)
       {
          Name = name;
       }
       public string Name { get; private set; }
    }
    
    public string GetNameFromGiraffe(Giraffe animal)
    {
       return animal.Name;
    }
    
    [Test]
    public void Invariance()
    {
        var herby = new Giraffe("Herby");
        // keine Umwandlung der Datentypen
        string name = GetNameFromGiraffe(herby);
        Assert.AreEqual("Herby", name);
    }
    

Im Folgenden wird verdeutlicht, wann die Typsicherheit gewahrleistet bleibt, wenn man eine [Funktion](https://de.m.wikipedia.org/wiki/Funktion_\(Programmierung\)) durch eine andere ersetzen will. Dies lasst sich im Weiteren dann auf Methoden in der Objektorientierung ubertragen, wenn nach dem Liskovschen Substitutionsprinzip Methoden von Objekten ersetzt werden.

Seien und Funktionen, die beispielsweise folgende [Signatur](https://de.m.wikipedia.org/wiki/Signatur_\(Programmierung\)) haben:

    , wobei und , und

Wie man sieht, ist eine Obermenge von , jedoch eine Untermenge von . Wenn man die Funktion anstelle von einsetzt, dann nennt man den Eingabetyp C kontravariant, den Ausgabetyp D kovariant. Im Beispiel kann die Ersetzung ohne Typverletzung geschehen, da die Eingabe von den gesamten Bereich der Eingabe von abdeckt. Außerdem liefert Ergebnisse, die den Wertebereich von nicht uberschreiten.

Als Modell soll die [UML](https://de.m.wikipedia.org/wiki/UML)-Schreibweise zur Darstellung der Vererbungshierarchie dienen:
    
    
                           Kontravarianz           Kovarianz             Invarianz
     ┌─────────┐         ┌───────────────┐     ┌───────────────┐     ┌───────────────┐
     │    T    │         │ ClassA        │     │ ClassA        │     │ ClassA        │
     ├─────────┤         ├───────────────┤     ├───────────────┤     ├───────────────┤
     │         │         │               │     │               │     │               │
     ├─────────┤         ├───────────────┤     ├───────────────┤     ├───────────────┤
     │         │         │ method(t':T') │     │ method():T    │     │ method(t :T&) │
     └─────────┘         └───────────────┘     └───────────────┘     └───────────────┘
          ↑                      ↑                     ↑                     ↑
     ┌─────────┐         ┌───────────────┐     ┌───────────────┐     ┌───────────────┐
     │    T'   │         │ ClassB        │     │ ClassB        │     │ ClassB        │
     ├─────────┤         ├───────────────┤     ├───────────────┤     ├───────────────┤
     │         │         │               │     │               │     │               │
     ├─────────┤         ├───────────────┤     ├───────────────┤     ├───────────────┤
     │         │         │ method(t :T ) │     │ method():T'   │     │ method(t :T&) │
     └─────────┘         └───────────────┘     └───────────────┘     └───────────────┘
    

_Kontravarianz_: Das Substitutionsprinzip wird eingehalten, denn man kann _method(t : T)_ der Unterklasse _ClassB_ so verwenden, als ware es die Methode der Oberklasse _ClassA_.  
Prufen: Man kann der _method(t : T)_ eine Variable eines spezielleren Typs _T'_ ubergeben, da aufgrund der Vererbung _T'_ alle Informationen enthalt, die sich auch in _T_ befinden.

_Kovarianz_: Das Substitutionsprinzip wird eingehalten, denn man kann _method():T'_ der Unterklasse _ClassB_ so verwenden, als ware es die Methode der Oberklasse _ClassA_.  
Prufen: Der Ruckgabewert der Methode aus _ClassB_ ist _T'_. Man darf diesen Wert einer vom Typ _T_ deklarierten Variable ubergeben, da _T'_ aufgrund der Vererbung uber alle Informationen verfugt, die sich auch in _T_ befinden.

Auf Grund der Eigenschaften des Substitutionsprinzipes ist statische Typsicherheit dann gewahrleistet, wenn die Argumenttypen kontravariant und die Ergebnistypen kovariant sind.

Die in der Objektorientierten Modellierung oft wunschenswerte Kovarianz der Methodenparameter wird trotz resultierender Typunsicherheit in vielen Programmiersprachen unterstutzt.

Ein Beispiel fur die Typunsicherheit kovarianter Methodenparameter findet sich in den folgenden Klassen Person und Arzt, und deren Spezialisierungen Kind und Kinderarzt. Der Parameter der Methode untersuche in der Klasse Kinderarzt ist eine Spezialisierung des Parameters derselben Methode von Arzt und demnach _kovariant_.

**Typunsichere Kovarianz - allgemein**
    
    
    ┌─────────┐         ┌───────────────┐
    │    T    │         │ ClassA        │
    ├─────────┤         ├───────────────┤
    │         │         │               │
    ├─────────┤         ├───────────────┤
    │         │         │ method(t :T ) │
    └─────────┘         └───────────────┘
         ↑                      ↑
    ┌─────────┐         ┌───────────────┐
    │    T'   │         │ ClassB        │
    ├─────────┤         ├───────────────┤
    │         │         │               │
    ├─────────┤         ├───────────────┤
    │         │         │ method(t':T') │
    └─────────┘         └───────────────┘
    

**Beispiel fur typunsichere Kovarianz**
    
    
    ┌────────────────┐         ┌───────────────────────┐
    │ Person         │         │ Arzt                  │
    ├────────────────┤         ├───────────────────────┤
    │                │         │                       │
    ├────────────────┤         ├───────────────────────┤
    │ stillHalten()  │         │ untersuche(p: Person) │
    └────────────────┘         └───────────────────────┘
             ↑                             ↑
    ┌────────────────┐         ┌───────────────────────┐
    │ Kind           │         │ Kinderarzt            │
    ├────────────────┤         ├───────────────────────┤
    │                │         │                       │
    ├────────────────┤         ├───────────────────────┤
    │ tapferSein()   │         │ untersuche(k: Kind)   │
    └────────────────┘         └───────────────────────┘
    

Die Implementierung des Beispiels in Java sieht folgendermaßen aus: Ein Programm unter Verwendung der Klassen konnte so aussehen: Die Ausgabe lautet dann:
    
    
       public class Person {
           protected String name; public String getName() { return name; }
           public Person(final String n) { name = n; }
           public void stillHalten() {
               System.out.println(name + " hält still");
           }
       }
    
       public class Kind extends Person {
           boolean tapfer = false;
           public Kind(final String n) {super(n); }
           public void stillHalten() {
               if(tapfer)
                   System.out.println(name + " hält still");
               else
                   System.out.println(name + " sagt AUA und wehrt sich");
           }
           public void tapferSein() {
               tapfer = true;
               System.out.println(name + " ist tapfer");
           }
       }
    
       public class Arzt extends Person {
           public Arzt(final String n) { super(n); }
           public void untersuche(Person person) {
               System.out.println(name + " untersucht " + person.getName());
               person.stillHalten();
           }
       }
    
       public class Kinderarzt extends Arzt {
           public Kinderarzt(final String n) { super(n); }
           public void untersuche(Kind kind) {
               System.out.println(name + " untersucht Kind " + kind.getName());
               kind.tapferSein();
               kind.stillHalten();
           }
       }
    
    
    
    public class Main {
        public static void main(String[] args) {
           Arzt arzt = new Kinderarzt("Dr. Meier");
           Person person = new Person("Frau Müller");
           arzt.untersuche(person);    
           Kind kind = new Kind("kleine Susi");
           arzt.untersuche(kind);
           // und jetzt RICHTIG
           Kinderarzt kinderarzt = new Kinderarzt("Dr. Schulze");
           kinderarzt.untersuche(person);
           kinderarzt.untersuche(kind);
        } 
    }
    
    
    
    Dr. Meier untersucht Frau Müller
    Frau Müller hält still
    Dr. Meier untersucht kleine Susi
    kleine Susi sagt AUA und wehrt sich
    Dr. Schulze untersucht Frau Müller
    Frau Müller hält still
    Dr. Schulze untersucht Kind kleine Susi
    kleine Susi ist tapfer
    kleine Susi hält still
    

Wichtig ist, dass das Objekt arzt richtig deklariert werden muss, weil hier eine Methode nicht uberschrieben, sondern uberladen wird, und der Vorgang des Überladens an den statischen Typ des Objekts gebunden ist. Die Folge sieht man beim Vergleich der Ausgaben: Dr. Meier kann keine Kinder untersuchen, Dr. Schulze hingegen schon.

In Java funktioniert das Beispiel korrekt: Die Methode untersuche von Arzt wird in Kinderarzt nicht uberschrieben sondern aufgrund der unterschiedlichen Parameter lediglich uberladen, dadurch wird jeweils die richtige Methode aufgerufen. Wenn Arzt untersuche aufgerufen wird, wird die Methode auch immer dort aufgerufen; wenn jedoch Kinderarzt untersuche aufgerufen wird, wird je nach Typ einmal untersuche bei Arzt und einmal bei Kinderarzt aufgerufen. Laut der Sprachdefinition von Java muss eine Methode welche uberschrieben werden soll, die gleiche Signatur (in Java bestehend aus Parameter + evtl. Exceptions) besitzen.

Bei Array-Datentypen kann Kovarianz bei Sprachen wie C++, Java und C# zu einem Problem fuhren, da diese intern den Datentyp auch nach der Umwandlung beibehalten:

Java C#
    
    
    @Test (expected = ArrayStoreException.class)
    public void ArrayCovariance()
    {
        Giraffe[] giraffen = new Giraffe[10];
        Schlange alice = new Schlange("Alice");
    
        // Kovarianz (Typumwandlung in Vererbungsrichtung)
        Tier[] tiere = giraffen;
    
        // führt zur Laufzeit zu einer Ausnahme,
        // da das Array intern vom Typ Giraffe ist
        tiere[0] = alice;
    }
    
    
    
    [Test, ExpectedException(typeof(ArrayTypeMismatchException))]
    public void ArrayCovariance()
    {
        var giraffen = new Giraffe[10];
        var alice = new Schlange("Alice"); 
     
        // Kovarianz 
        Tier[] tiere = giraffen;
     
        // Ausnahme zur Laufzeit
        tiere[0] = alice; 
    }
    

Abhilfe schafft hier die Verwendung von generischen Datentypen. Insbesondere kann bei C# das Interface `IEnumerable<T>`, welches vom Array-Datentyp implementiert wird, eingesetzt werden um Schreibzugriffe zu verhindern:
    
    
    [Test]
    public void ArrayCovariance()
    {
        var giraffen = new Giraffe[10]; 
        var alice = new Schlange("Alice");
     
        IEnumerable<Tier> tiere = giraffen;
        tiere.ToList().Add(alice);
     
        Assert.Contains(alice, tiere);
    }
    
