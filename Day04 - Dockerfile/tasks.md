# 🛠️ Day 04 - Dockerfile & Image Build

---

## 🎯 Objective

* Create Dockerfile
* Build custom images
* Understand Dockerfile instructions
* Run containers from images

---

### Task 6.1: Create Docker Image using Dockerfile

#### Task 6.1.1: Create Dockerfile

```bash
vi Dockerfile
```

Paste:

```dockerfile
FROM ubuntu
RUN apt update -y
RUN apt install git maven tree apache2 -y
```


#### Task 6.1.2: Build Image

```bash
docker build -t myimage:v1 .
```


#### Task 6.1.3: Verify Image

```bash
docker images
```

---

### Task 6.2: Run Container

```bash
docker run -it --name mycont1 myimage:v1
```

---

### Task 6.3: Verify Installed Packages

```bash
git --version
apache2 -v
tree --version
mvn -v
```

---

### Task 6.4: RUN vs CMD

#### Task 6.4.1: Create Dockerfile:

```bash
vi Dockerfile
```

```dockerfile
FROM ubuntu
RUN apt update -y
RUN apt install git maven -y
CMD apt install tree apache2 -y
```


#### Task 6.4.2: Build Image

```bash
docker build -t myimage:v2 .
```


#### Task 6.4.3: Run Container

```bash
docker run -it --name mycont2 myimage:v2
```

#### Task 6.4.4: Observe the Container process creation and Notedown what happens with CMD and RUN

---

### Task 6.5: COPY vs ADD

#### Task 6.5.1: Create Dockerfile:

```dockerfile
FROM ubuntu
RUN apt update -y
RUN apt install maven git tree apache2 -y
COPY index.html /tmp
ADD https://dlcdn.apache.org/maven/maven-3/3.9.11/binaries/apache-maven-3.9.11-bin.tar.gz /tmp
```


#### Task 6.5.2: Build Image

```bash
docker build -t myimage:v3 .
```


#### Task 6.5.3: Run Container

```bash
docker run -it --name mycont3 myimage:v3
```


#### Task 6.5.4: Verify Files

```bash
cd /tmp
ls -l
```

---

### Task 6.6: WORKDIR & LABEL
#### Task 6.6.1: Create Dockerfile
```bash
vi Dockerfile
```

Paste the below content:

```dockerfile
FROM ubuntu
RUN apt update -y
RUN apt install git maven tree apache2 -y
COPY index.html /tmp
ADD https://dlcdn.apache.org/maven/maven-3/3.9.11/binaries/apache-maven-3.9.11-bin.tar.gz /tmp
WORKDIR /tmp
LABEL author="Krishna"
```


#### Task 6.6.2: Build Image

```bash
docker build -t myimage:v4 .
```



#### Task 6.6.3: Run Container

```bash
docker run -it --name mycont4 myimage:v4
```

#### Task 6.6.4: Observe the Working directory

You must be in /tmp

```bash
pwd
```
then, exit from the container

#### Task 6.6.5: Check Label

```bash
docker inspect mycont4 | grep author
```

---

### Task 6.7: ENV Variables
#### Task 6.7.1: Create Docker file
```bash
vi Dockerfile
```
Paste the Content:

```dockerfile
FROM ubuntu
RUN apt update -y
RUN apt install maven git tree apache2 -y
ENV name=Krishna
ENV client=Teraskill
```
####  Task 6.7.2: Build Image

```bash
docker build -t myimage:v5 .
```

####  Task 6.7.3: Run Container

```bash
docker run -it --name mycont5 myimage:v5
```

#### ✅ Task 6.7.4: Verify ENV

```bash
echo $name
echo $client
```

---

### Task 6.8: VOLUME & EXPOSE
#### Task 6.8.1: Create Dockerfile
```bash
vi Dockerfile
```
Pasthe the content:

```dockerfile
FROM ubuntu
RUN apt update -y
RUN apt install maven git tree apache2 -y
VOLUME ["/volume1"]
EXPOSE 8080
```

#### Task 6.8.2: Build the Image & Run container

```bash
docker build -t myimage:v6 .
docker run -it --name mycont6 myimage:v6
```

---

### Mini-Project1: Real-World Project (Node.js App)

#### Step 1.1: Clone Application
```bash
git clone https://github.com/docker/getting-started-app.git 
cd getting-started-app
```

#### Step 1.2: Create Dockerfile
```bash
vi Dockerfile
```

Paste the content:
```Dockerfile
FROM node:lts-alpine 
WORKDIR /app COPY . . 
RUN yarn install --production 
CMD ["node", "src/index.js"] 
EXPOSE 3000
```
#### Step 1.3: Build Image
```bash
docker build -t gettingstarted .
```

#### Step 1.4: Run Container
```bash
docker run -d -p 3000:3000 gettingstarted
```
Note: Docker host's 3000 post must be opened in security group, if you ar eusing EC2 instance.

#### Step 1.5: Verify Running containers
```bash
docker ps
```

#### step 1.6: Access Application
Open Browser:  
http://EC2-PublicIP:3000


### Task 6.9: Cleanup

```bash
docker stop $(docker ps -q)
docker rm $(docker ps -a -q)
docker rmi -f $(docker images -q)
```

---

## 🎯 Final Outcome

After completing this lab, you will:

* Write Dockerfiles
* Build images professionally
* Understand Dockerfile instructions
* Replace manual image creation
