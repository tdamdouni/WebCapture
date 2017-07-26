# Wie schlechtes Design Unfälle provozieren kann und wie gute UX dagegen hilft

_Captured: 2017-05-19 at 10:03 from [t3n.de](http://t3n.de/news/user-experience-design-824133/)_

![    Wie schlechtes Design Unfälle provozieren kann und wie gute UX dagegen hilft
](http://img.t3n.sc/news/wp-content/uploads/2017/05/online-werbung-kosten-steigen-mobile-traffic.jpg?auto=compress%2Cformat&fit=crop&fm=jpg&h=347&ixlib=php-1.1.0&q=65&w=620&s=8709c816c508872fad2e3ba46cbcf99b)

> _ (Foto: [Shutterstock](https://www.shutterstock.com/image-photo/coworkers-team-brainstorming-process-modern-design-440063827)) _

## Wie schlechtes Design Unfalle provozieren kann

Am 14. August 2005 verungluckte Helios-Flug 522 und riss 121 Menschen mit in den Tod. Als Ursache wurde menschliches Versagen festgestellt: Die Piloten hatten trotz Warnung durch das System nicht auf den Luftdruckabfall in der Maschine reagiert. Eine nahere Untersuchung zeigte, dass derselbe Warnton, der den Luftdruckabfall anzeigte, auch verwendet wurde, um eine fehlerhafte Fahrwerkstellung anzuzeigen, die zwar unschon, aber nicht kritisch ist. Und sie zeigte, dass die Piloten deswegen den Warnton falsch deuteten und nicht ernst nahmen - bis es zu spat war. Ist dies ein Fall von menschlichem Versagen? Oder eher ein massiver Designfehler?

## Der Nutzen der Human-Factors-Forschung

Erkenntnisse aus Unfallanalysen wie der von Flug Helios 522 gibt es viele, und die Human-Factors-Forschung hat es sich zum Ziel gesetzt, alle denkbaren Arten von Fehlerquellen zu finden und zu minimieren. In sicherheitskritischen Bereichen wie der Luftfahrt oder der Kraftwerkssteuerung hat man damit in den letzten Jahren viel erreicht. In den meisten anderen Bereichen der Anwendungsentwicklung ist hier noch viel zu tun. Das Forschungsinteresse der Human-Factors-Forschung ist uberraschend breit angelegt: Welche Faktoren steuern das menschliche Verhalten und erzeugen oder verhindern Fehler im menschlichen Verhalten? Es hat sich gezeigt, dass man dafur in ganz verschiedene Aspekte menschlichen Lebens hinein blicken muss: Neben menschlichen Fehlern kommen Emotionen und die Art, Entscheidungen zu treffen, die Zusammenarbeit im Team (speziell wenn Hierarchien im Spiel sind) und Stress und Mudigkeit in den Fokus. Und wie beeinflusst diese Forschung nun den Bereich Anwendungsentwicklung?

Hier sind wir am Kern des User-Experience-Designs. Es zeigt sich, dass und warum User-Experience-Design weit uber reines Grafikdesign hinaus geht. User-Experience-Design wird heute nach wie vor haufig als reine Schonheitsoperation und Luxusthema angesehen. In sicherheitskritischen Bereichen kann User-Experience-Design jedoch ein außerst sicherheitsrelevantes Thema sein. Was gemeinhin unter „menschlichem Versagen" firmiert, kann vom Design(er) maßgeblich beeinflusst werden. In der Medizintechnik oder in der Anlagensteuerung konnen Menschenleben gerettet oder Umweltkatastrophen geschaffen bzw. verhindert werden, in „Alltagssoftware" kann es immerhin noch um Geld, Zeit und Nerven gehen. Menschen funktionieren anders als Computer, und sie sind beeinflussbar - auch durch Technik und ganz speziell auch durch visuelles und strukturelles Design. Ein Beispiel aus dem strukturellen Design soll zeigen, wo die Expertise des Designers zum Tragen kommt.

## Wie Hierarchie zum Sicherheitsrisiko wird

Ein Cockpit, besetzt mit einem erfahrenen Piloten mit langjahriger Erfahrung und einem jungen Piloten, frisch aus der Ausbildung. In welcher Konstellation fliegt man wohl sicherer: Wenn der alte Hase fliegt und der Junior den Copiloten gibt oder umgekehrt, also wenn der Junior fliegt und der Ältere Copilot ist?

Die Erfahrung zeigt, dass man in der zweiten Besatzung besser fliegt. Aus einem ganz einfachen Grund: Es ist fur den Senior einfacher, den Junior zu kontrollieren und gegebenenfalls zu korrigieren als fur den Junior. Es sind tatsachlich schon Flugzeuge gegen die Felswand geprallt, weil der Copilot lediglich beim Piloten nachfragte, ob er sich sicher sei, auf der richtigen Flughohe zu sein anstatt klar auszusprechen, dass das Flugzeug geradewegs auf eine Steilwand zuraste.

Ich hatte in meiner Berufspraxis einen ahnlichen Fall: Wir entwickelten eine Software zum Telemonitoring chronisch erkrankter Patienten. Als ich in das Projekt kam, sah alles ganz einfach aus: Der Arzt gibt die Therapie vor, die Pflegekraft fuhrt aus und nimmt die Befunde auf und der Arzt kontrolliert anhand der Befunde den Heilungsverlauf und passt gegebenenfalls die Therapievorgaben an. Die formalen Verantwortlichkeiten waren klar: Der Arzt hat die Verantwortung fur die Festlegung der Therapie und die Pflegekraft fur die Durchfuhrung.

  


Bei naherem Hinsehen stellte sich heraus, dass die Expertise fur die Behandlung dieser Art von Erkrankung ein Pflegethema war. Es gab Spezialausbildungen dafur, die zu 99 Prozent von Pflegekraften besucht wurden und nur zu einem Prozent von Ärzten. Die Pflegekrafte erzahlten von der Zwickmuhle, in die sie geraten konnten, wenn der Arzt Therapievorgaben machte, die aus Sicht der Pflege falsch waren: Sie waren dem Arzt gegenuber verantwortlich fur die korrekte Ausfuhrung der Therapievorgaben, und sie waren dem Patienten gegenuber verantwortlich fur eine gute und korrekte Behandlung.

Hier standen also die rechtlichen und formalen Vorgaben im Widerspruch zu den tatsachlich gelebten Verhaltnissen - was keine Seltenheit ist im gelebten Alltag, fur den wir User-Experience-Designer Software konzipieren.

Die Losung des Problems lag in der geschickten Umstrukturierung des Prozesses. Es ware ungunstig gewesen, den Pfleger als Kontrollinstanz des Arztes einzusetzen, denn dies hatte dem Statusgefuhl der Beteiligten widersprochen und ware potentiell demutigend aus Sicht des Arztes gewesen. Das neue Systemdesign sieht vor, dass die Pflegefachkraft die Therapie definiert und der Arzt als Kontrollinstanz fungiert. Auf diese Art hat der fachlich besser Qualifizierte die Initiative - und ihn zu korrigieren kostet Aufwand, den sich niemand gerne grundlos macht.

t3n ist Medienpartner der Developer Week 2017. Developer Week 2017: 26. bis 29. Juni 2017, NCC Ost, Messe Nurnberg. Informationen und Anmeldung [hier](http://www.developer-week.de). Weitere Beispiele, die zeigen, wie Erkenntnisse aus der Human-Factors-Forschung ganz pragmatisch in Designlosungen umgesetzt werden konnen, lernt ihr dort kennen. Wer mehr uber das Thema erfahren will, kann Monika Gillessen am Mittwoch, den 28.06.2016 von 10:30 bis 11:30 Uhr in Nurnberg live erleben.

**Ebenfalls spannend:**
