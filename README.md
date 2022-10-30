[![CI](https://github.com/slydien/ansible-docker-media-stack/actions/workflows/ci.yml/badge.svg)](https://github.com/slydien/ansible-docker-media-stack/actions/workflows/ci.yml)

# General info

This will setup Docker with various media automation containers (Sonarr, Radarr, Prowlarr..) on a Debian or RedHat server.

# Technologies

Project created with:
* Ansible version: 2.12.1
* Molecule version: 3.5.2
* Podman version: 3.2.1
* Molecule podman version: 1.0.1
* Docker version: 20.10.12

# TODO

* Find solution for labels if traefik container is disabled
* Add *geerlingguy.security* role from Ansible galaxy
* Write ansible role for Crowdsec, a great replacement for fail2ban
* Add *no_log* parameter to tasks with sensitive informations

# Setup
## Requirements

You need to install ansible before you can run this project. It's best to get the latest version of Ansible using pip. Install pip by following instructions at: https://pip.pypa.io/en/stable/cli/pip_install/

and then type this command into a terminal:

``` sh
pip install ansible
```

## Usage

First clone the repository:

``` sh
git clone https://github.com/zedxlucian/ansible-docker-media-stack.git
cd ansible-docker-media-stack

```

Now, you need to fill some variables before you can run this project. Open the file *group_vars/all* and change the values in the variable according to your needs. Now open the file *group_vars/all* and change the values.

:warning: If you plan on pushing this into a github repository make sure to follow the next step.

You need to encrypt *group_vars/all* because it contains sensitive informations. To do so, type this command:

``` sh
ansible-vault encrypt group_vars/secret.yml
```

We can finally launch our ansible playbook to install our docker media stack:

``` sh
ansible-playbook -i hosts/<your-host-ip-address> playbook.yml --ask-vault-pass
```

If you encrypted your *group_vars/all* file Ansible will ask you to provide the password. Once entered, it will proceed with the playbook.
