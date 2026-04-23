# 🐳 Day 09 - Deploying Real Application using Docker Compose


## 🧠 What You’ll Learn

- Deploy a real-world application using Docker Compose  
- Understand multi-container architecture (Web + Database)  
- Work with persistent volumes in real projects  
- Verify data persistence after container deletion  
- Understand application lifecycle  

---

## Real-World Application Deployment

In this lab, we deploy a PHP-based application:

👉 **Teraskill Student App**

This application includes:

- Frontend (PHP Web App)  
- Backend (MySQL Database)  


### Architecture Overview

Application consists of:

1. **Web Container**
   - Runs PHP application  
   - Handles user requests  

2. **Database Container**
   - Runs MySQL  
   - Stores student data  

3. **Docker Volume**
   - Stores database data  
   - Prevents data loss  



### How It Works

1. User accesses application via browser  
2. Request goes to Web container  
3. Web container interacts with Database  
4. Data is stored in Docker volume  



### Named Volumes (Important Concept)

- Used to store database data  
- Data persists even if containers are removed  

👉 Location:
```bash
/var/lib/docker/volumes/<volume_name>/_data
```



### Data Persistence Flow

- Add data → stored in DB  
- Stop containers → data still exists  
- Delete containers → data still exists  
- Restart containers → data restored  


###  docker compose up
```bash
docker compose up -d
```

👉 Starts all services defined in docker-compose.yml  



### Why This Project is Important

- Simulates real-world DevOps workflow  
- Shows how applications use databases  
- Demonstrates persistence using volumes  
- Useful for interviews and production  

## 🎯 Summary

- Deployed multi-container application  
- Used Docker Compose  
- Stored data using volumes  
- Verified no data loss after container removal  
- Understood real application workflow  