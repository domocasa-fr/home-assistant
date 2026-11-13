# Domocasa Maison

Cette app relie votre Home Assistant aux applications Domocasa (iPhone et Android). Elle
fonctionne sans rien ouvrir sur Internet : votre maison appelle elle-même le service Domocasa,
et rien ne peut entrer chez vous sans le code que vous générez ici.

## Installation

1. Dans Home Assistant : **Paramètres, Apps** (anciennement « Modules complémentaires »), puis
   **Installer une app**.
2. Menu à trois points en haut à droite, **Dépôts**, et ajoutez l'adresse du dépôt Domocasa
   que votre installateur vous a communiquée.
3. Ouvrez **Domocasa Maison**, puis **Installer**. Activez **Démarrer au lancement** et
   **Chien de garde**.
4. **Démarrer**. Un nouvel élément **Domocasa** apparaît dans la barre latérale : c'est la page
   qui permet de jumeler un téléphone, de voir la liste des téléphones jumelés et de retirer
   l'un d'eux.

Les options (nom de la maison, alarme…) se règlent dans l'onglet **Configuration** de l'app. La
plupart sont réservées à votre installateur : laissez les valeurs proposées si vous n'êtes pas
sûr.

## Ce que fait l'app

- Elle lit la liste de vos appareils dans Home Assistant et les présente dans l'application
  Domocasa, pièce par pièce.
- Elle transmet les commandes de la famille (allumer, ouvrir un volet, régler la clim…) à
  Home Assistant.
- Elle ne demande aucun mot de passe Home Assistant : elle utilise l'accès que Home Assistant
  lui prête lui-même.
- Dans le journal de Home Assistant, les actions faites depuis l'application Domocasa
  apparaissent sous le nom « Supervisor ». Le journal de l'app indique qui a fait quoi.

## Chien de garde

Le **chien de garde** de Home Assistant vérifie que l'app répond. Si elle s'arrête sans raison,
Home Assistant la relance tout seul. Gardez-le activé (case **Chien de garde** dans la page de
l'app).

## Mises à jour : toujours avec une sauvegarde

Les mises à jour automatiques sont désactivées : Domocasa vous prévient, ou s'en charge pour
vous, après avoir vérifié la version. Quand une mise à jour est proposée :

1. Ouvrez l'app, puis **Mettre à jour**.
2. **Cochez « Sauvegarder avant la mise à jour »**. C'est ce qui permet de revenir en arrière si
   quelque chose se passe mal : la restauration de cette sauvegarde remet la version précédente
   de l'app **et** ses données.
3. Validez.

Attention : si vous restaurez une sauvegarde, tout ce qui s'est passé depuis (téléphones
jumelés, journal) est perdu. Un téléphone jumelé après la sauvegarde devra être jumelé de nouveau.

## Sauvegardes

Les données de l'app, **y compris l'identité de votre maison**, sont incluses dans les
sauvegardes de Home Assistant. Si votre box tombe en panne, restaurez la sauvegarde sur la
nouvelle : les téléphones continuent de fonctionner sans être jumelés de nouveau. Gardez donc au
moins une sauvegarde hors de la box, et protégez-la comme un trousseau de clés : qui détient la
sauvegarde détient l'identité de la maison.

## Désinstaller l'app

**Désinstaller l'app efface l'identité de la maison.** Tous les téléphones jumelés cessent de
fonctionner, et il faudra tout jumeler de nouveau, comme pour une maison neuve. Ne désinstallez
pas l'app « pour réessayer » : arrêtez-la, ou redémarrez-la, c'est sans conséquence.

Si vous la désinstallez malgré tout, faites d'abord une sauvegarde, elle contient l'identité.

## Appareils à ne pas montrer : « masquer » n'est pas « masquer »

Deux réglages portent le même mot, pour deux effets différents.

- **L'option `masquer`** (onglet Configuration de l'app, notre liste « Appareils exclus »)
  **exclut** l'appareil : il n'existe plus du tout pour les applications. Personne dans la
  famille ne le voit, et personne ne peut le commander. À réserver à ce qui ne doit jamais être
  piloté depuis un téléphone.
- **« Masquer » dans l'application Domocasa** (mode technicien) **cache** l'appareil à la
  famille sans le supprimer : il reste commandable par ceux qui en ont le droit, par exemple
  depuis une scène.

En cas de doute, utilisez « Masquer » dans l'application : c'est réversible d'un geste.

## Jumeler un téléphone

1. Ouvrez **Domocasa** dans la barre latérale de Home Assistant (réservé aux administrateurs).
2. Dans **Ajouter un téléphone**, saisissez le prénom, choisissez l'accès (**Partout**, **À la
   maison seulement** ou **Partagée**), puis **Afficher le QR**.
3. Dans l'application Domocasa sur le téléphone, scannez le QR.

Le QR est valable 10 minutes, une seule fois. Chaque jumelage est inscrit au journal de l'app
avec le nom de la personne connectée à Home Assistant.

## Si quelque chose ne va pas

- **Le journal de l'app** (onglet Journal) dit en une ligne pourquoi elle ne démarre pas.
  Joignez-le à votre message à Domocasa.
- **Les téléphones ne retrouvent plus la maison en Wi-Fi** : vérifiez que l'option « Annonce
  sur le réseau de la maison » est activée et que l'app est démarrée.
- **Une seule passerelle par maison** : n'installez pas Domocasa Maison sur deux Home Assistant
  pour la même maison, elles se disputeraient la connexion.

Contact : contact@domocasa.fr
