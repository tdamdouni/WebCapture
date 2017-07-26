# PHP-Performance: Entwicklungen und Einflussfaktoren 

_Captured: 2016-02-14 at 23:16 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/entwicklung/programmiersprachen/php-performance-entwicklungen-und-einflussfaktoren.html)_

![Rund 80% des Webs werden von PHP-Webseiten betrieben.](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720_Depositphotos_72523717_m-2015_Nongkran_ch_a4373babc7.jpg)© depositphotos.com / Nongkran_ch

**Vor wenigen Wochen wurde die siebte Version der Sprache PHP offiziell veröffentlicht und sie verspricht eine zwei- bis dreifache Verbesserung der Performance aller in der vorherigen Version PHP 5.6 geschriebenen Programme. Zum 20-jährigen Bestehen der Sprache gibt es Grund genug, sich einmal mit der Performance der beliebten Skriptsprache auseinander zu setzen.**

**Rund 80 Prozent des Webs werden von PHP-Webseiten betrieben. Der Grund für die breite Nutzung der Sprache im Internet ist jedoch nicht ihre Geschwindigkeit, sondern der leichte Einstieg, das weitverbreitete Hostingangebot und Open Source-Standardsoftware wie Wordpress, Magento oder Drupal. Historisch betrachtet ist PHP eine eher langsame Sprache und diesen Ruf hat sie noch heute, auch wenn die Sprache mittlerweile mit jeder Version riesige Geschwindigkeitssprünge macht.**

## Architektur von PHP

Ein zentraler Grund, warum PHP als langsam angesehen wird, ist sicherlich die Shared-Nothing-Architektur der Sprache. Für jeden PHP-Request wird ein neuer Speicherbereich reserviert, jeweils mit vollständig unabhängigen Funktionstabellen und Variablen. Alle Funktionen und Klassen werden in jedem Aufruf neu im Speicherbereich für diesen einen Request geladen. Dieser Bereich wird dann nach dem Ende des Requests wieder komplett freigegeben. Für den Programmierer ist diese Architektur praktisch, da kein globaler Zustand zwischen Requests existiert und Speichermanagement (fast) unnötig wird. Ein weiterer Vorteil dieser Shared-Nothing-Architektur ist die problemlose horizontale Skalierbarkeit von PHP-Anwendungen auf mehr als einen Webserver. 

Für die Performance ist das dauerhafte Erzeugen und Freigeben von Speicher jedoch problematisch, besonders wenn komplexe Konfigurationen, Applikations- und Framework-Objekte in jedem Request neu geladen werden. Dazu kommt, dass ein PHP-Request vollständig linear verläuft und alle I/O-Operationen synchron sind. Da die Menge an parallel ausführbaren PHP-Requests üblicherweise gedeckelt ist, kann es passieren, dass der Webserver nicht mehr auf neue Requests antworten kann, wenn mehrere PHP-Requests zu lange auf I/O-Operationen warten. 

Diese Architektur steht im krassen Gegensatz zu vielen anderen Sprachen, die häufig im Web genutzt werden, z. B. Java, Python, Ruby, Go oder NodeJS. Zwar setzen einige Frameworks in diesen Sprachen auch auf Shared-Nothing-Architektur, aber prinzipiell können Variablen oder Objekte zwischen verschiedenen Requests geteilt werden. Konsequenterweise sind diese Sprachen in den allermeisten synthetischen Hello-World-Benchmarks deutlich schneller als PHP. Ein gutes Beispiel dafür ist die TechEmpower-Benchmark-Reihe, die eine große Zahl von Frameworks und Sprachen vergleicht ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[1]](http://www.informatik-aktuell.de/entwicklung/programmiersprachen/php-performance-entwicklungen-und-einflussfaktoren.html#c14746).

## PHP-Interpreter, Virtual Machine und Bytecode-Caches

Um einen Einblick in die Performance eines einzelnen PHP Scripts zu geben blicken wir tiefer in die Laufzeitumgebung von PHP. 

PHP ist in C implementiert und bis Version 3 eine interpretierte Sprache gewesen. Bei jedem Aufruf eines PHP-Skripts wurde der Programmcode vollständig Statement für Statement neu durch den PHP-Interpreter ausgeführt. Syntaxfehler, die mitten im Programm auftraten, wurden auch erst beim Ausführen des fehlerhaften Statements entdeckt, alle vorherigen Statements wurden trotzdem ausgeführt. Diese Spracharchitektur erlaubt keine Optimierungen von Programmen, da keine Möglichkeit besteht, Zwischenschritte in der Ausführung zwischen verschiedenen Requests wiederzuverwenden. 

Seit dem Release von PHP 4 (2000) verwendet die Sprache unter der Haube eine virtuelle Maschine (VM) mit dem Namen Zend Engine ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[2]](http://www.informatik-aktuell.de/entwicklung/programmiersprachen/php-performance-entwicklungen-und-einflussfaktoren.html#c14746). Seitdem werden PHP-Skripte nicht mehr sofort interpretiert, sondern zuerst in Bytecodes/Opcodes übersetzt, die dann auf der Zend Engine-VM ausgeführt werden. Da diese beiden Schritte zur Laufzeit in jedem Request passieren, wird damit zu PHP 3 zunächst keine Performance-Steigerung erreicht. 

Jedoch erlaubt diese Architektur die Entwicklung von Bytecode-Caches, die den Compile-Schritt von PHP zu Zend-Bytecode zwischenspeichern. Dabei wird der Bytecode im Shared Memory des Webservers zwischengespeichert und aus diesem Speicher für jeden Request wiederverwendet. So wird die teure Übersetzung (Kompilierung) eines PHP-Skripts nur einmalig ausgeführt. Bytecode-Caches verbessern die Performance eines PHP-Requests üblicherweise um mindestens das Doppelte, wobei in einigen alten PHP-Versionen auch Steigerungen von fünffach bis zehnfach möglich waren. Da für die Verwendung von Bytecode-Caches keine Änderungen an der eigenen Code-Basis notwendig sind, ist der Betrieb einer PHP-Applikation in Produktion ohne einen Bytecode-Cache schon lange unüblich. 

Da PHP-Entwickler daran gewöhnt sind, Skripte zu verändern und durch Neuladen des Browsers direkt auszuführen, arbeiten Bytecode-Caches häufig mit einer Cache-Invalidierung basierend auf der "Last Modified"-Uhrzeit einer PHP-Datei. So wird beim Speichern des Bytecodes in den Cache zusätzlich die Uhrzeit der letzten Änderung mit gespeichert und dann bei jedem Lesen mit der aktuellen Änderungszeit der Datei verglichen. Da diese Abfrage einen Dateizugriff notwendig macht, kann sie in Produktion abgeschaltet werden. 

Bekannte Bytecode-Caches für PHP sind Zend Optimizer, APC, eAccelerator, XCache oder IonCube PHP Accelerator. Seit Version 5.5 wird PHP von Werk aus mit der Extension Zend Optimizer Plus ausgeliefert, die dafür in "Opcache" umbenannt wurde. Damit enthält PHP jetzt in jedem neuen Release sofort einen kompatiblen Bytecode-Cache, der den sofortigen Einsatz der neuen Version in Produktion ermöglicht. In vorherigen Versionen hat es häufig Monate gedauert, bis Bytecode-Caches stabil in Produktion eingesetzt werden konnten. Seitdem Opcache Teil von PHP 5.5 ist, wird außer XCache keines der Konkurrenzprodukte aktiv weiterentwickelt.

## Optimierungen der PHP-Engine

Unabhängig von den massiven Vorteilen durch den Einsatz eines Bytecode-Caches hat sich die Performance von PHP in allen Versionen mehr oder weniger stark verbessert. Die Gründe dafür sind vielfältig und technisch interessant.  
  
In PHP 5.3 wurde der Scanner des Compilers von einer veralteten Flex-Version auf re2c portiert, was zu einer Performance-Steigerung von bis zu 20-30 Prozent geführt hat. 

In PHP 5.4 wurde eine Reihe von Optimierungen eingeführt, die erneut bis zu 20-30 Prozent Verbesserung zu 5.3 erreichen. Unter anderem wurde "String interning" für Strings implementiert, die zur Compile-Zeit bekannt sind. Mit dieser Technik wird für jeden String nur ein einziges Mal Speicher alloziert und an allen folgenden Stellen wiederverwendet. Im Gegensatz zur Sprache Ruby wurde dafür kein eigener Datentyp eingeführt, sondern der Compiler erkennt selbst, welche Strings interniert werden können. Eine Unterscheidung zwischen internierten und normalen Strings ist wichtig, da internierte Strings nicht verändert werden können (immutable). Im Falle von häufigen String-Manipulationen würde es sich negativ auf die Performance auswirken, wenn alle Strings interniert würden.

> Für Version 7 wurde die Zend-Engine stark verbessert. 

Auch neu in PHP 5.4 ist eine effizientere Repräsentation von Klassen und Objekten, was sowohl Speicher- als auch Geschwindigkeitsvorteile mit sich bringt. Speicher(de-)allokationen in C mit malloc/free sind nicht kostenlos und weniger Allokationen sparen viel CPU-Zeit: In PHP 5.4 werden die Hash-Tables für Variablen, Konstanten und Funktionen auf Klassen erst initialisiert, wenn sie auch wirklich benötigt werden. Außerdem werden Objektvariablen intern nicht mehr mit dem Namen der Variable als Schlüssel einer Hash-Table gespeichert, sondern in einem numerischen Array. Diese beiden Änderungen sparen viel Speicher, was eine deutlich schnellere Ausführung nach sich zieht. 

Die neue Version 7 basiert auf einer stark verbesserten Zend-Engine und beschleunigt die Performance von PHP-Skripten auf 50-70 Prozent der Originalzeit. Diese Steigerung basiert hauptsächlich auf drei Änderungen in der Speicherverwaltung:

  1. Die interne Datenstruktur für PHP-Variablen "zval" wird nun größtenteils auf dem Stack und nicht mehr auf dem Heap alloziert. Stack-Allokierung ist deutlich schneller als Memory-Management auf dem Heap.
  2. Reference-Counting wird jetzt direkt auf den Datenstrukturen für PHP String-, Objekt- und Array-Variablen implementiert. Integer, Float, Booleans und einige andere Typen sind damit viel leichtgewichtiger, da keine Referenzen mehr gezählt werden müssen.
  3. Die Größe der beiden wichtigsten internen Datentypen zval und Hash-Table wurde von 24 auf 16 bytes bzw. 72 auf 56 bytes reduziert. Damit wird deutlich weniger Speicher benötigt und ein signifikanter Zeitaufwand für die Allokierung wird gespart.

Obwohl die Änderungen am C-Code von PHP sehr umfangreich waren, ist PHP 7 fast vollständig rückwärtskompatibel zu PHP 5.6. Nur Autoren von in C implementierten PHP-Extensions müssen große Teile ihres Codes an die neue Zend-Engine anpassen.

## Speichermanagement von PHP

Da die Performance von PHP 5 so stark durch das ineffiziente Speicherverhalten beeinflusst wurde, blicken wir etwas detaillierter auf das Speichermanagement von PHP. Um für jeden Request einen unabhängigen Speicherbereich für PHP bereitzustellen, implementiert die Zend-Engine einen eigenen Memory-Manager (Zend MM). Dafür werden im C-Code die Funktionen emalloc/efree als Abstraktion bereitgestellt. 

Die Vorteile eines eigenen Memory-Managers sind dabei:

  1. Vermeidung von Heap-Fragmentierung durch Allokation und Management von Speicherbereichen (Pages). Dadurch ist das PHP5-Memory-Management bereits sehr effizient, da eine direkte Nutzung von malloc/free bei der großen Menge an kleinen, kurzweiligen Allokationen in PHP-Requests sehr ineffizient wäre.
  2. Automatische Freigabe von Speicher beim PHP-Request shutdown.
  3. Implementierung eines Speicherlimits für einen Request (128 MB).
  4. Automatische Memory-Leak-Erkennung, wenn PHP im Debug-Modus kompiliert wurde.

Die Funktionen emalloc/efree arbeiten dabei immer auf der Heap-Abstraktion, die für einen Request bereit gestellt wird. Damit ist der Speicher immer nur so lange verfügbar wie der Request dauert. Damit wird die Shared-Nothing-Architektur von PHP zentral auf Basis des Memory-Managers implementiert. 

Um persistenten Speicher zu allokieren, der über die Request-Grenze hinweg verfügbar ist, müssen entweder die Funktionen malloc/free direkt verwendet werden oder die vom Zend-Memory-Manager bereitgestellten Funktionen pemalloc/pefree ("p" steht hier für persistent). 

Diese Implementierungsdetails des Memory-Managers erklären, warum vermehrte Speichernutzung in einem PHP-Request zusätzlichen Performance-Overhead bedeuten. 

In PHP 7 wurde der Zend-Memory-Manager überarbeitet, basierend auf Implementierungsdetails der beiden High-Performance-Allokatoren jemalloc und tcmalloc. Mit dieser Änderung wurde die Performance von PHP-Anwendungen noch einmal um einige Prozentpunkte verbessert. 

## Alternative Implementierungen von PHP

HHVM ist eine alternative Implementierung der Sprache PHP, die von Facebook entwickelt wurde und deutlich schneller ist als PHP 5 ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[3]](http://www.informatik-aktuell.de/entwicklung/programmiersprachen/php-performance-entwicklungen-und-einflussfaktoren.html#c14746). Facebook hat 2008/09 begonnen, einen alternativen PHP-Compiler zu implementieren, der 2010 als Open Source-Projekt veröffentlicht wurde. Die erste Version hatte den Namen HPHPc (HipHop for PHP) und war als Transpiler von PHP zu C++-Code implementiert. Die gesamte Facebook-Webseite wurde damit in ein einzelnes Binary übersetzt, das auf allen Servern ausgeführt wurde. Da dieser Compile-Prozess sehr aufwändig war, musste noch ein zweiter Entwicklermodus implementiert werden, der den üblichen Change-Refresh-Repeat-Entwicklungsprozess für PHP-Anwendungen möglich macht. 

In 2013 wurde HPHPc bei Facebook durch die neue Laufzeit HHVM abgelöst, die auf einer virtuellen Maschine basiert. HHVM nutzt Just-in-time-Compilierung (JIT) um performancekritischen Codepfade in Maschinencode zu übersetzen. Wird ein Stück dynamischer PHP-Code drei- oder mehrmals mit exakt denselben Datentypen ausgeführt, kann diese Optimierung durchgeführt werden. Damit ist Code der auf HHVM ausgeführt wird am Anfang langsam, wird dann aber bei häufiger Nutzung Schritt für Schritt optimiert. 

Viele Optimierungen für PHP 7 haben sich die Sprachentwickler bei HHVM abgeschaut. Je nachdem, welchen Benchmarks man glaubt, ist PHP 7 ein bisschen schneller oder ein bisschen langsamer als HHVM. Jedenfalls hat die Existenz von HHVM dazu geführt, dass die Sprachentwickler von PHP aktuell einen so starken Fokus auf Performance-Optimierungen legen. 

Neben HHVM gibt es aktuell keine weiteren alternativen PHP-Laufzeiten, die für den Produktivbetrieb geeignet sind. Mit Quercus existiert eine Implementierung der Sprache, die in Java-Bytecode übersetzt werden kann, jedoch ist es um das Projekt eher ruhig geworden. Ebenfalls scheinbar nicht mehr aktiv ist das Projekt HippyVM, das eine alternative Implementierung basierend auf RPython/PyPy bietet. Beide Implementierungen haben deutliche Performance-Vorteile versprochen, sind aber immer weit davon entfernt gewesen, den vollen Sprach- und Funktionsumfang der offiziellen PHP-Implementierung zu erreichen.

## Schneller PHP-Code

Natürlich ist nicht nur die PHP-Implementierung für die Performance verantwortlich, sondern auch die vom Entwickler in PHP geschriebenen Skripte. Die massiven Performance-Schübe in den einzelnen PHP-Versionen machen jedoch sofort deutlich, dass die meisten Mikrooptimierungen für kleine Prozentpunkte Verbesserung überflüssig sind. Vor allen Dingen, weil Mikrooptimierungen basierend auf aktuellen Sprachdetails in der nächsten PHP-Version durch interne Optimierungen zunichte gemacht werden können. 

Ein Beispiel ist eine Optimierung, die wir vor einigen Jahren zu Zeiten von PHP 5.3 am Doctrine-ORM gemacht haben. Da Objekt-Instanzierung damals noch ineffizient und "teuer" war, haben wir ein Refaktoring zu einfachen Arrays/Hashtables vorgenommen. Mit PHP 5.4 war dieses Refaktoring bereits obsolet und die Implementierung mit Objekten wäre schneller gewesen. 

Es lassen sich insgesamt nur einige wenige pauschale Aussagen über PHP-Performance machen, die allgemeingültig sind. 

Offensichtlich sollte sein, dass native PHP-Funktionen in C schneller sind als dieselbe Funktionalität implementiert in PHP. Damit ist es bei rechenintensiven Algorithmen sinnvoll, sich über Datenstrukturen Gedanken zu machen, die mit Funktionen der Standardbibliothek bearbeitet werden können, anstatt reine Implementierungen in PHP vorzunehmen. 

Der Grund für den Performance-Unterschied ist offensichtlich: In C implementierte Funktionen können direkt auf den nativen C-Datenstrukturen arbeiten, während die Ausführung von PHP-Code immer über die virtuelle Maschine läuft und aufgrund der dynamischen Natur der Sprache einige Abstraktionslevel zu überwinden hat, bis die eigentliche Operation ausgeführt werden kann. 

Eine weiterer Faktor mit Auswirkungen auf PHP-Performance ist die Geschwindigkeit von Funktionsaufrufen. Da PHP keinen Just-in-time-Compiler wie HHVM hat, ist der Overhead eines PHP-Funktionsaufrufs immer gleich hoch und steigt in der Menge der pro Request ausgeführten Funktionen. Generell sind Programme mit weniger Funktionsaufrufen immer schneller als solche mit vielen Aufrufen. Das verleitet Entwickler leider dazu, mit Blick auf die Performance-Grundsätze gute Softwarequalität und Abstraktionen zu vernachlässigen. Doch möglicherweise ist dieses Problem in Zukunft auch nicht mehr relevant, falls es gelingt, auch für PHP einen JIT-Compiler wie für HHVM zu entwickeln, der performanceintensive Codepfade automatisch in Maschinencode übersetzt. 

Für PHP-Code gilt daher ebenso wie für Programme in allen anderen Sprachen, dass man Performance-Probleme besser mit einem Profiler misst und nicht einfach auf Basis von Bauchgefühlen Veränderungen und Optimierungen implementiert. Eine Reihe verschiedener Profiler kann dabei helfen. Am bekanntesten ist sicherlich XDebug ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[4]](http://www.informatik-aktuell.de/entwicklung/programmiersprachen/php-performance-entwicklungen-und-einflussfaktoren.html#c14746), eine Open Source-Extension für PHP, die Debugging und Profiling von PHP-Skripten ermöglicht. Der Profiler von XDebug ist sehr detailliert, hat jedoch auch einen signifikanten Overhead. Das kann dazu führen, dass sehr häufig ausgeführte Funktionen mit kurzer Laufzeit als viel langsamer eingestuft werden, als sie ohne die Verwendung des Profilers eigentlich sind. Alternativ kann man daher Profiler verwenden, die nicht so viel Overhead haben, dafür aber weniger Informationen sammeln. XHProf ist ein Open Source-Profiler für PHP, Tideways oder Blackfire sind zwei proprietäre Profiler ![Interner Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[4]](http://www.informatik-aktuell.de/entwicklung/programmiersprachen/php-performance-entwicklungen-und-einflussfaktoren.html#c14746).

## Ergebnis

PHP hat in den letzten Versionen signifikante Sprünge in der Performance gemacht und muss sich im Vergleich zu anderen dynamischen Sprachen wie Ruby oder Python nicht verstecken. Mit statischen Sprachen kann PHP natürlich trotzdem noch nicht mithalten, vor allen Dingen, so lange noch kein JIT für PHP existiert. Besonders gespannt sollte man trotzdem auf die Ergebnisse der TechEmpower-Benchmarks sein, wenn diese in Zukunft PHP 7 statt PHP 5 verwenden. Aus Entwicklersicht ist es wichtig, immer mit den aktuellsten PHP-Versionen zu arbeiten um von den Performance-Steigerungen zu profitieren.

Quellen

  1. ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[TechEmpower-Benchmarks](https://www.techempower.com/benchmarks/)
  2. ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Zend-Engine  ](https://en.wikipedia.org/wiki/Zend_Engine)
  3. ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[HHVM ](http://hhvm.com/)
  4. Profiler: ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[XDebug](http://xdebug.org/), ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[XHProf](http://xhprof.io/), ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Tideways](https://tideways.io/), ![Externer Link](http://www.informatik-aktuell.de/typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Blackfire](https://blackfire.io/)
