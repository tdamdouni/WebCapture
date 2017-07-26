# Dem Anwender über die Schulter geschaut

_Captured: 2015-12-11 at 10:10 from [www.tecchannel.de](http://www.tecchannel.de/it-strategie/3205341/dem_anwender_ueber_die_schulter_geschaut/?qle=rssfeed_)_

## End2End-Monitoring

End2End-Monitoring simuliert Prozesse aus Sicht des Anwenders. Es stellt dadurch sicher, dass Applikationen und Ablaufe wirklich funktionieren. Dieser Beitrag gibt einen Überblick fur Einsteiger.

Zu einem umfassenden Monitoring der IT-Infrastruktur gehort langst nicht mehr nur, dass ein System per Ping erreichbar ist oder das Mailrelay auf einen SMTP-Request wie erwartet antwortet. Ein umfassendes [Netzwerk](http://workshop.tecchannel.de/p/netzwerk,4181)\- und Systemmonitoring ist die Grundvoraussetzung zur Fehlersuche und fuhrt dazu, Probleme fruhzeitig zu erkennen und zu verhindern. Allerdings kann es einen wichtigen Aspekt nicht abbilden, namlich die Sicht des Anwenders.  
Hier setzt das End2End-Monitoring - nicht zu verwechseln beispielsweise mit einem SAP-Monitoring - an. Es simuliert Prozesse aus Sicht eines Endanwenders und stellt dadurch sicher, dass eine Applikation beziehungsweise ein Ablauf auch wirklich funktioniert.

In der Regel wird dazu ein typischer Mitarbeiterrechner (Robot) eingerichtet, der die Umgebung fur die End2End-Überwachung bereitstellt. Die Entwicklung eines Ablaufs erfolgt meist mit einer Scriptsprache wie AutoIT. Um sich einen schnellen Überblick verschaffen zu konnen, bietet es sich an, die Robots an verschiedenen Orten im Netzwerk aufzubauen und die Ergebnisse in einem zentralen Systemmanagement-Tool zusammenzufuhren und auszuwerten.

### Die Anwendersituation nachvollziehen

Eine immer funktionierende IT wird inzwischen von jedem Anwender als gegeben angesehen. Erschwert wird das immer mehr durch die zentrale Bereitstellung von Applikationen und Services, weil dadurch immer mehr Fehlerquellen auftreten konnen.

Es gibt viele Fehlerquellen, die dazu fuhren konnen, dass eine Applikation fur den Benutzer nicht zur Verfugung steht (sh. Abb. 1) . Zum einen ist das der SAP [Server](http://www.tecchannel.de/server/), der die Applikation als solche bereitstellt, zum anderen ist das die Infrastruktur, uber die der Benutzer auf die Applikation zugreift. Zu guter Letzt gibt es noch den Anwender-PC, uber den die Applikation aufgerufen wird.

Mit einem End2End-Monitoring werden die Applikationen aus dem Blickwinkel eines Endanwenders betrachtet. Stellt man durch das Monitoring fest, dass die Applikation reibungslos funktioniert, hat man zeitgleich auch eine Information daruber, dass der SAP Server funktionieren muss und auch die Netzwerkinfrastruktur. Das End2End-Monitoring stellt somit eine Korrelation von mehreren Komponenten dar.

Doch kann diese Art der Überwachung deutlich mehr. Da es sich um programmierte und simulierte Ablaufe handelt, kann an jedem einzelnen Punkt die Zeit gemessen werden. Dadurch ist es nicht nur moglich, zu uberprufen, ob eine Applikation zur Verfugung steht, sondern auch, in welcher Qualitat. Ein Beispiel hierfur ware ein Webshop, bei dem ein Kaufer naturgemaß lange Ladezeiten ungern in Kauf nimmt.

Die Beweggrunde, End2End-Monitoring einzurichten, sind daher meist der Wunsch, eine hohere Kundenzufriedenheit zu erreichen, oder Verfugbarkeiten und die Qualitat einer Applikation nachweisen zu konnen.

### Aufbau eines stabilen End2End-Monitorings

End2End-Monitoring wird oft nur als Aufzeichnung eines Ablaufs angesehen, der immer wieder abgespielt wird. Diese Sicht ist zwar grundsatzlich richtig, da ein Script genau das macht, aber auch nur solange, bis der Ablauf nicht mehr so ist, wie gewohnt. Recorder neigen dazu, Mausbewegungen und Klicks an entsprechenden Stellen aufzunehmen. Die Qualitat ist, wie man sich vorstellen kann, meist schlecht, da schon kleinere Verschiebungen dazu fuhren konnen, dass der gewohnte Ablauf nicht mehr funktioniert.

Um ein stabiles End2End Script zu programmieren, sollte man sich im Vorfeld folgende Fragen stellen:

  * Existieren Abweichungen im Ablauf, die keinen Fehler darstellen?
  * Wie kann die Applikation im Fehlerfall sauber beendet werden?

Je genauer der Ablauf beschrieben wird, desto hoher ist die Wahrscheinlichkeit, am Ende ein stabiles End2End-Monitoring zu haben.

  * ![](http://images.tecchannel.de/images/tecchannel/bdb/1876402/522x294.png)

> _Zehn Tipps, Ihre Applikationen zu verbessern_

  * ![](http://images.tecchannel.de/images/tecchannel/bdb/1880294/522x294.png)

  * Die Verwendung von Positionsangaben sollte vermieden werden
  * Pixelpunkte sollten als Indikatoren nicht verwendet werden
  * Die Nutzung von bereitgestellten Methoden ist empfehlenswert:
  * Lauft die Applikation zu lange, muss sie beendet werden:
  * Wenn nicht anders moglich, Prozesse beenden
  * Ausfuhrung auf mindestens zwei Robots und Korrelation der Ergebnisse, um die Wahrscheinlichkeit von Fehlalarmen zu minimieren
