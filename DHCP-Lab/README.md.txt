# DHCP and Troubleshooting Lab

## Objective
This lab demonstrates how to configure DHCP on a Cisco router, troubleshoot IP conflicts, and resolve network connectivity issues using Cisco Packet Tracer.

## Topology
Include a visual representation of the network topology here. (e.g., upload a screenshot of your Packet Tracer setup).

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

## Screenshots and Supporting Files
Include screenshots and configurations from Packet Tracer here.

---

## Future Work
- Test VLAN segmentation and routing.
- Experiment with more advanced DHCP configurations, such as reservations and exclusions.
