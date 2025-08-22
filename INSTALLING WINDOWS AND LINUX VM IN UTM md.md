# INSTALLING WINDOWS AND LINUX VM IN UTM

## WINDOWS VM INSTALLATION

**🛠️SETUP INSTRUCTIONS**

1. **INSTALLING THE UTM**
- The UTM application was downloaded from [https://mac.getutm.app](https://mac.getutm.app/).
- After the download completed, the application’s disk image was moved into the Applications folder.

1. **DOWNLOADING THE WINDOWS 11 ARM64 ISO**

There are two main methods of downloading the Windows 11 ARM64 ISO  

- Downloading it from the Crystal Fetch app
- Visiting  [https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewARM64](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewARM64) to download .

 Crystal Fetch application was selected due to its faster download speed, whereas downloading from Microsoft required account creation.

![Image 19-08-2025 at 14.39.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_19-08-2025_at_14.39.jpeg)

1. **CREATING THE VIRTUAL MACHINE IN UTM**
- Upon opening UTM, the process of creating a new virtual machine was initiated.
    
    ![Image 24-06-2025 at 14.10.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_24-06-2025_at_14.10.jpeg)
    
- The “Virtualise” option was selected.

![Image 24-06-2025 at 14.12.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_24-06-2025_at_14.12.jpeg)

- Followed by the choice of “Windows” as the operating system.

![Image 24-06-2025 at 14.12.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_24-06-2025_at_14.12%201.jpeg)

- The Windows ISO file was then imported into UTM.

![Image 24-06-2025 at 14.17.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_24-06-2025_at_14.17.jpeg)

- The virtual machine was configured with 8 GB of RAM, 8 CPU cores storage allocation of 64 GB, with all other settings retained at their default values.

1. **STARTING THE VM AND INSTALLING WINDOWS**
- The virtual machine was started, launching the Windows Setup Wizard. The installation proceeded successfully, and the virtual machine was restarted upon completion of the Windows installation process.

**👾CHALLENGES AND SOLUTIONS**

1. **BOOT LOOP**

**Problem:**

During the Windows installation, the virtual machine entered a continuous restart cycle. Investigation revealed that the Windows ISO remained mounted in the CD/DVD drive, causing the VM to boot from it rather than the installed operating system.

**Solution:** 

- The virtual machine was completely shut down.
- The CD/DVD drive settings were adjusted to remove the Windows ISO.
- The hard disk was prioritized in the boot order. Following these adjustments, the VM successfully booted from the installed Windows system.

1. **NO NETWORK CONNECTION**

**Problem:**

After installation, the virtual machine initially lacked internet connectivity. A basic network test using the ping command to google.com returned negative results, confirming the absence of network access. Inspection of the VM settings indicated that network drivers were not properly configured.

**Diagnosis:**

- The latest VirtIO drivers were downloaded from [https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/latest-virtio/](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/latest-virtio/), specifically the virtio-win.iso.
    
    ![Image 24-06-2025 at 18.56.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_24-06-2025_at_18.56.jpeg)
    
- The ISO was mounted in UTM, and the network driver was installed via the Windows Device Manager.
- After installation of the driver, network connectivity was restored and verified through successful ping responses.

---

## LINUX VM INSTALLATION

**Ubuntu Virtual Machine Setup in UTM** 

---

1. A new virtual machine was created within UTM.
2. Two virtualization options were available: “Virtualise,” which supports the native CPU architecture and provides faster performance, and “Emulate,” which allows other CPU architectures but operates more slowly. The “Virtualise” option was selected to ensure optimal VM performance.
3. The operating system for the virtual machine was specified as Linux.
4. The next step involved attaching a bootable ISO image. A Linux ISO file was obtained from the official distribution website.
    - Ubuntu Server ISO was downloaded from [https://ubuntu.com](https://ubuntu.com/).
    
    ![image.png](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/image.png)
    
    - The “Products” menu was accessed, and “Ubuntu Server” was selected.
    - The “Download Ubuntu Server” option was chosen, followed by “Alternative architectures.”
        
        ![Image 14-08-2025 at 12.13.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_14-08-2025_at_12.13.jpeg)
        
    - The architecture matching the host CPU was selected; for an Apple Silicon M1 system, the ARM architecture was used.
    - The 24.04.3 LTS version was downloaded due to its long-term support and stability.
    
    ![Image 14-08-2025 at 12.20.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_14-08-2025_at_12.20.jpeg)
    
- Within UTM, the downloaded Ubuntu ARM ISO was attached to the VM as the boot image.

![Image 13-08-2025 at 14.39.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_13-08-2025_at_14.39.jpeg)

- Memory and CPU resources were allocated based on available host system resources.
- Virtual storage was assigned to the VM.
- A shared directory was configured, located within the host’s Downloads folder.
- The VM configuration was reviewed and finalized.
- The virtual machine was started, initiating the Ubuntu installation process.

---

### **Ubuntu Server Installation Process**

- The installation menu presented the option to “Try or Install Ubuntu Server.” The selection was made to proceed with installation.

![Image 14-08-2025 at 12.32.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_14-08-2025_at_12.32.jpeg)

- The installation language was selected.
- The desired keyboard layout was chosen.
- The type of installation was confirmed as Ubuntu. The option to search for third-party drivers was enabled.
- Network configuration settings were left at their default values.
- Proxy settings were left blank.
- Mirror location tests were executed and passed successfully.

![Image 14-08-2025 at 12.53.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_14-08-2025_at_12.53.jpeg)

- Storage configuration was left at default settings, and the setup proceeded.
- User credentials were entered to create a profile.
- The Ubuntu Pro upgrade prompt was skipped.
- Secure remote access was enabled by installing the OpenSSH server.
- Third-party driver installation continued as prompted.
- Server snaps configuration was reviewed and finalized.
- The installation process completed successfully.

![Image 14-08-2025 at 13.03.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_14-08-2025_at_13.03.jpeg)

- The VM was instructed to reboot; however, an initial reboot failure occurred, necessitating a manual restart.
- The ISO image was removed from the CD/DVD drive to prevent the installation process from restarting.

![Image 14-08-2025 at 13.30.jpeg](INSTALLING%20WINDOWS%20AND%20LINUX%20VM%20IN%20UTM%202542b90cbf228098ab10e9e5d47a344e/Image_14-08-2025_at_13.30.jpeg)

- After clearing the ISO, the VM was restarted.
- User credentials were provided to log into the Ubuntu server successfully.

---

### **Post-Installation Configuration**

- A graphical user interface (GUI) was required for ease of operation. The Ubuntu desktop environment was installed to allow GUI-based interaction, reducing the reliance on command-line operations.
- The installation of the Ubuntu desktop was executed via command-line instructions.
- We can install ubuntu desktop by using the following commands in the command line:

```bash
sudo apt update
sudo apt install tasksel
sudo apt install ubuntu-desktop
```

- The system was updated with this command:

```bash
sudo apt update
```

- Followed by:

```bash
sudo apt install tasksel
```

- Finally :

```bash
sudo apt install ubuntu-desktop
```

- The installtion of ubuntu commenced.
- Upon completion, the OS was rebooted with this command:

```bash
sudo reboot now
```

- After rebooting, the graphical user interface appeared.
- Ubuntu should be up and running.