# DevOps – Testautomation I – Infrastructure as Code 

_Captured: 2017-02-05 at 13:43 from [www.informatik-aktuell.de](https://www.informatik-aktuell.de/entwicklung/methoden/testautomation-im-bereich-continuous-delivery.html)_

![Deployment-Pipelines sind zentraler Part von Continuous Delivery. © Andrei Merkulov / Fotolia.com](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_720_Fotolia_131567200_Andrei_Merkulov_1db19dec88.jpg)

> _(C) Andrei Merkulov / Fotolia.com_

**Viele Unternehmen haben ihren Softwareentwicklungs-Prozess agil ausgerichtet, um Releases schneller und hochwertiger produktiv zu setzen, sprich, die "Time to Market" zu reduzieren. Denn noch immer gilt die Regel: nur Software, die vom Kunden genutzt werden kann, bringt dem Unternehmen Geld. Um dieses Vorhaben zu unterstutzen, setzen immer mehr Unternehmen auf Continuous Delivery und DevOps.**

Dieser zweiteilige Beitrag befasst sich mit der Notwendigkeit einer durchgehenden Testautomation in einer Continuous Deployment-Pipeline (Abb. 1) um erfolgreiche kontinuierliche Auslieferung in das Produktionssystem zu gewahrleisten. Es wird erklart, welche Werkzeuge, Frameworks und technische Ansatze moglich sind, um in vollem Umfang von automatisierten Tests profitieren zu konnen. Teil 1 behandelt die Testautomation von Applikationsumgebungen (Infrastructure as Code), Teil 2 beschaftigt sich mit der Testautomation von Webapplikationen & Mobile Device Clouds.

## Was ist DevOps?

"_DevOps is a software development method that emphasizes communication, collaboration (information sharing and web service usage), integration, automation, and measurement of cooperation between software developers and other IT professionals…   
… The specific goals of a DevOps approach span the entire deployment pipeline. They include improved deployment frequency, which can lead to faster time to market, lower failure rate of new releases, shortened lead time between fixes, and faster mean time to recovery..._" [[1]](https://www.informatik-aktuell.de/entwicklung/methoden/testautomation-im-bereich-continuous-delivery.html)

Ein kritischer Erfolgsfaktor ist dabei die durchgangige Automatisierung. Doch obwohl viele Unternehmen Releasemanagement, Lieferung und Bereitstellung automatisiert haben, ignorieren einige noch immer die Bedeutung von automatisierten Tests als Teil der DevOps-Werkzeuge.

![Abb.1: Deployment-Pipeline. © Rudolf Grötz](https://www.informatik-aktuell.de/fileadmin/_processed_/csm_pipeline_28d515da15.png)

> _Abb.1: Deployment-Pipeline. (C) Rudolf Grotz_

## Deployment-Pipeline

"_One of the challenges of an automated build and test environment is you want your build to be fast, so that you can get fast feedback, but comprehensive tests take a long time to run. A deployment pipeline is a way to deal with this by breaking up your build into stages. Each stage provides increasing confidence, usually at the cost of extra time. Early stages can find most problems yielding faster feedback, while later stages provide slower and more through probing. Deployment pipelines are a central part of Continuous Delivery_" (Martin Fowler [[2]](https://www.informatik-aktuell.de/entwicklung/methoden/testautomation-im-bereich-continuous-delivery.html))

## Testframeworks in der Pipeline

Im Prinzip kann jedes Test-Framework fur die Ausfuhrung der Tests verwendet werden. Um aber den wahren DevOps-Gedanken hoch zu halten, sollte eines gewahlt werden, dass von allen Teams in der gleichen Art und Weise benutzt werden kann, alle Arten von Teststages unterstutzt und leicht in die Continuous Deployment-Pipeline integriert werden kann. In diesem Fall ist einem Framework, das die naturliche Sprache unterstutzt, der Vorzug zu geben, weil die naturliche Sprache die Erstellung und Wartung der Tests erleichtert.
