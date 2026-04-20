# 🛠️ Day 06 - Docker Monitoring & Troubleshooting


## 🎯 Objective

- Monitor Docker system resources  
- Analyze container performance  
- Inspect running processes  
- Clean up unused resources  

---

## Docker System Monitoring

### Task 6.1: Check Docker Disk Usage
```bash
docker system df  
```

### Task 6.2: Detailed Disk Usage
```bash
docker system df -v  
```

### Task 6.3: View Full System Info
```bash
docker system info  
```

### Task 6.4: Monitor Live Events
```bash
docker system events  
```

👉 Press Ctrl + C to stop  

---

## Cleanup Tasks


### Task 6.5: Clean Unused Resources
```bash
docker system prune  
```

### ✅ Task 6.6: Remove Unused Volumes
```bash
docker system prune --volumes  
```

---  

## Container  Monitoring

###  Task 6.7: View Running Processes
```bash
docker top <container_name>  
```
Example:
```bash
docker top unruffled_chaplygin  
```


### Task 6.8: View Container Stats
```bash
docker stats unruffled_chaplygin  
```

### Task 6.9: Monitor Multiple Containers
```bash
docker stats unruffled_chaplygin mycont6  
```

### Task 6.10: View All Containers Stats
```bash
docker stats --all  
```

### Task 6.11: One-Time Stats Snapshot
```bash
docker stats --no-stream  
```
---

##  Port Mapping

### Task 6.12: View Port Mapping
```bash
docker port unruffled_chaplygin  
```

### Task 6.13: Check Specific Port
```bash
docker port unruffled_chaplygin 80  
```

---

## 🎯 Final Outcome

After completing this lab, you will:

- Monitor Docker system resources  
- Analyze container performance  
- Debug container issues  
- Clean up unused Docker resources  