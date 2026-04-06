# Docker Volumes - Complete Practical Flow

## 🧠 Core Concept
- Container = Temporary (data lost on delete)
- Volume = Persistent (data survives)

---

## Step 1: Create Volume
docker volume create projectdata

---

## Step 2: Verify Volume
docker volume ls

---

## Step 3: Inspect Volume
docker volume inspect projectdata

Mountpoint:
 /var/lib/docker/volumes/projectdata/_data

---

## Step 4: Run Container with Volume
docker run -dit --name project_container -v projectdata:/app/data ubuntu

---

## Step 5: Create File Inside Volume
docker exec -it project_container bash

cd /app/data
echo "this is my first volume" > report.txt

---

## Step 6: Verify File
ls /app/data
cat /app/data/report.txt

---

## Step 7: Remove Container
docker rm -f project_container

---

## Step 8: Run New Container
docker run -dit --name proj_container_new -v projectdata:/app/data ubuntu

---

## Step 9: Verify Persistence
docker exec -it proj_container_new ls /app/data
docker exec -it proj_container_new cat /app/data/report.txt

---

## ✅ Expected Output
report.txt
this is my first volume

---

## ⚠️ Common Mistakes
- Creating file in /app instead of /app/data ❌
- Wrong -v syntax ❌
- Assuming container stores data ❌

---

## 🧠 Mental Model
Container = Temporary Room
Volume = Permanent Locker

---

## 🔥 Key Rule
Volume lifecycle != Container lifecycle
