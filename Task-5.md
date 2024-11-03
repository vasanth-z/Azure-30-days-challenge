# Managing Identities, Permissions, and Access Control using Azure CLI

## Overview
This guide provides an overview of how to manage identities, permissions, and access control in Azure Active Directory (AAD), with a hands-on task demonstrating how to:
1. Create a user with limited permissions.
2. Generate access keys and assign roles.
3. Access a Blob container using Azure CLI.

---

## Hands-On Task

### Step 1: Create a User in Azure Active Directory with Limited Permissions

1. **Navigate to AAD in the Azure Portal**:
   - Go to **Azure Active Directory** in the Azure portal.
   
2. **Create a New User**:
   - Select **Users** > **New user**.
   - Choose **Create user**.
   - Fill out the **Username**, **Name**, and other required fields.
   - Set the **User Role** to **User**.
   - Select **Create** to create the user.

---

### Step 2: Assign Roles and Generate Access Keys for Blob Storage

1. **Assign the Storage Blob Data Reader Role to the User**:
   - In the AAD page, go to **Users**, select the newly created user, then select **Assigned roles**.
   - Click on **Add assignment**.
   - Search for and select **Storage Blob Data Reader** (for read-only access to Blob storage).
   - Assign this role to the user.

2. **Generate Access Keys for the Storage Account**:
   - In the Azure portal, navigate to **Storage accounts**.
   - Select the storage account you want to grant access to.
   - Go to **Access keys** under **Security+networking**.
   - Copy the **Storage account name** and one of the access keys (Key1 or Key2).

---

### Step 3: Use Azure CLI to Access the Blob Container with the User’s Keys

1. **Log in to Azure CLI**:
   - Open a terminal or command prompt and use the following command to log in:
     ```bash
     az 
     ```

2. **List All Containers in the Storage Account**:
   - To list all containers in the storage account, run:
     ```bash
     az storage container list --account-name <your_storage_account_name> --account-key <your_access_key> --output table

     ```

4. **Create a Container**
   -To create a container, use:
     ```bash
     az storage container create --new <container name> --account-name "storageaccountname" --account-key "paste the key copied"
     ```
   - Replace `<container_name>` with the name of your container name and enter your storage account name and enter the access key you copied.

5. **Upload a File to the Blob Container**:
   - To upload a file to the container, use:
   - Directly upload the file in Azure CLI which you want to upload and run the command:
   - 
     ```bash
    az storage blob upload --container-name <container_name> --file <path_to_file> --name <file_name> --account-name "storageaccountname" --account-key "accesskeycopied"
     ```
   - Replace `<container_name>`, `<path_to_file>`, and `<blob_name>` with your container name, file path, and desired blob name, respectively.

6. **Download a Blob from the Container**:
   - To download a blob from the container, use:
     ```bash
     az storage blob download --container-name <container_name> --name <blob_name> --file <path_to_save_file>
     ```
   - Replace `<container_name>`, `<blob_name>`, and `<path_to_save_file>` with your container name, blob name, and file save path, respectively.

---

This guide walks you through creating a user with limited permissions, assigning roles, and accessing a Blob container with Azure CLI.
