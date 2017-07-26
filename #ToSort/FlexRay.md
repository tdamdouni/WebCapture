# FlexRay

_Captured: 2015-10-12 at 13:40 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/FlexRay)_

![](http://upload.wikimedia.org/wikipedia/de/thumb/2/2c/FlexRay_Logo.svg/220px-FlexRay_Logo.svg.png)

> _FlexRay-Logo_

FlexRay sollte die erhohten Anforderungen zukunftiger Vernetzung im Fahrzeug erfullen, die durch den [CAN-Bus](https://de.m.wikipedia.org/wiki/CAN-Bus) nicht befriedigt werden konnen, insbesondere eine hohere [Datenubertragungsrate](https://de.m.wikipedia.org/wiki/Daten%C3%BCbertragungsrate), [Echtzeit](https://de.m.wikipedia.org/wiki/Echtzeit)-Fahigkeit und [Ausfallsicherheit](https://de.m.wikipedia.org/wiki/Ausfallsicherheit) (fur _[X-by-Wire](https://de.m.wikipedia.org/wiki/X-by-Wire)_-Systeme). Im aktuellen Fokus steht jedoch vorrangig die hohere Datenrate, welche durch den kontinuierlichen Anstieg von Fahrerassistenzsystemen im Bereich Antrieb und Fahrwerk in Premiumfahrzeugen heute notwendig ist. FlexRay definiert die Layer 1 (physikalische Schicht) und 2 (Datensicherungsschicht) im [ISO/OSI-Referenzmodell](https://de.m.wikipedia.org/wiki/ISO/OSI-Referenzmodell). Der Serieneinsatz im Automobil erfolgte erstmals 2006 im [BMW X5](https://de.m.wikipedia.org/wiki/BMW_E70). Der FlexRay-Cluster in diesem Fahrzeug basiert auf der Protokollversion v2.0, der Physical Layer Spezifikation v2.1 Revision A.

Um auch die Anforderungen aktiver Sicherheitssysteme zu erfullen, wurde FlexRay vor allem in Bezug auf zeitlichen [Determinismus](https://de.m.wikipedia.org/wiki/Determinismus) und [Fehlertoleranz](https://de.m.wikipedia.org/wiki/Fehlertoleranz) weiter entwickelt. Ein [Bus Guardian](https://de.m.wikipedia.org/w/index.php?title=Bus-Guardian&action=edit&redlink=1) sollte eine zentrale bzw. dezentrale Überwachung der Buszugriffe auf Basis des statisch festgelegten [TDMA-Schemas](https://de.m.wikipedia.org/wiki/Time_Division_Multiple_Access) ermoglichen, kommt aber praktisch nicht zum Einsatz. FlexRay bietet zusatzlich zu [ByteFlight](https://de.m.wikipedia.org/wiki/ByteFlight) eine Nachrichtenkommunikation mit einem festgelegten TDMA-Schema. Dabei setzt FlexRay ahnliche Mechanismen ein, wie das an der [Technischen Universitat Wien](https://de.m.wikipedia.org/wiki/Technische_Universit%C3%A4t_Wien) entwickelte [Time-Triggered Protocol](https://de.m.wikipedia.org/wiki/Time-Triggered_Protocol) TTP. Zusatzlich zum TDMA-Schema bietet das von ByteFlight ubernommene Minislotting-Protokoll einen kollisionsfreien, priorisierten, dynamischen Kommunikationskanal.

Um einen Knoten, z. B. ein [Steuergerat](https://de.m.wikipedia.org/wiki/Steuerger%C3%A4t), an einem FlexRay-Bus zu betreiben, braucht man zwei Komponenten: den _Bus Transceiver_ und den _Communication Controller_. Der Bus Transceiver stellt die direkte Verbindung zur Datenleitung her: Einerseits schreibt er die logische Information, die versendet werden soll, in Form von Spannungspulsen auf den Bus; andererseits liest er die Signale aus, die von anderen Teilnehmern auf dem Bus gesendet werden. Diese Ebene wird als physikalische Bitubertragungsschicht oder _Physical Layer_ bezeichnet. Außerdem umfasst FlexRay noch das Busprotokoll. Das Busprotokoll regelt, wie ein Netzwerk startet, wie eine _global Clock_ etabliert wird und welche Steuergerate zu welchem Zeitpunkt senden durfen. Der Communication Controller setzt das Busprotokoll in jedem Steuergerat um, beispielsweise verpackt er die zu ubertragenden Informationen in ein Datenpaket und ubergibt dieses Datenpaket zum richtigen Zeitpunkt zur Übertragung an den Bus Transceiver.

FlexRay unterstutzt:

  * Bitraten bis 10 Mbit/s je Kanal
  * dezentrale Uhrensynchronisation
  * Zweikanaligkeit im Protokoll
  * zentrale & dezentrale Zugriffskontrolle
  * Stern-, Bustopologie sowie Topologien mit Bussen an den Sternarmen
![](http://upload.wikimedia.org/wikipedia/commons/thumb/9/92/Flexray.svg/440px-Flexray.svg.png)

> _TDMA (Time Division Multiple Access) nach FlexRay-Version 2.1_

Die Kommunikation auf dem Bus lauft in Zyklen ab. Jeder dieser Zyklen ist in verschiedene Segmente unterteilt:

  * Im statischen Segment hat jedes [Steuergerat](https://de.m.wikipedia.org/wiki/Steuerger%C3%A4t) seinen bestimmten Slot (Zeitfenster), in dem es Nachrichten senden kann. Es darf dabei die zeitliche Lange seines Slots nicht uberschreiten. Ist die Nachricht zu lang, muss der nachste Zyklus oder das dynamische Segment genutzt werden, um die Nachricht fortzusetzen.

    Dies ist der deterministische Teil des Protokolls, mit dem sichergestellt werden kann, dass wichtige Nachrichten (z. B. Lenkung, Bremse) innerhalb einer bekannten Zeit ubertragen werden.

  * Das dynamische Segment kann von einem Steuergerat benutzt werden, wenn es langere oder zusatzliche Nachrichten senden mochte, und beispielsweise die Breite seines statischen Slots nicht ausreicht oder fur wichtigere Nachrichten benotigt wird. 
    * Wenn ein Steuergerat keine Nachricht absetzen mochte, lauft sein Zeitfenster (Minislot) einfach ab (Mini 1 bis Mini 3).
    * Will das Steuergerat beispielsweise in Minislot 4 eine langere Nachricht senden, so verschiebt sich der Zeitpunkt, an dem das nachste Steuergerat senden kann, nach hinten. Im ungunstigsten Fall ist der dynamische Minislot 4 so lang, dass in diesem Zyklus kein weiteres Steuergerat mehr senden kann.
    * Weil fur Steuergerate, die im dynamischen Slot am hinteren Ende der Reihenfolge stehen, die Wahrscheinlichkeit am großten ist, dass sie mit einer Nachricht in diesem Slot warten mussten (oder gar herausfallen wurden), sollte die Anzahl der dynamischen Slots k > n sein (n ist die Anzahl der Steuergerate, die auf dem Bus kommunizieren und dazu einen Slot haben).

    Dieser Teil entspricht von seiner Übertragungsstruktur eher dem CAN-Bus.

  * Das Symbolfenster (symbol) war fur den Test des Buszugriffs vorgesehen und wird voraussichtlich nicht mehr zum Einsatz kommen.
  * NIT (Network Idle Time) soll den am Bus hangenden Steuergeraten ermoglichen, sich wieder mit dem Bus exakt zu synchronisieren.

Die Synchronisation bewirkt, dass alle Steuergerate am Bus nach dem gleichen Takt Nachrichten senden und nicht durch zeitliche Verschiebungen im Minislot (Zeitfenster) eines fremden Steuergerates senden. Der Zeittakt wird von den Steuergeraten nach bestimmten Regeln beim Aufwachen ausgehandelt. Es ist daher kein Master notwendig, der den Takt vorgibt und bei seinem Ausfall den Bus lahmlegen konnte.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/1/19/FlexRay_Frame.svg/440px-FlexRay_Frame.svg.png)

> _Der FlexRay-Rahmen_

Der FlexRay-Rahmen (engl. Frame) ist wie in nebenstehender Abbildung dargestellt aufgebaut.

Um Leitungsreflektionen zu verhindern, wird die Leitung mit ihrem [Leitungswellenwiderstand](https://de.m.wikipedia.org/wiki/Leitungswellenwiderstand) im Bereich von 80 Ω bis 110 Ω abgeschlossen. Die Leitungen werden verdrillt. Die maximale Leitungslange hangt von der Datenrate und der Anzahl, Lange und Position der Stichleitungen ab. BMW und andere OEMs setzen spezielle TP-Leitungen mit PE-Isolation ein, da PE als Isolierwerkstoff gegenuber PVC erhebliche Vorteile bei der temperaturbedingten Toleranz hat, folglich die Anforderungen an die Impedanz erfullt werden konnen. Fur Laboraufbauten eignen sich Ethernet-Kabel, sowohl Standardvarianten (CAT5, etc.) wie auch [Profinet](https://de.m.wikipedia.org/wiki/Profinet)-Kabel, letztere gibt es in robusten Ausfuhrungen und eignen sich auch fur Verkabelungen im Fahrzeug.

Die Signale werden durch Spannungspegel von 1,5 V und 3,5 V ubertragen, je nach Lage dieser Spannungspegel auf den Leitungen wird eine 0 oder 1 ubertragen. Haben beide Leitungen den Pegel 2,5 V, ist der Bus im Leerlauf (Idle). Zur Energieeinsparung kann auch der Pegel 0 V fur beide Leitungen verwendet werden.
