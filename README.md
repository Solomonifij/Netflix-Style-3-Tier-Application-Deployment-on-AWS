# **<u>Netflix-Style 3-Tier Application Deployment on AWS</u>**

### Overview
This project demonstrates the deployment of a Netflix-style web application using a 3-tier architecture on AWS. The system is composed of a frontend, backend, and database, each hosted on separate EC2 instances to simulate a real-world production environment.

## <u>Architecture</u>
The application follows a 3-tier architecture:

- Frontend (Presentation Layer)
- Built with Node.js and served to users via a web browser.
- Backend (Application Layer)
- Developed using Java (Spring Boot) to handle business logic and API requests.
- Database (Data Layer)
- MongoDB used for storing and retrieving application data.

All components are deployed on AWS EC2 instances within a configured VPC.

## <u>AWS Infrastructure</u>

- VPC with public subnet (for learning setup)
- EC2 Instances:
- Frontend Server
- Backend Server
- Database Server
- Route Tables & Internet Gateway
- Security Groups for controlled access between layers

## <u>Tech Stack</U>

- Frontend: Node.js
- Backend: Java (Spring Boot)
- Database: MongoDB
- Cloud Provider: AWS (EC2, VPC)

# <u>Deployment Steps</u>

## 1. **Infrastructure Setup**

- Created a VPC and subnet
- Configured route tables and internet access
- Launched three EC2 instances (frontend, backend, database)
- 
## 2. **Database Setup (MongoDB)**

- Installed MongoDB on the database server
- Configured remote access (bindIp: 0.0.0.0)
- Opened port 27017 in security group (restricted access)
- Verified connection using Mongo shell and GUI tools

## 3. **Backend Deployment (Java Spring Boot)**
- Cloned backend repository from GitHub
- Configured MongoDB connection in application.properties:
  
```spring.data.mongodb.uri=mongodb://<DB_PUBLIC_IP>:27017/netflix_db```

- Built and ran the application
- Tested API endpoints

## 4. **Frontend Deployment (Node.js)**

- Cloned frontend repository
- Installed dependencies:
  
```npm install```

- Updated API base URL to backend server
- Built and served the application:
  
```npm run build```
```npx serve -s build -l 80```

## 5. **Access Application**

Open browser and navigate to:

<pre markdown="1">```bash http://<FRONTEND_PUBLIC_IP>:3000 ```</pre>

## **<u>Security Configuration</u>**

### -**Frontend**

- Ports: 80, 443 open to public
- SSH restricted to personal IP

### -**Backend**

- Port 8080 open only to frontend server
- SSH restricted

### -**Database**

- Port 27017 open only to backend server
- SSH restricted

## **<u>Testing</u>**

- Verified backend API responses via browser and curl
- Tested database connectivity from backend server
- Connected to MongoDB using MongoDB Compass
- Confirmed full data flow: Frontend → Backend → Database

## **<u>Challenges & Troubleshooting</u>**

- MongoDB package not available in default Ubuntu repo → resolved using official MongoDB repository
- Connection errors due to incorrect ports and security group rules
- Frontend build delays and environment configuration issues
- Debugging backend-to-database connectivity

## **<u>Conclusion</u>**

This project successfully demonstrates a full-stack application deployed on AWS, integrating frontend, backend, and database layers into a functional system. It highlights practical experience in cloud infrastructure, deployment, and troubleshooting.

  
