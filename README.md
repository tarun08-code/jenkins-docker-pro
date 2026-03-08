# CI/CD Pipeline with Jenkins (Docker) for React Portfolio

## Project Overview

This project demonstrates a complete CI/CD pipeline using **Jenkins running inside a Docker container** to automatically build and deploy a React portfolio website.

The pipeline automates the process from **code commit to production deployment**.

This was my second DevOps project.  
My first CI/CD pipeline was deployed on an **AWS server**, but for this project I challenged myself by running **Jenkins inside a Docker container on my local machine**.

The goal was to understand how CI/CD works inside containerized environments and handle real-world pipeline issues.

---

## Architecture
Developer Push
│
▼
GitHub Repository
│
▼
Jenkins (Running inside Docker)
│
▼
Install Dependencies
│
▼
Build React Application
│
▼
Deploy to Netlify

---

## Tech Stack

- Docker
- Jenkins
- GitHub
- Node.js
- Netlify
- React

---

## Pipeline Stages

### 1️⃣ Clone Repository
Jenkins clones the React portfolio project from GitHub.

git clone

### 2️⃣ Install Dependencies

All project dependencies are installed using npm.

npm install

### 3️⃣ Build React Application

The React application is built using:

npm run build


This generates the **dist/** folder used for deployment.

---

### 4️⃣ Deploy to Netlify

The build artifacts are deployed to Netlify using the Netlify CLI.

netlify deploy --prod --dir=dist


---

## Jenkins Pipeline

![alt text](<screenshots/Screenshot 2026-03-06 215810.png>)

---

## Jenkins Stages View

![alt text](<screenshots/Screenshot 2026-03-06 215736.png>)

---

## Docker Jenkins Container

![alt text](<screenshots/Screenshot 2026-03-06 211210.png>)

---

## Netlify Deployment

![alt text](<screenshots/Screenshot 2026-03-06 220020.png>)

---

## Challenges Faced

During the development of this pipeline several real-world issues were encountered and resolved:

- Jenkins branch detection issues
- Node.js and npm missing in Jenkins container
- Docker container permission errors
- Netlify CLI authentication issues
- Workspace ownership problems
- Incorrect build directory configuration (build vs dist)
- Jenkins pipeline debugging

These challenges helped me understand how CI/CD systems behave in containerized environments.

---

## Learning Outcomes

Through this project I gained practical experience with:

- Running Jenkins inside Docker
- Creating CI/CD pipelines using Jenkins
- Automating build and deployment workflows
- Debugging containerized environments
- Handling permissions inside Docker
- Integrating Netlify deployments into CI/CD pipelines

---

## Future Improvements

Next improvements planned for this pipeline:

- Build Docker images inside Jenkins
- Push images to Docker Hub
- Deploy containers automatically
- Add Jenkins agents for scalable builds

---

## Author

Dineshtarun G

DevOps | Cloud | 

For using 

# Pull jenkins
docker pull tarun08code/jenkins:lts

# Running container with volume attached 
docker run -d \
  -p 8081:8080 \
  -v jenkins_home:/var/jenkins_home \
  --name jenkins \
  tarun08code/jenkins:lts
