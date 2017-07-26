# Oracle 12c: Multitenant Database

_Captured: 2015-10-21 at 07:38 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/betrieb/datenbanken/oracle-database-12c-multitenant-database.html)_

![In absehbarer Zeit wird die Multitenant Database das Rennen machen. © depositphotos.com / everythingposs](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720_Depositphotos_33311561_s__everythingposs_d4cd60d26d.png)

> _In absehbarer Zeit wird die Multitenant Database das Rennen machen. (C) depositphotos.com / everythingposs_

**Die mit Oracle 12c neu eingefuhrte Datenbank Option ist fur viele Unternehmen derzeit ein Buch mit sieben Siegeln. Was bedeutet die Mandantenfahigkeit der Datenbank? Lohnt sich die Anschaffung dieser doch recht teuren Option? Wie andert sich die Datenbankverwaltung? Geht das in meinem Unternehmen uberhaupt? Diese und weitere Fragen werden in diesem Artikel erlautert.**

Seit Mitte 2013 gibt es das neues Oracle Datenbank Release 12.1 und damit die zusatzliche Moglichkeit, eine Datenbank „mandantenfahig" zu machen. Mit „_Pluggable Database"_ oder, wie der offizielle Name lautet, „_Multitenant_" ist es jetzt erstmalig moglich, mehrere Oracle Datenbanken zu einer zusammen zu fassen. Wenn man dem Oracle Marketing glauben darf, war das aber doch schon immer so, oder? Durch die Konsolidierung von mehreren Schemata in einer Datenbank entstand doch eine Mandantenfahigkeit.

> Die Oracle Datenbank von morgen (oder heute?)!

Wer das mal ausprobiert hat, wird aber sehr schnell die Grenzen dieser Implementierung erkennen. Angefangen bei profanen Limitierungen, wie der Eindeutigkeit von Public Synonymen uber die von einigen Anwendungen - zu Recht oder Unrecht - geforderte Namensgebung bei den Tablespaces bis hin zum leidigen Patchen der Datenbank. Es gibt unzahlige Grunde, die die Schemakonsolidierung in der Praxis unmoglich gemacht haben. Dabei will ich nicht bestreiten, dass Schema-Konsolidierung funktionieren kann, aber die Widrigkeiten sind doch sehr groß.

> Was also ist anders bei einer Pluggable Database? - Alles!

Seit Version 6 beschaftige ich mich mit Oracle Datenbanken und muss sagen, dass ich in der ganzen Zeit keine so gravierende Änderung erlebt habe, wie mit der Oracle 12c Multitenant Database. Nicht nur, dass die Architektur sich geandert hat, auch penibel gepflegte Skripte mussen muhsam angepasst bzw. aufgegeben werden.

## Architektur der Oracle Database 12c mit Multitenant

### Container Datenbank (CDB)

Zunachst einmal besteht eine Multitenant Database aus einer Container Datenbank, der so genannten CDB, und ein oder mehreren Pluggable Databases. Die Container Datenbank ist dabei in etwa unserer bisherigen Datenbank gleichzusetzen. D.h. sie besteht aus dem SYSTEM, SYSAUX, TEMP und UNDO-Tablespace, hat Redolog-Dateien, Controlfiles und eine Parameterdatei (spfile). Der einzige Unterschied zur „klassischen" Datenbank besteht darin, dass wir hier keine Benutzer- bzw. Anwendungsdaten sehen wollen (obwohl die CDB merkwurdigerweise einen USERS Tablespace hat). Wie bisher ublich wird die Container Datenbank uber den Datenbanknamen (db_name) identifiziert und ist idealerweise mit einer gleichnamigen Instanz (ORACLE_SID) verknupft. Bei RAC oder RON durfen es auch gerne ein paar mehr Instanzen sein.

### Pluggable Database

In diese Container Datenbank werden jetzt ein oder mehrere so genannte Pluggable Databases eingehangt. Auch wenn in der Oracle Dokumentation teilweise von „_Starten_" und „_Stoppen_" einer Pluggable Database die Rede ist, trifft es eher zu, dass die Pluggable Databases geoffnet und geschlossen werden.

Das bedeutet, dass die Pluggable Database keine Instanz hat (denn diese Starten und Stoppen wir ja bei einer „normalen" Datenbank) und dem entsprechend auch keine eigenen Prozesse. Hinzu kommt, dass auch das Redo- und Undo-Management nur uber die CDB erfolgen kann, d.h. sowohl den UNDO-Tablespace als auch Redolog-Dateien sucht man in der PDB vergeblich.

Im Schaubild sieht das dann so aus:

![Abb.1: Multitenant Database Architektur. © Johannes Ahrends](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_Multitenant_uebersicht_68c4b13e0d.png)

> _Abb.1: Multitenant Database Architektur. (C) Johannes Ahrends_
