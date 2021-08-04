---
title: "La standard Télétexte pour les sous-titres TV"
date: 2021-07-28
draft: false
author: "liscare"
tags: ["TV", "Norme", "Français"]
categories: ["Informatique"]
featuredImagePreview: "/posts/pexels-tim-mossholder.jpg"
summaryStyle:
  hiddenImage: false
  hiddenDescription: false
  hiddenTitle: true
  tags:
    theme: "image"
    color: "white"
    background: "black"
    transparency: 0.7
page:
    theme: full
lightgallery: true
toc:
  auto: false
---

Ici, nous allons parler de norme de transmission pour les sous-titres TV.
Les sous-titres sont transmis via le protocole appelé NewFor. Depuis que je travaille sur ce thème, je n'ai jamais vu une documentation officielle mentionnant le nom de "Newfor". Ainsi, nous allons parler de [Télétexte](https://fr.wikipedia.org/wiki/Télétexte) plutôt que de NewFor dans cet article.

## Télétexte
Ce standard, créé par [EBU](https://fr.wikipedia.org/wiki/Union_européenne_de_radio-télévision), [ETSI](https://fr.wikipedia.org/wiki/European_Telecommunications_Standards_Institute) and [CENELEC](https://fr.wikipedia.org/wiki/Comit%C3%A9_europ%C3%A9en_de_normalisation_en_%C3%A9lectronique_et_en_%C3%A9lectrotechnique), a été publié la première fois en 1986 puis une dernière fois en mars 1997. Il est également appelé [CCIR Teletext System B](https://en.wikipedia.org/wiki/CCIR_System_B). Il permet d'encoder et d'afficher les informations Télétexte via un signal de transmission TV.

Télétexte est également le nom d'un service sur la télévision. Il permet de consulter des informations comme la météo, le résultat du sport, les actualités etc.
Suite à l'arrivée de la TNT et au développement d'internet dans les foyers, ce service est en déclin jusqu'à son arrêt en 2016.

## Sous-titrage
### Introduction
En France, le sous-titrage à destination des personnes Sourdes ou Mal-Entendantes (SME) est obligatoire, depuis 2005, pour les chaînes de télévision ayant plus 2.5 % de l'[audience](https://fr.wikipedia.org/wiki/Audience_(média)) totale des services de télévision. Ces chaînes de télévision doivent sous-titrer tous leurs programmes (sauf la publicité et quelques dérogations). Pour les autres chaînes, le [CSA](https://fr.wikipedia.org/wiki/Conseil_supérieur_de_l'audiovisuel_(France)) (Conseil Supérieur de l'Audiovisuel) fixe [les proportions des programmes à sous-titrer](https://www.csa.fr/Proteger/Garantie-des-droits-et-libertes/Les-droits-des-personnes-handicapees/Le-sous-titrage).

Les programmes sont sous-titrés en direct ou en stock (le sous-titreur a plusieurs jours pour sous-titrer le programme). La qualité d'un sous-titrage en direct est plus basse qu'un sous-titrage en stock puisque le sous-titreur n'a pas le temps de réécouter le programme pour se corriger. Pour chaque sous-titrage effectué en direct, entre une et trois personnes sont mobilisées pour sous-titrer le temps du programme (à l'aide d'un logiciel de reconnaissance vocale). Plus il y a de personnes mobilisées, plus les sous-titres sont de meilleure qualité et plus c'est cher pour les chaînes.
Le sous-titrage des programmes est effectué par les chaînes puisqu'il y a une loi les obligeant. L'intérêt des chaînes dans le sous-titrage varie énormément selon la chaîne.

Les sous-titres sont incrustés dans le signal de transmission de la vidéo via le télétexte. Dans un premier temps, il faut informer le receveur de la langue des futurs sous-titres pour ensuite les transmettre.
Ce standard a pris son origine avec la télévision analogique donc ses caractéristiques ne correspondent plus aux infrastructures numériques de notre époque. Par exemple, l'utilisation d'[Hamming](https://fr.wikipedia.org/wiki/Code_de_Hamming) pour détecter une erreur dans le signal n'est plus justifiable avec les technologiques actuelles.

Le préfixe 0x désigne un nombre hexadécimal.

### Initialisation
#### Transmission de la page
Cette trame est composée de 5 octets :

|1||||5|
|---|---|---|---|---|
|0xOE|0|N° du magazine|N° de la page (dizaine)|N° de la page (unité)|

Exemple avec le français :
|1||||5|
|---|---|---|---|---|
|0xOE|0x15|0xD0|0xD0|0xD0|

#### Transmission de la langue
Cette trame est composée de 5 octets :

|1||||5|
|---|---|---|---|---|
|0xOE|0|0|0|Code langue|

Exemple avec le français :
|1||||5|
|---|---|---|---|---|
|0xOE|0x15|0x15|0x15|0x64|

##### Code langue

Ce code désigne quelle table de caractères choisir pour encoder les caractères des sous-titres. Voir page 109 du document [ETS 300 706](https://www.etsi.org/deliver/etsi_i_ets/300700_300799/300706/01_60/ets_300706e01p.pdf) pour voir toutes les possibilités.

|X|Hamming(X)|Langue|
|---|---|---|
|0|0x15|Anglais|
|1|0x02|Allemand|
|2|0x49|Suédois/Finlandais/Hongrois|
|3|0x5E|Italien|
|4|0x64|Français|
|5|0x73|Espagnol/Portugais|

#### Transmission des données
La trame de transmission des données est composée d'un entête de 2 octets et de X fois 42 octets. Elle est composée de sous-trames de 42 octets en fonction du nombre de lignes de sous-titre à transmettre et les rangées 26 (niveau 1.5).

##### Entête principale
Le télétexte niveau 1.0 permet de transmettre des caractères simples de la table G0 (page 114 pour le latin) et 11 caractères spécifiques au langage (page 115 pour le latin). Très peu d'accents sont présents à ce niveau.
Une ligne peut seulement transmettre 36 caractères voire 37 dans un cas spécifique.

La trame commence par l'octet 0x8F puis un octet définissant le nombre de lignes inclu dans la trame.
Le nombre de lignes est défini de deux manières :
- 8 + Nombre de lignes + Nombre de rangées 26 (permet de supprimer à l'antenne le sous-titre précédent)
- Nombre de lignes + Nombre de rangées 26

Le 8 du premier cas correspond au _bit clear_, si le bit est à un, les sous-titres précédents à l'antenne sont supprimés.

L'octet doit être encodé en Hamming 8/7.
Quelques exemples :

- 2 lignes de sous-titres + pas de *bit clear* = 0x49
- 2 lignes de sous-titres + *bit clear* = 0x8C
- 2 lignes de sous-titres + 2 rangées 26 + *bit clear* = 0xA1

Condition : Nombre de lignes + Nombre de rangées 26 <= 7

##### Entête des sous-trames

Hors rangée 26, chaque sous-trame (correspondante à une ligne de sous-titre) est composée de 42 octets dont 3 ou 4 octets d'entête.

Position du ST sur l'écran (2 octets) + Double hauteur (1 octet) + Couleur (1 octet) + Incrustation (2 octets) + 36 caractères

{{< image src="/posts/newfor_sous_trame.png" caption="Composition d'une trame pour une ligne de sous-titre" alt="Tableau de la composition d'une trame pour une ligne de sous-titre">}}

##### Position du ST

Sur 2 octets, la position du sous-titre est comprise en 0 et 22. 0 correspond au haut de l'écran et 22 au bas de l'écran.

{{< image src="/posts/newfor_numero_rangee.png" caption="Encodage du numéro de rangée" alt="Tableau de correspondance entre position en encodage de cette position">}}

##### Double hauteur

La double hauteur (0x0D) permet d'indiquer que chaque ligne de sous-titre est affichée sur 2 lignes à l'écran. Dans ce cas, vous ne pouvez pas mettre deux lignes de sous-titres sur la ligne 20 puis 21 puisqu'il faut 2 lignes de différence.

D'autres possibilités aux pages 76-80 (table 26) du document [ETS 300 706](https://www.etsi.org/deliver/etsi_i_ets/300700_300799/300706/01_60/ets_300706e01p.pdf).

##### Couleur

Cet octet est optionnel. Sans celui-ci, la couleur par défaut est définie par le matériel (généralement blanc) et cela permet de mettre un caractère de plus (37 caractères au lieu de 36).

|X|Impair(X)|Couleur|
|---|---|---|
|0x01|0x01|Rouge|
|0x02|0x02|Vert|
|0x03|0x83|Jaune|
|0x05|0x85|Magenta|
|0x06|0x86|Cyan|
|0x07|0x07|Blanc|

Voir tableau 30 à la page 96 du document [ETS 300 706](https://www.etsi.org/deliver/etsi_i_ets/300700_300799/300706/01_60/ets_300706e01p.pdf).

##### Incrustation

L'incrustation est composée de 2 octets : 0x0B 0x0B

#### Caractères
##### Nombre de caractères inférieur à 36/37

Si le nombre de caractères est inférieur à 36/37 caractères, il faut ajouter un octet de fin d'incrustation (0x8A) et remplir le reste par des espaces (0x20).

{{< image src="/posts/newfor_sous_trame_mirempli.png" caption="Composition d'une trame pour une ligne de sous-titre avec 18 caractères" alt="Tableau de la composition d'une trame pour une ligne de sous-titre avec 18 caractères">}}

##### Encode d'un caractère

Chaque caractère est encodé sur un seul octet. Le tableau 35 (page 114) du document [ETS 300 706](https://www.etsi.org/deliver/etsi_i_ets/300700_300799/300706/01_60/ets_300706e01p.pdf) regroupe l'encodage de chaque caractère (pour le latin). Par exemple, la majuscule A correspond à 0x41.
Plusieurs tableaux G0 sont disponibles, le choix est effectué par le code langue défini plus haut.

Les caractères grisés ne sont pas disponibles pour le niveau 1.0. Ils sont remplacés par des caractères spécifiques aux langues disponibles dans le tableau 36 (page 115) en fonction de la langue choisie. Par exemple en français, le caractère è correspond à 0x60.

**Tous les caractères sont encodés en Impair().**

#### Télétexte niveau 1.5
Le niveau 1.5 rajoute tous les caractères accentués, des caractères spéciaux et les caractères grisés de la table G0 via des rangées 26 (sans modifier le reste). Elles ne sont pas visibles mais elles modifient les lignes de sous-titres en insérant les caractères nécessaires.

##### Introduction aux rangées 26

Les rangées 26 sont à transmettre en premier.

Dans un premier temps, il faut se positionner sur la ligne de sous-titre (position à l'écran) grâce à l'Active position. Ensuite, il y a 3 possibilités par chaque caractère :
- Caractère accentué
- Caractère grisé de la table G0
- Caractère spécial

La rangée 26 est finalement une trame de 42 octets positionnée à la ligne 26 qui n'est pas affichée sur l'écran.

{{< image src="/posts/newfor_rangee_26.png" caption="Composition d'une trame de la rangée 26" alt="Tableau de la composition d'une trame de la rangée 26">}}

Chaque triplet est découpée en 3 valeurs sur 3 octets au total :
- DATA : 7 bits
- MODE : 5 bits
- ADDRESS : 6 bits

Voir table 27 page 81 du document [ETS 300 706](https://www.etsi.org/deliver/etsi_i_ets/300700_300799/300706/01_60/ets_300706e01p.pdf)

**Le tout est ensuite encodé en Hamming 24/18.** De la façon suivante : Hamming2418(ADDRESS, MODE, DATA).

Les rangées sont prioritaires par rapport au caractère de niveau 1.0. Pour la transmission classique des caractères (vue précédemment), vous pouvez transmettre des caractères sans accent pour remplacer les caractères accentués et des espaces pour le reste des caractères.
Il existe 5 types de triplet, les voici :

##### Set Active Position
Cette triplet permet de se positionner sur une ligne de sous-titre à l'écran (entre 0 et 22). Il faut le transmettre en premier avant d'envoyer les triplets de la ligne en question.

- DATA = 0
- MODE = 0x04
- ADDRESS = 40 + N° de rangée

Positionnement à la ligne 15 :
- ADDRESS = 55
Soit Hamming2418(55, 4, 0) : 35 93 80

##### Caractère spécial

- DATA = Code du caractère spécial dans la table G2 (table 37 page 116 pour le latin) sauf la colonne 4
- MODE = 0x0F
- ADDRESS = N° de colonne de 0 à 39, correspond à la position dans la sous-trame

Positionnement à la ligne 15 :
- ADDRESS = 55
Soit Hamming2418(55, 4, 0) : 0x35 0x93 0x80

##### Caractère accentué

- DATA = Code du caractère (sans accent) dans la table G0 (table 35 page 114 pour le latin)
- MODE = Code de l'accent (colonne 4 uniquement) dans la table G2 (table 37 page 116 pour le latin)
- ADDRESS = N° de colonne de 0 à 39, correspond à la position dans la sous-trame

Exemple avec le caractère accentué Ẽ à la colonne 5 dans une configuration avec couleur:
- DATA = 0x45 = 69
- MODE = 10100 = 20
- ADDRESS = 5
Soit Hamming2418(5, 20, 68) : 0xAC 0xD0 0x44

##### Caractère grisé G0

- DATA = Code du caractère grisé dans la table G0 (table 35 page 114 pour le latin)
- MODE = 16
- ADDRESS = N° de colonne de 0 à 39, correspond à la position dans la sous-trame

Exemple avec le caractère grisé G0 } à la colonne 6 dans une configuration sans couleur:
- DATA = 0x7D = 125
- ADDRESS = 5
Soit Hamming2418(5, 16, 125) : 0x2F 0xC0 0x7D

##### Triplet de remplissage

La trame de la rangée 26 doit toujours contenir 13 triplets, il faut remplir le reste par des triplets de remplissage (0x74 0xFF 0x80) jusqu'à atteindre 13 triplets.

### Effacement des sous-titres à l'antenne

Pour effacer les sous-titres à l'antenne, il faut envoyer des espaces (0x20) dans une trame de caractères.

### Affichage des sous-titres à l'antenne

La trame est composée d'un seul octet (0x10), elle est à transmettre après chaque trame de sous-titre.

### Exemples
#### Exemple n°1

Envoi de deux lignes à la rangée 20 et 22 :
- Bonjour à tous
- À % @ $

{{< image src="/posts/newfor_exemple_1.png" caption="Exemple n°1" alt="Trame envoyée pour l'exemple n°1">}}

#### Exemple n°2

Envoi de deux lignes à la rangée 20 et 22 :
- ã " _
- Nous sommes içi

{{< image src="/posts/newfor_exemple_2.png" caption="Exemple n°2" alt="Trame envoyée pour l'exemple n°2">}}

### Hamming
Le code de Hamming permet, à la réception, de vérifier si un bit est erroné. Une fonction Hamming X/Y signifie que Y bits sont transformés en X bits.

Le signe + correspond à l'addition binaire.

Voir page 21 du document [ETS 300 706](https://www.etsi.org/deliver/etsi_i_ets/300700_300799/300706/01_60/ets_300706e01p.pdf).

#### 8/4

En entrée, nous avons 4 bits D1, D2, D3 et D4. Prenons l'exemple avec le chiffre 3 (0011, D1 = 1, D2 = 1, D3 = 0 et D4 = 0)
Nous rajoutons à ces 4 bits, 4 bits de protection que nous appelons P1, P2, P3 et P4.

La composition finale est : P1 D1 P2 D2 P3 D3 P4 D4

P1 = 1 + D1 + D3 + D4

P2 = 1 + D1 + D2 + D4

P3 = 1 + D1 + D2 + D3

P4 = 1 + P1 + D1 + P2 + D2 + P3 + D3 + D4

Dans notre exemple :
P1 = 1 + 1 + 0 + 0 = 0

P2 = 1 + 1 + 1 + 0 = 1

P3 = 1 + 1 + 1 + 0 = 1

P4 = 1 + 0 + 1 + 1 + 1 + 1 + 0 + 0 = 1

Soit 0 1 1 1 1 0 1 0 soit 0x5E (01011110)

#### 24/18

En entrée, nous avons 18 bits D1, D2, D3, D4, D5, D6, D7, D8, D9, D10, D11, D12, D13, D14, D15, D16, D17, D18. Prenons l'exemple avec le chiffre 3 (0011)
Nous rajoutons à ces 6 bits, 6 bits de protection que nous appelons P1, P2, P3, P4, P5 et P6.

P1 = 1 + D1 + D2 + D4 + D5 + D7 + D9 + D11 + D12 + D14 + D16 + D18

P2 = 1 + D1 + D3 + D4 + D6 + D7 + D10 + D11 + D13 + D14 + D17 + D18

P3 = 1 + D2 + D3 + D4 + D8 + D9 + D10 + D11 + D15 + D16 + D17 + D18

P4 = 1 + D5 + D6 + D7 + D8 + D9 + D10 + D11

P5 = 1 + D12 + D13 + D14 + D15 + D16 + D17 + D18

P6 = 1 + P1 + P2 + D1 + P3 + D2 + D3 + D4 + P4 + D5 + D6 + D7 + D8 + D9 + D10 + D11 + P5 + D12 + D13 + D14 + D15 + D16 + D17 + D18

{{< gist Liscare 3834b8ba79b4df14d71616b1b197f96d >}}

### Impair

Le 8ème bit est à 0 si le nombre de bits total est impair sinon 1.

Exemple avec 0x03, Impair(000 0011) = 1000 0011
Exemple avec 0x04, Impair(000 0100) = 0000 0100