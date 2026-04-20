# 🐳 Day 07 - Hosting a Website using Docker (Mini Project)

## 🧠 What You’ll Learn

- Build a simple web application using Docker  
- Use official Docker images (httpd)  
- Copy application files into container  
- Expose ports and access application in browser  
- Create image from running container  


## Hosting a Website using Docker

In this lab, we will:

1. Create a simple HTML webpage  
2. Build a Docker image using Apache HTTPD  
3. Run a container  
4. Access the website in browser  

---

## Base Image (httpd)

We are using:

httpd:latest

👉 This is the official Apache Web Server image  



## COPY Instruction
```Dockerfile
COPY index.html /usr/local/apache2/htdocs/
```
### ✅ What it does:
- Copies your HTML file into Apache's default web directory  

👉 This is where Apache serves web content  



## EXPOSE Instruction
```Dockerfile
EXPOSE 80
```
### What it does:
- Tells Docker that container listens on port 80  

👉 Default HTTP port  


## docker build

docker build -t mywebsite .

### ✅ What it does:
- Builds image from Dockerfile  
- Tags image as "mywebsite"  



### 🚀 docker run with Port Mapping
```bash
docker run -d -p 80:80 --name container1 mywebsite
```
#### Explanation:

- `-d` → Run in background  
- `-p 80:80` → Map host port 80 → container port 80  
- `--name` → Container name  

👉 Now website is accessible via browser  



##  Accessing Application

http://<EC2-PUBLIC-IP>

👉 Uses:
- Host IP  
- Port mapping  



## docker commit
```bash
docker commit container1 mywebsiteimage:latest
```

### What it does:
- Creates new image from running container  
- Saves current state  


## Running Container on Different Port
```bash
docker run -d -p 81:80 --name newcontainer mywebsiteimage
```

👉 Host port = 81  
👉 Container port = 80  

---
## Docker Log Monitoring
### docker logs
```bash
docker logs container_name  
```
👉 Shows logs of container  


### Follow Logs (Live)
```bash
docker logs -f container_name  
```
👉 Real-time logs  
### Logs with Timestamp
```bash
docker logs -t container_name  
```
### Last N Lines
```bash
docker logs --tail 50 container_name  
```
### Tail + Follow
```bash
docker logs -f --tail 100 container_name  
```

### Only Error Logs
```bash
docker logs --stderr container_name  
```

### Only Output Logs
```bash
docker logs --stdout container_name  
```

### Logs Since Time
```bash
docker logs --since 10m container_name  
```

### Logs Until Time
```bash
docker logs --until 2025-01-01T10:00:00 container_name  
```


# 🎯 Summary

- Used httpd image to host website  
- Copied HTML into container  
- Used port mapping to access app  
- Created image from running container  
- Ran multiple containers on different ports 
- Monitored logs using docker logs 
