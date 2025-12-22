# AWS Hands-on Lab: Managing Persistence with Elastic IPs (EIP)

## 👤 Project Overview
In this second technical simulation, I acted as a **Cloud Support Engineer** for a Fortune 500 client, Bob (Cloud Admin). The project focused on solving a critical infrastructure stability issue where dynamic IP changes were breaking downstream resources. 

I successfully replicated the issue, analyzed the behavior of **Public vs. Private IPv4 addresses**, and implemented a persistent solution using **AWS Elastic IPs (EIP)**.

---

## 📞 The Scenario
**The Client:** Bob, Cloud Administrator.
**The Issue:** The client has a "Public Instance" that must be stopped and started frequently to save on costs.
**The Conflict:** Every time the instance restarts, it is assigned a new, random Public IP. This "dynamic" behavior breaks the static configurations of Bob's other connected resources.


<img width="1160" height="734" alt="Screenshot 2025-12-22 024448" src="https://github.com/user-attachments/assets/ba4c12cc-620a-4fdc-9170-d399ef28e6b9" />


---

## 🛠️ Troubleshooting & Implementation (Step-by-Step)

### Phase 1: Replicating the "Dynamic IP" Issue
To understand the client's pain point, I built a test environment to observe IP behavior during state changes:
1. **Instance Launch:** I launched a `t3.micro` instance running **Amazon Linux 2** in a Public Subnet with "Auto-assign Public IP" enabled.
2. **Initial Audit:** I recorded the initial **Public IPv4** and **Private IPv4** addresses from the Networking tab.
3. **The State Change Test:**
    * **Action:** I performed a "Stop" command on the instance.
    * **Observation:** The **Public IPv4 address was released** (became empty), while the **Private IPv4 remained persistent**.
    * **Action:** I performed a "Start" command.
    * **Result:** A brand new Public IPv4 was assigned. This confirmed the customer's issue: standard Public IPs are **dynamic** and do not survive an instance stop/start cycle.

<img width="1583" height="772" alt="image" src="https://github.com/user-attachments/assets/773b8543-d205-4663-be12-f43e881ac8dc" />


### Phase 2: Implementing the Static Solution (Elastic IP)
To provide Bob with a permanent entry point that survives restarts, I utilized **AWS Elastic IPs**:
1. **Allocation:** I navigated to **Network & Security > Elastic IPs** and allocated a new EIP from Amazon’s pool.
2. **Association:** I manually associated this EIP with the "test instance" and its corresponding Private IP.
3. **Final Verification:** I stopped and started the instance again. 
    * **Success:** The Public IPv4 address (now the EIP) **remained identical** before and after the restart.

---<img width="1592" height="811" alt="Screenshot 2025-12-22 031408" src="https://github.com/user-attachments/assets/9cf8fedc-3b86-47f8-98a2-6089f5c307e3" />


## 🔬 Technical Analysis: Static vs. Dynamic
I summarized the following findings for the client to explain why their original setup failed:

| Address Type | Persistence | Cost Factor | Behavior |
| :--- | :--- | :--- | :--- |
| **Private IP** | Persistent | Included | Stays with the instance for its lifetime. |
| **Public IP (Auto-assigned)** | **Dynamic** | Free | Released whenever the instance is stopped. |
| **Elastic IP (EIP)** | **Static** | Hourly (if unused) | Remains mapped to the account/instance until manually released. |

---

## 🎯 Solution Summary & Findings
By implementing an **Elastic IP**, I provided a solution that balances Bob's need for **cost-saving** (stopping the instance when not in use) with **architectural stability** (a static IP that doesn't break external links). This lab demonstrated my ability to distinguish between different IP behaviors and apply the correct AWS resource to meet specific business requirements.

---
