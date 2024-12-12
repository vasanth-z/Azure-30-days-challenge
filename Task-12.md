# Adding and Configuring a Data Disk to an Azure Virtual Machine

This guide walks you through adding a new data disk to an Azure Virtual Machine and initializing it for use.

---

## Step 1: Navigate to the Virtual Machine

### **Service Used**: Azure Portal  
1. Log in to the [Azure Portal](https://portal.azure.com).  
2. In the left-hand menu, select **"Virtual machines"**.  
3. From the list of virtual machines, select the one you want to add the disk to.  

---

## Step 2: Add a Data Disk

### **Service Used**: Azure Managed Disks  
1. In the VM pane, locate the **"Settings"** section on the left side and click **"Disks"**.  
2. Click on the **"+ Add data disk"** button at the top of the Disks page.  
3. In the "Name" drop-down, select **"Create disk"** to create a new managed disk.  

---

## Step 3: Create a New Disk

### **Service Used**: Azure Managed Disks  
1. Fill in the following details for the new disk:  
   - **Name**: Enter a unique name for the disk.  
   - **Resource Group**: Choose the same resource group as your VM.  
   - **Location**: Ensure it matches the VM's location.  
   - **Size**: Specify the desired disk size (e.g., 32 GB).  
   - **Performance Tier**: Choose based on your workload (e.g., **Standard SSD** or **Premium SSD**).  
2. Click **"Review + create"**, and then click **"Create"** to provision the disk.  

---

## Step 4: Attach the Disk

### **Service Used**: Azure Portal  
1. After creating the disk, return to the **Disks** pane of your VM.  
2. In the **Name** drop-down under the "Data disks" section, select the newly created disk.  
3. Click **"Save"** at the top of the page to attach the disk to the VM.  

---

## Step 5: Initialize the Disk (within the VM)

### **Service Used**: Operating System Disk Management Tools  
Once the disk is attached, you need to initialize and format it within the operating system.

### **Windows Virtual Machines**  
1. **Connect to the VM** using **RDP (Remote Desktop Protocol)**.  
   - Open the Remote Desktop Connection app on your local machine.  
   - Enter the public IP of the VM and log in using the VM's credentials.  
2. Open **Disk Management**:  
   - Press `Win + R`, type `diskmgmt.msc`, and hit Enter.  
3. Initialize the Disk:  
   - Locate the new disk marked as **"Not Initialized"**.  
   - Right-click on the disk and select **"Initialize Disk"**.  
   - Choose the partition style (MBR or GPT) and click **OK**.  
4. Create a New Volume:  
   - Right-click on the unallocated space and select **"New Simple Volume"**.  
   - Follow the wizard to assign a drive letter, format the disk (NTFS), and complete the setup.  

### **Linux Virtual Machines**  
1. **Connect to the VM** using **SSH**:  
   - Use a tool like **PuTTY** or a terminal command:  
     ```bash
     ssh <username>@<VM-public-IP>
     ```
2. Verify the Disk:  
   - Run the following command to list the attached disks:  
     ```bash
     lsblk
     ```
   - The new disk will appear as `/dev/sdX` (e.g., `/dev/sdb`).  
3. Partition the Disk:  
   - Use `fdisk` to create a partition:  
     ```bash
     sudo fdisk /dev/sdX
     ```
     Follow the prompts to create a new partition.  
4. Format the Partition:  
   - Format the partition with a filesystem, such as ext4:  
     ```bash
     sudo mkfs.ext4 /dev/sdX1
     ```
5. Mount the Disk:  
   - Create a mount point:  
     ```bash
     sudo mkdir /mnt/mydatadisk
     ```
   - Mount the disk:  
     ```bash
     sudo mount /dev/sdX1 /mnt/mydatadisk
     ```
6. Make the Mount Permanent:  
   - Add the disk to `/etc/fstab` for auto-mounting on reboot.  
     ```bash
     echo '/dev/sdX1 /mnt/mydatadisk ext4 defaults 0 0' | sudo tee -a /etc/fstab
     ```

---

## Step 6: Verify and Use the Disk

1. Confirm that the disk is accessible:  
   - In Windows, check File Explorer for the new drive.  
   - In Linux, navigate to the mount point:  
     ```bash
     cd /mnt/mydatadisk
     ```
2. Start using the disk for your application or data storage.

