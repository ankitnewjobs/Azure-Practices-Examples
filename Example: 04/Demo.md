# Manage Governance via Azure Policy

- In this lab, you learn how to implement your organization’s governance plans. You learn how Azure policies can ensure operational decisions are enforced across the organization. You learn how to use resource tagging to improve reporting.

# Lab scenario

- Your organization’s cloud footprint has grown considerably in the last year. During a recent audit, you discovered a substantial number of resources that do not have a defined owner, project, or cost center. To improve management of Azure resources in your organization, you decide to implement the following functionality:

- apply resource tags to attach important metadata to Azure resources

- enforce the use of resource tags for new resources by using Azure policy

- update existing resources with resource tags

- use resource locks to protect configured resources

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/94eb0315-c37e-4304-a5b2-23468619dcc1)

Job skills

Task 1: Create and assign tags via the Azure portal.

Task 2: Enforce tagging via an Azure Policy.

Task 3: Apply tagging via an Azure Policy.

Task 4: Configure and test resource locks.

# Task 1: Assign tags via the Azure portal

- In this task, you will create and assign a tag to an Azure resource group via the Azure portal. Tags are a critical component of a governance strategy as outlined by the Microsoft Well-Architected Framework and Cloud Adoption Framework. Tags can allow you to quickly identify resource owners, sunset dates, group contacts, and other name/value pairs that your organization deems important

1. Sign in to the Azure portal - https://portal.azure.com.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/83683d54-b74f-4f4c-b61b-fa8ef6e961c0)

2. Search for and select Resource groups.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/2ed29fd8-d471-4078-8cd3-26abdecbe073)

3. From the Resource groups, select + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/5ebd6318-65d5-42d1-93db-24ae8a8269ee)

- Setting	Value

- Subscription name	your subscription

- Resource group name	az104-rg2

- Location	East US

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/fbe3ff12-4a3a-4fbe-ad31-be76320dbcd2)

4. Select Next: Tags and create a new tag.

- Setting	Value

- Name	Cost Center

- Value	000

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/cf6f5f6f-adf2-41f3-a109-863b2cb672bb)


5. Select Review + Create, and then select Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/45177326-7673-4036-90b8-4d4326037ae6)

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/c40e33a9-5107-44ec-ad99-1fe9875a67f0)

# Task 2: Enforce tagging via an Azure Policy

- In this task, you will assign the built-in Require a tag and its value on resources policy to the resource group and evaluate the outcome. Azure Policy can be used to enforce configuration, and in this case, governance, to your Azure resources.

1. In the Azure portal, search for and select Policy.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/671e7dcf-dde3-4d24-8e55-f2b58ea25263)

2. In the Authoring blade, select Definitions. Take a moment to browse through the list of built-in policy definitions that are available for you to use. Notice you can also search for a definition.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d798f2c8-0ede-4d7f-ab03-fbd12d6e2511)

3. Click the entry representing the Require a tag and its value on resources built-in policy. Take a minute to review the definition.

4. On the Require a tag and its value on resources built-in policy definition blade, click Assign.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/f53486f6-b128-45eb-af5f-3de1e9bf434a)


5. Specify the Scope by clicking the ellipsis button and selecting the following values. Click Select when you are done.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/76cf7c3c-557e-4875-8ff8-736221a63d52)

- Setting	Value

- Subscription	your subscription

- Resource Group	az104-rg2

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/a3f71963-62e6-4254-bcff-9c3f1832d688)

6. Configure the Basics properties of the assignment by specifying the following settings (leave others with their defaults):

- Setting	Value

- Assignment name	Require Cost Center tag with the Default value

- Description	Require Cost Center tag with default value for all resources in the resource group

- Policy enforcement	Enabled

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d2074c02-6f43-46e9-a97a-554e8e1fa143)

7. Click Next twice and set Parameters to the following values:

- Setting	Value

- Tag Name	Cost Center
  
- Tag Value	000

  ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6b89dafe-a908-43cb-8d2b-966077f0d095)

8. Click Next and review the Remediation tab. Leave the Create a Managed Identity checkbox unchecked.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/d29b0af1-9d5f-44cf-92c9-7e66dfbd530d)

9. Click Review + Create and then click Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/66ab264b-a539-4642-88e6-fd6ba8d7ce47)

10. In the portal, search for and select Storage Account, and select + Create.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/6128e502-e9ec-4a66-b47d-62003eb52d79)

11. On the Basics tab of the Create storage account blade, complete the configuration.

- Setting	Value

- Resource group	az104-rg2

- Storage account name	any globally unique combination of between 3 and 24 lowercase letters and digits, starting with a letter

  ![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/dda7f01e-353e-49e5-be41-7d8d32eee64d)

12. Select Review and then click Create.

13. You should receive a Validation failed message. View the message to identify the reason for the failure. Verify the error message states that the resource deployment was disallowed by the policy.

![image](https://github.com/ankitnewjobs/Azure-Practices-Examples/assets/154872782/1931cc8d-9366-464c-a654-754356b4b288)

