# 🌐 Lab 265: Internet Protocol (IP) Troubleshooting & Network Diagnostics

This project documents my technical workflow for diagnosing and resolving network connectivity issues in a Linux environment. **I directed this investigation** using standard IP troubleshooting suites to isolate faults at various layers of the OSI model.

---

## 🎯 Project Objective
To demonstrate proficiency in network diagnostics by using a suite of command-line tools to verify IP configurations, test reachability, trace routing paths, and troubleshoot DNS resolution.

---

## 📑 Detailed Implementation Guide

### Phase 1: Local Interface & IP Verification
**I began by auditing the local host configuration** to ensure the network stack was initialized correctly.
1.  **IP Address Verification:** Used `ip addr show` to verify the assignment of IPv4 addresses to local interfaces (eth0/lo).
2.  **Routing Table Analysis:** Executed `ip route` to identify the **Default Gateway**, ensuring the system knew where to send traffic destined for outside the local subnet.
3.  **Interface Statistics:** Used `ip -s link` to check for hardware-level errors or dropped packets on the physical layer.

### Phase 2: Testing Connectivity & Reachability
**I performed targeted testing** to determine if the network path was open to both internal and external targets.
1.  **ICMP Testing:** Used `ping -c 4 <target_ip>` to check end-to-end reachability. I analyzed the **Round Trip Time (RTT)** to evaluate network latency.
2.  **Gateway Check:** Pinged the Default Gateway discovered in Phase 1 to isolate if the connectivity issue was local or external.

### Phase 3: Path Discovery & Route Tracing
To identify exactly where packets were being dropped, **I performed a hop-by-hop analysis**.
1.  **Traceroute Execution:** Ran `traceroute <domain_name>` to visualize the path to the destination.
2.  **Bottleneck Identification:** Identified high-latency hops or timeouts (`* * *`) to determine if an ISP or a specific router was causing the failure.
3.  **MTR (My Traceroute):** (Optional/Advanced) Used `mtr` to combine ping and traceroute into a single live-updating diagnostic view.


### Phase 4: DNS Resolution Troubleshooting
**I isolated the application layer** by verifying that the system could correctly translate domain names into IP addresses.
1.  **DNS Lookup:** Used `dig <domain_name>` to query DNS records and check response times from the configured nameservers.
2.  **Host Analysis:** Used `nslookup` for a quick verification of A-records and CNAMEs.
3.  **Resolution Logic:** Inspected `/etc/resolv.conf` to verify that the correct DNS recursive resolvers were being utilized.

---

## 📊 Results & Key Achievements
* **Fault Isolation:** Successfully distinguished between local configuration errors, gateway failures, and external DNS issues.
* **
