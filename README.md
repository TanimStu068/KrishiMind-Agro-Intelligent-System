

# 🌱 KrishiMind — Agro-Intelligent System

[![Next.js](https://img.shields.io/badge/Next.js-14-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115-009688?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![PostgreSQL](https://img.shields.io/badge/PostGIS-16-336791?style=for-the-badge&logo=postgresql)](https://postgis.net/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker)](https://www.docker.com/)

**KrishiMind** is an AI-powered agricultural intelligence platform designed specifically for Bangladesh. It bridges the gap between grassroots farmers and government agricultural officers by providing real-time crop recommendations, AI disease scanning, market insights, and localized broadcast alerts via an intuitive bilingual (Bangla & English) interface.

---

## 👥 Team & Attribution

**KrishiMind** was developed collaboratively as a team project during our industrial attachment at **EchoLogyx Ltd.**

This repository is a portfolio copy of the original team project, shared here for project showcase purposes.

### Team Members

- **Tanim Mahmud** — [GitHub](https://github.com/TanimStu068)
- **Md Imam Sabbir** — [GitHub](https://github.com/md-imam75)
- **Abtahi Mustakim** — [GitHub](https://github.com/Abtahi71)
- **Robiul Alam**
- **Abid Hasan Zarif**
- **Md Mehedi**



> All team members contributed to the development of KrishiMind. The repository and project should be considered a collaborative team effort, not an individual project.

**Original Team Repository:**  
[KrishiMind-Agro-Intelligent-System](https://github.com/md-imam75/KrishiMind-Agro-Intelligent-System)

---

## 👨‍💻 My Contribution

As a member of the KrishiMind development team, my contributions included:

- 💡 **Project Ideation:** Proposed the core idea for KrishiMind, which was selected by the company from the ideas presented by the team.
- 🎨 **Frontend Development:** Contributed to the development and implementation of the frontend interface and user-facing features.
- 📚 **Frontend & Backend Documentation:** Prepared and organized technical documentation covering both the frontend and backend components of the system.
- 📝 **Detailed Project Documentation:** Contributed to the company's requested comprehensive documentation by documenting system features, workflows, technical components, and implementation details across the frontend and backend.
- 🔍 **Feature Documentation:** Added detailed explanations of the project's major features, their purpose, workflows, and technical behavior.
- 🧪 **Testing & Review:** Ran and tested the complete application, reviewed its features and workflows, identified issues, and provided feedback for improvements.
- 🔧 **Ongoing Improvements:** Currently contributing to code improvements, README updates, documentation refinement, and project maintenance.

> KrishiMind was developed collaboratively as a team project, and these contributions represent my individual involvement within the team.

---

## ✨ Key Features

### For Farmers 🌾
* **Bilingual Onboarding:** Easy setup using phone numbers with secure OTP verification, available natively in both English and Bengali.
* **Smart Farm Profiling:** Farmers can register their plots with specific soil types, land elevation, and water availability to receive tailored advice.
* **AI Crop Recommendations:** Powered by Gemini AI, suggests the most profitable and suitable crops based on plot conditions and current season.
* **Disease Scanner:** Upload photos of infected crops for instant AI-based disease diagnosis and actionable remedies.
* **Yield Prediction:** Machine learning models predict expected harvest volume using farm parameters.
* **Market Insights:** Real-time mandi (market) price tracking across various districts.
* **Agricultural Advisory:** Localized weather forecasts coupled with actionable agronomic advice.

### For DAE Officers 📊
* **Command Dashboard:** A professional analytics portal for district/regional officers to monitor agricultural activities.
* **Risk Heatmaps:** PostGIS-powered geospatial data visualization showing potential risk zones (e.g., floods, pests).
* **Broadcast Alerts:** Officers can send instantaneous, localized emergency push notifications to all farmers in specific districts via async Celery background workers.
* **Farmer Directory:** Searchable database tracking farmer onboarding and active crop progress.

---

## 📸 Screenshots

### Onboarding & Login
<p align="center">
  <img src="./docs/images/welcome.png" width="80%" alt="Welcome Screen" />
</p>
<p align="center">
  <img src="./docs/images/login.png" width="80%" alt="Login Screen" />
</p>

### Farmer Dashboard & Market Prices
<p align="center">
  <img src="./docs/images/farmer_dashboard.png" width="80%" alt="Farmer Dashboard" />
</p>
<p align="center">
  <img src="./docs/images/marketprice.png" width="80%" alt="Market Prices" />
</p>

### AI Core: Disease Scanner & Crop Recommendation
<p align="center">
  <img src="./docs/images/disease_scanner.png" width="80%" alt="AI Disease Scanner" />
</p>
<p align="center">
  <img src="./docs/images/recommendation.png" width="80%" alt="Crop Recommendation" />
</p>

### AI Core: Yield Prediction & Intelligent Assistant
<p align="center">
  <img src="./docs/images/prediction.png" width="80%" alt="Yield Prediction" />
</p>
<p align="center">
  <img src="./docs/images/assistant.png" width="80%" alt="AI Assistant" />
</p>

### Officer Analytics Portal
<p align="center">
  <img src="./docs/images/officer_dashboard.png" width="100%" alt="Officer Dashboard" />
</p>

---

## 🏗️ System Architecture

KrishiMind is built using a modern, scalable microservices architecture orchestrated with Docker Compose:

* **Frontend:** Next.js 14 (App Router), React, Tailwind CSS, TypeScript
* **Backend API:** FastAPI (Python 3.11), Pydantic v2
* **Database:** PostgreSQL 16 with PostGIS extensions (Asyncpg engine)
* **Background Workers:** Celery + Redis for async tasks (like bulk notifications)
* **ORM & Migrations:** SQLAlchemy 2.0 + Alembic
* **Authentication:** JWT (JSON Web Tokens) with secure bcrypt hashing
* **Reverse Proxy:** Nginx

---

## 🚀 Getting Started

### Prerequisites
Make sure you have [Docker](https://www.docker.com/products/docker-desktop/) and [Docker Compose](https://docs.docker.com/compose/) installed on your machine.

### 1. Clone the repository
```bash
git clone https://github.com/md-imam75/KrishiMind-Agro-Intelligent-System.git
cd KrishiMind-Agro-Intelligent-System
```

### 2. Environment Variables
Create a `.env` file in the `backend/` directory (you can copy `.env.example`):
```bash
cp backend/.env.example backend/.env
```
Ensure you add your `GEMINI_API_KEY` to the `.env` file for the AI features to work.

### 3. Build and Run via Docker Compose
Run the following command in the root directory to build the stack. (This process takes a few minutes as it pulls base images and installs dependencies).
```bash
docker compose up -d --build
```

### 4. Run Database Migrations
Once the containers are healthy, execute Alembic migrations to build the tables:
```bash
docker compose exec backend alembic upgrade head
```

### 5. Seed an Officer Account (Optional)
To test the Officer Dashboard, you can seed an admin account into the database:
```bash
docker compose exec backend python seed_officer.py
```


### 6. Access the Application
* **Web App (Farmers & Officers):** [http://localhost:3000](http://localhost:3000)
* **Backend API Documentation (Swagger):** [http://localhost:8000/docs](http://localhost:8000/docs)

---

## 🧪 Running Tests
The backend includes a comprehensive automated test suite (Pytest) for critical API endpoints.
```bash
docker compose exec backend pytest
```

---

## 📄 License

Copyright © 2026 Tanim Mahmud. All rights reserved.

This repository is publicly available for viewing and portfolio purposes.
The source code may not be copied, modified, distributed, or reused
without prior written permission.
