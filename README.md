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

# **🔐 HOUDA — Analyste Sécurité & Hardening**

🎯 Mon rôle
Sécuriser le serveur  déployé par IMANE

& Ce que j'ai fait
 🔥 Pare-feu (UFW)
- Bloqué tous les ports par défaut
- Autorisé uniquement SSH (22), HTTP (80), HTTPS (443)
 🔑 Sécurisation SSH
- Désactivé la connexion root
- Changé le port par défaut
- Authentification par clé uniquement
  🛡️ Fail2ban
- Installé et configuré
- Bannissement après 3 tentatives échouées
 🛠️ Commandes principales utilisées
- ufw enable / ufw allow / ufw deny
- systemctl restart ssh
- fail2ban-client status

---



---

## 📊 Résultat

Ce projet illustre le cycle complet d’un site web sécurisé : du déploiement à la défense, jusqu’à la simulation d’attaques, en mettant en évidence les forces et les faiblesses du système.
<p align="center">
  <img src="https://media.licdn.com/dms/image/v2/D4D12AQGbSto9IhhMhg/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1689472520460?e=2147483647&v=beta&t=02RdiCtCXEnYz-s_50jyGnXeeJFPeKrIW3pq7kfglkI" 
       style="width:100%; max-height:300px; object-fit:cover;">
</p>

# 🔐 Secure-web-app-lab

Ce projet est un laboratoire pratique centré sur le déploiement, le hardening et le test de sécurité d'un site web hébergée sur un serveur Linux. Il simule un environnement réel où un système est d’abord mis en place, ensuite sécurisé, puis testé face à des vulnérabilités courantes.  
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
- **security/** → Configuration de la sécurité et durcissement du système  
- **test/** → Tests de vulnérabilité et simulations d’attaques  
- **screenshots/** → Captures d’écran des résultats  

---

## 👥 Répartition des rôles 

*(ajouter vos rôles ici si nécessaire)*

---

## 🚀 Compétences acquises

- Administration système Linux  
- Configuration de serveurs web    
- Introduction au pentesting

---

## 📊 Résultat

Ce projet illustre le cycle complet d’un site web sécurisé : du déploiement à la défense, jusqu’à la simulation d’attaques, en mettant en évidence les forces et les faiblesses du système.

---

## 👥 Collaborateurs

- 👨‍💻 [TAZROUTI IMANE – Déploiement](www.linkedin.com/in/imane-tazrouti-656215400)  
- 🔐 [SANDOUBI HOUDA 2 – Sécurité & Hardening](linkedin.com/in/houda-s-9284aa315)  
- 🕵️ [SABSIBO NAAMA 3 -Pentester ](linkedin.com/in/naama-sabsibo-5b05a0286)


