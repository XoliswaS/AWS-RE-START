
Lab 160: Your Database Server & Interact With Your DB Using an App


Overview# 🗄️ AWS Database Integration: Building & Connecting a Scalable Backend

## 🎯 Project Overview
In this project, **I architected a database-driven application environment** on AWS. Moving beyond standalone compute, **I directed the deployment of a relational database server** and successfully established secure connectivity between a frontend application and a backend data store.

This lab simulates a real-world production scenario where application code must communicate with a persistent database to manage dynamic user data.

---

## 🛠️ Technology Stack
* **Cloud Provider:** AWS (Amazon Web Services)
* **Compute:** Amazon EC2 (Application Hosting)
* **Database Engine:** MySQL / MariaDB
* **Security:** AWS Security Groups (Port 3306)
* **Connectivity:** PHP/Python Application Integration

---

## 🚀 The Technical Workflow

### 1. Provisioning the Database Tier
**I deployed a dedicated database server**, ensuring the environment met specific performance and storage requirements. I focused on choosing the appropriate instance class to balance cost and query speed while ensuring the database engine was correctly initialized.

### 2. Network Security & Handshaking
A database is only as secure as its network configuration. **I implemented a strict "Least Privilege" network policy:**
* **Security Group Orchestration:** I configured the database firewall to block all public traffic, specifically allowing inbound traffic **only** from the Application Server's Security Group.
* **Isolation:** By restricting access to Port 3306, I ensured that the data layer remained shielded from the public internet.



### 3. Application-to-Database Interaction
**I successfully "closed the loop"** by configuring a live application to interact with the database.
* **Connection String Management:** I updated the application's configuration files with the Database Endpoint and credentials.
* **Data Validation:** I performed live CRUD (Create, Read, Update, Delete) operations through the App interface, verifying that data was being persisted correctly in the backend tables.

---

## 📊 Results & Key Achievements
| Metric | Implementation | Status |
| :--- | :--- | :--- |
| **Data Persistence** | Verified across instance reboots | ✅ Successful |
| **Network Security** | Zero public access to DB port | ✅ Validated |
| **Full-Stack Connectivity** | Frontend-to-Backend Sync | ✅ Active |



---

## 🧠 Lessons Learned
By completing this project, **I mastered the Three-Tier architecture logic**. I learned that managing a database server is as much about **networking and security** as it is about the data itself. Establishing a secure handshake between an EC2-hosted application and a database is a foundational skill that I now apply to all my full-stack cloud designs.

