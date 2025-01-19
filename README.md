# Ansible Playbook: Install and Start Nginx

This repository contains an Ansible playbook to automate the installation and startup of the Nginx web server on remote servers.

## Overview

An Ansible playbook is a set of instructions that Ansible executes on authenticated servers. This playbook performs the following actions:
1. Updates the package index on the remote servers.
2. Installs the latest version of Nginx.
3. Starts the Nginx service and enables it to start on system boot.

---

## Prerequisites

### 1. Install Ansible
Ensure Ansible is installed on your local machine:
```sh
sudo apt update
sudo apt install ansible -y
```

### 2. Configure the Inventory File
Add the target servers to your Ansible inventory file, located at /etc/ansible/hosts. Below is an example configuration:
```sh
[servers]
server_1 ansible_host=<server_1_public_ip>
server_2 ansible_host=<server_2_public_ip>

[servers:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_user=ubuntu
ansible_ssh_private_key_file=<path_to_private_key>
```

### 3. Ensure SSH Access
Configure passwordless SSH access from your local machine to the target servers using the private key specified in the inventory file.

## Ansible Commands

Test Connectivity: Before running the playbook, verify connectivity to the target servers:
ansible servers -m ping

Check memory usage on target servers:
ansible servers -a "free -h"

List inventory details:
ansible-inventory --list

Run the Playbook
Execute the playbook to install and start Nginx on the target servers:
ansible-playbook install_nginx_playbook.yml
