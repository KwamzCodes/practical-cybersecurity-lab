# VULNERABILTY CHECK WITH NMAP

**Port Scanning with NMAP**

In this exercise, the Linux virtual machine (VM) serves as the scanning host, while the Windows VM acts as the target system. The objective is to identify open ports on the Windows VM to assess potential vulnerabilities.

Prior to scanning, the firewall on the Windows VM was temporarily disabled to allow accurate detection of open ports.

```powershell
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False
```

**Target:** Windows VM (192.168.xxx.xxx)

**Tool Used:** Nmap

**Command :**

The following command was run to identify open ports:

```bash
sudo nmap -sT 192.168.xxx.xx  #scans for ports

```

![image.png](Images/1a5a1fc4-dde0-4075-a84a-09d61a0bce70.png)

**Findings:**

- Port 135 (RPC Endpoint Mapper) : Open
- Port 139 (NETBIOS) : Open
- Port 445 (SMB) : Open

Subsequently, additional scans were conducted against the system’s public IP address to verify whether these ports were exposed to the internet. Port 135 appeared in an ignored or filtered state, suggesting that it was blocked by the firewall and not externally accessible. This confirmed that the isolated lab configuration prevented exposure of these services to the outside network.

```bash
nmap -p 445 your.public.ip.address
nmap -p 135 your.public.ip.address
nmap -p 135 your.public.ip.address
```

![Image 17-08-2025 at 13.17.jpeg](Images/486d4f1a-3c0c-435a-b9d6-25dca5917e68.png)

**Risk of Open Ports:**

Even in isolated environments, the presence of open ports poses risks if exploited by an attacker with local access.

- **Port 135 (RPC):** Can be abused for privilege escalation, lateral movement, or remote code execution.
- **Port 139 (NetBIOS):** Exposes the machine’s NetBIOS name, shared resources, and user information.
- **Port 445 (SMB):** A common attack vector for ransomware campaigns and credential theft within enterprise networks.

**Solution:**

Since these ports contribute to core Windows functionality, they cannot be fully disabled without impacting system operations. However, their attack surface can be reduced by hardening configurations and restricting unnecessary access.

**Port 445**

**Disabling SMBv1**

The outdated SMBv1 protocol should be disabled while keeping SMBv2 and SMBv3 enabled. This can be achieved through the Windows Features panel by deselecting “SMB 1.0/CIFS File Sharing Support” and restarting the system.

![image.png](Images/imagecopy3.png)

**Block SMB Ports with Firewall**

Inbound firewall rules can be configured to block traffic on TCP port 445 across Domain, Private, and Public profiles, thereby reducing external exposure without fully disabling SMB services.

![Image 17-08-2025 at 13.49.jpeg](Images/Image_17-08-2025_at_13.49.jpeg)

**Port 139 (NetBIOS)**

**Disabling NetBIOS**

The NetBIOS service can be disabled through the network adapter’s advanced settings under the WINS configuration.

- Control Panel > Network & Internet > Network and Sharing Centre
- In the “Change adapter settings” > NIC > Properties> Internet Protocol Version 4 (TCP/IPv4)
- In Advanced > WINS > Disable NetBIOS over TCP/IP

![Image 19-08-2025 at 17.23.jpeg](Images/Image_19-08-2025_at_17.23.jpeg)

**Blocking NetBIOS port with Firewall**

- An inbound firewall rule can be applied to block TCP port 139, further restricting access to this service.

**Port 135 (RPC)**

**Disabling RPC**

- Core RPC functionality should be retained, but services such as *Remote Registry* and *Routing and Remote Access* can be disabled via the Services console if not required.

![image.png](Images/image%201.png)

![image.png](Images/image%202.png)

![image.png](Images/image%203.png)

Additionally, system properties can be configured to disallow remote connections.

![Image 17-08-2025 at 20.31.jpeg](Images/Image_17-08-2025_at_20.31.jpeg)

![image.png](Images/image%204.png)

## **Conclusion**

The port scanning process confirmed that the Windows VM exposed several critical ports (135, 139, and 445) within the isolated lab network. While these services were not exposed to the internet, they represent potential attack surfaces for local adversaries. By disabling outdated protocols (e.g., SMBv1), restricting unnecessary services (e.g., NetBIOS), and applying targeted firewall rules, the system’s attack surface can be significantly reduced without compromising core functionality.

---
