# Oracle PL/SQL Workshop: Verwaltung von Anwendungsparametern

_Captured: 2015-11-19 at 13:47 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/entwicklung/programmiersprachen/oracle-plsql-workshop-beispiel-anhand-einer-parametertabelle.html)_

**Mandantenfähige Software stellt besondere Anforderungen an die Architektur von Anwendungen. Dieser Workshop zeigt am Beispiel einer Verwaltung von Anwendungsparametern auf, wie Oracle solche Anwendungen unterstützen kann. Neben der eigentlichen Verwaltung der Parameter ist dieser Workshop allerdings auch eine Blaupause für die zentralisierte Verwendung von Tabellen und PL/SQL-Code in Anwendungen.**

![Datenmodell PL/SQL @ Alkmene Verlags- und Mediengesellschaft mbh](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720-405-Datenmodell-PL-SQL_01_566adc8171.jpg)@ Alkmene Verlags- und Mediengesellschaft mbh

Eine generelle Funktionalität wie die Verwaltung der Parameter ist immer ein guter Kandidat für einen separaten Utilites-Benutzer in der Datenbank. Verschiedene Benutzer sind ein einfaches und sehr gut funktionierendes Mittel, um Anwendungsbereiche voneinander zu trennen. Da Packages eines Benutzers nur dann von anderen Benutzern verwendet werden dürfen, wenn dies der Eigentümer erlaubt, haben wir einerseits eine feingranulare Trennung der Zugriffsberechtigungen, andererseits stellt uns der Aufruf mit Eigentümer (Definer)- oder Aufruferrechten (Invokers Rights) einen Mechanismus zur Verfügung, den Zugriff auf Tabellen sehr elegant zu kontrollieren, denn wenn ein Package mit Benutzerrechten aufgerufen wird, »sieht« die Anwendung die Datenbanktabelle aus Sicht des aufrufenden Benutzers und nicht des Eigentümers des Packages. Daher kann der aufrufende Benutzer die zentrale Parametertabelle für globale Parameter sehen, in unserem Beispiel wird er aber zusätzlich auch eine lokale Parametertabelle sehen, in der die Parameterwerte des Mandanten gespeichert werden. Abbildung 1 zeigt das Datenmodell in der Übersicht:

![Abbildung 1: Übersicht über das Datenmodell in Oracle PL/SQL© Jürgen Sieben](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_Juergen-Sieben-Oracle-PLSQL-1_02_1cc39be140.jpg)Abbildung 1: Übersicht über das Datenmodell © Jürgen Sieben

Eine View integriert beide Tabellen in eine resultierende Parameteransicht. Diese View gibt den lokalen Parametern gleichen Namens und gleicher Parametergruppe den Vorrang vor den zentralen Parametern. Lokale Parameter decken zentrale Parameter also ab, ohne diese umdefinieren zu müssen. Parallel dazu wird jedoch die Logik zur Verwaltung der Parameter nur einmal implementiert, nämlich im zentralen Parameterpackage. Da dieses Package aber mit Benutzerrechten definiert wird, greift es auf die für den jeweiligen Benutzer lokal definierte Parameter-View zu und sieht daher die dort gültigen Parameter. 

Dieser einfache Aufbau gibt uns nun alle Möglichkeiten an die Hand: Im Schema der zentralen Tabelle existiert eine View PARAMETER_VIEW, die letztlich lediglich einen direkten Durchgriff auf die zentrale Tabelle darstellt, im lokalen Schema kann eine gleichnamige View eine lokale Tabelle integrieren, wie gezeigt, oder aber auch einfach nur auf die zentrale Tabelle verweisen, oder aber auch eine vollständig eigene Tabelle repräsentieren, ohne Backup durch eine zentrale Tabelle, oder aber … die Möglichkeiten sind endlos. Wenn Sie, zum Beispiel im zentralen Schema, lediglich einen Durchgriff auf die zentrale Tabelle wünschen, müssen Sie nicht einmal eine View anlegen, es reicht dann ein einfaches Synonym auf die lokale Tabelle. In unserem Beispiel wird die lokale View über das Synonym PARAMETER zur Verfügung gestellt, wenn Sie mögen, können Sie hierauf aber auch verzichten und immer mit dem Namen der View arbeiten. 

## Die Parametertabelle

Unsere Parametertabelle enthält eine Spalte für jeden grundsätzlichen Parametertyp, und zwar für Zeichenketten, Zahlen, Datumsangaben, XML und Wahrheitswerte. Jeder Parameter ist einer Parametergruppe zugewiesen, die über eine Lookup-Tabelle geschützt wird, sowie über einen alphanumerischen Parameternamen ansprechbar. Optional können Sie zusätzlich vorsehen, eine Spalte zur Speicherung des Namens der Anwendung einzufügen, falls Sie mehrere Anwendungen unterstützen und die Parameter hierfür getrennt verwalten möchten. Auch in diesem Fall empfiehlt es sich dann, eine Lookup-Tabelle mit den erlaubten Anwendungen zu hinterlegen. 

Interessant sind überdies die Metainformationen, die wir den Parametern noch hinzufügen. Zum einen können wir in der Tabelle für die Parametergruppen festlegen, ob der Endanwender die Parameter dieser Gruppe ändern darf oder nicht. Sind die Daten nicht änderbar, könnten wir die Änderung solcher Parameter an einen Super-Adminstrator-Account binden oder aber komplett verbieten. Sinnvoll ist eine Spalte, die festlegt, welche Art der Parameter hat. Damit ist ein Wert gemeint, der auf einer Oberfläche dazu genutzt werden kann, dem Parameter einen Editor zur Bearbeitung zuzuweisen. So kann ein Zeichenkettenparameter, den wir in unserer Tabelle als clob speichern, eine Reihe unterschiedlicher Typen wie Text, HTML, SQL repräsentieren und mit passenden Editoren bearbeitet werden. 

Dann enthält unsere Parametertabelle noch eine Spalte zur Validierung des Parameterwertes. In diese Spalte werden wir eintragen, welche Bedingungen ein Parameter erfüllen muss, um valide zu sein. Hier stehen mehrere Möglichkeiten zur Verfügung: Wir könnten einen regulären Ausdruck speichern, der einen Mustervergleich durchführt. Mächtiger ist aus meiner Sicht ein PL/SQL-Fragment mit einem booleschen Ausdruck, der den Parameterwert testet und zu wahr oder falsch evaluiert werden kann. Ein solches PL/SQL-Fragment lässt sich zur Laufzeit leicht dynamisch auswerten und dabei auch auf die verschiedenen Datentypen besser eingehen als ein regulärer Ausdruck. Die Validierung eines Parameters können wir einfach in das Package integrieren, indem wir diesen Ausdruck für einen Parameter auslesen und im Package dynamisch ausführen lassen. Allerdings sollten Sie der Oberfläche nicht ohne Not erlauben, diese Validierungen zu editieren. Zu groß wäre das Einfallstor für SQL-Injektionen, denn ein Code der beliebige PL/SQL-Blöcke ausführen kann, ist dann doch etwas heikel … Aus diesem Grund werden wir einem Parameter, der von einem Mandanten angelegt wird, nicht erlauben, eine Validierung für diesen Parameter zu definieren, sondern diese muss von einem Administrator oder einem Entwickler erstellt werden. Umfangreiche Validierungen lagern Sie in ein Validierungspackage aus und rufen die entsprechenden Funktionen dann von hier aus auf. 

Unsere Tabelle könnte also aussehen wie folgt:

![Abbildung 2: Das Datenmodell der Parametertabelle © Jürgen Sieben](http://www.informatik-aktuell.de/fileadmin/_migrated/pics/Juergen-Sieben-Oracle-PLSQL-2_01.jpg)Abbildung 2: Das Datenmodell der Parametertabelle © Jürgen Sieben

Das Datenmodell birgt soweit keine weiteren Geheimnisse. Die Tabellen PARAMETER_GROUP und PARAMETER_TYPE sind übrigens perfekte Kandidaten für die Speicherung als Index Organized Tables (IOT). Aus : »Übersicht über das Datenmodell« können Sie entnehmen, dass wir eine zentrale und eine lokale Parametertabelle vorhalten werden. Die lokale Tabelle muss dabei nicht alle Spalten der zentralen Tabelle enthalten. Sie können in der lokalen Tabelle die Spalten DESCRIPTION, PARAMETER_TYPE_ID und alle nachfolgenden streichen, denn die View übernimmt diese Bezeichnungen aus der zentralen Tabelle. 

## Einrichtung der Parametertabelle und der Zugriffsrechte

Als Eigentümer für unsere Parameterverwaltung wählen wir den Benutzernamen ORA_API. Das Skript zum Artikel legt diesen Benutzer an, erzeugt die Parametertabellen, ein Synonym für die zentrale Parametertabelle und eine kleine Hilfsprozedur PRINT_STRING_PARAM, die ich zur Demonstration des Ansatzes verwende und im zweiten Teil wieder entferne. Diese Hilfsprozedur ist mit dem Pragma authid current_user erstellt worden. Wichtig ist, dass wir in der Prozedur das Synonym PARAMETER verwenden (das auf die lokale View zeigt), nicht den Tabellennamen PARAMETER_TAB, auf die das Synonym innerhalb von ORA_API zeigt! Unsere Idee basiert ja darauf, dass wir später, innerhalb des Benutzers SCOTT, ein Synonym dieses Namens auf die View zeigen lassen, die beide Parametertabellen integriert. Der Aufruf der Prozedur hält keinerlei Überraschung bereit: 

    
    
    SQL> set serveroutput on;  
    SQL> call print_string_param('TEST_PARAM');
    
    Das Resultat lautet: Peter  
    Aufruf wurde abgeschlossen.

Um nun zu demonstrieren, wie ein anderer Benutzer mit diesen Tabellen arbeiten kann, gestatten wir SCOTT, mit diesen Parametern zu arbeiten. SCOTT benötigt folgende Rechte:

  * Ein Ausführungsrecht an der Prozedur print_string_param
  * Ein Leserecht auf die Tabelle PARAMETER_TAB

Diese Rechte hat unser Skript bereits an SCOTT erteilt, daher kann SCOTT nun die Parameter dieser Tabelle (bzw. des auf dieser Tabelle eingerichteten Synonyms) lesen: 

    
    
    SQL> select string_value  
     2   from ora_api.parameter_tab;   
      
    STRING_VALUE  
    ----------------------------------  
    Peter  
      
    

Listing 1: SCOTT hat Zugriff auf die Tabelle PARAMETER_TAB 

Nun erstellen wir die benötigten Datenbankobjekte im Schema SCOTT. Im Einzelnen benötigen wir:

  * Eine Parametertabelle, analog zur Tabelle PARAMETER_TAB
  * Eine View, um die lokale und die zentrale Parametertabelle zu integrieren
  * Ein Synonym PARAMETER auf diese View, das dann von der Prozedur print_string_param aufgrund des Pragmas authid current_user verwendet wird
  * Optional ein Synonym auf diese Prozedur, damit wir beim Aufruf nicht das Schema ORA_API voranstellen müssen

Ein Wort zur View, die beide Parametertabellen integriert. Im Skript sehen Sie, wie diese View definiert ist. Das Vorgehen ist eigentlich einfach: Wir hängen beide Tabellen (zentral und lokal) mittels einer union all-Abfrage aneinander, weisen jedoch in einer neu definierten Spalte dieser Abfrage den Werten der lokalen Tabelle einen Wert 1 und den Werten der zentralen Tabelle einen Wert 2 zu, um bei gleichnamigen Parametern ein Sortierkriterium zu erhalten. Dann verwenden wir eine analytische Funktion (nämlich rank), um einen Rang über die Parameternamen, gruppiert nach Parametergruppe und –name, sortiert nach dem Sortierkriterium, zu berechnen. Das Prinzip: Ist ein lokaler Parameter vorhanden, erhält dieser den Rang 1, weil er über die Sortierspalte vorrangig sortiert wurde. Ist dies nicht der Fall, wird der zentrale Parameter verwendet. Dieses Vorgehen ist auch anders möglich, wir könnten zum Beispiel die Spalten mittels einer coalesce-Funktion prüfen lassen und uns den ersten not null-Wert ausgeben lassen. Ich mag den Weg über die analytische Funktion jedoch lieber, weil ich so einen Parameter auch auf den Wert null ändern kann. 

Nun können wir uns einige Testwerte anzeigen lassen, die wir in die lokale Parametertabelle eingefügt haben: 

    
    
    SQL> connect scott/tiger   
    Connected.
    
    SQL> set serveroutput on   
    SQL> call print_string_param('TEST_PARAM'); 
    
    Das Resultat lautet: Willi  
    Call completed.
    
    SQL> call print_string_param('TEST_PARAM_2');
    
    Das Resultat lautet: Walter   
    Call completed.   
      
    

Listing 2: Die Lösung funktioniert

Beachten Sie, dass der lokale Parameter den zentralen überschreibt und der nur lokal vorhandene, zweite Parameter nun verfügbar ist. 

## Das Parameterpackage

Im vorigen Abschnitt habe ich Ihnen erläutert, wie die beiden Parametertabellen sich überlagern und so eine mandantenfähige Parameterverwaltung realisieren. Aber natürlich ist die einfache Zugriffsprozedur nicht, was wir später haben möchten, sie diente ja nur der Demonstration. Nun werden wir, basierend auf diesen Tabellen, Views und Synonymen, ein Package erstellen, das uns die Parameter ausgibt, aber auch bestehende Parameter bearbeiten kann. Um nicht den Überblick zu verlieren: Analog zur oben verwendeten Prozedur, wird auch dieses Package im Schema ORA_API erstellt und mit Benutzerrechten ausgeführt, denn ein wesentlicher Punkt dieser Strategie ist es ja, den Zugriffscode zentral vorzuhalten und anschließend in mehreren Schemata nutzen zu können. 

Die Idee des Packages ist einfach: Es soll eine typsichere Schnittstelle zu den einzelnen Parametern anbieten. 

    
    
    SQL> create or replace  
     2 	package param  
     3 as  
     4 	/* SETTER */  
     5	 procedure set_string(  
     6 		p_parameter_id in varchar2,  
     7 		p_parameter_group_id in varchar2,  
     8 		p_parameter_value in clob,  
     9 		p_is_modifiable in boolean default false);  
     …   
     47  
     48 	/* GETTER */   
     49 	function get_string(  
     50 		p_parameter_id in varchar2,  
     51 		p_parameter_group_id in varchar2)  
     52 	return clob;   
     …  
     83  
     84 end param;  
     85 /  
     Package wurde erstellt.   
      
    

_ _Listing 3: Ausriss aus der Packagespezifikation

Für das Verständnis reicht der oben gezeigte Ausriss (Das Skript zum Workshop enthält selbstverständlich das gesamte Package). Stellvertretend für die Methoden, mit denen die Parameter gelesen und geschrieben werden, habe ich eine get- und eine set-Methode für den Parametertyp string ausgewählt. Alle anderen Methoden sind identisch konstruiert. Demzufolge ist auch die Package-Implementierung recht einfach. Vor der Änderung eines Parameters durch den Benutzer lesen wir zunächst einige Einstellungen zu diesem Parameter mittels einer Hilfsfunktion GET_PARAMETER_SETTINGS:

_Listing 4: get_parameter_settings_

Diese Hilfsfunktion liest einige Einstellungen zum Parameter und ermöglicht später eine einfachere Logik. Erwähnenswert ist vielleicht die Tatsache, dass eine Parametergruppe, für die vereinbart wurde, dass sie nicht änderbar ist, dies in jedem Fall auch bleibt, ein Einzelparameter kann lediglich die Änderung eines Parameters verhindern, wenn die Gruppe änderbar ist.

Listing 5: PL/SQL-Prozedur set_parameter__

Hier die zentrale Methode zur Änderung eines Parameters. Die Logik ist recht schlicht: Ist der Parameter änderbar, wird eine Validierung durchgeführt, sofern eine entsprechende Logik hinterlegt wurde. Ist diese erfolgreich (oder nicht vorhanden), wird ein merge auf die lokale PARAMETER_TAB vorgenommen. Die merge-Anweisung ist hier erforderlich: Wird ein zentraler Parameter zum ersten Mal geändert, ist dieser in der lokalen Tabelle noch nicht vorhanden und muss daher eingefügt werden. Validierungs-Strings etc. spielen hier jedoch keine Rolle, da diese aus der zentralen Tabelle in die View übernommen werden. 

Die Validierung des Parameters wird nur durchgeführt, wenn auch ein Validierungsstring mitgegeben wurde. Dann jedoch ist es relativ einfach, diese durchzuführen: Zunächst ersetzen wir im Validierungsstring die entsprechenden Platzhalter durch die Parameterwerte. Ich verwende hier mehrere Platzhalter, weil im Ausnahmefall ein Parameter durchaus auch einmal eine Zeichenkette und eine Zahl beinhalten könnte. Dieser Validierungsstring wird in einen anonymen Block gepackt, der als Ergebnis der Validierung eine 1 zurückgibt, wenn der Test bestanden wurde, ansonsten einen null-Wert. Ist die Validierung erfolgreich, verzichtet der weitere Code darauf, einen Fehler zu werfen.

Listing 6: PL/SQL-Prozedur get_parameter

Noch schlichter ist die zentrale Methode zum Lesen der Parameter: Es wird ganz einfach eine Zeile aus PARAMETER in einen Record übernommen und zurückgeliefert. Die einzelnen Zugriffsmethoden bedienen sich dann in diesem Record und liefern die entsprechenden Parmeterwerte an die aufrufende Umgebung zurück:

Listing 7: Ausschnitt der Package-Implementierung

## Das Oracle PL/SQL-Package im Einsatz 

Sehen wir uns abschließend noch an, ob das Package auch tut, wofür wir es gebaut haben. Für das Beispiel habe ich das Package so installiert, dass es dem Benutzer ORA_API gehört und zusätzlich SCOTT zur Verfügung gestellt wird. Das bedeutet, dass SCOTT nun eine lokale Tabelle mit Parameterwerten pflegt, um Vorgaben aus der Tabelle PARAMETER_TAB, die sich nun bei ORA_API befindet, zu überschreiben. Ich beginne damit, der Tabelle PARAMETER_TAB des Benutzers ORA_API einen Testparameter einzufügen. Dazu benutze ich das Package PARAM_ADMIN, das ich dem Workshop-Skript beigefügt habe, und für das ich die Ausführungsrechte an SCOTT übertragen habe. Dieser wiederum hat sich auf dieses Package dann ein Synonym eingerichtet. Beachten Sie bitte, dass dieses Package mit authid definer erstellt wurde und daher auf die zentrale Tabelle PARAMETER_TAB zugreift: 

    
    
     SQL> connect scott/tiger
    
     Connect durchgeführt. 
    
     SQL> begin 
    
    
    PL/SQL-Prozedur erfolgreich abgeschlossen.

Nun ist der Parameter in ORA_API.PARAMETER_TAB verfügbar. Wenn wir als Benutzer SCOTT die Daten des Synonyms PARAMETER ansehen, ist der Parameter bereits sichtbar: 

    
    
     SQL> select parameter_id, parameter_group_id,  
     2           parameter_description description, string_value   
     3    from   parameter;
    
     PARAMETER_ID 	PARAMETER_GROUP_ID DESCRIPTION    STRING_VALUE  
     -------------- ------------------ -------------- ---------------   
     TEST           DEFAULT            Testparameter  Testwert
    
     

Nun also möchten wir diesen Parameter lokal überschreiben. Das geht, indem wir das - über ein Synonym unter dem Namen PARAM zur Verfügung gestellte - Package ORA_API.PARAM_PKG aufrufen und den Wert ändern: 

    
    
     SQL> begin  
     2 	param.set_string('TEST', 'DEFAULT', 'Neuer Wert');   
     3 	commit;  
     4 end;   
     5 /
    
     PL/SQL-Prozedur erfolgreich abgeschlossen.

Nachdem dies geschehen ist, kann SCOTT den neuen Parameterwert sofort verwenden: 

    
    
     SQL> set serveroutput on
    
     SQL> begin   
     2 	dbms_output.put_line(   
     3 	param.get_string('TEST', 'DEFAULT'));   
     4 end;   
     5 / 
    
     Neuer Wert
    
     PL/SQL-Prozedur erfolgreich abgeschlossen.
    
     

Sicherheitshalber sehen wir uns an, welchen Wert ORA_API beim Aufruf des gleichen Parameters zurückerhält: 

    
    
     SQL> connect ora_api/ora_api;
    
     Connect durchgeführt. 
    
     SQL> set serveroutput on
    
     SQL> begin   
     2 	dbms_output.put_line(   
     3 	param.get_string('TEST', 'DEFAULT'));   
     4 end;   
     5 / 
    
     Testwert
    
     PL/SQL-Prozedur erfolgreich abgeschlossen.

Wie Sie sehen, bleibt der Vorgabewert in der zentralen Tabelle PARAMETER_TAB unverändert erhalten. Alles funktioniert wie geplant, auch die Ausgabe einer Fehlermeldung, falls unser Parameter etwas zu lang geraten sein sollte, geht: 

    
    
       
     SQL> connect scott/tiger 
    
     Connect durchgeführt.
    
     SQL> begin   
     2 	param.set_string(   
     3 	'TEST', 'DEFAULT',   
     4 	'Ein gaaaaaaaaaaaaaaaaaaaaaanz langer Wert');   
     5 end;   
     6 / 
    
     begin  
     *
    
     FEHLER in Zeile 1:   
     ORA-20000: Maximallänge von 25 Zeichen überschritten.  
     ORA-06512: in "ORA_API.PARAM_PKG", Zeile 106  
     ORA-06512: in "ORA_API.PARAM_PKG", Zeile 164   
     ORA-06512: in Zeile 2

Nun haben wir also die Keimzelle für eine leistungsfähige Parameterverwaltung. Dieser Workshop war nur am Rande ein Problem in PL/SQL, denn die eigentliche Funktionalität des Packages ist überschaubar. Ich habe die Chance genutzt, Ihnen in diesem Workshop eine Strategie der Verteilung von Packages auf mehrere Benutzer aufzuzeigen, die Ihnen in Ihren Projekten mit Sicherheit hilfreich sein wird. Gleichzeitig wirft dieser Workshop ein Licht darauf, dass PL/SQL-Entwicklung vor allem auch das Arbeiten mit den Möglichkeiten der Datenbank umfasst.
