# Secure Node.js Deployment on AWS EC2 🚀

This project demonstrates the end-to-end deployment of a Node.js application (integrated with Stripe) on an AWS EC2 instance. Originally part of the **"DevOps Zero to Hero"** roadmap by Abhishek Veeramalla, this fork includes critical security patches and runtime bug fixes discovered during the deployment process.

---

## 🛠️ My Contributions & Improvements
I focused on making this deployment stable and secure. My primary updates include:

* **Security Patching**: Performed a full security audit and updated `nodemon` from `^2.0.16` to `^3.1.14` to resolve 3 high-severity vulnerabilities.
* **Bug Fix (ReferenceError)**: Identified and resolved a runtime crash caused by a missing `path` module import in `server.js`.
* **Path Optimization**: Standardized the `STATIC_DIR` configuration to ensure consistent file serving on Ubuntu/Linux environments.
* **Documentation**: Enhanced the setup guide to include Stripe integration requirements.

---

## 🔒 Infrastructure & Security
* **AWS Security Groups**: Configured inbound rules to strictly allow traffic only on Port 22 (SSH) and Port 3000 (Application).
* **Secret Management**: Implemented `dotenv` to protect sensitive API keys (Stripe) from being exposed in version control.
* **Dependency Auditing**: Utilized `npm audit` to verify a 100% vulnerability-free production environment.



---

## 📋 Prerequisites
- An **AWS Account** (Free Tier is sufficient)
- A **Stripe Account** for API keys
- **Node.js** (v18 or higher) installed locally and on the server

---

## ⚙️ Setup Instructions

### 1. Environment Variables
Create a `.env` file in the root directory and add the following:
```env
DOMAIN="http://<YOUR_AWS_ELASTIC_IP>:3000"
PORT=3000
STATIC_DIR="client"

# Stripe Keys
STRIPE_SECRET_KEY="sk_test_..."
PUBLISHABLE_KEY="pk_test_..."
2. Deployment Steps (AWS EC2)
Clone the project on your Ubuntu instance:

Bash
git clone [https://github.com/Akash-bhaumik/AWS-Session.git](https://github.com/Akash-bhaumik/AWS-Session.git)
cd AWS-Session
Install Dependencies:

Bash
npm install
Start the Server:

Bash
npm run start
🛠️ Troubleshooting
During this project, I documented the following common issues:

ERR_INVALID_ARG_TYPE: Occurs if the .env file is not saved or the STATIC_DIR variable is missing.

ReferenceError: path is not defined: Fixed in this repo by importing the path module correctly for Linux directory resolution.

🤝 Credits
Original Project: verma-kunal/AWS-Session

Tutorial Guidance: Abhishek Veeramalla's "DevOps Zero to Hero" series

Maintained by Akash Bhaumik Final Year B.Tech Student in Cyber Security @ IEM, Kolkata


---
