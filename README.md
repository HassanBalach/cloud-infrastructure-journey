# 🚀 Cloud Infrastructure & DevOps Journey

Welcome to my hands-on Platform Engineering and Cloud Infrastructure repository. This repository serves as a live, evolving **Proof of Work** documenting my transition from isolated theoretical networking into practical, real-world cloud engineering on **Amazon Web Services (AWS)**.

---

## 🎯 Mindset Shift: Real Infrastructure Over Abstract Theory

Rather than relying on simulated environments or passive tutorials, I learn by building, securing, and maintaining live infrastructure. Every configuration in this repository is executed directly on cloud servers, emphasizing the critical **"why"** behind cloud security, system administration, and automation.

* **Primary Cloud Provider:** Amazon Web Services (AWS)
* **Compute Instance:** EC2 (`t2.micro` / `t3.micro`) running Ubuntu 26.04 LTS
* **Region:** `eu-north-1` (Stockholm)
* **Core Tooling:** Linux/Bash, SSH (ED25519), Git, Nginx, Systemd

---

## 📚 Repository Structure & Lab Modules

Each module in this repository covers a core operational milestone, formatted with step-by-step documentation and architectural breakdowns:

| Module | Topic | Description | Status |
| :--- | :--- | :--- | :---: |
| **`_01_`** | **EC2 Provisioning & Security** | Provisioning live EC2, configuring Security Groups, and initial connection. | Completed |
| **`_02_`** | **SSH Key Pair Upgrades** | Upgrading from default `.pem` keys to custom ED25519 asymmetric key pairs using `ssh-copy-id`. | Completed |
| **`_03_`** | **Shell Scripting & Automation** | Writing `bootstrap.sh` scripts to automate package updates, service provisioning, and configuration. | In Progress |

---

## 🛠️ Key Technical Concepts Mastered

### 🔑 Cryptographic SSH Authentication
* Configured asymmetric public/private key pairs (`ed25519`) for passwordless authentication.
* Understood the underlying SSH cryptographic handshake process and remote `~/.ssh/authorized_keys` management.
* Implemented secure file permission standards (`chmod 600` for keys, `chmod 700` for `.ssh` directories).

### 🌐 AWS Security & Networking
* Configured AWS Security Group inbound rules (Port 22 for SSH, Port 80 for HTTP).
* Managed dynamic vs. static IP connectivity constraints for secure remote access.

### 🐧 Linux System Administration
* Monitored core system resources using `free -h`, `df -h`, and `htop`.
* Managed system services (`systemctl`) and analyzed active processes.

---

# Clone the repository

git clone https://github.com/HassanBalach/cloud-infrastructure-journey.git
cd cloud-infrastructure-journey