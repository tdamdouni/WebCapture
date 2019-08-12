# Neue Technik findet Sicherheitslücken in Prozessoren

_Captured: 2019-03-28 at 10:02 from [www.ingenieur.de](https://www.ingenieur.de/technik/fachbereiche/ittk/neue-technik-findet-sicherheitsluecken-in-prozessoren/?utm_source=Maileon&utm_medium=email&utm_campaign=NewsletterING&utm_content=20190328)_

2018 griffen Unbekannte bestimmte Prozessoren an. Forscher der TU Kaiserslautern und der Universitat Stanford entwickelten nun eine Technik, mit der Sicherheitslucken aufgespurt werden konnen.

![Platine eines Prozessors](https://www.ingenieur.de/wp-content/uploads/2019/03/panthermedia_B10538963_1000x625_bearbeitet.jpg)

> _Prozessoren kommen in zahlreichen alltaglichen Dingen zum Einsatz - vom Smartphone bis zur Spielekonsole._

Anfang 2018 entdeckten Forscher relevante Sicherheitslucken bei bestimmten Prozessoren. Dies betraf vor allem Chiphersteller von High-End-Prozessoren, die in der Lage sind, anspruchsvolle Videoschnitte oder aufwendige Spiele effizient und moglichst storungsfrei zu verarbeiten. Ein gemeinsames Forscherteam von der Technischen Universitat Kaiserslautern (TUK) und der Universitat Stanford fand nun bei weiteren Prozessoren solche Sicherheitslucken. Gleichzeitig entwickelten sie ein Verfahren, mit dem sich diese Lucken aufspuren und schon wahrend des Entwicklungsprozesses beheben lassen.

## Architektur der Prozessoren birgt Risiken

Hauptsachlich waren - und sind es zum Teil immer noch - High-End-Prozessoren betroffen, die von großen US-amerikanischen Herstellern produziert werden. Sie sind aufwendig gebaut und genau diese komplexe Architektur macht sie anfallig fur Angriffe. Was charakterisiert diese Prozessoren? Sie setzen auf eine sogenannte „Out-of-order-execution". Das bedeutet: Der Prozessor ist so konzipiert, dass er Arbeitsschritte effizient ausfuhrt - gegebenenfalls abweichend von der Reihenfolge, die ihm der Programmierer eigentlich vorgegeben hat. Das sorgt fur eine deutliche Leistungssteigerung des Rechners. Denn es ermoglicht ihm, auf hohem Niveau mehrere Programme gleichzeitig auszufuhren.

Genau bei dieser parallelen Programmausfuhrung entstehen aber auch Nebeneffekte, die ein Angreifer ausnutzen kann. Bei den im vergangenen Jahr festgestellten Sicherheitslucken „Meltdown" und „Spectre" waren es Seitenkanale oder verdeckte Kanale, die Forscher als die verantwortlichen Schwachstellen identifizierten. Um in solche Seitenkanale eindringen zu konnen, benotigt man weder administrative Rechte, noch einen physischen Zugang zum Rechner. „Es genugt, ein Programm mit Benutzerrechten zur Ausfuhrung zu bringen", erklart Wolfgang Kunz, Leiter des Forschungsteams und Lehrstuhlinhaber fur den Entwurf Informationstechnischer Systeme an der TUK. „Man nutzt Nebeneffekte wie beispielsweise Zugriffskonflikte im Speicher, die Auswirkungen auf das zeitliche Verhalten des Programmablaufs haben. Damit kann man Ruckschlusse auf den vertraulichen Inhalt des Speichers ziehen." Vergleichbar ist dies mit der Eckkneipe: Ein Gast kommt jeden Freitag um 21 Uhr und bestellt ein Bier. Nach wenigen Wochen zapft der Wirt das Bier schon einmal an und es steht fertig vor dem Stammgast, kaum, dass er Platz genommen hat. Prozessoren nutzen Vorhersagen, um schneller arbeiten zu konnen. Angreifer kommen auf diese Art und Weise an Passworter oder verschlusselte Daten.

## Simulierter Angriff zeigt, wie Hacker an Daten gelangen

Mikrochips gehoren zu unserem taglichen Leben. Sie erleichtern es, sorgen fur Unterhaltung, schaffen Sicherheit und vernetzen uns. Sie kommen haufig in eingebetteten Systemen zum Einsatz, wo sie Überwachungs-, Steuerungs- oder Regelfunktionen ubernehmen, Daten oder Signale verarbeiten. Sie steuern technische Systeme in der Unterhaltungselektronik, Medizintechnik, Telekommunikation, Gebaude- und Produktionsautomatisierung. Zahlreiche dieser Bereiche unterliegen besonderen Sicherheitsstandards, wie beispielsweise autonomes Fahren oder das Internet der Dinge, bei dem verschiedene Gerate miteinander vernetzt sind und Daten austauschen.

Die Forscher des Teams der TUK und der Stanford Universitat fanden heraus, dass es bei anderen Prozessoren mit einfacherer Hardware-Architektur ahnliche Lucken gibt. Sie simulierten einen Angriff, bei dem sie auch hier Seitenkanale aufzeigten. Dieser von ihnen entwickelte „Orc-Angriff" leitet sich vom englischen Technikbegriff „orchestration" ab, zu deutsch Orchestrierung. Da einfache Prozessoren in vielen Anwendungen zum Einsatz kommen - vom Smartphone uber das Notebook bis zur Spielekonsole -, haben Hacker große Chancen, an vertrauliche Daten zu gelangen.

## Rechenverfahren deckt Sicherheitslucken auf

Dem Forscherteam gelang es, mit einem neuen Rechenverfahren, Sicherheitslucken zu enthullen. Sie nannten es „Unique Program Execution Checking", kurz UPEC. Anhand eines freizuganglichen „open-source" Prozessors zeigten die Forscher, dass solche kritischen Stellen leicht moglich sind. „Open-source" bedeutet, dass der Quelltext offentlich und von Dritten eingesehen, geandert und genutzt werden kann - Daten der Prozessoren sind normalerweise Betriebsgeheimnisse. Die Hersteller mussten diese Methode also selbst im Entwicklungsprozess einsetzen, um zu testen, ob es Angriffspunkte gibt oder eine Sicherheitslucke dieser Art vorhanden ist. Mit diesem fruhzeitigen Wissen konnte die Lucke noch wahrend der Entwicklung geschlossen werden.

**Lesen Sie weitere Beitrage zur IT-Sicherheit:**
