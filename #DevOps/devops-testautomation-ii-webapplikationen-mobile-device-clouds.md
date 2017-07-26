# DevOps – Testautomation II – Webapplikationen & Mobile Device Clouds 

_Captured: 2017-02-05 at 13:44 from [www.informatik-aktuell.de](https://www.informatik-aktuell.de/entwicklung/methoden/devops-testautomation-ii-webapplikationen-mobile-device-clouds.html)_

![© Andrei Merkulov / Fotolia.com](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_720-Fotolia_131567130_Andrei-Merkulov_a57155a2fb.jpg)

> _(C) Andrei Merkulov / Fotolia.com_

**Viele Unternehmen haben ihren Softwareentwicklungs-Prozess agil ausgerichtet, um Releases schneller und hochwertiger produktiv zu setzen, sprich, die "Time to Market" zu reduzieren. Denn noch immer gilt die Regel: nur Software, die vom Kunden genutzt werden kann, bringt dem Unternehmen Geld. Um dieses Vorhaben zu unterstutzen, setzen immer mehr Unternehmen auf Continuous Delivery und DevOps.**

Dieser Beitrag befasst sich mit der Notwendigkeit einer durchgehenden Testautomation in einer Continuous Delivery-Pipeline (Abb. 1) um erfolgreiche kontinuierliche Auslieferung in das Produktionssystem zu gewahrleisten. Es wird erklart welche Werkzeuge, Frameworks und technische Ansatze moglich sind, um in vollem Umfang von automatisierten Tests profitieren zu konnen.

![Abb.1: Deployment-Pipeline. © Rudolf Grötz](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_pipeline_28d515da15.png)

> _Abb.1: Deployment-Pipeline. (C) Rudolf Grotz_

## Testautomation fur Applikations Code (Feature Code)

Die Stages innerhalb einer Continuous Delivery-Pipeline haben verschiedene Testziele. Nur wenn ein Build alle Stages fehlerfrei durchlaufen hat wird der Build fur die Produktion freigegeben. In der Acceptance Stage wird gepruft, ob die Anwendung und die dazugehorigen Services laufen. Es werden automatisierte Akzeptanztests ausgefuhrt, welche alle notwendigen Geschaftsfalle auf Regression prufen. Die Capacity-Stage pruft, ob die Anwendung den erwarteten nichtfunktionalen Anforderungen (Performance, Load, Stress, …) Stand halt. Als letzten Überprufungsschritt fuhrt der Kunde in der User-Acceptance Stage einen manuellen Akzeptanztest durch.

Eine in unserem Beispiel besondere - aber nicht immer ubliche - Rolle spielt dabei die Browser-Stage.

![Abb. 2: Login-Seite. © Rudolf Grötz](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_Testauto_II_Abb2_Groetz_37be2585b7.png)

> _Abb. 2: Login-Seite. (C) Rudolf Grotz_

![Abb. 3: Parent-Job für die Pipeline © Rudolf Grötz](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_Testauto_II_Abb3_Groetz_7491ee938a.png)

> _Abb. 3: Parent-Job fur die Pipeline (C) Rudolf Grotz_
