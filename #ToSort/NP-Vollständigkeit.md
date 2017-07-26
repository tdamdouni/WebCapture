# NP-Vollständigkeit

_Captured: 2015-10-10 at 17:37 from [de.m.wikipedia.org](https://de.m.wikipedia.org/wiki/NP-Vollst%C3%A4ndigkeit)_

![](http://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/P_np_np-complete_np-hard.svg/220px-P_np_np-complete_np-hard.svg.png)

> _Mengendiagramm der moglichen Beziehungen zwischen P, NP und den Mengen der NP-schweren und NP-vollstandigen Probleme._

In der [Informatik](https://de.m.wikipedia.org/wiki/Informatik) bezeichnet man ein [Problem](https://de.m.wikipedia.org/wiki/Problem) als **NP-vollstandig** ([vollstandig](https://de.m.wikipedia.org/wiki/Vollst%C3%A4ndigkeit_\(Komplexit%C3%A4tstheorie\)) fur die Klasse der Probleme, die sich [nichtdeterministisch](https://de.m.wikipedia.org/wiki/Nichtdeterminismus) in [Polynomialzeit](https://de.m.wikipedia.org/wiki/Polynomialzeit) losen lassen), wenn es zu den schwierigsten Problemen in der Klasse [NP](https://de.m.wikipedia.org/wiki/NP_\(Komplexit%C3%A4tsklasse\)) gehort, also sowohl in NP liegt, als auch [NP-schwer](https://de.m.wikipedia.org/wiki/NP-Schwere) ist. Dies bedeutet umgangssprachlich, dass es sich _vermutlich_ nicht effizient losen lasst.

Formal wird NP-Vollstandigkeit nur fur [Entscheidungsprobleme](https://de.m.wikipedia.org/wiki/Entscheidungsproblem) definiert (mogliche Losungen nur "ja" oder "nein"), wahrend man bei anderen Problemtypen von _[NP-Äquivalenz](https://de.m.wikipedia.org/wiki/NP-%C3%84quivalenz)_ spricht (etwa bei [Suchproblemen](https://de.m.wikipedia.org/wiki/Suchproblem) oder [Optimierungsproblemen](https://de.m.wikipedia.org/wiki/Optimierungsproblem)). Umgangssprachlich wird diese Unterscheidung jedoch oft nicht vollzogen, so dass man ganz allgemein von "NP-vollstandigen Problemen" spricht, unabhangig davon, ob ein Entscheidungsproblem vorliegt oder nicht. Dies ist moglich, da verschiedene Problemtypen ineinander uberfuhrbar (aufeinander reduzierbar) sind.

Ein Entscheidungsproblem ist NP-vollstandig, wenn es

  * in der [Komplexitatsklasse](https://de.m.wikipedia.org/wiki/Komplexit%C3%A4tsklasse) [NP](https://de.m.wikipedia.org/wiki/NP_\(Komplexit%C3%A4tsklasse\)) liegt: Ein _[deterministisch_ arbeitender Rechner](https://de.m.wikipedia.org/wiki/Turingmaschine) benotigt nur polynomiell viel Zeit, um zu entscheiden, ob eine vorgeschlagene Losung eines zugehorigen Suchproblems tatsachlich eine Losung ist und
  * zu den [NP-schweren](https://de.m.wikipedia.org/wiki/NP-Schwere) Problemen gehort: Alle anderen Probleme, deren Losungen deterministisch in polynomieller Zeit uberpruft werden konnen, konnen auf das Problem derart [zuruckgefuhrt](https://de.m.wikipedia.org/wiki/Reduktion_\(Theoretische_Informatik\)) werden, dass diese Ruckfuhrung auf einem deterministischen Rechner hochstens polynomielle Zeit in Anspruch nimmt. Man spricht von einer [Polynomialzeitreduktion](https://de.m.wikipedia.org/wiki/Polynomialzeitreduktion).

Die Klasse aller NP-vollstandigen Probleme wird mit _NP-C_ bezeichnet. Die Eigenschaften dieser und anderer Klassen werden in der [Komplexitatstheorie](https://de.m.wikipedia.org/wiki/Komplexit%C3%A4tstheorie) erforscht, einem Teilgebiet der [theoretischen Informatik](https://de.m.wikipedia.org/wiki/Theoretische_Informatik).

Eine wesentliche Eigenschaft NP-vollstandiger Probleme ist, dass sie sich _vermutlich_ nicht [effizient](https://de.m.wikipedia.org/wiki/Polynomialzeit) losen lassen, dass also ihre Losung auf realen Rechnern viel Zeit in Anspruch nimmt. In der Praxis wirkt sich diese Eigenschaft nicht in jedem Fall negativ aus, das heißt, es gibt fur viele NP-vollstandige Probleme Losungsverfahren, anhand deren sie fur in der Praxis auftretende Großenordnungen in akzeptabler Zeit losbar sind.

Viele in der Praxis auftauchende und wichtige Probleme sind NP-vollstandig, was NP-Vollstandigkeit zu einem zentralen Begriff der Informatik macht. Weiter verstarkt wird diese Bedeutung durch das sogenannte [P-NP-Problem](https://de.m.wikipedia.org/wiki/P-NP-Problem):

  1. Fur kein NP-vollstandiges Problem konnte bisher nachgewiesen werden, dass es in polynomieller Zeit losbar ware.
  2. Falls nur ein einziges dieser Probleme in polynomieller Zeit losbar ware, dann ware jedes Problem in NP in polynomieller Zeit losbar, was große Bedeutung fur die Praxis haben konnte (jedoch nicht notwendigerweise haben muss).

Seit der Einfuhrung der NP-Vollstandigkeit durch Cook wurde die [Vollstandigkeit](https://de.m.wikipedia.org/wiki/Vollst%C3%A4ndigkeit_\(Komplexit%C3%A4tstheorie\)) zu einem allgemeinen Konzept fur beliebige Komplexitatsklassen ausgebaut.
