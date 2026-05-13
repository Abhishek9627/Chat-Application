# Real-Time Chat Application

A full-stack real-time chat application built with the MERN stack and Socket.io, 
featuring JWT authentication and automated CI/CD deployment.

## Tech Stack
- **Frontend** — React.js
- **Backend** — Node.js, Express.js
- **Database** — MongoDB
- **Real-time** — Socket.io
- **Authentication** — JWT
- **DevOps** — Docker, Docker Compose, Jenkins, GitHub Actions
- **Cloud** — AWS EC2

## Features
- User registration and login with JWT authentication
- Real-time messaging using Socket.io
- Containerized with Docker (separate frontend & backend containers)
- Automated CI/CD pipeline via Jenkins with GitHub webhook integration
- Deployed on AWS EC2

## Getting Started

### Prerequisites
- Node.js
- MongoDB
- Docker (optional)

### Installation
```bash
# Clone the repo
git clone https://github.com/Abhishek9627/Chat-Application

# Install backend dependencies
cd backend
npm install

# Install frontend dependencies
cd frontend
npm install

# Run backend
npm start

# Run frontend
npm start
```

## CI/CD Pipeline
- GitHub webhook triggers Jenkins on every push
- Jenkins builds and tests the application
- Docker containers are built and deployed automatically
