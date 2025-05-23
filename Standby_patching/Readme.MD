# 🚀 Oracle OPatch & Patch Automation with Ansible

This Ansible playbook automates the process of applying Oracle RDBMS patches using `OPatch` across multiple Oracle homes. It supports:

* OPatch update automation 🛠️
* Patch zip deployment and conflict checks 🔍
* Database shutdown/startup and listener control 🔄
* Safe rollback with backup of existing `OPatch` folder 📂
* `datapatch` execution for SQL patch finalization 🧹

---

## 📁 Files

* `oracle_patch.yml`: Main playbook for patching Oracle homes.

---

## 📌 Features

✅ Ensures Oracle user and home directories
✅ Handles OPatch zip backup and extraction
✅ Dynamically detects Oracle SIDs from PMON
✅ Shuts down databases and listeners gracefully
✅ Applies patches silently with retries
✅ Starts database and listeners
✅ Applies post-patch SQL changes with `datapatch`
✅ Validates final patch state with `opatch lspatches`

---

## 🧰 Prerequisites

* Oracle Database 19c installed
* Ansible 2.9+
* SSH access and passwordless sudo for the `oracle` user
* Patch and OPatch zip files downloaded from [Oracle Support](https://support.oracle.com/)

---

## 📦 Variables

Set the following variables inside `oracle_patch.yml`:

```yaml
oracle_homes:
  - /u01/app/oracle/product/19c/db_1

patch_zip: /tmp/p37642901_190000_Linux-x86-64.zip
opatch_zip: /tmp/p6880880_190000_Linux-x86-64.zip
patch_base_dir: /u01/Patch
oracle_user: oracle
oracle_sid: ORCL
```

---

## ▶️ How to Use

1. Copy your patch zips (`OPatch` and main patch) to `/tmp` on your Ansible controller.
2. Update `oracle_patch.yml` with your environment paths.
3. Run the playbook:

```bash
ansible-playbook -i inventory oracle_patch.yml
```

---

## 🧪 Tested On

* Oracle Linux 7/8
* Oracle Database 19c
* OPatch version: 12.2.x

---

## ⚠️ Disclaimer

> This playbook is designed for test and automation labs. Always test in lower environments before production use. Ensure backups are taken prior to patching.

---

## 🙌 Contributions

Feel free to fork, enhance, and submit PRs. Suggestions and bug reports are welcome via [Issues](../../issues).

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

⭐ If you find this helpful, give it a star and share it with your fellow DBAs!
