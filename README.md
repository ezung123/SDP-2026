# Docker Hands-on Workshop (SDP 2026)

This project contains a web application packaged and served with Nginx in a Docker container, designed for Docker and Kubernetes (Minikube) hands-on practice.

---

## 📁 Project Structure

- `Dockerfile`: Container image definition copying `index.html` and `style.css` into an Nginx image.
- `docker-compose.yaml`: Docker Compose deployment file to run the multi-container / service configuration with Docker.
- `deployment.yaml`: Kubernetes Deployment and Service manifest configured for `mevi-webv1` on Minikube.
- `index.html`: Web page for the Docker workshop.
- `style.css`: Styling for the web page.

---

## 🐳 Docker Deployment

### Option A: Using Docker Compose (Recommended for Docker)
```bash
# Start container in background
docker compose up -d

# Check status
docker compose ps

# View logs
docker compose logs -f

# Stop container
docker compose down
```
Access the application in your browser at: [http://localhost:8080](http://localhost:8080)

### Option B: Using Plain Docker CLI
```bash
# 1. Build image
docker build -t mevi-webv1 .

# 2. Run container
docker run -d -p 8080:80 --name mevi-website mevi-webv1
```

---

## ☸️ Kubernetes (Minikube) Deployment

### 1. Start Minikube
```bash
minikube start
```

### 2. Load Local Image into Minikube
```bash
minikube image load mevi-webv1
```

### 3. Deploy to Cluster
```bash
kubectl apply -f deployment.yaml
```

### 4. Check Status
```bash
kubectl get pods
kubectl get services
```

### 5. Access the Kubernetes Service
```bash
minikube service mevi-web-service
```
