#  Day 0 - Tasks (Docker Installation on Amazon Linux 2023 EC2)

---

## 🎯 Objective

* Set up an EC2 instance
* Install Docker on Amazon Linux 2023
* Configure users for Docker access
* Run Docker successfully

---

##  Task 1: Set Hostname (Optional but Recommended)

Set a meaningful hostname:

```bash
sudo hostnamectl set-hostname DockerHost
```

Switch to root user:

```bash
sudo -i
```

👉 Now your terminal should show:

```
root@DockerHost
```

---

##  Task 2: Install Docker on Amazon Linux 2023

---

### 🔹 Step 1: Check Kernel Version

```bash
uname -r
```

👉 Requirement: Kernel version should be **3.10 or higher**

---

### 🔹 Step 2: Verify 64-bit OS

```bash
uname -m
```

👉 Output should be:

```
x86_64
```

---

### 🔹 Step 3: Update System Packages

```bash
sudo dnf update -y
```


---

### 🔹 Step 4: Install Docker

```bash
sudo dnf install docker -y
```

👉 All dependencies will be installed automatically

---

### 🔹 Step 5: Verify Docker Installation

```bash
docker version
```

---

### 🔹 Step 6: Check Docker Service Status

```bash
systemctl status docker
```

---

### 🔹 Step 7: Start Docker Service

```bash
sudo systemctl start docker
```

---

### 🔹 Step 8: Verify Docker is Running

```bash
systemctl status docker
```

👉 Status should be: **active (running)**

---

### 🔹 Step 9: Enable Docker at Boot

```bash
sudo systemctl enable docker
```

> 📌 Note: Your notes used `chkconfig`, but `systemctl enable` is the modern approach

---

## 👤 Profile Configuration (Important Concept)

By default, only **root users** can run Docker.

To allow normal users:

### 🔹 Required Groups

* **wheel** → Admin (sudo access)
* **docker** → Run Docker without sudo

---

## Task 3: Create User & Configure Docker Access

---

### 🔹 Step 1: Create User

```bash
sudo useradd -m krishna
```

---

### 🔹 Step 2: Set Password

```bash
sudo passwd krishna
```

---

### 🔹 Step 3: Add User to Groups

```bash
sudo usermod -aG wheel krishna
sudo usermod -aG docker krishna
```

---

### 🔹 Step 4: Switch User

```bash
su - krishna
```

---

### 🔹 Step 5: Verify Docker Access (Without sudo)

```bash
docker version
```

👉 If working without `sudo` →  **Configuration successful**

---

## 🧪 Bonus Task: Run Your First Container 🎉

```bash
docker run hello-world
```

👉 This confirms Docker is working properly

---


## 🎯 Final Outcome

After completing this lab, you will:

* Install Docker on EC2
* Understand system requirements
* Manage Docker service
* Configure non-root Docker access
* Run your first container

---
