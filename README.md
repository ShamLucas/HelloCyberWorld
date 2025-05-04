# 🛠️ Projet Hellocyberworld Labs

## 🧠 Objectif du projet

Créer un environnement de développement auto-hébergé pour expérimenter l’administration système, le dev web et le déploiement d’applications. 

## 🍓 La configuration choisie est la suivante :

| Composant                       | Modèle / Détail                                 | Quantité | Prix estimé |
|---------------------------------|-------------------------------------------------|----------|--------------|
| Raspberry Pi                    | Raspberry Pi 4 - 8 Go RAM                       | 1        | ~85 €        |
| Boîtier                         | DeskPi Pro V2 (avec ventilation + support SSD)  | 1        | ~70 €        |
| SSD interne                     | Samsung 870 EVO - 1 To (SATA)                   | 1        | ~90 €        |
| Disque dur externe (sauvegarde) | Seagate Expansion 1 To (USB)                    | 1        | ~50 €        |
| Carte microSD (optionnelle)     | SanDisk / Samsung - 32 Go ou 64 Go (classe 10)  | 1        | ~15 €        |

**Total estimé : ~310 € (hors promotions ou bons d'achat)**

Ce projet s’appuie sur un **workflow reproductible** :  
- développement local dans une VM (via **Vagrant + Ansible**),  
- staging sur un sous-domaine public (`test.hellocyberworld.com`),  
- déploiement final sur un Raspberry Pi auto-hébergé.

---

## 🏗️ Architecture & Stack technique

```
+---------------------+
|    Poste local      |
|---------------------|
| VM Vagrant + Ansible| <-- provisionnée automatiquement
| Ubuntu Server       |
| Nginx, GitLab, etc. |
+---------------------+

          |
          | Test via DNS public (test.hellocyberworld.com)
          v

+---------------------+
|  Raspberry Pi       | <-- cible finale
| Ubuntu, Docker, etc |
+---------------------+
```

---

## ⚙️ Stack technique

- **Provisioning & Infra** :
  - [Vagrant](https://www.vagrantup.com/) pour gérer l’environnement de dev local
  - [Ansible](https://www.ansible.com/) pour la configuration automatique des services
- **Services à tester** :
  - Nginx (reverse proxy)
  - GitLab CE (hébergement de code)
  - Serveur mail (type Mailu ou Poste.io)
  - Moteur de blog (Hugo, Ghost…)
  - Outils annexes (gestionnaire de documents, etc.)
- **Nom de domaine** : `hellocyberworld.com`
  - Sous-domaine de staging : `test.hellocyberworld.com`
  - DNS gérés via OVH

---

## 🛠️ Mise en place (en local avec Vagrant)

```bash
git clone https://monrepo.git
cd monrepo
vagrant up         # Démarre la VM et la provisionne avec Ansible
```

---

## 🌍 Tester le projet en ligne (staging)

Une fois le déploiement validé localement, les mêmes rôles Ansible seront utilisés pour :

- déployer sur un VPS (ou ton Pi connecté en IP publique)
- tester depuis `test.hellocyberworld.com`

---

## 🚀 Déploiement final (Raspberry Pi)

Tu trouveras dans `ansible/inventory/raspberry` la configuration dédiée à la cible Raspberry Pi.

---

## 📝 TODO / Feuille de route

- [ ] Écrire les playbooks Ansible de base
- [ ] Configurer le DNS OVH pour staging
- [ ] Déployer GitLab dans la VM
- [ ] Documenter les rôles Ansible
- [ ] Ajouter le moteur de blog
- [ ] Sauvegarde et monitoring (à venir)

---

## ✨ Pourquoi ce projet ?

Ce projet me permet de :
- me remettre à jour sur Linux, le devops, et le déploiement
- construire une stack perso réutilisable
- documenter un projet pédagogique et open-source
