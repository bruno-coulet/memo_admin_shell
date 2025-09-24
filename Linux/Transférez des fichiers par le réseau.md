les deux logiciels les plus utilisés pour télécharger des fichiers en HTTP sur le réseau depuis un terminal : **`wget`** et `curl`

## wget
**`wget`** est [un projet GNU](https://www.gnu.org/software/wget/). Ce petit logiciel permet de télécharger des fichiers en utilisant les protocoles Internet communs, comme HTTP, ou FTP.


## curl
`curl` s'appuie sur [les librairies partagées libcurl, et diffusé sous licence MIT](https://curl.se/)
il ne propose pas de téléchargement récursif
liste des protocoles compatibles : DICT, FILE, FTP, FTPS, Gopher, HTTP, HTTPS, IMAP, IMAPS, LDAP, LDAPS, POP3, POP3S, RTMP, RTSP, SCP, SFTP, SMB, SMBS, SMTP, SMTPS, telnet and TFTP.

Pour plus d'informations, vous pouvez vous rendre sur [le site de référence](https://curl.haxx.se/).


## scp
`scp`  fourni une fonctionnalité de transfert de fichier sécurisée en s'appuyant sur le protocole SSH. 

Pour cela, **`scp`** va tout simplement utiliser le client **ssh**. La seule condition de son utilisation étant bien entendu de posséder un compte de connexion et un service SSH en écoute.


## Transfer de fichiers par FTP/FTPS/SFTP

#### **FTP**
Ce protocole tend à disparaître, car par défaut les flux transitant sur le réseau pendant les échanges ne sont pas chiffrés. 

#### FTPS
Il est nécessaire de coupler le serveur FTP avec un certificat **TLS/SSL,** pour obtenir un service **FTPS**. 

#### SFTP
Sur un serveur disposant d'un accès SSH, il est possible de faire du “**FTP par SSH**”, aussi nommé **SFTP**.

Le principe est simple :

- Définition d'un nouveau protocole de communication s'appuyant sur SSH spécialisé dans la gestion des fichiers,
    
- Utilisation d'un programme comme client SFTP.
    

Alors, idem que pour **`scp`**, SFTP reposant sur SSH va utiliser les principes de cryptographie asymétrique. Il suffit d'utiliser un logiciel compatible pour bénéficier de ses fonctionnalités.

Par exemple, **FileZilla** est, à l'origine, un logiciel client pour FTP très connu, gratuit et proposé sous licence GNU, compatible avec SFTP.