# Connecting Azure Logic Apps to a Firewall-Protected Resource

Follow these steps to connect **Azure Logic Apps** to a resource protected by a **Firewall**:

---

## Step 1: Create or Configure Your Azure Logic App
1. **Log in to Azure Portal**:
   - Go to the [Azure Portal](https://portal.azure.com).
   - Navigate to your Logic App or create a new one:
     - Search for **Logic Apps** in the search bar and select **+ Create**.
     - follow the same procedure to create another logic app

2. **Select the Hosting Plan**:
   - Choose the **Standard** plan (required for VNet integration).
   - Complete the creation process.

---

3. **Create a Storage Account**:
   - Create a storage account with same resource group.
   - Then click "review and create"
  
     **Create a container**:
   - Go to container and add data into it.

---

## Step 4: Add Firewall Rules
1. **Locate to Storage Account (networking)**:
   - Enable Firewall options with "virtual network" and leave it as default.
---

## Step 5: Test the Configuration
1. **Add a data to container**:
   -If adding container this may shows that "access denied"

2. **Monitor the Connection**:
   - Use the **Monitor** section in the Logic App to view run history and troubleshoot any issues.

---

## Step 6: Troubleshooting (if needed)
- **Check NSG Rules**: Ensure the NSG associated with your VNet subnet permits required traffic.
- **Private DNS Configuration**: If private endpoints are used, configure DNS appropriately to resolve the private IP of resources.
- **Firewall Logs**: Review firewall logs to identify blocked traffic and adjust rules.

---

This configuration ensures that your Logic App can securely connect to resources behind a firewall while leveraging Azure's networking capabilities.
