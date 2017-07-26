# Testgetriebene Entwicklung – Mehr als nur Qualitätssicherung

_Captured: 2017-04-06 at 20:04 from [blogs.itemis.com](https://blogs.itemis.com/de/testgetriebene-entwicklung-mehr-als-nur-qualit%C3%A4tssicherung?utm_source=hs_email&utm_medium=email&utm_content=50066132&_hsenc=p2ANqtz-_T7zJbCVpN13y-yc1rtzwFiv2cO-6SiJFBbSugELpwSSH9tt7a_Uuk-wUfPUDSorIZGPc3HYVFjf_Kfs0CAKwSKMBhWgzDvgPw5zXI9gXkhtLIe0Q&_hsmi=50065691)_

Testen gehort in der (agilen) Softwareentwicklung dazu - keine Frage: Das Projekt ist abgeschlossen und das Ergebnis wird getestet. Dieses klassische Testverfahren birgt jedoch oftmals Gefahren.

Getestet wird, aber in der Regel zu spat, zu selten und entsprechend zu zeit- und kostenintensiv - oder vollig planlos. Die Methode des **T**est **D**riven **D**evelopment (kurz TDD) oder testgetriebener Entwicklung will diesen klassischen Problemen entgegentreten.

**![Testgetriebene-Entwicklung-Dilbert](https://blogs.itemis.com/hs-fs/hubfs/Blog/Comics/dc_c110324.gif?t=1491488351797&width=362&name=dc_c110324.gif)**

> _DILBERT (C) (2011) Scott Adams. Used By permission of UNIVERSAL UCLICK. All rights reserved._

## **Testdriven Development als Vorgehensmodell**

TDD ist ein Vorgehensmodell fur die Programmierung. Ähnlich wie sich ein Sportler seinen Bewegungsablauf bewusst macht, um immer bessere Ergebnisse zu erzielen, hilft uns in der testgetriebenen Entwicklung ein expliziter Ablauf bei der kontinuierlichen Optimierung unserer Entwicklungsarbeit. Stets das bestmogliche Ergebnis zu erreichen, wird so nicht dem Zufall uberlassen, sondern ist die Konsequenz einer Methodik.

## **Stichwort: Test First!**

Das Thema der Fehlervermeidung ist in der testgetriebenen Entwicklung eine wesentliche Starke. Durch den Test First-Ansatz wird das klassische Testen umgedreht: Es wird nicht die fertige Implementierung am Ende des Projektes getestet - die testgetriebene Entwicklung ist im Gegenteil von Anfang an Bestandteil des Projektes. So wird nicht nur von Anfang an die Testbarkeit eines Systems sichergestellt, sondern auch eine vollstandige und automatisierte Überprufung aller Komponenten erreicht. Regressionsfehler konnen damit bereits zu einem fruhen Zeitpunkt erkannt und mit vergleichbar geringem Aufwand behoben werden.

## **Multitasking als Herausforderung**

Neben diesem offensichtlichen Vorteil gibt es aber noch einen anderen, wesentlichen Aspekt in der testgetriebenen Entwicklung, den wir an einem Beispiel verdeutlichen, das nicht mit Softwareentwicklung zu tun hat:

Wenn wir fur Freunde kochen, ist es immer eine große Herausforderung, alles zeitgleich fertig zu bekommen: Alle Speisen mussen gar und warm - aber hoffentlich nicht angebrannt - sein. Auch sollten wir eventuelle Sonderwunsche unserer Gaste berucksichtigt haben und beim Essen dafur sorgen, dass die Glaser nicht zu lange leer bleiben. Das alles erfordert Multitasking und hochste Aufmerksamkeit - und geht leider doch gelegentlich schief.

![Wistia video thumbnail](https://embedwistia-a.akamaihd.net/deliveries/20bdd202e2dcc469781adb679cde529f2ec7b25d.jpg?image_crop_resized=960x540)

Auch in der Softwareentwicklung mussen wir verschiedene Aspekten gleichzeitig im Auge behalten:

### **Die Spezifikation**

Zu Beginn unseres Softwareentwicklungsprojektes mussen wir das Ausgangsproblem genau benennen und definieren konnen: Welche Anforderungen mochten und mussen wir mit unserer Implementierung erfullen? Die Frage beinhaltet, dass wir uns uber Rand-, Vor- und Nachbedingungen ebenso Gedanken machen mussen wie um Grenzfalle.

### **Die Implementierung**

Das Problem ist definiert, nun mussen wir die richtige Losung finden. Dabei muss gewahrleistet werden, dass die bisherigen Tests weiterhin fehlerfrei durchlaufen werden.

### **Die Optimierung**

Der Code, also das Ergebnis unseres Projektes, soll nicht nur ein einmaliges Problem losen - er soll fur den dauerhaften Einsatz optimiert sein. Er sollte den entsprechenden Entwicklungsstandards folgen und wartbar sein. Andere Entwickler, die spater auf ihm aufsetzen mussen, sollten die Funktionsweise meines Codes verstehen und ihn ggf. leicht erweitern bzw. an ihn anknupfen konnen.

## **Multitasking durch Methodik**

Mehrere Dinge parallel optimal zu erledigen, ist auch in der Programmierung schwierig. In der testgetriebenen Entwicklung hilft uns der TDD-Zyklus dabei, die oben genannten Aspekte in getrennten Phasen anzugehen und unsere Aufmerksamkeit so genau einer Aufgabe widmen zu konnen - und am Ende unseres Projektes ein rundes Ergebnis zu erzielen.

Wir sehen, die Qualitatssicherung ist ein wichtiger Punkt beim Einsatz von TDD: Durch das kontinuierliche Testing von Anfang an, entsteht ein konstanter Arbeitsfluss, durch den wir regelmaßig einen lauffahigen Stand unserer Software vorliegen haben - und genau wissen, wo wir in der Entwicklung stehen, welche Meilensteine noch bewaltigt und welche Probleme noch gelost werden mussen. Die Qualitatssicherung findet also nicht halbherzig am Ende der Entwicklung statt, sondern wird im laufenden Prozess sichergestellt.

Doch TDD bietet noch mehr: Durch das von Anfang an testbare System und die so entstehende Moglichkeit, Fehler fruhzeitig zu erkennen und beheben zu konnen, werden Nachhaltigkeit und Kosteneffizienz in der Produktentwicklung gesichert. Als Entwickler konnen wir uns außerdem immer auf die aktuellen Themen fokussieren, ohne alle Nebenschauplatze im Auge haben zu mussen. Durch die testgetriebene Entwicklung wird also nicht nur das Ergebnis, sondern auch unsere eigene Entwicklungsarbeit optimiert.
