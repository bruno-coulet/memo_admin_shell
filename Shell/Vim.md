[[Vi, emac, nano]]

Tutoriel intégré à vim, dans shell : `vimtutor` 
Ouvrir un fichier : `vim nom_du_fichier`

3 modes :
- <font color='orange'>Mode édition</font>
Saisie de texte classique
- <font color='green'>Mode commande</font> 
Les saisies représentent des commandes qui déclenchent une action
On y accède avec la touche `Echap`

- <font color='purple'>Mode ligne de commande</font>
On y accède depuis le mode Commande avec la touche `:`
Ligne en bas de l'écran
Valide avec la touche `entrée`


Format d'une commande de changement :
`opérateur [nombre] déplacement`
- opérateur : ce qu'il faut faire
- nombre : (optionnel) pour répéter le déplacement
- déplacement : déplace le long du texte à opérer


| Touche.s                                         | Mode édition                                                    | Mode commande                                                                 |                                               |
| ------------------------------------------------ | --------------------------------------------------------------- | ----------------------------------------------------------------------------- | --------------------------------------------- |
| <font color='orange'>i                           | <font color='orange'>-- INSERT -- </font>                       |                                                                               | texte à insérer avant le curseur              |
| <font color='green'>echap<font>                  |                                                                 | <font color='green'>Mode commande</font>                                      |                                               |
| <font color='orange'>shift A</font> (majuscule)  | <font color='orange'> -- INSERT -- </font>                      |                                                                               | texte à ajouter en fin de ligne               |
| h, j, k, l                                       |                                                                 | Gauche / bas / haut / droite                                                  | déplacement                                   |
| 2 j                                              |                                                                 | Déplace de 2 lignes vers le bas                                               | etc...                                        |
| <font color='purple'>: <entrée></font>           | éxécuter une commande                                           |                                                                               |                                               |
| <font color='purple'>: q <entrée></font>         | quitter                                                         |                                                                               |                                               |
| <font color='purple'>: w q <entrée></font>       | enregistrer et quitter                                          |                                                                               |                                               |
| <font color='purple'>: q !  <entrée></font>      | quitte SANS enregistrer                                         |                                                                               |                                               |
| x                                                |                                                                 | supprime le cartactère                                                        |                                               |
| w                                                |                                                                 | déplace au prochain mot                                                       | déplacement                                   |
| 2 w                                              |                                                                 | 2 mots                                                                        | déplacement                                   |
| 3 w                                              |                                                                 | 3 mots etc....                                                                | déplacement                                   |
| e                                                |                                                                 | à la fin du mot                                                               | déplacement                                   |
| 3e                                               |                                                                 | à la fin du 3ème mot                                                          | déplacement                                   |
| 0                                                |                                                                 | au début de la ligne                                                          | déplacement                                   |
| delete 0                                         |                                                                 | Efface tout ce qu'il y a sur la ligne avant le curseur                        |                                               |
| $                                                |                                                                 | fin de la ligne                                                               | déplacement                                   |
| delete $                                         |                                                                 | Efface tout ce qu'il y a sur la ligne après le curseur                        |                                               |
| d                                                |                                                                 | opérateur d'effacement                                                        |                                               |
| e, w, $                                          |                                                                 |                                                                               | déplacement                                   |
| dw                                               |                                                                 | efface 1 mot & 1 espace                                                       | va au prochain mot                            |
| d2w                                              |                                                                 | efface 2 mots                                                                 |                                               |
| de                                               |                                                                 | efface 1 mot                                                                  | n'efface pas l'espace                         |
| d$                                               |                                                                 | efface jusqu'à la fin de la ligne                                             |                                               |
| dd                                               |                                                                 | efface la ligne                                                               |                                               |
| 2 dd                                             |                                                                 | efface 2 lignes                                                               |                                               |
| u                                                |                                                                 | Annule la dernière commande                                                   |                                               |
| U                                                |                                                                 | Annule tous les changments sur une ligne                                      |                                               |
| ctrl r                                           |                                                                 | Annule l'annulation                                                           | Refait la dernière commande                   |
| p                                                |                                                                 | Colle  après le curseur                                                       | (ce qu'on vient d'effacer )                   |
| P (majuscule)                                    |                                                                 | Colle avant le curseur                                                        |                                               |
| r +  caractère                                   |                                                                 | remplace le caractère                                                         | Mettre le curseur sur le caractère à rempacer |
| ce                                               | Passe en Mode édition<font color='orange'> -- INSERT -- </font> | efface le reste du mot<br>passe en <font color='orange'>mode insertion</font> |                                               |
| U (majuscule)                                    | Récupérer toute une ligne                                       |                                                                               |                                               |
| G (majuscule)                                    | Déplace à la fin du fichier                                     |                                                                               |                                               |
| gg                                               | Déplace au début du fichier                                     |                                                                               |                                               |
| <font color='purple'>: numéro de la ligne</font> | Déplace à la ligne voulue                                       |                                                                               |                                               |
| N                                                | Déplace au résultat précédent                                   |                                                                               |                                               |
| n                                                | Déplace au résultat suivant                                     |                                                                               |                                               |

