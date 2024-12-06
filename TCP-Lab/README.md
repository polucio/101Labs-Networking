# TCP-Lab

## Objective
The purpose of this lab was to establish a Telnet connection to a public server, analyze TCP traffic using Wireshark, and troubleshoot network connectivity issues.

---

## Lab Setup
### Tools Used:
- **Kali Linux** (running in VirtualBox)
- **PuTTY** (Telnet client)
- **Wireshark** (for traffic analysis)

### Target Host:
- **Server**: `telehack.com`
- **Port**: 23 (default Telnet port)

---

## Troubleshooting Steps
### Initial Issue:
Attempting to connect to `telehack.com` on port 143 resulted in the error:
Unable to open connection to telehack.com port 143: Name or service not known

### Resolution:

The issue was resolved by:

1. Testing connectivity to `telehack.com` on the default Telnet port (23).
2. Changing the port in PuTTY and Telnet commands from 143 to 23, which is the correct port for Telnet communication on `telehack.com`.
