# Connect Virtual Machine Through Azure Bastion

Azure Bastion provides secure RDP and SSH connectivity to your Azure Virtual Machines without the need for a public IP. Follow these steps:

---

## **Step 1: Deploy a Virtual Machine**
1. Go to the [Azure Portal](https://portal.azure.com).
2. Navigate to **Virtual Machines** and click **+ Create**.
3. Fill in the necessary details:
   - **Resource Group:** Select or create a new one.
   - **VM Name:** Enter a name for the VM.
   - **Region:** Ensure the region supports Azure Bastion.
   - **Image:** Choose an OS (e.g., Windows or Linux).
   - **Size:** Select an appropriate size.
   - **Authentication Type:** Use either Password or SSH Key.
4. Disable **Public IP** (Bastion doesn't require a public IP).
5. Review and create the VM.

---

## **Step 2: Set Up an Azure Bastion Host**
1. Go to the **Azure Bastion** service in the portal or search for **Bastion**.
2. Click **+ Create** to deploy a Bastion host.
3. Fill in the required details:
   - **Resource Group:** Use the same as your VM.
   - **Name:** Enter a name for the Bastion host.
   - **Region:** Same as the VM's region.
   - **Virtual Network:** Select the VNet that contains your VM.
   - **Subnet:** A dedicated subnet (`AzureBastionSubnet`) is required:
     - If it doesn't exist, create it with a prefix of `/27` or larger (e.g., `10.0.0.0/27`).
4. Click **Review + Create** to deploy the Bastion.

---

## **Step 3: Connect to the Virtual Machine**
1. Go to **Virtual Machines** in the Azure portal.
2. Select the VM you want to connect to.
3. In the VM's menu, click **Connect** → **Bastion**.
4. Click **Use Bastion** to open the connection interface.
5. Enter the following details:
   - **Username:** VM's admin username.
   - **Password/SSH Key:** Depending on the authentication type used during VM creation.
6. Click **Connect**.

---

## **Step 4: Verify the Connection**
1. A new browser tab opens with the VM session.
2. Confirm you have access to the VM using RDP or SSH.

---

## **Additional Notes**
- Ensure proper Network Security Group (NSG) rules are applied to allow Bastion connectivity within the VNet.
- Azure Bastion requires HTTPS (port 443) for communication.
- If issues arise, verify that the **AzureBastionSubnet** exists and has the correct CIDR range.

---

**You are now securely connected to your VM using Azure Bastion!**
