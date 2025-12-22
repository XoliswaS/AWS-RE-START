
# 🛠️ Lab 266: Troubleshooting a Complex Network Issue

This repository documents my structured approach to diagnosing and resolving a real-world network outage. **I directed this investigation** by moving systematically through the OSI layers to isolate a failure point between a local host and a remote server.

---

## 🎯 Project Objective
To demonstrate a professional troubleshooting methodology—moving from the local physical/data link layer up to the application layer—to restore service to a disconnected system.

---

## 📑 Detailed Implementation Guide

### Phase 1: Problem Definition & Initial Scoping
**I began by verifying the symptoms** of the reported outage to narrow the search area.
1.  **Verification:** Attempted to access a remote resource (e.g., a website or remote server) to confirm the failure.
2.  **Symptom Analysis:** Noted the specific error message (e.g., "Connection Timed Out" vs. "Unknown Host") to determine if the issue was related to routing or DNS.

### Phase 2: Local Stack & Interface Audit
**I inspected the local machine** to ensure the problem wasn't "starting at home."
1.  **Interface Check:** Used `ip link` to verify that the network interface (eth0) was `UP`.
2.  **Configuration Check:** Used `ip addr` to ensure a valid IP was assigned.
3.  **Default Gateway:** Ran `ip route` to confirm the host knew the exit path for non-local traffic.



### Phase 3: Segmented Connectivity Testing
**I used a "Divide and Conquer" approach** to find the break in the chain.
1.  **Loopback Test:** Pinged `127.0.0.1` to confirm the local TCP/IP stack was functional.
2.  **Gateway Ping:** Attempted to ping the Default Gateway. 
    * *Discovery:* If the gateway fails, the issue is on the local subnet.
3.  **External IP Ping:** Pinged a known public IP (e.g., `8.8.8.8`).
    * *Discovery:* If successful, the internet is reachable, and the issue is likely DNS-related.

### Phase 4: Path & Name Resolution Analysis
**I isolated the routing path and the application layer.**
1.  **Path Tracing:** Executed `traceroute` to identify the specific router/hop where packets were being dropped.
2.  **DNS Verification:** Used `nslookup` or `dig` to see if the system could resolve the target hostname to an IP address.
3.  **Resolution:** Checked `/etc/resolv.conf` and `/etc/hosts` for incorrect entries preventing successful name resolution.


### Phase 5: Incident Resolution & Verification
1.  **Remediation:** Based on findings (e.g., updating a DNS entry or restarting a network service), I applied the fix.
2.  **Final Test:** Successfully pinged the remote target and verified application-level access (HTTP/HTTPS).
3.  **Documentation:** Logged the root cause and the solution to prevent future occurrences.

---

## 📊 Troubleshooting Matrix
| Tool | Layer | Logic |
| :--- | :--- | :--- |
| `ip link` | Layer 2 | Is the cable/interface "on"? |
| `ip addr` | Layer 3 | Do I have an identity on this network? |
| `ping` | Layer 3 | Can I "see" the target? |
| `traceroute` | Layer 3 | Where exactly did the connection drop? |
| `nslookup` | Layer 7 | Can I translate names to numbers? |

