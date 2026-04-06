# Docker DevOps Practice Notes

## 1. Deploy Apache (httpd) Container

### Key Concepts
- Container = isolated environment
- Apache serves files from: /usr/local/apache2/htdocs/

### Steps
1. Run container with port mapping
2. Add HTML file inside container
3. Verify using curl
4. Stop and remove container

### Common Mistakes
- Wrong path (/usr/apache2 ❌)
- Container not running
- Using bash when not available

---

## 2. MongoDB Port Mapping Insight

### Default Port
- MongoDB runs on 27017

### Key Learning
- Mapping wrong ports works syntactically but fails logically
- Example:
  - 80:8082 ❌ (wrong)
  - 8080:27017 ✅ (correct)

---

## 3. Docker Volume Error (Mac)

### Error
mounts denied: path not shared

### Fix
- Use home directory:
  ~/data:/data
- Or add path in Docker Desktop → File Sharing

---

## 4. Docker Run Flags

### Command
docker run -it --name my-app -e APP_ENV=production -v ~/data:/data ubuntu bash

### Meaning
- -it → interactive terminal
- --name → container name
- -e → environment variable
- -v → bind mount

---

## 5. Docker Commands Cheat Sheet

### Basic Commands
docker pull nginx
docker run nginx
docker ps
docker ps -a

### Lifecycle Commands
docker stop container
docker kill container
docker pause container
docker unpause container

### Removal
docker rm container
docker rm $(docker ps -aq)
docker rm $(docker ps -aq -f status=exited)

### Utility
docker rename old new

---

## 6. Important Differences

### stop vs kill
- stop → graceful shutdown
- kill → force shutdown

### run vs start
- run → create + start
- start → start existing

### pause vs stop
- pause → freeze
- stop → shutdown

---

## 7. Mental Model

Container lifecycle:
create → run → pause → unpause → stop → kill → remove

---

## 8. Key DevOps Learnings

- Always verify paths inside container
- Prefer volumes over manual exec
- Understand system, not just commands
- Debug step-by-step

---

## 9. Practice Challenges

- Why docker exec is not production safe?
- Difference between bind mount vs volume?
- Why Mac needs file sharing but Linux doesn’t?

---

End of Notes
