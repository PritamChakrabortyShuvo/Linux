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
    /mnt/nfs_share 192.168.1.0/24(rw,sync,no_subtree_check,no_root_squash,no_all_squash)
```
Save and exit.

Replace **`192.168.1.0/24`** with **Client Machine IP Address**.

- **`rw`**: Allow read/write access.
- **`sync`**: Ensures data is written to disk before confirming the write.
- **`no_subtree_check`**: Improves performance by disabling subtree checks.
- **`no_root_squash`**: Allows the root user on the client to have root privileges on the server.
- **`no_all_squash`**: Preserves user permissions across the network.
 4. **Export the Directories and Restart NFS services**
We export the directory to make it available to clients. For NFS Export Changes run :
```bash
    sudo exportfs -a
```
Then restart the NFS service to apply the changes.
```bash
    sudo systemctl restart nfs-kernel-server
```
```bash
    sudo systemctl enable nfs-kernel-server
```
```bash
    sudo systemctl status nfs-kernel-server
```