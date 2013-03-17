---
layout: post
title: Vérification des journaux système
description: ""
category: OS X
tags: ['OS X']
---
{% include JB/setup %}

Lorsque j'ai 
[remis en route Time Machine]({% post_url 2013-03-17-time-machine %}) que 
la sauvegarde reste en phase de nettoyage pendant une vingtaine de minutes.

Suite à cela, j'ai regardé les journaux système et constaté plusieurs
anomalies sans lien avec Time Machine.

- mdworker: Unable to talk to lsboxd

  Ce problème a été traité en éditant le fichier `/System/Library/Sandbox/Profiles/system.sb`
  et en y ajoutant:

        ;;; MDWorker Fix
            (allow mach-lookup
                (global-name "com.apple.ls.boxd")
                (local-name "com.apple.ls.boxd")
                (global-name "com.apple.coresymbolicationd")
                (local-name "com.apple.coresymbolicationd"))

- usbmuxd: Could not start session kAMDInvalidHostIDError

    Ce problème signifie prboablement une erreur de communication avec 
    l'iPhone via Wi-Fi. La solution adaptée est donc de reconnecter l'iPhone
    au Mac avec un calbe USB.

- mdworker[33140]: Exception raised during new decode: *** -[NSKeyedUnarchiver decodeObjectForKey:]: data to unarchive contains class (NSFontDescriptor) which has not been allowed

- SystemUIServer[306]: problem with path Modifier les paramètres de l’ordinateur — Windows 7 x64

La plupart des problèmes semblant liés à Spotlight, l'index a été regénéré. 
Un bon ménage serait sans doute bienvenue pour supprimer les fichiers source
d'erreurs.
