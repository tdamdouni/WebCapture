# Redundanz in sicheren Automatisierungssystemen Safety mit zwei Kernen

_Captured: 2019-04-03 at 14:15 from [www.elektroniknet.de](https://www.elektroniknet.de/markt-technik/automation/safety-mit-zwei-kernen-30528.html)_

![Der Aufbau des sicheren Dualcore-Prozessors MPC5643L von Freescale Semiconductor ](https://cdn.weka-fachmedien.de/thumbs/media_uploads/images/1289561656-6-freescal-mpc5643l.jpg.950x534.jpg)

> _(C) Freescale SemiconductorDer Aufbau des sicheren Dualcore-Prozessors MPC5643L von Freescale Semiconductor_

Der US-Halbleiterhersteller Freescale Semiconductor bietet Dualcore-Prozessoren an, die den Sicherheits-Niveaus SIL 3 nach EN/IEC 62061 bzw. PL e nach EN ISO 13849-1 entsprechen. Ein Beispiel ist der Baustein MPC5643L, der nicht nur zwei Cores komplett dupliziert mitsamt den zugehorigen Komponenten, sondern auch zahlreiche Sicherheitsfunktionen umfasst.

Roger Ungerer, Senior Field Application Engineer bei der Freescale Halbleiter Deutschland GmbH, erlautert die Safety-Komponenten und Prufmethoden, die einen Prozessor zum Safety-Prozessor machen.

**Markt&Technik: Welche technischen Moglichkeiten in Hard- und Software bestehen, um Singlecore- und Multicore-Prozessoren so sicher zu machen, dass sie die von der Industrie geforderten Sicherheits-Niveaus SIL 3 nach EN/IEC 62061 bzw. PL e nach EN ISO 13849-1 einhalten?   
  
**Roger Ungerer: Grundsatzlich sind hier die verschiedenen Fehlerarten, die auftreten konnen, zu betrachten. Je nach Art des zu erwartenden Fehlers und den spezifischen Anforderungen des Systems ist dann zu entscheiden, ob eine Software- oder eine Hardware-Losung bzw. eine Kombination besser geeignet ist. Hier fließen naturlich auch Analysen des Performance/Zeit-Bedarfs zur Erkennung, Behebung und Meldung des Fehlers sowie okonomische Betrachtungen mit ein. Wenn beispielsweise nur ein sehr kurzes Zeitfenster zur Erkennung des Fehlers zur Verfugung steht, ist in der Regel eine Hardware-Losung erforderlich, die sich dann naturlich in den Bauteilkosten entsprechend niederschlagt.

Speichertest: Ein gutes Beispiel ist das Prufen und eventuelle Beheben von Speicherfehlern. Moglich ist die Überprufung entweder mittels Software (CRC, Cyclic Redundancy Check) oder mittels Hardware (ECC, Error Correction Coding). Die CRC-Software benotigt naturlich eine gewisse Zeit, bis der entsprechende Speicherblock bearbeitet ist und ein Ergebnis zur Verfugung steht. Die ECC-Logik, die in den Mikrocontrollern der MPC56xx-Familie von Freescale implementiert ist, arbeitet dagegen quasi in Echtzeit, d.h. wahrend des Zugriffs auf einen RAModer Flash-Speicher wird bereits ein eventuell vorhandener Fehler erkannt und im Falle eines Ein-Bit-Fehlers gleich behoben.

CPU-Test: In anderen Bereichen wiederum ist Software zwingend erforderlich. Die korrekte Funktion der CPU beispielsweise muss mittels Software festgestellt werden. Hierfur stellt Freescale entsprechende Software-Losungen (CPU-Selftest-Software) zur Verfugung, die eine fur ASILD- bzw. SIL-3-Zertifizierung geforderte Testabdeckung bietet.

Dualcore Redundancy: Redundante Systeme sind grundsatzlich geeignet, hohe Sicherheitsanforderungen zu erfullen. Die Redundanz lasst sich auf Mikrocontroller-Ebene entweder durch den Einsatz zweier eigenstandiger Komponenten erreichen, die sich gegenseitig uberwachen. Oder man setzt einen Mikrocontroller ein, der zwei Cores auf einem Chip integriert hat. Um mit einer solchen Single-Chip-Losung ein hohes Sicherheitsniveau erreichen zu konnen, mussen allerdings neben der Duplizierung der CPU weitere Komponenten redundant ausgelegt werden. Wir sprechen hier von einer sogenannten »Sphere of Replication«.

A/D-Wandler-BIST: Um analoge Funktionsblocke wie A/D-Wandler effizient testen zu konnen, sind spezielle Funktionen implementiert, die diese Aufgabe unterstutzen. Hierbei handelt es sich um eine Kombination aus Hardware- und Software-Komponenten, die entsprechend zusammenwirken. Dieser sogenannte Built-in Self Test (BIST) sollte beim Start des Systems ausgefuhrt und dann in regelmaßigen Abstanden wiederholt werden.

FCCU: Tritt ein Fehler auf, muss das System reagieren und eine entsprechende Fehlerbehandlung durchfuhren. Außerdem ist in der Regel eine Statistik uber die Haufigkeit und Art der Fehler zu erstellen. Um diese Aufgaben zu losen, haben die Safety-MCUs von Freescale eine sogenannte Fault Collection and Control Unit (FCCU). Die FCCU kann dazu dienen, Fehler aufzuzeichnen und entweder die On-Chip-CPUs oder externe Komponenten uber das Auftreten von Fehlern zu informieren.

**Wie funktionieren die entsprechenden Hard- und Software-Architekturen technisch?   
  
**Hier mochte ich zwei Schlusselkomponenten herausgreifen, die einen wesentlichen Beitrag zu einer hohen »Diagnostic Coverage« der Hardware leisten: die ECC-Logik fur die RAM- und Flash-Speicher sowie die Sphere of Replication, die den Dualcore Lockstep Mode (LSM) ermoglicht.

Die ECC-Logik sorgt dafur, dass 1-Bit-Fehler behoben und gemeldet und 2-Bit-Fehler erkannt und gemeldet werden, wobei ein modifizierter Hamming Code genutzt wird. Bei der Behebung des 1-Bit-Fehlers wird dabei nicht die fehlerhafte Bit-Zelle physikalisch behoben, sondern das Datenwort korrigiert, das fur die CPU auf den Bus gelegt wird. Außerdem wird ein Flag gesetzt, um das Auftreten des 1-Bit-Fehlers zu signali- sieren. Damit ist es moglich, auch fur die 1-Bit-Fehler eine Statistik zu fuhren und bei einer etwaigen Haufung entsprechend zu reagieren.

Das Ganze funktioniert naturlich nur dann einwandfrei, wenn die ECC-Logik selbst nicht fehlerhaft ist. Um das zu uberprufen, ist eine Funktion implementiert, die einen ECC-Fehler gezielt erzeugt. Diese Funktion muss in regelmaßigen Abstanden durchgefuhrt werden, abhangig von den jeweiligen Sicherheitsanforderungen.

Auch die Anordnung der einzelnen Bits eines Wortes ist von entscheidender Bedeutung. Es ist beispielsweise sicherzustellen, dass das Auftreffen eines Alpha-Teilchens nicht mehrere Bits des gleichen Wortes, sondern nur ein Bit in unterschiedlichen Worten beeinflusst. Die Bits der RAM- und Flash-Speicher in den MPC55xxund MPC56xx-Controllern sind entsprechend angeordnet.

Der Dualcore Lockstep Mode ermoglicht eine hohe »Diagnostic Coverage« der Hardware, und zwar, indem beide Cores die gleiche Software ausfuhren und mittels sogenannter Redundancy Checker an verschiedenen Stellen uberpruft wird, ob die Ergebnisse identisch sind. Wie bereits erwahnt, ist es entscheidend, dass nicht nur die CPU doppelt ausgefuhrt ist. Weitere Systemkomponenten wie Busse, DMA-Controller, Watchdog, Interrupt-Controller und I/O-Bridge sind ebenfalls dupliziert, um einen Single Point of Failure zu vermeiden.
