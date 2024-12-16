# 1. Creating an Azure Data Factory
### Step 1:
- Open the Azure portal.
- In the search bar at the top, type **Azure Data Factory** and select it from the results.

### Step 2:
- Click on the **Create** button to start creating a new data factory.

### Step 3:
- Fill in the required details:
  - **Subscription**: Choose your Azure subscription.
  - **Resource group**: Select an existing resource group or create a new one.
  - **Name**: Provide a unique name for your data factory.
  - **Region**: Choose the region where you want the data factory to be deployed.
  - **Version**: Ensure to select **V2** as it is the latest version.

### Step 4:
- Navigate to the **Review + Create** tab.
- Verify all the details and click on the **CREATE** button to start the deployment process.
- Wait for the deployment to complete.

---

# 2. Creating an SQL Database
### Step 1:
- In the Azure portal search bar, type **SQL Database** and select it.
- Click on **Create** to start creating a new database.

### Step 2:
- Fill in the required details:
  - **Subscription**: Select your Azure subscription.
  - **Resource group**: Choose an existing resource group or create a new one.
  - **Database Name**: Provide a unique name for the SQL database.
  - **Region**: Select the region where you want the database deployed.
  - **Compute + Storage**: Configure the compute tier and storage settings.
  - **Backup Storage Redundancy**: Choose the desired redundancy option (e.g., Locally redundant or Geo-redundant).
  - **Workload Environment**: Define the workload type (e.g., production or development).
  - **Server**: Select an existing server or create a new one for hosting the database.

### Step 3:
- Move to the **Review + Create** tab.
- Confirm the details and click on **CREATE**.
- Wait for the deployment to finish.

---

# 3. Creating a Storage Account
### Step 1:
- In the Azure portal, search for **Storage Accounts** and select it.
- Click on **Create** to begin the process.

### Step 2:
- Fill in the required information:
  - **Storage Account Name**: Enter a unique name for the storage account.
  - **Performance**: Choose the performance tier (e.g., Standard).
  - **Region**: Select the desired region for deployment.
  - **Redundancy**: Select the redundancy level (e.g., Hot or Cool Access Tier).

### Step 3:
- Proceed to the **Review + Create** tab.
- Verify the information and click on **CREATE**.

### Step 4:
- Once the deployment completes, navigate to the resource group to view and manage your storage account.

---

# 4. Creating a Pipeline
### Step 1:
- Go to the Azure Data Factory interface.
- Navigate to the **Author** section and click on **Add Pipeline** to create a new pipeline.

### Step 2:
- Optionally, rename the pipeline for easier identification.
- This can be done by editing the name field in the pipeline editor.

---

# 5. Linking a Service
### Step 1:
- In Azure Data Factory, navigate to the **Manage** section.
- Click on **Linked Services** to create a new linked service.

### Step 2:
- Choose **Blob Storage** from the list of available services.

### Step 3:
- Enter the required details:
  - **Name**: Provide a name for the linked service.
  - **Description**: Optionally, add a description.
  - **Authentication Type**: Select the authentication method (e.g., Azure Key Vault or account key).
  - **Account Selection Method**: Specify how the storage account will be identified.
  - **Azure Subscription**: Choose your Azure subscription.
  - **Storage Account Name**: Select the desired storage account.

### Step 4:
- Test the connection by clicking **Test Connection**.
- If successful, click **CREATE** to finalize the linked service.

---

# 6. Creating a Dataset
### Step 1:
- In the Azure Data Factory interface, go to the **Author** section.
- Click on **Add Dataset**.

### Step 2:
- Select the source type.
  - For instance, choose **Azure Blob Storage** if working with Blob storage.

### Step 3:
- Choose the file format.
  - For example, select **CSV** as the dataset format.

### Step 4:
- Provide a name for the dataset to identify it.

### Step 5:
- Configure the dataset location.
  - Browse and select the file location from the linked storage account.

### Step 6:
- Finalize by clicking **Add** to save the dataset.
