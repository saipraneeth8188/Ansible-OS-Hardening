# 🛡️ Ansible OS Hardening Project

A production-grade Ansible automation project to **harden Linux servers** based on **real-world Root Cause Analysis (RCA)** scenarios. This project helps enforce security policies, apply system-level hardening, and configure critical services using idempotent Ansible playbooks and roles.

---

## 📌 Use Case

In many production environments, system outages are traced back to **unhardened OS settings**, insecure SSH configurations, or missing monitoring agents. This project automates remediation for common issues such as:

- SSH brute force attacks
- Unrestricted user logins
- Missing memory/file descriptor limits
- Absence of auditing or logging tools (fail2ban, auditd)
- PAM configuration vulnerabilities

This project was designed to **prevent such RCA incidents from recurring**, making your Linux servers **compliant, secure, and production-ready**.

---

## ⚙️ What This Project Does

| Feature Area                     | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| 🔐 SSH Hardening                | Enforces key-only login, disables root login, limits sessions              |
| 👥 PAM & Limits Configuration  | Sets file descriptor limits, login control, session policies               |
| 📈 Monitoring Setup             | Installs fail2ban, sets up basic audit rules for suspicious activities     |
| 🔒 Security Patches            | Ensures systems are patched using `yum` or `apt`                           |
| 🛠️ Common Tools                | Installs tools like `tree`, `net-tools`, `curl`, `vim`, `htop`             |
| ✅ Validations                  | Uses `ansible_facts` to validate and log system state before enforcement   |

---

## 📂 Project Structure


ansible-OS-Hardening/
├── inventory/
│   └── hosts.yml
├── playbooks/
│   ├── 01-ssh-hardening.yml
│   ├── 02-pam-limits.yml
│   ├── 03-monitoring-tools.yml
│   └── site.yml
├── roles/
│   ├── ssh/
│   ├── pam/
│   ├── monitoring/
│   └── common/
├── group_vars/
│   └── all.yml
└── README.md


---

## 🚀 Getting Started

### 1️⃣ Clone the repository

git clone https://github.com/saipraneeth8188/Ansible-OS-Hardening.git
cd Ansible-OS-Hardening


### 2️⃣ Update Inventory File

# inventory/hosts.yml
all:
  hosts:
    server1:
      ansible_host: 192.168.1.10
      ansible_user: ec2-user


### 3️⃣ Run the Playbook

ansible-playbook -i inventory/hosts.yml playbooks/site.yml


---

## 📘 Reference: Root Cause Scenarios Addressed

- 🐛 RCA-001: Brute-force SSH attacks → Resolved via fail2ban & SSH config
- 🐛 RCA-002: PAM login failures & session lockouts → Set up `pam_limits` and alerting
- 🐛 RCA-003: High memory usage → Enforced process limits
- 🐛 RCA-004: Missing monitoring tools → Installed fail2ban, auditd
- 🐛 RCA-005: Log tampering → Enabled immutable audit rules

---

## 📦 Prerequisites

- Ansible ≥ 2.9
- Python installed on control node
- SSH access to managed nodes
- Sudo privileges on target hosts

---

## 🤝 Contributing

Want to add a role for AppArmor, firewalld, or logging to ELK? Feel free to fork and raise a PR!

---

## 🧠 Author

Built by [Sai Praneeth](https://github.com/saipraneeth8188), based on handwritten RHCE-level Ansible notes and real-world troubleshooting scenarios.

---

## 📄 License

MIT License
