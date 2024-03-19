<div align="center"><h1>Projet 1 - TSSR 2024</h1></div>
<div align="center"><h1>Sécurisation de mot de passe</h1></div>
<br>
<br>


<details>

<summary><strong><font size="+2">Sommaire</font></strong></summary>

- <b><i>Présentation du projet & Objectifs finaux</i></b>
  
- <b><i>Introduction : Mise en contexte</i></b>

- <b><i>Présentation des membres du groupe et de leur rôles</i></b>

- <b><i>Choix techniques et contraintes</i></b>

- <b><i>Difficultés rencontrées</i></b>

- <b><i>Solutions et/ou Alternatives trouvées pour palier aux problèmes</i></b>

- <b><i>Améliorations possibles envisagées</i></b>

</details>

<HR>

<details>

<summary><strong>Présentation du projet & Objectifs finaux</strong></summary>
  
   
##### Objectif principal :
Effectuer une attaque par dictionnaire pour tester la robustesse du mot de passe d’un fichier zippé chiffré sur un serveur Les logiciels John the Ripper ou Hashcat doivent être utilisés Serveur : Windows Server 2022 Client : Ubuntu 22.04 LTS
   

##### Objectif secondaire :
Effectuer une attaque sur un compte local du serveur
   

##### Les livrables

- Les livrables sont les résultats ou les produits finaux du projet qui sont livrés au client ou aux parties prenantes. Ils peuvent inclure rapports, documents, logiciels, etc ...
<br>

- Ils sont disponibles sur la plateforme GitHub, un dépôt a été créé à cet effet : [TSSR-2402-P1-G1](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse)

</details>

<br>

<details>

<summary><strong>Introduction : Mise en contexte</strong></summary>

> Dans un contexte actuel, il est devenu de plus en plus indispensable de protéger nos données de la manière la plus efficace qui soit.
> L'objectif de ce projet est avant tout de démontrer qu'un mot de passe simple est vulnérable, que le hack de mots de passe est malheureusement à la portée de tous, et enfin, de proposer des solutions pour complexifier l'accès à vos données par des personnes tierces.

</details>

<br>

<details>

<summary><strong>Présentation des membres du groupe et de leur rôles</strong></summary>

##### Le Projet est composé de :
- **Grégory**
- **Maxime**
- **Alexandre**
- **Thomas**
- **Franck**


###### Rôle du Scrum Master (SM) :

Le SM est le garant de la bonne application de la méthode Scrum. Il est responsable de la communication entre les membres de l'équipe et de la bonne réalisation des tâches.

###### Rôle du Product Owner (PO) :

Le PO est le représentant du client. Il est responsable de la définition des besoins et de la priorisation des tâches. Il est le garant de la qualité du produit final.

###### Sont nommés pour la première semaine de Projet (Sprint 1) :

- SM : **Alexandre**
- PO : **Thomas**

###### Sont nommés pour la seconde semaine de Projet (Sprint 2) :

- SM : **Maxime**
- PO : **Grégory**


###### Attribution des tâches/activités par membre :

 - **Grégory** : Gestion des VM
 - **Maxime** : Installation de [JohnTheRipper](https://github.com/openwall/john) + Documentation `User_Guide.md`
 - **Alexandre** : Aide sur les différentes autres tâches + Open SSH
 - **Thomas** : Mise en forme des documentations et en charge des respositorys sur le GitHub de la WCS
 - **Franck** : Vérification du bon fonctionnement des programmes du projet

</details>

<br>

<details>

<summary><strong>Choix techniques et contraintes</strong></summary>
<br>

Le client est sous OS [Ubuntu 22.04 LTS](https://releases.ubuntu.com/jammy/)
  - Nom : `CLILIN01`
  - Compte Utilisateur : `wilder`
  - Mot de passe : `Azerty1*`
  - Adresse IP fixe : `172.16.10.20/24`

Le Serveur est sous OS [Windows Server 2022](https://www.microsoft.com/fr-fr/evalcenter/download-windows-server-2022)

  - Nom : `SRVWIN01`
  - Compte : `Administrator`
  - Mot de passe : `Azerty1*`
  - Adresse IP fixe : `172.16.10.10/24`

</details>

<br>

<details>

<summary><strong>Difficultés rencontrées</strong></summary>
<br>

- Installation de JohnTheRipper

</details>

<br>

<details>

<summary><strong>Solutions et/ou Alternatives trouvées pour palier aux problèmes</strong></summary>

</details>

<br>

<details>

<summary><strong>Améliorations possibles envisagées</strong></summary>

</details>
