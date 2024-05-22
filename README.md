# Ansible Proxy Server

This project is designed to configure a [dumbproxy](https://github.com/senseunit/dumbproxy) on a server using Ansible.


## How to run the playbook?

### 1. Install ansible
Look ["Installing Ansible"](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) for more details (Ansible official documentation)


### 2. Install playbook dependencies
```bash
ansible-galaxy role install -r requirements.yml
```

### 3. Change inventory.ini file
In this file you should put your server IP (`ansible_host`)
```
[server]
SERVER_NAME ansible_host=255.255.255.255 ansible_user=root
```

### 4. Change variables in group_vars/server
This is credentials you will use to connect to your proxy server
```
---
# This is example values
dumbproxy_user: admin
dumbproxy_password: 12345
dumbproxy_port: 8080
```

The URL for working proxy will be `http://admin:12345@255.255.255.255:8080`

### 5. Run playbook
```
ansible-playbook playbook.yml -i inventory.ini -K
```
