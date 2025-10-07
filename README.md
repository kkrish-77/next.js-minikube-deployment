## 🚀 Next.js Minikube Deployment

This project demonstrates how to containerize a Next.js app, automate CI/CD with Docker, GitHub Actions, and GitHub Container Registry (GHCR), and deploy to a local Kubernetes cluster using Minikube. It was created for a DevOps internship assessment to showcase automation, infrastructure-as-code, and efficient K8s deployment practices.

***

### 📝 **Objectives**

- **Containerize** a Next.js app using Docker best practices
- **Automate** build & image push to GHCR via GitHub Actions
- **Deploy** with Kubernetes manifests on Minikube
- **Document** setup, usage, and deployment clearly

***

### 🗂️ **Repository Structure**

```
.
├── .github/workflows/       # GitHub Actions workflows
├── k8s/                    # Kubernetes manifests (deployment, service)
├── src/app/                # Next.js app source code
├── Dockerfile              # Container image definition
├── README.md               # Project documentation
├── package.json            # Dependencies
└── ...                     # Additional configs, lockfiles, etc.
```

***

### 🛠️ **Tech Stack**

- Next.js
- Docker
- Kubernetes (Minikube)
- GitHub Actions
- GitHub Container Registry (GHCR)
- TypeScript

***

### ⚡ **Quick Start**

#### 1. **Clone Repository**

```bash
git clone https://github.com/kkrish-77/next.js-minikube-deployment.git
cd next.js-minikube-deployment
```

#### 2. **Install Dependencies**

```bash
npm install
```

#### 3. **Run Locally (Dev Mode)**

```bash
npm run dev
# App runs at http://localhost:3000
```

#### 4. **Docker Build**

```bash
docker build -t ghcr.io/<your-username>/nextjs-minikube:latest .
docker run -p 3000:3000 ghcr.io/<your-username>/nextjs-minikube:latest
```

#### 5. **CI/CD via GitHub Actions**

- On push to `main` branch:
  - Docker image builds, tags by commit/semver, and pushes to GHCR.
  - Requires GHCR_TOKEN (PAT with `write:packages`).

#### 6. **Kubernetes Deployment (Minikube)**

```bash
minikube start
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
minikube service nextjs-service
```

***

### 📦 **Project Highlights**

- **Dockerfile:** Production-ready images
- **GitHub Actions:** Fully automated—build, tag, and push to GHCR
- **Kubernetes:** Manifests with replicas, health checks, NodePort service for web access

***

### 🧰 **Useful Commands**

| Task                  | Command                                    |
|-----------------------|--------------------------------------------|
| Build Docker image    | `docker build -t image:tag .`              |
| Run container locally | `docker run -p 3000:3000 image:tag`        |
| Apply K8s manifests   | `kubectl apply -f k8s/`                    |
| Get pod status        | `kubectl get pods`                         |
| Access app (Minikube) | `minikube service nextjs-service`          |

***

### 📝 **References**
- [Next.js Documentation](https://nextjs.org/docs/)
- [Minikube Getting Started](https://minikube.sigs.k8s.io/docs/start/)
- [GitHub Actions](https://docs.github.com/en/actions)

***

### 📃 **License**

Open source under the MIT License.
