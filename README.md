# 🖥️ Projet 1 : Téléassistance

<br>

<img src="https://github.com/WildCodeSchool/TSSR-1025-P1-G1/blob/main/Ressources/Image_Teleassistance.png" align="center" width="500" height="500"/>

## Sommaire 

- [🎯 Présentation du projet](#presentation-du-projet)
- [👥 Membres du groupe par sprint](#membres-du-groupe-par-sprint)
- [⚙️ Choix Techniques](#choix-techniques)
- [🧗Difficultés rencontrées](#difficultes-rencontrees)
- [💡 Solutions trouvées](#solutions-trouvees)
- [🚀 Améliorations possibles](#ameliorations-possibles)

# 🎯 Présentation du projet
<span id="presentation-du-projet"></span>
### La téléassistance

**Présentation**  
Le but de ce projet est la mise en place de systèmes de téléassistance pour la prise de contrôle à distance. Pour cela nous avons utilisés 4 machines en réseaux local et installé plusieurs logiciels pour la communication entre les machines.

**Objectifs finaux**  
Les objectifs finaux de ce projet sont :
 - 1 : la prise de contrôle à distance du : 
      - Client Windows vers Windows Server avec **VNC** et **RDP**
      - Client Windows vers Debian Server avec **PuTTY**
      - Client Linux Vers Windows Server avec **VNC**
      - Client Linux vers Debian Server avec **openssh**

 - 2 : La création d'un groupe local "Assistance" sur le client Windows pour la prise de contrôle à distance
 - 3 : La sécurisation d'une connexion SSH 

# 👥 Membres du groupe par sprint
<span id="membres-du-groupe-par-sprint"></span>
**Sprint 1**

| Membre     | Rôle       | Missions |
| ---------- | ---------- | -------- |
| Christian  | SM         | Mise en place des serveurs, documentation des serveurs      |
| Sami       | PO         | Mise en place Windows Client, documentation Windows Client  |
| Anis       | Technicien | Mise en place de Linux Client, documentation Linux Client   | 


**Sprint 2**

| Membre     | Rôle       | Missions |
| ---------- | ---------- | -------- |
| Sami       | SM         | - Documentation de Linux Client sur USER_GUIDE.md & INSTALL.md |
| Anis       | PO         | - Documentation des Serveurs (Windows & Linux) sur USER_GUIDE.md & INSTALL.md |
| Christian  | Technicien | - Documentation de Windows Client sur USER_GUIDE.md & INSTALL.md |

# ⚙️ Choix techniques
<span id="choix-techniques"></span>
## **Matériels Serveurs**

**Serveur Debian :**
- Nom : **SRVLX01**
- OS : **Debian 13.1.0 CLI**
- Compte utilisateur :  **Root** / **Wilder**
- Mot de passe : **Azerty1***
- IP : **172.16.10.5**
- Masque : **255.255.255.0**

**Serveur Windows :**
  - Nom : **SRVWIN01**
  - OS : **Windows server 2022**
  - Compte utilisateur :  **Administrator** / **Wilder**
  - Mot de passe : **Azerty1***
  - IP & Masque : **172.16.10.5**
  - Masque : **255.255.255.0**

## **Matériels Clients**

**Client Ubuntu :**
- Nom : **UBU01**
- OS : **Ubuntu 24.04 LTS**
- Compte utilisateur : **Wilder**
- Mot de passe : **Azerty1***
- IP : **172.16.10.20**
- Masque : **255.255.255.0**

**Client Windows :**
- Nom : **WIN01**
- OS : **Windows 11 Pro**
- Compte utilisateur : **Wilder**
- Mot de passe : **Azerty1***
- IP : **172.16.10.10**
- Masque : **255.255.255.0**



## **Logiciels**
 
- Serveur Windows : **TightVNCServer - RDP (intégré à l'OS)**

- Serveur Debian : **OpenSSHServer (intégrer à l'OS, mais non installé par défaut — installation requise au premier démarrage)** 

- Client Windows : **TightVNCViewer - RDP (intégré à l'OS) - PuTTY**

- Client Ubuntu : **TightVNCViewer - OpenSSHClient**

# 🧗 Difficultés rencontrées
<span id="difficultes-rencontrees"></span>
- Transfert de fichier crossplateforme sur le logiciel TightVNC 

- Choix d'un VNC facile d'utilisation & gratuit.

# 💡 Solutions trouvées
<span id="solutions-trouvees"></span>
- Utilisation de TightVNC : via ce [lien](https://www.malekal.com/configurer-utiliser-vnc-controle-distance-pc/)
  

# 🚀 Améliorations possibles
<span id="ameliorations-possibles"></span>

- Monitoring réseau, surveillance des connexions.

- Authentification multi-facteurs MFA Windows, pour renforcer la sécurité d'accès.

- Tunnel SSH pour VNC, chiffrement supplémentaire des flux VNC via tunnel SSH.

- D'autres logiciels de téléassistances sont disponibles, via ce [lien](https://vnc.fr.softonic.com/windows/alternatives) gratuits et payants, TightVNC est classé 2éme.
  
