# 🛠️ Day 08 - Docker Compose


## 🎯 Objective

- Install Docker Compose  
- Create multi-container application  
- Run web + database using Compose  
- Manage services  

---

## Install Docker Compose

### Task 8.1: Install Docker
```bash
sudo yum update -y  
sudo yum install docker -y  
sudo systemctl start docker  
sudo systemctl status docker  
```

### Task 8.2: Install Docker Compose Plugin
```bash
sudo mkdir -p /usr/local/lib/docker/cli-plugins  

sudo curl -SL https://github.com/docker/compose/releases/download/v2.29.2/docker-compose-linux-x86_64 -o /usr/local/lib/docker/cli-plugins/docker-compose  

sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose   
```
### Task 8.3: Check the docker compose version
```bash
docker compose version 
```


## Create Compose File

### Task 8.4: Create docker-compose.yml
```bash
vi docker-compose.yml  
```
Paste:
```Dockerfile
services:
  web:
    image: nginx
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
    depends_on:
      - db

  db:
    image: mysql:8
    environment:
      - MYSQL_ROOT_PASSWORD=root123
      - MYSQL_DATABASE=teraskillacademy
      - MYSQL_USER=student
      - MYSQL_PASSWORD=pass123
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:

```

### Task 8.5: Create HTML Content
```bash
mkdir html  

echo "Hello from Nginx + Docker Compose!" > html/index.html  
```

### Task 8.6: Create & Run the app containers 

```bash
docker compose up -d  
```

### Task 8.7: Verify Containers
```bash
docker ps  
```

### Task 8.8: Access Application

http://EC2-PUBLIC-IP:8080  

---

## Compose Commands Practice



### Task 8.9: Stop / Start / Pause
```bash
docker compose stop  
docker compose start  
docker compose pause  
docker compose unpause  
```

### Task 8.10: Remove Containers
```bash
docker compose down  
```
### Task 8.11: View Project Containers
```bash
docker compose ps  
```
### Task 8.12: List Images
```
docker compose images  
```

### Task 8.13: View Logs
```bash
docker compose logs  
```

### Task 8.14: Logs for Web Service
```bash
docker compose logs web  
```

### Task 8.15: Kill Containers
```bash
docker compose kill  
```

### Task 8.16: Remove Stopped Containers
```bash
docker compose rm  
```

### Task 8.17: View Processes
```bash
docker compose top web  
```
### Task 8.18: Validate File
```bash
docker compose config  
```

## Scaling Containers

### Task 8.19: Scale Web Service
```bash
docker compose up -d --scale web=5  
```

## Custom Compose File

### Task 8.20: Use Custom File
```bash
docker compose -f krishna.yml up -d  
```
---

## 🎯 Final Outcome

After completing this lab, you will:

- Deploy multi-container applications  
- Use Docker Compose effectively  
- Manage services easily  
- Understand real-world architecture  