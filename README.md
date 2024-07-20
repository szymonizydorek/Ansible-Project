![Ansible Logo](file/pics/ansible.logo)
# Linux Servers Automation with Ansible

In this project, we will explore the most important Ansible functionalities to provision services, manage users, and configure SSH authentication across three Linux servers.
## Prerequisities 
- **Control Machine**: A Linux server with Ansible installed.
- **Web Server 1**: Ubuntu 20.04 Server.
- **Web Server 2**: CentOS.
- **Database Server**: CentOS.
- **Ansible Documentation**: [Ansible Documentation](https://www.ansible.com/)


## Project Requirements

- Install HTTP service.
- Install MariaDB service.
- Create admin users.
- Configure NTP server in the Europe pool.
- Configure Chrony service in the CN pool.
- Restart NTP service whenever there is a change in the configuration.

## Steps

1. **Setting Up the Control Machine**:
    - Ensure Ansible is installed on the control machine.
    - Verify SSH access to all target servers from the control machine.

2. **Inventory Setup**:
    - Define the inventory file with details of the target servers.

3. **Playbook Creation**:
    - Create playbooks for each task:
        - Installing HTTP and MariaDB services.
        - Creating admin users.
        - Configuring NTP and Chrony.
        - Ensuring services are restarted after configuration changes.

4. **Variables and Templates**:
    - Define variables in `group_vars/all`.
    - Create Jinja2 templates for configuration files.

5. **Executing Playbooks**:
    - Run the playbooks from the control machine.
    - Verify the changes on the target servers.


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
