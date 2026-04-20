# 🐳 Day 05 - Docker Volumes (Data Persistence)


## 🧠 What You’ll Learn

- What are Docker Volumes  
- Why volumes are needed  
- Types of volumes  
- How data persists in containers  
- Different ways to mount volumes  

---

## What are Docker Volumes?

Docker Volumes are used to **store data outside the container**.

👉 This means:
Even if the container is deleted → data will NOT be lost  

### Problem Without Volumes

- Container deleted → data lost  
- No persistence  
- Not suitable for databases, logs, uploads  


### Solution → Docker Volumes

- Data stored outside container  
- Independent of container lifecycle  
- Can be reused and shared  


### Key Features

- Persistent storage  
- Share data between containers  
- Easy backup & restore  
- Better performance than bind mounts  


### Where Volumes are Stored?

On Docker host:

/var/lib/docker/volumes/volume-name/_data  



## How Volumes Work

When Docker sees a volume:

- Creates directory inside container (e.g., /data)  
- Maps it to host location  

👉 So even if container is removed → data remains  



##  Types of Docker Volumes

### 1. Named Volumes

- Created explicitly  
- Managed by Docker  

Example:

docker volume create mydata  

Attach:

docker run -v mydata:/app/data ubuntu  



###  2. Anonymous Volumes

- Created automatically  
- No name assigned  

Example:

docker run -v /app/data ubuntu  

### 3. Bind Mounts

- Maps host directory → container  

Example:

docker run -v /home/user/app:/app ubuntu  


### 4. tmpfs Mounts

- Stored in RAM (memory)  
- Temporary (not persistent)  

Example:

docker run --tmpfs /app/cache ubuntu  


## Methods to Use Volumes

1. Dockerfile (VOLUME instruction)  
2. CLI using -v  
3. Named volumes  
4. Bind mounts  
5. --mount (modern approach)  

---

##  Volume Sharing

- One container → another container  
- Useful for:
  - Logs  
  - Data sharing  
  - Multi-container apps  


##  Important Notes

- Volumes exist even if container is deleted  
- Docker manages volume location  
- Named volumes are preferred in production  
- Bind mounts give direct host control  

---

# 🎯 Summary

- Volumes store data outside container  
- Data persists even after container deletion  
- Named volumes are most commonly used  
- Volumes can be shared between containers 