# Flask + Redis App using Docker & Docker Compose

##  Project Overview

This project demonstrates a simple **Python Flask** web application connected to **Redis**, fully containerized using **Docker** and orchestrated with **Docker Compose**.

The application displays a greeting message along with a counter that increments every time the page is refreshed. Redis is used to store the hit count.

This project is part of my DevOps learning journey and focuses on:

* Dockerizing applications
* Using Docker Compose for multi-container environments
* Understanding image rebuilds vs bind mounts

---

##  Technologies Used

* Python (Flask)
* Redis
* Docker
* Docker Compose

---

##  Project Structure

```
.
├── app.py
├── requirements.txt
├── Dockerfile
└── docker-compose.yml
```

---

##  How to Run the Project

### 1- Clone the repository

```bash
git clone <your-repo-url>
cd project
```

### 2- Run the application

```bash
docker-compose up -d
```

### 3- Access the application

Open your browser and go to:

```
http://localhost:9000
```

---

##  Application Update Scenarios

###  Scenario 1: Update without Volume (Image Rebuild Required)

If you modify `app.py` after running the containers, the change **will NOT reflect** immediately.

You must rebuild the image:

```bash
docker-compose down
docker-compose up -d --build
```

 This approach is **not recommended for development** because rebuilding images is time-consuming.

---

###  Scenario 2: Update Using Bind Mount Volume (Recommended)

By adding a bind mount volume in `docker-compose.yml`:

```yaml
volumes:
  - .:/app
```

Any change in the source code is reflected **immediately** without rebuilding the image.

---

##  Why Did the Application Update Without Rebuilding the Image?

When using a **bind mount volume**, the application code inside the container is directly linked to the local project directory on the host machine.

So when `app.py` is modified:

* The container sees the change instantly
* Flask reloads the application
* No image rebuild is required

This approach is ideal for **development environments**.

---

##  Key Learning Outcomes

* Building Docker images for Python applications
* Running multi-container apps with Docker Compose
* Difference between image rebuilds and bind mounts
* Practical use of Redis as a service container

---

##  Author

Ahmed Mostafa


