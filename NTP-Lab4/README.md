# Network Time Protocol (NTP) Lab

## Objective
Learn how to configure a Cisco router to synchronize its clock with an NTP server.

## Lab Setup
- **Topology**: A Cisco 1841 router connected to a generic server using FastEthernet.
- **IP Addresses**:
  - Router: `192.168.1.2`
  - Server: `192.168.1.1`

## Steps
1. Connect the router and server using a crossover cable.
2. Configure IP addresses on both devices.
3. Enable NTP service on the server.
4. Configure the router to use the NTP server.
5. Verify NTP synchronization using:
   - `show ntp associations`
   - `show ntp status`
   - `show clock`

## Troubleshooting

During the lab, several issues were encountered and resolved:

### **1. Ping to the NTP Server Failing**
- **Issue**: The router could not ping the server (`192.168.1.1`), resulting in 0% success.
- **Cause**: The server's IP address was not configured properly.
- **Solution**:
  - Rechecked the server's FastEthernet IP settings and assigned the correct IP address:
    ```plaintext
    Server IP: 192.168.1.1
    Subnet Mask: 255.255.255.0
    ```

---

### **2. `show ntp status` Reporting `Clock is unsynchronized`**
- **Issue**: The router displayed `Clock is unsynchronized` in `show ntp status`.
- **Cause**:
  - The NTP service on the server was disabled.
  - The router's NTP configuration needed to be reset.
- **Solution**:
  - Enabled the NTP service on the server via Packet Tracer:
    - Go to **Services > NTP** and toggle the service to **On**.
  - Cleared and reconfigured the NTP server on the router:
    ```plaintext
    Router#config t
    Router(config)#no ntp server 192.168.1.1
    Router(config)#ntp server 192.168.1.1
    Router(config)#end
    ```

---

### **3. `show running-config` Pagination**
- **Issue**: The `show running-config` output was paginated, making it difficult to capture the full configuration.
- **Cause**: The `terminal length 0` command was not supported in the current IOS version.
- **Solution**:
  - Manually navigated through the output using **Spacebar**.
  - Captured the output incrementally.

---

### **4. `write memory` Command Not Working**
- **Issue**: The `write memory` command resulted in an error.
- **Cause**: The IOS version required the modern `copy` command instead.
- **Solution**:
  - Used the updated syntax to save the configuration:
    ```plaintext
    Router#copy running-config startup-config
    ```

---

## Commands Used
```plaintext
interface fastethernet0/0
ip address 192.168.1.2 255.255.255.0
no shut
ntp server 192.168.1.1
show ntp associations
show ntp status
show clock
copy running-config startup-config
