# **Creating Azure Machine Learning Workspace**

## **Brief Steps**
1. Search for **Azure Machine Learning** in the search bar.
2. Fill in required details:  
   - Name, Resource Group, Storage Account, Region, etc.  
3. Configure **Networking**: Set it to **Public**.  
4. Configure **Identity**: Use an existing User Assigned Identity (UAI) or allow Azure to create resources like Storage Account, Key Vault, etc.  
5. Review and create the workspace.  
6. Access the resource group and verify deployment.  

---

## **Detailed Steps**

### **Step 1: Search for Azure Machine Learning**
- Log in to the [Azure Portal](https://portal.azure.com).
- Search for **Azure Machine Learning** in the search bar and select the service.

---

### **Step 2: Enter Necessary Details**
1. Fill in the following fields:
   - **Name**: Provide a unique name for the workspace.
   - **Resource Group**: Select an existing resource group or create a new one.
   - **Storage Account**: Choose an existing storage account or allow Azure to create one.
   - **Region**: Select the appropriate region for your deployment.
   - **Key Vault**: Use an existing Key Vault or allow Azure to create one.
   - **Application Insights**: Specify an existing one or let Azure handle it.
   - **Container Registry**: Use an existing container registry or let Azure provision it.
   - **Subscription**: Ensure the correct subscription is selected.

---

### **Step 3: Configure Networking**
- Under the **Networking** tab:
  - Set connectivity to **Public** to allow external access to the workspace.

---

### **Step 4: Configure Identity**
- Under the **Identity** tab:
  - Choose **User Assigned Identity** if you already have:
    - Storage Account
    - Key Vault
    - Application Insights
    - Container Registry  
  - If not, Azure will create these resources automatically.

---

### **Step 5: Review and Create**
- Click **Review + Create** to validate the configuration.
- Once validation passes, click **Create** to deploy the workspace.

---

### **Step 6: Access the Resource Group**
- After deployment completes, navigate to the **Resource Group** to verify all components are deployed successfully.

---

# **Launching Azure Machine Learning Studio**

## **Brief Steps**
1. Go to the **Azure ML resource** and select **Overview**.  
2. Click **LAUNCH ML STUDIO** from the overview page.  
3. Access your **Azure Machine Learning Studio** for further operations.  

---

## **Detailed Steps**

### **Step 1: Access the Azure ML Resource**
- Go to the deployed **Azure Machine Learning Workspace** resource.
- The **Overview** tab will display the workspace details.

---

### **Step 2: Launch ML Studio**
- In the **Overview** tab, click the **LAUNCH ML STUDIO** button.
- This redirects you to the **Azure Machine Learning Studio** interface.

---

### **Step 3: Access the ML Studio**
- Explore features like dataset uploads, training experiments, and model deployment within the ML Studio environment.
