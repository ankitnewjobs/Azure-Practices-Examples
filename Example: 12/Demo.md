# Implement Traffic Management

# Lab introduction

- In this lab, you learn how to configure and test a public Load Balancer and an Application Gateway.

# Lab scenario

- Your organization has a public website. You need to load and balance incoming public requests across different virtual machines. You also need to provide images and videos from different virtual machines. You plan on implementing an Azure Load Balancer and an Azure Application Gateway. All resources are in the same region.

# Job skills

- Task 1: Use a template to provision an infrastructure.

- Task 2: Configure an Azure Load Balancer.

- Task 3: Configure an Azure Application Gateway.

# Link to the Required template and parameters file:

- https://github.com/ankitnewjobs/Azure-Example-Trafffic-Management-Files

# Task 1: Use a template to provision an infrastructure

- In this task, you will use a template to deploy one virtual network, one network security group, and two virtual machines.

1. Download the \Azure-Example-Trafffic-Management-Files  lab files (template and parameters).

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9d3489f2-8d87-4e6c-9061-9b6036fe2022)

2. Sign in to the Azure portal - https://portal.azure.com.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0bb77bd1-e4e8-41a2-b028-8cc7153f9b2f)

3. Search for and select Deploy a custom template.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/42a01d61-b475-441c-ba97-fe489852a0f3)

4. On the custom deployment page, select Build your template in the editor.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/8f2f2712-61c0-428f-805f-5398da9a9eaf)

5. On the edit template page, select Load file.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e8b49031-cafa-4cd9-8dc4-92abcfb3a814)

6. Locate and select the template.json file and select Open.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/723da3cb-3d89-47d8-9df0-4a3460cd475c)

7. Select Save.

8. Select Edit parameters and load the \Allfiles\Lab06\az104-06-vms-parameters.json file.

9. Select Save.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2db60a9f-42cb-42cc-93e4-2e5d182192b0)

10. Use the following information to complete the fields on the custom deployment page, leaving all other fields with the default value.

- Setting	Value

- Subscription	your Azure subscription

- Resource group	az104-rg6 (If necessary, select Create new)

- Password	Provide a secure password

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/058c431b-7d97-4b11-bf17-616cfe32d59b)

11. Select Review + Create and then select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a47f6528-53f8-43f6-a8c1-ca09c3896734)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/7cfed1be-b937-4aa4-ae3a-7f5451ddb99c)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/db5d7ee4-9cd0-4f3f-8b46-0c85d6023a0d)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ae1d38de-3a94-44f7-b269-e7ca446d2cb2)




