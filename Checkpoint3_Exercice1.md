# Checkpoint3_Exercice1

## Exercice 1 : Manipulations pratiques sur VM Windows :

### Partie 1 : Gestion des utilisateurs :

**Q.1.1.1 :**

Pour créé mon utilisateur `Lionel Lemarchand` je vais dans l'AD user and computer. je clique sur `Action/Find` je recherche `Kelly Rhameur` afin d'afficher ses attributs. 

![1](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint.JPG?raw=true)

Ceci fait je sais que `Kelly Rhameur` je situe dans `l'OU LabUsers , DirectionDesRessourcesHumaines`. je me place dans cet OU est je créé mon nouvel Utilisateur en prenant compte des attribut de Kelly pour les affecter a Lionel.  

![2](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint2.JPG?raw=true)

![3](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint3.JPG?raw=true)

**Q.1.1.2 :**

Pour la création de `l'ou DeactivatedUsers` je fait un clique droit sur l'OU LabUsers et je fait `new/Organizational Unit`
je nomme mon `OU DeactivatedUsers` et je valide

![4](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint4.JPG?raw=true)

je clique droit sur l'utilisateur `Kelly.Rhameur` et je le desactive et je le deplace dans `l'OU DeactivatedUsers` que je vien de cree

![5](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint5.JPG?raw=true)


**Q.1.1.3 :**

Connaissant les attributs de `Kelly` je sais qu'elle est dans le group `GrpUsersDirectionDesRessourcesHumaines` du coup je vais dans se groupe et je le modifie afin de verifier que notre nouvel utilisateur est bien dedans et que `Kelly` n'y est plus

![6](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint6.JPG?raw=true)


**Q.1.1.4 :** 

je cherche l'emplacement des dossier personnel qui se trouve dans `DossiersIndividuels F:` et je modifie le dossier de Kelly afin qu'il passe en -ARCHIVE et je créé le dossier personnel de Lionel nommé `Lionel.Lemarchand`

![7](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint7.JPG?raw=true)



### Partie 2 : Restriction utilisateurs :

**Q.1.2.1 :**

Pour faire en sorte que l'utilisateur `Gabriel Ghul` ne puisse se connecter que du `lundi au vendredi, de 7h à 17h`. je vais faire ca en 2 étapes: 

`1ere étape :` recherche L'utilisateur Gabriel Ghul et modifier le LogonHour pour qu'il ne puisse se connecter que du lundi au vendredi, de 7h à 17h

![8](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint8.JPG?raw=true)

`2eme étape :` aller créé une GPO pour restrindre l'utilisation qu'aux heures permissent je vais dans `Group Policy Management` et je créé ma GPO nommé `Computer_Restriction` car la GPO s'applique sur un Ordinateur mais agit sur le client grace a la plage horaire indiquer en amont

![9](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint9.JPG?raw=true)

![10](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint10.JPG?raw=true)

![12](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint12.JPG?raw=true)

la gpo créé pour l'appliquer faut la Link a l'OU LabComputer et c'est bon.

![11](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint11.JPG?raw=true)

**Q.1.2.2 :**

Pour bloquer sa connexion au seul ordinateur `CLIENT01`. dans le Security filtering je rajoute le computer CLIENT1

![13](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint13.JPG?raw=true)

**Q.1.2.3 :**

Pour mettre en place une stratégie de mot de passe pour durcir les comptes des utilisateurs de `l'OU LabUsers` je me dirige vers `Active Directory Administrative Center` et je vais dans `TSSR(local)/System/Password Settings Contener`

![14](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint14.JPG?raw=true)

je fait New et je met en place ma strategie de mot de Passe

![15](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint15.JPG?raw=true)


### Partie 3 : Lecteurs réseaux :

**Q.1.3.1 :**

Créer une GPO Drive-Mount qui monte les lecteurs E: et F: sur les clients, je vais dans Group Policy Management et je créé ma GPO nommé User_MapDrive, je regle le status GPO sur `Computer configuration settings disabled` et je l'edit pour mapper les dossier 

![16](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint16.JPG?raw=true)

![17](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint17.JPG?raw=true)

et je link la GPO sur l'OU LabUser car elle doit agir sur tout les utilisateurs.

![18](https://github.com/michaelc31/Checkpoint3/blob/main/Exo1/Checkpoint18.JPG?raw=true)
