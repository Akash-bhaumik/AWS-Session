# Deploying a Node JS Application on AWS EC2

> **Note:** This project was completed while following the **"DevOps Zero to Hero"** playlist by **Abhishek Veeramalla**. This repository is a fork of the original [verma-kunal/AWS-Session](https://github.com/verma-kunal/AWS-Session) project, modified to resolve runtime errors and security vulnerabilities discovered during deployment.

---

## 🛠️ Bug Fixes & Security Improvements
While deploying this application, I identified and implemented the following technical improvements to ensure a stable production environment:

- **Fixed `ReferenceError: path is not defined`**  
  Corrected the `path` module import in `server.js`.  
  *Logic*: The application crashed because it attempted to use `path.resolve()` without first importing the Node.js `path` module. I added `const path = require("path");` to resolve this.

- **Security Dependency Update**  
  Updated `nodemon` from `^2.0.16` to `^3.1.14`.  
  *Logic*: The original version contained 3 high-severity security vulnerabilities. As a Cyber Security student, I performed an `npm audit` and patched these dependencies to ensure a secure environment.

- **Static Directory Configuration**  
  Refined the `.env` variable logic for `STATIC_DIR`.  
  *Logic*: Standardized the path to `"client"` to ensure the Express server correctly locates frontend assets on a Linux/Ubuntu file system.

---

## 🚀 Testing the Project Locally

1. **Clone this project**
   ```bash
   git clone https://github.com/Akash-bhaumik/AWS-Session.git
Setup environment variables in a .env file

env
DOMAIN="http://localhost:3000"
PORT=3000
STATIC_DIR="client"

PUBLISHABLE_KEY="your_stripe_publishable_key"
SECRET_KEY="your_stripe_secret_key"
Initialize and start the project

bash
npm install
npm run start
☁️ Deploying on AWS EC2
Step 1: Set up an AWS EC2 instance
Create an IAM user & login to your AWS Console

Access Type: Password

Permissions: Admin

Create an EC2 instance

OS Image: Ubuntu

Instance type: t2.micro

Key Pair: Create a new key pair & download .pem file

Step 2: Connect to the instance using SSH
bash
ssh -i instance.pem ubuntu@<IP_ADDRESS>
Step 3: Configure Ubuntu on remote VM
Update outdated packages and dependencies:

bash
sudo apt update
Install Git (DigitalOcean Guide)

Configure Node.js and npm (DigitalOcean Guide)

Step 4: Deploy the project on AWS
Clone this project in the remote VM

bash
git clone https://github.com/Akash-bhaumik/AWS-Session.git
Setup environment variables in a .env file

env
DOMAIN="http://<YOUR_ELASTIC_IP>:3000"
PORT=3000
STATIC_DIR="client"

PUBLISHABLE_KEY="your_stripe_publishable_key"
SECRET_KEY="your_stripe_secret_key"
Note: For this project, you must set up an Elastic IP Address for your EC2; that IP will be your DOMAIN.

Initialize and start the project

bash
npm install
npm run start
🔒 Security Note
You must edit the inbound rules in the security group of your EC2 instance to allow traffic on Port 3000.

🎉 Project Deployed on AWS
Your Node.js application is now live on AWS EC2 
