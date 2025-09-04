# Ansible Project: Server Hardening

This Ansible project automates system hardening tasks such as:
- SSH configuration enforcement
- Password and account policy setup
- Sensitive file permission management

### Structure

- `roles/ssh_hardening`: Secures SSH configuration
- `roles/password_policy`: Enforces account security
- `roles/file_permissions`: Secures critical system file permissions
- `inventory/hosts`: Inventory definition
- `group_vars/all.yml`: Global variables
- `playbooks/hardening.yml`: Main playbook to run all roles

### How to Run

```bash
ansible-playbook -i inventory/hosts playbooks/hardening.yml
```
