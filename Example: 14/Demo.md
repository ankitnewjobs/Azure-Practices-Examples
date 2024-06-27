# Implement Data Protection

# Lab introduction

- In this lab, you learn about backup and recovery of Azure virtual machines. You learn to create a Recovery Service vault and a backup policy for Azure virtual machines. You learn about disaster recovery with Azure Site Recovery.

# Lab scenario

- Your organization is evaluating how to backup and restore Azure virtual machines from accidental or malicious data loss. Additionally, the organization wants to explore using Azure Site Recovery for disaster recovery scenarios.

# Job skills

- Task 1: Use a template to provision an infrastructure.

- Task 2: Create and configure a Recovery Services vault.

- Task 3: Configure Azure virtual machine-level backup.

- Task 4: Monitor Azure Backup.

- Task 5: Enable virtual machine replication.

# Architecture diagram

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d60ead69-25bf-4ad1-a8c5-9d3dab3f0a08)

# Task 1: Use a template to provision an infrastructure

- In this task, you will use a template to deploy a virtual machine. The virtual machine will be used to test different backup scenarios.

1. Download the (https://github.com/ankitnewjobs/Azure-Practices-Examples/edit/main/Example%3A%2014/Demo.md) lab files.

2. Sign in to the Azure portal - https://portal.azure.com.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ba3d0d5d-1d2b-47be-98e7-670aa4f1333c)

3. Search for and select Deploy a custom template.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/fa9315d4-214d-4627-8b4f-1e1c633d5fd6)

4. On the custom deployment page, select Build your template in the editor.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d38373c6-6fb7-4eed-8007-8e9ef7cda22a)

5. On the edit template page, select Load file.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6c992126-98f8-45b7-97ee-4d1cc4a048f7)

6. Locate and select the template.json file and select Open.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/73fcb512-b45a-4b81-bb01-c18220728e66)

7. Save your changes.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/18488223-3d2b-4786-9b94-221d96cafd81)

8. Select Edit parameters and then Load file.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1989498a-d16a-4a1d-b5a4-7f5084affc7f)

9. Load and select the parameters.json file.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/cf53336f-6b02-4f6b-a806-daa3c89137ae)

10. Save your changes.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/fd471657-897c-4f65-9ac8-4b109d90f1eb)

11. Use the following information to complete the custom deployment fields, leaving all other fields with their default values:

- Setting	Value

- Subscription	Your Azure subscription

- Resource group	az104-rg-region1 (If necessary, select Create new)

- Region	East US

- Username	as per your choice

- Password	Provide a complex password

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2b34ad27-d6f0-49ad-80d7-22d6d354d40b)

12. Select Review + Create, then select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4aececc9-bb4b-4b3b-9ff7-aebab7867e7b)

- Vnet:

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/18d12d01-ec3d-4ed7-925b-0f7b1db308e1)

- VM Disk:

  ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e73b17ed-2a49-4d5f-b1d5-5c5ff876ac0e)

- VM:

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1c367a92-9497-4e58-9bfb-60ecfbffb8ae)

- NSG:

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/997f972a-b33c-4bf9-8676-2fb3ae7c1ed6)

- Public IP:

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/fb294d63-4d92-4364-856e-c56e2c624b82)

- Network Interference:

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a9cfb9fc-0159-4bde-9f4a-cfc162395caa)

# Task 2: Create and configure a Recovery Services vault

- In this task, you will create a Recovery Services vault. A Recovery Services vault provides storage for the virtual machine data.

1. In the Azure portal, search for and select Recovery Services vaults and, on the Recovery Services vaults blade, click + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/7c0358ed-47c6-4e2f-87bf-b7a435eac98e)

2. On the Create Recovery Services vault blade, specify the following settings:

- Settings	Value

- Subscription	the name of your Azure subscription

- Resource group	az104-rg-region1

- Vault Name	az104-rsv-region1

- Region	East US

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e8cd299c-1838-4c5c-9b8c-f17fded75ff7)

3. Click Review + Create, ensure that the validation passes, and then click Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1e688410-5544-4aa7-a656-32ddb3c8a78c)

4. When the deployment is completed, click Go to Resource.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/44b61c28-8446-4456-b762-5b4a5fa10659)

5. In the Settings section, click Properties.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/54e9dd78-131f-4af7-8138-9b6f18f0f217)

6. Select the Update link under the Backup Configuration label.

7. On the Backup Configuration blade, review the choices for Storage replication type. Leave the default setting of Geo-redundant in place and close the blade.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/75479e57-ab4c-43de-be4a-306a837e8875)

8. Select the Update link under Security Settings > Soft Delete and security settings label.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/959b90ca-9772-41c2-b4e4-2111c2151250)

9. On the Security Settings blade, note that Soft Delete (For workload running in Azure) is Enabled. Notice the soft delete retention period is 14 days.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e7fc1d66-68a0-492a-b36f-ba1114da289c)

# Task 3: Configure Azure virtual machine-level backup

- In this task, you will implement Azure virtual-machine level backup. As part of a VM backup, you will need to define the backup and retention policy that applies to the backup. Different VMs can have different backup and retention policies assigned to them.

1. On the Recovery Services vault blade, click Overview, then click + Backup.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/88630dcd-9108-40ab-8826-786eadd87121)

2. On the Backup Goal blade, specify the following settings:

- Settings	Value

- Where is your workload running?	Azure (notice your other options)

- What do you want to back up?	Virtual machine (notice your other options

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f19f6737-726d-4559-b79e-d90983233d0e)

3. Select Backup.

4. Notice there a two Policy subtypes: Enhanced and Standard. Review the choices and select Standard.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4deca811-1f59-41ed-9e3c-6a8c97761ef3)

5. In Backup policy, select Create a new policy.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0f355d2f-3c43-4545-9c86-7672f32ce030)

6. Define a new backup policy with the following settings (leave others with their default values):

- Setting	Value

- Policy name	az104-backup

- Frequency	Daily

- Time	12:00 AM

- Timezone	the name of your local time zone

- Retain instant recovery snapshot(s) for	2 Days(s)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/beca0d04-8702-4aff-baed-0997c55be298)

7. Click OK to create the policy and then, in the Virtual Machines section, select Add.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/7917e122-b67d-469c-8f47-6212005d1b22)

8. On the Select virtual machines blade, select az-104-10-vm0, click OK, and then back on the Backup blade, click Enable backup.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/48ae7b39-a2f4-418c-a8c2-5b986edcea94)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/985ee992-2fda-4be8-8797-b1e3f19de956)

9. In the Protected items section, click Backup items, and then click the Azure virtual machine entry.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/dbbe91ea-ca18-48d4-b23e-2823bf092fae)

10. Select the View Details link for az104-10-vm0, and review the values of the Backup Pre-Check and Last Backup Status entries.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3de189ea-a0ea-4772-a9a5-b64480597b82)

11. Select Backup now, accept the default value in the Retain Backup Till drop-down list, and click OK.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/dfda6787-faec-4ab7-a925-88079fa1bcc9)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9abe57c9-7c74-4dac-addb-ed3fa480f9d6)

# Task 4: Monitor Azure Backup

- In this task, you will deploy an Azure storage account. Then you will configure the vault to send the logs and metrics to the storage account. This repository can then be used with Log Analytics or other third-party monitoring solutions.

1. From the Azure portal, search for and select Storage accounts.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/60c8763d-f639-4d58-ad84-361e09892224)

2. On the Storage accounts page, select Create.

3. Use the following information to define the storage account, then select Review.

- Settings	Value

- Subscription	Your subscription

- Resource group	az104-rg-region1

- Storage account name	Provide a globally unique name

- Region	East US
  
- ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2cefc7e2-4693-4de8-9ce2-08a5e8ac1c28)

 4. On the Review tab, select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/504c3651-8a66-41c1-8bce-d5489eae9090)

5. Search and select your Recovery Services vault.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/71aae854-0c00-4085-ab53-f7c36fc40ead)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/66a26320-ad41-4ede-8dd2-6c5a5c271c54)

6. Select Diagnostic Settings and then select Add diagnostic setting.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a9c14e2d-fd35-47e7-bacd-13faa79fa7f1)

7. Name the setting Logs and Metrics to storage.

8. Place a checkmark next to the following log and metric categories:


**- Azure Backup Reporting Data**
**- Add-on Azure Backup Job Data**
**- Add-on Azure Backup Alert Data**
**- Azure Site Recovery Jobs**
**- Azure Site Recovery Events**
**- Health****

9. In the Destination details, place a checkmark next to Archive to a storage account.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d6a8bb4d-c4c4-440b-b7f0-e9c9501cd619)

10. In the Storage account drop-down field, select the storage account that you deployed earlier in this task.

11. Select Save.

12. Return to your Recovery Services vault, in the Monitoring blade select Backup jobs.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1da20c81-70cc-489e-9ef2-31d8fcdacfc0)

13. Locate the backup operation for the az104-10-vm0 virtual machine.

14. Review the details of the backup job

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f48bf85d-950c-4e07-9b91-faad49fc4c0a)
