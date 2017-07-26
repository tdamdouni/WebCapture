# Checkliste Incident-Priorität

_Captured: 2016-05-08 at 00:26 from [wiki.de.it-processmaps.com](http://wiki.de.it-processmaps.com/index.php/Checkliste_Incident-Priorit%C3%A4t)_

**ITIL-Prozess**: [ITIL 2011 Service Operation](http://wiki.de.it-processmaps.com/index.php/ITIL_Service_Operation_-_Servicebetrieb) \- [Incident Management](http://wiki.de.it-processmaps.com/index.php/Incident_Management)

**Checklisten-Kategorie**: [Checklisten ITIL 2011](http://wiki.de.it-processmaps.com/index.php/ITIL-Checklisten) \- Service Operation (Servicebetrieb)

**Quelle**: Checkliste "Richtlinie Incident-Priorisierung" aus der [ITIL-Prozesslandkarte](http://de.it-processmaps.com/produkte/itil-prozesslandkarte.html)

![Checkliste Incident-Priorität](http://wiki.de.it-processmaps.com/images/4/48/Incident-priorisierung.png)

Die _Richtlinie Incident-Priorisierung_ beschreibt die Regeln fur die Zuordnung von _Prioritaten zu Incidents_ und definiert, welche Incidents als _Major Incidents_ zu behandeln sind. Da die Eskalationsregeln fur Incidents in der Regel auf Prioritaten basieren, ist die Zuordnung der richtigen Prioritat maßgeblich fur die angemessene _Eskalation von Incidents_.

**Die Prioritat eines Incidents ergibt sich in der Regel aus der Bewertung von Incident-Auswirkung und Incident-Dringlichkeit, wobei**

  * Dringlichkeit _("Urgency")_ ausdruckt, wie schnell der Incident gelost werden muss, und
  * Auswirkung _("Impact")_ ausdruckt, wie umfangreich der Incident ist und welcher (potentielle) Schaden durch den Incident verursacht werden kann.

## Incident-Dringlichkeit (Dringlichkeits-Kategorien)

Dieser Abschnitt gibt _Incident-Dringlichkeits-Kategorien_ vor. Die Definitionen mussen auf die jeweilige Organisation genau abgestimmt sein, deshalb ist die folgenden Tabelle lediglich ein Beispiel:

Um die _Incident-Dringlichkeit_ zu bestimmen, wahle die hochste zutreffende Kategorie:

Kategorie  Beschreibung 

**Hoch (H)**

  * Der von dem Incident verursachte Schaden nimmt im schnell zu.
  * Die Aufgaben, die von den Mitarbeitern nicht erfullt werden konnen, sind sehr zeitkritisch.
  * Durch schnelles Handeln kann verhindert werden, dass aus einem Minor Incident ein Major Incident wird.
  * Mehrere Benutzer mit VIP-Status sind betroffen.

**Mittel (M)**

  * Der von dem Incident verursachte Schaden nimmt im Verlauf der Zeit substantiell zu.
  * Die Aufgaben, die von den Mitarbeitern nicht erfullt werden konnen, sind nur maßig zeitkritisch.
  * Ein einzelner Benutzer mit VIP-Status ist betroffen.

**Niedrig (N)**

  * Der von dem Incident verursachte Schaden nimmt im Verlauf der Zeit nur unwesentlich zu.
  * Die Aufgaben, die von den Mitarbeitern nicht erfullt werden konnen, sind nicht zeitkritisch.

## Incident-Auswirkung (Auswirkungs-Kategorien)

Dieser Abschnitt gibt _Incident-Auswirkungs-Kategorien_ vor. Die Definitionen mussen auf die jeweilige Organisation genau abgestimmt sein, deshalb ist die folgenden Tabelle lediglich ein Beispiel:

Um die _Incident-Auswirkung_ zu bestimmen, wahle die hochste zutreffende Kategorie:

Kategorie  Beschreibung 

**Hoch (H)**

  * Eine große Anzahl von Mitarbeitern ist betroffen und/oder kann ihre Aufgaben nicht erfullen.
  * Eine große Anzahl von Kunden ist betroffen und/oder ist in irgendeiner Weise akuten Nachteilen ausgesetzt.
  * Der finanzielle Schaden durch den Incident ist voraussichtlich hoher als (zum Beispiel) 10.000 EUR.
  * Eine Beschadigung der Reputation des Unternehmens in großem Umfang ist wahrscheinlich.
  * Es besteht Gefahr fur Leib und Leben.

**Mittel (M)**

  * Eine maßige Anzahl von Mitarbeitern ist betroffen und/oder kann ihre Aufgaben nicht wie vorgesehen erfullen.
  * Eine maßige Anzahl von Kunden ist betroffen und/oder erfahrt Einschrankungen beim Komfort.
  * Der finanzielle Schaden durch den Incident liegt voraussichtlich zwischen (zum Beispiel) 1.000 EUR und 10.000 EUR.
  * Eine Beschadigung der Reputation des Unternehmens in maßigem Umfang ist wahrscheinlich.

**Niedrig (N)**

  * Eine minimale Anzahl von Mitarbeitern ist betroffen und/oder kann ihre Aufgaben erfullen, jedoch nur mit zusatzlichem Aufwand.
  * Eine minimale Anzahl von Kunden ist betroffen und/oder erfahrt Einschrankungen beim Komfort, jedoch nur in geringem Umfang.
  * Der finanzielle Schaden durch den Incident ist voraussichtlich weniger als (zum Beispiel) 1.000 EUR.
  * Eine Beschadigung der Reputation des Unternehmens ist nur in minimalem Umfang zu erwarten.

Die _Prioritat eines Incidents_ leitet sich aus [Dringlichkeit](http://wiki.de.it-processmaps.com/index.php/Checkliste_Incident-Priorit%C3%A4t) und [Auswirkung](http://wiki.de.it-processmaps.com/index.php/Checkliste_Incident-Priorit%C3%A4t) ab.

Wenn Klassen zur Bestimmung von Dringlichkeit und Auswirkung definiert sind, kann eine Dringlichkeits-Auswirkungs-Matrix ("Urgency-Impact Matrix" oder auch "Incident Priority Matrix" genannt) verwendet werden, um Klassen von Prioritaten festzulegen, wie im folgenden Beispiel:

Auswirkung 

H 
M 
N 

**Dringlichkeit**
H 
1 
2 
3 

M 
2 
3 
4 

N 
3 
4 
5 

Prioritats-Code  Beschreibung  Reaktionszeit-Vorgabe  Losungszeit-Vorgabe 

**1**
Kritisch 
Sofort 
1 Stunde 

**2**
Hoch 
10 Minuten 
4 Stunden 

**3**
Mittel 
1 Stunde 
8 Stunden 

**4**
Niedrig 
4 Stunden 
24 Stunden 

**5**
Sehr niedrig 
1 Tag 
1 Woche 

## Kriterien fur die Behandlung eines Incidents als Major Incident

_Major Incidents_ erfordern die Etablierung eines [Major Incident Teams](http://wiki.de.it-processmaps.com/index.php/Rollen_in_ITIL) und werden durch den Prozess [Behebung von Major Incidents](http://wiki.de.it-processmaps.com/index.php/Incident_Management) behandelt.

Über das oben gezeigte Schema hinaus ist es oft angeraten, zusatzliche und leicht verstandliche Indikatoren zur [Bestimmung von Major Incidents](http://wiki.de.it-processmaps.com/index.php/Checkliste_Incident-Priorit%C3%A4t) zu definieren. Beispiele fur solche Indikatoren sind:

  1. Bestimmte (Gruppen von) geschaftskritischen Services, Anwendungen oder Infrastruktur-Komponenten sind nicht verfugbar und die voraussichtliche Zeit bis zur Wiederherstellung ist zu lang oder unbekannt (hier ist zu spezifizieren, welche Services, Anwendungen oder Infrastruktur-Komponenten zutreffen)
  2. Bestimmte (Gruppen von) geschaftskritischen Prozessen ("Vital Business Functions") sind betroffen und die voraussichtliche Zeit bis zur Wiederherstellung der vollstandigen Leistungsfahigkeit dieser Prozesse ist ubermaßig lang oder unbekannt (hier ist zu spezifizieren, welche geschaftskritischen Prozesse zutreffen)

Die Bereitstellung klarer Richtlinien zum Bestimmen von Major Incidents ist oft ein schwieriges Unterfangen, aber der [1st Level Support](http://wiki.de.it-processmaps.com/index.php/Rollen_in_ITIL) entwickelt zumeist einen "sechsten Sinn" fur diese. Im Zweifelsfall ist es auch besser, auf der sicheren Seite zu bleiben.

Ein _Major Incident_ ist durch seine großen Auswirkungen charakterisiert, insbesondere auch auf Kunden. Beispiele hierfur sind:

  * Die Netzwerkanbindung fallt aus und damit ist die Kommunikation des Unternehmens mit der Außenwelt unterbrochen.
  * Ein Web-Server fallt wegen unerwartet hoher Belastung aus, z.B. weil viele Kunden zugreifen, um Eintrittskarten zu einer Veranstaltung zu reservieren; dadurch wird es vielen Kunden unmoglich, Eintrittskarten zu erwerben.
  * Eine zentrale Datenbank stellt sich als korrupt heraus.
  * Mehrere fur das Geschaft wichtige Server sind von einem Virus befallen.
  * Vertrauliche Informationen zu einer großeren Zahl von Kunden sind in die Öffentlichkeit gelangt.

Daruber hinaus sind alle Katastrophenfalle (die von der [IT-Service-Continuity-Strategie](http://wiki.de.it-processmaps.com/index.php/IT_Service_Continuity_Management) und unterstutzenden [ITSCM-Planen](http://wiki.de.it-processmaps.com/index.php/IT_Service_Continuity_Management) behandelt werden) als Major Incidents zu bewerten. Zu beachten ist auch, dass unkritische Incidents durch Fehler oder zu lange Inaktivitat zu Major Incidents werden konnen.

#### Die wichtigsten Eigenschaften von Major Incidents

Die wichtigsten Eigenschaften, an denen sich Major Incidents erkennen lassen, sind unter anderem:

  * Eine signifikante Anzahl von Kunden bzw. von wichtigen Kundengruppen ist betroffen.
  * Die Kosten bzw. aus dem Incident resultierenden Verluste fur Kunden und/oder die Service-Organisation sind betrachtlich.
  * Die Reputation des Service-Providers wird wahrscheinlich beschadigt.

UND

  * Der Arbeits- und Zeitaufwand zur Losung des Incidents ist vermutlich groß und es ist sehr wahrscheinlich, dass bestehende Service-Level-Vereinbarungen verletzt werden.

Ein Major Incident ist in aller Regel auch mit der Prioritat "Kritisch" oder "Hoch" versehen.

## [ Infobox ]
