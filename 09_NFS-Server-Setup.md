# Setting Up NFS Server and Client on Ubuntu

## What is Linux NFS (Network File System) Server?
The Network File System (NFS) allows us to share directories & files with other Linux clients over a network. It enables users to mount remote directories on their system as if they were local folders making it useful for centralizing file management and sharing resources.

## Overall Workflow

## Configuration Steps of NFS Server Server Setup (Host/Server Machine)

### Step 1. Install and Configure the NFS Server
1. **Install the NFS Server Package**
We install the NFS server package to enable the system to share directories over the network.
```bash
    sudo apt update
```
Then run:
```bash
    sudo apt install nfs-kernel-server
```
2. **Create a Shared Directory**
This directory will hold the files we want to share with clients allowing them to access & modify data remotely.
To create the directory run:
```bash
    sudo mkdir -p /mnt/nfs_share
```
Set the correct permissions for the directory
```bash
    sudo chown nobody:nogroup /mnt/nfs_share
```
And
```bash
    sudo chmod 755 /mnt/nfs_share
```
3. **Define Export Options**
We configure how and with whom the directory is shared, controlling access and performance optimizations.
To open the NFS exports file run :
```bash
    sudo vim /etc/exports
```
Add the following line to share the directory with clients. 
```bash
    /mnt/nfs_share client_machine_ip(rw,sync,no_subtree_check,no_root_squash,no_all_squash)
```
Save and exit.

Replace **`client_machine_ip`** with actual **Client Machine IP Address**.

- **`rw`**: Allow read/write access.
- **`sync`**: Ensures data is written to disk before confirming the write.
- **`no_subtree_check`**: Improves performance by disabling subtree checks.
- **`no_root_squash`**: Allows the root user on the client to have root privileges on the server.
- **`no_all_squash`**: Preserves user permissions across the network.
4. **Export the Directories**
We export the directory to make it available to clients. For NFS Export Changes run :
```bash
    sudo exportfs -a
```
5. **Adjust Firewall Settings (If Applicable)**
If a firewall is active, we must allow NFS traffic. To allow NFS Service run :
```bash
    sudo ufw allow from client_machine_ip to any port nfs
```
Then reload the Firewall. Run :
```bash
    sudo ufw reload
```
6. **Start and Enable the NFS Service**
To start the NFS service run 
```bash
    sudo systemctl start nfs-kernel-server
```
Enable it to start on boot.
```bash
    sudo systemctl enable nfs-kernel-server
```
Check the Status
```bash
    sudo systemctl status nfs-kernel-server
```
7. **Verify NFS Share**
Ensure the NFS share is being exported correctly.
```bash
    sudo exportfs -v
```
### Step 2. Install NFS Client and Mount the Share (Client Machine)
1. **Install NFS Client Utilities**
We need to install the NFS client utilities on the client machine.
```bash
    sudo apt install nfs-common
```
2. **Create a Mount Point**
Create a directory to mount the NFS share.
```bash
    sudo mkdir -p /mnt/nfs_clientshare
```
3. **Mount the NFS Share**
To mount the shared directory from the NFS server run :
```bash
    sudo mount nfs_server_ip:/mnt/nfs_share /mnt/nfs_clientshare
```
Replace **nfs_server_ip** with the actual **IP address** of the **Server**.
- **`nfs_server_ip`**: The IP address of the NFS server.
- **`/mnt/nfs_share`**: Directory shared by the NFS server.
- **`/mnt/nfs_clientshare`**: Local directory where the share will be mounted.
4. **Verify the Mount**
This step ensures the shared directory has been successfully mounted and is accessible.
```bash
    df -h
```