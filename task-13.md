# Azure Functions Hands-On Task: Creating a Serverless Function

## **Overview**
Azure Functions is a serverless compute service that enables you to run code without managing infrastructure. In this task, you'll create an Azure Function using Python (or C#), configure a Blob Storage trigger, and test it by uploading a file to a Blob container.

---

## **Steps to Complete the Task**

### **Step 1: Create an Azure Function App**
1. **Log in to the Azure Portal**:
   - Navigate to [Azure Portal](https://portal.azure.com).

2. **Create a Function App**:
   - Search for **Function App** in the search bar.
   - Click **+ Create**.
   - Fill in the required details:
     - **Subscription**: Select your subscription.
     - **Resource Group**: Create a new or select an existing one.
     - **Function App Name**: Provide a unique name.
     - **Runtime Stack**: Choose **Python** (or **.NET** for C#).
     - **Region**: Select the closest location.
   - Click **Review + create** and then **Create**.

---

### **Step 2: Create a Blob Storage Account**
1. **Search for Storage Accounts**:
   - In the Azure Portal, search for **Storage Accounts**.
   - Click **+ Create**.

2. **Set up the Storage Account**:
   - Fill in the required fields:
     - **Subscription** and **Resource Group**: Match the Function App settings.
     - **Storage Account Name**: Provide a unique name.
     - **Performance**: Standard.
     - **Redundancy**: Locally-redundant storage (LRS) is sufficient for this task.
   - Click **Review + create** and then **Create**.

---

### **Step 3: Create a Blob Container**
1. **Navigate to the Storage Account**:
   - Open the newly created storage account in the Azure portal.

2. **Create a Blob Container**:
   - Go to the **Containers** section.
   - Click **+ Container**.
   - Name it (e.g., `input-files`) and set **Public access level** to **Private**.
   - Click **Create**.

---

### **Step 4: Create an Azure Function with a Blob Trigger**
1. **Navigate to the Function App**:
   - Open the Function App you created.

2. **Add a New Function**:
   - Click **Functions** in the left-hand menu, then click **+ Add**.
   - Choose the **Blob Trigger** template.

3. **Configure the Blob Trigger**:
   - Provide a name for the function (e.g., `ProcessBlob`).
   - Select the storage account created earlier.
   - Provide the path to the Blob container (e.g., `input-files/{name}`).
   - Click **Create**.

4. **Edit the Function Code**:
   - If using **Python**, use the following example:
     ```python
     import logging

     def main(myblob: bytes, name: str):
         logging.info(f"Blob trigger function processed blob \n"
                      f"Name: {name} \n"
                      f"Size: {len(myblob)} bytes")
     ```
   - If using **C#**, the default template is sufficient for this task.

---

### **Step 5: Test the Function**
1. **Upload a File to the Blob Container**:
   - Use Azure Portal or Azure Storage Explorer to upload a file to the `input-files` container.
   - For example, upload a text file (`sample.txt`).

2. **Verify the Function Execution**:
   - Navigate to the **Monitor** tab of your function in the Azure portal.
   - Check the logs for the processed file details (name and size).

3. **Optional: Debug Locally**:
   - Use Azure Functions Core Tools to run and debug the function locally if needed.

---

## **Summary**
1. **Created a Function App in Azure.**
2. **Configured a Blob Storage account and container.**
3. **Set up an Azure Function with a Blob Trigger.**
4. **Uploaded a file to test the serverless function.**
