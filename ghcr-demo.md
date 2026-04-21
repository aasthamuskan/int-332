# 📦 GHCR Demo (Docker + GitHub Container Registry)

## 🎯 Objective
Learn how to:
- Build a Docker image locally  
- Push it to GitHub Container Registry (GHCR)  
- Pull and run it  

---

## 🧠 Concept (ELI5 Hinglish)

- Docker Image = ready-made app package  
- Container = running app  
- GHCR = cloud storage for images  

Flow:
Build → Push → Store → Pull → Run

---

## 📁 Project Setup

### Create Folder
mkdir ghcr-demo
cd ghcr-demo

---

## 🐳 Dockerfile

Create `Dockerfile`

FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html

### Why?
- nginx:alpine → lightweight web server  
- COPY → your HTML file will be served  

---

## 🌐 index.html

Create `index.html`

<h1>GHCR Demo Success</h1>

---

## 🔨 Build Docker Image

docker build -t ghcr.io/yourusername/ghcr-demo .

### Naming Format
ghcr.io/<username>/<image-name>

---

## 🔐 Authentication (Important)

docker login ghcr.io

Enter:
- Username → GitHub username  
- Password → Personal Access Token (PAT)  

### ⚠️ Note
- PAT ≠ GitHub password  
- Token is shown only once  

---

## 🚀 Push Image to GHCR

docker push ghcr.io/yourusername/ghcr-demo

### What happens?
- Image layers uploaded  
- Stored in GitHub Packages  

---

## 🔍 Verify on GitHub

Go to:
GitHub → Profile → Packages

---

## 🧹 Remove Local Image

docker rmi ghcr.io/yourusername/ghcr-demo

---

## 📥 Pull Image

docker pull ghcr.io/yourusername/ghcr-demo

---

## ▶️ Run Container

docker run -p 8080:80 ghcr.io/yourusername/ghcr-demo

### Port Mapping
Host (8080) → Container (80)

---

## 🌍 Output

Open browser:
http://localhost:8080

Expected:
GHCR Demo Success

---

## ⚠️ Common Errors

### ❌ Wrong image name
docker push ghcr-demo

✔ Correct:
docker push ghcr.io/username/ghcr-demo

---

### ❌ Using GitHub password
✔ Always use PAT  

---

### ❌ Not logged in
✔ Run:
docker login ghcr.io

---

### ❌ Case mismatch
ghcr.io/UserName ❌  
ghcr.io/username ✔  

---

## ⚙️ Complexity (Engineering View)

| Operation | Complexity |
|----------|----------|
| Build    | O(n) (file size) |
| Push     | O(n) |
| Pull     | O(n) |
| Run      | O(1) |

---

## 🧠 Real DevOps Insight

This workflow simulates:
- CI → Build image  
- Registry → Store image  
- CD → Pull & deploy  

---

## 🚀 Next Steps

- Add image tags (:v1, :latest)  
- Make image public/private  
- Automate using GitHub Actions  

---

## ✅ Summary

You successfully:
- Built a Docker image  
- Pushed to GHCR  
- Pulled and ran container  

👉 This is a real industry workflow (mini version)
