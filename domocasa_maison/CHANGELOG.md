# Notes de version

## 0.1.11

- Direct et clips des caméras Eufy : la box n'abandonne plus le réveil d'une caméra quand Home
  Assistant met plus de 3 secondes à le confirmer ; elle attend l'image jusqu'à 20 secondes.

## 0.1.10

- Direct des caméras corrigé sur Home Assistant OS : la box ne propose plus au téléphone que
  ses chemins utiles, et sa réponse n'est plus refusée pour sa taille. Hors de chez soi, le
  relais sécurisé prend la suite quand le réseau bloque le chemin direct.
- Une caméra lente à se réveiller a 20 secondes au lieu de 15 pour envoyer son image.

## 0.1.9

- Le journal de l'app indique, pour chaque direct ouvert, refusé ou fermé, les chemins proposés
  par le téléphone et par la box (réseau local, Internet, relais), sans jamais écrire une
  adresse. Il aide à comprendre un direct qui ne s'ouvre pas hors de chez soi.

## 0.1.8

- Le direct des caméras passe par le port 28555 : il n'entre plus en conflit avec l'intégration
  WebRTC Camera, qui occupe déjà le port 8555 sur beaucoup d'installations.

## 0.1.7

- Vue Sécurité : les caméras Eufy de la maison dans l'application Domocasa. Image tout de suite,
  puis le direct en 5 à 9 secondes, en pleine qualité, directement de la box au téléphone (la
  vidéo ne passe par aucun serveur). Le direct s'arrête seul après 5 minutes sans activité pour
  ménager les batteries. Une caméra intérieure n'est visible que lorsque l'alarme est en
  « Absent ». Les caméras se règlent dans les options de l'app (voir la documentation).
- Notifications chiffrées avec la photo du passage : une personne détectée quand la maison est
  vide ou l'alarme en « Absent », la sonnette toujours ; 2 minutes de silence ensuite. Ni Apple,
  ni Google, ni Domocasa ne voient l'image.
- Historique des passages sur 7 jours, avec la photo et un clip de 15 secondes enregistré par la
  box elle-même ; tout reste dans la box. Sur la tablette « Partagée », l'historique s'ouvre avec
  le code de l'alarme.
- Quand on sonne, la box prévient aussitôt les applications ouvertes (appel de la sonnette en
  plein écran).
- Tout cela demande une application Domocasa à jour. Les apps Domocasa déjà installées
  continuent de fonctionner, sans les caméras.
- Un téléphone de technicien perdu peut être coupé : Domocasa publie la liste des certificats
  révoqués, l'app la récupère chaque heure et refuse aussitôt ces certificats, même sans
  Internet ensuite. Les téléphones de la famille ne sont pas concernés.
- Les certificats de technicien durent 90 jours au plus.
- La vidéo passe par go2rtc 1.9.14, intégré à l'app (mot de passe exigé même depuis la box).
- La page Domocasa de Home Assistant sert à l'installation avec Domocasa Pro ; les téléphones
  de la famille s'ajoutent depuis Domocasa Pro ou l'application Domocasa. Les apps Domocasa
  déjà installées continuent de fonctionner.

## 0.1.5

- La température d'une pièce et de la maison ne prend plus la sonde intégrée d'une
  climatisation pour un capteur de la pièce : cette sonde mesure l'air près de la sortie de la
  clim, en haut du mur, et donnait une maison trop chaude. La température d'une clim reste
  affichée sur sa fiche.

## 0.1.4

- Le technicien Domocasa peut renommer un appareil depuis son app, sans ouvrir Home Assistant :
  le nouveau nom est écrit dans Home Assistant lui-même, et l'app Domocasa, Alexa et la tablette
  murale l'utilisent aussitôt. Seuls les appareils montrés dans l'app peuvent être renommés, et
  seulement par le technicien. Les apps Domocasa déjà installées continuent de fonctionner.

## 0.1.3

- Arrosage : quand le programme d'arrosage Domocasa est posé dans Home Assistant, l'app Domocasa
  montre et règle tout le programme (automatique, heure, fréquence et durée de chaque saison,
  pluie), lance un arrosage de 15, 30 ou 60 minutes, lève la pause de pluie, et montre la pile
  et le dernier arrosage de la vanne. Sans ce programme, l'arrosage reste une simple mise en
  marche et un arrêt. Les apps Domocasa déjà installées continuent de fonctionner.
- Le mode technicien de l'app connaît l'adresse locale de la maison même quand il y entre à
  distance.

## 0.1.2

- Les comptes, l'accès hors de chez soi et l'abonnement sont en service : l'app Domocasa peut
  désormais se connecter à la maison.
- Arrosage : une vanne d'eau de Home Assistant paraît dans l'app Domocasa, dans sa pièce, avec
  sa mise en marche et son arrêt. Un arrosage commandé par un interrupteur s'ajoute par le
  réglage **Arrosage** de l'app.
- Les capteurs techniques (température d'une antenne, d'un module…) ne sont plus pris pour la
  température d'une pièce.
- Premier démarrage sur Home Assistant OS corrigé (création de la clé de la maison).

## 0.1.1

Première version publiée, à titre d'essai (la 0.1.0 n'a pas été publiée).

## 0.1.0

Première version, à titre d'essai.

- La passerelle Domocasa devient une app Home Assistant : installation, démarrage, surveillance
  et sauvegarde par Home Assistant lui-même.
- Page **Domocasa** dans la barre latérale pour jumeler un téléphone, voir les téléphones
  jumelés et en retirer un.
- L'identité de la maison est créée au premier démarrage et incluse dans les sauvegardes.
- Aucun accès demandé aux dossiers de Home Assistant : seuls les réglages de l'app sont
  accessibles à l'app.
