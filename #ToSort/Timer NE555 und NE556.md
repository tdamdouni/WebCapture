# Timer NE555 und NE556

_Captured: 2016-04-21 at 11:26 from [www.elektronik-kompendium.de](http://www.elektronik-kompendium.de/sites/bau/0206115.htm)_

Der NE555 liefert keine fertigen Funktionen. Die werden erst mit einer außeren Beschaltung hinzugefugt. Deshalb muss man zuerst die Innenschaltung eines NE555 verstehen, bevor man die Funktionsweise einer Schaltung mit dem NE555 verstehen kann.  
Über eine außere Beschaltung wird dem NE555 bestimmte Funktionen oder Eigenschaften beigebracht. Zum Beispiel wird uber eine Kondensator-Widerstandskombination eine zeitliche Komponente hinzugefugt, uber die zeitabhangige Eigenschaften erzeugt werden konnen. Zum Beispiel die beliebten Taktgeberschaltungen, um LEDs zum Blinken zu bringen oder Lauflichter zu betreiben.

![Innenschaltung des NE 555](http://www.elektronik-kompendium.de/sites/bau/schalt/02061151.gif)

Die Innenschaltung ist hier als Blockschaltbild dargestellt. Eigentlich besteht der NE555 (Bipolar-Version) nur aus 23 Transistoren, 15 Widerstanden und 2 Dioden. Er lasst sich also grundsatzlich auch diskret aufbauen.  
Das Kernstuck des NE555 ist ein RS-Flip-Flop. Dessen (Setz-) Eingang wird durch den Komparator 2 gesteuert. Der Rucksetzeingang wird durch den Komparator 1 oder den Reset-Anschluss gesteuert (logische ODER-Funktion). Über den Reset-Eingang wird das RS-Flip-Flop immer zuruckgesetzt. Unabhangig davon, wie die anderen Eingange beschaltet sind. Damit das Zurucksetzen auslost, reicht eine Spannung unterhalb 0,7V aus.   
Die Komparatoren vergleichen jeweils zwei Spannungen, die an ihren Eingangen anliegen. Jeweils ein Eingang hat ein voreingestelltes Spannungsverhaltnis. Diese Spannungsverhaltnis wird durch den dreiteiligen Spannungsteiler (3 Widerstande) hergestellt. Die drei Widerstande haben jeweils den gleichen Wert. An ihnen teilt sich die Betriebsspannung +VCC in drei gleich große Spannungen auf. Diese Referenzspannungen werden fur je einen Eingang der Komparatoren abgegriffen. Einmal 1/3 der Betriebsspannung fur den Komparator 2 (2) und 2/3 der Betriebsspannung fur den Komparator 1 (6).  
Wird am Trigger-Anschluss (2) eine Spannung angeschlossen, die kleiner ist als 1/3 der Betriebsspannung, dann geht der Ausgang des Komparators 2 auf "1". Das RS-Flip-Flop wird gesetzt. Der Ausgang des NE555 (3) geht auf "1".  
Wird am Schwelleneingang (6) eine Spannung angeschlossen, die großer ist, als 2/3 der Betriebsspannung, dann geht der Ausgang des Komparators 1 auf "1". Das RS-Flip-Flop wird zuruckgesetzt. Der Ausgang des NE555 geht auf "0".  
Bevor der Ausgang des Flip-Flops herausgefuhrt wird, erzeugt ein invertierender Verstarker (Operationsverstarker) ein brauchbares Signal. Alternativ steht ein Open-Kollektor-Ausgang (7) zur Verfugung.
