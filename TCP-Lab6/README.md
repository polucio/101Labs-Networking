# Lab 6: TCP Packet Analysis

## Objective

This lab demonstrates how to recognize and analyze TCP packets using tools like Wireshark and Putty. You will learn how TCP underpins connection-oriented protocols such as Telnet and FTP.

## Lab Purpose

TCP (Transmission Control Protocol) is a foundational part of the TCP/IP suite, enabling reliable, connection-oriented communication. This lab explores TCP through Telnet, examining the underlying packet structure and security concerns.

## Lab Setup and Requirements

### Tools

- **VirtualBox** and **Wireshark** installed on a Windows 10 VM, or
- A home PC with Wireshark and Putty (downloadable from [Putty.org](https://putty.org/)).

### Topology

- A PC running Wireshark and Putty.
- External Telnet hosts (refer to [telnet.org](https://www.telnet.org/htm/places.htm) for accessible servers).

---

## Lab Walkthrough

### Task 1: Install Putty

1. Download and install Putty from [https://putty.org](https://putty.org).
2. Configure it for Telnet connections.

### Task 2: Identify Accessible Telnet Hosts

1. Use [telnet.org](https://www.telnet.org/htm/places.htm) to find hosts that allow Telnet connections.
2. Test multiple hosts, as availability may vary.

### Task 3: Configure Wireshark

1. Launch Wireshark on your PC.
2. Select the appropriate network interface for capturing traffic.
3. Start a packet capture session.

### Task 4: Establish a Telnet Session

1. Open Putty and configure it for Telnet:
    - Change the connection type from SSH to Telnet.
    - Enter a valid Telnet host (e.g., `telehack.com`).
2. Start the Telnet session and interact with the host.

### Task 5: Analyze Captured Traffic

1. In Wireshark, filter the capture by typing `telnet` in the filter box.
2. Observe the captured packets and their details.

### Task 6: Examine TCP Fields

1. Click on a Telnet packet in Wireshark to expand its details.
2. Analyze the TCP fields, including:
    - Source Port (default is 23 for Telnet).
    - Sequence and Acknowledgment numbers.
    - Flags (SYN, ACK, FIN, etc.).

3. Examine the bottom frame to view the actual data being transmitted, noting that Telnet sessions are unencrypted.

### Task 7: Security Concerns

1. Observe how Telnet transmits data, including passwords, in plain text.
2. Use this as a learning point to understand the security risks of Telnet.

---

## Notes

- This lab demonstrates how Telnet uses TCP as its transport protocol.
- Wireshark provides a detailed view of TCP headers, helping to understand how data flows through the network.
- Due to its lack of encryption, Telnet is not recommended for secure environments.

---

## Troubleshooting

1. **Initial Issue:**
   - Attempting to connect to telehack.com on port 143 resulted in the error: Unable to open connection to telehack.com port 143: Name or service not known.

   **Resolution:**
   - Tested connectivity to telehack.com on the default Telnet port (23).
   - Changed the port in PuTTY and Telnet commands from 143 to 23, which is the correct port for Telnet communication on telehack.com.

2. **No Packets Captured in Wireshark:**
   - Verify that the correct network interface is selected.
   - Ensure Wireshark is running with administrative privileges.

3. **Telnet Session Fails:**
   - Test different hosts from [telnet.org](https://www.telnet.org/htm/places.htm).
   - Ensure the Telnet service is enabled on the host.

4. **No TCP Data Visible:**
   - Ensure the Wireshark filter is set to `telnet`.
   - Check that the session generates traffic (e.g., by typing commands in Telnet).
   - Verify that the correct network interface is selected.
   - Ensure Wireshark is running with administrative privileges.

2. **Telnet Session Fails:**
   - Test different hosts from [telnet.org](https://www.telnet.org/htm/places.htm).
   - Ensure the Telnet service is enabled on the host.

3. **No TCP Data Visible:**
   - Ensure the Wireshark filter is set to `telnet`.
   - Check that the session generates traffic (e.g., by typing commands in Telnet).

---

## Additional Resources

- [TCP Overview](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)
- [Telnet Protocol](https://en.wikipedia.org/wiki/Telnet)
- [Wireshark Documentation](https://www.wireshark.org/docs/)

---

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---

Happy analyzing!
