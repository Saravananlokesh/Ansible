# 🔄 Oracle GoldenGate Patching with Ansible

This Ansible playbook automates the patching process for Oracle GoldenGate on Linux systems. It helps in applying PSU patches, updating the OPatch utility, and managing GoldenGate processes — all with a few simple steps.

---

## 📦 Playbook: `goldengate_patch.yml`

### 🛠️ Features
- Stops all running GoldenGate processes
- Validates and transfers patch files
- Backs up and updates the OPatch utility
- Applies the GoldenGate patch using `opatch apply -silent`
- Validates the patch installation
- Restarts GoldenGate processes

---

## 📁 Directory Structure

```bash
oracle-ansible-playbooks/
└── goldengate_patch/
    ├── goldengate_patch.yml
    ├── README.md
    └── files/
        ├── p37071355_2116000OGGRU_Linux-x86-64.zip
        └── p6880880_190000_Linux-x86-64.zip
