# Human Resource Machine – Lösung aller Level

_Captured: 2018-08-25 at 15:35 from [www.check-app.de](https://www.check-app.de/2016/07/22/human-resource-machine-loesung-aller-level/)_

_Input zu Output. Was ist daran schon so schwierig? Vor etwa drei Wochen hatte ich euch die Human Resource Machine vorgestellt und bis heute habe ich an einer Losung der Level getuftelt. Doch hier ist sie nun. Falls ihr also in einer der Raume feststeckt oder die perfekte Routine sucht, dann wird euch hier geholfen. Weiterhin ist das Spiel mobil nur auf iOS erhaltlich. Da jedoch die Losungen auf Steam fur PC ahnlich scheinen, gehe ich davon aus, dass die Human Resource Machine Losung hier dann auch fur Android gelten werden, sobald es bei Google Play erscheint. Schauen wir mal. Schreibt mir einen Kommentar, wenn ihr mit irgendeiner Level-Walkthrough nicht klar kommen solltet. Ich oder andere Leser von Check-App versuchen euch dann zu helfen._

Ihr spielt die Human Resource Machine noch nicht? Den Kauf der Ratsel-App kann ich euch nur empfehlen, wenn ihr ein Faible fur logische Ratsel habt, wie man sie in der Programmierung (Coding) antrifft. Das hort sich stark nach Informatik-Unterricht an, ist aber mega spaßig verpackt, wie ihr euch [hier in meinem Review der App](https://www.check-app.de/2016/07/01/rede-zur-personalversammlung-der-tomorrow-corporation-es-gilt-das-geschriebene-wort/) uberzeugen konnt.

![Human_Resource_Machine_App](https://www.check-app.de/wp-content/uploads/2016/06/Human_Resource_Machine_App.jpg)

## Hinweise zur Losung

Selber denken macht klug. Bitte nutzt die Losung nur dann, wenn ihr wirklich nicht weiterkommt!

Die Losungen funktionieren alle, jedoch sind nicht alle fur die beiden Kriterien optimal. Wer beide der grunen Punkte mochte, muss richtig gut sein. Also was Großenoptimierung und Laufzeitoptimierung angeht, kann hier und da noch was erganzt werden. Manchmal brauche ich mehr Befehle und Schritte, da ich einfach nur weiterkommen wollte.

Die Level sind alle recht seltsam benannt. Anfang heißen sie noch wie Raume, spater werden sie recht beschreibend. Die Namen sagen meist schon aus, was es zu losen gibt: Dateiordnung, Die kleine Zahl oder etwa Multiplikationsworkshop. Neben dem linearen Strang hin zum Programmende gibt es außerdem drei Weichen mit Zusatzlevels. Aber fangen wir mal bei der Poststelle an. Achja, die Level sind in der Human Resource Machine nicht so offensichtlich durchnummeriert, ich mache es zur Übersichtlichkeit mal trotzdem fur die Losung hier und halte mich an die jeweils angegebenen Jahre in der "In- und Outbox-Verwaltung".

## Human Resource Machine Losung Level/Jahr 1 bis 10

Nachfolgend die ersten 10 Jahre als Losung, bei hoheren Levels fuge ich euch dann immer ein Screenshot hinzu. Okay, in Wirklichkeit sind es nur 9 Jahre, da wir im Jahr 5 ne Pause einlegen durfen. Das ist ein Arbeitsleben.

### Losung Level / Jahr 1 - Poststelle:

Willkommen an Ihrem ersten Tag! Bist du ein ausgezeichneter Befehlsbefolger? Dann ziehe einfach den Befehl Inbox auf Zeile 1 und Outbox auf Zeile 2. Das war zu einfach? Klar ordne dreifach hinterander diese beiden Befehle an: inbox-outbox, inbox-outbox, inbox-outbox. Nicht besonders effizient diese sechs Zeilen, aber effektiv.

### Losung Level / Jahr 2 - Belebte Poststelle:

Ja, nun lost ihr die gleiche Aufgabe mit nur drei Befehlen. Alle Objekte von links nach rechts mit: Inbox - Outbox - Jump, mit Pfeil ber Zeile 01.

### Jahr 3, die Kopieretage:

Das Fließband ist ausgefallen. In der Mitte des Raums sind sechs Speicherplatze mit Buchstaben. Wir sollen das Wort "BUG" in die Outbox legen. Die Befehlskette lautet:

copyfrom 4  
outbox  
copyfrom 0  
outbox  
copyfrom 3  
outbox

Fertig. Weiter zum Aufzug.

### Verwirrungsverwalter, Jahr 4:

Der Angestellte, also du, soll zwei Dinge in umgekehrter Reihenfolge zur Outbox befordern. Wir benotigen alle funf Befehle und werden neun Zeilen Code generieren. Ab diesem Level werde ich euch die Losungen der Human Resource Machine sogleich als Bild mitliefern, sodass ihr genau die Zeilennummern seht.

inbox  
copyto 0  
inbox  
copyto 2  
copyfrom 2  
outbox  
copyfrom 0  
outbox  
jump in Zeile 0

![HumanM_Level_4_Verwirrungsverwalter](https://www.check-app.de/wp-content/uploads/2016/08/HumanM_Level_4_Verwirrungsverwalter.jpg)

"Ihre Anwesenheit wird auf der nachsten Etage verlangt" sagt dir rothaarige Brunette (lol) mit den verruckten Augen.

-Kaffeepause Jahr 5-

### Verregneter Sommer:

Draußen schuttet es, die arbeiten wir lieber im Jahr 6. In ebensovielen Zeilen, also 6, werden wir eine einfache Addition zweier Ziffern aus der Inbox durchfuhren und das immer wiederholen bis keine mehr da sind:

inbox  
copyto 0  
inbox  
add 0  
outbox  
jump in Zeile 0

![Human_Resource_Machine_Loesung_Level_6_Verregnerter_Sommer](https://www.check-app.de/wp-content/uploads/2016/08/Human_Resource_Machine_Loesung_Level_6_Verregnerter_Sommer.jpg)

### Human Resource Machine Losung, Nullenvernichter (Jahr 7):

Verflixt, das 7. Alle Zahlen außer die Nullen sollen in die Outbox. Das geht recht simpel mit sechs Befehlen. Da drei Jump dabei sind, u.a. auch der neue Zero, sieht das auf den ersten Blick recht verwirrend aus. Ist aber wirklich recht einfach, jedoch habe ich nicht die optimale Losung mit vier Befehlen und maximal 23 Schritten.

![Human_Resource_Machine_Loesung__Level_7_Nullenvernichter](https://www.check-app.de/wp-content/uploads/2016/08/Human_Resource_Machine_Loesung__Level_7_Nullenvernichter.jpg)

### Verdreifacherraum, Human Resource Machine (Jahr 8):

Harsch werden wir begrußt. Wir seien zu spat, sieben Jahre. Und eine Leistungssteigerung werde erwartet. Herje. Wir sollen jedes Objekt der Inbox verdreifacht in die Outbox legen. Multiplikation also.

inbox  
copyto 0  
add 0  
add 0  
outbox  
jump fur die Schleife auf Zeile 0

![Human_Resource_Machine_Loesung__Level_8_Verdreifacherraum](https://www.check-app.de/wp-content/uploads/2016/08/Human_Resource_Machine_Loesung__Level_8_Verdreifacherraum.jpg)

Das ist die optimale Losung in sechs Befehlen und 24 Schritten.

### Nullerhaltungsinitiative, Jahr 9 Losung:

Nur Nullen sollen in die Outbox diesmal. Also die umgekehrte Zielstellung zu Level 7. Entsprechend habe ich auch hier nicht die optimale Losung. Hiermit werden 6 Befehle und 32 Schritte benotigt. Ziel ins 5 und 25.

![Human_Resource_Machine_Loesung__Level_9_Nullerhaltungsinitiative](https://www.check-app.de/wp-content/uploads/2016/08/Human_Resource_Machine_Loesung__Level_9_Nullerhaltungsinitiative.jpg)

Update: Danke an den Kommentator - lasst mal das copyto 0 in Zeile 03 weg. Damit sind wir optimal.

### Jahr 10, der Verachtfacherraum:

Wie der Name sagt, sollen alle Objekte der Inbox mit 8 multipliziert in die Outbox wandern.

inbox  
copyto 0  
add 0  
copyto 1  
add 1  
copyto 2  
add 2  
outbox  
jump zu Zeile 0

Das sind neun Befehle mit 36 Schritten. Optimierung erreicht.

![Human_Resource_Machine_Loesung__Level_10_Verachtfacherraum](https://www.check-app.de/wp-content/uploads/2016/08/Human_Resource_Machine_Loesung__Level_10_Verachtfacherraum.jpg)

### Jahr 11, Subgang

Als in diesem Level sollen wir substrahieren. Die Beschreibung liest sich erst etwas verwirrend, was soll von wem abgezogen werden? Also meine Losung ist wieder nicht optimal, aber sie geht. Und so sieht sie aus:  
inbox  
copyto 1  
inbox  
copyto 2  
copyfrom 2  
sub 1  
outbox  
copyfrom 1  
sub 2  
outbox  
jump zu Zeile 0 fur Schleife

Die Großenoptimierung ergibt 11 Befehle (10 ware optimal) und 44 in der Laufzeitoptimierung, wo vier weniger gesucht sind. Naja, wir sind ja nicht bei den Barfaktionisten. Weiter gehts.

### Jahr 12, Vervierzigfacher

14 Befehle und 56 Schritte sind bei dieser Human Resource Machine Losung furs Optimum gesucht. Alle Zahlen sollen vervierzigfacht werden.

inbox  
copyto 0  
add 0  
add 0  
add 0  
add 0  
copyto 1  
add 1  
add 1  
add 1  
copyto 2  
add 2  
outbox  
jump zu Zeile 0 fur Schleife

![](https://www.check-app.de/wp-content/uploads/2016/07/Human_Ressource_Machine_Jahr_12_Vervierzigfacher.jpg)

### Jahr 13, Ausgleichsraum

Das Levelziel lautet diesmal, dass man nur von zwei gleichen Paaren eins in die Outbox werfen darf.  
inbox  
copyto 0  
inbox  
copyto 1  
copyform 0  
sub 1  
jump if zero in ubernachste Zeile  
jump nach oben vor Zeile 1  
copyfrom 0  
outbox  
jump ganz nach oben

Diese Losung von Human Ressoure Machine hat zwar nur wie gefordert 9 Befehle, wir laufen aber einen verdammten Schritt zuviel. Why?

### Jahr 14, Maximierungsraum

Plananderung! Es sollen nur große Zahlen in die Outbox. Nichts leichter als das:

inbox  
copyto 0  
inbox  
coppy 1  
sub 0  
jump if negative in zeile zwischen 9 und 10  
copyfrom 1  
outbox  
jump nach oben vor Zeile 1  
copyfrom 0  
outbox  
jump ganz nach oben

12 Befehle und 36 Schritte leider nicht optimal.

- Jahr 15 ist Pause / Einschub zur Arbeitsmoral-

### Jahr 16, Absolut Positiv

Eine positive Einstellung erhohe also die Produktivitat. Ist ja interessant. So ein Quatsch! Jedenfalls sollen negative Zahlen in positive gewandelt werden, bevor sie in die Outbox gelangen.

inbox  
jump if negative zu Zeile zwischen 4 und 5  
outbox  
jump uber inbox  
copyto 0  
sub 0  
sub 0  
outbox  
jump ganz nach oben

Neun Befehle anstat acht, jedoch genau 36 Schritte habe ich zu bieten. Tata.

![](https://www.check-app.de/wp-content/uploads/2016/07/Human_Ressource_Machine_Jahr_16_Absolut_Positiv.jpg)

### Jahr 17 - 33 als Video

Auf YouTube habe ich zwei Videos gefunden. Zwar sind diese Englisch, aber die Befehle sind gleich. Schaut mal rein.

Wenn ihr Fragen habt zu einer dieser Losungen, dann schreibt nen Kommi!
