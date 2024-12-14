# Lab 3: Telnet Configuration

Welcome to **Lab 3**, where we learn how to enable Telnet access on a Cisco router. This README provides detailed instructions on the objectives, tools, and walkthrough for this lab.

## Objectives

1. Enable Telnet access to a Cisco router.
2. Test Telnet functionality using a connected PC.
3. Understand the limitations and security concerns of Telnet.

## Lab Purpose

Telnet is a protocol for remotely connecting to network devices. However, it is not secure as it transmits data, including passwords, in plain text. This lab demonstrates how to configure Telnet for learning purposes but emphasizes its limitations in real-world applications.

## Lab Setup and Requirements

### Tools

- **Packet Tracer** for simulating network topology.

### Topology

- One PC connected to a Cisco router using a crossover cable.
- IP addresses assigned to both the PC and the router.

---

## Lab Walkthrough

### Task 1: Configure IP Addresses

1. Connect a generic PC to a Cisco router using a crossover cable.
2. Configure IP addresses on both devices:

   **On the Router:**
   ```
   Router>enable
   Router#config t
   Router(config)#interface g0/0
   Router(config-if)#ip address 192.168.1.2 255.255.255.0
   Router(config-if)#no shut
   Router(config-if)#end
   ```

   **On the PC:**
   - Set the IP address to `192.168.1.1` with a subnet mask of `255.255.255.0`.

3. Test connectivity by pinging the router from the PC:

   ```
   ping 192.168.1.2
   ```

   A successful ping confirms connectivity.

### Task 2: Enable Telnet Access

1. Configure the router to allow Telnet connections:

   ```
   Router#conf t
   Router(config)#line vty 0 15
   Router(config-line)#transport input telnet
   Router(config-line)#password cisco
   Router(config-line)#login
   Router(config-line)#end
   ```

2. This configuration allows Telnet connections on virtual terminal lines (VTY 0-15).

### Task 3: Test Telnet Connectivity

1. Open a terminal on the PC and connect to the router using Telnet:

   ```
   telnet 192.168.1.2
   ```

2. Enter the password `cisco` when prompted. The Telnet session should start, giving access to the router.

3. Exit the session using `Ctrl + Shift + 6`, followed by `X`.

### Task 4: Monitor Telnet Sessions

1. Use the `show line` command on the router to view active Telnet sessions:

   ```
   Router#show line
   ```

   The output will display the allocated virtual terminal lines for incoming connections.

---

## Notes

- Telnet is not encrypted, so avoid using it in secure environments.
- Use SSH instead of Telnet for secure communication.
- Ensure the password for VTY lines is strong to prevent unauthorized access.

---

## Troubleshooting

1. **Ping Fails:**
   - Verify the IP configurations on the PC and the router.
   - Check the status of the router interface with `show ip interface brief`.

2. **Telnet Fails:**
   - Ensure Telnet is enabled on the router with `transport input telnet`.
   - Verify that the correct password is used during login.

---

## Additional Resources

- [Telnet Overview](https://en.wikipedia.org/wiki/Telnet)
- [Packet Tracer Documentation](https://www.netacad.com/courses/packet-tracer)
- [Cisco Router Configuration Guide](https://www.cisco.com/c/en/us/td/docs/routers/)
