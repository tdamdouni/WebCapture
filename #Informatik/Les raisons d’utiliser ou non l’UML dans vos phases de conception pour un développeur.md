# Les raisons d’utiliser ou non l’UML dans vos phases de conception pour un développeur

_Captured: 2016-05-06 at 11:37 from [www.blog-nouvelles-technologies.fr](http://www.blog-nouvelles-technologies.fr/1038/les-raisons-dutiliser-ou-non-luml-dans-vos-phases-de-conception-pour-un-developpeur/)_

Dans de nombreuses professions, les gens utilisent des modeles graphiques pour representer ce qu'ils ont cree ou ce qu'ils sont en train d'etudier. Par exemple, les chimistes font des diagrammes en 2D et 3D pour les modeles de molecules, les cartographes utilisent differents types de cartes pour representer les multiples aspects geographiques d'une region, d'un pays, du monde.  
Si vous etes un developpeur de logiciels, vous avez certainement vu des diagrammes representant quelques faits sur la conception de logiciels. **[UML](http://fr.wikipedia.org/wiki/Unified_Modeling_Language) est un langage visuel, couramment utilise pour creer de tels diagrammes.**

![Les raisons d'utiliser ou non l'UML dans vos phases de conception pour un développeur - Exemples de diagrammes](http://www.blog-nouvelles-technologies.fr/wp-content/uploads/2011/01/utiliser-ou-non-uml-pour-developpeur-1.png)

> _Les raisons d'utiliser ou non l'UML dans vos phases de conception pour un developpeur - Exemples de diagrammes_

_UML_ n'est pas specifique a un processus de logiciel, au paradigme de programmation (par exemple, la [programmation orientee objet](http://www.blog-nouvelles-technologies.fr/688/programmation-orientee-objet-en-php/)), ou de la technologie (par exemple : _Java_, _.NET_, _PHP_, …). Il etait axe a l'origine sur les systemes d'objets, mais a evolue et peut maintenant etre utilise pour modeliser tout type de logiciel.

Recemment, un ami m'a demande la raison pour laquelle les gens n'aiment pas utiliser _UML_ et pourquoi ce dernier est tres peu utilise dans les phases de conception ? Je lui ai donne mon avis (que je vous partage ici) et meme si vous n'aimez pas _UML_, il y a de bonnes raisons de l'utiliser.

> UML (Unified Modeling Language, que l'on peut traduire par "langage de modelisation unifie) est une notation permettant de modeliser un probleme de façon standard. Ce langage est ne de la fusion de plusieurs methodes existantes auparavant, et est devenu desormais la reference en terme de modelisation objet, a un tel point que sa connaissance est souvent necessaire pour obtenir un poste de developpeur objet. [[commentcamarche.net](http://www.commentcamarche.net/contents/uml/umlintro.php3)]

> La modelisation consiste a creer une representation simplifiee d'un probleme: le modele.
> 
> Grace au modele il est possible de representer simplement un probleme, un concept et le simuler. La modelisation comporte deux composantes :
> 
>   * L'analyse, c'est-a-dire l'etude du probleme
>   * la conception, soit la mise au point d'une solution au probleme
>   * Le modele constitue ainsi une representation possible du systeme pour un point de vue donne
> 
> [[commentcamarche.net](http://www.commentcamarche.net/contents/uml/umlmodel.php3)]

##  La notation n'est pas connue 

**Certaines personnes n'utilisent pas _UML_ tout simplement parce qu'elles ne connaissent pas la notation.** Dans de nombreux cas, la personne peut lire des diagrammes _UML_, mais n'est pas suffisamment en confiance pour les creer. Par analogie, certains developpeurs de logiciels peuvent lire l'anglais mais ne sont pas a l'aise a l'ecrit. Effectivement je ne suis pas parfait !

##  _UML_ est trop complexe

_UML_ a gagne en complexite et en taille au fil des ans. Aujourd'hui il existe 14 differents types de diagrammes ! C'est trop a retenir pour un etre humain. **Certaines personnes sont degoutees par l'_UML_ parce qu'elles jugent que l'effort pour gravir la courbe d'apprentissage ne sera pas payant.**

![Les raisons d'utiliser ou non l'UML dans vos phases de conception pour un développeur - 14 différents types de diagrammes UML](http://www.blog-nouvelles-technologies.fr/wp-content/uploads/2011/01/utiliser-ou-non-uml-pour-developpeur-2.jpg)

> _Les raisons d'utiliser ou non l'UML dans vos phases de conception pour un developpeur - 14 differents types de diagrammes UML_

##  Beaucoup ne connaissent pas la notion de classe _UML_

Beaucoup d'anciens developpeurs n'ont jamais appris a l'universite l'_UML_. Personnellement des l'IUT j'ai appris l'_UML_ avec des cours d'Analyse et conception des systemes d'information. Ainsi avant chaque phase de developpement nous devions realiser une analyse _UML_ du projet.  
De plus, la formation _UML_ n'est pas tellement repandue et les gens en general ne se sentent pas obliges d'acheter et de lire des livres _UML_, beaucoup n'ont tout simplement jamais appris _UML_.

##  Des notations informelles peuvent faire tout aussi bien

Dans de nombreuses situations, les gens ne pensent pas avoir besoin des diagrammes _UML_ pour communiquer leurs idees. Ils vous est possible de creer des diagrammes informels qui sont faciles a creer dans [PowerPoint](http://office.microsoft.com/fr-fr/powerpoint/), [Visio](http://office.microsoft.com/fr-fr/visio-help/), ou meme pour les amateurs du crayon sur un tableau blanc ! De plus, des outils en ligne existent pour realiser ce genre de diagramme : [Gliffy](http://www.gliffy.com/) est un service ou il est possible de faire des diagrammes de reseaux informatiques, des plans de salle, des diagrammes de processus et des organigrammes… La version gratuite est limitee a 2Mo de photos, mais le nombre de diagrammes est illimite a partir du moment ou ils sont publics. Pour quelque chose de plus confidentiel il faudra passer a la version _premium_.

Les developpeurs de logiciels sont habitues a etre formels au niveau du code (apres tout, les langages de programmation sont des langages officiels), mais ils n'aiment pas le formalisme au niveau de l'architecture.

##  La phase d'analyse n'est pas jugee importante 

Dans de nombreux projets, l'architecture du logiciel est assez simple car il suit juste une architecture de reference et donc il n'y a pas de besoin important de creer des diagrammes pour representer et communiquer sur la conception.  
Dans certains cas, la conception est communiquee oralement ou en utilisant d'autres notations graphiques, tels que les diagrammes informels et en ligne (comme mentionne ci-dessus).

## Conclusion

**Que ce soit par un manque de documentation sur la conception ou d'une decision deliberee qui resulte d'un manque de connaissance, de telles situations sont assez frequentes, et dans ce cas la creation de modeles _UML_ est sans importance.**

**Il est facile de dire "Ne pas utiliser _UML_", mais l'inverse l'est moins. **

Les notations informelles aident a la comprehension dans de nombreux contextes mais dans d'autres, l'ambiguite nuit a la capacite de comprendre la conception.  
Il est vrai que l'on peut se passer d'une documentation de conception dans certains cas, mais le manque de documentation devient un probleme quand la conception doit etre communiquee a travers le temps (pour un developpeur qui se joindra a l'equipe de six mois plus tard) ou de la distance (pour un developpeur qui travaille dans un autre pays).

Ainsi, bien que je suis d'accord avec certaines des critiques sur _UML_, je ne peux pas vous donner une meilleure alternative pour tout faire. Je pense qu'utiliser l'_UML_ est indispensable.

##  C'est une norme 

_UML_ est le langage standard de facto pour la conception de logiciels. **En d'autres termes, c'est le seul logiciel de notation de conception donc qu'attendez-vous pour l'utiliser **

##  Outils d'aide 

Des outils _UML_ a partir de logiciels libres abondent sur le marche, y compris des _plugins_ pour les _IDE_ les plus populaires. Pour ma part, j'utilise [UMLet](http://marketplace.eclipse.org/content/umlet-uml-tool-fast-uml-diagrams) pour [Eclipse](http://www.eclipse.org/). A noter egalement que ce logiciel est disponible en installation sur votre machine pour editer directement des diagrammes.

![Les raisons d'utiliser ou non l'UML dans vos phases de conception pour un développeur - Plugin UML pour Eclipse](http://www.blog-nouvelles-technologies.fr/wp-content/uploads/2011/01/utiliser-ou-non-uml-pour-developpeur-3.jpg)

> _Note : Voici des alternatives pour UMLet._

Outre les diagrammes, certains de ces outils peuvent generer du code, appliquer des modeles de conception, vous vous essaierez egalement a la pro-ingenierie et a la retro-ingenierie, _refactoring_, et l'analyse de la complexite.  
**La capacite de generer du code depuis la conception dans les nombreux outils _UML_ est une bonne raison d'utiliser _UML_.**

##  _UML_ est flexible 

Les stereotypes et les profils _UML_ peuvent vous permettre de personnaliser vos besoins. En d'autres termes, vous pouvez avoir des elements de modelisation et des relations qui sont specialises pour votre domaine ou pour les technologies que vous utilisez.

##  Les modeles _UML_ sont portables 

**  
Les modeles _UML_ peuvent etre sauvegardes dans le format standard [XMI](http://fr.wikipedia.org/wiki/XML_Metadata_Interchange).** Ces fichiers _XMI_ peuvent etre lus par differents outils _UML_, bien que certains ont un peu plus de mal que d'autres (c'est souvent le cas avec n'importe quel fichier interchangeable entre differents systemes).

![Les raisons d'utiliser ou non l'UML dans vos phases de conception pour un développeur - Génération en XMI des diagrammes UML](http://www.blog-nouvelles-technologies.fr/wp-content/uploads/2011/01/utiliser-ou-non-uml-pour-developpeur-4.jpg)

> _Les raisons d'utiliser ou non l'UML dans vos phases de conception pour un developpeur - Generation en XMI des diagrammes UML_

##  Inutile de tout connaitre 

_UML_ dispose de 14 differents types de diagrammes. Vous ne trouverez personne qui ne les utilise pour un systeme logiciel. Ce n'est pas un objectif de l'essayer   
J'avais vu il y a quelques mois (impossible de remettre la main dessus…) une enquete montrant que dans la pratique les developpeurs utilisent regulierement les diagrammes de classe, de sequence et de cas d'utilisation. **La [loi de Pareto](http://fr.wikipedia.org/wiki/Loi_de_Pareto) semble s'appliquer : 20% du langage _UML_ peut couvrir 80% de vos besoins de modelisation.**  
Cela signifie que vous pouvez apprendre un sous-ensemble de la notation et de communiquer efficacement vos conceptions en utilisant _UML_.

##  L'architecture est importante 

L'architecture logicielle est le modele pour le systeme, elle permet d'analyser les performances, la disponibilite, la securite, la planification pour un [developpement incremental,](http://en.wikipedia.org/wiki/Iterative_and_incremental_development) et des guides pour l'attribution des taches et le suivi.  
**Cependant, meme la meilleure des architectures creees avec des annees d'experience et dont les modeles ont ete conçus avec soin, peut etre inutile si elle n'est pas correctement documentee et expliquee aux personnes qui ont besoin de l'utiliser.**

##  Conclusion 

Étant donne que la valeur strategique pour les nombreuses entreprises correspond a l'augmentation de logiciels, les industries cherchent des techniques pour automatiser la production de logiciels et d'ameliorer la qualite tout en reduisant les couts et les delais de mise en service.

Le _Unified Modeling Language_ a ete conçu pour repondre a ces besoins.

**De la meme façon qu'il vaut mieux dessiner une maison avant de la construire, il vaut mieux modeliser un systeme avant de le realiser.** L'_UML_ permet :

  * Obtenir une modelisation de tres haut niveau independante des langages et des environnements 
  * Faire collaborer des participants de tout horizon autour d'un meme document de synthese 
  * Exprimer dans un seul modele tous les aspects statiques, dynamiques, juridiques, specifications, etc…
  * Documenter un projet 
  * Generer automatiquement la partie logiciel d'un systeme 

Voici une petite liste des livres que j'ai pu lire sur le sujet, que je vous recommande :

  * "[UML 2 par la pratique](http://www.editions-eyrolles.com/Livre/9782212114805/)" de Pascal Roques chez Eyrolles, livre d'etude de cas et exercices corriges 
  * "[UML 2 en action](http://www.editions-eyrolles.com/Livre/9782212114621/)" de Pascal Roques chez Eyrolles, livre oriente sur l'analyse des besoins a la conception J2EE
  * "[Real Time Uml](http://books.google.fr/books?id=LewzKVv3A20C&printsec=frontcover&dq=Real+Time+Uml&source=bl&ots=VcMa_Lke1M&sig=tBuLvMD1Vza8OFGLYTGOuM8xgKs&hl=fr&ei=t7AtTfKTIdLH4Abr_dSDCw&sa=X&oi=book_result&ct=result&resnum=4&ved=0CEUQ6AEwAw#v=onepage&q&f=false)" de Bruce Powel Douglass, disponible gratuitement sur [Google Books](http://books.google.fr/)

Et vous, utilisez-vous UML pendant vos phases de conception ? Si oui, pourquoi ? Si non, pourquoi egalement ?
