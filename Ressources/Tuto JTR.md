
#### Installation de JohnTheRipper :
> `sudo snap install john-the-ripper`

.................................................................................................

#### Installation des librairies permettant le hack des mots de passe :
> `sudo apt install ocl-icd-opencl-dev -y`

.................................................................................................

#### Editer un alias pour la commande `zip2john` :
> `sudo snap alias john-the-ripper.zip2john zip2john`

.................................................................................................

#### Créér un fichier `test.txt` ( /!\ Avec du contenu dedans) :
> `touch /home/wilder/test.txt` 

.................................................................................................

#### Créer une archive encryptée avec un mot de passe :
> `zip -e /home/wilder/test.zip /home/wilder/test.txt`

.................................................................................................

#### Permet d'extraire le hash de l'archive dans un fichier texte :
> `zip2john /home/wilder/test.zip > /home/wilder/hash.txt`

.................................................................................................

#### JohnTheRipper va indiquer le mot de passe du fichier `.zip` dans les lignes de commande ci-dessous :
> `john /home/wilder/hash.txt`
