# Wanderlust - Your Ultimate Travel Blog 🌍✈️

WanderLust is a simple MERN travel blog website ✈ This project is aimed to help people to contribute in open source, upskill in react and also master git.

![Preview Image](https://github.com/krishnaacharyaa/wanderlust/assets/116620586/17ba9da6-225f-481d-87c0-5d5a010a9538)

## [Figma Design File](https://www.figma.com/file/zqNcWGGKBo5Q2TwwVgR6G5/WanderLust--A-Travel-Blog-App?type=design&node-id=0%3A1&mode=design&t=c4oCG8N1Fjf7pxTt-1)
## [Discord Channel](https://discord.gg/FEKasAdCrG)

## 🎯 Goal of this project

At its core, this project embodies two important aims:

1. **Start Your Open Source Journey**: It's aimed to kickstart your open-source journey. Here, you'll learn the basics of Git and get a solid grip on the MERN stack and I strongly believe that learning and building should go hand in hand.
2. **React Mastery**: Once you've got the basics down, a whole new adventure begins of mastering React. This project covers everything, from simple form validation to advanced performance enhancements. And I've planned much more cool stuff to add in the near future if the project hits more number of contributors.

_I'd love for you to make the most of this project - it's all about learning, helping, and growing in the open-source world._

## Setting up the project locally

### Setting up the Backend

1. **Fork and Clone the Repository**

   ```bash
   git clone https://github.com/{your-username}/wanderlust.git
   ```

2. **Navigate to the Backend Directory**

   ```bash
   cd backend
   ```

3. **Install Required Dependencies**

   ```bash
   npm i
   ```

4. **Set up your MongoDB Database**

   - Open MongoDB Compass and connect MongoDB locally at `mongodb://localhost:27017`.

5. **Import sample data**

   > To populate the database with sample posts, you can copy the content from the `backend/data/sample_posts.json` file and insert it as a document in the `wanderlust/posts` collection in your local MongoDB database using either MongoDB Compass or `mongoimport`.

   ```bash
   mongoimport --db wanderlust --collection posts --file ./data/sample_posts.json --jsonArray
   ```

6. **Configure Environment Variables**

   ```bash
   cp .env.sample .env
   ```

7. **Start the Backend Server**

   ```bash
   npm start
   ```

   > You should see the following on your terminal output on successful setup.
   >
   > ```bash
   > [BACKEND] Server is running on port 5000
   > [BACKEND] Database connected: mongodb://127.0.0.1/wanderlust
   > ```

### Setting up the Frontend

1. **Open a New Terminal**

   ```bash
   cd frontend
   ```

2. **Install Dependencies**

   ```bash
   npm i
   ```

3. **Configure Environment Variables**

   ```bash
   cp .env.sample .env.local
   ```

4. **Launch the Development Server**

   ```bash
   npm run dev
   ```

## 🌟 Ready to Contribute?

Kindly go through [CONTRIBUTING.md](https://github.com/krishnaacharyaa/wanderlust/blob/main/.github/CONTRIBUTING.md) to understand everything from setup to contributing guidelines.

## 💖 Show Your Support

If you find this project interesting and inspiring, please consider showing your support by starring it on GitHub! Your star goes a long way in helping me reach more developers and encourages me to keep enhancing the project.

🚀 Feel free to get in touch with me for any further queries or support, happy to help :)







# 🌍 Wanderlust - DevSecOps CI/CD Project

A **Full Stack Travel Listing Platform** built using the **MERN Stack** and deployed using a complete **DevSecOps CI/CD pipeline**.

This project demonstrates how modern DevOps tools can be integrated with security scanning to automate application build, testing, containerization, and deployment.

---

# 🚀 Features

- Travel listing platform
- User authentication
- Create and manage listings
- Image uploads
- Caching using Redis
- Secure CI/CD pipeline
- Containerized deployment

---

# 🏗️ Tech Stack

## Frontend
- React.js
- Vite
- TailwindCSS

## Backend
- Node.js
- Express.js

## Database
- MongoDB
- Redis (Caching)

---

# ⚙️ DevOps & DevSecOps Tools

- GitHub (Source Control)
- Jenkins (CI/CD Pipeline)
- SonarQube (Code Quality Analysis)
- OWASP Dependency Check (Vulnerability Scan)
- Trivy (Container Security Scan)
- Docker (Containerization)
- Docker Compose (Deployment)
- Docker Hub (Image Registry)

---

# 🏛️ System Architecture

User
↓
React Frontend
↓
Node.js / Express Backend
↓
Redis Cache
↓
MongoDB Database





---

# 🔄 CI/CD Pipeline Flow

The CI/CD pipeline is implemented using **Jenkins**.

Pipeline stages include:

1️⃣ Clone Code from GitHub  
2️⃣ Install Dependencies  
3️⃣ Static Code Analysis using SonarQube  
4️⃣ Sonar Quality Gate Check  
5️⃣ OWASP Dependency Vulnerability Scan  
6️⃣ Docker Image Build  
7️⃣ Trivy Security Scan  
8️⃣ Push Images to Docker Hub  
9️⃣ Deployment using Docker Compose  

---

# 🔍 Security Scanning

Security is integrated at multiple levels in the pipeline.

### Static Code Analysis
Tool used:

Sonarqube



Detects:
- Code smells
- Bugs
- Security vulnerabilities
- Code duplication

---

### Dependency Vulnerability Scan

Tool used:

OWASP Dependency Check



Detects vulnerabilities in:
- npm packages
- third-party libraries

---

### Container Security Scan

Tool used:

Trivy 


Detects:

- OS vulnerabilities
- Library vulnerabilities
- Secret leaks
- Misconfigurations

---

# 🐳 Docker Images

Docker images created in the pipeline:

wanderlust-back:v1
wanderlust-front:v2


Images pushed to Docker Hub:


docker.io/lucky0111/wanderlust-back:v1
docker.io/lucky0111/wanderlust-front:v2




---

# 🚀 Deployment

Deployment is handled using **Docker Compose**.

Services deployed:

- Frontend Container
- Backend Container
- MongoDB
- Redis

Run the application using:
docker-compose up -d





---

# 📊 Pipeline Tools Integration

| Tool | Purpose |
|-----|------|
| Jenkins | CI/CD Automation |
| SonarQube | Code Quality Analysis |
| OWASP Dependency Check | Dependency Vulnerability Scan |
| Trivy | Container Security Scan |
| Docker | Containerization |
| Docker Compose | Multi-container Deployment |

---

# 📸 Screenshots

Add screenshots of:

- Jenkins Pipeline
- ![Preview Image](C:\Users\wd894\OneDrive\Pictures\Screenshots\Screenshot 2026-03-15 011138.png)
  
- SonarQube Dashboard
 ![Preview Image](C:\Users\wd894\OneDrive\Pictures\Screenshots\Screenshot 2026-03-15 011013.png)
- OWASP Scan
   ![Preview Image]("C:\Users\wd894\OneDrive\Pictures\Screenshots\Screenshot 2026-03-15 011119.png")
- Trivy Scan
  ![Preview Image]("C:\Users\wd894\OneDrive\Pictures\Screenshots\Screenshot 2026-03-15 143321.png")
- Application UI
  ![Preview Image]("C:\Users\wd894\OneDrive\Pictures\Screenshots\Screenshot 2026-03-15 121924.png")

---

# 🧠 Key DevOps Concepts Demonstrated

- CI/CD Automation
- DevSecOps Pipeline
- Containerization
- Infrastructure Automation
- Security Scanning
- Automated Deployment

---

# 📌 Future Improvements

- Kubernetes deployment
- Helm charts
- GitHub Actions pipeline
- Monitoring using Prometheus & Grafana

---

# 👨‍💻 Author

**Anas Mansuri**


GitHub  
https://github.com/mansurianas

---



