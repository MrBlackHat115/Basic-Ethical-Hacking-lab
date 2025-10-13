# Basic-Ethical-Hacking-lab
A hands-on, beginner-friendly lab that teaches the fundamentals of ethical hacking and penetration testing. Through guided exercises and vulnerable targets, learners practice reconnaissance, scanning, exploitation basics, privilege escalation, and reporting, all within a safe, legal environment.

# Table of Contents
* **Installation Requirements**
    * **VirtualBox** 
    * **Kali Linux**
    * **Metasploitable 2**
        * **DVWA**    
    * **Windows 10**
* **Lab Structure**
* **Fundamental Knowledge**
* **Tools**
* **Other Resources**

# Installation Requirements
### **VirtualBox**
<img width="632" height="251" alt="Screenshot 2025-10-12 130317" src="https://github.com/user-attachments/assets/bb6e4789-e00c-477c-aa14-1951266cb0b9" />
<img width="1902" height="837" alt="Screenshot 2025-10-12 130345" src="https://github.com/user-attachments/assets/248636d7-a7c2-4802-a233-05fb8d1ed754" />
Download the latest VirtualBox from https://www.virtualbox.org/

YouTube Tutorial: https://www.virtualbox.org/wiki/Downloads

Here is a video of how you add virtual machines to VirtualBox: https://www.youtube.com/watch?v=CMGa6DsGIpc&t=25s&pp=ygUXdmlydHVhbGJveCBhZGQgbWFjaGluZXM%3D

### **Kali Linux** 
<img width="1078" height="798" alt="Screenshot 2025-10-12 131905" src="https://github.com/user-attachments/assets/257019b5-8a1d-482e-9d1b-923fbcee3636" />
<img width="658" height="460" alt="Screenshot 2025-10-12 131838" src="https://github.com/user-attachments/assets/d9559d2b-5ed7-4b32-bbb5-18d0fe95156f" />

Download Kali Linux from https://www.kali.org/get-kali/#kali-installer-images. I recommend downloading the installer version.

Here is a tutorial on downloading Kali and installing it on VirtualBox: https://www.youtube.com/watch?v=wX75Z-4MEoM&t=1090s

### **Metasploitable 2**
<img width="1455" height="794" alt="Screenshot 2025-10-12 132812" src="https://github.com/user-attachments/assets/0300bcdb-a43f-45a0-b663-370d42735afe" />

Download Metasploitable 2 from https://sourceforge.net/projects/metasploitable/files/Metasploitable2/

### **DVWA**   
<img width="594" height="519" alt="Screenshot 2025-10-12 135905" src="https://github.com/user-attachments/assets/92619022-4fbc-4362-84d2-fc775e7804ff" />
<img width="622" height="572" alt="Screenshot 2025-10-12 135853" src="https://github.com/user-attachments/assets/3c9af927-8663-499d-b4c0-c88a3733a448" />

You can access DVWA by running your metasploitable 2 and entering its IP address in the URL bar.

### **Windows 10**
<img width="754" height="671" alt="Screenshot 2025-10-12 144651" src="https://github.com/user-attachments/assets/56bbda5b-b73e-4cbc-8b11-b32199766dd5" />
<img width="748" height="303" alt="Screenshot 2025-10-12 144644" src="https://github.com/user-attachments/assets/23eaaf43-cccc-4f50-825c-747e6da441db" />

Below are clear, ordered steps to download a Windows 10 ISO (version 1903 / 1909) and install it on your virtual machine.

1. Download Rufus (portable) from https://rufus.ie/en/.

2. Run Rufus (right-click → Run as administrator). If prompted by UAC, allow it.

Click the small arrow beside Select → choose Download.

**Important note:** If the arrow doesn't appear: close & re-open Rufus, or go into Settings → toggle check-for-updates, restart Rufus.

4. Rufus will open a small download dialog. Choose:

   * Windows 10

   * Release: select 19H1 build 18362.356 (this corresponds to Windows 10 v1903) — or pick the 1909 build if you prefer.

   * Edition: Windows 10 Home (or whichever you want)

   * Language: English (or your preference)

   * Architecture: x64

5. Click Download and save the .iso to a folder (ISO ≈ 4–6 GB). Wait for the download to finish.

6. After the ISO is finished, you can now upload it to your VirtualBox.

   * Name: Windows-10-1903 (or similar).

   * Type: Microsoft Windows

   * Version: Windows 10 (64-bit)

   * Memory: allocate 2048 MB (2 GB) minimum; 4096 MB+ recommended if the host has RAM.

   * Hard disk: Create a virtual hard disk now → VDI → Dynamically allocated → size 25 GB (or larger).

   * Click Create.

# Lab Structure

Here is a full guide of setting up your lab network and machines if you need assistance.

1. **Kali (attacker)**

   * In VirtualBox, click New.

   * Name: kali-attacker; Type: Linux; Version: Debian (64-bit).

   * Settings → System → Set RAM to 2048–4096 MB.

   * Settings → Storage → Create a virtual hard disk (VDI, dynamically allocated, 20 GB+).
  
   * Settings → Network → Adapter 1 → Attached to: NAT Network → Name: NAT Network.
   
   * Boot the VM and install Kali (or import appliance).
     
   * After installation, take a snapshot named kali-clean.

2. **Metasploitable2**

   * If you have an OVA: VirtualBox → File → Import Appliance → select Metasploitable2 OVA → import.
   
   * Settings → Name metasploitable2; Type: Linux; Version: Other Linux (32-bit); attach downloaded disk.
  
   * Settings → System → Set RAM to 1024–2048 MB.

   * Settings → Network → Adapter 1 → Attached to: NAT Network → Name: NAT Network.
  
   * Start VM to confirm it boots.
  
   * Take a snapshot named msf2-baseline.

3. **Windows 10 (v1903 / 1909)**

   * Name: Windows-10-1903 (or similar).

   * Type: Microsoft Windows

   * Version: Windows 10 (64-bit)
  
   * Settings → Network → Adapter 1 → Attached to: NAT Network → Name: NAT-Lab.

   * Memory: allocate 2048 MB (2 GB) minimum; 4096 MB+ recommended if the host has RAM.

   * Hard disk: Create a virtual hard disk now → VDI → Dynamically allocated → size 25 GB (or larger).

   * Click Create.
  
   * Start VM to confirm it boots.
  
   * Take a snapshot named msf2-baseline.

# Fundamental Knowledge

1. **Operating Systems:** Understanding how processes, files, users, and permissions are managed is essential. Mastery of Linux and Windows helps identify vulnerabilities like misconfigured services, privilege escalation, rootkits, or malware.

2. **Networking:** All communication happens through networks. Understanding networking fundamentals, such as IP addressing, ports, protocols, and routing, helps identify vulnerabilities like sniffing, man-in-the-middle (MitM) attacks, DDoS attacks, or open service exploitation.

3. **Programming & Scripting:** All applications and services are built using programming languages. Understanding programming and scripting languages (such as Python, Bash, and PowerShell) helps identify vulnerabilities, including buffer overflows, SQL injection, command injection, and weakly automated scripts.

# Tools

Here are a couple of tools I recommend you start with.

1. **Recon / Discovery**

   * **Nmap:** port scanning & service detection.

   * **Netdiscover / ARP-scan:** network host discovery on LAN.

2. **Service & Port Enumeration**

   * **smbclient:** list and connect to SMB shares.

   * **smbmap:** enumerate SMB shares and permissions.

   * **enum4linux:** comprehensive SMB/NetBIOS enumeration for Windows/Samba hosts.

   * **SNMP tools (snmpwalk):** enumerate SNMP-enabled devices.

3. **Web Recon & Enumeration**

   * **curl / httpie:** quick HTTP requests and header inspection.

   * **Burp Suite (Community):** intercept proxy, spider, repeater for web testing.

   * **Gobuster / Dirb / Dirbuster:** brute force directories & files on web servers.

   * **Nikto:** web server scanner for common misconfigs & vulnerabilities.

4. **Credential Attacks & Passwords**

   * **Hydra:** fast online password brute‑forcing (SSH, FTP, HTTP auth, etc.).

   * **John the Ripper / Hashcat:** offline password cracking for hashes.

5. **Exploitation**

   * **Metasploit Framework:** exploit development, payloads, listeners, post‑exploitation modules.

   * **SearchSploit (Exploit-DB CLI):** offline database of public exploits.

6. **Pivoting & Tunneling**

   * **Netcat (nc):** simple TCP/UDP connection tool and ad‑hoc listener / reverse shell.

   * **SSH (local/remote port forwarding):** pivoting and port tunnels.

7. **Post‑Exploitation / Persistence**

   * **Mimikatz:** (analysis in lab): Windows credential dumping (only in isolated labs).

   * **Meterpreter:** (Metasploit): advanced post‑exploit agent with builtin modules for collection and pivoting.

# Other Resources

* **YouTube Channels:**

   * **NetworkChuck:** https://www.youtube.com/networkchuck
     
   * **David Bombal:** https://www.youtube.com/@davidbombal
     
   * **Loi Liang Yang:** https://www.youtube.com/@LoiLiangYang
     
   * **John Hammond:** https://www.youtube.com/@_JohnHammond

* **Online Courses:**

  * **Udemy:** https://www.udemy.com/
 
  * **Google Coursera:** https://www.coursera.org/google-career-certificates

* **Certifications:**
  
     * **TCM Practical Junior Penetration Tester (PJPT) Certification:** https://certifications.tcm-sec.com/
 
     * **TCM Practical Network Penetration Tester (PNPT) Exam:** https://certifications.tcm-sec.com/
 
     * **OffSec PEN-200: Penetration Testing with Kali Linux:** https://www.offsec.com/courses/pen-200/
 
     * **CompTIA PenTest+ V3:** https://www.comptia.org/en-us/certifications/pentest/v3/
 
     * **Certified Ethical Hacker (CEH) certification:** https://www.eccouncil.org/train-certify/certified-ethical-hacker-ceh-v13-north-america/
