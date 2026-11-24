# Docker Hands-on Workshop (SDP 2026)

This project contains a web application packaged and served with Nginx in a Docker container, designed for Docker and Kubernetes (Minikube) hands-on practice.

---

## 📁 Project Structure

- `Dockerfile`: Container image definition copying `index.html` and `style.css` into an Nginx image.
- `kubernetes/`:
  - `deployment.yaml`: Kubernetes Deployment manifest configuring 3 replicas of `mevi-web:v1`.
  - `service.yaml`: Kubernetes NodePort Service manifest exposing `mevi-web` on port 80 (NodePort 30080).
- `index.html`: Web page for the Docker workshop.
- `style.css`: Styling for the web page.

---

## 🐳 Docker Commands

### 1. Build Image
```bash
docker build -t mevi-web:v1 .
```

### 2. Run Container
```bash
docker run -d -p 8080:80 --name my-website mevi-web:v1
```
Access the application in your browser at: [http://localhost:8080](http://localhost:8080)

---

## ☸️ Kubernetes (Minikube) Deployment

### 1. Start Minikube
```bash
minikube start
```

### 2. Load Local Image into Minikube
```bash
minikube image load mevi-web:v1
```

### 3. Deploy to Cluster
```bash
kubectl apply -f kubernetes/
```

### 4. Check Status
```bash
kubectl get pods
kubectl get services
```

### 5. Access the Kubernetes Service
```bash
minikube service mevi-web
```
