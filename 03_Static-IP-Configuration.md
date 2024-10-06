# Setting a Static IP in Ubuntu Using Netplan🌍

## Why we use Static IP Address?
Static IP addresses are used because they provide a **fixed address** for devices on a network making it easier to connect to them. This consistency is crucial for servers & printers allowing for reliable remote access & hosting services like websites & email. **Static IPs** simplify network setup and avoid conflicts ensuring that devices can always be found at the same address. They are especially useful for older systems that don’t support dynamic IPs. Overall **Static IPs make managing networked devices easier and more reliable**.

## What is Netplan?
**Netplan** is a utility used in **Ubuntu** (starting from *version 17.10*) for managing and configuring **network settings**. It provides a simple way to **configure networking** through human-readable **YAML files** & works with modern **networking backends** like **systemd-networkd** & **NetworkManager**.

## What is YAML file?
A **YAML** file is a **human-readable text file** used for **storing data** in a structured format. It stands for **"Yet Another Markup Language"**. It’s designed to be **simple** & **easy** for both **humans** & **machines** to understand.

## Configure Static IP Address on Ubuntu 22.04 
<div align="center">
  <img src="Images/Static IP Configuration workflow.png" alt="Project Logo" width=100% height=30%/>
</div>

### Step 1 : Check Network Interface Name and which Network manager is active
```bash
    ip link show # For checking network interface
```
Or,
```bash 
    ip a #For checking network interface
```
```bash
    systemctl status NetworkManager # For which Network manager is active
```
### Step 2 : Edit the Netplan Configuration File
Open the **Netplan configuration file**. The filename may vary but common names include **`01-netcfg.yaml`** or **`01-network-manager-all.yaml`** or something similar. We can use vim, nano or any text editor.
```bash
    sudo vim /etc/netplan/01-network-manager-all.yaml
```
### Step 3: Configure the Static IP
Add or modify the configuration for the identified interface.
```bash
    network:
      version: 2
      renderer: NetworkManager # Use the correct renderer name here
      ethernets:
        ens33:  # Use the correct interface name here
          dhcp4: no
          addresses:
            - 192.168.100.1/32
          routes:
            - to: default
              via: 192.168.0.1
          nameservers:
            addresses: [8.8.8.8, 1.1.1.1]
```
### Step 4 : Save & Exit
 - **In `vim`:** Press **`Esc`**, type **`:wq`** & hit **Enter** to save and exit.
 - **In `nano`:** Press **`CTRL`** **+** **`X`** then **Y** to confirm saving & hit **Enter**.

### Step 5 : Apply the Configuration
```bash
    sudo netplan apply
```
### Step 6: Check IP Configuration
Verify that our static IP has been assigned correctly by checking the IP configuration.
```bash
    ip link show 
```
Or,
```bash 
    ip a 
```
Or,
```bash
    ip addr show
```
## Explanation 
 - **`network :`** This is the top-level key that starts the network configuration.
 - **`version: 2`** Specifies the version of the Netplan configuration format. **`Version 2`** is the most commonly used version.
 - **`renderer: NetworkManager`** Indicates that **NetworkManager** is responsible for managing the network settings on this system. If we were using **`systemd-networkd`** we would replace this with **`renderer: networkd`**.
 - **`ethernets:`** This key specifies the configuration for Ethernet interfaces.
 - **`ens33:`** This is the name of the **network interface** we want to configure. We should replace **`ens33`** with the actual name of our interface which can be found by using the command **`ip link show`**.
- **`dhcp4: no`** Disables **DHCP (Dynamic Host Configuration Protocol)** for this interface meaning that the system will not automatically obtain an IP address from a DHCP server. Instead, we will assign a static IP address.
- **`addresses`**: This key allows you to specify the **static IP** address for the interface. In this case, **`192.168.100.1/32`** is the assigned **IP address** with **`/32`** indicating the **subnet mask** (which is unusual for most LAN configurations and usually means it's a single host).
 - **`routes:`** This key allows you to define routing information for the interface.
   - **`- to: default`**: This indicates that the following route applies to all traffic that does not match any other specific route.
   - **`via: 192.168.0.1`**: Specifies the **`gateway IP address`** for outgoing traffic. This is the **router's IP address** through which all non-local traffic will be sent.
   - **Alternative for Default Gateway:** Instead of using the **`routes:`** section we can simply specify the default gateway directly under the interface like this:

     ```bash
      gateway4: 192.168.0.1  # Sets the default gateway directly
     ```
     We can use **`gateway4`** there is no need for the **`routes:`** key specifying **`to: default`** and **`via:.`**
 - **`nameservers:`** This key specifies the **DNS servers** to be used for resolving **domain names** into **IP addresses**. The example specifies two DNS servers: **`8.8.8.8`** **(Google's DNS)** and **`1.1.1.1`** **(Cloudflare's DNS)**.