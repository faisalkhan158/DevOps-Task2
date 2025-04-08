# 🚀 DevOps Task 2 - CI/CD Pipeline using Jenkins & Docker

## 📌 Objective
Automate the CI/CD pipeline for a React portfolio application using Jenkins and Docker.

---

## 🛠️ Tools Used
- Jenkins  
- Docker  
- GitHub  
- Node.js  
- React  
- DockerHub  

---

## 🔄 CI/CD Pipeline Flow
1. Checkout code from GitHub repository
2. Install dependencies and build the React app
3. Build Docker image using a multi-stage Dockerfile
4. Push Docker image to DockerHub
5. Deploy the container on EC2 via Jenkins pipeline

---

## 📦 DockerHub Repository
[👉 faisalkhan15/portfolio](https://hub.docker.com/repository/docker/faisalkhan15/portfolio)

---

## ✅ Status
The Jenkins pipeline successfully builds, pushes, and deploys the React application container.

---

## 🧰 Pre-requisites & Setup Notes

- Install the following on your EC2 instance:
  - Java (for Jenkins)
  - Jenkins
  - Docker
  - Node.js and npm

- Set up DockerHub credentials in Jenkins:
  - Go to **Manage Jenkins → Credentials**
  - Add your DockerHub username and password as a **Username/Password** credential
  - Give it an ID like `dockerhub`

- Install these Jenkins plugins (required for this pipeline):
  - Git plugin
  - pipeline
  - Pipeline Stage View
  - Docker Pipeline
  - Docker Commons

- Update the `Jenkinsfile`:
  - Replace `DOCKERHUB_CREDENTIALS` with your actual Jenkins credential ID
  - Replace `faisalkhan15/portfolio` with your own DockerHub username/repo name

- Allow Jenkins to access Docker:
  ```bash
  sudo usermod -aG docker jenkins
  sudo systemctl restart jenkins

## 🔧 Additional Tip
- To auto-trigger builds on GitHub commits:
  - Enable **“GitHub hook trigger for GITScm polling”** in Jenkins
  - Add a webhook in GitHub pointing to your Jenkins URL: `/github-webhook/`
- Use Node.js version 18+ to avoid compatibility issues when building React apps.
