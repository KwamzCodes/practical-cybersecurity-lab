# SETTING UP A BRIDGED/EMULATED NIC OR A VIRTUAL INTERNAL NETWORK IN UTM.

By configuring a bridged network interface card (NIC) or a virtual internal network, communication is restricted to the host machine and the two virtual machines (Windows and Linux). This setup is critical for maintaining a safe environment for vulnerability testing, port scanning, and simulated attack demonstrations, as it prevents exposure of the lab to the external network.

**STEP-BY-STEP IMPLEMENTATION**

- Both virtual machines were first powered off.
- In UTM, the Windows VM was selected and its settings accessed.
- Within the network configuration, the network mode was adjusted to **Bridged (Advanced)**.

![image.png](SETTING%20UP%20A%20BRIDGED%20EMULATED%20NIC%20OR%20A%20VIRTUAL%20INT%202542b90cbf2280728c97cbbebf0a88d1/image.png)

- The same configuration was then applied to the Linux VM.
- Once both virtual machines were configured, they were started simultaneously.
- To verify connectivity, the IP addresses of both systems were obtained.
- On the Windows VM, the IPv4 address was identified using the system’s network configuration output:

```powershell
ipconfig
```

- The IPv4 address was obtained on the Linux VM with the below command. The address was  located under the inet field in the network interface details.

```bash
ip addr show
```

- With the addresses identified, connectivity between the two systems was tested by initiating ICMP echo requests (pings) from each VM to the other.
- Successful replies confirmed that the bridged network configuration allowed direct communication between the Windows and Linux VMs while maintaining isolation from the wider LAN.