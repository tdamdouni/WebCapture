# Fundamental Modeling Concepts

_Captured: 2015-10-23 at 16:05 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Fundamental_Modeling_Concepts)_

Seit Ende der 1970er Jahre wurden ihre Grundlagen von [Siegfried Wendt](https://de.m.wikipedia.org/wiki/Siegfried_Wendt) und seinen Mitarbeitern und Schulern an der [Universitat Kaiserslautern](https://de.m.wikipedia.org/wiki/Technische_Universit%C3%A4t_Kaiserslautern) entwickelt. An dem 1999 unter Leitung von Siegfried Wendt gegrundeten [Hasso-Plattner-Institut](https://de.m.wikipedia.org/wiki/Hasso-Plattner-Institut) an der [Universitat Potsdam](https://de.m.wikipedia.org/wiki/Universit%C3%A4t_Potsdam) wurden diese Konzepte zunachst unter dem Namen SPIKES (**S**tructured **P**lans for **I**mproving **K**nowledge Transfer in **E**ngineering of **S**ystems) gelehrt, bevor sie im Jahre 2001 den Namen FMC (**F**undamental **M**odeling **C**oncepts) erhielten.

Mit FMC werden eine Vielzahl von Softwaresystemen analysiert, entworfen und dokumentiert. Bekannter Nutzer ist u.a das Walldorfer Softwarehaus [SAP](https://de.m.wikipedia.org/wiki/SAP), welches die [SAP R/3](https://de.m.wikipedia.org/wiki/SAP_R/3) Architektur damit dokumentiert. [Hasso Plattners](https://de.m.wikipedia.org/wiki/Hasso_Plattner) Begeisterung fur diese Methodik resultierte in der Grundung des HPI ([Hasso-Plattner-Institutes](https://de.m.wikipedia.org/wiki/Hasso-Plattner-Institut)), welches die Lehren von FMC in der Vergangenheit in der universitaren Grundausbildung vermittelte.

Nach FMC gibt es drei miteinander verwobene Arten, Softwaresysteme zu betrachten:

  * Aufbau des Systems
  * Ablaufe im System
  * Wertebereiche

Fur jede dieser Betrachtungsweisen gibt es einen Diagrammtyp, mit dessen Hilfe der jeweilige Aspekt zeichnerisch dargestellt werden kann. Die resultierenden, meist leicht zu erstellenden, aber auch leicht zu verstehenden [Diagramme](https://de.m.wikipedia.org/wiki/Diagramm) haben FMC unter seinen Anhangern popular gemacht.

Grundsatzlich dienen FMC-Diagramme einem von zwei Zwecken: Sie sollen entweder von einer Gruppe verwendet werden, um uber ein Softwaresystem zu kommunizieren, oder sie werden benutzt, um andere (Entwickler, Kunden, Manager etc.) in ein Softwaresystem einzufuhren. Im ersten Falle werden die Diagramme meist etwas umfangreicher, um die Kommunikation uber komplexere Zusammenhange zu erleichtern; im zweiten Fall werden aus didaktischen Grunden zumeist kleine Diagramme mit wenigen Komponenten verwendet. Immer aber sollen Ästhetik und Anschaulichkeit im Vordergrund stehen, da wesentlicher Antrieb in der Verwendung von FMC die Forderung der Kommunikation sein soll. Deshalb sind die Diagramme zwar wichtigster Bestandteil von FMC, erubrigen aber keinen Kommentar.

Allen Diagrammen ist gemein, dass es sich um sogenannte [bipartite Graphen](https://de.m.wikipedia.org/wiki/Bipartiter_Graph) handelt. Ein bipartiter Graph ist dabei ein [Graph](https://de.m.wikipedia.org/wiki/Graph_\(Graphentheorie\)), dessen [Knoten](https://de.m.wikipedia.org/wiki/Typen_von_Graphen_in_der_Graphentheorie) aus zwei verschiedenen [Klassen](https://de.m.wikipedia.org/wiki/Klasse_\(Mengenlehre\)) stammen, mit der Bedingung, dass kein Knoten direkt mit Knoten aus seiner Klasse verbunden sein darf. Die Knoten der einen Klasse werden immer als [Rechteck](https://de.m.wikipedia.org/wiki/Rechteck) gezeichnet (eckiger Knoten), die Knoten der anderen als [Kreis](https://de.m.wikipedia.org/wiki/Kreis_\(Geometrie\)), [Ellipse](https://de.m.wikipedia.org/wiki/Ellipse), [Oval](https://de.m.wikipedia.org/wiki/Oval_\(Geometrie\)) oder Stadion (Rechteck mit zwei angesetzten Halbkreisen an zwei gegenuberliegenden Seiten) gezeichnet (runder Knoten).

Außerdem konnen in allen Diagrammen dargestellte Zusammenhange nahezu beliebig in anderen Diagrammen gleichen Typs verfeinert oder [abstrahiert](https://de.m.wikipedia.org/wiki/Abstraktion) werden. Damit konnen alle fur die Software relevanten Abstraktionsstufen eines Systems mit der gleichen Methodik dargestellt werden.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/5/5b/Aufbaubild.gif/220px-Aufbaubild.gif)

> _FMC-Aufbaubild_

Ein Aufbaudiagramm beschreibt, wie eine Menge von Systemkomponenten zueinander in Beziehung stehen. Zu diesem Zwecke wird jede Komponente als _Akteur_, _Kanal_ oder _Speicher_ identifiziert. Kanale und Speicher werden auch als passive Komponenten bezeichnet, Akteure entsprechend als aktive Komponenten. Dabei konnen passive Komponenten nicht direkt mit anderen passiven Komponenten in Beziehung stehen, ebenso wenig wie aktive mit aktiven. Daraus resultiert ein bipartites Systemverstandnis, das seinen Niederschlag in bipartiten Aufbaubildern findet.

In Aufbaubildern werden aktive Komponenten durch eckige Knoten und passive Komponenten durch runde Knoten dargestellt, wobei Kanale meist durch einen kleineren Kreis, und Speicher durch ein großeres Oval oder Stadion dargestellt werden. Die _Kanten_ (Verbindungslinien) zwischen Speichern und Akteuren mussen _gerichtet_ sein, zwischen Kanalen und Akteuren konnen sie auch _ungerichtet_ sein. Die Richtung hat folgende Bedeutung:

  * Speicher/Kanal -> Akteur: Akteur liest aus Speicher bzw. empfangt vom Kanal
  * Akteur -> Speicher/Kanal: Akteur schreibt in Speicher bzw. sendet uber Kanal

Es gibt keine Kanten, die in beide Richtungen gerichtet sind. Stattdessen werden, um auszudrucken, dass ein Akteur sowohl aus einem Speicher liest als auch in diesen schreibt, zwei entgegengesetzt gerichtete Kanten verwendet (auch als _modifizierender Zugriff_ bezeichnet). Bei Kanalen wird im Gegensatz dazu eine ungerichtete Kante benutzt.

Knoten konnen gruppiert werden, um Gemeinsamkeiten zu veranschaulichen. Dazu wird einfach ein weiterer Knoten eingefuhrt, der diese anderen Knoten enthalt. So konnen einige Akteure und Speicher Teil eines großeren Akteurs sein, dessen innerer Aufbau dargestellt werden soll, oder es gibt eine Menge von Speichern, auf die vom selben Akteur zugegriffen werden soll.

Eine spezielle Form des Kanals ist ein Request/Response-Kanal, bei dem eine benutzende Komponente einen Dienst einer anderen Komponente aufruft und eine entsprechende Antwort erhalt. Diese Kanale werden mit einem "R" und einem Pfeil gekennzeichnet, der von der aufrufenden zur aufgerufenen Komponente zeigt.

![](http://upload.wikimedia.org/wikipedia/de/4/43/FMC_Strukturvarianz.gif)

> _Beispiel fur die Darstellung von Strukturvarianz mit FMC_

Die Struktur vieler Softwaresysteme kann sich zur Laufzeit andern. Diese Strukturvarianz wird in FMC folgendermaßen interpretiert: Das betroffene Teilsystem wird unabhangig von seiner tatsachlichen Struktur als Speicher aufgefasst, das von einem nicht in diesem Teilsystem enthaltenen Akteur modifiziert werden kann. Entsprechend werden im Aufbaubild ein Speicher (zur Unterscheidung mit gestrichelter Außenlinie), der dieses Teilsystem enthalt, und der modifizierende Zugriff des Strukturvarianz-Akteurs auf diesen Speicher eingezeichnet.

Ablaufe werden mit einer Klasse von [Petrinetzen](https://de.m.wikipedia.org/wiki/Petrinetz), den Bedingungs-Ereignis-Netzen, dargestellt, da diese ebenfalls bipartit sind. In FMC-Petrinetzen kann jede Stelle normalerweise nur eine Marke aufnehmen, so dass die Schaltregel lautet:

_Eine Transition schaltet genau dann, wenn alle Eingangsmarken belegt sind und alle Ausgangsmarken, die nicht gleichzeitig Eingangsmarken sind, frei sind._

Zusatzlich gibt es noch Stellen, die beliebig viele Stellen aufnehmen konnen und durch einen Doppelkreis dargestellt werden. Besondere ,unendliche' Stellen sind [Stack](https://de.m.wikipedia.org/wiki/Stapelspeicher)-Stellen und Rucksprungstellen.

Außerdem gibt es in FMC-Petrinetzen das Mittel der Auflosung von Konflikten uber Bedingungsevaluierung. Gehen von einer Stelle mehrere Kanten ab, so konnen Bedingungen an diese Kanten geschrieben werden, anhand derer bestimmt werden kann, in welchem Fall welche Transition schaltet.

Hierbei handelt es sich um leicht veranderte und erweiterte [Entity-Relationship-Diagramme](https://de.m.wikipedia.org/wiki/Entity-Relationship-Modell). [Entitaten](https://de.m.wikipedia.org/wiki/Entit%C3%A4t) (Gegenstande) sind in FMC-Diagrammen runde Knoten, [Relationen](https://de.m.wikipedia.org/wiki/Relation) eckige. Entitaten konnen mit [Attributen](https://de.m.wikipedia.org/wiki/Attribut_\(Relationale_Algebra\)) behaftet werden, die als Liste im Knoten der Entitat notiert werden. Abstraktion ermoglicht es Entitaten, Relationen zu enthalten, so dass Relationen in Relation zu anderen Entitaten oder Relationen stehen konnen. Partitionen von Entitaten werden entweder dargestellt, indem die Sub-Entitaten in die zu partionierende Entitat gezeichnet werden, oder durch das dreieckige Partitionssymbol (das sozusagen die "Partitionsrelation" darstellt).

Zur exemplarischen Darstellung von quadratischen Relationen, d. h. Relationen auf _einer_ Menge von Elementen, konnen sogenannte Schichtungsdiagramme genutzt werden. Dabei handelt es sich um die verkurzte Darstellung einer Matrixdarstellung, mit der sich beliebige zwei-stellige Relationen darstellen lassen. Beispielsweise kann dieser Diagrammtyp dazu genutzt werden, die Aufrufschichtung von Prozeduren oder die Anhangigkeiten der Pakete innerhalb eines Computerprogrammes darzustellen (wobei der Rekursionsfall ebenfalls darstellbar ist).

Obwohl diese Form der Darstellung in einer Reihe FMC-basierter Modellierungsdokumente verwendet wird, ist sie nicht als konzeptioneller _Bestandteil_ von FMC angesehen. Vielmehr handelt es sich um die fallweise nutzliche Erganzung der Beschreibung, so wie fur bestimmte andere Aspekte UML-Klassendiagramme oder Bildschirmfotos zweckmaßige Beschreibungsmittel sind.

    Eine PDF-Fassung, die durch den Autor nach Einstellung der ursprunglichen Verlagsauflage freigegeben wurde. Auch wenn dieses Werk nicht speziell auf die Beschreibung von FMC abzielt, sondern in Inhalt und Struktur sehr viel grundsatzlicher angelegt ist, so wird der interessierte Leser hier dennoch das FMC zugrundeliegende Erkenntnisfundament erkennen.
