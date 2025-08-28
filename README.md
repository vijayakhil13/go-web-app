<<<<<<< HEAD
# Go Web Application

This is a simple website written in Golang. It uses the `net/http` package to serve HTTP requests.

## Running the server

To run the server, execute the following command:

```bash
go run main.go
```

The server will start on port 8080. You can access it by navigating to `http://localhost:8080/courses` in your web browser.

## Looks like this

![Website](static/images/golang-website.png)


=======
# go-web-app
>>>>>>> e51dc0f1a83ee9dd191c860f1896395eaa04f657



# 🚀 Go Web App on AWS EKS ☁️

Welcome to the **Go Web App** project! This repo contains everything needed to deploy a containerized Go web application on AWS EKS using Docker, Kubernetes, and a full CI/CD pipeline with GitHub Actions and ArgoCD. 🎉


## 🛠️ Project Overview

- 🖥️ **Launch**: EC2 instance (Ubuntu) on AWS for app hosting and development  
- 🐳 **Containerize**: Dockerize the Go app, expose port 8080  
- ☁️ **Cloud Native**: Push Docker image to Docker Hub  
- ☸️ **Kubernetes**: Deploy on EKS with deployments, services, and ingress  
- 📡 **Ingress Setup**: Expose app with NGINX ingress controller and custom DNS  
- 🔄 **CI/CD Pipeline**: GitHub Actions for build, test, push, and deploy automation  
- ⚙️ **GitOps**: ArgoCD for continuous deployment  


## 📝 Setup Instructions

1. **EC2 Setup**  
   - Launch t2.medium Ubuntu EC2 instance on AWS  
   - SSH into the instance with your public IP  

2. **Clone the Repository**  
   ```
   git clone <repo-url>
   cd go-web-app
   ```

3. **Dockerize the App**  
   - Build your Docker image:  
     ```
     docker build -t go-web-app:latest .
     ```  
   - Run Docker container:  
     ```
     docker run -d -p 8080:8080 go-web-app:latest
     ```  

4. **Push Image to Docker Hub**  
   ```
   docker login
   docker push <your_dockerhub_username>/go-web-app:latest
   ```

5. **Setup AWS EKS**  
   - Install AWS CLI & `eksctl` locally  
   - Configure AWS credentials:  
     ```
     aws configure
     ```  
   - Create your EKS cluster and verify nodes:  
     ```
     eksctl create cluster --name go-web-cluster --region us-west-2
     kubectl get nodes
     ```

6. **Kubernetes Deployment & Service**  
   - Update deployment YAML with your Docker image  
   - Deploy:  
     ```
     kubectl apply -f deployment.yaml
     kubectl apply -f service.yaml
     kubectl get pods,svc
     ```

7. **Ingress & NGINX Controller Setup**  
   - Add NGINX ingress controller via Helm:  
     ```
     helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
     helm install nginx-ingress ingress-nginx/ingress-nginx
     ```  
   - Apply ingress resource:  
     ```
     kubectl apply -f ingress.yaml
     ```  
   - Update local `/etc/hosts` to map your DNS to Load Balancer IP  

8. **CI/CD Pipeline with GitHub Actions & ArgoCD**  
   - Commit and push changes to trigger the GitHub Actions pipeline 🚦  
   - ArgoCD syncs your Kubernetes manifests for continuous deployment ⚙️  

---

## 📌 Key Commands Summary

| Action                           | Command                                 |  
|---------------------------------|-----------------------------------------|  
| Clone Repo                      | `git clone <repo-url>`                   |  
| Build Docker Image              | `docker build -t go-web-app:latest .`   |  
| Run Docker Container            | `docker run -d -p 8080:8080 go-web-app` |  
| Push Image                     | `docker push <username>/go-web-app:latest` |  
| Create EKS Cluster              | `eksctl create cluster ...`              |  
| Deploy Kubernetes Resources     | `kubectl apply -f <manifest>.yaml`      |  
| Install NGINX Ingress Controller| `helm install nginx-ingress ...`         |  
| Edit /etc/hosts                 | `sudo vim /etc/hosts`                     |  

---

## ❤️ Contributions

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/yourusername/go-web-app/issues). 
