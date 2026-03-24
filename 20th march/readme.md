# 🐳 Docker Apache (httpd) Practice Guide

---

## 🧠 Core Mental Model

```
Image → Container → Port Mapping → Browser
```

* **Image** = Blueprint 📦
* **Container** = Running instance 🚀
* **Port Mapping** = Bridge between laptop & container 🌐

---

# ⚙️ 1. Pull Apache Image

```bash
docker pull httpd
```

### Verify

```bash
docker images httpd
```

---

# ⚙️ 2. Run Container

```bash
docker run -d -p 8081:80 --name task3 httpd
```

### Breakdown

* `-d` → background run
* `-p 8081:80` → localhost:8081 → container:80
* `--name task3` → custom name

---

# ⚙️ 3. Check Running Containers

```bash
docker ps
```

### All containers

```bash
docker ps -a
```

---

# 🌐 4. Access in Browser

```
http://localhost:8081
```

---

# 🧩 5. Modify Content (Method 1: docker exec)

## Enter container

```bash
docker exec -it task3 /bin/bash
```

## Go to Apache folder

```bash
cd /usr/local/apache2/htdocs/
```

## Update file

```bash
echo "<h1>Hello Aastha 🚀</h1>" > index.html
```

## Exit

```bash
exit
```

---

# 🧩 6. Modify Content (Method 2: Volume Mount)

## Remove old container

```bash
docker rm -f task3
```

## Create folder + file

```bash
mkdir mysite
cd mysite
echo "<h1>From Local Folder 🚀</h1>" > index.html
```

## Run with volume

```bash
docker run -d -p 8081:80 \
--name task3 \
-v $(pwd):/usr/local/apache2/htdocs/ \
httpd
```

---

# ⚠️ Important Concepts

## Apache serves only:

```
index.html
```

---

## Container Immutability

```
Container = temporary
Image = permanent
```

---

# ❌ Common Errors

### 1. Name conflict

```
container name already in use
```

### Fix:

```bash
docker rm -f task3
```

---

### 2. Image not found

```
Unable to find image 'httpd'
```

### Fix:

```bash
docker pull httpd
```

---

### 3. vi not found

```
vi: command not found
```

### Fix:

```bash
echo "<h1>text</h1>" > index.html
```

---

### 4. Wrong place for URL

❌ Terminal:

```
http://localhost:8081
```

✅ Browser

---

# 🧠 DevOps Mindset

```
DO NOT GUESS → ALWAYS VERIFY
```

Commands:

```bash
docker images
docker ps
docker logs <container>
```

---

# 🔁 Full Practice Flow

```bash
# Clean

docker rm -f task3

# Pull

docker pull httpd

# Run

docker run -d -p 8081:80 --name task3 httpd

# Verify

docker ps

# Modify

docker exec -it task3 /bin/bash
cd /usr/local/apache2/htdocs/
echo "<h1>Practice 🚀</h1>" > index.html
exit
```

---

# 🚀 Interview Key Points

* Port mapping: `host:container`
* Container lifecycle: create → run → stop → remove
* Volume vs exec difference
* Why containers are temporary

---

# 🧠 Final Summary

```
Pull → Run → Verify → Modify → Access
```

---

# 🎯 Next Level Topics

* Dockerfile (COPY vs volume)
* Container networking
* Logs & debugging
* Multi-container setup

---

End of Notes ✅
