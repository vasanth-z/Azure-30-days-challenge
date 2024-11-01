# Launch and Manage an Azure Virtual Machine with SSH and Web Server Setup

## 1. Launch an Azure Virtual Machine

### Step 1: Sign in to Azure Portal
1. Go to the [Azure Portal](https://portal.azure.com/) and sign in with your account.

### Step 2: Create a Virtual Machine
1. On the Azure Portal homepage, select **Create a resource**.
2. In the search bar, type **Virtual Machine** and select it from the dropdown.
3. Click **Create** to begin configuring your VM.

### Step 3: Configure Basic Settings
1. **Subscription**: Select your subscription.
2. **Resource Group**: Choose an existing one or create a new resource group.
3. **Virtual Machine Name**: Enter a unique name for your VM.
4. **Region**: Choose a region close to you.
5. **Image**: Select **Ubuntu Server** from the dropdown (or another OS you prefer).
6. **Size**: Choose a VM size based on your needs (e.g., Standard B1s).
7. **Authentication Type**: Select **SSH public key**.
8. **Username**: Enter a username for SSH access.
9. **SSH Public Key**: Paste your public SSH key here (you can generate it using `ssh-keygen` on your local machine).

### Step 4: Configure Networking
1. **Virtual Network**: Leave it at default or create a new one.
2. **Public IP**: Ensure a Public IP is created.
3. **Inbound Port Rules**: Allow **SSH (22)** and **HTTP (80)** to enable SSH and web access.

### Step 5: Create the VM
1. Review your settings, then click **Review + Create**.
2. Once the validation passes, click **Create** to start VM deployment.
3. After a few minutes, your VM should be ready.

---

## 2. SSH into the Instance

1. In the Azure portal, go to **Virtual Machines** and select your VM.
2. Under **Overview**, copy the **Public IP address** of your VM.
3. Open a terminal on your local machine and enter:
   ```bash
   ssh <username>@<public-ip-address>
