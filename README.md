# 🛡️ Wazuh SIEM Lab (Self-Hosted Setup)

This project documents the deployment of a Wazuh SIEM environment using two Ubuntu virtual machines and one Windows host, simulating a real-world, centralized log monitoring and threat detection solution.

🎥 **Reference Tutorial**:  
[Setup Your Own FREE SIEM at Home – Wazuh](https://www.youtube.com/watch?v=bltbJ2TUQWU)

---

## ⚙️ Lab Architecture

- **Ubuntu VM #1** – Wazuh Server/Manager (with Dashboard, Filebeat, OpenSearch)
- **Ubuntu VM #2** – Linux Agent (Ubuntu Linux)
- **Windows Host** – Windows Agent

---

## 🔧 Steps Performed

### 1️⃣ Wazuh Server Setup (Ubuntu VM)
- Provisioned a clean Ubuntu 22.04 VM
- Installed Wazuh 4.12 with:
  ```bash
  curl -sO https://packages.wazuh.com/4.12/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
Accessed the Wazuh Web UI at https://<wazuh-vm-ip>:443

Signed in successfully and verified all services running

2️⃣ Deploying Linux Agent (Ubuntu VM #2)
Installed the Wazuh agent on a second Ubuntu VM:

wget https://packages.wazuh.com/4.x/apt/wazuh-agent_4.12.0-1_amd64.deb
sudo dpkg -i wazuh-agent_4.12.0-1_amd64.deb
Registered and connected it to the Wazuh server

Confirmed the agent is active in the Wazuh dashboard

Ran test commands (e.g., SSH attempts, file edits) — entries successfully appeared in the dashboard

3️⃣ Deploying Windows Agent (Windows Host)
Installed Wazuh agent using PowerShell:

Invoke-WebRequest -Uri https://packages.wazuh.com/4.x/windows/wazuh-agent-4.12.0-1.msi -OutFile wazuh-agent.msi
Start-Process .\wazuh-agent.msi
Registered the Windows agent with the Wazuh manager

Agent appeared as active in the dashboard

Installed a sample program on Windows — logs appeared in Wazuh under Security Events

✅ Outcomes
All three endpoints (Ubuntu agent, Windows host, Wazuh server) are online and communicating

Real-time logs and security events populate the Wazuh dashboard

Hands-on experience with agent deployment, event correlation, and threat visibility

📌 Next Steps
Simulate common attack vectors (brute force, malware)

Configure email alerting via SMTP

Add Suricata/Zeek for deeper network traffic analysis

Automate deployment with Ansible or Terraform

