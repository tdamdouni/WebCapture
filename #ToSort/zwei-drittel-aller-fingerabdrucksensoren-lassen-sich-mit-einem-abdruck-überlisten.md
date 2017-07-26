# Zwei Drittel aller Fingerabdrucksensoren lassen sich mit einem (1) Abdruck überlisten

_Captured: 2017-05-17 at 20:32 from [www.mobilegeeks.de](https://www.mobilegeeks.de/news/fingerabdrucksensor-sicherheit-generalschluessel/)_

![](https://c.mobilegeeks.de/wp-content/uploads/2017/05/Smartphone-Fingerabdruck-837x500.jpg)

Dass die Fingerabdrucksensoren auf [Smartphones](https://www.mobilegeeks.de/hub/smartphones/) nicht ganz so sicher sind, wie uns die Hersteller glauben machen wollen, hat sich bereits beim ersten iPhone mit diesem Feature herausgestellt. Der Chaos Computer Club erstellte [bereits 2013](https://www.mobilegeeks.de/chaos-computer-club-knackt-apple-iphone-5s-fingerabdrucksensor-touch-id-video/) mit einfachsten Mitteln eine Kopie des passenden Fingerabdrucks und konnte das Gerat damit entsperren.

Die Technik hat sich seitdem zwar verbessert, die Methoden sie zu knacken aber wiederum auch. Das ewige Katz- und Maus-Spiel zwischen [Team Blau und Team Rot](https://danielmiessler.com/study/red-blue-purple-teams/) eben. Jetzt ist es einem Sicherheitsteam in den USA gelungen, eine Art Generalschlussel zu erstellen, mit dem sich 65% aller Smartphones mehr oder weniger problemlos entsperren lassen. Und zwar nicht mit Mitteln der analogen, sondern der digitalen Welt - via Machine Learning und einer Kunstlichen Intelligenz.

## 800 Fingerabdrucke als Vorlage reichen

Die Forscher nahmen dazu einen Datensatz aus rund 800 Fingerabdrucken, die mit uberdurchschnittlich vielen anderen Fingerabdrucken hohe Übereinstimmungen aufweisen. Man kann sich dieses Schema wie Schlussel mit einer bestimmten Passform vorstellen, die sich - jeder fur sich - in die entsprechenden Zylinder stecken lassen, ohne jedoch - wiederum jeder fur sich - das Schloß offnen zu konnen.

Nun erstellten sie aus dem Datensatz insgesamt 8.200 Teilabdrucke, die wiederum gegeneinander abgeglichen wurden. Sprich: es wurden alle moglichen Varianten von ganzen Fingerabdrucken erstellt, die mit der Kombination der Teilabdrucke moglich sind.

Aus diesem Pool nahmen die Forscher nun die Abdrucke, die mit vier Prozent aller anderen Abdrucke in der Datenbank ubereinstimmten, also bereits jetzt eines von 25 testweise vorliegenden Smartphones entsperren konnten (statistisch hinkt der Vergleich ein wenig, da nicht jeder Mensch der Welt ein Smartphone mit Fingerabdrucksensor hat).

Diese rund 1.200 kunstlich erzeugten Abdrucke waren im nachsten Schritt die Datenbasis fur eine Kunstliche Intelligenz, welche die Vorlagen willkurlich minimal veranderte. Stimmte eine Änderung mit mehr Musterabdrucken uberein als die unveranderte Variante, wurde die neue Version beibehalten. Quasi so, als wenn man sich beim Puzzlen bei Passform und Große immer mehr dem passenden Puzzleteil nahert oder als wenn man solange an einem Musterschlussel rumfeilt, bis er irgendwann das Schloss offnet.

Nach einiger Rodelei erstellte der Algorithmus dann quasi einen General-Fingerabdruck, einen Masterkey. Dieser konnte zwei von drei Smartphones entsperren, obwohl es sich nicht um den Abdruck des Eigentumers handelte. Das funktionierte zwar nur im bestmoglichsten Fall, abhangig von den zuvor bereitgestellten Erstabdrucken. Es beweist aber, dass die Methode funktionieren kann, ohne jemals den echten Fingerabdruck als Referenz nehmen zu mussen. Fur einen potentiellen Angreifer entfallt damit die Muhe, sich den Original-Fingerabdruck auf irgendeine Weise besorgen zu mussen.

Dem Forscherteam zufolge liegt das Problem der Scanner darin, dass die verbauten Sensoren zu klein sind, um einen gesamten Abdruck auf einmal zu prufen. Vielmehr wurde die Übereinstimmung eines Teilabdrucks mit einem einzigen weiteren Teilabdruck reichen, um das Smartphone zu entsperren. Im Schnitt speichern die Gerate insgesamt etwa zehn Teilabdrucke.

Weiterlesen:  
[iPhone-Display kann Fingerabdrucke erkennen](https://www.mobilegeeks.de/news/neues-patent-von-apple-dieses-display-kann-fingerabdruecke-erkennen/)

Wer sich fur die Details des Projekts interessiert, kann sich das entsprechende [Paper auf IEEE.org](http://ieeexplore.ieee.org/document/7893784/) herunterladen. Das Team schlagt vor, Scanner zu entwickeln, die auch Rillen und Hohenunterschiede von Fingerabdrucken scannen. Einige Smartphones machen das bereits in Ansatzen - in Zukunft werden hoffentlich noch weitere Hersteller diesen Ratschlag befolgen..
