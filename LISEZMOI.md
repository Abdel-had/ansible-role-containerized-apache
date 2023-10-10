Auteur : Abdel-had HANAMI

Contexte : Formation Bootcamp DevOps, 12ème promotion

Centre de formation : eazytraining.fr

Date de sortie : 10 octobre 2023

LinkedIn : [https://www.linkedin.com/in/abdel-had-hanami/](https://www.linkedin.com/in/abdel-had-hanami/)

Voici mon [dépôt de formation](https://github.com/Abdel-had/ansible-training)

------------

![Mini-projet-ansible](https://github.com/Abdel-had/ansible-role-containerized-apache/assets/101605739/f5a62325-778f-46db-abd3-ee1ba8c4e1c3)

Rôle Ansible : Apache conteneurisé
=========

Ce playbook Ansible permet de déployer et d'exécuter un projet Docker pour une instance apache. Il ne nécessite qu'un seul conteneur en cours d'exécution :

* apache

Ce rôle a été créé dans le cadre d'un [mini-projet](https://github.com/Abdel-had/mini-projet-ansible-role-containerized-apache) du Bootcamp DevOps EazyTraining 12. L'objectif est d'installer un conteneur apache avec un montage de volume qui permet de déployer un site web.

Exigences
------------

Pour que ce rôle fonctionne, il est nécessaire d'avoir Docker et Python installés et configurés. Si vous ne l'avez pas déjà fait (manuellement), alors ce rôle s'en chargera : [ansible-role-containerized-apache](https://github.com/Abdel-had/ansible-role-containerized-apache)

Variables du Rôle
--------------

Ce rôle est livré avec les variables suivantes définies dans defaults/main.yml :

```
system_user: vagrant
home_page_message: Bienvenue sur {{ ansible_hostname }}
docker_container_name: webapp
external_port: 80
apache_port: 80
home_page_file_name: index.html
domain: localhost
python_version: 2.7
```

Si le rôle est exécuté sans changer ces variables, les paramètres de l'instance apache seront configurés avec ces valeurs.

Exemple de Playbook
----------------

```
- hosts: servers
  system_user: root
  roles:
    - {{ role: ansible-role-containerized-apache }}  
```
