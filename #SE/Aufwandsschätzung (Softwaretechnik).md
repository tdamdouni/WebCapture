# Aufwandsschätzung (Softwaretechnik)

_Captured: 2015-10-23 at 15:51 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/Aufwandssch%C3%A4tzung_(Softwaretechnik))_

Im Bereich der Softwareentwicklung sind die Hauptkosten die _Personalkosten_; die Schatzung bezieht sich daher hauptsachlich darauf.

Daneben gibt es noch _Sachkosten_ (soweit nicht in den Personalkosten enthalten) wie z. B.

  * benotigte Computer,
  * Rechenzeiten und Netzwerkkosten,
  * Lizenzen fur Betriebssysteme und Tools,
  * Testhardware,
  * Kurse,
  * Reisekosten.

Diese hangen oft von den _Personalkosten_ ab, denn je langer ein Projekt dauert, je mehr Leute damit beschaftigt sind, desto mehr Sachkosten fallen auch an.

Fur die zu erwartenden Gesamtkosten sind darauf noch erhebliche _kaufmannische Aufschlage_ erforderlich, so fur

  * Realisierungsrisiko (ein Großteil der IT-Projekte wird abgebrochen, ist nicht machbar etc.)
  * Sicherheitsaufschlag fur Fehleinschatzung (Eisberg-Faktor)
  * Vorfinanzierungskosten
  * Inflation, Personalkostensteigerung (bei langer laufenden Projekten)
  * Wechselkursrisiken (bei Auslandsprojekten)

Die [Schatzmethode](https://de.m.wikipedia.org/wiki/Sch%C3%A4tzmethode) ist abhangig von der Große des Aufgabenumfangs (also Schatzung vor der Schatzung).

Fur die Schatzung kleinerer Aktivitaten, z. B. Arbeitspakete in einem laufenden Projekt oder Änderungen in einem bestehenden System wird meistens die [Schatzklausur](https://de.m.wikipedia.org/w/index.php?title=Sch%C3%A4tzklausur&action=edit&redlink=1) oder [Delphi-Methode](https://de.m.wikipedia.org/wiki/Delphi-Methode) benutzt, weil hier das Augenmaß der Beteiligten die beste und kostengunstigste Schatzung liefert.

Fur die Schatzung sehr großer Projekte wird meist der Vergleich mit anderen sehr großen Projekten benutzt, mit Auf- und Abschlagen werden dann die Kosten fur das aktuelle grob geschatzt. Durch Herunterbrechen auf einzelne Teilaufgaben wird dann der große Topf verteilt. Fur diese Teilaufgaben werden dann Schatzungen erstellt. Diese konnen dann wieder zusammengerechnet werden.

Die Grundstruktur fur die Schatzung des Personalaufwandes eines mittelgroßen Projektes ist:
    
    
       Menge * Preis * Kompetenzfaktoren
    

Dies kann sowohl fur einzelne Teile oder Phasen gemacht werden und die Kosten dann addiert werden, oder fur das Gesamtprojekt.

Gebrauchliche [Großenmaße](https://de.m.wikipedia.org/w/index.php?title=Gr%C3%B6%C3%9Fenma%C3%9F&action=edit&redlink=1) fur Programme sind [Lines of Code](https://de.m.wikipedia.org/wiki/Lines_of_Code) (LOC), Function Points (FP), DSI (Delivered Source Code Instructions), Dokumentseiten.

Nach [Watts Humphrey](https://de.m.wikipedia.org/wiki/Watts_Humphrey) (Autor von _The Personal Software Process_) sind die meisten Menschen nicht sehr gut darin, den Zeitaufwand direkt zu schatzen. Stattdessen kann man aber erstaunlich genau die Große des Programmcodes vorhersagen. Aus den Großen der geplanten Softwarebausteine, Korrekturfaktoren fur diverse Einflussgroßen und Erfahrungsdaten wird dann der zu erwartende Zeitaufwand ermittelt. Das Schatzverfahren [COCOMO](https://de.m.wikipedia.org/wiki/Cocomo) berucksichtigt besonders viele Einflussfaktoren.

LOC wird haufig kritisiert, da der Wert schon durch eine unterschiedliche Codeformatierung beeinflusst wird (bis zum Faktor 3). Das LOC-Großenmaß stuft lange Programme als aufwandiger ein als kurze Losungen. Die Lange eines Programms muss aber nicht zwangslaufig eine schlechtere Losung bedeuten. Gut geschriebener, selbsterklarender Code muss nicht kurz sein, da er aufgrund seiner Lesbarkeit in der Regel wartbarer ist als ein auf Textkurze optimierter Programmcode.

Ferner benotigen unterschiedliche Entwickler fur die gleiche Funktionalitat unterschiedlich viele Programmzeilen. In der Praxis gibt es dramatische Produktivitatsunterschiede bei Entwicklern. Sogenannte „Superprogrammierer" konnen 10- bis 100-fach mehr LOC pro Tag erzeugen als der Durchschnitt. Es gibt Projekte, bei denen kaum eine Zeile Code geschrieben wird, sondern z.B. nur interaktive Eingaben in ein vorhandenes System erfolgen (z. B. Datenbank-Tuning). Bei Projekten, bei denen die Codierung des Quellcodes nur 7 % des Gesamtaufwands ausmacht, ist LOC kein geeignetes Maß. LOC als Schatzgrundlage muss heute eher als historisch angesehen werden.

Trotz aller Kritik ist das LOC-Großenmaß noch weit verbreitet, wahrscheinlich deshalb, weil es intuitiv und leicht zu messen ist. Insbesondere im Nachhinein werden mitunter LOC (wozu dann auch Scripts und Test-Code zahlen) als Maß fur den Umfang einer Software und als Maß fur die Leistung der Entwickler herangezogen. Davor ist zu warnen: Wer LOC als Maß fur Leistung nimmt, wird viele davon bekommen, mit allen negativen Auswirkungen auf Einfachheit, Wartbarkeit, Performance, Zuverlassigkeit.

Statt LOC wurden spater oft auch DSI (delivered source instructions) genommen. Das scheint vernunftiger, aber die prinzipiellen Probleme bleiben. Kommentare, die erheblich zu Qualitat beitragen, zahlen nicht mit.

Die Function-Point-Methode (nach Allen J. Albrecht, IBM) geht nicht vom zu erwartenden Code aus, sondern von den Anforderungen und versucht, die Anzahl und Komplexitat von Datenstrukturen und Funktionen/Methoden zu schatzen, indem diese als einfach/normal/schwierig klassifiziert und mit entsprechenden Aufwandsfaktoren versehen werden. Diese Mengenfaktoren werden dann fur Erschwernisse korrigiert. Die Function-Point-Methode ist im kommerziellen Umfeld weit verbreitet. Es wurde versucht, sie an andere Umfelder anzupassen.

In Fallen, wo das Hauptergebnis in Textdokumenten besteht wird auch haufig die zu erwartenden Seiten Papier als Maß benutzt und mit 1PT/Seite bewertet. (Z. B. Studien, Analysen, Pflichtenhefte)

In anderen Fallen (z. B. Pflichtenheft) wird auch die Anzahl von Sitzungen eines Gremiums herangezogen und daraus der Zeitaufwand einschließlich Vorbereitung und Nacharbeiten aller Beteiligter errechnet.

Fur eine gute Aufwandsschatzung ist es erforderlich, dass man gut verstanden hat, was gefordert wird, dass der Leistungsumfang genau definiert ist und Dinge, die zwar sinnvoll, nutzlich oder nahe liegend, aber nicht gefordert sind, explizit ausgeschlossen werden. Zwingende Notwendigkeit ist das Vorliegen eines Pflichtenheftes (Requirement Specification), das ggf. noch weiter prazisiert werden muss. Darauf basierend kann eine Liste der zu liefernden Komponenten und der im Projektverlauf zusatzlich zu erstellenden Hilfskomponenten erstellt werden. (Insbesondere Scripts, Tests, Diagnose-Hilfen) Es kann dann der Umfang oder Aufwand fur jede Komponente einzeln geschatzt werden. Unter der Annahme, dass die jeweiligen Schatzfehler voneinander statistisch unabhangig sind, heben sich die Schatzfehler fur die einzelnen Komponenten teilweise gegenseitig auf.

Hierbei ist jedoch zu beachten, dass systematische Schatzfehler, wie zum Beispiel ein generelles Unterschatzen von Aufwanden durch komponenten-basiertes Schatzen, nicht behoben werden. Ferner stellt sich oft heraus, dass im Laufe des Projekts noch Komponenten benotigt werden, die gar nicht geschatzt wurden. Um solchen systematischen Schatzfehlern zu begegnen, kann man Schatzungen von alten Projekten mit den tatsachlichen Projektgroßen korrelieren und aus dieser Korrelation einen entsprechenden Korrekturfaktor fur den systematischen Schatzfehler ableiten (Eisbergfaktor).

Soweit nicht schon bei der Komponentenschatzung berucksichtigt mussen Erschwernisse oder Restriktionen durch Korrekturfaktoren berucksichtigt werden. Bei der [COCOMO](https://de.m.wikipedia.org/wiki/COCOMO)-Methode sind 14 solcher Faktoren angegeben, die aus statistischer Auswertung von vielen Projekten gewonnen wurden. Manche sind heute irrelevant (z. B. Turnaround-zeit im Closed-Shop-Betrieb), die meisten aber noch nutzlich. Der wichtigste ist die Qualitat der Entwickler. Er ist bei Bohm mit einer Spanne von 4.2 zwischen bestem und schlechtestem Team angegeben und durfte heute noch hoher sein.

Barry W.Boehm, der Vater von COCOMO nennt auch noch einige andere Schatzverfahren:

Man sucht nach ahnlichen Projekten und nimmt mit Auf- und Abschlagen fur dies und jenes deren Kosten. Vorteil: Bezug auf reale Kosten. Nachteil: Unterschiede in Aufgabe, Systemumgebung, Personal. Geeignet fur Gesamtsicht, wo man sich sonst in Details verlieren wurde und fur Plausibilisierung.

„[Parkinsons erstes Gesetz"](https://de.m.wikipedia.org/wiki/Parkinsonsche_Gesetze) besagt „Arbeit dehnt sich aus, so weit es geht": Wenn man Budget und den Endtermin kennt, ergibt sich daraus, wie viele Leute man einsetzen kann und was es kostet. Dieses Verfahren ist aus der Praxis bekannt: Wenn man zu fruh fertig ist, macht man Verschonerungen und testet mehr. Wenn man nicht fertig wird, aber das Budget erschopft oder der Endtermin erreicht ist, wird der erreichte Zustand als fertig erklart.

Aus diversen Quellen weiß man, was der Kunde bereit ist zu zahlen, oder was ein Konkurrent anbietet; meist weit weniger als eine solide Arbeit kosten wurde. Die Schatzung wird solange frisiert, bis sie zur Erwartung passt. Boehm schreibt weiter dazu: „The price-to-win technique has won a large number of software contracts for a large number of companies. Almost all of them are out of business today." („Die Price-to-Win-Technik hat vielen Softwarefirmen eine große Zahl an Auftragen verschaffen konnen. Die meisten dieser Firmen sind heute nicht mehr im Geschaft.")

Alternativ oder zusatzlich kann die Aufwandsschatzung nach der [Delphi-Methode](https://de.m.wikipedia.org/wiki/Delphi-Methode) verbessert werden. Dabei werden einfach mehrere Personen gebeten, unabhangig voneinander Schatzungen abzugeben. Die Hoffnung ist wieder, dass sich Schatzfehler bei der Mittelwertbildung gegenseitig ausgleichen. Zusatzlich besteht bei der Delphi-Methode die Moglichkeit, die Schatzer uber stark voneinander abweichende Schatzungen diskutieren zu lassen. Dabei kann z. B. aufgedeckt werden, dass das Gros der Schatzer einen Problemaspekt ubersehen und deswegen den Aufwand unterschatzt hat. Ebenso kann es sein, dass ein Schatzer eine Realisierungsidee hat, die einen wesentlich geringen Aufwand erfordert. Wichtig ist dabei, dass sich die Beteiligten uber den Schatzgegenstand klar sind, also z. B. Netto-Zeitaufwand fur eine Programm-Änderung, Bruttozeitaufwand fur Änderung samt Test, Dokumentationsanderung und Benutzerinformation. Die Schatzklausur arbeitet so ahnlich, nur weniger formalisiert. Die Experten schatzen hier nicht getrennt voneinander sondern im Kollektiv. Es werden die 3 Phasen Vorbereitung, Durchfuhrung und Nachbereitung durchlaufen.

Die Grundidee der [COCOMO](https://de.m.wikipedia.org/wiki/COCOMO)-Methode „Constructive Cost Model" besteht darin, alle kostenrelevanten Elemente zu erfassen, zu bewerten und hochzurechnen. Die Bewertung stutzt sich dabei auf Erfahrungswerte, die aus einer [Erfahrungsdatenbank](https://de.m.wikipedia.org/w/index.php?title=Erfahrungsdatenbank&action=edit&redlink=1) gewonnen wurde, in die eine Vielzahl von Projekten eingetragen wurden. Diese Erfahrungsdatenbank basiert auf DSI und einer Systemumgebung aus der Lochkartenzeit. Die Formeln fur den Basisaufwand sind daher heute nicht mehr brauchbar, das Grundkonzept mit passenden Bezugsgroßen sehr wohl.

[Functional Size Measurement](https://de.m.wikipedia.org/wiki/Functional_Size_Measurement), oder als eine Auspragung das [Function-Point-Verfahren](https://de.m.wikipedia.org/wiki/Function-Point-Verfahren), sind selbst keine Aufwandsschatzverfahren, sondern dienen zur Bewertung des Umfangs fachlicher Anforderungen an ein Softwareprojekt. Wenn man annimmt, dass die Functional Size ein wesentlicher Aufwandstreiber fur ein Softwareprojekt ist, kann daraus auf den Aufwand fur das Projekt geschlossen werden. Eine einfache oder gar lineare Beziehung zwischen der Functional Size und dem Projektaufwand besteht jedoch nicht. Deshalb ist fur eine Aufwandsschatzung auf jeden Fall noch ein Modell wie z.B. [COCOMO](https://de.m.wikipedia.org/wiki/COCOMO) notwendig, das die weiteren Aufwandstreiber beschreibt. Viele kommerzielle Aufwandsschatzmodelle verwenden die Functional Size ebenfalls als Input-Variable.

An Schatzverfahren werden neben Genauigkeit noch eine Reihe weiterer z. T. sich widersprechende Anforderungen gestellt:

  * Es soll moglichst fruh einsetzbar sein (Der Auftraggeber will am Anfang wissen, was es am Ende kostet)
  * Änderungen in den Anforderungen sollen sich auf die Schatzung auswirken (Mehr-/ Minderkosten)
  * Die Ergebnisse sollen einfach nachvollziehbar sein
  * Außer den Kosten soll auch ein grober Terminplan herauskommen, der den Übergang zur Projektplanung ermoglicht
  * Das Schatzverfahren selbst soll moglichst wenig kosten

Eine gute Aufwandsschatzung sollte auch immer mit Angaben zur Genauigkeit der Schatzung einhergehen. Solche Angaben konnen wieder aus der statistischen Betrachtung von fruheren Schatzungen abgeleitet werden. Im Softwarebereich geht man bei einfachen Schatzansatzen von einer Genauigkeit von bis zu 10 aus. Das heißt, bei einem geschatzten Aufwand von einem Personenjahr liegt der wahrscheinliche Aufwand zwischen z. B. 36 Tagen und 10 Jahren. Durch Komponentenschatzung und Delphi-Methode kann dies oft auf einen Schatzfehler in der Großenordnung des Faktor 2 verbessert werden. Humphrey berichtet in seiner Probe-Methode in sehr gunstigen Fallen sogar von einem Schatzfehler von nur 15 % in 75 % Prozent der Projekte. Dies gelingt aber nur, wenn eine große Anzahl von ahnlich gelagerten Vergleichsprojekten zur Verfugung steht und wenn sich bei dem neuen Projekt kein entscheidender Einflussfaktor geandert hat. Neues Personal, neue technische Anforderungen, neue Entwicklungswerkzeuge, neue Laufzeitumgebungen, neue Kunden oder ahnliche Risiken konnen leicht wieder zu einem Schatzfehler von mehreren Großenordnungen fuhren.

Es gibt dabei auch ein Paradoxon: Je mehr „Faktoren" (nicht Summanden) berucksichtigt werden, umso plausibler ist das Ergebnis, weil Faktoren, die offensichtlich einen großen Einfluss haben berucksichtigt werden. Allerdings wird die Schatzgenauigkeit dabei verschlechtert, denn wenn z. B. 10 Faktoren um einen Faktor 1.05 zu optimistisch oder pessimistisch geschatzt werden, so macht das einen Faktor 1.6 aus. Softwareentwickler tendieren stark zu Optimismus. Verantwortliche auch wegen des „price-to-win".

Aufwand entsteht

  * fur das Lesen und Verstehen der Anforderungen meist fur mehrere Personen
  * fur die Definition von Leistungen, Einschrankungen, Restriktionen
  * fur die eigentliche Schatzung
  * fur das Verkaufen der Schatzung, Nacharbeiten, Pflege von Schatz-Datenbanken

Schatzen ist oft ein iteratives Verfahren, indem Leistungen reduziert oder erganzt werden, Annahmen korrigiert werden.

Die Kosten fur eine gute Schatzung betragen nach manchen Angaben bis zu 3 % des Projektumfangs, die fur ein gutes Angebot bis zu 5 % des Projektumfangs.

Damit wird die Schatzung oft schon selbst zum Problem: Bei 10 Anbietern und 5 % Aufwand je Anbieter machen schon die Angebotskosten 50 % des Projektumfangs aus. Aus Sicht des Anbieters muss er aber bei einem erfolgreich akquirierten Projekt die Angebotskosten fur alle 9 anderen wieder mit herein holen. Er musste dazu ziemlich teuer sein, was es unwahrscheinlich macht, dass er den Auftrag bekommt. Dies legt es nahe, eine eher grobe Schatzung mit hohem Aufschlag zu machen um Schatzaufwand (und dadurch auch Schatzkosten) gering zu halten.

  * Manfred Burghardt: _Projektmanagement: Leitfaden fur die Planung, Überwachung und Steuerung von Entwicklungsprojekten._ 7\. Auflage. Publicis Corporate Publishing, Erlangen 2006, [ISBN 3-89578-274-2](https://de.m.wikipedia.org/wiki/Spezial:ISBN-Suche/3895782742), S. 156ff.
  * IBM Deutschland: _Die Funktion Point Methode, Schatzmethode fur IS-Anwendungs-Projekte_. Formnr. E12-1618, 1985.
  * [Harry M. Sneed](https://de.m.wikipedia.org/wiki/Harry_Sneed): _Software-Projektkalkulation._ Hanser, 2005.
