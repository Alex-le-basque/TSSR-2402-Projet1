# Configuration des VM
## 1. Création VM-Ubuntu-Client
### a. Prérequis
- 4G Ram
- 2 CPU
- 2 Cartes réseau : 1 NAT et 1 Interne
_Dans affichage cocher l'option : "Activer l'accéleration 3D"_

### b.Post-installation
- Désactivation veille
- Faire maj système sudo apt update && sudo apt upgrade -y
- Installer les guest additions (en GUI)

Installer SSH : sudo apt-get install openssh-server  # Installer le serveur SSH

Générer clé SSH : ssh-keygen -R 172.16.10.10

vérifier la clé : ssh-keyscan -t rsa 172.16.10.10

Au cas ou vérifier la connexion "ssh Administrator@172.16.10.10"

### c.Paramétrer IP fixe (sur carte réseau 2)
- En GUI, dans activités rechercher “réseau” puis choisir Connexion filaire 2
- Ajouter dans IPV4 
Adresse :172.16.10.20
Masque de réseau : 255.255.255.0 (le nombre 24 s'inscira automatiquement)

## 2. Création VM-Windows Server 2022
### a. Prérequis
- 4G Ram
- 2 CPU
- 2 Cartes réseau : 1 NAT et 1 Interne

  
Installer SSH

https://247-it.io/windows-serveur-2022-installer-serveur-ssh/

### 3. Commande pour récupérer le fichier

**scp Administrator@172.16.10.10:/C:/Users/Administrator/testrecep.txt ~/Documents**


