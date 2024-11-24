# Errors and Fixes: DNS Lab

This file captures the errors encountered during the DNS Lab and the solutions applied to resolve them. These notes are intended to help troubleshoot similar issues in future labs.

---

## 1. **Error: Hostname Unresolved**
- **Symptom:** PC displayed "Host Name Unresolved" when attempting to access `www.mypage.com`.
- **Cause:** DNS server was not configured with the required A record.
- **Fix:**
  1. Opened the DNS service on the router and ensured it was enabled.
  2. Added an A record for `www.mypage.com` pointing to `192.168.1.2`.
  3. Retested by accessing the hostname via the PC browser.

---

## 2. **Error: Devices Unable to Ping**
- **Symptom:** Devices could not ping each other across the network.
- **Cause:** Misconfigured IP addresses or subnet mismatches.
- **Fix:**
  1. Double-checked the static IP configurations on all devices.
  2. Ensured all devices were in the correct subnet.
  3. Corrected any issues and verified connectivity using `ping`.

---

## 3. **Error: Incorrect Gateway on PC**
- **Symptom:** The PC could not resolve DNS queries or communicate with other devices.
- **Cause:** Gateway address on the PC was misconfigured.
- **Fix:**
  1. Updated the default gateway on the PC to point to the router's interface (`192.168.1.1`).
  2. Retested network communication.

---

## 4. **Error: DNS Not Enabled**
- **Symptom:** The DNS service was not functioning, leading to failed name resolution.
- **Cause:** The DNS server was not enabled on the router.
- **Fix:**
  1. Enabled the DNS service on the router using the `ip dns server` command.
  2. Added the appropriate DNS records and saved the configuration.

---

These notes summarize the main issues encountered during the DNS Lab and the solutions applied. Proper documentation ensures easier troubleshooting in future labs.
