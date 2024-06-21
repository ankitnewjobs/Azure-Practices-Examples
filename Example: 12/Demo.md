# Implement Traffic Management

# Lab introduction

- In this lab, you learn how to configure and test a public Load Balancer and an Application Gateway.

# Lab scenario

- Your organization has a public website. You need to load and balance incoming public requests across different virtual machines. You also need to provide images and videos from different virtual machines. You plan on implementing an Azure Load Balancer and an Azure Application Gateway. All resources are in the same region.

# Job skills

- Task 1: Use a template to provision an infrastructure.

- Task 2: Configure an Azure Load Balancer.

- Task 3: Configure an Azure Application Gateway.

# Task 1: Use a template to provision an infrastructure

- In this task, you will use a template to deploy one virtual network, one network security group, and two virtual machines.

1. Download the \Allfiles\Lab06 lab files (template and parameters).

2. Sign in to the Azure portal - https://portal.azure.com.

3. Search for and select Deploy a custom template.

4. On the custom deployment page, select Build your template in the editor.

5. On the edit template page, select Load file.

6. Locate and select the \Allfiles\Lab06\az104-06-vms-template.json file and select Open.

7. Select Save.

8. Select Edit parameters and load the \Allfiles\Lab06\az104-06-vms-parameters.json file.

9. Select Save.

10. Use the following information to complete the fields on the custom deployment page, leaving all other fields with the default value.

- Setting	Value

- Subscription	your Azure subscription

- Resource group	az104-rg6 (If necessary, select Create new)

- Password	Provide a secure password

11. Select Review + Create and then select Create.



