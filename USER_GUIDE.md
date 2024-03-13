<div align="center"><h1>Sécurisation de mot de passe</h1></div>

<details>

<summary><strong><font size="+2">Sommaire</font></strong></summary>

<br>

- JohnTheRipper ou Hashcat ?
-  Caractéristiques de JohnTheRipper et Hashcat
-  Utilisation
-  FAQ

</details>

<HR>

<details>

<summary><strong><font size="+1">JohnTheRipper ou Hashcat ?</font></strong></summary>

<br>

- [JohnTheRipper](https://github.com/openwall/john) est un outil de "cracking" de mots de passe, prenant en charge de nombreux algorithmes de "hash".
La version "-jumbo" est une amélioration de cet outil, et permet, entre autres, de récupérer le "hash" des fichiers `.zip`

<br>

- [Hashcat](https://github.com/hashcat/hashcat), quand à lui, se définit comme l'utilitaire de         récupération de mots de p  asse "*le plus rapide et le plus avancé du monde*".
Cependant, contrairement [JohnTheRipper](https://github.com/openwall/john), il ne posséde pas la fonctionnalité lui permettant de récupérer le "hash" des fichiers `.zip`

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

   - **Attaque par dictionnaire** : L'outil essaiera un à un tous les mots contenus dans une liste préalablement chargée (Par défault, la liste `passworld.lst` fournie contiens plus de 3000 mots), en leur appliquant les mêmes modifications que dans le mode "simple".

<br>

- #### Avantages :
   - [JohnTheRipper](https://github.com/openwall/john) est un outil puissant et polyvalent pour la récupération de mots de passe et l'audit de sécurité informatique.
  Bien qu'il soit principalement utilisé par des professionnels de la sécurité informatique, il peut également être utile pour les utilisateurs individuels qui cherchent à renforcer la sécurité de leurs mots de passe

<br>
<br>

## [Hashcat](https://github.com/hashcat/hashcat)

- ##### Modes de fonctionnement :

  - **Attaque par combinateur** : Les mots de passe étant souvent constitués de mots composés, Hashcat va exploiter cette habitude et se servir de la méthode de l'attaque par dictionnaire afin de créer une nouvelle liste, chaque mot sur deux de la liste sera combiné ; L'outil pourra également utiliser les signes de ponctuation et les caractères spéciaux pour créer une liste finale de mots de passe potentiels.

  - **Attaque par masque** : En partant du postulat que beaucoup d'utilisateurs utilisent des mots de passe en adoptant un certain type de séquence (Par exemple, une lettre majuscule suivi de 6 lettres et d'un chiffre à la fin ; "Bananas1"), Haschat va rechercher tous les mots de passe dans ce format. L'attaque par masque exploite donc les habitudes des humains et la façon dont ils conçoivent les mots de passe afin de faciliter l'opération.

<font size="-1">**NB** : [Hashcat](https://github.com/hashcat/hashcat) dispose également des mêmes modes de fonctionnement que [JohnTheRipper](https://github.com/openwall/john).</font> 
<br>
- ##### Avantages :
  - Flexibilité : Prise en charge de nombreux formats de "hash".
  - Performance : Considéré comme l'un des outils de "cracking" de mot de passe les plus performants.




</details>

<details>

<summary><strong><font size="+1">Utilisation</font></strong></summary>

</details>

<details>

<summary><strong><font size="+1">FAQ</font></strong></summary>

<br>

 - ***Qu'est ce que le "hash"*** ?
   - *La fonction de hachage (En anglais : [hash](https://fr.wikipedia.org/wiki/Fonction_de_hachage)) est une fonction cryptographique formée d'une unique châine de caractères destinée à coder des données (Par exemple : des mots de passe), servant ainsi à garantir l'authenticité de ces dernières.*

<br>

- ***Qu'est ce que le "cracking"*** ?
   - *le cassage de mot de passe (En anglais : [password cracking](https://fr.wikipedia.org/wiki/Cassage_de_mot_de_passe)) est le processus de récupération de mots de passe à partir de données stockées ou transmises par un système informatique*.

</details>
