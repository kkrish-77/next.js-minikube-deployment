Next.js Minikube Deployment
🚀 Overview
This project demonstrates how to containerize a Next.js application, automate its CI/CD workflow using Docker, GitHub Actions, and the GitHub Container Registry (GHCR), and deploy it to a local Kubernetes cluster with Minikube. The repository is created as part of a DevOps Internship Assessment to showcase key DevOps practices—automation, infrastructure-as-code, and efficient Kubernetes deployment.

📝 Assessment Objectives
Containerize a Next.js app using Docker (with best practices)

Automate build & image push to GHCR using GitHub Actions

Deploy to Kubernetes (Minikube) via manifest files

Document all processes with clear setup, usage, and deployment instructions

🗂️ Repository Structure
text
.
├── .github/
│   └── workflows/         # GitHub Actions workflow(s)
├── k8s/                   # Kubernetes manifests (deployment, service)
├── src/app/               # Source code of Next.js application
├── Dockerfile             # Docker image definition
├── README.md              # Project documentation
├── package.json           # Project dependencies
└── ...                    # Additional configs, lockfiles, etc.
🛠️ Technology Stack
Next.js

Docker

Kubernetes (via Minikube)

GitHub Actions

GitHub Container Registry (GHCR)

TypeScript

⚡ Quick Start
1. Local Development
bash
# Clone the repository
git clone https://github.com/kkrish-77/next.js-minikube-deployment.git
cd next.js-minikube-deployment

# Install dependencies
npm install

# Run the development server
npm run dev
# App is now running at http://localhost:3000
2. Docker Containerization
bash
# Build Docker image (replace <tag> as needed)
docker build -t ghcr.io/<your-github-username>/nextjs-minikube:<tag> .

# Run locally (optional)
docker run -p 3000:3000 ghcr.io/<your-github-username>/nextjs-minikube:<tag>
3. GitHub Actions - CI/CD
GitHub Actions is configured to:

Build the Docker image on every push to the main branch

Tag the image by commit SHA or version

Push the image to the GitHub Container Registry (GHCR)

Secrets Required:

GHCR_TOKEN: GitHub PAT with write:packages scope

See .github/workflows/ for the pipeline definition.

4. Kubernetes Deployment (Minikube)
a. Start Minikube
bash
minikube start
b. Pull Image (if not public)
Authenticate your local Docker to GHCR if needed.

c. Apply Kubernetes Manifests
bash
# Inside the project root
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
d. Access the Application
bash
minikube service nextjs-service
# This will open the app in your default browser
📂 Project Highlights
Dockerfile: Multi-stage build for efficient, production-ready images

Actions Workflow: End-to-end automation—build, tag, and push to GHCR on main branch update

Kubernetes Manifests:

deployment.yaml: Configures replicas, health checks (livenessProbe/readinessProbe)

service.yaml: Exposes your app via NodePort for easy access via Minikube

🧰 Useful Commands
Task	Command
Build Docker image	docker build -t <image:tag> .
Run container locally	docker run -p 3000:3000 <image:tag>
Apply k8s manifests	kubectl apply -f k8s/
Get pod status	kubectl get pods
View service (Minikube)	minikube service nextjs-service
📝 References
Next.js Official Docs

Minikube Tutorials

GitHub Actions Docs

📃 License
This project is open source under the MIT License.