Author: Abdel-had HANAMI

Context: Bootcamp DevOps Training, 12th promotion

Training Center: eazytraining.fr

Date: October 10, 2023

LinkedIn: [https://www.linkedin.com/in/abdel-had-hanami/](https://www.linkedin.com/in/abdel-had-hanami/)

Here is my [training repository](https://github.com/Abdel-had/ansible-training)

And here is the [deployment environment](https://github.com/Abdel-had/mini-projet-ansible-role-containerized-apache) for my mini-project

------------

![Mini-project-ansible](https://github.com/Abdel-had/ansible-role-containerized-apache/assets/101605739/f5a62325-778f-46db-abd3-ee1ba8c4e1c3)

# README.md for the Ansible Role `ansible-role-containerized-apache`

## Overview

The `ansible-role-containerized-apache` role is designed to deploy an Apache server in a Docker container on CentOS-based hosts. This role ensures that the necessary prerequisites such as Python and Docker are installed and properly configured before deploying the Apache container.

## Role Structure

```plaintext
ansible-role-containerized-apache/
├── defaults/        # Default values for the role variables
│   └── main.yml
├── meta/            # Role metadata, including dependencies
│   └── main.yml
├── tasks/           # Tasks of the role
│   ├── install-docker.yml
│   ├── install-python.yml
│   └── main.yml
├── templates/       # Templates used by this role
│   └── index.html.j2
├── tests/           # Tests for the role
│   ├── inventory
│   └── test.yml
└── vars/            # Other variables for the role
    └── main.yml
```

## Variables

The variables used in this role are defined in the files `defaults/main.yml` and `vars/main.yml`. Here are some key variables:

- `home_page_message`: Message to be displayed on the homepage of the Apache server.
- `system_user`: System user under which the Docker container will be executed.
- `docker_container_name`: Name of the Docker container.
- `external_port` and `apache_port`: Ports for accessing the Apache server.
- `home_page_file_name`: Name of the homepage file.
- `domain`: Domain or IP address of the host.
- `python_version`: Version of Python to install.

## Dependencies

This role depends on the following Ansible modules:

- `pip`
- `ansible.builtin.yum`
- `ansible.builtin.yum_repository`
- `ansible.builtin.systemd`
- `docker_container`

## Dependencies Installation

The tasks to install Docker and Python are included in the files `tasks/install-docker.yml` and `tasks/install-python.yml`, respectively.

## Apache Server Deployment

The deployment of the Apache server is managed by the tasks defined in `tasks/main.yml`. These tasks:

- Import the tasks for Docker and Python installation.
- Copy the homepage template to the target host.
- Create and start a Docker container for the Apache server.
- Wait for the Docker container to be operational and the website to be accessible.

## Tests

The tests for this role are defined in `tests/test.yml`, with a test inventory specified in `tests/inventory`.

## Usage

To use this role, include it in your playbook and specify the necessary variables to configure your Apache server and Docker according to your needs.

A [deployment environment](https://github.com/Abdel-had/mini-projet-ansible-role-containerized-apache) is provided for this purpose.

```yaml
- hosts: your_hosts
  roles:
    - ansible-role-containerized-apache
```

You can also run the included tests to validate the functionality of this role in your environment.
