# Amazon Inspector: Automated Vulnerability Management & Remediation

## 🎯 Project Overview
In this project, **I implemented a continuous security monitoring pipeline** using Amazon Inspector. I focused on securing a serverless architecture by identifying, analyzing, and remediating software vulnerabilities within AWS Lambda functions.

As the cloud landscape evolves, manual security audits are no longer sufficient. **I directed this project** to demonstrate how an event-driven security posture can automatically protect resources the moment they are deployed.

---

## 🛠️ Technology Stack
* **Cloud Provider:** AWS (Amazon Web Services)
* **Security Service:** Amazon Inspector
* **Compute:** AWS Lambda (Python 3.x)
* **Vulnerability Intelligence:** National Vulnerability Database (NVD)

---

## 🚀 The Process

### 1. Activating Continuous Monitoring
I began by enabling Amazon Inspector. Unlike traditional scanners, **I configured it to provide environment-wide coverage**, ensuring that any new deployment of EC2 instances, ECR images, or Lambda functions would be instantly assessed.

> <img width="1919" height="771" alt="Screenshot 2025-12-22 034636" src="https://github.com/user-attachments/assets/82d9915b-f271-41db-adf6-8db445632d4a" />


### 2. Identifying Vulnerabilities
Upon the initial scan, Inspector flagged a **Medium Severity** vulnerability: `CVE-2023-32681`. 
* **The Issue:** An outdated `requests` library in the `get-request` Lambda function.
* **My Analysis:** I cross-referenced the finding with the NVD database to understand the impact on our application's data integrity.

### 3. Targeted Remediation
**I took direct action** to secure the code. By accessing the Lambda development environment, I modified the `requirements.txt` file to ensure the latest, patched version of the library would be used.

```python
# Updated requirements.txt to pull latest secure version
requests
