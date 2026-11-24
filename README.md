# Docker Hands-on Workshop (SDP 2026)

This project contains a simple web application packaged and served with Nginx in a Docker container, designed for Docker and Kubernetes (Minikube) hands-on practice.

---

## 📁 Project Structure

- `Dockerfile`: Nginx-based image definition copying `index.html` and `style.css`.
- `index.html`: Web page for the Docker workshop.
- `style.css`: Styling for the web page.
- `k8s-deployment.yaml`: Kubernetes Deployment and Service manifest for Minikube.

---

## 🐳 Docker Commands

### 1. Build the Docker Image
```bash
docker build -t sdp-app:latest .
```

### 2. Run the Container
```bash
docker run -d -p 8080:80 --name sdp-website sdp-app:latest
```
Access the application in your browser at: [http://localhost:8080](http://localhost:8080)

### 3. Manage the Container
- View running containers: `docker ps`
- View container logs: `docker logs sdp-website`
- Stop container: `docker stop sdp-website`
- Remove container: `docker rm sdp-website`

---

## ☸️ Kubernetes (Minikube) Deployment

### 1. Start Minikube
```bash
minikube start
```

### 2. Load Local Image into Minikube
Since Minikube runs inside its own isolated environment, load your locally built Docker image into it:
```bash
minikube image load sdp-app:latest
```

### 3. Deploy to Cluster
```bash
kubectl apply -f k8s-deployment.yaml
```

### 4. Check Status
```bash
kubectl get pods
kubectl get services
```

### 5. Access the Kubernetes Service
```bash
minikube service sdp-service
```
Or forward the port directly:
```bash
kubectl port-forward service/sdp-service 8080:80
```
