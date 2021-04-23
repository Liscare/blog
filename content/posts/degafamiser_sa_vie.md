---
title: "Dégafamiser sa vie"
date: 2020-10-17
draft: false
author: "liscare"
tags: ["Vie", "GAFAM", "Français"]
categories: ["Informatique", "Libre"]
page:
    theme: full
lightgallery: true
featuredImagePreview: "/posts/gafam_logos.jpeg"
summaryStyle:
    hiddenImage: false
    hiddenDescription: false
    hiddenTitle: true
    tags:
      theme: "image"
      color: "white"
      background: "black"
      transparency: 0.7
toc:
  auto: false
---

{{< image src="/posts/slide-degooglisons-internet.png" caption="Illustration de [Framasoft](https://degooglisons-internet.org/fr/) sous [Creative Commons By-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.fr)" alt="Dessin illustrant une bataille entre Twitter, Google et Facebook">}}

Dans un premier temps, j’avoue le terme « dégafamiser » vient du slogan « [Dégooglisons internet](https://degooglisons-internet.org/fr/) » de [Framasoft](https://framasoft.org/fr/). Depuis deux ans, je souhaite « reprendre mes données en main », entendez par là, « ne pas les livrer à des acteurs privés » (typiquement les GAFAM). Depuis 2018, j’ai entrepris un changement d’utilisation des outils numériques du quotidien : Facebook, Google Search, Android, Windows, Instagram, WhatsApp, Google Chrome, Google Calendar, Google Gmail,. Vous voyez le topo ? **Les GAFAM étaient très présents dans ma vie.**

Cet article est écrit sous la forme d’étapes sans avoir la prétention d’être un tutoriel, de l’habitude la plus facile à changer à la plus difficile à mon avis. L’idée est de se défaire du monopôle des très grosses entreprises type GAFAM et de reprendre en main, quand c’est possible, ses données personnelles. Vous aurez très probablement toujours des données personnelles sur internet. Pour autant, diminuer l’exposition de vos données vous permet d’être moins influencé sur vos choix, par exemple, sur YouTube et d’aller à l’essentiel. En parallèle, vous pouvez changer votre manière d’utiliser les outils numériques indépendamment de l’outil lui-même. Je ferai un article à ce propos.

>  La dégafamisation ne s’est pas faite en un jour !

Commençons par le plus facile : la navigation sur internet (navigateur + moteur de recherche). Le changement doit être radical, sinon vous ne ferez jamais le pas !

## Navigateur : Mon renard préféré

Désinstallez Google Chrome puis installez Mozilla Firefox (ou Brave). Mettez-vous à l’aise, organisez vos favoris (par dossier, sous-dossier, etc), ajoutez des extensions ([Dark Reader](https://darkreader.org/), [Privacy badger](https://privacybadger.org/) et [Ghostery](https://www.ghostery.com/) pour moi), utilisez un coffre-fort de mots de passe (Mozilla Lockwise par exemple) et configurez votre navigateur. Tout cela prend seulement 1 h 30. Soyez curieux pour configurer votre navigateur, vous pouvez même avoir plusieurs configurations (profil), choisissez-les en allant sur l’URL : about:profiles.

### Moteur de recherches : CanardCanardAller

Choisissez un moteur de recherche sur Firefox, j’ai choisi [DuckDuckGo](https://duckduckgo.com/) (métamoteur de recherches), il en existe plein d’autres ([Ecosia](https://www.ecosia.org/?c=fr), [QWant](https://www.qwant.com/), etc.). En désactivant les cookies et en activant la suppression de l’historique, vous allez (re)découvrir certains sites.

## OS : Bye Bill, bonjour Linus

{{< image src="/posts/meme/meme_tv_peru.gif" caption="Quand tu te rends compte de ta dépendance aux GAFAM après des années d'ignorance" alt="Marionnette avec un air étonnée">}}

La première étape (la plus facile) étant réussie, passons à la suivante. Je suppose que vous avez l’habitude d’utiliser Windows à la maison ou au travail. Il y a malheureusement peu d’entreprises proposant un Linux comme poste de travail, la coutume est plutôt Windows voire MacOs. Pour moi, le développement ou le DevOps est largement mieux sur un Linux voire sur un MacOs. Alors faites le premier pas en installant une distribution en Dual boot sur votre PC, comme ça, vous gardez un Windows sous le coude.

J’ai choisi [Debian](https://www.debian.org/distrib/) mais je recommande plutôt [Ubuntu](https://ubuntu.com/download/desktop) pour une utilisation bureautique (Debian est moins adapté à la bureautique). Le téléchargement de Linux, la mise sur clé USB pour démarrer dessus, l’installation de votre distribution préférée vous prendra 1 h 30 avec les mises à jour en ayant un bon débit internet. Vous trouverez un tutoriel comme installer Debian 10 sur un PC Windows 10 en dual boot ici et comment rendre votre clé USB *bootable* [ici](https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/). Ensuite, prenez l’habitude d’utiliser Linux au quotidien, cela fera l’affaire.

### En entreprise

En entreprise, il est plus compliqué de changer pour des raisons de sécurité (mais pas que), discutez-en avec les administrateurs réseaux et votre responsable. Configurez votre navigateur Firefox de la même manière que sur Windows (vous pouvez utiliser [Firefox Sync](https://support.mozilla.org/fr/kb/configurer-firefox-sync?redirectslug=comment-configurer-firefox-sync&redirectlocale=fr) pour synchroniser vos marque-pages (et plus encore) sur vos différents appareils).

Vous avez maintenant un Linux avec Firefox installé, la troisième étape se passe sur votre smartphone Android. Si vous avez un iPhone, cela devrait être semblable. Vous allez limiter les données récupérées par Google sans pour autant être sûr, mais autant essayer.

## Limiter l’emprise de Google sur son smartphone

### Moins de permissions, mieux protégé

Dans un premier temps, désactivez les différentes permissions inutiles de toutes vos applications : pas d’inquiétude, l’application vous redemandera cette permission en temps voulu. Pour cela, allez dans *Paramètres –> Applications –> cliquez sur la route crantée en haut à gauche –> Autoris. des applis* : vous avez maintenant la liste des différentes autorisations Android. En cliquant sur une des autorisations, vous pourrez désactiver cette autorisation pour certaines applications. Par exemple, refusez que Outlook puisse utiliser votre microphone.

### Moins d'applications, mieux protégé

Toujours sur Android, vous allez désactiver certaines applications installées « par défaut » (pour ne pas dire « par obligation »). Pour cela, allez dans *Paramètres –> Applications*, sélectionnez l’application que vous voulez désinstaller puis cliquez sur *Désinstaller*.

La plupart des applications de Google ne peuvent pas être désinstallées mais désactivées, alors cliquez sur *Désactiver* au lieu de *Désinstaller*. L’application va se réactiver automatiquement lorsque vous allez l’ouvrir. Vous pouvez désactiver les applications suivantes : Google Duo, Google Cloud Print, Google Play Films et séries, Google Play Musique, Google Hangouts, Thèmes, Appli Google, Chrome, Drive, etc. Depuis que j’ai désactivé YouTube, j’ai régulièrement le message d’erreur YouTube a cessé de fonctionner lorsque je navigue sur n’importe quelle autre application, étrange n’est-ce pas ?

## Envoyer Google Cloud au ciel

Passons à Google Drive, je vous conseille fortement de vous diriger vers une solution Cloud 100 % européen, laisser ses données transiter par les États-Unis, c’est exposer aux lois américaines sur les données personnelles (et ce n’est pas bon pour vous). Vous pouvez opter pour [PCloud](https://www.pcloud.com/fr/eu) ou [Nextcloud](https://nextcloud.com/) qui sont des sociétés basées en Europe. Vous pouvez utiliser [Google TakeOut](https://takeout.google.com/) pour télécharger toutes vos photos sur le Cloud de Google afin de les sauvegarder sur votre nouveau compte Cloud.

Il vous reste encore du chemin pour s’émanciper des GAFAM, il faut pour cela un changement en profondeur de vos habitudes. Encore une fois, c’est un changement difficile mais qui en vaut la chandelle. Les conséquences se verront au fur et à mesure, les GAFAM ne se sont pas toujours les plus qualitatifs ou les moins chers.

Je vous conseille fortement de cette [page](https://degooglisons-internet.org/fr/alternatives) de Framasoft, vous y trouverez toutes les alternatives libres aux applications que vous utilisez quotidiennement.