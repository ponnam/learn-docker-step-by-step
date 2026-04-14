# 🐳 Day 03 - Custom Images, Tagging & Docker Hub

## 🧠 What You’ll Learn

* Working inside containers
* Creating custom Docker images
* Image tagging (local vs remote)
* Pushing images to Docker Hub
* Understanding image layers



##  Working Inside a Container

Once you enter a container using interactive mode:



👉 **You can:**

* Install Required packages
* Create files
* Configure environment

**Note:** Containers are minimal → Required packages must be installed manually

---

## Docker Commit (Creating Custom Image)



### docker commit

```bash
docker commit container_name image_name
```

👉 Creates a new image from an existing container

### 🧠 Use Case:

* Save current state of container
* Reuse pre-installed environment

📌 Example:

```bash
docker commit cont1 krishna
```


### ⚠️ Important Note

* This method is **manual**
* Not used in real-world production

👉 Real-world uses **Dockerfile (automation)**

---

## 🏷️ Docker Image Tagging



### What is Tag?

A tag = version label for an image

👉 Format:

```bash
image_name:tag
```

📌 Examples:

* ubuntu:latest
* ubuntu:20.04
* myapp:v1



### Types of Tags:



### 1. Local Tag

```bash
docker image tag ubuntu latestubuntu
```

👉 Exists only on your local system



### 2. Remote Tag

```bash
docker image tag ubuntu:22.04 username/image_name
```

👉 Used for pushing to Docker Hub

---

## Docker Registry (Docker Hub)



### docker login

```bash
docker login
```

👉 Connects your system to Docker Hub



### docker push

```bash
docker push username/image_name
```

👉 Uploads image to Docker Hub

📌 Requirement:

* Must have remote tag

---

## Image Layers & History


### docker image history

```bash
docker image history image_name
```

👉 **Shows:**

* Layers of image
* Commands used to build it

---

### 🧠 Why Important?

* Helps debug image
* Understand how image was built

---

# 🎯 Summary

* Containers can be customized
* `docker commit` creates image from container
* Tags help manage versions
* Remote tags are required for Docker Hub
* `docker push` uploads image
* Images are built in layers


