# Prototyping (Softwareentwicklung)

_Captured: 2015-10-23 at 00:47 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Prototyping_(Softwareentwicklung))_

Ein Prototyp steht fur ein lauffahiges Stuck Software oder eine anderweitige konkrete Modellierung (z. B. [Mock-up](https://de.m.wikipedia.org/wiki/Mock-up)) einer Teilkomponente des Zielsystems. Dieser Prototyp dient anschließend oft als Basis fur eine bessere Kommunikation mit den Kunden oder auch innerhalb des Entwicklungsteams uber konkrete Dinge (statt abstrakte Modelle).

Das [explorative](https://de.m.wikipedia.org/wiki/Explorativ) Prototyping wird zur Bestimmung der Anforderungen und zur Beurteilung bestimmter Problemlosungen verwendet und konzentriert sich dabei auf die [Funktionalitaten](https://de.m.wikipedia.org/wiki/Funktionalit%C3%A4t) des Systems.

    Erstes Ergebnis: Ein Programm mit den Grundfunktionalitaten
    Ziel: Anhand der Grundfunktionalitaten die Akzeptanz beim Nutzer und die Notwendigkeit erganzender Funktionen zu uberprufen

Beim evolutionaren Prototyping wird die Anwendung nach und nach erweitert. Dabei wird vor Allem das Feedback der zukunftigen Nutzer bzw. des Auftraggebers genutzt. Der Prototyp wird dabei stets lauffahig gehalten und bis zur [Produktreife](https://de.m.wikipedia.org/w/index.php?title=Produktreife&action=edit&redlink=1) weiterentwickelt.

    Erstes Ergebnis: ein erster experimenteller Prototyp
    Ziel: Sammeln von Erfahrungen mit dem Prototyp

Bei diesem Vorgehen wird zu Forschungszwecken bzw. zur Suche nach Moglichkeiten zur Realisierung ein experimenteller Prototyp entwickelt. An diesem wird anschließend eine sehr umfangreiche Problemanalyse und [Systemspezifikation](https://de.m.wikipedia.org/wiki/Systemspezifikation) durchgefuhrt. Die gewonnenen Erkenntnisse konnen anschließend in einem richtigen Produkt verwertet werden.

[Rapid Control Prototyping](https://de.m.wikipedia.org/wiki/Rapid_Control_Prototyping) bezeichnet die Softwareentwicklung von Regelungen und Steuerungen, mit Hilfe grafischer Tools. Diese ist nicht zu verwechseln mit dem aus dem Maschinenbau bekannten [Rapid Prototyping](https://de.m.wikipedia.org/wiki/Rapid_Prototyping)

    Erstes Ergebnis: Ein ausgewahlter Teil des Systems wird durch alle Ebenen hindurch implementiert.
    Ziel: Bestrebung explizit einen konkreten Teil eines Programms anzufertigen.

Hierbei wird ein ausgewahlter Teil umgesetzt. Dies eignet sich besonders fur Falle, in denen noch Funktionalitats- oder Implementierungsfragen ungeklart sind. Abgeschlossene Teile konnen dann bereits umgesetzt werden, bevor die Anforderungen fur den Rest komplett festgelegt wurden.

    Erstes Ergebnis: Eine ausgewahlte Ebene des Gesamtsystems wird fertiggestellt.
    Ziel: Eine funktionierende Ebene, die vorgestellt werden kann, oder an der sich andere Ebenen orientieren konnen.

In diesem Fall wird nur eine spezifische Ebene des Gesamtsystems realisiert, welche jedoch moglichst vollstandig abgebildet wird. (z. B. Realisierung der GUI (Oberflache) (ohne tiefer liegende Funktionalitaten), zur Vorlage fur den Auftraggeber.) Diese Methode hat den Vorteil, dass man dem Auftraggeber schon etwas zeigen kann, ohne das komplette System entwickelt zu haben. Dies setzt jedoch eine starke (sowieso sinnvolle) Trennung der einzelnen Komponenten voraus. Die Oberflache muss dementsprechend unabhangig von der dahinter liegenden Logik funktionieren oder wenn die Logik-Ebene umgesetzt wird, muss sie unabhangig von der Oberflache funktionieren.

  * Die Anforderungen der Anwender konnen laufend prazisiert und verifiziert werden. Damit sinkt das Risiko einer Fehlentwicklung.
  * Unbeabsichtigte [Wechselwirkungen](https://de.m.wikipedia.org/wiki/Interaktion) zwischen einzelnen Komponenten des Produkts konnen fruher erkannt werden.
  * Der Fertigstellungsgrad ist besser verifizierbar.
  * Die [Qualitatssicherung](https://de.m.wikipedia.org/wiki/Qualit%C3%A4tssicherung) kann fruhzeitig eingebunden werden.
  * Prototyping verfuhrt oft dazu, Anforderungen weder korrekt zu erheben noch sauber zu [dokumentieren](https://de.m.wikipedia.org/wiki/Dokumentation). Der Entwicklungsprozess kann sich dadurch erheblich verlangsamen.
  * Es entstehen wahrend der Entwicklung zusatzliche Kosten, weil der Prototyp nur als Basis fur die folgende eigentliche Entwicklung des Produktes dient. Diese Kosten und Zeitaufwand konnen durch weniger Nacharbeit am Endprodukt wieder ausgeglichen werden.

Ein klassisches Beispiel ist ein Oberflachenprototyp, der dem spateren Nutzer der Software einen ersten Eindruck der [Benutzeroberflache](https://de.m.wikipedia.org/wiki/Benutzeroberfl%C3%A4che) (meist [graphisch](https://de.m.wikipedia.org/wiki/Grafische_Benutzeroberfl%C3%A4che)) und des Programmablaufs vermittelt. Die inkrementelle Entwicklung eines Produkts in den Anfangsphasen kann fruhzeitig auf Probleme im Design aufmerksam machen und zusatzliche Kundenwunsche in die Anforderungen einfließen lassen. Im Bereich des Projektmanagement konnen die Ergebnisse dazu genutzt werden, ein Softwareprojekt hinsichtlich Aufwand und Kosten einzuschatzen.
