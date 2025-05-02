# 🚀 Node.js Application Deployment Guide

This repository is used for deploying a **Node.js application** on a **Linux server** using **PM2** for process management.

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

- A Linux server (e.g., Amazon EC2)
- Port 80 (HTTP) opened in the security group
- Git installed on the server
- Node.js installed on the server
- PM2 installed on the server

---

## 🛠️ Step-by-Step Setup

```bash
# 1️⃣ Clone the Repository

# SSH into your server and install Git
sudo yum install git -y

# Clone the repository
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name

# 2️⃣ Install Node.js and npm

# Install Node.js and npm
curl -fsSL https://rpm.nodesource.com/setup_18.x | sudo bash -
sudo yum install -y nodejs

# 3️⃣ Install Dependencies

# Install all dependencies from the package.json
npm install

# 4️⃣ Run the App

# Start the app
npm start

# It will run on:
# http://<your-server-ip>:3000

# ⚠️ App Stops on Logout?

# To keep the app running in the background:
nohup npm start &

# To store logs in a file:
nohup npm start > output.log 2>&1 &

# 🔍 Monitor or Stop the App

# Check if the app is running:
ps aux | grep index.js

# Stop the app:
pkill -f index.js

# ♻️ Use PM2 to Keep App Running

# 1️⃣ Install PM2
npm install -g pm2

# 2️⃣ Start the App with PM2
pm2 start index.js --name node-app

# PM2 will:
# - Keep your app running continuously
# - Restart the app in case of failure
# - Monitor logs and CPU/memory usage

# 3️⃣ Optional PM2 Commands
pm2 list                  # Show running apps
pm2 logs node-app         # View logs
pm2 restart node-app      # Restart app
pm2 stop node-app         # Stop app
pm2 delete node-app       # Delete app
pm2 startup               # Enable PM2 startup on reboot
pm2 save                  # Save running processes

# 🌐 Access the App
# Once the app is running on port 80, you can access it in the browser by navigating to:
# http://<your-ec2-public-ip>

# 📁 File Structure
# your-node-repo/
# ├── index.js
# ├── package.json
# └── package-lock.json

# 📌 Notes
# - Port 80 requires sudo if you're not using PM2 or another process manager with permission elevation.
# - Ensure security group allows inbound access on port 80.

# 📷 Sample Output
# Once everything is up and running, the app will show:
# Welcome to Sample Node.js Application
