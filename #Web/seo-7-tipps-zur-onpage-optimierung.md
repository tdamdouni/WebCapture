# SEO: 7 Tipps zur Onpage-Optimierung 

_Captured: 2017-02-24 at 18:20 from [t3n.de](http://t3n.de/news/tipps-onpage-optimierung-584112/)_

![SEO: 7 Tipps zur Onpage-Optimierung](http://img.t3n.sc/news/wp-content/uploads/2015/01/shutterstock_191238782.jpg?auto=compress%2Cformat&fit=crop&fm=jpg&h=347&ixlib=php-1.1.0&q=65&w=620&s=65ec0437e278c7639cd756adbdc2e404)

> _ 

(Grafik: [Shutterstock](http://www.shutterstock.com/pic-191238782/stock-vector-seo-tag-with-gear-wheel.html))

_

Wer seine Website erfolgreich in Suchmaschinen platzieren will, sollte versuchen, ein tieferes Verstandnis fur deren Funktionsweise zu bekommen. Es sollte als Privileg angesehen werden, uber die Suchergebnisse zielgruppenrelevanten Traffic zu erhalten.

Damit Seitenbetreiber von diesem Privileg profitieren konnen, sollten sie Suchmaschinen das Crawling der eigenen Website vereinfachen. Diese haben schließlich das Interesse, Suchenden die passenden Antworten auf ihre Fragen zu geben. Fragen, die Seitenbetreiber am liebsten mit ihrer eigenen Website beantworten.

## Worauf legen Suchmaschinen wert?

Damit die eigene Website zu den relevanten Fragen beziehungsweise Keywords gefunden wird, mussen die Crawler der Suchmaschinen die relevanten Unterseiten erreichen, deren Inhalte interpretieren und korrekt verarbeiten. Erst dann landen sie im Index und werden gegebenenfalls zu passenden Suchanfragen ausgeliefert.

Heutzutage geht es in fast allen Bereichen um Energie und Effizienz - so auch bei Suchmaschinen. Jede Website erhalt ein bestimmtes Index- und Crawlingbudget, das den Crawlern den fur eine Domain veranschlagten Zeitaufwand vorgibt. Webmaster konnen hier entscheidende Fehler machen, indem sie die vorhandenen Budgets fur die falschen Ressourcen verwenden. Mithilfe einiger Hinweise konnen sie die Relevanz einzelner Inhalte festlegen. Suchmaschinen verstehen diese Hinweise, setzen davon ausgehend Prioritaten und lassen sich somit in gewissem Ausmaß steuern.

## Die Anweisungen im Detail

Webmaster, die verstanden haben, dass sie mit den vorhandenen Budgets sorgsam haushalten sollten, konnen von den Ressourcen, die ihnen die Suchmaschine zur Verfugung stellt, bestmoglich profitieren. Doch worauf achten Crawler? Welche Hinweise sind fur sie relevant und beeinflussen die Verarbeitung einer Website? Diese Fragen soll mein Artikel beantworten.

### 1\. Schutze dich vor Duplicate Content

![Vorsicht, vor „Duplicate Content“. \(Foto: <a href=](http://t3n.de/news/wp-content/uploads/2015/01/duplicate-content-595x334.jpg)

> _Vorsicht, vor „Duplicate Content". (Foto:_

Vielen Webmastern ist nicht bewusst, dass doppelte Inhalte zu Problemen fuhren. Zum einen fallt es Suchmaschinen schwer, das „richtige" Dokument fur Suchanfragen auszuliefern. Zum anderen verschwenden doppelte Inhalte das vorhandene Crawling-Budget, sodass relevante Inhalte moglicherweise nicht in den Index gelangen. Suchmaschinen werden immer besser darin, doppelte Inhalte zu erkennen und das erstgenannte Problem zu beheben. Fur Webmaster resultieren doppelte Inhalte aber dennoch in einer Verschwendung des eigenen Budgets.

In einigen Fallen lassen sich doppelte Inhalte nicht vermeiden. Seitenbetreiber sollten den Crawlern unter diesen Umstanden im Quelltext erklaren, wie sie damit umgehen sollen. Hilfreich sind dabei folgende Moglichkeiten:

  * **Das Meta-Tag _„noindex"_:** Es sorgt dafur, dass eine Webseite nicht in den Index aufgenommen wird. Das Meta-Tag wird in den <head> der Seite geschrieben und sieht folgendermaßen aus: <meta name="robots" content="noindex">. Es hilft dabei, die doppelte Indexierung von „Duplicate Content" zu vermeiden.
  * **Das Canonical-Tag:** Es wird genutzt, wenn sich mehrere Seiten kaum oder gar nicht voneinander unterscheiden. Die „Duplikate" einer Seite verweisen per Canonical-Tag auf das „Original". Webmaster erklaren der Suchmaschine damit, welche Unterseite in den Index aufgenommen und bei passenden Suchanfragen ausgeliefert werden soll. Auch das Canonical-Tag wird in den <head> der Seite geschrieben und sieht folgendermaßen aus: <link rel="canonical" href="http://www.beispiel.de/">.
  * **Korrekte Statuscodes:** Seitenbetreiber sollten auf korrekte Statuscodes achten, damit Suchmaschinen wichtige Ressourcen sparen. Die folgenden Statuscodes sind fur Suchmaschinen besonders relevant: 
    * **Statuscode 200 - OK:** Er signalisiert den Crawlern, dass mit dieser Seite alles in Ordnung ist und dass ein Dokument erreichbar ist. Wichtig: Sollte es sich um eine Fehlerseite handeln, die eigentlich den Status 404 erhalten sollte, dann muss diese auch als 404-Seite gekennzeichnet werden. Ist das nicht der Fall, spricht man von „Soft 404"-Fehlern.
    * **Statuscode 301 - Moved Permanently: **Ist eine Ressource dauerhaft unter einer anderen URL vorhanden, sollte die Weiterleitung per Statuscode 301 erfolgen. Dieser Statuscode sorgt dafur, dass relevanter „Linkjuice" weitergegeben wird. Wenn also eine Weiterleitung dauerhaft und nicht temporar ist, nutze immer „Statuscode 301".
    * **Statuscode 302 - Found: **Beim Statuscode 302 erhalten Crawler die Information, dass eine Webseite nur temporar unter einer anderen URL erreichbar ist. Dadurch wird kein „Linkjuice" an das neue Linkziel weitergegeben.
    * **Statuscode 404 - Not found:** Ein 404-Fehler erklart Crawlern, dass ein Dokument nicht unter der angegebenen URL verfugbar ist - ein schlechtes Zeichen. Webmaster sollten die Anzahl dieser Fehler gering halten. Die Webmaster-Tools helfen, 404-Fehler auf der eigenen Website aufzuspuren.
    * **Statuscode 500 - Internal Server Error:** Wenn Server einen internen Fehler feststellen, geben sie meist einen Statuscode 500 aus. Crawler beenden an dieser Stelle haufig das Crawling und kommen zu einem spateren Zeitpunkt noch einmal zuruck, damit der Server nicht zusatzlich belastet wird.
    * **Statuscode 503 - Service Unavailable:** Wird der Statuscode 503 ausgeben, ist der Server uberlastet oder wird gewartet. Fur Crawler ist das ein Hinweis darauf, dass sie ihre Arbeit zu einem spateren Zeitpunkt fortsetzen sollten. Mithilfe des Header-Felds „Retry-After" konnen Webmaster angeben, wann der Server wieder in der Lage ist, externe Anfragen zu bearbeiten.

### 2\. Vermeide Weiterleitungsketten

Weiterleitungsketten (auch „Redirect-Chains") rauben Crawlern wichtige Ressourcen. Webmaster sollten diese deshalb bestmoglich vermeiden. Die inkorrekte Nutzung von Statuscodes kann dazu fuhren, dass „Linkjuice" nicht weitergegeben wird, weshalb Seitenbetreiber mit dem korrekten Statuscode (meist 301) auf neue Linkziele verweisen sollten. Suchmaschinen brechen das Crawling der Weiterleitungsketten teilweise ab. Auf mobilen Geraten sorgen sie außerdem fur steigende Ladezeiten.

### 3\. Strukturiere deine Website mit Sitemaps

Sitemaps bieten die Chance, Crawlern schon zu Beginn ihrer Arbeit einen Überblick zu geben und Prioritaten zu setzen. Sie konnen inhaltlich separiert werden und lassen sich auch nach Datentyp trennen. so gibt es Sitemaps fur:

  * Inhalte,
  * Videos,
  * Bilder,
  * News,
  * mobile Inhalte.

Damit sie gefunden wird, sollte die Sitemap in der [robots.txt](http://t3n.de/news/robotstxt-alles-seo-daruber-442643/) der Website stehen. Ist die maximale Große limitiert, konnen Webmaster einen Master erstellen, der alle weiteren Sitemaps enthalt.

Die einzelnen Sitemaps konnen Seitenbetreiber außerdem in den Google-Webmaster-Tools einreichen. So lasst sich kontrollieren, inwieweit die Sitemaps bereits von der Suchmaschine bearbeitet wurden.

Mithilfe folgender Attribute konnen Webmaster dem Crawler weitere Informationen zukommen lassen:

  * <changefreq>: Dieses Attribut gibt an, wie haufig sich der Inhalt des Dokuments andert und wann ein Recrawl angebracht ist. Es stehen folgende Attribute zur Auswahl: _always_, _hourly_, _daily_, _weekly_, _monthly_, _yearly_, _never_. Seitenbetreiber konnen mithilfe dieser Attribute beispielsweise auch einzelne Seitenbereiche kennzeichnen, deren Inhalte sich seltener andern, Archive sind hierfur ein gutes Beispiel.
  * <priority>: Webmaster, die in der Sitemap die Wertigkeit einzelner Unterseiten unterscheiden mochten, konnen das mit diesem Attribut tun. Es gibt an, wie hoch die Prioritat eines einzelnen Dokuments im Vergleich zu allen anderen Dokumenten ist. Der Standardwert liegt bei „0,5", die gesamte Spanne liegt zwischen „0,1" und „1,0". Mithilfe dieses Attributs konnen Webmaster der Suchmaschine mitteilen, welche Dokumente ihnen besonders wichtig sind, damit die Suchmaschine hierfur mehr Ressourcen aufwendet.
  * <lastmod>: Das Attribut gibt an, wann eine Sitemap das letzte Mal geandert wurde. Wichtig: Es geht hierbei nicht um die Inhalte, sondern um die Sitemap. Der Einsatz dieses Attributs ist also nur nach der Anpassung der Sitemap notig.

### 4\. Mache schwer crawlbare Inhalte verstandlich

Crawler hatten in der Vergangenheit teilweise Schwierigkeiten mit Ajax-basierten Inhalten. Obwohl die Verarbeitung mittlerweile besser geworden ist, sollten Webmaster den Crawlern bei der Verarbeitung aller Unterseiten helfen. Wenn Ajax genutzt wird, um Content dynamisch nachzuladen, sollte folgendes beachtet werden:

  * Damit Crawler die per Ajax ausgezeichneten Elemente verarbeiten, mussen sie ausgezeichnet werden. Hierzu mussen den Crawlern andere URLs zur Verfugung gestellt werden, wie Google [in einer Anleitung](https://developers.google.com/webmasters/ajax-crawling/docs/getting-started) erklart.
  * Die URLs mussen ein Token in den Hash-Fragmenten enthalten, das den Crawlern den Ajax-Inhalt signalisiert. Bei eindeutigen Seiten handelt es sich bei dem Token um ein Ausrufungszeichen.
  * Die Crawler mussen fur jede zu indexierende URL vom Server einen HTML-Snapshot erhalten, der alle fur den Nutzer sichtbaren Inhalte enthalt. Damit der Server weiß, welche Version er den Crawlern geben muss, andert dieser temporar die Ajax-URL. Er ersetzt den Hashwert (#!) in „?_escaped_fragment_=" und erfragt damit den Snapshot.
  * Bei Seiten, die ohne Hash-Fragmente indexiert werden sollen (beispielsweise die Startseite oder einzelne Unterseiten), muss folgendes Meta-Tag in den <head> der Seite eingefugt werden: <meta name="fragment" content="!">. Auch hier wird ein HTML-Snapshot fur die jeweilige Seite benotigt, die Crawler vom Server erfragen konnen.
  * In den Sitemaps sollten die URLs eingetragen werden, die auch so in dieser Form indexiert werden sollen.

Um als Webmaster sicher zu gehen, dass die Suchmaschine alle Ajax-Inhalte verarbeiten und indexieren konnte, sollte man es mithilfe der Google-Webmaster-Tools prufen. Im Bereich „Crawling" findet man den Menupunkt „Abruf wie durch Google". Hier mussen Nutzer nur die URL mit dem Hashwert (#!) eintragen und auf „Abrufen und rendern" klicken.

### 5\. Nutze die Vorteile von internen Links

![Nutze das Potenzial interner Links. \(Bild: <a href=](http://t3n.de/news/wp-content/uploads/2014/03/linkaufbau_bjorn_tantau-595x371.jpg)

> _Nutze das Potenzial interner Links. (Bild:_

Mithilfe von internen Links konnen Seitenbetreiber die wichtigsten Unterseiten ihrer Website definieren. Die Haufigkeit, mit der ein Dokument verlinkt wird, signalisiert Crawlern dessen Prioritat. Besonders wichtig ist auch die Erreichbarkeit: Je schneller eine Unterseite von der Startseite aus erreichbar ist, desto großer ihre Bedeutung. Seitenbetreiber sollten demnach eine flache Hierarchie wahlen oder alle Unterseiten mithilfe von optimierten Paginierungen, Linkmodulen oder Sitemaps zur Verfugung stellen.

### 6\. Schaffe Zusammenhange

Crawler haben Probleme, den Zusammenhang zweier Unterseiten zu erkennen, insbesondere, wenn es sich um paginierte Artikel handelt. Seitenbetreiber konnen hier mit den Attributen <rel="next"> und <rel="prev"> abhelfen. Sie werden im <head> einer Webseite hinterlegt und stellen so eine Beziehung zwischen mehreren Dokumenten her.

Das Attribut <rel="next"> verweist auf die nachsten Teile eines Dokuments, <rel="prev"> auf die vorherigen Teile. Crawler erkennen dadurch nicht nur den Zusammenhang zweier Webseiten, sondern auch ihre Reihenfolge.

### 7\. Stelle strukturierte Inhalte bereit

Strukturierte Daten bieten Seitenbetreibern eine weitere Moglichkeit, dem Crawler [zusatzliche Informationen](http://schema.org/docs/gs.html) uber die auf einer Webseite hinterlegten Inhalte zu geben. Sie werden mittels Tags auf den Unterseiten eingebunden und wirken sich teilweise auf deren Darstellung in den Suchergebnissen aus. Man spricht in diesem Kontext auch von „[Rich Snippets](http://t3n.de/news/rich-snippets-anleitung-534054/)". Es gibt sie unter anderem fur folgende Informationstypen:

  * Bewertungen
  * Veranstaltungen
  * Personen
  * Breadcrumbs
  * Rezepte
  * Produkte
  * Unternehmen
  * Musik

Um zu testen, ob diese Daten innerhalb des Dokuments korrekt ausgezeichnet wurden, bietet Google ein „[Test-Tool fur strukturierte Daten](http://www.google.de/webmasters/tools/richsnippets)".

## Fazit

Nicht nur einzigartige und hochwertige Inhalte, sondern auch eine optimale technische Infrastruktur beflugeln die Rankings deiner Websites. Denke deshalb immer an deine zwei Zielgruppen: die Nutzer, die deine Inhalte lesen mochten, und die Crawler, die sie interpretieren und verarbeiten mussen.

Sie wollen beide ...

  * inhaltliche Zusammenhange erkennen,
  * wichtige Informationen auf einen Blick erhalten,
  * mit wenig Aufwand thematisch ahnliche Informationen finden,
  * das ausgewahlte Dokument lesen,
  * einen gut strukturierten Aufbau erkennen,
  * moglichst viele relevante Zusatzinformationen erhalten und
  * wenig Energie fur das Suchen relevanter Informationen aufwenden.

Wenn du auf diese Wunsche eingehst, sicherst du dir die Sympathie der Nutzer und Crawler. Und das Beste ist: Sie werden es zu schatzen wissen.

**Einen grundlegenden Einstieg in das Thema Onpage-Optimierung liefert unser Artikel „[Onpage-SEO: Die wichtigsten Rankingfaktoren](http://t3n.de/news/onpage-seo-rankingfaktoren-473617/)".**

**Über den Autor**

Kevin Jackowski ist Online-Marketing-Experte und veroffentlicht auf [OnlineMarketingEinstieg.de](http://www.onlinemarketingeinstieg.de/) regelmaßig Inhalte rund um die Themen „Online-Marketing-Grundlagen" und „Karriere im Online-Marketing". Wenn du dich fur dieses Thema interessierst, folge ihm auf [Facebook](https://www.facebook.com/kevinjackowski.de).
