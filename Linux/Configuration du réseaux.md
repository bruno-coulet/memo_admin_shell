
Appuyer 2 sur la touche tabulation pour afficher les options d'une commande


### Nom de réseau du serveur
**system hostname**
sert d'identifiant par défaut de la machine pour tous les services et applications qui s'exécutent en local et pour beaucoup de services et d'applications lorsque ceux-ci communiquent sur le réseau.
Garder un format simple, un mot.

### Affiche le nom du serveur depuis un compte root :
`cat /proc/sys/kernel/hostname`
ou
`sysctl kernel.hostname
ou 
`hostnamectl status`

### Change le nom du serveur 

de manière dynamique :
`hostnamectl set-hostname nom_de_mon_serveur`
ou
modifier le fichier qui contietn le nom du serveur
`/etc/hostname`

### Display message
affiche les messages du noyau au démarrage
`dmesg`
filtre les message liés au réseau :
`dmesg | grep Network`

### /sys
**sysfs** : Arborescence du système de fichiers virtuels sous Linux
introduit avec le noyau Linux 2.6 

Le répertoire `/sys` est principalement utilisé par le noyau et les programmes système pour :
- Interagir avec les pilotes de périphériques.
- Configurer des aspects spécifiques des périphériques matériels.
- Obtenir des informations en temps réel sur les périphériques et le matériel.

Affiche des infos sur les carte réseaux  :
`/sys/class/net`
vérifier la vitesse actuelle d'un processeur : `/sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq`.


### configurer une interface réseau de manière dynamique

paquet `iproute2`

sur toutes les distributions Linux, configurer de manière dynamique les cartes réseaux avec la commande **`ip`**.

`ip `+2 x la touche tabulation pour afficher les options disponibles

Toutes les configurations de réseau sur les cartes gérées par la commande **`ip`** sont dynamiques. Elles seront donc perdues entre chaque "reboot" du serveur.

Pour configurer de manière statique les cartes réseaux de Linux, il est nécessaire de saisir les informations dans des fichiers de configuration qui vont être lus pendant le boot du serveur.

Affiche les routes :
`ip route list`


## DNS
**Domain Name System**. Ce service permet au serveur d'effectuer la résolution des noms de domaines en adresse IP, afin d'envoyer des requêtes selon le protocole du service destinataire.

fichiers `/etc/hosts` et **`/etc/resolv.conf`** 


