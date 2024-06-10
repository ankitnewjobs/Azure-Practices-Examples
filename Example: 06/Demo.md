# Manage Azure resources by using Azure Resource Manager Templates

# Lab introduction

In this lab, you learn how to automate resource deployments. You learn about Azure Resource Manager templates and Bicep templates. You learn about the different ways of deploying the templates.

# Lab scenario

Your team wants to look at ways to automate and simplify resource deployments. Your organization is looking for ways to reduce administrative overhead, reduce human error, and increase consistency.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/b29ea570-3984-42c9-9ced-524cd67583b6)

# Task 1: Create an Azure Resource Manager template

- In this task, we will create a managed disk in the Azure portal. Managed disks are storage designed to be used with virtual machines. Once the disk is deployed you will export a template you can use in other deployments.

1. Sign in to the Azure portal - https://portal.azure.com.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e2d4f783-a84c-4c0e-a299-6b912ec10a69)

2. Search for and select Disks.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/74bf8aab-d256-41a3-9fde-874b58630f65)

3. On the Disks page, select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/9555e3b0-0749-4426-bada-14dc1b6432db)

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

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/ffee5d35-d6d2-48d0-b0ff-15cb2f39c73c)

5. Click Review + Create then select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f7ee7439-5993-4ddb-80d4-644d54f3fdb4)

6. Monitor the notifications (upper right) and after the deployment select Go to the resource.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c0da90f4-8231-4d5e-8030-e7f7cf97ddbc)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c33c7254-e5e2-40b1-ae70-4cc4644157c3)

7. In the Automation blade, select Export template.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/3b649d7e-c775-4679-852b-cf40311c0f9e)

- Downloading the file:

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/40fefcd8-5173-4f9c-b311-422c486e9aa6)

8. Take a minute to review the Template and Parameters files.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/e6f0da83-94d8-41e2-9a96-ceccb8b73e6a)

9. Click Download and save the templates to the local drive. This creates a compressed zipped file.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/70ec6148-eb35-40a3-abcb-aac9547cb872)

10. Use File Explorer to extract the content of the downloaded file into the Downloads folder on your computer. Notice there are two JSON files (template and parameters).

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/adda1e45-ba19-40e9-8e10-1525c1b3e29f)

# Task 2: Edit an Azure Resource Manager template and then redeploy the template

- In this task, you use the downloaded template to deploy a new managed disk. This task outlines how to quickly and easily repeat deployments.

1. In the Azure portal, search for and select Deploy a custom template.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/14ccdb97-1717-4fbd-8898-7ad6e1cfa0e7)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/4e507123-332c-47bb-bdce-533c346b6cd7)

2. On the Custom deployment blade, notice there is the ability to use a Quickstart template. There are many built-in templates as shown in the drop-down menu.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a828de74-a3e7-4892-bf0f-6484d10dd776)

3. Instead of using Quickstart, select Build your template in the editor.

4. On the Edit template blade, click Load file and upload the template.json file you downloaded to the local disk.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/817a3475-1a81-4cc7-b85e-66276dd797bc)

5. Within the editor pane, make these changes.

- Change disks_az104_disk1_name to disk_name (two places to change)
- Change az104-disk1 to az104-disk2 (one place to change)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c5765252-3487-430f-9e6d-58dabe907d71)

6. Notice this is a Standard disk. The location is east us. The disk size is 32GB.

7. Save your changes.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d988c7b1-b41d-45ac-9c85-8db246fa674b)

8. Don’t forget the parameters file. Select Edit parameters, click Load file, and upload the parameters.json.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/71c05c18-ebb8-4213-b1c6-c9e353e29b1d)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a4f9e535-cf0f-42a7-9c7d-4b26e4b172b4)

9. Make this change so it matches the template file.

- Change disks_az104_disk1_name to disk_name (one place to change)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0edd8548-ad66-4d5b-9bfe-cddef8121e1c)

10. Save your changes.

11. Complete the custom deployment settings:

- Setting	Value

Subscription	your subscription
Resource Group	az104-rg3
Region	(US) East US)
Disk_name	az104-disk2

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/dbc0c886-3f18-47fc-ad68-ab86445d56be)

12. Select Review + Create and then select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/eaab5b03-ebd0-4dfc-adda-de3b19033c41)

13. Select Go to resource. Verify az104-disk2 was created.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1f49d682-275a-42b2-944c-0a4b6d4debe0)

15. On the Overview blade, select the resource group, az104-rg3. You should now have two disks.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/7358bf38-6810-453f-851a-d4fcf0395979)

16. In the Settings section, click Deployments.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/68ef7a54-f9a4-44c4-b101-0b68e0bce078)

17. Select a deployment and review the content of the Input and Template blades.

# Task 3: Configure the Cloud Shell and deploy a template with Azure PowerShell

- In this task, you work with the Azure Cloud Shell and Azure PowerShell. Azure Cloud Shell is an interactive, authenticated, browser-accessible terminal for managing Azure resources. It provides the flexibility of choosing the shell experience that best suits the way you work, either Bash or PowerShell. In this task, you use **PowerShell** to deploy a template.

1. Select the Cloud Shell icon in the top right of the Azure Portal. Alternatively, you can navigate directly to

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/90b1958a-5772-4f15-8ae5-a318846c15f2)

2. When prompted to select either Bash or PowerShell, select PowerShell.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c2735913-e838-4e8e-b6aa-17533508fa5c)

3. On the Getting Started screen select Mount storage account and then I want to create a storage account.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/0dbb4231-288a-450e-838a-1c6a8080b726)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/23ccbbf1-8e79-4c38-8e2f-b6df58fb18f8)

- Settings	Values
- 
Subscription	Select your subscription
Resource Group	az104-rg3
Region	select your region
Storage account (Create new)	must be globally unique, between 3 and 24 characters in length, and use numbers and lowercase letters only
File share (Create new)	fs-cloudshell

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/25b2ea18-880f-4295-aed7-3f395b377b28)

4. When completed select Next. You only need to do this the first time you use the Cloud Shell. It will take a couple of minutes to provision the storage.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f7efe50b-9d97-4205-99f8-a224fa0462b2)

5. Use the Upload/Download files icon to upload the template and parameters file from the downloads directory. You will need to upload each file separately.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a26c7633-961b-4ba0-8cf6-ecfd9f1e68d5)

6. Verify your files are available in the Cloud Shell storage.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d76e0755-05ab-4db2-a200-17b80839ecb8)

7. Select the Editor (curly brackets) icon and navigate to the template JSON file.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/43ef8c06-adbb-4929-8220-1c3bc596ffdd)

8. Make a change. For example, change the disk name to az104-disk3. Use Ctrl +S to save your changes.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c78c1752-190a-4e4b-8395-fc256573f56a)

To deploy to a resource group, use New-AzResourceGroupDeployment.

- Code:  New-AzResourceGroupDeployment -ResourceGroupName az104-rg3 -TemplateFile template.json -TemplateParameterFile parameters.json

