# Die Details der Definition of Done

_Captured: 2017-02-22 at 11:07 from [entwickler.de](https://entwickler.de/online/agile/die-details-der-definition-of-done-579760929.html)_

![Die Details der Definition of Done](https://entwickler.de/wp-content/uploads/2017/01/shutterstock_246730075-900x450.jpg)

(C) Shutterstock.com / Andrei Simonenko

![Kanban-Board](https://entwickler.de/wp-content/uploads/2016/02/kanban-board.jpg)

> _[Kanban-Meetings … und die Rollen in Scrum](https://entwickler.de/online/agile/kanban-meetings-scrum-rollen-205837.html)_

Wann ist ein Produkt fertig? Naturlich nie! Je nachdem, woran man die Fertigstellung eines Produkts definiert, ist das die einzig wahre Antwort. Es gibt immer noch einen Bug zu beheben oder ein Feature zu optimieren. Auf der anderen Seite steht aber die Deadline, die eine Frist zur Fertigstellung setzt und oft nur begrenzt verhandelbar ist. Irgendwann muss das Produkt also in die freie Wildbahn entlassen werden, komme was wolle.

## Die richtige Definition of Done

Wie schafft man es also, mit knappen Deadlines das Beste fur den Kunden herauszuholen? Woran erkennt man, ob Code nun gut genug ist oder ob man noch etwas daran tun sollte? Fur agile Teams ist eine [Definition of Done](https://entwickler.de/online/agile/agile-methoden-planung-211822.html) naturlich die Leitlinie fur all diese Fragen, sodass die Antworten bereits zu Projektbeginn feststehen. Und doch lohnt es sich, auch einmal daruber nachzudenken, wie genau man die Definition of Done formuliert, um sowohl den Entwicklern, als auch dem Kunden gerecht zu werden.

## Anspruche uberdenken

[Was braucht der Kunde wirklich](https://simpleprogrammer.com/2016/12/07/one-thing-developers-forget/)? Das sollte die erste Frage sein, die vor einer technischen Entscheidung fur bestimmte Losungen beantwortet wird. Nicht immer ist es namlich die allerneuste Technologie, die der Kunde gerade braucht. Naturlich kann man in der Definition of Done festhalten, dass das Projekt dem State of the Art entsprechen sollte. Bei bestimmten Aspekten ist das auch durchaus sinnvoll. Aber nicht immer.

Wenn der Kunde sich vor allem eine schnelle Losung wunscht, um eine Idee zu testen oder Mitbewerbern zuvor zu kommen, sind bewahrte Technologien oft ausreichend und sinnvoller. Gleiches gilt auch fur die Tests: Es mag durchaus sinnvoll sein, jeden Bug im Backend zu finden; das Frontend muss allerdings genau so grundlich getestet werden. Nur, wenn die Usability stimmt, kann das Projekt zum Erfolg werden, egal wie gut die Technologie dahinter ist. Das alles gehort in den Bereich der geschaftlichen Perspektive auf ein Projekt, die Entwickler oft vergessen. Sie einzubeziehen fuhrt haufig zu einer besseren Definition of Done.

## Gute Schulden machen …

Zur Fertigstellung eines Projekts gehoren auch technische Schulden, die manchmal in Kauf genommen werden mussen. Es gibt gute und schlechte Schulden: Gute Schulden sind Losungen im Code, die zwar nicht so elegant sind, wie man gern hatte, aber einem definierten Zweck dienen, der uber „wenig Aufwand" hinaus geht. Gute Schulden sind eine Investition in die Zukunft!

[Harry Roberts erklart](https://24ways.org/2016/we-need-to-talk-about-technical-debt/) das Problem mit den technischen Schulden am Beispiel des Studienkredits: Wer einen Studienkredit aufnimmt, um spater in einem guten Job ein hohes Einkommen zu erzielen, macht nichts falsch. Er investiert in eine Zukunft, in der er diese Schulden abtragen kann. Wer hingegen einen Kredit fur einen neuen Fernseher aufnimmt und weiß, dass er diesen Kredit eigentlich nicht abzahlen kann, bekommt uber kurz oder lang Probleme. Auf Code bezogen heißt das: Kurzfristige Workarounds sind okay, wenn dadurch ein Ziel erreicht werden kann, das eine spatere, bessere Losung ermoglicht. Das darf sich auch in der Definition of Done niederschlagen. Ein Projekt kann durchaus mit ein paar technischen Schulden ausgeliefert werden, wenn die Schulden gerechtfertigt sind. Man darf nur nicht den Überblick verlieren und braucht einen Plan zum Schuldenabbau.

## … und schlechte Bugs abarbeiten

Bugs sind naturlich noch einmal etwas anderes als technische Schulden. Technische Schulden entstehen haufig aus Bugs und Bugs gelegentlich aus nicht gut durchdachten Losungen, die langfristig keiner mehr versteht. Aber: Wahrend technische Schulden zu einer erst einmal funktionsfahigen Losung fuhren, fuhren Bugs unmittelbar zu Fehlern. Sobald ein paar Bugs im Code toleriert wurden, steigt die Wahrscheinlichkeit, dass es immer mehr werden.

Bugs kommen naturlich in allen Farben und Formen daher, um es einmal bildlich auszudrucken. Vom winzigen Anzeigefehler bis hin zum nicht mehr funktionierenden Produkt ist alles moglich. Insofern mussen agile Teams auf jeden Bug unterschiedlich reagieren. Ein Null-Toleranz-Regel in der Definition of Done kann dabei helfen, einer Bug-Flut vorzubeugen. Gerade dadurch entsteht aber die Notwendigkeit einer schnellen Reaktion - und das passt nicht so gut zu festen, vorgeplanten Sprints in [Scrum](https://entwickler.de/online/agile/scrum-meetings-197774.html).

Teams, die mit Scrum arbeiten, stehen darum [verschiedene Optionen zur Bearbeitung von Bugs zur Verfugung](https://www.sitepoint.com/4-agile-ways-to-handle-bugs-in-production/). Die War-Room-Variante ist schwerwiegenden Problemen vorbehalten: Der Sprint wird unterbrochen, das Team arbeitet gemeinschaftlich an der Losung des Problems, weil das Produkt nicht mehr lauft. Das ist fur kleinere Bugs nicht notwendig. Sie im laufenden Sprint parallel zu bearbeiten, bringt allerdings die Planung durcheinander - vorerst kann das Sprintziel dann nicht mehr erreicht werden. Das gilt jedoch nur kurzfristig. Wenn es zur Regel wird, dass Bugs parallel durch einen Teil des Teams bearbeitet werden, sinkt einfach die Velocity des Teams insgesamt ein wenig und stabilisiert sich dann wieder, weil immer jemand an Bugs arbeitet statt Features umzusetzen.

## Richtig planen

Das wirkt sich aber auf die langfristige Planung aus, insofern es so etwas in Agile uberhaupt gibt. Zwar wird immer nur von Sprint zu Sprint geplant, am Ende will der Kunde aber ja doch wissen, wann er mit dem fertigen Produkt rechnen kann. Und wenn die [Velocity](https://entwickler.de/online/agile/scrum-vs-kanban-teil-1-scrum-235976.html) sinkt, verschiebt sich die Einschatzung diesbezuglich erst einmal. Immerhin schafft man vordergrundig weniger als geplant. Langfristig zahlt sich das aus, wenn es um die Zahl der spater auftretenden Fehler geht; wenn das Team kurzfristig jedoch anhand seiner Velocity bewertet wird, kann das zum Problem werden. Das sollte zwar in Agile nicht vorkommen, ist aber doch ein Maßstab, der immer wieder [zur Beurteilung](https://entwickler.de/online/development/agiler-burnout-261956.html) agiler Projektteams herangezogen wird.

Daraus kann eine Art der [Inflation von Story Points entstehen](https://www.infoq.com/news/2016/05/estimate-inflation), die durch das Team zugewiesen werden. Statt von funf Punkten auszugehen, werden auf einmal acht Story Points angesetzt, um die Velocity hoch zu halten. Das hilft am Ende jedoch keinem: Das Projekt wird so kunstlich aufgeblaht und schreitet nicht schneller voran, die Vergleichbarkeit des Umfangs der einzelnen Features geht verloren. Dagegen kann es helfen, [vor der endgultigen Entscheidung uber die Punktzahl](https://entwickler.de/online/agile/agile-methoden-planung-211822.html) einer Story einen Vergleich mit zwei fruher umgesetzten Stories vorzunehmen: Einem kleineren und einem großeren. Dadurch entsteht eine Einschatzung des Umfangs im Verhaltnis zum restlichen Projekt, die oft realistischer und weniger von anti-agilem außerem Druck gepragt ist.

## Gute Planung - schneller Erfolg

Ein Projekt innerhalb der Deadline abzuschließen ist nicht immer moglich. Wer die richtigen Prioritaten setzt, auch mal ein paar Abstriche an den richtigen Stellen macht und Fehler in der Planung vermeidet, kann allerdings viel Zeit sparen. So wird das Ziel, den Kunden innerhalb der vorgegebenen Zeitspanne zufrieden zu stellen, erreicht, ohne dass das Produkt darunter signifikant leidet. Technische Schulden sind namlich nicht immer schlecht, und wer es sich zur Gewohnheit macht, Bugs gleich auszubessern, hat am Ende richtig schonen Code. Man muss nur fruh genug daruber nachdenken, wie man mit diesen unvermeidlichen Hurden des Projektalltags umgehen will. Dann kann man sie ganz leicht uberwinden. Wenn die Definition of Done jedoch unerreichbar hohe Ziele setzt, fur deren Umsetzung an anderen Stellen Abstriche gemacht werden mussen, steht dem Team eine schwere Zeit bevor.
