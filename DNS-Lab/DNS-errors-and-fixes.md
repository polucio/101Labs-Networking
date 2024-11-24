# Errors and Fixes: DNS Lab

This file documents the errors encountered during the DNS Lab and the steps taken to resolve them. These notes aim to help troubleshoot similar issues in the future.

---

## 1. **Error: Duplicate IP Address**
- **Symptom:** Received `%IP-4-DUPADDR: Duplicate address` error during router configuration.
- **Cause:** The same IP address (`192.168.1.1`) was assigned to multiple devices or interfaces.
- **Fix:**
  1. Verified IP address assignments for all devices in the lab.
  2. Changed the conflicting IP address on the router's interface.
  3. Re-tested connectivity with `ping` to ensure the issue was resolved.

---

## 2. **Error: Interface Down**
- **Symptom:** Router interfaces showed `administratively down` or `protocol down` in the output of `show ip interface brief`.
- **Cause:** Interfaces were not enabled or had no connected cable.
- **Fix:**
  1. Used the `no shutdown` command on each interface to enable them.
  2. Verified that all cables were properly connected.
  3. Rechecked the interface status to ensure they were `up/up`.

---

## 3. **Error: PC Cannot Ping Router**
- **Symptom:** The PC timed out when pinging the router's interface.
- **Cause:** Incorrect gateway configuration or unconfigured DNS settings on the PC.
- **Fix:**
  1. Verified the PC's static IP configuration, ensuring it was in the same subnet as the router interface.
  2. Set the correct default gateway (router’s IP).
  3. Retested by pinging the router from the PC.

---

## 4. **Error: DNS Hostname Unresolved**
- **Symptom:** PC displayed "Host Name Unresolved" when querying the DNS server.
- **Cause:** DNS server was not configured with the required A record.
- **Fix:**
  1. Enabled the DNS server feature on the router using `ip dns server`.
  2. Created an A record with `ip host www.mypage.com 192.168.1.2`.
  3. Re-tested DNS queries from the PC.

---

## 5. **Error: Unable to Access Telnet**
- **Symptom:** Telnet to the router failed or prompted for incorrect credentials.
- **Cause:** VTY lines were not configured properly.
- **Fix:**
  1. Configured VTY lines with `password cisco`, `login`, and `transport input telnet`.
  2. Verified the router's Telnet accessibility from the PC.
  3. Ensured Telnet was enabled on the correct interfaces.

---

## 6. **Error: Invalid Command in Configuration Mode**
- **Symptom:** `% Invalid input detected at '^' marker` error appeared for certain commands.
- **Cause:** Commands were issued in the wrong mode (e.g., global config vs. interface config).
- **Fix:**
  1. Verified the appropriate mode for each command (e.g., used `configure terminal` for global commands).
  2. Exited to the correct mode before reissuing the command.

---

## 7. **Error: VLAN Unassigned and Down**
- **Symptom:** VLAN1 remained `administratively down`.
- **Cause:** VLAN1 was not assigned an IP address or brought `up`.
- **Fix:**
  1. Skipped configuring VLAN1 since it was not required for this lab.
  2. Focused on enabling and configuring FastEthernet interfaces.

---

## 8. **Error: Show Command Fails in Config Mode**
- **Symptom:** `% Invalid input detected` when using `show` commands in configuration mode.
- **Cause:** Show commands cannot be executed in configuration modes (e.g., `config` or `config-if`).
- **Fix:**
  1. Exited to privileged EXEC mode using `end` or `exit`.
  2. Re-executed the `show` commands in privileged EXEC mode.

---

These notes summarize the major issues encountered and how they were resolved, ensuring smoother troubleshooting for similar setups in the future.
