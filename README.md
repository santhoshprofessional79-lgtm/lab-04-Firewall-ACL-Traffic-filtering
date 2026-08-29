# 🚀 SOC Analyst Network Foundations: Lab 4 (Firewall ACLs & Traffic Filtering)

Welcome to Lab 4! This simulation transitions from pure networking to proactive Network Security. I implemented an Access Control List (ACL) on a Cisco Router, treating it as a foundational network firewall to block a simulated compromised host while allowing legitimate traffic.

## 🛠️ Tools Used
* Cisco Packet Tracer 
* Router CLI (Standard IPv4 Access Control Lists)
* Simulation Mode (for visual packet drop verification)

---

## 📸 Lab Workflow & Configuration

 1. The Baseline Setup
 2. Action: Configured a Router as a default gateway between two networks: a user network (`192.168.1.0/24`) and a secure server network (`192.168.2.0/24`). Verified that both a legitimate user (`192.168.1.10`) and a simulated malicious host (`192.168.1.20`) could reach the target web server.

 2. Implementing the Firewall Rule (ACL)
Action: Acted as a SOC Analyst responding to an incident involving the malicious host. I wrote a Standard ACL to isolate the threat:
   `access-list 1 deny host 192.168.1.20` (Block the attacker)
   `access-list 1 permit any` (Allow legitimate traffic)
Application: Applied this ACL inbound on the Router's `Gig0/0` interface.

### 3. Verification & Packet Drop Analysis
Result: Successfully verified the ACL functionality in Simulation Mode. 
   Legitimate ICMP traffic from `192.168.1.10` successfully routed to the server.
   Malicious traffic from `192.168.1.20` was immediately dropped by the router, resulting in a "Destination host unreachable" message. *(See Packet Drop screenshot)*

---

## 🛡️ SOC & Security Takeaways
* **Threat Mitigation:** This lab mirrors the real-world SOC action of blacklisting a known malicious IP or isolating a compromised internal machine from lateral movement.
* **Implicit Deny & Zero Trust:** Understanding that any packet not explicitly permitted by an ACL is dropped by default (Implicit Deny), which is the foundational concept behind Zero Trust architectures, AWS Security Groups, and Next-Gen Firewalls (NGFW).
