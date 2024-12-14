# Lab 2: DNS Configuration

Welcome to **Lab 2**, where we explore the fundamentals of Domain Name System (DNS) configuration. This README provides detailed instructions on the objectives, tools, and walkthrough for this lab.

## Objectives

1. Learn to configure a DNS entry on a server.
2. Test DNS resolution from a client device.
3. Understand the role of DNS in translating hostnames to IP addresses.

## Lab Purpose

DNS is a critical service that allows the use of human-readable hostnames instead of numerical IP addresses in network communication. This lab demonstrates how to create and test DNS entries, helping you gain hands-on experience with this essential network service.

## Lab Setup and Requirements

### Tools

- **Packet Tracer** for simulating network topology.

### Topology

- A server and a host PC connected via a switch.
- Ensure the network allows communication between the devices.

---

## Lab Walkthrough

### Task 1: Setup the Network

1. In Packet Tracer, drag a generic host PC and a server onto the canvas.
2. Connect the Ethernet ports of both devices to a generic or Cisco switch.
3. Assign the following IP configurations:

   **On the Host PC:**
   - IP Address: `192.168.1.5`
   - Subnet Mask: Auto-generated
   - DNS Server: `192.168.1.1`

   **On the Server:**
   - IP Address: `192.168.1.1`
   - Subnet Mask: `255.255.255.0`

### Task 2: Verify Connectivity

1. Open the Command Prompt on the host PC.
2. Ping the server to ensure connectivity:

   ```bash
   ping 192.168.1.1
   ```

3. A successful response confirms proper network setup.

### Task 3: Test DNS Resolution

1. On the host PC, open a web browser.
2. Enter the URL `www.mypage.com`. The browser will not resolve the name since there is no DNS entry yet.

### Task 4: Configure DNS on the Server

1. On the server, open the `DNS` service configuration.
2. Add a new DNS record:

   - Record Type: `A Record`
   - Hostname: `www.mypage.com`
   - IP Address: `192.168.1.1`

3. Click `Add` and ensure the DNS service is enabled.

### Task 5: Retest DNS Resolution

1. Return to the host PC's web browser.
2. Enter the domain name `www.mypage.com`.
3. The browser should now resolve the name to the server's IP address and load the page.

---

## Notes

- DNS simplifies network communication by using hostnames instead of IP addresses.
- Always ensure the DNS server's IP address matches the one configured on the client device.
- The default record type for most DNS entries is `A Record`, which maps hostnames to IP addresses.

---

## Troubleshooting

1. **Ping Fails:**
   - Check the network connections.
   - Ensure correct IP configuration on both devices.

2. **DNS Resolution Fails:**
   - Verify the DNS server IP address on the host PC.
   - Ensure the DNS service is active and the record is correctly configured.

3. **No Response in Browser:**
   - Confirm connectivity using the `ping` command.
   - Recheck DNS entries on the server.

---

## Additional Resources

- [DNS Overview](https://en.wikipedia.org/wiki/Domain_Name_System)
- [Packet Tracer Documentation](https://www.netacad.com/courses/packet-tracer)
- [Networking Basics](https://www.cisco.com/c/en/us/solutions/enterprise-networks/networking-basics.html)
