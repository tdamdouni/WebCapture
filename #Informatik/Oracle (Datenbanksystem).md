# Oracle (Datenbanksystem)

_Captured: 2015-10-23 at 00:31 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Oracle_(Datenbanksystem))_

Zusammen mit [DB2](https://de.m.wikipedia.org/wiki/DB2) und [MS SQL-Server](https://de.m.wikipedia.org/wiki/MS_SQL-Server) gehort Oracle zu den [Marktfuhrern](https://de.m.wikipedia.org/wiki/Marktanteil) im RDBMS-Segment. Im [Großrechner](https://de.m.wikipedia.org/wiki/Gro%C3%9Frechner)-Bereich sind [Sun](https://de.m.wikipedia.org/wiki/Sun_Microsystems)-Fire-Maschinen mit dem [Unix](https://de.m.wikipedia.org/wiki/Unix)-System [Solaris](https://de.m.wikipedia.org/wiki/Solaris_\(Betriebssystem\)) oder [IBM](https://de.m.wikipedia.org/wiki/IBM)-Maschinen haufig verwendete Plattformen. Im Midrange-Bereich werden nahezu alle Unix-Systeme unterstutzt und eingesetzt, daneben aber auch [OpenVMS](https://de.m.wikipedia.org/wiki/OpenVMS). [Linux](https://de.m.wikipedia.org/wiki/Linux) wurde neben Solaris als strategische Hauptplattform langere Zeit favorisiert und findet sehr starke Verbreitung. [Windows](https://de.m.wikipedia.org/wiki/Microsoft_Windows) wird aufgrund der hohen Verbreitung ebenfalls strategisch unterstutzt. Oracle ist laut dem DB-Engines Ranking das popularste Datenbankmanagementsystem[[2]](https://de.m.wikipedia.org/wiki/Oracle_\(Datenbanksystem\)).

Das Oracle-Datenbankmanagementsystem kann als Express-Edition (XE) kostenlos genutzt werden. Diese Version ist jedoch starker eingeschrankt als die kostenlose [DB2](https://de.m.wikipedia.org/wiki/DB2)-Version, weil sie u. a. das Laden von [Javaklassen](https://de.m.wikipedia.org/wiki/Java_\(Technik\)) in die Datenbank selbst nicht unterstutzt (der [JDBC](https://de.m.wikipedia.org/wiki/JDBC)-Treiberzugriff ist jedoch moglich). Zusatzlich gibt es eine Beschrankung von 1 [GiB](https://de.m.wikipedia.org/wiki/Bin%C3%A4rpr%C3%A4fix) [RAM](https://de.m.wikipedia.org/wiki/Random_Access_Memory), Nutzung maximal eines [CPU](https://de.m.wikipedia.org/wiki/Hauptprozessor)-Kerns sowie eine maximale Datenbankgroße von 11 GiB fur Anwenderdaten.

Fur Studienzwecke ist die Oracle-Datenbank auf der Herstellerseite frei erhaltlich. Technische Hemmnisse, wie [Lizenz-Server](https://de.m.wikipedia.org/w/index.php?title=Lizenz-Server&action=edit&redlink=1) oder [Lizenzschlussel](https://de.m.wikipedia.org/wiki/Lizenzschl%C3%BCssel), sind nicht vorhanden. Auch die anderen Produkte des Unternehmens Oracle stehen dort zur Verfugung.

Der Oracle Database Server in aktuellen Versionen unterstutzt den Zugriff auf ein Datenvolumen von 40 [EiB](https://de.m.wikipedia.org/wiki/Exbibyte). Damit weist er eine Speicherkapazitat auf, die derzeit (2006) kaum von einzelnen Organisationen ausgeschopft werden kann.

Mit dem Release 10g wurde die Vision eines Oracle-Grid (siehe auch [Grid-Computing](https://de.m.wikipedia.org/wiki/Grid-Computing)) weiter umgesetzt: Auch das kleine „g" im Release-Namen steht fur **G**rid. Kernstuck des Oracle-Grid ist der _Aktiv/Aktiv-Cluster_, der von Oracle unter dem Namen [Real Application Cluster](https://de.m.wikipedia.org/wiki/Real_Application_Cluster) (RAC) vertrieben wird. Oracle bietet seit 10g eine eigene [Cluster Manager](https://de.m.wikipedia.org/wiki/Cluster_Manager)-Software unter dem Namen _Oracle Cluster Ready Services_ an. Diese wurde erstmals in 9i zunachst fur Linux, spater auch fur Windows freigegeben. Seit Oracle 10g steht diese fur jede von Oracle unterstutzte Plattform zur Verfugung.

Da [SQL](https://de.m.wikipedia.org/wiki/SQL) nur eine deskriptive Sprache ist, wurde eine proprietare prozedurale Erweiterung von SQL mit dem Namen [PL/SQL](https://de.m.wikipedia.org/wiki/PL/SQL) entwickelt. PL/SQL steht fur _Procedural Language / Structured Query Language_. PL/SQL-Kommandos konnen ad hoc als anonyme Blocke eingegeben werden oder in Form von sogenannten 'Stored Procedures' in der Datenbank abgelegt werden.

Es konnen [XML](https://de.m.wikipedia.org/wiki/Extensible_Markup_Language)-Datenstrukturen (XMLDB, XDK) gespeichert werden. Das Speichern nichtrelationaler Daten (Video, Musik, Dokumente, Fax etc.) wird mit [BLOBs](https://de.m.wikipedia.org/wiki/Binary_Large_Object) (_binary large objects_) und [CLOBs](https://de.m.wikipedia.org/wiki/Character_Large_Object) (_character large objects_) unterstutzt. Die [Indizierung](https://de.m.wikipedia.org/wiki/Indexierung) von zahlreichen nichtrelationalen Datenformaten wird bereits mitgeliefert. Die Erweiterung um eigene programmatische Indizierungen wird unterstutzt. [Raumbezogene Daten](https://de.m.wikipedia.org/wiki/Geodaten) konnen relational abgelegt werden, raumliche Indizierungen und Abfragen werden unterstutzt ([SPATIAL Option](https://de.m.wikipedia.org/wiki/Oracle_Spatial)).

Die Standardeinstellung der [Isolationsebene](https://de.m.wikipedia.org/wiki/Isolation_\(Datenbank\)) einer Oracle-Datenbank ist „Read committed", d. h. eine Abfrage sieht alle Daten konsistent in dem Zustand, in dem sie zu Beginn der Abfrage festgeschrieben waren. Man kann auch die Isolationsebenen „Serialize" oder „Read only" (kein SQL-Standard) fur eine Session oder eine Transaktion festlegen. Die anderen beiden im SQL-Standard definierten Isolationsebenen („Read uncommitted", „Repeatable read") werden nicht explizit unterstutzt. Durch die Speicherung von Rollback-Informationen fuhren lesende Zugriffe nie zu [Sperren](https://de.m.wikipedia.org/wiki/Lock) der schreibenden Zugriffe (non-blocking reads) und umgekehrt (non-blocking writes).

  * plattformubergreifende Unterstutzung verteilter Datenbanken
  * intelligente [Datensicherung](https://de.m.wikipedia.org/wiki/Datensicherung) (wahlweise mit Block oder Row Change Tracking)
  * [Java](https://de.m.wikipedia.org/wiki/Java_\(Programmiersprache\)) (man kann Java innerhalb der Datenbank ausfuhren)
  * Absicherung gegen 
    * Instance Failure (z. B. Stromausfall) durch die Option eines Aktiv/Aktiv-Clusters mit [Failover](https://de.m.wikipedia.org/wiki/Failover)-Funktionalitat ([Oracle RAC](https://de.m.wikipedia.org/wiki/Oracle_RAC)),
    * Media Failure (Festplattenfehler) durch optionale [Standby-Datenbank](https://de.m.wikipedia.org/wiki/Standby-Datenbank) und [Oracle Dataguard](https://de.m.wikipedia.org/wiki/Oracle_Dataguard) sowie
    * Anwenderfehler mittels Flashback (auf Satzebene, Tabellenebene oder auch datenbankweit)
  * Data-Warehouse Features sind z. B. Datentypen zur Speicherung großer Datenmengen ([CLOB](https://de.m.wikipedia.org/wiki/Character_Large_Object), [BLOB](https://de.m.wikipedia.org/wiki/Binary_Large_Object)), Partitioning (Aufteilung der Daten in Untertabellen, etwa nach Datum), transportable [Tablespaces](https://de.m.wikipedia.org/wiki/Tablespace), Big Tablespaces (Datendateien mit maximal 128 PiB), [Bitmap](https://de.m.wikipedia.org/wiki/Bitmap)-Indexe fur [OLAP](https://de.m.wikipedia.org/wiki/OLAP)-Queries, Star-Transformation, Zugriff auf verteilte Datenbanken, [Standby-Datenbank](https://de.m.wikipedia.org/wiki/Standby-Datenbank)
  * Große Auswahl an eingebauten SQL-Funktionen und analytischen Funktionen, beide durch selbst definierbare Funktionen beliebig erweiterbar
  * Kostenbasierter Optimizer, der automatisch Ausfuhrungsplane zur Laufzeit entsprechend dem vorgegebenen Ziel Durchsatz oder Reaktionszeit erstellt
  * Umfangreiches Sicherheitskonzept zur Verwaltung und Weitergabe von Rechten an allen Datenbankobjekten, Vergabe von Rollen und Policies
  * Zeilenweise [Zugriffskontrolle](https://de.m.wikipedia.org/wiki/Zugriffskontrolle) (FGAC) als Erganzung zur sowieso vorhandenen spaltenweisen Zugriffskontrolle
  * [Auditing](https://de.m.wikipedia.org/wiki/Auditing_\(Informationstechnik\)) (Protokollierung aller Zugriffe oder in Teilen)
  * Resource Manager zum dynamischen Verteilen der Ressourcen (Speicher, CPU-Zeit, I/O) auf Profile
  * Ausgefeilte Tuningmoglichkeiten, ab Version 10g durch sogenannte „Advisors" erganzt (Datenbank kann sich selbst tunen oder Hinweise geben, Stichwort „ADDM")
  * Performance Features wie Index-Organized Tables (Tabellen werden als Index abgespeichert, Grundtabelle entfallt)
  * Proprietare, mit SQL verwobene eingebaute Programmiersprache [PL/SQL](https://de.m.wikipedia.org/wiki/PL/SQL) (native Kompilierung moglich, native Datentypen)
  * Seit Version 8i zusatzlich Verzahnung mit Java im Oracle Kernel (Laden von Java in die Datenbank)

Das Datenbanksystem entspricht, wie die meisten Datenbanksysteme, nicht vollstandig dem jeweils gultigen [SQL-Standard](https://de.m.wikipedia.org/wiki/SQL-Standard) - vor allem, weil die ersten Versionen von Oracle programmiert wurden, bevor SQL erstmals von der [ANSI](https://de.m.wikipedia.org/wiki/American_National_Standards_Institute) festgeschrieben wurde. Doch wurden sukzessive ANSI-Standards erfullt. So wird neben der proprietaren Syntax, die auch weiterhin zur Verfugung steht, inzwischen die ANSI-Join-Syntax unterstutzt.

Hier noch einige Probleme, vor denen man bei einer Portierung zwischen Datenbanksystemen eventuell steht bzw. uber die man stolpert, wenn man den SQL-Standard kennt:

  * Der Datentyp _date_ enthalt zusatzlich die Uhrzeit
  * In UNIONs ist der Wert NULL nur mit Zeichenketten statt mit allen Datentypen kompatibel (muss konvertiert werden)
  * Der Datentyp zum Speichern von unterschiedlich langen Zeichenketten heißt in _Oracle_ „VARCHAR2" und ist auf 4000 Bytes begrenzt. Ab Oracle 12 sind auch 32767 Bytes moglich. Die Angabe des ANSI-Datentyps VARCHAR wird zwar auch unterstutzt, doch wird die Spalte intern trotzdem als VARCHAR2 erstellt. In fruheren Versionen konnte bei Tabellenspalten vom Typ VARCHAR nur maximal 2000 Zeichen gespeichert werden (bis Version 7) und eine Folge von Leerzeichen wurde als NULL interpretiert (bis Version 6).

Ein Oracle-[Datenbanksystem](https://de.m.wikipedia.org/wiki/Datenbanksystem), welches von Clients verwendbar ist, besteht aus:

  * einem oder mehreren Listener-Prozessen (Oracle-Listener)
  * einer oder mehreren Datenbank-Instanzen (Oracle-Instance), das eigentliche Datenbankmanagementsystem (DBMS)
  * eine Menge von Datenbank-Dateien (Oracle-Database), die eigentliche Datenbank (DB)

Eine Menge von Datenbank-Dateien kann von mehreren Datenbank-Instanzen gleichzeitig geoffnet sein, dies bezeichnet man als [Oracle RAC](https://de.m.wikipedia.org/wiki/Oracle_RAC).  
Eine Datenbank-Instanz kann zu einem Zeitpunkt nur eine Menge von Datenbank-Dateien offen haben.

Im Einzelnen kann das System wie folgt charakterisiert werden:

Nimmt Verbindungswunsche von Datenbank-Clients entgegen und verbindet sie mit einer Datenbank-Instanz. Startet Oracle-Server-Prozesse fur Datenbank-Clients.

Hier erfolgt die Ressourcen-Zuteilung fur CPU und RAM. Eine Instanz besteht aus mehreren Oracle-Server-Prozessen (Vordergrund- und Hintergrundprozesse), welche den gemeinsamen Arbeitsspeicher in Form von Shared Memory bereitstellen. Die Vordergrundprozesse nehmen [Datenbankabfragen](https://de.m.wikipedia.org/wiki/Datenbankabfrage) (Query) oder Datenmodifikationsanweisungen (DML) in der Sprache SQL von den Datenbank-Clients entgegen, fuhren diese Auftrage aus und liefern Ergebnisdaten zuruck. Dabei agieren die Oracle-Server-Prozesse teilweise direkt auf den Datenbank-Dateien, teilweise ubertragen sie jedoch auch Aktivitaten auf die Hintergrundprozesse der Datenbank-Instanz.  
Die wichtigsten Hintergrundprozesse sind:

  * Der _Database Writer_ (DBWR), der Änderungen an den Datenblocken in die Data-Files schreibt.
  * Der _Log Writer_ (LGWR), der Redo-Informationen in die Redo-Log-Files schreibt.
  * Der _Archiver_ (ARCH), der Redo-Log-Files archiviert, sofern die Datenbank im sogenannten Archive-Log-Modus betrieben wird.
  * Der _System Monitor_ (SMON), der [Konsistenzinformationen](https://de.m.wikipedia.org/wiki/Konsistenz_\(Datenspeicherung\)) in die Control-Files sowie in die Header von Data-Files und in Redo-Log-Files schreibt. Beim Wiederanlauf einer Datenbank nach einem Crash pruft der System-Monitor diese Konsistenzinformationen in einem Quercheck uber alle Control-Files, Data-Files und Redo-Log-Files. Sollte der SMON Inkonsistenzen feststellen, so leitet der System-Monitor eine _Crash Recovery_ ein, bei dem aus den Redo-Log-Files solange fehlende Transaktionen in die Data-Files ubertragen werden, bis die Datenbank mit allen Data-Files wieder in sich konsistent ist.
  * Der _Prozess Monitor_ (PMON), der die Oracle-Prozesse uberwacht.

Die Datenbank-Instanz benotigt auch einige Dateien zur Steuerung und Protokollierung, diese werden unterschieden nach:

    Speicherort der Control-Files. Initiale Angabe vom Hauptspeicher und weitere Attribute.

Hier werden die Daten gespeichert. Dies erfolgt zumeist in Dateien in einem [Dateisystem](https://de.m.wikipedia.org/wiki/Dateisystem). Es werden jedoch auch [Raw Devices](https://de.m.wikipedia.org/wiki/Raw_Device) oder per ASM ([Oracle Automatic Storage Management Cluster File System](https://de.m.wikipedia.org/wiki/Oracle_Automatic_Storage_Management_Cluster_File_System)) verwaltete Diskgroups verwendet.  
Man unterscheidet die Dateiarten:

Data-Files
    die eigentlichen Datendateien mit den Dateninhalten.
    sehr schnell schreibbare Dateien, die als [Transaktions](https://de.m.wikipedia.org/wiki/Transaktion_\(Informatik\))[logs](https://de.m.wikipedia.org/wiki/Logdatei) dienen und die die Datenblockanderungen (Change-Vektoren) von Transaktionen aufnehmen. Diese gespeicherten Change-Vektoren dienen zur Wiederherstellung von Datenblocken, falls ungeplant oder beabsichtigt das Datenbankmanagementsystem terminiert werden muss. Noch nicht in die Data-Files ubertragene, festgeschriebene Änderungen konnen so rekonstruiert und nachgefahren werden (roll forward). Im Anschluss daran werden alle Änderungen nach dem letzten erfolgreichen Festschreibvorgang (check point) zuruckgeschrieben (_[roll back](https://de.m.wikipedia.org/wiki/Roll_back)_).
    Dateien, die u. a. die Struktur- und Zustandsinformation der Datenbank enthalten. Hierzu zahlen die System-Change-Number (SCN) sowie die Pfade und Namen aller Data-Files und Redo-Log-Files.

Werkzeuge zur Entwicklung und Datenbankverwaltung werden sowohl von Oracle als auch von anderen Herstellern zur Verfugung gestellt.

  * Werkzeuge vom Hersteller Oracle: 
    * _SQL*Plus_ ist ein kommandozeilenorientiertes Verwaltungswerkzeug zur Administration und Bedienung von Oracle-Datenbanken. SQL*Plus steht auf jedem [Rechnersystem](https://de.m.wikipedia.org/wiki/Computer) zur Verfugung, auf dem die Oracle Client- oder Serversoftware installiert ist. Hiermit lassen sich alle Verwaltungstatigkeiten sowie die Eingabe, Änderung, Abfrage und Loschen der eigentlichen Dateninhalte vornehmen. Der Aufruf von SQL*Plus erfolgt - unabhangig von der verwendeten Betriebssystemplattform - durch Eingabe von _sqlplus_. SQL*Plus stand mit den ersten Oracle-Versionen zur Verfugung. Aufgrund der Orientierung an Kommandozeilen sind umfangreiche SQL-Kenntnisse erforderlich. Mit iSQL*Plus stellt Oracle auch ein Webfrontend fur SQL*Plus bereit.
    * _Oracle SQL Developer (Project Raptor)_: Oracles kostenloses Werkzeug fur den Datenbankentwickler lauft als Java-Programm mit graphischer Benutzeroberflache und ermoglicht das Bearbeiten von Datenbankobjekten, Erstellen und Testen von SQL-Statements und Skripten, Erstellen und Debuggen von PL/SQL-Prozeduren und einfache Datenbankanalyse. Oracle SQL Developer kann auch auf MySQL Datenbanken arbeiten.
    * Oracle Enterprise Manager (Java-Konsole): Graphische Bedienoberflache zur Datenbankverwaltung auf Java-Basis (Entwicklung eingestellt).
    * Oracle Enterprise Manager Database Control: Web-basierende, graphische Bedienoberflache zur Verwaltung einer Datenbank
    * Oracle Enterprise Manager Grid Control: Web-basierende, graphische Bedienoberflache zur Verwaltung einer Oracle Umgebung inkl. mehrerer Datenbanken, Datenbankcluster, Standby-Systeme
    * Server Control: Kommandozeilenorientiertes Werkzeug zur Verwaltung von Datenbanken, Services und Application in einem Cluster
    * Oracle [JDeveloper](https://de.m.wikipedia.org/wiki/JDeveloper): Integrierte Entwicklungsumgebung zur Entwicklung von Datenbankanwendungen mit Oracle und Java
  * Werkzeuge anderer Hersteller: 
    * [TOAD](https://de.m.wikipedia.org/wiki/TOAD): Grafisches Werkzeug zur Verwaltung und Entwicklung mit Oracle-Datenbanken von dem Unternehmen [Quest](https://de.m.wikipedia.org/wiki/Quest_Software)
    * TOra: Grafisches Werkzeug zur Verwaltung und Entwicklung mit Oracle- und [PostgreSQL](https://de.m.wikipedia.org/wiki/PostgreSQL)-Datenbanken, mittlerweile ein [Sourceforge](https://de.m.wikipedia.org/wiki/Sourceforge)-Projekt, also [Open Source](https://de.m.wikipedia.org/wiki/Open_Source)
    * PL/SQL Developer: Graphisches Werkzeug zur Verwaltung und Entwicklung mit Oracle-Datenbanken von dem Unternehmen [Allround Automations](https://de.m.wikipedia.org/w/index.php?title=Allround_Automations&action=edit&redlink=1)
    * Omega9: Werkzeug zur Administration und Entwicklung von PL/SQL-Code mit Oracle-Datenbanken
    * SQL Workbench/J: The free DBMS-independent SQL Tool
    * [QueryAdvisor](https://de.m.wikipedia.org/w/index.php?title=QueryAdvisor&action=edit&redlink=1): The tool for advanced GUI based tracefile and wait interface analysis. Free and commercial licenses are available.
    * DBShadow: Standardlosung mit Graphischem User Interface fur die Erstellung, Überwachung und Verwaltung von Standby Datenbanken.
    * [Aqua Data Studio](https://de.m.wikipedia.org/wiki/Aqua_Data_Studio): Grafisches Werkzeug zur Verwaltung und Entwicklung von Datenbanken von dem Unternehmen AQUAFOLD
    * [SQuirreL SQL Client](https://de.m.wikipedia.org/wiki/SQuirreL_SQL_Client): Grafisches Werkzeug zur Verwaltung und Entwicklung fur verschiedene Datenbanken

Oracle lizenzierte fur lange Zeit alle seine Produkte entweder nach der Anzahl der [Prozessorkerne](https://de.m.wikipedia.org/wiki/Prozessorkern) (nicht wie zum Beispiel Microsoft nach der Anzahl der physikalischen [CPU-Sockel](https://de.m.wikipedia.org/wiki/CPU-Sockel)) oder nach der Anzahl sogenannter Named User, also benannter/registrierter Benutzer, wobei die Anzahl der moglichen Benutzer ausschlaggebend ist, nicht die Anzahl der tatsachlichen Benutzer. Dies wird so auch in der Enterprise Edition beibehalten. Bei Intel-Systemen benotigt man eine Lizenz fur 2 Kerne, bei Sparc eine Lizenz fur 4 Kerne.

Seit einiger Zeit ist fur die Standard Edition und die Standard Edition One jedoch auch die Lizenzierung abhangig von Anzahl der CPU-Sockel moglich.

Die _Express Edition_ ist kostenlos nutzbar und darf auch als Datenbank fur eigene Programmentwicklungen an Dritte weitergegeben werden, ohne dass dafur eine Lizenz erworben werden muss.

Die Anfange der Oracle Datenbank gehen zuruck auf die Forschungsarbeit von [Edgar F. Codd](https://de.m.wikipedia.org/wiki/Edgar_F._Codd), der in den 70er Jahren im Auftrag von IBM den Datenbank-Prototypen [System R](https://de.m.wikipedia.org/wiki/IBM_System_R) entwickelte. Diese Studie inspirierte [Larry Ellison](https://de.m.wikipedia.org/wiki/Larry_Ellison) zur Weiterentwicklung der Ergebnisse und zur Entwicklung einer eigenen Datenbank mit dem Namen Oracle. Die Datenbank wurde zu Beginn gleich als Version 2 auf den Markt gebracht, da man befurchtete, dass sich eine Version 1 schlechter verkauft.

1979 wurde die Datenbank als Oracle V2 erstmals am Markt angeboten. Diese Version stellte die Basis-Funktionen fur die Ausfuhrung von Queries und Joins zur Verfugung. Transaktionen wurden damals noch nicht unterstutzt.

1983 wurde das Release 3 angeboten mit der wesentlichen Erweiterung, dass nun Transaktionen mittels COMMIT und ROLLBACK gesteuert werden konnten.

1984 wurde die Version 4 mit read-consistency herausgebracht. Das bedeutet, dass lesende Transaktionen immer freien und konsistenten Zugriff auf die Daten haben, auch wenn diese gerade von einer anderen Transaktion verandert werden. Die lesende Transaktion erhalt in einem solchen Fall die zuvor gultige Version der Daten, die in Rollback-Segmenten aufgehoben wird. Das Verfahren wird heute [Multiversion Concurrency Control](https://de.m.wikipedia.org/wiki/Multiversion_Concurrency_Control) genannt.

1985 wurde die Version 5 als Datenbank in einer Client-Server-Architektur herausgebracht, die bis heute so beibehalten wurde.

1988 wurde die Version 6 mit weiteren zusatzlichen Funktionen herausgebracht:

  * PL/SQL
  * Oracle Forms v3
  * row-level [locking](https://de.m.wikipedia.org/wiki/Lock) (bedeutet, wenn ein Datensatz verandert wird, dann muss nicht mehr wie in fruheren Versionen der gesamte Datenblock (4 KB) gesperrt werden, sondern nur der einzelne Datensatz wird gesperrt)

1992 wurde Version 7 herausgebracht mit diesen neuen Funktionen:

  * Tabellen konnen mit Fremdschlussel-Beziehungen verknupft werden
  * Stored Procedures
  * Trigger
  * Package UTL_FILE zur Datenaus- und -eingabe vom Oracle-Server auf sequentielle Dateien.

1997 wurde Version 8i herausgebracht mit diesen neuen Funktionen:

  * Kostenbasierter [Anfrageoptimierer](https://de.m.wikipedia.org/wiki/Anfrageoptimierer). Der bisher verwendete regelbasierte Anfrageoptimierer kann auch weiter benutzt werden.
  * Moglichkeit zum Speichern objektorientierter Daten

Administration:

  * Drop column. In vorherigen Versionen konnten angelegte Tabellenspalten nicht geloscht werden.
  * Stored Outlines. Damit kann man den Zugriffsweg fur ein SQL-Statement festlegen.
  * Einfuhrung von Transportable Tablespaces jedoch zunachst noch mit etlichen Restriktionen
  * Funktionsbasierter Index

SQL:

  * Erweiterung der Gruppierungs-Moglichkeiten durch ROLLUP und CUBE

PL/SQL:

  * Execute Immediate als PL/SQL-Befehl zum Ausfuhren von dynamischen SQL-Anweisungen in einem Programm.
  * Bulk-Collect zum Lesen von mehreren Satzen uber einen Cursor in eine Collection mit nur einem Statement (nur noch ein Kontextwechsel erforderlich)
  * FORALL-Klause zum Einfugen/Ändern/Loschen von mehreren Satzen, die in einer Collection gespeichert sind.
  * Package UTL_SMTP zum Versand von E-Mails

2001 wurde Version 9i herausgebracht mit diesen neuen Funktionen:

Administration:

  * online Reorganisation von Tabellen (Indizes ging schon in Version 8)
  * mehrere Blockgroßen fur eine Datenbank moglich
  * Rollbacksegmente werden automatisch verwaltet
  * Partition-Splitting
  * List-Partitionierung (Partitionierung anhand von explizit benannten Werten)
  * das Flashback-Konzept wird eingefuhrt zur Wiederherstellung (Recovery) von Daten auf Session- oder Statement-Ebene.
  * Verwendung des SPFILE (ServerParameterFile) zur Aufnahme binar gespeicherter DB-Parameter

SQL:

  * Datentypen fur Zeitraume (z.B. Intervall year to month)
  * MERGE-Statement, eine Kombination aus INSERT und UPDATE
  * Multi-Table-Insert. (Befullen mehrerer Tabellen in einem Verarbeitungsschritt)
  * Bitmap-Join-Index (ein [Bitmap-Index](https://de.m.wikipedia.org/wiki/Bitmap-Index), der mehrere Tabellen referenziert, die haufig gejoint werden)
  * Full outer Joins werden unterstutzt
  * With-Klausel zur Definition von "Inline-Views", die nur fur die Formulierung einer Abfrage Gultigkeit haben, und nicht permanent im Katalog gespeichert werden mussen
  * mehr Funktionen fur die Verarbeitung von [XML](https://de.m.wikipedia.org/wiki/Extensible_Markup_Language)-Daten

Tools:

  * iSQL*Plus ein Browser zum Ausfuhren von Abfragen und PL/SQL-Skripten uber das Internet.

2003 wurde Version 10g herausgebracht mit diesen neuen Funktionen: [[4]](https://de.m.wikipedia.org/wiki/Oracle_\(Datenbanksystem\))

Administration:

  * Recycle-Bin (=Papierkorb-Funktion zur Aufnahme von (mit DROP TABLE) geloschten Tabellen)
  * ASM (Automatic Storage Management)

SQL:

Tools:

  * Data Pump fur schnellen Import / Export
  * OWB (Oracle Warehouse Builder)
  * SQL Profile, eine Option, die bestimmte kritische SQL-Statements, die haufig verwendet werden, ausfuhrlich analysiert und einen optimalen Zugriffsplan im Katalog ablegt.
  * ADDM Automatic Database Diagnose Monitor. Eine Funktion, die Performance-Reports erstellt und auf kritische Stellen aufmerksam macht.
  * SQL Tuning Advisor. Unterstutzung fur das automatische Generieren von Statistiken und Analysieren von SQL-Statements
  * Package UTL_MAIL zum einfachen Versand von E-Mails aus einer PL/SQL-Prozedur. Dadurch wird das bisher zur Verfugung stehende Package UTL_SMTP abgelost.

2007 wurde Version 11g Release 1 herausgebracht mit diesen neuen Funktionen (Auswahl):[[5]](https://de.m.wikipedia.org/wiki/Oracle_\(Datenbanksystem\))

  * Clientseitiger Abfrage-Cache
  * Unicode-5.0-Unterstutzung
  * SecureFiles (komplette Neuentwicklung der LOB-Speicherung)
  * Virtuelle Tabellen-Spalten
  * Unsichtbare Indizes

2009 wurde Version 11g Release 2 herausgebracht mit diesen neuen Funktionen (Auswahl):[[6]](https://de.m.wikipedia.org/wiki/Oracle_\(Datenbanksystem\))

  * Intelligente Datenplatzierung beim Automatic Storage Management (ASM)
  * Komprimieren von Daten
  * Neue Datenbankoption "Oracle RAC One Node" (= Ein-Knoten-Version von Real Application Clusters)

2013 wurde Version 12c Release 1 herausgebracht mit diesen neuen Funktionen (Auswahl):[[7]](https://de.m.wikipedia.org/wiki/Oracle_\(Datenbanksystem\))[[8]](https://de.m.wikipedia.org/wiki/Oracle_\(Datenbanksystem\))[[9]](https://de.m.wikipedia.org/wiki/Oracle_\(Datenbanksystem\))[[10]](https://de.m.wikipedia.org/wiki/Oracle_\(Datenbanksystem\))

  * Der Datentyp VARCHAR2 unterstutzt bis zu 32767 Bytes
  * [Unicode](https://de.m.wikipedia.org/wiki/Unicode)-6.1-Unterstutzung
  * Unsichtbare Spalten
  * Select mit Zeilen Offset und Begrenzung (OFFSET, FETCH NEXT..)
  * Innerhalb einer Container-Datenbank bis zu 252 „Pluggable" Datenbanken moglich
  * Container-Datenbank organisiert wie eine VM den RAM und CPU fur die „Pluggable" Datenbanken
  * Automatische Datenoptimierung (Automatic Data Optimization, ADO) mit Heat Maps fur automatische Komprimierung von Daten ([Informationslebenszyklusmanagement](https://de.m.wikipedia.org/wiki/Informationslebenszyklusmanagement))
  * Verwendung von [JSON](https://de.m.wikipedia.org/wiki/JavaScript_Object_Notation)-Daten (JavaScript Object Notation) in der Datenbank

Nach der Unternehmensgrundung 1977 war Bruce Scott einer der ersten Angestellten[[11]](https://de.m.wikipedia.org/wiki/Oracle_\(Datenbanksystem\)); seine Tochter hatte eine Katze namens Tiger. Daraus entstand der Benutzername „scott" mit Passwort „tiger" fur einen heute noch gern eingesetzten Demo-Benutzer.

  * Andrea Held, Mirko Hotzy, Lutz Frohlich, Marek Adar, Christian Antognini, Konrad Hafeli, Daniel Steiger, Sven Vetter, Peter Welker: _Der Oracle DBA_ Oktober 2011, [ISBN 3-446-42081-9](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3446420819) ([Website zum Buch](http://www.trivadis.com/kompetenzen/literatur/der-oracle-dba.html))
  * Michael Abbey, Mike Corey, Ian Abramson: _Oracle 10g. A Beginner's Guide._ McGraw-Hill/Osborne, Berkeley 2004, [ISBN 0-07-223078-9](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/0072230789) (engl.)
  * Johannes Ahrends, Dierk Lenz, Patrick Schwanke, Dr. Gunter Unbescheid: _Oracle 10g fur den DBA. Effizient konfigurieren, optimieren und * verwalten._ Addison-Wesley 2006, [ISBN 3-8273-2171-9](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3827321719)
  * Andrea Held: _Oracle 10g Hochverfugbarkeit. Die ausfallsichere Datenbank mit Real Application Cluster (RAC), Data Guard und Flashback._ Addison-Wesley, Munchen 2005, [ISBN 3-8273-2163-8](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3827321638)
  * Uwe Herrman, Dierk Lenz, Gunter Unbescheid, Johannes Ahrends: _Oracle 9i fur den DBA. Effizient konfigurieren, optimieren und verwalten._ McGraw-Hill/Osborne, Berkeley 2004, [ISBN 0-07-223078-9](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/0072230789)
  * Thomas Kyte: _Expert Oracle Database Architecture: 9i and 10g Programming Techniques and Solutions_, APress, 2005, [ISBN 1-59059-530-0](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/1590595300) (engl.)
  * Michael Wagner: _SQL/XML:2006 - Evaluierung der Standardkonformitat ausgewahlter Datenbanksysteme_, Diplomica Verlag, 2010, [ISBN 3-8366-9609-6](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3836696096)
