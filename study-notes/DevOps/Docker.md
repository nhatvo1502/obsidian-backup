# Installation

## Windows 11

[Docker Installation Guide](https://docs.docker.com/desktop/setup/install/windows-install/)

## Linux

### 1. Install `gnome-terminal`

```bash
sudo apt install gnome-terminal
```

### 2. Install Docker Desktop

```bash
sudo apt-get update
sudo apt-get install ./docker-desktop-amd64.deb
```

### 3. Launch Docker

```bash
systemctl --user start docker-desktop
```

### 4. Check Docker and Docker Compose Versions

```bash
docker compose version
# Output:
# Docker Compose version v2.29.1

docker --version
# Output:
# Docker version 27.1.1, build 6312585

docker version
# Output:
# Client:
#  Version:           23.0.5
#  API version:       1.42
#  Go version:        go1.21.12
```

### 5. Enable and Stop Docker Desktop

```bash
systemctl --user enable docker-desktop
systemctl --user stop docker-desktop
```

### 6. Upgrade Docker

```bash
sudo apt-get install ./docker-desktop-amd64.deb
```

## macOS

(Installation steps needed)

---

# How Docker Works

1. Docker allows packaging an application with all its dependencies into a **container**.
2. A **container** is a lightweight, standalone, executable package that includes everything needed to run the application.
3. Docker provides:
    - **Images**: Blueprints for containers that contain all dependencies and configurations.
    - **Containers**: Running instances of Docker images.
    - **Dockerfile**: A script that defines how to build a Docker Image.

---

# Workflow

**Write `Dockerfile` → Create `Container`**

---

# Example: Hosting a Simple Web Application on Windows 11

## Requirements

### 1. Python Flask Web App (`app.py`)

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Hello, Dockerized Flask App!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

### 2. `requirements.txt`

```
blinker==1.9.0
click==8.1.8
colorama==0.4.6
Flask==3.1.0
itsdangerous==2.2.0
Jinja2==3.1.6
MarkupSafe==3.0.2
Werkzeug==3.1.3
```

### 3. `Dockerfile`

```dockerfile
# Use an official Python image as the base
FROM python:3.11

# Set the working directory in the container
WORKDIR /app

# Copy the application files
COPY . .

# Install dependencies
RUN pip install -r requirements.txt

# Expose the port Flask runs on
EXPOSE 5000

# Run the application
CMD ["python", "app.py"]
```

### 4. Create and Run Container
```bash
docker build -t flask-app .
docker run -p 5000:5000 flask-app
```
---

# Tags

`#docker` `#cicd` `#orchestration` `#pipeline`