# 🚀 Node.js Application Deployment Guide

This repository is used for deploying a **Node.js application** on a **Linux EC2 server** using **PM2** for process management.

---

## 🧰 Tools & Technologies Used

<table>
  <tr>
    <td><img src="https://img.shields.io/badge/Amazon%20EC2-%23232F3E.svg?style=for-the-badge&logo=amazon-ec2&logoColor=white" /></td>
    <td><img src="https://img.shields.io/badge/Amazon%20Linux-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white" /></td>
    <td><img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" /></td>
    <td><img src="https://img.shields.io/badge/PM2-2B037A?style=for-the-badge&logo=pm2&logoColor=white" /></td>
  </tr>
  <tr>
    <td><img src="https://img.shields.io/badge/npm-CB3837?style=for-the-badge&logo=npm&logoColor=white" /></td>
    <td><img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" /></td>
    <td><img src="https://img.shields.io/badge/Bash-121011?style=for-the-badge&logo=gnu-bash&logoColor=white" /></td>
  </tr>
</table>

---

## 📦 Prerequisites

- A Linux EC2 instance
- Port 80 (or 3000) open in your security group
- Basic knowledge of Linux terminal

---

## 🛠️ Deployment Steps


### 1️⃣ Connect to EC2 Instance

```bash
ssh ec2-user@<your-ec2-public-ip>
```

### 2️⃣ Install Git

```bash
sudo yum install git -y
```

### 3️⃣ Install Node.js and npm
```bash
sudo dnf install -y nodejs
```

### 4️⃣ Clone the Project Repository
```bash
git clone git@github.com:gou8m/sample-nodejs-application.git
cd sample-nodejs-application
```

### 5️⃣ Install Dependencies from package.json
```bash
npm install
```

### 6️⃣ Start the App (interactive mode)
```bash
npm start
# App will be available at http://<your-ec2-ip>:3000
```
### 7️⃣ Issue: App stops on logout or CTRL+C
### To fix that, use PM2 (a process manager)

### 8️⃣ Install PM2 Globally
```bash
npm install -g pm2
```

### 9️⃣ Run App with PM2
```bash
pm2 start index.js --name node-app
```

### ✅ PM2 ensures your app:
### - Runs continuously
### - Restarts on crashes
### - Provides monitoring and logs

### 🔄 Optional PM2 Commands

```bash
pm2 list                  # View all apps
pm2 logs node-app         # View logs
pm2 restart node-app      # Restart app
pm2 stop node-app         # Stop app
pm2 delete node-app       # Remove app
pm2 save                  # Save current process list
pm2 startup               # Enable PM2 on boot
```

### 🌐 Access the App
### Once the app is running via PM2 on your EC2 instance, access it in your browser:
```
http://<your-ec2-public-ip>
```

