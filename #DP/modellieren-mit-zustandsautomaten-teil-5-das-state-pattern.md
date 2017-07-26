# Modellieren mit Zustandsautomaten (Teil 5): Das State Pattern

_Captured: 2017-05-10 at 21:55 from [blogs.itemis.com](https://blogs.itemis.com/de/modellieren-mit-zustandsautomaten-teil-5-das-state-pattern?utm_source=hs_email&utm_medium=email&utm_content=51748968&_hsenc=p2ANqtz-9K5uwDeHmB9WmwWxVpznk8JcSmsewIVXxpUbBaMPJfWtVMMZlWy6xDSInb0hyYsRQIzSrOKl4Zi-aEwrShIOYRiul1Hw&_hsmi=51749262)_

Nachdem wir die [Modellierung von Zustandsautomaten](https://blogs.itemis.com/de/modellieren-mit-zustandsautomaten-teil-1) und ihre Realisierung mit Hilfe von [Switch-Anweisung](https://blogs.itemis.com/de/modellieren-mit-zustandsautomaten-teil-3-die-gro%C3%9Fe-switch-anweisung) und [Tabelle](https://blogs.itemis.com/de/modellieren-mit-zustandsautomaten-teil-4-darstellung-als-tabelle) kennengelernt haben, schauen wir uns nun eine objektorientierte Implementierungsvariante an: das State Pattern. Anschließend vergleichen wir die drei Varianten.

Das Software-Entwurfsmuster State Pattern verwenden etwa Spring Statemachine, Boost Meta State Machine (MSM) oder das Qt State Machine Framework. Es zahlt zu den Verhaltensmustern (behavioral design patterns) und kapselt das zustandsabhangige Verhalten eines Objekts nach außen hin. Jeder Zustand ist als eine eigene Klasse implementiert, die das Verhalten des Automaten in diesem Zustand definiert. Alle Zustandsklassen leiten sich von einem gemeinsamen Interface ab, so dass sich samtliche Zustande einheitlich behandeln lassen.

Das Klassendiagramm der Jalousiesteuerung sieht so aus:

![Klassendiagramm-von-Zustandsautomaten-einer-Jalousiesteuerung.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/Klassendiagramm-einer-Jalousiesteuerung.png?t=1494425153587&width=362&name=Klassendiagramm-einer-Jalousiesteuerung.png)

Das Interface _State_ definiert diejenigen Methoden, deren Verhalten zustandsabhangig ist. Neben den mit _raise…_ beginnenden Methode zum Auslosen eines Event gibt es hier die Methode _getName_, die den Name des Zustands zuruckgibt.

Die Klasse _StateMachine_ reprasentiert den Zustandsautomaten. Sie verwaltet die dem aktiven Zustand entsprechende Klasse und damit das zustandsspezifische Verhalten im Attribut activeState. Damit ahnelt das State Pattern dem Strategy Pattern, wobei ein Zustand einer Strategie entspricht, sprich: der Implementierung eines konkreten Verhaltens. Wahrend die Strategie im Strategy Pattern aber von außen gesetzt wird, kummern sich die Zustande im State Pattern selbst darum. Wenn man so will, ersetzt im State Pattern eine "Strategie" sich selbst durch eine andere, oder in der richtigen Nomenklatur: Ein Zustand aktiviert seinen Folgezustand selbst.

Schauen wir uns das am Beispiel naher an: Die Client-Anwendung sendet Nachrichten an den Zustandsautomaten, indem sie _StateMachine_-Methoden aufruft. Nehmen wir an, der Benutzer druckt die [↓]-Taste. Der Client informiert den Zustandsautomaten uber diese Aktion durch Aufruf der Methode _raiseUserDown_. Die Reaktion des Automaten hangt vom aktiven Zustand ab:

  * Im Zustand **Moving up** wechselt der Automat in den Zustand **Idle**. 
  * Im Zustand **Idle** wechselt der Automat in den Zustand **Moving down**. 
  * Im Zustand **Moving down** ignoriert der Automat das Ereignis. 

Daher delegiert _StateMachine_ den Aufruf an die entsprechende Methode des aktiven Zustandsobjekts. Die _StateMachine_-Methode _raiseUserDown_ ruft die gleichnamige Methode von _activeState_ auf:
    
    
    public void raiseUserDown() {  
        activeState.raiseUserDown();  
    }

Was nun geschieht, entscheidet das Zustandsobjekt. Handelt es sich um ein Objekt der Klasse _Idle_, erfolgt ein Zustandsubergang zu **Moving down**. So sieht _raiseUserDown_ in _Idle_ aus:
    
    
    public void raiseUserDown() {  
        stateMachine.activateState(new MovingDown(stateMachine));  
    }

Die Methode aktiviert den neuen Zustand durch Übergabe eines entsprechenden Zustandsobjekts an die _StateMachine_-Methode _activateState_, die es _activeState_ zuweist.  
Befindet sich der Automat hingegen im Zustand **Moving down**, soll beim Aufruf von _raiseUserDown_ nichts geschehen. Die Klasse _MovingDown_ implementiert diese Methode daher gar nicht. Es "zieht" vielmehr die _raiseUserDown_-Implementierung der Oberklasse _AbstractState_:
    
    
    public void raiseUserDown() {  
    }

Diese Methode tut nichts und ignoriert somit das Ereignis - in unserem Fall ein sinnvolles Standardverhalten fur alle Ereignisse, fur die die jeweilige konkrete Zustandsklasse kein Verhalten implementiert.

## Quellcode der Beispielanwendung

Hier der Quellcode der Jalousiesteuerung in der Implementierung gemaß dem State Pattern. Der Zustandsautomat besteht aus sechs Klassen; hinzu kommt eine Client-Klasse, die den Automaten nutzt.

Das Interface _State_ spezifiziert, was in der Beispielanwendung ein Zustand ist:
    
    
    package de.itemis.state_machine.example.state_pattern;  
      
    public interface State {  
      
    public void raiseUserUp();  
      
    public void raiseUserDown();  
      
    public void raisePosSensorUpperPosition();  
      
    public void raisePosSensorLowerPosition();  
      
    public String getName();  
      
    }

Die abstrakte Klasse _AbstractState_ implementiert den Bezug zur _StateMachine_ und das Standardverhalten fur Events, namlich diese zu ignorieren:
    
    
    package de.itemis.state_machine.example.state_pattern;  
      
    abstract public class AbstractState implements State {  
      
    protected StateMachine stateMachine;  
      
    public AbstractState(StateMachine stateMachine) {  
    this.stateMachine = stateMachine;  
    }  
      
    public void raiseUserUp() {  
    }  
      
    public void raiseUserDown() {  
    }  
      
    public void raisePosSensorUpperPosition() {  
    }  
      
    public void raisePosSensorLowerPosition() {  
    }  
      
    abstract public String getName();  
      
    }

Die Klassen _Idle_, _MovingUp_ und _MovingDown_ reprasentieren die drei konkreten Zustande:
    
    
    package de.itemis.state_machine.example.state_pattern;  
      
    public class Idle extends AbstractState {  
      
    public Idle(StateMachine stateMachine) {  
    super(stateMachine);  
    }  
      
    @Override  
    public void raiseUserUp() {  
            stateMachine.activateState(new MovingUp(stateMachine));  
    }  
      
    @Override  
    public void raiseUserDown() {  
            stateMachine.activateState(new MovingDown(stateMachine));  
    }  
      
    @Override  
    public String getName() {  
    return "Idle";  
    }  
      
    }  
      
    package de.itemis.state_machine.example.state_pattern;  
      
    public class MovingUp extends AbstractState {  
      
    public MovingUp(StateMachine stateMachine) {  
    super(stateMachine);  
    }  
      
    @Override  
    public void raiseUserDown() {  
            stateMachine.activateState(new Idle(stateMachine));  
    }  
      
    @Override  
    public void raisePosSensorUpperPosition() {  
            stateMachine.activateState(new Idle(stateMachine));  
    }  
      
    @Override  
    public String getName() {  
    return "Moving up";  
    }  
      
    }  
      
    package de.itemis.state_machine.example.state_pattern;  
      
    public class MovingDown extends AbstractState {  
      
    public MovingDown(StateMachine stateMachine) {  
    super(stateMachine);  
    }  
      
    @Override  
    public void raiseUserUp() {  
            stateMachine.activateState(new Idle(stateMachine));  
    }  
      
    @Override  
    public void raisePosSensorLowerPosition() {  
            stateMachine.activateState(new Idle(stateMachine));  
    }  
      
    @Override  
    public String getName() {  
    return "Moving down";  
    }  
      
    }

Die Klasse _StateMachine_ ist das "Gesicht" des Zustandsautomaten nach außen hin:
    
    
    package de.itemis.state_machine.example.state_pattern;  
      
    public class StateMachine {  
      
    public StateMachine() {  
            activateState(new Idle(this));  
    }  
      
    State activeState = null;  
      
    public void activateState(State state) {  
            activeState = state;  
    }  
      
    public State getActiveState() {  
    return activeState;  
    }  
      
    public void raiseUserUp() {  
            activeState.raiseUserUp();  
    }  
      
    public void raiseUserDown() {  
            activeState.raiseUserDown();  
    }  
      
    public void raisePosSensorUpperPosition() {  
            activeState.raisePosSensorUpperPosition();  
    }  
      
    public void raisePosSensorLowerPosition() {  
            activeState.raisePosSensorLowerPosition();  
    }  
      
    }

Und so wird der Zustandsautomat vom Anwendungscode aus genutzt:
    
    
    package de.itemis.state_machine.example.state_pattern;  
      
    import java.io.BufferedReader;  
    import java.io.IOException;  
    import java.io.InputStreamReader;  
      
    public class Example {  
      
    public static void main(String[] args) throws IOException {  
    StateMachine stateMachine = new StateMachine();  
            stateMachine.activateState(new Idle(stateMachine));  
    BufferedReader console = new BufferedReader(new InputStreamReader(System.in));  
    while (true) {  
    System.out.println("Active state: " + stateMachine.getActiveState().getName());  
    System.out.print("Please enter event number! ");  
    System.out.print("1: User.up, 2: User.down, 3: PosSensor.upperPosition, ");  
    System.out.println("4: PosSensor.lowerPosition");  
    String line = console.readLine();  
    int eventNr = -1;  
    try {  
                    eventNr = Integer.parseInt(line);  
    } catch (NumberFormatException ex) {  
                    eventNr = -1;  
    }  
    switch (eventNr) {  
    case 1:  
                    stateMachine.raiseUserUp();  
    break;  
    case 2:  
                    stateMachine.raiseUserDown();  
    break;  
    case 3:  
                    stateMachine.raisePosSensorUpperPosition();  
    break;  
    case 4:  
                    stateMachine.raisePosSensorLowerPosition();  
    break;  
    default:  
    System.out.println("Unknown event number: " + eventNr + ".");  
    break;  
    }  
    }  
    }  
      
    }

Übrigens ist fur das State Pattern nicht zwingend eine objektorientierte Programmiersprache notig. Es lasst sich auch mit einer imperativen Sprache umsetzen, sofern diese uber Funktionszeiger verfugt, wie beispielsweise C. Der Wesenskern des State Patterns ist, dass der aktive Zustand auf Ereignisse reagiert und gegebenenfalls einen anderen Zustand aktiviert.  
Bei einer C-Implementierung gehort zu jedem Zustand eine Funktion ("Zustandsfunktion"), die diese Aktionen implementiert. Der Zustandsautomat merkt sich den aktiven Zustand durch einen Zeiger auf dessen Zustandsfunktion. Diese liefert als Ruckgabewert den Zeiger auf den nachsten Zustand, genau: auf dessen Zustandsfunktion.

## Welcher Implementierungsansatz ist der beste?

Fur "richtige" Computer wie Notebooks, Desktop-PCs oder Server fallen die Unterschiede zwischen den betrachteten Implementierungsansatzen nicht wirklich ins Gewicht. Anders sieht es bei eingebetteten Geraten (embedded devices) aus, die in puncto Speicherplatz oder CPU-Leistung typischerweise stark eingeschrankt sind. Hier lautet die klare Antwort: Es kommt darauf an.

Erfahrungsgemaß sind Zustandsautomaten sehr schnell. Bei einem Zustandsautomaten mit wenigen Zustanden und wenigen Events lohnen sich Optimierungsuberlegungen daher kaum. Anders sieht es bei einer hohen Anzahl von Zustanden oder Events aus. Es soll an dieser Stelle allerdings nicht darum gehen, was genau eine "hohe" Anzahl ist - 500?, 50.000?, 5 Millionen? -, sondern lediglich um einige grundsatzliche Überlegungen.

Eine hohe Anzahl von Zustanden bedeutet:

  * Die Switch-Anweisung enthalt sehr viele Falle. 
  * Die (eindimensionale) Zustandsubergangstabelle wird sehr hoch. 
  * Das State Pattern benotigt sehr viele Zustandsklassen. 

Ist die Zahl der Events hoch, heißt das:

  * Innerhalb der einzelnen Falle in der Switch-Anweisung gibt es - abhangig vom jeweiligen Zustand - viel zu tun. 
  * Die Zustandsubergangstabelle wird sehr breit. 
  * Im State Pattern werden die einzelnen Zustandsklassen - abhangig vom jeweiligen Zustand - recht umfangreich. 

In allen Implementierungsansatzen setzt sich die Ausfuhrungszeit aus folgenden Elementen zusammen:

  * Suche nach dem aktiven Zustand 
  * Suche nach Transition anhand des oder der vorliegenden Events 
  * Aktivierung des Folgezustands 

Hinzu kommen die Ausfuhrungszeiten von Guard Conditions und Aktionen. Da diese aber hochst anwendungsspezifisch sind, betrachten wir sie hier nicht weiter. Die Aktivierung des Folgezustands besteht jeweils aus einer einfachen Zuweisung, deren Zeit- und Speicherbedarf wir vernachlassigen konnen.

### Laufzeitbedarf

Fur die Suche nach dem aktiven Zustand fuhrt die Switch-Anweisung mindestens einen Vergleich aus, namlich dann, wenn der erste Fall der Switch-Anweisung bereits der aktive Zustand ist. Schlimmstenfalls benotigt die Switch-Anweisung so viele Vergleiche wie es Zustande gibt, namlich dann, wenn erst die letzte Case-Klausel den aktiven Zustand behandelt. Sind alle Zustande gleich haufig aktiv, fuhrt die Switch-Anweisung im Mittel _z/2_ Vergleiche durch, wobei z die Anzahl der Zustande ist. Die Ausfuhrungszeit liegt also in der Großenordnung _O(z)_. Es folgt die Analyse, ob bestimmte Events vorliegen, die die entsprechenden Transitionen auszulosen. Die Ausfuhrungszeit hierfur liegt - mit ahnlicher Überlegung wie bei den Zustanden - in der Großenordnung _O(e)_, wobei _e_ die Anzahl der Event-Typen ist.

Der Zeitbedarf fur die Suche in einer eindimensionalen Zustandsubergangstabelle liegt ebenfalls bei _O(z)_ \+ _O(e)_. Der erste Term beschreibt die zeilenweisen Suche nach dem aktiven Zustand, der zweite Term steht fur die Suche nach einem Event innerhalb der Zeile. Fuhren vom aktiven Zustand mehrere Transitionen zu unterschiedlichen Folgezustanden, so sind im Allgemeinen mehrere Zeilen zu durchsuchen. An der Großenordnung des Laufzeitbedarfs andert das aber nichts.

Der objektorientierte Ansatz punktet mit einem Zeitbedarf, der von der Anzahl der Zustande unabhangig ist. Da der aktive Zustand bereits als Objekt vorliegt, liegt der Zeitbedarf fur die "Suche" nach dem aktiven Zustand in der Großenordnung _O(1)_. Der Aufruf der dem Event entsprechenden Methode kommt hinzu. Auf den ersten Blick mag das ebenfalls nach _O(1)_ aussehen, doch durfte der Aufwand abhangig von der jeweiligen Sprache und Laufzeitumgebung konservativ geschatzt eher bei _O(e)_ liegen.

### Speicherplatzbedarf

Switch-Anweisung wie Zustandsubergangstabelle mussen samtliche Kombinationen aus Zustand und Event entweder im Programmcode der Switch-Anweisung oder in den Tabellendaten berucksichtigen. Der Speicherbedarf liegt daher in beiden Fallen in der Großenordnung _O(z * e)_. Allerdings belegt die Tabelle davon immer den vollen Umfang, auch wenn sie nur sparlich besetzt ist. Die Switch-Anweisung hingegen braucht nur diejenigen Zustand-/Event-Kombinationen zu kodieren, bei denen ein Event zu einer Transaktion fuhrt. Andererseits belegt ein Funktionszeiger in der Tabelle nur den Speicherplatz einer Adresse, was im Allgemeinen weniger sein durfte, als der Code einer einzelnen Zustand-/Event-Kombination im Mittel belegt.

Im State Pattern enthalt jede Zustandsklasse eine Methode fur jedes Event, das der jeweilige Zustand berucksichtigt. Wir haben es also ebenfalls mit der Großenordnung _O(z*e)_ zu tu n. Ähnlich wie bei der Switch-Anweisung brauchen aber nur diejenigen Event-Methoden kodiert zu werden, die etwas anderes bewirken sollen als das in der abstrakten Oberklasse implementierte allgemeine Verhalten fur dieses Event. Nur diese Methoden benotigen Speicherplatz fur den Programmcode.

### ROM- oder RAM-Speicher  
  


Zu bedenken ist, auf welchen Geraten ein Zustandsautomat laufen soll. Objektorientierte Sprachen benotigen in der Regel eine umfangreiche Laufzeitumgebung und mehr RAM, was den Einsatz auf eingebetteten Geraten einschranken oder verhindern kann. Je mehr Programmteile in das unveranderliche ROM passen, desto besser. Ausfuhrbarer Code wie in der Switch-Anweisung fallt in diese Kategorie, ebenso festkodierte Zustandsubergangstabellen. Bei einer objektorientierten Implementierung des State Patterns sollte man statische Zustandsobjekte wiederverwenden statt stets dynamisch neue Objekte im RAM zu erzeugen.

### Debug-Fahigkeit

Wichtig ist auch, wie leicht sich eine Statechart-Anwendung wahrend der Entwicklung debuggen lasst. Der Entwickler mochte an bestimmten Stellen seiner Anwendung gern Breakpoints setzen. Dort soll die Anwendung anhalten, damit er sie Schritt fur Schritt ausfuhren und analysieren kann, warum sie sich nicht wie erwartet verhalt. In einer State-Klasse ist das recht einfach. Auch Switch-Anweisungen eignen sich. Bei Tabellen kann der Entwickler zwar Breakpoints in den Funktionen setzen, auf die die Funktionsszeiger in der Tabelle verweisen. Aber wenn diese Zeiger in den falschen Zellen stehen, ist die Analyse knifflig.

### Verstandlichkeit und Wartbarkeit

Überhaupt ist der Code von Zustandsautomaten im Allgemeinen weder ubersichtlich noch anschaulich oder verstandlich. Am besten schneidet das State Pattern ab, denn es vermeidet eine unubersichtliche und schwer lesbare Switch-Anweisung. Solange ein Zustand nicht zu viele unterschiedliche Events behandeln muss, bleibt er uberschaubar. Neue Zustande erfordern lediglich neue Zustandsklassen; eine Änderung des Verhaltens beschrankt sich auf eine Änderung der betroffenen Zustande. Insgesamt verringert sich der Wartungsaufwand.  
Bei Automaten mit wenigen Zustanden hingegen lohnt sich der Aufwand einer objektorientierten Implementierung nicht unbedingt, weil die Switch-Anweisung in diesem Fall gar nicht so unubersichtlich ware.

Falls ein State-Machine-Framework zur Verfugung steht und sich vom Ressourcenbedarf her fur die Zielplattform eignet, sollte es zum Einsatz kommen. Verstandlichkeit und Wartbarkeit kann das nur gut tun.

## Ausblick: Quellcode automatisch erzeugen

Alle vorgestellten Implementierungsvarianten kranken prinzipbedingt an einer Reihe von Nachteilen:

  * Keine Form der Implementierung reicht in puncto Anschaulichkeit und Verstandlichkeit an das Zustandsdiagramm heran. Je umfangreicher ein Zustandsautomat ist, desto unlesbarer und unuberschaubarer ist seine Darstellung als Programmcode oder Zustandsubergangstabelle.
  * Die Transformation eines Zustandsdiagramms in eine Implementierung ist aufwendig und fehlertrachtig. 
  * Änderungen am Zustandsdiagramm bedeuten Änderungen an der Implementierung. Dies ist erneut aufwendig, fehlertrachtig und in keiner Weise wartungsfreundlich. 

Implementierungsaufwand und -komplexitat schreien geradezu nach Tool-Unterstutzung, so dass sich der Entwickler im Idealfall nur noch um das graphische Statechart zu kummern braucht. Das werden wir uns im folgenden Teil dieser Serie am Beispiel YAKINDU Statechart Tools naher anschauen.

Das Werkzeug konnt ihr euch vorab auch schon kostenfrei bei uns herunterladen.

Übrigens:

Wenn ihr euch fur unsere komplette Serie zum Thema "Modellieren mit Zustandsautomaten" interessiert - hier findet ihr alle Artikel:
