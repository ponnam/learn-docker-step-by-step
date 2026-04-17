# 🐳 Day 02 - Docker Containers - Deep Dive

---

## 🧠 What You’ll Learn

* Container lifecycle
* Difference between create vs run
* Interactive containers
* Managing container states
* Executing commands inside containers

---

##  Container Lifecycle

A container goes through multiple states:

* **Created** → Container created but not started
* **Running** → Container is active
* **Paused** → Temporarily frozen
* **Stopped (Exited)** → Execution finished or stopped
* **Removed** → Deleted from system

---

##  docker create vs docker run

---

### docker create

Creates a container but **does NOT start it**

```bash
docker create --name container1 ubuntu
```

👉 **Use case:**

* When you want to configure container first and start later



###  docker run

Creates + starts container in one step

```bash
docker run --name container2 ubuntu
```

👉 **Internally:**

* Pulls image (if not available)
* Creates container
* Starts container

---

##  Container Exit Status

When container stops → it shows **Exited**

### Common Exit Codes:

* **0** → Success
* **1** → General error
* **137** → Killed (often due to memory issue)

---

##  Interactive Containers

---

### docker run -it

```bash
docker run -it --name container3 ubuntu
```

### What it does:

* `-i` → Interactive mode
* `-t` → Terminal (TTY)

👉 Opens a shell inside container



###  Exiting Container

```bash
exit
```

👉 **This:**

* Stops container
* Ends session



### Detach Without Stopping

Press:

```
CTRL + P + Q
```

👉 Container keeps running in background

---

## Managing Containers

---

### docker stop

Gracefully stops container

```bash
docker stop container_name
```

👉 Sends **SIGTERM → SIGKILL (if needed)**



###  docker kill

Forcefully stops container

```bash
docker kill container_name
```

👉 Sends **SIGKILL immediately**



###  docker start

Starts a stopped container

```bash
docker start container_name
```



### Start + Attach

```bash
docker start -ai container_name
```

👉 Starts and logs into container






### docker pause

```bash
docker pause container_name
```

👉 Freezes container processes



### docker unpause

```bash
docker unpause container_name
```

👉 Resumes execution

---

## Accessing Containers

---

### docker attach

```bash
docker attach container_name
```

👉 Connects to main process

**Risk:**

* If you exit → container may stop



### docker exec (IMPORTANT)

```bash
docker exec -it container_name /bin/bash
```

👉 Opens new shell inside container

#### Why better than attach?

* Safe
* Does not affect main process
* Can open multiple sessions

---

## Managing Containers

---

### docker rename

```bash
docker rename old_name new_name
```

👉 Changes container name



### docker rm

```bash
docker rm container_name
```

👉 Deletes container

📌 **Important:**

* Container must be stopped before executing this command



### Force Remove

```bash
docker rm -f container_name
```

👉 Removes running container

---

## Managing Images

---

###  docker rmi

```bash
docker rmi image_name
```

👉 Deletes Docker image

📌 **Notes:**

* Cannot delete if container is using it
* Use `-f` to force

---

## Bulk Operations

---

### Stop All Containers

```bash
docker stop $(docker ps -q)
```

👉 Stops all running containers

---

## 🎯 Summary

* `docker create` → only creates
* `docker run` → create + start
* `-it` → interactive container
* `stop` vs `kill` → graceful vs force
* `exec` is safer than `attach`
* Containers have lifecycle states

