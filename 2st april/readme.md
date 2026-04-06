# 🐳 Docker Commands – Practice Notes

## 🧠 Mental Model (ELI5 – Hinglish)

Docker container = ek chhota isolated computer 📦

* Image = blueprint
* Container = running instance
* Env variable = setting/config
* Logs = system diary

---

# ✅ Q1: Run nginx container + ENV variable

## Command

```bash
docker run -d -e ENV_MODE=production --name my_nginx nginx
```

## Breakdown

* `docker run` → new container start
* `-d` → background me run
* `-e` → environment variable set
* `--name` → container name
* `nginx` → image

---

# ✅ Q2: Check logs + real-time follow

## Command

```bash
docker logs -f my_app
```

## Breakdown

* `logs` → output dekhna
* `-f` → live follow (real-time logs)

---

# ✅ Q3: Start / Stop container

## Start container

```bash
docker start web_server
```

## Stop container

```bash
docker stop web_server
```

---

# 🧠 Mental Model (Important)

| Action | Real Life Analogy     |
| ------ | --------------------- |
| run    | naya laptop ON karna  |
| start  | existing system ON    |
| stop   | shutdown              |
| logs   | system console output |
| -e     | settings/config       |

---

# ⚠️ Common Mistakes

* ❌ `-e` bhool jana → env variable set nahi hoga
* ❌ `docker logs` without `-f` → live logs nahi milenge
* ❌ `run` vs `start` confuse karna

---

# 🧪 Practice Commands

```bash
docker run -d -e MODE=test nginx

docker logs -f <container_id>

docker stop <container_id>

docker start <container_id>
```

---

# 📌 Key Rule

* `run` → new container create + start
* `start` → existing container start

---

# 🚀 Next Step

Practice with:

* Port mapping (`-p`)
* Volumes (`-v`)
* Multiple env variables

These are interview-critical topics.
