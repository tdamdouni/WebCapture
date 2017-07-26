# Versionsverwaltung

_Captured: 2015-10-23 at 18:02 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Versionsverwaltung)_

Eine **Versionsverwaltung** ist ein System, das zur Erfassung von Änderungen an Dokumenten oder Dateien verwendet wird. Alle Versionen werden in einem Archiv mit [Zeitstempel](https://de.m.wikipedia.org/wiki/Zeitstempel) und Benutzerkennung gesichert und konnen spater wiederhergestellt werden. Versionsverwaltungssysteme werden typischerweise in der Softwareentwicklung eingesetzt, um [Quelltexte](https://de.m.wikipedia.org/wiki/Quelltext) zu verwalten. Versionsverwaltung kommt auch bei [Buroanwendungen](https://de.m.wikipedia.org/wiki/B%C3%BCroanwendung) oder [Content-Management-Systemen](https://de.m.wikipedia.org/wiki/Content-Management-System) zum Einsatz.

Ein Beispiel ist auch die [Wikipedia](https://de.m.wikipedia.org/wiki/Wikipedia), hier erzeugt die Software nach jeder Änderung eines Artikels eine neue Version. Alle Versionen bilden in Wikipedia eine Kette, in der die letzte Version gultig ist; es sind keine Varianten vorgesehen. Da zu jedem Versionswechsel die grundlegenden Angaben wie Verfasser und Uhrzeit festgehalten werden, kann genau nachvollzogen werden, wer wann was geandert hat. Bei Bedarf - beispielsweise bei versehentlichen Änderungen - kann man zu einer fruheren Version zuruckkehren.

Die Versionsverwaltung ist eine Form des [Variantenmanagements](https://de.m.wikipedia.org/wiki/Variantenmanagement); dort sind verschiedene Sprachvarianten oder modal auch anders bestimmte Varianten moglich. Fur Versionsverwaltungssysteme ist die Abkurzung **VCS** (Version Control System) gebrauchlich.

  * [Protokollierungen](https://de.m.wikipedia.org/wiki/Protokoll) der Änderungen: Es kann jederzeit nachvollzogen werden, wer wann was geandert hat.
  * [Wiederherstellung](https://de.m.wikipedia.org/wiki/Rollback) von alten Standen einzelner Dateien: Somit konnen versehentliche Änderungen jederzeit wieder ruckgangig gemacht werden.
  * [Archivierung](https://de.m.wikipedia.org/wiki/Elektronische_Archivierung) der einzelnen Stande eines Projektes: Dadurch ist es jederzeit moglich, auf alle Versionen zuzugreifen.
  * Koordinierung des gemeinsamen Zugriffs von mehreren Entwicklern auf die Dateien.
  * Gleichzeitige Entwicklung mehrerer [Entwicklungszweige](https://de.m.wikipedia.org/wiki/Abspaltung_\(Softwareentwicklung\)) (engl. _Branches_) eines Projektes.

Ein _Branch_, zu deutsch Zweig, ist eine Abspaltung von einer anderen Version, so dass unterschiedliche Versionen parallel weiterentwickelt werden konnen. Änderungen konnen dabei von einem Branch auch wieder in einen anderen einfließen, das wird dann als _Merging_, zu deutsch verschmelzen, bezeichnet. Oft wird der Hauptentwicklungszweig als _Trunk_ (z. B. bei [Subversion](https://de.m.wikipedia.org/wiki/Apache_Subversion)) oder _Master_ (z. B. bei [Git](https://de.m.wikipedia.org/wiki/Git)) bezeichnet. Branches konnen zum Beispiel fur neue Hauptversionen einer Software erstellt werden oder fur Entwicklungszweige fur unterschiedliche Betriebssysteme oder aber auch, um experimentelle Versionen zu haben. Wird ein Zweig in einer neuen, unabhangigen Versionsverwaltung erstellt, spricht man von einem [Fork](https://de.m.wikipedia.org/wiki/Abspaltung_\(Softwareentwicklung\)). Ein bestimmter Stand kann auch mit einem _Tag_ (einem frei wahlbaren Bezeichner) gekennzeichnet werden.

Damit die eingesetzten Programme wie z. B. [Texteditoren](https://de.m.wikipedia.org/wiki/Texteditor) oder [Compiler](https://de.m.wikipedia.org/wiki/Compiler) mit den im _[Repository](https://de.m.wikipedia.org/wiki/Repository)_ (engl. Behalter, Aufbewahrungsort) abgelegten Dateien arbeiten konnen, ist es erforderlich, dass jeder Entwickler sich den aktuellen (oder einen alteren) Stand des Projektes in Form eines Verzeichnisbaumes aus herkommlichen Dateien erzeugen kann. Ein solcher Verzeichnisbaum wird als _Arbeitskopie_ bezeichnet. Ein wichtiger Teil des Versionsverwaltungssystems ist ein Programm, das in der Lage ist, diese _Arbeitskopie_ mit den Daten des Repositorys zu synchronisieren. Das Übertragen einer Version aus dem Repository in die Arbeitskopie wird als _Checkout_, _Auschecken_ oder _Aktualisieren_ bezeichnet, wahrend die umgekehrte Übertragung _Check-in_, _Einchecken_ oder _[Commit](https://de.m.wikipedia.org/wiki/Commit)_ genannt wird. Solche Programme werden entweder [kommandozeilenorientiert](https://de.m.wikipedia.org/wiki/Kommandozeile), mit [grafischer Benutzeroberflache](https://de.m.wikipedia.org/wiki/Grafische_Benutzeroberfl%C3%A4che) oder als Plugin fur [integrierte Softwareentwicklungsumgebungen](https://de.m.wikipedia.org/wiki/Integrierte_Entwicklungsumgebung) ausgefuhrt. Haufig werden mehrere dieser verschiedenen Zugriffsmoglichkeiten wahlweise bereitgestellt.

Es gibt drei Arten der Versionsverwaltung, die alteste funktioniert lokal, also nur auf einem Computer, die nachste Generation funktionierte mit einem zentralen Archiv und die neueste Generation arbeitet verteilt, also ohne zentrales Archiv. Allen gemein ist, dass die Versionsverwaltungssoftware dabei ublicherweise nur die Unterschiede zwischen zwei Versionen speichert, um Speicherplatz zu sparen. Die meisten Systeme verwenden hierfur ein eigenes [Dateiformat](https://de.m.wikipedia.org/wiki/Dateiformat) oder eine [Datenbank](https://de.m.wikipedia.org/wiki/Datenbank). Dadurch kann eine große Zahl von Versionen archiviert werden. Durch dieses Speicherformat kann jedoch nur mit der Software des Versionsverwaltungssystems auf die Daten zugegriffen werden, die die gewunschte Version bei einem Abruf unmittelbar aus den archivierten Versionen rekonstruiert.

Bei der lokalen Versionsverwaltung wird oft nur eine einzige Datei versioniert, diese Variante wurde mit Werkzeugen wie [SCCS](https://de.m.wikipedia.org/wiki/SCCS) und [RCS](https://de.m.wikipedia.org/wiki/Revision_Control_System) umgesetzt. Sie findet auch heute noch Verwendung in Buroanwendungen, die Versionen eines Dokumentes in der Datei des Dokuments selbst speichern. Auch in [technischen Zeichnungen](https://de.m.wikipedia.org/wiki/Technische_Zeichnung) werden Versionen zum Beispiel durch einen Ä[nderungsindex](https://de.m.wikipedia.org/wiki/%C3%84nderungsindex) verwaltet.

Diese Art ist als [Client-Server-System](https://de.m.wikipedia.org/wiki/Client-Server-System) aufgebaut, sodass der Zugriff auf ein Repository auch uber Netzwerk erfolgen kann. Durch eine [Rechteverwaltung](https://de.m.wikipedia.org/wiki/Mehrbenutzersystem) wird dafur gesorgt, dass nur berechtigte Personen neue Versionen in das Archiv legen konnen. Die Versionsgeschichte ist hierbei nur im Repository vorhanden. Dieses Konzept wurde vom Open-Source-Projekt [Concurrent Versions System](https://de.m.wikipedia.org/wiki/Concurrent_Versions_System) (CVS) popular gemacht, mit [Subversion](https://de.m.wikipedia.org/wiki/Apache_Subversion) (SVN) neu implementiert und von vielen kommerziellen Anbietern verwendet.

Die verteilte Versionsverwaltung (**DVCS**, distributed VCS) verwendet kein zentrales Repository mehr. Jeder, der an dem verwalteten Projekt arbeitet, hat sein eigenes Repository und kann dieses mit jedem beliebigen anderen Repository abgleichen. Die Versionsgeschichte ist dadurch genauso verteilt. Änderungen konnen lokal verfolgt werden, ohne eine Verbindung zu einem Server aufbauen zu mussen.

Im Gegensatz zur zentralen Versionsverwaltung kommt es nicht zu einem Konflikt, wenn mehrere Benutzer dieselbe Version einer Datei andern. Die sich widersprechenden Versionen existieren zunachst parallel und konnen weiter geandert werden. Sie konnen spater in eine neue Version zusammengefuhrt werden. Dadurch entsteht ein [gerichteter azyklischer Graph](https://de.m.wikipedia.org/wiki/Graph_\(Graphentheorie\)) ([Polyhierarchie](https://de.m.wikipedia.org/wiki/Polyhierarchie)) anstatt einer Kette von Versionen. In der Praxis werden bei der Verwendung in der Softwareentwicklung meist einzelne Features oder Gruppen von Features in separaten Versionen entwickelt und diese bei großeren Projekten von Personen mit einer Integrator-Rolle uberpruft und zusammengefuhrt.

Systembedingt bieten verteilte Versionsverwaltungen keine Locks. Da wegen der hoheren Zugriffsgeschwindigkeit die Granularitat der gespeicherten Änderungen viel kleiner sein kann, konnen sie sehr leistungsfahige, weitgehend automatische Merge-Mechanismen zur Verfugung stellen.

Eine Unterart der Versionsverwaltung bieten einfachere Patchverwaltungssysteme, die Änderungen nur in eine Richtung in Produktivsysteme einspeisen.

Obwohl konzeptionell nicht unbedingt notwendig, existiert in verteilten Versionsverwaltungsszenarien ublicherweise ein offizielles Repository. Das offizielle Repository wird von neuen Projektbeteiligten zu Beginn ihrer Arbeit geklont, d.h. auf das lokale System kopiert.

Diese Arbeitsweise eines Versionsverwaltungssystems wird auch als Lock Modify Unlock bezeichnet. Die zugrunde liegende Philosophie wird **pessimistische Versionsverwaltung** genannt. Einzelne Dateien mussen vor einer Änderung durch den Benutzer gesperrt und nach Abschluss der Änderung wieder freigegeben werden. Wahrend sie gesperrt sind, verhindert das System Änderungen durch andere Benutzer. Der Vorteil dieses Konzeptes ist, dass kein Zusammenfuhren von Versionen erforderlich ist, da nur immer ein Entwickler eine Datei andern kann. Der Nachteil ist, dass man unter Umstanden auf die Freigabe eines Dokuments warten muss, um eine eigene Änderung einzubringen. Zu beachten ist, dass Binardateien (im Gegensatz zu Quelltextdateien) in der Regel diese Arbeitsweise erfordern, da das Versionsverwaltungssystem verteilte Änderungen nicht automatisch synchronisieren kann. Ältester Vertreter dieser Arbeitsweise ist das [Revision Control System](https://de.m.wikipedia.org/wiki/Revision_Control_System), ebenso bekannt ist [Visual SourceSafe](https://de.m.wikipedia.org/wiki/Visual_SourceSafe). Verteilte Versionsverwaltungssysteme kennen systembedingt diese Arbeitsweise nicht.

Ein solches System lasst gleichzeitige Änderungen durch mehrere Benutzer an einer Datei zu. Anschließend werden diese Änderungen automatisch oder manuell zusammengefuhrt ([Merge](https://de.m.wikipedia.org/wiki/Merge)). Somit wird die Arbeit des Entwicklers wesentlich erleichtert, da Änderungen nicht im Voraus angekundigt werden mussen. Insbesondere wenn viele Entwickler raumlich getrennt arbeiten, wie es beispielsweise bei Open-Source-Projekten haufig der Fall ist, ermoglicht dies erst effizientes Arbeiten, da kein direkter Kontakt zwischen den Entwicklern benotigt wird. Problematisch bei diesem System sind Binardateien, da diese oft nicht automatisch zusammengefuhrt werden konnen, sofern kein passendes Werkzeug verfugbar ist. Manche Vertreter dieser Gattung unterstutzen daher auch alternativ das Lock-Modify-Write-Konzept fur bestimmte Dateien.

Die zugrunde liegende Philosophie wird als **optimistische Versionsverwaltung** bezeichnet und wurde entwickelt, um die Schwachen der pessimistischen Versionsverwaltung zu beheben. Alle modernen zentralen und verteilten Systeme setzen dieses Verfahren um.

Über die Grenze des abspeichernden Mediums, der [Datei](https://de.m.wikipedia.org/wiki/Datei), hinaus geht die Objekt-basierte Versionierung. Objekte werden in der Informatik als sogenannte [Instanzen](https://de.m.wikipedia.org/wiki/Instanz_\(Informatik\)), also Auspragungen eines Schemas, erzeugt. Auch diese konnen versioniert gespeichert werden. Die Versionsverwaltung, welche die unterschiedlichen Objektversionen abspeichert, muss mit den entsprechenden Objekttypen umgehen konnen. Aus dem Grund liest ein solches System nicht allein die Datei und uberpruft diese auf Veranderungen, sondern kann die darin enthaltene [Semantik](https://de.m.wikipedia.org/wiki/Semantik) interpretieren. Üblicherweise werden Objekte dann nicht dateibasiert, sondern in einer Datenbank abgespeichert. [Produktdatenmanagement](https://de.m.wikipedia.org/wiki/Produktdatenmanagement)-Systeme (PDM-Systeme) verwalten ihre Daten nach diesem Prinzip.

Die folgende Tabelle enthalt einige Versionsverwaltungssysteme als Beispiele fur die verschiedenen Auspragungsarten.

[Open-Source](https://de.m.wikipedia.org/wiki/Open_Source)-Systeme [Proprietare](https://de.m.wikipedia.org/wiki/Propriet%C3%A4r) Systeme

**Zentrale Systeme**

  * [RCS](https://de.m.wikipedia.org/wiki/Revision_Control_System)
  * [CVS](https://de.m.wikipedia.org/wiki/Concurrent_Versions_System)
  * [Subversion](https://de.m.wikipedia.org/wiki/Apache_Subversion) (SVN)

  * [Alienbrain](https://de.m.wikipedia.org/wiki/Alienbrain)
  * [Perforce](https://de.m.wikipedia.org/wiki/Perforce)
  * [Team Foundation Server](https://de.m.wikipedia.org/wiki/Team_Foundation_Server)
  * [Visual SourceSafe](https://de.m.wikipedia.org/wiki/Visual_SourceSafe)
  * [ClearCase](https://de.m.wikipedia.org/wiki/Rational_ClearCase)
  * [IBM Rational Synergy](https://de.m.wikipedia.org/wiki/Rational_Synergy)
  * [PTC Integrity](https://de.m.wikipedia.org/w/index.php?title=PTC-Integrity&action=edit&redlink=1)
  * SAP [Design Time Repository](https://de.m.wikipedia.org/w/index.php?title=Design_Time_Repository&action=edit&redlink=1) (DTR)

**Verteilte Systeme**

  * [Bazaar](https://de.m.wikipedia.org/wiki/Bazaar)
  * [Darcs](https://de.m.wikipedia.org/wiki/Darcs)
  * [Fossil](https://de.m.wikipedia.org/wiki/Fossil_\(Software\))
  * [Git](https://de.m.wikipedia.org/wiki/Git)
  * [GNU arch](https://de.m.wikipedia.org/wiki/GNU_arch)
  * [Mercurial](https://de.m.wikipedia.org/wiki/Mercurial)
  * [Monotone](https://de.m.wikipedia.org/wiki/Monotone)

  * [BitKeeper](https://de.m.wikipedia.org/wiki/BitKeeper)
  * Rational Team Concert
