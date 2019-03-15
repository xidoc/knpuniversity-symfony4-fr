# Notre Micro-App & Mise en place de PhpStorm

Notre mission: aller là où personne n'est jamais allé auparavant... en consultant notre application!
J'ai déjà ouvert le nouveau dossier dans PhpStorm, alors allumez votre tricordeur(outil dans Star Trek qui permet de détecter, enregistrer et analyser) et allons explorer!

## Le Dossier public/

Il y a seulement trois répertoires auxquels vous devez faire attention. Le premier, `public/` est le
document root: donc il contiendra *tous* les* fichiers publiquement accessibles. Et... il y a
un fichier que tu dois connaître maintenant ! `index.php`. C'est le "front controller": un mot fantaisiste que les programmeurs ont inventé qui signifie que c'est le fichier qui est exécuté quand vous allez dans *n'importe quelle* URL.

Mais, *vraiment*, vous n'aurez presque jamais besoin de vous en soucier. En fait, maintenant que nous avons
parlé de ce répertoire, arrêtez d'y penser !

## src/ and config/

Oui, j'ai menti ! Il n'y a *vraiment* que *deux* répertoires auxquels vous devez penser :
`config/`et `src/`. `config/`' contient.... euh... vous savez... des fichiers de configuration et `src/`'.
est l'endroit où vous allez mettre *tout* votre code PHP. C'est aussi simple que ça.

Où est Symfony ? Comme d'habitude, lorsque nous avons créé le projet, Composer a lu notre `composer.json`.
et téléchargé toutes les librairies tierces - y compris des parties de Symfony -, 
dans le répertoire `vendor/`.

## Installation du Serveur

Retournez à votre terminal et trouvez l'onglet d'origine. Regardez cela : en bas,
il dit que nous pouvons obtenir un *meilleur* serveur web en exécutant `composer require server`.
J'aime mieux ! Alors, essayons ! Appuyez sur `Ctrl`+`C` pour arrêter le serveur existant,
et entrez :

```terminal
composer require server
```

Si vous êtes familier avec Composer.... ce nom de paquet peut paraître drôle ! Vraiment,
mauvais! *Normalement*, chaque nom de paquet est "quelque chose" *slash* "quelque chose", comme
"symfony/console". Alors.... `server` ne devrait pas fonctionner ! Mais c'est le cas ! Voici
qui fait partie d'un nouveau système cool appelé Flex. Plus d'informations à ce sujet bientôt !

Une fois ce processus terminé, vous pouvez maintenant exécuter le programme :

```terminal
./bin/console server:run
```

Ceci fait *basiquement* la même chose qu'avant... mais la commande est plus courte. Et
quand nous rafraichissons, ça marche toujours !

D'ailleurs, cette commande `bin/console` va être notre nouveau robot acolyte. Mais
ce n'est *pas* magique : notre projet a un répertoire `bin/` avec un fichier `console` à l'intérieur.
Les utilisateurs de Windows devraient dire `php bin/console`... parce que c'est juste un fichier PHP.

Alors, quelles sont les choses incroyables que ce robot `bin/console` peut faire? Trouve l'onglet de 
ton terminal ouvert, et juste, exécute:

```terminal
./bin/console
```

Oui ! C'est une liste de *toutes* les commandes `bin/console`. Certaines d'entre elles sont du debugging
*en or*. Nous en parlerons en cours de route !

## Mise en place de PhpStorm

Ok, nous sommes *presque* prêts à commencer à coder ! Mais nous devons parler de notre vaisseau spatial,
Je veux dire, éditeur ! Ecoutez, vous pouvez utiliser *tout ce que vous voulez... mais.... Je vous recommande *fortement* 
PhpStorm ! Sérieusement, cela fait du développement de Symfony un *rêve* ! Et non, ces gentils gars et  filles de PhpStorm ne me paient pas pour dire ça... mais ils le peuvent s'ils le veulent !

Hum, si vous *l'utilisez*... ce  serait génial pour vous... il y a 2 secrets
que vous devez savoir pour customiser votre vaisseau spatial, ah, *éditeur* ! Clairement, j'étais en hyper-sommeil
trop longtemps.

Allez dans Preferences, Plugins, puis cliquez sur "Browse Repositories". Il y a 3
plugins indispensables. Cherchez "Symfony". Premièrement : le "Symfony Plugin". Il a plus de
2 millions de téléchargements pour une raison : cela vous donnera des *tonnes* d'auto-complétion
ridicules. Vous devriez également télécharger "PHP Annotations" et "PHP Toolbox". Je les ai déjà installés. Si vous ne le *faites pas*, vous verrez un bouton "Install" à droite.
en haut de la description. Installez-les et redémarrez PHPStorm.

*Ensuite, revenez à Preferences, cherchez "symfony" et trouvez la nouvelle section "Symfony". Cochez la case "Enable Plugin"  : vous devez activer le plugin Symfony.
pour *chaque* projet. Ça dit que vous devez redémarrer... mais je pense que c'est un mensonge. C'est l'espace !
Qu'est-ce qui pourrait mal tourner ?

C'est donc le tour n°1 de PhpStorm. Pour la seconde, recherchez "Composer" et cliquez sur la section
 "Composer". Cliquez pour rechercher le "Path to composer.json" et sélectionnez l'option
Qu'est-ce qui pourrait mal tourner ?

C'est donc le custom n°1 de PhpStorm. Pour la seconde, recherchez "Composer" et cliquez sur la
section "Composer". Cliquez pour rechercher le "Path to composer.json" et sélectionnez l'option
dans notre projet. Je ne sais pas pourquoi ce n'est pas automatique... mais peu importe ! Merci pour cela, PhpStorm facilitera la création de classes dans `src/`. Vous verrez ceci
*vraiment* bientôt.

D'accord ! Notre projet est en place et il fonctionne déjà. Commençons à créer quelques pages
et découvrons d'autres choses intéressantes sur la nouvelle application.
