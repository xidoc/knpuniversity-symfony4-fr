# Symfony 4: Let's Launch!

Salut les gars ! Oui! C'est l'heure de Symfony 4! Je suis *si* excité. Pourquoi? Parce que *rien* 
ne me rend plus heureux que de m'asseoir pour travailler à l'intérieur d'un cadre où le codage est en fait
*fun*, et où je peux construire des fonctionnalités rapidement, mais *sans* sacrifier la qualité. Eh bien,
peut-être que je serais encore plus heureux de faire tout ça sur une plage... avec, peut-être, une boisson fraîche ?

Quoi qu'il en soit, Symfony 4 a complètement réimaginé l'expérience développeur: vous allez
créer de meilleures fonctionnalités, plus rapide que jamais. *Et*, Symfony a un *nouveau*, unique
super pouvoir: il démarre comme un microframework, puis s'adapte automatiquement en taille
au fur et à mesure que votre projet prend de l'ampleur. Comment ? Restez à l'écoute....

Oh, et je n'ai pas mentionné que Symfony 4 est la version la plus rapide? Et le framework
PHP le plus rapide? Honnêtement, *tous* les frameworks sont assez rapides de toute façon, mais l'intérêt
est ceci: vous construisez sur une fondation vraiment magnifique.

***TIP
Voir http://www.phpbenchmarks.com pour les stats du benchmark!
***

## Prep: Télécharger & mettre à jour Composer

Ok, commençons tout de suite! Ouvrez un nouveau terminal et déplacez-vous dans le dossier
que vous voulez. Soyez sûr que vous avez déjà [Composer](https://getcomposer.org/) installé
globalement donc que vous pouvez juste dire `composer`. Si vous avez des questions, poser les nous
dans les commentaires!

Et *aussi* soyez sûr que vous ayez la dernière version:

```terminal-silent
composer self-update
```

C'est important : Composer a récemment corrigé un bug pour aider Symfony.

## Installer Symfony!

Pour télécharger votre nouveau projet Symfony, exécuter `composer create-project symfony/skeleton`
et le déplacer dans un nouveau dossier appelé `the_spacebar`.

```terminal-silent
composer create-project symfony/skeleton the_spacebar
```

C'est le nom de notre projet! "The Spacebar" sera *le* lieu où les gens 
*de toute* la galaxy pourront communiquer, partager des nouvelles et discuter au sujet des célébrités
et du BitCoin. Ça va être extraordinaire!

Cette commande clone le projet `symfony/skeleton` et alors exécute `composer install`
pour télécharger ses dépendances.

Plus bas, il y a quelque chose de *special*: quelque chose à propos des "recipes". OooOOO.
Recipes sont un nouveau et très important concept. Nous parlerons de lui dans quelques minutes.

## Démarrage du serveur web

Et en bas, cool! Symfony nous donne des instructions claires de ce que fait
la suite.Déplacez-vous dans le nouveau dossier:

```terminal-silent
cd the_spacebar
```

Apparemment, nous pouvons exécuter notre application en exécutant:

```terminal
php -S 127.0.0.1:8000 -t public
```

Cela démarre le web serveur construit en PHP, lequel est *bon* pour le  développement. `public/`
est le document root du projet - mais on en saura plus bientôt!

***TIP
Si vous voulez utiliser Nginx ou Apache pour un développement local, vous pouvez voir
http://bit.ly/symfony-web-servers.
***

C'est l'heure de décoller! Va sur ton navigateur et entre `http://localhost:8000`. Dit
hello à ta nouvelle application Symfony!

## Notre petit projet

***TIP
Symfony ne crée plus de répertoire git automatiquement pour vous. Mais, pas de problème!
Tapez simplement `git init` une fois pour initialiser votre répertoire.
***

Retourner dans le terminal, je créerai un nouveau onglet. Symfony *a déjà* inititalisé
un nouveau répertoire git pour nous *et* nous donne un fichier parfait `.gitignore`. Merci Symfony!

***TIP
Si tu es en train d'utiliser PhpStorm, vous voudrez ignorer le dossier `.idea` de git. Je l'ai déjà
ignoré dans mon fichier global .gitignore : https://help.github.com/articles/ignoring-files/
***

Cela signifie que nous pouvons créer notre *premier* commit juste en disant:

```terminal
git init
git add .
git commit
```

Créer un message calme et bien pensé du commit

```terminal-silent
# Woohoo! OMG WE ARE USING SYMFONY4
```

Woh! Vérifions cela: le projet entier - *incluant* Composer et `.gitignore`
n'est que de 16 fichiers! Notre application est minuscule!

Allons apprendre plus sur notre prochain projet *et* installons notre éditeur pour faire
du développement magnifique en Symfony!
