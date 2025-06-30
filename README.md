{
  "title": "# online-music-store",
  "description": "An end-to-end MERN e-commerce application specializing in musical instruments.",
  "tableOfContents": [
    "1. 🚀 Project Overview",
    "2. ✨ Key Features",
    "3. 🛠️ Tech Stack",
    "4. 🔧 Prerequisites",
    "5. ⚙️ Environment Variables",
    "6. 🚀 Local Setup",
    "   - Backend",
    "   - Frontend",
    "7. 📦 Docker & Docker Compose",
    "8. 🔗 API Endpoints",
    "   - Auth",
    "   - Users",
    "   - Products & Reviews",
    "   - Cart & Orders",
    "   - Admin & Product Manager",
    "   - Category & Delivery",
    "9. 🧪 Testing",
    "10. ☁️ Deployment",
    "11. 📄 License"
  ],
  "sections": [
    {
      "heading": "1. 🚀 Project Overview",
      "content": "This repository houses a full-stack music instrument store, built with:\n\n- **Backend**: Node.js, Express, MongoDB (Mongoose)\n- **Frontend**: React, React Router\n- **Auth**: JWT-based login/register\n- **Containerization**: Docker & Docker Compose"
    },
    {
      "heading": "2. ✨ Key Features",
      "content": "- Role-based auth: customer, product-manager, sales-manager\n- Product-level price approval workflow\n- Review moderation with admin approval\n- Guest & authenticated cart persistence\n- Delivery tracking & management\n- Dockerized for easy local spin-up"
    },
    {
      "heading": "3. 🛠️ Tech Stack",
      "content": "| Layer      | Tech                          |\n|------------|-------------------------------|\n| Backend    | Node.js, Express, Mongoose    |\n| Frontend   | React, React Router, Axios    |\n| Auth       | JSON Web Tokens (JWT)         |\n| Database   | MongoDB                       |\n| CI/CD      | Docker, Docker Compose        |"
    },
    {
      "heading": "4. 🔧 Prerequisites",
      "content": "- Node.js v18+\n- npm or yarn\n- Docker & Docker Compose (for containerization)\n- MongoDB (or use the bundled Docker image)"
    },
    {
      "heading": "5. ⚙️ Environment Variables",
      "content": "Create a `.env` file in `/backend` with:\n\n```\nMONGO_URI=<your_mongo_uri>\nJWT_SECRET=<your_jwt_secret>\nEMAIL_USER=<your_email>\nEMAIL_PASS=<your_email_password>\nPORT=5001\n```"
    },
    {
      "heading": "6. 🚀 Local Setup",
      "subsections": [
        {
          "subheading": "🔹 Backend",
          "content": "```bash\ncd backend\nnpm install\nnpm start\n```"
        },
        {
          "subheading": "🔹 Frontend",
          "content": "```bash\ncd frontend\nnpm install\nnpm start\n```"
        }
      ]
    },
    {
      "heading": "7. 📦 Docker & Docker Compose",
      "content": "```bash\ndocker-compose up --build\n```  \nThis will spin up three containers:\n- **mongo** (MongoDB)\n- **backend** (Node API)\n- **frontend** (Nginx-served React build)"
    },
    {
      "heading": "8. 🔗 API Endpoints",
      "subsections": [
        {
          "subheading": "Auth",
          "content": "| Method | Route           | Description                  |\n|--------|-----------------|------------------------------|\n| POST   | /auth/register  | Create new user             |\n| POST   | /auth/login     | Obtain JWT token            |"
        },
        {
          "subheading": "Users",
          "content": "| Method | Route          | Description               |\n|--------|----------------|---------------------------|\n| GET    | /users/profile | Get logged-in user's info |"
        },
        {
          "subheading": "Products & Reviews",
          "content": "| Method | Route                         | Description                  |\n|--------|-------------------------------|------------------------------|\n| GET    | /products                     | List all approved products   |\n| POST   | /products                     | Create product (manager)     |\n| GET    | /products/:id/reviews         | List approved reviews        |"
        },
        {
          "subheading": "Cart & Orders",
          "content": "| Method | Route                      | Description                      |\n|--------|----------------------------|----------------------------------|\n| GET    | /cart                      | Get current user's cart         |\n| POST   | /orders                    | Create order                    |"
        },
        {
          "subheading": "Admin & Product Manager",
          "content": "| Method | Route                    | Description                     |\n|--------|--------------------------|---------------------------------|\n| GET    | /admin/users             | List all users                  |\n| PATCH  | /products/:id/stock      | Update stock (manager)          |"
        },
        {
          "subheading": "Category & Delivery",
          "content": "| Method | Route                  | Description                     |\n|--------|------------------------|---------------------------------|\n| POST   | /categories            | Create new category (manager)   |\n| GET    | /deliveries            | List all deliveries (manager)   |"
        }
      ]
    },
    {
      "heading": "9. 🧪 Testing",
      "content": "```bash\ncd backend\nnpm test\n```  \nRuns unit & integration tests with Jest & Supertest."
    },
    {
      "heading": "10. ☁️ Deployment",
      "content": "- Push to Docker Hub or your registry\n- Deploy stack with `docker-compose up -d`"
    },
    {
      "heading": "11. 📄 License",
      "content": "MIT © [Your Name]"
    }
  ]
}
