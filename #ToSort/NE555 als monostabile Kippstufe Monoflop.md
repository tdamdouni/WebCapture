# NE555 als monostabile Kippstufe / Monoflop

_Captured: 2016-04-21 at 11:29 from [www.elektronik-kompendium.de](http://www.elektronik-kompendium.de/sites/slt/0310121.htm)_

![Monostabile Kippstufe](http://www.elektronik-kompendium.de/sites/slt/schalt/03101211.gif)

### Beschreibung der Schaltung

Die dargestellte Schaltung ist die Grundschaltung des [Timer NE555](http://www.elektronik-kompendium.de/sites/bau/0206115.htm) als monostabile Kippstufe, auch Monoflop genannt. Der Name kommt daher, weil diese Kippstufe nur einmal einen Impuls am Ausgang (A) abgibt, wenn ein Impuls von etwa 0 V am Eingang (E) anliegt. Dieser Triggerimpuls muss kleiner als 1/3 von +VCC sein.  
Die Bauteile R1 und C1 sind fur die Funktionsweise dieser Schaltung verantwortlich. Die Dauer des Ausgangsimpulses wird durch die Bauteile R1 und C1 vorgegeben. Der Widerstand R2 ist ein Pullup-Widerstand, der den Eingang der Schaltung auf einen festen Pegel (+VCC) legt.  
In der dargestellten Schaltung wurde auf einen Stutzkondensator fur die Versorgungsspannung direkt am Timer verzichtet. In einer aufgebauten Schaltung sollte er berucksichtigt werden. 100 nF sollten es schon sein. Ein einfacher Wickelkondensator reicht aus.

Der Kondensator C2 sorgt dafur, dass die Schaltung nicht schwingt. Besonders der NE555 kann ohne C2 leicht ins unkontrollierte Schwingen geraten. Beim Betrieb als stabiler Multivibrator ist es am schlimmsten. Der Grund ist, dass bei jeder Umschaltflanke am Ausgang von Pin 3 eine Stromtransienten auf der Speiseleitung +VCC erzeugt wird. Die Losung beim NE555 ist ein Elko mit mindestens 10 µF und parallel dazu ein 100 nF Kerko zwischen +VCC und GND.  
Schon sehr kleine Spannungsanderungen an +VCC ubertragen sich auf das Widerstandsnetzwerk. Dadurch entstehen kurzzeitige Veranderungen der Referenzspannungen. Die Folge ist ein Storverhalten. Vor allem bei hoheren Frequenzen. Mit dem Kondensator C2 wir die Frequenz stabiler.

### Funktionsbeschreibung

![Spannungsverlauf](http://www.elektronik-kompendium.de/sites/slt/diagramm/03101211.gif)

Im Ruhezustand der Schaltung (Trigger (Pin 2) > 2/3 von +VCC) ist der Kondensator C1 entladen. Der Discharge-Ausgang (Pin 7) schaltet ihn auf 0 V (GND). Man konnte auch sagen, "schließt ihn kurz". Erfolgt ein Impuls von 0 V am Steuereingang (Pin 2), dann wird das interne RS-Flip-Flop gesetzt. Der Discharge-Ausgang (Pin 7) wechselt in einen offenen Zustand (Open Collector). Die Spannung an Pin 7 (Kollektor) hat - im offenen Zustand des Transistors - immer gerade die Spannung die an C1 anliegt. Man kann auch sagen, dass in diesem Moment parallel zu C1 ein unendlich hoher Widerstand liegt. Über den Widerstand R1 wird der Kondensator C1 aufgeladen, bis er 2/3 von +VCC erreicht hat. Dann kippt die Schaltung in den Ursprungszustand zuruck.

Im weiteren Betrieb wird der Discharge-Ausgang (Pin 7), wegen des nicht vorhandenen Kollektorwiderstands ([siehe Innenschaltung NE555](http://www.elektronik-kompendium.de/sites/bau/0206115.htm)), extrem hochohmig. Über den Widerstand R1 wird der Kondensator C1 aufgeladen, bis er 2/3 von +VCC erreicht hat. Dann schaltet der Discharge-Ausgang (Pin 7) wieder auf 0 V (GND). Der Kondensator C1 wird aufgrund eines fehlenden strombegrenzenden Widerstandes kurzgeschlossen und entladt sich daher schlagartig. Es gibt also keine typische exponentielle Entladekurve. Sie ist sehr steil und in bestimmten Bereichen linear. Vereinfacht gesagt, die Schaltung kippt in den Ursprungszustand zuruck.  
Um die Wirkung dieser Schaltung zu verstehen, muss man nur im Diagramm die Signale von E (oben) und A (unten) miteinander vergleichen.

### Beispiel fur eine Bauteilliste

Zeichen Bauteil Wert / Typ

R1
Widerstand
68 kOhm

R1 (Alternative)
Potentiometer
50/100 kOhm

R2
Widerstand
10 kOhm

C1
Kondensator
10 µF

C2
Kondensator
10 nF

### Berechnung der Impulsdauer

Die Dauer des Ausgangsimpulses ti wird durch die Bauteile R1 und C1 vorgegeben. Im Diagramm oben wird deutlich, an welchen Stellen in der Schaltung und welche Zustande innerhalb des NE555 auf die Ladezeit des Kondensators einen Einfluss haben.  
Mochte man die Impulsdauer ti einstellen, dann setzt man fur den Widerstand R1 ein Potentiometer ein. Bei den hier angegebenen Beispielswerten eignet sich ein Poti von 50 kOhm oder 100 kOhm am besten.

### Berechnung

**R1 (Ohm)**  

**C1 (µF)**  


### Anwendung der monostabilen Kippstufe

Die monostabile Kippstufe eignet sich, um einen kurzen Impuls zu verlangern und auf eine Impulsdauer festzulegen. Aus einem variablen Eingangsimpuls am Eingang wird ein definierter Impuls am Ausgang.

### Problem: Lange Leitung

Wenn der Eingang (E) mit einer langen Leitung beschaltet ist, dann kommt es vor, dass die monostabile Kippstufe immer wieder auslost, obwohl kein Impuls anliegt. Das Problem ist die lange Leitung. Dabei werden Schaltflanken von Bauelementen in der Nahe der Leitung immer wieder eingekoppelt. Ein weiterer Kondensator mit 100 nF zwischen Eingang und GND wirkt als Tiefpass und beseitigt das Problem.

### Retriggerbares Monoflop

Bei einer normalen Monostabilen Kippstufe wird in jedem Fall ein Ausgangsimpuls erzeugt, wenn ein Signal (Triggersignal) am Steuereingang (Triggereingang) anliegt. Doch manchmal mochte man, dass am Ausgang das Signal noch eine Zeit lang anliegt. Das bedeutet, dass erst dann der letzte Zyklus am Ausgang gestartet werden soll, wenn der Eingangsimpuls nicht mehr vorhanden ist. Rein technisch gesehen ware das eine Nachlaufsteuerung.  
Dazu wird zwischen Pin 6 bzw. 7 und Pin 2 eine Standard-Diode eingebaut (Kathode an Pin 2). Sie zieht Pin 6 und 7 auf GND, solange ein Signal am Eingang anliegt.  
Im Gegensatz zum normalen Monoflop wird bei einem retriggerbaren Monoflop mit jedem Triggerimpuls innerhalb der Impulsdauer die Ausgangsimpulsdauer (nicht der Ausgangsimpuls) erneut gestartet und so der Ausgangsimpuls verlangert.

### Schaltungen mit dem Timer 555

### Weitere verwandte Themen:
