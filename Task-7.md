# Step-by-Step Guide to Setting Up Azure Communication Services for Sending a Test Email

## Step 1: Set Up Azure Communication Services
1. **Log in to the Azure Portal**: Go to [https://portal.azure.com](https://portal.azure.com) and log in to your Azure account.

2. **Create a Resource**: In the Azure portal, select **Create a resource** at the top left.

3. **Search for "Communication Services"**: In the search box, type "Communication Services" and select it from the list.

4. **Set Up Communication Services**:
   - **Subscription**: Choose your Azure subscription.
   - **Resource Group**: Create a new resource group or use an existing one.
   - **Region**: Choose a region close to your users.
   - **Name**: Provide a unique name for your Communication Services resource.

5. **Review and Create**: Click **Review + create** to verify the information. Once confirmed, click **Create** to deploy the service.

## Step 2: Create an Email Identity and Verify It
1. **Navigate to Communication Services**: Once your Communication Services resource is created, go to it from your resource group or the dashboard.

2. **Set Up Email**: In the Communication Services resource page, find and select **Email** under the **Settings** menu.

3. Create a default "azure domain" and "resource".

4. **Create an Email Identity**:
   - **Sender Email Address**: Provide the email address you want to use as the sender. This email address should be within a verified domain for authentication and security reasons.
   - **Verify the Email**: Depending on your configuration, you may need to verify the email address. Azure will send a verification email to the address you provided, and you must follow the link in that email to complete verification.

## Step 3: Send a Test Email Using the Azure Portal or SDK
### Using the Azure Portal
1. **Test Email Setup**: Go back to the **Email** section in Communication Services.

2. **Compose Test Email**: You’ll find an option to send a test email within the portal interface. Enter the **recipient’s email address**, **subject**, and **message body** for your test email.

3. **Send**: Click **Send** to deliver the test email. You can check the recipient’s inbox to confirm it was successfully sent.
