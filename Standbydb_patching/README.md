# 🛠️ Oracle Standby Database Patching with Ansible

![Ansible](https://img.shields.io/badge/Automation-Ansible-2088FF?style=flat&logo=ansible)
![Oracle](https://img.shields.io/badge/Oracle-19c-red?style=flat&logo=oracle)

This Ansible playbook automates the process of patching an Oracle **19c Standby Database**. It handles everything from shutting down managed recovery to applying the patch and restarting services—reducing manual errors and ensuring consistency across environments.

---

## 📂 Project Structure

```
apply_oracle_patch_standby.yml     # Main playbook
README.md                          # Project documentation
```

---

## ✅ Features

- Verifies database and managed recovery status
- Stops listener and cancels recovery
- Backs up and replaces the OPatch utility
- Unzips and applies Oracle database patches
- Restarts standby database and resumes recovery

---

## ⚙️ Requirements

- Oracle 19c installed on standby host(s)
- Ansible 2.9+ installed on control node
- SSH access to the target standby database server
- Oracle patch ZIP files downloaded and available locally

---

## 🔧 Variables

You can customize these variables by editing the playbook or overriding them at runtime:

```yaml
oracle_home: /opt/oracle/product/19.3.0/db_1
local_patch_dir: /tmp
patch_dir: /oraback/patch
patch_db_zip: p37642901_190000_Linux-x86-64.zip
patch_opatch_zip: p6880880_190000_Linux-x86-64.zip
```

---

## 🚀 Usage

Run the playbook with:

```bash
ansible-playbook apply_oracle_patch_standby.yml -e "hostlist=db_standby"
```

Replace `db_standby` with your target standby server or inventory group.

---

## 🗃️ Inventory Example

```ini
[db_standby]
standby1 ansible_host=192.168.1.100 ansible_user=ansible
```

---

## 📌 Important Notes

- Patch files must be pre-downloaded and placed under `/tmp` (or your defined `local_patch_dir`).
- This playbook assumes the Oracle software owner is `oracle` and the group is `oinstall`.
- Make sure the `oracle` user’s `.bash_profile` is correctly configured.
- Only tested on Linux-based Oracle 19c installations (e.g., RHEL, Oracle Linux).

---

## 🧪 Patch Status Verification

This playbook includes:

- Oracle patch conflict check (`opatch prereq`)
- OPatch version validation
- Oracle inventory check (`opatch lsinventory`)
- Post-patch log history to confirm sync

---

## 📤 Contributing

Feel free to fork the repository, improve the logic, and submit pull requests. Suggestions and enhancements are welcome!

---

## 👨‍💻 Maintainer

**Saravanan Mahalingam**  
📧 saravananlokesh2@gmail.com
🌐 https://dbanavigator.blogspot.com/ 
