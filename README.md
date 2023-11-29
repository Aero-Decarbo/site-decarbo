Ce site web est réalisé avec le générateur de site statique [Nikola](https://getnikola.com).

Le site est prévu pour être entièrement bilingue, en français et en anglais.


# Installation

Pour installer l’environnement nécessaire pour faire fonctionner cet outil, veuillez commencer par installer Python 3, puis suivre la première étape de [ce tutoriel](https://getnikola.com/getting-started.html). Comme le recommande le tutoriel, nous vous recommandons également d’utiliser un environnement virtuel pour Python, et de commencer par lire [ce tutoriel](https://chriswarrick.com/blog/2018/09/04/python-virtual-environments/) si vous n’êtes pas familier avec les environnements virtuels.

Ensuite, à chaque fois que vous voulez utiliser Nikola, il vous faudra commencer par réactiver l’environnement virtuel dans votre terminal.

Pour éditer les fichiers, un éditeur de texte basique suffit, mais vous pouvez évidemment utiliser un environnement de développement si vous préférez.



# Modifications

Après toute modification, il faut lancer la commande `nikola build` pour mettre à jour le site, puis `nikola serve --browser` pour lancer un serveur web local vous permettant de consulter le site dans votre navigateur. 

## Déploiement

Après les commandes précédentes, vos modifications n’existent que sur votre ordinateur. Pour les déployer sur l’hébergement Github Pages que nous utilisons actuellement, une commande est prévue de base dans Nikola : `nikola github_deploy`.

Comme expliqué dans [le manuel de Nikola](https://getnikola.com/handbook.html#deploying-to-github), cette commande bascule sur une nouvelle branche de votre projet Git nommée `gh-pages` dans laquelle elle vient déposer les fichiers du site via un commit automatique, puis elle pousse ces modifications vers Github. Avant de faire cela, il est préférable de committer de votre côté les modifications du code source (branche `src`) avec un message explicite quant aux modifications que vous avez réalisées.


## Contenu :

Le contenu est rédigé soit en [Markdown](https://www.markdownguide.org/basic-syntax/) pour une mise en forme basique, soit en [reStructuredText](https://docutils.sourceforge.io/docs/user/rst/quickref.html) pour une mise en forme plus avancée (par exemple plusieurs colonnes ou du centrage). Cela se voit à l’extension du fichier : `.md` pour Markdown, `.rst` pour reStructuredText. Veuillez consulter les documentations dans les liens ci-dessus pour l’utilisation de la syntaxe de ces langages. Cette documentation est elle-même rédigée en Markdown.

Vous pouvez également vous inspirer des pages déjà créées.

### Modifier un article ou une page existante

Toutes les pages sont dans le dossier `pages`. Tous les articles de blog sont dans le dossier `posts`. Il est possible de faire des sous-dossiers si besoin. Pensez à modifier également la version anglaise (voir ci-dessous).

### Ajouter une nouvelle page

Utilisez la commande `nikola new_page`. Remplissez tous les champs demandés dans le terminal (sans vous prendre la tête, tout sera modifiable ultérieurement). Pensez à traduire la page nouvellement créée (voir ci-dessous).

### Ajouter un article de blog

Utilisez la commande `nikola new_post`. Remplissez tous les champs demandés dans le terminal (sans vous prendre la tête, tout sera modifiable ultérieurement). Pensez à traduire l’article nouvellement créé (voir ci-dessous).

### Traduction

Actuellement, le paramètre pour le chemin des traductions est : `TRANSLATIONS_PATTERN = "{path}.{lang}.{ext}"`. Cela signifie que si vous avez créé la page `mapage.md`, vous devrez mettre la traduction anglaise à `mapage.en.md`. Cela ne signifie pas que l’URL sera ensuite `mapage.en.html` puisque l’URL est modifiable dans les métadonnées en en-tête du fichier, vous pourrez donc la modifier en `mypage.html`. Il s’agit du champ `slug`.

### Images

À des fins de sobriété numérique, il est recommandé, si vous utilisez une image qui ne va être utilisée qu’une seule fois, de la redimensionner préalablement afin de l’inclure directement à la bonne taille. Cela vous évite également de galérer avec Markdown qui n’offre pas de moyen de redimensionner les images sans inclure du HTML.


## Graphismes

Nous utilisons un thème personnalisé nommé `theme-decarbo`. Les fichiers correspondants se situent dans le dossier `themes`.

Ce thème hérite du thème par défaut `bootblog4`, un thème de blog responsive basé sur bootstrap. La liste des thèmes par défaut disponibles pour Nikola est [ici](https://themes.getnikola.com/). 

Pour modifier les polices, les couleurs… c’est dans le fichier `assets/theme-decarbo.css`.

Pour modifier la structure de la page, c’est dans le dossier `templates`.

Pour les traductions de texte dans les différentes langues, c’est dans le dossier `messages`.

Les principales modifications effectuées par rapport au thème `bootblog4` :
- Ajout des icônes réseaux sociaux dans `templates/base.tmpl` et des bons liens dans une nouvelle variable `SOCIAL_LINKS` de `conf.py`, utilisation de `messages` pour les alt text des icônes
- Traduction : ajout des icônes de drapeaux, retrait du texte "Also available in" sur chaque page ou article dont une traduction est disponible mais lien dans l’en-tête vers la bonne page ou le bon article plutôt que vers l’accueil (bloc renommé de "belowtitle" en "translations\_menu" dans `templates/base.tmpl`, ajout des drapeaux dans une version par défaut dans `templates/base_helper.tmpl`, déplacement du header vers le bloc translations dans `templates/post_header.tmpl` et `templates/story.tmpl`)
- Ajout d’un lien vers les mentions légales dans chaque langue en pied de page (modifs dans `templates/base.tmpl`, `templates/base_helper.tmpl` et `messages`)
- Ajout des couleurs du logo Aéro Décarbo (`assets/theme-decarbo.css`).

De façon générale, si vous rajoutez une image au niveau du thème, pensez à lui associer un alt text traduit dans chaque langue via le mécanisme des messages, pour l’accessibilité aux utilisateurs de lecteur d’écran.



## Configuration

Le fichier `conf.py` contient beaucoup de paramètres importants. Consultez-le en parallèle du [manuel Nikola](https://getnikola.com/handbook.html).

C’est également là qu’est la configuration du menu de navigation.


# Licence

Les fichiers du site (code et contenu) sont publiés avec la licence BSD 3 clauses en suivant [les conseils avisés de Nicolas Dao](https://gist.github.com/nicolasdao/a7adda51f2f185e8d2700e1573d8a633). La licence est trouvable dans le fichier LICENSE situé à la racine du dépôt.
