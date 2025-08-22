# INSTALLING THE NETWORK SECURITY TOOLS.

## INSTALLING SECURITY TOOLS

**NETWORK MAPPER (NMAP)**

- In the terminal the system was updated to ensure all packages and dependencies were current prior to application installation with this command:

```bash
sudo apt update
```

- Following the update, Nmap was installed on the Ubuntu virtual machine to provide network scanning capabilities. It was done with this command:

```bash
sudo apt install nmap -y
```

The -y answers YES to a prompt during the installation.

![Image 14-08-2025 at 15.04.jpeg](INSTALLING%20THE%20NETWORK%20SECURITY%20TOOLS%202542b90cbf2280f89a8de23ca41c7b7d/Image_14-08-2025_at_15.04.jpeg)

**NESSUS**

- The latest version of Nessus was downloaded from the official Tenable website.  https://www.tenable.com/downloads/nessus
- The platform was selected to match the Ubuntu system architecture (aarch64).
- After downloading it, copy the curl command in the “Download by curl” and  head over to the terminal to download the packages.
- After the download, the curl command in the “Download by curl” was copied and pasted in the terminal. This is used to download the packages.

```bash
curl --request GET \
  --url 'https://www.tenable.com/downloads/api/v2/pages/nessus/files/Nessus-10.9.2-ubuntu1804_aarch64.deb' \
  --output 'Nessus-10.9.2-ubuntu1804_aarch64.deb'
```

- The packages were then installed with this command:

```bash
sudo dpkg -i Nessus-10.9.2-ubuntu1804_aarch64.deb

#the 'Nessus-10.9.2-ubuntu1804_aarch64.deb' is the version and platfomr of Nessus you downloaded. 
```

- Upon installation, Nessus was accessed via a web browser using the local host URL, which was verified through this command:

```bash
ping LocalHost
```

- The setup wizard guided the configuration process.
- For the free version, Nessus Essentials was opted.
- The registration was completed and an activation code was obtained. The system initialized Nessus successfully, providing full access to the vulnerability scanning platform.

**WIRESHARK**

- In the terminal, the system was updated to provide the latest version of Wireshark.

```bash
sudo apt update
```

- Wireshark was installed was the installed with this command:

```bash
sudo apt install wireshark
```

- Following the installation, Wireshark was launched, providing a graphical interface for network traffic capture and analysis.

Once all security tools were installed, the virtual machines were configured to be isolated from the rest of the LAN. This was achieved by setting up a virtual internal network or by configuring a bridged/emulated network interface card. This ensured that other devices on the local network could not detect or access the virtual machines.