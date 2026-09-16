# GitHub Actions CI/CD Pipeline Setup

## Pipeline Stages

1. **Fetch from GitHub** - Code checkout karta hai
2. **Build Application** - npm dependencies install karta hai  
3. **Create Docker Image** - Dockerfile se image build karta hai
4. **Push to Docker Hub** - Image ko Docker Hub pe push karta hai

## Setup Steps

### Step 1: Add GitHub Secrets
GitHub repo settings mein jao aur ye secrets add karo:
- `DOCKER_USERNAME` - Aapka Docker Hub username
- `DOCKER_PASSWORD` - Aapka Docker Hub password ya token

**How to add secrets:**
1. GitHub repo > Settings > Secrets and variables > Actions
2. Click "New repository secret"
3. Add above secrets

### Step 2: Push Code to GitHub
```bash
git add .
git commit -m "Add GitHub Actions CI/CD pipeline"
git push origin main
```

### Step 3: Verify Pipeline
1. GitHub repo > Actions tab
2. Latest workflow run dekho
3. Har step successfully complete hona chahiye

## Pipeline Workflow File
Location: `.github/workflows/ci-cd.yml`

Pipeline trigger hota hai jab:
- Main branch pe push hota hai
- Pull request main branch ke liye create hota hai

## Docker Hub Image Access
Pipeline complete hone ke baad, image yahan available hoga:
```
docker pull <DOCKER_USERNAME>/devops-app:latest
docker pull <DOCKER_USERNAME>/devops-app:<commit-sha>
```

## Run Locally
```bash
npm install
node app.js
# App runs on http://localhost:3000
```

## Build & Run Docker Locally
```bash
docker build -t devops-app:latest .
docker run -p 3000:3000 devops-app:latest
```
