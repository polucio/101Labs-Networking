# Lab 1: SSH Configuration

Welcome to **Lab 1**, where we explore how to enable SSH access to a Cisco router. This README provides detailed instructions on the objectives, tools, and walkthrough for this lab.

## Objectives

1. Enable SSH on a Cisco router.
2. Secure remote access to network devices.
3. Test SSH and Telnet connectivity.

## Lab Purpose

SSH is a secure protocol for accessing and managing network devices. Unlike Telnet, SSH encrypts the connection, making it the preferred choice for secure communication in corporate environments. In this lab, you will configure SSH on a router and test its functionality.

## Lab Setup and Requirements

### Tools

- **Packet Tracer** for simulating network topology.

### Topology

- Two routers connected directly via a crossover cable.
- Configure one router to allow SSH access and test connectivity from the other.

---

## Lab Walkthrough

### Task 1: Configure Router Hostnames

1. Drag two Cisco routers (e.g., 1941 models) onto the Packet Tracer canvas.
2. Connect the routers using a crossover cable.
3. Open the CLI for each router and configure the hostnames:

   **On Router0:**
   ```
   Router>enable
   Router#config t
   Router(config)#hostname R0
   R0(config)#
   ```

   **On Router1:**
   ```
   Router>enable
   Router#config t
   Router(config)#hostname R1
   R1(config)#
   ```

   Ensure you select "no" when prompted for the configuration dialog.

### Task 2: Configure IP Addresses

1. Assign IP addresses to the Ethernet interfaces and bring them up:

   **On R0:**
   ```
   R0(config)#interface g0/0
   R0(config-if)#ip address 192.168.1.1 255.255.255.0
   R0(config-if)#no shut
   ```

   **On R1:**
   ```
   R1(config)#interface g0/0
   R1(config-if)#ip address 192.168.1.2 255.255.255.0
   R1(config-if)#no shut
   ```

2. Test connectivity by pinging R1 from R0:

   ```
   R0#ping 192.168.1.2
   ```

   A successful ping confirms connectivity.

### Task 3: Enable SSH on R1

1. Configure a domain name and generate RSA keys:

   ```
   R1(config)#ip domain-name 101labs.net
   R1(config)#crypto key generate rsa
   ```

   - Choose a modulus size of 1024 bits.

2. Configure SSH settings:

   ```
   R1(config)#ip ssh time-out 60
   R1(config)#ip ssh authentication-retries 2
   ```

3. Set up login credentials:

   ```
   R1(config)#line vty 0 15
   R1(config-line)#transport input ssh
   R1(config-line)#password cisco
   R1(config-line)#login
   ```

4. Verify SSH configuration:

   ```
   R1#show ip ssh
   ```

   Ensure SSH is enabled and configured correctly.

### Task 4: Test SSH Connectivity

1. From R0, connect to R1 using SSH:

   ```
   R0#ssh -l admin 192.168.1.2
   ```

   - Use the password `cisco` when prompted.
   - Once connected, you should see the R1 prompt.

2. Exit the session using `Ctrl + Shift + 6`, followed by `X`.

### Task 5: Test Telnet Refusal

1. Attempt to connect to R1 using Telnet from R0:

   ```
   R0#telnet 192.168.1.2
   ```

   - The connection should be refused, confirming SSH-only access.

---

## Notes

- Always use SSH for secure device access.
- Ensure that the domain name and RSA keys are configured correctly for SSH to work.
- Use a strong password for the VTY lines to enhance security.

---

## Troubleshooting

1. **Ping Fails:**
   - Verify the IP configurations on both routers.
   - Check the status of the Ethernet interfaces (`show ip interface brief`).

2. **RSA Key Generation Fails:**
   - Ensure a domain name is configured before generating keys (`ip domain-name <domain>`).
   - Verify sufficient processing power and memory on the router for key generation.
   - Use a modulus size of at least 1024 bits for compatibility.

3. **SSH Fails:**
   - Confirm that the RSA keys are generated and SSH is enabled (`show ip ssh`).
   - Ensure the correct username and password are used.

4. **Telnet Not Refused:**
   - Verify that `transport input ssh` is set for all VTY lines.
   - Verify the IP configurations on both routers.
   - Check the status of the Ethernet interfaces (`show ip interface brief`).

2. **SSH Fails:**
   - Confirm that the RSA keys are generated and SSH is enabled (`show ip ssh`).
   - Ensure the correct username and password are used.

3. **Telnet Not Refused:**
   - Verify that `transport input ssh` is set for all VTY lines.

---

## Additional Resources

- [SSH Overview](https://en.wikipedia.org/wiki/Secure_Shell)
- [Packet Tracer Documentation](https://www.netacad.com/courses/packet-tracer)
- [Cisco Router Configuration Guide](https://www.cisco.com/c/en/us/td/docs/routers/)
