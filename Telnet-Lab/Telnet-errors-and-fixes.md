# Errors and Fixes: Telnet Lab

This file documents the issues encountered during the Telnet Lab and the steps taken to resolve them. These notes are intended to aid troubleshooting in similar scenarios.

---

## 1. **Error: Devices Unable to Ping Each Other**
- **Symptom:** PC was unable to ping the router, resulting in "Request Timed Out."
- **Cause:** Interface on the router or PC was not configured properly or was administratively down.
- **Fix:**
  1. Verified that both the PC and router interfaces had correct IP configurations:
     - PC: `192.168.1.2/24`
     - Router FastEthernet0/0: `192.168.1.1/24`
  2. Ensured that the router interface was enabled using the `no shutdown` command.
  3. Retested connectivity using the `ping` command.

---

## 2. **Error: Duplicate IP Address**
- **Symptom:** Router logs displayed `%IP-4-DUPADDR: Duplicate address 192.168.1.1 on FastEthernet0/0`.
- **Cause:** Another device in the network was assigned the same IP as the router's FastEthernet0/0 interface.
- **Fix:**
  1. Identified the duplicate IP address using logs and interface settings.
  2. Changed the conflicting device's IP address to an unused one within the subnet.
  3. Retested by pinging both devices to confirm unique IP assignment.

---

## 3. **Error: Telnet Access Not Working**
- **Symptom:** Attempting to connect via Telnet resulted in "Connection Refused" or no response.
- **Cause:** Telnet was not properly configured on the router.
- **Fix:**
  1. Configured the router for Telnet access:
     ```plaintext
     Router#configure terminal
     Router(config)#line vty 0 4
     Router(config-line)#password cisco
     Router(config-line)#login
     Router(config-line)#transport input telnet
     Router(config-line)#exit
     ```
  2. Retested Telnet functionality using the PC's command prompt.

---

## 4. **Error: Unable to Enter Privileged EXEC Mode on Telnet**
- **Symptom:** Accessing Telnet only provided basic user mode (Router>), and entering `enable` returned "% No password set."
- **Cause:** No enable password was set on the router.
- **Fix:**
  1. Set an enable password on the router:
     ```plaintext
     Router#configure terminal
     Router(config)#enable password cisco
     Router(config)#exit
     ```
  2. Retried entering privileged EXEC mode during the Telnet session by typing `enable` and entering the password.

---

## 5. **Error: Incorrect Subnet Configuration**
- **Symptom:** Devices in the same network could not communicate with each other.
- **Cause:** Subnet mask mismatch between PC and router interfaces.
- **Fix:**
  1. Updated the subnet mask on the PC and router interfaces to match (`255.255.255.0`).
  2. Verified connectivity using `ping` commands between devices.

---

## 6. **Error: Router Not Responding to Telnet**
- **Symptom:** Telnet connection failed even after configuration.
- **Cause:** Router interfaces were not configured with the correct gateway IP for the PC.
- **Fix:**
  1. Confirmed that the PC’s default gateway was set to the router’s FastEthernet0/0 IP (`192.168.1.1`).
  2. Verified router’s interface IP settings with `show ip interface brief`.
  3. Ensured that the router’s Telnet service was correctly configured and retested.

---

## 7. **Error: Telnet Session Freezes**
- **Symptom:** Telnet session froze while connected to the router.
- **Cause:** Network latency or incorrect session termination.
- **Fix:**
  1. Terminated the session using `Ctrl + Shift + 6` followed by `x`.
  2. Checked network latency with `ping` to ensure stable connectivity.
  3. Reconnected via Telnet after verifying proper configuration.

---

These troubleshooting notes outline the key issues faced and the solutions applied during the Telnet Lab. Proper configuration, verifying settings, and understanding error messages are critical to resolving similar issues in the future.

