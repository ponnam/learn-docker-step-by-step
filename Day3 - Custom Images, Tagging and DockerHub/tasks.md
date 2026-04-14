# 🛠️ Day 03 - Custom Images, Tagging & Docker Hub

---

## 🎯 Objective

* Work inside containers
* Install packages
* Create custom Docker image
* Tag and push images to Docker Hub

---

### Task 3.1: Pull Ubuntu Image

```bash
docker pull ubuntu
```



### Task 3.2: Create Interactive Container

```bash
docker run -it --name cont1 ubuntu
```

###  Task 3.3: Install Required Packages

Inside container:

```bash
apt update
apt install git maven apache2 tree -y
```

### Task 3.4: Verify Installed Packages

```bash
git --version
apache2 -v
tree --version
mvn -v
```


### Task 3.5: Detach from Container

Press:

CTRL + P + Q



### Task 3.6: Verify Container is Running

```bash
docker ps
```

### Task 3.7: Attach Back to Container

```bash
docker attach cont1
```

### Task 3.8: Create Files

```bash
touch file{1..10}
ll
```

### Task 3.9: Create Custom Image - ponnam

```bash
docker commit cont1 ponnam
```

### Task 3.10: Verify Image

```bash
docker images
```

### Task 3.11: Create Container from Custom Image - ponnam

```bash
docker run -it --name cont2 ponnam
```


### Task 3.12: Verify Installed Packages

```bash
git --version
apache2 -v
tree --version
mvn -v
```

---

### Task 3.13: Create Local Tag

```bash
docker image tag ubuntu latestubuntu
docker images
```

### Task 3.14: Create Remote Tag

```bash
docker image tag ubuntu:22.04 <your-dockerhub-username>/remotetag_ubuntu
docker images
```

### Task 3.15: Login to Docker Hub

```bash
docker login
```


### Task 3.16: Push Image to Docker Hub

```bash
docker push <your-dockerhub-username>/remotetag_ubuntu
```

### Task 3.17: Verify in Browser

👉 Open:
https://hub.docker.com

👉 Check your repository

### Task 3.18: View Image History

```bash
docker image history ubuntu
```

---

## 🎯 Final Outcome

After completing this lab, you will:

* Customize containers
* Create Docker images manually
* Understand tagging system
* Push images to Docker Hub
* Explore image layers
