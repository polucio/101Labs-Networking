# Lab 8: ICMP Communication

Welcome to **Lab 8**, where we delve into the workings of the Internet Control Message Protocol (ICMP). This README provides detailed instructions on the objectives, tools, and walkthrough for this lab.

## Objectives

1. Recognize and analyze ICMP packets.
2. Understand the role of ICMP in reporting errors and network diagnostics.
3. Use tools like Wireshark to capture and inspect ICMP traffic.

## Lab Purpose

ICMP is a crucial protocol used by network devices to report errors and communicate network diagnostics. Unlike other TCP/IP protocols, ICMP is not used to transport data but for reliability and error messaging. One common use of ICMP is in the `ping` utility, which helps check connectivity.

## Lab Setup and Requirements

### Tools

- **VirtualBox** and **Wireshark**, or your home PC.
- A Windows 10 virtual machine (VM) or a local machine with internet access.

### Topology

You can either:

- Use Wireshark on your home PC.
- Install and run Wireshark on a Windows 10 VM.

Ensure your machine can access the internet to ping external websites.

---

## Lab Walkthrough

### Task 1: Install Wireshark

1. Download and install Wireshark from [https://www.wireshark.org](https://www.wireshark.org).
2. Follow the installation guide for your operating system.

### Task 2: Launch Wireshark

1. Open Wireshark on your PC or VM.
2. Select the correct network interface to monitor (e.g., Wi-Fi or Ethernet).
3. Click on the interface name to open the capture window.

### Task 3: Start Capturing Traffic

1. Ensure Wireshark is capturing general network traffic.
2. Look for ICMP packets in the capture window.

### Task 4: Ping a Website

1. Open the command line:

   - On Windows: Press `Win + R`, type `cmd`, and hit Enter.

2. Use the `ping` command to send ICMP packets:

   ```bash
   ping cisco.com
   ```

   Note: Some websites may block ICMP packets. If `ping` fails, try another URL or an internal machine on your network.

### Task 5: Filter ICMP Packets

1. Use Wireshark's filter bar to isolate ICMP traffic:

   ```
   icmp
   ```

2. Ensure the filter is typed in lowercase for it to work.

### Task 6: Analyze ICMP Packets

1. Observe ICMP echo request and reply packets in Wireshark.
2. Compare the packet details with the output in the command line.
3. Look for the following fields:

   - Response time
   - Packet length
   - Time-to-live (TTL)

4. Examine the TTL field in the IP header for deeper understanding.

---

## Notes

- ICMP packets provide valuable information about network reliability and diagnostics.
- Use Wireshark's detailed packet view to explore the structure and fields of ICMP packets.
- Analyze differences between echo requests and replies.

---

## Troubleshooting

1. **Wireshark Not Capturing Traffic**:
   - Ensure the correct interface is selected.
   - Run Wireshark with administrator privileges.

2. **Ping Not Working**:
   - Try an internal machine or ensure the destination allows ICMP traffic.

3. **No ICMP Packets in Wireshark**:
   - Double-check your filter syntax.
   - Ensure the interface being monitored is active.

---

## Additional Resources

- [Wireshark Documentation](https://www.wireshark.org/docs/)
- [ICMP Protocol on Wikipedia](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol)
- [Ping Command Documentation](https://www.computerhope.com/pinghlp.htm)

---

### **Acknowledgments**
Lab based on "101 Labs - CompTIA Network+" by Paul Browning.

---

### **References**
Browning, Paul. *101 Labs - CompTIA Network+: Hands-on Practical Labs for the N10-008 Exam.*
