# Notes


##  Notes de cours - VirtualBox et Debian 8.5

### Pourquoi une machine virtuelle ?

Les machines _virtuelles_ ont plusieurs buts, mais l'intérêt reste globalement le même:

  - Réduction des coûts liés au matériel : un ordinateur n'est généralement utilisé qu'à 20% de ses capacités. Utiliser une ou des machines virtuelles sur une même machine _hôte_ permet de rentabiliser le matériel, tout en diminuant le nombre de machines physiques.
  - Séparation des logiciels dans les machines virtuelles: si une machine plante, les autres peuvent continuer leur fonctionnement.
  - Réplication et partage des machines: dans le cadre d'une maintenance, une configuration de machine donnée peut être dupliquée et partagée facilement. De même, les machines virtuelles permettent de créer des environnements de développement avec les mêmes spécifications. Fini le temps du _mais ça fonctionne chez moi !_...

Cet article n'a pas pour but de réaliser pas à pas l'installation d'un système Debian, mais plutôt de voir les quelques étapes de configuration à réaliser pour une meilleure intégration du système invité dans le système hôte.

**J'assumerai donc qu'une installation fraîche de Debian 8.5 est réalisée.**

### Notes préliminaires
  - Télécharger [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
  - Télécharger l'[image de Debian 8](https://www.debian.org/CD/http-ftp/#stable). Choisir l'image en fonction de votre machine _hôte_: une machine en 32 bits ne pourra pas lancer un hôte 64bits, mais une machine 64bits pourra lancer les deux.

### Installation des additions système invité:

Les _additions système invité_ correspondent, pour linux, en un module du noyau, chargé au démarrage de la machine afin de la configurer pour une meilleure intégration avec le système _hôte_.
Entre autres, le support des dossiers partagés, le copier/coller bi-directionnel et le glisser/déposer de fichiers.

Les _addons invité_ nécessitant de compiler le module, il faudra tout d'abord installer les outils nécessaires à la compilation.

```sh
# Passage en mode super-utilisateur:
su
# Rafraichissement de la liste de paquet et mise à jour (si non fait auparavant):
apt-get update && apt-get upgrade
# Installation des paquets:
apt-get install make gcc build-essential module-assistant
```

Afin d'installer cet _addon_, il faut, dans la fenêtre de la machine VirtualBox, cliquer sur _Périphériques_ > _Insérer l'image CD des Addons Invité_. Suivant la version de linux, l'OS proposera de monter automatiquement le CD. Avec Debian 8.5, il sera accessible dans `/media/cdrom`.

Une fois le _CD virtuel_ monté, il faut maintenant installer les addons:

```sh
# Passage en mode super-utilisateur:
su
# Installation:
cd /media/cdrom
sh VBoxLinuxAdditions.run
```

Ensuite, redémarrer la machine virtuelle pour que le module soit bien chargé par le système.


### Préparation du partage sur la machine invité

Si aucun dossier n'a été partagé dans la configuration de la machine virtuelle, il faut éteindre la machine pour les configurer. Dans le gestionnaire de VirtualBox, ouvrir les propriétés de la machine et cliquer sur l'onglet _Dossiers partagés_. Ajouter un partage en sélectionnant le dossier que vous souhaitez partager et cochez la case _Montage automatique_. Ainsi, le dossier sera accessible sur la machine à chaque démarrage.

Démarrer la machine virtuelle.

Si vous tentez maintenant de créer un fichier dans le dossier partagé avec un utilisateur _standard_ (`touch /media/sf_partage/test`), le système ne vous autorisera pas à le faire. En effets, vous n'avez pas les droits suffisants pour écrire dedans:

```sh
ls -lha /media
# Retourne 
drwxrwx---  1 root vboxsf 4,0K août  23 11:04 sf_partage
```
Nous voyons bien ici que le dossier partagé *sf_partage* appartient à l'user **root** et au groupe **vboxsf**. Il faut donc que l'utilisateur en cours appartienne au groupe **vboxsf**.

### Création d'un nouvel utilisateur

```sh
# Passage en mode super-utilisateur:
su
# Creation de l'user 'toto' (remplir les questions si besoin est, valider par 'entrée' pour des entrées vides.)
adduser toto
```

### Ajou d'un utilisateur à un groupe

```sh
# Passage en mode super-utilisateur:
su
# Ajou de l'user au groupe vboxsf
adduser toto vboxsf
```

L'utilisateur doit maintenant avoir accès en lecture/écriture au dossier partagé, disponible dans */media/sf_<nom_du_dossier>*. Cela peut se férifier en essayant de créer un fichier en utilisateur "lambda":

```sh
touch /media/sf_partage/test
```

### Notes en vrac

#### Commandes usuelles:

```sh
# Passage en super-utilisateur
su

# Passage en un utilisateur spécifique:
su <nom_de_l_utilisateur>

# Mise à jour de la liste des paquets
apt-get update

# Mise à jour des paquets
apt-get upgrade

# Installation de paquets en console:
apt-get install <paquet_1 paquet_2 ...>

# Exécuter plusieurs commandes en une ligne : &&
commande 1 && commande 2 && commande x
# Cela executera la commande suivante si la précédente réussit. ex:
apt-get update && apt-get upgrade
```

**Cet article est une ébauche et un essai de prise de notes**