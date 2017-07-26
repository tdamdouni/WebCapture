# Testkonzepte - Hettwer UnternehmensBeratung GmbH - HUB

_Captured: 2016-09-28 at 22:09 from [www.hettwer-beratung.de](http://www.hettwer-beratung.de/konzepte/testkonzept/testabweichungsmanagement/?mobile=1)_

![](https://image.jimcdn.com/app/cms/image/transf/dimension=282x10000:format=jpg/path/sfb8526475ed9bfe9/image/ib1bc20ea3323f235/version/1403648485/image.jpg)

Im Rahmen eines Testkonzeptes sollte verbindlich festgelegt werden, welche Gewichtungen und Prioritäten für ein Testprojekt zu verwenden sind.

Sollten bei einer Testauswertung vom erwarteten Testergebnis Abweichungen festgestellt werden, sind diese in einem Fehlerprotokoll klar und präzise schriftlich zu beschreiben.

Die Einstufung der Schwere und Dringlichkeit der Fehlerbehebung obliegt beim Auftreten eines Fehlers dem fachlichen Tester. 

  

Es empfiehlt sich, dass alle Fehler an einer gesammelten Stelle erfasst werden. Des Weiteren sollte an dieser Stelle auch der aktuelle (Bearbeitungs-) Status des Fehlers gepflegt/ weiterverfolgt werden können.

Der Status einer Testdurchführung kann beispielsweise in regelmäßigen Jour Fixes mit den benötigten Teilnehmern festgestellt werden.

**Die Ergebnisse eines Test Jour Fixes können sein:**

» Neue Abweichungen sind adressiert und priorisiert

» Alte Prioritäten werden überwacht, Fertigstellungstermine sind gesetzt/ werden gewährleistet

» Notwendige Entscheidungen werden abgestimmt und eingeleitet

» Testdurchführung von Re-Tests wird vorangetrieben

Vor einem produktiven Einsatz sollten nicht behobene Restfehler einzeln auf deren Auswirkung bewertet und in entsprechenden Testnachweisen dokumentiert werden.

## Kriterien für die Klassifizierung von Abweichungen

### Gewichtung der Fehlerschwere

**Gewicht**

**Wirkung**

**Beispiele**

1

Aufgrund einer schwerwiegenden Fehlermeldung kann die Software nicht in der Produktion eingesetzt werden.

Komplettabstürze

Anzeigen nicht abgefangener Fehler

Applikation steht temporär nicht zur Verfügung

Daten werden nicht oder falsch gespeichert

Eingegebene Daten lassen sich nicht mehr finden

Grundlegende Funktionsprobleme (z.B. Speichern = Abbruch)

Datenzugriff ist entgegen der Spezifikation möglich

Rolle kann Funktionen nutzen, die nicht verfügbar sein sollten

2

Ein Fehler schränkt die Funktionalität ein, lässt jedoch die Benutzung der Software noch zu.

Ergebnis der Prüfungen entspricht nicht Anforderungen

Schnittstellen lassen sich nicht ansprechen/ stehen nicht bereit

Felder werden falsch initialisiert

Dokumente werden mit falschen Textbausteinen erstellt

3

Ein Fehler schränkt die Funktionalität geringfügig ein, der Anwender kann damit halbwegs gut weiter arbeiten

Vorbelegung von Feldern entspricht nicht Spezifikation

Texte werden bei der Ausgabe abgeschnitten

Das Layout der Dokumente entspricht nicht den Vorgaben

Labels von Feldern sind nicht vollständig

keine Plausibilitätsprüfung von Eingabewerten

### Priorität der Fehlerbehebung

Für eine Priorisierung genügt im Allgemeinen eine vierstufige Skala. Jeder Stufe ist dann eine Reaktionszeit zuzuordnen, innerhalb deren mit der Fehlerbehebung begonnen werden muss.

**Priorität**

**Bedeutung**

**Reaktionszeit (Beispiel)**

1

sehr hohe Priorität

Beginn der Fehlerbehebung sofort

2

hohe Priorität

Beginn der Fehlerbehebung innerhalb von 2 Arbeitstagen

3

mittlere Priorität

Beginn der Fehlerbehebung wird individuell festgelegt; jedoch nicht innerhalb von 2 Arbeitstagen oder später als x Tage/Wochen

4

geringe Priorität

Beginn der Fehlerbehebung wird individuell festgelegt; kann jedoch bei hohem Aufwand mehr als x Tage/Wochen zurückgestellt werden.

### Dringlichkeit der Fehlerbehebung

Die Dringlichkeit mit der eine Fehlerbehebung erfolgen soll, wird aus dem Fehlergewicht und der Kategorie des Testobjektes - bei dessen Test die Abweichung aufgetreten ist - abgeleitet.

Bei einer Verwendung von Standardklassen der ABC Risikoanalyse können in Verbindung mit der Fehlerschwere beispielhaft folgende Prioritäten definiert werden.

**Severity**

**Testobjekt Kategorie A**

**Testobjekt Kategorie B**

**Testobjekt Kategorie C**

1

sehr hohe Priorität

hohe Priorität

mittlere Priorität

2

hohe Priorität

mittlere Priorität

geringe Priorität

3

mittlere Priorität

geringe Priorität

geringe Priorität

## Prozessflow einer Abweichungsbeschreibung/-bearbeitung

Die Feststellung und Erfassung von Abweichungen sowie die Festlegung deren Priorität obliegt in der Regel den (fachlichen) Testern.

In Abhängigkeit von der Größe einer Projektorganisation kann die Bewertung eines Fehlers und die Ermittlung der Zuständigkeit für dessen Behebung einem (fachlichen) Testmanager bzw. dem Testkoordinator zugeordnet werden.

Der Testmanager bzw. Testkoordinator leitet die Fehlermeldung an eine zentrale Person in der Softwareentwicklung weiter. Dieser sogenannte Defectmanager koordiniert die Fehlerbearbeitung durch eine entsprechende Zuweisung wiederum an einen zuständigen Entwickler.

Der Entwickler prüft und weist den Fehler an den Testmanager/ Testkoordinator zurück beziehungsweise er akzeptiert und behebt diesen vor einer Zuweisung an den Testmanager/ Testkoordinator.

Daraufhin kann der Fehler dem Tester zu einer abschließenden Bewertung und zum Nachtest (Re- Test) zugewiesen werden. Ist der Nachtest erfolgreich, wird der Fehler mit einer entsprechenden Dokumentation geschlossen.

### Anmerkung

Die parallele Verwaltung von allen Fehlern erfolgt prinzipiell durch einen Testmanager. Dieser kann beispielsweise durch die Generierung von unterschiedlichen Reports jederzeit einen aussagekräftigen Teststatus (Anzahl Testobjekte, Anzahl geplante Testfälle, davon bereits ausgeführte Testfälle, davon fehlerhafte Testfälle) und Testfortschritt erhalten sowie somit bei Bedarf qualifizierte Maßnahmen vorschlagen, die eingeleitet werden sollen/können.

