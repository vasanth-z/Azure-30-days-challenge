# Azure Blob Storage Static Website Hosting

This guide outlines the steps to host a static website using Azure Blob Storage's static website hosting feature. Additionally, it covers enabling versioning to manage different versions and roll back if needed.

## Objectives

- **Primary**: Host a static website on Azure Blob Storage.
- **Secondary**: Implement versioning on the storage account to track different versions of the website.

---

## Prerequisites

- [Azure Portal](https://portal.azure.com) access and permissions to create storage accounts.

---

## Steps

### 1. Set Up the Azure Storage Account

1. **Login to Azure Portal**  
   Go to [Azure Portal](https://portal.azure.com) and log in with your credentials.
   
2. **Create a Storage Account**
   - In the Azure Portal, select **Create a resource** > **Storage** > **Storage account**.
   - Fill in the required details:
     - **Subscription**: Choose your subscription.
     - **Resource group**: Select an existing one or create a new one.
     - **Storage account name**: Provide a unique name.
     - **Region**: Choose a location near you.
     - **Performance**: Select *Standard*.
     - **Redundancy**: Choose any redundancy option.
   - Click **Review + Create** and then **Create**.

---

### 2. Enable Static Website Hosting

1. Go to your storage account in the Azure Portal.
2. Under **Data management**, select **Static website**.
3. Enable static website hosting by selecting **Enabled**.
4. Set the **Index document name** (e.g., `index.html`) and **Error document path** (optional, e.g., `404.html`).
5. Click **Save** to activate the website. Note the primary endpoint URL provided by Azure for accessing your website.

---

### 3. Upload Website Files

1. Go to the **Containers** section of your storage account.
2. Locate the `$web` container (automatically created when static website hosting is enabled).
3. Click on **Upload** to add all website files (e.g., `index.html`, `styles.css`, images).
   - Ensure **public access level** allows files to be viewed publicly.
4. Once uploaded, use the endpoint URL to access your website.

---

### 4. Enable Versioning on the Storage Account

1. In your storage account, navigate to **Data protection** under **Data management**.
2. Locate **Blob versioning** and click on **Enable**.
3. Click **Save**.  
   - Versioning automatically tracks changes to files in the `$web` container, allowing for version management.

---

### 5. Manage Website Versions

1. **Update Website Files**  
   When you update any file in the `$web` container, a new version is created.
   
2. **Roll Back to a Previous Version**:
   - Go to the `$web` container.
   - Right-click the file you want to revert and select **Manage versions**.
   - Choose a specific version and select **Restore** to roll back or download it for editing.

---

Your static website is now hosted on Azure Blob Storage with versioning enabled for easy rollback and version control.

