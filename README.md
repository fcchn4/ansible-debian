# Ansible Install Linux

This repository contains a list of packages for Fedora, Debian, and Ubuntu distributions. It only contains a long list of packages for some GNU/Linux distributions.

## List

- [Debian Packages](debian-software.md)

## Debian 10

## Packages Extra no Included

- [zoom](https://zoom.us/download#client_4meeting)
- [slack](https://slack.com/intl/en-bo/downloads/linux)
- [brave](https://brave.com/download/)
- [aws](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html#cliv2-linux-install)
- [awless](https://github.com/wallix/awless/releases)
- [helm](https://helm.sh/docs/intro/install/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
- [terraform](https://www.terraform.io/downloads.html)
- [packer](https://learn.hashicorp.com/tutorials/packer/get-started-install-cli)
- [assume-role](https://github.com/remind101/assume-role)
- [ulauncher](https://ulauncher.io/#Download)
- [hugo](https://github.com/gohugoio/hugo/releases)
- [docker-compose](https://github.com/docker/compose/releases)

## List of Repositories

### Debian

- Debian Official
- DEB Multimedia
- MariaDB
- VirtualBox
- Docker CE
- Typora
- VSCode
- NodeJS
- Yarn
- Postgresql

## Pre-Requisites

First we must manually execute the following commands on the computer where the installation will take place:

```bash
$ su -c "vim.tiny /etc/group"       # Add user name in sudo group: "sudo:x:27:user_name"
$ su -c "systemctl enable --now sshd.service"
```

Then we must copy a public SSH key on the computer where the installations will be executed:

```bash
$ ssh-copy-id -o PubkeyAuthentication=no -i ~/.ssh/demo-ssh.pub user_name@ip_address_or_localhost
```

This ansible poroject is for automatic install on post-installation for Debian Operating System.

## Config Files and replace values

The project have three playbooks:

- debian-base-repos.yml
- debian-desktop.yml
- debian-security.yml

## Versions

- XFCE: 4.12.0
- Debian: 10 Buster
- Ansible: 2.9

## Commands

First we are located on the route:

```bash
$ cd ansible-debian
```

Execution order:

1. **debian-base-repos.yml**:

```bash
$ ansible-playbook debian-base-repos.yml \
--ask-become-pass \
-i inventory/inventory.yml
```

2. **debian-desktop.yml**:

```bash
$ ansible-playbook debian-desktop.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```

3. **debian-security.yml**:

```bash
$ ansible-playbook debian-security.yml \
--ask-become-pass \
-i inventory/inventory.yml \
-e "ansible_python_interpreter=/usr/bin/python3"
```
