Voir aussi [[Vim]]

Il y a 2 éditeurs de texte en mode terminal  des systèmes Unix :
- [VI](#VI) 
- [emac](#emac)
- [nano](#nano) (autre éditeur pus simple d'utilisation)

## VI

[cheatsheet VI](https://www.atmos.albany.edu/daes/atmclasses/atm350/vi_cheat_sheet.pdf)
**vi** est un éditeur de texte en mode terminal pour les systèmes Unix

- `vi nom-du-fichier`  ouvre le fichier avec vi
- Touche `i` pour activer le mode "saisie"
- Touche `echap` pour activer le mode commande


**vi** est installé par défaut avec quasiment toutes les distributions Linux à ce jour, mais vous le retrouvez aussi sur tous les Unix (HP, Solaris, AIX, etc.). Si vous n'avez aucun outil sur votre Unix/Linux, vous avez toujours **vi**


1. le mode **commande**
    
2. et le mode **saisie**.


| **Touche** | **Effet**                                                                                                                                                                  |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| i          | Insertion de texte à partir du curseur.                                                                                                                                    |
| a          | Insertion de texte après le curseur.                                                                                                                                       |
| x          | Suppression du caractère sous le curseur.                                                                                                                                  |
| cw         | Suppression du mot sous le curseur + Insertion.                                                                                                                            |
| dd         | Suppression de la ligne sous le curseur.                                                                                                                                   |
| Ndd        | Suppression de N lignes à partir de celle sous le curseur.                                                                                                                 |
| yy         | Copie de la ligne sous le curseur.                                                                                                                                         |
| Nyy        | Copie de N lignes à partir de celle sous le curseur.                                                                                                                       |
| p          | Colle le buffer sous la position actuelle du curseur.                                                                                                                      |
| /          | Recherche un pattern dans le fichier.                                                                                                                                      |
| :          | Lance une commande vi.<br><br>- :set number affiche les numéros de ligne ;<br>    <br>- :s%/patternA/patternB/g cherche et remplace patternA par patternB dans le fichier. |
| :N         | Déplacement du curseur à la ligne N.                                                                                                                                       |
| G          | Déplacement du curseur en fin de fichier.                                                                                                                                  |
## emac
- [GNU emacs Reference Card](https://studylib.net/doc/8133095/gnu-emacs-reference-card)
- [The woodnotes emacs cheatsheet for writers, not-coders](https://studylib.net/doc/13336392/the-woodnotes-emacs-cheatsheet-for-writers--not-coders)

- [GNU emacs Reference](https://www.gnu.org/graphics/gnuemacsref.png) 
- [Cheat sheets: emacs cider](https://www.cheatography.com/bilus/cheat-sheets/emacs-cider/)
Logiciel écrit en C avec une gestion d'extension en Lisp

modularité et une flexibilité importante, permettant d'ajouter ou de configurer des fonctionnalités à la volée, sans avoir à recompiler le programme. Peut servir d'IDE

pas souvent installé par défaut sur les distributions Linux, le volume de packages nécessaires à son installation n'est pas anodin.


| **Touche**  | **Effet**                                                          |
| ----------- | ------------------------------------------------------------------ |
| **CTRL n**  | (n pour "next") déplace le curseur sur la ligne suivante.          |
| **CTRL p**  | (p pour "previous") déplace le curseur sur la ligne précédente.    |
| **CTRL f**  | (f pour "forward") déplace le curseur sur le caractère suivant.    |
| **CTRL b**  | (b pour "backward") déplace le curseur sur le caractère précédent. |
| **CTRL a**  | Déplace le curseur au début d'une ligne.                           |
| **CTRL e**  | (e pour "end") déplace le curseur à la fin d'une ligne.            |
| **ALT <**   | Déplace le curseur au début du fichier.                            |
| **ALT >**   | Déplace le curseur à la fin du fichier.                            |
| **DEL**     | Supprime le mot avant le curseur.                                  |
| **CTRL d**  | Efface le caractère après le curseur.                              |
| **ALT DEL** | Supprime le mot **avant** le curseur.                              |
| **ALT d**   | Supprime le mot **après** le curseur.                              |
| **CTRL k**  | Coupe le reste de la ligne après le curseur.                       |
| **CTRL y**  | Colle le reste de la ligne ci-après.                               |


## nano

éditeur de texte en mode terminal
mode de fonctionnement similaire à Notepad, ou bloc-notes.

- les fonctionnalités d'édition sont classiques,
    
- pas de distinction entre mode commande et mode saisie,
    
- à l'ouverture de nano, vous êtes prêt à saisir,
    
- et les touches de direction fonctionnent !

Ctrl + O pour enregistrer (sauvegarder) les modifications
Entrée pour confirmer le nom du fichier
Ctrl + X pour quitter Nano

Si vous quittez avec Ctrl + X sans avoir enregistré au préalable, Nano vous demandera si vous voulez enregistrer les modifications avant de quitter. Vous pouvez alors répondre Y (oui) ou N (non).