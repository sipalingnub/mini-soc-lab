# 🛡️ Mini SOC Lab & Attack Simulation

## 📖 Overview
Project ini adalah sebuah lab Mini Security Operations Center (SOC) yang dirancang untuk mensimulasikan serangan siber dan melakukan deteksi ancaman secara *real-time*. Tujuan utama dari project ini adalah untuk mempraktikkan dan memahami *workflow* deteksi insiden (Incident Response) dari sudut pandang Blue Team / SOC Analyst.

## 🛠️ Tools & Technologies
* **SIEM / XDR:** [Wazuh](https://wazuh.com/) (Deployed via Docker)
* **IDS / IPS:** Suricata *(Planned phase)*
* **Case Management:** IRIS *(Planned phase)*
* **Attack Tools:** Hydra (SSH Brute-force simulation)
* **Environment:** Ubuntu Linux, Virtual Machine

## 🏗️ Lab Topology
Lab ini berjalan di lingkungan virtual yang terisolasi, terdiri dari:
1.  **Wazuh Server (VM 1):** Bertindak sebagai "otak" utama untuk mengumpulkan log, menganalisis data, dan memicu *alert*.
2.  **Target / Victim (VM 2):** Mesin target yang diinstal OpenSSH Server dan dipantau menggunakan Wazuh Agent.
3.  **Attacker Machine:** Mesin yang mengeksekusi serangan *brute-force* untuk menguji aturan deteksi.

## 🚀 Project Phases
- [x] **Phase 1:** Setup Repository & Folder Structure.
- [ ] **Phase 2:** Deployment Wazuh Manager menggunakan Docker Compose.
- [ ] **Phase 3:** Setup Target Machine & instalasi Wazuh Agent.
- [ ] **Phase 4:** Attack Simulation (SSH Brute-force & Invalid Logins).
- [ ] **Phase 5:** Threat Detection & Log Analysis di dashboard Wazuh.

## 📁 Repository Structure
* `docs/`: Dokumentasi, *screenshot alert*, dan gambaran topologi.
* `server-wazuh/`: File `docker-compose` dan konfigurasi server Wazuh.
* `target-machine/`: Script dan catatan *setup* untuk mesin target.
* `attack-scripts/`: Kumpulan *command* dan *script* untuk simulasi serangan.
* `configs/`: File konfigurasi tambahan (Wazuh custom rules, Suricata, dll).

## ⚠️ Disclaimer
*Project ini dibuat sepenuhnya untuk tujuan edukasi dan portofolio Cybersecurity. Simulasi serangan hanya dilakukan di dalam lingkungan lab yang terisolasi secara mandiri.*