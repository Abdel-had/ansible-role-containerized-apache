
Author: Abdel-had HANAMI

Context: Bootcamp DevOps training, 12th promotion

Training center: eazytraining.fr

Release date: 10th of October, 2023

LinkedIn : https://www.linkedin.com/in/abdel-had-hanami/

Here is my [training repo](https://github.com/Abdel-had/ansible-training)

------------

Ansible Role: Containerized apache
=========

This Ansible playbook will Deploy & run Docker project for apache instance. It only need one container running:

* apache

This role was created as part of a EazyTraining DevOps Bootcamp 12's [mini-project](https://github.com/Abdel-had/mini-projet-ansible-role-containerized-apache)
The goal is to install an apache container with a volume bind mount which permits to deploy a website.

Requirements
------------

For this role to work, it is required to have Docker and Python installed and setup. If you haven't done this already (manually), then the role will handle it : [ansible-role-containerized-apache](https://github.com/Abdel-had/ansible-role-containerized-apache)

Role Variables
--------------

This role comes with following variables defined in defaults/main.yml:

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

If role is ran without changing these, apache instance settings will be setup with these values. 


Example Playbook
----------------

```
- hosts: servers
  remote_user: "{{ system_user }}"
  roles:
    - {{ role: ansible-role-containerized-apache }}  
```
