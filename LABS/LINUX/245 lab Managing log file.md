# 📜 Step-by-Step: Linux Log Management & System Observability

This project documents my technical process for managing, rotating, and analyzing Linux system logs. **I directed this workflow** to ensure that server storage remains optimized and that system errors are easily searchable for rapid troubleshooting.

---

## 🛠 Project Objective
To implement a robust logging strategy that prevents disk-space exhaustion and provides a clear audit trail for system events using `rsyslog`, `logrotate`, and `journalctl`.

---

## 📑 Detailed Implementation Guide

### Phase 1: Locating & Analyzing Core Logs
**I began by identifying the critical telemetry files** required for system monitoring.
1.  **System Events:** Navigated to `/var/log/` to analyze the `syslog` (or `messages`) file for kernel and service-level events.
2.  **Security Audits:** Inspected `/var/log/auth.log` (or `secure`) to identify SSH login attempts and escalation of privileges (sudo).
3.  **Real-Time Debugging:** Executed `tail -f /var/log/syslog` to monitor system behavior live while restarting services.

### Phase 2: Configuring Automated Log Rotation
To ensure logs do not consume 100% of the disk, **I configured the `logrotate` utility**.
1.  **Configuration Entry:** Accessed `/etc/logrotate.conf` to understand global settings.
2.  **Custom Rule Creation:** Created a specific configuration file in `/etc/logrotate.d/myapp` with the following parameters:
    * **Rotation Frequency:** `weekly`
    * **Retention:** `rotate 4` (keeps 4 weeks of history)
    * **Compression:** `compress` (uses gzip to save space)
    * **Post-Rotation:** Used `postrotate` scripts to restart logging services after a file is moved.



### Phase 3: Advanced Querying with `journalctl`
**I transitioned to modern systemd-journal analysis** to perform faster, filtered searches.
1.  **Boot Logs:** Executed `journalctl -b` to analyze errors that occurred during the last system startup.
2.  **Service Isolation:** Used `journalctl -u ssh` to filter logs specifically for the SSH daemon.
3.  **Time-Based Filtering:** Ran `journalctl --since "1 hour ago"` to isolate recent incidents during a simulated outage.
4.  **Priority Filtering:** Used `journalctl -p err` to hide informational messages and focus exclusively on system errors.

### Phase 4: Storage Optimization Testing
1.  **Manual Trigger:** Ran `logrotate -f /etc/logrotate.conf` to force a rotation.
2.  **Verification:** Verified that new `.gz` compressed files were created and that the active log file was truncated to 0 bytes.

---

## 📊 Key Results
* **Disk Efficiency:** Compression reduced the storage footprint of logs by approximately 85%.
* **Audit Readiness:** Established a 4-week retention policy for all critical security logs.
* **Resolution Speed:** Reduced troubleshooting time by using filtered `journalctl` queries instead of manual file scrolling.

---

