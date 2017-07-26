# Wie die Fachseite Produkte selbst entwickeln kann

_Captured: 2017-06-30 at 21:51 from [blogs.itemis.com](https://blogs.itemis.com/de/wie-die-fachseite-produkte-selbst-entwickeln-kann?utm_source=hs_email&utm_medium=email&utm_content=53657294&_hsenc=p2ANqtz--cUXuroknD00k39Swlyngd-g3JtSo_z7hmeNqEE-MgRzgD25-NoSIge6IS7KSonsInbRchul0jQEen2jO0DtCq-X85QQ&_hsmi=53657294)_

Wir leben in einer rasanten Zeit: Neue Produkte kommen mit unglaublicher Geschwindigkeit auf den Markt. Dass wir unser Produkt schneller als unsere Konkurrenz auf den Markt bringen, kann bereits ein wesentliches Kriterium fur den Erfolg des Produkts sein. Hinter einer Produktentwicklung steht jedoch meist ein umfangreicher und aufwandiger Prozess, der viele Übergaben zwischen verschiedenen Rollen erfordert.   
Ich zeige euch eine Moglichkeit, wie ihr diesen Prozess abkurzen und somit die Time to Market beschleunigen konnt.

## Was ware, wenn Mitarbeiter der Fachseite in die Entwicklung einbezogen wurden?

Das klingt erst einmal komisch: Jemand, der die Fachseite in einem Unternehmen vertritt und eigentlich dafur zustandig ist, Produkte zu spezifizieren, soll auch an der Entwicklung des Produkts beteiligt werden? Ist dafur nicht umfangreiches technisches Knowhow notwendig?

Lassen wir das _Wie _zunachst einmal außen vor und uberlegen uns, was wir uberhaupt davon hatten, wenn dies tatsachlich der Fall ware. Wenn wir einen Blick auf Produktentwicklungsprozesse in verschiedenen Branchen werfen, dann gibt es oftmals die Unterteilung in den Fachbereich und die IT. Mitarbeiter des Fachbereichs haben, wie der Name sagt, umfangreiches fachspezifisches Wissen, das fur die fachliche Funktionalitat bzw. Korrektheit des Produkts essentiell ist. Meist verfugen sie jedoch uber wenig technisches Wissen. Die IT-Mitarbeiter wiederum haben dieses technische Wissen, ihnen fehlt jedoch das fachliche Knowhow bzw. das Interesse, sich in das Thema tief einzuarbeiten. Das fuhrt dazu, dass sich der Fachbereich Gedanken uber die Ausgestaltung und Art des Produktes macht, diese Gedanken in irgendeiner Form, z. B. in Anforderungsdokumenten oder Pflichtenheften, dokumentiert und dann an die IT ubergibt, die fur die Umsetzung des Produkts verantwortlich ist.

![Übergabe-Anforderungen-IT-Fachseite.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Usability/Austausch-zwischen-Kollegen.jpg?t=1498831770942&width=2172&name=Austausch-zwischen-Kollegen.jpg)

## Probleme durch Übergaben zwischen Fachbereich und IT

Diese Übergaben bringen jedoch einige Probleme und Herausforderungen mit sich. Beispielsweise muss der Fachbereich seine Ideen fur das Produkt so formulieren, dass die IT diese in Quellcode ubersetzen kann. Die Anforderungsbeschreibung muss dabei eindeutig verstandlich sein, um Fehler zu vermeiden. Um das zu gewahrleisten, ist es oftmals nicht mit diesen beiden Übergaben getan: Fur eine gute Übergabe werden Personen zwischengeschaltet, die die Gedanken zum Produkt in strukturierter Form erfassen oder im Extremfall sogar in Modelle oder Pseudocode ubersetzen, welche von der IT dann in Quellcode ubertragen werden konnen.

Diese Erfassung ist vor allem wichtig, wenn ein IT-Dienstleister eingebunden ist, der im Ausland sitzt, denn in diesem Fall sind auch sprachliche Barrieren zu beachten: Neben der inhaltlichen Richtigkeit muss gewahrleistet werden, dass die Spezifikation von beiden Seiten sprachlich verstanden wird. Zum Testen der Umsetzung erfolgt dann meist wieder eine Übergabe, denn es muss sichergestellt werden, dass das implementierte Produkt auch so funktioniert, wie es funktionieren soll - und das kann wiederum besser die Fachseite beurteilen.

## Was waren die Vorteile, wenn die Fachseite an der Implementierung beteiligt ware?

Das alles kann sehr zeitaufwandig sein, denn die gleichen Sachverhalte mussen wiederholt in unterschiedlicher Art und Weise beschrieben werden - dass sich Fehler oder redundanzbedingte Inkonsistenzen einschleichen, ist dabei fast vorprogrammiert. Stellen wir uns jetzt also vor, wir wurden uns alle diese Übergaben sparen und die Fachseite hatte direkt die Moglichkeit, ihre Gedanken so auszudrucken, dass dies automatisch in Quellcode ubersetzt werden kann. Wir wurden uns dadurch einiges an Zeit sparen, denn wir mussten die Dinge nur einmal aufschreiben. Gleichzeitig vermeiden wir, dass durch die Übergaben Fehler entstehen, z. B. weil etwas falsch verstanden wurde. Und: Das Produkt konnte deutlicher schneller an den Markt kommen.

## Wie kann sich die Fachseite bei der Entwicklung einbringen?

Der Grundgedanke klingt also erstmal gut. Aber wie ist das moglich, ohne dass der Fachbereich Schulungen in Java, C und Co. absolviert oder man alles in Excel-Monstern ausdruckt?

![die-fachseite-entwickelt-selber-code.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Usability/programming-laptop.jpg?t=1498831770942&width=2172&name=programming-laptop.jpg)

Die technischen Moglichkeiten dafur existieren. Tools wie beispielsweise [MPS von Jetbrains](https://www.jetbrains.com/mps/) erlauben es, Sachverhalte in domanenspezifischen Sprachen (also Sprachen aus der Anwendungsdomane des Nutzers) zu erfassen und daraus dann spater Quellcode zu generieren. Der Anwender, also in diesem Fall der Fachbereich, formuliert die Sachverhalte dabei so, wie er es gewohnt ist (z. B. in Form mathematischer, tabellarischer, graphischer oder textueller Notationen), druckt hinterher auf einen Knopf und heraus kommt eine ausfuhrbare Implementierung. Wenn die Sprachen und Werkzeuge richtig gestaltet werden, konnen die Fachbereiche auch gleich Tests schreiben oder Anwendungsfalle durchsimulieren und dadurch die Korrektheit weiter steigern.

## Eine gute Usability ist das A und O

Da wir - wie eingangs erwahnt - jedoch nicht davon ausgehen konnen, dass der Fachbereich ein umfassendes technisches Verstandnis mitbringt (was er auch nicht soll!), ist es umso wichtiger, dass entsprechende Tools den Nutzer unterstutzen, seine Gedanken korrekt zu formulieren - die Usability muss also stimmen, sowohl die der domanenspezifischen Sprache, als auch die der Anwendung, in welcher der Nutzer mit der Sprache arbeitet.

In Bezug auf die domanenspezifische Sprache ist es zunachst wichtig zu identifizieren, wie der Nutzer Dinge normalerweise dokumentieren wurde und welche Abstraktionen, Notationen und Begrifflichkeiten er in seinem Arbeitsalltag und seiner Fachdomane verwendet. Durch dieses Wissen kann der Nutzer spater im Tool mit einer Sprache und Notation arbeiten, die er bereits kennt.

Gewohnungsbedurftig kann es dagegen fur den Nutzer sein, mit Werkzeugen zu arbeiten, die sich stellenweise anders verhalten als ihm Bekanntes, wie Microsoft Word oder Excel. Grund dafur ist, dass ein solches Werkzeug auf Basis einer Sprachdefinition arbeitet, die den Nutzer dazu zwingt, sich an die Sprache zu halten. Nutzer konnen dies zunachst als Einschrankung sehen. Auf der anderen Seite konnen solche Werkzeuge die Nutzer besser unterstutzten (z. B. bei Fehlerprufungen, Tests oder Simulationen). Daher ist im Hinblick auf die Usability der Werkzeuge essentiell, den Nutzer bei seinen typischen Arbeitsschritten zu unterstutzen: Das Werkzeug kann dem Nutzer beispielsweise Vorschlage machen, was er als nachstes eingeben konnte, kann ihm Konstrukte, die immer wiederverwendet werden, als Templates anbieten, in denen er nur noch die variablen Teile ausfullen muss, und es ihm erlauben, bestehende Elemente zu referenzieren und wiederzuverwenden. Zudem helfen im Hintergrund laufende Validierungen und daraus erzeugte Fehlermeldungen dem Nutzer, eingeschlichene Fehler direkt aufzudecken und zu beheben.

## Schneller als der Markt sein

Es ist also tatsachlich durch nutzergerecht gestaltete Tools und Sprachen moglich, dass der Fachbereich die definierten Produkte auch direkt umsetzt. Wir werden dadurch schneller, vermeiden Fehler und reduzieren die Komplexitat der Entwicklungsprozesse. Es kann also wirklich eine gute Moglichkeit bieten, mit der Schnelllebigkeit unserer Markte mitzuhalten und diese vielleicht sogar zu uberholen.
