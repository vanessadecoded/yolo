# 1 DEVOPS IP2 PROJECT YOLO

- Yolo is a (MongoDB, Express, React, Node.js) MERN stack application. 

# 2 SETTING UP AND RUNNING
Before running the application with Docker Compose,these are the prerequisites 
1. The latest version of Docker Desktop.

# Clone the repository:

```bash
git clone git@github.com/vanessadecoded/yolo
```

# Navigate to the project directory:
```bash
cd yolo
```

# Run Docker Compose:

```bash
docker-compose up
```

- This will build and start the application containers.

# Images on Docker Hub

- The application images are available on Docker Hub:
    - Frontend Image: [vanessamayama/client:1.0](https://hub.docker.com/repository/docker/vanessamayama/client/tags)
    - Backend Image: [vanessamayama/backend:1.0](https://hub.docker.com/repository/docker/vanessamayama/backend/tags)

>Note:These images are versioned and tagged accordingly.

# 3 SCREENSHOT OF DOCKERHUB IMAGES.

Below is a screenshot of the images built and pushed to dockerhub.
![alt text](<Screenshot from 2024-05-11 17-26-03.png>)

# Usage
- Once the Docker containers are up and running, you can access the application at:
    - Frontend: http://localhost:3000
    - Backend: http://localhost:5000

