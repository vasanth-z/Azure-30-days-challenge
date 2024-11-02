# Setting Up Azure Monitor for Virtual Machine Monitoring

This guide walks you through setting up monitoring for an Azure Virtual Machine (VM) using Azure Monitor, creating a CPU usage alert, and triggering the alert.

## Prerequisites
- **Azure VM**: Ensure you have an Azure Virtual Machine created and running.
- **Azure CLI or Azure Portal**: You can follow these steps in either the Azure Portal or the Azure CLI.

---

## Step 1: Set Up Monitoring for the VM

### Enable Azure Monitor for the VM
1. In the **Azure Portal**, go to **Virtual Machines** and select your VM.
2. Under **Monitoring**, select **Insights**.
3. Click **Enable** to turn on Azure Monitor for the VM. This allows Azure Monitor to collect data about the VM's performance, including CPU, memory, and disk usage.

### Install the Dependency Agent (if needed)
- Azure Monitor may require you to install the **Dependency Agent** on the VM to collect additional metrics.
- Follow the prompts to install it directly from the **Insights** tab.

---

## Step 2: Create an Alert Based on CPU Usage

### Navigate to Azure Monitor
1. In the **Azure Portal**, search for **Azure Monitor** and open it.

### Create an Alert Rule
1. Under **Alerts**, select **+ Create > Alert rule**.
2. In **Scope**, select the VM you want to monitor.
3. In **Condition**, choose **Percentage CPU** and set the threshold value for CPU usage (e.g., 80%) to trigger the alert.
4. In **Actions**, create an **Action Group** if you don't have one already. Configure it to send email notifications or trigger other actions when the alert is activated.
5. **Alert Details**: Provide a name and description for the alert rule, then review and create the alert rule.

---

## Step 3: Trigger the Alert by Running a CPU-Intensive Process

### Connect to Your VM
- Use **SSH** or **RDP** to connect to your VM, depending on its OS.
- Use "SSH" for Linux and Ubuntu and "RDP" for Windows.
- After connecting follow these commands:

### Run a CPU-Intensive Process
- **On a Linux VM**:
  ```bash
  sudo apt update && sudo apt install -y stress
  stress --cpu 2 --timeout 300
  ```

  **On a Windows powershell**:
  ```powershell
  while ($true) { Start-Process notepad.exe }
  ```
  - After running this command the notepad opens mirror times and this makes the CPU to trigger.
  - To stop the process open "Task manager" and click on notepad "endtask".
  - To stop in powershell use this command:
    ```powershell
    Stop-Process -Name notepad -Force
    ```

 
## Step 4: Verify the Alert

### Monitor Alerts
1. Go back to **Azure Monitor** in the portal.
2. Under **Alerts**, you should see the alert status change to **Fired** if the CPU threshold is exceeded.

### Receive Notifications (if configured)
- Check for email notifications or any other action specified in the action group.

Once the alert is triggered and verified, you can stop the CPU-intensive process on the VM. This setup allows you to keep an eye on critical resources and receive notifications promptly when thresholds are breached.

    


