# Lab 7: UDP Communication

Welcome to **Lab 7**, where we explore the fundamentals of the User Datagram Protocol (UDP) and learn to recognize and analyze UDP packets. This README provides detailed instructions on the objectives, tools, and walkthrough for this lab.

## Objectives

1. Recognize and analyze UDP packets.
2. Understand the role of UDP in networking and its use cases.
3. Use tools like Wireshark to capture and inspect UDP traffic.

## Lab Purpose

UDP is a connectionless protocol used by many services and applications, such as RIP, DNS, SNMP, and DHCP. While it offers low overhead, it does not guarantee delivery or acknowledgments. Understanding UDP is essential for working with various networking protocols and services.

## Lab Setup and Requirements

### Tools

- **Kali Linux** with Wireshark pre-installed.
- A local machine or VirtualBox with internet access.

### Topology

You can:

- Use Wireshark on a Kali Linux installation or live environment.
- Use Wireshark on a virtual machine in VirtualBox.

Ensure your system can access the internet, as you will perform a DNS lookup for analysis.

---

## Lab Walkthrough

### Task 1: Install Wireshark

1. Wireshark is pre-installed in most Kali Linux distributions. If not, install it using:

   ```bash
   sudo apt update
   sudo apt install wireshark -y
   ```

2. Verify the installation:

   ```bash
   wireshark --version
   ```

### Task 2: Prepare the Browser

1. Open a web browser on your Kali Linux system, but do not input any URL yet.
2. Ensure the browser's DNS cache is cleared to prompt a fresh DNS lookup.

   ```bash
   sudo systemd-resolve --flush-caches
   ```

### Task 3: Launch Wireshark

1. Open Wireshark on Kali Linux.
2. Select the correct network interface to monitor (e.g., `eth0`, `wlan0`, etc.).
3. Click on the interface name to start capturing traffic.

### Task 4: Generate Traffic

1. In your browser, visit a website that is not cached locally (e.g., `example.com`).
2. This action will trigger a DNS lookup, which uses UDP.

### Task 5: Filter DNS Packets

1. Stop the capture in Wireshark by clicking the red square.
2. Use the filter bar to search for DNS packets:

   ```
   dns
   ```

   Note: The filter must be entered in lowercase.

### Task 6: Analyze UDP Packets

1. Click on one of the DNS packets in the capture window.
2. Expand the UDP header section and examine the fields. Key fields to note:

   - Source Port
   - Destination Port
   - Length
   - Checksum

3. Observe that UDP packets lack fields like sequence numbers and flags, which are present in TCP.

### Task 7: Inspect the Checksum

1. In the UDP header, locate the checksum field.
2. Understand that while UDP has minimal error checking, the checksum ensures basic data integrity.

### Task 8: Compare with Protocol Behavior

- Note that some protocols, like DNS, start with UDP but may switch to TCP under specific circumstances (e.g., for zone transfers or if no response is received).

---

## Notes

- UDP provides low overhead and is used in applications where speed is preferred over reliability.
- Use Wireshark to thoroughly examine packet headers and learn the differences between TCP and UDP.
- Refer to the official UDP documentation for further study.

---

## Troubleshooting

1. **Wireshark Not Capturing Traffic**:
   - Ensure you run Wireshark with root privileges on Kali Linux:

     ```bash
     sudo wireshark
     ```

   - Confirm the correct network interface is selected.

2. **DNS Lookup Not Working**:
   - Verify your internet connection.
   - Use a different website or clear your DNS cache again.

3. **No UDP Packets Found**:
   - Double-check your Wireshark filter.
   - Ensure the capture was started before generating traffic.

---

## Additional Resources

- [Wireshark Documentation](https://www.wireshark.org/docs/)
- [UDP on Wikipedia](https://en.wikipedia.org/wiki/User_Datagram_Protocol)
- [Kali Linux Documentation](https://www.kali.org/docs/)

---

### **Acknowledgments**
Lab based on "101 Labs - CompTIA Network+" by Paul Browning.

---

### **References**
Browning, Paul. *101 Labs - CompTIA Network+: Hands-on Practical Labs for the N10-008 Exam.*

