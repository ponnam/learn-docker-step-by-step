# 🐳 Day 06 - Docker Monitoring & Troubleshooting


## 🧠 What You’ll Learn

- Monitor Docker resources  
- Analyze container performance  
- View running processes inside containers  
- Debug container issues  
- Clean up unused Docker resources  

---

## Docker System Monitoring


### docker system df
```bash
docker system df
```
####  What it does:
- Shows disk usage of Docker components  

#### Includes:
- Images  
- Containers  
- Volumes  
- Build cache  


### docker system df -v
```bash
docker system df -v
```

#### What it does:
- Detailed disk usage per container and image  

### docker system info
```bash
docker system info
```

#### What it does:
- Displays full Docker system information  

#### Includes:
- Containers count  
- Images count  
- Storage driver  
- CPU & memory  
- Docker version  


### docker system events
```bash
docker system events
```

#### What it does:
- Shows real-time Docker events  

#### Examples:
- Container start  
- Container stop  
- Image pull  

---

## Docker Cleanup

### docker system prune
```bash
docker system prune
```

#### What it does:
- Removes:
  - Stopped containers  
  - Unused networks  
  - Dangling images  
  - Build cache  


### docker system prune --volumes
```bash
docker system prune --volumes
```

#### What it does:
- Removes unused volumes also  

⚠️ Use carefully (data loss possible)

---

## Container Process Monitoring

### docker top
```bash
docker top container_name
```

#### What it does:
- Shows processes running inside container  

#### Output:
- PID  
- USER  
- CPU / Memory  
- COMMAND  


#### Use Cases:

- Debug high CPU usage  
- Check running processes  
- Identify issues inside container  

---

##  Real-Time Monitoring


### docker stats
```bash
docker stats
```

#### What it does:
- Shows real-time resource usage  

#### Metrics:
- CPU usage  
- Memory usage  
- Network I/O  
- Disk I/O  

### docker stats (multiple containers)
```bash
docker stats container1 container2  
```

###  docker stats --all
```bash
docker stats --all  
```
👉 Includes stopped containers  


###  docker stats --no-stream
```bash
docker stats --no-stream  
```

👉 Shows one-time snapshot  

#### Use Cases:

- Detect high CPU usage  
- Identify memory leaks  
- Monitor performance issues  

---

## Port Mapping Inspection

### docker port
```bash
docker port container_name  
```

#### What it does:
- Shows port mappings  

### Specific Port
```bash
docker port container_name 80  
```

👉 Shows mapping for port 80  

#### Use Cases:

- Check exposed ports  
- Debug connectivity issues  
- Verify application access  

---

## 🎯 Summary

- docker system → system-level monitoring  
- docker top → process-level inside container  
- docker stats → real-time performance  
- docker port → network mapping  
- docker prune → cleanup resources  