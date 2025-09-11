
### **Technical Interview Questions for a Digital Forensics Analyst Position**

Here are 27 technical questions to assess a candidate's practical knowledge of digital forensics tools and methodologies.

<p align="center">
  <img src="https://github.com/user-attachments/assets/1519c242-c702-421b-a43b-06d5df024d59" />
</p>

#### 1. **The Foundation: Evidence Acquisition**
**Question:** A client provides a powered-on Windows 10 laptop suspected of illicit activity. Describe the steps you would take to create a forensically sound disk image, including the tools and commands you would use. How would you verify the integrity of the acquired image?

**Expected Answer:**
*   **Steps:** First, I would use a hardware write-blocker to connect the laptop's drive to my forensic workstation. If a hardware blocker is unavailable, I would use a software write-blocker like `libguestfs` tools on Linux. To acquire the image, I would use `FTK Imager` (GUI) or `dcfldd`/`dd` on Linux with specific parameters.
*   **Command (Linux):** `dcfldd if=/dev/sda of=./evidence.img hash=md5,sha256 hashwindow=256M hashlog=./evidence.hash`
*   **Verification:** I would verify integrity by comparing the acquired hash (MD5/SHA256) generated during acquisition with a hash generated afterward: `sha256sum evidence.img` and compare it to the value in `evidence.hash`. Any mismatch indicates corruption.

#### 2. **SleuthKit Core: File System Analysis**
**Question:**
You have a disk image from a Linux EXT4 system. Using SleuthKit (TSK) command-line tools, how would you:
a) List all deleted files that still have data blocks allocated?
b) Recover the contents of a specific deleted file named `notes.txt` (inode 38576) to your local analysis machine?

**Expected Answer:**
*   **a) List deleted but not unlinked files:** `ils -e /path/to/evidence.img` | Analyze the output for entries with `a` (allocated) flags but no corresponding file name in the file system namespace.
*   **b) Recover a specific file:** Use `icat` to output the file's content by its inode and redirect it: `icat /path/to/evidence.img 38576 > /local/path/recovered_notes.txt`

#### 3. **Autopsy: Timeline Analysis**
**Question:** In Autopsy, the timeline analysis feature is powerful. What are the different types of timelines it can generate (e.g., from what data sources), and in a fraud investigation, why might you filter the timeline to show only "File Accessed" times instead of "File Modified" times?

**Expected Answer:**
*   **Timeline Sources:** Autopsy builds a timeline from file system metadata (`mactime`), browser history, registry entries (via Plaso), event logs, and other parsed artifacts.
*   **Accessed vs. Modified:** "File Modified" time changes when the file's content is altered. "File Accessed" time changes when the file is simply opened or read. In a fraud investigation, if a document was only viewed but not altered right before a fraudulent transaction, the "Accessed" timestamp could be a crucial piece of evidence showing the suspect had knowledge of the file's contents, even if they didn't change it.

#### 4. **Windows Artifacts: Registry Deep Dive**
**Question:** A user claims they never plugged a specific USB drive into their system. What specific Windows Registry keys would you examine to prove otherwise? What tools would you use, and what information (like unique identifiers) would you look for?

**Expected Answer:**
*   **Registry Keys:** The primary keys are `SYSTEM\ControlSet00x\Enum\USBSTOR` and `SYSTEM\MountedDevices`.
*   **Tools:** Autopsy's registry analyzer, `regripper`, or even `strings`/`grep` on the `SYSTEM` hive.
*   **Information:** In `USBSTOR`, I would look for the device's Vendor ID (VID), Product ID (PID), and most importantly, the unique **Serial Number**. The `MountedDevices` key can show which drive letter was assigned (e.g., `\DosDevices\E:`). Finding the unique serial number of the disputed drive in these keys is definitive proof it was connected.

#### 5. **Memory Forensics: Volatility**
**Question:** You have a memory dump (`memdump.mem`) from a potentially compromised Windows 10 system. What Volatility 2/3 command would you use to identify suspicious or hidden processes? Following that, how would you dump one of those processes for further analysis?

**Expected Answer:**
*   **Identify Processes:** `vol.py -f memdump.mem windows.pslist` (lists active processes) and `vol.py -f memdump.mem windows.psscan` (scans for hidden or terminated processes). Comparing the two outputs can reveal discrepancies.
*   **Dump a Process:** Once you have the PID (e.g., 1234), use: `vol.py -f memdump.mem -o /path/to/output/dir windows.memmap --pid 1234 --dump` This will dump the process's memory space for static analysis or string extraction.

#### 6. **Network Forensics: PCAP Analysis**
**Question:** In an investigation, you have a packet capture (PCAP) file. Describe how you would use Wireshark or `tshark` to filter and find all DNS queries made to a known malicious domain, `evil.c2.domain`.

**Expected Answer:**
*   **Wireshark GUI Filter:** `dns.qry.name contains "evil.c2.domain"`
*   **Tshark Command-Line:** `tshark -r capture.pcap -Y 'dns.qry.name contains "evil.c2.domain"' -T fields -e ip.src -e dns.qry.name` This command would also extract the source IP making the query, which is critical for identifying the infected host.

#### 7. **Anti-Forensics: Data Carving**
**Question:** A suspect has used the `shred` command on a file in a Linux environment. Is it possible to recover the content? Why or why not? How would your answer differ if the file was on an SSD versus an HDD?

**Expected Answer:**
*   **`shred` on HDD:** On a traditional HDD, `shred` overwrites the data blocks multiple times. This makes recovery via software carving tools (like `foremost` or `scalpel`) effectively impossible.
*   **`shred` on SSD:** On an SSD, it's even less reliable due to **wear leveling** and the **TRIM command**. The SSD controller may have already marked the blocks as invalid and moved the data elsewhere, making the `shred` operation operate on blocks that no longer contain the original data. A full forensic image might contain remnants of the file in previously allocated blocks that haven't been physically erased yet. The key difference is the storage technology's behavior.

#### 8. **Browser Artifacts: SQLite Analysis**
**Question:** Where does Chrome typically store its browsing history on a Windows 10 system, and what is the format? Name a command-line tool you could use to query this database to find all visits to a specific URL.

**Expected Answer:**
*   **Location/Format:** `C:\Users\%USERNAME%\AppData\Local\Google\Chrome\User Data\Default\History`. The format is **SQLite**.
*   **Tool & Query:** I would use `sqlite3.exe` (command-line utility). A basic query could be:
    ```sql
    sqlite3 History "SELECT datetime(visit_time/1000000 + (strftime('%s', '1601-01-01')), 'unixepoch') as timestamp, url FROM urls JOIN visits ON urls.id = visits.url WHERE url LIKE '%suspicious-domain.com%';"
    ```
    This complex query handles Chrome's epoch time conversion and joins the necessary tables.

#### 9. **Log Analysis: Linux SSH Intrusion**
**Question:** You are investigating a potential SSH brute-force attack on an Ubuntu server. What is the full path to the relevant log file, and what `grep` command would you use to list all unique IP addresses that attempted to authenticate (successfully or not)?

**Expected Answer:**
*   **Log File:** `/var/log/auth.log`
*   **Grep Command:** `grep "Failed password" /var/log/auth.log | grep -Po "[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+" | sort | uniq -c | sort -nr` This pipeline finds failures, extracts IPs, sorts them, counts unique occurrences, and sorts by count to show the most aggressive attackers first.

#### 10. **Mac Forensics: Spotlight Metadata**
**Question:** On macOS, what are `extended attributes` and how can they be forensically significant? Give an example of a command to list them for a file.

**Expected Answer:**
*   **Significance:** Extended attributes (xattr) store metadata beyond standard permissions, including download source (`com.apple.metadata:kMDItemWhereFroms`), quarantine information, and more. This is crucial for determining a file's origin.
*   **Command:** `ls -l@ filename` will show the extended attributes. To view the content of a specific attribute (which is often binary plist data), you would use `xattr -l filename`.

#### 11. **Mobile Forensics: SQLite WAL**
**Question:** In mobile forensics (iOS/Android), application data is often stored in SQLite databases. What is the Write-Ahead Log (WAL) and how can it provide valuable forensic evidence that might not be present in the main database file?

**Expected Answer:**
*   **What is WAL:** The Write-Ahead Log is a logging method where changes are written to a separate `-wal` file before being committed to the main database. This improves performance.
*   **Forensic Value:** Deleted records or older versions of data may still reside in the WAL file even after they have been removed from the main database. A forensic examiner must always acquire and analyze the `-wal` and `-shm` files alongside the main `.db` file to get a complete picture of all database transactions.

#### 12. **Reporting & Documentation**
**Question:** Imagine you found a crucial piece of evidence—a deleted file containing stolen data. How would you document this finding in your report to ensure it is admissible and understandable for both technical and non-technical audiences (e.g., law enforcement, lawyers)?

**Expected Answer:**
*   **For Technical Readers:** Provide the absolute path to the file, its inode, the tool/command used to recover it (e.g., `icat image.img 12345 > recovered_file.pdf`), and its file hash.
*   **For Non-Technical Readers:** Explain the finding in plain language: "A deleted PDF file named 'project_plans.pdf' was recovered from the suspect's laptop. The recovery process is a standard digital forensic technique that restores data that has been marked for deletion but not yet overwritten." **Most importantly,** the report must clearly document the **chain of custody** and the **hashing** process to prove the evidence was not altered from acquisition to analysis.





#### 13. **Loki: IoC Scanner Customization & Limitations**
**Question:** You are using **Loki** to scan a Windows server for indicators of compromise (IOCs). The scan returns a potential hit on a YARA rule, but you suspect it might be a false positive. Describe the process to temporarily disable this specific YARA rule for a subsequent scan without removing it from the signature base. Furthermore, given that Loki is now in "inactive maintenance mode," what is its recommended successor and what is one key improvement it offers? 

**Expected Answer:**
*   **Disabling a Rule:** Loki doesn't have a built-in switch to disable individual rules via command line for a single run. The practical approach is to temporarily move or rename the specific `.yar` file (e.g., `suspicious_rule.yar`) within the `./signature-base/yara/` directory before running the scan, and then move it back afterward.
*   **Loki's Successor:** The recommended successor is **THOR Lite** (or the commercial THOR). 
*   **Key Improvement:** THOR is significantly faster, more stable, undergoes rigorous CI testing, and likely includes a more extensive and updated signature set compared to the now-archived Loki. 

#### 14. **UAC: Trusted Binary Collection in a Compromised Environment**
**Question:** The **Unix-like Artifacts Collector (UAC)** relies on system binaries to collect data. You are investigating a potentially compromised Linux system where critical binaries (`ps`, `ls`, `netstat`) might be trojanized. How can you configure UAC to use a set of known-trusted binaries instead? What is a major technical challenge in creating these trusted binaries, especially for a wide range of Unix-like systems? 

**Expected Answer:**
*   **Configuration:** Trusted binaries can be placed in the `/bin` directory within the UAC archive, under a subdirectory for the target OS (e.g., `uac/bin/linux/`). UAC will prioritize these binaries over the system's own binaries.
*   **Technical Challenge:** The major challenge is **statically compiling** these binaries so they do not depend on any shared libraries (`libc`, etc.) on the potentially compromised target system. Dynamically linked binaries brought from a clean system will likely fail if the target system has malicious or incompatible libraries. Statically compiling every necessary tool for every supported OS (AIX, Solaris, Linux, macOS) is a complex and tedious task. 

#### 15. **APT-Hunter: TTP Detection in Windows Event Logs**
**Question:** **APT-Hunter** identifies malicious activity in Windows event logs using pre-defined rules. A rule triggers an alert for "Suspicious PowerShell commands Detected." What are *two* specific pieces of information from the original Windows event log (e.g., Security, PowerShell Operational) that APT-Hunter would have parsed to generate this alert, and which field in its output would allow an investigator to quickly find the original raw log entry for deeper context? 

**Expected Answer:**
*   **Parsed Information:** 1) The actual PowerShell command line (`ScriptBlockText` or `Message` fields). 2) The user context (`SubjectUserName`) or process ID generating the activity.
*   **Original Log Field:** The `Original Log` column in APT-Hunter's output contains the raw event data, allowing the investigator to review the complete, unaltered log entry for maximum context. 

#### 16. **USBRip: Proving a Specific USB Device Connection**
**Question:** Using **USBRip** on a Linux system, you need to prove that a specific USB storage device (Vendor ID `abcd`, Product ID `1234`, Serial Number `SERIAL123`) was connected between two specific dates. What is the exact command to run? Furthermore, how would you use USBRip to quickly check if *any* devices not on your authorized list (`auth.json`) had ever been connected? 

**Expected Answer:**
*   **Specific Device Command:** `sudo usbrip events history --vid abcd --pid 1234 --serial SERIAL123 -d "YYYY-MM-DD" "YYYY-MM-DD"`
*   **Violations Check Command:** `sudo usbrip events violations /path/to/auth.json` This command compares the entire connection history against the authorized list in `auth.json` and outputs any discrepancies. 

#### 17. **Docker Forensics: Container Memory Acquisition**
**Question:** During a live response on a Linux server, you identify a suspicious Docker container (`ID: badc0de`). You need to acquire its memory for analysis with Volatility. Describe the process, including the exact command to dump the memory of *all* processes belonging to this container. Why is using `docker commit` alone insufficient for a full forensic capture? 

**Expected Answer:**
*   **Process:** 1) Find the PIDs of all processes inside the container: `docker top badc0de` or `pgrep -a container_id`. 2) Use a tool like `gcore` on each PID: `for pid in $(pgrep -f container_id=badc0de); do sudo gcore -o container_mem_$pid $pid; done`. Alternatively, use `psexec` within the container if necessary.
*   **Why `docker commit` is insufficient:** `docker commit` only captures the container's **file system state** (the copy-on-write layer). It does **not** capture the volatile memory, running process state, network connections, or other runtime artifacts, which are often critical for detecting in-memory malware or understanding active attacks. 

#### 18. **Wireshark/TShark: Extracting Downloaded Files**
**Question:** You have a large PCAP file from a network breach. You need to use **TShark** (Wireshark's command-line tool) to extract all files that were transferred over HTTP. What is the command to do this, and how does it function? What is a significant limitation of this method against modern web traffic?

**Expected Answer:**
*   **Command:** `tshark -r breach.pcap --export-objects http,./output_dir/` This command scans the PCAP for HTTP traffic, reassembles TCP streams, and writes any transferred files (images, documents, etc.) to the `./output_dir` directory.
*   **Limitation:** This method is largely ineffective against **HTTPS** (TLS/SSL) encrypted traffic, which constitutes the vast majority of modern web traffic. The content of the transfers is encrypted and cannot be extracted without the session keys.

#### 18. **ExifTool: Timeline from Decoy Documents**
**Question:** A phishing email contained a malicious PDF document. Using **ExifTool**, what command would you use to extract all embedded metadata, which could include creation software, author, and potentially embedded script information? Based on this metadata, how could you quickly build a timeline of the document's creation and modification history?

**Expected Answer:**
*   **Command:** `exiftool -a -u -g1 phishing_document.pdf` The `-a` shows all tags, `-u` shows unknown tags, and `-g1` groups them for readability.
*   **Timeline Building:** Key metadata fields for a timeline include:
    *   `CreateDate` / `CreationDate`: When the document was initially created.
    *   `ModifyDate`: When it was last modified.
    *   `MetadataDate`: When the metadata was last updated.
    *   Software fields (`Producer`, `Creator`, `CreatorTool`): Can indicate what tools were used and in what order. Correlating these timestamps can reveal the document's history.

#### 20. **Xplico: Reconstructing Webmail Sessions**
**Question:** **Xplico** is used to reconstruct network traffic. From a PCAP file, you need to reconstruct a user's webmail session (e.g., Gmail) to see what emails were viewed or sent. In which Xplico output module would you primarily look for this information, and what kind of artifacts (specific file types) would you expect to find?

**Expected Answer:**
*   **Xplico Module:** The **HTTP** module is the primary place to look for webmail traffic.
*   **Expected Artifacts:** You would look for reconstructed files such as:
    *   `HTML` pages: The rendered content of the webmail inbox and emails.
    *   `CSS` and `JS` files: Supporting files for the page layout.
    *   Potentially downloaded email attachments.
    *   While not the primary source, the **Mail (POP/IMAP/SMTP)** module should also be checked for any non-web-based email traffic, but webmail typically runs over HTTP/S.

#### 21. **EnCase: Parsing Compound Windows Artifacts**
**Question:** In **EnCase**, you need to analyze a user's recent activity comprehensively. You decide to examine the Shellbags artifact. What does the Shellbags artifact record, and how does it provide value that is not immediately available from just looking at the `RecentDocs` or `LNK` files?

**Expected Answer:**
*   **What it Records:** Shellbags store Windows Explorer folder viewing preferences (window size, position, view mode - e.g., details vs. icons).
*   **Added Value:** Crucially, Shellbags can reveal the existence of **deleted folders** or **network drives** that a user navigated to, long after the folders themselves have been removed from the file system or disconnected. This provides a historical record of directory structures and user navigation that persists beyond the life of the files themselves, unlike `RecentDocs` which typically points to existing files.

#### 22. **Bulk Extractor: Scraping Unallocated Space for Intel**
**Question:** You are processing a disk image using **Bulk Extractor**. Your goal is to find as many email addresses and credit card numbers as possible, even if they are in unallocated space or slack space. What command would you use? Why is Bulk Extractor particularly well-suited for this task compared to a traditional file carver?

**Expected Answer:**
*   **Command:** `bulk_extractor -o output_dir -e email -e ccn disk_image.img` This command runs the email and credit card number scanners and writes results to `output_dir`.
*   **Why it's better:** Bulk Extractor is specifically designed to ignore file system structures. It scans the disk image **byte-by-byte** (like a `dd` image), allowing it to find patterns (like email addresses and CC numbers) that exist in unallocated space, slack space, swap files, and hibernation files, which would be completely missed by tools that only operate on allocated files.

#### 23. **Loki vs. APT-Hunter: Complementary Use**
**Question:** Describe a scenario where you would use both **Loki** (on a disk image) and **APT-Hunter** (on event logs) in tandem during an investigation. What does each tool provide that the other does not, making them complementary?

**Expected Answer:**
*   **Scenario:** Investigating a potential ransomware infection on a Windows server.
*   **Loki's Role:** Scan the disk image (`-p path/to/image`) with YARA rules to identify the static ransomware binary, known malicious hashes of encrypted files, or specific ransom note filenames (IoC-based detection on storage). 
*   **APT-Hunter's Role:** Analyze the Windows event logs to identify the **execution chain**: what user account triggered the malware (Logon Event), what process spawned the ransomware binary (Process Creation Event), and if it attempted lateral movement (Network Share Access Event). This provides the *context* and *timeline* of the attack. 
*   **Complementary:** Loki finds the *what* (malicious files), APT-Hunter explains the *how, when, and who* (execution, timing, user context).

#### 24. **UAC & USBRip: Cross-Platform Triage**
**Question:** You are responding to an incident on a network with mixed Windows and Linux servers. You need to quickly triage all systems. How would you use **UAC** on the Linux servers and, assuming you have Linux event forwarding or a SIEM, how could you conceptually apply the **USB device tracking** capability of **USBRip** to your Windows systems? What Windows log would you need to analyze? 

**Expected Answer:**
*   **Linux Triage:** Use UAC with the `ir_triage` profile on all Linux servers: `./uac -p ir_triage /output_dir`. This collects volatile data and key artifacts without the overhead of full application data. 
*   **Windows USB Tracking:** USBRip is for Linux. To do this on Windows, you would need to analyze the **Windows Security Event Log** (Event ID 6416 for installing a new device) or, more effectively, the **Microsoft-Windows-DriverFrameworks-UserMode/Operational** log (Event IDs 2000-2015 for device setup). The concept (tracking device connections) is the same, but the tool and data source are different.

#### 25. **EnCase & Xplico: Correlation Analysis**
**Question:** From a disk image analyzed in **EnCase**, you find a suspicious file `malware.zip` downloaded at a specific time. You also have a full packet capture (PCAP) from the network border covering that time. How would you use **Xplico** to corroborate the findings from EnCase and potentially identify the external C2 server IP address?

**Expected Answer:**
*   **Process:** 1) In EnCase, note the precise download time of `malware.zip`. 2) In Xplico, load the PCAP and navigate to the HTTP module. 3) Use Xplico's filtering capabilities to look for HTTP GET or POST requests around that specific time. 4) Look for a request that resulted in a file with a similar size and type (`application/zip`) being transferred. The source IP would be the internal host, and the destination IP would be the likely C2 server from which the malware was downloaded.

#### 26. **Bulk Extractor & ExifTool: Privacy Incident**
**Question:** During an investigation into a data privacy incident, you need to find all JPEG images on a corporate laptop and determine if any were taken outside of company property (e.g., at an employee's home). Describe how you would combine **Bulk Extractor** and **ExifTool** to automate this analysis at scale.

**Expected Answer:**
*   **Step 1 (Find Images):** Use `bulk_extractor -o output -e jpeg disk_image.img`. This will scrape all JPEG files (allocated and unallocated) and save them to the `output/jpeg` directory.
*   **Step 2 (Extract GPS):** Write a script that iterates through all recovered JPEGs and runs `exiftool -GPSLatitude -GPSLongitude -n -q -q filename.jpg`. The `-n` flag gives coordinates in decimal format, and `-q -q` suppresses other output.
*   **Step 3 (Analyze):** The script would output filenames and coordinates only for images that contain GPS metadata. These coordinates could then be plotted on a map or checked against a list of company geofences to identify images taken off-site.

#### 27. **Docker & Wireshark: Microservices Investigation**
**Question:** A malicious container is discovered in a Kubernetes cluster. Using concepts from **Docker Forensics** and **Wireshark**, what two key sources of evidence would you prioritize from the *host node* to understand the container's network activity and lateral movement attempts? Name the specific files or interfaces you would analyze. 

**Expected Answer:**
*   **1. Container Network Interface:** Analyze the PCAP from the specific virtual network interface (e.g., `vethxxxxxx`) attached to the malicious container. This requires tracing the container's network namespace and capturing traffic directly. Wireshark would be used to analyze this PCAP.
*   **2. Host-level Netfilter/IPTables Logging:** If available, examine firewall logs. Kubernetes and Docker manipulate IPTables rules for networking and security policies. Configuring IPTables to log dropped packets or specific flows can provide evidence of the container attempting to communicate with unauthorized internal or external IPs. These logs could be found in the host's `dmesg` or `kern.log` and analyzed with Wireshark or other log analysis tools. 

***

These questions cover a wide range of fundamental and intermediate topics, testing practical skills with tools, understanding of underlying concepts, and the ability to communicate findings effectively. 

Good luck with the interview process! 
