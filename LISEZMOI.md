Auteur : Abdel-had HANAMI

Contexte : Formation Bootcamp DevOps, 12ème promotion

Centre de formation : eazytraining.fr

Date : 10 octobre 2023

LinkedIn : [https://www.linkedin.com/in/abdel-had-hanami/](https://www.linkedin.com/in/abdel-had-hanami/)

Voici mon [dépôt de formation](https://github.com/Abdel-had/ansible-training)

Et voici l'[environnement de déploiement](https://github.com/Abdel-had/mini-projet-ansible-role-containerized-apache) de mon mini-projet

------------

![Mini-projet-ansible](https://github.com/Abdel-had/ansible-role-containerized-apache/assets/101605739/f5a62325-778f-46db-abd3-ee1ba8c4e1c3)

# README.md pour le rôle Ansible `ansible-role-containerized-apache`

## Présentation

Le rôle `ansible-role-containerized-apache` est conçu pour déployer un serveur Apache dans un conteneur Docker sur des hôtes basés sur CentOS. Ce rôle assure que les prérequis nécessaires comme Python et Docker soient installés et correctement configurés avant de déployer le conteneur Apache.

## Structure du Rôle

```plaintext
ansible-role-containerized-apache/
├── defaults/        # Valeurs par défaut pour les variables du rôle
│   └── main.yml
├── meta/            # Métadonnées du rôle, y compris les dépendances
│   └── main.yml
├── tasks/           # Tâches du rôle
│   ├── install-docker.yml
│   ├── install-python.yml
│   └── main.yml
├── templates/       # Modèles utilisés par ce rôle
│   └── index.html.j2
├── tests/           # Tests pour le rôle
│   ├── inventory
│   └── test.yml
└── vars/            # Autres variables pour le rôle
    └── main.yml
```

## Variables

Les variables utilisées dans ce rôle sont définies dans les fichiers `defaults/main.yml` et `vars/main.yml`. Voici quelques variables clés :

- `home_page_message`: Message à afficher sur la page d'accueil du serveur Apache.
- `system_user`: Utilisateur système sous lequel le conteneur Docker sera exécuté.
- `docker_container_name`: Nom du conteneur Docker.
- `external_port` et `apache_port`: Ports pour l'accès au serveur Apache.
- `home_page_file_name`: Nom du fichier de la page d'accueil.
- `domain`: Domaine ou adresse IP de l'hôte.
- `python_version`: Version de Python à installer.

## Dépendances

Ce rôle dépend des modules Ansible suivants :

- `pip`
- `ansible.builtin.yum`
- `ansible.builtin.yum_repository`
- `ansible.builtin.systemd`
- `docker_container`

## Installation des Dépendances

Les tâches pour installer Docker et Python sont incluses dans les fichiers `tasks/install-docker.yml` et `tasks/install-python.yml`, respectivement.

## Déploiement du Serveur Apache

Le déploiement du serveur Apache est géré par les tâches définies dans `tasks/main.yml`. Ces tâches :

- Importent les tâches d'installation de Docker et de Python.
- Copient le modèle de page d'accueil sur l'hôte cible.
- Créent et démarrent un conteneur Docker pour le serveur Apache.
- Attendre que le conteneur Docker soit opérationnel et que le site Web soit accessible.

## Tests

Les tests pour ce rôle sont définis dans `tests/test.yml`, avec un inventaire de test spécifié dans `tests/inventory`.

## Utilisation

Pour utiliser ce rôle, incluez-le dans votre playbook et spécifiez les variables nécessaires pour configurer votre serveur Apache et Docker selon vos besoins.

Un [environnement de déploiement](https://github.com/Abdel-had/mini-projet-ansible-role-containerized-apache) est prévu à cet effet.

```yaml
- hosts: your_hosts
  roles:
    - ansible-role-containerized-apache
```

Vous pouvez également exécuter les tests inclus pour valider la fonctionnalité de ce rôle sur votre environnement.
