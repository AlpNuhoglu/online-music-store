# 🎸 online-music-store
An end-to-end **MERN** e-commerce application specializing in musical instruments.

## 📚 Table of Contents
1. [Project Overview](#project-overview)  
2. [Key Features](#key-features)  
3. [Tech Stack](#tech-stack)  
4. [Prerequisites](#prerequisites)  
5. [Environment Variables](#environment-variables)  
6. [Local Setup](#local-setup)  
7. [Docker & Docker Compose](#docker--docker-compose)  
8. [Deployment Notes](#deployment-notes)  
9. [License](#license)  

## 🔍 Project Overview
This repository contains a full-stack music instrument store built with the MERN stack:
- **Backend**: Node.js, Express, MongoDB (Mongoose)  
- **Frontend**: React, React Router, Axios  
- **Authentication**: JWT-based login & registration  
- **Containerization**: Docker & Docker Compose  
**Features include:**
- Customer shopping flow (browse, search, filter, cart, checkout)  
- Product reviews (star ratings + comments with admin approval)  
- Admin panel (user & order management, review moderation)  
- Product manager panel (category & product CRUD with approval workflow)  
- Sales manager role (set product sale price and cost)  

## ✨ Key Features
- **Role-based Access Control**: `customer`, `product-manager`, `sales-manager`  
- **Price Approval Workflow**: New products hidden until approved  
- **Review Moderation**: Admin can approve or reject comments  
- **Guest Cart**: Persist cart via `x-guest-session` header  
- **Delivery Tracking**: Managers can view and mark deliveries complete  
- **Dockerized**: Spin up the full stack with a single command  

## 🛠️ Tech Stack
| Layer        | Technology                 |
|--------------|----------------------------|
| **Backend**  | Node.js, Express, Mongoose |
| **Frontend** | React, React Router, Axios |
| **Auth**     | JSON Web Tokens (JWT)      |
| **Database** | MongoDB                    |
| **Testing**  | Jest, Supertest            |
| **Container**| Docker, Docker Compose     |

## 📋 Prerequisites
1. [Node.js v18+](https://nodejs.org/)  
2. [npm](https://www.npmjs.com/)  
3. Docker & Docker Compose  
> *Optional:* MongoDB Atlas account or local MongoDB instance

## 🔐 Environment Variables
Create a `.env` file in the **backend** directory:
```bash
MONGO_URI=your-mongodb-connection-string
JWT_SECRET=your-secret-key
PORT=5001
EMAIL_USER=your-email@example.com
EMAIL_PASS=your-email-password
