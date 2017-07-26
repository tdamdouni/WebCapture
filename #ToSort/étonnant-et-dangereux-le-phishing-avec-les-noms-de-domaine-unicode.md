# Étonnant et dangereux : le phishing avec les noms de domaine Unicode

_Captured: 2017-04-20 at 23:14 from [slice42.com](https://slice42.com/divers/2017/04/etonnant-et-dangereux-le-phishing-avec-les-noms-de-domaine-unicode-58326/)_

![](https://slice42.com/wp-content/uploads/2017/04/phishing-696x418.jpg)

Belle demonstration du chercheur en securite [Xudong Zheng](https://www.xudongz.com/blog/2017/idn-phishing/), qui montre un moyen astucieux (mais pas infaillible) d'afficher dans certains navigateurs une url reproduisant fidelement celle du site pour lequel des malfaiteurs voudraient se faire passer, dans la cadre d'une attaque de type phishing. En utilisant [Punycode](https://fr.wikipedia.org/wiki/Punycode), une syntaxe de codage conçue pour etre utilisee en adequation avec les noms de domaines internationalises, il est possible d'enregistrer des noms de domaine comme « xn--pple-43d.com » » qui s'afficheront sur certains navigateurs comme « аpple.com ».

L'astuce consiste ici a utiliser le « а » cyrillique (U+0430) plutot que le « a » ASCII (U+0061). On parle ici d'attaque [homographe](https://fr.wikipedia.org/wiki/Homographe). Pour l'utilisateur, l'url qui s'affiche apres avoir clique sur un lien (dans un mail, ou reçu par SMS, ou depuis une app) est la bonne, avec meme le https qui securisera la plupart des gens. Mais il sera bel et bien sur un site tiers, et s'il entre ses informations de login, il lui en cuira.

L'attaque peut tromper de nombreux navigateurs pour peu que tous les caracteres de l'url soient issus d'une meme langue, par exemple tout en cyrillique « [xn--80ak6aa92e.com](https://www.xn--80ak6aa92e.com/)« . L'un des moyens de decouvrir la supercherie est d'aller verifier le certificat SSL, mais mieux vaut habituer les utilisateurs a ne JAMAIS cliquer les liens reçus directement par mail, SMS ou autre, et a entrer eux-meme les url des sites qu'ils veulent visiter.

Xudong a prevenu les principaux fournisseurs de navigateur de cette vulnerabilite : Safari est immunise, Google le corrige dans Chrome 58, tandis que Firefox estime que c'est un probleme a gerer du cote des gestionnaires de noms de domaine (on doute qu'ils maintiennent leur position longtemps).

En attendant, il est possible de forcer Firefox a afficher les noms non traduits : saisissez « about:config » dans la barre d'url et basculez « network.IDN_show_punycode » sur « true ».

![](https://slice42.com/wp-content/uploads/2017/04/Firefox.jpg)
