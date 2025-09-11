# Defcon 2019 DFIR CTF Memory Forensics Challenge: A Comprehensive Technical Breakdown

## Introduction to the Challenge and Digital Forensics

The **Defcon 2019 Digital Forensics and Incident Response (DFIR) Capture The Flag (CTF)** [challenge](https://defcon2019.ctfd.io/challenges), created by the Champlain College Digital Forensics Association and shared by David Cowen, provided a hands-on opportunity to practice memory forensics skills. This challenge involved analyzing a Windows memory dump (`Triage-Memory.mem`) to uncover evidence of cyber intrusion and malicious activity. Memory forensics is a critical branch of digital forensics that involves analyzing volatile data from a system's RAM to uncover artifacts such as running processes, network connections, and hidden data. This write-up details the technical process and methodologies used to solve the memory forensics questions, showcasing essential tools and techniques.

## [Download the images](https://drive.google.com/drive/folders/1JwK8duNnrh12fo9J_02oQCz8HlILKAdW)

## [All images](https://www.dropbox.com/scl/fo/4wi8n7fm01yfcbwv4nom5/AIO_qWCQRyjl9-QtLa70wrE?rlkey=4uu6og3vph3rth8lp1ap86f9c&e=1&dl=0)

- - -

<img width="2104" height="2104" alt="image" src="https://github.com/user-attachments/assets/1c29df6a-da7a-4512-9225-cd1282594467" />

## 1. ✅ Establishing Evidence Integrity: SHA1 Hash
**Task:** Determine the SHA1 hash of the memory image to ensure its integrity throughout the analysis.  
**Tool/Command:** `sha1sum Triage-Memory.mem`  
**Finding:** `c95e8cc8c946f95a109ea8e47a6800de10a27abd`  
**Significance:** Hashing verifies that the memory dump remains unaltered since acquisition, which is crucial for maintaining evidence integrity in forensic investigations.

## 2. 🔍 Selecting the Right Volatility Profile
**Task:** Identify the appropriate Volatility profile for the memory dump.  
**Tool/Command:** `vol.py -f Triage-Memory.mem imageinfo`  
**Finding:** `Win7SP1x64` was the most suitable profile.  
**Significance:** Correct profile selection ensures accurate interpretation of memory structures and OS-specific data.

## 3. ✍️ Identifying Notepad Process ID
**Task:** Locate the Process ID (PID) of `notepad.exe`.  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 pstree | grep -i "notepad.exe"`  
**Finding:** PID `3032`  
**Significance:** Processes like Notepad often contain user-generated data, which can be critical in investigations.

## 4. 👨‍👦 Child Processes of wscript.exe
**Task:** Find the child processes of `wscript.exe`.  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 pstree | grep -A 2 -i "wscript.exe"`  
**Finding:** `UWkpjFjDzM.exe` (a suspicious child process) and its child `cmd.exe`.  
**Significance:** Malicious scripts often spawn additional processes to execute payloads.

## 5. 🌐 IP Address of the Compromised System
**Task:** Determine the system's IP address at the time of the memory dump.  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 netscan`  
**Finding:** `10.0.0.101`  
**Significance:**
- Understanding network configuration helps map attacker lateral movement.
- The same `netscan` output revealed a connection to `10.0.0.106:4444` (common Metasploit port), indicating potential reverse shell activity.

## 6. ⚠️ Attacker's IP Address
**Task:** Identify the attacker's IP address based on the infected process.  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 netscan | grep "UWkpjFjDzM.exe"`  
**Finding:** `10.0.0.106`  
**Significance:** Confirms command and control (C2) infrastructure.

## 7. 🔗 Process Associated with VCRUNTIME140.dll
**Task:** Locate the process linked to `VCRUNTIME140.dll`.  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 dlllist | grep -B 33 "VCRUNTIME140.dll"`  
**Finding:** `OfficeClickToR` (PID 1136)  
**Significance:** Legitimate processes can be hijacked for DLL injection or sideloading.

## 8. 🦠 MD5 Hash of the Malware
**Task:** Extract and hash the malicious executable.  
**Tool/Command:** 
```bash
vol.py -f Triage-Memory.mem --profile=Win7SP1x64 procdump -p 3496 -D .
md5sum executable.3496.exe
```
**Finding:** `690ea20bc3bdfb328e23005d9a80c290`  
**Significance:** Hashing allows for malware indexing and threat intelligence correlation.

## 9. 🔓 LM Hash of Bob's Account
**Task:** Dump the LM hash for the user "Bob".  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 hashdump`  
**Finding:** `aad3b435b51404eeaad3b435b51404ee` (null hash, indicating no password set)  
**Significance:** Weak credentials facilitate easy attacker access.

## 10. 🛡️ VAD Node Protections (1)
**Task:** Inspect protections of the VAD node at `0xfffffa800577ba10`.  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 vadinfo | grep -A 2 "0xfffffa800577ba10"`  
**Finding:** `PAGE_READONLY`  
**Significance:** VAD nodes track memory regions; protections hint at code injection or evasion techniques.

## 11. 🛡️ VAD Node Protections (2)
**Task:** Inspect protections of the VAD node from `0x00000000033c0000` to `0x00000000033dffff`.  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 vadinfo | grep -A 2 "Start 0x00000000033c0000 End 0x00000000033dffff"`  
**Finding:** `PAGE_NOACCESS`  
**Significance:** Suggattempts to hide malicious code.

## 12. 📜 VBS Script Name
**Task:** Find the name of the executed VBS script.  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 cmdline -p 5116`  
**Finding:** `vhjReUDEuumrX.vbs` (submit without extension: `vhjReUDEuumrX`)  
**Significance:** Scripts are often used to deploy malware.

## 13. ⏰ Application Execution Timestamp
**Task:** Identify an application run at `2019-03-07 23:06:58 UTC`.  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 shimcache | grep "2019-03-07 23:06:58"`  
**Finding:** `Skype.exe`  
**Significance:** The Application Compatibility Cache (Shimcache) logs execution artifacts.

## 14. 📝 Notepad Content Extraction
**Task:** Recover text from `notepad.exe`.  
**Tool/Command:** 
```bash
vol.py -f Triage-Memory.mem --profile=Win7SP1x64 memdump -p 3032 -D .
strings -e l 3032.dmp > 3032.dmp.strings
grep "flag" 3032.dmp.strings
```
**Finding:** `REDBULL_IS_LIFE`  
**Significance:** Volatile memory can contain user-generated content not saved to disk.

## 15. 📁 MFT File Record Short Name
**Task:** Locate the short name of the file at Master File Table (MFT) record `59045`.  
**Tool/Command:** `vol.py -f Triage-Memory.mem --profile=Win7SP1x64 mftparser | grep -A 20 "59045"`  
**Finding:** `EMPLOY~1.XLS`  
**Significance:** MFT analysis reveals file system metadata.

## 16. ☠️ Meterpreter PID Identification
**Task:** Determine the PID of the Meterpreter process.  
**Tool/Command:** Based on prior process analysis (e.g., `netscan`, `pstree`).  
**Finding:** `3496` (PID of `UWkpjFjDzM.exe`)  
**Significance:** Meterpreter is a common Metasploit payload for post-exploitation.
