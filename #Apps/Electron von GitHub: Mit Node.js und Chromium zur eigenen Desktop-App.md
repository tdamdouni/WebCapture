# Electron von GitHub: Mit Node.js und Chromium zur eigenen Desktop-App

_Captured: 2015-11-15 at 16:31 from [t3n.de](http://t3n.de/news/electron-github-nodejs-chromium-656328/?utm_source=feedburner+t3n+News+12.000er&utm_medium=feed&utm_campaign=Feed%3A+aktuell%2Ffeeds%2Frss+%28t3n+News%29)_

Electron setzt auf Node.js und Chromium. Die Inhalte einer damit erstellten App bestehen aus HTML, CSS und JavaScript. Zusatzliche Node.js-Module werden direkt in der Applikation hinterlegt und ausgeliefert. Wir konnen mit Electron Cross-Device-Applikation erstellen, sprich: Es ist egal, ob wir mit Windows, Mac oder Linux arbeiten.

## Electron von Github auf den Zahn fuhlen

Da Electron von Github auf allen Betriebssystemen lauft, bietet es nicht nur eine Schnittstelle fur die Entwicklung von Desktop-Applikationen mit Web-Technologien, wir konnen unsere erstellte Applikation auch auf mehreren Systemen ausliefern. Das spart nicht nur Zeit, sondern auch viel Geld in der Entwicklung. Das Know-how muss nicht mehr fur unterschiedliche Systeme und Sprachen erworben, sondern kann fokussiert werden.

Electron von Github ist Open Source und kann kostenfrei auch fur kommerzielle Projekte genutzt werden. Es bietet zusatzlich Schnittstellen zur System-Hardware, Crash-Reportings, Live-Updates, Windows-Installer und Debugging. Naturlich konnen alle Projekte auch mit Node.js-Modulen erweitert und angepasst werden.

![Der Showroom von Electron \(Screenshot: Electron\)](http://t3n.de/news/wp-content/uploads/2015/11/electron-von-github-showroom.png)

> _Der Showroom von Electron (Screenshot:_

Electron von Github wurde initial fur den eigenen [Atom-Editor](http://t3n.de/news/atom-github-t3n-test-536855/) entwickelt. Die Engine Electron wurde dann weiterentwickelt und Open Source fur Entwickler bereitgestellt. Schon nennenswerte [Unternehmen und Applikationen ](http://electron.atom.io/#built-on-electron) setzen auf Electron - unter anderem Facebook, Microsoft, Slack und Docker.

## Aufbau unserer "Hello-World"-Applikation mit Electron von Github

Damit wir Electron von Github benutzen konnen, mussen wir auf unserem System zuerst [Git ](https://git-scm.com/) und [Node.js ](https://nodejs.org/en/) installieren. Dann konnen wir mit dem [Electron-Quick-Start-Projekt ](https://github.com/atom/electron-quick-start) beginnen. Über folgende Terminal-Befehle laden wir das Repository runter, installieren alle Abhangigkeiten und starten das Projekt.
    
          1. #Clonethis repository
      2. $ git clone https://github.com/atom/electron-quick-start
      3. #Go into the repository
      4. $ cd electron-quick-start
      5. #Install dependencies and run the app
      6. $ npm install && npm start

Sobald wir die Befehle ausgefuhrt haben, startet die App automatisch. Der Quellcode, der hier ausgefuhrt wird, besteht immer aus einer `index.html`, `main.js` und `package.json`. Die `index.html` beinhaltet den Content, die `main.js` liefert die JavaScript-Logik und die `package.json` hinterlegt alle wichtigen Eckdaten zu der App.

![Die erstellte Hello-World-Electron-App \(Screenshot: Electron\)](http://t3n.de/news/wp-content/uploads/2015/11/electron-hello-world-595x446.png)

> _Die erstellte Hello-World-Electron-App (Screenshot: Electron)_

Automatisch offnen sich auch die Chromium-Developer-Tools. Das ist kein Fehler, sondern wurde in der `main.js` programmiert. Ein kurzer Blick in die Datei gibt uns folgenden Befehl: `mainWindow.webContents.openDevTools();` Sollte das nicht gewunscht sein, loschen wir diese Funktion und starten unsere App erneut mit `npm start`.

Wollen wir jetzt unsere App ausliefern und als Standalone-App benutzen, mussen wir uns zum Ordner `electron-quick-start/node_modules/electron-prebuilt/dist` navigieren. Hier finden wir eine fertige Elektron-Applikation. Starten wir sie, erhalten wir allerdings die Default-App. Damit jetzt unserer Content angezeigt wird, lassen wir uns den Inhalt dieser App anzeigen und navigieren uns zu `/Contents/Resources/`. Hier erstellen wir einen neuen Ordner namens „app" und kopieren unsere`index.html`, `main.js` und `package.json `hinein. Unsere App kann jetzt an einen belieben Ort kopiert und gestartet werden.

Welche Schnittstellen, Distributions-Moglichkeiten und weitere Funktionen es gibt, konnt ihr in der [offiziellen Dokumentation ](http://electron.atom.io/docs/v0.34.0/) nachschlagen. Viel Erfolg bei der ersten Desktop-Applikation!

**Konnt ihr euch auch vorstellen, Applikationen fur den Desktop zu erstellen oder bleibt ihr lieber dem Web treu? Und habt ihr schon unseren Artikel „[Mac-Boilerplate fur HTML und CSS: Mit Photon schicke Mac-Apps erstellen](http://t3n.de/news/mac-boilerplate-fuer-html-css-654775/)" gelesen?**
