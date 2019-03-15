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
le dossier`Controller` et aller à "New" or presser `Cmd`+`N` on a Mac. Choisir "PHP Class".
Et, oui! Souvenez-vous de l'installation du Composer que nous avons fait dans les Preferences? Grâce à cela, PhpStorm
devine correctement le namespace! La force est avec lui... Le namespace
pour chaque class dans `src/` doit être `App` plus dans le sous-répertoire dans lequel il se trouve.

Nomme cela `ArticleController`:

[[[ code('b80d9887fc') ]]]

Et à l'intérieur, ajoute `public function homepage()`:

[[[ code('87255115fa') ]]]

*Cette* fonction est le controller... et c'est *notre* place pour construire la page. Pour être
plus confus, il est aussi appelé "action", ou "ghob" pour ses amis klingons.

Anyways, we can do *whatever* we want here: make database queries, API calls, take
soil samples looking for organic materials or render a template. There's just *one*
rule: a controller must return a Symfony `Response` object.

So let's say: `return new Response()`: we want the one from `HttpFoundation`. Give
it a calm message: `OMG! My first page already! WOOO!`:

[[[ code('9b6091d1b8') ]]]

Ahem. Oh, and check this out: when I let PhpStorm auto-complete the `Response` class
it added this `use` statement to the top of the file automatically:

[[[ code('8c7baf2d54') ]]]

You'll see me do that a lot. Good job Storm!

Let's try the page! Find your browser. Oh, this "Welcome" page only shows if you
don't have *any* routes configured. Refresh! Yes! This is *our* page. Our first of
*many*.

## Annotation Routes

That was *pretty* easy, but it can be easier! Instead of creating our routes in
YAML, let's use a cool feature called *annotations*. This is an extra feature, so
we need to install it. Find your open terminal and run:

```terminal
composer require annotations
```

Interesting... this `annotations` package *actually* installed `sensio/framework-extra-bundle`.
We're going to talk about how that works *very* soon.

Now, about these annotation routes. Comment-out the YAML route:

[[[ code('aa861906ab') ]]]

Then, in `ArticleController`, above the controller method, add `/**`, hit enter,
clear this out, and say `@Route()`. You can use either class - but make sure PhpStorm
adds the `use` statement on top. Then add `"/"`:

[[[ code('e9f8d1dc4a') ]]]

That's it! The route is defined *right* above the controller, which is why I *love*
annotation routes: everything is in one place. But don't trust me, find your browser
and refresh. It's a traaaap! I mean, it works!

***TIP
What *exactly* are annotations? They're PHP comments that are read as configuration.
***

## Fancy Wildcard Routes

So what else can we do with routes? Create another public function called `show()`.
I want this page to eventually display a full article. Give it a route:
`@Route("/news/why-asteroids-taste-like-bacon")`:

[[[ code('cae709ac9c') ]]]

Eventually, this is how we want our URLs to look. This is called a "slug", it's
a URL version of the title. As usual, return a
`new Response('Future page to show one space article!')`:

[[[ code('7ba5de7f42') ]]]

Perfect! Copy that URL and try it in your browser. It works... but this sucks!
I don't want to build a route and controller for *every* single article that lives
in the database. Nope, we need a route that can match `/news/` *anything*. How?
Use `{slug}`:

[[[ code('d572f8cdbc') ]]]

This route *now* matches `/news/` anything: that `{slug}` is a *wildcard*. Oh, and
the name `slug` could be anything. But whatever you choose now becomes available
as an *argument* to your "ghob", I mean your action.

So let's refactor our success message to say:

> Future page to show the article

And then that slug:

[[[ code('f97fda18bb') ]]]

Try it! Refresh the same URL. Yes! It matches the route *and* the slug prints!
Change it to something else: `/why-asteroids-taste-like-tacos`. So delicious!
Go back to bacon... because... ya know... everyone knows that's what asteroids
*really* taste like.

And... yes! We're 3 chapters in and you *now* know the first *half* of Symfony:
the route & controller system. Sure, you can do fancier things with routes, like
match regular expressions, HTTP methods or host names - but that will all be pretty
easy for you now.

It's time to move on to something *really* important: it's time to learn about Symfony
Flex and the *recipe* system. Yum!
