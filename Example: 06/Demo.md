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

- In this task, you use the downloaded template to deploy a new managed disk. This task outlines how to quicky and easily repeat deployments.

1. In the Azure portal, search for and select Deploy a custom template.

2. On the Custom deployment blade, notice there is the ability to use a Quickstart template. There are many built-in templates as shown in the drop-down menu.

3. Instead of using Quickstart, select Build your own template in the editor.

4. On the Edit template blade, click Load file and upload the template.json file you downloaded to the local disk.

5. Within the editor pane, make these changes.

- Change disks_az104_disk1_name to disk_name (two places to change)
- Change az104-disk1 to az104-disk2 (one place to change)

6. Notice this is a Standard disk. The location is east us. The disk size is 32GB.

7. Save your changes.

8. Don’t forget the parameters file. Select Edit parameters, click Load file and upload the parameters.json.

9. Make this change so it matches the template file.

- Change disks_az104_disk1_name to disk_name (one place to change)

10. Save your changes.

11. Complete the custom deployment settings:

- Setting	Value

Subscription	your subscription
Resource Group	az104-rg3
Region	(US) East US)
Disk_name	az104-disk2

12. Select Review + Create and then select Create.

13. Select Go to resource. Verify az104-disk2 was created.

14. On the Overview blade, select the resource group, az104-rg3. You should now have two disks.

15. In the Settings section, click Deployments.

16. Select a deployment and review the content of the Input and Template blades.
