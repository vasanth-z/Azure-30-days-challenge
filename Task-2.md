# Replicate Data within and between Azure Regions Using Azure Blob Storage

## Step 1: Set Up the Primary Storage Account
1. **Sign in to the Azure Portal**  
   Go to [Azure Portal](https://portal.azure.com/) and sign in using your Azure account.

2. **Navigate to Storage Accounts**  
   - On the left sidebar, select **Storage accounts**.
   - If you don’t see it, search for “Storage accounts” in the top search bar.

3. **Create a New Storage Account** (two storage accounts)
   - Click **+ Create**.
   - Under the **Basics** tab, fill out the required fields:
     - **Subscription**: Select the subscription for billing.
     - **Resource Group**: Choose an existing or create a new one.
     - **Storage Account Name**: Enter a unique name (3-24 characters, lowercase letters and numbers only).
     - **Region**: Choose the primary region for your storage account (e.g., East US).
   - For **Performance** and **Redundancy**, select **Standard**.

4. **Choose Redundancy Option (GRS or RA-GRS)**  
   - In the **Redundancy** dropdown, choose:
     - **Geo-redundant storage (GRS)**: Data is replicated to a paired secondary Azure region.
     - **Read-access geo-redundant storage (RA-GRS)**: Data replication with read access in the secondary region.

## Step 2: Configure Additional Settings (optional):
1. Go to the **Advanced** tab:
   - **Access Tier**: Choose **Hot** (frequent access), **Cool** (infrequent), or **Archive**.
   - **Blob Public Access Level**: Adjust public access level if needed.
   - **Encryption**: Enable additional encryption if required.

2. **Network Settings** (optional):
   - Configure **firewall** and **virtual network** settings for network access.
   - Specify IP ranges and allow selected virtual networks.

3. **Review and Create the Storage Account**  
   - Review settings on the final page.
   - Click **Create** to deploy the storage account.

## Step 3 Creation a Containers
1. **TO Create a container**  
   - Go to **Storage Account** > **Data storage** > **container**.
   - click on "+create" and name it as container1.
  


2. **go to storage account2**  
   - Go to **Storage Account** > **Data storage** > **container**.
   - click on "+create" and name it as container2.
  
## Step 4 : Data Replication
   -Go to **Storage Account1** > **Data Management** > **Object Replication**.
   -click on "+create replication rules".
   -Assign Destination account as "storage Account2".
   -source conatiner as "container1" and destination container as "container2".(which to be stored in another account)

## Step 5: Validate Data Replication
1. **Upload a Test Blob**  
   - In **storage account1**, go to **Container1**.
   - Upload a test blob (e.g., .txt or .jpg file).
   - This blob is automatically replicated to the secondary region.

2. **Validate RA-GRS Access (If Applicable)**  
   - If **RA-GRS** was selected, you can access data in the secondary region via the **Secondary endpoint** URL:
     - Format: `https://<accountname>-secondary.blob.core.windows.net`.

## Step 6: Monitor Replication and Configure Failover (If Necessary)
1. **Check Replication Status**  
   - In **Geo-replication**, monitor replication status for delays or issues.

2. **Initiate a Failover** (optional)  
   - For a prolonged outage in the primary region, initiate a **failover** to the secondary region.
   - In **Geo-replication** settings, select **Initiate account failover**.

---

By following these steps, you enable data replication across Azure regions using Azure Blob Storage, ensuring durability and accessibility. The replication options (GRS or RA-GRS) provide resilience and potential read access during regional disruptions.
