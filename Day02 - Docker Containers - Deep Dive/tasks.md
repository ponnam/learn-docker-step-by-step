# 🛠️ Day 02 - Tasks (Docker Containers - Deep Dive)

---

## 🎯 Objective

* Create and manage containers
* Understand container lifecycle
* Practice container operations

---

###  Task 2.1: Create Container (Without Starting)

```bash
docker create --name container1 ubuntu
```



### Task 2.2: Verify Container Status

```bash
docker ps
docker ps -a
```



###  Task 2.3: Create & Run Container

```bash
docker run --name container2 amazonlinux
```


### Task 2.4: Check All Containers

```bash
docker ps -a
```


###  Task 2.5: Run Interactive Container

```bash
docker run -it --name container3 ubuntu
```

👉 Exit using:

```bash
exit
```

### Task 2.6: Verify Container Status

```bash
docker ps -a
```



### Task 2.7: Run & Detach Container

```bash
docker run -it --name container4 ubuntu
```

👉 Press:
CTRL + P + Q

---

### Task 2.8: Check Container Status

```bash
docker ps -a
```



### Task 2.9: Stop Container

```bash
docker stop container4
```



### Task 2.10: Verify Status

```bash
docker ps -a
```



### Task 2.11: Run Another Container

```bash
docker run -it --name container5 amazonlinux
```



### Task 2.12: Kill Container

```bash
docker kill container5
```



### Task 2.13: Start Container Again

```bash
docker start container4
```



### Task 2.14: Pause Container

```bash
docker pause container4
```

### Task 2.15: Unpause Container

```bash
docker unpause container4
```

---

### Task 2.16: Run Specific Version

```bash
docker run -it --name container6 ubuntu:20.04
```

### Task 2.17: Attach to Container

```bash
docker attach container4
```


### Task 2.18: Exec into Container

```bash
docker exec -it container6 /bin/bash
```

### Task 2.19: Rename Container

```bash
docker rename container4 container4_new
```

### Task 2.20: Remove Stopped Container

```bash
docker rm container2
```

### Task 2.21: Force Remove Running Container

```bash
docker rm -f container6
```

---

### Task 2.22: Delete Image

```bash
docker rmi tomcat
```

### Task 2.23: Delete Specific Version

```bash
docker rmi ubuntu:20.04
```


### Task 2.24: Stop All Containers

```bash
docker stop $(docker ps -q)
```

### Task 2.25: Delete All stooped Containers

```bash
docker rm $(docker ps -q)
```

### Task 2.26: Delete All Images

```bash
docker rmi $(docker images -q)
---


## 🎯 Final Outcome

After completing this lab, you will:

* Understand container lifecycle
* Manage containers effectively
* Use exec, attach, stop, kill
* Remove containers and images


### Keep Learning :) 