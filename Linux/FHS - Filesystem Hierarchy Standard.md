**FS** ou filesystem : systeme de fichiers qui défini l'organisation des données sur un support de stockage.

Linux est un sytème d'exploitation entièrement orienté fichier
tout (ou presque) est représenté par un fichier (données, périphériques, sockets, tubes nommés, etc...)

**FHS** Filesystem Hierarchy Standard défini l'arborescence des fichiers
C'est une norme maintenue par la fondation linux

![**FHS** Filesystem Hierarchy Standard](img/admin/fhs.jpeg)


| Répertoire | Description                                                                                                                                          |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/`        | Le répertoire racine de tout le système de fichiers. Tous les autres répertoires sont montés sous celui-ci.                                          |
| `/bin`     | Contient les programmes binaires essentiels (commandes de base) nécessaires au démarrage et au fonctionnement du système pour tous les utilisateurs. |
| `/boot`    | Contient les fichiers nécessaires au démarrage du système, comme le noyau et les fichiers de configuration du chargeur de démarrage (GRUB).          |
| `/dev`     | **device**<br>Contient les fichiers spéciaux représentant les périphériques matériels (disques, terminaux, etc.).                                    |
| `/etc`     | **Editing Text Config**<br>Contient les fichiers de configuration spécifiques au système, pour l'administration et les services.                     |
| `/home`    | Contient les répertoires personnels des utilisateurs (par exemple, `/home/user1`).                                                                   |
| `/lib`     | Contient les bibliothèques essentielles partagées par les programmes dans `/bin` et `/sbin`.                                                         |
| `/media`   | Point de montage pour les médias amovibles tels que les CD-ROMs, clés USB, etc.                                                                      |
| `/mnt`     | Point de montage temporaire pour les systèmes de fichiers montés manuellement.                                                                       |
| `/opt`     | Contient des paquets logiciels additionnels installés manuellement (souvent des logiciels tiers).                                                    |
| `/proc`    | Système de fichiers virtuel qui fournit des informations sur les processus et l'état du noyau.                                                       |
| `/root`    | Répertoire personnel de l'utilisateur root (administrateur système).                                                                                 |
| `/run`     | Contient des informations sur l'état actuel du système (par exemple, les PID des services en cours d'exécution).                                     |
| `/sbin`    | Contient les programmes binaires essentiels pour l'administration du système (gérés principalement par root).                                        |
| `/srv`     | Contient les données des services offerts par le système (par exemple, les données des serveurs web).                                                |
| `/sys`     | Système de fichiers virtuel qui expose les informations et les points de contrôle du noyau.                                                          |
| `/tmp`     | Contient les fichiers temporaires créés par les programmes. Il est généralement nettoyé au démarrage.                                                |
| `/usr`     | Contient les programmes, bibliothèques, documentation et autres fichiers partagés pour les utilisateurs.                                             |
| `/var`     | Contient les fichiers variables, comme les logs, les mails, les bases de données, etc.                                                               |




