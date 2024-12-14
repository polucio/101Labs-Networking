# Lab 4: Network Time Protocol (NTP) Configuration

Welcome to **Lab 4**, where we explore how to configure a Cisco router to synchronize its clock using an NTP server. This README provides detailed instructions on the objectives, tools, and walkthrough for this lab.

## Objectives

1. Enable an NTP server.
2. Configure a Cisco router to obtain its clock time from the NTP server.
3. Verify synchronization between the server and the router.

## Lab Purpose

NTP ensures accurate timekeeping for devices across a network, which is critical for logging, security protocols, and scheduling. This lab demonstrates the fundamental steps to set up an NTP server and configure a Cisco router to synchronize with it.

## Lab Setup and Requirements

### Tools

- **Packet Tracer** for simulating network topology.

### Topology

- A generic server connected to a Cisco router using a crossover cable.
- IP addresses assigned to both devices.

---

## Lab Walkthrough

### Task 1: Configure IP Addresses

1. Connect the server to the Cisco router using a crossover cable.
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

   **On the Server:**
   - Set the IP address to `192.168.1.1` with a subnet mask of `255.255.255.0`.

3. Test connectivity by pinging the server from the router:

   ```
   Router#ping 192.168.1.1
   ```

   A successful ping confirms connectivity.

### Task 2: Check the Router's Current Clock

1. View the current clock settings on the router:

   ```
   Router#show clock
   ```

   - The clock will display an internal, out-of-date time.

### Task 3: Configure the Router to Use the NTP Server

1. Set the NTP server's IP address on the router:

   ```
   Router#config t
   Router(config)#ntp server 192.168.1.1
   Router(config)#end
   ```

2. Save the configuration:

   ```
   Router#write memory
   ```

### Task 4: Configure the Server as an NTP Server

1. Set up the server to provide time via NTP. The server will use its system clock as the reference.
2. Ensure the NTP service is active on the server.

### Task 5: Verify NTP Synchronization

1. Wait a few minutes for the router to synchronize with the NTP server.
2. Check NTP associations on the router:

   ```
   Router#show ntp associations
   ```

   - Look for the `*` symbol, which indicates the selected time source.

3. Verify NTP status:

   ```
   Router#show ntp status
   ```

   - Confirm the clock is synchronized and the reference is the NTP server.

4. View the updated router clock:

   ```
   Router#show clock
   ```

   - The time should now be accurate.

---

## Notes

- NTP ensures accurate timekeeping, which is critical for log accuracy and troubleshooting.
- Ensure proper connectivity and correct IP configurations to avoid synchronization issues.
- It may take a minute for the router to synchronize with the server after configuration.

---

## Troubleshooting

1. **Ping Fails:**
   - Verify IP configurations on both the server and the router.
   - Check the status of the router interface with `show ip interface brief`.

2. **NTP Synchronization Fails:**
   - Ensure the server is configured to act as an NTP server.
   - Verify the router has the correct NTP server IP address.
   - Use `debug ntp` on the router to troubleshoot NTP messages.

---

## Additional Resources

- [NTP Overview](https://en.wikipedia.org/wiki/Network_Time_Protocol)
- [Packet Tracer Documentation](https://www.netacad.com/courses/packet-tracer)
- [Cisco Router Configuration Guide](https://www.cisco.com/c/en/us/td/docs/routers/)
