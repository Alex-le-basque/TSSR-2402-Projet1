# Configuration du SSH

## 1. VM Windows Server
Ouvrir Powershell en Admisistrator

- Pour installer le service SSH:  
**``Add-WindowsCapability -Online -Name OpenSSH.Server``**

- Pour un démarrage automatique :  
**``Set-Service sshd -StartupType Automatic``**

![install](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Images%20Greg/install%20ssh%20Windows.PNG?raw=true)

_Vérifier si le service est bien actif (cf copies d'écran ci-dessous)_

![services](https://github.com/Seyia11/capture-cran-2/blob/main/service%20SSH%20Windows.PNG?raw=true)

- Redémarer la VM


## 2. VM Ubuntu client

Ourvir le Terminal

- Pour installer le service SSH:  
**``sudo apt-get install openssh-server``**

![UBUNTU](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Images%20Greg/install%20ssh%20Ubuntu%201.PNG?raw=true)

Lors du message : _Souhaitez-vous continuer ? [O/n]_ Taper O

- Une fois le SSH installé, il faut l'activer:  
**``sudo systemctl enable ssh``**

![active](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Images%20Greg/activation%20ssh%20ubuntu.PNG?raw=true)

- Pour terminer génerez une clé à destination du Server Windows:  
**``ssh-keyscan -t rsa 172.16.10.10``**

![gen](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Images%20Greg/generer%20cl%C3%A9%20ubuntu.PNG?raw=true)

Redémarer la VM

# 3. Test transfert de fichier

Nous avons paramétré le service SSH sur les deux VM pour le partage de fichier.

- Sur la VM Server Windows, créer le fichier test1.txt à la racine du dossier Administrator :  
**``New-Item -ItemType File -Path "test1.txt``**

![fic](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Images%20Greg/cr%C3%A9a%20fichier%20test1.PNG?raw=true)

- Depuis la VM Cleint Ubuntu, ouvrer le Terminal et taper la commande ci dessous:

**``scp Administrator@172.16.10.10:/C:/Users/Administrator/test1.txt ~/Documents``**

![copie](https://github.com/WildCodeSchool/TSSR-2402-P1-G1-SecurisationDeMotDePasse/blob/main/Images/Images%20Greg/copie%20fichier.PNG?raw=true)

_Attention: le mot de passe demandé sera celui du compte Administrator Windows_

- Le fichier test1 est copié dans le dossier Documents du compte wilder.

_Si problème se reporter à la FAQ_

