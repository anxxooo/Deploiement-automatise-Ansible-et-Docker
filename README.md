# Déploiement automatisé MySQL avec Ansible et Docker

## Table des matières

1. [Présentation](#présentation)
2. [Objectif du projet](#objectif-du-projet)
3. [Prérequis](#prérequis)
4. [Architecture](#architecture)
5. [Préparation des machines](#préparation-des-machines)
6. [Échange de clés SSH](#échange-de-clés-ssh)
7. [Configuration de l’inventaire Ansible](#configuration-de-linventaire-ansible)
8. [Playbook Ansible](#playbook-ansible)
9. [Exécution du playbook](#exécution-du-playbook)
10. [Vérifications et tests](#vérifications-et-tests)
11. [Idempotence et bonnes pratiques](#idempotence-et-bonnes-pratiques)
12. [Captures d’écran](#captures-décran)
13. [Conclusion](#conclusion)

---

## Présentation

Ce projet illustre le déploiement automatisé d’un service MySQL sur une machine distante à partir d’une machine de contrôle utilisant Ansible et Docker.

> Technologies utilisées :

- **Ansible** pour l’automatisation  
- **Docker** pour les conteneurs  
- **MySQL 8** comme service déployé  
- **RHEL 9** comme Control Node  
- **Kali Linux** comme Managed Node  
---

## Objectif du projet

* Automatiser le déploiement d’un conteneur MySQL sur une VM distante
* Rendre le service accessible via le réseau

---

## Prérequis

* Une machine de contrôle avec Ansible installé
* Une machine cible avec Docker installé ou installation via Ansible
* Accès SSH entre les deux machines

---

## Architecture

```
Control Node (Ansible)  ---- SSH ---->  Managed Node (Docker)
                                           |
                                           v
                                     Conteneur MySQL
```

---

## Préparation des machines

Configurer les machines avec les outils nécessaires pour Ansible et Docker.

---

## Échange de clés SSH

Mettre en place une connexion SSH sans mot de passe entre la machine de contrôle et la machine cible pour permettre à Ansible d’agir automatiquement.

> **Connexion SSH fonctionnelle :**
<img width="1311" height="326" alt="image" src="https://github.com/user-attachments/assets/78aba3d1-f7ed-4fa6-ade3-5b72ad023650" />

---

## Configuration de l’inventaire Ansible

Préparer un fichier d’inventaire listant la machine cible et les paramètres de connexion nécessaires.

---

## Playbook Ansible

Créer un playbook qui vérifie l'installation de Docker et déploie le conteneur MySQL sur la VM cible.

> Le playbook gère l’état du service et du conteneur de manière idempotente.

---

## Exécution du playbook

Exécuter le playbook depuis la machine de contrôle pour automatiser le déploiement sur la VM cible.
<img width="1890" height="556" alt="image" src="https://github.com/user-attachments/assets/d2627cfa-0711-4439-81a4-ffea2343a3c9" />


---

## Vérifications et tests

* Vérifier que le conteneur MySQL est actif et accessible
<img width="1892" height="152" alt="image" src="https://github.com/user-attachments/assets/a42d6bc7-dc5d-447a-82bd-3908046b8791" />


* Tester la connexion au service depuis le réseau ou la machine de contrôle
<img width="1892" height="421" alt="image" src="https://github.com/user-attachments/assets/27f90710-d82b-422a-9182-ae3e9b787aa2" />

---

## Idempotence et bonnes pratiques

* Le playbook peut être relancé sans modifier l’état si tout est déjà en place
* Séparation claire entre la machine de contrôle et la machine cible

---

## Captures d’écran

* Connexion SSH fonctionnelle
* Sortie du playbook
* Conteneurs actifs
* Accès au service MySQL

---

## Conclusion

Ce projet démontre :

* L’automatisation du déploiement d’un service critique sur une VM distante
* La maîtrise de Docker et Ansible dans un environnement multi-OS


