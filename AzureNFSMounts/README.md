# Azure NFS Mounts

This is a "Quickstart" guide for mounting an Azure Blob Storage container to a Linux-based Azure Virtual Machine.

[See more, from Microsoft.](https://learn.microsoft.com/en-us/azure/storage/blobs/network-file-system-protocol-support-how-to)

## Quickstart Guide: Azure Blob Storage NFS Mount to Azure VM

1. Create a Virtual Machine (VM) and a storage account with default settings.

When you create the storage account...
* ensure that `Enable network file system v3` is checked when you create the storage account.
* under Networking, select "Enable public access from selected virtual networks and IP addresses"; then select the virtual network (vnet) associated with your VM. You may also want to add your client IP address at this time.

2. Create a container within the storage account.

3. Install the Azure NFS mount helper package.
    ```sh
    wget -O - -q https://github.com/Azure/AZNFS-mount/releases/latest/download/aznfs_install.sh | bash
    ```

4. Create a directory for the NFS mount.
    ```sh
    mkdir -p /nfsdata
    ```

5. Add the NFS mount entry to `/etc/fstab`. Then, reload the systemd daemon and mount the NFS directory.
    ```sh
    echo "<account-name>.blob.core.windows.net:/<account-name>/<container-name>  /nfsdata  aznfs defaults,sec=sys,vers=3,nolock,proto=tcp,nofail,_netdev  0 0" | sudo tee -a /etc/fstab
    
    sudo systemctl daemon-reload
    
    sudo mount /nfsdata
    ```