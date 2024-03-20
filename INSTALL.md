<div align="center"><h1>Sécurisation de mot de passe</h1></div>
<div align="center"><h1>Guide d'installation</h1></div>
<br>
<br>


<details>

<summary><strong><font size="+2">Sommaire</font></strong></summary>

- <b><i>Prérequis techniques</i></b>
  
- <b><i>Installation du poste Client</i></b>

- <b><i>Installation du poste Serveur</i></b>

- <b><i>Test de l'outil JohnTheRipper en local</i></b>

- <b><i>Configuration du SSH</i></b>

- <b><i>FAQ</i></b>

</details>

<HR>

<details>

<summary><strong>Prérequis techniques</strong></summary>

<br>

Disposer de deux machines :

- Une machine avec un OS Ubuntu 22.04 LTS (Client)
- Une machine avec un OS Windows Server 2022 (Serveur)

Outils :

- L'outil [JohnTheRipper](https://github.com/openwall/john) (Version -jumbo)

</details>

<br>

<details>

<summary><strong>Installation du poste Client</strong></summary>

<br>

Pour le poste Client, il nous faut :
  - OS : [Ubuntu 22.04 LTS](https://releases.ubuntu.com/jammy/)
  - Nom : `CLILIN01`
  - Compte Utilisateur : `wilder`
  - Mot de passe : `Azerty1*`
  - Adresse IP fixe : `172.16.10.20/24`

<br>

- Installation des MàJ système : `sudo apt update && sudo apt upgrade -y`
- Installation des "Guest Additions" (Dans le cadre d'une VM)
- Désactivation du parefeu : `sudo ufw disable`
- Installation de l'outil [JohnTheRipper](https://github.com/openwall/john) : `sudo snap install john-the-ripper`
- Installation des librairies de [JohnTheRipper](https://github.com/openwall/john) : `sudo apt install ocl-icd-opencl-dev -y`
- Edition d'un alias  pour la commande `zip2john` : `sudo snap alias john-the-ripper.zip2john zip2john`

<br>


  

</details>

<br>

<details>

<summary><strong>Installation du poste Serveur</strong></summary>

<br>

Pour le poste Serveur, il nous faut : 
  - OS : [Windows Server 2022](https://www.microsoft.com/fr-fr/evalcenter/download-windows-server-2022)
  - Nom : `SRVWIN01`
  - Compte : `Administrator`
  - Mot de passe : `Azerty1*`
  - Adresse IP fixe : `172.16.10.10/24`

<br>

  - Installation des MàJ via Windows Update
  - Installation des "Guest Additions" (Dans le cadre d'une VM)
  - Désactivation du parefeu

</details>

<br>

<details>

<summary><strong>Test de l'outil JohnTheRipper en local</strong></summary>

</details>

<br>

<details>

<summary><strong>Configuration du SSH</strong></summary>

test1

</details>

<br>

<details>

<summary><strong>FAQ</strong></summary>

</details>
