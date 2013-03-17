---
layout: post
title: Installer un Fusion Drive
tagline: "<br>Un SSD dans un iMac non supporté par Apple"
category: OS X
tags: ['OS X']
---

## Introduction

À l'occasion de du remplacement préventif de mon disque interne par Apple et
de la mise à disposition dans Mountain Lion de Fusion Drive, je me suis dit
que ça serait une 
[bonne idée](http://forum.macbidouille.com/index.php?showtopic=365122) de
remplacer mon lecteur optique par un SSD.

## Materiel

La première étape consite à 
[ouvrir la bête](http://forum.macbidouille.com/index.php?showtopic=365122).
Une fois ceci fait, il faut retirer le lecteur puis ajouter le [SSD](http://www.topachat.com/pages/detail2_cat_est_micro_puis_rubrique_est_w_ssd_puis_ref_est_in10050056.html)
dans son [support](http://www.newmodeus.com/shop/index.php?main_page=product_info&products_id=260).

## Logiciel

Il faut ensuite configurer le disque pour utiliser Fusion Drive, pour cela,
j'ai démarré sur la partition de récupération OS X, puis j'ai appliqué la
méthode suivante:

Tout d'abord lister les partitions et repérer les identifiants de la partition
principale du disque interne (ex: disk2s2) et le disque SSD (disk1). Pour cela 
on utilise la commande suivante:

	diskutil list

Ensuite il faut créer le volume CoreStorage avec la commande. Cela va créer
le volume Fusion Drive et évidemment supprimer les données présentes sur la
partition principale et le contenu du disque SSD. Mon SSD étant vierge et le
disque dur préalablement sauvegardé, cela ne m'ap pas posé de problème.

	diskutil cs create "Fusion Drive" disk2s2 disk1

Lors de cette commande un nouveau groupe de volumes logique est créé. Le 
Terminal affiche son UUID, il peut également être retrouvé avec la commande:

	diskutil cs list

Avec cette identifiant, je crée un système de fichier sur ce volume:

	diskutil cs createVolume UUID jhfs+ "Macintosh HD" 100%

En remplaçant UUID par l'identifiant récupéré précédemment. Après cette étape,
il suffit d'installer OS X à partir de la partition actuelle, puis de
restaurer la sauvegarde Time Machine.

Source: [http://reviews.cnet.com/8301-13727_7-57550128-263/how-to-make-a-custom-corestorage-drive-in-os-x/](http://reviews.cnet.com/8301-13727_7-57550128-263/how-to-make-a-custom-corestorage-drive-in-os-x/)
