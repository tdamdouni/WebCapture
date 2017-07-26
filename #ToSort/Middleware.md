# Middleware

_Captured: 2015-10-23 at 00:32 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Middleware)_

**Middleware** ([englisch](https://de.m.wikipedia.org/wiki/Englische_Sprache) fur _Diensteschicht_ oder _Zwischenanwendung_) bezeichnet in der [Informatik](https://de.m.wikipedia.org/wiki/Informatik) anwendungsneutrale [Programme](https://de.m.wikipedia.org/wiki/Computerprogramm), die so zwischen [Anwendungen](https://de.m.wikipedia.org/wiki/Anwendungsprogramm) vermitteln, dass die Komplexitat dieser Applikationen und ihre Infrastruktur verborgen werden.[[1]](https://de.m.wikipedia.org/wiki/Middleware) Man kann Middleware auch als eine Verteilungsplattform, d. h. als ein [Protokoll](https://de.m.wikipedia.org/wiki/Netzwerkprotokoll) (oder Protokollbundel) auf einer hoheren [Schicht](https://de.m.wikipedia.org/wiki/Schichtenmodell) als jener der gewohnlichen Rechnerkommunikation auffassen. Im Gegensatz zu niveautieferen Netzwerkdiensten, welche die einfache Kommunikation zwischen Rechnern handhaben, unterstutzt Middleware die Kommunikation zwischen _Prozessen_.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/e/eb/Middleware.png/220px-Middleware.png)

> _Middleware ist eine zusatzliche Schicht zwischen Betriebssystem und Anwendungen._

Im Bereich der [Computerspieleentwicklung](https://de.m.wikipedia.org/wiki/Computerspiel) werden hingegen Subsysteme fur Teilbereiche wie etwa die Spielphysik als _Middleware_ bezeichnet. Diese Middleware wird oft von Fremdentwicklern hergestellt und angeboten.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Middleware_Schema.svg/330px-Middleware_Schema.svg.png)

> _Aufbau: Middleware_

Middleware stellt eine Ebene in einem komplexen [Software](https://de.m.wikipedia.org/wiki/Software)system dar, die als „Dienstleister" anderen ansonsten entkoppelten Softwarekomponenten den Datenaustausch ermoglicht. Meist erfolgt diese Kommunikation mit Hilfe eines [Netzwerkes](https://de.m.wikipedia.org/wiki/Rechnernetz), das durch die Middleware fur die sie benutzenden Softwarekomponenten transparent gemacht wird. Middleware arbeitet dabei auf einem hohen Niveau innerhalb des [Schichtenmodells](https://de.m.wikipedia.org/wiki/Schichtenmodell): Ihre Aufgabe ist also nicht die Low-Level-Kommunikation fur einzelne [Bytes](https://de.m.wikipedia.org/wiki/Byte) (wie sie beispielsweise schon ein [Betriebssystem](https://de.m.wikipedia.org/wiki/Betriebssystem) bereitstellt). Middleware organisiert den Transport komplexer Daten (sog. _messaging_), vermittelt Funktionsaufrufe zwischen den Komponenten (sog. _[Remote Procedure Calls](https://de.m.wikipedia.org/wiki/Remote_Procedure_Call)_), stellt die [Transaktionssicherheit](https://de.m.wikipedia.org/wiki/Transaktion_\(Informatik\)) uber ansonsten unabhangige Teilsysteme her (Funktion als [Transaktions-Monitor](https://de.m.wikipedia.org/wiki/Transaktions-Monitor)) etc.

Middleware-Software ist als [Standardsoftware](https://de.m.wikipedia.org/wiki/Standardsoftware) von mehreren Herstellern verfugbar. Technisch stellt sie [Software-Schnittstellen](https://de.m.wikipedia.org/wiki/Application_Programming_Interface) oder [Dienste](https://de.m.wikipedia.org/wiki/Systemdienst) bereit. Eine Softwarekomponente _A_, die die Middleware-Schicht benutzen mochte, um mit einer Softwarekomponente _B_ zu kommunizieren, kann diese Schnittstellen benutzen. Die entsprechenden Aufrufe werden von der Middleware-Softwarekomponente uber ein Netzwerk weitergereicht. Dabei werden in der Regel gebrauchliche Netzwerk-Standardprotokolle - fast immer [IP](https://de.m.wikipedia.org/wiki/Internet_Protocol) und [TCP](https://de.m.wikipedia.org/wiki/Transmission_Control_Protocol), darauf aufbauend meist [HTTP](https://de.m.wikipedia.org/wiki/Hypertext_Transfer_Protocol), darauf aufbauend u. a. [SOAP](https://de.m.wikipedia.org/wiki/SOAP) oder [Web Services](https://de.m.wikipedia.org/wiki/Web_Services) - verwendet. Auf der Empfangerseite setzt die Middleware die Anforderung in einen Funktionsaufruf an die Software _B_ um. Gegebenenfalls leitet sie die „Antwort" der Komponente _B_ an Komponente _A_ auf demselben Weg zuruck.

Als Nachteil von Middleware kann ihre Große und Schwerfalligkeit genannt werden. Eine Optimierung der Leistungsfahigkeit dieser Programme ist durch den Programmierer nur selten moglich.

Eine grobe Unterteilung zum besseren Verstandnis:

Anwendungsorientierte Middleware
    Im Mittelpunkt steht neben der Kommunikation vor allem die Unterstutzung [verteilter Anwendungen](https://de.m.wikipedia.org/wiki/Verteilte_Anwendung). Beispiele sind sowohl allgemeine Architekturen, wie [CORBA](https://de.m.wikipedia.org/wiki/Common_Object_Request_Broker_Architecture), [JEE](https://de.m.wikipedia.org/wiki/JEE) oder [.NET](https://de.m.wikipedia.org/wiki/.NET), als auch komplette Betriebssysteme, wie z. B. 

  * [MHP](https://de.m.wikipedia.org/wiki/Multimedia_Home_Platform) (Multimedia Home Platform), Java-basiertes System fur das interaktive Fernsehen.
  * [MIDP](https://de.m.wikipedia.org/wiki/MIDP) (Mobile Information Device Profile), Java-basiertes System fur Mobiltelefone,

Kommunikationsorientierte Middleware
Nachrichtenorientierte Middleware
    Nachrichtenorientierte Middleware arbeitet nicht mit Methoden- oder [Funktionsaufrufen](https://de.m.wikipedia.org/wiki/Funktionsaufruf), sondern uber den Austausch von [Nachrichten](https://de.m.wikipedia.org/wiki/Nachricht) _(messages)_. Das Nachrichtenformat gibt die eingesetzte Middleware vor. Eine Nachrichtenorientierte Middleware kann sowohl [synchron](https://de.m.wikipedia.org/wiki/Synchrone_Kommunikation) als auch [asynchron](https://de.m.wikipedia.org/wiki/Asynchrone_Kommunikation) arbeiten. Bei einer asynchronen Variante wird eine [Warteschlange](https://de.m.wikipedia.org/wiki/Warteschlange) verwendet, in die der message-Produzent seine Nachrichten stellt. Ein Konsument kann die Nachrichten dann konsumieren. Vorteile sind u.a. die vollstandige Entkopplung von Nachrichtensender und -empfanger und dass Anwendungen auch weiterarbeiten konnen, wenn Teilkomponenten ausgefallen sind. Eine Architektur fur Nachrichtenorientierte Middleware gibt z. B. [JMS](https://de.m.wikipedia.org/wiki/Java_Message_Service) vor.
