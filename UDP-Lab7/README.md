# Lab 5: UDP Lab

## Objective
Learn how to recognize and analyze UDP packets using Wireshark. This lab demonstrates the simplicity and efficiency of the User Datagram Protocol (UDP), highlighting its use in DNS queries.

---

## Lab Purpose
UDP is a connectionless protocol commonly used by services and protocols such as RIP, DNS, SNMP, and DHCP. It offers low overhead but does not guarantee delivery. In this lab, we capture and analyze DNS traffic (which uses UDP by default) to observe its structure and behavior.

---

## Lab Setup
- **Tools**: Kali Linux, Wireshark, and a web browser.
- **Network**: The lab is run on a single machine, with Wireshark capturing live network traffic.
- **Files**:
  - `UDP_Lab.pcapng`: Wireshark capture file showing DNS traffic.


---

## Lab Steps

### Step 1: Install and Launch Wireshark
1. Verify Wireshark is installed:
   ```bash
   sudo apt update
   sudo apt install wireshark -y
