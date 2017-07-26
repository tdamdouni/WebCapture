# Java Platform, Enterprise Edition

_Captured: 2015-10-23 at 00:33 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/J2EE)_

**Java Platform, Enterprise Edition**, abgekurzt **Java EE** oder fruher **J2EE**, ist die [Spezifikation](https://de.m.wikipedia.org/wiki/Spezifikation) einer [Softwarearchitektur](https://de.m.wikipedia.org/wiki/Softwarearchitektur) fur die [transaktionsbasierte](https://de.m.wikipedia.org/wiki/Transaktion_\(Informatik\)) Ausfuhrung von in [Java](https://de.m.wikipedia.org/wiki/Java_\(Programmiersprache\)) programmierten Anwendungen und insbesondere Web-Anwendungen. Sie ist eine der großen [Plattformen](https://de.m.wikipedia.org/wiki/Plattform_\(Computer\)), die um den [Middleware](https://de.m.wikipedia.org/wiki/Middleware)-Markt kampfen. Großter Konkurrent ist dabei die [.NET](https://de.m.wikipedia.org/wiki/.NET)-[Plattform](https://de.m.wikipedia.org/wiki/Plattform_\(Computer\)) von [Microsoft](https://de.m.wikipedia.org/wiki/Microsoft).

In der Spezifikation werden Softwarekomponenten und Dienste definiert, die hauptsachlich in der Programmiersprache Java erstellt werden. Die Spezifikation dient dazu, einen allgemein akzeptierten Rahmen zur Verfugung zu stellen, um auf dessen Basis aus modularen [Komponenten](https://de.m.wikipedia.org/wiki/Komponente_\(Software\)) [verteilte](https://de.m.wikipedia.org/wiki/Verteiltes_System), [mehrschichtige](https://de.m.wikipedia.org/wiki/Mehrschichtig) Anwendungen entwickeln zu konnen. Klar definierte Schnittstellen zwischen den [Komponenten und Containern](https://de.m.wikipedia.org/wiki/Container_\(Entwurfsmuster\)) sollen dafur sorgen, dass Softwarekomponenten unterschiedlicher Hersteller [interoperabel](https://de.m.wikipedia.org/wiki/Interoperabilit%C3%A4t) sind, wenn sie sich an die Spezifikation halten, und dass die verteilte Anwendung gut [skalierbar](https://de.m.wikipedia.org/wiki/Skalierbarkeit) ist.

Bestandteile der Spezifikation werden innerhalb des [Java Community Process](https://de.m.wikipedia.org/wiki/Java_Community_Process) von diversen Unternehmen erarbeitet und schließlich der Öffentlichkeit in Form eines Dokuments und einer Referenzimplementierung zur Verfugung gestellt.

  * [Implementierungen](https://de.m.wikipedia.org/wiki/J2EE)

Die aktuelle Version der Java-EE-Spezifikation ist die Version 7.0[[1]](https://de.m.wikipedia.org/wiki/J2EE).

Der neue Name fur die Spezifikation lautet **Java Platform, Enterprise Edition**, kurz **Java EE** [[ˈdʒɑːvə ˌiːˈiː](https://de.m.wikipedia.org/wiki/Liste_der_IPA-Zeichen)]. Dies ersetzt die vorherige Abkurzung J2EE [[ˌdʒeɪˈtuː ˌiːˈiː](https://de.m.wikipedia.org/wiki/Liste_der_IPA-Zeichen)] (**Java 2 Platform, Enterprise Edition**).

Version Ausfuhrlicher Name Veroffentlichungsdatum der Final Release

1.0
Java 2 Platform Enterprise Edition, v 1.0
Dezember 1999

1.2
Java 2 Platform Enterprise Edition, v 1.2
2000

1.2.1
Java 2 Platform Enterprise Edition, v 1.2.1
23\. Mai 2000

1.3
Java 2 Platform Enterprise Edition, v 1.3
24\. September 2001

1.4
Java 2 Platform Enterprise Edition, v 1.4
24\. November 2003

5
Java Platform, Enterprise Edition, v 5
11\. Mai 2006

6
Java Platform, Enterprise Edition, v 6
10\. Dezember 2009

7
Java Platform, Enterprise Edition, v 7
12\. Mai 2013
![](http://upload.wikimedia.org/wikipedia/de/thumb/8/87/J2ee-overview.svg/400px-J2ee-overview.svg.png)

> _Schematischer Aufbau der Architektur, wie sie in der J2EE-Spezifikation 1.4 beschrieben ist_

Java-EE-Komponenten erfordern als [Laufzeitumgebung](https://de.m.wikipedia.org/wiki/Laufzeitumgebung) eine spezielle Infrastruktur, einen sogenannten Java EE [Application Server](https://de.m.wikipedia.org/wiki/Application_Server). Dieser Server stellt technische Funktionalitaten wie

  * Sicherheit (Security),
  * Persistenzdienste zum langfristigen Speichern von Java-Objekten,
  * Management der Komponenten uber den gesamten Lebenszyklus (inklusive [Instanziierung](https://de.m.wikipedia.org/wiki/Objekt_\(Programmierung\))),
  * Unterstutzung fur die Installation ([Deployment](https://de.m.wikipedia.org/wiki/Softwareverteilung))

zur Verfugung. Des Weiteren kapselt der Server den Zugriff auf die Ressourcen des zugrundeliegenden [Betriebssystems](https://de.m.wikipedia.org/wiki/Betriebssystem) (Dateisystem, Netzwerk, …).

Ein Java-EE-Server wird in diverse logische Systeme unterteilt. Diese werden [Container](https://de.m.wikipedia.org/wiki/Container_\(Entwurfsmuster\)) genannt. Die aktuelle Spezifikation erfordert die folgenden Container:

  * einen [JCA-Container](https://de.m.wikipedia.org/w/index.php?title=JCA-Container&action=edit&redlink=1) als Laufzeitumgebung fur [JCA](https://de.m.wikipedia.org/wiki/J2EE_Connector_Architecture) Connectoren. Dieser ist zwar nicht explizit definiert, faktisch jedoch muss jeder Application-Server-Hersteller diesen implementieren. Denn im [Enterprise Java Beans](https://de.m.wikipedia.org/wiki/Enterprise_Java_Beans) (EJB) sowie im Web-Container sind Restriktionen definiert, welche fur die JCA-Laufzeitumgebung nicht gelten. Dabei handelt es sich beispielsweise um das Starten von [Threads](https://de.m.wikipedia.org/wiki/Thread_\(Informatik\)) oder das Lesen und Schreiben in Dateien etc.

Es sind zahlreiche Implementierungen fur Java-EE-Server verfugbar, teils [proprietar](https://de.m.wikipedia.org/wiki/Propriet%C3%A4r), teils in Form frei verfugbarer [Open-Source](https://de.m.wikipedia.org/wiki/Open_Source)-Losungen (z. B. [JBoss](https://de.m.wikipedia.org/wiki/JBoss_Application_Server)). Eine Referenzimplementierung wird von [Oracle](https://de.m.wikipedia.org/wiki/Oracle) zur Verfugung gestellt. Zu beachten ist, dass nicht alle Server die Spezifikation von Java EE vollstandig abdecken. Jedoch veroffentlicht Oracle fur jede Version eine Liste der derzeit zertifizierten Server.[[2]](https://de.m.wikipedia.org/wiki/J2EE)

Als weitere Infrastrukturkomponente kommt fur die persistente Speicherung von Daten ein [Datenbankmanagementsystem](https://de.m.wikipedia.org/wiki/Datenbankmanagementsystem) (DBMS) zum Einsatz. Hierbei kann es sich um ein [relationales System](https://de.m.wikipedia.org/wiki/RDBMS) handeln, oder aber auch um ein vergleichbares System wie beispielsweise ein [OODBMS](https://de.m.wikipedia.org/wiki/Objektdatenbank). Die Anbindung der Datenbankmanagementsysteme erfolgt meist uber einen [JDBC](https://de.m.wikipedia.org/wiki/Java_Database_Connectivity)-Treiber.

Der clientseitige Zugriff auf eine Java-EE-Anwendung erfolgt oft uber einen [Browser](https://de.m.wikipedia.org/wiki/Webbrowser), daneben sind aber auch Applikations-Clients (Java-Applikationen, [CORBA](https://de.m.wikipedia.org/wiki/Common_Object_Request_Broker_Architecture)-Komponenten, [Web Service](https://de.m.wikipedia.org/wiki/Web_Service)-Clients) verbreitet.

Die Java-EE-[APIs](https://de.m.wikipedia.org/wiki/Application_Programming_Interface) beinhalten verschiedene Technologien, die die Funktionalitat des Basis-[Java-SE](https://de.m.wikipedia.org/wiki/Java_Platform,_Standard_Edition)-APIs erweitern bzw. ersetzen.[[3]](https://de.m.wikipedia.org/wiki/J2EE)

Name und Abkurzung Beschreibung J2EE 1.4 Java EE 5 Java EE 6 Java EE 7

[Enterprise JavaBeans](https://de.m.wikipedia.org/wiki/Enterprise_JavaBeans) (EJB)
beinhalten die [Geschaftslogik](https://de.m.wikipedia.org/wiki/Gesch%C3%A4ftslogik) einer Enterprise Anwendung oder gestatten Zugriff auf persistente Daten. Die Beans laufen in einem [EJB-Container](https://de.m.wikipedia.org/wiki/EJB-Container) ab. Es gibt drei unterschiedliche Typen von EJBs: 

  * Session-Beans, sowohl zustandsbehaftet als auch zustandslos, implementieren die Geschaftslogik und sind meistens vom [Client](https://de.m.wikipedia.org/wiki/Client) zugreifbar
  * Message-Driven-Beans, kurz MDB, fur die Verarbeitung von [JMS](https://de.m.wikipedia.org/wiki/Java_Message_Service)-Nachrichten, wurden in Version 2.1 neu eingefuhrt
  * Entity-Beans fur die Abbildung von persistenten Datenobjekten (ab Version 3.0 obsolet, da EJBs durch [Detachment](https://de.m.wikipedia.org/wiki/Enterprise_Java_Beans) auch außerhalb des Containers nutzbar sind)
Ja (2.1)
Ja (3.0)
Ja (3.1)
Ja (3.2)

[Java Servlet](https://de.m.wikipedia.org/wiki/Servlet)
erlaubt im Allgemeinen die Erweiterung von Servern, deren Protokoll auf Anfragen und Antworten basiert. Primar werden Servlets im Zusammenhang mit dem [Hypertext Transfer Protocol](https://de.m.wikipedia.org/wiki/Hypertext_Transfer_Protocol) (HTTP) verwendet, wo sie in einem Web-Container leben und Anfragen von [Webbrowsern](https://de.m.wikipedia.org/wiki/Webbrowser) beantworten.
Ja (2.4)
Ja (2.5)
Ja (3.0)
Ja (3.1)

[JavaServer Pages](https://de.m.wikipedia.org/wiki/JavaServer_Pages) (JSP)
sind Textdokumente, die zum einen aus statischem Text und zum anderen aus dynamischen Textelementen - den JSP-Elementen - bestehen. Die JSP-Seiten werden transparent vom Web-Container in ein Servlet umgewandelt.
Ja (2.0)
Ja (2.1)
Ja (2.2)
Ja (2.3)

[Webservices](https://de.m.wikipedia.org/wiki/Webservice) (WS)
definieren Schnittstellen zu EJBs, die mit einem Uniform Resource Identifier (URI) eindeutig identifizierbar sind und deren Schnittstellen als XML-Artefakte definiert, beschrieben und gefunden werden konnen.
Ja (1.0)
Ja (1.2)
Ja (1.3)
Ja (1.4)

[Java Naming and Directory Interface](https://de.m.wikipedia.org/wiki/Java_Naming_and_Directory_Interface) (JNDI)
ist eine gemeinsame Schnittstelle mit der alle Java-Klassen auf Namens- und Verzeichnisdienste zugreifen konnen. Über JNDI wird insbesondere der Zugriff auf Java-EE-Komponenten sichergestellt.
Ja (1.2)
Ja (1.2)
Ja (1.2 SE)
Ja (1.2 SE)

[Java Message Service](https://de.m.wikipedia.org/wiki/Java_Message_Service) (JMS)
ist eine API fur die asynchrone Nachrichtenverarbeitung.
Ja (1.1)
Ja (1.1)
Ja (1.1)
Ja (2.0)

[Java Transaction API](https://de.m.wikipedia.org/wiki/Java_Transaction_API) (JTA)
erlaubt der Anwendung die Steuerung der Transaktionsverwaltung. JTA ist die Java-Schnittstelle zu [Transaktionsmonitoren](https://de.m.wikipedia.org/wiki/Transaktionsmonitor). Standardmaßig wird diese Schnittstelle implementiert vom Java Transaction Service (JTS), welcher eine Schnittstelle zu [CORBA](https://de.m.wikipedia.org/wiki/CORBA) Object Transaction Service (OTS) bietet.
Ja (1.0.1B)
Ja (1.1)
Ja (1.1)
Ja (1.2)

[Java Authentication and Authorization Service](https://de.m.wikipedia.org/wiki/Java_Authentication_and_Authorization_Service) (JAAS)
ist eine Java-API, die es ermoglicht, Dienste zur Authentifikation und Zugriffsrechte in Java-Programmen bereitzustellen. JAAS implementiert ein Standard-[Pluggable Authentication Module](https://de.m.wikipedia.org/wiki/Pluggable_Authentication_Module) (PAM) und unterstutzt durch dieses Modul eine einfache [Authentifizierung](https://de.m.wikipedia.org/wiki/Authentifizierung) und benutzerbasierte [Autorisierung](https://de.m.wikipedia.org/wiki/Autorisierung).
Ja (1.0)
Ja (1.0)
Ja (1.0)
Ja (1.0)

[JavaMail](https://de.m.wikipedia.org/wiki/JavaMail)
erlaubt den Zugriff auf Mail Services, wie z. B. [SMTP](https://de.m.wikipedia.org/wiki/SMTP), [POP3](https://de.m.wikipedia.org/wiki/POP3) oder [IMAP](https://de.m.wikipedia.org/wiki/Internet_Message_Access_Protocol).
Ja (1.2)
Ja (1.4)
Ja (1.4)
Ja (1.5)

[Java Architecture for XML Binding](https://de.m.wikipedia.org/wiki/Java_Architecture_for_XML_Binding) (JAXB)
ermoglicht es, ein [XML-Schema](https://de.m.wikipedia.org/wiki/XML-Schema) direkt an Java-Klassen zu binden. Wurde offiziell erst seit Java EE Version 1.5 gefordert, wird jedoch evt. schon vorher unterstutzt.
Nein
Ja (2.0)
Ja (2.2)
Ja (2.2)

[Java API for XML Processing](https://de.m.wikipedia.org/wiki/Java_API_for_XML_Processing) (JAXP)
hilft dem Entwickler bei der Bearbeitung von [XML](https://de.m.wikipedia.org/wiki/Extensible_Markup_Language)-Dokumenten.
Ja (1.2)
Ja (1.3)
Ja (1.4 (SE))
Ja (1.4 (SE))

[Java API for XML-based RPC](https://de.m.wikipedia.org/wiki/Java_API_for_XML-based_RPC) (JAX-RPC)
ermoglicht den entfernten Zugriff auf [RPC](https://de.m.wikipedia.org/wiki/Remote_Procedure_Call)-Dienste.
Ja (1.0)
Ja (1.1)
Ja (1.1)
Ja (1.1)

[Java API for RESTful Web Services](https://de.m.wikipedia.org/wiki/Java_API_for_RESTful_Web_Services) (JAX-RS)
Nein
Nein
Ja (1.1)
Ja (2.0)

[Java API for XML Registries](https://de.m.wikipedia.org/w/index.php?title=Java_API_for_XML_Registries&action=edit&redlink=1) (JAXR)
dient dazu, einen transparenten Zugriff auf so genannte Business-Registries, wie beispielsweise [ebXML](https://de.m.wikipedia.org/wiki/EbXML) oder ein [UDDI](https://de.m.wikipedia.org/wiki/UDDI) basiertes Verzeichnis sicherzustellen.
Ja (1.0)
Ja (1.0)
Ja (1.0)
Ja (1.0)

[Java Authorization Contract for Containers](https://de.m.wikipedia.org/w/index.php?title=Java_Authorization_Contract_for_Containers&action=edit&redlink=1) (JACC)
definiert diverse Sicherheitsrichtlinien fur die diversen Java-EE-Container.
Ja (1.0)
Ja (1.1)
Ja (1.4)
Ja (1.5)

[J2EE Connector Architecture](https://de.m.wikipedia.org/wiki/J2EE_Connector_Architecture) (JCA)
dient dazu, andere Systeme transparent zu integrieren (Stichwort: [EAI](https://de.m.wikipedia.org/wiki/Enterprise_Application_Integration)).
Ja (1.5)
Ja (1.5)
Ja (1.6)
Ja (1.7)

[JavaBeans Activation Framework](https://de.m.wikipedia.org/w/index.php?title=JavaBeans_Activation_Framework&action=edit&redlink=1) (JAF)
bietet die Moglichkeit, verschiedene Daten anhand des [MIME](https://de.m.wikipedia.org/wiki/Multipurpose_Internet_Mail_Extensions)-Headers zu erkennen.
Ja (1.0)
Ja (1.1)
Ja (1.1)
Ja (1.1)

[Java API for XML Web Services](https://de.m.wikipedia.org/wiki/Java_API_for_XML_Web_Services) (JAX-WS)
hilft bei der Erstellung von [Web Services](https://de.m.wikipedia.org/wiki/Web_Service) und zugehorigen [Clients](https://de.m.wikipedia.org/wiki/Client), die uber [XML](https://de.m.wikipedia.org/wiki/Extensible_Markup_Language) kommunizieren, z. B. uber [SOAP](https://de.m.wikipedia.org/wiki/SOAP).
Nein
Ja (2.0)
Ja (2.2)
Ja (2.2)

Web Service Metadata
beschreibt Web-Services mit [Java-Annotationen](https://de.m.wikipedia.org/wiki/Annotation_\(Java\))
Nein
Ja (2.0)
Ja (2.1)
Ja (2.1)

[Java Persistence API](https://de.m.wikipedia.org/wiki/Java_Persistence_API) (JPA)
stellt eine einheitliche und datenbankunabhangige Schnittstelle fur [Object-Relational-Mapping](https://de.m.wikipedia.org/wiki/Objektrelationale_Abbildung) und das Arbeiten mit [Entitaten](https://de.m.wikipedia.org/wiki/Entit%C3%A4t) bereit.
Nein
Ja (1.0)
Ja (2.0)
Ja (2.1)

[Streaming API for XML](https://de.m.wikipedia.org/wiki/Streaming_API_for_XML) (StAX)
ist eine Cursor basierte XML-Verarbeitung in Erganzung der [DOM](https://de.m.wikipedia.org/wiki/Document_Object_Model)\- und [SAX](https://de.m.wikipedia.org/wiki/Simple_API_for_XML)-Parser
Nein
Ja (1.0)
Ja (1.0)
Ja (1.0)

[JavaServer Faces](https://de.m.wikipedia.org/wiki/JavaServer_Faces) (JSF)
dient dazu Komponenten fur Benutzerschnittstellen in Webseiten einzubinden und die Navigation zu definieren.
Nein
Ja (1.2)
Ja (2.0)
Ja (2.2)

[Expression Language](https://de.m.wikipedia.org/w/index.php?title=Expression_Language&action=edit&redlink=1) (EL)
Nein
Nein
Ja (2.2)
Ja (3.0)

[JavaServer Pages Standard Tag Library](https://de.m.wikipedia.org/wiki/JavaServer_Pages_Standard_Tag_Library) (JSTL)
ist eine Sammlung von JSP-Tags fur die Strukturierung, XML, SQL, Internationalisierung und so weiter
Nein
Ja (1.2)
Ja (1.2)
Ja (1.2)

[Contexts and Dependency Injection](https://de.m.wikipedia.org/wiki/Contexts_and_Dependency_Injection) (CDI)
ist eine Technik um Felder nach dem [Inversion of Control](https://de.m.wikipedia.org/wiki/Inversion_of_Control)-Prinzip zu setzen. Es erlaubt dem Entwickler verschiedene fachliche Kontexte, miteinander zu verbinden. Es verbindet außerdem JSF mit EJB.
Nein
Nein
Ja (1.0)
Ja (1.1)

[Java API for WebSocket](https://de.m.wikipedia.org/w/index.php?title=Java_API_for_WebSocket&action=edit&redlink=1) (WebSocket)
Nein
Nein
Nein
Ja (1.0)

[Java API for JSON Processing](https://de.m.wikipedia.org/w/index.php?title=Java_API_for_JSON_Processing&action=edit&redlink=1) (JSON-P)
Nein
Nein
Nein
Ja (1.0)

[Batch Applications for the Java Platforms](https://de.m.wikipedia.org/w/index.php?title=Batch_Applications_for_the_Java_Platforms&action=edit&redlink=1) (Batch)
Nein
Nein
Nein
Ja (1.0)

[Bean Validation](https://de.m.wikipedia.org/w/index.php?title=Bean_Validation&action=edit&redlink=1)
Nein
Nein
Ja (1.0)
Ja (1.1)

[Managed Beans](https://de.m.wikipedia.org/w/index.php?title=Managed_Beans&action=edit&redlink=1)
Nein
Nein
Ja (1.0)
Ja (1.0)

[Concurrency Utilities for Java EE](https://de.m.wikipedia.org/w/index.php?title=Concurrency_Utilities_for_Java_EE&action=edit&redlink=1) (Concurrency Utilities)
Nein
Nein
Nein
Ja (1.0)

[Interceptors](https://de.m.wikipedia.org/w/index.php?title=Interceptors&action=edit&redlink=1)
Nein
Nein
Ja (1.1)
Ja (1.2)

[Common Annotations for the Java Platform](https://de.m.wikipedia.org/w/index.php?title=Common_Annotations_for_the_Java_Platform&action=edit&redlink=1)
Nein
Nein
Ja (1.1)
Ja (1.2)

[Authentication Service Provider Interface for Containers](https://de.m.wikipedia.org/w/index.php?title=Authentication_Service_Provider_Interface_for_Containers&action=edit&redlink=1) (JASPIC)
Nein
Nein
Ja (1.0)
Ja (1.1)

[Enterprise Edition Management API](https://de.m.wikipedia.org/w/index.php?title=Enterprise_Edition_Management_API&action=edit&redlink=1)
Nein
Nein
Ja (1.1)
Ja (1.1)

[Enterprise Edition Deployment API](https://de.m.wikipedia.org/w/index.php?title=Enterprise_Edition_Deployment_API&action=edit&redlink=1)
Nein
Nein
Ja (1.2)
Ja (1.2)
