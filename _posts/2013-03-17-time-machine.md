---
layout: post
title: Remise en route de Time Machine
description: ""
category: OS X
tags: ['OS X']
---
{% include JB/setup %}

## Reconstruire l'héritage

Time Machine est particulièrement simple à configurer. Dans mon cas je
souhaite pouvoir utiliser ma sauvegarde précédente bien que j'ai changé
de carte mère.

Pour cela, il suffit de suivre les instructions de 
[cet article](http://pondini.org/TM/B5.html).

En pratique, tout se déroule bien, Time Machine demande de lui-même si je
shouhaite hériter de ma sauvegarde précédente malgré le changement de carte
mère.

Si ce n'était pas le cas, [cet article](http://pondini.org/TM/B6.html) sera
plus approprié.

## Problème de nettoyage ?

Lorsque j'ai remis en route Time Machine j'ai remarqué que la sauvegarde reste
longtemps en phase de nettoyage (20 minutes).

Pour pallier à cela, j'ai regardé les journaux système et constaté plusieurs
anomalies. Cependant rien dans les problèmes constatés ne semble être lié à
Time Machine même. Le seul message dans les journaux renvoyé par Time Machine
est 'Starting post-backup cleaning' suivi un peu plus tard de 'Post-backup 
thinning complete'.

Une recherche Google sur le premier message n'a pas renvoyé de résultat 
satisfaisant. Une réindexation de Spotlight n'a pas non plus résolu le problème. 
Utilitaire de disque ne détecte pas de problème particulier.

Après quelques sauvegardes et la réinitialisation de l'index Spotlight du
disque, le problème semble avoir disparu.
