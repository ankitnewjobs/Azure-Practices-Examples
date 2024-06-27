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
