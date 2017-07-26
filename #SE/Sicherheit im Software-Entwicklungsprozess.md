# Sicherheit im Software-Entwicklungsprozess

_Captured: 2015-11-03 at 11:44 from [www.informatik-aktuell.de](http://www.informatik-aktuell.de/betrieb/sicherheit/sicherheit-im-software-entwicklungsprozess.html)_

![Sicherheit sollte während des gesamten Entwicklungsprozesses der Anwendung berücksichtigt werden. © depositphotos.com / Wavebreakmedia](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_720-Depositphotos_51562003_m-2015_Wavebreakmedia_c94ed86fff.png)© depositphotos.com / Wavebreakmedia

**Geschäftskritische Webanwendungen erfordern ein hohes Sicherheitsniveau, um gegen gängige Webangriffe angemessen geschützt zu sein – insbesondere dann, wenn sie über das Internet verfügbar sind. Und hiervon gibt es einige. Um einen solchen Schutz zu gewährleisten, ist es erforderlich, dass Sicherheit nicht erst am Ende, sondern während des gesamten Entwicklungsprozesses der Anwendung berücksichtigt wird. Dies fängt bei ihrer Konzeption an, nicht zuletzt natürlich der Anwendungsarchitektur. Denn gerade hier werden Entscheidungen getroffen, die eine massive Auswirkung auf die spätere Sicherheit der Anwendung haben können – sowohl zum Guten, wie auch zum Schlechten. Da architekturelle Änderungen zu einem späteren Entwicklungszeitpunkt schnell mit erheblichen Kosten verbunden sind, werden dort sicherheitsrelevante Mängel, die im Nachhinein identifiziert werden, in der Praxis nur in den seltensten Fällen angegangen. **

## Das Prinzip "Secure SDLC"

Dieser Zusammenhang ist natürlich genauso wenig neu wie entsprechende Empfehlungen für die Verbesserung von Sicherheit im Anwendungsdesign. Bereits im Jahr 1977 haben Saltzer und Schröder ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[1]](betrieb/sicherheit/sicherheit-im-software-entwicklungsprozess.html#c11825) zentrale "Secure Design Patterns" wie etwa "Defense in Depth" oder "Least Privilege" formuliert, die bis heute nichts an Gültigkeit verloren haben. Viele heute wieder diskutierte Sicherheitskonzepte waren sogar noch Jahre davor bestens bekannt, sind jedoch im Webzeitalter in Vergessenheit geraten. Erst Anfang dieses Jahrtausends ist das Thema wieder stärker aufgegriffen und insbesondere auf die Welt der Webanwendungen bezogen worden. Einen großen Anteil daran hatte sicherlich die Gründung des Open Web Application Security Projects (OWASP) Ende 2001 sowie wenig später die Trustworthy Computing Initiative, die durch Bill Gates bei Microsoft initiiert wurde ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[2]](betrieb/sicherheit/sicherheit-im-software-entwicklungsprozess.html#c11825). Beides hatte eine massive Auswirkung auf das was wir heute über Anwendungssicherheit wissen bzw. auf Maßnahmen wie wir Anwendungen absichern. Microsoft formulierte in dieser Zeit auch das Konzept eines um Sicherheitsaspekte ergänzten Entwicklungsprozesses und betitelte diesen entsprechend als Secure (Software) Development Lifecycle ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[3]](betrieb/sicherheit/sicherheit-im-software-entwicklungsprozess.html#c11825). 

Das Grundprinzip lässt sich dabei auch gut anhand des in der Softwareentwicklung wohlbekannten V-Modells erklären. Dieses stellt jeder Tätigkeit der Spezifikation und Umsetzung (z. B. Coding) eine entsprechenden für deren Kontrolle entgegen (z. B. Unit Tests). Dieses Prinzip lässt sich auch auf die Softwaresicherheit beziehen. Denn über den gesamten Entwicklungsprozess hinweg lassen sich ebenfalls sicherheitsrelevante Aktivitäten (Entwurf von Sicherheitsanforderungen und der Sicherheitsarchitektur, Secure Coding Guidelines, Sicherheit im Deployment und Betrieb der Anwendung) definieren, denen entsprechend geeignete Aktivitäten für deren Review bzw. Test  gegenüber gestellt werden. Entsprechend wird das Design der Sicherheitsarchitektur am besten durch ein architekturelles Sicherheitsreview und die Implementierung durch ein Security Code Review bzw. Security Codescanner geprüft. Am Ende gelangen wir dadurch zu einer Sicht auf den Entwicklungsprozess, der idealerweise in jeder Phase Security Engineering und Security Review/Tests zugeordnet und gegenübergestellt sind.

![Abb.1: Microsoft's Secure SDLC. © Microsoft](fileadmin/_processed_/csm_Rohr_Abb1_fd59915f60.png)Abb.1: Microsoft's Secure SDLC. © Microsoft

Obwohl das Konzept eines solchen "Secure SDLCs" von Anfang an vielen einleuchtete, schlugen viele Initiativen, einen solchen in Unternehmen zu etablieren, fehl. Das lag nicht zuletzt an den lange Zeit noch nur wenig praxistauglich beschriebenen Konzepten, Maßnahmen und auch Tools. Viele Versuche der Implementierung scheiterten auch deshalb frühzeitig, weil sie zu einseitig betrachtet wurden. Eine Leitlinie für sichere Softwareentwicklung – und mag sie noch so gut sein – bringt nichts, wenn sie nicht auch von den Entwicklern verstanden wird und ein Prozess ihre Einhaltung sicherstellt, idealerweise durch Unterstützung geeigneter Tools. Ein Tool hilft jedoch genausowenig, wenn es zwar Unsummen gekostet hat, jedoch von niemandem bedient werden kann. Nahezu jede Maßnahme zur nachhaltigen Verankerung von Sicherheit im Entwicklungsprozess erfordert die Berücksichtigung der vier Ebenen: Vorgaben, Prozesse, Qualifikation (der Mitarbeiter) sowie Technologien. Wird nur eine dieser Ebenen ausgeblendet, scheitert nicht selten das ganze Vorhaben. Dieses zentrale Konzept der Applikationssicherheit ist in Abb.2 dargestellt.

![Abb.2: Vier Elemente der Anwendungssicherheit. © Matthias Rohr](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_Rohr-Abb2_27504ee707.png)Abb.2: Vier Elemente der Anwendungssicherheit. © Matthias Rohr 

## Reifegrade

Ein weiteres wichtiges Konzept in diesem Zusammenhang basiert auf der Erkenntnis, dass Unternehmen nicht nur einen unterschiedlichen Bedarf an Sicherheit besitzen ("Risk Appetite"), sondern sich auch im Hinblick auf den Reifegrad in Bezug auf die Umsetzung bestimmter Sicherheitsmaßnahmen sehr stark unterscheiden können. Auch dies ist sicherlich keine wirklich neue Erkenntnis, wurde jedoch für den Bereich der Applikations- bzw. Softwaresicherheit erst in 2008 durch das Reifegradmodell der OWASP (OpenSAMM) ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[4]](betrieb/sicherheit/sicherheit-im-software-entwicklungsprozess.html#c11825) sowie den BSIMM-Studien der Firma Cigital ab 2009 formuliert ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[5]](betrieb/sicherheit/sicherheit-im-software-entwicklungsprozess.html#c11825). Mittels dieser Modelle lässt sich nun der Reifegrad einer Organisation in unterschiedlichen Bereichen bewerten und ermitteln, wo konkreter Handlungsbedarf besteht. 

Der Weg zu einer Organisation mit hohem Reifegrad geschieht nicht über Nacht, sondern erfordert üblicherweise mehrere Jahre und natürlich auch entsprechende Investitionen. Da dies ohne die Unterstützung der Geschäftsführung (bzw. des Managements) nicht möglich ist, besteht der erste Schritt üblicherweise darin, dort Awareness für die Wichtigkeit solcher Investitionenen in Applikationssicherheit zu schaffen. Dies geschieht etwa durch den Einsatz von externen Sicherheitsanalysten, welche das bestehende Sicherheitsniveau geschäftskritischer produktiver Anwendungen durchleuchten und den potentiellen Schaden (z. B. Auslesen von Kundendaten durch Angreifer) durch dort gefundene Sicherheitsmängel verdeutlichen. Fließen dann die entsprechenden Mittel, kann ein Unternehmen schrittweise mit dem Aufbau der Applikationssicherheit in der Organisation beginnen. Stützt sich dies anfangs in der Regel noch stark auf den Einsatz von externen Experten und auf einzelne Unternehmensbereiche, muss das langfristige Ziel stets in der Emanzipation der Organisation von externen Dienstleistern und dem Aufbau sowie der Qualifikation eigener Experten liegen.

## Sicherheit trotz Agilität

Wichtig ist allerdings nicht alleine, welche Maßnahmen ein Unternehmen wann umsetzen sollte, sondern auch, wie diese auszugestalten sind. Denn im vergangenen Jahrzehnt hat sich die Art und Weise, wie insbesondere Webanwendungen entwickelt werden, dramatisch geändert: Weg von schwergewichtigen linearen Vorgehen (Wasserfall) hin zu agilen und zyklischen Modelle, wie vor allem SCRUM. Mit einigem Verzug führen nun auch immer mehr Großkonzerne und sogar Behörden agile Modelle in ihre Entwicklung ein. 

Neue Trends innerhalb der Softwareentwicklung warten in der Regel nicht darauf, dass es für diese erforderliche Sicherheitsmaßnahmen und -konzepte gibt. Stattdessen müssen Sicherheitsmaßnahmen sich anpassen um praktikabel zu sein. Antworten kamen aus der Sicherheitsbranche anfangs jedoch nur sehr spärlich. Und auch heute scheinen viele Sicherheitsexperten gedanklich immer noch in einer Zeit zu leben, in der die Produktivsetzung neuer Anwendung-Releases Jahre und nicht Wochen dauert. Neue Ansätze wie DevOPS sehen sogar Änderungen an der Produktion im Stunden- oder gar Minutentakt vor. Dennoch hat sich auch hier in den vergangenen Jahren vieles getan. Nicht zuletzt auch durch zwei Aspekte: Die zunehmende Berücksichtigung von sicheren Standards (Secure Defaults) in Basistechnologien wie APIs und Webframeworks sowie die Unterstützung durch Tools.

## Technologien

Musste ein Entwickler früher noch eine Vielzahl an Sicherheitskontrollen selbst implementieren, wird ihm heute häufig ein großer Teil durch das von ihm eingesetzte Webframework (z. B. JSF oder ASP.NET) oder eine extern eingebundene Sicherheitskomponente (z. B. ein Single-Sign-On-Dienst) abgenommen. Die richtige Wahl und Härtung dieser Komponenten ist für die Sicherheit einer Anwendung daher von großer Wichtigkeit. 

Ebenfalls viel getan hat sich im Bereich der Toolunterstützung, auch wenn hier sicherlich noch viel Luft nach oben ist. Zum einen sind hier Web-Security-Scanner ("DAST-Tools") zu nennen. Neben kommerziellen Tools wie IBM AppScan, Accunetix oder Burp gibt es hier durchaus verwendbare kostenfreie Tools, z. B. OWASP ZAP. Diese Art von Tools arbeitet praktisch dadurch, dass sie eine Webanwendung mittels http-Anfragen auf Sicherheitsmängel testet.

![Abb.3: HP Fortify’s Auditworkbench. © Matthias Rohr](http://www.informatik-aktuell.de/fileadmin/_processed_/csm_Rohr_Abb3_e89ed3b2ee.png)Abb.3: HP Fortify’s Auditworkbench. © Matthias Rohr 

Daneben gibt es schon seit längerem Tools die den Programmcode selbst analysieren ("SAST-Tools"). Enterprise-Produkte wie HP Fortify oder Checkmarx stellen nicht nur verschiedene Plug-ins zur Verfügung, mit denen sich Entwickler die Scanergebnisse in Ihrer Entwicklungs-GUI (s. Abb.3) anzeigen lassen können, sie lassen sich auch in gängige Build-Systeme wie Jenkins einbinden, um darüber Code automatisiert analysieren zu können. 

Recht jung ist dagegen eine Toolgattung, welche auch die eingebundenen 3rd-Party-Komponenten (z. B. verwendete Bibliotheken) nach Sicherheitsmängeln untersuchen kann. In einer Zeit, in der moderne Webanwendungen immer stärker auf externen Komponenten basieren, eröffnen Schwachstellen in diesen natürlich auch Angreifern neue Möglichkeiten, um darüber Anwendungen zu kompromittieren. In der Regel erfordern Security Tools jedoch stets entsprechend qualifiziertes Personal, welches diese bedienen, Findings analysieren und etwaige False Positives herausfiltern kann. Gerade an dem Punkt scheitert die Integration dieser Tools in der Praxis häufig. 

## Vorgaben

Erst durch entsprechende Sicherheitsvorgaben gewinnen Maßnahmen (welche die Vorgaben letztlich umsetzen), Tools sowie natürlich Tester (welche die Einhaltung der Vorgaben kontrollieren) erst wirklich an Bedeutung und Gewicht. Dies betrifft zum einen anwendungsübergreifende Vorgaben, z. B. in Form von Guidelines oder Standards. Wichtig ist dabei, die Umsetzbarkeit von Vorgaben durch die Entwicklung zu berücksichtigen, was sich durch konkrete Empfehlungen und Beispiele für Maßnahmen der tatsächlich dort eingesetzten Technologien (Programmiersprachen, Frameworks und APIs) erreichen lässt. Besonders hilfreich sind in diesem Zusammenhang auch konkrete Veranschaulichungen anhand von Positiv- und Negativ-Code-Beispielen: 

    
    
    // Negativ-Beispiel:  
    <h:outputText … escape=“false“ />  
      
    // Positiv-Beispiel  
    <h:outputText … />

Werden innerhalb der Entwicklung bereits Wikis (z. B. Confluence) eingesetzt, eignen sich diese sehr gut zur Dokumentation, insbesondere von Secure Coding Guidelines. Ein weiterer wichtiger Aspekt ist neben solchen implementierungsspezifischen Vorgaben auch der Bezug auf existierende übergreifende Sicherheitsvorgaben (z. B. eine IT-Security Policy). Letzteres gelingt durch einen implementierungsübergreifenden technischen Standard. Mit dem TSS-Web ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[6]](betrieb/sicherheit/sicherheit-im-software-entwicklungsprozess.html#c11825) existiert hierfür eine Vorlage speziell für Webanwendungen, die sich kostenlos verwenden und beliebig erweitern lässt. In jedem Fall sollten in Standards und Guidelines die folgenden Themen behandelt werden:

  * Datenvalidierung (Ein- und Ausgabe)
  * Registrierung von Benutzern 
  * Authentifizierung und Session Management (inkl. Identity Management)
  * Access Controls
  * Sichere Datenbehandlung und Kryptographie
  * Fehlerbehandlung
  * http-Sicherheit (Security Header etc.)

Daneben sollten in einer größeren Organisation auch konkrete architekturelle Vorgaben und Blue Prints nicht fehlen. In diesen lassen sich etwa Art und Weise von Kommunikationsbeziehungen oder die Verwendung und Anbindung bestimmter Sicherheitskomponenten wie Access Gateways oder Application Firewalls beschreiben. Auch konkrete Vorgaben an den erlaubten Technologiestack (Technologiestandards) können eine sinnvolle Maßnahme sein. Denn wie bereits weiter oben gezeigt wurde kann die Wahl einer bestimmten Technologie (z. B. ein MVC-Framework) größere Auswirkungen auf die Sicherheit einer Anwendung bzw. die Umsetzbarkeit von Sicherheitsaspekten haben. 

Neben diesen allgemeinen Vorgaben sollten grade bei größeren Projekten auch solche erstellt werden, die spezifisch zum jeweiligen Projekt (bzw. der darin entwickelten Anwendung) sind. Um diese zu identifizieren existieren schon seit einigen Jahren entsprechende Methoden zur Bedrohungsmodellierung (Threat Modeling). Darunter etwa die Analyse von Anwendungsfällen (Misuse oder Abuse Case Modellierung) sowie die von sensiblen Datenflüssen und architektureller Vertrauensbeziehungen (Trust Boundaries) der Anwendung, woraus sich dann unterschiedliche Sicherheitsmaßnahmen ableiten lassen ![Interner Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/internal_link.gif)[[7]](betrieb/sicherheit/sicherheit-im-software-entwicklungsprozess.html#c11825).

## Security Gates 

Erst durch die Einbettung in entsprechende Entwicklungs- bzw. Qualitätssicherungs-Prozesse lässt sich die tatsächliche Umsetzung von Vorgaben sicherstellen. Wichtig ist hier, kein starres Korsett vorzugeben, sondern eines, welches für alle Arten von Vorgehensmodellen, Projektgrößen und Änderungen (Changes) an produktiven Anwendungen gleichermaßen funktioniert. Ein wichtiges Mittel hierzu ist die Festlegung von flexiblen Security Gates (Sicherheitskontrollpunkten). Diese lassen sich prinzipiell als eine spezielle Form von Quality Gate sehen. Die drei folgenden Security Gates sind hierbei von besonderer Wichtigkeit:

  * Security Gate 1: Nach Spezifikation (verpflichtend)
  * Security Gate 2: Nach Abschluss des technischen Designs (optional)
  * Security Gate 3: Vor Inbetriebnahme (optional)

Der Grundgedanke ist dabei der, dass am Anfang eines Vorhabens (Änderung an einer produktiven Anwendung oder ein völlig neues Projekt) betrachtet wird, welche Sicherheitsmaßnahmen für dieses erforderlich sind, deren Umsetzung dann bei Bedarf im Rahmen von späteren Gates (2+3) geprüft wird. Soll etwa ein neues Webportal erstellt werden, dann kann hier ein IT-Sicherheitsbeauftragter im Rahmen des ersten Security Gates die Erstellung eines Sicherheitskonzepts einfordern, welches dann gemeinsam mit der Sicherheitsarchitektur in Security Gate 2 abzunehmen ist. Weiterhin lässt sich im ersten Gate etwa festlegen, dass vor der Produktivsetzung der erstellten Anwendung ein Sicherheitstest (Pentest) durch eine externe Firma durchzuführen ist, deren Ergebnisse dann wieder in Security Gate 3 abgenommen werden. 

Gleichzeitig funktionieren Security Gates aber auch im Falle von trivialen Änderungen an einer Bestandsanwendung (z. B. die Änderung einer Font-Größe). In dem Fall könnte etwa das Team selbst diese aufgrund bestimmter Kriterien als "nicht-sicherheitsrelevant" einstufen, wodurch die beiden anderen Security Gates automatisch wegfallen würden.

## Rollen und Verantwortlichkeiten

Um Sicherheit in der Softwareentwicklung zu Verankerung bedarf es somit an zahlreichen Stellen Zuständigkeiten und auch Know-how, darunter:

  * Security Architekt: Definition der Sicherheitsarchitektur (anwendungsspezifisch und anwendungsübergreifend) 
  * Security Tester: Verantwortlich für die Durchführung von Sicherheitstests
  * Security Officer: Verantwortlich für Definition von Vorgaben und Abnahme von Maßnahmen an den Security Gates
  * Security Champion: Zuständige Person innerhalb eines Projektes bzw. Teams.

Dem Security Testing kommt hierbei für die nachhaltige Verankerung von Sicherheit in der Softwareentwicklung eine gleichwohl wichtige wie schwierig intern zu besetzende Rolle zu. Denn in der Regel fehlt es hier in den meisten Unternehmen gänzlich am erforderlichen Personal bzw. Know-how, weswegen hier häufig stark auf den Einsatz von externen Experten (Pentestern) gesetzt wird. Die Möglichkeit, auch intern, zumindest einfache Sicherheitstests durchführen zu können, ist jedoch gerade bei agilen Projekten mit laufenden, potentiell sicherheitsrelevanten, Neuerungen von großer Wichtigkeit. 

Eine weitere kritische Zuständigkeit ist die innerhalb von Projekten bzw. Entwicklungsteams. Ein solcher Security Champion dient als lokaler Ansprechpartner und Multiplikator für Sicherheitsthemen, der in jedem größeren Team bzw. Projekt besetzt werden sollte.  Gewöhnlich wird diese Rolle dort durch einen Entwickler übernommen. 

## Absicherung der Plattform

Zu guter Letzt spielt natürlich auch der sichere Betrieb der Anwendung eine wichtige Rolle. Zum einen in Bezug auf die Härtung der Plattform (z. B. durch Abschaltung nicht benötigter Dienste). Aber auch durch die Aktivierung von zusätzlichen Schutzmechanismen, welche auf der Anwendungsschicht (OSI Layer 7) greifen. Hierzu gehört etwa der bereits angesprochene Betrieb von Access Gateways oder Application Firewalls. Aber auch damit verbundene Prozesse, etwa das Auswerten und Verfolgen von Angriffen auf die Anwendung und die Einleitung entsprechender Maßnahmen sollte es tatsächlich einmal zu einem Sicherheitsvorfall kommen (Security Incident Response).

## Fazit

Applikationssicherheit ist kein punktuelles, sondern ein Querschnittsthema. Insbesondere für geschäftskritische Anwendungen die noch dazu aus dem Internet verfügbar sind, ist es unumgänglich, Sicherheit im gesamten Lebenszyklus einer Anwendung, angefangen bei der Spezifikation über die eigentliche Entwicklung bis einschließlich dem Betrieb, angemessen zu  berücksichtigen. Die dort ergriffenen Maßnahmen sollten dabei dem jeweiligen Reifegrad und Sicherheitszielen einer Organisation entsprechen und stets die Dimensionen Vorgaben, Technologien, Organisation und Qualifikation gleichermaßen berücksichtigen. Die nachhaltige Verankerung von Sicherheit in der Organisation erfordert ein schrittweises Vorgehen sowie häufig ein Umdenken in verschiedenen Bereichen (angefangen beim Management) und nicht zuletzt natürlich auch entsprechende Investitionen. Kommt es allerdings aufgrund einer Schwachstelle in einer Webanwendung zu einem tatsächlichen Sicherheitsvorfall, können die dadurch entstandenen Kosten diese Investitionen schnell um ein Vielfaches übersteigen. Daher sind sie auch wirtschaftlich in vielen Fällen für Organisationen schlicht alternativlos. 

Quellen

  1. Saltzer und Schröder: ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[zentrale "Secure Design Patterns"](http://www.cs.virginia.edu/~evans/cs551/saltzer/)
  2. ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Memo from Bill Gates](http://news.microsoft.com/2012/01/11/memo-from-bill-gates/)
  3. ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Secure (Software) Development Lifecycle ](https://www.microsoft.com/en-us/sdl/)
  4. ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[opensamm.org](http://www.opensamm.org) 
  5. ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[BSIMM-Studien](http://www.bsimm.com) 
  6. ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[TSS-Web](https://www.secodis.com/tss-web/) 
  7. ![Externer Link](typo3/sysext/rtehtmlarea/htmlarea/plugins/TYPO3Browsers/img/external_link_new_window.gif)[Application Threat Modeling ](https://www.owasp.org/index.php/Application_Threat_Modeling)
