## 1️⃣ Forward Proxy (Proxy)

### What it is

A **forward proxy** sits **between the client and the internet**.
It represents the **client**.

### Who configures it?

👉 **Client** (browser / OS knows the proxy)

### Main purposes

* Hide **client IP**
* Internet access control (block sites)
* Caching (speed up browsing)
* Monitoring user activity

### Real-life example

You → Office Proxy → google.com
(google.com never sees *your* IP)

---

## 2️⃣ Reverse Proxy

### What it is

A **reverse proxy** sits **between the internet and servers**.
It represents the **server**.

### Who configures it?
👉 **Server / DevOps team**

### Main purposes
* Hide backend servers
* SSL termination (HTTPS handling)
* Caching
* Security (WAF, rate limiting)
* Routing requests to services

### Real-life example

You → nginx → app_server
(you never directly access the app server)

---

## 3️⃣ Load Balancer
### What it is

A **load balancer** is a **specialized reverse proxy** that distributes traffic across **multiple servers**.

### Who configures it?

👉 **Server / Cloud / DevOps team**

### Main purposes

* Distribute load
* High availability
* Fault tolerance
* Scale applications



### Load balancing algorithms

* Round Robin
* Least Connections
* IP Hash
* Weighted




## 🧠 Easy Memory Trick (Exam Tip)

* **Proxy** → protects **CLIENT**
* **Reverse Proxy** → protects **SERVER**
* **Load Balancer** → protects **SERVER + SCALE**

---

## 🧩 Relationship Between Them

* A **load balancer is a type of reverse proxy**
* Not all reverse proxies do load balancing
* Forward proxy is totally different

---

## 🧪 One-line Definitions (for exams)

* **Forward Proxy:** Intermediary that forwards client requests to the internet.
* **Reverse Proxy:** Intermediary that forwards internet requests to backend servers.
* **Load Balancer:** A reverse proxy that distributes traffic among multiple servers.

---
