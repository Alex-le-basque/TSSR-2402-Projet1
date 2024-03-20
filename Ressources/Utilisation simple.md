## Utilisation simple

### Pré-requis pour la machine virtuelle

- **Système d'exploitation :** Ubuntu Jammy Jellyfish 22.04.4
- **Mémoire vive :** 4096 Mo
- **Nombre de processeurs :** 2
- **Carte réseau :** Nat et Réseau interne (même plage IP)
- **SSH :** Configuration installée et configurée

### Installation de John the Ripper

Pour installer John the Ripper, utilisez la commande suivante :

sudo snap install john-the-ripper

![John the Ripper est installé avec le pack jumbo](John-the-ripper-est-installe-avec-le-pack-jumbo.png)

John the Ripper version jumbo installé

![John the Ripper pas installé](John-the-ripper-pas-installe.png)

### Installation des librairies pour le hack de mots de passe

sudo apt install ocl-icd-opencl-dev -y

![ocl-icd-opencl-dev installé](installe-ocl-icd-opencl-dev.png)

### Utilisation de zip2john

Pour obtenir le hash d'un fichier zip, vous devez utiliser la commande `zip2john`. Pour vous faciliter la tâche, je vous propose de créer un alias de `zip2john` avec la commande suivante :

sudo snap alias john-the-ripper.zip2john zip2john


Testez la commande en entrant `zip2john` dans le terminal. Si l'alias fonctionne, vous devriez obtenir le même résultat que sur l'image ci-dessous :

![Résultat de l'alias zip2john](Resultat-de-l-alias-zip2john.png)

Pour récupérer le hash du zip, créez un fichier `.txt` que vous nommerez `hash.txt`.

![Création de hash.txt](Creation-de-hash.txt.png)

### Connexion SSH au serveur

Pour vous connecter au serveur en SSH (Secure Shell), suivez ces étapes :

1. Ouvrez votre gestionnaire de fichiers.
   
   ![Gestionnaire de fichier](Gestionnaire-de-fichier.png)

2. Cliquez sur "Autre emplacement".
   
   ![Autre emplacement](Autre-emplacement.png)

3. Entrez dans la barre de connexion `ssh://nom_utilisateur@adresse_serveur`. Exemple : `ssh://Administrator@172.16.10.10`.
   
   ![connexion à un serveur](connexion-a-un-serveur.png)

4. Entrez le mot de passe de la session où vous souhaitez vous connecter.
   
   ![MDP de la session de connexion ssh](MDP-de-la-session-de-connexion-ssh.png)

Une fois connecté, recherchez le fichier zip dont vous voulez connaître le mot de passe.

![Fichier zip dans mes documents](Fichier-zip-dans-mes-documents.png)

Copiez et collez le fichier zip à l'emplacement souhaité.

![emplacement souhaité](emplacement-souhaite.png)

Dans votre terminal, utilisez John the Ripper pour récupérer le hash du fichier .zip vers le fichier `hash.txt` :

zip2john /home/wilder/SECRETDEFENSE.zip > /home/wilder/hash.txt


![Permet d'extraire le hash de l'archive dans un fichier texte](Permet-dextraire-le-hash-de-larchive-dans-un-fichier-texte.png)

Vérifiez le contenu de votre `hash.txt`.

![Hash du fichier hash.txt](Hash-du-fichier-hash.txt.png)

Utilisez John the Ripper pour décrypter le hash du fichier .zip afin de trouver le mot de passe. Voilà, vous avez trouvé le mot de passe du fichier .zip grâce à cette bibliothèque.

![Résultat du fichier hash](Resultat-du-fichier-hash.png)

