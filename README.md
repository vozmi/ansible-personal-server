# How to run the playbook?

## 1. Install ansible 
Look ["Installing Ansible"](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) for more details (Ansible official documentation)


## 2. Install playbook dependencies
```bash
ansible-galaxy role install -r requirements.yml
```

## 3. Create local inventory file
Copy `inventory.ini.example` to `local-inventory.ini`, so you can safely modify it.

## 4. Create encrypted vars file
Remove my personal vault
```
rm group_vars/server
```

Create your own vault (example variables are located at `group_vars/server.example`)
```
ansible-vault create --vault-id @prompt ./group_vars/server
```

## 4. Run playbook
```
ansible-playbook playbook.yml -i local-inventory.ini --ask-vault-pass
```

---
## Debugging
You can save your vault password in file, so you won't need to enter it every time:
- save vault password in `vault-pass.local` file
- run playbook with `--vault-password-file=vault-pass.local` instead of `--ask-vault-pass`