[[Ligne de commande]] 
 
- Le terminal est l’outil de prédilection de l’administrateur Unix/Linux
- Lorsqu'on est physiquement devant la machine, on utilise une des 7 consoles proposées par Linux
- Pour se connecter à distance sur un serveur Linux, on utilise un **émulateur de terminal**
- Il existe des **émulateurs de terminal** pour Windows, macOS et bien sûr Linux

Terminal, émulateur de terminal, console… Avec ces outils, on se connecte localement ou à distance sur le serveur Linux à administrer.
Quelle que soit la version du logiciel a utiliser, il  faut interagir avec le système en mode texte, c'est-à-dire saisir des **commandes**. Ce processus est assuré au moyen d'un [[shell]]



Table des matières :
	[Le terminal](#Le terminal)
	- [prompt -invite de commande](#prompt -invite de commande)
	- [Commandes internes](#Commandes internes)
	- [Commandes externes](#Commandes externes)
	- [Histoire](#Histoire)
	- [Connection au serveur en directe](#Connection au serveur en directe)
	- [Connection au serveur à distance](#Connection au serveur à distance)
		- [PuTTY sous Windows](#PuTTY sous Windows)
		- [Terminal sous macOS](#Terminal sous macOS)
		- [xterm et autres sous Linux](#xterm et autres sous Linux)
	[Hyperviseurs de type 1 et 2](# Hyperviseurs de type 1 et 2)
	[Canaux de linux](# Canaux de linux)
	[inodes](#inodes)
	[Gestion des droits](#Gestion des droits)
	
	
	 



## Le terminal

[command line reference](https://ss64.com/bash/syntax-prompt.html)

Nativement interactif  avec le poste de travail qui le fait tourner, il permet de :
- se connecter avec un protocole réseau sur le serveur distant autant de fois que souhaité,
- y compris plusieurs fois sur le même serveur avec des utilisateurs différents (dans la limite de connexions simultanées configurées sur chaque serveur).
### prompt -invite de commande
`nom_utilisateur@hostname_machine:~$`
par exemple
`bruno@virtualbox:~$`

| caractère | nom       | signification                               |
| --------- | --------- | ------------------------------------------- |
| `@`       |           | séparateur                                  |
| `$`       | delimiter | utillisateur non privilégié<br><br>variable |
| `#`       | delimiter | utilisateur root                            |
| `~`       | tilde     | répertoire personnel de l'utilisateur       |
La configuration du prompt est définie dans la variable  `$PS1`  .

| Variable | contient                                                           |
| -------- | ------------------------------------------------------------------ |
| `$SHELL` | la commande exécutée pour lancer le shell après l'authentification |
| $PATH    | la liste des répertoires référençant des commandes externes.       |
| `$PS1`   | La configuration du prompt                                         |




### Changer d'utilisateurs Ubuntu

#### Passer en mode `root` avec `sudo`, `sudo -i` ou `sudo su`

Ubuntu, par défaut, désactive le compte `root` et encourage l'utilisation de `sudo` pour exécuter des commandes en tant que superutilisateur. Pour exécuter une commande avec des privilèges `root`, utilisez :
`sudo <commande>`

Si vous souhaitez obtenir une session `root` interactive, vous pouvez utiliser :

- **Avec `sudo -i` :** Cela ouvre un shell avec les privilèges `root` :    
    `sudo -i`

- **Avec `sudo su` :** Cela change l'utilisateur actuel en `root` :

    `sudo su`

#### Passer en utilisateur standard
Si vous êtes actuellement en mode super-utilisateur dans le terminal, vous pouvez retourner à votre compte utilisateur standard en entrant la commande suivante :

`exit`

Cela fermera la session root et vous ramènera à votre session utilisateur normale si vous avez utilisé `sudo -i` ou `sudo su` pour passer en mode root.

Si vous avez utilisé la commande `su` pour passer à l'utilisateur root, vous pouvez revenir à votre utilisateur standard en utilisant `exit` ou en spécifiant directement le nom d'utilisateur :

`su - <nom_utilisateur>`




### Commandes internes
sont livrées avec l'interpréteur de commandes
pas forcément intégrées à l’interpréteur de commandes qu'on utilise. 
leurs options ne sont pas forcement toutes identiques.
exemple : `echo`
```bash
~$ type echo
echo is a shell builtin
```


Aide du shell
```bash
~$ help nom_de_la_commande
```
### Commandes externes
pas fournies par le shell.
sont généralement sous la forme d'un fichier compilé binaire ou d'un fichier disposant des droits d'exécution (comme un script Perl par exemple).
exemple : `bash`
```bash
~$ type bash
bash is /usr/bin/bash
```

Aide du shell
```bash
# Résumé de la documentation
~$ nom_de_la_commande --help
# Manuel officiel unix
~$ man nom_de_la_commande
```
### Histoire
Dans les 60ies 70ies, Les ordinateurs étaient de très grosses machines

Le terminal informatique désignait un équipement périphérique entrée/sortie  permettant d'opérer le système. Il pouvait posséder un clavier, un écran avec un pointer.

Avec la miniaturisation, les terminaux physiques ont laissé la place aux **terminaux virtuels, ou émulateurs de terminaux**.
Un logiciel émule (simule) l'équipement terminal physique et toutes ses fonctionnalités.

Un  programme qui se lance sur un système d'exploitation et qui permet de se connecter localement ou à distance sur le serveur à administrer.

Il devient donc possible de lancer plusieurs terminaux simultanément depuis le même environnement

Le protocole VNC ([Virtual Network Computing](https://openclassrooms.com/fr/courses/1733046-prenez-le-controle-a-distance-dun-poste-linux-windows-avec-vnc)) permet notamment de prendre la main à distance sur un ordinateur. C’est un protocole de terminal virtuel graphique.

Le protocole RDP ([Remote Desktop Protocol](https://fr.wikipedia.org/wiki/Remote_Desktop_Protocol))  permet de se connecter sur des serveurs Windows Terminal Serveur.

La **console** sous Linux est un périphérique gérant le clavier et l'écran de l'ordinateur et propose d'interagir avec l'utilisateur via un **terminal en mode texte**

### Connection au serveur en directe

la console de Linux propose 7 terminaux en mode texte, appelés aussi les **terminaux physiques**. Ils sont directement sur le clavier branché à l'ordinateur et disponibles à partir des combinaisons de touches : “CTRL+ALT+F1” ; “CTRL+ALT+F2” ; … jusqu’à “CTRL+ALT+F7”.
Chacune de ces combinaisons de touches propose l'émulation d'un terminal (en mode console) différent sur lequel il est possible de se connecter de manière indépendante avec un compte utilisateur différent.

### Connection au serveur à distance

connecté à distance sur votre serveur Linux via un émulateur de terminal. Il s’agit d’un programme lancé sur votre poste de travail Windows/Mac ou même Linux. Il gère la connexion au serveur distant avec un protocole réseau (telnet, rlogin ou SSH).

#### PuTTY sous Windows
est à la fois un émulateur de terminal et un client pour différents protocoles réseau tels que telnet, SFTP, SSH, rlogin, et TCP

#### Terminal sous macOS

**MacOS** étant un dérivé de la branche historique BSD (Berkeley Software Distribution) des Unix communautaires universitaires, l'émulateur de terminal est dans un milieu natif : l'application est livrée par défaut avec le système.

#### xterm et autres sous Linux

**xterm**, c'est  le papy de la famille, beaucoup d'émulateurs sont des variantes de xterm.
- GNOME propose [**GNOME Terminal**](https://help.gnome.org/users/gnome-terminal/stable/). C’est un grand classique également qui, outre les fonctionnalités de son grand-père, est livré avec la gestion des onglets, la transparence et les fonctions de drag and drop notamment. [La page de documentation](https://help.gnome.org/users/gnome-terminal/stable/) sur le site gnome.org est très bien faite !
    
- KDE propose l'émulateur **[Konsole](https://konsole.kde.org/)**, qui réécrit toutes les fonctionnalités de xterm, avec des ajouts assez intéressants comme, par exemple, son intégration native dans divers outils de développement tels que KDevelop, Kate, ou encore l'explorateur de fichier Dolphin.
    
- **[xfce-terminal](https://docs.xfce.org/apps/terminal/start)** a été développé pour remplacer GNOME Terminal et propose les fonctionnalités essentielles, comme ses cousins mais sans dépendance à tel ou tel environnement de bureau (GNOME ou KDE par exemple). Il est donc très léger. Il est livré par défaut avec XFCE.
    
- **[urxvt](https://sourceforge.net/projects/rxvt/)**, mon terminal préféré, malgré son nom un peu nerd... Ce programme est la suite logique de xterm épuré des fonctionnalités jugées non indispensables. Donc, c'est difficile de faire plus léger ! Outre le fait de pouvoir le lancer en arrière-plan en tant que démon (ou _daemon_) il propose également les fonctionnalités classiques : gestion des couleurs et des onglets lorsque nécessaire notamment.



## Hyperviseurs de type 1 et 2

Comment sont gérés les terminaux virtuels dans un environnement Linux virtualisé ?

L'installation d'un serveur Linux sur un hyperviseur de niveau 1 ne change rien. L'installer sur un hyperviseur de niveau 2 peut en revanche créer quelques ambiguïtés.

En effet, l'hyperviseur de niveau 2 (dans l'exemple ci-dessous Oracle Virtualbox) va proposer l'affichage de la console et des terminaux physiques… de manière virtuelle :
1. L'une étant la console, elle “capture” votre souris lorsque vous cliquez dedans, et vous êtes virtuellement considéré devant le serveur Linux avec le clavier et l'écran géré par la console et 7 terminaux physiques à votre disposition.
    
2. L'autre est l'émulateur de terminal, intégré nativement dans l'environnement graphique de votre poste de travail, qui ne “capture” pas votre souris, mais permet au contraire le copier/coller etc.

## Canaux de linux
Dans la majorité des cas, tous les programmes exécutés sous Linux disposent de 3 canaux de données :

1. **`stdin`**(pour standard input) : c'est le canal de l'entrée standard, et par défaut, lorsque vous lancez une commande, c'est votre clavier. La commande sera éventuellement capable de lire les informations saisies avec le clavier via ce canal. Il porte le descripteur de fichier **numéro 0** ;
    
2. **`stdout`**(pour standard output) : c'est le canal de la sortie standard, et lorsque vous lancez une commande depuis un terminal, c'est l'écran par défaut. Le résultat et les données affichées par la commande sont diffusés sur l'écran. Il porte le descripteur de fichier **numéro 1** ;
    
3. **`stderr`**(pour standard error) : c'est le canal du flux concernant les erreurs, et par défaut, lorsque vous lancez une commande, c'est aussi l'écran. La commande va différencier les données “normales” des données “erreur” et peut changer de canal pour diffuser ces informations.
    

![stdout est le canal de la sortie standard, et lorsque vous lancez une commande depuis un terminal, c'est l'écran par défaut.  stdin est le canal de l'entrée standard, et par défaut, lorsque vous lancez une commande, c'est votre clavier.   stderr est l](https://user.oc-static.com/upload/2021/11/03/16359498508624_2c2-1.png)

Pour manipuler ces canaux, il est nécessaire d'utiliser les caractères représentant des :
- chevrons simples tels que**`>`**et**`<`**
- mais aussi doublés tels que**`>>`**et**`<<`**


## inodes

un fichier est une structure du langage C nommée "inode"
elle est définie directement au niveau [du code noyau de Linux](https://github.com/torvalds/linux/blob/master/fs/inode.c).

Elle peut se représenter par une **[liste de champs](https://en.wikipedia.org/wiki/Inode_pointer_structure#/media/File:Ext2-inode.svg)** illustrée généralement sous la forme d’un tableau, que l'on va étudier par dézooms successifs

Inode, ses informations (taille, propriétaire et groupe propriétaire, permissions, date de ses derniers accès (lecture, modification), etc.) :
![Inode](img/admin/inode.png)

Dans cet inode, il y a :
- **les adresses de blocs directes**. Ces 12 champs contiennent les adresses directes des données du fichier sur les périphériques de type blocs les contenant (disque dur, périphériques externes type clé USB, etc.) :
![inode-2](img/admin/inode-2.png) 

**les adresses de blocs indirects**. Ces champs contiennent simplement des pointeurs vers d'autres inodes dont la totalité des champs est adressée pour des blocs de données.

L’adresse contenue dans la ligne 13 renvoie à un nouvel inode ou bloc de pointeurs. Ce nouvel inode contient, lui, **128 lignes.** Chacune des adresses contenues dans ces lignes renvoient vers un bloc de données. On dit que ces blocs de donnés sont indirects :
![inode-3](img/admin/inode-3.png)



L’adresse contenue dans la ligne 14 renvoie à un nouvel inode ou bloc de pointeurs de **128 lignes.**  Chacune des adresses contenues dans ces lignes renvoient vers un nouvel inode contenant à nouveau 128 lignes (oui c’est énorme !) Et chaque adresse contenue dans chaque ligne renvoie vers un bloc de données. On dit que ces blocs de donnés sont **doublement indirects**
![inode-4](img/admin/inode-4.png)

ligne 15... triple redirection !

Les **liens** durs/symboliques sous Linux représentent des pointeurs entre inodes et sont gérés avec la commande **ln**


## Gestion des droits

[[Autorisations des fichiers Linux]]

principe fondamental de la gestion des droits sous Unix et Linux : **DAC** (**Discretionary Access Control**)

Les droits associés aux objets (répertoires, fichiers, processus, etc.) sont  définis pour :

- Le propriétaire de l'objet
- Le groupe propriétaire de l'objet
- Tous les autres : comptes utilisateurs et/ou système qui ne sont pas le compte et le groupe propriétaire.

le propriétaire de l'objet (ainsi que le super utilisateur **root**) peut directement gérer les droits associés à cet objet.
Un utilisateur peut  créer, modifier ou supprimer ses propres objets, et définir quels autres comptes utilisateurs peuvent accéder en lecture ou modification à cet objet.

**`chown`** change owner, modification du compte propriétaire.
`chown utilisateur_propriétaire:groupe_propriétaire nom_du_fichier`

On peut ajouter l'option récursive, FAIRE TRES ATTENTION
Tous les fichiers et tous les dossier (et leurs contenu) du répertoire actuel seront impactés :
`chown -R utilisateur_propriétaire:groupe_propriétaire *`



`chgrp` change groupe
`chgrp groupe_propriétaire nom_du_fichier`