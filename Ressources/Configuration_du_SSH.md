# Configuration du SSH

## 1. VM Windows Server
Ouvrir Powershell en Admisistrator

- Pour installer le service SSH:
>**Add-WindowsCapability -Online -Name OpenSSH.Server**

- Pour un démarrage automatique :
>**Set-Service sshd -StartupType Automatic**

_Vérifier si le service est bien actif (cf copie d'écran ci-dessous)_

![services](https://github.com/Seyia11/capture-cran-2/blob/main/service%20SSH%20Windows.PNG?raw=true)

- Redémarer la VM


## 2. VM Ubuntu client

Ourvir le Terminal

- Pour installer le service SSH:
>**sudo apt-get install openssh-server**

Lors du message : _Souhaitez-vous continuer ? [O/n]_ Taper O

- Une fois le SSH installé, il faut l'activer:
>**sudo systemctl enable ssh**

- Pour terminer génerez une clé à destination du Server Windows:
>**ssh-keyscan -t rsa 172.16.10.10**

Redémarer la VM

# 3. Test transfert de fichier

Nous avons paramétré le service SSH sur les deux VM pour le partage de fichier.

- Sur la VM Server Windows, créer le fichier test1.txt à la racine du dossier Administrator.

- Depuis la VM Cleint Ubuntu, ouvrer le Terminal et taper la commande ci dessous:
>scp Administrator@172.16.10.10:/C:/Users/Administrator/test1.txt ~/Documents

_Attention: le mot de passe demandé sera celui du compte Administrator Windows_

- Le fichier test1 est copié dans le dossier Documents du compte wilder.

_Si problème se reporter à la FAQ_

