# SSH Lab

## Objective
Configure secure remote access to a Cisco router using SSH. This lab demonstrates how to secure management access to a router, replacing insecure Telnet connections with SSH.

---

## Tutorial Information
This lab is part of the 101 Labs series and is designed to teach secure remote management using SSH. The steps in this lab align with practical networking scenarios you might encounter in real-world environments, particularly when replacing legacy Telnet connections with secure SSH access.

### Why SSH?
- SSH (Secure Shell) encrypts communication, ensuring that sensitive data (e.g., passwords) is not transmitted in plaintext.
- Replacing Telnet with SSH is a critical step in hardening network security, especially in corporate environments.

---

## Steps
1. **Set the hostname and domain name**:
   - Hostname: `R1`
   - Domain name: `101labs.net`
   - The hostname is used in the RSA key generation process, and the domain name is required for generating cryptographic keys.
2. **Assign IP addresses**:
   - Configure the `FastEthernet0/0` interface on Router1 with the following IP address:
     - `192.168.1.2/24`
   - Ensure the interface is active with the `no shutdown` command.
3. **Generate RSA keys for SSH**:
   - Use 1024-bit RSA keys for encryption.
4. **Restrict VTY lines to SSH only**:
   - Allow only SSH connections on VTY lines and block Telnet.
5. **Test SSH access and deny Telnet access**:
   - SSH into Router1 from another device using:
     - Username: `admin`
     - Password: `cisco`
   - Verify that Telnet connections are denied.

---

## Files
- `SSH_Lab.pkt`: Packet Tracer file for this lab.

---

## Commands Used
```plaintext
# Step 1: Set the hostname and domain name
hostname R1
ip domain-name 101labs.net

# Step 2: Configure the IP address and activate the interface
interface FastEthernet0/0
ip address 192.168.1.2 255.255.255.0
no shutdown

# Step 3: Generate RSA keys
crypto key generate rsa
# Specify key length: 1024 bits

# Step 4: Configure the VTY lines for SSH
line vty 0 15
transport input ssh
password cisco
login

# Step 5: Set SSH timeout and retry limits (optional, but recommended)
ip ssh time-out 60
ip ssh authentication-retries 2

# Step 6: Test connectivity
# From another device:
ping 192.168.1.2
ssh -l admin 192.168.1.2
