# 🛡️ Lab 281: Cloud Observability — Monitoring Amazon EC2

This project documents my technical workflow for establishing a robust monitoring and alerting framework for Amazon EC2 instances. **I directed this implementation** to ensure high availability, performance optimization, and proactive security auditing using **Amazon CloudWatch**.

---

## 🎯 Project Objective
To implement an automated monitoring solution that tracks system health metrics, identifies performance bottlenecks, and triggers real-time alerts when hardware or software thresholds are exceeded.

---

## 📑 Detailed Implementation Guide

### Phase 1: Metric Selection & Dashboarding
**I began by identifying the Key Performance Indicators (KPIs)** essential for server health.
1.  **Metric Analysis:** Leveraged standard CloudWatch metrics including **CPU Utilization**, **Disk I/O**, and **Network In/Out**.
2.  **Dashboard Creation:** Constructed a centralized CloudWatch Dashboard to provide a "single pane of glass" view of the instance's real-time performance.
3.  **Status Checks:** Configured monitoring for both **System Status Checks** (AWS hardware health) and **Instance Status Checks** (OS/software health).



### Phase 2: Alarm Configuration & Automation
**I implemented a proactive response strategy** by configuring CloudWatch Alarms to monitor for anomalies.
1.  **Threshold Definition:** Set a "Static Threshold" (e.g., CPU Utilization > 80% for 5 minutes).
2.  **Action Orchestration:** Configured the alarm to trigger specific actions:
    * **Notifications:** Integrated with **Amazon SNS** (Simple Notification Service) to send instant email alerts to the admin team.
    * **Auto-Recovery:** (Optional) Set up EC2 Auto-Recovery actions to reboot the instance if a system status check fails.

### Phase 3: Stress Testing & Incident Simulation
To verify the monitoring logic, **I performed a manual stress test** on the EC2 instance.
1.  **Load Generation:** Used Linux utilities (like `stress` or a heavy computational loop) to artificially inflate CPU usage.
2.  **Alarm Verification:** Monitored the CloudWatch console as the metric moved from `OK` to `ALARM` state.
3.  **Notification Audit:** Confirmed that the SNS email alert was delivered within the expected timeframe, validating the communication path.



### Phase 4: Log Management & Analysis
**I extended the monitoring scope** to include application and system logs.
1.  **CloudWatch Logs:** Configured the instance to push core system logs (`/var/log/messages`) to CloudWatch Logs.
2.  **Filter Patterns:** Created metric filters to scan logs for "Error" or "Critical" keywords, allowing for alerting based on log data rather than just hardware metrics.

---

## 📊 Monitoring Matrix
| Component | Monitoring Tool | Action on Failure |
| :--- | :--- | :--- |
| **CPU/RAM** | CloudWatch Metrics | SNS Email Alert |
| **Hardware Health** | System Status Check | Automated Recovery |
| **Application Errors** | CloudWatch Log Groups | Metric Filter Alarm |
| **Network Traffic** | VPC Flow Logs | Security Audit |

---

## 🧠 Lessons Learned
By completing this lab, **I mastered the lifecycle of Cloud Observability**. I learned that effective monitoring isn't about collecting *all* data, but about identifying the *right* metrics and automating the response to ensure 99.9% system uptime.

