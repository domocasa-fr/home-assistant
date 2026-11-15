# Notes de version

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
