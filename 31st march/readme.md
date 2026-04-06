# 🐳 Docker Commands Practice (Hands-on Notes)

---

## 🔥 1. Run Container

```bash
docker run -d -p 8080:80 --name my-nginx nginx
```

👉 Use: Start nginx container in background and expose port

---

## 📜 2. Logs

```bash
docker logs <container_id>
```

👉 Use: View past logs

```bash
docker logs -f <container_id>
```

👉 Use: View live logs (real-time)

---

## 📊 3. Stats

```bash
docker stats
```

👉 Use: Monitor CPU, memory, network usage

---

## 🧠 4. Exec (Enter Container)

```bash
docker exec -it <container_id> bash
```

👉 Use: Open terminal inside running container

⚠️ If bash not available:

```bash
docker exec -it <container_id> sh
```

---

## ❌ Common Mistake

```bash
docker exec -it <container_id>
```

👉 ❌ Missing command (bash/sh required)

---

## 📁 5. File Operations Inside Container

```bash
mkdir /data
echo "hello docker" > /data/test.txt
```

👉 Use: Create folder and file inside container

---

## 📂 6. Copy Files (Container ↔ Host)

### Container → Host

```bash
docker cp <container_id>:/data/test.txt ~/Desktop
```

### Host → Container

```bash
docker cp ~/Desktop/test.txt <container_id>:/data/sample.txt
```

👉 Use: Transfer files between host and container

---

## ❌ Wrong Path Issue

```bash
docker cp <container_id>:/data/test.txt C:\Users\HP\Desktop
```

👉 ❌ Windows path on Mac/Linux

---

## 📄 7. Read File Inside Container

```bash
docker exec -it <container_id> cat /data/sample.txt
```

👉 Use: Read file content

---

## ❌ Wrong Command

```bash
docker exec -it <container_id> ls cat /data/sample.txt
```

👉 ❌ Multiple commands incorrectly passed

---

## ✅ Correct Multiple Commands

```bash
docker exec -it <container_id> sh -c "ls /data && cat /data/sample.txt"
```

---

## ⚠️ 8. docker attach (Danger)

```bash
docker attach <container_id>
```

👉 Use: Attach to main container process

⚠️ Pressing Ctrl+C will STOP container

---

## 🧠 Mental Model

| Command        | Meaning                      |
| -------------- | ---------------------------- |
| docker run     | create + start container     |
| docker exec    | run command inside container |
| docker logs    | past logs                    |
| docker logs -f | live logs                    |
| docker stats   | resource usage               |
| docker cp      | file transfer                |
| docker attach  | control main process         |

---

## ⚡ Key Learnings

* Always specify command with `docker exec`
* Use correct OS paths (Mac/Linux vs Windows)
* Avoid `attach` unless necessary
* Use `logs -f` for debugging
* Understand command structure before combining

---

## 🚀 Next Topics

* exec vs attach vs run
* volumes vs docker cp
* container restart & debugging
* nginx custom HTML deployment

---


