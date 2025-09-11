
## **EZDump - A Linux Memory Forensics Deep Dive**

<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/f2ab90e4-ca2c-4716-97e8-972af04207fa" />

#### **1. Introduction: The Challenge of Linux Memory Analysis**

This forensic challenge involved analyzing a memory dump from a Linux system, specifically from the SharkyCTF competition. The initial task required building a custom Volatility profile to properly analyze the memory image, as standard profiles would be incompatible without knowing the exact system specifications . This process highlights a common real-world scenario in digital forensics where investigators must first determine the environment from which evidence was acquired before any meaningful analysis can begin.

The core challenge revolved around the `bash_history` artifact, a common source of valuable investigative clues on Linux systems. Our objective was to extract this history from the memory dump to find the first flag .

#### **2. Phase I: System Identification - The Foundation of Analysis**

The first and most critical step in Linux memory forensics is identifying the exact operating system and kernel version. This information is paramount for building a compatible Volatility profile. Without it, attempting to analyze the dump would be futile.

We employed basic `grep` commands to search for tell-tale strings within the raw memory dump that would reveal these details:

*   **Kernel Version Identification:** The command `grep -a "Linux version" dump.mem` successfully revealed the kernel version: `3.10.0-1062.el7.x86_64`. This output also contained a crucial clue—a reference to `Red Hat`, pointing towards a Red Hat-based distribution like CentOS or Fedora .
*   **Distribution Identification:** To pinpoint the exact distribution, we searched for release information using `grep -a "Linux release" dump.mem`. This confirmed the system was running `CentOS Linux release 7.7.1908 (Core)` .

**Key Technical Detail:** The boot parameters, found via `grep -a "BOOT_IMAGE" dump.mem`, provided additional confirmation of the kernel path and version, further solidifying our target environment .

#### **3. Phase II: Building the Volatility Profile - Recreating the Environment**

With the target system identified as CentOS 7.7.1908 with kernel `3.10.0-1062.el7.x86_64`, the next step was to reconstruct a compatible analysis environment.

1.  **Virtual Machine Setup:** A CentOS 7.7.1908 disk image was sourced and installed in a virtual machine. Fortunately, the default kernel for this distribution version was the correct one, eliminating the need for a complex kernel downgrade process .
2.  **Installing Build Dependencies:** Before compiling the profile, essential development tools were installed on the clean VM using `yum`:
    *   `kernel-devel` & `kernel-headers`: For the kernel build environment.
    *   `gcc`: The GNU Compiler Collection.
    *   `git`: To clone the Volatility repository.
    *   `libdwarf-tools` & `elfutils-libelf-devel`: Libraries necessary for generating debugging information .
3.  **Profile Compilation:** The Volatility project was cloned, and the `module.dwarf` file was compiled. This file contains the crucial DWARF debugging information for the kernel. It was then zipped together with the `System.map` file from `/boot/` to create the final profile archive .

**Note on Version Tolerance:** It's worth noting that using slightly newer kernel sources (e.g., `3.10.0-1127`) often still works for creating a functional profile, as the core structures remain largely unchanged. This provides some flexibility if the exact sources are unavailable .

#### **4. Phase III: Analysis and Flag Extraction - Putting the Profile to Work**

The custom profile, named `LinuxCentOS-7_7_1908-3_10_0-1062x64`, was placed in the appropriate Volatility plugins directory. Its successful installation was verified by running `volatility --info | grep Linux` .

Guided by the challenge hint, the `linux_bash` plugin was executed to recover the command history from the memory dump:
```bash
volatility -f dump.mem --profile=LinuxCentOS-7_7_1908-3_10_0-1062x64 linux_bash
```
The output immediately revealed a highly suspicious command :
```bash
echo "c2hrQ1RGe2wzdHNfc3Q0cnRfdGgzXzFudjNzdF83NWNjNTU0NzZmM2RmZTE2MjlhYzYwfQo=" > y0ush0uldr34dth1s.txt
```
This command was a classic flag-hiding technique: a Base64-encoded string being written to a file. Decoding it is straightforward with the `base64` utility :
```bash
echo "c2hrQ1RGe2wzdHNfc3Q0cnRfdGgzXzFudjNzdF83NWNjNTU0NzZmM2RmZTE2MjlhYzYwfQo=" | base64 -d
```
This decoded to the complete flag: **`shkCTF{l3ts_st4rt_th3_1nv3st_75cc55476f3dfe1629ac60}`** .

#### **5. Conclusion and Lessons Learned**

This challenge served as an excellent practical introduction to the initial stages of Linux memory forensics. The process underscored that effective analysis often depends on meticulous preparation—correctly identifying the source system and building the right tools for the job.

The discovery method—searching for a Base64 string in the bash history—is a common trick in CTFs but also a simple yet effective real-world anti-forensics technique. Obscuring data in plain sight by encoding it relies on the investigator either missing the encoded blob or not recognizing its format. This reinforces the importance of thorough string extraction and familiarity with common encoding schemes during an investigation .

