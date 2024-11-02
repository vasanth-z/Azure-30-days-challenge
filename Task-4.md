## Set up monitoring for a Virtual Machine (VM) using Azure Monitor, create a CPU usage alert, and trigger the alert.


### Overview
Azure Monitor is a comprehensive solution to monitor and manage the performance and availability of your resources in Azure. It helps you gain insights into your applications, infrastructure, and network by collecting, analyzing, and acting on telemetry data.

### Hands-On Task
Follow these steps to set up and test monitoring for a Virtual Machine (VM) using Azure Monitor:

#### 1. Set up Monitoring for a Virtual Machine
   - Go to the **Azure Portal**.
   - Navigate to **Virtual Machines** and select the VM you want to monitor.
   - Under the **Monitoring** section, select **Insights** to enable monitoring.
   - Confirm that **CPU**, **Memory**, **Disk**, and **Network** metrics are being collected.

#### 2. Create an Alert Based on CPU Usage
   - In the **Azure Portal**, go to **Monitor** > **Alerts** > **Create** > **Alert rule**.
   - Under **Scope**, select your VM.
   - For **Condition**, choose **Signal name** as `Percentage CPU`.
   - Set a threshold (e.g., 80%) to trigger an alert when CPU usage exceeds this level.
   - Configure **Action Groups** to define what action to take when the alert triggers (e.g., email notification).
   - Click **Create alert rule**.

#### 3. Trigger the Alert by Running a CPU-Intensive Process on the VM
   - **Connect to the VM** using RDP (Windows) or SSH (Linux).
   - Open **PowerShell** or **Command Prompt** (Windows) or the **terminal** (Linux).
   - Run a CPU-intensive command to increase CPU usage:
     - **Windows**: Open multiple instances of `notepad.exe` in a loop with PowerShell:
       ```powershell
       for ($i = 1; $i -le 100; $i++) { Start-Process notepad.exe }
       ```
     - **Linux**: Run a CPU-intensive command like `stress` if installed:
       ```bash
       sudo apt install stress -y   # Install if not already installed
       stress --cpu 4 --timeout 60  # Runs CPU load for 60 seconds
       ```
   - Monitor Azure Monitor to confirm that the alert is triggered based on the increased CPU usage.

This hands-on task demonstrates how to monitor a VM, create alerts, and simulate a CPU spike to test alerting functionality in Azure Monitor.
