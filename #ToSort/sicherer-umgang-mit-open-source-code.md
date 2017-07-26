# Sicherer Umgang mit Open Source Code

_Captured: 2017-04-22 at 16:39 from [www.security-insider.de](http://www.security-insider.de/sicherer-umgang-mit-open-source-code-a-597990/?utm_campaign=Sharing%20Security%20Stories&utm_content=52325711&utm_medium=social&utm_source=twitter)_

![Ohne Inventarisierung, Management und Sicherung der in Anwendungen verwendeten Open-Source-Komponenten bieten Unternehmen Angreifern ein leichtes Ziel.](http://images.vogel.de/vogelonline/bdb/1213000/1213046/41.jpg)

> _[Ohne Inventarisierung, Management und Sicherung der in Anwendungen verwendeten Open-Source-Komponenten bieten Unternehmen Angreifern ein leichtes Ziel.](http://www.security-insider.de/index.cfm?pid=10700&pk=1213046&type=article&fk=597990)_

Die Verwendung von Open Source Code in Anwendungen hat sich im Laufe der Jahre dramatisch erhoht. Mittlerweile umfassen Open Source-Komponenten 50 Prozent und mehr von vielen Software-Applikationen. Unternehmen ubersehen dabei aber oft die Sicherheitsfragen im Zusammenhang mit Open Source-Anwendungen. Es gibt aber ein paar einfache Tipps, wie Unternehmen ihre Open Source Codebasis besser managen und Sicherheitsrisiken vermeiden konnen.

Wahrend die Vorteile der Nutzung von Open Source offensichtlich sind - schnelleres Time-to-Market, großere Innovationsmoglichkeiten, niedrigere Entwicklungskosten, Unterstutzung einer globalen Community - durfen die Sicherheitsfragen im Zusammenhang mit Open Source-Anwendungen nicht ubersehen werden. Mehr als 80 Prozent aller Cyber-Attacken zielen auf Software-Applikationen. Angreifer sehen Open-Source-Komponenten innerhalb von Anwendungen als lohnendes Ziel. Zudem sind Informationen uber Open Source Schwachstellen weit verbreitet, und Angreifer konnen potenziell Tausende von Anwendungen mit minimalem Aufwand kompromittieren.

Um Missverstandnissen vorzubeugen: Open Source ist genauso sicher wie kommerzieller Code. Die Debatte zu "Sicher oder nicht so sicher?" zieht sich wie ein roter Faden durch viele Diskussionsforen, ubersieht aber den springenden Punkt: viele Unternehmen sind sich einfach im Unklaren daruber, wie viel Open-Source bei ihren Anwendungen zum Einsatz kommt. Als Folge sind sie anfallig fur Schwachstellen, die sich in ihrem Open-Source befinden.

Obwohl es fur ihre Anwendungsentwicklung eigentlich kritisch ist, verfugen nur wenige Organisationen uber strenge Prozesse, um die von ihnen verwendeten Open Source-Komponenten zu identifizieren, zu verfolgen und zu verwalten. Black Duck Audits von Kunden-Codebasen zeigen durchgehend, dass die meisten Unternehmen doppelt so viel Open-Source verwenden, wie sie glauben, dass sie in ihren Anwendungen haben. Hier folgen nun einige Hinweise, wie Unternehmen ihre Open Source Codebasis besser managen und Sicherheitsrisiken vermeiden.

### Inventarisieren Sie Ihren Open Source Code

Zunachst benotigen Sie eine vollstandige und genaue Bestandsaufnahme aller Open-Source-Komponenten in Ihrer Codebasis. Ein vollstandiges Open-Source-Inventar sollte alle Open Source-Komponenten, die Version(en) im Einsatz und Download-Standorte fur jede Anwendung in Entwicklung und Produktion enthalten. Sie mussen alle Abhangigkeiten - die Komponenten, auf die Ihr Code zugreift, sowie die Komponenten, mit denen die Abhangigkeiten verknupft sind - in Ihr Inventar aufnehmen.

### Verzeichnis uber bekannte Schwachstellen

Stellen Sie sich eine Liste der bekannten Sicherheitslucken zusammen, die sich auf die von Ihnen inventarisierten Open-Source-Komponenten beziehen. Ihre primare Ressource wird wahrscheinlich die [National Vulnerability Database](https://nvd.nist.gov) sein. Beachten Sie jedoch, dass nicht alle Schwachstellen der NVD gemeldet werden und dass das Format von NVD-Datensatzen es oft schwierig macht, festzustellen, welche Version einer bestimmten Open-Source-Komponente von einer Sicherheitslucke betroffen sind.

### Identifizieren Sie mogliche Lizenz- und Code-Qualitatsrisiken

Wenn Sie Software-Bundles, eingebettete oder kommerzielle SaaS-Software erstellen, ist Open-Source-Lizenzkonformitat auch ein wichtiger Punkt - insbesondere fur Ihr juristisches Team. Unabhangig davon, wie Ihre Apps bereitgestellt werden, sollten Sie auch uberprufen, ob Sie qualitativ hochwertige Open-Source-Komponenten sowie aktuelle und stabile Versionen dieser Komponenten verwenden, die zudem von einer zuverlassigen Community aktiv verwaltet werden.

### Risiko kontrollieren

Sobald Sie Sicherheitslucken identifiziert sowie die Lizenzierung und Qualitat der Komponenten geklart haben, ist es an der Zeit, diese Risiken zu priorisieren und diese zu anzugehen. Bestimmen Sie, welche Korrekturmaßnahmen durchgefuhrt werden mussen. Ordnen Sie den entsprechenden Personen die Sanierungsarbeiten zu und verfolgen Sie den Korrekturprozess: Was wird uberpruft? Was wurde uberpruft? Was wurde behoben? Welche Fixes wurden verschoben? Was wurde gepatcht? Die Arbeit hort nicht auf, wenn eine Applikation frei gegeben wird, sie mussen sie uberwachen, solange die Anwendung in Betrieb ist.

### Manuelles versus automatisiertes Open Source Security Management

Die Chancen sind leider groß, dass manuelles Open Source-Sicherheits-Management mit erheblichen Investitionen in Zeit, Ressourcen und Budget ablauft - und dabei dennoch nie komplett sein wird. Es wird sowohl die Produktivitat Ihrer Software-Entwickler negativ beeinflussen als den gesamten SDLC (Secure Software Development Lifecycle). Daher wenden sich viele Organisationen einer automatisierten Losung zum Open Source-Risikomanagement zu. So inventarisieren sie effektiv Open Source Code, schutzen ihn vor Sicherheitsproblemen und anderen Open Source-Risiken und stellen die Anwendung von Open Source-Richtlinien sicher.

Anwendungs-Schwachstellen sind die Sicherheitsgefahr Nummer 1 fur Ihr Unternehmen. Ohne Inventarisierung, Management und Sicherung der in Ihren Anwendungen verwendeten Open Source-Komponenten bieten Sie Angreifern ein leichtes Ziel.

**Über den Autor:** Patrick Carey ist Leiter Produktmarketing bei Black Duck Software.
