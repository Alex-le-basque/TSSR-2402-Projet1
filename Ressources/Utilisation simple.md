## Utilisation simple

### Pré-requis pour la machine virtuelle

- **Système d'exploitation :** Ubuntu Jammy Jellyfish 22.04.4
- **Mémoire vive :** 4096 Mo
- **Nombre de processeurs :** 2
- **Carte réseau :** Nat et Réseau interne (même plage IP)
- **SSH :** installée et configurée

### Installation de John the Ripper

Pour installer John the Ripper, dans ton terminal utilisez la commande suivante :

`sudo snap install john-the-ripper`

John the Ripper version jumbo installé

![John the Ripper est installé avec le pack jumbo](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Image%20de%20max/John%20the%20ripper%20est%20install%C3%A9%20avec%20le%20pack%20jumbo.png?raw=true)

### Installation des librairies pour le hack de mots de passe

`sudo apt install ocl-icd-opencl-dev -y`

![ocl-icd-opencl-dev installé](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Image%20de%20max/install%C3%A9%20ocl-icd-opencl-dev.png?raw=true)

### Utilisation de zip2john

Pour obtenir le hash d'un fichier zip, vous devez utiliser la commande `zip2john`. Pour vous faciliter la tâche, je vous propose de créer un alias de `zip2john` avec la commande suivante :

`sudo snap alias john-the-ripper.zip2john zip2john`


Testez la commande en entrant `zip2john` dans le terminal. Si l'alias fonctionne, vous devriez obtenir le même résultat que sur l'image ci-dessous :

![Résultat de l'alias zip2john](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/assets/162970946/d1e8286e-45de-4900-9379-8e4c145aff1c)


Pour récupérer le hash du zip, créez un fichier `.txt` que vous nommerez `hash.txt`.

![Création de hash.txt](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/assets/162970946/bea15156-d678-4136-9c30-d1e7296373ae)


### Connexion SSH au serveur

Pour vous connecter au serveur en SSH (Secure Shell), suivez ces étapes :

1. Ouvrez votre gestionnaire de fichiers.
   
![Gestionnaire de fichier](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Image%20de%20max/Gestionnaire%20de%20fichier.png?raw=true)

2. Cliquez sur "Autre emplacement".
   
![Autre emplacement](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Image%20de%20max/Autre%20emplacement.png?raw=true)

3. Entrez dans la barre de connexion `ssh://nom_utilisateur@adresse_serveur`. Exemple : `ssh://Administrator@172.16.10.10`.
   
![connexion à un serveur](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Image%20de%20max/connexion%20%C3%A0%20un%20serveur.png?raw=true)

4. Entrez le mot de passe de la session où vous souhaitez vous connecter.
   
![MDP de la session de connexion ssh](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Image%20de%20max/MDP%20de%20la%20session%20de%20connexion%20ssh.png?raw=true)

Une fois connecté, recherchez le fichier zip dont vous voulez connaître le mot de passe.

![image](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/assets/162970946/246f2f61-0937-4799-9f3b-0daeb4aad55d)


Copiez et collez le fichier zip à l'emplacement souhaité.

![image](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/assets/162970946/47060d03-4ec0-44b6-bb66-71c63eab0962)


Dans votre terminal, utilisez John the Ripper pour récupérer le hash du fichier .zip vers le fichier `hash.txt` :

`zip2john /home/wilder/SECRETDEFENSE.zip > /home/wilder/hash.txt`


![image](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/assets/162970946/b85140f2-c668-406e-b563-a3c684f0da09)


Vérifiez le contenu de votre `hash.txt`.

![Hash du fichier hash.txt](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Image%20de%20max/Hash%20du%20fichier%20hash.txt%20.png?raw=true)

Utilisez John the Ripper pour décrypter le hash du fichier .zip afin de trouver le mot de passe. Voilà, vous avez trouvé le mot de passe du fichier .zip grâce à cette bibliothèque.

![Résultat du fichier hash](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Image%20de%20max/Resultat%20du%20fichier%20hash.png?raw=true)

