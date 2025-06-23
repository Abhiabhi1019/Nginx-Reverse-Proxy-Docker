# Multi-Service Reverse Proxy with Docker (Golang + Python + NGINX)

This project demonstrates a microservices setup using:

-  Golang service (Service 1)
-  Python Flask service (Service 2)
-  NGINX as a reverse proxy

All services run in isolated Docker containers and are accessible via a single entry point.

---

##  Project Structure

.
├── docker-compose.yml
├── nginx/
│ ├── Dockerfile
│ └── nginx.conf
├── service_1/
│ ├── Dockerfile
│ └── main.go
├── service_2/
│ ├── Dockerfile
│ ├── app.py
│ └── requirements.txt

Routing (via NGINX)

| Path                    | Routed To             |
|-------------------------|-----------------------|
| `/service1/hello`       | Go app at port `8000` |
| `/service2/hello`       | Flask app at `8001`   |
| `/service1/ping`        | Health endpoint (Go)  |
| `/service2/`            | Default Flask route   |

---

##  Run the Project

```bash
docker compose up --build


Then test:

curl http://localhost:8080/service1/hello
curl http://localhost:8080/service2/hello
