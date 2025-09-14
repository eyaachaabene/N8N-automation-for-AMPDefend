
# 🔒 N8N & Metabase Automation for AMPDefend

This repository contains an **end-to-end cybersecurity automation platform** using:

* **[n8n](https://n8n.io)** → for alert ingestion, AI summarization, notifications, and monthly reporting.
* **[Metabase](https://www.metabase.com/)** → for real-time dashboards and SOC analytics on stored logs.

Together, they provide **automated alert management + live dashboards** to strengthen AMPDefend’s cybersecurity operations.

---

## 📌 Features

### 🚨 n8n (Automation Layer)

* Collects logs from Raspberry Pi devices via **Webhook**.
* Stores alerts in **Postgres**.
* Summarizes logs into **human-readable WhatsApp/email alerts**.
* Generates **monthly AI reports** → exported to **Google Docs + Drive**.
---
  <img width="2291" height="1170" alt="Capture d'écran 2025-09-14 201134" src="https://github.com/user-attachments/assets/6e54379b-a2c9-49e3-b6da-cec25791417c" />
  
---

### 📊 Metabase (Analytics Layer)

* Connects directly to the **same Postgres DB**.
* Provides dashboards for:

  * Threat detection timeline (hourly/daily).
  * Threat type distribution by severity.
  * Geo heatmap of alerts by region/country.
---

  <img width="2148" height="1233" alt="image" src="https://github.com/user-attachments/assets/3a4ebd0c-559c-4ab6-b9ae-d0344209536c" />


---

## ⚙️ Architecture

```mermaid
flowchart TD
    A[Webhook / Cron Job] --> B[Postgres DB]
    B --> C[n8n AI Agent - Summaries]
    C --> D[Gmail Alerts]
    C --> E[WhatsApp Alerts]
    B --> F[n8n AI Agent - Monthly Reports]
    F --> G[Google Docs Export]
    G --> H[Google Drive Archive]
 
    B --> J[Metabase Dashboards]
```

---

## 🚀 Getting Started

### 1. Requirements

* **Docker & docker-compose**
* API credentials: Gmail, WhatsApp Business (Meta), Google Docs, Google Drive
* AI key (Groq)

### 2. Install & Run

```bash
# Clone repository
git clone https://github.com/<your-org>/N8N-automation-for-AMPDefend.git
cd N8N-automation-for-AMPDefend

# Build and start all services
docker compose build
docker compose up -d
```

This will launch:

* **n8n** (workflow automation engine)
* **Postgres** (alert storage + analytics source)
* **Metabase** (dashboards)
*  **pgadmin** 

---

## 🛡️ Security Benefits

* **Reduced alert fatigue** → AI summaries.
* **Faster response** → WhatsApp & Gmail instant notifications.
* **Better visibility** → Metabase dashboards.
* **Audit-ready** → Monthly AI reports stored in Google Docs & Drive.

