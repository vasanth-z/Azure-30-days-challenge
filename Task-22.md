# Exploring Azure DevOps: A Hands-On Experience 🌟

Here’s a step-by-step guide to accomplish the project:

---

## 1. Repository Setup

### Steps:
1. **Create a New Repository in Azure DevOps**:
   - Go to **Azure DevOps Portal** → Select your project.
   - Navigate to **Repos** → Click **New Repository**.
   - Name the repository (e.g., `MyAppRepo`) and initialize it with a `.gitignore` file and README.

2. **Add Application Code**:
   - Clone the repository to your local machine:
     ```bash
     git clone <repository-url>
     ```
   - Create two branches:
     ```bash
     git checkout -b branch1-runtime-stack1
     git checkout -b branch2-runtime-stack2
     ```
   - Add application code for different runtime stacks in respective branches:
     ```bash
     git add .
     git commit -m "Add code for runtime stack"
     git push origin branch1-runtime-stack1
     git push origin branch2-runtime-stack2
     ```

---

## 2. Configure Azure App Services

### Steps:
1. **Create App Services for Each Runtime Stack**:
   - Go to the **Azure Portal** → Navigate to **App Services** → Click **Create**.
   - Fill in the details:
     - **Subscription**: Choose your subscription.
     - **Resource Group**: Create a new group or select an existing one.
     - **App Name**: Enter names like `app-service-runtime1` and `app-service-runtime2`.
     - **Runtime Stack**: Select the desired runtime stack (e.g., Node.js, Python, .NET).
   - Click **Review + Create** → **Create**.

2. **Note Down Deployment URLs**:
   - After creation, go to each App Service → Copy the default **URL** (e.g., `https://app-service-runtime1.azurewebsites.net`).

---

## 3. Build CI/CD Pipelines

### Pipeline 1: Branch 1 to App Service 1
1. Go to **Azure DevOps Portal** → Select **Pipelines** → Click **Create Pipeline**.
2. Choose **Classic Editor** → Select your repository → Continue.
3. Configure the pipeline:
   - **Pipeline Name**: `Pipeline-Branch1-AppService1`.
   - Add tasks for build and deployment:
     - **Build Task**:
       - Agent: Select the appropriate agent pool.
       - Task: Add build tasks (e.g., npm install/build for Node.js).
     - **Azure App Service Deploy Task**:
       - Azure Subscription: Authorize your Azure account.
       - App Service Name: Select `app-service-runtime1`.
       - Package/Directory: Specify the build artifact directory.
4. Save and Run the pipeline.

### Pipeline 2: Branch 2 to App Service 2
1. Repeat the above steps for branch 2:
   - **Pipeline Name**: `Pipeline-Branch2-AppService2`.
   - Azure App Service: Select `app-service-runtime2`.

---

## 4. Test the Deployment

### Steps:
1. Push changes to the respective branches:
   ```bash
   git add .
   git commit -m "Test deployment"
   git push origin branch1-runtime-stack1
