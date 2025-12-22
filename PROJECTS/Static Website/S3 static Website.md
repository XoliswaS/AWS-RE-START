
# 🍽️ Restaurant Cloud Launch: Static Web Hosting on AWS

## 📌 Project Overview
As part of a collaborative group challenge, **we architected and deployed a professional restaurant website** leveraging the power of AWS. This project moves beyond local development to demonstrate how cloud infrastructure can provide high availability, global scalability, and cost-efficient hosting for modern web applications.

---

## 🎯 Project Objectives
To successfully transition a restaurant concept from local code to a globally accessible cloud environment, **we focused on several key milestones:**
* **Functional Development:** Building a responsive, clean frontend for a restaurant use case.
* **Cloud Hosting:** Utilizing **Amazon S3 Static Website Hosting** to eliminate server management.
* **Resource Management:** Centralizing asset storage (logos, menu items, interiors) in the cloud.
* **Security & Governance:** Implementing IAM policies and public access configurations.
* **Team Collaboration:** Practicing agile documentation and synchronized cloud deployment.

---

## 🛠️ The Technology Stack

### **Frontend & Design**
* **HTML5:** Structured the menu and content sections.
* **CSS3:** Styled the aesthetic to match a modern dining brand.
* **JavaScript:** Added interactivity and dynamic elements.

### **AWS Cloud Infrastructure**
* **Amazon S3:** Used for 99.999999999% durability hosting and asset storage.
* **IAM (Identity & Access Management):** Configured permissions for secure team access.
* **AWS Management Console:** Used as the primary orchestration interface.

---

## ☁️ AWS Architecture & Services

### 🔹 Amazon S3 (The Backbone)
**I directed the setup of our S3 bucket** to act as our serverless web server. By enabling Static Website Hosting, we ensured:
* **Zero Server Maintenance:** No patching or OS management required.
* **Scalability:** The site automatically handles traffic spikes.
* **Optimized Costs:** We only pay for the storage and data transfer used.



### 🔹 IAM & Security
**We implemented strict security protocols** to ensure the site remained public while the backend stayed secure:
* Defined **Bucket Policies** to allow public `s3:GetObject` permissions for website visitors.
* Used **IAM Users** to manage who within the team could modify site files.

---

## 🚀 Step-by-Step Deployment Workflow

1.  **Asset Consolidation:** We gathered our HTML, CSS, and JS files along with high-res restaurant imagery.
2.  **Bucket Provisioning:** Created a uniquely named Amazon S3 bucket in a target region.
3.  **Hosting Activation:** Enabled the **Static Website Hosting** feature and designated `index.html` as the entry point.
4.  **Security Orchestration:** Updated the **Block Public Access** settings and wrote a JSON bucket policy to allow global read access.
5.  **Live Validation:** Deployed the files and accessed the site via the unique Amazon S3 website endpoint.



---

## 🧩 Team Contribution & Group Synergy
This project was a true collaborative effort. **Our team synchronized on:**
* **Design & Dev:** Sharing the workload of UI/UX and coding.
* **Cloud Ops:** Working together in the AWS Console to ensure correct configurations.
* **Documentation:** Drafting the presentation and this README to communicate our architecture clearly.

---

## 📊 Business Intelligence & Presentation
Beyond the code, **we delivered a high-level presentation** covering:
* **Cloud Value:** Why moving from on-premise to AWS saves restaurants money.
* **S3 Versatility:** Explaining why object storage is ideal for static assets.
* **Security First:** How AWS keeps restaurant and customer data protected.

---
































































































































