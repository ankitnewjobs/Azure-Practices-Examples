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

10. Save your changes.

11. Use the following information to complete the custom deployment fields, leaving all other fields with their default values:

- Setting	Value

- Subscription	Your Azure subscription

- Resource group	az104-rg-region1 (If necessary, select Create new)

- Region	East US

- Username	local admin

- Password	Provide a complex password

- Select Review + Create, then select Create.

