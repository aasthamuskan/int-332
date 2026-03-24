You can copy-paste this directly into docker-notes.md and push 🚀

# 🐳 Docker Notes (Run Commands + Flags + Environment Variables)

---

# 🧠 First Principles (ELI5)

- **Image = Blueprint 📦**
- **Container = Running Process 🏃**
- **Docker = Factory 🏭**

👉 `docker run = Image + Config + Command`

---

# 📌 Basic Commands

## Check Docker Version
```bash
docker --version
System Info
docker info
📌 Image Commands
Pull Image
docker pull httpd
List Images
docker images
Image Layers (Advanced)
docker history httpd
📌 Container Basics
Run Container
docker run ubuntu

⚠️ Problem: Container exits immediately (no process running)

📌 Important Flags
🔹 Detached Mode (-d)
docker run -d httpd
Runs in background
🔹 Interactive Mode (-it)
docker run -it ubuntu bash
Access container terminal
🔹 Name Container (--name)
docker run --name my-container httpd
🔹 Auto Delete (--rm)
docker run --rm ubuntu
🔹 Port Mapping (-p)
docker run -d -p 8080:80 httpd
Host → 8080
Container → 80

👉 Open: http://localhost:8080

🔹 Environment Variables (-e)
docker run -e MY_VAR=value ubuntu env
🔹 Volume Mount (-v)
docker run -v /host/path:/container/path ubuntu
Data persistence
📌 Running Commands Inside Container
❌ Wrong Understanding
docker run httpd echo "hello world"
Does NOT write to file
Just prints output
✅ Correct Way (Write to file)
docker run ubuntu sh -c 'echo "hello" > file.txt'
📌 Environment Variables Deep Dive
Without -e
docker run ubuntu env

👉 Only default variables

With -e
docker run -e MY_VAR=value ubuntu env
Multiple Variables
docker run -e APP_ENV=production -e APP_VERSION=1.0 nginx
Interactive Example
docker run -it -e MY_NAME=aasthamuskan ubuntu bash

Inside container:

echo $MY_NAME
📌 Passing Env Variables from Host
Method 1
export MY_VAR=hello
docker run -e MY_VAR=$MY_VAR ubuntu env
Method 2 (Auto)
export MY_VAR=hello
docker run -e MY_VAR ubuntu env
📌 Combined Example
docker run -dit \
  --name webapp \
  -p 8080:80 \
  -e APP_ENV=production \
  httpd
📌 Common Mistakes
❌ Wrong Command
docker run ununtu

✅ Correct:

docker run ubuntu
❌ Wrong Env Syntax
-e MY VAR=value

✅ Correct:

-e MY_VAR=value
❌ Using $docker
$docker --version

✅ Correct:

docker --version
🧠 Mental Model (Interview Level)

Before running container, think:

Do I need image or container?
Foreground or background?
Need terminal access?
Need external access (port)?
Need config (env variables)?
🧪 Practice Commands
docker pull httpd
docker run -d -p 8080:80 httpd
docker ps

👉 Open browser:

http://localhost:8080
🚨 Key Takeaway

👉 docker run = create + configure + start container

🔍 Checkpoint Question

Explain step-by-step:

docker run -d -p 8080:80 -e ENV=prod httpd
What happens internally?
Image → Container → Network → Process

---

# 📌 Next Step
- Isko GitHub pe upload karo  
- Phir next: **Docker networking + volumes deep dive**

If you want, I can also:
- convert this into **interview revision sheet**
- or **viva questions + answers format**