# **POC: Automating Configuration Management with Azure Arc**

Azure Arc enables the automation of configuration management across hybrid and multi-cloud environments. In this POC, we demonstrate how to deploy a configuration to an Arc-enabled server using Azure Policy and Azure Automation State Configuration (DSC).

---

## **Steps for the POC**

### **1. Prerequisites**
- An Azure subscription with the Azure Arc resource provider registered.
- An on-premises or cloud server connected to Azure Arc.
- Administrator access to the Arc-enabled server.

---

### **2. Set Up Azure Automation Account**
1. **Create Automation Account**:
   - Go to the Azure Portal and search for **Automation Accounts**.
   - Click **+ Create** and provide the following details:
     - **Name**: `ArcAutomationAccount`
     - **Resource Group**: Choose an existing or create a new one.
     - **Region**: Select a region.
   - Click **Review + Create** and then **Create**.

2. **Enable System Assigned Identity**:
   - Navigate to the Automation Account.
   - Under **Identity**, enable **System Assigned Managed Identity**.
   - Assign the role of **Contributor** to the managed identity for the Arc-enabled resource group.

---

### **3. Import Desired State Configuration (DSC) Modules**
1. Navigate to the Automation Account.
2. Under **Shared Resources**, click on **Modules**.
3. Import the required modules, such as:
   - `PSDesiredStateConfiguration`
   - `Az.Accounts`
   - `Az.Resources`

---

### **4. Create a Desired State Configuration (DSC) Script**
1. Create a DSC script to configure the Arc-enabled server. Example script to ensure IIS is installed on a Windows server:
   ```powershell
   Configuration InstallIIS
   {
       Node "localhost"
       {
           WindowsFeature IIS
           {
               Ensure = "Present"
               Name = "Web-Server"
           }
       }
   }
   InstallIIS -OutputPath C:\DSC

### **5. Upload the Compiled `.mof` File to the Automation Account**
1. Navigate to **State Configuration (DSC)** in the Automation Account.
2. Click **+ Add Configuration** and upload the `.mof` file.

---

### **6. Assign DSC to an Arc-Enabled Server**
1. In the Automation Account, go to **State Configuration (DSC)**.
2. Select the uploaded configuration and assign it to the Arc-enabled server:
   - Click **+ Add Node**.
   - Select the Arc-enabled server from the list.
   - Apply the configuration.

---

### **7. Verify the Configuration**
1. Log in to the Arc-enabled server.
2. Check if the configuration has been applied successfully. For example:
   - Open a web browser and navigate to `http://localhost` to see the IIS welcome page.

---

### **8. Automate with Azure Policy**
1. Go to the **Azure Policy** section in the portal.
2. Assign a policy definition to enforce the DSC configuration across multiple Arc-enabled servers.
3. Monitor compliance through the **Policy Dashboard**.

---
