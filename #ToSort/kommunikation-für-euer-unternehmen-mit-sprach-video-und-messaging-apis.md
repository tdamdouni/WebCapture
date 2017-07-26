# Kommunikation für euer Unternehmen: Mit Sprach-, Video- und Messaging-APIs

_Captured: 2017-02-02 at 12:23 from [t3n.de](http://t3n.de/news/kommunikation-fuer-unternehmen-788836/)_

![](http://t3n.de/news/wp-content/uploads/2017/01/Sprach-Video-und-Messaging-APIs-e1485355221869.jpg)

> _Digitale Kommunikation ist fur Mitarbeiter und Kunden von Unternehmen nicht mehr wegzudenken. (Foto:_

Anzeige   
Mit Twilio konnen [Entwickler](http://t3n.de/tag/entwicklung-design) Telefonie-, Video- und Messaging-Features in ihre Applikationen einbinden. Dabei bleibt die Losung jederzeit anpassbar, frei skalierbar und ohne Fixkosten.

Kommunikation spielt heute fur viele Unternehmen eine wichtigere Rolle als jemals zuvor. Ob wir telefonisch einen Kunden kontaktieren, an einer Videokonferenz teilnehmen oder per Chat Kundensupport leisten - Kommunikation ist aus dem Unternehmensalltag nicht mehr wegzudenken.

Kommunikationsfunktionen sind aber haufig auch ein zentraler Bestandteil des Produkts oder der Dienstleistung eines Unternehmens. Beispielsweise [kommunizieren taglich hunderttausende Uber-Nutzer uber SMS und Anrufe](https://customers.twilio.com/208/uber/?utm_medium=cpc&utm_source=t3n&utm_campaign=t3n_sponsored_post). Ohne diese Funktion konnten Fahrer und Fahrgaste haufig keinen exakten Treffpunkt vereinbaren - die User Experience der Uber-App ware weitaus schlechter.

[Als Jeff Lawson vor 16 Jahren CTO des Startups StubHub war](https://www.twilio.com/blog/2015/11/how-jeff-lawson-founded-twilio-build-with-conviction-or-risk-burnout.html?utm_medium=cpc&utm_source=t3n&utm_campaign=t3n_sponsored_post), stand er vor einer ahnlichen Herausforderung: Die Ticketborse StubHub benotigte ein System, das den Interessenten fur ein Veranstaltungsticket sofort und anonym uber Telefon mit dem Verkaufer verbinden sollte.

Als Softwareentwickler kannte er sich in Sachen Telekommunikation nicht aus. Also wandte er sich an einschlagige Anbieter. Die Antwort war ernuchternd: Das System konne man mit einer Projektlaufzeit von zwei Jahren und einem Budget von zwei Millionen US-Dollar umsetzen.

Von da an war Lawson klar, dass der Telekommunikationsmarkt eine „Disruption" dringend notig hat. Nachdem er bei Amazon Web Services (AWS) Erfahrungen im Management von skalierbaren Cloudangeboten gesammelt hatte, setzte er seine Geschaftsidee um und grundete Twilio, den ersten Telekommunikationsanbieter fur Softwareentwickler. Das Konzept „Communications Platform as a Service" (CPaaS) war geboren.

## Die Vorteile einer CPaaS-Losung

![](http://t3n.de/news/wp-content/uploads/2017/01/shutterstock-350398172-e1485361444880.jpg)

> _Straßen von San Francisco, dem Hauptsitz von Uber und Twilio: In den vielen Einbahnstraßen kommunizieren minutlich Fahrer und Fahrgaste uber den genauen Treffpunkt. (Foto:_

Mit [Twilio](https://www.twilio.com/?utm_medium=cpc&utm_source=t3n&utm_campaign=t3n_sponsored_post) loste Jeff Lawson zwei Probleme, die er als CTO eines Startups mit den herkommlichen Kommunikationsanbietern hatte: Sowohl funktional als auch vom Preis waren diese viel zu unflexibel.

**Twilio**

Der CPaaS-Anbieter Twilio wurde 2008 in San Francisco gegrundet. Das Startup gewann fruh Techunternehmen wie Uber, Airbnb und Whatsapp als Kunden und wuchs mit ihnen rasant. 2016 ging Twilio an die Borse. Twilio Germany hat Buros in Munchen und Berlin, zu den wichtigsten Kunden zahlen Drivenow, die Delivery Hero Group und Shore.

Lawson hatte fur die Entwicklung dieses Services kein großes Budget. Daher wollte er keine Investitions- und Fixkosten tragen, schließlich konnten er und seine Mitgrunder den wirtschaftlichen Erfolg von StubHub nicht uber Monate vorhersagen. Gleichzeitig waren ausreichende Kapazitaten Pflicht, da von dem Service die erfolgreichen Transaktionsabschlusse abhingen.

Deshalb machte ihm auch die technische Skalierbarkeit Sorgen. Wurde StubHub eine gewisse Nutzerzahl uberschreiten, ware die gesamte Infrastruktur nicht mehr fahig, die Last zu bewaltigen. Lawson schaute sich daher fur Twilio das Prinzip der flexiblen unendlichen Skalierbarkeit bei Anbietern virtueller Server wie AWS ab. So ist es kein Wunder, dass Twilios Infrastruktur selbst vollstandig auf AWS lauft, um fur alle Leistungsspitzen gewappnet zu sein.

Was aber ware gewesen, wenn StubHub sein Geschaftsmodell plotzlich geandert hatte? Ware das System dann auch fur die neue Aufgabe geeignet oder eine teure, nutzlose Investition gewesen? Denn herkommliche Telekommunikationsangebote sind in der Regel viel zu statisch, um Innovationen umzusetzen. Sie bieten einen vordefinierten Funktionsumfang.

CPaaS-Anbieter bieten hingegen Kommunikationskanale als Bausteine fur Softwareentwickler an. Damit unterscheidet man sich von anderen Cloud-Anbietern, die das klassische Konzept der Telefonanlage „as a Service" anbieten. Einen vertiefenden Einblick in dieses Thema bietet der [CPaaS-Report der IDC](https://www.twilio.com/white-papers/idc-marketscape-leader-2016?utm_medium=cpc&utm_source=t3n&utm_campaign=t3n_sponsored_post).

## Kommunikationsbausteine via API

Angefangen hat bei Twilio alles mit den Kommunikationsbausteinen Telefonie und SMS. Heute bietet der CPaaS-Anbieter mit dem großten Portfolio auch Videocalls, Chat und die Integration von Kurznachrichtendiensten wie den Facebook-Messenger an.

Die Twilio-Bausteine wie Telefonie, SMS oder Chat sind als RESTful-Webservices verfugbar, konnen also einfach in bestehende Projekte integriert werden. Um die Integration einfach und schnell zu ermoglichen, stellt Twilio Helper-Libraries und Beispielcode in vielen popularen Programmiersprachen wie Node.js, PHP, Ruby, C#, Java oder Python sowie SDKs fur Web und Mobile zur Verfugung.

Hinzu kommt eine große Community von Entwicklern, die bereits Apps mit Twilio umgesetzt haben. Ein Blick in [Github](https://github.com/twilio) oder den [Twilio-Blog](https://www.twilio.com/blog?utm_medium=cpc&utm_source=t3n&utm_campaign=t3n_sponsored_post) lohnt sich, um auf neue Ideen zu kommen.

## Komplexitat und Reichweite nach Bedarf steigern - mit agiler Entwicklung

Obwohl CPaaS keine „Out-of-the-box-Losungen" bietet, ware es falsch zu glauben, dass es Wochen oder Monate Entwicklungszeit benotigt, um als kleines Unternehmen Resultate zu erzielen.

Ein naheliegendes Beispiel ist die Kundenkommunikation, da sie fur die meisten Unternehmen ein unentbehrliches Thema ist. Gerade Startups tun sich hier anfangs schwer - dabei kann sie ein entscheidender Wettbewerbsvorteil sein.

Je nach ihrer Große oder Kundenstruktur verschwenden Unternehmen keinen Gedanken an Callcenter-Strukturen. Dabei konnen auch bei geringerem Interaktionsvolumen viele Funktionen, die man aus dem Callcenter kennt, die Situation deutlich verbessern, wie zum Beispiel Sprachansagen, das Durchstellen von Anrufern auf Basis von Tasteneingaben oder der eingehenden Rufnummer, und anstelle von Besetztzeichen das Einrichten einer Warteschleife oder eines automatischen Ruckrufservices.

Mit Twilio lassen sich nicht nur solche Einzelfunktionen sehr schnell umsetzen, sondern spater auch die verschiedenen Kommunikationskanale orchestrieren oder direkt in die eigenen Apps einbinden. Wer sich das Beispiel „Callcenter" und seine Moglichkeiten naher anschauen will, findet eine Referenzarchitektur auf [Github](https://github.com/nash-md/twilio-contact-center). Eine [Youtube-Einfuhrung](https://www.youtube.com/watch?v=fEyoGI4m-lc) ist auch dabei. Mehr Informationen gibt es naturlich auch in der offiziellen [Twilio-Dokumentation](https://www.twilio.com/docs/?utm_medium=cpc&utm_source=t3n&utm_campaign=t3n_sponsored_post).

## Sofort global erreichbar

Es ist einfach, mit Twilio in allen fur das Unternehmen relevanten Markten in kurzer Zeit erreichbar zu sein und bei Bedarf in weitere Regionen zu expandieren, denn der CPaaS-Anbieter verfugt uber Rufnummern in mehr als 50 Landern.

Da die gebuchten Nummern sofort einsetzbar sind, steht einer Prototypenentwicklung nichts im Weg. Probiere es einfach kostenlos aus - frei nach Twilios Motto: „We can't wait to see what you build!"
