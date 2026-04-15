# 🐳 Day 04 - Dockerfile (Image Automation & Best Practices)

---

## 🧠 What You’ll Learn

- What is a Dockerfile  
- How to automate image creation  
- Core Dockerfile instructions  
- RUN vs CMD  
- COPY vs ADD  
- ENV vs ARG  
- ENTRYPOINT, EXPOSE, VOLUME  
- Building real-world applications  

---

## 📄 What is a Dockerfile?

A Dockerfile is a text file that contains instructions to build a Docker image automatically.

👉 Instead of manually creating images using `docker commit`, Dockerfile is used in real-world projects.



### Dockerfile Workflow

1. Write Dockerfile  
2. Build image using:

docker build -t image_name:tag .

3. Run container from image  

---

## Dockerfile Instructions Explained

---

###  FROM

Defines base image (mandatory)

Example:
FROM ubuntu



###  RUN

Executes commands during image build time

Example:
RUN apt update -y  
RUN apt install git -y  


### COPY

Copies files from local system → image

Example:
COPY index.html /tmp  



### ADD

Same as COPY + extra features:
- Auto extract `.tar` files  
- Download from URL  

👉 Use COPY unless extra features are needed  


### WORKDIR

Sets default working directory

Example:
WORKDIR /app  



### CMD

Runs command during container start

Example:
CMD ["python", "app.py"]

👉 Can be overridden  


### ENTRYPOINT

Defines main command of container

Example:
ENTRYPOINT ["node", "app.js"]

👉 Higher priority than CMD  


### EXPOSE

Defines port used by container

Example:
EXPOSE 3000  


### ENV

Runtime environment variable

Example:
ENV APP_ENV=production  



### ARG

Build-time variable

Example:
ARG VERSION=1.0  

👉 Not available inside container  


### VOLUME

Creates persistent storage

Example:
VOLUME ["/data"]



### LABEL

Adds metadata

Example:
LABEL author="Phani Krishna"

---

##  Important Differences


### RUN vs CMD

RUN → Build time  
CMD → Runtime  



### COPY vs ADD

COPY → Simple copy  
ADD → Copy + extract + download  


### ENV vs ARG

ENV → Runtime  
ARG → Build time  

---
## USEFULL COMMANDS:

### docker build

docker build -t myimage:v1 .

- -t → name:tag  
- . → current directory  



### docker inspect

docker inspect container_name

👉 Used to view container details  

---

## 🌍 Real-World Example (Node.js App)

Dockerfile:
```bash
FROM node:lts-alpine  
WORKDIR /app  
COPY . .  
RUN yarn install --production  
CMD ["node", "src/index.js"]  
EXPOSE 3000  
```
---

# 🎯 Summary

- Dockerfile automates image creation  
- RUN → build time, CMD → runtime  
- COPY preferred over ADD  
- ENV vs ARG → runtime vs build time  
- docker build creates images  
