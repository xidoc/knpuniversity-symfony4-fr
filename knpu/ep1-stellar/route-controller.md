# Routes, Controllers, Pages, oh my!

Allons créer notre *première* page! Actuellement, cela est le job *principal* d'un framework:
te donner un système de *route* et de *controller*. Une route est la configuration qui definit
l'URL pour une page et un controller. C'est une fonction que *nous* écrivons qui *en fait*
construit le contenu pour cette page.

Et tout de suite... notre application est *réellement* petite! Au lieu d'alourdir votre projet
avec *toutes* les fonctionnalités dont vous avez besoin- après tout, nous ne sommes *pas* en
apesanteur - une application Symfony est basiquement juste un petit système de route-controller.
Plus-tard, nous installerons plus de fonctionnalités quand nous en aurons besoin, comme un moteur de distorsion! C'est toujours pratique.
Ajouter plus de fonctionnalités va être assez impressionnant. On en reparlera plus tard.

## Première Route & Controller

Ouvrez le fichier de routage principal de votre application: `config/routes.yaml`:

[[[ code('ca7e7b48e4') ]]]

Hey! Nous avons déjà un exemple! Décommentez cela. Ignorez la clé `index`  pour l'instant:
c'est le *name* interne de la route, mais ce n'est pas important.
Cela dit que quand quelqu'un va sur la page d'accueil - `/` - Symfony doit executer
une méthode `index()` dans une classe `DefaultController`. Changer cela à `ArticleController`
et la méthode à `homepage`:

[[[ code('f5c6ae0ed2') ]]]

Et... yea! C'est une route! Bonjour route! Il définit l'URL et dit à Symfony quelle
fonction du controller doit être executée.

La classe controller n'existe pas encore, alors créons-la ! Cliquez avec le bouton droit de la souris sur 
le dossier`Controller` et aller à "New" or presser `Cmd`+`N` sur un Mac. Choisir "PHP Class".
Et, oui! Souvenez-vous de l'installation du Composer que nous avons fait dans les Preferences? Grâce à cela, PhpStorm
devine correctement le namespace! La force est avec lui... Le namespace
pour chaque class dans `src/` doit être `App` plus dans le sous-répertoire dans lequel il se trouve.

Nommez cela `ArticleController`:

[[[ code('b80d9887fc') ]]]

Et à l'intérieur, ajoutez `public function homepage()`:

[[[ code('87255115fa') ]]]

*Cette* fonction est le controller... et c'est *notre* place pour construire la page. Pour être
plus confus, il est aussi appelé "action", ou "ghob" pour ses amis klingons(Star Trek).

Quoi qu'il en soit, nous pouvons faire  *tout ce que nous voulons* ici: faire des requêtes de base de données, des appels API, prendre des échantillons de sol à la recherche de matériaux organiques ou rendre une  template. Il y a juste *une*
règle: un controller doit retourner un objet Symfony `Response`.

Donc disons: `return new Response()`: nous voulons celui de `HttpFoundation`. Donnez-lui
un message calme: `OMG! My first page already! WOOO!`:

[[[ code('9b6091d1b8') ]]]

Ahem. Oh, et vérifions cela: quand je laisse PhpStorm auto-complété la class `Response`
il a ajouté cette instruction `use` automatiquement en haut du fichier:

[[[ code('8c7baf2d54') ]]]

Vous me verrez beaucoup faire cela. Good job Storm!

Allons essayer la page! Retrouvez votre navigateur. Oh, cette page "Welcome"  se montre seulement si tu
n'as *aucune* routes configurées. Rafraichit! Yes! Cela est *notre* page. Notre première
*d'une longue série*.

## L'annotation des routes
C'était *plutôt* facile, mais ça peut l'être encore plus! Au lieu de créer notre route dans
YAML, utilisons une fonction cool appelée *annotations*. C'est une fonctionnalité extra, donc
nous avons besoin de l'installer. Trouve ton terminal ouvert et exécute:

```terminal
composer require annotations
```

Intéressant... ce package `annotations` *actuellement* installé `sensio/framework-extra-bundle`.
Nous allons parlé de comment cela fonctionne *très* bientôt.

Maintenant, à propos de ces annotations de routes. Commentez la route YAML:

[[[ code('aa861906ab') ]]]

Ensuite, dans `ArticleController`, au-dessus de la méthode du controller, ajoutez `/**`, appuyez sur entrer,
effacez ceci, et tapez `@Route()`. Vous pouvez utiliser l'une ou l'autre classe- mais soyez sûr que PhpStorm
ajoute l'instruction `use`  au-dessus. Ensuite ajoute `"/"`:

[[[ code('e9f8d1dc4a') ]]]

C'est tout! La route est définie *juste* au-dessus du controller, c'est pourquoi je *préfère*
les annotations de route: tout est au même endroit. Mais ne me croyez pas, retrouvez votre navigateur
et rafraîchissé. C'est un pièèèège! Je plaisante, ça fonctionne!

***TIP
Que sont *exactement* les annotations? Il y a des commentaires PHP qui sont lus comme configuration.
***

## Fancy Wildcard Routes

Alors que pouvons-nous faire avec les routes? Créer une autre fonction publique appelée `show()`.
Je veux que cette page affiche éventuellement un article complet. Donne lui une route:
`@Route("/news/why-asteroids-taste-like-bacon")`:

[[[ code('cae709ac9c') ]]]

En fin de compte, c'est ainsi que nous voulons que nos URLs apparaissent. Cela est appelé un "slug", c'est une version de l'URL du titre. Comme d'habitude, return a
`new Response('Future page to show one space article!')`:

[[[ code('7ba5de7f42') ]]]

Parfait! Copie cette URL et essaye là dans ton navigateur. Ça fonctionne... mais ça craint!
Je ne veux pas construire une route et un controller *pour chaque* article qui est en base de données. Nope, nous avons besoin d'une route qui peut matchée  `/news/` *quelque chose*. Comment?
Utilise `{slug}`:

[[[ code('d572f8cdbc') ]]]

Cette route *maintenant* matche `/news/` quelque chose: que `{slug}` est un *joker*. Oh, et le nom `slug` peut être n'importe quoi. Mais ce que tu choisis maintenant devient maintenant disponible comme un *argument* à ton "ghob", je veux dire ton action.

Donc allons redéfinir notre message de succès pour dire:

> Future page to show the article

Et puis ce slug:

[[[ code('f97fda18bb') ]]]

Essaye! Rafraichit la même URL. Yes! Ça matche la route *et* the slug imprimé!
Change pour autre chose: `/why-asteroids-taste-like-tacos`. C'est si délicieux!
Retourne au bacon... parce que... tu sais... tout le monde sait que les astéroïdes sont 
*très* gouteux.

Et... yes! Nous sommes au chapitre 3 et tu connais *maintenant* la première *moitié* de Symfony:
le système de la route & du controller. Bien sûr, tu peux faire des choses plus intéressantes avec les routes, comme matché les expressions régulières, les méthodes HTTP ou  les noms d'hôtes - mais tout cela sera joliment facile pour toi.

C'est l'heure de bouger sur quelque chose de *vraiment* important: c'est l'heure d'apprendre autour de Symfony
Flexet le système de *recettes*. Yum!
