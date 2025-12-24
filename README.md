# 🚀 iPhone 17 Launch — Flash Sale Microservices System

![Docker](https://img.shields.io/badge/Container-Docker-blue.svg?style=for-the-badge&logo=docker)
![Python](https://img.shields.io/badge/Backend-Flask-green.svg?style=for-the-badge&logo=python)
![Redis](https://img.shields.io/badge/Cache-Redis-red.svg?style=for-the-badge&logo=redis)
![Nginx](https://img.shields.io/badge/Load%20Balancer-Nginx-009639.svg?style=for-the-badge&logo=nginx)
![Grafana](https://img.shields.io/badge/Monitoring-Grafana-F46800.svg?style=for-the-badge&logo=grafana)

> **Cloud Architecture Simulation for High-Concurrency Flash Sale Events**

Proyek ini merupakan simulasi sistem **Flash Sale** untuk peluncuran **iPhone 17 Pro Max (2025)**.  
Sistem dibangun menggunakan arsitektur **Microservices** yang dirancang untuk menangani **traffic ekstrem** dengan karakteristik:

- ⚡ High concurrency  
- ❌ Zero downtime  
- 🛡️ Zero overselling (anti stok minus)

---

## 🌟 Key Features

| Fitur | Deskripsi | Teknologi |
|------|----------|-----------|
| 🛡️ **Race Condition Proof** | Menjamin stok tetap akurat meskipun 1000+ request/detik | Redis Atomic Operation |
| ⚖️ **Load Balancing** | Distribusi beban otomatis ke beberapa replika server | Nginx (Round Robin) |
| ❤️ **Self-Healing System** | Container otomatis pulih saat terjadi kegagalan | Docker Compose |
| 👁️ **Observability** | Monitoring trafik sukses vs gagal secara real-time | Prometheus & Grafana |
| 💎 **Modern UI** | Tampilan frontend bertema *Apple Event* | HTML5 & CSS3 |

---

## 🏗️ System Architecture

Seluruh sistem berjalan dalam lingkungan **containerized microservices** dengan alur sebagai berikut:

```mermaid
graph TD
    User[User / Bot Attack] -->|HTTP Request| LB[Nginx Load Balancer]
    LB -->|Round Robin| App1[Web App Replica 1]
    LB -->|Round Robin| App2[Web App Replica 2]
    LB -->|Round Robin| App3[Web App Replica 3]
    App1 & App2 & App3 -->|Atomic Decrement| Redis[(Redis)]
    App1 & App2 & App3 -.->|Metrics| Prometheus
    Prometheus -.->|Visualization| Grafana
