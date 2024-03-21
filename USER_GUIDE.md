<div align="center"><h1>Sécurisation de mot de passe</h1></div>
<div align="center"><h1>Guide de l'utilisateur</h1></div>

<details>

<summary><strong><font size="+2">Sommaire</font></strong></summary>

<br>

-  <b><i>JohnTheRipper ou Hashcat ?</i></b>
-  <b><i>Caractéristiques de JohnTheRipper et Hashcat</i></b>
-  <b><i>Utilisation simple</i></b>
-  <b><i>Utilisation avancée</i></b>
-  <b><i>FAQ</i></b>

</details>

<HR>

<details>

<summary><strong><font size="+1">JohnTheRipper ou Hashcat ?</font></strong></summary>

<br>

- [JohnTheRipper](https://github.com/openwall/john) est un outil de "cracking" de mots de passe, prenant en charge de nombreux algorithmes de "hash".
La version "-jumbo" est une amélioration de cet outil, et permet, entre autres, de récupérer le "hash" des fichiers `.zip`

<br>

- [Hashcat](https://github.com/hashcat/hashcat), quand à lui, se définit comme l'utilitaire de récupération de mots de passe "*le plus rapide et le plus avancé du monde*". 
Cependant, contrairement à [JohnTheRipper](https://github.com/openwall/john), il ne posséde pas la fonctionnalité lui permettant de récupérer le "hash" des fichiers `.zip`

<br>

### ***Dans le cadre de notre projet, et des pour des raisons pratiques, nous utiliserons uniquement l'outil [JohnTheRipper](https://github.com/openwall/john) (Version -jumbo).***

<br>

</details>

<details>

<summary><strong><font size="+1">Caractéristiques de JohnTheRipper et Hashcat</font></strong></summary>

<br>

## [**JohnTheRipper**](https://github.com/openwall/john) 

- #### Modes de fonctionnement :

   - **Mode "simple"** : L'outil effectue quelques modifications sur le nom d'utilisateur afin de trouver le mot passe (Par exemple, si l'utilisateur s'appelle `toto`, l'outil essaierait les mots de passe "`ToTo`", "`toto123`", "`ToTo123`', etc ...).
  Ce mode étant le plus rapide à effectuer, le mot de passe qui serait trouvé avec cette méthode serait un mauvais mot de passe.

   - **Mode incrémental** (*Ou attaque "brute force"*): Dans ce mode, l'outil va essayer toutes les combinaisons de caractères possibles jusqu'à trouver le bon mot de passe. Cette technique est techniquement infaillible, bien que la robustesse du mot de passe influe grandement sur le temps de calcul nécessaire à le trouver. 
  Afin d'augmenter la pertincence de l'algorithme, l'outil va implémenter la recherche des caractères par fréquence d'utilisation, pour rechercher en priorité les caractères les plus utilisés statistiquement.

   - **Attaque par dictionnaire** : L'outil essaiera un à un tous les mots contenus dans une liste préalablement chargée (Par défault, la liste `password.lst` fournie contiens plus de 3000 mots), en leur appliquant les mêmes modifications que dans le mode "simple".

<br>

- #### Avantages :
   - [JohnTheRipper](https://github.com/openwall/john) est un outil puissant et polyvalent pour la récupération de mots de passe et l'audit de sécurité informatique.
  Bien qu'il soit principalement utilisé par des professionnels de la sécurité informatique, il peut également être utile pour les utilisateurs individuels qui cherchent à renforcer la sécurité de leurs mots de passe

<br>
<br>

## [Hashcat](https://github.com/hashcat/hashcat)

- #### Modes de fonctionnement :

  - **Attaque par combinateur** : Les mots de passe étant souvent constitués de mots composés, Hashcat va exploiter cette habitude et se servir de la méthode de l'attaque par dictionnaire afin de créer une nouvelle liste, chaque mot sur deux de la liste sera combiné ; L'outil pourra également utiliser les signes de ponctuation et les caractères spéciaux pour créer une liste finale de mots de passe potentiels.

  - **Attaque par masque** : En partant du postulat que beaucoup d'utilisateurs utilisent des mots de passe en adoptant un certain type de séquence (Par exemple, une lettre majuscule suivi de 6 lettres et d'un chiffre à la fin ; "Bananas1"), Haschat va rechercher tous les mots de passe dans ce format. L'attaque par masque exploite donc les habitudes des humains et la façon dont ils conçoivent les mots de passe afin de faciliter l'opération.

<font size="-1">**NB** : [Hashcat](https://github.com/hashcat/hashcat) dispose également des mêmes modes de fonctionnement que [JohnTheRipper](https://github.com/openwall/john).</font> 
<br>
- #### Avantages :
  - Flexibilité : Prise en charge de nombreux formats de "hash".
  - Performance : Considéré comme l'un des outils de "cracking" de mot de passe les plus performants.

</details>

<details>

<summary><strong><font size="+1">Utilisation simple</font></strong></summary>

## "Hack" du mot de passe d'un fichier `.zip` distant

### 1 - Accès aux fichiers de Windows Server depuis Ubuntu

- Se rendre dans `Fichiers`, puis `Autres emplacements`, puis `Connexion à un serveur`, et taper l'adresse suivante :
```bash
ssh://Administrator@172.16.10.10
```

![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/SSH%20Ubuntu/SSH_Ubuntu_4.jpg)

Cliquer sur `Se connecter`

<br>

- Un mot de passe sera demandé, il s'agira de celui du compte `Administrator` de Windows Server (Dans notre cas : `Azerty1*`)
  
![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/SSH%20Ubuntu/SSH_Ubuntu_6.jpg)

<br>

- L'accès aux fichiers situés sur la machine Windows Server sera effectif

![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/SSH%20Ubuntu/SSH_Ubuntu_5.jpg)

<br>

### 2 - Copie du fichier `.zip` sur la machine hôte Ubuntu

- Localiser le fichier `.zip` dans l'arborescence de la machine Windows Server (içi : `Private.zip`)

  ![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20ZIP/Ubuntu_ZIP_1.jpg)

<br>

- Le copier, via un simple glisser-déposer par exemple, dans un dossier de la machine hôte Ubuntu (içi : `Dossier personnel`)

![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20ZIP/Ubuntu_ZIP_2.jpg)

<br>

- Exécuter le Terminal et lancer la commande :
```bash
zip2john <nom_du_fichier.zip> > <nom_du_fichier_hash.txt>
```
![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20ZIP/Ubuntu_ZIP_3.jpg)

<br>

- Le fichier "hash" ayant été crée, et contenant le "hash" du fichier `.zip` précédent, nous allons taper la commande suivante afin de tenter de récupérer le mot de passe :
```bash
john <nom_du_fichier_hash.txt>
```
![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20ZIP/Ubuntu_ZIP_4.jpg)

Le mot de passe du fichier `.zip` est indiqué en clair dans le cas où il serait trouvé (içi : `toto123456`)

<br>

- Nous pouvons extraire le contenu de l'archive via un simple clic droit -> `Extraire` , puis en inscrivant le mot de passe (içi : `toto123456`)

![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20ZIP/Ubuntu_ZIP_5.jpg)

<br>

- Après extraction, un dossier du nom du fichier `.zip` a été créé, avec le contenu de l'archive à l'intérieur

![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20ZIP/Ubuntu_ZIP_6.jpg)

<br>

- Dans notre exemple, le dossier contient un fichier `Info.txt`, que nous pouvons dorénavant ouvrir

![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20ZIP/Ubuntu_ZIP_7.jpg)

</details>

<details>

<summary><strong><font size="+1">Utilisation avancée</font></strong></summary>

## "Hack" de la base "SAM" de Windows Server

- Exectuter le Terminal sur Ubuntu et taper la commande suivante :
```bash
ssh Administrator@172.16.10.10
```
![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20SAM/Ubuntu_SAM_3.jpg)

Un mot de passe sera demandé, il s'agira de celui du compte `Administrator` de Windows Server (içi : `Azerty1*`)

<br>

- Une fois le mot de passe entré et validé, le Terminal sur Ubuntu prendra l'apparence d'un Terminal Windows :

![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20SAM/Ubuntu_SAM_4.jpg)

<br>

- Exécuter les commandes suivantes :
```cmd
reg.exe save hklm\sam C:\sam
reg.exe save hklm\system C:\system
```
![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20SAM/Ubuntu_SAM_5.jpg)

<br>

- Deux fichiers, `sam` et `system`, ont été créés à la racine de `C:\` sur la machine distante Windows Server :

![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20SAM/Ubuntu_SAM_1.jpg)

- Copier ces deux fichiers (via un glisser-déposer par exemple) dans votre dossier personnel de la machine hôte Ubuntu

![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20SAM/Ubuntu_SAM_2.jpg)

<br>

- Installer l'outil `Impacket` via le Terminal Ubuntu :
```bash
sudo apt install python3-impacket
```
![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20SAM/Ubuntu_SAM_6.jpg)

<br>

- Exécuter la commande suivante afin de récupérer le hash des deux fichiers précédemment copiés :
```bash
impacket-secretsdump -system system -sam sam local > <nom_du_fichier_hash.txt>
```
![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20SAM/Ubuntu_SAM_7.jpg)

Un fichier "hash" a été crée (içi : `hashsam.txt`)

<br>

- Ouvrir le fichier "hash" et vérifier qu'il contient des informations sur les comptes distants Windows Server

![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20SAM/Ubuntu_SAM_8.jpg)

<br>

- Exécuter la commande suivante :
```bash
john --format=NT <nom_du_fichier_hash.txt>
```
![](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Ubuntu%20SAM/Ubuntu_SAM_9.jpg)

Dans notre exemple, le mot de passe du compte local `Test` a été trouvé, il s'agit de `toto123456!`


</details>

<details>

<summary><strong><font size="+1">FAQ</font></strong></summary>

<br>

 - ***Q : Qu'est ce que le "hash"*** ?

   *R : La fonction de hachage (En anglais : [hash](https://fr.wikipedia.org/wiki/Fonction_de_hachage)) est une fonction cryptographique formée d'une unique châine de caractères destinée à coder des données (Par exemple : des mots de passe), servant ainsi à garantir l'authenticité de ces dernières.*

<br>

- ***Q : Qu'est ce que le "cracking"*** ?

  *R : le cassage de mot de passe (En anglais : [password cracking](https://fr.wikipedia.org/wiki/Cassage_de_mot_de_passe)) est le processus de récupération de mots de passe à partir de données stockées ou transmises par un système informatique*.

<br>

- ***Q : Où sont stockés les mot de passe "crackés" ?***

  *R : Les mots de passe "crackés" sont stockés dans un fichier caché, vous pouvez accéder au contenu de ce fichier via cette commande :*
    ```bash
    cat /home/wilder/snap/john-the-ripper/610/.john/john.pot
    ```

<br>

- ***Q : Malgré plusieurs minutes/heures, John The Ripper ne trouve pas le mot de passe, comment faire ?***

  *R : Comme expliqué en introduction de ce README, John The Ripper utilise différents types d'attaques afin de réussi à trouver un mot de passe ; Cependant, les mots de passe complexes (Par exemple : Avec des caractères spéciaux) réprésentent une vraie difficulté dans le cadre d'une attaque de mots de passe par dictionnaire.*

   - *Cependant, vous pouvez ajouter une "wordlist" (La "wordlist" [RockYou](https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt) étant la plus connue) à John The Ripper, ce qui lui permettra d'étoffer sa base de mots de passe potentiels.*

   - *Il faudra ajouter le paramètre `--wordlist=<nom_de_la_wordlist.txt>` à la commande :*

   ```bash
    john --wordlist=<nom_de_la_wordlist.txt> <fichier_hash.txt>
    ```
   
</details>
