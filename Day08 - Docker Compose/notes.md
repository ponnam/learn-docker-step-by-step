# 🐳 Day 08 - Docker Compose (Multi-Container Applications)


## 🧠 What You’ll Learn

- What is Docker Compose  
- Why Docker Compose is needed  
- How to define multi-container apps  
- Understanding docker-compose.yml  
- Managing multiple services with one command  

---

## What is Docker Compose?

Docker Compose is a tool used to **define and run multi-container Docker applications**.

👉 Instead of running multiple containers manually, you can manage everything using a single file.


### Example Use Case

- Web application (Nginx)  
- Database (MySQL)  
- Cache (Redis)  

👉 All started with one command  

---

## Why Docker Compose?

Without Compose:
- Run multiple `docker run` commands is difficult 
- Hard to manage dependencies  

With Compose:
- Single YAML file  
- Easy to manage  
- One command to start everything  

---

## 📄 docker-compose.yml Structure


### version
```Dockerfile
version: "3.9"
```
👉 Defines compose file version  

### services

Defines all containers  
```Dockerfile
Example:
- web  
- db  
```
### image
```Dockerfile
image: nginx  
```
👉 Uses official image  

### ports
```Dockerfile
"8080:80"
```
👉 Host port → Container port  

### volumes
```Dockerfile
./html:/usr/share/nginx/html  
```

👉 Mount local directory into container  

### depends_on
```Dockerfile
depends_on:
  - db  
```

👉 Ensures DB starts before web  

###  environment

Used to pass variables  

Example:
```Dockerfile
MYSQL_ROOT_PASSWORD=root123  
```

### named volumes
```Dockerfile
db_data:/var/lib/mysql  
```
👉 Stores database data persistently  

---

##  What This Setup Does

- Runs Nginx on port 8080  
- Serves website from local folder  
- Runs MySQL database  
- Stores DB data in volume  
- Web depends on DB  


### docker compose up
```bash
docker compose up -d  
```
👉 Starts all services  

---

##  Common Docker Compose Commands

### docker compose stop

Stops containers (keeps data)

### docker compose start

Starts stopped containers  

### docker compose pause / unpause

Pause / resume containers  

###  docker compose down

Stops and removes containers + network  

### docker compose ps

Shows containers of this project  

### docker compose images

Shows images used  

### docker compose logs

View logs of all services  

### docker compose logs web

Logs for specific service  `web`

### docker compose kill

Force stop containers  

### docker compose rm

Remove stopped containers  

### docker compose top `web`

View processes inside container named 


### docker compose config

Validate compose file  


### Scaling Containers
```bash
docker compose up -d --scale web=5  
```
👉 Runs 5 instances of web service  

📌 Note:
- No load balancing by default  
- Use Docker Swarm for load balancing  

---

## 🎯 Summary

- Docker Compose manages multi-container apps  
- Uses YAML file for configuration  
- One command to start everything  
- Supports volumes, networks, scaling  
- Simplifies DevOps workflows  
