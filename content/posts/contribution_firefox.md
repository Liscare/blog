---
title: "Le jour où j'ai voulu contribuer à Firefox"
date: 2020-06-17
draft: false
author: "liscare"
tags: ["Contribution", "Projet", "Mozilla", "Français"]
categories: ["Libre"]
featuredImage: "/posts/moz-logo-main-rgb.png"
featuredImagePreview: "/posts/moz-logo-main-rgb.png"
summaryStyle:
    hiddenImage: false
    hiddenDescription: false
    hiddenTitle: true
    tags:
      theme: "image"
      color: "black"
      background: "white"
      transparency: 0.7
page:
    theme: full
lightgallery: true
toc:
  auto: false
---
# Le jour où j'ai voulu contribuer à Firefox

Il y a déjà quelques mois, avec mon côté libriste, j'ai eu envie de contribuer à un projet open-source. A priori, je ne partais déjà pas de la bonne manière, mais je vais m'en rendre compte plus tard, vous allez voir.

Commençons par les bases, pourquoi contribuer à un projet libre ? C’est venu du fait que dans mon alternance, je ne m’éclatais pas techniquement. Je travaille sur des technologies (sans framework) que j’ai déjà vues, donc 0 challenge. L’idée est d’avoir un apport de connaissances grâce à un projet très technique et aux revues de code assurées par la communauté du projet. Je n’avais pas d’idée de projet à créer de zéro, ça prend beaucoup beaucoup de temps et les résultats ne sont pas là en conséquence. Alors je décide de contribuer à un projet libre (comprenez open-source) avec une communauté présente et avec un intérêt pour moi afin de me motiver.

J’utilise tous les jours Firefox, alors pourquoi pas le projet [Mozilla](https://www.mozilla.org/fr/) ? **Le projet est immense.** Je décide de me lancer dans la contribution à Firefox avec mes petits moyens, bien-sûr. J’avais conscience que le projet est long à s’approprier puisqu’il y a énormément d’outils à utiliser pour contribuer et il est important de bien comprendre les différentes étapes de contribution. Cependant, en choisissant ce projet, j’ai plus de chances d’être guidé dans la contribution que dans un petit projet : important pour débuter. De plus, le choix des technos est large : C++, Java, Python, JavaScript, Rust etc.

## Direction Firefox

La première partie est surtout composée de lectures et d’installations. Je m’impressionne moi-même, j’ai vraiment envie d’y arriver, malgré toute la doc technique en anglais à lire. Je vais de lien en lien puis je commence à installer l’[environnement de travail](https://developer.mozilla.org/fr/docs/Mozilla/Developer_guide/Introduction) : quelques commandes Linux, [Mercurial](https://www.mercurial-scm.org/) (hg pour les intimes) et le téléchargement du code source de Firefox. Quelques inscriptions à différents sites sont nécessaires comme pour [Bugzilla](https://bugzilla.mozilla.org/home) ou [Riot](https://chat.mozilla.org/#/welcome) (chat des contributeurs), chose anodine mais je découvre [OTP](https://fr.wikipedia.org/wiki/Mot_de_passe_%C3%A0_usage_unique) à ce moment-là. La mise en place d’environnement prend toujours du temps, avec ce projet, j’ai découvert plusieurs outils et manières de faire. Parfait ! C’est ce que je recherche. 😉

Le projet Mozilla gravite autour de plusieurs outils : [Bugzilla](http://bugzilla.mozilla.org/home), [Codetribute](https://codetribute.mozilla.org/), [Mercurial](https://www.mercurial-scm.org/), [Phabricator](https://secure.phabricator.com/), [Riot](https://chat.mozilla.org/#/welcome), [SearchFox](https://searchfox.org/), etc qui font partis, pour la plupart, du projet lui-même. Grâce à ça, j’ai pu apprendre de nouveaux outils en cliquant de lien en lien dans la documentation du projet, je conseille fortement cette technique : prenez votre temps pour lire de la doc. Cette partie d’apprentissage m’a remotivé pour contribuer !

## Avant de contribuer : l'environnement

### L'installation des outils

Pour l’installation de l’environnement, je rencontre quelques problèmes avec ma Debian, mais rien de bloquant : une recherche sur Internet et hop ! Résolu ! Jusqu’à maintenant, les instructions pour contribuer sont claires, enfin de la bonne doc !!! (contrairement au code de [Symfony](https://symfony.com/) 😉 ). Choisir un gros projet et vous aurez de la bonne documentation pour commencer à contribuer, en théorie, hein !

### La compilation

L’environnement est prêt, passons aux choses sérieuses ! Je commence par le fameux ./mach build pour compiler, après quelques problèmes de configurations et 1 h 30 de compilation, Firefox s’ouvre 🤩🤩🤩. C’est la dernière étape avant la contribution. Ah bah non en faite 🤦. Comment je vais modifier le code C++ ? avec Vim ? Certainement pas ! Firefox suggère d’utiliser [Eclipse CDT](https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/Eclipse/Eclipse_CDT) compilé spécialement pour le projet Mozilla. Alors on recommence une compilation, plus courte cette fois-ci. Quelques configurations sont nécessaires avant la compilation, mais c’est plus lié à Eclipse lui-même qu’à Firefox. Cette période était difficile, je ne voyais pas le bout. J’avais déjà passé plusieurs après-midi jusque-là. Cette partie était bien documentée (certes moins que l’installation et la compilation de Firefox) mais il est difficile de prendre du temps pour cela, pour finalement passer 4 heures pour juste ouvrir un IDE.

**L’installation n’en finissait pas, la motivation en prenait un coup.**

## L’ultime étape : la contribution

### Un peu d'ordre pour la première

Je peux enfin consulter le code source sur mon ordi ! La phase finale est la plus intéressante : la contribution. Pour une bonne prise en main, le tutoriel suggère comme première contribution un bug étiqueté : *[Good First Bug](https://codetribute.mozilla.org/languages/c++?tag%3Dgood-first-bug)*. J’ai choisi de partir doucement avec un bug de style, un else à supprimer, rien de bien méchant. Une fois la modification faite, il ne reste plus qu’à envoyer un patch à Phabricator pour une validation afin de le fusionner avec le reste du code. Cette étape est délicate, je n’avais pas envie de faire de la merde et pour ne embêter pas les autres contributeurs plus qu’autre chose. Pour déposer un patch sur Phabricator, il faut assigner un relecteur. Le concept est super quand tu connais bien le projet. Pour ma part, j’ai choisi le (supposé) responsable du module modifié comme conseillé. La fin approche !

Le relecteur suggère de rajouter un espace comme le style l’indique. Donc maintenant, je vais devoir modifier mon patch sans en créer un autre, opération délicate. 😬 Finalement, rien de plus facile avec Mercurial et Phabricator (phab pour les intimes), il suffit de bien lire la documentation fournie (comme d’habitude, vous allez me dire).

**Voilà [ma première contribution](https://bugzilla.mozilla.org/show_bug.cgi?id=1624230) à Firefox réussie !!!**

### Premier ressenti

Le chemin était long et éprouvant, je suis content, j’ai réussi ! Je me suis rendu compte que je n’avais pas assez de temps ou d’intérêt pour contribuer à Firefox (si vous avez l’intérêt, le temps s’y prêtera). Je conclus que je suis mal parti depuis le début : les modifications de Firefox ne m’affecte pas. Outre l’intérêt de monter en compétences, je n’en ai pas. Dans un même temps, je ne crois pas à l’idée que les contributions ne font qu’avec un intérêt économique direct ou indirect. Alors, je ne m’arrête pas là. D’un autre côté, c’est seulement ma première contribution à un projet, les effets d’une contribution se font ressentir sur le long terme. Donc je tire une conclusion plutôt rapide mais si vous n’avez plus motivation ou de temps dès le début de votre projet : il sera difficile de continuer, vous l’avez bien compris.

## Un changement de projet

Je continue l’aventure mais sur le projet [ThunderBird](https://developer.thunderbird.net/). Pourquoi avoir changer de projet ? Pour plusieurs raisons :

- Peu de bugs en C++ sur Codetribute sont abordables à mon niveau (il y a pas mal de bugs très anciens >6 ans) pour Firefox
- ThunderBird est plus petit donc plus facile pour aborder des bugs
- C’est un logiciel que j’apprécie et je souhaite qu’il grandisse
- En manque de motivation, le changement peut être bénéfique

Finalement, après quelques heures pour contribuer à Thunderbird (mise en place de l’environnement, compilation et documentation), je décide de mettre en pause pour un certain temps puisque je manque de temps et de motivations. J’ai des projets plus importants comme ce blog et je n’ai pas d’intérêt, autre que l’apprentissage technique, dans ce projet. C’est finalement le plus gros frein que j’ai rencontré jusqu’ici pour contribuer dans l’open-source. Contribuer à un projet sera plus facile si vous avez un intérêt dans le projet. Vous pouvez avoir besoin du projet pour vos projets perso/pro, vous êtes payé à faire ça, vous corrigez des bugs, vous amusez avec la communauté ou vous êtes un libriste à 100 % qui a du temps…

Je sors grandi de cette expérience, j’ai pu avoir un premier pas (très léger) dans l’open-source. Je vous livre quelques conseils personnels suite à ma petite expérience.

## Quelques conseils pour vous lancer dans la contribution

- Choisir un projet qui vous plaît, voire dont vous avez besoin
- Trouver un tuteur si ce système est en place pour les nouveaux contributeurs
- Lire, lire et lire de la documentation sur les outils à utiliser
- Prendre son temps pour mettre en place l’environnement de travail (qui doit être nickel !)
- Évaluer la charge de travail nécessaire au projet, avez-vous le temps de contribuer ?
- S’approprier, un peu, les outils du projet avant de contribuer