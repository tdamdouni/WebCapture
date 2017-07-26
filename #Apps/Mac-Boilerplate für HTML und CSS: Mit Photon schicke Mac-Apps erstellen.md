# Mac-Boilerplate für HTML und CSS: Mit Photon schicke Mac-Apps erstellen

_Captured: 2015-11-14 at 09:59 from [t3n.de](http://t3n.de/news/mac-boilerplate-fuer-html-css-654775/?utm_source=feedburner+t3n+News+12.000er&utm_medium=feed&utm_campaign=Feed%3A+aktuell%2Ffeeds%2Frss+%28t3n+News%29)_

Fur Smartphone- und Tablet-Applikationen gibt es eine Vielzahl an HTML- und CSS-Boilerplates, die den nativen Look einer App nachempfinden. In vergangenen Artikeln haben wir solche [HTML- und CSS-Boilerplates](http://t3n.de/news/chocolatechip-ui-html-theme-fuer-640391/) schon vorgestellt. Damit aber auch eine Desktop-Applikation fur den Mac ausieht wie eine echte Desktop-Applikation, gibt es eine Mac-Boilerplate namens Photon.

## Die Mac-Boilerplate Photon im Einsatz

![Eine Demo vom Mac-Boilerplate Photon. \(Screenshot: Photon\)](http://t3n.de/news/wp-content/uploads/2015/11/mac-boilerplate-photon-595x282.png)

> _Eine Demo vom Mac-Boilerplate Photon. (Screenshot:_

Der Aufbau und der Umgang mit Photon ist simpel. Wir konnen mit den gelieferten Assets unsere eigene Mac-Applikation visuell erstellen. Dabei kann die Entwicklungsumgebung, wie auch bei einer Webseite ublich, aus Browser und Editor bestehen. Vorzugsweise sollten wir hierbei auf den [Chromium ](https://www.chromium.org/) oder [Google Chrome ](https://www.google.de/chrome/browser/desktop/) setzen.

Bevor wir beginnen konnen, mussen wir naturlich das Photon-Paket herunterladen. Das konnen wir direkt uber das [GitHub-Repository ](https://github.com/connors/photon) oder uber die [offizielle Photon-Seite ](http://photonkit.com/getting-started/) tun. Zu empfehlen ist fur Einsteiger die Precompiled-Photon-Version. In der erhalten wir nicht nur die benotigten Assets, sondern auch direkt eine vorgefertigte Projektstruktur fur unsere App.

Jetzt konnen wir beginnen, unsere App zu fullen. Über die index.html-Datei konnen wir die grundsatzliche Struktur bearbeiten und verandern. Da Photon eine fertige CSS-Datei mit vielen Mac-Styles liefert, konnen wir uns frei bedienen und unsere Elemente mit Klassen und IDs bestucken. Damit wir einen Überblick uber die Moglichkeiten der Komponenten erhalten, konnen wir einen Blick auf die [Components-Seite ](http://photonkit.com/components/) werfen.

Wollen wir beispielsweise einen Mac-typischen Header und Footer setzen, reichen schon folgende Zeilen:
    
          1. <headerclass="toolbar toolbar-header">
      2. <h1class="title">Header</h1>
      3. <footerclass="toolbar toolbar-footer">
      4. <h1class="title">Footer</h1>

Über die Klassen wird der Style aus der mitgelieferten CSS-Datei zugeordnet. Grundsatzlich gibt es im Erstellungsprozess keinen Unterschied zu einer normalen Webseite.

## Die Mac-Boilerplate Photon verpacken

Haben wir unser Projekt abgeschlossen und mit unseren Funktionalitaten gefullt, konnen wir aus diesem Projekt eine fertige App erstellen. Die einfachste Moglichkeit ist, sie als Web-App auf einem Server bereitzustellen und mit [Fluid ](http://fluidapp.com/) als Desktop-Anwendung zu benutzen. Naturlich konnen wir auch das Xcode-Projekt [MacGap ](https://macgapproject.github.io/) benutzen, um unsere App in einen nativen Container einzubetten.

Die wohl beste, aber auch anspruchsvollste, Losung ist sicherlich, [Electron ](http://electron.atom.io/) von GitHub einzusetzen. Auch der Atom-Editor oder der Slack-Client basieren auf dieser Engine. Mit ihr lassen sich unsere HTML-, CSS- und JavaScript-Dateien in einen Container verpacken, der auf [Chromium ](https://www.chromium.org/) und [Node.js ](https://nodejs.org/en/) setzt. Damit wird auch ermoglicht, dass Node.js-Module eingebettet werden konnen und unsere Applikation funktionell auf ein ganz neues Level gehoben werden kann. Der Export einer solchen App kann zugleich fur Mac, Windows und Linux erfolgen.

**Habt ihr auch schon Desktop-Applikationen mit Web-Technologien entwickelt?**

Bleibe immer up-to-date. Sichere dir deinen Wissensvorsprung!
