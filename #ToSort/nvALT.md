# nvALT

_Captured: 2015-12-10 at 22:44 from [aya.io](http://aya.io/blog/nvalt-prise-de-notes/)_

_ou_

## La prise de notes pour les perfectionnistes

[nvALT](http://brettterpstra.com/projects/nvalt/) est une application _gratuite_, legere et rapide qui permet de **prendre des notes instantanement**.

![](http://aya.io/blog/images/nvALT.jpg)

nvALT c'est egalement :

  * une gestion des notes par etiquettes et mots-cles
  * le plaisir d'ecrire en [Markdown](http://fr.wikipedia.org/wiki/Markdown)
  * vos notes synchronisees sur tous vos appareils avec [Dropbox](https://www.dropbox.com/)
  * vos notes accessibles par toute application sur n'importe quelle plateforme, puisque constituees de simples fichiers texte

Apres avoir essaye [Springpad](http://www.springpad.com), [Simplenote](http://simplenote.com/), [Evernote](https://evernote.com/) et de nombreuses autres solutions pour prendre des notes de maniere efficace, j'ai fini par realiser que rien ne pouvait remplacer la rapidite, la versatilite, la perennite et le plaisir d'utiliser de simples fichiers texte.

Le desir d'efficacite m'a pousse vers la meilleure solution a ce jour sur Mac : nvALT de [Brett Terpstra](http://brettterpstra.com/).

Si vous aimez prendre des notes et que vous etes sur Mac, c'est incontournable, comme vous allez vous en rendre compte.

## Principaux avantages de nvALT

fork[1](http://aya.io/blog/nvalt-prise-de-notes/) du deja tres bon [Notational Velocity](http://notational.net/fr/), **nvALT** possede de nombreux avantages :

  * vitesse : application ultra reactive, meme sur une machine modeste
  * implementation markdown avancee
  * une interface graphique mais une philosophie hacker
  * bonne qualite de previsualisation et export
  * interface speciale amoureux du clavier
  * openmeta tags pour tri et recherche (mdfind, spotlight, meta indexeurs)
  * prise de note immediate, jamais aucun delai
  * on peut ouvrir une note dans un autre editeur a tout instant
  * inutile de penser a enregistrer, c'est automatique et instantane

### Pourquoi pas une base de donnees ?

La plupart des logiciels de prise de notes enregistrent celles-ci dans un format qui leur est propre, souvent de maniere compressee et encodee dans une base de donnees ([BDD](http://fr.wikipedia.org/wiki/Base_de_donn%C3%A9es)).

Ce principe souffre de nombreux defauts. Parmi les principaux :

  * fragile : une BDD encodee est susceptible d'etre corrompue par un bug ou une mauvaise manipulation
  * binaire : la BDD est illisible en dehors d'une application qui en comprend le format
  * pas portable : si personne n'a cree d'outil pour exporter le contenu de votre BDD vers un autre format, vous etes enfermes
  * pas perenne : que deviennent vos notes si le logiciel qui cree et lit la BDD n'existe plus ?
  * exige une maintenance : les logiciels evoluent, le format de la BDD aussi, d'ou mises a jour fastidieuses et pouvant occasionner de nouveaux bugs

Une BDD pour ses notes peut etre utile dans certains cas[2](http://aya.io/blog/nvalt-prise-de-notes/) : si vous avez d'enormes quantites de donnees a traiter, donnees ayant les memes champs et tags, alors manipuler plusieurs milliers de fichiers n'est _peut-etre_ pas le bon choix. A vous de voir.

Personnellement je n'en suis absolument pas certain : avec des outils Unix et des scripts Bash ou Ruby, on fait des merveilles sur des fichiers, meme en surnombre.

### Pourquoi ecrire en Markdown ?

C'est comme ecrire en langage naturel, avec simplement quelques variations tres faciles a retenir.

Et c'est un format texte, compatible avec tout, facilement exportable en pdf, doc, html, etc.

Une fois le texte ecrit, on peut varier l'habillage visuel independamment du contenu.

Les avantages sont nombreux !

On peut se referer a [Markdown Guide](http://bywordapp.com/markdown/guide.html) (en anglais) ou [Markdown Wikipedia](http://fr.wikipedia.org/wiki/Markdown) (en français).

Le mode fichiers texte permet d'etre accessible par un grand nombre d'apps, y compris sur appareils mobiles.

Surtout : les fichiers texte en Markdown, c'est _universel_ et pare pour le futur (contrairement a mes vieux fichiers des annees 80, sniff).

![](https://www.evernote.com/shard/s89/sh/6b594b93-cf66-4b66-b8ae-2f8e44dbf287/527fdc44b4e82a1a094589a5149715ea/deep/0/nvalt-prise-de-notes.jpg)

> _Pourquoi pas un traitement de texte ?_

Utiles au bureau, quoi que de moins en moins, [LibreOffice](https://www.libreoffice.org/) ou [MSWord](https://office.microsoft.com/) sont totalement inadaptes a la prise de note : dedies au traitement de longs textes et lourds en fonctions telle collaboration ou revisions, pour la prise de notes rapide c'est enfoncer un clou avec un engin de chantier !

De plus, le format doc est ferme… et payant ! A moins de pirater le produit, il faut debourser… franchement, de nos jours il est devenu inutile de se livrer a ce jeu.

Word n'est meme pas utile pour l'ecriture de textes courts ou moyens, il y a des outils mille fois meilleurs ([Scrivener](http://www.literatureandlatte.com/scrivener.php) par exemple).

## Installation et configuration

### L'essentiel

nvALT est une application facile a installer : telechargez-la [en bas de la page](http://brettterpstra.com/projects/nvalt/) puis deplacez-la dans le dossier Application.

Vous pouvez commencer a l'utiliser.

Mais si vous voulez aller encore plus loin dans la productivite, plus tard, apres vous etre familiarise avec cet outil, je vous conseille de considerer les liens suivants des maintenant : ça permet de prendre les devants.

### Recommande

  * Si vous prevoyez d'utiliser un systeme d'automatisation des taches tel [Hazel](http://www.noodlesoft.com/hazel.php) (ce que je vous recommande vivement), telechargez [Open Meta](https://code.google.com/p/openmeta/downloads/list), installez la fonction "cachee" OpenMeta pour Hazel, puis installez le binaire et activez la fonction :
    
    
        cd ~/Downloads
        unzip openmeta_commandline_1.3.0.zip
        sudo chown u=rw /usr/local/bin
        mv openmeta /usr/local/bin
        defaults write com.noodlesoft.Hazel OMToolPath /usr/local/bin/openmeta
    

  * [L'extension](http://elasticthreads.tumblr.com/post/8212672178/nvit-chrome-and-safari-extensions-for-nvalt) pour le navigateur Chrome (et Safari) est egalement pratique, avec entre autres fonctions la selection d'un texte, d'une URL ou meme du contenu d'une page transcrit en Markdown, envoye directement a nvALT en tant que nouvelle note. Il y a aussi un [bookmarklet](http://jots.mypopescu.com/post/8529405944/nvalt-bookmarklet) pour Firefox.

### Configuration

  * Dans les preferences, choisissez la gestion par fichiers texte et indiquez ou se trouve votre dossier de notes dans Dropbox
![Fichiers, Dropbox, extensions](https://www.evernote.com/shard/s89/sh/1d1dce8a-1db6-4abe-8cf2-ed289dd742d3/1f192c6cc9f7d5e9fa185960e9a7567e/deep/0/Notes.jpg)

> _Fichiers, Dropbox, extensions_

  * [Ajoutez](http://faceofgeoff.com/post/9665888623/nvalt-quick-tip-making-markdown-readable-and-your) les bons types d'extensions de fichier (nvALT ne met pas d'extension a ses fichiers textes, mais effectuer cette operation lui permet de lire tous les fichiers markdown que l'on copie dans son dossier notes a partir de l'exterieur)

  * Reglez quelques options

![Options d'édition](https://www.evernote.com/shard/s89/sh/82ccea41-1213-49cc-b27a-560e5597123a/e2f9e19ce8a78478b039bc865e25fe7c/deep/0/Editer.jpg)

> _Choisissez une presentation horizontale ou verticale_

  * Choisissez vos themes et couleurs
![Polices et couleurs](https://www.evernote.com/shard/s89/sh/47065da6-a7b9-455d-bbe9-e374ce58dcdc/224e495255f8b9ba9a33f3cb6010a48f/deep/0/Polices/Couleurs.jpg)

> _Polices et couleurs_

### Importer ses notes

Si vous preniez vos notes dans un autre format ou logiciel et que vous faites le grand saut vers le mode hacker, vous pourrez trouver quelques utilitaires et scripts interessants pour recuperer vos notes et les exporter en Markdown.

On trouve egalement quelques scripts sh/python/ruby sur [github](https://github.com/) pour exporter et transformer quelques formats de notes particuliers.

## Pour commencer

### Principe de base

**Il n'y a pas de bouton "+" ou "Nouvelle note", pas plus que de bouton "Rechercher".**

_Une fois l'application active[3](http://aya.io/blog/nvalt-prise-de-notes/) on commence tout de suite a ecrire dans la zone de titre._

![Nouvelle note](https://www.evernote.com/shard/s89/sh/b5a220a7-83e1-4ab9-b300-03c8f96f1151/7dada37c05fb4ae8219667b622cda7bc/deep/0/nvALT.jpg)

> _Nouvelle note_

Au fur et a mesure que l'on tape les premieres lettres du titre, la liste des notes qui contiennent ces caracteres s'actualise en temps reel : si une note existe deja avec ce titre on peut l'editer en appuyant sur Entree ou apres avoir navigue avec les fleches du clavier.

![Liste des notes](https://www.evernote.com/shard/s89/sh/b2e3c819-b1f5-4e4b-bc8e-1d86eb989218/30bafb2433584b98c13e7c194a3280aa/deep/0/nvALT.jpg)

> _Si l'on continue de taper et que le titre devient unique, la note le devient aussi et est automatiquement creee._

Le titre ecrit, en appuyant sur Entree le curseur est deplace dans la zone principale et on peut commencer a ecrire le corps du texte.

### Raccourcis clavier

nvALT est pensee pour les amoureux du clavier et ceux qui veulent toucher la souris le moins possible.

En effet, que ce soit pour des raisons de sante (traumatismes repetes au poignet) ou simplement de productivite, il vaut mieux eviter de trop souvent manipuler la souris : les raccourcis permettent de travailler rapidement sans avoir a bouger les mains hors du clavier.

_Liste des principaux raccourcis clavier de nvALT :_

  * **Chercher** ou **creer** une note = `CMD+L` (revient a se placer dans la barre principale)

  * **Supprimer** une note = `CMD+DEL` (mais je deconseille de supprimer, il vaut mieux archiver)

  * **Tagger** une note (ajouter des mots-cles) = `SHIFT+CMD+T` (attention, la liste de tags, separes par une virgule, est selectionnee par defaut : ne pas l'effacer par erreur, d'abord faire `fleche droite` avant d'ajouter des tags)

  * **Renommer** une note = `CMD+R`

  * **Inserer** un lien = `SHIFT+CMD+L`

  * **Afficher** la fenetre de previsualisation = `CTRL+CMD+P`

  * **Editer** la note dans un logiciel externe = `SHIFT+CMD+E`

## Organiser ses notes

La maniere d'organiser ses notes est un vaste sujet et meriterait d'y consacrer une oeuvre a part entiere.

De grands esprits se sont penches sur la question et on mis au point des techniques efficaces, toutes differentes et dignes d'interet : [Getting things done](http://fr.wikipedia.org/wiki/Getting_Things_Done), [Inbox zero](http://inboxzero.com/), etc.

Personnellement, je me "contente" d'utiliser un systeme de classement a la fois semantique et completement libre et anarchique.

En effet, la recherche et les tags dans nvALT sont une fonction si puissante et rapide qu'il suffit de bien tagger et titrer ses notes pour les retrouver en un instant.

### Conventions dans les titres

Une des meilleures manieres de s'organiser est de mettre la date en debut ou fin de titre, ce qui autorise une recherche aisee pour plus tard.

Mais taper manuellement la date a chaque fois est tres desagreable et source d'erreurs. Je recommande fortement l'utilisation de cette merveille qu'est [TextExpander](http://www.smilesoftware.com/TextExpander/index.html) qui vous permettra d'inserer la date et/ou l'heure en tapant deux ou trois lettres seulements.

Je prefere pour mon usage personnel utiliser uniquement un nombre restreint de mots-cles dans mes titres.

Ils correspondent a des categories plus generales que les tags, ou a des declencheurs pour Hazel.

Exemples : `@post`, `@email`, `@logins`, `@list`, `@critique`, `@edito`, `@tuto`, `@phone`, `@links`, etc.

Je les fais preceder d'un `@` pour les retrouver plus facilement.

Si une note doit rester au top de la liste pour que je me souvienne de la traiter, je peux mettre un `#` au debut du titre : `#urgent`, `#anniv`, `#work`, etc.

L'usage de l'anglais est recommande, les mots sont plus courts et synthetiques.

Bien sur ça marche aussi en français, il est simplement moins facile de rester coherent a cause des accents et de l'orthographe plus complexe.

**Attention** a ne pas surcharger vos titres avec des mots-cles, les… mots-cles sont la pour ça !

### Meta tags

**Un reflexe a prendre rapidement dans nvALT est de tagger votre note avant d'oublier de le faire**.

J'aime tagger mes notes en deux temps : immediatement apres avoir entre le titre et le debut du contenu, puis a la fin avant de passer a autre chose.

Avec le raccourci `SHIFT+CMD+T` vous ajoutez des tags en les separant par une virgule.

Vous pouvez tagger de maniere plus large que dans les titres, il n'y a pas de limites.

Je recommande neanmoins de respecter une certaine voie du milieu : une grosse dizaine de tags maximum par note semble raisonnable.

Les tags peuvent representer des categories, des index, des genres, des mots-cles semantiques, bref, tout ce que vous souhaitez.

Le genre de tag que j'utilise souvent :
    
    
    food, films, blog, work, app, list, link, email
    podcast, article, webpage, image, mp3, text
    idea, dev, citation, book, ebay, snippet
    css, php, ruby, jade, tuto, flow
    space, philo, physics, ref, galaxy
    sandwich, cronenberg, tech, racc, song
    perso, reminder, where-keys, when-meeting
    todo, done, archive, null, wtf, cool
    

### Liens inter notes

**Une fonction simple a utiliser qui permet de classer ses notes : les liens inter-notes**.

Il suffit de taper deux fois un crochet carre gauche (`[`, sous le `5`), ce qui est immediatement transforme en double crochet `[[]]` grace a l'auto-completion, et de continuer a taper le titre d'une note : les titres correspondants s'affichent sous le curseur et permettent de choisir la note a laquelle on veut referer.

Exemple : `[[@food riz au lait 07/04/2013]]` est un lien vers la note ayant le titre "@food riz au lait 07/04/2013.txt". Je n'ai eu qu'a taper deux fois le crochet puis '@food' pour voir apparaitre une liste de fichiers a referencer (puisque je place ce tag au debut de toutes mes recettes completes).

Cela permet de creer aisement un systeme de chapitrage a partir de notes independantes.

Vous pouvez par exemple creer une note qui contiendra uniquement des appels a d'autres notes, comme une table des matieres : l'index des recettes taggees 'dessert', les chapitres de votre futur roman, les grandes lignes de vos examens d'histoire, rassembler des notes par theme pour un article a publier, etc.

Vous pouvez egalement vous laisser porter au gre de vos inspirations et ecrire des references au fur et a mesure que vous accumulez les notes : il sera toujours facile ensuite de creer une nouvelle note contenant tous les liens grace a une recherche sur vos tags.

On peut placer un lien inter-notes a n'importe quel endroit du texte.

## Recherche de notes

### Dans nvALT

**Rien de special a faire, si les notes sont bien titrees et taggees, il suffit de commencer a ecrire dans la barre de titre et les notes concernees apparaissent en temps reel.**

C'est un des gros atouts de nvALT : une reactivite exemplaire et une recherche intuitive.

### En dehors de nvALT

Une simple recherche dans Spotlight fait apparaitre les notes. De meme dans le Finder, bien sur.

Dans le Terminal, avec `mdfind` (commande pour Spotlight):
    
    
    mdfind @food
    mdfind Janvier
    

Brett Terpstra a de bonnes idees de fonctions a placer dans `~/.bashrc` ou `~/.zshrc`. Je les ai simplifiees :
    
    
    fbox () { mdfind -onlyin ~/Dropbox "$1";}
    fposts () { mdfind -onlyin ~/Dropbox/articles "$1";}
    fnotes () { mdfind -onlyin ~/Dropbox/Notes "$1";}
    

mais vous pouvez trouver les originales quelques part au fond de son blog…

## Previsualisation Markdown

nvALT inclut une fenetre flottante pour previsualiser le rendu de votre document.

![Prévisualisation nvALT](https://www.evernote.com/shard/s89/sh/5a820308-00f6-4cea-ba3a-b0f7d43e6882/f117db887cc9a42b9bb88df85ccae21e/deep/0/Capture%20d%E2%80%99e%CC%81cran%202013-04-06%20a%CC%80%2002.33.58.jpg)

> _On la fait apparaitre avec le raccourci clavier_

`CTRL+CMD+P`.

Il est possible de personnaliser l'apparence du document dans cette fenetre avec du CSS.

Integrez le CSS de votre blog ou ebook a nvALT pour avoir un aperçu de ce que donnera votre document[4](http://aya.io/blog/nvalt-prise-de-notes/).

On peut egalement visualiser le document dans [Marked](http://markedapp.com/) avec `SHIFT+CMD+E` a condition d'avoir choisi Marked comme application a la place de l'editeur externe dans les preferences de nvALT.

## Export

Un des grands avantages de prendre ses notes en Markdown est que la mise en forme est separee de la structure.

Le document Markdown existant, il est facile ensuite de lui appliquer des styles differents et de l'exporter dans un grand nombre de formats.

Bien sur le format d'exportation de base est le HTML, mais nvALT excelle a l'export de PDF et permet egalement de sortir ses notes en DOC (format MS Word), RTF (Rich text format) et TXT (simple texte).

De plus, en choisissant [Marked](http://markedapp.com/) comme editeur externe dans les preferences, vous beneficiez de la grande richesse en options d'exportation que possede cette app.

## Tri et archivage

### Automatismes

Comme vous avez installe Open Meta, vos tags sont partageables par toutes les applications qui reconnaissent ce format ouvert : aujourd'hui, c'est [Hazel](http://www.noodlesoft.com/hazel.php) qui nous interesse.

Nous pouvons par exemple decider qu'une note peut devenir obsolete, mais que l'on ne veut pas l'effacer pour autant : on pourra alors lui ajouter un tag "archive".

Avec Hazel, je peux creer une action qui va archiver cette note dans un dossier de backup des que j'entre le mot-cle :

![Hazel : déplace vers archive](https://www.evernote.com/shard/s89/sh/0edf1d29-517b-41a5-a17a-f44a43c33225/5fbd6103db5a16dd50f806cfe1e333c6/deep/0/Capture%20d'%C3%A9cran%2006/04/13%2004:22.jpg)

> _Hazel : deplace vers archive_

Autre cas typique : j'ai souvent dans nvALT une note qui a evolue et qui rassemble dorenavant assez d'elements pour pouvoir commencer a rediger un texte a part entiere.

Elle passe alors de _note_ a _brouillon_ dans mon esprit : aussitot je la tagge avec `SHIFT+CMD+T` avec le mot-cle de mon choix, ici `post` ou `brouillon` par exemple.

Grace a Hazel, je peux faire une action automatique qui, lors du changement de mot-cle, va deplacer le document dans mon dossier Brouillons et immediatement l'ouvrir dans un autre editeur, [Mou](http://mouapp.com/) par exemple :

![Hazel : déplace vers autre éditeur](https://www.evernote.com/shard/s89/sh/a47c7b15-6953-4ccd-861f-95644bb996b9/8366339e4e308f0c804e381f18e2e9c4/deep/0/Capture%20d%E2%80%99e%CC%81cran%202013-04-06%20a%CC%80%2003.53.39.jpg)

> _Hazel : deplace vers autre editeur_

## Mode auteur

On peut configurer nvALT pour le mettre dans un etat que j'appelle le mode _auteur_, c'est-a-dire sans distractions et concentre sur le texte.

Avec `SHIFT+CMD+C` on cache la liste des notes, puis avec `SHIFT+CMD+F`on passe en contraste faible, on cache la preview si elle est affichee avec `CTRL+CMD+P` et enfin avec `CTRL+CMD+F` on entre en plein ecran.

Cependant, meme si ça marche bien dans nvALT, je prefere l'utiliser uniquement pour des petits documents, des notes.

Pour ecrire des articles longs, des textes complets, je prefere utiliser un editeur dedie.

Par exemple [Scrivener](http://www.literatureandlatte.com/scrivener.php) pour un scenario, des dialogues, un roman ; [Sublime Text 2](http://www.sublimetext.com) pour du code ; [Mou](http://mouapp.com/) pour un article de blog ou un editorial, etc.

![Mou](https://www.evernote.com/shard/s89/sh/0a7daf5c-fd65-4be3-8887-760b0ae1f7f9/d28a1cc19f784ad1c48b71e19ae0af40/deep/0/nvalt-prise-de-notes.jpg)

> _Il est egalement facile d'utiliser Marked avec ces apps._

## Astuces

### Astuces Markdown

#### Rappel/fondamentaux

  * Deux fois `Entree` = nouveau paragraphe

  * `>` ou `tab` puis votre texte = citation

  * `#`= titre

  * `##` = sous-titre

  * `###` = section

  * `[texte](lien)` = lien vers URL

  * `*texte*` ou `_texte_` = texte en _italique_

  * `**texte**` ou `__texte__` = texte en **gras**

#### Inserer une image

Pour faire un lien vers une image il suffit d'ajouter un `!` devant la formule habituelle servant a creer un lien :
    
    
    ![texte](lien)
    

On peut egalement faire un **drag-n-drop** (glisser-deplacer) du Finder (ou de PathFinder) vers le corps de la note, un lien sera automatiquement cree.

Lien : [explications](http://brettterpstra.com/2012/09/27/quick-tip-images-in-nvalt/) (en anglais) pour beneficier des liens relatifs dans les notes.

#### Markdown service tools

Brett Terpstra a cree les [markdown service tools](http://brettterpstra.com/projects/markdown-service-tools/), un ensemble de services pour OSX accessibles par toutes les applications.

Vous selectionnez une partie de votre texte, et un service se charge d'y appliquer une action.

Par exemple : avec "Auto search link", vous selectionnez un ou plusieurs mots, actionnez ce service, et nvALT transforme le mot en lien avec le resultat de la recherche de Google.

### Mode todo list

Meme si je gere mes taches et toutes mes TODO list dans [Wunderlist](http://www.6wunderkinder.com/wunderlist), j'aime bien de temps en temps me laisser des reminder dans mes notes.

Dans ce cas j'ai un systeme tout simple : je tagge avec `todo` toutes les notes qui contiennent une tache a effectuer mais qui ne sont pas urgentes (la plupart du temps ce sont des references a chercher).

Chaque week-end je mets de l'ordre dans mes documents, et j'en profite pour afficher toutes les notes contenant `todo` et je change le tag en `done` ou `archive` pour celles qui sont accomplies.

Une action Hazel se charge de deplacer les notes concernees dans un dossier d'archive.

## Apps iOS et Android

La plupart des apps mobiles de prise de notes qui fonctionnent avec Dropbox vous obligent a utiliser leur propre dossier predefini pour stocker vos notes. Ce n'est pas acceptable.

Parmi les rares apps qui permettent de choisir un dossier personnel, la seule qui soit vraiment de qualite sur iOS est [Drafts](http://agiletortoise.com/drafts).

Et la seule sur Android, pour les memes raisons, est… [Draft](https://play.google.com/store/apps/details?id=com.mvilla.draft).

_**Update** \- Drafts pour iOS est une formidable application mais n'est pas si bien adaptee que ça a notre workflow avec nvALT et Dropbox. Il vaut mieux utiliser un bon editeur [iOS](http://aya.io/blog/editeurs-de-texte-osx-ios/)._

![](http://aya.io/blog/images/elements-small.jpg)

## Aller plus loin

  * On peut approfondir les automatismes avec [Keyboard Maestro](http://www.keyboardmaestro.com/main/) ou tout simplement ses propres AppleScripts.
  * nvALT n'existe que sur OSX, mais il y a des outils bases sur la meme philosophie sur chaque plateforme. De plus, [Notational Velocity](http://notational.net), l'ancetre de nvALT, est disponible pour Linux et Windows.
  * On peut etendre sa gestion des notes a [Omnifocus](https://www.omnigroup.com/applications/omnifocus/), [DayOne](http://dayoneapp.com/), etc.
  * Hazel copie mes notes vers [Google Drive](https://drive.google.com/) pour un backup supplementaire.
  * Des automatismes avec [ifttt](http://www.ifttt.com) ou [zapier](https://zapier.com/) permettent d'uploader automatiquement ses notes a partir de Dropbox vers un autre service[5](http://aya.io/blog/nvalt-prise-de-notes/).

## Liens en vrac

## Credits

  1. nvALT propose en option de fonctionner avec une base de donnees au lieu de fichiers texte. Meme si l'application reste agreable a utiliser dans ce cas, ça reste une gestion "a l'ancienne" avec un format que l'on ne peut pas utiliser en dehors de l'application qui le produit. [↩](http://aya.io/blog/nvalt-prise-de-notes/)

  2. click sur son icone dans le dock ou dans la menubar, active par ALT/TAB, par son raccourci clavier, etc [↩](http://aya.io/blog/nvalt-prise-de-notes/)

  3. vous pouvez egalement telecharger des themes predefinis : [Byword](http://bywordapp.com/extras/index.html), [iAwriter](https://github.com/moritzz/iAWriterCSS), [play with Marked](http://www.candlerblog.com/2012/02/29/marked-as-css-playground/) [↩](http://aya.io/blog/nvalt-prise-de-notes/)
