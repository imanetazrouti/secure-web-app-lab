<p align="center">
  <img src="https://media.licdn.com/dms/image/v2/D4D12AQGbSto9IhhMhg/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1689472520460?e=2147483647&v=beta&t=02RdiCtCXEnYz-s_50jyGnXeeJFPeKrIW3pq7kfglkI" 
       style="width:100%; max-height:300px; object-fit:cover;">
</p>

# 🔐 Secure-web-app-lab

Ce projet est un laboratoire pratique centré sur le déploiement, le hardening et le test de sécurité d'un site web hébergé sur un serveur Linux. Il simule un environnement réel où un système est d’abord mis en place, ensuite sécurisé, puis testé face à des vulnérabilités courantes.  
L’objectif est de comprendre comment différents rôles (administrateur système, analyste sécurité et pentester) collaborent pour construire et protéger une infrastructure web.

---

## 🎯 Objectifs 

- Déployer un serveur web fonctionnel sur un environnement Linux 
- Sécuriser le système en appliquant les bonnes pratiques 
- Identifier et exploiter des vulnérabilités web courantes 
- Évaluer l’efficacité des mesures de sécurité mises en place 

---

## 🛠️ Technologies utilisées

- Linux (Apache Server)  
- Apache  
- MySQL 
- PHP   
- SSH  
- UFW / iptables  
- Nmap  

---

## 📁 Structure du projet

- **deployment/** → Installation du serveur et déploiement de l’application  
- **security/** → Configuration de la sécurité et durcissement(hardening) du système  
- **test/** → Tests de vulnérabilité et simulations d’attaques  
- **screenshots/** → Captures d’écran des résultats  

---

## 👥 Répartition des rôles 
### **🖥️ IMANE - Deploiement**
###### Déploiement de l’infrastructure 
- Installation et configuration d’une machine virtuelle Linux. 
- Mise en place du serveur Apache. 
- Installation et configuration de MariaDB pour la base de données. 
- Installation de PHP pour le traitement côté serveur.
  ###### Développement d’une page web test 

- Création d’une page web simple intégrant PHP, HTML et CSS. 
- Vérification du bon fonctionnement du serveur Apache et de PHP sur la machine virtuelle.
  ###### explication du code utilisé
   Partie PHP : traitement des données
  
  - **Connexion à la base de données** : le script utilise `mysqli` pour se connecter à MariaDB avec les informations définies (`host`, `db`, `user`, `pass`).  
  - **Récupération des données du formulaire** : les champs `fullname`, `username`, `password`, `email` et `phone` sont récupérés via `$_POST`.  
  - **Insertion sécurisée** : utilisation d'une **requête préparée** (`prepare`) et `bind_param` pour éviter les injections SQL.  
  - **Retour utilisateur** : si l'insertion réussit, un message de succès est affiché ; sinon, l'erreur est renvoyée.  
  - **Fermeture** : la requête et la connexion à la base de données sont fermées après exécution.
  Partie HTML : structure du formulaire
- Formulaire simple avec des champs pour le nom complet, le nom d’utilisateur, le mot de passe, l’email et le téléphone.  
- Méthode `POST` utilisée pour envoyer les données au serveur.  
- Chaque champ obligatoire est marqué avec `required`.
  Partie CSS : style et interactivité
- Formulaire attractif et interactif.  
- Données correctement insérées dans MariaDB.  
- Retour clair à l’utilisateur sur le succès ou l’échec de l’inscription.
    
  ###### Objectif :
- S’assurer que l’environnement de développement est opérationnel pour accueillir le projet.
- Fournir une page web de démonstration comme preuve de concept. 


---


### **🔐 HOUDA — Analyste Sécurité & Hardening**

##### 🎯 Mon rôle
Sécuriser le serveur  déployé par IMANE

##### Ce que j'ai fait
 ###### 🔥 Pare-feu (UFW)
- Bloqué tous les ports par défaut
- Autorisé uniquement SSH (22), HTTP (80), HTTPS (443)
  ###### 🔑 Sécurisation SSH
- Désactivé la connexion root
- Changé le port par défaut
- Authentification par clé uniquement
  ###### 🛡️ Fail2ban
- Installé et configuré
- Bannissement après 3 tentatives échouées
  ###### 🛠️ Commandes principales utilisées
- ufw enable / ufw allow / ufw deny
- systemctl restart ssh
- fail2ban-client status


### **🔍🔐 NAAMA - Pentesting & Analyse de Sécurité**
Vérifier l’efficacité des mesures de sécurité mises en place après le hardening et identifier d’éventuelles failles résiduelles. 
#### Scan reseau:
- commande utilisée :  nmap -sS -sV --script vuln <IP>
  
Objectif : 
*Identifier les services actifs 
*Détecter automatiquement les vulnérabilités connues (CVE) 
Cette vulnérabilité indique une faille connue dans la version du serveur Apache
Elle peut potentiellement permettre :
*exécution de code  
*fuite d’informations 
*compromission du serveur (selon exploitation) 
Même après hardening : 
✅ L’accès au serveur est bien contrôlé (firewall, SSH sécurisé) 
⚠️ Mais une faille applicative persiste au niveau du service web 


#### Test de résistance SSH (Brute Force): 
- commande utilisée : hydra -t 2 -W 2 -l user -P /usr/share/wordlists/rockyou.txt ssh://<IP>

🔍 Analyse: 
 Aucun mot de passe compromis 
 L’attaque est fortement ralentie (preuve d’un mécanisme de défense actif) 
 Le service SSH résiste aux attaques par dictionnaire 
 Cela confirme que : 
Fail2ban fonctionne correctement (blocage après tentatives) 
L'authentification par clé SSH empeche toute compromission 


#### Analyse des headers HTTP:
- commande utilisée : curl -I http://<IP>
  
Objectif : 
Examiner les en-têtes HTTP retournés par le serveur 
Identifier les informations sensibles et les mécanismes de protection 
* Divulgation d’information
→ La version exacte d’Apache est exposée (utile pour un attaquant)
* Manque de headers de sécurité
→ Le serveur est potentiellement vulnérable à :
Clickjacking
XSS
MIME sniffing
 Cela montre que le serveur est sécurisé au niveau réseau, mais le hardening web est incomplet.

---

## 📊 Résultat

Ce projet illustre le cycle complet d’un site web sécurisé : du déploiement à la défense, jusqu’à la simulation d’attaques, en mettant en évidence les forces et les faiblesses du système.

---

## 🚀 Compétences acquises

- Administration système Linux  
- Configuration de serveurs web    
- Introduction au pentesting

---


## 👥 Collaborateurs

- 👨‍💻 [TAZROUTI IMANE – Déploiement](www.linkedin.com/in/imane-tazrouti-656215400)  
- 🔐 [SANDOUBI HOUDA 2 – Sécurité & Hardening](linkedin.com/in/houda-s-9284aa315)  
- 🕵️ [SABSIBO NAAMA 3 -Pentester ](linkedin.com/in/naama-sabsibo-5b05a0286)


