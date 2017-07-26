# Web-Notifications für deine Webseite: Das kann die JavaScript-Library notie.js

_Captured: 2015-11-28 at 19:47 from [t3n.de](http://t3n.de/news/web-notifications-mit-notiejs-659803/?utm_source=feedburner+t3n+News+12.000er&utm_medium=feed&utm_campaign=Feed%3A+aktuell%2Ffeeds%2Frss+%28t3n+News%29)_

Mit Web-Notifications haben wir die Moglichkeit, den Nutzer an einer zentralen Stelle uber diverse Dinge zu informieren. Das immer gleichbleibende Verhaltensmuster einer solchen Web-Notification lasst solche Web-Applikationen transparenter wirken. Egal ob Trello, Wunderlist oder Evernote, alle verwenden Web-Notifications, um Nutzer auf ein Ereignis aufmerksam zu machen.

## Eigene Web-Notifications mit notie.js erstellt

![notie-web-notifications-demo](http://t3n.de/news/wp-content/uploads/2015/11/notie-web-notifications-demo-595x256.gif)

> _Klick auf das Bild fur eine Web-Notifications-Demo! (Gif: notie.js )_

notie.js ist eine JavaScript-Library die keine Abhangigkeiten benotigt. Es spielt keine Rolle, ob wir mit jQuery oder MooTools arbeiten. Auch mussen wir zuvor keine HTML-Elemente anlegen, in denen die Web-Notifications ausgefuhrt werden konnen. Wir konnen direkt vom [offiziellen GitHub-Repository ](https://github.com/jaredreich/notie.js/) die notie.js-Datei runterladen und in unsere Seite einbetten
    
          1. <scriptsrc="notie.js"></script>

Alle [Einstellungen ](https://github.com/jaredreich/notie.js/#options) zu Farben, IDs und Großen konnen direkt in der notie.js bearbeitet werden. Da die Web-Notifications keinen zuvor angelegten HTML-Container benotigen, konnen wir sie direkt mit JavaScript steuern. Sobald wir die Datei eingebettet haben, konnen wir auf eine Reihe von [Funktionen ](https://github.com/jaredreich/notie.js/#usage) zugreifen. Insgesamt gibt es drei Typen von Web-Notifications: alert, confirm und input.
    
          1. notie.alert(style_number,'message', time_in_seconds);
      2. notie.confirm('Title text','Yes button text','No button text', yes_callback)
      3. notie.input('Title text','Submit button text','Cancel button text','type','placeholder', submit_callback,'Optional pre-filled value');

Alert stellt eine einfache Benachrichtigung dar, Confirm lasst uns eine Ja-/Nein-Abfrage erstellen und mit Input konnen wir auch auf eine Eingabe reagieren. Die Funktionsweise ist ahnlich wie bei den veralteten Alert()- und Confirm()-Funktionen, nur dass wir hier keine PopUps bekommen, sondern hubsche Web-Notifications, die am oberen Rand erscheinen. Alle weiteren Optionen konnt ihr in der [README.md ](https://github.com/jaredreich/notie.js/#usage) nachlesen.

## Wieso notie.js die richtige Library fur eure Web-Notifications ist?

[Notie.js ](https://jaredreich.com/projects/notie.js/) uberzeugt durch die Einfachheit der Integration und der Benutzung. Wir mussen keine Assets, CSS-Dateien oder andere Abhangigkeiten bereitstellen. Es genugt ausschließlich eine JavaScript-Datei. Zudem benotigen wir auch keine Veranderung unserer aktuellen HTML-Struktur. Notie.js ist vollstandig modular aufgebaut und lasst sich problemlos auch spater integrieren. Alle Inhalte und Benachrichtigungen werden uber die JavaScript-Funktion ubergeben. Das Erscheinungsbild kann individuell uber die eigene CSS-Datei angepasst werden.

Erhalten wir ein automatischen Success-Callback von einer Ajax-Anfrage? Dann mussen wir nur noch den Response mit einem notie.js-Alert ausfuhren und erhalten direkt ein visuelles Feedback. Sicher auch praktisch in der Entwicklung, wenn ein QA-Testing bevorsteht.

**Was haltet ihr von Web-Notifications?**

Windows 10 wird bald eines der meist genutzten Betriebssysteme sein. Der neue Standardbrowser in Windows heißt Microsoft Edge. Er gehort deshalb kunftig in jede Testmatrix. Wie kannst Du Deine Webprojekte schon heute mit Mac, Linux oder Windows fur Egde testen?  
[Hier erfahrst Du mehr](http://guruads.de/api/click/5640cda9497959d33100000b)
