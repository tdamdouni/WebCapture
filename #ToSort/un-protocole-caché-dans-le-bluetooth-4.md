# Un protocole caché dans le Bluetooth 4

_Captured: 2017-04-01 at 22:27 from [macbidouille.com](http://macbidouille.com/news/2017/04/01/un-protocole-cache-dans-le-bluetooth-4)_

Aujourd'hui, les constructeurs, a commencer par Apple, nous poussent a abandonner les connexions filaires au benefice de systemes sans fils qui utilisent pour l'essentiel le Bluetooth 4 et bientot son derive le 5.  
Dans le principe, ce Bluetooth utilise une connexion specifique pour les liaisons bas debit et peut utiliser le materiel Wi-Fi integre a nos machines pour des connexions plus lointaines ou de plus haut debit. Dans les faits, cette derniere fonction n'est pas utilisee au quotidien car il ne serait pas envisageable d'en doter des petits appareils nomades, le Wi-Fi consommant trop d'energie.

Un hacker surnomme Thymallus s'est interesse a ces protocoles et les a disseques. Il a ainsi pu regarder comment se passe l'appairage entre deux peripheriques et a regarde de pres comment Apple faisait avec ses AirPods pour realiser un appairage via iCloud.

A cette occasion, et en procedant par comparaisons et analogie, il a decouvert un protocole cache et absolument pas documente dans ce systeme d'appairage. En l'activant en force sur un iPhone via une application dediee, il a decouvert qu'il pouvait scanner tous les peripheriques Bluetooth, meme si ces derniers etaient censes ne pas etre detectables. Chose aussi interessante, il s'est aperçu qu'il arrivait a voir des appareils meme lointains, comme les ordinateurs, leur wi-fi venant suppleer au Bluetooth pour en augmenter la portee sans que les scanners Wi-Fi habituels n'arrivent a detecter des trames Bluetooth specifiques.

Apres de nombreuses tentatives de modifications du firmware d'une carte Wi-Fi externe il a decouvert qu'il est possible, sans appairage visible et meme si le Bluetooth est desactive au niveau logiciel, de se connecter a des machines distantes, en toute discretion. Il a deja reussi a recuperer les trames reseau et les frappes clavier. Il considere qu'avec un developpement specifique, il devrait aussi pouvoir afficher des captures d'ecran en temps reel des machines et acceder au contenu de leur disque dur.

Ce hacker blanc a tire le signal d'alarme de la communaute et demande aux specialistes de se pencher la-dessus tout en refusant pour le moment de donner trop de details sur sa decouverte et les moyens de l'exploiter.

Il semble toutefois evident que ce n'est pas une faille mais une fonction cachee ajoutee par un gouvernement pour espionner facilement n'importe qui ou simplement tout le monde.

Actuellement la seule solution pour echapper a un risque d'espionnage est de deconnecter physiquement le module Bluetooth des machines. C'est possible sur un ordinateur en retirant la carte, mais cela prive aussi du Wi-Fi qui est presque toujours sur la meme carte. C'est bien entendu impossible sur les iPhone, iPad et Mac recents dont les Wi-Fi et le Bluetooth sont parties integrantes des cartes meres.
