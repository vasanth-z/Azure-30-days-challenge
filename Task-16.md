# Steps for Immutable Backup for Ransomware Protection in Azure Recovery Services Vault

## Objective:
Protect backup data against ransomware or accidental/malicious deletion by enabling **immutable backups**.

---

## Prerequisites:
1. A **Recovery Services Vault** is already created in your Azure subscription.
2. **Backups are configured** for at least one resource (e.g., Azure VM, SQL database, or Azure File Shares).
3. The user has **Contributor** or **Backup Contributor** permissions for the Recovery Services Vault.

---

## Step 1: Enable Soft Delete
Soft delete ensures deleted backup data is retained for 14 days.

1. Open the **Azure Portal**.
2. Navigate to your **Recovery Services Vault**.
3. Under the **Settings** section, click **Properties**.
4. Locate the **Soft Delete** option.
5. Ensure that **Soft Delete** is enabled (it is enabled by default).

---

## Step 2: Configure Immutable Backup Policies
1. Go to the **Recovery Services Vault**.
2. Under **Settings**, click **Backup Policies**.
3. Select an existing **Backup Policy** or create a new one:
   - Set the **Backup Frequency** and **Retention Periods** (daily, weekly, monthly, or yearly backups).
   - For long-term data security, ensure the retention period is sufficiently long.
4. Save the policy and associate it with the resources you want to protect (e.g., VMs or file shares).

---

## Step 3: Test Deletion Prevention
1. Navigate to the **Backup Items** blade in the Recovery Services Vault.
2. Select a resource protected by the immutable policy (e.g., Azure VM or File Share).
3. Attempt to delete the backup or resource:
   - The deletion will be blocked or retained in a **Soft Deleted** state for 14 days.

---

## Step 4: Restore Backup from Soft Deleted State
1. After attempting deletion:
   - Go to the **Backup Items** section.
   - Select the backup marked as **Soft Deleted**.
2. Click **Undelete** to restore the backup item.
3. Restore the resource from a recovery point:
   - Use the **Restore VM**, **Restore Database**, or equivalent option based on the workload.

---

## Step 5: Enable Alerts for Backup Protection
1. Open the **Monitor** service in the Azure Portal.
2. Create alert rules to track:
   - Backup deletion attempts.
   - Failed or completed backup jobs.
3. Configure action groups to send notifications via email, SMS, or webhook.

---

## Step 6: Validate Immutable Protection
1. Attempt the following actions to validate immutability:
   - Modify or delete the backup policy (should be restricted).
   - Permanently delete backups or the Recovery Services Vault (should be blocked).
2. Confirm that backups remain secure and immutable during the defined retention period.

---

## Outcome:
- Backup data is protected from accidental or malicious deletion.
- Immutable policies ensure compliance with security standards and regulatory requirements.
- Backups remain accessible for recovery, even after deletion attempts.

---

## Key Considerations:
- **Immutability cannot be reversed:** Once enabled, backups and policies cannot be changed until the retention period expires.
- Use immutability for critical data, especially in highly regulated industries or ransomware-prone environments.
