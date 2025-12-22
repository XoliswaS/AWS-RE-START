# AWS Hands-on Lab: Troubleshooting IPv4 & Network Connectivity

## 👤 Project Overview
In this technical lab, I stepped into the role of a **Cloud Support Engineer** to resolve a networking reachability issue for a simulated Fortune 500 client. This project allowed me to apply theoretical knowledge of **VPC architecture**, **IPv4 addressing**, and **Internet Gateways** to a practical, high-stakes scenario.

My goal was not just to fix the connectivity gap, but to provide a clear, professional analysis of the underlying network principles.

---

## 📞 The Challenge
**The Scenario:** A client named Jess (Cloud Admin) reported that two EC2 instances ($A$ and $B$) were in the same public subnet, yet Instance $A$ could not reach the internet. 

**The Investigation:**
* **Instance A:** No internet access.
* **Instance B:** Full internet access.
* **Bonus Inquiry:** The client was considering using a public IP range ($12.0.0.0/16$) for an internal VPC and needed professional guidance on the risks involved.


<img width="1655" height="871" alt="image" src="https://github.com/user-attachments/assets/6a433df9-4fc5-4ef3-9534-913cbe4bb252" />

---

## 🛠️ Step-by-Step Lab Execution

I followed a **bottom-up troubleshooting approach**, beginning at the instance level (Layer 3 of the OSI model) and moving up to the VPC configuration.

### 1. Comparative Analysis
I accessed the **AWS Management Console** and navigated to the EC2 Dashboard. By comparing the networking properties of both instances, I identified the root cause:
* **Observation:** Instance $B$ had a Public IPv4 address assigned, but **Instance A only had a Private IP**.
* **Diagnosis:** Without a Public IP, the Internet Gateway (IGW) cannot perform the necessary Network Address Translation (NAT) to route traffic back from the internet to Instance $A$.


<img width="1572" height="812" alt="Screenshot 2025-12-22 022054" src="https://github.com/user-attachments/assets/c68f903f-c69f-4dbe-81e2-8284f22e9fdc" />

### 2. Implementing the Solution
To restore connectivity, I performed the following steps in the AWS Console:
* **Allocated an Elastic IP:** Created a static, public IPv4 address.
* **Associated the IP:** Manually linked the Elastic IP to Instance $A$'s network interface.
* **Verification:** Confirmed that Instance $A$ could now successfully reach external endpoints (e.g., `ping 8.8.8.8`).

### 3. Scaling for the Client
To prevent this issue from recurring, I modified the **Subnet Settings** within the VPC Dashboard. I enabled **"Auto-assign public IPv4 address"** so that any future instances launched by the client would be internet-capable by default.


---

## 🔬 Technical Insight: Public vs. Private IP Addressing

I provided the client with a strategic warning against using $12.0.0.0/16$ (a public range owned by AT&T) for their internal VPC.

| IP Type | Purpose | Risk of using Public Ranges ($12.x.x.x$) internally |
| :--- | :--- | :--- |
| **Private (RFC 1918)** | Internal VPC traffic | **None.** This is the industry standard. |
| **Public** | Global Internet communication | **High.** Creates a "routing black hole." |

**Why it matters:** If the client uses a public range for internal traffic, their instances will never be able to reach the *actual* websites or services hosted on those IPs in the real world. The VPC will mistakenly keep that traffic "local."

---

## 🎯 Summary of My Learning
Through this lab, I demonstrated:
* **Analytical Thinking:** Identifying specific configuration gaps in a complex environment.
* **AWS Proficiency:** Navigating the EC2 and VPC dashboards to implement networking fixes.
* **Professional Communication:** Explaining technical "Whys" to a client in a way that is easy to understand and follow.

---
