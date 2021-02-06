---
title: "Allô la doc ?"
date: 2021-01-18
draft: false
author: "liscare"
tags: ["Documentation", "ChartJs", "Français"]
categories: ["Informatique", "Projet"]
page:
    theme: full
featuredImagePreview: "/posts/book.jpg"
summaryStyle:
    hiddenImage: false
    hiddenDescription: false
    hiddenTitle: true
    tags:
      theme: "image"
      color: "white"
      background: "black"
      transparency: 0.7
lightgallery: true
toc:
  auto: false
---

Qui n’a jamais trouvé une librairie sur GitHub sans documentation ? C’est la librairie que vous cherchez, mais aucun renseignement sur son API. Combien de développeurs ont pleuré dans leur coin après ce genre de découverte ? L’auteur a passé des nuits à coder cette librairie, sauf que personne ne peut l’utiliser à son maximum. Elle aurait pu passer 4 heures (sur des dizaines d’heures de travail) à documenter son projet pour faire gagner plusieurs heures à ses collègues, aux contributeurs, aux clients… Dans cet article, je vous donne quelques repères pour écrire votre documentation technique (voire même fonctionnelle).

La documentation (technique) est parfois oubliée, malmenée ou encore bâclée. Elle a pourtant un intérêt fondamental dans la vie de votre produit (que ce soit un site, un logiciel, un produit physique, etc.). En effet, elle permet de :

- Utiliser votre produit à son plus fort potentiel (guide utilisateur)
- Guider les futurs contributeurs
- C’est un atout pour « vendre » votre projet
- Vous apporter une réflexion en cours/fin de projet
- Et plus encore…

> Un projet sans doc, c’est comme un ordinateur sans clavier. Nul ne peut l'utiliser.

{{< image src="/posts/meme/meme_femme_doigt.gif" caption="Quand le chef de projet te désigne pour faire la documentation." alt="Une femme désigne le photographe avec un sourire.">}}

## Qui fait la doc ?

Dans un premier temps, la documentation doit faire partie du projet sous forme d’une User Story, un ticket, une tâche etc. De cette manière, vous garantissez qu’elle sera affectée à une personne, et donc, faite (en toute logique). Ainsi, je suggère de réaliser la documentation de la même manière qu’un développement :

- Pour qui s’adresse cette documentation ? (= besoin client)
- Définition de l’architecture
- Rédaction de la documentation (peut inclure des schémas, des scripts batch etc.)
- Tests de la documentation par un pair

En effet, il est conseillé d’intégrer la documentation technique avec votre code, par exemple, dans un dossier nommé « doc » et suivi par votre système de versionnage. Pour quelles raisons ? Une documentation doit être facile d’accès : passer 1 heure à chercher la documentation, on conclut qu’il n’y avait pas de documentation. De plus, elle se doit être différente en fonction des versions de votre projet. N’oubliez pas d’indiquer à quelle version de votre projet la documentation correspond. J’en viens à un deuxième point : l’actualisation de votre documentation.

Une doc vieille d’un an, ou même de 4 mois, peut induire en erreur l’utilisateur du projet, mais c’est mieux que rien. A chaque version du projet, une revue de la documentation est nécessaire. Mettre à jour la documentation est une tâche longue et, il faut l’avouer, ennuyeuse. Pensez aux sourires sur les visages des développeurs quand ils verront votre excellente documentation.

{{< image src="/posts/meme/meme_dicaprio_documents.gif" caption="« Regardez comment la doc est belle. »" alt="Leonardo Dicaprio montre deux documents.">}}

## Quelle type de documentation ?

Je compte trois types de documentation (il y en a peut-être plus), elles répondent chacune à une question :

- Guide d’installation/intégration: Comment installer/accéder à votre projet ?
- Notice utilisateur : Comment utiliser votre projet ?
- Guide de contribution : Comment contribuer à votre projet ?

Les trois sont imbriqués, le guide de contribution est le plus complet : il inclut les deux autres. Le guide utilisateur inclut le guide de démarrage. Ce dernier peut être très trivial selon votre projet, cela peut être simplement une ligne indiquant d’appuyer sur le bouton Start de votre produit (physique).

### Une étude de cas : Chart.js

Nous allons rapidement étudier la documentation de Chart.js que j’ai pue utiliser au travail. C’est une librairie JavaScript (entre autre) pour faire afficher des graphes interactifs. Dans un premier temps, la librairie possède son propre site : [https://www.chartjs.org](https://www.chartjs.org/docs/latest/) et la documentation est [ici](https://www.chartjs.org/docs/latest/). Le projet compte plus de 350 contributeurs sur la partie JavaScript, il est d’autant plus facile d’avoir une documentation complète sur un grand projet comme celui-ci. Ou voyons cela de l’autre sens, il a plus de 350 contributeurs puisque la documentation est claire et complète. Parmi les 2 éléments précédents, qui la cause ? qui la conséquence ?

{{< image src="/posts/meme/meme_femme_jumelles.gif" caption="Recherchant la doc d’un projet..." width=300 height=300 alt="Une femme regarde avec des jumelles.">}}

Comme je vous le disais plus haut, la documentation est riche : [guide de démarrage](https://www.chartjs.org/docs/latest/getting-started/), [exemples](https://www.chartjs.org/docs/latest/charts/bar.html) avec rendu visuel, [guide pour contribuer](https://www.chartjs.org/docs/latest/developers/contributing.html) etc. Quelles critiques pouvons-nous à cette documentation ? Bien entendu, son état actuel est déjà suffisant, mais nous pouvons l’améliorer encore un peu. Pour chaque graphe, des paramètres optionnels peuvent être rajoutés aux données ou au graphe lui-même (un exemple [ici](https://www.chartjs.org/docs/latest/charts/bar.html#dataset-configuration)). La documentation contient la liste des options, leurs types, leurs valeurs par défaut et une description. Malgré tout, il n’y a pas d’exemple. L’exemple disponible en haut de page ici pour les graphes de type « barre » est très basique, et c’est mieux ainsi, tout le monde n’a pas besoin des options. Que retenir de cet exemple ? Toujours mettre des exemples, en l’occurrence, un exemple de code dans ce cas. Vous pouvez faire encore mieux en ajoutant le rendu visuel de l’exemple.

Une mauvaise documentation peut faire partie du plan d’affaires (business plan) comme avec le projet [Symfony](https://symfony.com/) de [SensioLabs](https://sensiolabs.com/). Leurs revenues viennent des formations, alors si nous pouvons nous former seuls avec leurs documentations, leurs formations n’auraient plus d’intérêt.

## Quel est son contenu ?

Une documentation répond à plusieurs questions :

**Comment télécharger ou intégrer cette librairie à un projet ?**

- Un bout de congifuration Maven à copier/coller dans le `pom.xml` pour intégrer la librairie
- La ligne de commande pour ajouter la librairie avec Composer
- La ligne de commande pour lancer le script bash d'installation (disponible pour chaque OS)

Exemples :
- [Chart.js](https://www.chartjs.org/docs/latest/getting-started/)
- [DataTables](https://www.datatables.net/manual/installation)
- [DoctrineExtensions](https://github.com/beberlei/DoctrineExtensions#installation)

**Quel est le rendu ?**

- Captures d’écran d’éléments graphiques utilisant votre librairie avec son bout de code.
- Résultat d'une fonction de votre librairie

Exemple :
- [Chart.js](https://www.chartjs.org/docs/latest/charts/line.html).

**Comment utiliser cette librairie ?**

- Bout de code à copier/coller dans son projet
- Bout de code ou script avec des données de test (pour faire voir les fonctionnalités principales)

Selon le type de projet, cette partie peut être très semblable ou identique au premier point.

Exemple :
- [Chart.js](https://www.chartjs.org/docs/latest/getting-started/)

**Comment résoudre un problème suite à une erreur ?**

- Foire aux questions (FAQ) pour les questions/erreurs fréquentes
- Lien vers les discussions sur cette librairie (GitHub Issue, StackOverFlow…)

**Quel est le potentiel de cette librairie ?**

- Nom, description, valeur par défaut, type de chaque paramètre avec des exemples pertinents sur quelques paramètres (exemple : deux par type ou par catégorie)
- Lien vers les modules additionnels populaires (plugins)
- Performance de votre projet par rapport aux autres du même type

**Comment modifier le code de cette librairie ?**

- Guide pour contribuer (récupération des sources, compilation, commit etc.)

Exemple :
- [Firefox](https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/Introduction)

**Par qui ce projet est-il maintenu ?**

- Liste des contributeurs, responsable du projet

Exemple :
- Tout projet Github a une liste de contributeurs

## Comment organiser ma documentation ?

Votre documentation doit être claire, les pages vont des éléments les plus basiques au plus complexes et, en même temps, des plus utilisés au moins utilisés. Par exemple, il n’est pas convenable de placer, dès le début, les paramètres optionnels de votre librairie. Pour autant, le guide de démarrage est le premier élément qui intéresse vos utilisateurs. N’oubliez pas, votre projet doit donner envie à ces futurs utilisateurs, un exemple qui impressionne est préférable pour votre page d’écran. Vous pouvez également vous aider d’outils pour créer votre documentation : [doxygen](github.com/doxygen/doxygen), [Swagger](https://swagger.io/), [Read the docs](https://readthedocs.org/)…


J’espère vous avoir guidé dans la construction d’une documentation solide. Elle servira aux utilisateurs et peut-être bien à vous-même dans quelques années.