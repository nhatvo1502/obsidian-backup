Elastic Container Service

# What for?

1. Fully managed container orchestration services
2. Deploy, manage, and scale containerized ap

# Layers:

1. Capacity - infra where containers run
2. Controller - deploy and manager 
3. Provisioning - manage tools such as scheduler to deploy

---

# Sample Project:
Host a simple docker web application on ECS

### Workflow:
Create AWS ECR Repo > Build Docker Image > Push Docker Image to AWS ECR > Create ECS Cluster > Define Task Definition > Create ECS Service (Networking) > Attach Load Balancing (Optional)


### 1. Create AWS ECR Repo:
Login to AWS console > AWS ECR > Create repo > nnote/app


### 2. Build Docker Image

1. Python WebApp (app.py())

```python
from flask import Flask

from website import create_app



app = create_app()



if __name__ == '__main__':

app.run(host='0.0.0.0', port=5000)
```

2. Dockerfile

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


3. Build container

```bash
docker build -t simple-flask-app 
```


### 3. Push Docker Image to AWS ECR

1. Tag image
```bash
docker tag simple-flask-app:latest 566027688242.dkr.ecr.us-east-1.amazonaws.com/nnote/app:latest
```


2. Retrieve ECR authentication token
```bash
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 566027688242.dkr.ecr.us-east-1.amazonaws.com
```


3. Push Image to ECR Repo
```bash
docker push 566027688242.dkr.ecr.us-east-1.amazonaws.com/nnote/app:latest
```


### 4. Create ECS Cluster

1. AWS ECS Console -> Cluster -> Create Cluster

2. Service -> Fargate

### 5. Define Task Definition

1. ECS Console -> Task Definition -> Create new task definition
2. Chose Fargate
3. Image URL = paste ECR image URL
4. Port Mapping = `5000` (port that app run *inside* the container)

### 6. Create ECS Service

1. AWS ECS Console -> Cluster -> select `dev-nnote-cluster-us-east-1-firstCluster`
2. create service
3. Set:
	1. Launch Type = `Fargate`
	2. Task Definition = `nnote-task`
	3. Service Name = `nnote-service`
	4. Number of Task = `1`


### 7. Load Balancer (optional)
1. EC2 Console -> Load Balancers -> Create Load Balancer
2. Select application 


### 8. Get container Public IP address
1. AWS ECS Console -> Cluster -> select `dev-nnote-cluster-us-east-1-firstCluster` ->

