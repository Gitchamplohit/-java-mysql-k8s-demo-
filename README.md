# java-mysql-k8s-app

# 🚀 Spring Boot + MySQL + Docker + Kubernetes

## 📌 Overview
This project is a **Java-Spring Boot** web application that provides a REST API for user management.
It uses **MySQL** as the database, is containerized with **Docker**, and deployed using **Kubernetes (Minikube)**.

## What the App Does

The application provides a RESTful API to manage users. It allows users to submit their details (name and email) via a POST request to the /users endpoint. The application processes the input and stores it in a MySQL database. Users can also retrieve stored user data via a GET request.

---

## **📜 Features**
✅ REST API to manage users (`/users`)
✅ Uses **MySQL** for persistent data storage
✅ Docker Compose for easy containerization
✅ Kubernetes (Minikube) deployment
✅ Accessible via http://localhost:35622/users

---
## ** Prerequisites **
Ensure you have the following installed:

1. Docker & Docker Compose
2. Minikube
3. kubectl

## ** Security & Network Configuration **

To ensure proper access to the application, configure firewall rules to allow necessary inbound ports
*Ensure that Inbound of MySQL port is allowing only the security group of Ec2 instance where webapp hosted*

## **🔧 Setup & Run Locally**

### **1️⃣ Clone the Repository**
```sh
git clone https://github.com/Gitchamplohit/java-mysql-k8s-demo.git
cd java-mysql-k8s-demo

### **2️⃣ 🐳 Containerization with Docker Compose **
1. Build the Docker image :
   ```sh
   docker build -t springboot-mysql-app .
   
2. Start the services using Docker Compose:
   ```sh
   docker-compose up -d

3. Verify the running containers:
   ```sh
   docker ps

4. Access the application at:
   http://localhost:35622/users

### **3️⃣ ☸️ Deploy on Kubernetes (Minikube)****
1️. Start Minikube 
    ```sh
    minikube start
    
2️. Deploy Spring Boot App with MySQL
    ```sh
    kubectl apply -f k8s-deployment.yml

3️. Enable Autoscaling (Web Server)
    ```sh
    kubectl autoscale deployment springboot-app --cpu-percent=50 --min=1 --max=5

4. Access the app from the Host Machine
   ```sh
   curl http://minikube-ip:35622/users

5. Use Minikube Tunnel (Optional)
   If you want to map the service to localhost instead of Minikube’s IP:
   ```sh
   minikube tunnel

   Then, access it at:
➡️ http://localhost:35622/users



📜 API Endpoints
Method	     Endpoint	       Description
 GET	      /users      	   Get all users
 POST	      /users      	   Add a new user
Example Request:

### **Verifying the Deployment**
```sh
curl -X POST http://localhost:8080/users \
     -H "Content-Type: application/json" \
     -d '{"name": "John Doe"}'

## Cleanup

To stop and remove Docker Compose containers:
 ```sh
 docker-compose down

To delete Kubernetes resources:
 ```sh
 kubectl delete all --all
 minikube stop

