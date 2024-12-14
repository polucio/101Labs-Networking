# FTP Lab - Remote File Access

## **Objective**
Learn how to save router configurations using FTP and troubleshoot common errors encountered during the process.

---

## **Lab Overview**
- **Purpose:** Backup router configurations to avoid data loss using FTP.
- **Lab Tool:** Cisco Packet Tracer
- **Topology:** A router connected to an FTP server via a crossover cable.

---

## **Steps Performed**

### **1. Connect Router to FTP Server**
- Used a crossover cable to connect the router’s `f0/0` interface to the server's Ethernet interface.

### **2. Configure Router Ethernet Interface**
Commands used:
```plaintext
Router>en
Router#configure terminal
Router(config)#interface f0/0
Router(config-if)#ip address 192.168.1.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit
```

### **3. Configure FTP Server**
- Assigned the server IP `192.168.1.2` and set the default gateway to `192.168.1.1`.
- Added FTP user credentials:
  - Username: `101labs`
  - Password: `hello`
  - Permissions: Full (read, write, etc.).

### **4. Test Connectivity**
Pinged the server from the router:
```plaintext
Router#ping 192.168.1.2

!!!!!
Success rate is 100 percent (5/5)
```

### **5. Save Running Configuration**
Saved the router’s configuration:
```plaintext
Router#copy running-config startup-config
Destination filename [startup-config]? 
Building configuration...
[OK]
```

### **6. Configure FTP Credentials on Router**
Configured the FTP username and password on the router:
```plaintext
Router#configure terminal
Router(config)#ip ftp username 101labs
Router(config)#ip ftp password hello
Router(config)#exit
```

### **7. Copy Configuration to FTP Server**
Copied the `startup-config` to the FTP server:
```plaintext
Router#copy startup-config ftp:
Address or name of remote host []? 192.168.1.2
Destination filename [Router-confg]? 14dec24

Writing startup-config...
[OK - 566 bytes]
566 bytes copied in 0.077 secs (7000 bytes/sec)
```

### **8. Verify File on FTP Server**

#### **Initial Command Attempt**
```plaintext
Router#dir ftp://192.168.1.2
%Error opening flash:/ftp://192.168.1.2 (File Not Found)
```

#### **Resolution**
- Opened the FTP server in Packet Tracer:
  - Navigated to **Services > FTP**.
  - Verified the `14dec24` file was successfully uploaded.

---

## **Errors and Troubleshooting**

### **Error 1: `%Error copying nvram:Router#copy running-config startup-config (Invalid argument)`**
#### **Cause:**
- Possible NVRAM corruption or syntax issues.

#### **Solution:**
- Cleared NVRAM:
  ```plaintext
  Router#write erase
  Router#reload
  ```
- Re-entered configurations and retried saving.

### **Error 2: `%Error opening flash:/ftp://192.168.1.2 (File Not Found)`**
#### **Cause:**
- Misinterpretation of `dir` command by the router.

#### **Solution:**
- Verified the file directly on the FTP server via the Packet Tracer interface.

---

## **Lessons Learned**
1. Always test connectivity between devices before performing operations like file transfers.
2. Use clear and meaningful filenames (e.g., `14dec24`) for backups.
3. Check FTP server configurations for proper permissions and active service.
4. Be prepared to troubleshoot simulation-specific quirks, especially in environments like Packet Tracer.

---

## **Commands Summary**
### **Router Commands**
```plaintext
# Configure router Ethernet interface
configure terminal
interface f0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

# Save running configuration
copy running-config startup-config

# Configure FTP credentials
ip ftp username 101labs
ip ftp password hello

# Copy configuration to FTP server
copy startup-config ftp:
```

---

## **Future Improvements**
- Explore SFTP for secure file transfers.
- Automate backups using scripts or scheduled tasks.
- Investigate real-world router logs to gain deeper troubleshooting experience.

---

### **Acknowledgments**
Lab based on "101 Labs - CompTIA Network+" by Paul Browning.

---

### **References**
Browning, Paul. *101 Labs - CompTIA Network+: Hands-on Practical Labs for the N10-008 Exam.*
