[[Bash]]  
[[Shell]] 
[[Ligne de commande]]  
[[Bash]]  
[[Autorisations des fichiers Linux]]

## Extension
Le fichier avec l'extension `.sh` peut être un simple `.txt` à la base, puis on l'enregistre en `.sh` pour en faire un script.

## Ajouter des lignes de commandes
- Ajouter des boucles ou des conditions si besoin.
- Donner des droits d'exécution (permission mode administrateur).

## execution du script
```shell
source nom_du_script
``` 
exécute des scripts dans le contexte du shell actuel plutôt que dans un sous-shell.
Charge les commandes et les variables définies dans le script directement dans l'environnement de l'utilisateur.

```shell
# première possibilité
./nom-du-fichier
# permet d’exécuter le fichier même sans permission `chmod +x`
sh nom-du-fichier
# autre possibilité
bash nom-du-fichier
```


##  Paramètres

Arguments donnés avec le titre du fichier
```shell
./Monfichier.sh param1 param2 param3
```
chaine de caractère :
Utiliser des  guillemets s’il y a un espace dans le nom du paramètre 

- `$1`: variable (pas de chiffre dans le nom de la variable).
- `$1` permet de récupérer le paramètre 1, `$2` permet de récupérer le paramètre 2.
- `$1` jusqu'à `$` infini, ce sont des variables réservées par bash pour les paramètres.



## Variables

- un nom
- une valeur qui peut changer
- une memoire temporaire

On crée une variable : pas de dollar
On utilise la variable : Il faut un dollar

$1 variable (pas de chiffre dans le nom de la variable)

$1 permet de récupérer le parametre 1

$2 permet de récupérer le parametre 2

$1 jusqu’a $ infini, c’est des variable réservés par 
bash pour les paramètres.

## condition
```bash
if elseif else
if [ $1 = “test” ]
then
echo “mon paramètre 1 est test”
elif $1
```
- `if`, `elseif`, `else`.
```bash
if [ $1 = "test" ]; then
    echo "mon paramètre 1 est test"
elif $1; then
    # Votre condition ici
if
```


## Boucles
Il y a les boucles `For` et les boucles `While`.
- Boucle `for` :
```bash
for i in {1..5}; do
    echo "$i"
done
```
- Boucle `while` :
Avec les boucles `while`, il faut vérifier qu'il y a bien une condition pour en sortir. Sinon ça risque d'être une boucle infinie.
```bash
i=0
while ((i<5)); do
    echo $i
    ((i++))
done
```
### Incrémentation :
```bash
i++
i+=1
((i=i+1))
```
Ce sont trois manières de faire la même chose.
On peut incrémenter, décrémenter avec `i--` par exemple, multiplier, diviser, etc...
