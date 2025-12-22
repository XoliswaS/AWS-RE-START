# 🚀 Step-by-Step: Deploying & Scaling Secure EC2 Web Servers

This project documents my technical process for launching, securing, and scaling virtual servers on AWS. **I directed this workflow** to demonstrate how to move from a manual "click-and-launch" process to an automated, protected deployment.

---<img width="605" height="443" alt="image" src="https://github.com/user-attachments/assets/3cca972f-4a94-44bc-a9f9-a9fefb1479cd" />


## 🛠 Project Objective
To deploy a functional Apache web server on Amazon EC2, implement production-grade security guardrails, and execute a vertical scaling strategy.

---

## 📑 Detailed Implementation Guide

### Phase 1: Automated Provisioning
**I chose to automate the server setup** to ensure consistency and speed.
1.  **AMI Selection:** Selected the **Amazon Linux 2023 AMI** for its optimized performance and security.
2.  **Instance Sizing:** Chose a `t3.micro` to balance cost and performance for a web-tier workload.
3.  **Bootstrapping (User Data):** I utilized the **Advanced Details** pane to inject a Bash script. This script automatically handled the installation and activation of the Apache web server upon the first boot.
    ```bash
    #!/bin/bash
    yum -y install httpd
    systemctl enable httpd
    systemctl start httpd
    echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html
    ```

### Phase 2: Security & Protection Configuration
**I implemented a "Security-First" configuration** by applying the following:
1.  **Termination Protection:** I explicitly enabled this setting to prevent the instance from being accidentally deleted during maintenance.
2.  **Security Group Refinement:** * I created a new Security Group named `Web Server security group`.
    * **Decision:** I removed the default SSH rule to close Port 22.
    * **Action:** Added a custom Inbound Rule for **HTTP (Port 80)** from `0.0.0.0/0` to allow public web traffic.



### Phase 3: Validation & Vertical Scaling
Once the instance was `Running`, **I verified the deployment** by accessing the Public IPv4 address in a browser.
1.  **State Management:** I stopped the instance to simulate a maintenance window.
2.  **Vertical Scaling:** I modified the **Instance Type** to a larger tier, demonstrating the elasticity of the cloud.
3.  **Verification:** I restarted the instance and verified the web server was still active and the hardware upgrade was successful.

### Phase 4: Resource Decommissioning
1.  **Guardrail Test:** I attempted to terminate the instance to verify that **Termination Protection** was active.
2.  **Cleanup:** I manually disabled protection and terminated the instance to ensure efficient resource cleanup and cost management.

---

## 📊 Key Results
* **Deployment Time:** < 3 minutes from launch to "Live" status.
* **Security:** 0 management ports exposed to the public internet.
* **Elasticity:** Successfully transitioned between different instance families.

---

## 📬 Connect with Me
* **LinkedIn:** [Your Link]
* **Portfolio:** [Your Website]

---
*Created by a Cloud Engineer focusing on secure, automated, and scalable compute.*
