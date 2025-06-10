
# 🚀 Dockerized Full-Stack App

This is a simple full-stack application with:

- 🔧 *Backend*: Node.js + Express
- 🎨 *Frontend*: React
- 🐳 Docker & Docker Compose setup

---

## 📁 Folder Structure

docker-fullstack-app/ │ ├── backend/ │   ├── Dockerfile │   ├── server.js │   └── package.json │ ├── frontend/ │   ├── Dockerfile │   ├── package.json │   └── src/ │       └── App.js │ └── docker-compose.yml

---

## ⚙ Getting Started

### 1. Clone this repository

```bash
git clone <your-repo-url>
cd docker-fullstack-app

2. Run the App with Docker Compose

docker-compose up --build


---

🌐 Access the App

Frontend: http://localhost:3000

Backend: http://localhost:5000



---

🛠 Backend Setup (Node.js + Express)

Located in /backend/

server.js:

const express = require('express');
const app = express();
const port = 5000;

app.get('/', (req, res) => {
  res.send('Backend is running!');
});

app.listen(port, () => {
  console.log(Server running at http://localhost:${port});
});

Dockerfile:

FROM node:18
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 5000
CMD ["node", "server.js"]


---

🎨 Frontend Setup (React)

Located in /frontend/

App.js:

function App() {
  return (
    <div>
      <h1>Hello from React Frontend!</h1>
    </div>
  );
}

Dockerfile:

FROM node:18
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build
RUN npm install -g serve
EXPOSE 3000
CMD ["serve", "-s", "build"]


---

🧩 Docker Compose

docker-compose.yml:

version: '3'
services:
  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
    depends_on:
      - backend

  backend:
    build: ./backend
    ports:
      - "5000:5000"


---

📦 Future Enhancements

🔗 Add MongoDB as a database service

📡 Connect frontend to backend with API calls

🛡 Add CORS, validation, error handling
