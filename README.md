# **Cybersecurity VM Vulnerability Scanning Project**

## **📖 Overview**

This project demonstrates a basic cybersecurity lab setup for practicing vulnerability scanning and analysis. Two virtual machines were configured in a controlled environment:

- **Linux VM (Kali/Ubuntu-based)** → used as the **attacker/scanning machine**
- **Windows VM (Windows 10/11)** → used as the **target machine**

The Linux VM was equipped with open-source security tools such as **Nmap** and **Nessus** to perform active reconnaissance and vulnerability scanning on the Windows VM.

The project highlights how attackers might identify weaknesses in a system and how defenders can detect, mitigate, or remediate these vulnerabilities.

---

## **🛠️ Tools & Technologies**

- **Virtualization:** UTM
- **Scanning Tools:**
    - [Nmap](https://nmap.org/) – Network discovery & port scanning
    - [Nessus Essentials](https://www.tenable.com/products/nessus/nessus-essentials) – Vulnerability assessment
- **Target System:** Windows Virtual Machine
- **Attacker System:** Linux Virtual Machine (Ubuntu)

---

## **⚙️ Project Setup**

1. **Virtual Machines**
    - Installed Linux as the scanning machine
    - Installed Windows as the target machine
    - Ensured both were on the same virtual network (Bridged NIC)
2. **Installed Security Tools** on Linux VM
    - Nmap for port scanning.
    - Nessus for vulnerability scanning and reporting
3. **Performed Scans**
    - Used **Nmap** to detect open ports.
    - Used **Nessus** to perform a vulnerability scan of the Windows VM
4. **Mitigation Example**
- Identified open ports 445, 135, 139
- Diasbled these ports and enforced firewall rules.
- Identified the **ICMP Timestamp Request Disclosure** vulnerability
- Created Windows Firewall inbound rules to block ICMP type 13 (requests) and type 14 (replies)
- Verified the mitigation by re-scanning with Nessus

---

## **🧪 Results**

- Successfully identified open ports and potential vulnerabilities on the Windows VM
- Demonstrated how ICMP timestamp requests can leak system time information
- Implemented firewall rules to mitigate the disclosure vulnerability
- Confirmed remediation through re-testing

---

## **🚀 How to Reproduce**

- Set up two VMs (Linux + Windows) on the same virtual network.
- Run port and vulnerability scans against the Windows VM.
- Review identified vulnerabilities.
- Apply firewall rules on Windows to mitigate risks.
- Re-run scans to confirm successful remediation.

---

## **🛡️ Lessons Learned**

- The importance of network segmentation and firewall rules in reducing attack surface
- How common tools like **Nmap** and **Nessus** can reveal critical system weaknesses
- Practical steps in mitigating vulnerabilities after detection

---

## **⚠️ Disclaimer**

This project was conducted in a **controlled lab environment** for **educational purposes only**. Do not use these techniques on networks or systems you do not own or have explicit permission to test.
