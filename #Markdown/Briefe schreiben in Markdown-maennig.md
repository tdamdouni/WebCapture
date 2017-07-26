# Briefe schreiben in Markdown

_Captured: 2016-12-16 at 00:51 from [maennig.de](http://maennig.de/briefe-markdown)_

![](http://maennig.de/wp-content/uploads/2013/10/briefeheader.jpg)

Briefe. Erinnert sich noch jemand? Das waren die personlichen oder geschaftlichen Nachrichten, die man auf _Papier_ genannten, optische Datentragern in ebenfalls aus Zell- oder Holzstoffen gefertigten Hullen versandte. Und man glaubt es kaum: Auch heute noch ist es scheinbar so dann und wann unvermeidlich, sich dieses anachronistischen Mediums zur Weitergabe von Informationen zu bedienen. Dies ist dann auch meist der einzige Grund innerhalb eines langeren Zeitraums, sich an ein Hilfsmittel namens _Word_ oder _Pages_ zu erinnern, mit dem man bekanntermaßen einen Brief halbwegs vernunftig aufs Papier zu bringen vermag.

Aber halt, sollte nicht selbst eine derart exotische Aufgabe mit dem Allzweckmittel _Markdown_ zu losen sein, das im dritten Jahrtausend unter Pragmatikern fur ballastfreies Handling von Texten sorgt? In der Tat: Selbst mit uberschaubaren Kenntnissen in CSS und mit einem weiteren Softwaretool, das sich vermutlich ohnehin auf der Festplatte jedes Markdownfreunds befindet, ist es relativ einfach machbar, einen eng an die Standards der [DIN 5008](http://de.wikipedia.org/wiki/DIN_5008) angelehnten Brief vorzubereiten und auszudrucken. Und ist das entsprechende Stylesheet erst einmal eingerichtet, dann gehen Briefe mit dem Lieblings-Texteditor außerst flink von der Hand.

Beim gerade erwahnten, unverzichtbaren Softwaretool handelt es sich naturlich um Brett Terpstras Markdownvorschau- und -exportprogramm [Marked](http://marked2app.com/), das vor wenigen Tagen in zweiter, erheblich verbesserter Auflage erschienen ist. Die mehrfach upgedatete Urversion der App ist nach wie vor fur 3,59 Euro [im Mac App Store](https://itunes.apple.com/de/app/marked/id448925439?ls=1&mt=12) zu haben. Wer sich jedoch von den Einschrankungen durch Apples _Sandboxing_ befreien und die zahlreichenn neue Funktionen nutzen mochte, dem wird es um die 9,99 Euro, die fur Marked 2 zu berappen sind, sicherlich nicht schade sein. Eine gute Gelegenheit, um sich bei einem Entwickler zu bedanken, der zahlreiche nutzliche Scripts und Apps [kostenlos zur Verfugung stellt](http://brettterpstra.com/projects/), ist der Kauf von Marked 2 obendrein.

Doch zuruck zum Schreiben von Briefen mit Markdown. Da Marked seit jeher als _editor agnostic_ firmiert, ist es freilich egal, mit welchem Texteditor man selbst seine Texte tippen mag. Meine erste Wahl ist schon seit einiger Zeit [FoldingText](http://www.foldingtext.com/), doch jeder andere Editor, der idealerweise das _code highlighting_ fur Markdown beherrscht, funktioniert naturlich ebenso. Damit fokussiert sich die Problematik des Briefeschreibens schnell darauf, das erforderliche Stylesheet so zu gestalten, dass Marked auf dessen Basis die bestmogliche PDF-Daten zur Übergabe an einen beliebigen Drucker generieren kann.

**_Kurzanleitung fur Profis:_**  
_Die [CSS-Datei](http://cricetus.com/brief.css) herunterladen, gegebenenfalls anpassen, an einer sicheren Stelle der Festplatte speichern und unter_ Preferences - Style - Custom CSS _in Marked einfugen. [Muster-Briefkopf](http://maennig.de/wp-content/uploads/2013/10/briefkopf.txt) herunterladen, mit den eigenen Daten versehen und als Textbaustein ablegen. Fertig geschriebene Briefe in Marked offnen und einfach ausdrucken oder als PDF-Datei speichern._

Freilich sind die Anspruche an einen Brief zunachst einmal ganz andere als an eine HTML-Datei, zu deren Erstellung Markdown ja eigentlich entwickelt wurde. Da aber typische Strukturelemente wie die Überschriftformate `<h1>` bis `<h6>`, in Markdown also `#` bis `######`, in Briefen nur selten benotigt werden, liegt es nahe, diese fur die ublichen und erforderlichen Brieftextelemente zu missbrauchen. Dazu gehoren beispielsweise der Briefkopf mit ein bis zwei verschiedenen Schriftgroßen oder -typen, die Absenderzeile im Adressfenster, die Betreffzeile, auf Mittelachse oder rechtsbundig gesetzter Text und naturlich auch der ganz gewohnliche, linksbundige Flattersatz.

Obwohl der Gedanke nahe liegt, einen Briefkopf einfach als Grafik in ein Dokument einzufugen, sprechen dennoch mehrere Punkte gegen dieses Vorgehen. Zum einen lasst die Qualitat ordentlich gerenderter Fonts mit einer auch noch so guten Grafik nur schwer erreichen. Erstellt man mit dem neuen Markdown-Workflow nicht nur gedruckte Briefe, sondern auch PDF-Dateien, die beispielsweise per E-Mail verschickt werden, dann werden diese Dateien mit eingebetteten Grafiken erheblich großer als mit reinen Texten als Inhalt. Überdies sind sie naturlich beim Empfanger nur noch eingeschrankt durchsuchbar, da der Informationsgehalt grafischer Briefkopfe den Algorithmen von Spotlight & Co. naturlich verborgen bleibt.

Die [kompakte CSS-Datei fur Marked 2](http://cricetus.com/brief.css) sieht daher nach einigen Formatierungsexperimenten so aus:
    
    
    body {
        margin:0;
    }
    

Seitenrander gemaß DIN 5008, diese setzen die Margin-Einstellungen 0-0-0-0 unter _Preferences - Printing_ in Marked 2 voraus:
    
    
    #wrapper {
        margin-top: 0.6cm;
        margin-bottom: 2cm;
        margin-left: 2.4cm !important;
        margin-right: 2.5cm
    }
    

Als Standardfont wird hier eine Officina Sans Book in 10 Punkt verwendet:
    
    
    body {
        font-family: "OfficinaSanITCBoo";
        font-size: 10pt
    }
    

Fur Überschriften `h1` und `h2` kommt ein fetter Schriftschnitt zum Einsatz:
    
    
    h1 {
        font-family: "OfficinaSanITCBol";
        font-size: 10pt;
        font-weight: normal;
        margin-bottom: 10pt;
    }
    
    h2 {
        font-family: "OfficinaSanITCBol";
        font-size: 10pt;
        font-weight: normal;
        margin-bottom: 10pt
    }
    

`h3` bzw. `###` wird verwendet, um Textblocke bedarfsweise zentriert zu setzen:
    
    
    h3 {
        text-align: center;
        font-size: 10pt;
        font-weight: normal
    }
    

`h4` bzw. `####` wird verwendet, um Textblocke bedarfsweise rechtsbundig zu setzen:
    
    
    h4 {
        text-align: right;
        font-size: 10pt;
        font-weight: normal
    }
    

`h5` (`#####`) und `h6` (`######`) werden eingesetzt, um den Briefkopf in zwei verschiednen Schriftgroßen in einer Rotis Sans Serif zu gestalten:
    
    
    h5 {
        font-family: "RotisSansSerif";
        font-size: 18pt;
        font-weight: normal;
        margin-top: 0;
        margin-bottom: 12pt
    }
    
    h6 {
        font-family: "RotisSansSerif";
        font-size: 8pt;
        font-weight: normal;
        margin-top: 4pt;
        margin-bottom: 0
    }
    

Fetter Text wird im Bold-Schriftschnitt …
    
    
    strong {
        font-family: "OfficinaSanITCBol"
    }
    

… kursiver in Italic umgesetzt:
    
    
    em {
        font-family: "OfficinaSanITCBooIta"
    }
    

Listen werden um 20 Punkt eingeruckt:
    
    
    ul, ol {
        padding-left: 20pt
    }
    

Zitate werden um 20 Punkt eingeruckt und kursiv gesetzt:
    
    
    blockquote {
        margin-left: 20pt;
        font-family: "OfficinaSanITCBooIta"
    }
    

Um die Features dieses Stylesheets optimal zu nutzen, wird ein in Markdown geschriebener Brief beispielsweise so erstellt:
    
    
    ##### Adrian Muck-Bruggenau
    ###### Talbrugger Straße 28 | 75622 Scholberach
    ###### Telefon 07828 472890 | mobil 0167 3428876 | E-Mail amuckb@t-online.de
    <br/><br/>
    ###### Muck-Bruggenau | Talbrugger Straße 28 | 75622 Scholberach  
    <br/>
    Rezeptor GmbH
    Herrn Lothar Leser
    Heilmannstraße 30  
    82049 Pullach
    <br/>
    <br/>
    1. Oktober 2013
    <br/>
    **Verzicht auf übliche Inhalte**
    <br/>
    Sehr geehrter Herr Leser,
    
    Sie lesen Verse, die nichts weniger vorhaben, als auf die Sprache zu verzichten. Dada Johann Fuchsgang Goethe. Dada Stendhal. Dada Buddha, Dalai Lama, Dada m'dada, Dada m'dada, Dada mhm' dada. Auf die Verbindung kommt es an, und dass sie vorher ein bisschen unterbrochen wird. Ich will keine Worte, die andere erfunden haben. Alle Worte haben andere erfunden. Ich will meinen eigenen Unfug, und Vokale und Konsonanten dazu, die ihm entsprechen. Wenn eine Schwingung sieben Ellen lang ist, will ich füglich Worte dazu, die sieben Ellen lang sind. Die Worte des Herrn Schulze haben nur zweieinhalb Zentimeter.
    
    Da kann man nun so recht sehen, wie die artikulierte Sprache entsteht. Ich lasse die Laute ganz einfach fallen. Worte tauchen auf, Schultern von Worten; Beine, Arme, Hände von Worten. Ay, oi, u. Man soll nicht zuviel Worte aufkommen lassen. Ein Vers ist die Gelegenheit, möglichst ohne Worte und ohne die Sprache auszukommen. Diese vermaledeite Sprache, an der Schmutz klebt wie von Maklerhänden, die die Münzen abgegriffen haben. Das Wort will ich haben, wo es aufhört und wo es anfängt.
    
    Jede Sache hat ihr Wort; da ist das Wort selber zur Sache geworden. Warum kann der Baum nicht Pluplusch heissen, und Pluplubasch, wenn es geregnet hat? Und warum muss er überhaupt etwas heissen? Müssen wir denn überall unseren Mund dran hängen? Das Wort, das Wort, das Weh gerade an diesem Ort, das Wort, meine Herren, ist eine öffentliche Angelegenheit ersten Ranges.
    
    Mit freundlichen Grüßen
    <br/><br/>
    Adrian Muck-Bruggenau
    
    **Anlage**�
    

Man sieht: Ganz ohne HTML kommt man leider nicht aus, da Markdown mehrere, aufeinanderfolgende Leerzeilen systembedingt leider ignoriert. Hier mussen also fallweise `<br/>`-Tags eingesetzt werden. Mit dieser kleinen Einschrankung ist das Briefeschreiben mit dieser Technik aber wieder genau so schon einfach, wie es Anno Tobak mit der Schreibmaschine war. Es empfiehlt sich naturlich, den immer wieder benotigten Briefkopf als Textbaustein abzulegen. Wird die Absenderzeile fur den Fensterumschlag nicht benotigt, so kann man sie einfach durch `######&nbsp;` ersetzen, um die gestalterische Nahe zur Norm zu erhalten. Ebenso lasst sich naturlich eine Grafik mit einer Unterschrift nach der Grußformel integrieren, sofern man eine PDF-Datei generieren mochte. Per Knopfdruck generiert Marked aus der Textdatei einen schlichten und zweckmaßigen Brief:

![Musterbrief klein](http://maennig.de/wp-content/uploads/2013/10/musterbrief_klein.jpg)

(Hier als [PDF-Datei](http://maennig.de/wp-content/uploads/2013/10/musterbrief.pdf))

Selbstverstandlich sind mehrseitige Briefe mit Seitenumbruchen ebenso moglich. Marked unterstutzt ja sowohl die optionale Verwendung des `<hr>`-Tags (`***` oder `\---` in Markdown) als Seitenumbruch-Indikator als auch eine proprietare Syntax mit `<!--BREAK-->`. Fur mehrseitige Briefe sollte man sich naturlich ebenfalls einen Textbaustein abspeichern, der den Seitenumbruch und bei Bedarf einen reduzierten Briefkopf fur die Folgeseiten beinhaltet.

Klar: Fur Menschen, die sich bisher noch nicht mit Markdown beschaftigt haben, wird sich der Charme der hier beschriebenen Methode kaum erschließen. Wer aber ohnehin uber flinke und nervensparende Markdown-Workflows verfugt, dem eroffnet sich die Moglichkeit, auch das Tippen anachronistischer Briefe ganz simpel und nebenbei in diesen Prozessen mitlaufen zu lassen. So lasst sich das Starten klassischer Textverarbeitungs-Monster wie Word oder Pages einsparen - und gleichzeitig darf man sich daruber freuen, seine Briefkorrespondenz im außerst kompakten und zukunftssicheren Textformat archivieren zu konnen.  
​

_Über Erfahrungsberichte, Tipps und Verbesserungsvorschlage freue ich mich naturlich jederzeit!_
