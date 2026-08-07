# HelloCyberWorld

Homelab auto-hébergé : administration système, déploiement de services, et
modèle de projet type « scripter l'installation d'un serveur, tester en VM,
déployer en production ».

## État actuel de la stack

- **Machine de production** : HP Envy sous Debian (le README, historique,
  décrit l'époque Raspberry Pi — il est à mettre à jour).
- **Conteneurs** : Docker, gérés via Portainer.
- **Provisioning** : Ansible (`ansible/`), Vagrant pour les tests en VM
  locale (`VagrantFile`).
- **Domaine** : `hellocyberworld.com` (DNS OVH), staging sur
  `test.hellocyberworld.com`.

## Structure

- `ansible/` — rôles et inventaires (VM de test et cible production).
- `doc/` — documentation par étapes, format `NN.Sujet.md`.
- `data/` — données locales, non versionnées.

## Conventions

- Repo **public** : jamais de secret, de clé, de mot de passe ni de donnée
  personnelle dans un fichier commité. Les secrets vivent dans le keepass
  local (gitignoré) et les variables Ansible chiffrées.
- Documentation des installations dans `doc/`, une étape par fichier.
- Directives de session personnelles : `CLAUDE.local.md` (gitignoré).
