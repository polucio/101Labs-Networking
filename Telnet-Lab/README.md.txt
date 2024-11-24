# Telnet Lab

## Objective
Learn how to configure and test Telnet access on a Cisco router using Packet Tracer. This lab demonstrates the setup of Telnet for remote device management.

## Lab Purpose
Telnet allows remote connectivity to network devices but transmits data in plain text, making it unsuitable for secure environments. This lab focuses on enabling Telnet, testing its functionality, and understanding its limitations.

## Lab Topology
- **PC0:** Connected to `FastEthernet0/0` of the router with IP `192.168.1.1`.
- **Router (Cisco 1841):** Configured with IP addresses on both FastEthernet interfaces for testing Telnet access.
- **Server (Optional):** Connect a server to simulate additional network services.

### Network Configuration
| Device       | Interface       | IP Address    | Subnet Mask      |
|--------------|-----------------|---------------|------------------|
| PC0          | FastEthernet    | 192.168.1.1   | 255.255.255.0    |
| Router       | FastEthernet0/0 | 192.168.1.2   | 255.255.255.0    |
| Router       | FastEthernet0/1 | 192.168.2.1   | 255.255.255.0    |

## Lab Tasks
1. **Connect PC0 to the Router:**
   - Connect `PC0` to the `FastEthernet0/0` interface of the router.
   - Assign static IP addresses on both devices.
   - Test connectivity using `ping`.

2. **Enable Telnet Access on the Router:**
   - Enter configuration mode on the router:
     ```plaintext
     Router> enable
     Router# configure terminal
     Router(config)# line vty 0 4
     Router(config-line)# password cisco
     Router(config-line)# login
     Router(config-line)# transport input telnet
     ```

3. **Test Telnet from PC0:**
   - From `PC0`, open the command prompt and run:
     ```plaintext
     telnet 192.168.1.2
     ```
   - Enter the password (`cisco`) to access the router.

4. **Verify Telnet Connections:**
   - Use the `show users` and `show line` commands to verify active Telnet sessions.

5. **Secure Telnet (Optional):**
   - Configure an `enable secret` password on the router for administrative access:
     ```plaintext
     Router(config)# enable secret strongpassword
     ```

## Commands Used
```plaintext
# Assign IP addresses and enable interfaces
Router> enable
Router# configure terminal
Router(config)# interface fastEthernet0/0
Router(config-if)# ip address 192.168.1.2 255.255.255.0
Router(config-if)# no shutdown
Router(config)# interface fastEthernet0/1
Router(config-if)# ip address 192.168.2.1 255.255.255.0
Router(config-if)# no shutdown

# Configure Telnet access
Router(config)# line vty 0 4
Router(config-line)# password cisco
Router(config-line)# login
Router(config-line)# transport input telnet

# Optional: Set enable secret password
Router(config)# enable secret strongpassword
