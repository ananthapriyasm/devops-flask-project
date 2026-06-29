# Flask DevOps Deployment on AWS

## Project Overview

This project demonstrates a complete DevOps workflow by deploying a Flask web application on AWS EC2 using Docker and automating builds with GitHub Actions.

The application is containerized with Docker, stored in GitHub, deployed on an AWS EC2 instance, and integrated with a CI/CD pipeline.

---

## Technologies Used

- Python Flask
- Docker
- Git & GitHub
- GitHub Actions
- AWS EC2
- Amazon Linux
- Linux (WSL)

---

## Project Architecture

Developer
↓
GitHub Repository
↓
GitHub Actions
↓
Docker Build
↓
AWS EC2
↓
Docker Container
↓
Flask Application

---

## Features

- Flask web application
- Docker containerization
- AWS EC2 deployment
- GitHub version control
- GitHub Actions CI pipeline
- Linux server management

---

## Project Structure

```text
flask-devops-deployment/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── app.py
├── Dockerfile
├── requirements.txt
└── README.md
```

## Application Code

### app.py

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "DevOps Project Successfully Deployed!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

## Docker Commands

### Build Docker Image

```bash
docker build -t flask-app .
```

### Run Docker Container

```bash
docker run -d -p 5000:5000 --name flask-container flask-app
```

### Check Running Containers

```bash
docker ps
```

### View Container Logs

```bash
docker logs flask-container
```

---

## AWS EC2 Deployment Steps

1. Launch an Amazon Linux EC2 instance.
2. Configure Security Groups:
   - Port 22 (SSH)
   - Port 80 (HTTP)
   - Port 5000 (Application)
3. Connect using SSH.
4. Install Docker.
5. Clone the GitHub repository.
6. Build and run the Docker container.
7. Access the application using the EC2 Public IP.

---

## GitHub Actions CI Pipeline

The workflow automatically runs whenever code is pushed to the `main` branch.

### Workflow File

```yaml
name: Build Docker Image

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Build Docker Image
        run: docker build -t flask-app .
```

---

## Learning Outcomes

- Containerization using Docker
- CI/CD using GitHub Actions
- AWS EC2 deployment
- Linux administration
- Git and GitHub workflows
- DevOps fundamentals

---

## Future Enhancements

- Automatic deployment from GitHub Actions to AWS EC2
- Nginx reverse proxy
- Terraform infrastructure automation
- AWS CloudWatch monitoring
- Docker Compose implementation

---

## Author

Anantha Priya

DevOps Engineer Aspirant
