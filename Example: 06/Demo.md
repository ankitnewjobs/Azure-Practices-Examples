# Manage Azure resources by using Azure Resource Manager Templates

# Lab introduction

In this lab, you learn how to automate resource deployments. You learn about Azure Resource Manager templates and Bicep templates. You learn about the different ways of deploying the templates.

# Lab scenario

Your team wants to look at ways to automate and simplify resource deployments. Your organization is looking for ways to reduce administrative overhead, reduce human error, and increase consistency.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b29ea570-3984-42c9-9ced-524cd67583b6)

# Task 1: Create an Azure Resource Manager template

- In this task, we will create a managed disk in the Azure portal. Managed disks are storage designed to be used with virtual machines. Once the disk is deployed you will export a template you can use in other deployments.

1. Sign in to the Azure portal - https://portal.azure.com.

2. Search for and select Disks.

3. On the Disks page, select Create.

4. On the Create a managed disk page, configure the disk and then select Ok.

- Setting	Value
  
Subscription	your subscription
Resource Group	az104-rg3 (If necessary, select Create new.)
Disk name	az104-disk1
Region	East US
Availability zone	No infrastructure redundancy is required
Source type	None
Performance	Standard HDD (change size)
Size	32 Gib

5. Click Review + Create then select Create.

6. Monitor the notifications (upper right) and after the deployment select Go to the resource.

7. In the Automation blade, select Export template.

8. Take a minute to review the Template and Parameters files.

9. Click Download and save the templates to the local drive. This creates a compressed zipped file.

10. Use File Explorer to extract the content of the downloaded file into the Downloads folder on your computer. Notice there are two JSON files (template and parameters).
