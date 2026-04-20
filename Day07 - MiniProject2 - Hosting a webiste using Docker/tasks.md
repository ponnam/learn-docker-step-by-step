# 🛠️ Day 07 - MiniProject2 - Host Website using Docker


## 🎯 Objective

- Create a simple HTML website  
- Build Docker image using Apache  
- Run container and access website  
- Create image from container  

---

## Project Setup

### Task 7.1: Create Project Directory
```bash
mkdir myproject  
cd myproject  
```

### Task 7.2: Create index.html

vi index.html  

Paste:
```html
<html>
<head><title>TeraSkill Academy Website</title></head>
<body>
<h1>Welcome to TeraSkill Academy!</h1>
<p>This is a simple HTML website hosted on Apache HTTPD inside a Docker container.</p>
</body>
</html>
```


## Create Dockerfile

### Task 7.3: Create Dockerfile
```bash
vi Dockerfile  
```
Paste:

```bash
FROM httpd:latest  
COPY index.html /usr/local/apache2/htdocs/  
EXPOSE 80  
```

### Task 7.4: Build Image
```bash
docker build -t mywebsite .  
```
## Run Container


### Task 7.5: Create & Run Container
```bash
docker run -d -p 80:80 --name container1 mywebsite  
```

### Task 7.6: Verify Container

docker ps -a  


## 🌐 Access Website

### Task 7.7: Open in Browser

http://EC2-PUBLIC-IP   

---

## Create Image from Container


### Task 7.8: Commit Container
```bash
docker commit container1 mywebsiteimage:latest  
```
### Task 7.9: Verify Image
```bash
docker images  
```

## Create & Run New Container


### Task 7.10: Create & Run container on Port 81
```bash
docker run -d -p 81:80 --name newcontainer mywebsiteimage  
```

### Task 7.11: Verify Container
```bash
docker ps -a  
```


## 🌐 Access Website (Port 81)

http://EC2-PUBLIC-IP:81  

---

## Docker Logs

### ✅ Task 7.12: View Logs
```bash
docker logs container1  
```
### Task 7.13: Follow Logs
```bash
docker logs -f container1  
```
### Task 7.14: Logs with Timestamp
```bash
docker logs -t container1  
```
### Task 7.15: Last 50 Lines
```bash
docker logs --tail 50 container1  
```
### Task 7.16: Tail + Follow
```bash
docker logs -f --tail 100 container1  
```
### Task 7.17: Error Logs
```bash
docker logs --stderr container1  
```

### Task 7.18: Output Logs
```bash
docker logs --stdout container1  
```
### Task 7.19: Logs from Last 10 Minutes
```bash
docker logs --since 10m container1  
```

### Task 7.20: Logs Until Time
```bash
docker logs --until 2025-01-01T10:00:00 container1  
```
---

## 🎯 Final Outcome

After completing this lab, you will:

- Host a website using Docker  
- Use Apache HTTPD container  
- Understand port mapping  
- Create image from running container  
- Run multiple containers on different ports 
- Monitor logs for debugging  