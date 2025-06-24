
# 🐳 Microservices Reverse Proxy with Docker, NGINX, and AWS EC2

This project demonstrates a simple microservices architecture using:

- **Go (Service 1)**
- **Python Flask (Service 2)**
- **NGINX reverse proxy**
- **Docker + Docker Compose**
- **Hosted on an Ubuntu-based AWS EC2 instance**

All services are containerized and accessible via a single NGINX entry point on port **8080**.

---

## 📁 Project Structure

```

.
├── docker-compose.yml
├── nginx
│   ├── nginx.conf
│   └── Dockerfile
├── service\_1
│   ├── main.go
│   └── Dockerfile
├── service\_2
│   ├── app.py
│   └── Dockerfile
└── README.md

````

---

## ⚙️ Services Overview

| Service     | Tech           | Port | Endpoint                          |
|-------------|----------------|------|-----------------------------------|
| Service 1   | Go (net/http)  | 8001 | `/service1/hello`, `/service1/ping` |
| Service 2   | Python Flask   | 8002 | `/service2/`                      |
| NGINX       | Reverse Proxy  | 8080 | Routes traffic to services        |

---

## 🚀 How to Run (on Ubuntu AWS EC2)

### 1. 🔧 Launch EC2 Instance

- Choose **Ubuntu Server** 
- Open **port 8080** in Security Group:
  - Inbound Rule → Custom TCP → Port 8080 → Source: `0.0.0.0/0` (or restrict to your IP)

### 2. 🧰 Install Docker & Docker Compose

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

# Install Docker Compose (v2+)
sudo apt install docker-compose -y
````

### 3. 🗂 Clone Your Project

```bash
git clone <your-repo-url>
cd Devops-assignment
```

### 4. 🐳 Build and Run

```bash
# Start everything
sudo docker compose up -d

# Check if services are running
sudo docker-compose ps

# Tear everything down when done
sudo docker-compose down -v
```

---

## 🌐 Access the Services

Replace `<your-ec2-ip>` with your public EC2 IP.

* **Service 1 (Go):**

  * `http://<your-ec2-ip>:8080/service1/hello`
  * `http://<your-ec2-ip>:8080/service1/ping`

* **Service 2 (Flask):**

  * `http://<your-ec2-ip>:8080/service2/hello`
  * `http://<your-ec2-ip>:8080/service2/ping`

---

## ✅ Sample Output

**Service 1 – `/service1/hello`**

```json
{
  "message": "Hello from Service 1"
}
```

**Service 2 – `/service2/hello`**

```json
{
  "message": "Hello from  Service 2"
}
```

---



