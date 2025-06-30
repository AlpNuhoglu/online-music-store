online-music-store

An end-to-end MERN e-commerce application specializing in musical instruments.

⸻

Table of Contents
	1.	Project Overview
	2.	Key Features
	3.	Tech Stack
	4.	Prerequisites
	5.	Environment Variables
	6.	Local Setup
	•	Backend
	•	Frontend
	7.	Docker & Docker Compose
	8.	API Endpoints
	•	Auth
	•	Users
	•	Products & Reviews
	•	Cart & Orders
	•	Admin & Product Manager
	•	Category & Delivery
	9.	Testing
	10.	Deployment
	11.	License

⸻

Project Overview

This repository houses a full-stack music instrument store, built with:
	•	Backend: Node.js, Express, MongoDB (Mongoose)
	•	Frontend: React, React Router
	•	Auth: JWT-based login/register
	•	Containerization: Docker & Docker Compose

It supports:
	•	Customer shopping flow (browse, search, filter, cart, checkout)
	•	Product reviews (star ratings + comments with admin approval)
	•	Admin panel (user & order management, review approval)
	•	Product manager panel (category/product CRUD with price-approval workflow)
	•	Sales manager role to set product sale-price and cost

Key Features
	•	Role-based auth: customer, product-manager, sales-manager
	•	Product-level price approval: New items hidden until sales manager sets price
	•	Review moderation: Admin approves or rejects comments
	•	Guest cart: Persist cart via x-guest-session header
	•	Delivery tracking: Managers can view and mark deliveries
	•	Dockerized: Easily spin up entire stack locally

Tech Stack

Layer	Technology
Backend	Node.js, Express, Mongoose
Frontend	React, React Router, Axios
Auth	JSON Web Tokens
DB	MongoDB
Dev & CI	Jest, Supertest
Container	Docker, Docker Compose

Prerequisites
	1.	Node.js v18+
	2.	npm
	3.	Docker & Docker Compose
	4.	MongoDB Atlas or local MongoDB

Environment Variables

Create a .env in the project root (backend folder):

MONGO_URI=your-mongodb-connection-string
JWT_SECRET=your-secret-key
PORT=5001
EMAIL_USER=your-email@example.com
EMAIL_PASS=your-email-password

Note: Frontend reads no secrets; it calls backend on port 5001 by default.

Local Setup

Backend

cd backend
npm install
npm start        # Runs server on http://localhost:5001

Key scripts:
	•	npm run test – run Jest unit & integration tests
	•	npm run test:watch – watch mode

Frontend

cd frontend
npm install
npm start        # Runs React app on http://localhost:3000

Docker & Docker Compose

A docker-compose.yml stands up three services:
	•	mongo – MongoDB (data stored in volume)
	•	backend – Node/Express API
	•	frontend – Nginx serving React build

Build & run:

docker compose up --build

Access:
	•	Frontend: http://localhost
	•	API: http://localhost:5001

API Endpoints

Auth

Method	Path	Access	Description
POST	/auth/register	Public	Create new user
POST	/auth/login	Public	Returns JWT token

Users

Method	Path	Access (JWT)	Description
GET	/users	admin	List all users
GET	/users/profile	Authenticated	Get current user profile
POST	/users/wishlist/:productId	Authenticated	Add to wishlist
GET	/users/wishlist	Authenticated	View wishlist

Products & Reviews

Method	Path	Access	Description
GET	/products	Public	List approved products
GET	/products/:id	Public	Single product + average rating
POST	/products	product-manager	Create product (priceApproved=false)
DELETE	/products/:id	product-manager	Delete product
PATCH	/products/:id/stock	product-manager	Update stock

Reviews (nested under /products/:productId/reviews)

Method	Path	Access	Description
POST	/products/:id/reviews	Authenticated + purchased/delivered	Submit rating & comment
GET	/products/:id/reviews	Public	List approved comments
PUT	/reviews/:id/approve	product-manager	Approve comment
PUT	/reviews/:id/disapprove	product-manager	Reject comment
GET	/reviews/unapproved	product-manager	List all pending reviews

Cart & Orders

Method	Path	Access	Description
GET	/cart	Optional (JWT or guestId)	View cart
POST	/cart	Optional (JWT or guestId)	Add to cart
DELETE	/cart/:productId	Optional	Remove from cart
GET	/orders/all	product-manager	List all orders
POST	/orders	Authenticated	Place an order
PATCH	/orders/:id/status	product-manager	Update order status
GET	/orders/:id	Authenticated	Get single order details

Admin & Product Manager

Method	Path	Access	Description
GET	/admin/users	product-manager	List users
DELETE	/admin/users/:username	product-manager	Delete one user
DELETE	/admin/users	product-manager	Delete all users
GET	/admin/reviews/unapproved	product-manager	Pending reviews
GET	/deliveries	product-manager	List deliveries
PATCH	/deliveries/:id/complete	product-manager	Mark delivery complete

Category & Delivery

Method	Path	Access	Description
POST	/categories	product-manager	Create category
DELETE	/categories/:id	product-manager	Delete if unused

Testing
	•	Backend: in /backend run npm test (Jest + Supertest)
	•	Frontend: currently no unit tests (add with React Testing Library)

Deployment
	1.	Push images to Docker registry
	2.	On server: docker compose pull && docker compose up -d
	3.	Ensure environment variables set on host

License

MIT © Your Name

⸻

This README was generated to help you get started quickly and thoroughly.
