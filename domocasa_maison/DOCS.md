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

## Arrosage

Les vannes d'eau de Home Assistant (entités `valve.…`, hors gaz) apparaissent d'office dans
l'application, dans la pièce de la vanne : « En marche » / « Arrêté », un toucher pour basculer.

Un arrosage branché sur un simple interrupteur (`switch.…`) n'apparaît **que si vous le
nommez** dans l'option `arrosage` (onglet Configuration), par exemple `switch.arrosage_jardin` :
Home Assistant crée des dizaines d'interrupteurs (voyants, verrous enfant…) qu'on ne veut pas
piloter depuis un téléphone. Les programmes d'arrosage restent des automatisations de Home
Assistant. Mettez l'app Domocasa à jour sur les téléphones **après** cette app.

## Caméras (vue Sécurité)

Il faut l'intégration `eufy_security` avec son add-on `eufy-security-ws` et son go2rtc. Pour
votre sécurité, ni go2rtc ni `eufy-security-ws` ne doivent être joignables depuis le réseau de la
maison : Domocasa vous aide à le vérifier.

### Réglages

- `cameras` : une ligne par caméra Eufy, `camera.entree=T8140P1234567890` (le numéro de série se
  lit dans l'application Eufy).
- `cameras_interieures` : celles qui filment l'intérieur. Elles ne sont visibles dans
  l'application que lorsque l'alarme est en « Absent », jamais sur la tablette « Partagée ».
- `cameras_louees` : celles qui voient une partie louée (étiquette « Airbnb ») ; à signaler dans
  l'annonce, et aucune ne doit filmer l'intérieur du logement loué.
- `cameras_sonnettes` : les caméras des sonnettes (par exemple `camera.doorbell`).
- `camera_principale` : la caméra montrée en grand dans l'écran Sécurité (sinon la sonnette).

### En direct

L'image de la caméra s'affiche tout de suite, puis le direct en 5 à 9 secondes (le temps que la
caméra se réveille), dans la meilleure qualité qu'elle donne. La vidéo va directement de la box
au téléphone, chiffrée ; elle ne passe par aucun serveur Domocasa. Pour ménager les batteries, un
direct s'arrête seul après 5 minutes sans activité, et 4 directs au plus sont ouverts en même
temps dans la maison. Les personnes qui gèrent la maison voient les caméras ; les autres membres
aussi, sauf si on leur retire ce droit. Le technicien Domocasa ne voit jamais d'image.

### Notifications

Une notification part avec la photo du passage quand une personne est détectée et que la maison
est vide ou l'alarme en « Absent ». La sonnette notifie toujours. Ensuite, 2 minutes de silence
pour la même caméra. Elles sont chiffrées de bout en bout : ni Apple, ni Google, ni Domocasa ne
voient l'image. La tablette « Partagée » ne reçoit jamais de notification. Quand on sonne, les
applications ouvertes montrent l'appel de la sonnette en plein écran.

### Historique

À chaque passage notifié, la box garde la photo et un clip de 15 secondes qu'elle enregistre
elle-même ; le clip commence 5 à 9 secondes après la détection (réveil de la caméra). Tout reste
**dans la box** (dossier de l'app, jamais envoyé au cloud), 7 jours au plus et 512 Mo en tout :
quand la place manque, la caméra qui en prend le plus perd d'abord ses passages les plus anciens.
Sur la tablette « Partagée », l'historique ne s'ouvre qu'avec le code de l'alarme, pour 5 minutes.

## Installer avec Domocasa Pro

1. Ouvrez **Domocasa** dans la barre latérale de Home Assistant (réservé aux administrateurs).
2. Dans **Installer avec Domocasa Pro**, touchez **Afficher le QR**.
3. Le technicien Domocasa le scanne avec Domocasa Pro, pendant l'installation.

Le QR est valable 10 minutes, une seule fois. Les téléphones de la famille s'ajoutent ensuite
depuis Domocasa Pro ou depuis l'application Domocasa ; la page **Téléphones de la maison** les
liste, et **Retirer** coupe aussitôt un téléphone perdu.

## Si quelque chose ne va pas

- **Le journal de l'app** (onglet Journal) dit en une ligne pourquoi elle ne démarre pas.
  Joignez-le à votre message à Domocasa.
- **Les téléphones ne retrouvent plus la maison en Wi-Fi** : vérifiez que l'option « Annonce
  sur le réseau de la maison » est activée et que l'app est démarrée.
- **Une seule passerelle par maison** : n'installez pas Domocasa Maison sur deux Home Assistant
  pour la même maison, elles se disputeraient la connexion.

Contact : contact@domocasa.fr
