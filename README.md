
# FastAPI Dockerized Application with CI/CD & Monitoring

## Overview

This project demonstrates how to build, containerize, deploy, and monitor a FastAPI application using modern DevOps tools.
The application provides basic user APIs and stores data in a JSON file. Docker volumes are used to ensure data persistence even after container restart.

## Tools

* FastAPI (Python backend)
* Docker & Docker Compose
* Jenkins (CI/CD)
* Prometheus (Monitoring)
* Grafana (Visualization)

---

## Project Structure

```bash
docker-fastapi-test/
│
├── app/
│   ├── main.py
│   ├── services.py
│   ├── schema.py
│   └── data/
│       └── users.json
│
├── Dockerfile
├── docker-compose.yml
├── prometheus.yml
├── requirements.txt
└── Jenkinsfile
```

---

## API Endpoints

* `GET /` → Returns welcome message
* `GET /users` → Returns list of users
* `POST /users` → Adds new user

Swagger UI:

```
http://localhost:8000/docs
```

---

## Running the Application

### Start Application

```bash
docker-compose up --build
```

### Stop Application

```bash
docker-compose down
```

---

## Data Persistence

* User data is stored in:

```
app/data/users.json
```

* Docker volume ensures:

  * Data is not lost after container restart
  * Data remains available across deployments

---

## Monitoring

### Prometheus

* URL: http://localhost:9090
* Collects metrics from:

```
/metrics
```

### Grafana

* URL: http://localhost:3000
* Login:

```
admin / admin
```

### Example Query

```
rate(http_requests_total[1m])
```

---

## Jenkins CI/CD

Jenkins is used to automate the pipeline.

### Pipeline Steps:

1. Clone code from GitHub
2. Trigger deployment (manual or host-based)

Note:
In this setup, Docker commands are executed on the host machine because Jenkins runs inside a container.

---

## Workflow

```
GitHub → Jenkins → Docker → FastAPI App
                           ↓
                  Prometheus → Grafana
```

---

## Testing

1. Open:

```
http://localhost:8000/docs
```

2. Add users using POST `/users`

3. Restart containers:

```bash
docker-compose down
docker-compose up
```

4. Verify data still exists 

## Challenges

* Jenkins + Docker integration on Windows
* Handling file paths in pipeline
* Prometheus configuration

## Future Improvements

* Deploy on AWS EC2
* Add Kubernetes support
* Use database instead of JSON file
* Enable auto CI/CD with webhooks



## Summary

This project covers the complete DevOps lifecycle:

* Application development
* Containerization
* CI/CD automation
* Monitoring and visualization

---
