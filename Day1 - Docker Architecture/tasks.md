# Day 01 - Tasks (Docker Commands & Image Management)

---

## 🎯 Objective

* Practice basic Docker commands
* Work with Docker images
* Interact with Docker Hub
* Understand container lifecycle

---

## Task 1.1: Check Docker Version

```bash
docker version
```

👉 Verify both **Client** and **Server** versions are displayed

---

## Task 1.2: View Docker System Information

```bash
docker info
```

👉 **Observe:**

* Number of containers
* Number of images
* Storage driver
* System details

---

## Task 1.3: View Available Docker Commands

```bash
docker
```

👉 **Scroll and observe:**

* Management commands
* General commands

---

## Task 1.4: Create Docker Hub Account

1. Open: https://hub.docker.com
2. Click **Sign Up**
3. Follow On-Screen instructions
3. Complete registration
4. Verify your email

---

## Task 1.4(a): Search for an Image

```bash
docker search ubuntu
```

👉 Observe:

* Name of image
* Description
* Stars (popularity)
* Official images

---

## Task 1.5: Download Ubuntu Image

```bash
docker pull ubuntu
```

---

## Task 1.6: Download Amazon Linux Image

```bash
docker pull amazonlinux
```

---

## Task 1.7: Download Tomcat Image

```bash
docker pull tomcat
```

---

## Task 1.8: List Downloaded Images

```bash
docker images
```

👉 **Observe:**

*  Repository
* Tag
* Image ID
* Size

---

## Task 1.9: Download Specific Version

```bash
docker pull ubuntu:22.04
```

👉 **Understand:**

* `ubuntu` → image name
* `22.04` → version (tag)

---

## 📋 Task 1.10: Verify Images Again

```bash
docker images
```

---

## Task 1.11: Run First Container

```bash
docker run hello-world
```

👉 **Expected:**

* Docker pulls image (if not present)
* Container runs successfully

---

## Task 1.12: List Running Containers

```bash
docker ps
```

OR

```bash
docker container ls
```

---

## Task 1.13: List All Containers

```bash
docker ps -a
```

OR

```bash
docker container ls -a
```

---

## Task 2.14: Observe Image Size vs OS Size

Check OS size (in Docker Host):


```bash
du -sh /
```

Check Docker images:

```bash
docker images
```

👉 Compare:

* OS size (~GBs)
* Image size (~MBs)

👉 **Conclusion:**
Containers are lightweight

---

## 🎯 Final Outcome

After completing this lab, you will:

* Execute basic Docker commands
* Pull images from Docker Hub
* Run containers
* Understand image vs container
* Explore container lifecycle

