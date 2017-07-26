# Brauchen auch Werkzeugketten ein Refactoring?

_Captured: 2017-05-10 at 21:53 from [blogs.itemis.com](https://blogs.itemis.com/de/brauchen-auch-werkzeugketten-ein-refactoring?utm_source=hs_email&utm_medium=email&utm_content=51748968&_hsenc=p2ANqtz-_fvk5VEzX9AgMQUpPtCMPJTk2sE_NlxvFGNZbEjFChUqTYEBWFziWERUtZ95rb5ZJz7H4XgNTv3irrlGONu4XVAypdCg&_hsmi=51749262)_

Neulich traf ich Emil, den erfahrenen Entwickler. Weil er uberarbeitet aussah, fragte ich ihn, was denn los sei. Als hatte er darauf gewartet, sprudelte er los: „Es geht nicht mehr, es geht einfach nicht mehr, wir kommen nicht weiter."

Ich erfuhr, dass die Weiterentwicklung in seinem Projekt seit Wochen stagniert. Das Team versucht, eine selbstregulierende Steuerung fur Ampelsysteme zu entwickeln, doch es kampft taglich mit Unzulanglichkeiten, wenn nicht Unzumutbarkeiten, ihrer Entwicklungssoftware. Die Entwickler arbeiten modellbasiert. Klingt fortschrittlich. Ist es aber nicht immer, wenn das Modellierungstool nicht zum Projekt passt - und genau das ist in Emils Projekt der Fall.

Er und seine Kollegen arbeiten mit einem in anderen Projekten bewahrten Modellierungstool, schimpfen aber standig daruber, dass der Code, den sie aus ihrem Statechart-Modell generieren, schlecht konfigurierbar sei. Der Codegenerator unterstutze nur C++03. Sie brauchen aber C++11 und C++14, erlautert Emil. Gleichzeitig gibt es keine Schnittstelle, um den Generator anzupassen. Sie ver(sch)wenden viel Zeit in umstandlichen Workarounds, um nutzbare Ergebnisse zu erhalten. Immerhin hat Emil erkannt, dass es so nicht weitergehen kann - und Einsicht ist bekanntlich der erste Schritt zur Besserung. Doch was nun?

## **Ruckbesinnung auf die wirklich wichtigen Fragen**

In solchen Phasen erweist es sich haufig als hilfreich, zu stoppen und innezuhalten, um Abstand von der alltaglichen Arbeit zu bekommen. Fur das Projektteam kann das bedeuten, sich einen [Labday](https://blogs.itemis.com/de/4-1-gewinnt-das-etwas-andere-arbeitszeitmodell) zu gonnen und sich auf die folgenden Fragen zu besinnen:

  * Welche Funktionen unseres Tools benutzen wir - und welche brauchen wir? Besitzt das Tool diese Funktionalitaten?
  * Entsprechen die vorhandenen Funktionen unseren Anforderungen?
  * Welche Anforderungen haben wir eigentlich an so ein Tool?
  * Welche Alternativen gibt es, die besser zu uns passen?
![Refactoring-von-Werkzeugketten-bringt-positive-Veränderungen.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/Vera%CC%88nderungen.jpg?t=1494425153587&width=362&name=Vera%CC%88nderungen.jpg)

Diese Fragen bauen zum Teil aufeinander auf - und ihre Beantwortung kann und sollte im Zweifel zu einem Toolwechsel fuhren. Parallel kann das Team naturlich schon nach alternativen Tools suchen.

Um sich fur das richtige Werkzeug zu entscheiden, sind die Anforderungen entscheidend: Welche Funktionen sind uns wirklich wichtig und auf welche konnen wir gegebenfalls auch verzichten? Diese Anforderungen ergeben sich idealerweise auch aus den Unzulanglichkeiten des aktuellen Werkzeugs. So ist dieses dann doch noch zu etwas zu gebrauchen ;)

Auch wenn die Entscheidung sicher nicht einfach ist und (vorerst) eine Menge zusatzlicher Arbeit mit sich bringt: Auf lange Sicht ist es nicht zielfuhrend, mit einem Tool zu arbeiten, das weder den Anspruchen des Teams noch den Anforderungen des Projektes gerecht wird.

Tauscht das Team das Werkzeug aber aus, wird die Werkzeugkette wieder fit fur die aktuelle Entwicklung - [so wie Refactorings auch Code oder Modelle fit halten](https://blogs.itemis.com/en/refactor-state-machine-yakindu-statechart-tools). Auf lange Sicht wird das Team mit einem passenden Werkzeug produktiver und sowohl Zeit- als auch Kostenaufwande werden reduziert.

Doch wie finden Entwickler wie Emil heraus, welches Modellierungswerkzeug das richtige fur ihr Projekt ist?
