# 15 Tipps für das perfekte Google-Analytics-Setup

_Captured: 2015-10-06 at 11:56 from [t3n.de](http://t3n.de/news/google-analytics-tipps-595562/?utm_content=buffer37cda&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

## 15 einfache Google-Analytics-Tipps

Google Analytics ist [laut BuiltWith ](http://trends.builtwith.com/analytics/Google-Analytics) auf uber 50 Prozent der Top-10.000-Websites im Einsatz. Doch trotz der hilfreichen Community und unzahligen Anleitungen nutzen viele Marketer nur einen Bruchteil der Moglichkeiten. Dabei lasst sich der Einsatz von Analytics schon mit einfachen Mitteln optimieren. Wie das geht, zeigt dieser Artikel.

### 1\. Nutze den Google-Tag-Manager

Der von Google kostenlos angebotene „Tag Manager" erleichtert Nutzern ohne technischen Hintergrund das Tracking mit Analytics. Anstatt bei jedem einzelnen Button in den Quellcode einzusteigen, richten Nutzer seitenubergreifende Falle und Regeln ein. In wenigen Schritten lassen sich damit beispielsweise samtliche Klicks auf externe Links erfassen.

Der initiale Aufwand lohnt, wenn regelmaßig neue Elemente einer Website erfasst werden. Bei weitgehend statischen Installationen von Analytics konnen Seitenbetreiber auf den Tag-Manager verzichten.

Fur die ersten Schritte mit dem Tag-Manager bietet Google eine [verstandliche Anleitung ](http://www.google.de/tagmanager/get-started.html). Wer kein Verstandnis fur Quellcode und die Architektur der eigenen Website hat, sollte fur das Einrichten des Tag-Managers einen Entwickler hinzuziehen.

### 2\. Verbinde Google Analytics mit deinem Webmaster- und AdWords-Konto

Wer neben Google Analytics auch Google-AdWords und die Webmaster-Tools nutzt, sollte sie miteinander verknupfen. Die Webdienste tauschen dann Informationen aus, die bei der Analyse der Website helfen. AdWords liefert beispielsweie Daten zu laufenden Kampagnen, die Webmaster-Tools zu relevanten Keywords.

Google Analytics versteckt die Integration hinter dem Menupunkt „Verwalten" auf Ebene der „Property" und dem Unterpunkt „Verknupfungen mit Produkten". Neben den schon genannten Diensten bietet Google Analytics dort auch die Integration von AdSense, DoubleClick und BigQuery.

### 3\. Erstelle dir ein „Analytics-Backup"

![Das Analytics-Backup von t3n.de. \(Screenshot: t3n/ Google Analytics\)](http://t3n.de/news/wp-content/uploads/2015/02/google-analytics-tipps-2-230x138.jpg)

> _Das Analytics-Backup von t3n.de. (Screenshot: t3n/ Google Analytics)_

Niemand ist fehlerfrei, auch Analytics braucht deshalb ein sicheres „Backup". Marketer sollten hierfur eine Datenansicht erstellen, die nur zum Sammeln der Rohdaten dient. Geht irgendwo irgendetwas schief und hinterlasst irreparable Schaden an den gesammelten Daten, dient sie als Backup.

Je fruher, desto besser. Wer seine Rohdaten aktuell nicht in einer eigenen Datenansicht speichert, sollte das dringend nachholen. Nutzer mussen unter dem Menupunkt „Verwaltung" nur eine „Neue Ansicht erstellen" und mit einem pragnanten Namen versehen. Mehr ist nicht notig - und in diesem speziellen Fall sogar schadlich!

### 4\. Richte die Site-Search ein

Die auf einer Website verwendeten Suchterme liefern Marketern haufig Informationen zu schlecht erreichbaren oder schlichtweg fehlenden Inhalten - vorausgesetzt, sie lassen sich einfach auswerten. Damit das moglich ist, mussen Nutzer die Seitensuche einmalig unter „Verwalten" > „Datenansicht" > „Einstellungen der Datenansicht" einrichten. Eine Anleitung hierfur [liefert Google ](https://support.google.com/analytics/answer/2819948?hl=de) selbst.

### 5\. Setze einen Filter auf interne Abrufe

Bei kleineren Seiten konnen interne Aufrufe die Zahlen verfalschen und ein unsauberes Bild der Besucher zeichnen. Es lohnt sich deshalb, die vom eigenen Unternehmen verwendeten IP-Adressen vom Tracking auszuschließen. Nutzer konnen hierfur Filter auf Ebene der „Datenansicht" erstellen. Auch hier liefert Google die [passende Anleitung ](https://support.google.com/analytics/answer/1034840?hl=de).

### 6\. Aktiviere die Demografie- und Interessens-Berichte

Google Analytics stellt Marketern uber das Google Display-Netzwerk zusatzliche Informationen zur Demografie und den Interessen der Besucher zur Verfugung. Sie sind unter „Zielgruppe" > „Demografische Merkmale" verfugbar, mussen aber aktiviert werden.

![Hier aktivierst du das zusätzliche Tracking von Nutzerdaten. \(Screenshot: google.com/ Google Analytics\)](http://t3n.de/news/wp-content/uploads/2015/02/google-analytics-tipps-1-595x320.jpg)

> _Hier aktivierst du das zusatzliche Tracking von Nutzerdaten. (Screenshot: google.com/ Google Analytics)_

Das Aktivieren dieser zusatzlichen Funktion ist in zwei einfachen Schritten erledigt: dem Aktivieren der „Funktionen fur Werbetreibende" unter „Verwalten" > „Property-Einstellungen" sowie dem Akivieren des Berichts unter „Zielgruppe" > „Demografische Merkmale" > „Übersicht".

Deutsche Datenschutzrichtlinien erfordern hierzulande daruber hinaus aber auch eine angepasste Datenschutzerklarung. Die Webagentur lunapark liefert hierzu [weitere Informationen ](http://www.luna-park.de/blog/9012-google-analytics-demografische-merkmale/).

### 7\. Events, die Basis deines Erfolgs

Wenn Nutzer eine vom Ladevorgang der Website unabhangige Aktion tatigen, nutzt du zum Erfassen sogenannte „Events" (dt. Ereignisse). Sie senden per JavaScript kurze Statusmeldungen an Analytics, die dort erfasst und gespeichert werden. Notig ist das beispielsweise beim Klicken auf Buttons oder dem Absenden von Formularen.

Um bei großeren Websites nicht den Überblick zu verlieren, solltest du Events in Kategorien sortieren. Auf zweiter, dritter und vierter Ebene kannst du jedem Event daruber hinaus sogenannte „Aktionen", „Labels" und „Werte" zuweisen. Wie das funktioniert, erklart [der Hilfebereich ](https://support.google.com/analytics/answer/1033068?hl=de) von Google Analytics.

  


### 8\. Tracke Social Shares auf deiner Website

Soziale Netzwerke sind fur viele Websites - darunter auch t3n.de - eine der wichtigsten Besucherquellen. Es lohnt sich deshalb, die sozialen Interaktionen der Besucher einer Website zu erfassen. Gemeint sind insbesondere Likes, Shares und Tweets. Je nach Zielgruppe sind aber auch andere Netzwerke wie beispielsweise Xing relevant.

Soziale Interaktionen werden in Google Analytics nicht mit sogenannten „Ereignissen" erfasst. Der Webdienst setzt stattdessen auf eine angepasste Losung, bei der das jeweilige Netzwerk (beispielsweise „Facebook") und die konkrete Handlung (beispielsweise „Share") definiert werden. Spater konnen Nutzer in Analytics nicht nur auf Interaktionen eines bestimmten Netzwerks filtern, sondern auch auf Handlungen.

Google liefert eine Anleitung zur Integration der „[Social Analytics" ](https://developers.google.com/analytics/devguides/collection/gajs/gaTrackingSocial). Wer schon den Tag-Manager nutzt, kann allerdings auch damit arbeiten. Eine Anleitung hierfur liefert Analytics-Experte [Simo Ahava ](http://www.simoahava.com/analytics/google-tag-manager-track-social-interactions/).

### 9\. Tracke Fehlerseiten

Fehlerseiten sind ein Anzeichen fur kaputte Links oder technische Fehler, die dringend behoben werden sollten. Es hilft deshalb, sie fruhzeitig zu erkennen. Marketern gelingt dies mit Zielen und Alerts.

Ziele helfen, die Ursachen der Fehlerseiten zu erkennen; Alerts garantieren, dass eine schnelle Reaktion erfolgt. Wie sie erstellt werden konnen, erklart Analytics-Advocate Daniel Waisberg [im „Google Analytics"-Blog ](http://analytics.blogspot.de/2013/09/monitoring-analyzing-error-pages–404s.html).

### 10\. Definiere Tracking-Ziele

Eines der zentralen Features von Google Analytics ist das Tracking von „Zielen". Ein solches Ziel lasst sich von Nutzern beliebig definieren, kann also der Aufruf einer bestimmten Seite (beispielsweise einer Danke-Seite) oder das Ausfullen eines Formulars (beispielsweise das Newsletter-Formular) sein.

Google Analytics bietet beim Erstellen der Ziele mehrere Vorlagen fur bestimmte Szenarien wie beispielsweise die Registration oder Kontaktaufnahme. Zusatzlich konnen Nutzer benutzerdefinierte Ziele entwerfen. Als Kriterien der Zielerreichung dienen verschiedene Szenarien, in den meisten Fallen handelt es sich um den Aufruf einer Seite.

Beim Erstellen der in Analytics erfassten Ziele sollten Nutzer das ubergeordnete Ziel der Website im Blick behalten. Eine Website, die Umsatz uber Werbung generiert, hat in Analytics andere Ziele, als eine Website, die zum Verkauf von Produkten dient.

![Der Sales Funnel eines in Google Analytics angelegten Ziels. \(Screenshot: Kissmetrics/ Google Analytics\)](http://t3n.de/news/wp-content/uploads/2015/02/google-analytics-tipps-3-595x530.jpg)

> _Der Sales Funnel eines in Google Analytics angelegten Ziels. (Screenshot: Kissmetrics/ Google Analytics)_

Wenn ein Ziel aus mehreren Schritten besteht, beispielsweise dem Aufruf mehrerer aufeinanderfolgender Seiten, konnen Marketer die Ziele detaillierter im Sales-Funnel analysieren. Google Analytics bietet hierfur unter „Berichte" > „Conversions" > „Zielvorhaben" > „Trichter-Visualisierung" eine grafische Darstellung.

### 11\. Behalte dank Vermerken den Überblick

Wer taglich an seiner Seite arbeitet, kennt alle technischen und vertrieblichen Maßnahmen. Er weiß, warum er mehr Besucher gewonnen oder einige Besucher verloren hat. So zumindest der Idealzustand. Was aber, wenn diese Änderungen schon einige Monate zuruckliegen oder von einem Kollegen durchgefuhrt wurden?

Die damit einhergehenden Problemen lassen sich durch sogenannte „[Vermerke ](https://www.google.de/intl/de/analytics/features/annotations.html)" losen. Sind sind nicht mehr als Berichts-ubergreifende Vermerke auf der Zeitachse - also ein Marker, der sagt: „Zu diesem Zeitpunkt haben wir X geandert."

![Über dieses kleine Formular unterhalb von Graphen kannst du neue Vermerke erstellen. \(Screenshot: Google Analytics/ t3n.de\)](http://t3n.de/news/wp-content/uploads/2015/10/google-analytics-vermerk-595x52.jpg)

> _Über dieses kleine Formular unterhalb von Graphen kannst du neue Vermerke erstellen. (Screenshot: Google Analytics/ t3n.de)_

Vermerke lassen sich in nahezu jedem Bericht anlegen. Klicke hierfur unterhalb der Graphen auf „\+ Vermerk erstellen", wahle das passende Datum sowie einen erklarenden Text und klicke auf „Speichern". Wenn ein Vermerk nur zur eigenen Orientierung dient, wahle „Privat" als Sichtbarkeit. Willst du ihn mit anderen Nutzern teilen, wahle „Freigegeben".

Solange du als einziger an einer Website arbeitest, kannst du den Überblick uber alle vorgenommenen Änderungen behalten. Sobald eine Website aber mehrere Jahre alt ist oder mehrere Nutzer fur zustandig sind, wird das schwierig.

### 12\. Sorge fur sauberes Kampagnen-Tracking

Sobald du mit externen Partnern in Kontakt trittst - fur Werbeanzeigen, Gastartikel oder Kooperationen - solltest du dessen Performance uberwachen. Analytics bietet hierfur die sogenannten „utm-Parameter". Hierbei handelt es sich um Variablen, die einer URL angehangt und beim Abruf ausgelesen werden.

Ein Beispiel hierfur ware der folgende Link: [http://t3n.de/news/google-analytics-tipps-595562/?utm_source=t3n.de&utm_medium=Rectangle&utm_campaign=t3n-promokampagne](http://t3n.de/news/google-analytics-tipps-595562/?utm_source=t3n.de&utm_medium=Rectangle&utm_campaign=t3n-promokampagne).

Beim Aufruf dieser URL trennt Analytics alle Parameter ab dem Fragezeichen (?) von der eigentlichen URL, liest die drei definierten Parameter (utm_source, utm_medium, utm_campaign) aus und weist deren Werte (t3n.de, Rectangle, t3n-promokampagne) der aktuellen Sitzung zu.

![Google erleichtert das Erstellen von Kampagnenlinks mit diesem Online-Tool. \(Screenshot: Google/ t3n.de\)](http://t3n.de/news/wp-content/uploads/2015/10/google-analytics-kampagnen-tracking-595x824.jpg)

> _Google erleichtert das Erstellen von Kampagnenlinks mit diesem Online-Tool . (Screenshot: Google/ t3n.de)_

Nutzt du diese Moglichkeit im Rahmen von Anzeigen, lasst sich anschließend genau auswerten, welche Handlungen die daruber gewonnenen Besucher vollzogen haben. Besonders relevant sind dabei in der Regel die generierten Leads (beispielsweise Anmeldungen fur Newsletter) oder Abverkaufe (beispielsweise Kaufen eines t3n-Abonnements).

### 13\. Erstelle benutzerdefinierte Berichte und richte automatische Benachrichtigungen ein

Analytics ist wie YouTube. Wer den Webdienst ohne klares Ziel vor Augen offnet, verliert sich schnell darin. Sinnvoll sind deshalb Berichte, die in regelmaßigen Abstanden automatisch uber wichtige Kennzahlen informieren sowie Benachrichtigungen, die auf kurzfristige Ausschlage in negativer wie positiver Hinsicht hinweisen.

> „Analytics ist wie YouTube. Wer den Webdienst ohne klares Ziel vor Augen offnet, verliert sich schnell darin."

Mithilfe von benutzerdefinierten [Berichten ](http://www.google.com/intl/de_ALL/analytics/features/custom-reports.html) konnen Nutzer von Google Analytics den Fokus auf einen Teilbereich der Datenmenge legen, etwa die sozialen Interaktionen oder Kaufabschlusse. Anschließend lassen sie sich mit Kollegen teilen oder automatisch per E-Mail versenden.

Eine ahnliche Automatisierung bieten auch die sogenannten „[benutzerdefinierten Benachrichtigungen ](https://support.google.com/analytics/answer/1033021?hl=de)", mit denen Nutzer unter zuvor festgelegten Bedingungen automatisch Hinweise von Analytics erhalten. Dies bietet sich nicht nur beim Aufruf von Fehlerseiten an, sondern auch bei stark sinkenden Umsatz- und Besucherzahlen.

### 14\. Erstelle benutzerdefinierte Segmente

Die benutzerdefinierten Segmente sind das filternde Pendant der benutzerdefinierten Berichte. Mit Segmenten kannst du einen Bericht auf bestimmte Daten filtern und diese Ansichten kombinieren. Was das genau bedeutet, zeigt der folgende Screenshot am Beispiel von t3n.de.

![Zwei Segmente zeigen in Graphen deutlich die Unterschiede, hier zwischen Such- und Verweiszugriffen. \(Screenshot: Google Analytics/ t3n.de\)](http://t3n.de/news/wp-content/uploads/2015/10/google-analytics-segmente-595x149.jpg)

> _Zwei Segmente zeigen in Graphen deutlich die Unterschiede, hier zwischen Such- und Verweiszugriffen. (Screenshot: Google Analytics/ t3n.de)_

Der Graph zeigt „Suchzugriffe" (blau) und „Verweiszugriffe" (orange) wahrend des angegeben Zeitraums. Denkbar ist dies auch fur andere Segmente, etwa Kaufer eines bestimmten Produkts. Google Analytics hat von Anfang an einige Segmente, die allen Nutzern zur Verfugung stellen. Du kannst aber auch eigene erstellen.

Neue Segmente erstellst du uber den Button „\+ Neues Segment", anschließend musst du die Bedingungen deines Segments festlegen, Denkbar sind alle verfugbaren Nutzerdaten, wie Google in [der eigenen Hilfe ](https://support.google.com/analytics/answer/3124493?hl=de) erlautert. Deine Segmente kannst du anschließend auch mit Kollegen teilen.

### 15\. Versorge deine Kollegen mit passenden Dashboards

Dashboards sind Sammlungen von Berichten. Sie verschaffen deinen Kollegen einen sofortigen Überblick uber all ihre relevanten Kennzahlen. Fur t3n.de nutzen wir sie beispielsweise furs Monitoring der Jobborse sowie des Marktplatz. Die zustandigen Kollegen mussen so in der Regel nur eine Seite im Blick behalten: ihr Dashboard.

Ein Dashboard legst du unter „Berichte" > „Dashboards" > „\+ Neues Dashboard". Allgemeingultige Dashboards kannst du aus der Solutions Gallery importieren, fur spezielle auf deine Website zugeschnittene Losungen ist Handarbeit notig.

![Die linke Option ist beim Anlegen von Dashboards in der Regel die richtige Wahl. \(Screenshot: Google Analytics/ t3n.de\)](http://t3n.de/news/wp-content/uploads/2015/10/google-analytics-dashboard-2-595x217.jpg)

> _Die linke Option ist beim Anlegen von Dashboards in der Regel die richtige Wahl. (Screenshot: Google Analytics/ t3n.de)_

Nachdem du ein neues Dashboard angelegt hast, kannst du oben rechts unter „Dashboard anpassen" das grundlegende Layout wahlen. Ich tendiere in der Regel zu geteilten Ansicht („50% / 50%"). Anschließend kannst du neue Widgets hinzufugen, die aktuellen loschen oder editieren.

Bist du mit deinem Ergebnis zufrieden, teilst du das Dashboard anschließend uber „Teilen" offentlich mit allen Nutzern der Datenansicht oder per Link mit einzelnen Kollegen. Die bereits erstellten Dashboards werden in der Sidebar aufgelistet.

## Fazit

Das intiale Setup von Google Analytics kostet Zeit (und Nerven), rentiert sich aber schnell. Es sichert eine moglichst umfangreiche Datenbasis, die bei allen weiteren Maßnahmen zum Einsatz kommt und dessen Qualitat sichert.

Hilfreich ist, Analytics mit Berichten und Dashboards an die Bedurfnisse der Nutzer anzupassen. Dies spart nicht nur unnotige Arbeitsschritte und damit Arbeitszeit, sondern beschleunigt auch den sich anschließenden Optimierungsprozess. Die genannten 15 Tipps bieten hierfur einen guten Ansatzpunkt.

**Welche Tipps wurdet ihr erganzen? Schreibt uns einen Kommentar!**
