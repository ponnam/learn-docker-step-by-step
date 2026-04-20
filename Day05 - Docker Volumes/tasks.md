# Day 05 - Docker Volumes



## 🎯 Objective

- Create and use Docker volumes  
- Persist data across containers  
- Share volumes between containers  
- Understand different volume types  

---

## 📦 Using Volume via Dockerfile

### Task 5.1: Create Dockerfile
```bash
vi Dockerfile
```
Paste the content:
```bash
FROM ubuntu  
VOLUME ["/volume1"]  
```


###  Task 5.2: Build Image
```bash
docker build -t myvolume:v1 .  
```

###  Task 75.3: Create Container
```bash
docker run -it --name mycont2 myvolume:v1  
```

### Task 5.4: Verify Volume
```bash
ls  
cd /volume1  
ls  
```

### Task 5.5: Create Files in Volume
```bash
cd /volume1  
touch file{1..10}  
```


## Share Volume Between Containers


### Task 5.6: Attach Volume to New Container

docker run -it --name mycont3 --volumes-from mycont2 --privileged=true ubuntu  


### Task 5.7: Verify Shared Data ( in the `mycont2` container)

```bash
cd /volume1  
ls  
```
---
## 📂 Anonymous Volume


### Task 5.8: Create Container with Anonymous Volume
```bash
docker run -it --name mycont4 -v /volume2 ubuntu  
```

###  Task 5.9: Create Files
```bash
cd /volume2  
touch file{11..20}  
```


### Task 5.10: Share Volume with another container `mycont5`
```bash
docker run -it --name mycont5 --volumes-from mycont4 --privileged=true ubuntu  
```


### Task 5.11: Verify Data (exec into mycont5)
```bash
cd /volume2  
ls  
```

---

## Named Volumes

### Task 5.12: Create Named Volume

docker volume create my_volume1  


###  Task 5.13: List Volumes

docker volume ls  


### Task 5.14: Inspect Volume

docker volume inspect my_volume1  


###  Task 5.15: Create Files in Volume (Host)

cd /var/lib/docker/volumes/my_volume1/_data  
touch file{100..110}  

### Task 5.16: Attach Volume to Container

```bash
docker run -it --name cont11 --mount source=my_volume1,destination=/my_volume1 ubuntu  
```
```bash
cd /my_volume1  
ls  
```

--> Exit from the docker container

### Copy Data into Volume


### Task 5.17: Create Volume

```bash
docker volume create my_volume4  
```


### Task 5.18: Get Volume Path
```bash
docker volume inspect my_volume4  
```

### Task 5.19: Add Files
```bash
cd /var/lib/docker/volumes/my_volume4/_data  
touch docker{1..10}  
```

### Task 5.20: Attach Volume to Container
```bash
docker run -it --name mycont6 -v my_volume4:/data ubuntu  
```
#### Task 5.20.1: Observe all the files are accessible in container
```bash
cd /data  
ls  
```


## 🎯 Final Outcome

After completing this lab, you will:

- Understand Docker volumes  
- Persist container data  
- Share data across containers  
- Use named & anonymous volumes  
