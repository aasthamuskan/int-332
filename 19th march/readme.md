# 🚀 Docker Basics & Commands – CA-1 Prep Notes

## 🧠 Core Concepts (First Principles)

* **Docker**: Tool to run applications in isolated environments (containers)
* **Image**: Blueprint (template)
* **Container**: Running instance of an image
* **Volume**: Persistent storage (data survives container deletion)
* **Network**: Communication layer between containers

---

## ⚙️ Container Commands

### Run Container

```bash
docker run -d --name <name> <image>
```

### List Containers

```bash
docker ps        # running
docker ps -a     # all
```

### Stop Container

```bash
docker stop <container>
```

### Remove Container

```bash
docker rm <container>
docker rm -f <container>   # force remove
```

---

## 🧪 Debugging Commands

### View Logs

```bash
docker logs <container>
docker logs -f <container>   # live logs
```

### Inspect Container

```bash
docker inspect <container>
```

### Resource Usage

```bash
docker stats
```

### Running Processes

```bash
docker top <container>
```

### Enter Container

```bash
docker exec -it <container> bash
```

---

## 📦 Volumes

### Create Volume

```bash
docker volume create <name>
```

### List Volumes

```bash
docker volume ls
```

### Inspect Volume

```bash
docker volume inspect <name>
```

### Use Volume

```bash
docker run -v <volume>:<path> <image>
```

### Mount Point

* Actual data location on host:

```
/var/lib/docker/volumes/<volume>/_data
```

---

## 🌐 Networks

### List Networks

```bash
docker network ls
```

### Create Network

```bash
docker network create <name>
```

### Inspect Network

```bash
docker network inspect <name>
```

### Remove Network

```bash
docker network rm <name>
```

---

## 🔁 Bulk Commands

### Stop All Containers

```bash
docker stop $(docker ps -q)
```

### Remove All Containers

```bash
docker rm $(docker ps -aq)
```

### Force Remove All

```bash
docker rm -f $(docker ps -aq)
```

### Remove All Images

```bash
docker rmi $(docker images -q)
```

---

## ⚠️ Important Differences

| Concept | Meaning                  |
| ------- | ------------------------ |
| logs    | output of container      |
| inspect | configuration + metadata |
| stats   | performance              |
| top     | running processes        |

---

## 🌐 Networking Types

| Network | Description  |
| ------- | ------------ |
| bridge  | default      |
| host    | no isolation |
| none    | no network   |

---

## 🌐 Apache Deployment Task

### Pull Image

```bash
docker pull httpd
```

### Verify Image

```bash
docker images
```

### Run Container

```bash
docker run -d --name apache-web -p 8081:80 httpd
```

### Check Running Containers

```bash
docker ps
```

### Access in Browser

```
http://localhost:8081
```

---

## 🧠 Key Mental Models

* Container = temporary compute
* Volume = permanent storage
* Network = communication layer

---

## ⚠️ Common Mistakes

* Using wrong IDs (container vs image)
* Forgetting `-d` (detached mode)
* Wrong port mapping (`:` vs `-`)
* Trying to remove running containers

---

## 🎯 Debugging Flow

1. Enter container
2. Check logs
3. Inspect configuration
4. Check processes

---

## 🏁 Final Takeaway

> Docker = Run → Connect → Store → Debug

* `logs` → what is happening
* `inspect` → how it is built
* `stats` → how it performs

---

## 🚀 Author

Prepared for CA-1 DevOps Exam Prep
