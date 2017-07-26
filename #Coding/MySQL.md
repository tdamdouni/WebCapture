# MySQL

_Captured: 2015-10-23 at 00:30 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/MySQL)_

![Logo von MySQL](http://upload.wikimedia.org/wikipedia/de/thumb/1/1f/Logo_MySQL.svg/250px-Logo_MySQL.svg.png)

> _[Logo von MySQL](https://de.m.wikipedia.org/w/index.php?title=Datei:Logo_MySQL.svg&filetimestamp=20070907102438&)_

**MySQL** [[ˌmaɪɛskjuːˈɛl](https://de.m.wikipedia.org/wiki/Liste_der_IPA-Zeichen)] ist eines der weltweit verbreitetsten [[3]](https://de.m.wikipedia.org/wiki/MySQL) [relationalen Datenbankverwaltungssysteme](https://de.m.wikipedia.org/wiki/Relationale_Datenbank). Es ist als [Open-Source](https://de.m.wikipedia.org/wiki/Open_Source)-Software sowie als kommerzielle Enterpriseversion fur verschiedene Betriebssysteme verfugbar und bildet die Grundlage fur viele [dynamische Webauftritte](https://de.m.wikipedia.org/wiki/Dynamische_Webseite).

MySQL wurde seit 1994 vom schwedischen Unternehmen [MySQL AB](https://de.m.wikipedia.org/wiki/MySQL_AB) entwickelt. Im Februar 2008 wurde MySQL AB vom Unternehmen [Sun Microsystems](https://de.m.wikipedia.org/wiki/Sun_Microsystems) ubernommen, das seinerseits im Januar 2010 von [Oracle](https://de.m.wikipedia.org/wiki/Oracle) gekauft wurde.

  * [Speichersubsysteme](https://de.m.wikipedia.org/wiki/MySQL)
    * [Offizielle Engines](https://de.m.wikipedia.org/wiki/MySQL)
  * [Partitionierung](https://de.m.wikipedia.org/wiki/MySQL)

MySQL ist mit rund 50 Millionen [Installationen](https://de.m.wikipedia.org/wiki/Installation_\(Computer\)) (Stand: 2013) das am meisten verbreitete [Open-Source](https://de.m.wikipedia.org/wiki/Open_Source)-Datenbankverwaltungssystem der Welt.[[4]](https://de.m.wikipedia.org/wiki/MySQL)

Ein bevorzugtes Einsatzgebiet von MySQL ist die Datenspeicherung fur [Webservices](https://de.m.wikipedia.org/wiki/Webservice). MySQL wird dabei haufig in Verbindung mit dem [Webserver](https://de.m.wikipedia.org/wiki/Webserver) [Apache](https://de.m.wikipedia.org/wiki/Apache_HTTP_Server) und der Skriptsprache [PHP](https://de.m.wikipedia.org/wiki/PHP) eingesetzt. Viele Webdienste bedienen sich dieser Architektur und betreiben je nach Große und Bedarf eine Vielzahl von MySQL-Servern, uber die die Zugriffe aus dem Netz abgewickelt werden.[[5]](https://de.m.wikipedia.org/wiki/MySQL) MySQL wird unter anderem verwendet von [Flickr](https://de.m.wikipedia.org/wiki/Flickr),[[6]](https://de.m.wikipedia.org/wiki/MySQL) [YouTube](https://de.m.wikipedia.org/wiki/YouTube),[[7]](https://de.m.wikipedia.org/wiki/MySQL) [Google](https://de.m.wikipedia.org/wiki/Google),[[8]](https://de.m.wikipedia.org/wiki/MySQL) [Facebook](https://de.m.wikipedia.org/wiki/Facebook)[[9]](https://de.m.wikipedia.org/wiki/MySQL)[[10]](https://de.m.wikipedia.org/wiki/MySQL) und [Twitter](https://de.m.wikipedia.org/wiki/Twitter).[[11]](https://de.m.wikipedia.org/wiki/MySQL) Daneben wird MySQL in vielen Produkten als [eingebettetes Datenbanksystem](https://de.m.wikipedia.org/wiki/Eingebettetes_Datenbanksystem) eingesetzt.[[12]](https://de.m.wikipedia.org/wiki/MySQL)

MySQL-Server und offizielle Bibliotheken sind zur Erzielung einer moglichst guten Performance hauptsachlich in [ANSI C](https://de.m.wikipedia.org/wiki/C_\(Programmiersprache\)) und [ANSI C++](https://de.m.wikipedia.org/wiki/C%2B%2B) implementiert.

MySQL ist auf vielen [Unix](https://de.m.wikipedia.org/wiki/Unix)-Varianten, [Mac OS X](https://de.m.wikipedia.org/wiki/Mac_OS_X) und [Linux](https://de.m.wikipedia.org/wiki/Linux), aber auch auf [Windows](https://de.m.wikipedia.org/wiki/Microsoft_Windows), [OS/2](https://de.m.wikipedia.org/wiki/OS/2) und [i5/OS](https://de.m.wikipedia.org/wiki/I5/OS) (ehemals OS/400) lauffahig. Seit Anfang 2008 gibt es auch eine [Symbian](https://de.m.wikipedia.org/wiki/Symbian-Plattform)-Variante.

MySQL sieht grundsatzlich einen MySQL-Server vor, auf dem Daten gespeichert sind, und einen oder mehrere MySQL-Clients, die Anfragen an den Server schicken, die dieser beantwortet.

Auf dem [Datenbankmanagementsystem](https://de.m.wikipedia.org/wiki/Datenbanksystem), dem MySQL-Server, konnen mehrere Datenbanken erstellt werden. In einer [Datenbank](https://de.m.wikipedia.org/wiki/Datenbank) konnen mehrere Tabellen angelegt werden. Praktisch erstellt MySQL dabei fur jede Datenbank einen Ordner auf der Festplatte, in dem Dateien fur die Struktur und die Daten der einzelnen Tabellen abgelegt werden. Das genaue Format dieser Dateien hangt von der fur die jeweilige Tabelle verwendeten Speicherengine ab.

Die Tabellen konnen jeweils von einem unterschiedlichen Typ sein. Der Tabellentyp legt fest, welche Speicherengine (Speichersubsystem) fur Anfragen an eine Tabelle verwendet wird. Jede Tabelle kann Spalten enthalten, in denen Daten eines festgelegten Datentyps gespeichert werden konnen (z. B. [Integer](https://de.m.wikipedia.org/wiki/Integer_\(Datentyp\)) (ganze Zahlen) oder [Strings](https://de.m.wikipedia.org/wiki/Zeichenkette) (Zeichenketten)). Die maximale Große der Tabellen wird grundsatzlich nur durch das [Betriebssystem](https://de.m.wikipedia.org/wiki/Betriebssystem) limitiert.

Ein Client kann Datenbankanfragen an einen MySQL-Server schicken. Dieser ist dafur zustandig, jede Anfrage moglichst performant zu bearbeiten. Dabei wird zunachst der Query-Cache befragt und bei nicht vorhandenem Ergebnis die Anfrage geparst, optimiert und schließlich ausgefuhrt; das Ergebnis wird dann zuruckgegeben.

Um die Performance zu verbessern, kann MySQL die Ergebnisse von Anfragen in einem Zwischenspeicher, dem Query-Cache, ablegen. Sollte spater eine identische Abfrage an den Server geschickt werden, ohne dass sich in der Zwischenzeit die Daten in der Datenbank verandert haben, wird sie aus dem Cache beantwortet. Es muss dann nicht auf die Datenbank selbst zugegriffen werden.[[13]](https://de.m.wikipedia.org/wiki/MySQL)

Soll eine Query ausgefuhrt werden, wird zunachst gepruft, ob ihre [Syntax](https://de.m.wikipedia.org/wiki/Syntax) gultig ist. Sie wird dazu in ihre einzelnen Komponenten zerlegt. Zugleich werden einige grundlegende Informationen uber die Query gesammelt, wie etwa die Art der Query (z. B. SELECT, INSERT, SET oder GRANT), die betroffenen Tabellen oder die Inhalte der WHERE-Klausel. Am Ende dieses Schrittes kennt MySQL den Parse-Baum, der danach optimiert werden kann.[[14]](https://de.m.wikipedia.org/wiki/MySQL)

Ist eine Abfrage syntaktisch gultig, dann wird sie als Nachstes optimiert. Dabei sucht der [Optimizer](https://de.m.wikipedia.org/wiki/Anfrageoptimierer) nach dem effizientesten Weg, die Query zu bearbeiten. Dazu wird hauptsachlich versucht, die Anzahl der zu lesenden Datensatze moglichst gering zu halten. Dies wird etwa, wenn Datensatze aus mehreren Tabellen gelesen werden mussen, durch eine geschickte Abfragereihenfolge ([JOIN](https://de.m.wikipedia.org/wiki/Relationale_Algebra)) der Tabellen erreicht; nicht benotigte Tabellen werden komplett aus dem JOIN entfernt. Der Optimizer berucksichtigt unter anderem, ob es sinnvoll ist, zur Lokalisierung der gesuchten Datensatze einen Index zu verwenden (und wenn ja, welchen), oder ob es performanter ware, stattdessen einen [Table-Scan](//en.wikipedia.org/wiki/Full_table_scan) durchzufuhren, d. h. die komplette Tabelle durchzulaufen.

Die zur Verfugung stehenden Alternativen werden vom Optimizer bewertet. Dabei wird aufgrund von [Heuristiken](https://de.m.wikipedia.org/wiki/Heuristik) fur jede Moglichkeit geschatzt, wie lange die Ausfuhrung benotigen wurde. Diejenige Alternative, die die geringsten Kosten hat, wird anschließend tatsachlich durchgefuhrt.

Die Arbeit des Optimizers lasst sich mit dem MySQL-Kommando EXPLAIN nachvollziehen. Dieser Befehl (gefolgt von einer bestimmten Query) beauftragt den Optimizer, seinen _Query-Plan_ zuruckzugeben. Als Ausgabe erhalt der Nutzer Informationen fur jeden Schritt, den der Optimizer zur Beantwortung der Query durchfuhren wurde. Auf diese Art lasst sich mit etwas Hintergrundwissen ermitteln, inwiefern die Query optimiert werden kann, so dass sie schneller ausgefuhrt werden kann.[[13]](https://de.m.wikipedia.org/wiki/MySQL)

[Michael Widenius](https://de.m.wikipedia.org/wiki/Michael_Widenius) und [David Axmark](https://de.m.wikipedia.org/w/index.php?title=David_Axmark&action=edit&redlink=1) begannen 1994 mit der Entwicklung von MySQL.[[15]](https://de.m.wikipedia.org/wiki/MySQL) Es wurde zunachst als Clone fur [mSQL](https://de.m.wikipedia.org/w/index.php?title=MSQL&action=edit&redlink=1) entwickelt, um Datenbanken des maskengesteuerten Datenbanksystems [UNIREG](https://de.m.wikipedia.org/w/index.php?title=UNIREG&action=edit&redlink=1) in Web-Anwendungen verfugbar zu machen. (UNIREG war 1979 von Michael Widenius entwickelt und ca. 1986 in die Programmiersprache C umgeschrieben worden, damit es auch unter UNIX-Systemen lief.) MySQL war daher sowohl zu mSQL als auch UNIREG voll kompatibel.

Der Name _MySQL_ setzt sich zusammen aus dem Vornamen _[My](https://de.m.wikipedia.org/wiki/My_\(Vorname\))_, den die Tochter des MySQL AB Mitbegrunders [Michael Widenius](https://de.m.wikipedia.org/wiki/Michael_Widenius) tragt, und [SQL](https://de.m.wikipedia.org/wiki/SQL).[[16]](https://de.m.wikipedia.org/wiki/MySQL)

Nach einem internen Release am 23. Mai 1995 wurde die Software im Jahr 1997 sofort unter der Versionsnummer 3.1 veroffentlicht, um zu signalisieren, dass sie auf einem Kern basiert, der schon eine lange Geschichte hat. Sie war von Anfang an fur große Datenmengen und sehr gute Performance ausgelegt, teils auf Kosten von Stabilitat und Verfugbarkeit. Der Funktionsumfang hingegen war zunachst beschrankt. So gab es nur wenige Tabellentypen und keine Transaktionen. Typischerweise werden neue Eigenschaften auf Wunsch der Anwender implementiert, die dadurch ein sehr großes „Mitspracherecht" haben.

Mit der im Januar 2001 veroffentlichten Version 3.23 verfugte MySQL uber zwei Tabellentypen mit [Transaktionen](https://de.m.wikipedia.org/wiki/Transaktion_\(Informatik\)), wobei der eine ([InnoDB](https://de.m.wikipedia.org/wiki/InnoDB)) den [ACID](https://de.m.wikipedia.org/wiki/ACID)-Kriterien genugt. Alle Operationen, die allgemeine SQL-Eigenschaften betreffen, sind fur alle Tabellentypen gleich, wahrend die Eigenschaften der Tabellentypen aufgrund der unterschiedlichen Architektur sehr verschieden sein konnen. So besitzt der Typ [MyISAM](https://de.m.wikipedia.org/wiki/MyISAM) bereits seit der fruhen Version 3.23 eine sehr leistungsfahige Volltext-Suche, die beim Typ InnoDB nicht implementiert ist. Neu in Version 3.23 ist ebenfalls das Replikationssystem. Es ist fur den Einsatz in einem [Rechnerverbund](https://de.m.wikipedia.org/wiki/Rechnerverbund) ausgelegt und bietet sich fur einen [unterbrechungsfreien](https://de.m.wikipedia.org/w/index.php?title=Unterbrechungsfrei&action=edit&redlink=1) Betrieb an. Dabei sind dem [Datenbankmanagementsystem](https://de.m.wikipedia.org/wiki/Datenbanksystem) (DBMS) mehrere Datenbanken auf unterschiedlichen Rechnerknoten zugeordnet. Eine der Datenbanken fungiert als Master; hier werden die Datenbankinhalte verandert. Das Replikationssystem verteilt anschließend die datenverandernden SQL-Kommandos auf die anderen Datenbanken, die diese Änderungen lokal auf ihren Tabellen nachvollziehen. Es handelt sich hierbei also um eine asynchrone [Replikation](https://de.m.wikipedia.org/wiki/Replikation_\(Datenverarbeitung\)) der SQL-Kommandos. Mit dem [MySQL Cluster](https://de.m.wikipedia.org/wiki/MySQL_Cluster) steht ein Tabellentyp zur Verfugung, bei dem die gesamte Datenbank im Arbeitsspeicher als [In-Memory-Datenbank](https://de.m.wikipedia.org/wiki/In-Memory-Datenbank) vorgehalten werden kann. Es wird synchrone Replikation zwischen allen Clusterknoten und Transaktionsverarbeitung unterstutzt, jedoch keine Volltextsuche.

MySQL 4.0, das im Marz 2003 freigegeben wurde, erlaubt die Nutzung von _Unions_ und fuhrte einen Query-Cache ein, der die Ergebnisse haufig benutzter SQL-Anfragen zwischenspeichert.[[17]](https://de.m.wikipedia.org/wiki/MySQL)

Im Oktober 2004 wurde MySQL 4.1 veroffentlicht. Es bietet eine Datenspeicherung in unterschiedlichen Zeichensatzen pro Tabelle an; unter anderem wird auch [Unicode](https://de.m.wikipedia.org/wiki/Unicode) unterstutzt. Unterabfragen (Subqueries/Subselects) sind moglich.[[18]](https://de.m.wikipedia.org/wiki/MySQL)

Version 5.0 wurde im Oktober 2005 freigegeben. Sie unterstutzt alle im [SQL3-Standard](https://de.m.wikipedia.org/w/index.php?title=SQL3-Standard&action=edit&redlink=1) definierten Objekttypen. Neu in Version 5 ist dabei die Unterstutzung von [Views](https://de.m.wikipedia.org/wiki/Sicht_\(Datenbank\)), [Triggern](https://de.m.wikipedia.org/wiki/Datenbanktrigger), [Stored Procedures](https://de.m.wikipedia.org/wiki/Stored_Procedure) und [User Defined Functions](https://de.m.wikipedia.org/wiki/User_Defined_Function).

Im Februar 2008 ubernahm Sun Microsystems MySQL AB. Als Kaufwert wird eine Milliarde Dollar genannt; davon 200 Millionen in Aktienoptionen.[[19]](https://de.m.wikipedia.org/wiki/MySQL)[[20]](https://de.m.wikipedia.org/wiki/MySQL)

Im November 2008[[21]](https://de.m.wikipedia.org/wiki/MySQL) wurde MySQL 5.1 freigegeben. Zu den Neuerungen zahlen außer [Partitionsfunktionen](https://de.m.wikipedia.org/wiki/Denormalisierung), mit denen sehr große Tabellen in mehrere physikalische Dateien aufgeteilt werden konnen, ein Event-Scheduler, mit dessen Hilfe zuvor definierte SQL-Kommandos in regelmaßigen Zeitabstanden ausgefuhrt werden konnen, sowie Funktionen des Instanzenmanagers. Die API wurde uberarbeitet, so dass nun das Laden und Entladen von Komponenten wahrend der Laufzeit und ohne Neustart des Servers moglich ist.[[22]](https://de.m.wikipedia.org/wiki/MySQL)

Im Januar 2010 wurde Sun Microsystems von Oracle gekauft.[[23]](https://de.m.wikipedia.org/wiki/MySQL) Wenige Monate spater gab Oracle bekannt, dass die bereits von MySQL AB begonnene Entwicklung der Datenbank-Engine [Falcon](https://de.m.wikipedia.org/w/index.php?title=Falcon_\(Datenbank\)&action=edit&redlink=1) eingestellt wird.

Ende 2010 wurde MySQL 5.5 veroffentlicht. InnoDB wurde zur Standard-Speicherengine. Die Performance wurde durch die Nutzung von asynchronem I/O verbessert. Neu sind auch die Kommandos SIGNAL/RESIGNAL, die standardkonforme Fehlerbehandlung in Stored Procedures erlauben.[[24]](https://de.m.wikipedia.org/wiki/MySQL)[[25]](https://de.m.wikipedia.org/wiki/MySQL)

Das im Jahr 2012 veroffentlichte MySQL 5.6 umfasst u. a. [Memcached](https://de.m.wikipedia.org/wiki/Memcached) [APIs](https://de.m.wikipedia.org/wiki/Programmierschnittstelle), globale Transaktions-IDs und Verbesserungen am PERFORMANCE_SCHEMA.[[26]](https://de.m.wikipedia.org/wiki/MySQL)

Seit der Übernahme von MySQL AB von Sun durch Oracle steht das Datenbanksystem immer haufiger in der Kritik. Der Unterschied zwischen der freien und kommerziellen Version von MySQL wird immer gravierender.[[27]](https://de.m.wikipedia.org/wiki/MySQL) Neue Funktionen sind haufig nur noch in der kommerziellen Version von MySQL enthalten, dazu kommen nicht-offentliche Fehlermeldungen, veraltete Bazaar-Archive und fehlende Tests fur die Fehlersuche.[[28]](https://de.m.wikipedia.org/wiki/MySQL)

Seit Ende 2012 erodiert auch der Ruckhalt in der OpenSource-Gemeinschaft fur MySQL. Nach [Fedora](https://de.m.wikipedia.org/wiki/Fedora_\(Linux-Distribution\)) und [OpenSUSE](https://de.m.wikipedia.org/wiki/OpenSUSE) haben Anfang 2013 auch [Slackware](https://de.m.wikipedia.org/wiki/Slackware) und [Arch Linux](https://de.m.wikipedia.org/wiki/Arch_Linux) das MySQL-Paket durch [MariaDB](https://de.m.wikipedia.org/wiki/MariaDB) ersetzt. Ausloser seien der mangelnde Respekt gegenuber der Gemeinschaft und die zunehmend abgeschottete Entwicklung des RDBMS.[[29]](https://de.m.wikipedia.org/wiki/MySQL)[[30]](https://de.m.wikipedia.org/wiki/MySQL) Ebenso wechselte die [Wikimedia](https://de.m.wikipedia.org/wiki/Wikimedia)-Foundation Anfang 2013 zu MariaDB.

Jaroslav Reznik, Red Hats Fedora-Projekt-Manager erklarte, dass sich MySQL in Richtung eines geschlossenen Projektes entwickle. Alle nutzlichen Informationen zu Sicherheitsfragen (CVEs) wurden nicht mehr veroffentlicht. Es existierten keine vollstandigen Regressionstests mehr und ein sehr großer Teil der MySQL-Bug-Datenbank sei nun nicht mehr offentlich.[[31]](https://de.m.wikipedia.org/wiki/MySQL)

Michael Widenius, der ehemalige Grunder von MySQL AB kritisiert Oracle scharf: Oracle habe klargemacht, dass sie kein Interesse an Open Source hatten, die Zusammenarbeit mit der Community ablehnten und auch MySQL im Allgemeinen nicht mogen wurden. Als Beispiele fur die Missachtung der Open-Source-Prinzipien nennt er die kommerziellen Erweiterungen fur MySQL, die inzwischen nichtoffentliche Fehler-Datenbank und den Mangel an Testfallen fur neuen MySQL-Code. Vorzeige-Funktionen, wie das Online-Backup und Fremdschlussel fur alle Speicher-Engines, die fur MySQL 6.0 versprochen wurden, seien nicht veroffentlicht worden, obwohl sie fertig entwickelt und bereit seien. Statt Fehler zu beheben, entferne Oracle Funktionen. Die meisten der ursprunglichen MySQL-Entwickler hatten Oracle verlassen. Als weitere Beweise fur die „Verachtung" der MySQL-Anwender nennt er den „scharfen" Anstieg der Lizenz- und Support-Gebuhren und das Fehlen einer offenen Roadmap.[[32]](https://de.m.wikipedia.org/wiki/MySQL)

MySQL bietet verschiedene Speichersubsysteme (Engines) an. Jede Engine ist fur ein spezielles Einsatz-Szenario optimiert. Im Vergleich zu der traditionellen Mehrschichtenarchitektur von Datenbanksystemen sind die Engines kein reines Speichersubsystem, sondern bieten mehr Funktionalitat. So liegt die Verwaltung von Transaktionen, von Indizes und referenziellen Integritaten in der Hand der Engine.

Die einzelnen Speicherengines unterstutzen unterschiedliche Funktionen und weisen je nach Einsatzgebiet eine unterschiedliche Performance auf. Je nachdem, wozu eine Tabelle benutzt wird (z. B. hauptsachlich lesende SELECT-Anfragen oder hauptsachlich schreibende INSERT/UPDATE-Anfragen), sollte eine passende Speicherengine gewahlt werden. Ein anderes Kriterium fur die Wahl der Speicherengine kann auch die Notwendigkeit sein, eine bestimmte Funktion zu nutzen, wie z. B. [Transaktionen](https://de.m.wikipedia.org/wiki/Transaktion_\(Informatik\)) oder referenzielle Integritat.

MySQL kann auch um eigene Speicherengines erweitert werden.[[33]](https://de.m.wikipedia.org/wiki/MySQL) Neben den von MySQL veroffentlichten und mit MySQL mitgelieferten Engines gibt es auch Engines anderer Hersteller.

MyISAM bietet schnellen Zugriff auf Tabellen und Indizes ohne Transaktionssicherung. Parallele Datenbankzugriffe (Concurrency) verwaltet MySQL auf Tabellenebene, das heißt die komplette Tabelle wird je nach Sperrungsart fur bestimmte Operationen gesperrt (Read- oder Write-[Lock](https://de.m.wikipedia.org/wiki/Lock)). Eine Vielzahl von simultanen Lesezugriffen ist moglich, da Lesezugriffe nur sogenannte READ-Locks akquirieren. Diese erlauben es anderen „READERN", auf den gleichen Datensatz gleichzeitig zuzugreifen. Schreibzugriffe mussen allerdings warten, bis alle gegenwartigen „READER" ihre Leseoperationen abgeschlossen haben und damit ihren READ-Lock freigeben. Ein „READER" muss somit nur andere „WRITER" blocken.

Ein Datensatz, der geandert wird, kann weder gelesen noch anderweitig geschrieben werden. Somit muss ein „WRITER" (schreibender Zugriff auf Daten) andere „READER" und „WRITER" blocken. Dies geschieht durch einen „Write-Lock". Auch dieser findet auf Tabellenebene statt, somit kann in dieser Zeit weder lesend noch schreibend auf die gesamte Tabelle zugegriffen werden, bis der „Write-Lock" aufgehoben wird.

Fur einen Querymix, der vor allem aus Lesezugriffen besteht, ist MyISAM eine sehr effiziente Speicher-Engine. Weitere Vorteile von MyISAM sind:

  * flexibelste Autoincrement-Eigenschaft aller Speicherengines
  * MyISAM-Tabellen konnen in komprimierte read-only Tabellen konvertiert werden
  * MyISAM-Tabellen konnen feste Zeilenlange haben, die eine schnellere Zeilensuche ermoglicht
  * MyISAM-Tabellen konnen verwendet werden, um MERGE Tabellen zu erstellen
  * MyISAM ist hoch portierbar, da die Tabellendateien (.frm Datei (Tabellenstruktur), .MYD (Datendatei), .MYI (Indexdatei)) auf eine andere Maschine kopiert werden konnen und dort sofort als Datenbanktabellen zur Verfugung stehen.
  * Machtige Volltextsuche

MySQL verwaltet die Zugriffsrechte uber Grant-Tabellen in der Datenbank mysql, die (auch in der neuesten Version) ausschließlich in MyISAM-Tabellen gespeichert werden. MyISAM kann beim Kompilieren oder Serverstart deshalb nicht ausgeschlossen werden. Bis MySQL Version 5.1 war MyISAM außerdem die Standard-Speicher-Engine, danach nahm InnoDB diesen Platz ein.

[InnoDB](https://de.m.wikipedia.org/wiki/InnoDB) bietet transaktionssichere Lese- und Schreibzugriffe, d. h. es bietet Beginn-, Commit- und Rollback-Funktionen. Dadurch wird sichergestellt, dass eine Abfrage oder ein Satz zusammengehoriger Abfragen entweder ganz oder gar nicht, nicht aber unvollstandig ausgefuhrt wird. Die gewunschte Isolationsebene der Transaktionen kann eingestellt werden. Dadurch kann die Sicherheit der vollstandigen und korrekten Ausfuhrung verringert werden, was sich positiv auf die Ausfuhrungsgeschwindigkeit auswirkt.

InnoDB bietet ferner die Moglichkeit, Fremdschlussel-Beziehungen zu uberprufen. Seit MySQL 5.5 ist InnoDB die Standard-Speicher-Engine.[[24]](https://de.m.wikipedia.org/wiki/MySQL) Ab MySQL 5.6 wird auch in InnoDB-Tabellen eine Volltextsuche moglich sein.[[34]](https://de.m.wikipedia.org/wiki/MySQL) Jedoch erfullt InnoDB den SQL3-Standard nicht vollstandig: Fremdschlussel werden nur eingeschrankt unterstutzt.[[35]](https://de.m.wikipedia.org/wiki/MySQL)

InnoDB speichert die Tabellenstruktur in einzelnen frm-Dateien, Nutzdaten und Indizes in einem Tabellenraum. Der Tabellenraum wird vor Beginn der Arbeit mit dem Datenbankserver eingestellt und kann sich uber eine oder mehrere Dateien erstrecken. Die Dateien des Tabellenraums konnen auf verschiedene Verzeichnisse verteilt werden. Die Konfiguration des Tabellenraums kann nicht nachtraglich angepasst werden, ohne Datenverlust zu riskieren. Nach einer Änderung der Konfiguration des Tabellenraums wird die gesamte Datenbank von einer Sicherungskopie wiederhergestellt.

MERGE bietet die Moglichkeit, mehrere Tabellen vom Typ MyISAM mit gleicher Struktur zu einer Tabelle zusammenzufassen und die Zugriffe darauf auszufuhren. Dabei konnen komprimierte MyISAM- mit nicht-komprimierten MyISAM-Tabellen zusammengefasst werden. Auf diese Weise lasst sich Datenarchivierung realisieren.

Management von temporaren Tabellen. Die Definition der Tabellen wird auf der Festplatte permanent gespeichert. Die Daten werden im Arbeitsspeicher gespeichert. Es werden jedoch nicht alle Datentypen unterstutzt. Bei einem Neustarten des Servers sind die Tabellenstrukturen noch vorhanden, die Inhalte mussen neu eingelesen werden, beispielsweise aus permanenten Tabellen. Es sind spezielle Verfahren zur Speicherplatz-Verwaltung implementiert, um den Platz von geloschten Satzen bei der nachsten Einfugung wiederzuverwenden.

Code-Beispiel fur die Entwicklung einer eigenen Speicher-Engine. EXAMPLE hat Funktionen zum Erstellen einer Tabelle, die Funktionen zum Schreiben und Lesen der Datensatze sind nur angedeutet. Ein SELECT-Statement liefert immer eine leere Ergebnismenge.

BDB ist die Abkurzung fur [Berkeley DataBase](https://de.m.wikipedia.org/wiki/Berkeley_DB). Diese Speicher-Engine wurde von [Sleepycat Software](https://de.m.wikipedia.org/wiki/Sleepycat_Software) entwickelt und spater an [Oracle](https://de.m.wikipedia.org/wiki/Oracle) verkauft. Die BDB bietet Transaktionssicherheit und besondere Vorkehrungen, damit bei einem Systemausfall die gespeicherten Daten erhalten bleiben.

Die BDB-Speicher-Engine wird seit Version 5.1 nicht mehr weiter unterstutzt.

Die FEDERATED-Engine bietet Zugriff auf Tabellen, die auf einem anderen Server liegen. Wenn man eine Tabelle vom Typ FEDERATED erstellt, dann muss die entfernte Tabelle auf dem anderen Server bereits existieren. Der lokale Server verhalt sich wie ein Client, der auf den entfernten Server zugreift. Die FEDERATED-Engine verhalt sich wie ein [foderiertes Informationssystem](https://de.m.wikipedia.org/wiki/F%C3%B6deriertes_Informationssystem), das bedeutet, dass sie die Daten selber nicht speichert, sondern Zugriff auf den fernen Server gewahrt, wahrend auf diesem ebenfalls auf die Daten zugegriffen werden kann. Bei der Version 5.0 kann nur auf andere MySQL-Server zugegriffen werden.

Die Zugangsdaten zu dem entfernten Datenbankserver werden dabei unverschlusselt in der lokalen frm-Datei gespeichert. Der Zugriff auf das Datenverzeichnis muss auf der Betriebssystemebene eingeschrankt werden um das Auslesen der Zugriffsrechte durch Unbefugte zu verhindern.

Die ARCHIVE-Engine ist fur die Speicherung von großen Datenmengen bei einem moglichst sparsamen Umgang mit dem zur Verfugung stehenden Speicherplatz konzipiert. Es konnen keine Indizes erstellt werden. Nur die Zugriffe INSERT und SELECT werden unterstutzt. Der schnelle Zugriff auf die Daten steht hier nicht im Vordergrund.

Vor dem Speichern der Daten auf dem Speichermedium werden diese zunachst in einem Kompressionspuffer gesammelt. Wenn eine Serie von Einfuge-Operationen beendet wird, wird der optimale [Kompressionsalgorithmus](https://de.m.wikipedia.org/wiki/Datenkompression) ermittelt und die Daten werden komprimiert ausgegeben.

Falls wahrend einer Sequenz von Einfuge-Operationen von einem anderen Benutzer eine SELECT-Anfrage kommt, wird eine vorzeitige Kompression und Ausgabe der im Kompressionspuffer gespeicherten Daten erzwungen.

Bei der CSV-Engine werden die Daten im [CSV-Format](https://de.m.wikipedia.org/wiki/CSV_\(Dateiformat\)) gespeichert: Zahlen werden nicht binar, sondern als Ziffernfolgen gespeichert; die einzelnen Werte werden durch Kommata getrennt.

BLACKHOLE wurde entwickelt, um die Syntax von SQL-Statements zu prufen und ein Binarlog zu schreiben. Die Daten werden nicht gespeichert. Dadurch konnen Syntaxprufungen von SQL-Statements ausgefuhrt werden, ohne dass Speicherplatz zum Speichern der Daten bereitgestellt werden muss. Die Ausgabe des Binarlogs kann uber einen Parameter aktiviert und deaktiviert werden.

Die BLACKHOLE-Engine ist ideal fur die folgenden Aufgaben:

  * Syntaxprufung von Dump-Dateien
  * Testen der Datenreplikation durch anschließenden Vergleich der Binarlogs auf dem Master-Server und dem Slave-Server.
  * Zeitmessungen zur Bestimmung des Aufwands fur das Schreiben des Binarlogs.

NDB ist die Abkurzung fur **N**etwork **D**ata **B**ase. Die NDB-Speicher-Engine ist eine unabhangige Komponente, die die persistente Speicherung von Daten ermoglicht und fur die Koordination aller Zugriffe auf Datenknoten in einem [MySQL Cluster](https://de.m.wikipedia.org/wiki/MySQL_Cluster) zustandig ist.[[36]](https://de.m.wikipedia.org/wiki/MySQL) Anwendungen konnen direkt auf die NDB-Speicher-Engine uber die NDB-API oder uber einen MySQL-Knoten zugreifen. Der Zugriff uber einen MySQL-Knoten ist fur Anwendungsprogrammierer wesentlich einfacher zu gestalten, da in diesem Fall Standard-SQL-Befehle verwendet werden konnen und das Erlernen der NDB-Spezialitaten nicht notwendig ist.

Die NDB-API ist eine [multithreading](https://de.m.wikipedia.org/wiki/Multithreading)-fahige Schnittstelle zur Annahme aller ankommenden Datenanfragen.[[36]](https://de.m.wikipedia.org/wiki/MySQL) Fur jede Anfrage werden ein oder mehrere Threads gestartet. Auf die NDB-API ist nur ein sequenzieller Zugriff moglich, wodurch die Leistung des Clusters bei sehr vielen ankommenden Anfragen vermutlich eingeschrankt wird.

Neben den offiziellen Engines bieten mehrere Hersteller auch andere Engines mit anderen Eigenschaften oder Zusatzfunktionen. Einige seien hier beispielhaft erwahnt.

Die Revision Engine von _DDEngine_ fugt eine automatische Versionierung als Plugin auf Ebene einer Speicherengine hinzu. Neben dem reinen Speichern von Daten kann diese Engine dadurch gewahrleisten, dass Daten so wieder herstellbar sind, wie sie zu einem bestimmten Zeitpunkt waren. Diese Eigenschaft kann z. B. genutzt werden um den Verlauf von Produkteigenschaften zu speichern oder um gesetzliche Auflagen zu erfullen. Um die Daten physisch zu speichern, werden die mitgelieferten Storage-Engines benutzt.[[37]](https://de.m.wikipedia.org/wiki/MySQL)

Die Firma Infobright[[38]](https://de.m.wikipedia.org/wiki/MySQL) stellt die Brighthouse Engine zur Verfugung. Sie ist fur [Datawarehouse](https://de.m.wikipedia.org/wiki/Datawarehouse)-Anwendungen konzipiert und auf die Verarbeitung besonders großer Datenmengen ausgerichtet. Indizes werden nicht unterstutzt. Die Daten werden komprimiert gespeichert, wodurch nach Angaben des Herstellers bis zu 90 % des Speicherplatzes eingespart werden konnen.[[39]](https://de.m.wikipedia.org/wiki/MySQL)

Seit der Version 5.1 konnen MySQL-Tabellen [partitioniert](https://de.m.wikipedia.org/wiki/Denormalisierung) werden. Es stehen mehrere Partitionierungsarten zur Auswahl.[[40]](https://de.m.wikipedia.org/wiki/MySQL)

Bei der Range-Partitionierung werden Wertebereiche fur die einzelnen Partitionen definiert.

In dem Beispiel wird eine Tabelle mit drei Partitionen erstellt. Die Spalte 'region' darf bei dieser Syntax nur Werte kleiner als 30 erhalten.
    
    
    CREATE TABLE `kunde` (
      region int NOT NULL,
      nr int NOT NULL,
      name char(30),
      ed date NOT NULL
    )
    PARTITION BY range(region) (
      PARTITION p0 VALUES LESS THAN (10),
      PARTITION p1 VALUES LESS THAN (20),
      PARTITION p2 VALUES LESS THAN (30)
    );
    

Die Partitionierung kann auch durch einen Ausdruck ermittelt werden. Der Ausdruck muss einen Integer-Wert als Ergebnis generieren. Wenn die letzte Partition mit dem Wert 'maxvalue' definiert wird, damit kann man in die Spalte 'region' (Beispiel oben) alle Integer-Zahlen einfugen bzw. in der Spalte 'ed' (Beispiel unten) alle Datumswerte einfugen.
    
    
    CREATE TABLE `kunde` (
      region int NOT NULL,
      nr int NOT NULL,
      name char(30),
      ed date NOT NULL
    )
    PARTITION BY range(year(ed)) (
      PARTITION p0 VALUES LESS THAN (1990),
      PARTITION p1 VALUES LESS THAN (2000),
      PARTITION p2 VALUES LESS THAN maxvalue
    );
    

Bei der List-Partition werden die Werte einzeln aufgezahlt.

Beispiel:
    
    
    CREATE TABLE `kunde` (
      region int NOT NULL,
      nr int NOT NULL,
      name char(30),
      ed date NOT NULL
    )
    PARTITION BY list(region) (
      PARTITION p0 VALUES IN (1, 3, 5 ),
      PARTITION p1 VALUES IN (2, 4, 6 ),
      PARTITION p2 VALUES IN (10, 11, 12 )
    );
    

Bei der Hash-Partitionierung wird die Verteilung der Satze auf die einzelnen Partitionen vom DBMS ermittelt. Bei der regularen Hash-Partitionierung wird die [Modulo-Funktion](https://de.m.wikipedia.org/wiki/Modulo_\(Rest\)) als [Hashfunktion](https://de.m.wikipedia.org/wiki/Hashfunktion) verwendet (Region modulo 4). Sie hat den Vorteil, dass in der Spalte 'region' alle Integer-Zahlen eingefugt werden konnen.
    
    
    CREATE TABLE `kunde` (
      region int NOT NULL,
      nr int NOT NULL,
      name char(30),
      ed date NOT NULL
    ) 
    PARTITION BY hash(region) PARTITIONS 4;
    

Es gibt auch eine 'Lineare' Hash-Partitionierung. Dabei kommt eine andere [Hashfunktion](https://de.m.wikipedia.org/wiki/Hashfunktion) zum Einsatz.

Bei der Key-Partitionierung wird implizit eine [Hashfunktion](https://de.m.wikipedia.org/wiki/Hashfunktion) verwendet. Als Input fur die Funktion dient der Primarschlussel der Tabelle.
    
    
    CREATE TABLE `kunde` (
      nr int NOT NULL primary key,
      name char(30),
      ed date NOT NULL
    )
    PARTITION BY key() PARTITIONS 4;
    

Die Key-Partitionierung wird bei der Speicherengine _NDB_ implizit bei allen Tabellen verwendet. Das erleichtert die interne Koordination der Replikation.

Bei jeder Art von Partitionierung konnen zusatzlich 'Subpartitions' definiert werden. Dadurch ist eine noch granularere Aufteilung der Daten moglich.

Unter Linux installiert sich MySQL in das Verzeichnis _/var/lib/mysql/_. Unter Windows legt der Nutzer den Ablageort der Datendateien fest - Standard ist der Ordner _%ProgramFiles%\MySQL_. Grundeinstellungen werden durch den Administrator in der Datei _my.cnf_ vorgenommen.

Zur Verwaltung von MySQL-Datenbanken dient der mitgelieferte Kommandozeilen-Client (Kommandos `mysql` und `mysqladmin`). Zum Funktionsumfang gehoren außerdem die folgenden [Kommandozeilenwerkzeuge](https://de.m.wikipedia.org/wiki/Kommandozeile):

mysqlimport
    kann als Ersatz fur 'LOAD DATA INFILE …' verwendet werden. Durch Angabe von Parametern konnen sich Benutzer anmelden und das Verhalten des Programms steuern.
mysqldump
    kann als Ersatz fur 'SELECT * INTO OUTFILE' verwendet werden. Zusatzlich kann die Tabellenstruktur als Dump ausgegeben werden. Durch Angabe von Parametern konnen sich Benutzer anmelden und das Verhalten des Programms steuern.
    zeigt zu Fehlercodes erweiterte Informationen an. Als Parameter wird beim Programmstart der Errorcode benotigt.
mysqlshow
    gibt Metadaten zu Datenbanken, Tabellen oder einzelnen Tabellenspalten aus.

Als grafische Verwaltungssoftware bietet Oracle die Software [MySQL Workbench](https://de.m.wikipedia.org/wiki/MySQL_Workbench) an. Sie ist fur die Betriebssysteme [Windows](https://de.m.wikipedia.org/wiki/Microsoft_Windows), [Mac OS X](https://de.m.wikipedia.org/wiki/Mac_OS_X) und [Linux](https://de.m.wikipedia.org/wiki/Linux) verfugbar.

Eine von vielen Alternativen ist die in der Skriptsprache [PHP](https://de.m.wikipedia.org/wiki/PHP) geschriebene Open-Source-Anwendung [phpMyAdmin](https://de.m.wikipedia.org/wiki/PhpMyAdmin). Die [grafische Benutzeroberflache](https://de.m.wikipedia.org/wiki/Grafische_Benutzeroberfl%C3%A4che) lasst sich uber einen [Browser](https://de.m.wikipedia.org/wiki/Webbrowser) bedienen. phpMyAdmin wird hauptsachlich zur Verwaltung von MySQL-Datenbanken auf Webservern verwendet, auf denen die einzelnen Benutzer keine Rechte haben, `mysql` und `mysqladmin` direkt auszufuhren. Zum Erstellen und Verwalten von Backups der Datenbanken auf Webservern werden - wenn keine Rechte fur die Ausfuhrung von `mysqldump` vorliegen - haufig die ebenfalls in PHP geschriebenen Open-Source-Anwendungen [phpMyBackupPro](https://de.m.wikipedia.org/wiki/PhpMyBackupPro) oder [MySQLDumper](https://de.m.wikipedia.org/wiki/MySQLDumper) eingesetzt.

Fur den Vertrieb von MySQL Server verwendet Oracle ein [duales Lizenzsystem](https://de.m.wikipedia.org/wiki/Mehrfachlizenzierung): Einerseits ist das Programm eine [freie Software](https://de.m.wikipedia.org/wiki/Freie_Software), die unter der [General Public License (GPL)](https://de.m.wikipedia.org/wiki/GNU_General_Public_License) steht, andererseits wird es auch unter einer kommerziellen [Lizenz](https://de.m.wikipedia.org/wiki/Lizenz) angeboten.

Unterstutzung fur den Einsatz von MySQL bietet zunachst das offizielle Handbuch.[[41]](https://de.m.wikipedia.org/wiki/MySQL) Außerdem gibt es mehrere Foren und [IRC](https://de.m.wikipedia.org/wiki/Internet_Relay_Chat)-Channels, in denen Fragen kostenlos beantwortet werden.

Daneben bietet Oracle auch kostenpflichtige Support-Lizenzen in drei Leistungsstufen an: MySQL Enterprise Silver, Gold und Platinum.[[42]](https://de.m.wikipedia.org/wiki/MySQL) Sie unterscheiden sich in Leistungsumfang und Preis.[[43]](https://de.m.wikipedia.org/wiki/MySQL)[[44]](https://de.m.wikipedia.org/wiki/MySQL)

Von MySQL wurde das Datenbank-Projekt [MariaDB](https://de.m.wikipedia.org/wiki/MariaDB) abgespalten, das es sich zum Ziel gesetzt hat, den fur MySQL verwendeten Quellcode weiterhin frei zur Verfugung zu stellen und aktiv auch fur OpenSource-Nutzer weiterzuentwickeln. Im Jahr 2008 folgte mit [Drizzle](https://de.m.wikipedia.org/w/index.php?title=Drizzle&action=edit&redlink=1) ein weiterer [Fork](https://de.m.wikipedia.org/wiki/Abspaltung_\(Softwareentwicklung\)).[[45]](https://de.m.wikipedia.org/wiki/MySQL)[[46]](https://de.m.wikipedia.org/wiki/MySQL)[[47]](https://de.m.wikipedia.org/wiki/MySQL) [MySQL Cluster](https://de.m.wikipedia.org/wiki/MySQL_Cluster) ermoglicht die Installation von MySQL auf einem Computercluster in einer [Shared Nothing Architecture](https://de.m.wikipedia.org/wiki/Shared_Nothing_Architecture).

  1. ↑ [a](https://de.m.wikipedia.org/wiki/MySQL) [b](https://de.m.wikipedia.org/wiki/MySQL) Fur weitere Details siehe vor allem Sasha Pachev: Understanding MySQL Internals, Chapter 9: Parser and Optimizer, O'Reilly
  2. ↑ Die fur das Parsing zustandigen Module befinden sich in den Dateien sql/sql_yacc.yy, sql/gen_lex_hash.cc and sql/gen_lex.cc.
  * Baron Schwartz, Peter Zaitsev, Vadim Tkachenko: _MySQL High Performance_, 3. Auflage, O'Reilly, 2012, [ISBN 978-1-4493-1428-6](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/9781449314286).
  * [Michael Kofler](https://de.m.wikipedia.org/wiki/Michael_Kofler): _MySQL. Einfuhrung, Programmierung, Referenz._ Programmer's Choice. 3., uberarb. u. erw. Aufl. 2005, [ISBN 3-8273-2253-7](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3827322537).
  * Stefan Proll, Eva Zangerle, Wolfgang Gassler: _MySQL: Das Handbuch fur Administratoren_. Galileo Computing, 2011, [ISBN 978-3-8362-1715-6](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/9783836217156).
