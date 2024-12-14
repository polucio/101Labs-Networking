# DHCP and Troubleshooting Lab

## Objective

This lab demonstrates how to configure DHCP on a Cisco router, troubleshoot IP conflicts, and resolve network connectivity issues using Cisco Packet Tracer. Additionally, it explores optional enhancements for network configuration.

## Steps Performed

### 1. Router Configuration

1. Configured DHCP with the following settings:
    - **Pool Name**: 101Pool
    - **Network**: 192.168.1.0/24
    - **Default Gateway**: 192.168.1.1
    - **DNS Server**: 8.8.8.8

    Commands used:
    ```plaintext
    ip dhcp pool 101Pool
    network 192.168.1.0 255.255.255.0
    default-router 192.168.1.1
    dns-server 8.8.8.8
    ```

2. Assigned an IP address to the router's interface:
    ```plaintext
    interface FastEthernet0/0
    ip address 192.168.1.1 255.255.255.0
    no shutdown
    ```

### 2. Switch Configuration

1. Configured VLAN1 for management and enabled ports for device connectivity:
    ```plaintext
    interface Vlan1
    ip address 192.168.1.10 255.255.255.0
    no shutdown
    ```

2. Ensured all connected ports were active and assigned to the correct VLAN.

### 3. Troubleshooting Steps

- **Resolved IP Conflicts**:
    - Identified conflicting devices using `show mac address-table` on the switch.
    - Updated IP configurations to ensure no duplicate IPs existed.

- **Verified Connectivity**:
    - Successfully pinged devices to confirm reachability:
        ```plaintext
        ping 192.168.1.4
        ping 192.168.1.1
        ```

## Results

- DHCP successfully assigned IP addresses to devices.
- All devices are reachable, and IP conflicts were resolved.

## Optional Enhancements

- Experimented with static routes to test inter-VLAN communication.
- Configured static DNS server settings for all devices.

---

## Additional Notes from Original Lab

### Lab 5: DHCP Configuration

### Objectives
1. Configure a DHCP server to allocate IP addresses dynamically.
2. Set up host devices to obtain IP information using DHCP.
3. Verify the DHCP configuration on hosts.

### Tools
- **Packet Tracer** for simulating network topology.

### Topology
- A generic server connected to a Cisco switch using a straight-through cable.
- Hosts connected to the same switch, configured to obtain IP addresses via DHCP.

### Tasks Overview
1. Configure the DHCP server on the generic server.
2. Set hosts to obtain IP information dynamically.
3. Verify configurations using `ipconfig` and Packet Tracer device information.
4. Experiment with adding DNS and default gateway configurations (not fully supported in Packet Tracer).

### Notes
- DHCP simplifies network administration by automating IP allocation.
- Ensure proper connectivity between the server and the hosts to avoid issues.
- Consider configuring a router to act as a DHCP server in advanced setups.
