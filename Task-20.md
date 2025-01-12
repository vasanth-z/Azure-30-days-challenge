# Azure Table Storage with Logic App Integration

## Step 1: Create a New Resource Group
1. Navigate to the Azure Portal.
2. Create a **Resource Group** if you don't already have one.

---

## Step 2: Create a Storage Account
1. Search for **Storage Accounts** in the search bar.
2. Click on **Create** and enter the following details:
   - **Storage Account Name**: Provide a unique name.
   - **Performance**: Choose **Standard**.
   - **Region**: Select your preferred region.
   - **Access Tier**: Select **Hot**.
3. Click on **Review + Create**, then click **Create**.
4. Once deployment is complete, go to the resource group to view your Storage Account.

---

## Step 3: Create a Table in the Storage Account
1. In the **Storage Account Overview**, click on **Tables**.
2. Enter the following details:
   - **Table Name**: Provide a name for the table.
3. In the created table, you can add **entities** as required.

---

## Step 4: Create a Logic App
1. Search for **Logic Apps** in the search bar.
2. Click on **Create** and enter the following details:
   - **Logic App Name**: Provide a unique name.
   - **Subscription**: Select your subscription.
   - **Region**: Choose your preferred region.
3. Click on **Review + Create**, then click **Create**.
4. Once deployment is complete, go to the resource group to view your Logic App.

---

## Step 5: Configure the Logic App
1. Open the Logic App and navigate to the **Logic App Designer**.
2. Add a trigger to your Logic App:
   - Select **Schedule** to define when the Logic App should run.
   - Add an **Azure Table** action to connect to your created Azure Table Storage.
3. Configure any additional actions or logic as needed.

---

## Step 6: Test the Logic App
1. Go to the **Overview** page of the Logic App.
2. Click **Run** to test your Logic App workflow.
3. Verify that the Logic App processes the data in the Azure Table as expected.

---

This integration of Azure Table Storage and Logic Apps simplifies automated workflows, making it easy to manage and process table data. 😊
