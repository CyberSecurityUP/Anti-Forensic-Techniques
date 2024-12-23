# Anti-Forensic-Techniques

### Checklist: Anti-Forensic Techniques for Windows and Linux

#### **Windows Techniques**

**1. Metadata Manipulation**
   - **Timestamp Alteration**: Use `Timestomp` or custom tools to modify file creation, access, and modification times.
   - **Log Editing**: Manually or automatically edit event logs using `EvtxEdit` or similar tools.
   - **File Renaming**: Rename files to inconspicuous names or extensions.

**2. Data Hiding**
   - **Alternate Data Streams (ADS)**: Use `stream.exe` to hide data in NTFS streams.
   - **Slack Space Utilization**: Hide data in file slack space using tools like `SlackCleaner`.
   - **File Attribute Manipulation**: Change attributes (e.g., hidden, system) with `attrib` command.

**3. Obfuscation**
   - **Executable Packing**: Use tools like UPX to pack or obfuscate binaries.
   - **Encryption**: Encrypt sensitive files with tools like `BitLocker` or third-party tools.
   - **Registry Obfuscation**: Store payloads or configuration in obscure registry keys.

**4. Log and Artifact Clearing**
   - **Event Logs**: Use `wevtutil` to clear event logs:
     ```powershell
     wevtutil cl System
     ```
   - **Prefetch Cleaning**: Delete files in `C:\Windows\Prefetch`.
   - **Recycle Bin**: Empty recycle bin contents.

**5. Disk Manipulation**
   - **Wiping Tools**: Use `sdelete` or similar to securely delete files.
   - **Volume Shadow Copy Deletion**:
     ```powershell
     vssadmin delete shadows /all /quiet
     ```
   - **Hibernation File Removal**:
     ```powershell
     powercfg -h off
     ```

**6. Memory and Process Manipulation**
   - **Anti-Dumping**: Use tools like `Pafish` to detect and avoid memory dumps.
   - **Process Hollowing**: Replace the memory of a legitimate process with malicious code.

**7. Network Obfuscation**
   - **Proxy Usage**: Route traffic through proxies or VPNs.
   - **Firewall Rules**: Create rules to block forensic tools from connecting to critical resources.
   - **DNS Manipulation**: Redirect traffic to fake or benign domains.

---

#### **Linux Techniques**

**1. Metadata Manipulation**
   - **Timestamp Alteration**: Use `touch` to modify file timestamps:
     ```bash
     touch -t 202401010101 targetfile
     ```
   - **Inode Modification**: Use tools like `debugfs` to edit inode metadata.

**2. Data Hiding**
   - **Hidden Directories**: Use `.` prefix to create hidden directories.
   - **Steganography**: Hide data in images or other file formats using tools like `steghide`.
   - **Filesystem Obfuscation**: Use obscure filesystems like EncFS or eCryptfs.

**3. Obfuscation**
   - **Binary Packing**: Compress executables with `upx`.
   - **Custom Encoding**: Encode scripts or binaries with `base64` or `shc`.

**4. Log and Artifact Clearing**
   - **Log Deletion**:
     ```bash
     rm -rf /var/log/*
     ```
   - **Command History Clearing**:
     ```bash
     history -c && rm ~/.bash_history
     ```
   - **Temp File Cleanup**:
     ```bash
     rm -rf /tmp/*
     ```

**5. Disk Manipulation**
   - **Secure File Deletion**: Use `shred` or `dd` for secure deletion:
     ```bash
     shred -u targetfile
     ```
   - **Partition Wiping**:
     ```bash
     dd if=/dev/zero of=/dev/sdX bs=1M
     ```

**6. Memory and Process Manipulation**
   - **Process Cloaking**: Use `libprocesshider` to hide processes.
   - **Kill Forensic Tools**: Identify and terminate forensic processes with `pkill`.

**7. Network Obfuscation**
   - **MAC Address Spoofing**:
     ```bash
     ifconfig eth0 hw ether XX:XX:XX:XX:XX:XX
     ```
   - **VPN and Proxy Usage**: Route traffic through `OpenVPN` or `tor`.
   - **Log Tampering**: Alter `/var/log/auth.log` to obscure SSH or other access logs.

---
