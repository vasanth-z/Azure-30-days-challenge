# Creating a Snapshot of the VM & creating VM from VHD give in steps and in markdown text format

----
## Step 1: Create a Snapshot of the VM

1. **Go to Azure Portal**  
   Open the [Azure Portal](https://portal.azure.com) and navigate to the **Virtual Machines** service.

2. **Select the VM**  
   Choose the VM for which you want to create a snapshot.

3. **Go to Disks**  
   In the VM's settings, click on **Disks**. This will display all the disks attached to the VM.

4. **Select the Disk**  
   Click on the OS disk (or any other disk) for which you want to create a snapshot.

5. **Create a Snapshot**  
   In the disk's settings, select **Create snapshot**. Enter the snapshot name and select the **Resource group**.

6. **Configure Snapshot Settings**  
   - **Snapshot type**: Choose **Full** (for a full copy) or **Incremental** (for changes since the last snapshot).
   - **Storage type**: Choose **Standard** or **Premium** depending on your needs.

7. **Review and Create**  
   Click **Review + create**, then **Create** to start the snapshot creation.

---

# Step 2: Create a VM from a VHD

1. **Go to Azure Portal**  
   Open the [Azure Portal](https://portal.azure.com) and navigate to the **Disks** service.

2. **Upload or Select VHD**  
   - If you already have a VHD file in a storage account, locate it in your Blob Storage.
   - If you are uploading a new VHD, go to **Storage Accounts** > **[Your Storage Account]** > **Containers** > **[Your Container]**, and upload the VHD file.

3. **Create Managed Disk from VHD**  
   - Go to **Disks** and select **Create disk**.
   - Choose the VHD file as the source by selecting **Storage blob** and providing the VHD URL.
   - Configure the disk name, size, and storage type, then click **Review + create**.

4. **Create VM from Managed Disk**  
   - Go to **Virtual Machines** and select **Create** > **Virtual Machine**.
   - Choose the managed disk you created from the VHD as the OS disk.
   - Configure other VM settings such as **VM size**, **Region**, **Networking**, etc.

5. **Review and Create the VM**  
   Click **Review + create**, then **Create** to deploy the new VM.
