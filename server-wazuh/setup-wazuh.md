# ⚙️ Setup Wazuh Server (Single Node)

Jalankan command ini di dalam **VM 1 (Ubuntu Server)**.
Pastikan Docker dan Docker Compose sudah terinstal.

```bash
# 1. Clone repository resmi Wazuh Docker
git clone [https://github.com/wazuh/wazuh-docker.git](https://github.com/wazuh/wazuh-docker.git)
cd wazuh-docker

# 2. PIN KE VERSI STABIL (4.10.x atau 4.14.x)
# Ini penting agar tidak terjebak di versi 5.x yang belum stabil
git checkout v4.10.1

# 3. Masuk ke direktori single-node
cd single-node

# 4. Generate Sertifikat (Wajib untuk v4 ke atas)
docker compose -f generate-indexer-certs.yml run --rm generator

# 5. Jalankan container
docker compose up -d
```

#  File `target-machine/install-agent.sh`
Pastikan agent yang diinstal di komputer korban juga merujuk ke versi 4.x agar sinkron dengan servernya.

**Di bagian ini (dalam file tersebut):**
```bash
# Ganti baris download agent dengan versi spesifik jika ingin lebih aman:
curl -sO https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent_4.10.1-1_amd64.deb
sudo WAZUH_MANAGER='IP_VM1' dpkg -i wazuh-agent_4.10.1-1_amd64.deb
```
