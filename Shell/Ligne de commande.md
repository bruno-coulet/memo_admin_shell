 [[Bash Scripting]]     [[Bash]]      [[Shell]]     [[Environnement virtuel Python 1]] [[Vim]]

**shell** :          interpréteur de commandes, exécute les commandes rentrées.
**Terminal** :    fenêtre graphique qui permet d'interagir avec l'interpréteur de commande 
		   est considéré comme un périphérique

## shell
C'est un interpréteur de commandes.

Un programme qui interprète les commandes saisies par l'utilisateur et les exécute en interagissant avec le noyau du système d'exploitation ou avec d'autres programmes.

Ce programme est lancé par le système juste après la phase d'authentification sur un [[#Terminal]]

![Shell](img/admin/shell.png)

Signifie “coquille”, désigne la première couche logicielle entourant le noyau linux

Ils fournissent généralement des fonctionnalités telles que :
- l'interprétation des commandes
- la redirection d'entrée/sortie
- la gestion des processus
- les variables
- les boucles
- les conditions
- etc...

Ils permettent aux utilisateurs d'effectuer une grande variété de tâches, de la gestion de fichiers à l'automatisation des tâches, en passant par la configuration du système.

Il existe plusieurs types de shell, chacun offrant ses propres fonctionnalités et caractéristiques.

Il y a 2 types de shell principaux :
1. [[#Shells d'interface utilisateur (UI)]]
2. [[#Shells de script]]
### PowerShell
<font color="orange">Conseil sur WIndows :</font>
**NE PAS** utiliser l'invite de commande et le powershell
Ou alors appeler `bash`depuis powershell
Il vaut mieux utiliser **WSL** ou **[[Gitbash]]** qui fonctionne comme un système Unix


## Terminal
(Plus précisement émulateur de terminal, puisque le terminal est un appareil physique des année 60/70)
fenêtre graphique qui permet d'interagir avec l'interpréteur de commande (shell)
## CLI - Command Line Interface
interface qui permet aux utilisateurs d'interagir avec un logiciel ou un système d'exploitation en saisissant des commandes sous forme de texte, plutôt qu'en utilisant une interface graphique.
Une CLI peut être fournie par un shell, mais elle peut aussi être intégrée à d'autres programmes ou environnements.


## Shells d'interface utilisateur (UI) 
 
 Ces shells sont interactifs et fournissent une interface à l'utilisateur pour interagir avec le système d'exploitation. L'utilisateur saisit des commandes et reçoit des réponses ou des résultats en retour. Les exemples incluent :

- [[Bash]] (Bourne Again SHell)    Le shell par défaut sur de nombreux systèmes Unix/Linux.
- PowerShell                             Le shell par défaut sur les systèmes Windows modernes.
- Zsh (Z Shell)                           Un shell amélioré et étendu basé sur Bash.

## Shells de script 

Ces shells sont utilisés pour exécuter des scripts, c'est-à-dire des séquences de commandes enregistrées dans un fichier texte. Ils interprètent les commandes contenues dans le script et les exécutent séquentiellement. Les exemples incluent :

- [[Bash]]
- PowerShell
- Csh (C Shell)
- Ksh (Korn Shell)

### shebang (ou _hashbang_)
Suite de caractères qu’on met **au tout début d’un script exécutable** pour indiquer **quel interpréteur doit être utilisé** pour l’exécuter.
c'est le #! suivi du chemin absolu vers l'interpreteur
`wich bash` donne le chemin absolu


Exemple avec script.sh :
```sh
#!/bin/bash
lignes de code 1
lignes de code 2
lignes de code n
```
  La première ligne dit au système d'utiliser le programme `/bin/bash` pour lire ce fichier

Il faut rendre le fichier executable avec la commande `chmod +x nom_du_fihier`
`x`veut dire éxécutable
```sh
chmod +x script.sh
```
Puis lancer l'execution
```sh
./script.sh
```
il sera lancé avec **Bash**, même si ton shell par défaut est `zsh` ou autre.

Dans un script :
- `$0` = le nom du script
- `$1`= le 1er  argument passé au script ou à la fonction
- `$2`= le 2ème argument passé au script ou à la fonction


 `tty`  ( teletypewriter, ancêtre du terminal )  affiche le nom du terminal
 

## Instruction

Par exemple :  ``cp -R dossier1 dossier2``

|             | commande | options       | paramètres                   |
| ----------- | -------- | ------------- | ---------------------------- |
| code        | `cp`     | `-R`          | `dossier1 dossier2`          |
| explication | copie    | récursivement | le 1er est copié dans le 2nd |
## - Options
Les **options** (aussi appelées **flags** ou **switches**) permettent d'activer ou de désactiver certaines fonctionnalités d'une commande. Elles se présentent généralement sous deux formes :

- **`-`** : options courtes, souvent représentées par une seule lettre 
             `-h` pour afficher l'aide
- **`--`** : options longues, plus explicites et composées de mots complets 
              `--help` pour afficher l'aide

Les options peuvent être combinées lorsqu'il s'agit d'options courtes.
`-a -b -c` peut être abrégé en `-abc`

### **`--`**       (sans option après)
- **`--`** tout seul, indique la **fin des options**.
  Cela permet d'utiliser des arguments qui pourraient être interprétés comme des options. 
  
  `rm -- -fichier.txt`
  Supprime lez fichier nommé `-fichier.txt`
  le nom commençant par un tiret, il aurait pût être confondu avec une option

### distinction entre flag et option

**flags = options sans argument**

- **Option** : terme générique qui englobe à la fois les **flags** et les options qui requièrent un argument (qui spécifient un comportement plus complexe).

- **flag** : sous-ensemble des options qui **n'a pas besoin d'argument**. Son seul but est d'indiquer la présence ou l'absence d'une fonctionnalité.

---

## Paramètres
Les **paramètres** incluent tout ce qui est passé à une commande, qu'il s'agisse d'options ou d'arguments. Ils sont généralement composés d'éléments sur lesquels la commande doit opérer (fichiers, répertoires, etc.). Les paramètres sont généralement placés après les options dans une commande.

$1 est le 1er argument
$2 le 2eme argument

---

## Arguments
Les **arguments** désignent spécifiquement les entrées sur lesquelles une commande agit, à l'exclusion des options. Ce sont les données ou les valeurs sur lesquelles la commande va opérer directement.

- Un argument est un type spécifique de paramètre qui se réfère principalement aux éléments qui ne sont ni des options ni des flags. Les arguments sont souvent des fichiers, des chaînes de texte ou d'autres valeurs de données.
  
- **Utilisation** : Les arguments fournissent les données sur lesquelles la commande doit effectuer une opération.

- **Exemple** : Dans la commande **`grep "text" file.txt`**, `"text"` et `file.txt` sont des arguments : `"text"` est la chaîne à rechercher et `file.txt` est le fichier dans lequel effectuer la recherche.  

## Commandes & raccourcis clavier

 `*` est un joker (wildcard) en ligne de commande Unix/Linux.
 Il correspond à n'importe quelle séquence de caractères

| Commande                                                    | Effet                                                                                                                                                                           |
| ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ``CTRL+A ``                                                 | début de la ligne                                                                                                                                                               |
| ``CTRL+E``                                                  | fin de la ligne                                                                                                                                                                 |
| ``MAJ+CTRL+C  MAJ+CTRL+V``                                  | copier coller                                                                                                                                                                   |
| ``uname -a``                                                | affiche les infos du système                                                                                                                                                    |
| ``whomai``                                                  | affiche l'user id                                                                                                                                                               |
| ``echo``                                                    | affiche les paramètres                                                                                                                                                          |
| ``man``                                                     | ouvre la page de manuel de la commande passée en paramètre                                                                                                                      |
| ``exit``                                                    | ferme le shell                                                                                                                                                                  |
| `pwd`                                                       | present working directory - dossier actuel                                                                                                                                      |
| [`mkdir nom-du-dossier`](#mkdir)                            | make directory - crée un dossier                                                                                                                                                |
| `touch nom-du-fichier.extension`                            | Crée un fichier                                                                                                                                                                 |
| ``echo "Blabla" > nouveau.txt``                             | Crée le fichier nouveau.txt qui contient le texte "Blabla"                                                                                                                      |
| `echo "blabla" >> fichier.txt`                              | Linux/Mac - ajoute blabla en bas d'un fichier                                                                                                                                   |
| `echo blabla  >> fichier.txt`                               | Windows - ajoute blabla en bas d'un fichier                                                                                                                                     |
| `cat ~/.mon_fichier`<br>`cat mon_fichier`                   | Affiche le contenu de mon_fichier                                                                                                                                               |
| ``rm``                                                      | Efface (remove)                                                                                                                                                                 |
| ``rm -r ``                                                  | Efface récursivement                                                                                                                                                            |
| ``rmdir rep ``                                              | Efface le répertoire vide rep                                                                                                                                                   |
| ``mv ancien_nom.txt nouveau_nom.txt``                       | Renomme un fichier                                                                                                                                                              |
| ``mv fichier /nouvel/emplacement``                          | Déplace un fichier                                                                                                                                                              |
| ``cp fichier1 fichier2``                                    | copie le fichier1 en fichier2                                                                                                                                                   |
| ``cp -r r1 r2``                                             | copie le répertoire r1 en r2                                                                                                                                                    |
| [`ls`](#ls)                                                 | lister les fichiers présents                                                                                                                                                    |
| `ls -a`                                                     | Liste les fichiers présents, y compris les fichiers cachés                                                                                                                      |
| `;` <br>                                                    | Séparateur de commande, permet d'exécuter plusieurs commandes en séquence, indépendamment du succès ou de l'échec de la commande précédente.<br>                                |
| `cd nom-du-dossier/nom-du-fichier`                          | change direction<br>Navigue vers un dossier ou fichier parmis ceux dans le dossier actuel                                                                                       |
| ``/``                                                       | répertoire racine                                                                                                                                                               |
| `./`                                                        | répertoire actuel (optionnel car implicite)                                                                                                                                     |
| `../`                                                       | répertoire parent                                                                                                                                                               |
| `../../fichier-voulu`                                       | remonte 2 niveaux dans l'arborescence                                                                                                                                           |
| ``~``                                                       | répertoire de l'user / de login / ouvert par défaut                                                                                                                             |
| ``cd`` =`` cd ~``                                           | cd sans paramètre équivaut à cd ~                                                                                                                                               |
| ``cd -``                                                    | retour au répertoire qu’on a quitté<br>(bash l’enregistre dans une variable d'environnement)                                                                                    |
| ``sudo pacman -Syu``                                        | manjaro <br>met à jour la liste des paquets et le système pour                                                                                                                  |
| ``apt update``                                              | Debian<br>met à jour la liste des paquets et le système à télécharger pour                                                                                                      |
| ``apt upgrade``                                             | Debian<br>télécharge les paquets et le système dans la liste                                                                                                                    |
| ``man``                                                     | Afficher le manuel                                                                                                                                                              |
| ``man [OPTION]... [COMMAND NAME]...``                       |                                                                                                                                                                                 |
| ``cat nom-du-fichier``                                      | concatenate<br>Affiche le contenu d'un fichier<br>peut être utilisé pour concaténer plusieurs fichiers ensemble.                                                                |
| ``cat fichier-1.txt fichier-2.txt``                         | pour joindre le contenu de deux fichiers et l'afficher.                                                                                                                         |
| ``less nom-du-fichier``                                     | affiche de grands fichiers texte page par page  <br>Cela ouvrira le fichier nom_du_fichier.txt dans l'interface de "less."                                                      |
| ``grep "exemple" fichier.txt  ``<br><br>                    | Affiche dans le terminal toutes les lignes contenant le mot "exemple"                                                                                                           |
| `grep -i "exemple" fichier.txt`                             | idem<br> mais insensible à la casse                                                                                                                                             |
| `grep -n "exemple" fichier.txt`                             | idem<br>affiche  le numéro de ligne pour chaque correspondance                                                                                                                  |
| `find . -type f -name "fichier.txt"`  <br>                  |                                                                                                                                                                                 |
| `find`<br>                                                  | commande de recherche de fichiers.                                                                                                                                              |
| `.` <br>                                                    | spécifie le répertoire de départ de la recherche (répertoire actuel)                                                                                                            |
| `-type f`                                                   | indique que nous recherchons des fichiers, pas des répertoires.                                                                                                                 |
| `-name "fichier.txt"`                                       | spécifie que nous recherchons un fichier ayant le nom "fichier.txt".                                                                                                            |
| ``sudo adduser nom-utilisateur``                            | crée un utilisateur                                                                                                                                                             |
| `file nom_du_fichier`                                       | information sur un fichier                                                                                                                                                      |
| `type nom-du-fichier`                                       | afffiche le type built-in ou externet                                                                                                                                           |
| `history`<br>`!124`<br>`CTRL R`<br>`CTRL R`<br>`tabulation` | affiche l'historique  numéroté du shell<br>relance la commande numéro 124<br>recherche par mot clé dans l'historique<br>remonter d'une occurence<br>relance la commande trouvée |
| `alias                                                      | affiche les alias<br>crée dans le fichier .bashrc                                                                                                                               |

### `ls`

Liste le contenu d'un répertoire


| Paramètre | signification                                                                           |
| --------- | --------------------------------------------------------------------------------------- |
| `ls -l`   | informations détaillées et sur une suele colonne                                        |
| `ls -a`   | inclus les fichiers cachés (commencent par un point)                                    |
| `ls -d`   | précie le répertoire, pas son contenu                                                   |
| `ls -F`   | spécifie le type :<br>`/` répertoire<br>`*` exécutable<br>`@` lien symbolique<br>etc... |
| `ls -R`   | récursif (contenu des répertoires)                                                      |
| `ls -t`   | trie par date de modification, du + récent au + ancien                                  |
| `ls -c`   | affiche par date de changement d'état                                                   |
| `ls -u`   | par date d'accès au fichier                                                             |
| `ls -r`   | inverse l'ordre                                                                         |
| `ls -i`   | affiche l'inode du fichier                                                              |
| `ls -C`   | sur plusieurs colonne (par défaut)                                                      |



```
$ ls -l
total 40
-rw-r--r-- 1 bruno collègues 2155 oct.29 12:51 resultat.txt
```

| Exemple       | Signification                                                                                                                                                                                                                     |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -rw-r--r--    | 1er caractère = type de fichier<br> -           ordinaire<br> d           répertoire<br> l            lien symbolique<br><br>9 caractères suivants = droits<br>rw-        utilisateur<br>r--         groupe<br>r--         autres |
| 1             | compteur de lien                                                                                                                                                                                                                  |
| bruno         | propriétaire                                                                                                                                                                                                                      |
| collègues     | groupe                                                                                                                                                                                                                            |
| 2155          | taille en octets                                                                                                                                                                                                                  |
| oct. 29 12:51 | date de dernière modification                                                                                                                                                                                                     |
| resultat.txt  | nom du fichier                                                                                                                                                                                                                    |



### `mkdir`
make directory

`mkdir factures devis previsionnel`

paramètre `-p`pour créer une arborescence
`mkdir -p factures/2024/janvier factures/2024/fevrier factures/2024/mars`



### Navigation less :

Une fois que le fichier est ouvert avec "less," naviguer dans le fichier de plusieurs manières :

| ``touches fléchées (haut/bas)`` | défile ligne par ligne                                                                            |
| ------------------------------- | ------------------------------------------------------------------------------------------------- |
| ``barre d'espacement``          | défile page par page                                                                              |
| ``q``                           | quitter                                                                                           |
| ``less``                        | revenir au terminal                                                                               |
| ``/texte-à-rechercher``         | Recherche less                                                                                    |
| ``n``                           | recherche la prochaine occurrence du mot-clé                                                      |
| ``N``                           | revenir en arrière                                                                                |
| ``man less``                    | pour en savoir plus sur ses fonctionnalités avancées.                                             |
| ``watch [options] commande``    | exécute une commande à intervalles réguliers et affiche la sortie de cette commande à l'écran<br> |
| ``date``                        | affiche la date                                                                                   |
| ``date –help``                  | affiche tous les paramètres possible pour la date                                                 |

 
### Compression tar

Utilisée pour créer des archives dans les systèmes Unix/Linux.  
Peux compresser plusieurs fichiers ou répertoires en un seul fichier 

tar -cvf nom_de_larchive.tar fichiers_ou_repertoires  

| tar -option destination source |                                                                       |
| ------------------------------ | --------------------------------------------------------------------- |
| c                              | Indique que l’on crée une nouvelle archive.                           |
| v                              | Active le mode verbeux, qui affiche les fichiers ajoutés à l'archive. |
| f                              | Spécifie le nom de l'archive.                                         |

wget [options] [url]  
wget  'Url-du-fichier' -O nom-du-fichier-destination.

wget -i répertoire/  'Url-du-fichier' -O nom-du-fichier-destination.

-i spécifie un fichier contenant une liste d’URLs à téléchager  
Télécharger un fichier accessible par un lien dynamique  
mettre l'adresse URL entre simple quote  
préciser le nom du fichier de destination avec l'option -O  
[https://doc.ubuntu-fr.org/wget](https://doc.ubuntu-fr.org/wget)

  
  
  

readarray  
  

readarray [options] tableau < fichier

tableau : Le nom du tableau dans lequel on va stocker les lignes lues.

fichier : Le fichier ou l'entrée standard dont vous souhaitez lire les lignes  
  

options  
t supprime le caractère de nouvelle ligne (\n) à la fin de chaque ligne, ce qui peut être utile pour traiter des fichiers CSV, par exemple.

  
  
  

  
chsh changer de shell  
Ctrl+c Stop a process  
bg To continue with its execution in the background  (stdin, stdout, and stderr are still joined to the terminal.)

& Run a Linux process in the background using the ampersand sign

tail -f /var/log/syslog | grep CRON affiche en temps réel les entrées de journal relatives aux tâches cron

  

jobs View all your background jobs

  

disown used after the process has been executed and put in the background, its work is to remove a shell job from the shell’s active list jobs, therefore you will not use fg, bg commands on that particular job anymore.

  
Therefore, to completely detach a process from a controlling terminal, use the command format below, this is more effective for graphical user interface (GUI) applications such as Firefox:   $ firefox </dev/null &>/dev/null &**


head fichier
tail fichier
less fichier

Démarrer python
`python` ou `python3`

## Processus
A chaque commande, le système crée un **processus**
**PID**: Process Identifier
**PPID**: Parent Process Identifier
L'ancêtre de tous les processus est le démarrage du système : ``init``  PID 1

``ps``               liste des processus   ( **SANS TIRET SUR MAC** )
``ps -u bob``  lancés par l'utilisateur bob
``ps -a``         de tous les utilisateurs lancés dans un terminal
``ps -x``         y compris ceux lancés hors terminal
``ps -u``         affiche des info (CPU, mémoire, état, date...)
``pstree``       arbre des processus (**sur linux**)
 
``top``             affiche les processus les plus gourmands en ressource CPU
``q ``               pour quitter

### contexte d'exécution :
- PID et PPID
- TTY le terminal qui l'a lancé
- code du programme à exécuter
- répertoire courant
- date du lancement
- temps de calcul cumulé
- mémoire nécessaire
- état du processus...

Le terminal est un processus (une fenêtre) qui lance le processus de l'interpréteur de ligne de commande. Une commande est  alors un processus fils de l'interpréteur, etc...
``exit`` ou ``CTRL+D`` ferme le shell courant.

Quand un processus se termine, il renvoi son code de retour au parent.
Le PID est libéré.
Ses fils sont rattachés à ``init`` ( PID 1 )
Si le parent est défaillant, le PID mort reste occupé (zombie) jusqu'à la fin du parent.

### Tâche

Une tâche correspond à un processus ou à un ensemble de processus en pipeline par exemple :
ps | less

| ``jobs``                                  | affiche la liste de tâches                                                                                                                   |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| ``jobs -l``                               | affiche la liste de tâches avec leur numéro de processus                                                                                     |
| ``fg %1``                                 | lance la tâche 1 en premier plan                                                                                                             |
| ``bg %1``                                 | lance la tâche 1 en arrière plan, ( idem pour ``nom_de_commande &`` )                                                                        |
| ``echo ./minuit.sh \| at 2359 24-12-31 `` | programme le script pour 23h59                                                                                           le 31 décembre 2024 |
| ``atq ``                                  | liste des tâches programmées                                                                                                                 |
| ``atq -c 3``                              | tâche programmée numéro 3                                                                                                                    |
| ``atrm 3``                                | suprime la tâche programmées numéro 3                                                                                                        |
### Etats possible d'un processus :
**R**   *running/runnable*    en exécution ou en attente d'exécution
**S**   *sleeping*                    attend un signal d'un autre processus pour se reveiller
**T**   *stopped*                    suspendu provisoirement, attend un signal de reveil
**Z**  *zombie*                      est mort mais son parent n'a pas reçu le code retour

### Signaux
les processus et l'utilisateur peuvent envoyer des signaux
``kill -le_nom_du_signal  PID_destinataire``

SIGTERM   terminaison propre (par défaut)
SIGINT       terminaison propre         CTRL+C
SIGHUP      fermeture du signal ou mort du parent : Hang up
SIGKILL       terminaison brutale, en dernier recours : perte de donné non enregistrée
SIGSTOP     suspension temporaire
SIGTSTP      suspension temporaire   CTRL+Z
SIGCONT    reprise d'activité

| ``killall bidule``               | Termine tous les processus exécutant la commande 'bidule'                                                                               |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| ``trap``                         | interception de signaux                                                                                                                 |
| ``nohup gros_calcul.sh &``  <br> | le script se poursuit après la fermeture du terminal                                                                                    |
| ``&``                            | lance en arrière plan<br>les sorties textuelles seront dans un fichier 'nohup.out'                                                      |
| SIGHUP                           | envoyé à tous les processus enfants, certain termineront,                                                    d'autres l'intercepterons. |
|                                  |                                                                                                                                         |
|                                  |                                                                                                                                         |

### Stopper un processus :

##### Ctrl+C  :  Interromps et arrête le processus en cours. SIGINT
- **Explication :** Lorsqu'on appuie sur `Ctrl+C`, le terminal envoie un signal SIGINT (interrupt) au processus en cours d'exécution. Cela interrompt immédiatement le processus et le termine.
- **Usage :** Très utile pour arrêter un programme qui tourne indéfiniment ou pour interrompre un script ou une commande qui ne répond pas comme prévu. C'est une méthode courante pour quitter rapidement un programme qui ne dispose pas d'un moyen propre pour être arrêté.
##### Ctrl+Z  :  Suspend le processus en cours, pouvant être repris plus tard. SIGTSTP.
- **Explication :** Lorsqu'on appuie sur `Ctrl+Z`, le terminal envoie un signal SIGTSTP au processus en cours d'exécution. Cela suspend temporairement le processus, le plaçant en arrière-plan dans un état "stoppé" mais toujours en mémoire.
- **Usage :** Très utile si vous voulez interrompre temporairement un programme interactif pour effectuer d'autres tâches dans le terminal, puis reprendre le programme plus tard avec la commande `fg` (foreground) ou `bg` (background).
##### Ctrl+D :  Signale la fin de l'entrée ou terminer une session du termina.
- **Explication :** `Ctrl+D` envoie un signal EOF (End Of File) à un programme de ligne de commande. Si vous êtes dans un shell interactif, cela indique que vous avez terminé votre session et souhaite fermer le shell. Si utilisé au sein d'un programme qui attend une entrée, cela signifie que vous avez terminé de fournir des données.
- **Usage :** Fermer proprement une session terminal ou signaler la fin de l'entrée de données à des programmes comme `cat`, `python` (en mode interactif), etc.
##### exit()    :  Ferme le shell actuel ou termine un script de shell.
- **Explication :** La commande `exit()` est utilisée pour quitter le shell en cours. Elle termine la session du terminal ou de la fenêtre de terminal dans laquelle elle est exécutée. Vous pouvez aussi spécifier un code de sortie (ex: `exit(0)` pour une sortie sans erreur).
- **Usage :** Utilisée pour fermer proprement le terminal ou pour sortir d'un script de shell. Dans certains shells, taper simplement `exit` (sans parenthèses) aura le même effet.


``file nom_du_fichier.extension``  affiche le type du fichier


## Cat et Less

## `awk`

|Tâche|Commande `awk`|Équivalent Python (basique)|
|---|---|---|
|Afficher la ligne entière|`awk '{print $0}' file`|`print(line.strip())`|
|Afficher la 1ère colonne|`awk '{print $1}' file`|`print(line.split()[0])`|
|Afficher colonnes 1 et 3|`awk '{print $1, $3}' file`|`cols = line.split(); print(cols[0], cols[2])`|
|Changer le séparateur de champ|`awk -F, '{print $2}' file.csv`|`line.split(',')[1]`|
|Afficher seulement la 1ère ligne|`awk 'NR==1' file`|`if i == 0: print(line)`|
|Ignorer la 1ère ligne|`awk 'NR>1' file`|`if i > 0: print(line)`|
|Filtrer sur une colonne|`awk '$3 > 100 {print $1,$2}' file`|`cols = line.split(); if int(cols[2]) > 100: print(cols[0], cols[1])`|
|Compter le nombre de colonnes|`awk '{print NF}' file`|`print(len(line.split()))`|
|Somme d’une colonne|`awk '{sum+=$2} END{print sum}' file`|`total = sum(int(line.split()[1]) for line in f)`|
|Moyenne d’une colonne|`awk '{sum+=$2} END{print sum/NR}' file`|`total = sum(int(l.split()[1]) for l in f); print(total/len(f))`|
|Compter occurrences d’une valeur|`awk '{count[$1]++} END{for (i in count) print i, count[i]}' file`|`from collections import Counter; print(Counter(l.split()[0] for l in f))`|
|Exécuter code avant/après lecture|`awk 'BEGIN{print "start"} {print $1} END{print "done"}' file`|`print("start"); ...; print("done")`|

