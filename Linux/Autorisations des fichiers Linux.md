
Les autorisations déterminent qui peut intervenir sur sur un fichier ou un répertoire 
### syntaxe

Le premier caractère indique le type de fichier :
- `-` : fichier régulier
- `d` : répertoire
- `l` : lien symbolique

 Il y a 3 caractères (3 bits ) pour `execute`, `write`, `read`,  et `aucune` :
- **Exécution** : `x` permet d'exécuter un fichier comme un programme ou de parcourir un répertoire.
- **Écriture** : `w` permet de modifier ou supprimer le contenu du fichier ou du répertoire.
- **Lecture** : `r` permet de lire le contenu d'un fichier ou d'un répertoire.
- ne rien faire     `-`

Elles se décompose en 3 parties pour 3 entités :
- u = compte propriétaire de l'objet/ User
- g = groupe propriétaire de l'objet / Group
- o = tous les autres comptes utilisateurs et/ou système / Other

Exemples : 

`user` peut lire et écrire
`group`peut lire
`other` peut lire 
`-rw-r--r--`

`user` peut lire et écrire
`group`peut lire
`other` peut écrire 
`-rw-r---w-`

### Notation octale

Les droits sont exprimés en puissance de 2 avec les valeurs **0, 1, 2 et 4** offrant une combinaison unique, par exemple 755

| Permissions | Notation symbolique (binaire) | Notation octale |                                     |
| ----------- | ----------------------------- | --------------- | ----------------------------------- |
| lecture     | ``r``  read                   | 4               | 1 bit à la position 2<br>2 exp2 = 4 |
| écriture    | ``w`` write                   | 2               | 1 bit à la position 1<br>2 exp1 = 2 |
| exécution   | ``x`` execute                 | 1               | 1 bit à la position 0<br>2 exp0 = 1 |
| aucune      | `-` no permission             | 0               |                                     |

**notation octale**
Les valeurs allant de 0 à 7 exprimant les 3 bits des permissions sont dites **octales** (8 caractères différents pour les exprimer).
Faire la somme des valeur de `r`, `w` , et `x`  dans chaque groupe de permissions :

| Permissions                    | Valeur<br>Alphanumérique | combinaisons<br>des 3 bits |       | Valeur<br>octale |
| ------------------------------ | ------------------------ | -------------------------- | ----- | ---------------- |
| aucun droit                    | ---                      | 000                        | 0+0+0 | 0                |
| exécution seulement            | --x                      | 001                        | 0+0+1 | 1                |
| écriture seulement             | -w-                      | 010                        | 0+2+0 | 2                |
| écriture et execution          | -wx                      | 011                        | 0+2+1 | 3                |
| lecture seulement              | r--                      | 100                        | 4+0+0 | 4                |
| lecture et exécution           | r-x                      | 101                        | 4+0+1 | 5                |
| lecture et écriture            | rw-                      | 110                        | 4+2+0 | 6                |
| lecture, écriture et exécution | rwx                      | 111                        | 4+2+1 | 7                |

| Permissions   |     |     | user  | group | other |
| ------------- | --- | --- | ----- | ----- | ----- |
| Read          | 4   |     | 4     | 4     | 4     |
| Write         | 2   |     | 2     | -     | -     |
| Execute       | 1   |     | 1     | 1     | 1     |
|               |     |     | 4+2+1 | 4+0+1 | 4+0+1 |
| Valeur Octale |     | =   | 7     | 5     | 5     |

### Exemple de conversion: 
rwxr-xr-x      en binaire
755               en notation octal 

1. Propriétaire.  **rwx**:      4 + 2 + 1 = 7
    - `r` (read) : 4
    - `w` (write) : 2
    - `x` (execute) : 1

2. Groupe.  **r-x**  :                4 + 0 + 1 = 5
    - `r` (read) : 4
    - `-` (no write) : 0
    - `x` (execute) : 1
 
3. Autres.   **r-x**  :                4 + 0 + 1 = 5
    - `r` (read) : 4
    - `-` (no write) : 0
    - `x` (execute) : 1
  

### 𝗣𝗲𝗿𝗺𝗶𝘀𝘀𝗶𝗼𝗻𝘀 typiques

- **𝟳𝟱𝟱** : Droits numériques par défaut lors de la création d'un répertoire ou d'un fichier exécutable.
  Utilisateur : peut lire, écrire, et exécuter.
  Groupe et Autres : peuvent lire et exécuter.

- **𝟲𝟰𝟰** : Permissions typiques pour les fichiers réguliers.
  Utilisateur : peut lire et écrire.
  Groupe et Autres : peuvent lire uniquement.


- **𝟳𝟳𝟳** : Permissions complètes pour un répertoire ou un fichier.
  Tous les utilisateurs : peuvent lire, écrire, et exécuter.
  
  **Remarque** : Ce n'est pas sécurisé, car tout le monde a un accès complet, donc à éviter pour des fichiers ou répertoires sensibles.


- **𝟲𝟲𝟲** : Permissions complètes pour les fichiers, mais sans exécution.
  Tous les utilisateurs : peuvent lire et écrire, mais pas exécuter.
  
  **Remarque** : Pas sécurisé pour des fichiers sensibles, car tout le monde peut modifier le fichier.



  


### `chmod` /  `chgrp`

- Les commandes **`chown/chgrp`**("change owner"/"change group") permettent de changer le propriétaire et le groupe propriétaire d'un objet

La commande`chmod` modifie les autorisations associées à un fichier ou un répertoire

1er argument l'utilisateur :
`u`pour `user`
`g`pour `group`
`o`pour `other`

2ème argument les permissions
`r`
`w`
`x`

`chmod u+rw nom_du_fichier` droit de lecture, écriture pour l'utilisateur 
`chmod u+x nom_du_fichier` ajout du droit d'execution pour l'utilisateur 


On peut le faire en base 2 :

`chmod 666 nom_du_fichier` droits de lecture et écriture (4+2) pour tout le monde

Le droit Lecture pour tous positionné sur le fichier ne suffit pas, il faut également le droit Exécution sur le répertoire qui le contient. On dit que le bit x positionné sur le répertoire donne le droit de “**traverser**” le répertoire.
[Droits d'accès sous Linux : gérer les accès aux fichiers](https://doc.ubuntu-fr.org/droits)

## Les droits spéciaux

- **`SetUID`** est un droit spécial permettant d'exécuter un fichier avec les droits de son propriétaire 
    
- **`Sticky Bit`** est un droit spécial permettant de gérer des espaces partagés

En plus des permissions des fichiers que l'on vient de voir, il existe 3 droits spéciaux :
- SUID
- SGID 
- Sticky Bit

Ces permissions sont également attribuées avec la commande `chmod`.
Elles peuvent aussi être définies en octal : on les place alors devant les permissions vues plus haut. On parle alors du groupe des droits spéciaux.