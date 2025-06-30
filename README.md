# 🎸 online-music-store

An end-to-end **MERN** e-commerce application specializing in musical instruments.

---

## 📚 Table of Contents
1. [🔍 Project Overview](#project-overview)    
2. [✨ Key Features](#key-features)  
3. [🛠️ Tech Stack](#tech-stack)  
4. [📋 Prerequisites](#prerequisites)  
5. [🔐 Environment Variables](#environment-variables)  
6. [🚀 Local Setup](#local-setup)  
7. [🐳 Docker & Docker Compose](#docker--docker-compose)  
8. [🚢 Deployment Notes](#deployment-notes)  
9. [📜 License](#license)  

---

## 🔍 Project Overview
This repository houses a full-stack music instrument store, built with:

- **Backend**: Node.js, Express, MongoDB (Mongoose)  
- **Frontend**: React, React Router, Axios  
- **Auth**: JWT-based login and registration  
- **Containerization**: Docker & Docker Compose  

It supports:

- Customer shopping flow (browse, search, filter, cart, checkout)  
- Product reviews (star ratings + comments with admin approval)  
- Admin panel (user & order management, review moderation)  
- Product manager panel (category & product CRUD with approval workflow)  
- Sales manager role to set product sale price and cost  

---

## ✨ Key Features
- **Role-based Auth**: `customer`, `product-manager`, `sales-manager`  
- **Price Approval Workflow**: New products hidden until approved  
- **Review Moderation**: Admin approves or rejects comments  
- **Guest Cart**: Persist cart via `x-guest-session` header  
- **Delivery Tracking**: Managers can view and complete deliveries  
- **Dockerized**: One-command setup for full stack locally  

---

## 🛠️ Tech Stack
| Layer     | Technology                          |
|-----------|-------------------------------------|
| **Backend**   | Node.js, Express, Mongoose           |
| **Frontend**  | React, React Router, Axios           |
| **Auth**      | JSON Web Tokens (JWT)                |
| **Database**  | MongoDB                              |
| **Dev & CI**  | Jest, Supertest                      |
| **Container** | Docker, Docker Compose               |

---

## 📋 Prerequisites
1. [Node.js v18+](https://nodejs.org/)  
2. [npm](https://www.npmjs.com/)  
3. Docker & Docker Compose  

*Optional:* MongoDB Atlas account or local MongoDB instance  

---

## 🔐 Environment Variables
Create a `.env` file in the **backend** folder:

```bash
MONGO_URI=your-mongodb-connection-string
JWT_SECRET=your-secret-key
PORT=5001
EMAIL_USER=your-email@example.com
EMAIL_PASS=your-email-password

Note: The frontend is decoupled and reads no secrets; it communicates with the backend on port 5001 by default.


🚀 Local Setup

🖥️ Backend

cd backend
npm install
npm start        # Runs server at http://localhost:5001


Key scripts:
	•	npm run test — run Jest unit & integration tests
	•	npm run test:watch — watch mode

🎨 Frontend

cd frontend
npm install
npm start        # Runs React app at http://localhost:3000

🐳 Docker & Docker Compose

A docker-compose.yml file orchestrates three services:
	•	mongo — MongoDB (data in a volume)
	•	backend — Node/Express API
	•	frontend — Nginx serving the React build

Build & run:
docker compose up --build
	•	Frontend: http://localhost
	•	API: http://localhost:5001

📜 License

MIT © AlpNuhoglu

🚢 Deployment Notes
	1.	Build and push images to your Docker registry.
	2.	On your server:
docker compose pull && docker compose up -d
	3.	Ensure environment variables are set on the host.
