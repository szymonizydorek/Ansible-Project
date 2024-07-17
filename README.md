![Description](https://github.com/szymonizydorek/Ansible-Project/blob/main/Screenshot%202024-07-17%20at%2020.19.03.png)


# Linux Servers Automation with Ansible

In the project, we will look over the most important Ansible functionalities to provision services, users, ssh authentication to three Linux servers. 

## Prerequisities 

- ControlMachine - Linux server with Ansible Installed
- WebServer_1 - Ubuntu 20.04 Server
- WebServer_2 - CentOS
- DbDerver - CentOS
- Ansible Documentation: [Ansible Documentation](https://www.ansible.com/])

## Installation and Cofiguration

1. Install Ansible on your Control Machine
   Firstly, we need to install Ansible on Control Machine (mine is using Ubuntu "22.04.4 LTS (Jammy Jellyfish)")
   To install Ansible go to:
   [Ansible Installation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

2. Verify the installation

   ```sh
    ubuntu@ip-172-31-16-122:~$ ansible --version
   ```
    The output:
     ```sh
     ansible [core 2.16.8]
     ```
3. Configure ansible.cfg
   
###  ansible.cfg:
```
[defaults]
host_key_checking=False
inventory = ./inventory/inventory
forks = 5
log_path=/var/log/ansible/ansible.log

[privlage_escalation]
become=True
become_method=sudo
become_ask_pass=False
```

4. Define your inventory:

###  inventory:

```all:
  hosts:
    web01:
      ansible_host: 172.31.91.30
    web02:
      ansible_host: 172.31.43.15
      ansible_user: ubuntu
    db01:
      ansible_host: 172.31.83.226
```
