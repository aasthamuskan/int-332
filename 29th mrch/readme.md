#  Docker Basics & Core Commands (Hands-on Notes)

## 1. Docker Run Command
### Syntax
```bash
docker run [OPTIONS] IMAGE [COMMAND]
Example
docker run -d -p 8080:80 nginx
Breakdown
Option	Meaning
-d	Run container in background
-p	Port mapping (host:container)
nginx	Image name
🔌 Port Mapping
-p HOST_PORT:CONTAINER_PORT
Example
-p 8080:80
Host	Container
8080	80

👉 Browser → localhost:8080
👉 Container → port 80

⚠️ Key Concept

UI tabhi dikhega jab container ke andar server run ho

Image	UI
ubuntu	❌
nginx/httpd	✅
📦 Container Lifecycle
Action	Command
Create + Run	docker run
Stop	docker stop <id>
Start	docker start <id>
Remove	docker rm <id>
🧠 docker ps
Running containers
docker ps
All containers
docker ps -a

👉 -a = all (running + stopped + exited)

🗑️ Remove Container
docker rm <container_id>
Force remove
docker rm -f <container_id>
🧱 Docker Images
List images
docker images
Remove image
docker rmi <image_id>
Force remove
docker rmi -f <image_id>
⚠️ Important Rule

Container depend karta hai image pe
Image delete nahi hogi agar container exist karta hai

🧪 MySQL Container Example
docker run -d -p 3307:3306 \
--name mysql-test \
-e MYSQL_ROOT_PASSWORD=root123 mysql
Connect from host
mysql -h 127.0.0.1 -P 3307 -u root -p
🔐 Environment Variables
Set variable
docker run -it -e collage=cse ubuntu bash
Access variable
echo $collage
Key Concept

Env variables are temporary (lost after container stops)

🧪 docker exec
Purpose

Run command inside running container

Syntax
docker exec -it <container_id> <command>
Examples
Open bash
docker exec -it <id> bash
View environment variables
docker exec -it <id> env
Run command via bash
docker exec -it <id> bash -c "env"
❌ Common Mistake
bash/env ❌

👉 Invalid because:

/ is path separator
not command chaining
🧠 Core Concepts
1. Container = Process

Container tab tak hi chalta hai jab tak main process chal raha hai

2. Ephemeral Nature

Container temporary hota hai (data lost on delete)

3. Foreground vs Background
Mode	Behavior
Without -d	terminal block
With -d	background
4. Ubuntu vs Nginx
Feature	Ubuntu	Nginx
OS	✅	✅
Web server	❌	✅
UI support	❌	✅
🔥 Debugging Workflow
Check running containers
docker ps
Check all containers
docker ps -a
Check logs
docker logs <id>
🧠 Mental Models
Container

Temporary running process

Image

Blueprint/template

Port Mapping

Bridge between host and container

💣 Golden Rules
Always check docker ps -a for debugging
Never blindly use -f
Use purpose-built images (nginx, mysql)
Container ≠ OS only, it needs a running process
🚀 Next Learning Path
Docker Volumes (data persistence)
Docker Networks
Dockerfile (custom images)
Multi-container apps (Docker Compose)

---

## 🎯 What you should do now

1. Copy this into a file:

docker-notes.md


2. Push to GitHub:
```bash
git add docker-notes.md
git commit -m "Added Docker fundamentals notes"
git push