Sure! Here is a **clean, well-structured README.md** based on everything you wrote — organized for fast revision and easy understanding.

---

# 📘 Docker Fundamentals — Quick Revision Notes

---

## 🚀 **1. Data in Containers is Ephemeral**

* Any data created *inside a running container* is **lost when the container is removed**.
* Reason: A container’s filesystem is isolated and tied to its lifecycle.

---

## 📦 **2. Data Built Into the Image**

* Data that must always exist when the container starts (e.g., **Node modules**, binaries, configs) should be **added in the Docker image**.
* Image consists of **read-only layers**.
* Only the **top container layer** is **read/write (R/W)** and **ephemeral**.

---

## 💾 **3. Persisting Application-Generated Data**

If the container generates data that must survive:

### Use:

1. **Volumes (docker-managed)**
2. **Bind Mounts (host folder → container folder)**

✔ Ensures data persists even if container is deleted.

---

## ⚡ **4. RUN Commands Create Layers**

* Each `RUN`, `COPY`, `ADD` command creates a **new layer**.
* Many layers → slow build + poor caching.
* Solution: **Combine commands** for optimization.

---

## 🏗️ **5. Multistage Docker Builds**

Used to reduce image size and separate build environment from runtime.

### ✔ Key Points:

* Dockerfile is split into **multiple stages**.
* Final stage is very small — includes only runtime files.
* Example:

```dockerfile
FROM node:18 AS build
RUN npm install

FROM node:18-slim
COPY --from=build /app /app
CMD ["node", "app.js"]
```

---

## 🦴 **6. Distroless Images**

* Ultra-minimal images with **no shell**, **no package manager**, **no utilities** (curl, nano, etc.).
* Only contain the **application runtime**.
* Very secure and tiny in size.
* Golang apps can even run on distroless **static** with no runtime.

---

## 🏛️ **7. Container Registry**

A storage system for container images.

Examples:

* Docker Hub
* GitHub Container Registry
* Google Artifact Registry
* AWS ECR

Registry → Repository → Tags → Images

---

## 🟢 **8. Docker Run Commands (Cheat Sheet)**

### ▶ `-d` (detached mode)

Runs in the background.

```
docker run -d ubuntu sleep 7
```

### ▶ `--entrypoint` (override default entrypoint)

```
docker run --entrypoint echo ubuntu hello
```

### ▶ `--env` Add environment variables

```
docker run --env MY_ENV=hello ubuntu printenv
```

### ▶ `--init`

Adds a tiny init process inside container.

```
docker run --init ubuntu ps
```

### ▶ `-it` Interactive terminal session

```
docker run -it ubuntu
```

### ▶ `--mount` (cache, bind, volume)

Used for caching or mounting directories.

```
docker run --mount type=cache,target=/root/.cache ...
```

### ▶ `--name`

Assigns container a custom name.

```
docker run -d --name my-container ubuntu sleep 20
```

### ▶ `--network`

Connect container to a network.

```
docker network create my-network
docker run -d --network my-network ubuntu sleep 14
```

### ▶ `--publish` (port mapping)

```
docker run -p 8080:80 nginx
```

---

## 🔍 **9. Useful Container Commands**

| Command                     | Purpose                |
| --------------------------- | ---------------------- |
| `docker container inspect`  | View container details |
| `docker container rm`       | Remove container       |
| `docker rm -f`              | Force remove           |
| `docker stop`               | Stop running container |
| `docker logs <id>`          | Show logs              |
| `docker exec -it <id> bash` | Exec inside container  |

---

## 🧱 **10. Docker Objects**

Docker manages four main objects:

1. **Images**
2. **Containers**
3. **Volumes**
4. **Networks**

---

## 🔐 **11. Image Vulnerability Scan**

Check CVEs inside an image:

```
docker image scout cves image-name
```

---

