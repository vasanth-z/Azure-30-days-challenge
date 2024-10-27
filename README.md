 # Azure 30 Days Challenge

## Objective
- Host a static website using Azure Blob Storage’s static website hosting feature.
- Implement versioning on the storage account to manage different versions of the website and roll back if needed.

---

### 1. Set Up the Azure Storage Account

1. **Login to Azure Portal**: Go to [https://portal.azure.com](https://portal.azure.com) and log in.

2. **Create a Storage Account**:
   - Go to **Create a resource** > **Storage** > **Storage account**.
   - Fill in the details:
     - **Subscription**: Choose your subscription.
     - **Resource group**: Select an existing one or create a new one.
     - **Storage account name**: Provide a unique name.
     - **Region**: Choose a preferred location.
     - **Performance**: Select *Standard*.
     - **Redundancy**: Choose any redundancy option.
   - Click **Review + Create** and then **Create**.

---

### 2. Enable Static Website Hosting

1. Go to your storage account in the Azure Portal.

2. Under **Data management**, select **Static website**.

3. Click **Enabled** to activate static website hosting.

4. Provide the **Index document name** (e.g., `index.html`).

5. (Optional) Specify the **Error document path** (e.g., `404.html`).

6. Click **Save**. Azure will generate a primary endpoint URL for your website.

   - **Note**: Copy this URL; it will be used to access your website.

---

### 3. Upload Your Website Files to the Storage Account

1. Go to the **Containers** section of your storage account.

2. Select the `$web` container (created automatically when static website hosting is enabled).

3. Click on **Upload** to upload your website files (e.g., `index.html`, `styles.css`, images, etc.).

   - **Public Access**: Ensure the files are accessible to the public.

4. After uploading, you can access the website using the endpoint URL you saved earlier.

---

### 4. Enable Versioning on the Storage Account

1. In your storage account, go to **Data protection** under **Data management**.

2. Locate **Blob versioning** and click **Enable**.

3. Click **Save**.

   - **Note**: Versioning ensures that any updates to files in the `$web` container create a new version, allowing for version management.

---

### 5. Update the Website and Manage Versions

1. When you update any file in the `$web` container (e.g., modify `index.html`), a new version is created automatically.

2. **To Roll Back to a Previous Version**:
   - Go to the **$web** container.
   - Right-click on the file you want to revert.
   - Select **Manage versions** to view all available versions.
   - Choose the desired version and either **Restore** it or download it for editing.

3. Once restored, the endpoint URL will reflect the chosen version.

---

Your static website is now hosted on Azure Blob Storage with version control, allowing for efficient management and rollbacks.
