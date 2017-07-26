# Was ist eigentlich dieses GitHub?

_Captured: 2015-09-26 at 20:06 from [t3n.de](http://t3n.de/news/eigentlich-github-472886/)_

Man kennt das - als ambitionierter Internet-User stoßt man fast taglich auf Begriffe, die man schon tausendmal gelesen, bei denen man aber noch nie wirklich verstanden hat, was sich dahinter verbirgt. Oder man hat nur eine ungefahre Ahnung, worum es geht und mochte durch das eigene Halbwissen nicht unangenehm auffallen. Wir bringen Licht ins Dunkel und erklaren die Begriffe und Plattformen auf leicht verstandliche Weise. In der Vergangenheit haben wir uns bereits [reddit](http://t3n.de/news/anleitung-funktioniert-442793/) und [tumblr](http://t3n.de/news/anleitung-funktioniert-2-457561/) gewidmet. Heute erklaren wir euch, was es mit [GitHub](http://t3n.de/tag/github) auf sich hat.

## Git: Versionsverwaltung fur Software-Projekte

Sinn und die Funktion von GitHub stecken schon im zweiteiligen Namen: Git ist namlich auch der Name einer Software zur Versionsverwaltung. Und was ist das schon wieder? Ganz einfach: An einem Software-Projekt arbeiten heutzutage dank OpenSource oftmals mehrere, teilweise sogar hunderte oder tausende Entwickler. Von denen widmet sich jeder einem anderen Teil des Programms, und deren Arbeitsergebnisse mussen irgendwo zusammengefuhrt werden. Naturlich konnte jeder Entwickler seine Änderungen und Neuerungen an eine zentrale Person schicken, und diese kummert sich dann ausschließlich darum, den erhaltenen Code immer zu aktualisieren. Genau diese Tatigkeit lasst sich aber mithilfe einer Versionsverwaltung wie Git automatisieren. Und weil das so praktisch ist und gut funktioniert, finden sich inzwischen viele bekannte OpenSource-Projekte auf GitHub wieder (zum Beispiel [der Linux-Kernel ](https://github.com/torvalds/linux), [die Programmiersprache Ruby on Rails ](https://github.com/rails/rails) oder die [JavaScript-Bibliothek jQuery ](https://github.com/jquery/jquery)).

![Diese GitHub-Seite kriegt man oft präsentiert, wenn man heutzutage OpenSource-Software runterladen will. Für Nicht-Entwickler ist eigentlich nur der „Zip“-Button in der linken Ecke wichtig, damit kann die aktuelle Version des Projekts heruntergeladen werden.](http://t3n.de/news/wp-content/uploads/2013/06/github_1-595x509.jpg)

> _Diese GitHub-Seite kriegt man oft prasentiert, wenn man heutzutage OpenSource-Software runterladen will. Fur Nicht-Entwickler ist eigentlich nur der „Zip"-Button in der linken Ecke wichtig, damit kann die aktuelle Version des Projekts heruntergeladen werden._

## GitHub: Samtliche Änderungen von allen Autoren werden gespeichert

Dazu gibt es diverse Client-Applikationen fur Git, hauptsachlich in Form von Kommandozeilen-Tools. Hiermit konnen Entwickler ihre Änderungen an einem Projekt zentral einreichen, und GitHub stellt diese Änderungen ausfuhrlich auf der zugehorigen Webseite dar. Außerdem speichert Git jede Version des Software-Projekts - egal, wie groß oder klein eine Änderung ist, mit Git konnt ihr immer auf die vorherige Version zugreifen.

![GitHub visualisiert alle Änderungen verschiedener Autoren an einem OpenSource-Projekt.](http://t3n.de/news/wp-content/uploads/2013/06/github_2-595x541.jpg)

> _GitHub visualisiert alle Änderungen verschiedener Autoren an einem OpenSource-Projekt._

## „Stash mal deinen Working-Tree, sonst gibt's einen Conflict, wenn du den Dev-Branch pullst."

Viele Menschen, die mit [Entwicklung](http://t3n.de/tag/entwicklung) nichts am Hut haben und GitHub nur nutzen um dort die neuste Version einer Software runterzuladen, fuhlen sich vielleicht vom GitHub-typischen Vokabular abgeschreckt. „Stash mal deinen Working-Tree, sonst gibt's einen Conflict, wenn du den Dev-Branch pullst" - solche Satze geben einige Entwickler anscheinend tatsachlich von sich. Aber keine Angst, wir haben hier ein kleines GitHub-Worterbuch fur euch zusammengestellt:

  * **Repository**: Ein Repository (oder kurz „Repo") kann bei GitHub einfach als „Projekt" verstanden werden. Die Dateien fur ein Software-Projekt werden in einem Repository abgelegt. Der Begriff stammt aus der Linux-Welt.
  * **Branch**: Innerhalb eines Repositories kann es mehrere Versionen einer Software geben. Zum Beispiel eine experimentelle Beta-Version und eine stabile Version fur den Produktiv-Einsatz. Jede Version stellt dabei einen Branch („Ast") des Repositories dar.
  * **Commit**: „Commit" nennt sich der Vorgang, wenn eine neue Version eines Branches bei der Versionsverwaltung eingereicht wird. Das heißt, nachdem der Entwickler einen Vorgang an einer Software abgeschlossen hat, „committed" er die Änderungen.
  * **Pull beziehungsweise Pull Request**: Hat ein Entwickler einen Bug gefixt oder eine neue Funktion eingebaut, mochte er, dass seine Änderung in das ursprungliche Projekt einfließt. Deswegen stellt er einen „Pull Request" an den Administrator des jeweiligen Projekts. Dieser kann sich die Änderungen dann ansehen und entscheiden, ob er den Pull durchfuhren mochte, oder nicht.
  * **Fork**: Da alle offentlichen Git-Projekte unter OpenSource-Lizenz stehen, kann auch jeder einen eigenen Ableger eines Repositories, einen sogenannten „Fork", starten. Dort kann jeder privat vor sich hin entwickeln und seine Version am Ende wieder dem ursprunglichen Projekt zufuhren (Pull Request stellen) - oder aber einfach eine eigenstandige Variante verbreiten.

## Hub: Web-Interface, Wiki und Support-System fur Entwickler

Im zweiten Teil des Namens „Hub" steckt dann noch der Hinweis auf die Web-Fahigkeiten von GitHub. Prinzipiell ließe sich Git namlich auch komplett ohne ein Web-Interface oder zentralen Server verwenden. Aber GitHub hostet nicht nur kostenlos die OpenSource-Projekte der Entwickler, sondern reichert den Funktionsumfang von Git auch zusatzlich an. Dank grafischer Darstellung im Browser lasst sich der Entwicklungsprozess von Software-Projekten anschaulich darstellen. Außerdem kann ein Großteil der Features, zum Beispiel das „Forken" eines Projekts, auch durch einen Mausklick ausgefuhrt werden und benotigt keinen Kommandozeilen-Befehl mehr.

![Mit Community-Features, wie etwa Entwickler-Profilen wertet GitHub die technischen Funktionen des Kommandozeilentools „Git“ deutlich auf.](http://t3n.de/news/wp-content/uploads/2013/06/github_3-595x504.jpg)

> _Mit Community-Features, wie etwa Entwickler-Profilen wertet GitHub die technischen Funktionen des Kommandozeilentools „Git" deutlich auf._

Dazu gibt es noch eine ganze Portion Web 2.0 in Bezug auf Community-Features. Indem ihr einem Repository oder einem Entwickler folgt, kriegt ihr automatisch alle Updates der Person beziehungsweise des Projekts mit und konnt euch sofort die neueste Version runterladen, einsetzen oder daran mitentwickeln. Außerdem gibt es Wiki-Funktionen fur jedes Projekt sowie ein Support-System, um auftretende Probleme bei Nutzern direkt und ubersichtlich bearbeiten zu konnen.

### Weiterfuhrende Links
