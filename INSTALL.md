# Documentation d'Installation - Administration à Distance

## Contexte du Projet
Ce document décrit l'installation et la configuration des outils d'administration à distance dans un environnement réseau local comprenant des machines Windows et Linux.

---

# Table des Matières
I. [Prérequis Techniques](#I-prérequis-techniques)  

II. [Installation sur Windows Server 2022 (Serveur)](#II-installation-sur-windows-server-2022-serveur)  
   - [1. TightVNC](#1-tightvnc)  
   - [2. RDP](#2-rdp)  
   - [3. Configuration Assistance](#3-configuration-assistance)

III. [Installation sur Debian 13.1 (Serveur)](#III-installation-sur-debian-131-serveur)  

IV. [Installation sur Windows 11 (Client)](#IV-installation-sur-windows-11-client)  
   - [1. PuTTY](#1-putty)  
      - [A. Téléchargement de PuTTY](#a-téléchargement-de-putty)  
      - [B. Installation de PuTTY](#b-installation-de-putty)  
   - [2. TightVNC](#2-tightvnc)  
      - [A. Téléchargement de TightVNC](#a-téléchargement-de-tightvnc)  
      - [B. Installation de TightVNC](#b-installation-de-tightvnc)

V. [Installation sur Ubuntu 24.04 (Client)](#V-installation-sur-ubuntu-2404-client)  
   - [1. Installation de TightVNC](#1-installation-de-tightvnc)  
   - [2. Mise en place du serveur SSH](#2-mise-en-place-du-serveur-ssh)  
      - [A. Installation d'OpenSSH et première connexion](#a-installation-d-openssh-et-première-connexion)  
      - [B. Création d'une clé SSH](#b-création-clé-ssh)

---

# I. Prérequis Techniques

## 1. Infrastructure Réseau
- **Topologie** : Réseau local privé avec adressage IP statique
- **Configuration requise** :
  - Serveur Windows Server 2022
  - Serveur Debian 13
  - Client Windows 11 Pro
  - Client Ubuntu 24.04
- **Connectivité** : Toutes les machines doivent pouvoir communiquer sur le réseau local

## 2. Configuration IP
Assurez-vous que chaque machine possède :
- Une adresse IP statique configurée sur le réseau (172.16.10.0)
- Un masque de sous-réseau 255.255.255.0

## 3. Logiciels Nécessaires

#### Pour Windows Server 2022
- TightVNC Server (pour l'accès distant graphique)
- OpenSSH Server (natif Windows Server)

#### Pour Debian 13
- OpenSSH Server (pour les connexions SSH)
- Accès root ou sudo

#### Pour Windows 11 (Client)
- PuTTY (pour SSH vers Debian)
- TightVNC Viewer (pour VNC vers Windows Server)
- Client RDP (natif Windows)

#### Pour Ubuntu 24.04 (Client)
- OpenSSH Client (généralement préinstallé)
- TightVNC Viewer ou Remmina (pour VNC vers Windows Server)



# II. Installation sur Windows Server 2022 (Serveur)

## 1. TightVNC

---  

### Etape 1 :   Lancer le téléchargement de TightVNC
 
Télécharger TightVNC : https://www.tightvnc.com/download/2.8.85/tightvnc-2.8.85-gpl-setup-64bit.msi

---  
### Etape 2 :   Lancer l’exécutable d’installation

- Dirigez-vous dans l’Explorateur de fichiers
- Ouvrez le dossier "Downloads"
- Lancez l'exécutable
- Cliquez sur "Next" pour poursuivre l'installation

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/TightVNC/01_InstallVNC.png?raw=true)

---  
### Etape 3 :   Accepter la licence et choisir le type d’installation
 
- Cochez la case : "I accept the terms in the License Agreement"
- Choisissez le type d'installation en "Typical"

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/TightVNC/02_InstallVNC.png?raw=true)

---  
### Etape 4 :   Vérifier les options avant l’installation
 
- Vérifiez que les cases "Associate .vnc files with TightVNC Viewer, Register TightVNC Server as a system service & Configure system to allow services simulate Ctrl-Alt-Del" sont bien cochées. 
- Cliquez ensuite sur "Install".

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/TightVNC/03_InstallVNC.png?raw=true)

---  
### Etape 5 :   Configurer la sécurité de TightVNC
   
- Cochez les cases "Require password-based authentication" et "Protect control interface with an administrative password".
- Saisissez des mots de passe différents pour le Remote Access et pour l’Administrative Access.
- Vérifiez dans les icones cachés si TightVNC est bien lancé.

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/TightVNC/04_InstallVNC.png?raw=true)  

---  
---  

## 2. RDP


### Dans cette section, nous verrons comment activer le Bureau à distance (Remote Desktop). 
---  
### Etape 1 :   Ouvrir le Panneau de configuration
  
- Sur le bureau, dans la barre de recherche, tapez "Control Panel"  
- Cliquez sur l'application "System and Security" 

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/RDP/RDP/01_ConfigRDP.png?raw=true)

---  
### Etape 2 :   Accéder aux paramètres de Remote Desktop
 
- Cliquez sur "System".
- Une nouvelle fenêtre s’ouvre. Selon votre résolution, recherchez "Remote Desktop" dans la page "About", il peut se trouver à droite ou en bas de la page. 
- Cliquez dessus.

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/RDP/RDP/02_ConfigRDP.png?raw=true)

---  
### Etape 3 :   Activer Remote Desktop
  
- Cliquez sur le bouton "Enable Remote Desktop"
- Acceptez l’autorisation en cliquant sur "Confirm"    

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/RDP/RDP/03_ConfigRDP.png?raw=true)

---  
### Etape 4 :   Remote Desktop activé


- Le Bureau à distance activé, le poste est prêt à accepter les connexions distantes, permettant aux utilisateurs autorisés d’accéder au système de manière sécurisée.

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/RDP/RDP/04_ConfigRDP.png?raw=true)

---  
---  

## 3. Configuration Assistance 
Dans cette section nous allons ajouter un utilisateur au groupe Remote Desktop Users
---  
### Etape 1

- Appuyez sur Windows + R
- Tapez "compmgmt.msc"
- Cliquez sur OK

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/Config_Assistance/01_assistance_config.png?raw=true)
---  
### Etape 2

- Cliquez sur Local Users & Groups
- Cliquez sur Users

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/Config_Assistance/02_assistance_config.png?raw=true)
---  
### Etape 3

- Cliquez sur "Action" puis sur "New User..."
- Tapez Wilder-Assistance
- Cliquez sur Create 

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/Config_Assistance/03_assistance_config.png?raw=true)
---  
### Etape 4

- Cliquez sur Action, puis sur New User...
- Tapez Wilder-Assistance
- Cliquez sur Create.

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/Config_Assistance/04_assistance_config.png?raw=true)
---  
### Etape 5

- Écrivez le nom de l’utilisateur qui doit avoir les autorisations nécessaires,
- Cliquez sur Check Names. Si aucune erreur de frappe ou utilisateur inexistant n’est détecté, vous verrez un aperçu comme ceci : "Fromthislocation\User"
 correspond au nom de la machine et User à l’utilisateur nécessitant les droits.
- Cliquez sur OK.
![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/Config_Assistance/05_assistance_config.png?raw=true)
---  
### Etape 6

- Cliquez sur Apply

![image URL](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Windows/Config_Assistance/06_assistance_config.png?raw=true)
 
---
---

# III. Installation sur Debian 13.1 (Serveur)

Pour la machine serveur Linux Debian, ici appelée "srvlx01", nous allons vérifier si la suite logicielle OpenSSH est bien installée et si le service SSH est bien activé pour les connexions via OpenSSH et PuTTY.

---

Mettre en route la machine serveur Linux (Debian), ici nommée "srvlx01".

- Se connecter en tant qu'administrateur et entrer son mot de passe.

![Image01](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Linux/01_Serveur_Linux_SSH.png)

---

- Vérifier si l'OS est à jour avec la ligne de commande `apt install update && apt upgrade`. (Ce dernier est à jour dans le cas présent.)

![Image02](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Linux/02_Serveur_Linux_SSH.png)

---

- Installer le serveur OpenSSH avec la commande `apt install openssh-server`. Si ça n'a pas été fait au moment de l'installation de l'OS.

![Image03](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Linux/03_Serveur_Linux_SSH.png)

---

- Vérifier le statut de la connexion SSH avec la commande `systemctl status ssh`.

- S'il n'est pas actif comme indiqué dans les lignes "Loaded" (2x "enabled" en vert) et "Active" ("active (running)" en vert), entrer les commandes à la suite les commandes `systemctl start ssh` et `systemctl enabled ssh` pour activer le service SSH.

![Image04](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Serveur_Linux/04_Serveur_Linux_SSH.png)

### Voilà, les vérifications sont terminées !

---
---

# IV. Installation et sur Windows 11 (Client)

## 1. PuTTY  

### A. Téléchargement de PuTTY  

- Télécharger PuTTY depuis le site officiel : https://www.putty.org/
- Lien direct vers la dernière version à installer : https://the.earth.li/~sgtatham/putty/latest/w64/putty-64bit-0.83-installer.msi
- Lien direct vers la dernière version portable (passer directement à l'étape 3) : https://the.earth.li/~sgtatham/putty/latest/w64/putty.exe

--- 

### B. Installation et de PuTTY  

**Étape 1 : Accueil et choix du dossier d'installation**

- Double-cliquer sur le fichier d'installation téléchargé
- L'assistant d'installation **PuTTY** s'affiche
- Cliquer sur **Next**
- Le dossier par défaut proposé est `C:\Program Files\PuTTY\`
- Conserver ce dossier ou cliquer sur **Change** pour le modifier
- Cliquer sur **Next**

![Sceenshot - PuTTY](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/PuTTY/02_putty_installation.png)  

---

**Étape 2 : Sélection des fonctionnalités et finalisation d'installation**

- Sélectionner les options souhaitées :
   - **Install PuTTY files**
   - **Add shortcut to PuTTY on the Desktop** (pour créer un raccourci bureau, il n'est pas activé par défaut)
   - **Put install directory on the PATH for command prompts**
   - **Associate .PPK files with PuTTYgen and Pageant**
- Cliquer sur **Install**
- L'installation est terminée
- Cocher **View README file** si vous souhaitez consulter la documentation
- Cliquer sur **Finish**
 
![Sceenshot - PuTTY](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/PuTTY/02_putty_installation.png)

---

**Étape 3 : Première utilisation et connexion** 
- Entrer une adresse IP dans la case **Host Name (or IP address)**
- Cliquer sur **Open**
- Un message d'avertissement apparait
- Cliquer sur **Accept** pour garder la clé en cache si vous souhaitez vous connecter plus tard sinon sur **Connect Once**

![Sceenshot - PuTTY](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/PuTTY/03_putty_installation.png)

---

**Étape 4 : Login et Password**
- Entrer l'identifiant utilisateur de la machine distante
- Entrer le mot de passe de l'utilisateur précédemment entré

![Sceenshot - PuTTY](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/PuTTY/04_putty_installation.png)

---

**Étape 5 : Vous êtes connecté!**  

![Sceenshot - PuTTY](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/PuTTY/05_putty_installation.png)  

---
---  

## 2. TightVNC  

### A. Téléchargement de TightVNC Viewer

- Télécharger TightVNC depuis le site officiel : https://www.tightvnc.com/
- Lien direct vers la dernière version : https://www.tightvnc.com/download/2.8.85/tightvnc-2.8.85-gpl-setup-64bit.msi

---

### B. Installation de TightVNC Viewer

**Étape 1 : Accueil et acceptation des termes de la licence**

- Double-cliquer sur le fichier d'installation
- L'assistant **TightVNC Setup** s'affiche
- Cliquer sur **Next**
- Cocher **I accept the terms in the License Agreement**
- Cliquer sur **Next**

![Sceenshot - TightVNC](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/TightVNC/01_vnc_installation.png)

---

**Étape 2 : Choix du type d'installation et choix des composants**

- Sélectionner **Custom** (pour choisir les composants à installer)
- Cliquer sur **Next**
- Dans l'arborescence, **enlever** **TightVNC Server** ( Sur le poste client nous utilisons seulement le viewer)
- Cliquer sur **Next**  

![Sceenshot - TightVNC](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/TightVNC/02_vnc_installation.png)  

---

**Étape 3 : Associations des fichiers et installation**

- Sous **File associations**, cocher **Associate .vnc files with TightVNC Viewer**
   - Cette option permet d'ouvrir automatiquement les fichiers `.vnc` avec TightVNC
- Cliquer sur **Next**
- L'écran **Ready to install TightVNC** confirme les paramètres
- Cliquer sur **Install** pour lancer l'installation

![Sceenshot - TightVNC](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/TightVNC/03_vnc_installation.png)  

---

**Étape 4 : Fin de l'installation**

- Cliquer sur **Finish**
- Ouvrir le menu Démarrer de Windows 11
- Rechercher **"tight"** dans la barre de recherche
- **TightVNC Viewer** apparaît dans les résultats sous **Meilleur résultat** ( TightVNC ne met pas de raccourci sur le bureau par défaut)
- Cliquer sur **TightVNC Viewer**  

![Sceenshot - TightVNC](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/TightVNC/04_vnc_installation.png)  

 ---

**Étape 5 : Première utilisation et connexion**
- Entrer une adresse IP dans **Remote Host**
- Cliquer sur **Connect**
- Entrer le mot de passe configurer sur VNC Server sur le poste distant dans **Password**  

![Sceenshot - TightVNC](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/TightVNC/05_vnc_installation.png)  

---  

**Étape 6 : Vous êtes connecté!**    

![Sceenshot - TightVNC](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Windows/TightVNC/06_vnc_installation.png)  

---
---

# V. Installation sur Ubuntu 24.04 (Client)

##  1. Installation de TightVNC

  Installation d'une application VNC, TightVNCViewer, sur un client Linux, dans le cas présent sur la version d'Ubuntu 24.04 LTS à jour pour le lier à une machine virtuelle serveur Windows et se connecter dessus. Le serveur en question est l'OS Windows Server 2022 GUI (interface graphique), préalablement installé et configuré de TightVNCServer (Voir partie I).   



---
 
- Mettre en route la machine Ubuntu qui se nomme ici "ubu01".

- Il vous faut ouvrir le Terminal d'Ubuntu. Cliquer sur le logo d'Ubuntu (Dock) en bas à gauche de l'écran ensuite cliquer sur l'icône sous laquelle est écrit Terminal s'il apparaît.

![Image01](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/01_TightVNC_Client_Linux.png)

---
- Sinon rechercher l'application Terminal directement dans la barre de recherche.

- Ouvrir donc le Terminal.

![Image02](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/02_TightVNC_Client_Linux.png)

---
- Entrer la ligne de commande `apt install xtightvncviewer` pour installer le logiciel TightVNCViewer.

- On constate qu'un message d'erreur apparaît concernant les droits utilisateurs.

![Image03](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/03_TightVNC_Client_Linux.png)

---
- On force l'installation en ajoutant la commande `sudo` à la précédente ligne de commande : `sudo apt install xtightvncviewer`

- Ne pas oublier d'ajouter le mot de passe permettant d'accéder aux droits administrateurs.

![Image04](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/04_TightVNC_Client_Linux.png)

---
- Tapez `O` et laissez l'installation s'opérer.

![Image05](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/05_TightVNC_Client_Linux.png)

---
- Une fois l'installation effectuée, mettre en route à côté la machine serveur Windows, ici nommée "srvwin01".

![Image06](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/06_TightVNC_Client_Linux.png)

---
- Vérifier que le processus TightVNCServer est bien actif :   
  Deux manières de faire :

---

  a) Avec une invite de commandes ou plus communément appelé "Shell" :

* Rechercher dans la barre de recherche le logiciel "PowerShell".

* Ouvrir PowerShell en tant qu'Administrateur avec une action de clic droit dessus.
  
![Image07](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/07_TightVNC_Client_Linux.png)
   
---
     
* Taper la ligne de commande `Get-Process -Name tvnserver`.

* On constate que le processus "tvnserver" est bien en cours.

![Image08](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/08_TightVNC_Client_Linux.png)
   
---
     
* "tvnserver" étant le processus de TightVNCServer, on peut le vérifier avec la ligne de commande suivante :  
`Get-Process -Name tvnserver -FileVersionInfo | Format-List`

* On constate donc que "tvnserver" est en cours et qu'il s'agit bien du processus de TightVNCServer.

![Image09](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/09_TightVNC_Client_Linux.png)
      
---
  b) Directement sur l'interface graphique :
 
* Cliquer sur la flèche dans la barre des tâches.
* Cliquer sur l'icône V entouré d'un carré blanc.

* On constate bien que TightVNCServer est en cours.
    
![Image10](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/10_TightVNC_Client_Linux.png)
    
---
- Laisser de côté "srvwin01" et revenir sur "ubu01". Taper ensuite la ligne de commande `vncviewer srvwin01` pour ouvrir le logiciel TightVNCViewer.

- Taper le mot de passe choisi au préalable sur le serveur VNC sur la machine serveur Windows.

![Image11](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/11_TightVNC_Client_Linux.png)

---
- Une fenêtre se lance : "TightVNC : srvwin01".

- Regarder simultanément les écrans de "ubu01" et "srvwin01".

![Image12](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/TightVNC/12_TightVNC_Client_Linux.png)
  

### **Voilà, vous avez connecté le client Linux au serveur Windows !**   


---
---


## 2. Mise en place du serveur SSH
### A. Installation d'OpenSSH et première connexion

  Installation de la suite logicielle OpenSSH sur un client Linux, dans le cas présent sur la version d'Ubuntu 24.04 LTS à jour pour le lier à une machine vituelle serveur Linux et se connecter dessus. Le serveur en question est l'OS Debian 13.1.0 CLI (interface d'invite de commandes).  

---

- Mettre en route la machine Ubuntu qui se nomme ici "ubu01".

- Ouvrir le Terminal. (Se référer au 1. pour le localiser.)

![Image01](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/01_OpenSSH_Client_Linux.png)

---

- Entrer la ligne de commande `apt install openssh-client` pour installer le client OpenSSH.
- On constate qu'un message d'erreur apparaît concernant les droits utilisateurs.

- On force l'installation en ajoutant la commande `sudo` à la précédente ligne de commande : `sudo apt install openssh-client`.

![Image02](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/02_OpenSSH_Client_Linux.png)

---


- Ne pas oublier d'ajouter le mot de passe permettant d'accéder aux droits administrateurs.

- Laisser l'installation s'opérer.

![Image03](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/03_OpenSSH_Client_Linux.png)

---

- Une fois l'installation effectuée, mettre en route à côté la machine serveur Linux (Debian), ici nommée "srvlx01".

- Se connecter en tant qu'administrateur et entrer son mot de passe.

![Image04](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/04_OpenSSH_Client_Linux.png)

---

- Vérifier si l'OS est à jour avec la ligne de commande `apt install update && apt upgrade`. (Ce dernier est à jour dans le cas présent.)

![Image05](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/05_OpenSSH_Client_Linux.png)

---

- Installer le serveur OpenSSH avec la commande `apt install openssh-server`. Si ça n'a pas été fait au moment de l'installation de l'OS.

![Image06](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/06_OpenSSH_Client_Linux.png)

---

- Vérifier le statut de la connexion SSH avec la commande `systemctl status ssh`.

- S'il n'est pas actif comme indiqué dans les lignes "Loaded" (2x "enabled" en vert) et "Active" ("active (running)" en vert), entrer les commandes à la suite les commandes `systemctl start ssh` et `systemctl enabled ssh` pour activer le service SSH.

![Image07](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/07_OpenSSH_Client_Linux.png)

---
- Laisser de côté "srvlx01" et revenir sur "ubu01".      
Taper ensuite la ligne de commande `ssh nom_utilisateur@adresse_ip_ou_nom_du_serveur`.

Ici le nom d'utilisateur est "wilder" et le nom du serveur est "srvlx01", comme celui de la machine, avec comme adresse ip 172.16.10.6 auparavant indiqué dans les prérequis) pour créer une clé SSH avec la machine "srvlx01".
 
- Taper `yes` et taper ensuite le mot de passe de la machine "srvlx01" (préalablement choisi dans la partie II).

![Image08](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/08_OpenSSH_Client_Linux.png)

---
- On constate bien un changement nom de machine à côté du `@` .

![Image09](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/09_OpenSSH_Client_Linux.png)

### **Voilà, vous avez connecté le client Linux au serveur Linux !**
 
---

### Bonus : Se déconnecter du serveur.

- Taper `logout` ou `exit` ou encore appuyer sur CTRL + D pour se déconnecter du serveur depuis le client.
- On constate bien que le nom de la machine a changé et que vous êtes revenu sur la machine client "ubu01".

![Image10](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/10_OpenSSH_Client_Linux.png)

---
---


### B. Création d'une clé SSH  

Vous pouvez générer une clé SSH entre le client et le serveur, ici entre "ubu01" et "srvlx01" pour ne pas avoir à rentrer le mot de passe à chaque fois et que le lien entre les deux machines soit solide.  

---

- Rester dans la même session du Terminal et entrer la ligne de commande `ssh-keygen -t ed25519` (Vous pouvez ajouter l'option de nommer la clé SSH avec l'argument `-C` et le nom que vous souhaitez à la suite de la ligne de commande. Par exemple `ssh-keygen -t ed25519 -C "utilisateur@entreprise.fr"`.  
  Appuyer ensuite sur Entrée, le début du processus de génération de clé commencera.
- Saisissez par la suite le fichier dans lequel enregistrer la clé (comme indiqué ici en anglais). Pour ma part, le chemin du fichier proposé me convient bien donc j'appuie sur Entrée.

![Image11](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/11_OpenSSH_Client_Linux.png)

---

- Saisissez une phrase secrète si vous en souhaitez une pour plus de sécurité et confirmez-la.
- Après avoir validé, on constate bien que la clé a été générée.

![Image12](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/12_OpenSSH_Client_Linux.png)

---

- Mettez en marche la machine serveur en même temps donc "srvlx01" et connectez-vous.
- Après cela, revenez sur ubu01 et entrer la ligne de commande `ssh-copy-id nom_utilisateur@adresse_ip_ou_nom_du_serveur` pour lier et sécuriser la clé SSH nouvellement créée à votre machine serveur (ici, `wilder@srvlx01`). 

![Image13](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/13_OpenSSH_Client_Linux.png)

---

- Entrer ensuite le mot de passe de "srvlx01" et valider.
- On constate bien qu'une clé a été ajoutée !

![Image14](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/14_OpenSSH_Client_Linux.png)

---

- Reconnectez-vous pour pouvoir constater que la clé SSH saisie a bien été ajoutée avec la ligne de commande suivante :  
`ssh nom_utilisateur@adresse_ip_ou_nom_du_serveur` (ici toujours `wilder@srvlx01`).
- On constate bien que vous n'avez pas eu besoin d'entrer un mot de passe avec le changement nom de machine à côté du `@` !

![Image15](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/15_OpenSSH_Client_Linux.png)


### **Voilà, vous avez généré une clé SSH avec la machine serveur !**

---

### Bonus : Se déconnecter du serveur.

- Taper `logout` ou `exit` ou encore appuyer sur CTRL + D pour se déconnecter du serveur depuis le client.
- On constate bien que le nom de la machine a changé et que vous êtes revenu sur la machine client "ubu01".

![Image16](https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Screens_INSTALL/Client_Linux%20/OpenSSH/16_OpenSSH_Client_Linux.png)


---
---













