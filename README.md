# 🛠️ [Projet Hellocyberworld Labs](https://github.com/ShamLucas/HelloCyberWorld)

## 🧠 Objectif du projet

Créer un environnement de développement auto-hébergé pour expérimenter l’administration système, le dev web et le déploiement d’applications. 

L'idée est aussi de créer un modèle de projet type pour scripter l'installation d'un server, le tester en local sur une vm puis le déployer en production.

---

## ⚙️ Stack technique

- **Provisioning & Infra** :
  - [Vagrant](https://www.vagrantup.com/) pour gérer l’environnement de dev local
  - [Ansible](https://www.ansible.com/) pour la configuration automatique des services et déployer soit sur la vm pour les test, soit en production.
  
- **Services déployés** :
  - [x] Nginx (reverse proxy)
  - [x] HTTPS via Certbot (certificats Let's Encrypt, renouvellement automatique)
  - [x] Socle Docker + Portainer, avec sauvegarde des volumes
  - [x] Publication de pages Markdown en HTML statique (pandoc)
  - [ ] GitLab CE (hébergement de code)
  - [ ] Serveur mail (type Mailu ou Poste.io)
  - [ ] Moteur de blog Ghost
  - [ ] Outils annexes (gestionnaire de documents, etc.)

---

## 🍓 La configuration choisie est la suivante :

| Composant                       | Modèle / Détail                                 | Quantité | Prix estimé        |
|---------------------------------|-------------------------------------------------|----------|--------------------|
| Raspberry Pi                    | Raspberry Pi 4 - 8 Go RAM                       | 1        | [85 €][kubii]      |
| Boîtier                         | DeskPi Pro V2 (avec ventilation + support SSD)  | 1        | [70 €][deskpi.com] | 
| Carte microSD (optionnelle)     | SanDisk / Samsung - 32 Go ou 64 Go (classe 10)  | 1        | ~15 €              |
| Disque dur externe (sauvegarde) | Seagate Expansion 1 To (USB)                    | 1        | ~50 €              |
| SSD interne                     | Samsung 870 EVO - 1 To (SATA)                   | 1        | ~90 €              |

**Total estimé : ~300 €**

---

## 🛠️ Mise en place (en local avec Vagrant)

```bash
git clone https://github.com/ShamLucas/HelloCyberWorld
cd HelloCyberWorld
vagrant up         # Démarre la VM et la provisionne avec Ansible
```

---

[Pour la configuration de vagrant et ansible, c'est ici](doc/01.ServerTest-VagrantAnsible.md)


## 🌍 Tester le projet en ligne (staging)

Une fois le déploiement validé localement, les mêmes rôles Ansible seront utilisés pour :

- déployer sur un VPS (ou un Raspberry Pi connecté en IP publique)
- tester depuis le sous-domaine de staging

---

## 🚀 Déploiement final (Raspberry Pi)

Les cibles sont décrites dans `ansible/inventory.ini`, et leurs variables
(domaines, certificats, services) dans `ansible/group_vars/`.

---

## ✨ Pourquoi ce projet ?

Ce projet me permet de :
- me remettre à jour sur Linux, le devops, et le déploiement
- construire une stack perso réutilisable
- documenter un projet pédagogique et open-source


[kubii.com]: https://www.kubii.com/fr/cartes-nano-ordinateurs/2955-raspberry-pi-4-modele-b-8gb-5056561800356.html?src=raspberrypi
[deskpi.com]: https://deskpi.com/products/deskpi-pro-for-raspberry-pi-4