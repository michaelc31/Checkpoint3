# Checkpoint3_Exercice2

## Exercice 2 : Manipulations pratiques sur VM Windows :

### Partie 1 : Gestion des utilisateurs :

**Q.2.1.1** 

Sur le serveur, créer un compte pour ton usage personnel. je me connecter en root via SSH de mon pc Hote et je lance la commande adduser mika et je rentre le mot de passe et les information utile

![1](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint.JPG?raw=true)

**Q.2.1.2**

Les préconisations que je proposes concernant ce compte mettre en place un mot de passe complexe, si on veut certain droit faut ajouter se compte au group concerner mais faire attention aux droit obtroyer 

### Partie 2 : Configuration de SSH :

**Q.2.2.1** 

Pour désactiver complètement l'accès à distance de l'utilisateur root, je vais modifier le fichier /etc/ssh/sshd_config en ajoutant la ligne PermitRootLogin no et je redemarre le service ssh avec la commande systemctl restart ssh

![2](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint10.JPG?raw=true)

et je verifie l'acces malheureusement je peut toujours me connecter car la ligne Include /etc/ssh/ssd_config.d/*.conf prend en compte les fichier de conf du dossier pour pas aller modifier tout les fichier conf je commente la ligne par `#` je redemarre le service ssh avec la commande systemctl restart ssh

![3](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint3.JPG?raw=true)

je test de me connecter en ssh avec le compte root acces refuser c'est bon

![4](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint4.JPG?raw=true)

**Q.2.2.2**

Pour autoriser l'accès à distance à ton compte personnel uniquement je vais modifier le ficheier /etc/ssh/sshd_conf avec la commande `nano /etc/ssh/sshd_conf` et ajouter la ligne AllowUsers mika afin de donner 
et lui rajouter l'acces au compte mika crée juste avant et en refusant la connexion avec le compte wilder en ajoutant la ligne DenyUsers wilder et je redemarre le service ssh avec la commande systemctl restart ssh

![5](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint5.JPG?raw=true)

je verifie que wilder n'as plus acces en ssh avec la commande `ssh wilder@IP` acces refuser c'est bon. et l'acces a mon compte personnel

![6](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint6.JPG?raw=true)

**Q.2.2.3**

Mettre en place une authentification par clé valide et désactiver l'authentification par mot de passe ca se passe en 2 etapes :

1ere generer une paire de cle valide grace a la commande ssh-keygen puis l'envoye sur le serveur avec la commande ssh-id-copy 

![7](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint7.JPG?raw=true)

![8](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint8.JPG?raw=true)

2 etape : modifier le fichier /etc/ssh/sshd_conf pour désactiver l'authentification par mot de passe et redemarre le service ssh avec la commande systemctl restart ssh

![9](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint9.JPG?raw=true)

lors de la reconnection en ssh on ne me demande plus le mot de passe c'est bon 

![10](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint10.JPG?raw=true)

### Partie 3 : Analyse du stockage :

**Q.2.3.1**
les systèmes de fichiers actuellement montés sont :

![11](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint11.JPG?raw=true)


**Q.2.3.2**

le type de système de stockage qu'ils utilisent sont :

![12](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint12.JPG?raw=true)

**Q.2.3.3**

j'eteins ma VM, j'ajoute un disque dur de 8Go afin de reparer le raid en place.

![13](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint13.JPG?raw=true)

je vais identifier le nouveau disque avec la commande lsblk, Préparer le disque avec la commande fdisk et je vais ajouter le disque au raid existant 

![14](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint14.JPG?raw=true)

![15](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint15.JPG?raw=true)

**Q.2.3.4**

**Q.2.3.5**

### Partie 4 : Sauvegardes :

**Q.2.4.1**

bareos-dir (Director) Gère la configuration, la planification des sauvegardes, la communication avec les autres composants (bareos-sd et bareos-fd)

bareos-sd (Storage Daemon) Reçoit les données à sauvegarder depuis le Bareaos-fd et les stockes sur les supports de stockage configurés, puis les restaure lorsqu'elles sont nécessaires.

bareos-fd (File Daemon) Il permet a Bareaos-dir de communiquer avec ces machines pour initier les sauvegardes, envoyer les données à sauvegarder vers le Bareos-sd

### Partie 5 : Filtrage et analyse réseau :

**Q.2.5.1**

les règles actuelle appliquées sur Netfilter sont :

![16](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint16.JPG?raw=true)

**Q.2.5.2**

les types de communication accepter sont IP et le TCP 

**Q.2.5.3**

**Q.2.5.4**

### Partie 6 : Analyse de logs :

**Q.2.6.1**

|Date |Heure| IP Machine|
| --- | --- | --------- |
|dec 20| 10:24:10|10.0.0.199|
|jan 03|11:06:30|10.0.0.199|
|jan 03|11:06:45|10.0.0.199|
|jan 03|11::23:03|10.0.0.199|
|jan 03|11:23:34|10.0.0.199|
|jan 03|11:23:40|10.0.0.199|
|jan 03|11:23:44|10.0.0.199|
|jan 03|12:09:28|fd26:ba41:c8d6:0:ba92:6393:cc55:8b8d|
|jan 03|12:09:34|fd26:ba41:c8d6:0:ba92:6393:cc55:8b8d|

![20](https://github.com/michaelc31/Checkpoint3/blob/main/Exo2/checkpoint20.JPG?raw=true)
