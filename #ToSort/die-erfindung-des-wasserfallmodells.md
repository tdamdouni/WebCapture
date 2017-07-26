# Die Erfindung des Wasserfallmodells

_Captured: 2017-05-31 at 18:49 from [blogs.itemis.com](https://blogs.itemis.com/de/die-erfindung-des-wasserfallmodells?utm_source=hs_email&utm_medium=email&utm_content=52554399&_hsenc=p2ANqtz-8OJ_1catLfKzpW-N2ZL-lk96ukHAj58LjluwvtbVCdnOyqSASRCKxozqWTY1AAj_-Nie4VKLTWHu_wyn-XCuusoEyJ7A&_hsmi=52553722)_

Spricht man uber Agilitat kommt immer mal wieder das Wasserfallmodell zur Sprache. Mit seiner strengen sequentiellen Abarbeitung einzelner Projektphasen gilt es als klassischer Gegenentwurf zu Agilitat.

Denn eine neue Phase im Wasserfallmodell kann erst gestartet werden, wenn eine andere abgeschlossen ist.

Dieses Vorgehensmodell wird fast immer mit [Winston W. Royce](https://en.wikipedia.org/wiki/Winston_W._Royce) in Verbindung gebracht. Und sein erweitertes Wasserfallmodell findet sich in vielen Abhandlungen zu diesem Thema.

![Wasserfallmodell im Schaubild – Darstellung aller Projektphasen von den Anforderungen bis zum Betrieb](https://blogs.itemis.com/hs-fs/hubfs/Bildschirmfoto%202017-03-17%20um%2013.57.43.png?t=1496243558067&width=2172&name=Bildschirmfoto%202017-03-17%20um%2013.57.43.png)

> _Wasserfallmodell im Schaubild - Darstellung aller Projektphasen von den Anforderungen bis zum Betrieb_

Damit erscheint Herr Royce in einem aus heutiger Sicht ziemlich schlechten, weil unagilem Licht. Und das hat er nicht verdient.

Er hat das [Wasserfallmodell](https://www.itemis.com/de/agile/scrum/kompakt/grundlagen-des-projektmanagements/wasserfall-modell) namlich gar nicht erfunden, sondern lediglich um eine agile Komponente erweitert, da auch ihm schon aufgefallen war, dass eine starre Vorgehensweise in der Praxis zu schlechten Ergebnissen fuhrte.

Um dies zu verstehen, muss man sich vor Augen halten, vor welchen Problemen die Softwareentwicklung damals stand.

## Wie die Softwarekrise zum Software Engineering fuhrte

In der Mitte der 60er-Jahre bestimmte die Hardware die Entwicklung von Software. Deren Anwendungsgebiete waren aufgrund der begrenzten Moglichkeiten der damals eingesetzten Hardware weder komplex, transparent noch gut strukturiert. Verbesserungen im Bereich der Hardware fuhrten dann allerdings dazu, dass sich immer mehr Aufgabengebiete fur eine elektronische Bearbeitung anboten. Die neuen Aufgabengebiete wurden komplexer und ließen sich nicht mehr einfach strukturieren.

Den Entwicklern jener Zeit standen nur Methoden zu Verfugung, mit denen man kleine Programme entwickeln konnte. Diese Modelle waren der neuen Komplexitat der Aufgaben jedoch nicht mehr gewachsen.

Es fehlte eine adaquate Technologie auf der Softwareseite fur die Entwicklung komplexer Systeme.

Als Konsequenz dieses Sachverhaltes wurde Software schlagartig sehr teuer und konnte nicht mehr termingerecht fertiggestellt werden. Kosten- und Zeitaufwande konnten nicht mehr geschatzt werden. Außerdem mangelte es an Fachkraften, weshalb Projekte oft von Laien erstellt werden mussten.

Undurchschaubare, kaum erweiterbare und weitgehend unzuverlassige Software waren die Folgen.

Die mangelnde Zuverlassigkeit der Software fuhrte dazu, dass ein Großteil der Programmierer mit Fehlersuche und Korrekturen beschaftigt war. Da insbesondere das Militar von diesem Umstand betroffen war, wurden gerade in diesem Bereich große Anstrengungen unternommen, die Krise zu uberwinden.

Und so wurde im Jahr 1968 auf einer NATO-Konferenz erstmalig von Software Engineering gesprochen. Definiert wurde dieser Begriff von [Peter Naur](https://de.wikipedia.org/wiki/Peter_Naur) und [Brian Randell](https://de.wikipedia.org/wiki/Brian_Randell) als "establishment and use of sound engineering principles in order to obtain economically software that is reliable and works efficiently on real machines".

Hiermit sollte zum Ausdruck gebracht werden, dass die Softwareentwicklung, wie andere Ingenieurwissenschaften auch, einer grundlegenden theoretischen Fundierung sowie einer fur die Praxis tauglichen Verfahrenstechnik bedurfe, um den folgenden Zielgroßen gerecht zu werden:

  * Produktion von Software in hoher Qualitat
  * Erstellung von Software innerhalb eines festen Budgetrahmens
  * Fertigstellung von Software zu einem geplanten Zeitpunkt

Mit der Übertragung von ingenieurwissenschaftlichen Methoden und Prinzipien auf die Softwareentwicklung ging man definitiv in die richtige Richtung. Allerdings passten die von Ingenieuren verwendeten Vorgehensmodelle nicht. Sie waren - wie bereits erwahnt - in einzelne Phasen aufgeteilt, die nacheinander abgearbeitet wurden.

Von Wasserfallmodellen war damals ubrigens nicht die Rede. Dieser Begriff etablierte sich erst einige Jahre spater.

## Ein Wasserfall, der keiner ist

Winston W. Royce erkannte die Schwache dieser Modelle und empfahl Ruckkopplungen zwischen den einzelnen Phasen zuzulassen. Diese waren fur ihn zwar immer noch Ausnahmen, da sie mit hohen Kosten verbunden waren, aber trotz allem notwendig, um den Erfolg eines Projekts sicherzustellen.

Royce setzte damit erstmalig agile Prinzipien um, wurde aber leider nicht richtig verstanden.

Dabei war er mit seiner Kritik an den bekannten Modellen sehr deutlich:

  * So war es immer noch unmoglich, im Rahmen einer einzigen Analysephase eine vollstandige, zeitlich uberdauernde Beschreibung einer Organisation als Grundlage fur eine Anforderungsdefinition zu erhalten.
  * Es war immer noch mit hohen Kosten verbunden, alle einzelnen Projektphasen ohne Ruckschritte vollstandig zu durchlaufen.
  * Eine Fehlerbehebung ausschließlich im Rahmen einer Pflege und Wartungsphase durchzufuhren war nach wie vor nicht wirtschaftlich.

Außerdem fuhrte er wichtige neue Prinzipien ein, die heute fur uns selbstverstandlich sind. So schlagt er beispielsweise eine fruhe Benutzerbeteiligung vor:

_It is important to involve the customer in a formal way so that he has committed himself at earlier points before final delivery. _

Usability lasst grußen!

Es lohnt sich auf jeden Fall mal einen Blick in das Originaldokument [MANAGING THE DEVELOPMENT OF LARGE SOFTWARE SYSTEMS](http://www.cs.umd.edu/class/spring2003/cmsc838p/Process/waterfall.pdf) zu werfen.

Das endgultige Modell von Royce sieht ubrigens wie folgt aus.

![Schaubild eines Projektmanagement Modell nach Royce. Ein Wasserfall, der keiner ist.](https://blogs.itemis.com/hs-fs/hubfs/Bildschirmfoto%202017-03-17%20um%2013.58.07.png?t=1496243558067&width=2172&name=Bildschirmfoto%202017-03-17%20um%2013.58.07.png)

> _Schaubild eines Projektmanagement Modell nach Royce. Ein Wasserfall, der keiner ist._

Mit einem Wasserfall, der als Begriff ubrigens im gesamten Dokument von Royce nicht genannt wird, hat das wohl nichts mehr zu tun!

Mehr uber das Wasserfallmodell und seine Alternativen erfahrst du ubrigens in unserem kostenlosen E-Book "Scrum Kompakt".
