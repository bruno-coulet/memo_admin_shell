la sécurité de l'échange entre vous et votre serveur sur deux aspects principaux :

1. l'échange provient bien de votre serveur,
2. vous êtes bien le seul à pouvoir lire les informations transmises.

| **Cryptologie**   | C'est la science du secret dans la transmission de l'information.                                                                             |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Cryptographie** | C'est une discipline de la cryptologie assurant notamment la confidentialité, l'authenticité et l'intégrité du message dans une transmission. |
| **Chiffrer**      | On **chiffre** un message afin de s'assurer qu'il est secret.                                                                                 |
| **Déchiffrer**    | On **déchiffre** un message afin de récupérer les données d'origine, lisibles et compréhensibles.                                             |
| **Crypter**       | On **crypte** lorsqu'on veut altérer un message dans l’objectif qu’il ne soit plus lisible, à jamais.                                         |
| **Décrypter**     | On essaie cependant de **décrypter** un message chiffré lorsqu'on ne connaît pas la clé de déchiffrement.                                     |
### cryptographie symétrique
“à clé secrète"

Le même algorithme, la même clé va servir à chiffrer et déchiffrer le message.
simple, efficace et très performant.

L'inconvénient de cette méthode réside dans la criticité de cette clé unique, qui doit être très protégée et transmise de façon sûre

**Algorithmes de chiffrement symétrique :
- **DES** (Data Encryption Standard) d'IBM,
- **AES** (Advanced Encryption Standard), probablement le plus courant aujourd'hui.
- **ChaCha20**

### cryptographie asymétrique

**Deux clés** :

1. Clé **publique**
   sert à chiffrer le message
   peut être diffusée, elle ne sert qu'à chiffrer
   
1. Clé **privée**
   sert à déchiffrer le message
   est conservée précieusement
   sans nécessité de la diffuser

**brèche secrète** :
La clé privée génère la clé publique
 la clé privée laisse une brèche secrète dans la clé publique
( élément permettant de déchiffrer le message )

Algorithmes de cryptographie asymétrique :
- **RSA** 
- **DSA**

- environ 1 000 fois plus lents que DES
- processus très sécurisé
- permet d'identifier de manière sûre la provenance du message en inversant la transmission.
  ( un message chiffré à l'aide de la clé privée présente une **empreinte** (condensat ou  hash) identique à celle du même message chiffré avec la clé publique )
  - beaucoup plus gourmande en ressources de calcul que la cryptographie symétrique.



### SSH

le protocole SSH se définit par l'utilisation des deux procédés de cryptographie :

1. asymétrique pour mettre en place un échange sécurisé avec le client,
2. et symétrique pour gérer les données.

Principe de fonctionnement SSH :

1. Le serveur écoute les demandes de connexions entrantes 
2. Un client demande une connexion, le serveur lui répond les algorithmes de chiffrement à sa disposition 
3. Le client valide un algorithme et le serveur fournit au client sa clé publique 
4. À partir de ce moment-là, le client peut vérifier que tous les messages qu'il va recevoir proviennent bien du serveur 
5. Le client et le serveur échangent grâce à la cryptographie asymétrique pour s'accorder sur une clé de chiffrement symétrique basée sur un très grand nombre premier, on l'appelle la **clé de session SSH** 
6. Une fois cette clé partagée, le client et le serveur peuvent l'utiliser pour tout le reste de la session.
### OpenSSH
brique logiciel basée sur le protocole SSH.
Cette brique logicielle fournit notamment les éléments suivants :

- **`sshd`**: le service SSH ;
    
- **`ssh`**: le client SSH ;
    
- **`ssh-keygen`** et **`ssh-copy-id`**: les utilitaires de gestion de clé RSA, DSA ;
    
- **`scp`** et **`sftp`**: les clients permettant le transfert de données via SSH



Le code source du service SSH est diffusé sous licence BSD et est porté pour les principales distributions Linux.

Ainsi, il est possible de trouver un **package  `openssh-server`** pour les distributions Debian, RedHat et leurs dérivées respectives. Néanmoins, il est également possible de trouver [les sources du serveur](https://www.openssh.com/portable.html).

Le service SSH est un logiciel installé par défaut avec toutes les distributions. Même lorsqu'il s'agit d'une version minimale de la distribution, vous aurez la possibilité de l'installer dès le départ.

la brique logicielle OpenSSH est disponible pour tous les Unix/Linux, si vous souhaitez utiliser un client SSH sur Windows, il est nécessaire d'installer **PuTTY** par exemple, qui permet d'obtenir avec le même logiciel un client SSH ainsi qu'un émulateur de terminal.
### Conneciotn SSH à distance

Par défaut SSH utilise le port 22

`ssh nom_utilisateur@adress_IP`
ou
`ssh nom_utilisateur@nom_serveur`

### résumé
- Pour sécuriser un message, il faut le chiffrer 
    
- La cryptographie permet de chiffrer et déchiffrer un message 
    
- SSH repose sur les principes de cryptographie symétrique et asymétrique 
    
- Sous Linux, les briques logicielles OpenSSH permettent de mettre en place un service SSH sécurisé 
    
- Il est nécessaire de sécuriser le service SSH, notamment en passant par une authentification par échange de clés