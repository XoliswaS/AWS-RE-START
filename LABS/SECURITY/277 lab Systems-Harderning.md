# Systems Hardening with AWS Systems Manager Patch Manager

## 🎯 Project Overview
In this project, **I architected and executed an automated patch management strategy** for a hybrid fleet of Amazon EC2 instances. Managing updates across hundreds of servers is a significant logistical challenge; **I utilized AWS Systems Manager** to ensure that both Windows and Linux environments remained compliant with security policies without requiring manual intervention on every node.

---

## 🛠️ Technology Stack
* **Cloud Provider:** AWS (Amazon Web Services)
* **Management Service:** AWS Systems Manager (Patch Manager, Fleet Manager, Run Command)
* **Operating Systems:** Amazon Linux 2 & Windows Server 2019
* **Governance:** Custom Patch Baselines and Patch Groups

---

## 🚀 The Process

### 1. Automated Linux Patching
I began by targeting the Linux fleet. Using the **AWS-AmazonLinux2DefaultPatchBaseline**, I performed a "Scan and Install" operation. By leveraging **Tag-based targeting** (Patch Group: `LinuxProd`), I ensured that the security updates were applied only to the intended production environment.

### 2. Creating Custom Windows Baselines
Standard defaults aren't always enough for enterprise compliance. **I designed a custom Patch Baseline** specifically for Windows Server 2019:
* **Criteria:** Filtered for "Critical" and "Security" updates.
* **Risk Mitigation:** I implemented a **3-day auto-approval delay** to ensure that new patches have time to be vetted before hitting production.
* **Compliance:** Assigned a "Critical" compliance priority to ensure immediate visibility into any failed updates.

> 
<img width="1904" height="870" alt="Screenshot 2025-12-22 045806" src="https://github.com/user-attachments/assets/f1cc60af-04ee-49a6-a847-fa18a446f7bb" />

### 3. Orchestration via Run Command
To trigger the updates, **I utilized the Run Command capability**. Behind the scenes, Systems Manager executed the `AWS-RunPatchBaseline` document on my behalf. I monitored the live execution output to verify that the `WindowsProd` patch group was being successfully processed.

### 4. Fleet Compliance Verification
The final phase was validation. **I used the Compliance Dashboard** to audit the entire fleet. 
* **Result:** All six managed nodes (3 Linux, 3 Windows) moved to a "Compliant" status.
* **Granularity:** I drilled down into specific Node IDs to verify exactly which security KB articles were installed and when.

---

## 📊 Results & Security Posture

| Feature | Implementation |
| :--- | :--- |
| **Fleet Visibility** | Managed via SSM Fleet Manager |
| **Automation** | Zero-touch patching via SSM Documents |
| **Security Status** | 100% Compliant (6/6 Instances) |
| **Targeting** | Logical separation via `Patch Group` tags |



---

## 🧠 Lessons Learned
By completing this project, **I demonstrated the ability** to manage hybrid cloud environments at scale. I learned how to balance the need for rapid security patching with the operational stability required by production workloads—specifically through the use of approval delays and patch groups.


