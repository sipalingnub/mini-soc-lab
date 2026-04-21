# ⚙️ Setup Wazuh Server (Single Node)

Jalankan command ini di dalam **VM 1 (Ubuntu Server)**.
Pastikan Docker dan Docker Compose sudah terinstal.

```bash
# 1. Clone repository resmi Wazuh Docker
git clone [https://github.com/wazuh/wazuh-docker.git](https://github.com/wazuh/wazuh-docker.git)

# 2. Masuk ke direktori single-node
cd wazuh-docker/single-node

# 3. Jalankan container
docker-compose up -d

---

### 3. Folder `target-machine`
Ini buat *script* instalasi agent dan SSH di komputer korban (VM 2).
* Bikin file: `install-agent.sh`
* **Isi file:**
```bash
#!/bin/bash
# Script dijalankan di VM 2 (Victim)

echo "[*] Menginstall OpenSSH & Fail2Ban..."
sudo apt update && sudo apt install openssh-server fail2ban -y

echo "[*] Mendownload Wazuh Agent..."
curl -sO https://packages.wazuh.com/4.x/wazuh-agent.sh

# PENTING: Ganti <IP_VM_1> dengan IP Address dari VM 1 (Wazuh Server)
echo "[*] Menginstall Wazuh Agent..."
sudo bash wazuh-agent.sh -a WAZUH_MANAGER="<IP_VM_1>"

echo "[*] Menjalankan layanan Wazuh Agent..."
sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent

echo "[+] Selesai! Cek dashboard Wazuh di VM 1 untuk memastikan agent terhubung."