# Day 09 - Deploy PHP Application using Docker Compose


## 🎯 Objective

- Deploy real-world application  
- Work with Docker Compose  
- Verify data persistence  
- Understand application behavior  

---

## Project Deployment


### Task 9.1: Login to Docker Host

Connect to your EC2 instance  using SSH


### Task 9.2: Clone GitHub Repository
```bash
git clone https://github.com/ponnam/Teraskill-StudentAPP.git  
```

### Task 9.3: Navigate to Project Directory
```bash
cd TeraSkill-StudentApp  
```

### Task 9.4: Start Containers
```bash
docker compose up -d  
```
### Task 9.5: Verify Volume Creation
```bash
docker volume ls  
```

### Task 9.6: Verify Containers
```bash
docker compose ps  
```

## Access Application

### Task 9.7: Open in Browser

http://EC2-PUBLIC-IP:8080  

---
## Use the Application
### Task 9.8: Add Student Data

- Enter student details  
- Submit form  

### Task 9.9: View Students List

- Click "View Students"  
- Verify data  

## Data Persistence Testing


### Task 9.10: Stop & Remove Containers
```bash
docker compose stop  
docker compose rm  
docker compose ps  
```

### Task 9.11: Verify Volume Data
```bash
docker volume ls  

docker volume inspect teraskill-studentapp_mysql_data  

cd /var/lib/docker/volumes/teraskill-studentapp_mysql_data/_data/  

ls  
```

### Task 9.12: Restart Application
```bash
docker compose up -d  
```

### Task 9.13: Verify Data Persistence

http://EC2-PUBLIC-IP:8080  

👉 Confirm previously added data still exists  

---

## 🎯 Final Outcome

After completing this lab, you will:

- Deploy real-world application using Docker  
- Understand multi-container architecture  
- Verify persistent storage using volumes  
- Gain production-level DevOps knowledge  
