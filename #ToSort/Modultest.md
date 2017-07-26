# Modultest

_Captured: 2015-10-23 at 17:42 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Modultest)_

Da Algorithmen auf Modulebene meist nur eine begrenzte Komplexitat aufweisen und uber klar definierte Schnittstellen aktiviert werden, konnen sie mit relativ wenigen [Testfallen](https://de.m.wikipedia.org/wiki/Testfall) weitgehend [vollstandig](https://de.m.wikipedia.org/wiki/Testabdeckung) getestet werden. Dies gilt als Voraussetzung fur die anschließende Teststufe [Integrationstest](https://de.m.wikipedia.org/wiki/Integrationstest), um dort die Testfalle auf das integrierte Zusammenwirken großerer Funktionsteile oder der gesamten Anwendung ausrichten zu konnen; die modulspezifischen Detailkonstellationen lassen sich damit dort auf Stichproben beschranken, was die Anzahl der erforderlichen Testfalle drastisch reduziert.

Zum Vergleich: Ein Gerat wird erst dann als Ganzes getestet, wenn die Funktionsfahigkeit seiner Einzelteile als gesichert gilt.

Aus dem Spektrum der zahlreichen [Testarten/Testtechniken](https://de.m.wikipedia.org/wiki/Softwaretest) treffen fur Modultests besonders die folgenden zu. Ein Modultest ist also zum Beispiel (mehrere Moglichkeiten):

ein Entwicklertest
    zum Testen werden haufig Testversionen der Software bereitgestellt, um z. B. Eingaben zu simulieren oder Ergebnisse zu protokollieren.
ein White-Box-Test
    die zu testenden funktionalen Details und ihre moglichen Kombinationen werden i. d. R. aus dem [Quellcode](https://de.m.wikipedia.org/wiki/Quellcode) oder sehr detaillierten technischen Spezifikationen abgeleitet.
ein Überdeckungstest
    unterschiedliche [Test-Abdeckungsgrade](https://de.m.wikipedia.org/wiki/Kontrollflussorientierte_Testverfahren) der codierten (Kontroll-) Anweisungen werden beim Testen angestrebt.
ein Äquivalenzklassentest
    die Testkonstellationen konnen damit auf das Testen bestimmter Grenzwerte beschrankt werden.

Modultests zahlen zu den White-Box-Tests. Das heißt, dass bei der Definition der Testfalle der zu testende Quellcode bekannt ist. Die Spezifikation der Software wird lediglich fur die Bestimmung der Soll-Ergebnisse benutzt. Prinzipiell mussen alle Quellcode-Teile mindestens einmal ausgefuhrt werden. [Anweisungsuberdeckung](https://de.m.wikipedia.org/wiki/Kontrollflussorientierte_Testverfahren), [Zweiguberdeckung](https://de.m.wikipedia.org/wiki/Kontrollflussorientierte_Testverfahren) oder [Pfaduberdeckung](https://de.m.wikipedia.org/wiki/Kontrollflussorientierte_Testverfahren) konnen dabei helfen festzustellen, welche Testfalle hierzu in der Theorie mindestens erforderlich sind (siehe dazu [Kontrollflussorientierte Testverfahren](https://de.m.wikipedia.org/wiki/Kontrollflussorientierte_Testverfahren)). In der Praxis versucht man in aller Regel, das gesetzte Überdeckungsziel mit moglichst wenigen Testfallen zu erreichen, da alle Modultests auch laufend gepflegt werden mussen.

Üblicherweise orientieren sich alle Modultests an einem einheitlichen Grundaufbau. Dabei wird zunachst (1) ein Ausgangszustand initialisiert, hierauf (2) die zu testende Operation ausgefuhrt und zuletzt (3) das Ist-Ergebnis mit einem aus der Spezifikation abgeleiteten Sollwert verglichen. Fur diese Vergleiche stellen die Test Frameworks `assert`-Methoden (deutsch etwa: feststellen, versichern) zur Verfugung.

Modultests testen ein Modul isoliert, d. h. weitgehend ohne Interaktion mit anderen Modulen. Deshalb mussen oder konnen bei Modultests andere Module beziehungsweise externe Komponenten wie etwa eine [Datenbank](https://de.m.wikipedia.org/wiki/Datenbank), [Dateien](https://de.m.wikipedia.org/wiki/Datei), [Backendsysteme](https://de.m.wikipedia.org/wiki/Front-End_und_Back-End) oder [Unterprogramme](https://de.m.wikipedia.org/wiki/Unterprogramm) durch Hilfsobjekte simuliert werden, soweit das zu testende Modul ([Prufling](https://de.m.wikipedia.org/wiki/Pr%C3%BCfling) oder Testobjekt) diese benotigt. Vollstandige Tests mit allen Komponenten in ihrer Originalversion sollten in den nachfolgenden [Integrations- und Systemtests](https://de.m.wikipedia.org/wiki/Softwaretest) durchgefuhrt werden - wobei ggf. im Modultest nicht erkannte Fehler (z. B. wegen identischer Falschannahmen fur das Testobjekt und die Hilfsroutine) entdeckt werden sollten.

Derartige Hilfsobjekte werden z. B. als [Stellvertreter](https://de.m.wikipedia.org/wiki/Stellvertreter_\(Entwurfsmuster\)) implementiert und mittels [Inversion of Control](https://de.m.wikipedia.org/wiki/Inversion_of_Control) bereitgestellt. Ein Modul kann so meist einfacher getestet werden, als wenn alle Module bereits integriert sind, da in diesem Fall die Abhangigkeit der Einzelmodule mit in Betracht gezogen und im Testhandling berucksichtigt werden musste. Auch sind derart isolierte Modultests schon moglich, wenn andere, eigentlich benotigte Komponenten fur den Test noch nicht verfugbar sind. Bekannt sind folgende Hilfsobjekte:[[2]](https://de.m.wikipedia.org/wiki/Modultest)

Dummy
    Ein Objekt, das im Code weitergereicht, aber nicht verwendet wird. Werden eingesetzt um Parameter mit Werten zu befullen.
    Ein Objekt mit Implementierung. Die Implementierung ist dabei jedoch eingeschrankt, wodurch ein Einsatz in der Produktionsumgebung nicht moglich ist. Ein typisches Beispiel fur ein Fake ist eine Datenbank, die Daten nur temporar im Speicher halt.
    Ein Objekt, welches beim Aufruf einer bestimmten Methode unabhangig von der Eingabe die gleiche Ausgabe liefert.
    Ein Objekt, das bei vorher bestimmten Funktionsaufrufen mit bestimmten ubergebenen Werten eine definierte Ruckgabe liefert. Zur Erstellung des Mock-Objektes verwendet man ublicherweise ein [Mocking Framework](https://de.m.wikipedia.org/wiki/Mocking_Framework).
    Ein Objekt, welches Aufrufe und ubergebene Werte protokolliert und bei Bedarf zuruckliefert. Dabei werden Fake-, Stub- oder Mock-Objekte zu einem Spy erweitert. Alternativ kann ein [Decorator](https://de.m.wikipedia.org/wiki/Decorator) eingesetzt werden.
Shim, Shiv
    Eine [Bibliothek](https://de.m.wikipedia.org/wiki/Programmbibliothek), welche die Anfrage an eine [Programmierschnittstelle](https://de.m.wikipedia.org/wiki/Programmierschnittstelle) abfangt und selbst behandelt (z. B. mittels eines Fake-, Stub- oder Mock-Objekts), die ubergebenen Parameter verandert oder die Anfrage umleitet.

Modultests testen gemaß dem [Design-by-contract](https://de.m.wikipedia.org/wiki/Design_by_contract)-Prinzip moglichst nicht die Interna einer Methode, sondern nur ihre externen Auswirkungen (Ruckgabewerte, Ausgaben, Zustandsanderungen, Zusicherungen). Werden die internen Details der Methode gepruft (dies wird als [White-Box-Testing](https://de.m.wikipedia.org/wiki/White-Box-Test) bezeichnet), konnte der Test fehlschlagen, obwohl sich die externen Auswirkungen nicht geandert haben. Daher wird in der Regel das sogenannte [Black-Box-Testing](https://de.m.wikipedia.org/wiki/Black-Box-Test) empfohlen, bei dem man sich auf das Prufen der externen Auswirkungen beschrankt.

Mit der Verbreitung von [agilen Softwareentwicklungsmethoden](https://de.m.wikipedia.org/wiki/Agile_Softwareentwicklung) und insbesondere [testgetriebener Entwicklung](https://de.m.wikipedia.org/wiki/Testgetriebene_Entwicklung) ist es ublich geworden, Modultests moglichst automatisiert auszufuhren. Dazu werden ublicherweise mit Hilfe von _Test Frameworks_ wie beispielsweise [JUnit](https://de.m.wikipedia.org/wiki/JUnit) Testprogramme geschrieben. Über die Test Frameworks werden die einzelnen Testklassen aufgerufen und deren Komponententests ausgefuhrt. Die meisten Test Frameworks geben eine grafische Zusammenfassung der Testergebnisse aus.

Automatisierte Modultests haben den Vorteil, dass sie einfach und kostengunstig ausgefuhrt und dass neue [Programmfehler](https://de.m.wikipedia.org/wiki/Programmfehler) schnell gefunden werden konnen. Dies setzt allerdings u. a. voraus, dass Testergebnisse aus fruheren Modultests vorliegen und die aktuellen Testergebnisse mit diesen verglichen werden konnen.

Modultests konnen (wie jeder Test) die Fehlerfreiheit des getesteten Moduls nicht garantieren oder nachweisen, sondern lediglich unterstutzen. Die Grenzen von Modultests liegen notwendigerweise darin, dass nur solche Fehler gefunden werden konnen, zu deren Entdeckung die verwendeten Tests geeignet sind. Eine Softwarekomponente, die „grun" testet, ist also nicht unbedingt fehlerfrei.

Das Merkmal von Code, „grun" zu testen, und durchaus auch der Wunsch nach diesem Ergebnis, konnte dazu fuhren, dass tatsachlich (unbewusst) nur soviel getestet wird, dass alle Tests „grun" sind. Module, die keine fehlschlagenden Modultests haben, als fehlerfrei zu behandeln, ist ein haufiges [Anti-Pattern](https://de.m.wikipedia.org/wiki/Anti-Pattern) in der Praxis testgetriebener Entwicklung.

Bei der Änderung von Code stellen Modultests sicher, dass keine solchen Fehler unbemerkt eingefugt werden, die der vorhandene Bestand an Tests sicher aufdeckt. Das Problem, eine ausreichende [Testabdeckung](https://de.m.wikipedia.org/wiki/Testabdeckung) herzustellen, kann nur durch entsprechende Beachtung und geeignete Maßnahmen gelost werden.

Wenn - wie ublicherweise - der Autor von Modultests mit dem Autor der Module identisch ist, konnen Denkfehler in der Implementierung auch im Test erscheinen und nicht aufgedeckt werden. Wenn es sich um dieselbe Person handelt, wird dies auch nicht dadurch ausgeschlossen, dass die Tests zuerst entwickelt werden, da sowohl die beabsichtigte Funktionsweise des Codes, als auch seine zukunftige Gestalt bereits im Denken des Testautors und spateren Codeautors prasent sein konnen.
